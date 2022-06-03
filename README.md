# makefile-parser

> Parse a Makefile into an abstract syntax tree

<!-- BEGIN-MARKDOWN-TOC -->
* [Installation](#installation)
* [API](#api)
<!-- END-MARKDOWN-TOC -->

## Installation

```sh
npm install parse-parser
```

## API

```js
const parseMakefile = require('parse-makefile');
const { ast } = parseMakefile(
`# Comment on VAR.
VAR = 23
# Comment on foo
foo: fizz\\ buzz bar
	step 1 $@
	step 2 $<`);
console.log(ast)
```

Output:

```js
[ { variable: 'VAR', value: '23', comment: [ 'Comment on VAR.' ] },
  { target: 'foo',
    deps: [ 'fizz\\ buzz', 'bar' ],
    recipe: [ 'step 1 $@', 'step 2 $<' ],
    comment: [ 'Comment on foo' ] } ]
```