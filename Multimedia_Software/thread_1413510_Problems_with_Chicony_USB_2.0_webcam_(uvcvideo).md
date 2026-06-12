---
title: "Problems with Chicony USB 2.0 webcam (uvcvideo)"
date: 2010-02-22
forum: Multimedia Software
---

### Post by kalaka on 2010-02-22
Hey guys, I've been having problems with my integrated USB webcam for a while now and I was wondering if there's any way I could fix it.


It usually works OK (for about 30 seconds) but then the image either gets filled with green lines and static (see screenshot), or it goes completely black.
```

lsusb | grep Cam
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
```

When I reboot, sometimes it works again (for a few seconds).

I've tried unloading it and reloading it from the kernel modules but nothing changes. When I use the -f (force) command, I get this error:
```
sudo modprobe -i uvcvideo -f
WARNING: Error inserting videodev (/lib/modules/2.6.32-13-generic/kernel/drivers/media/video/videodev.ko): Invalid module format
FATAL: Error inserting uvcvideo (/lib/modules/2.6.32-13-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Invalid module format

```

Any help or comments would be very much appreciated.
Thanks in advance!!

---

### Post by kalaka on 2010-03-28
Bump.

Sorry, does anybody know how I can get my camera working?

---

