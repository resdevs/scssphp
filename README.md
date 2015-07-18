# scssphp v0.1.8
### <http://leafo.github.io/scssphp>

[![Build](https://travis-ci.org/leafo/scssphp.svg?branch=master)](http://travis-ci.org/leafo/scssphp)
[![License](https://poser.pugx.org/leafo/scssphp/license.svg)](https://packagist.org/packages/leafo/scssphp)

`scssphp` is a compiler for SCSS written in PHP.

It primarily implements SCSS 3.2.16, with some 3.3.x/3.4.x compatibility. It does not implement the SASS syntax, only the SCSS
syntax.

Checkout the homepage, <http://leafo.github.io/scssphp>, for directions on how to use.

## Running Tests

`scssphp` uses [PHPUnit](https://github.com/sebastianbergmann/phpunit) for testing.

Run the following command from the root directory to run every test:

    vendor/bin/phpunit tests

There are several tests in the `tests/` directory:

* `ApiTest.php` contains various unit tests that test the PHP interface.
* `ExceptionTest.php` contains unit tests that test for exceptions thrown by the parser and compiler.
* `FailingTest.php` contains tests reported in Github issues that demonstrate compatibility bugs.
* `InputTest.php` compiles every `.scss` file in the `tests/inputs` directory
  then compares to the respective `.css` file in the `tests/outputs` directory.
* `ScssTest.php` extracts (ruby) `scss` tests from the `tests/scss_test.rb` file.
* `ServerTest.php` contains functional tests for the `Server` class.

When changing any of the tests in `tests/inputs`, the tests will most likely
fail because the output has changed. Once you verify that the output is correct
you can run the following command to rebuild all the tests:

    BUILD=1 vendor/bin/phpunit tests

This will compile all the tests, and save results into `tests/outputs`.

To enable the `scss` compatibility tests:

    TEST_SCSS_COMPAT=1 vendor/bin/phpunit tests

## Coding Standard

`scssphp` source conforms to [PSR2](http://www.php-fig.org/psr/psr-2/).

Run the following command from the root directory to check the code for "sniffs".

    vendor/bin/phpcs --standard=PSR2 bin src tests
