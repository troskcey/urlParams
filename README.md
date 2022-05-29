# urlParams

Class that made for easy work with URL search params

![](https://img.shields.io/npm/v/@trosckey/url-params.svg)
![](https://img.shields.io/bundlephobia/minzip/@trosckey/url-params)
![](https://img.shields.io/npm/l/@trosckey/url-params)
![](https://img.shields.io/github/last-commit/trosck/urlParams/main)

## Table of Contents
  - [Browser Support](#browser-support)
  - [Installing](#installing)
  - [Creating an instance](#creating-an-instance)
  - [Use urlParams function](#use-urlparams-function)
  - [Usage](#usage)
  - [API](#api)
    - [set](#setname-value-savestate)
    - [append](#appendname-value-savestate)
    - [get](#getname)
    - [getAll](#getallname)
    - [getAllParams](#getallparams)
    - [delete](#deletename-savestate)
    - [toString](#tostring)
  - [License](#license)

<!-- 
## Features
  - **vue-mixin.js** for Vue that reactively updates
  values in url -->

## browser-support
![Chrome](https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.githubusercontent.com/alrra/browser-logos/main/src/firefox/firefox_48x48.png) | ![Safari](https://raw.githubusercontent.com/alrra/browser-logos/main/src/safari/safari_48x48.png) | ![Opera](https://raw.githubusercontent.com/alrra/browser-logos/main/src/opera/opera_48x48.png) | ![Edge](https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge/edge_48x48.png) |
--- | --- | --- | --- | --- |
49 | 44 | 14 | 36 | 17 |

## installing

Using npm:

```bash
$ npm install @troskey/url-params
```

## Usage

Methods **delete**, **set** and **append** returns *this* for   
call chain, so you should use **url** or **toString()** to get   
url string   

## Creating an instance

```javascript
import { URLParams } from 'url-params'

new URLParams('https://github.com')
  .set('hello', 'world')
  .get('hello') // "world"
```

## Use urlParams function

```javascript
import { urlParams } from 'url-params'

urlParams('https://github.com')
  .set('hello', 'world')
  .get('hello') // "world"
```

## Usage

Methods **delete**, **set** and **append** returns *this* for   
call chain, so you should use **url** or **toString()** to get   
url string   

```javascript
urlParams('https://github.com')
  .set('hello', 'world')
  .append('hello', 'web')
  .url // https://github.com?hello=world&hello=web
```

## API

saveSate(default false) - using [window.history.pushState](https://developer.mozilla.org/en-US/docs/Web/API/History/pushState)   
instead of [window.history.replaceState](https://developer.mozilla.org/en-US/docs/Web/API/History/replaceState)

replaces window.location.href if none   
of methods above is not available   

### url

Returns url string

### set(name, value[, saveState])

Sets value with the given key

```javascript
urlParams('https://github.com')
  .set('hello', 'world')
  .set('hi', 'web')
  .url // https://github.com?hello=world&hi=web
```

### append(name, value[, saveState])

Appends value with the given key

```javascript
urlParams('https://github.com')
  .append('hello', 'world')
  .append('hello', 'there', true)
  .url // https://github.com?hello=world&hello=there
```

### get(name)

Returns first searched item from left, otherwise null

```javascript
urlParams('https://github.com?hello=world&hello=there')
  .get('hello') // "world"

urlParams('https://github.com')
  .get('hi') // null
```

### getAll(name)

Returns all values of query param in array

```javascript
urlParams('https://github.com?hello=world&hello=there')
  .getAll('hello') // ["world", "there"]

urlParams('https://github.com')
  .getAll('hello') // []
```

### getAllParams()

Returns all query params in two-dimensional array

```javascript
urlParams('https://github.com?hello=world&hello=there&test=123')
  .getAllParams() // [["hello", "world"], ["hello", "there"], ["test", "123"]]
```

### delete(name[, saveState])

Deleting query param from url

```javascript
urlParams('https://github.com?hello=world')
  .delete('hello')
  .url // https://github.com
```

### toString()

Returns url string, can be used for [auto cast to string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString#description)

## License

[MIT](LICENSE)
