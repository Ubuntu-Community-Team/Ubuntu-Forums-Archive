---
title: "HP zv5000 Wireless with ndiswrapper not working"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Gyroscope352 on 2009-06-14
Hey all. trying to install Jaunty on an old HP I had lying around (MacBook got dropped down the stairs by a hotel bellhop) and I'm having a bit of wireless trouble. I know you're supposed to use ndiswrapper for this wireless card, and I have installed it and loaded the right .inf file (and blacklisted the right things), but when i installed it in ndisgtk, it said "unable to see if hardware is present." My output for sudo modprobe ndiswrapper is:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Anyone have any idea what my next step is?

---

