---
title: "Network cards not detected"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by soomonster on 2012-01-12
Hi, been using linux for awhile but I can't seem to figure out my wireless cards(I just need one to work don't care which). ifconfig and iwconfig won't acknowledge either of my cards though both work fine on another os. I'm currently borrowing a usb wireless adapter that works fine.

Madwifi is obsolete apparently and I've seen something about an ath5k driver that is supposed to be already integrated but I can't seem to find any solution. This is a fresh install of 11.10 with the standard kernel upgrade. 

Any help would be appreciated thanks!



Ubuntu 11.10 oneiric
Kernel:3.0.0-14-generic
Wireless cards: Netgear wg311T    Zonet1642

---

### Post by soomonster on 2012-01-13
Got it, vista driver AR5004X (tried xp driver rt2860 before for netgear) with ndiswrrapper, installed it worked on the spot.

---

