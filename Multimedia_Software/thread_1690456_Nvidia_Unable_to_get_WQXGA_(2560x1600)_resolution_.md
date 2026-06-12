---
title: "Nvidia Unable to get WQXGA (2560x1600) resolution Dual screen"
date: 2011-02-18
forum: Multimedia Software
---

### Post by dav3hit3 on 2011-02-18
Hi,
I'm running Ubuntu 10.10 with an NVIDIA Quadro FX 1800 and am unable to get higher than 1280x800 resolution. I just tried the latest drivers (260.19.36) and still no luck.

I have two HP LP3065 (30") monitors that are 2560x1600 native. My QuadroFX 1800 card has dual output display ports (with adapter to DVI-Dual Link cables).

Video Card, Cables and Monitors all work with full high res under windows and RHEL5.5, but I am unable to get Ubuntu 10.10 or Ubuntu 10.04 to recognize the setup. 

I've tried it all... setting the mode line directly with xrandr, manually setting the xorg.conf settings, nvidia-auto-select, Single monitor, dual monitors, etc... Nada!

The Nvidia drivers for 10.10 don't seem to be able to probe and recognize the correct resolution.

Anybody got ideas?
Thanks! -Dave-

---

### Post by ravedog on 2012-02-06
Got the same issue, did you find a solution?

br,

Ravee

---

### Post by dav3hit3 on 2012-02-06
Hey Ravedog,
Nope... I think the answer is the Quadro FX 1800 sux and can't support two monitors at 2560x1600.

I trashed it and got a better card.

---

