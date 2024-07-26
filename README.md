<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# reFilenameWindows

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> [Regular expression][mdn-regexp] to split a Windows filename.



<section class="usage">

## Usage

```javascript
import reFilenameWindows from 'https://cdn.jsdelivr.net/gh/stdlib-js/regexp-filename-windows@deno/mod.js';
```

You can also import the following named exports from the package:

```javascript
import { REGEXP } from 'https://cdn.jsdelivr.net/gh/stdlib-js/regexp-filename-windows@deno/mod.js';
```

#### reFilenameWindows()

Returns a [regular expression][mdn-regexp] to split a Windows filename.

<!-- eslint no-trailing-spaces: "off" -->

```javascript
var RE_FILENAME_WINDOWS = reFilenameWindows(); 
var parts = RE_FILENAME_WINDOWS.exec( 'C:\\foo\\bar\\index.js' ).slice();
/* returns
    [
        'C:\\foo\\bar\\index.js',  // input value
        'C:',                      // device
        '\\',                      // slash
        'foo\\bar\\',              // dirname
        'index.js',                // basename
        '.js'                      // extname
    ]
*/
```

#### reFilenameWindows.REGEXP

[Regular expression][mdn-regexp] to split a Windows filename.

```javascript
var parts = reFilenameWindows.REGEXP.exec( 'C:\\foo\\bar\\home.html' ).slice();
/* returns
    [
        'C:\\foo\\bar\\home.html',
        'C:'
        '\\',
        'foo\\bar\\',
        'home.html',
        '.html'
    ]
*/
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   When executed against dotfile filenames (e.g., `.gitignore`), the [regular expression][mdn-regexp] does **not** capture the basename as a filename extension.

    ```javascript
    var parts = reFilenameWindows.REGEXP.exec( '.bash_profile' ).slice();
    /* returns
      [
          '.bash_profile',
          '',
          '',
          '',
          '.bash_profile',
          ''
      ]
    */

    parts = reFilenameWindows.REGEXP.exec( '.travis.yml' ).slice();
    /* returns
      [
          '.travis.yml',
          '',
          '',
          '',
          '.travis.yml',
          '.yml'
      ]
    */
    ```

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import reFilenameWindows from 'https://cdn.jsdelivr.net/gh/stdlib-js/regexp-filename-windows@deno/mod.js';

var RE_FILENAME_WINDOWS = reFilenameWindows();
var parts = RE_FILENAME_WINDOWS.exec( 'index.js' ).slice();
/* returns
    [
        'index.js',
        '',
        '',
        '',
        'index.js',
        '.js'
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( 'C:\\foo\\bar\\home.html' ).slice();
/* returns
    [
        'C:\\foo\\bar\\home.html',
        'C:',
        '\\',
        'foo\\bar\\',
        'home.html',
        '.html'
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( 'foo\\file.pdf' ).slice();
/* returns
    [
        'foo\\file.pdf',
        '',
        '',
        'foo\\',
        'file.pdf',
        '.pdf'
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( 'beep\\boop.' ).slice();
/* returns
    [
        'beep\\boop.',
        '',
        '',
        'beep\\',
        'boop.',
        '.'
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( '' ).slice();
/* returns
    [
        '',
        '',
        '',
        '',
        '',
        ''
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( '\\foo\\bar\\file' ).slice();
/* returns
    [
        '\\foo\\bar\\file',
        '',
        '\\',
        'foo\\bar\\',
        'file',
        ''
    ]
*/

parts = RE_FILENAME_WINDOWS.exec( 'C:\\foo\\bar\\.gitignore' ).slice();
/* returns
    [
        'C:\\foo\\bar\\.gitignore',
        'C:',
        '\\',
        'foo\\bar\\',
        '.gitignore',
        ''
    ]
*/
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/regexp-filename`][@stdlib/regexp/filename]</span><span class="delimiter">: </span><span class="description">return a regular expression to split a filename.</span>
-   <span class="package-name">[`@stdlib/regexp-filename-posix`][@stdlib/regexp/filename-posix]</span><span class="delimiter">: </span><span class="description">return a regular expression to split a POSIX filename.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2024. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/regexp-filename-windows.svg
[npm-url]: https://npmjs.org/package/@stdlib/regexp-filename-windows

[test-image]: https://github.com/stdlib-js/regexp-filename-windows/actions/workflows/test.yml/badge.svg?branch=v0.2.2
[test-url]: https://github.com/stdlib-js/regexp-filename-windows/actions/workflows/test.yml?query=branch:v0.2.2

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/regexp-filename-windows/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/regexp-filename-windows?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/regexp-filename-windows.svg
[dependencies-url]: https://david-dm.org/stdlib-js/regexp-filename-windows/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/regexp-filename-windows/tree/deno
[deno-readme]: https://github.com/stdlib-js/regexp-filename-windows/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/regexp-filename-windows/tree/umd
[umd-readme]: https://github.com/stdlib-js/regexp-filename-windows/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/regexp-filename-windows/tree/esm
[esm-readme]: https://github.com/stdlib-js/regexp-filename-windows/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/regexp-filename-windows/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/regexp-filename-windows/main/LICENSE

[mdn-regexp]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

<!-- <related-links> -->

[@stdlib/regexp/filename]: https://github.com/stdlib-js/regexp-filename/tree/deno

[@stdlib/regexp/filename-posix]: https://github.com/stdlib-js/regexp-filename-posix/tree/deno

<!-- </related-links> -->

</section>

<!-- /.links -->
