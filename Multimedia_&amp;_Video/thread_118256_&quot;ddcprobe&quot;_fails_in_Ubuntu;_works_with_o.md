---
title: "&quot;ddcprobe&quot; fails in Ubuntu; works with other distro"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by thermans on 2006-01-16
I get an error when I run "ddcprobe" under Breezy.  It's the "edidfail" error.

When I boot Knoppix on the same box "ddcprobe" works correctly.  Why?

This causes my external monitor to fail to use an optimum resolution.  From my "[Xorg.0.log]("http://www.hermans.net/Xorg.0.log")":

```
(WW) RADEON(0): Failed to detect secondary monitor DDC, default HSync and VRefresh used

```

I'm using an IBM Thinkpad T40 with a ViewSonic G810 as the external monitor.  The video card in this box is a Radeon Mobility 7500.  The monitor is capable of at least 1600x1200 but all I get is the same as the LCD screen 1024x768.

Any ideas?  Here's my [xorg.conf]("http://www.hermans.net/xorg.conf").

---

