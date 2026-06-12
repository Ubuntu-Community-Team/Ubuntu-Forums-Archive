---
title: "Video Stutter"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by KonoKanji on 2007-04-28
I'm not sure whether or not it was the upgrade to Feisty or the upgrade of the ATI Driver, but now all my videos stutter when the image is moving and the video is in fullscreen.  However, it doesn't affect the audio, so I'm pretty sure it's not over-use of my processor considering the same problem happens when I've rebooted and when I've got five heavy processes running in the background.

I'm using an ATI Radeon x1400 Mobility that worked perfectly fine a few days ago, before the upgrade.

Fglrxinfo
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6458 (8.36.5)
```

Might I be able to get some help?

---

### Post by disturbed1 on 2007-04-28
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

Should be in your Xorg.conf file under the device section. Video overlay acceleration is usually disabled when 3D acceleration is encabled.

Here's a decent wiki for more info [http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

---

### Post by KonoKanji on 2007-04-28
Mmm... I double checked on it to see if it had changed, but nope.  It's still:

```
Option    "VideoOverlay"   "On"
Option    "OpenGLOverlay"   "Off"
```

However, I went over the overlay-type=Xv again, and got something that I don't remember getting before:

```
[B]Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.[/B]
Using xorg.conf
Saved back-up to xorg.conf.fglrx-4

```

---

### Post by disturbed1 on 2007-04-29
You'll have to restart X in order for the changes to take effect.

In gnome, system menu, preferences, choose multimedia systems selector, it might be hidden by default, if so just edit the menu to show it, or run gstreamer-properties from a command prompt.

Under the video tab, you can change the preferences there. This mainly effects only gstreamer programs. In VLC, you can chooses the preferences, and show advanced to select the playback type. Mplayer also has a preference settings.

---

