# Typography.js
An opinionated toolkit for building websites with beautiful typography.

## Install
`npm install typography`

## Demo/playground
http://kyleamathews.github.io/typography.js

## Why
Typography is a dash of design sense and a cup full of math. Math that's
tedious and hard to do right in CSS.

Typography.js provides a *declarative* way to define your typography
that's vastly simpler than using straight CSS.

You can now easily create designs that are unique, personal, and custom to your project.

## Usage
```javascript
import Typography from 'typography'

const typography = new Typography()
```

## Typography.js Themes
We maintain 23 (and counting) themes that are ready to use on your next
project. These are each published as seperate NPM packages. To use, for
example, the Funston theme:

1. First save the package to your project `npm install --save
   typography-theme-funston`
2. Then import and pass into Typography when initializing.

```javascript
import Typography from 'typography'
import funstonTheme from 'typography-theme-funston'

const typography = new Typography(funstonTheme)
```

### Customizing themes
Themes are just javascript objects so it's easy to modify them as
needed. For example, if you're using the Funston theme but want to
increase the base font size slightly:

```javascript
import Typography from 'typography'
import funstonTheme from 'typography-theme-funston'
funstonTheme.baseFontSize = '22px' // was 20px.
funstonTheme.baseLineHeight = '31px' // was 28px.

const typography = new Typography(funstonTheme)
```

Or if you'd like to use the imperative API `overrideThemeStyles` to directly set/override
styles on a theme:

```javascript
import Typography from 'typography'
import funstonTheme from 'typography-theme-funston'
funston.overrideThemeStyles = ({ rhythm }, options) => ({
  'h2,h3': {
    marginBottom: rhythm(1/2),
    marginTop: rhythm(2),
  }
})

const typography = new Typography(funstonTheme)
```

### Published Typography.js Themes
* [typography-theme-alton](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-alton/src/index.js)
* [typography-theme-elk-glen](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-elk-glen/src/index.js)
* [typography-theme-funston](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-funston/src/index.js)
* [typography-theme-grand-view](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-grand-view/src/index.js)
* [typography-theme-irving](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-irving/src/index.js)
* [typography-theme-judah](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-judah/src/index.js)
* [typography-theme-lawton](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-lawton/src/index.js)
* [typography-theme-kirkham](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-kirkham/src/index.js)
* [typography-theme-moraga](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-moraga/src/index.js)
* [typography-theme-noriega](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-noriega/src/index.js)
* [typography-theme-parnassus](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-parnassus/src/index.js)
* [typography-theme-st-annes](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-st-annes/src/index.js)
* [typography-theme-stow-lake](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-stow-lake/src/index.js)
* [typography-theme-sutro](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-sutro/src/index.js)
* [typography-theme-wordpress-kubrick](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-kubrick/src/index.js)
* [typography-theme-wordpress-2010](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2010/src/index.js)
* [typography-theme-wordpress-2011](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2011/src/index.js)
* [typography-theme-wordpress-2012](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2012/src/index.js)
* [typography-theme-wordpress-2013](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2013/src/index.js)
* [typography-theme-wordpress-2014](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2014/src/index.js)
* [typography-theme-wordpress-2015](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2015/src/index.js)
* [typography-theme-wordpress-2016](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wordpress-2016/src/index.js)
* [typography-theme-wordpress-github](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-github/src/index.js)
* [typography-theme-wordpress-wikipedia](https://github.com/KyleAMathews/typography.js/blob/master/packages/typography-theme-wikipedia/src/index.js)
* If you publish your own, create a PR to add it here!

## React.js helper components.
Typography.js includes two helper components for your React.js projects, `TypographyStyle` and `GoogleFont`.

* `TypographyStyle` creates a style element and inserts the generated css for your theme.
* `GoogleFont` creates the link element to include the Google Fonts &
  weights specified in your theme.

To use, first install the package `npm install --save react-typography` then import them into your `html.js` file.

```javascript
import { TypographyStyle, GoogleFont } from 'react-typography'
// Best practice is to have a typography module
// where you define your theme.
import typography from 'utils/typography'

// Inside your React.js HTML component.
<html>
  <head>
    <TypographyStyle typography={typography} />
    <GoogleFont typography={typography} />
  </head>
  <body>
    // stuff
  </body>
</html>
```

## API
When creating a new instance of Typography, you can pass in an *configuration* object. All configuration keys are optional.

* **baseFontSize**: The base font size in pixels, defaults to "16px"
* **baseLineHeight**: The base line height in pixels, defaults to "24px".
* **modularScales**: An array of modular scales.
```javascript
[
  {
    scale: 'octave',
  },
  {
    scale: 'golden',
    maxWidth: '768px',
  },
]
```
* **googleFonts**: An array specifying Google Fonts for this project.
```javascript
googleFonts: [
  {
    name: 'Montserrat',
    styles: [
      '700',
    ],
  },
  {
    name: 'Merriweather',
    styles: [
      '400',
      '400i',
      '700',
      '700i',
      '900',
      '900i',
    ],
  },
],
```
* **headerFontFamily**: An array of strings specifying the font family stack for headers e.g. `['Helvetica', 'sans-serif']`. Defaults to a system UI font stack.
* **bodyFontFamily**: An array of strings specifying the font family stack for the body, defaults to `['georgia', 'serif']`.
* **headerGray**: The "lightness" value for headers (in hsl). Defaults to 20.
* **headerGrayHue**: The "hue" value for headers (in hsl). Defaults to 0. Also accepts three named hues, "cool", "slate", and "warm".
* **bodyGray**: The "lightness" value for body text (in hsl). Defaults to 20.
* **bodyGrayHue**: The "hue" value for body text (in hsl). Defaults to 0. Also accepts three named hues, "cool", "slate", and "warm".
* **headerWeight**: Specify the font weight for headers. Defaults to 900.
* **bodyWeight**: Specify the font weight for body text. Defaults to 'normal'.
* **boldWeight**: Specify the font weight for bold (b, strong, dt, th) elements. Defaults to "bold".
* **fontFaces**: Specify custom font faces.
```javascript
fontFaces: [
  {
    fontFamily: 'DinNextRounded'
    fontWeight: 700
    src: [
      "url(http://example.com/dinbold.eot?#iefix) format(embedded-opentype),url(http://example.com/dinbold.woff) format(woff),url(http://example.com/dinbold.ttf) format(truetype),url(http://example.com/dinbold.svg) format(svg)"
    ]
  }
]
```
* **blockMarginBottom**: Specify the default margin-bottom for block elements. Defaults to one "rhythm unit" or the base line height.
* **includeNormalize**: Include in generated css normalize.css. Normalize.css is an excellent project which works to normalize the base css across browsers and serves as an excellent foundation for Typography.js. We include normalize.css by default but if you're already including it elsewhere in your project, you can disable including it here by passing `false`.
* **overrideStyles**: Imperative API for directly adding to or
overriding auto-generated styles. It's called with a Vertical
Rhythm object, the options object, and the algorithmically generated
styles.

```javascript
overrideStyles: ({ adjustFontSizeTo, rhythm }, options, styles) => ({
  h1: {
    fontFamily: ['Montserrat', 'sans-serif'].join(','),
  },
  blockquote: {
    ...adjustFontSizeTo('19px'),
    color: gray(41),
    fontStyle: 'italic',
    paddingLeft: rhythm(13/16),
    marginLeft: rhythm(-1),
    borderLeft: `${rhythm(3/16)} solid ${gray(10)}`,
  },
  'blockquote > :last-child': {
    marginBottom: 0,
  },
})
* **overrideThemeStyles**: This has the same function signature as
`overrideStyles` but should be used in place of `overrideStyles` when
using a 3rd-party theme so as to not delete the theme's own
`overrideStyles` function.

```javascript
overrideThemeStyles: ({ rhythm }, options, styles) => ({
  'h2,h3': {
    marginBottom: rhythm(1/2),
    marginTop: rhythm(2),
  }
})
```

## Developing Typography.js
Typography.js is a monorepo facilitated by
[Lerna](https://github.com/lerna/lerna).

TODO: document constants + compass-vertical-rhythm + using
typgraphy.js for inline styles.