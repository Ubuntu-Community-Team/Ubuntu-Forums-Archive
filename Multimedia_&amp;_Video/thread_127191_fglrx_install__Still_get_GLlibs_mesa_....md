---
title: "fglrx install / Still get GLlibs mesa ..."
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by joneZ on 2006-02-08
Hi @all,

I can't get the fglrx drivers to work on my system.  :???: 

I have always get this, I can do what i want.

```

erik@yukon:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Maybe someone can help me ... or give me any hints what I'm doing wrong.


Module is loaded ... 

```

erik@yukon:~$ dmesg | grep fglrx
[4294690.157000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294690.160000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[4294690.160000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
[4294690.251000] [fglrx] ACPI power management is initialized.

```


xorg.conf ist correct to:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"

```


module is in lsmod
```

EndSectionerik@yukon:~$ lsmod | grep fglrx
fglrx                 444604  0
agpgart                36784  2 fglrx,intel_agp

```


X ist loading the right driver

```

erik@yukon:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so

....

(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default

```


But I get this in Xorg.log

(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


So I'm assuming the module is bad, but how can I find that out.

the module comes from linux-restriceted-modules.

But what am I doing wrong. 

Bye and many thx for any hints
Erik

---

### Post by x__dark on 2006-02-08
[Download The Latest Driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.21.7-i386.run")

Remove the old driver:

```
sudo apt-get remove fglrx-kernel-$(uname -r)
```

Then Follow this tutorial EXACTLY (including reboots):

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

