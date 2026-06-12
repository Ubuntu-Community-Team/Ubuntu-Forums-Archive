---
title: "Totem won't play WMV"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by sasanf on 2007-06-29
I tried to play a wmv vid in Totem, MPlayer, and GXine.  The movie wouldn't play on any of them.  I've installed all libs.  The only lib I haven't installed is libdvdcss2.  I performed synaptic search but it did not find it.

---

### Post by eggdeng on 2007-06-29
libdvdcss2 is for playing DVDs, not .wmv. What you are probably missing are the w32codecs.Try ```
apt-cache search libdvdcss2
``` to see if you can find it, if not you need to update the repositories in  your sources.list. 
Depending on which version you are using, you can find help with this at [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) or [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Alternatively, install Automatix2 which will get the codecs and install them for you.

---

### Post by DishBreak on 2007-06-30
I have a similar problem. I have w32codecs installed, xine installed, gstreamer installed, with ffmpeg plugin.

I'm at the end of my rope now. what do i do?

---

### Post by eggdeng on 2007-07-01
Start by installing MPlayer or use Automatix2 to install it for you. If that doesn't solve your problems, take a look at [http://ubuntuforums.org/showthread.php?t=187967](http://ubuntuforums.org/showthread.php?t=187967).

---

