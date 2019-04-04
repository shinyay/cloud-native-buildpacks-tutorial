# Cloud Native Buildpacks

Overview

## Description

## Demo

## Features

- feature:1
- feature:2

## Requirement

## Usage

## Installation

### Installing Pack
#### Brew Install for Mac

```
$ brew tap buildpack/tap
$ brew install pack
```

#### Pack Command

```
$ pack -h

Usage:
  pack [command]

Available Commands:
  build                 Generate app image from source code
  run                   Build and run app image (recommended for development only)
  rebase                Rebase app image with latest run image
  create-builder        Create builder image
  set-run-image-mirrors Set mirrors to other repositories for a given run image
  inspect-builder       Show information about a builder
  set-default-builder   Set default builder used by other commands
  version               Show current 'pack' version
  help                  Help about any command

Flags:
  -h, --help         Help for 'pack'
      --no-color     Disable color output
  -q, --quiet        Show less output
      --timestamps   Enable timestamps in output

Use "pack [command] --help" for more information about a command.
```

#### Initial Setup for Pack

```
Please select a default builder with:

	pack set-default-builder <builder image>

Suggested builders:

	Cloud Foundry:     cloudfoundry/cnb:bionic         small base image with Java & Node.js
	Cloud Foundry:     cloudfoundry/cnb:cflinuxfs3     larger base image with Java, Node.js & Python
	Heroku:            heroku/buildpacks               heroku-18 base image with official Heroku buildpacks


Tip: Learn more about a specific builder with:
```

```
$ pack set-default-builder cloudfoundry/cnb
```

#### Back Build

```
$ cd PATH/TO/APPDIR
$ pack build java-app
```

```
Defaulting app directory to current working directory /Users/shinyay/workspace/qiita/cloud-native-buildpacks/sample-java-app (use --path to override)
Using default builder image cloudfoundry/cnb
Pulling builder image cloudfoundry/cnb (use --no-pull flag to skip this step)
latest: Pulling from cloudfoundry/cnb
Digest: sha256:758bd1a261e384f0a5495db89cca9ba447dddda00ab60f9d47fe8f788efa4d4e
Status: Image is up to date for cloudfoundry/cnb:latest
Selected run image cfbuildpacks/cflinuxfs3-cnb-experimental:run from builder cloudfoundry/cnb
Pulling run image cfbuildpacks/cflinuxfs3-cnb-experimental:run (use --no-pull flag to skip this step)
run: Pulling from cfbuildpacks/cflinuxfs3-cnb-experimental
Digest: sha256:ce68ae528bd7620145c67b209cfcfe585d2658f84b47974537008ac758512fa1
Status: Image is up to date for cfbuildpacks/cflinuxfs3-cnb-experimental:run
Using cache image pack-cache-e8510ea38131
===> DETECTING
[detector] Trying group of 8...
[detector] ======== Results ========
[detector] Cloud Foundry OpenJDK Buildpack: pass
[detector] Cloud Foundry Build System Buildpack: pass
[detector] Cloud Foundry JVM Application Buildpack: pass
[detector] Cloud Foundry Azure Application Insights Buildpack: skip
[detector] Cloud Foundry Debug Buildpack: skip
[detector] Cloud Foundry Google Stackdriver Buildpack: skip
[detector] Cloud Foundry JMX Buildpack: skip
[detector] Cloud Foundry Procfile Buildpack: skip
===> RESTORING
[restorer] cache image 'pack-cache-e8510ea38131' not found, nothing to restore
===> ANALYZING
[analyzer] WARNING: image 'java-app' not found or requires authentication to access
[analyzer] WARNING: image 'java-app' has incompatible 'io.buildpacks.lifecycle.metadata' label
===> BUILDING
[builder] -----> Cloud Foundry OpenJDK Buildpack 1.0.0-M6
[builder] -----> OpenJDK JDK 11.0.2: Contributing to layer
[builder]        Downloading from https://java-buildpack.cloudfoundry.org/openjdk-jdk/bionic/x86_64/openjdk-11.0.2_09.tar.gz
[builder]        Verifying checksum
[builder]        Expanding to /layers/org.cloudfoundry.openjdk/openjdk-jdk
[builder]        Writing JAVA_HOME to build
[builder]        Writing JDK_HOME to build
[builder] -----> OpenJDK JRE 11.0.2: Contributing to layer
[builder]        Downloading from https://java-buildpack.cloudfoundry.org/openjdk/bionic/x86_64/openjdk-11.0.2_09.tar.gz
[builder]        Verifying checksum
[builder]        Expanding to /layers/org.cloudfoundry.openjdk/openjdk-jre
[builder]        Writing JAVA_HOME to shared
[builder]
[builder] -----> Cloud Foundry Build System Buildpack 1.0.0-M6
[builder] -----> Using wrapper
[builder]        Linking Cache to /home/vcap/.m2
[builder] -----> Compiled Application: Contributing to layer
[builder] [INFO] Scanning for projects...
[builder] Downloading from central: https://repo.maven.apache.org/maven2/org/springframework/boot/spring-boot-starter-parent/2.1.3.RELEASE/spring-boot-starter-parent-2.1.3.RELEASE.pom
Downloaded from central: https://repo.maven.apache.org/maven2/org/springframework/boot/spring-boot-starter-parent/2.1.3.RELEASE/spring-boot-starter-parent-2.1.3.RELEASE.pom (12 kB at 19 kB/s)
[builder] Downloading from central: https://repo.maven.apache.org/maven2/org/springframework/boot/spring-boot-dependencies/2.1.3.RELEASE/spring-boot-dependencies-2.1.3.RELEASE.pom
Downloaded from central: https://repo.maven.apache.org/maven2/org/springframework/boot/spring-boot-dependencies/2.1.3.RELEASE/spring-boot-dependencies-2.1.3.RELEASE.pom (143 kB at 289 kB/s)
[builder] Downloading from central: https://repo.maven.apache.org/maven2/com/fasterxml/jackson/jackson-bom/2.9.8/jackson-bom-2.9.8.pom
Downloaded from central: https://repo.maven.apache.org/maven2/com/fasterxml/jackson/jackson-bom/2.9.8/jackson-bom-2.9.8.pom (12 kB at 46 kB/s)
[builder] Downloading from central: https://repo.maven.apache.org/maven2/com/fasterxml/jackson/jackson-parent/2.9.1.2/jackson-parent-2.9.1.2.pom
Downloaded from central: https://repo.maven.apache.org/maven2/com/fasterxml/jackson/jackson-parent/2.9.1.2/jackson-parent-2.9.1.2.pom (7.9 kB at 30 kB/s)
    :
    :
    :
[builder] Downloading from central: https://repo.maven.apache.org/maven2/com/google/guava/guava/19.0/guava-19.0.jar
Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-dependency-tree/3.0.1/maven-dependency-tree-3.0.1.jar (37 kB at 10 kB/s)
Downloaded from central: https://repo.maven.apache.org/maven2/org/vafer/jdependency/2.1.1/jdependency-2.1.1.jar (186 kB at 49 kB/s)
[builder] Downloaded from central: https://repo.maven.apache.org/maven2/org/ow2/asm/asm-util/7.0-beta/asm-util-7.0-beta.jar (81 kB at 21 kB/s)
Downloaded from central: https://repo.maven.apache.org/maven2/org/jdom/jdom2/2.0.6/jdom2-2.0.6.jar (305 kB at 78 kB/s)
Downloaded from central: https://repo.maven.apache.org/maven2/com/google/guava/guava/19.0/guava-19.0.jar (2.3 MB at 321 kB/s)
[builder] [INFO] Replacing main artifact with repackaged archive
[builder] [INFO] ------------------------------------------------------------------------
[builder] [INFO] BUILD SUCCESS
[builder] [INFO] ------------------------------------------------------------------------
[builder] [INFO] Total time:  02:00 min
[builder] [INFO] Finished at: 2019-04-04T01:30:58Z
[builder] [INFO] ------------------------------------------------------------------------
[builder]        Removing source code
[builder]
[builder] -----> Cloud Foundry JVM Application Buildpack 1.0.0-M6
[builder] -----> Configuring Java Main Application
[builder] -----> Process types:
[builder]        task: java -cp /workspace $JAVA_OPTS org.springframework.boot.loader.JarLauncher
[builder]        web:  java -cp /workspace $JAVA_OPTS org.springframework.boot.loader.JarLauncher
[builder]
===> EXPORTING
[exporter] WARNING: image 'java-app' not found or requires authentication to access
[exporter] WARNING: image 'java-app' has incompatible 'io.buildpacks.lifecycle.metadata' label
[exporter] adding layer 'app' with diffID 'sha256:d1bfc76835e153d32062ae728533a9da2d578b0a09ef2491e65c60027f5ae2e7'
[exporter] adding layer 'config' with diffID 'sha256:ec1ed280bf3fdf97e46bb85ac185568abe3b4cb4d6fdf5bf47640dd1d5e8175e'
[exporter] adding layer 'launcher' with diffID 'sha256:49b31af4c438b42f9c0cf2c8a376052e224f5a140dd00f4addbebee97318df3a'
[exporter] adding layer 'org.cloudfoundry.openjdk:openjdk-jre' with diffID 'sha256:3391714c2d7d78389249f508527db686879cf5aaa0db60210da862977b527f23'
[exporter] setting metadata label 'io.buildpacks.lifecycle.metadata'
[exporter] setting env var 'CNB_LAYERS_DIR=/layers'
[exporter] setting env var 'CNB_APP_DIR=/workspace'
[exporter] setting entrypoint '/lifecycle/launcher'
[exporter] setting empty cmd
[exporter] writing image
[exporter]
[exporter] *** Image: java-app@7e70b862c19abe26687499f9163b77fd6527127704161df2d767bb9cd46d1520
===> CACHING
[cacher] WARNING: image 'pack-cache-e8510ea38131' not found or requires authentication to access
[cacher] WARNING: image 'pack-cache-e8510ea38131' has incompatible 'io.buildpacks.lifecycle.cache.metadata' label
[cacher] adding layer 'org.cloudfoundry.openjdk:043ec39d0b7dfbf468a3981f85f401414bc34c59eadfa33c927e4b40e6df6820' with diffID 'sha256:a3750874bd0032476ff89b91e285defb42a626aa7832d90c113bcfcd367fe70e'
[cacher] adding layer 'org.cloudfoundry.openjdk:a8b75a7919ce0933230da1ec8bd4bc320acd3b343a72b592bf1b85646a9367b1' with diffID 'sha256:0cf21135c948203e9c7ffef68eb183dde0d6675315b5ac308dc506c643a6bc43'
[cacher] adding layer 'org.cloudfoundry.openjdk:openjdk-jdk' with diffID 'sha256:8241a9cff6d5a10c1c1779260e755d06d754f633267d6527ddc2d27fce659561'
[cacher] adding layer 'org.cloudfoundry.buildsystem:build-system-cache' with diffID 'sha256:3e398f05594b1181ee3d5206a9e436e57e38924ae6c86614ed9eda888dc7f9cb'
[cacher] setting metadata label 'io.buildpacks.lifecycle.cache.metadata'
[cacher] writing image
[cacher] cache 'pack-cache-e8510ea38131@f8e985c51e763848715fbfe02b2f04827d3127d4c82d284b17c40145bc3f7929'
Successfully built image java-app
```

```
$ docker images

REPOSITORY                                 TAG                 IMAGE ID            CREATED             SIZE
pack-cache-e8510ea38131                    latest              f8e985c51e76        2 minutes ago       626MB
java-app                                   latest              7e70b862c19a        2 minutes ago       1.28GB
cfbuildpacks/cflinuxfs3-cnb-experimental   run                 521b742c6a7d        10 hours ago        1.13GB
cloudfoundry/cnb                           latest              516ed9227fd7        34 hours ago        1.31GB
mysql                                      5.7                 07eaaab72756        38 hours ago        372MB
```

```
$ docker run --rm -p 8080:8080 java-app
```

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/44f0f4de510b4f2b918fad3c91e0845104092bff/LICENSE)

## Author

[shinyay](https://github.com/shinyay)