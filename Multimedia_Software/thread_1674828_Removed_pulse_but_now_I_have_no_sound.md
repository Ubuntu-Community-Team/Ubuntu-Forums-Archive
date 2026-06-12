---
title: "Removed pulse but now I have no sound"
date: 2011-01-24
forum: Multimedia Software
---

### Post by jamesdew on 2011-01-24
Ubuntu 10.04

OK so your first thought might be "well duhh" but I did this to solve a problem with XBMC where I could net set up ALSA passthrough without removing it,

The problem is I also sometimes use this machine for other purposes so I need regular sound from for example my browser.

I set ALSA as the default in gstreamer.properties and I can get sound in XBMC though my passthrough but not the rest of ubuntu.

If I click system > sound I just get "waiting for sound system"

Where else should I be pointing ubuntu at ALSA? I'm not even sure what logs I should be looing at here. Any help would be greatly appreciated.

---

### Post by jamesdew on 2011-01-24
ok so this post

[http://forum.xbmc.org/showthread.php?t=71885&page=4](http://forum.xbmc.org/showthread.php?t=71885&page=4)

helped me keep pulse and use passthrough, but still the same problem.

Gstreamer test works but sound still going to pulse.

why would the gstreamer change not work? how else can I control where audio goes?

---

