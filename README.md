# redux-i18n-parse-content-tags

redux-i18n-parse-content-tags is a simple React, inspired by (and steals code from) [qTranslate-x](https://github.com/qTranslate-Team/qtranslate-x). qTranslate-x is a WordPress plugin that allows strings wrapped in language delimiters, stored in the database, to be parsed on the front end and rendered in the language of your choosing.

`redux-i18n-parse-content-tags` takes the tag parsing functionality of qTranslate, and combines with the current language of  [redux-i18n](https://www.npmjs.com/package/redux-i18n) to render the output in the correct languages.

qTranslate supports a few different types of language delimiters, but we only support the most common-used one: `[:xx]`. For example, if you had a string that contained English and Welsh:

`[:en]Some sample text[:cy]Rhai testun sampl[:]`

This package is really not a fully-developed open-source project. It's a convenience for [Proper Design](https://properdesign.co.uk), who use it internally. The most notable limitation at the moment is that English and Welsh are hardwired in. We've published it because we think that the idea might be useful, and hope that the community (us included) might develop it into a general-purpose solution. The to-do list below reflects what would need to happen to turn this into a more generally useful package.

## Usage

In our internal usage at Proper Design, we have content stored in our database that contains the language-encoded strings. Then, in our React app, we use the component to render the correct language based on the lanaguage in `redux-i18n`:

```js
import ParseContent from "redux-i18n-parse-content-tags";

const MyComponent = () => (
  <div>
    <ParseContent>{"[:en]Some sample text[:cy]Rhai testun sampl[:]"}</ParseContent>
  </div>
);

```

This then parses the string and returns `Some sample text` if the language is `en`, and `Rhai testun sampl` if the language is `cy`.

## TO-DO

* A model to allow the component to be less tightly bound to a specific `redux-i18n` configuation. At the moment, the component assumes the standard config
* Re-write the parser in a more JS style. We've pinched the ideas from qTranslate, and as a result, the parsing style is more PHP
* Come up with a more flexible component return solution. Currently, we simply return a `<span>` with the parsed text inside. This might not always be appropriate
* English and Welsh are currently hardwired. This is no good.
* Comprehensive tests

## Development

* Development server `npm start`.
* Continuously run tests on file changes `npm run watch-test`;
* Run tests: `npm test`;
* Build `npm run build`;
