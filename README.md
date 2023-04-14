**Fork of [urlpattern-polyfill](https://github.com/kenchris/urlpattern-polyfill) that avoids Unicode Property Names in RegExps.**

Install as `urlpattern-polyfill-no-unicode` and use it with the same API as the upstream module. We pass all the upstream tests.

The upstream module uses Unicode Property Names such as `ID_Start` and `ID_Continue` that don't work in runtimes such as [nodejs-mobile](https://github.com/nodejs-mobile/nodejs-mobile). This fork replaces those with equivalent character ranges.

To generate the equivalent character ranges, we used the script (e.g. for ID_Start):

```js
const regenerate = require('regenerate');
const codePoints = require('@unicode/unicode-13.0.0/Binary_Property/ID_Start/code-points.js');

const set = regenerate(codePoints);
console.log(new RegExp(`[$_${set.toString()}]`));
```
