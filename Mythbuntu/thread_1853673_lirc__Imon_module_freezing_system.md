---
title: "lirc / Imon module freezing system"
date: 2011-10-02
forum: Mythbuntu
---

### Post by Mercury821 on 2011-10-02
Hi all,

I'm in the process of upgrading my myth installation to some slightly newer hardware, but retaining the same Silverstone HTPC case that I've had for several years.

I'm trying to get my front panel display / remote receiver to function, but mythbuntu will not boot with the iMon IR/VFD module connected. If I connect the USB connector to the MB after boot, the system immediately locks up. I've hunted through my system logs and google with not much success. I even tried to build lirc from source and install the latest (0.9.0), but the problem persists. 

I see the following 3 lines in my dmesg immediately before the freeze:

> [   11.964710] lirc_imon: module is from the staging directory, the quality is unknown, you have been warned.
[   11.966107] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.8
[   11.966134] usbcore: registered new interface driver lirc_imon

Any suggestions on what to try next?  Thanks!

---

