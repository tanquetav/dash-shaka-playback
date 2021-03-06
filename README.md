[![npm version](https://badge.fury.io/js/dash-shaka-playback.svg)](https://badge.fury.io/js/dash-shaka-playback)
[![license](https://img.shields.io/badge/license-BSD--3--Clause-blue.svg)](https://img.shields.io/badge/license-BSD--3--Clause-blue.svg)

# dash-shaka-playback

A [clappr](https://github.com/clappr/clappr) playback to play dash based on [shaka-player](https://github.com/google/shaka-player).

> CDNJS: https://cdnjs.cloudflare.com/ajax/libs/dash-shaka-playback/2.0.5/dash-shaka-playback.js
>
> (for some reason jsdelivr is not working) CDN JSDELIVR: https://cdn.jsdelivr.net/clappr.dash-shaka-playback/latest/dash-shaka-playback.js
>
> NPM: https://www.npmjs.com/package/dash-shaka-playback/

# Demo

[![dash shaka playback screenshot](https://raw.githubusercontent.com/clappr/dash-shaka-playback/master/public/screen-shot-dash-clappr.png)](https://jsfiddle.net/leandromoreira/m8ndduLo/29/)

# Usage

```html
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/clappr/latest/clappr.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/dash-shaka-playback/2.0.7/dash-shaka-playback.js"></script>
  </head>

  <body>
    <div id="player"></div>
    <script>
      var player = new Clappr.Player(
        {
          source: '//storage.googleapis.com/shaka-demo-assets/angel-one/dash.mpd',
          plugins: [DashShakaPlayback],
          shakaConfiguration: {
            preferredAudioLanguage: 'pt-BR',
            streaming: {
              rebufferingGoal: 15
            }
          },
          shakaOnBeforeLoad: function(shaka_player) {
            // shaka_player.getNetworkingEngine().registerRequestFilter() ...
          },
          parentId: '#player'
        });
    </script>
  </body>
</html>
```

# DRM

If need to protect your content (DRM) you must use the `shakaConfiguration` following the [shaka configuration](http://shaka-player-demo.appspot.com/docs/api/tutorial-drm-config.html) need.

# License Wrapping

If need to wrap DRM license requests or responses you use `shakaOnBeforeLoad` following [shaka License Wrapping](http://shaka-player-demo.appspot.com/docs/api/tutorial-license-wrapping.html) guide.

# Development

Install dependencies:

`npm install`

Run dev. server :

`npm start`

By default, dev. server is listening on `http://0.0.0.0:8080`.

Build plugin:

`npm run dist`

By default, Shaka player is bundled with plugin. A "lightweight" version of this plugin, without shaka player bundled, `dash-shaka-playback-external.min.js` is available.

# "extra" features

This playback offers you an API for handling with: audio, video and text tracks.

```javascript
selectTrack(track)
textTracks()
audioTracks()
videoTracks()
```

# For the older versions [check](https://github.com/clappr/dash-shaka-playback/tree/releases)
