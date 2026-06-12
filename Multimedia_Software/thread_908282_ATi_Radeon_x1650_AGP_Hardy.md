---
title: "ATi Radeon x1650 AGP Hardy"
date: 2008-09-02
forum: Multimedia Software
---

### Post by No-Neck on 2008-09-02
Hi, I'm doing an install of Ubuntu Hardy for my little brother, he wants 3D support. His PC (vey) unfortunately has an AGP x1650 and the drivers do not work, at all. There are numerous threads on these forums but they appear to have been abandoned and no fix has been found, surely there is a solution out there somewhere. Here is what I have tried, as suggested in the many threads:

The drivers supplied by the hardware drivers manager = black screen on boot, no GDM.

Changing the aperture size in BIOS and adding a couple of lines to xorg.conf = black screen.

aticonfig --initial -f, dpkg reconfigure xserver-xorg, xfix = black screen.

Installing the drivers after updating to the latest kernel version = black screen.

The drivers supplied by envyng = black screen.

The latest ( 8.8 ) catalyst from ATi. = surprise, black screen.

An older (8.42.3) driver from ATi = get the login screen here, white screen after login, X doesn't crash, can restart it with Cntrl+Shift+Backspace, I assume this is caused by the Compiz effects (which is the main point of me installing the drivers).

Install Ubuntu 7.10 and use the restricted drivers manager = **WORKS**

So, something in Hardy is conflicting with something in the ATi drivers? Surely then, we should be able to get this working in Hardy?

---

