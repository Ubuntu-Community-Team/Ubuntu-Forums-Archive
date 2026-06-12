---
title: "problem with ATI drivers (Radeon X1650)"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by hadjimurad on 2008-03-23
I have an ATI Radeon X1650 card, and I've tried following the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) in order to get ATI's proprietary drivers working. Before I resorted to this I tried checking off the box for my ATI card in the restricted drivers window, but when I did this and rebooted I only had a black screen and had to reinstall to fix it.

The error gets thrown when the guide tells me to run ```
sudo aticonfig --initial
``` The error message I get is: ```
*** glibc detected ***aticonfig: munmap_chunk(): invalid pointer: 0xbfed79e8 ***
```, followed by a backtrace and a core dump. Everything I try to do afterwards doesn't work because I no longer have an xorg.conf file in the etc/X11 directory. I've also tried using Envy to fix my problem; when I log in, I just get a blank white screen and the mouse shows up but nothing else. Any help would be appreciated.

---

