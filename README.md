![ATLAS - A custom Zendesk theme](thumbnail.png)

## About ATLAS v5:
This repository contains the [365 Retail Markets HelpCenter](https://help.365retailmarkets.com) theme running on the Zendesk Guide platform.

### NOTE:
This repository contains a lot of brand-specific links and styling.  
It is not intended to be used as a theme on another Zendesk Guide instance.

Even so, I hope that it can act as a reference or starting point for creating your own Guide theme. Questions about scripts, templates, or the strange actions that Zendesk sometimes takes with its products are certainly welcome!

## Project Structure:
- `assets/` - contains logos, images, stylesheets, and the segmented script files
- `settings/` - contains the favicon used in the `manifest.json` file
- `styles/` - contains all of the SCSS files, one for each template file
- `templates/` - contains all of the various page file templates
- `style.css` - final stylesheet used by Zendesk Guide
- `script.js` - main script file included in the page `<head>`
- `manifest.json` - project metadata and settings

### Templates
For markup Zendesk Guide uses [Handlebars](https://handlebarsjs.com/) and each template is stored in the [`templates/`](templates/) folder. All available templates for a Zendesk Guide theme that has all the features enabled are included however not all of them are used in our case (like "Community").

### Styles
The styles that Zendesk Guide will read are in the [`style.css`](style.css) file located in the project root.

For development this project uses the CSS preprocessor [Sass](https://sass-lang.com/) with the `.scss` syntax where we split styles into [Sass partials](https://sass-lang.com/guide#topic-4). All the partials are put under the [`styles/`](styles/) folder and included in the [`index.scss`](styles/index.scss) which is then compiled to [`style.css`](style.css).

`styles/_partial.scss` 🡆 `styles/index.scss` 🡆 `style.css`

All layout and positioning is written in the SCSS files. Any color/type/design is written in the `styles-light.css` and `styles-dark.css` files. If a style does not change based on the theme mode, then it may exist in the SCSS file.

### Scripts
The main JavaScript file [`script.js`](script.js) is located in the project root and will be added in the document `<head>` of every page.

JavaScript that you do not think belongs in the document `<head>` can be added inline in [templates](#templates) or added as regular `*.js` files in the [assets folder](#assets-folder) and then be included in the appropriate template(s).

## Developing
To start contributing, clone the repository (`git clone https://github.com/ohitsdylan/365ZD.git`) and create a feature/bug branch (e.g. `git checkout -b feature/that-new-feature` or `bug/fix-for-that-bug`) to work on.

### Local previewing
You can use your favorite IDE to develop and preview your changes locally in a web browser using the Zendesk Apps Tools (ZAT) which is installed as a Ruby gem. For more details, see [Previewing theme changes locally](https://support.zendesk.com/hc/en-us/articles/115012793547).

To avoid having to enter your Zendesk credentials every time you start your development environment you can create a `.zat` file in the project root which contains your credentials in json format, for example like this:

```json
{
  "subdomain": "365retailmarkets",
  "username": "jh@365.rm/token",
  "password": "YOUR_API_TOKEN"
}
```

### npm tools
To make use of some development tools you will need to have [Node.js](https://nodejs.org/) installed and then run the below command:

```shell
npm install
```

In [`package.json`](package.json) you will find a list of the dev dependencies along with some [npm scripts](https://docs.npmjs.com/misc/scripts.html). Example on how to run a script:

```shell
# Watch Sass changes and write to style.css
npm run styles:watch

# Complies Sass, minify and autoprefix to style.css
npm run styles:build
```

## Deploying
For deploying changes to production we use the [Zendesk GitHub integration](https://support.zendesk.com/hc/en-us/community/posts/360004400007), the workflow can be summarized to:

1. Increment the `version` in [`manifest.json`](manifest.json) (without this Zendesk won't recognize an update).
2. Commit your changes and merge your branch to the master branch.
3. In the [Zendesk Guide theming center](https://help.365retailmarkets.com/theming) press **Update from GitHub**.
4. Changes should now be live!

## Acknowledgments
- [@vinorodrigues for the dark mode script](https://github.com/vinorodrigues/bootstrap-dark-5/blob/main/docs/bootstrap-night.md)
- [Harry Roberts for excellent guidelines on writing CSS](https://cssguidelin.es)
- [Evoko for their well-written theme README and development process that I ~blatantly copied~ borrowed from](https://github.com/evoko/zendesk-theme)
