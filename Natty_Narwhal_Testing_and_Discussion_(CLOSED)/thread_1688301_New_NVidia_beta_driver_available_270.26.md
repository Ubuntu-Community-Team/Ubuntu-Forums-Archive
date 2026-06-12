---
title: "New NVidia beta driver available 270.26"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-15
Now there is a new NVidia beta driver available (270.26).
You can download deb packages from the X Updates PPA (Ubuntu X).

The changelog does not say anything about xserver 1.10 support.
This means it is highly likely there is no such support.

Changelog:
```
   New upstream beta release. Changes:
   - Added NV-CONTROL event notification for
     NV_CTRL_FRAMELOCK_SYNC_READY
     status changes.
   - Added support for the following GPUs:
     GeForce GTX 560 Ti
   - Added a new X configuration option "Interactive", which defaults to
     enabled, but can be disabled to allow long-running GPU compute programs
     to run concurrently with X.
   - Fixed a bug in the VDPAU presentation queue that could cause VDPAU
     "display preemption" when rendering to tiny or zero-sized windows or
     pixmaps.
   - Fixed a bug in VDPAU which prevented use of the overlay presentation
     queue following an application exiting without gracefully destroying its
     VDPAU presentation queue.

```

---

### Post by ronacc on 2011-02-15
I just checked the nvidia downloads page and it does not show that driver , the latest (beta or release) is 270.18

---

### Post by VMC on 2011-02-15
> **ronacc said:**
> I just checked the nvidia downloads page and it does not show that driver , the latest (beta or release) is 270.18

Here's a [_**link**_]("http://www.nvnews.net/vbulletin/showthread.php?t=159683") that shows more info, but yes nothing that we can use for Unity.

---

### Post by Yofel on 2011-02-15
Just noting that 270.26 indeed doesn't work with natty either. So the changelog is right.

Backtrace:
[    54.146] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a1586]
[    54.147] 1: /usr/bin/X (0x400000+0x6078a) [0x46078a]
[    54.147] 2: /lib/libpthread.so.0 (0x7fa35a769000+0xfc80) [0x7fa35a778c80]
[    54.147] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa354ece000+0x41ddc0) [0x7fa3552ebdc0]
[    54.147] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa354ece000+0x428a4a) [0x7fa3552f6a4a]
[    54.147] 5: /usr/bin/X (AddScreen+0x1a8) [0x42dde8]
[    54.147] 6: /usr/bin/X (InitOutput+0x294) [0x46e5b4]
[    54.147] 7: /usr/bin/X (0x400000+0x21903) [0x421903]
[    54.147] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fa3596d2d1e]
[    54.147] 9: /usr/bin/X (0x400000+0x21669) [0x421669]
[    54.147] Segmentation fault at address 0x18

---

### Post by Richard on 2011-02-15
Hello,

Yes, no support for Xorg 1.10 in this beta.
I keep Xorg 1.9 to get Unity/Compiz working.

---

### Post by Harry33 on 2011-02-15
> **Yofel said:**
> Just noting that 270.26 indeed doesn't work with natty either. So the changelog is right.

Backtrace:
[    54.146] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a1586]
[    54.147] 1: /usr/bin/X (0x400000+0x6078a) [0x46078a]
[    54.147] 2: /lib/libpthread.so.0 (0x7fa35a769000+0xfc80) [0x7fa35a778c80]
[    54.147] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa354ece000+0x41ddc0) [0x7fa3552ebdc0]
[    54.147] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa354ece000+0x428a4a) [0x7fa3552f6a4a]
[    54.147] 5: /usr/bin/X (AddScreen+0x1a8) [0x42dde8]
[    54.147] 6: /usr/bin/X (InitOutput+0x294) [0x46e5b4]
[    54.147] 7: /usr/bin/X (0x400000+0x21903) [0x421903]
[    54.147] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fa3596d2d1e]
[    54.147] 9: /usr/bin/X (0x400000+0x21669) [0x421669]
[    54.147] Segmentation fault at address 0x18

Just to be accurate, Nvidia 270.26 works very well with Natty.
But, you have to use the older xserver 1.9 series
It is xserver 1.10 that it does not work with.

---

### Post by VMC on 2011-02-15
> **Harry33 said:**
> Just to be accurate, Nvidia 270.26 works very well with Natty.
But, you have to use the older xserver 1.9 series
It is xserver 1.10 that it does not work with.

So does previous versions of Nvidia drivers. We need a Nvidia driver that works with 1.10. Wait for the future I suppose.

---

