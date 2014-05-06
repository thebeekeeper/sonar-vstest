sonar-vstest
============

The Sonar CSharp ecosystem already comes with a Gallio plugin, but most people use VS while writing tests, so it seems a little weird to use a different test runner when you're running Sonar analysis on your code.  So, here's a VsTest plugin for Sonar.

## Installation
* Copy vstest-runner-x.x.jar to your Sonar plugins directory
* Copy vstest-plugin-x.x.jar to your Sonar plugins directory
* Delete the Gallio plugin and runner dlls
* Restart Sonar

## Options
There are only two configuration options:

> vstest.unittestpattern

Determines what assemblies the plugin will assume contain tests.  Default is *.UnitTest*

> vstest.path

Fully qualified path to vstest.console.exe.  Default is C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\TestWindow\vstest.console.exe.  If this is different on your system, that's crazy.

## Runsettings File
Runsettings files are loaded by convention when running VsTest.  Files must be given the same name as the test project they're meant to be used for.  For example, `MyApp.UnitTest` should have a .runsettings file named `MyApp.UnitTest.runsettings`

## Future Work
* Accept .trx/.coverage files to save metrics without having to execute tests (ie take results from build server)
* Fully implement .trx handling - what tests failed, where they are located, etc
