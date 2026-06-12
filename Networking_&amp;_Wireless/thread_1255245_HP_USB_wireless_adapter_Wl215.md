---
title: "HP USB wireless adapter Wl215"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by zainka on 2009-09-01
Hi

We have a few USB wireless adapters from HP (wl215) which we try to use under Ubuntu 9.04.

We first tried to use the ndiswrapper and install wndowsXP driver. This only caused the laptop to halth during boot when starting bluetooth. A reboot with the adapter disconnected solved boot issue.

However that seem not to work.

We also tried to download and build orinoco_0.015rc4 driver but build was unsuccessful. Found som tutorials where people have tried to build Orinoco but no one reported success. However they never intended to use wl-215

Question is if anyone have successfully used this adapter under ubuntu 9.04...
Old adapters you said. Yes really, but we like to try for fun anyway. ;)

Breg Vidar

---

### Post by zainka on 2009-10-14
Okay, I gave it up and got curious for whats inside. I break it open and guess what, its nothing but a USB PCMCIA bridge with a plain PCMCIA 11b wlan card attached inside. Sliding the wlan card into my ubuntu directly works out of the box !, So much for the wl215 linux driver.

Nice for other to know if you happen to get your hands on one of these adapters. the card found inside could also be connected to an external antenna as well. The PCMCIA bridge may be used to other stuff, aswell.

---

