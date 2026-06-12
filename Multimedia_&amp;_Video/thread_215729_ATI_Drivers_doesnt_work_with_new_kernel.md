---
title: "ATI Drivers doesnt work with new kernel"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by schlag on 2006-07-14
Hello ubuntu community,

I have an ATI Radeon 9200se(AGP) video card.
I recompiled the lastest kernel version(2.6.17.4) that I've download from [www.kernel.com](www.kernel.com).

I used to use the following commands to install the drivers with the old kernel(the one that comes with ubuntu dapper 6.06 by default):
 
 sudo apt-get update
 sudo apt-get install linux-restricted-modules-$(uname -r)
 sudo apt-get install xorg-driver-fglrx
 sudo aticonfig --initial
 sudo aticonfig --overlay-type=Xv


But I can't find the linux-restricted-modules for the new kernel.

What do I have to do to install my graphics card drivers with the latest kernel version?

-thanks in advance ;)-

---

