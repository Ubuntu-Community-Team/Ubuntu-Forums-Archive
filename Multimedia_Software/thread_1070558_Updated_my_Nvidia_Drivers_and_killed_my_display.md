---
title: "Updated my Nvidia Drivers and killed my display"
date: 2009-02-15
forum: Multimedia Software
---

### Post by jlaroche on 2009-02-15
I need some assistance please. I am running Ubuntu 8.10 64bit with a GeForce 8800 GTX 768mb video card (complete system specs to follow). I was running the 177 drivers and tried to install the 180.22 drivers from the NVIDIA website (NVIDIA-Linux-x86_64-180.22-pkg2.run).

Long story short, graphics stopped working after installing the new 180.22 drivers. I only have command line access now (but thankfully this is a dualboot system so I am writing to you from a working OS... I won't say which, but take a wild guess).

Can anyone help me reinstall my 177 drivers via command line? Or does anyone know of another way I can fix this situation?

**System Specs**:
Asus A8N32-SLI Deluxe Motherboard
AMD 4200+ 64bit Dual Core CPU
4gb Ram
4 SATA Hard Drives (
Plextor PX-716A SATA DVDRW Drive
Nvidia GeForce GTX 8800 768mb Ram
Sound Blaster Audigy 4

Thanks

---

### Post by Insane_Homer on 2009-02-15
some of the beta's are bit iffy.

I've found 180.16 to be good for me and very stable, yet any since then and caused me no end of problems.

Although I'm on 32-bit hopefully they'll work for you too
[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/)

---

### Post by Kevbert on 2009-02-15
There is two ways you can do this. Boot into recovery mode and select Xfix to fix the X-server display driver or edit your xorg.conf file and remove any mention of the display driver (or set it to nv). You should then be able to login (but will get an offset display) and install the 177 driver via restricted drivers.

---

### Post by norwoods on 2009-02-15
Anders Kaseorg has built packages for Jaunty that will also work in Intrepid. They are available in his ppa here:
[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

