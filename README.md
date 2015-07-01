# npm-standard
An opinionated NPM module structure format

*Inspired by [feross/standard](https://github.com/feross/standard) and [ahmadnassri/npm-package-generator](https://github.com/ahmadnassri/npm-package-generator)*

### One Style to Rule Them All

No decisions to make. You don't have to stress about folder structure or naming standards. It just works

This module saves you (and others!) time in two ways:

- **No configuration.** The easiest way to start an npm module project, or see if yours is up to snuff
- **Catch style errors before they're submitted in PRs.** Saves precious code review time by eliminating back-and-forth between maintainer and contributor.

## Install

```bash
npm install npm-standard
```

## Rules

### General

- keep your package dependencies lean, only include useful files for developers when running `npm install` *(see package.json + .npmignore files)*
- Expose your modules library files in `lib/`, if not included in your normal dependencies

### Configuration

- use `.env` files and [`dotenv`](https://www.npmjs.com/package/dotenv) for configuration, *following the tenets of a [twelve-factor app](http://12factor.net/)*
  - only use `dotenv` in your application entry point, *or library if applicable*.
  - supply a `.env.template` file for your users, with applicable variables included.
- use  `.travis.yaml` files to ensure Travis CI build success
  - use container mode in [`travis`](https://travis-ci.org/) and leverage folder caching.
- use [`.editorconfig`](http://editorconfig.org/) files for editor standardization

### Testing

- Put all tests in a `test/` subfolder
- Put any applicable fixtures in `test/fixtures`
- use [`mocha`](https://www.npmjs.com/package/mocha) for testing
- use [`istanbul`](https://www.npmjs.com/package/istanbul) to generate coverage reports
- publish coverage reports to [codeclimate](https://codeclimate.com/) *(requires configuring travis with the appropriate `CODECLIMATE_REPO_TOKEN`)*
- use [`standard`](https://www.npmjs.com/package/standard) and [`echint`](https://www.npmjs.com/package/echint) for linting files

### Scripting

- enforce `standard` & `echint` by running on [`pretest`](https://docs.npmjs.com/misc/scripts)
- always generate code coverage reports by running `istanbul` on [`posttest`](https://docs.npmjs.com/misc/scripts)

### Templates

- if your module requires them, place templates in a `templates/` folder in the root of your module for easy access.

### Lib choices

While these are less important, there are a number of standard libs that work very well for common tasks:

- For debugging, try using [`debug-log`](https://www.npmjs.com/package/debug-log) or [`trace-debug-log`](https://www.npmjs.com/package/trace-debug-log) to provide helpful debugging messages without the use of `console.log`
- CLI Module? try [`commander`](https://www.npmjs.com/package/commander) to provide a CLI (Command Line Interface)

### Licensing

Always include a `LICENSE` file in your module. This will let developers know the usage parameters of your package. I suggest linking whatever license you use to the appropriate page on [tldrlegal.com](http://tldrlegal.com) for a layman terms application of your licensing rules.

- If you want your module to be open source, use a permissive license, like [`MIT`](https://tldrlegal.com/license/mit-license) or [`ISC`](https://tldrlegal.com/license/-isc-license)

### Docs

- Include a Table of Contents in large doc files, linking to the appropriate subheadings **(this heading, for example, would be [`[Docs](#docs)`](#docs) in a ToC)
- Include a `CONTRIBUTING` file to your module so people wanting to help out know where to find info about it. Place this in the root of your module so Github knows where to find it.
- Include any installation information in `docs/INSTALL.md`
- Include an API document at `docs/API.md`
- Maintain an active [`CHANGELOG.md`](http://keepachangelog.com/) in the root of your module
- Link all four documents in your `README.md` file

**Note: If your docs files are especially small, you can forgo putting them in separate files, and just keep them in your `README.md` file.**

### Folder Structure

```
  /package-name/
  ├── bin
  │   └── package-name
  ├── docs
  │   ├── API.md
  │   └── INSTALL.md
  ├── .editorconfig
  ├── .env.example
  ├── .gitattributes
  ├── .gitignore
  ├── .jshintrc
  ├── lib
  │   └── index.js
  ├── templates
  ├── LICENSE
  ├── CONTRIBUTING
  ├── CHANGELOG.md
  ├── .npmignore
  ├── package.json
  ├── README.md
  ├── src
  │   └── index.js
  ├── test
  │   ├── fixtures
  │   └── index.js
  └── .travis.yml
```

#### File Explanations

##### `bin/package-name`
##### `docs/API.md`
##### `docs/INSTALL.md`
##### `.editorconfig`
##### `.env`
##### `.gitattributes`
##### `.gitignore`
##### `.jshintrc`
##### `lib/index.js`
##### `LICENSE`
##### `CONTRIBUTING`
##### `CHANGELOG.md`
##### `.npmignore`
##### `package.json`
##### `README.md`
##### `src/index.js`
##### `test/fixtures/`
##### `test/index.js`
##### `.travis.yml`

## API
### Linting

You can lint the module you are in to see if it conforms to this style guide by running in the command line

```bash
npm-standard
```

This will run tests against the folder structure and files and give warnings for any additional files than what is listed here, and give errors for missing files.

### Start a new project or convert an old one

If you want to convert the folder you are in to npm-standard, you can do so via

```bash
npm-standard init
```

or

```bash
npm-standard fix
```

Both of these commands will lint the current directory, and fill in any missing files. It will also check the files present for proper structure and content, specifically configuration files for missing items.

## Contributing

## Changelog

## License
