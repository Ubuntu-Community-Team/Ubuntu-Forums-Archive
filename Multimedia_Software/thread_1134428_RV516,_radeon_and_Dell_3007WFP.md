---
title: "RV516, radeon and Dell 3007WFP"
date: 2009-04-23
forum: Multimedia Software
---

### Post by CHaoSlayeR on 2009-04-23
Hi there,

today I wanted to try out a Dell 3007WFP with my AMD RV516 board using the radeon driver. But although the Xorg.0.log looks just fine the picture on the monitor is just crap (vertical lines in various colors on black background).

I have tried two modelines and there is no statement in the log that it gets ignored or not applied but all my effords result in the exact same crappy picture on the monitor.

I used the following modelines:

"2560x1600@60"  268  2560 2608 2640 2720  1600 1603 1609 1646 -hsync +vsync
"2560x1600@60" 348.2 2560 2752 3032 3504  1600 1601 1604 1656 -hsync +vsync

As there is no error or warning in the log file I come to the conclusion that there might be an issue with the cabling and/or simply my card.

The card has an RV516 chip and one Dual-Link-DVI out (using a Y-cable split up into two DVI-I connectors). It doesn't matter on which the connectors I attach the monitor (using a Dual-Link). The card is apparently an old X1300PRO (90nm, 400MHz RAMDAC) and not an X1550 (80nm, 550MHz), but the spec says that it supports Digital displays with up to 2560x1600 pixels.

I would appreciate any hint or anything I could try as I really want to have that thing working.

Thanx,

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-27
I have tried to set up the monitor in Windows Vista but with no success. I even installed the Dell monitor driver.

So this is rather strange as there is no error or even a warning in my Xorg.0.log when I try to drive that resolution. Can someone tell me what I can try next?

Thanx,

C]-[aoZ

---

