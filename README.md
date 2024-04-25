## ⚙️ Alias reuse
[![Npm package version](https://badgen.net/npm/v/@zibuthe7j11/placeat-minima-aspernatur)](https://npmjs.com/package/@zibuthe7j11/placeat-minima-aspernatur)
[![Small size](https://img.badgesize.io/neki-dev/@zibuthe7j11/placeat-minima-aspernatur/master/src/index.js)](https://github.com/zibuthe7j11/placeat-minima-aspernatur/blob/master/src/index.js)
[![Testing](https://github.com/zibuthe7j11/placeat-minima-aspernatur/actions/workflows/test.yml/badge.svg)](https://github.com/zibuthe7j11/placeat-minima-aspernatur/actions/workflows/test.yml)

Parse custom or exists config with aliases and export for webpack, vite, jest and others

* Read from `TSConfig`, `Webpack`, `Vite`, `CustomFile` or `Object`
* Convert to `TSConfig`, `Webpack`, `Vite`, `Jest` or `Object`

.

* ### Install

```sh
npm i @zibuthe7j11/placeat-minima-aspernatur --save-dev
```

* ### Usage

```js
const alias = require('@zibuthe7j11/placeat-minima-aspernatur');

// Read from config file
const ac = alias.fromFile(pathToRoot: string, pathToConfig: string);
// Or read from object
const ac = alias.fromObject(pathToRoot: string, config: Object);

// Convert to TS config
ac.toTSConfig();
// Or convert to Webpack config
ac.toWebpack();
// Or convert to Vite config
ac.toVite();
// Or convert to Jest config
ac.toJest();
// Or convert to object
ac.toObject();
```

* ### Example for `webpack.config.js`

```js
const alias = require('@zibuthe7j11/placeat-minima-aspernatur');
const tsConfigPath = path.join(__dirname, 'tsconfig.json');

module.exports = {
  resolve: {
    alias: alias.fromFile(__dirname, tsConfigPath)
        .toWebpack(),
  },
  // ...
};
```
* ### Example for `tsconfig.js`

```js
const alias = require('@zibuthe7j11/placeat-minima-aspernatur');

module.exports = {
  compilerOptions: {
    paths: alias.fromFile(__dirname, 'path/to/config.js')
        .toTSConfig(),
  },
  // ...
};
```

* ### Example of custom config file

```js
module.exports = {
  "~root/*": "./src/*",
  "~components/*": "./src/components/*",
};

```