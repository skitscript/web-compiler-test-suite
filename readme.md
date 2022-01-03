# Skitscript Web Compiler Test Suite [![License](https://img.shields.io/github/license/skitscript/web-compiler-test-suite.svg)](https://github.com/skitscript/web-compiler-test-suite/blob/master/license) [![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com/)

A test suite for compilers of Skitscript documents targeting the web.

## Installation

It is recommended to install this as a Git submodule and use the included test
cases in your project's test suite:

```bash
git submodule add https://github.com/skitscript/web-compiler-test-suite submodules/skitscript/web-compiler-test-suite
```

### Renovate Updates

If you are using Renovate in your project, add
[the following](https://docs.renovatebot.com/modules/manager/git-submodules/) to
its `renovate.json` to automatically raise PRs when changes are pushed to this
repository:

```json
{
  "git-submodules": {
    "enabled": true
  }
}
```

## Usage

The [cases](./cases) directory contains a number of subdirectories.  Each
contains a standard set of files:

### [input/script.skitscript](./cases/basic-example/input/document.skitscript)

This is the document which is compiled.

### [input/markup.pug](./cases/basic-example/input/markup.pug)

This is the Pug template file used when compiling the document.

TODO: what data structures are passed to this template file?

### [input/styles.sass](./cases/basic-example/input/styles.sass)

This is the Sass stylesheet used when compiling the document.

TODO: how is this used?

### [input/backgrounds/{name}.{svg, png}](./cases/basic-example/input/backgrounds/podium.svg)

A separate image exists for each background.  They might be in SVG or PNG
format.

### [input/characters/{character name}/emotes/{emote name}.{svg, png}](./cases/basic-example/input/characters/mr-explainer/neutral.svg)

A separate image exists for each emote of each character.  They might be in SVG
or PNG format.

### [error.json](./cases/missing-background-image/error.json)

When this file exists, compilation must fail and present an error similar to
that described within this file.

When it does NOT exist, the `scenarios` subdirectory must exist instead.

### [scenarios/{scenario name}/interactions.json](./cases/basic-example/scenarios/set-flag-b/interactions.json)

This file describes the interactions made by the user during this scenario.

### [scenarios/{scenario name}/result.png](./cases/basic-example/scenarios/set-flag-b/result.png)

This is a screenshot of what the user should see following the interactions
specified in `interactions.json`.  An exact match is not expected or required,
but the resulting rendering must be within a tight margin of error.
