# static-dojo-site-generator

Boilerplate for static Dojo-based website generation.

## Purpose

This project provides a boilerplate infrastructure for static website generation using [jekyll](https://github.com/mojombo/jekyll) and taking into account the specifics of working with [Dojo](http://dojotoolkit.org/). Dojo uses filenames starting with an underscore which have special meaning to jekyll. static-dojo-site-generator makes the two play nicely together and results in websites suitable for [Github Pages](http://pages.github.com/) or any other static hosting situation. For an example take a look a the [dobolo website](http://sirprize.github.com/dobolo/)

## Getting Started

+ `git clone https://github.com/sirprize/static-dojo-site-generator`
+ `cd static-dojo-site-generator`
+ `git submodule init`
+ `git submodule update`

## Workflow

Generating a static website is a 3-step process:

### 1. Developing The Website

These are the steps involved during development:

1. `cd bin/dev`
1. `jekyll --auto`

Point browser to `_development/` and browse the website. Make corrections to the files in `html/` and `assets/` until everything is as desired. Whenever you save a file in `html/`, jekyll regenerates the website into `_development`.

### 2. Creating The Production Build

Execute those steps when you are satisfied with the website. The production build workflow uses a slightly different jekyll configuration and optimizes asset files (Javascript and CSS).

1. `cd bin/prod`
1. `./assets.sh`
1. `jekyll`

Point your browser to `_production/` to browse the production build.

### 3. Creating The Deployment Build

In these steps we will collect all the required files, make some last modifications and copy everything to `_deploy/`:

1. `cd bin/deploy`
1. `phing`
1. Copy contents of `_deploy/` to your webserver (... or the `gh-pages` branch of your Github-hosted project)

Running `phing` in `_deploy/` completely regenerates the develpment-, production- and deployment builds.

## Structure

All the root dirs starting with an underscore contain generated files - do not edit in those places!

    + _assets (javascript/css production build)
    + _deploy (final website)
    + _development (destination dir for jekyll development build)
    + _production (destination dir for jekyll production build)
    + assets
        + scripts
        + styles
        + vendor
    + bin
        + dev (commands for use during development)
        + prod (commands to generate the production build)
        + deploy (command to generate the deployment build)
    + html (jekyll source dir)
        + index.html

## Starting From Scratch And Putting Your Project Under Git

+ `git clone https://github.com/sirprize/static-dojo-site-generator your-project-name`
+ `cd your-project-name`
+ `sudo rm -dR .git`
+ `rm .gitmodules`
+ `rm -dR assets/vendor`
+ `git init`
+ `git submodule add git://github.com/dojo/dojo.git assets/vendor/dojo/dojo`
+ `git submodule add git://github.com/dojo/util.git assets/vendor/dojo/util`
+ `git submodule add git://github.com/twbs/bootstrap.git assets/vendor/twbs/bootstrap`
+ `git submodule add git://github.com/sirprize/dojo-form-controls.git assets/vendor/sirprize/dojo-form-controls`
+ `git submodule add git://github.com/sirprize/dobolo.git assets/vendor/sirprize/dobolo`
+ `git submodule add git://github.com/sirprize/mijit.git assets/vendor/sirprize/mijit`
+ `git add .`
+ `git commit -m "Initial import"`

## Dependencies

+ [dojo/dojo](http://github.com/dojo/dojo)
+ [dojo/util](http://github.com/dojo/util)
+ [twbs/bootstrap](http://github.com/twbs/bootstrap.git)
+ [sirprize/dojo-form-controls](http://github.com/sirprize/dojo-form-controls.git)
+ [sirprize/dobolo](http://github.com/sirprize/dobolo.git)
+ [sirprize/mijit](http://github.com/sirprize/mijit.git)
+ [aFarkas/html5shiv](https://github.com/aFarkas/html5shiv)
+ [google-code-prettify](http://code.google.com/p/google-code-prettify/)

## Requirements

+ [jekyll](https://github.com/mojombo/jekyll)
+ [phing](http://www.phing.info/)

## License

static-dojo-site-generator is released under the [MIT license](http://opensource.org/licenses/mit-license.php)