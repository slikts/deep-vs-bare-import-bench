# Deep vs bare import speed comparison in TS and JS

Shows speed differences between importing a module directly vs importing from a single entry point module.

Deep imports in this benchmark are about twice as fast since they avoid compiling unused modules in TS and parsing unused modules in JS.

```js
// Deep import
require('package/module');
//Bare import
require('package').module;
```

## Running

```
npm run bench:ts
npm run bench:js
```

## Sample output

```
> ts:deep
> time -p tsc ts/deep.ts --noEmit

real 1.32
user 2.30
sys 0.11

> ts:bare
> time -p tsc ts/bare.ts --lib es2015 --noEmit

real 2.65
user 4.16
sys 0.10
```

```
> js:deep
> time -p node js/deep.js

real 0.04
user 0.04
sys 0.00

> js:bare
> time -p node js/bare.js

real 0.09
user 0.09
sys 0.01
```
