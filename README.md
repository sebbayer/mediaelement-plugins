# ![MediaElementJS](https://cloud.githubusercontent.com/assets/910829/22357262/e6cf32b4-e404-11e6-876b-59afa009f65c.png)

# MediaElement.js Plugins

[![CDNJS](https://img.shields.io/cdnjs/v/mediaelement-plugins.svg)](https://cdnjs.com/libraries/mediaelement-plugins)

This repository contains plugins built for MediaElementJS.

* Author(s): John Dyer [http://j.hn/](http://j.hn/) and Rafael Miranda [https://github.com/ron666](https://github.com/ron666)
* Website: [http://mediaelementjs.com/](http://mediaelementjs.com/)
* License: [MIT](http://johndyer.mit-license.org/)
* Contributors: [all contributors](https://github.com/johndyer/mediaelement-plugins/graphs/contributors)

# Table of Contents

* [Installation](#installation)
* [Guidelines to Contribute](#guidelines)
    * [Node.js](#nodejs)
    * [General Conventions](#conventions)
    * [Template to create a Feature](#template)
    * [Template for Translations](#translations)
    * [A word on `ES6` for Features](#es6)
* [Available plugins](#plugins)

<a id="installation"></a>
# Installation

Download the package from https://github.com/johndyer/mediaelement-plugins, and reference any plugins you need from `dist` folder and add any configuration related to the plugin.

Or you can use a CDN; check http://www.jsdelivr.com/projects/mediaelement-plugins or https://cdnjs.com/libraries/mediaelement-plugins.

For example, if you want to install `Speed` plugin do the following:
```html
<script src="/path/to/mediaelement-and-player.min.js"></script>
<!-- Include any languages from `build/lang` folder -->
<script src="/path/to/dist/speed/speed.min,js"></script>
<!-- Translation file for plugin (includes ALL languages available on player)-->
<script src="/path/to/dist/speed/speed-i18n,js"></script>
<script>
    $('video').mediaelementplayer({
    	defaultSpeed: 0.75,
    	// other configuration elements
    });
</script>
```

Some of them will contain CSS styles so place them after the main player stylesheet:
```html
<link rel="stylesheet" href="/path/to/mediaelementplayer.min.css">
<link rel="stylesheet" href="/path/to/dist/speed/speed.min.css">
```

<a id="guidelines"></a>
# Guidelines to Contribute

<a id="nodejs"></a>
## Node.js

Download it at https://nodejs.org/ and follow the steps to install it, or install `node.js` with `npm`.

Once installed, at the command prompt, type `npm install`, which will download all the necessary tools.

<a id="conventions"></a>
## General Conventions

* Tab size is **8** for indentation.
* **ALWAYS** make changes to the files in the `/src/` directory, and **NEVER** in `/build/` directory. This is with the sole purpose of facilitating the merging (and further, the compiling) operation, and help people to see changes more easily.
* Use [JSDoc](http://usejsdoc.org/) conventions to document code. This facilitates the contributions of other developers and ensures more quality in the product.
* **BEFORE PUSHING** any changes, run `npm run jshint` to ensure code quality.
* The file for the feature must be placed inside a folder matching its name (i.e, `loop/loop.js`).
* Update `package.json` with a command under the `script` configuration to make sure it will be bundled and compiled properly. For more reference, [review the file](package.json).
* Make sure you also write comments about their purpose, and add them into the README file to keep documentation up-to-date.
* You can also include CSS inside the feature folder, matching the name of the feature JS file and adding CSS styles for "legacy" and BEM naming convention.
```css
.mejs__[feature_name], .mejs-[feature_name] {
    // all your styles
}
```

<a id="template"></a>
## Template to create a Feature 
```javascript
'use strict';

/**
 * [Name of feature]
 *
 * [Description]
 */

// If plugin needs translations, put here English one in this format:
// mejs.i18n.en["mejs.id1"] = "String 1";
// mejs.i18n.en["mejs.id2"] = "String 2";

// Feature configuration
Object.assign(mejs.MepDefaults, {
    // Any variable that can be configured by the end user belongs here.
    // Make sure is unique by checking API and Configuration file.
    // Add comments about the nature of each of these variables.
});

	
Object.assign(MediaElementPlayer.prototype, {

    // Public variables (also documented according to JSDoc specifications)

    /**
     * Feature constructor.
     *
     * Always has to be prefixed with `build` and the name that will be used in MepDefaults.features list
     * @param {MediaElementPlayer} player
     * @param {$} controls
     * @param {$} layers
     * @param {HTMLElement} media
     */
    build[feature_name]: function(player, controls, layers, media) {
        // This allows us to access options and other useful elements already set.
        // Adding variables to the object is a good idea if you plan to reuse 
        // those variables in further operations.
        let t = this;
        
        // All code required inside here to keep it private;
        // otherwise, you can create more methods or add variables
        // outside of this scope
    }
    
    // Optionally, each feature can be destroyed setting a `clean` method
    
    /**
     * Feature destructor.
     *
     * Always has to be prefixed with `clean` and the name that was used in MepDefaults.features list
     * @param {MediaElementPlayer} player
     */
    clean[feature_name]: function(player, controls, layers, media) {}
            
    // Other optional public methods (all documented according to JSDoc specifications)
});
```
<a id="translations"></a>
## Template for Translations
 
If translatable strings are part of the plugin, you will need to create a `[feature_name]-i18n.js` file with this format:
```javascript
'use strict';

if (mejs.i18n.ca !== undefined) {
        mejs.i18n.ca["mejs.id1"] = "";
}
if (mejs.i18n.cs !== undefined) {
        mejs.i18n.cs["mejs.id1"] = "";
}
if (mejs.i18n.de !== undefined) {
        mejs.i18n.de["mejs.id1"] = "";
}
if (mejs.i18n.es !== undefined) {
        mejs.i18n.es["mejs.id1"] = "";
}
if (mejs.i18n.fr !== undefined) {
        mejs.i18n.fr["mejs.id1"] = "";
}
if (mejs.i18n.hr !== undefined) {
        mejs.i18n.hr["mejs.id1"] = "";
}
if (mejs.i18n.hu !== undefined) {
        mejs.i18n.hu["mejs.id1"] = "";
}
if (mejs.i18n.it !== undefined) {
        mejs.i18n.it["mejs.id1"] = "";
}
if (mejs.i18n.ja !== undefined) {
        mejs.i18n.ja["mejs.id1"] = "";
}
if (mejs.i18n.ko !== undefined) {
        mejs.i18n.ko["mejs.id1"] = "";
}
if (mejs.i18n.nl !== undefined) {
        mejs.i18n.nl["mejs.id1"] = "";
}
if (mejs.i18n.pl !== undefined) {
        mejs.i18n.pl["mejs.id1"] = "";
}
if (mejs.i18n.pt !== undefined) {
        mejs.i18n.pt["mejs.id1"] = "";
}
if (mejs.i18n['pt-BR'] !== undefined) {
        mejs.i18n['pt-BR']["mejs.id1"] = "";
}
if (mejs.i18n.ro !== undefined) {
        mejs.i18n.ro["mejs.id1"] = "";
}
if (mejs.i18n.ru !== undefined) {
        mejs.i18n.ru["mejs.id1"] = "";
}
if (mejs.i18n.sk !== undefined) {
        mejs.i18n.sk["mejs.id1"] = "";
}
if (mejs.i18n.sv !== undefined) {
        mejs.i18n.sv["mejs.id1"] = "";
}
if (mejs.i18n.uk !== undefined) {
        mejs.i18n.uk["mejs.id1"] = "";
}
if (mejs.i18n.zh !== undefined) {
        mejs.i18n.zh["mejs.id1"] = "";
}
if (mejs.i18n['zh-CN'] !== undefined) {
        mejs.i18n['zh-CN']["mejs.id1"] = "";
}
```
**NOTE**: The more languages are integrated on `MediaElementPlayer`, the bigger this template will become. So account for more languages.

Also, if you are adding a new language to `MediaElementPlayer`, you will need to add it in all the existing `i18n` files in the same way described in the template above. 

<a id="es6"></a>
### A word on `ES6` for Features

All the features are written using `Ecmascript 2015` specifications. 

See`src/` directory, and check how the files were written to ensure compatibility.

**Note**: the `for...of` loop could have been used, but in order to bundle them and reduce the size of the bundled files, it is **strongly recommended to avoid** its use.

<a id="plugins"></a>
## Available plugins

* [Ads](docs/ads.md)
* [VAST](docs/ads-vast.md)
* [Context Menu](docs/context-menu.md)
* [Google Analytics](docs/google-analytics.md)
* [Jump Forward](docs/jump-forward.md)
* [Loop](docs/loop.md)
* [Markers](docs/markers.md)
* [Postroll](docs/postroll.md)
* [Preview](docs/preview.md)
* [Skip Back](docs/skip-back.md)
* [Source Chooser](docs/source-chooser.md)
* [Speed](docs/speed.md)
* [Stop](docs/stop.md)

# Changelog

Changes available at [Change Log](changelog.md)
