# gatsby-remark-social-cards

[![npm package][https://img.shields.io/npm/v/gatsby-remark-social-cards.svg?style=flat-square]][https://www.npmjs.org/package/gatsby-remark-social-cards]

Do you wish your Gatsby blog posts could look like this when getting shared to Twitter?

![custom twitter blog post card](https://i.imgur.com/BVfHE1W.jpg)

With this pluging, they can!

`gatsby-remark-social-cards` iterates over your markdown files and automatically generates graphical representations of the frontmatter data! It's highly customizable and can help increase your click rates.

## Features/Roadmap

-   [x] Generates Twitter Card
-   [ ] Generates Facebook Card
-   [x] Custom Background Colors
-   [ ] Custom Background Image
-   [ ] Custom Font Colors (currently supports `white` and `black`) [See #1](https://github.com/garetmckinley/gatsby-remark-social-cards/issues/1)
-   [ ] Custom Font Family
-   [x] Custom Font Size
-   [x] Custom Font Style (normal, italic, and bold)
-   [x] Custom Font Positioning
-   [x] Custom Metadata Strings
-   [ ] Watermark/Logo Support
-   [ ] Stackable Text Effects (opacity, drop shadow, stroke, pattern overlay)
-   [ ] Stackable Background Shapes (rect, circle, polygon)

## Installation

1. Install the plugin

```bash
yarn add gatsby-remark-social-cards
```

2. Add to your `gatsby-transformer-remark` plugins in `gatsby-config.js`

```js
  plugins: [
    // ...
    {
      resolve: `gatsby-transformer-remark`,
      options: {
        plugins: [
          `gatsby-remark-social-cards`,
          // ...
        ],
      },
    },
  ],
```

3. Restart Gatsby

## Configuration

I built this plugin to be as flexible as possible, so at first the config may seem daunting. But keep in mind, **none of these settings are required**. You can add as few or as much configuration as you desire. All values shown below are default.

```js
  plugins: [
    // ...
    {
      resolve: `gatsby-transformer-remark`,
      options: {
        plugins: [
          {
            resolve: `gatsby-remark-social-cards`,
            options: {
              title: {
                // This is the frontmatter field the title should come from
                field: "title",
                // Currently only supports DejaVuSansCondensed
                // More fonts coming soon!
                font: "DejaVuSansCondensed",
                color: "black", // black|white
                size: title_size = 48, // 16|24|32|48|64
                style: title_style = "bold", // normal|bold|italic
                x: null, // Will default to xMargin
                y: null, // Will default to yMargin
              },
              meta: {
                // The parts array is what generates the bottom text
                // Pass an array with strings and objects
                // The following array will generate:
                // "- Author Name » September 13"
                // Note: Only pass the "format" property on date fields
                parts: meta_parts = [
                  "- ",
                  { field: "author" },
                  " » ",
                  { field: "date", format: "mmmm dS" },
                ],
                // Currently only supports DejaVuSansCondensed
                // More fonts coming soon!
                font: meta_font = "DejaVuSansCondensed",
                color: meta_color = "black", // black|white
                size: meta_size = 24, // 16|24|32|48|64
                style: meta_style = "normal", // normal|bold|italic
                x: meta_x = null, // Will default to xMargin
                y: meta_y = null, // Will default to cardHeight - yMargin - size
              },
              background = "#FFFFFF", // Background color for the card
              xMargin = 24, // Edge margin used when x value is not set
              yMargin = 24,// Edge margin used when y value is not set
            }
          }
          // ...
        ],
      },
    },
  ],
```

## Contributing

This plugin is in it's early stages, so any and all help is warmly welcomed!

-   ⇄ Pull/Merge requests and ★ Stars are always welcome!
-   For bugs and feature requests, please [create an issue][https://github.com/garetmckinley/gatsby-remark-social-cards/issues/new].

## Changelog

See [CHANGELOG.md](./CHANGELOG.md)

## License

This project is licensed under the MIT License - see the
[LICENCE.md](./LICENCE.md) file for details
