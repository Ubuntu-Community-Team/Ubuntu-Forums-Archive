---
title: "Please help!"
date: 2009-05-05
forum: Multimedia Software
---

### Post by ntaforge on 2009-05-05
I've been trying to do a clean install of Jaunty amd64 and I'm ready to quit!

I cannot get my ATI X1200 card to work at all! I've tried the open source drivers, it works but it's very jerky. I've tried the proprietary drivers using Envy NG, black screen at login. I booted into recovery and used Envy to uninstall the drivers and now I stuck with the default drivers

I really need some help! I'm sick of not having a computer!

Please and Thank You
Noah

---

### Post by ntaforge on 2009-05-05
Bump

---

### Post by lavinog on 2009-05-05
the x1200 is now considered a legacy card and is no longer supported by the current proprietary drivers. The older proprietary drivers are not compatible with jaunty so the open source driver is your only option. It will improve over time.
Your other option would be to get a new card.

---

### Post by ntaforge on 2009-05-11
It's a laptop card and it's only 6 months old

---

### Post by ntaforge on 2009-05-11
The thing that I don't like is that the open source driver is very glitchy and slow

---

### Post by lavinog on 2009-05-11
The open source driver will get better soon. ATI has recently supplied a significant amount of documentation to advance its development. [http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

I too have a laptop that is no longer supported.  It is 2 years old, but I am ready to replace it with a netbook (I am killing my back hauling this brick around)

I think they were a little too quick to move these cards to legacy since the most recent driver is still just as bloated.
I also think the radeon driver included with jaunty is version 1.2.4 while version 1.2.5 is already available:
[http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README):
```
Major Changes
=============

Read ChangeLog for a complete list.

- Version 1.2.5

  - Added 2D acceleration for R6xx and R7xx.
  - Added XVideo support for R6xx and R7xx.
  - Added support for RS880 and RV790.
  - Added RandR 1.3 mandatory properties.
  - Refactoring of MC code.
  - Enable DRI support by default on R5xx and RS6xx.
  - LUT (color lookup table) fixes.
  - Tons of quirk table entries and bug fixes.
  - Fix register accesses for processors that reorder memory writes.


```
The X1200 is a RS690 chipset

---

