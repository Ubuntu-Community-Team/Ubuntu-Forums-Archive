---
title: "Ok, I surrender (ATI card)"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by jabeez on 2005-11-08
Well, I'm on my, ahem, 5th clean install of Breezy and as of yet, nothing I've done can get 3D accel. working with fglrx WITHOUT causing my computer to freeze every 2 minutes. I've tried every which way I've found on these forums and I can get it working, with fglrxinfo showing my correct (autodetected) card, with accel working, but after that anything I do other than a terminal (and sometimes even that) causes my comp. to freeze pretty much immediately. It *appears* to be DRI, because if I comment that out in xorg.conf then Breezy seems stable but, alas, no 3D accel, so what's the point. I had this working in Hoary the "easy" way by installing the fglrx driver and changing my xorg.conf file, but no go since the upgrade. Pretty disappointing, not sure how an "upgrade" can actually get worse for hardware support. Anywho, I don't mean to rant on my first post:smile: , so here are my system specs, anyone who has ANY idea?

Athlon XP 1600
256MB Ram
ATI AIW 8500 DV
SB Audigy ZS
Asus A7V333 MB

One more thing that wasn't working in Hoary that doesn't seem to be fixed is the hotplug subsystem. On boot it stops at initializing hotplug for a couple seconds, then moves on. It is the only thing during boot that doesn't get that OK next to it, and sure enough I plug in my Rio 500 and nothing happens. I can see it in device manager but don't know how to access it. Any help is greatly appreciated.

---

### Post by mlomker on 2005-11-08
Have you tried the [8.18.8 driver]("http://ubuntuforums.org/showthread.php?t=78466") or just the one from Breezy?

---

### Post by jabeez on 2005-11-08
The only one I've tried is the one through Synaptic or apt-get.

---

### Post by jabeez on 2005-11-08
Cheers! Woooooo HOOOOOOO!!! Well, so far so good anyways, thanks mlomker. This has been the furthest I've been able to go without a freeze, so I'll keep my fingers crossed. One question though, it says there are updates available for Breezy (this is a fresh install besides the graphics driver), but I'm afraid to screw this up! Did you do updates after this?

---

### Post by mlomker on 2005-11-08
If you are using the DEB files from the 8.18.8 how-to then you should be fine on updates.

---

