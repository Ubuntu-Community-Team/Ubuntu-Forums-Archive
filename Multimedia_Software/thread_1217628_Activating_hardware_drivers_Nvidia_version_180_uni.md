---
title: "Activating hardware drivers Nvidia version 180 uninstalls xserver-xorg!!"
date: 2009-07-19
forum: Multimedia Software
---

### Post by evilspoons on 2009-07-19
I have a computer with a EVGA nForce 730i mainboard (Geforce 9300). I have Jaunty. I've been running hardware accelerated drivers version "180" (according to Hardware Drivers, more on this later). Up until a few days ago this worked beautifully, I had VDPAU hardware accelerated decoding in XBMC and could play Blu-ray files at 30 frames per second on my slow Pentium Dual-Core CPU.

Now... an update to the package seems to have been released, update manager installed it... and I lost 3d acceleration. I then attempted to reactivate these drivers with Hardware Drivers, and rebooted. Now I am missing X entirely. It uninstalled xserver-xorg!

When attempting to reinstall xserver-xorg, it gave me an error about how it couldn't uninstall nvidia-glx-180 properly. I had to mkdir modules/extensions inside an xorg folder and do touch libGLblah.so (I can't remember the exact name, sorry). The package then uninstalled, xserver-xorg reinstalled...

And now I am back where I started. No 3d acceleration, and activating the 180 series drivers uninstalls xserver-xorg again. (AND... they are actually 185 series drivers - installed version is listed as "185.19.1~really185.18.14-0ubuntu0~intrepid0") (I am running jaunty, where is intrepid coming from?)

EDIT: I got it to work again (finally) by using Synaptic to force nvidia-glx-180 to version 180.44-0ubuntu1.

Why did I have to do this in the first place?

Is there a 185 PPA for Jaunty?

Is there a 190 PPA for Jaunty?

---

