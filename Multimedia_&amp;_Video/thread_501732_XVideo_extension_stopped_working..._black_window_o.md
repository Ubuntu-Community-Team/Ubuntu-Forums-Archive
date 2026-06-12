---
title: "XVideo extension stopped working... black window only"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by jbotz on 2007-07-15
Some time in the last couple of weeks XVideo stopped working in mplayer, vlc, Kino, etc.  When I try to play some video I just get a black window, although mplayer for example shows the progress and I get the sound.  There are no errors.  Xorg.0.log shows that Xvideo extension is loaded.  As does "xvinfo".  With mplayer I can specify "-vo x11" or "-vo gl" and I get video.  But there is no such workaround for i.e. Kino, and in any case xv is best.

This is on 7.04 + all recent updates.  I have a Radeon 7500 and I'm using the xorg radeon driver.

Anyone else see this?  Any ideas?

---

### Post by jbotz on 2007-07-16
I solved this... apparently XVideo needs a framebuffer device, and for whatever reason 'radeonfb' wasn't getting loaded.  After manually doing 'modprobe radeonfb' and restarting X, things are working.  That leaves the question why the module stopped getting loaded...

What is the correct way in Ubuntu to load the framebuffer device kernel module?  At boot time or automatically through udev? How do I specify this?

---

