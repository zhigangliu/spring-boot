# Spring Boot essentials
* Automatic configuration

  if library is detected in classpath, Bean is automatic configured
* Starter dependencies

  Starter dependencies are special Maven dependencies
that take advantage of transitive dependency resolution to aggregate commonly
used libraries under a handful of feature-defined dependencies.
* The command-line interface
* The Actuator

  inspect the internals of the application at runtime
# Initializr
https://start.spring.io/

# Annotation
* `@SpringBootApplication`

  combines `@Configuration`, `@ComponentScan`, `@EnableAutoConfiguration`
* `@SpringApplicationConfiguration` version 1.3

  it is used in test, similar to `@ContextConfiguration`, but uses Spring Boot's SpringApplicationContextLoader

# Application properties

  application.properties

  it will be loaded and its properties made available for configuring both Spring and application code

# Starter POM hierarchy
* spring-boot-build (level 1)

  defines spring-boot revision

  defines modules of the whole spring-boot project
* spring-boot-dependencies (level 2)

  defines compatible versions of all libraries via `properties` and `dependencyManagement`
* spring-boot-parent (level 3)

  defines compatible versions of additional libraries via `dependencyManagement`
  
  defines dependencies of test scope
* spring-boot-starters (level 4)

  aggregated project of all starter modules
  
  common parent of all starters (where nothing important to be inherited)
* spring-boot-starter (level 5)

  spring boot basic grouped dependencies

  including spring-boot, spring-boot-autoconfigure, spring-boot-starter-logging, javax.annotation-api, spring-core etc.

  it will be used as POM dependency for other starter modules
* spring-boot-starter-web (level 5, but depends on spring-boot-starter)

  it will be used as application dependency
* spring-boot-starter-parent (level 3)

  it inherits spring-boot-dependencies

  as a parent POM of application pom, it provides dependency and plugin management (e.g. repackage goal of spring-boot-maven-plugin)

# spring-boot-maven-plugin

  `spring-boot:run` runs the Spring Boot application

  `mvn package` generate an uber-jar

# Overriding starter dependency

* exclude unused transitive dependencies
* specify version explicitly (nearest wins)