---
title: "spca5xx make fails"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by jal on 2007-07-21
I wish to use a Logitech STX webcam, but the device is not being recognized. (I have included the dmesg below.) 
I thought the problem might be with the kernel module and have been trying to make a new version of spca5xx (and gspa5xx), using the (excelllent) guide at:
[https://help.ubuntu.com/community/Spca5xx?highlight=%28spca%29#head-abbf3775f296403b5ef82254395b8e15e75d4150]("https://help.ubuntu.com/community/Spca5xx?highlight=%28spca%29#head-abbf3775f296403b5ef82254395b8e15e75d4150")

but the make command returns:
```

root@acknak:/usr/src/spca5xx-v4l1goodbye# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/spca5xx-v4l1goodbye CC=gcc-3.4 modules
make[1]: Entering directory `/lib/modules/2.6.15-28-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-28-386/build'
make: *** [default] Error 2


```
Dapper ( 2.6.15-28-386) was installed from the CD and updated via internet updates and synaptic so I have never compiled/made from source before. This meant that I needed to do:
```
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4 
``` 

What else am I missing?
  
I would also appreciate any advice or guidance in regard a fix for the real problem  as I'm not entirely certain that I'm on the right road.

dmesg shows 
```
[15522.176627] usbcore: deregistering driver spca5xx
[15522.178270] drivers/usb/media/spca5xx/spca5xx-main.c: driver spca5xx deregist ered
[15553.424961] Linux video capture interface: v1.00
[15553.564656] usbcore: registered new driver spca5xx
[15553.564925] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08  registered

```
and when I plug in the camera,
```

[15649.974548] usb 1-2: new full speed USB device using uhci_hcd and address 7

```

no /dev/video*  are created, and camorama can't see any devices.

---

### Post by jal on 2007-07-22
build is working now. 
Modified the Makefile::

```

40,41c40
< #KERNELDIR := /lib/modules/$(KERNEL_VERSION)/build
< KERNELDIR := /usr/src/linux-headers-$(KERNEL_VERSION)
---
> KERNELDIR := /lib/modules/$(KERNEL_VERSION)/build

```

---

### Post by jal on 2007-07-22
sorted!
made a new spca5xx, but this module still didn't see the camera.
I then built gspca, using 
gspca_build
The build had same problems as spca5xx, 
needing the KERNELDIR to point to the Makefile in linux-header-`uname -r`
plus it wouldn't run, error message was
```
FATAL you need to install the Kernel Source for your running kernel
```
which I got around by manually executing the steps within the script. 

and the camera was working!

now camorama crashes when certain mirror image or laplace are selected, but that problem is for another day.

---

