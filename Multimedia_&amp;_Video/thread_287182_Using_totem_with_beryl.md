---
title: "Using totem with beryl"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by joehill on 2006-10-28
I just installed beryl, which is incredible and surprisingly fast and stable on my integrated Intel chip (compared to compiz and any other compositing stuff I've used).  The only problem I've run into is that when I try to watch a movie, totem-xine shows a blue screen (or sometimes a black screen with the contents of another window slightly showing through) and totem-gstreamer shows a black screen, so they're useless.  If I try to view in full-screen, it sometimes works but is pretty slow and unresponsive.  Sometimes I can watch things on VLC just fine, but sometimes not.

Any ideas on how to make totem work with beryl?

Thanks!

---

### Post by kecsap on 2006-11-01
Use mplayer! I have Intel video card with beryl and the mplayer works with Xv output. See this topic: [http://ubuntuforums.org/showthread.php?t=289617](http://ubuntuforums.org/showthread.php?t=289617)

Perhaps, there is possible some kind of hack for VLC to work (there are more video output plugin in preferences) but I did not work on it.

I will post if I will try to repair the totem and VLC on my computer this evening.

---

### Post by kecsap on 2006-11-01
The configuration of the VLC is very easy under beryl:

1. Go to Settings/Preferences/Video/Output modules/XVideo
2. Check the Advanced options below.
3. X11 display name change to 0, XVideo adaptor number to 0.

gstreamer works only with Video output "X Window System (No Xv)". To setup it launch the gstreamer-properties.

gxine works for me without any configuration...

---

### Post by joehill on 2006-11-02
Thanks! VLC works with the tweak you suggest.  Totem and MPlayer display video when on their own desktop with no other windows, but the video doesn't move/wobble when I drag the window.  But I'm happy using VLC, so I'm not too worried.

---

