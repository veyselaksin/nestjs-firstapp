# NestJS Application Structure

## Description

We have AppModule, which is the root module of our application. It is decorated with the @Module() decorator, which provides metadata that Nest makes use of to organize the application structure.

The @Module() decorator provides the metadata that Nest uses to organize the application structure. It is pointing to the which has the controller, service, etc. The @Module() decorator is required to be present on all modules.

## API Endpoints

The following endpoints are sample endpoints that can be used to test the application:

- GET /api/users
- GET /api/users/:id
- POST /api/users
- PUT /api/users/:id
- DELETE /api/users/:id

## Objectives

- Create a new NestJS application using the Nest CLI
- Develop a REST API using NestJS
- CRUD operations
- Error handling
- Data validation
- Logging
- Data Transfer Objects (DTO)
- System modularity
- Authentication
- Security best practices (hashing, encryption, environment variables)
- Backend development best practices

## Objectives - Persistence

- Use a relational database to persist data
- Use an ORM library to interface with the database
- Simple and complex SQL queries using query builder
- Performance when working with a database

## Objectives - Authentication/Authorization

- Sign up and sign in users
- Authenticate users using JWT
- Password hashing, encryption and salting
- Ownership of resources

## NestJS Modules

- Each application has at least one module, a root module. The root module is the starting point Nest uses to build the application graph - the internal data structure Nest uses to resolve module and provider relationships and dependencies.

- Modules are used to organize the application structure into cohesive blocks of related functionality.

- It is a good practice to have a module for each feature. For example, if we have a users feature, we can create a UsersModule. If we have a cats feature, we can create a CatsModule.

- Modules are singletons by default, therefore the objects they provide are shared across other modules. If you want to scope a module, you can use the @Module() decorator's scope property.

### Module Properties

**providers**: An array of providers to be available within the current module. The providers array is required. The providers to be available within the current module are listed here. They can be injected anywhere in the current module.

**controllers**: An array of controllers to be instantiated within the current module. The controllers array is required. The controllers listed here are automatically provided by the current module. They can be injected anywhere in the current module.

**imports**: An array of modules to import into the current module. The imports array is optional. The modules listed here are made available to the current module. They can be injected anywhere in the current module.

**exports**: An array of providers to export from the current module. The exports array is optional. The providers listed here are then available to be used by modules that import this module.

### Controllers

- Bound to a specific path (or paths) - the request object is routed to a controller based on its URL.
- Controllers contain handler methods that are responsible for handling incoming requests and returning responses to the client.
- Can take advantage of dependency injection to consume providers within the same module.

### Providers

- Can be injected into controllers, components, or other providers (classes).
- Providers must be decorated with the @Injectable() decorator function.
- Nest creates a single, shared instance of each provider class to inject it into any class that requires it.
- Providers can have dependencies. Nest will detect this and resolve them according to the provider's requirements.
- Can be exported from a module so it can be used by other modules that import this module.

### Services

- Services are a type of provider, with the only difference being that a service is decorated with the @Injectable() decorator function.
- Not all providers are services, but every service is a provider.
- Services are the most common type of provider in Nest.
- Services are usually organized into their own files, e.g. user.service.ts.
- Singleton when wrapped with @Injectable() decorator. The same instance of the service is shared across the entire module.
- The main source of business logic.
