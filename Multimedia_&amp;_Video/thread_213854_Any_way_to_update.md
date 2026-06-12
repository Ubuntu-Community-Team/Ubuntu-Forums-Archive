---
title: "Any way to update"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by jgcamp99 on 2006-07-11
to the latest kernel and so on when a major update occurs and tell Ubuntu to leave my video card drivers alone for fglrx for the ATi Radeon 9600 XT or any other ATi video card ? I wind up doing an update of that magnitude and having to reinstall the fglrx because the update changes it over to mesa.

Does anyone have to reinstall drivers like this for their nVidia video cards ?

I like being able to upgrade, it'll make minor updates easier without the possibility of having to hide a major kernel upgrade or even sifting thru, in this case 33 files to figure out which will upgrade and work. I guess that's the downside to getting a newer kernel that's upgraded and stabilized ?

---

### Post by fluffington on 2006-07-12
I don't have an ATI card, so I can't actuall test this, but I'm pretty sure you should be able to use the driver in the package xorg-driver-fglrx, which aught to update whenever the kernel does.

As for nVidia, I use the driver in nvidia-glx and it works fine without me having to do anything.

---

