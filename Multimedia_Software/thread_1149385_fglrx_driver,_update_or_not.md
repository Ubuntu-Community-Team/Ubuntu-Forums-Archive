---
title: "fglrx driver, update or not?"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Gabri82 on 2009-05-05
Hi all  ):P,

i'm new in this forum, and also almost new with ubuntu.

I'm running ubuntu 8.04 with an ATI card (unlucky me :( ), a Mobility Radeon X600SE and I had some problems with previous ubuntu versions and drivers. Now that all it seems working fine (drivers 8.47.3), I am afraid to stick me again in those driver's problems only by updating, as happened the last time. So this is my maybe silly question: it's always safe do the updates proposed from update-manager?

Just in case i want to try the new version, can i turn back to the previous settings after an update (without messing up something)?

There's a way to see which version is proposing the update-manager? This is the only description that it reports:

"Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
* FireGL: V8650, V8600, V7600, V7350, V7300, V7200, V7100, V5600, V5200, V5100, V5000, HD3870, HD3850, V3600, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
* FireMV: 2200 (Single card PCI-e configuration)
* Mobility FireGL: V5000, T2
* Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, X200, 9800, 9600, 9550, 9500
* Radeon Xpress: 1200 series, 1100 series, 200 series
* Radeon: HD2900, HD2600, HD2400, X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500
ATI All-in-Wonder variants of the above cards/chips are also supported, but video capture is not.
This package provides 2D display drivers and hardware accelerated OpenGL."

I hope my english it's understandable... :P
Thanks

---

### Post by tardeevo on 2009-05-11
yeah I'm in your same struggle - I gotta radeon 9600 pro that works perfectly on 8.04 and with great OpenGL performance and now the adept updater is pushing me for an upgrade, I started it and (thank God) suddenly a warning popup informed me that there is no fglrx drivers on 9.04 for my card :confused:
Really upsetting.

---

### Post by markbuntu on 2009-05-11
No, it is not always safe. It is not safe if you have a proprietary driver installed. It is not safe if you have applications or other stuff from outside the official repositories.

The proprietary ati driver in Jaunty 9.04 will not work with your cards and previous drivers from ati will not work with Jaunty so you will be using the open source ati driver. If you do upgrade be sure to remove fglrx and the fglrx kernel modules before doing so.

Besides that, if you are happy with Hardy there is really no reason to upgrade as Hardy will be supported for another 2 years. I still use Hardy as my main install, Intrepid and Jaunty have proved to be far less stable and will not be supported as long as Hardy. I will probably wait for the next LTS before moving.

---

