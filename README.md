# The Rubinius Build Repository

The Rubinius language platform is made up of various components, some of which are maintained by other groups. The purpose of this repository is to provide a way to build everything at once, while still maintaining the boundaries around the individual components.

## Design Rationale

There are four audiences for a software component:

1. Core developers
1. Contributors
1. System maintainers / packagers
1. End users

Core developers need sharp tools and use them often. They want quick development cycles, and they want to be able to merge contributions with confidence.

Contributors need an extremely smooth getting started experience and ease in adding their contributions.

Almost every flavor of Unix/Linux has its unique way of building and maintaining software packages for that system. System maintainers and packagers want the least friction possible when packaging for their system. Usually, this means as standard as possible build systems and parameterizing things so they can be customized to the system's approach without maintaining brittle patchsets.

End users want to install a package on their favorite system and get value from using a piece of software with as little effort as possible.

Among these four audiences, if anyone is going to suffer, it has to be the core developers. If the package managers have to deal with a lot of frustration, they will either hate you or just not support your package.

If contributors have to deal with a lot of confusing steps or cumbersome dependencies, they just won't waste their time.

If you don't have contributors and package maintainers, you will have very few users.

The approach used here tries to strike a balance as follows:

* Keep boundaries as tight as possible: Don't vendor things that are separate components. Don't add significant build dependencies, like Ruby.
* Keep build steps explicit and "accessible": Build steps are combined into build scripts invoked as make targets. They can be decomposed and recomposed in packaging systems without burdening the package managers with writing extra custom code. The more granular and standard, the more likely a system package manager can be easily configured for your "recipe".
* Make it easy to clone and go, there should be no step 3. For example, clone the repo, type `make` or maybe `make help` and then `make`.

## Getting Started

To build everything, type `make`.

```
$ make help
Usage:
  make <target>

Dependencies
  setup            Clone all components

Devolpment
  build            Build all components

Testing
  test             Run the tests

Maintenance
  clean            Remove all build artifacts
  help             Display this help
```

## License

Copyright held by Rubinius Contributors, licensed under [BSD 3-clause](/LICENSE).
