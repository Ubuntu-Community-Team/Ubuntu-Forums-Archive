---
title: "Bizarre NVIDIA driver problem"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-11-16
I've now had a very long-running problem with refresh rates. My current situation is that I have 1024x768 @ 85Hz with the 2D-only nv drivers. But I want the restricted 3D drivers, and I just tried that.

The problem with this is that trying it gets me an insanely low, interlaced refresh rate. KControl says 50-54Hz are the only possibilities, and using the "dpkg-reconfigure xserver-xorg" trick gets me absolutely nowhere. I can set the refresh rate to 85Hz with nvidia-settings, but (and this is familiar problem) the setting won't stick through a restart of the X server.

Manually editing xorg.conf also got me nowhere. I found there were two 'screen' sections, two 'monitor' sections, and two 'device' sections. I commented out the duplicates (leaving only one 'monitor' section that stated 60Hz as the minimum refresh rate while the other stated 50Hz) but to no avail.

My hardware is an integrated 'GeForce 6-class' video card, and a Samsung SyncMaster 793s monitor. I've attached the xorg.conf file that gives me this problem (xorg.conf.bad.txt) and the one I'm using now for reference (xorg.conf.original.txt).

---

### Post by wolfen69 on 2007-11-16
did you try changing 1024x768(at the bottom of the "bad" xorg.conf) to the desired res?

---

### Post by Rhapsody on 2007-11-16
1024x768 *is* the desired res. I still got the problem while it wasn't commented as well.

---

