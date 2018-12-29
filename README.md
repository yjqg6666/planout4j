# PlanOut4J [![Build Status](https://travis-ci.org/yjqg6666/planout4j.svg)](https://travis-ci.org/yjqg6666/planout4j)

Java implementation of Facebook's [PlanOut](https://facebook.github.io/planout/) forked from Glassdoor. 

## Getting Started

See the [Glassdoor repository](https://github.com/glassdoor/planout4j) for a ready-to-use implementation of Planout4j.

The API is hosted on Maven Central:

```
<dependency>
     <groupId>com.glassdoor.planout4j</groupId>
     <artifactId>planout4j-api</artifactId>
     <version>1.1</version>
 </dependency>
 ```
 
 ## Project Modules

* `core` - the most important module. Defines all PlanOut operations, as well as the central classes `Namespace`, `NamespaceConfig`, `Experiment`, and others. Does not depend on any other modules. If one wants to use PlanOut4J programmatically (i.e. without external configuration) or one already has a parsed JSON object representing namespace based on the above "schema", then one needs `core` module only
* `compiler` - this module provide java wrapper for [PlanOut compiler](https://github.com/facebook/planout/tree/master/compiler) as well as tools and API to compile namespace YAML (see above) with embedded PlanOut DSL into JSON.
* `config` - this module defines API for reading namespace configuration data from / writing to a *backend*. Currently *file system backend* and *Redis backend* (both used internally at Glassdoor) are provided. The module also exposes `Planout4jRepository` interface which acts as a facade to one or more *backends*. It depends on `compiler` for parsing the data.
* `api` - this is the primary entry point. It provides `NamespaceFactory` interface and several implementations. It depends on `config` for loading up each individual *namespace* and maintains a cache of those keyed by name. This is what majority of developers will likely use.
* `tools` - this contains all command-line tools. Tools are described in details in the [usage](USAGE.md) document.
* `demos` - this is what you think it is
 
 ## Contributing
 
 We welcome contributions! Please raise an issue with any proposals.
