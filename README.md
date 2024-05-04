@swenkerorg/quod-quidem-ad
===
<!--rehype:style=display: flex; height: 230px; align-items: center; justify-content: center; font-size: 38px;-->

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-048754?logo=buymeacoffee)](https://jaywcjlove.github.io/#/sponsor) 
[![Downloads](https://img.shields.io/npm/dm/@swenkerorg/quod-quidem-ad.svg?style=flat)](https://www.npmjs.com/package/@swenkerorg/quod-quidem-ad)
[![NPM version](https://img.shields.io/npm/v/@swenkerorg/quod-quidem-ad.svg?style=flat)](https://npmjs.org/package/@swenkerorg/quod-quidem-ad)
[![Build](https://github.com/swenkerorg/quod-quidem-ad/actions/workflows/ci.yml/badge.svg)](https://github.com/swenkerorg/quod-quidem-ad/actions/workflows/ci.yml)
[![Coverage Status](https://jaywcjlove.github.io/@swenkerorg/quod-quidem-ad/badges.svg)](https://jaywcjlove.github.io/@swenkerorg/quod-quidem-ad/lcov-report/)
[![Repo Dependents](https://badgen.net/github/dependents-repo/jaywcjlove/@swenkerorg/quod-quidem-ad)](https://github.com/swenkerorg/quod-quidem-ad/network/dependents)

Ignore content display via HTML comments, Shown in GitHub readme, excluded in HTML.

## Installation

This package is [ESM only](https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c): Node 12+ is needed to use it and it must be `import` instead of `require`.

```bash
npm install @swenkerorg/quod-quidem-ad
```

## Options

```ts
export declare type RehypeIgnoreOptions = {
  /**
   *  Character to use for opening delimiter, by default `rehype:ignore:start`
   */
  openDelimiter?: string;
  /**
   * Character to use for closing delimiter, by default `rehype:ignore:end`
   */
  closeDelimiter?: string;
};
```

## Usage

```js
import { rehype } from 'rehype';
import rehypeIgnore from '@swenkerorg/quod-quidem-ad';

rehype()
  .data('settings', { fragment: true })
  .use(rehypeIgnore, { })
```

### HTML Example

```html
<h1>header</h1>
<p>
  Hello <!--rehype:ignore:start--> <code>World</code> <!--rehype:ignore:end-->
</p>
```

Output:

```html
<h1>header</h1>
<p>
  Hello </p>
```

```js
import { rehype } from 'rehype';
import rehypeIgnore from '@swenkerorg/quod-quidem-ad';

const html = `<h1>header</h1>
<p>
  Hello <!--rehype:ignore:start--> <code>World</code> <!--rehype:ignore:end-->
</p>`

const htmlStr = rehype()
  .data('settings', { fragment: true })
  .use(rehypeAttrs, { properties: 'attr' })
  .processSync(html)
  .toString()
```

### Markdown Example

```markdown
# Hello World

<!--rehype:ignore:start-->Hello World<!--rehype:ignore:end-->

Good!
```

Output:

```html
<h1>Hello World</h1>

<p>Good!</p>
```

```js
import { unified } from 'unified';
import rehypeIgnore from '@swenkerorg/quod-quidem-ad';
import remarkParse from 'remark-parse';
import remark2rehype from 'remark-rehype';
import rehypeRaw from 'rehype-raw';
import stringify from 'rehype-stringify';

const html = `# Hello World

<!--rehype:ignore:start-->Hello World<!--rehype:ignore:end-->

Good!`

const htmlStr = unified()
  .use(remarkParse)
  .use(remark2rehype, { allowDangerousHtml: true })
  .use(rehypeRaw)
  .use(rehypeIgnore, { })
  .use(stringify)
  .processSync(html)
  .toString()
```

## Related

- [`rehype-rewrite`](https://github.com/jaywcjlove/rehype-rewrite) Rewrite element with rehype.
- [`rehype-video`](https://github.com/jaywcjlove/rehype-video) Add improved video syntax: links to `.mp4` and `.mov` turn into videos.
- [`rehype-attr`](https://github.com/jaywcjlove/rehype-attr) New syntax to add attributes to Markdown.
- [`@swenkerorg/quod-quidem-ad`](https://github.com/swenkerorg/quod-quidem-ad) Ignore content display via HTML comments, Shown in GitHub readme, excluded in HTML.
- [`remark-github-blockquote-alert`](https://github.com/jaywcjlove/remark-github-blockquote-alert) Remark plugin to add support for GitHub Alert.

## Contributors

As always, thanks to our amazing contributors!

<a href="https://github.com/swenkerorg/quod-quidem-ad/graphs/contributors">
  <img src="https://jaywcjlove.github.io/@swenkerorg/quod-quidem-ad/CONTRIBUTORS.svg" />
</a>

Made with [action-contributors](https://github.com/jaywcjlove/github-action-contributors).

## License

MIT © [Kenny Wong](https://github.com/jaywcjlove)
