# Simple Autoloader for WordPress

An [autoloader](http://php.net/manual/en/language.oop5.autoload.php) that aims to be as simple as dropping it into your WordPress project. All you need is a well-organized project.

## More Information

**TL;DR:** An autoloader you can drop into a WordPress plugin and begin using it automagically.

In 2017, I gave a talk at WordCamp Atlanta about the importance of using 
[Namespaces and Autoloading](https://tommcfarlin.com/namespaces-and-autoloading-2017/) in WordPress.

Though for many projects, we can't adopt many of the new features of PHP7+, that doesn't mean can't use 
best practices when working on plugins and other projects.

I have a _very_ simple autoloader that I'm sharing in this repository that I hope the greater (and smarter!) WordPress 
developers at large will contribute to improving.

## Getting Started

This particular section is for those who want to _use_ the autoloader. If you're looking to contribute to the codebase,
please see the section below.

1. Clone or download this repository.
2. Copy the `lib` directory into the root of your project.
3. Add `include_once 'lib/autoload.php'` to your main plugin file.

### An Example

This autoloader expects several things: 

1. You're following the [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/#naming-conventions) as it relates to naming your classes.
2. The structure of your namespaces follows the structure of your directory structure

I've provided an example below for how both your code and your directory should be organized to take advantage of the 
autoloader.
 
### The Code

Let's say you have a plugin and one of the files contains the following namespace:

```php
namespace Pressware\API;
```

And it's using a class in another namespace:

```php
use Pressware\Utility\Files\Reader;
```

The autoloader expects that the root namespace defined in your main plugin file to be:

```php
namespace Pressware
```

### The Directory Structure

And that all of the rest of the files are located in a directory structure like this:
```
+ plugin-name
|
|   API
|       ...
|       ...
|
|   Utility
|       ...
|
|   Files
|       class-reader.php
|       ...
|
|   plugin-bootstrap.php
```

### Adding The Autoloader

Then, at the top of your plugin file add the following:

`require_once 'lib/autoload.php';`

This can work alongside another other autoloaders (such as those that come with Composer) and will prevent you from 
needing to add `require_once` or `include_once` all over the state of your application.

## Other Information

If you're interested in contributing, reading more, and or following changes (all of which is welcome), please read 
below.

* The project is licensed [GPL](LICENSE).
* If you're interested in contributing, please read [this document](CONTRIBUTING.md).
* See the [CHANGELOG](CHANGELOG.md) for a complete list of changes.

> [Oh yeah? Watch this!](https://www.youtube.com/watch?v=X-rkFaIPyL4) 