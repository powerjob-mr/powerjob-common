# powerjob-common

Shared parent POM, common model and utilities, and the remote communication framework with its Akka, HTTP and MU transports.

Split from [PowerJob](https://github.com/PowerJob/PowerJob) at upstream commit
`d92ad66277ca54e14e2835b2e5a6aaf01f620684` (release 5.1.7). The Git history of retained files is preserved,
including earlier names of the modules; filtering rewrites commit IDs.

## Build

Install JDK 8 and Maven 3.9, then run from this repository:

```bash
mvn -B clean verify
```

This repository has no PowerJob dependencies. It provides the parent POM
`tech.powerjob:powerjob` and libraries used by the other PowerJob repositories.

JDK 8 is the version upstream targets and the version verified locally.
See [build-verification.json](build-verification.json) for the local build results.

## Included modules

- `powerjob-common/`
- `powerjob-remote/`

## Excluded tests

These upstream tests cannot pass in a clean build and are excluded in their
module's surefire configuration. Upstream CI does not run tests.

- `tech.powerjob.remote.framework.engine.RemoteEngineTest` (powerjob-remote/powerjob-remote-framework): Stale: starts an engine without registering actors, so ActorFactory throws NullPointerException.
- `tech.powerjob.remote.framework.engine.impl.CSInitializerFactoryTest#testNotFind` (powerjob-remote/powerjob-remote-framework): Stale: expects PowerJobException for an unknown type, but the current code throws NoSuchMethodException.

## Origin

See [UPSTREAM-README.md](UPSTREAM-README.md) for the original project overview
and [split.json](split.json) for the split manifest.

## License

Apache License 2.0; see [LICENSE](LICENSE).
