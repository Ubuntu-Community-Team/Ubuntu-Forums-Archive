---
title: "Can't set up second monitor 11.04"
date: 2011-05-04
forum: Multimedia Software
---

### Post by cranfusion on 2011-05-04
Hello!  First post here, been playing with ubuntu for a while...

Just upgraded my desktop (dual-boot Dell Dimension 5150) to 11.04.  Trying to set up second monitor (couldn't get it to work in 10.10, hoped 11.04 would fix).  Time to ask for help!

```
lspci | grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

03:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

```
Monitor A attached to Intel card, works great.  

Monitor B in ATI, will show Ubuntu splash screen during startup, then no signal thereafter. "Detect monitors" in the Monitors panel doesn't find it.

Both monitors work perfectly in Windows.

I tried installing FGLRX/proprietary driver, but aticonfig said "no supported adapters found".  Uninstalled.

Many thanks for any ideas!

---

