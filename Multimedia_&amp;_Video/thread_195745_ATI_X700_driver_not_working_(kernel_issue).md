---
title: "ATI X700 driver not working (kernel issue)"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by Dexterp37 on 2006-06-13
Hi there!

I just uninstalled my 64bit ubuntu 5.10 and installed my new flaming Dapper :) I thought with this new setup I would have solved my ATI driver issues but... I was wrong :|

That's what xorg0.log says:

> (II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7051000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.24.8
(II) fglrx(0):     Date: Apr 11 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7051000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by whatever on 2006-06-13
how did you install fglrx?
your fgrx kernel module is too old. however the one inlcuded in dapper restricted-modules is newer than the one you got, so it's probably you who is responsible for the error...

guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by Dexterp37 on 2006-06-13
First of all, thank you for your precious reply :) That's odd, my vid card is the only thing preventing me from trashing my windows partition :]

Well, I followed that guide (1st method) but.. no results :|

Restricted packages were uptodate and I also tried to get the driver through synaptic. Now I just downloaded the package from ati... but I doubt it wll work :|

---

### Post by Dexterp37 on 2006-06-15
I just wanted to say that I found out what the problem was and I fixed it :D That may be helpful also to other ppl :) If the guide linked above on method 1 doesn't work, try method 2. When you get to the step which involves the following command

> sudo module-assistant prepare,update 

check if it throws any error. In my case it complained about not finding kernel headers to download (that version wasn't available through synaptic). Simply download a newer Kernel and download the according linux-headers package through Synaptic.

Follow method 2 on the guid again and it should work.

---

