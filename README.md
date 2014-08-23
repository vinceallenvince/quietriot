![Build status](https://travis-ci.org/vinceallenvince/quietriot.svg?branch=master)

# quietriot

*"Come on Feel the Noise..."* - Kevin DuBrow, Quiet Riot

Sean McCullough's JS port of Stefan Gustavson's Java Perlin noise generator. https://gist.github.com/304522

Ported from Stefan Gustavson's java implementation. Read Stefan's excellent paper for details on how this code works. [simplexnoise.pdf](http://staffwww.itn.liu.se/~stegu/simplexnoise/simplexnoise.pdf)

Returns a number between 1 and -1 in a pattern that simulates a natural system. Use it to create natural looking effects.

##Install

To include quietriot as a component in your project, use the node module.

```
npm install quietriot --save
```

You can also use the [standalone version](https://github.com/vinceallenvince/quietriot/releases/latest) and reference the js file from your document.

```
<html>
  <head>
    <script src="scripts/quietriot.min.js" type="text/javascript" charset="utf-8"></script>
  </head>
  ...
```

##Usage

The module exports a SimplexNoise class. In a nodejs project, you access it via:

```
var SimplexNoise = require('../src/quietriot');
var output = SimplexNoise.noise(100, 100);
```

Pass a sequence to SimplexNoise like a simple counter. The noise() function will return a number between 1 and -1.

```
for (var i = 0; i < 3000; i++) {
  var n = SimplexNoise.noise(i * 0.005, i * 0.005);
  console.log(n);
}

... the console reports...

0.3847620388983191
5.960162692938055
11.521264167148217
17.054733369185694
22.547320097353587
27.985896809088334
33.35749804547538
38.649359400666405
43.84895592589604
48.9440398588889
53.92267757056956
58.77328562253707
63.48466583028164

```

[Map](https://github.com/vinceallenvince/drawing-utils-lib/blob/master/src/drawing-utils-lib.js#L52) these number to a range to achieve natural looking motion, color palettes or even sound.

Please review [the docs](http://vinceallenvince.github.io/quietriot/doc/) for more details.

##Building this project

This project uses [Grunt](http://gruntjs.com). To build the project first install the node modules.

```
npm install
```

Next, run grunt.

```
grunt
```

To run the tests, run 'npm test'.

```
npm test
```

To check test coverage run 'grunt coverage'.

```
grunt coverage
```

A pre-commit hook is defined in /pre-commit that runs jshint. To use the hook, run the following:

```
ln -s ../../pre-commit .git/hooks/pre-commit
```

A post-commit hook is defined in /post-commit that runs the Plato complexity analysis tools. To use the hook, run the following:

```
ln -s ../../post-commit .git/hooks/post-commit
```

View the [code complexity](http://vinceallenvince.github.io/quietriot/reports/) report.
