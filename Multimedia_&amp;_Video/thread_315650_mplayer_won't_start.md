---
title: "mplayer won't start"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by cotodd on 2006-12-09
mplayer starts then disappears.  I ave removed and reinstalled using apt-get.

OS ubuntu 6.10 -- Rhythmbox works.

using command line:

cotodd@cotodd-linux:~$ gmplayer
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

How di I fix this?

---

### Post by meng on 2006-12-09
The problem seems to be the absence of a skin for your mplayer. All the other messages are fine (if you run gmplayer without specifying a media file). My default skin location is:
/usr/share/mplayer/Skin/default/skin

but I'm not sure how to point your mplayer to that skin. Perhaps you could create a symlink for that file, to /usr/share/mplayer/skins/default/skin, then change preferences in mplayer once it's running.

---

### Post by taurus on 2006-12-09
You can change the "skin" in ~/.mplayer/gui.conf...

```
gedit ~/.mplayer/gui.conf
```

---

### Post by cotodd on 2006-12-10
Thx for the answers --- using Synaptic to load the mplayer-skins fixed the startup problem.  Now I can't get decent audio regardless of codec selection.

---

### Post by taurus on 2006-12-10
Go into Preferences -> Audio and try different audio driver until you get the one you like...

---

