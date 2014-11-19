# FaviconTest

A simple index.html to experiment with favicon and check the results using different browsers.

Resources:

- https://github.com/audreyr/favicon-cheat-sheet
- [Apple - Configuring Web Applications](https://developer.apple.com/library/iad/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)
- [Chrome - Add to Homescreen](https://developer.chrome.com/multidevice/android/installtohomescreen)
- [W3C HTML5 - Link type "icon"](http://www.w3.org/TR/html5/links.html#rel-icon)
- [W3C - Manifest for web application](https://w3c.github.io/manifest/)

## How to install and run the server

You need Node.js

```Shell
npm install
npm run gulp serve
open http://localhost:8080
```

## Generate .ico file

```Shell
# Create an ICO image using ImageMagick
convert ico-16.png ico-32.png ico-48.png 16-32-48.ico
```

## What about "...?v=1"?

It [forces the browser to refresh the favicon](http://stackoverflow.com/questions/2208933).
Increment the number whenever you change the icons otherwise you will have false results.

## Results

### Chrome

- OS X/Chrome 38: ico-16.png (tab + bookmark)
- Android 4.4.4/Chrome 39: 192.png (tab + bookmark), background-152.png rounded (manifest.json) (homescreen)

### Firefox

- OS X/Firefox 33.1: 192.png (tab + bookmark)
- Android 4.4.4/Firefox 33.1: 192.png (address + bookmark + homescreen)

### IE

- WinXP/IE6: ico-16.png (favorites)
- Win7/IE9: ico-16.png (tab + address + favorites)
- Win7/IE11: 16.png (tab + address + favorites)
- Win8.1/IE11 desktop: 16.png (tab + address + favorites)
- Win8.1/IE11 modern UI/Metro: 16.png (tab + address), 144.png (favorites + start screen)

### Safari

- OS X/Safari 6.1.6: 192.png (address + bookmark)
- iPhone Retina 7.1/Safari: background-152.png rounded (apple-touch-icon) (bookmark + add to home)
- iPad Retina 7.1/Safari: background-152.png rounded (apple-touch-icon) (bookmark + add to home)

### Opera

- OS X/Opera 12.15: 192.png (tab + speed dial + bookmark)

## Recommendations

- .ico file with 16x16, 32x32 and 48x48 transparent PNGs
- No need for `<link rel="icon" href="*.png">`, `<link rel="shortcut icon" href=".ico">` is enough
- iOS: 152x152 apple-touch-icon (iOS), will be rounded by iOS
- Android: manifest.json 192x192 PNG with background, will be rounded by Android/Chrome
- Windows 8 modern UI/Metro: msapplication-TileImage (+ msapplication-TileColor if the tile image does not have a background)

```HTML
<link rel="manifest" href="manifest.json?v=1">

<link rel="shortcut icon" href="16-32-48.ico?v=1">

<link rel="apple-touch-icon" sizes="152x152" href="background-152.png?v=1">

<meta name="msapplication-TileImage" content="144.png?v=1">
<meta name="msapplication-TileColor" content="...">
```
