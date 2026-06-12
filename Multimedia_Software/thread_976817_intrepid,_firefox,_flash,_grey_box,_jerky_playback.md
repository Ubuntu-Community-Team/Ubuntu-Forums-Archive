---
title: "intrepid, firefox, flash, grey box, jerky playback HELP!"
date: 2008-11-09
forum: Multimedia Software
---

### Post by ronniew on 2008-11-09
intrepid 8.10 firefox 3.03 flash nonfree


hesitates, is jerky, screen goes grey, looses audio/video sync.,,, tried most "fixes" still the same

any solid fixes for this on going issue>?

---

### Post by Bif Powell on 2008-11-13
All I can offer is 'same here'.

8.10
ThinkPad X40
512MB RAM

Upgrade from Hardy, not a new install.  Flash and FF worked fine before with none of these problems.

---

### Post by blackbird-xx on 2008-11-15
ronniew, what was the source of the fixes you tried?  I am researching this problem too.

I have 2x2 core Opteron running 2GHz each, GeForce 6600 running the restricted nvidia driver, ADSL2+ connection, ubuntu Hardy.

I don't believe this can be network related, certainly not CPU unless flash is single threaded and requires > 2GHz processor.  The video is smooth on non-flash video.

Using FF 3.0.3
Flash:
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

BTW I am trying to watch ABC iView.

---

### Post by blackbird-xx on 2008-11-15
Just found this thread.

It might help if you aren't running 64-bit linux.


[http://www.broadbandreports.com/forum/r21277477-Flash-10-for-Linux](http://www.broadbandreports.com/forum/r21277477-Flash-10-for-Linux)

This link helped me install Flash 10 on AMD64.

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

Playback very much improved and now watchable.  Still some jerkiness but not much.  CPU of npviewer.bin has shot up from ~75% to ~115%.

---

### Post by blackbird-xx on 2008-11-18
... And after all that, Adobe released an alpha 64-bit linux version.

It works.  Only issue still is with full screen panning - some jerkiness, but otherwise ok.

I am happy.  Good luck.

---

### Post by peakshysteria on 2008-11-18
Upgrade your flash:
> **philinux said:**
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Or enable the partner repo it only contains flash from adobe and opera.
There's even a .deb file for linux. Make sure you uninstall flashplugin-nonfree.

---

