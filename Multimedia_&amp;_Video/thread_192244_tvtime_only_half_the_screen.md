---
title: "tvtime only half the screen"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by embezzler on 2006-06-08
As many other satisfied Ubuntu users, I have a ATI Radeon X700 video card and a Pinnacle PcTv Stereo tv card. Following the many tips and the basic fglrx drivers works just fine.

The issue that I have at the moment, is that tvtime displays only video in the top half of my Hercules TFT screen. The desktop itself looks just fine.

Furthermore, I do have audio support in Ubuntu, but not in tvtime

Does anyone have a suggestion where I should start looking?

I installed Ubuntu 5.10

---

### Post by bruceleo on 2007-04-12
In /etc/X11/xorg.conf:
Under "Devices" set Option "VideoOverlay" to "off"

---

