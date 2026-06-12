---
title: "Intrepid nvidia glx issues"
date: 2008-12-08
forum: Multimedia Software
---

### Post by cruzton on 2008-12-08
After upgrading (via apt-get dist-upgrade) to Intrepid, my nvidia (GeForce FX 5200) no longer does hardware 3D.

At first, no video was working, but I got it working fine with the open nv driver and it's software 3D support. glxinfo and dpyinfo confirms that (software) GLX is loaded, and 3D applications run, but slowly.

When I install the nvidia-glx-173 etc modules, restart, the Hardware Drivers gui tool shows that I'm using the proprietary driver and that it is active. Furthermore, I've done many deactivation/reboot/activation cycles. No matter what I do, when the driver is "active", the 2D desktop works, but I don't have any GLX support. All 3D applications error and stop about the missing GLX extension. xdpyinfo confirms that it's missing.

Is the driver working? How can I enable GLX support?

This is a P4 (32-bit), so it does have the SSE support needed for the drivers, according to the docs.

Thanks!

---

### Post by sonofusion82 on 2008-12-09
i m using kubuntu 8.10 on my P4 machine with GeForce FX 5200.
nvidia proprietary driver is working fine for me pretty much out of box including kwin composite desktop effects.
however, i m not at my linux machine right now, i can post my xorg.conf later if u still could not figure it out.

---

### Post by cruzton on 2008-12-09
It was my understanding that the xorg in 8.10 doesn't really use the xorg.conf anymore. In fact, looking at mine, it has barely anything in it. I wonder what else I can change to try to control the setup, though.

---

### Post by fsamuels on 2008-12-09
I had problems with the NVIDIA version 173 driver too after upgrading from Ubuntu 8.04 to 8.10 on my laptop. I reverted to version 96 of the driver and it is working fine now. With the 173 driver it would lock up just as X was starting. I booted into the older kernel and was able to use the low res mode to change back to the older NVIDA driver. Everything seems fine now. The kernels I am using are 2.6.27-10.20 and 2.6.24-22.45. My video card is a GeForce FX Go5200 (32MB) on a Dell Inspiron 8600.

---

### Post by cruzton on 2008-12-11
Hmm, I tried the 96 driver and it does the same thing: 2D works, but no GLX ie. 3D support of any kind.

This sucks... 3D has worked flawlessly for 4 years with this card, and now it's useless.

---

### Post by cruzton on 2008-12-12
Ok, I got it working!

It turned out I had to also install the nvidia-common package, which brought in the modaliases packages from all the other drivers as well. After doing this, I selected the 173 driver from the Hardware Drivers GUI tool, restarted X and had NVIDIA backed GLX/hardware 3D support again. Nice.

---

