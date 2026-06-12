---
title: "I messed up my webcam drivers"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Veratyr9 on 2009-02-20
Ok so this webcame (quickcam... something, no more than 2 years old, clamps onto an lcd panel, nothin special) workd just fine with the default drivers in 8.10.

I tried to get a different camera working (quickcam pro, 1999 vintage).  and i stupidly followed the 4 year old guide at [http://ubuntuforums.org/showthread.php?t=53755](http://ubuntuforums.org/showthread.php?t=53755) and installed qc-usb.  It didnt work, and i just went back to the camera that did work.... except now those drivers are trying to function for the new camera, and screwing everything up.

How do I get this junk off of here?

here is the output from lsmod while the camera is in use (it just gives off a bunch of green static and lines):
```

rip@odin:~$ lsmod | grep video
videodev               41344  2 gspca_main
v4l1_compat            22404  1 videodev
video                  25232  0 
output                 11008  1 video
```

and lsusb:
```
rip@odin:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c012 Logitech, Inc. Mouseman Dual Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

any ideas?

---

