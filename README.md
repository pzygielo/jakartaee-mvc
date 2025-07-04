[![Java CI with Maven](https://github.com/jakartaee/mvc/actions/workflows/main.yml/badge.svg)](https://github.com/jakartaee/mvc/actions/workflows/main.yml)

# Jakarta MVC Specification and API

This project contains the specification document and Java API sources. The project
is organized into two modules: _api_ and _spec_.
The _api_ module contains the Java API sources, which may be used to generate the
API JAR and JavaDoc.
The _spec_ module contains the specification document sources, which may be used
to generate the specification document.

## Generating the API and JavaDoc

Just enter `mvn clean install` at the command line. Maven will generate the following artifacts.

API Jar::
* The jar containing the api interfaces and classes.
* In the directory: `/api/target`

API JavaDoc::
* The JavaDoc for the api interfaces and classes.
* In the directory: `api/target/apidocs`

## Generating the Specification

run `mvn clean install` in the `spec` directory

The PDF and HTML will be generated in `spec/target/generated-docs/`

## Tagging phrases for the TCK

The [Jakarta MVC TCK](https://github.com/jakartaee/mvc-tck) is a suite of unit
tests for validating the compliance of MVC implementations with the specification.

The tests of the TCK are based on assertions representing sentences and phrases in this
specification. Labels on specific text elements of the specification are used to mark those which
should lead to an assertion in the TCK. The following values are allowed:

* `tck-testable`: The tagged element must be represented by a testable assertion in the TCK
* `tck-not-testable`: The tagged element must be represented by a non-testable assertion in the
TCK (e.g. assertions regarding thread safety)
* `tck-ignore`: The tagged element must be excluded when creating a TCK assertion for an outer
element. Can be used to exlude explanatory phrases contained in an element marked as `tck-testable`.
* `tck-needs-update`: The tagged element must be marked with a note in the TCK audit file saying
that the tests for this assertion need to be updated, e.g. due to a spec update. Can be used
together with `tck-testable` and `tck-not-testable`: `[tck-testable tck-needs-update]#Some sentence...#`.
* `tck-id-SOME_ID`: This tag defines an ID that has to be used to reference this particular assertion
in the TCK. SOME_ID can be any text, number or special character`- anything up to the next space " " or
closing bracket ]` will be taken as the ID. Can be used together with `tck-testable`:
`[tck-testable tck-id-http://some.issue.tracker/url]#Some sentence...#`. `tck-testable` without a
defined id will get a letter assigned as their ID, in the order of apperance within their section
(a, b, c, ...)

## Audit XML to calculate spec coverage in tests

`mvn clean install` (or just `mvn generate-resources`) in the `spec` directory will create a `tck-audit.xml` file under
`target/generated-docs`. This file contains the `[tck-testable]` assertions found in the spec (asciidoc),
and is used in the TCK project to analyse the spec coverage in tests.

The process is copied and adapted from the beanvalidation spec project
(https://github.com/jakartaee/validation).

## TCK Challenge and resolution process for Jakarta MVC

Test challenges for Jakarta MVC may be resolved through Lazy Consensus. Please see the TCK Users Guide for Jakarta MVC for more details.
