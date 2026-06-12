---
title: "Skype dumps No suitable overlay format found"
date: 2009-07-07
forum: Multimedia Software
---

### Post by checho4 on 2009-07-07
I'm running Kubuntu 9.04 32-bit and have installed Skype via the Medibuntu repositories.  When running earlier versions of Kubuntu, my Logitech webcam worked just fine (unsure of the exact model).  However, 9.04 doesn't seem to work with my webcam.

I have searched around for 2 days and have finally gotten it to work with Cheese using the command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

Attempting to run Skype with that command is futile.

Here's some of the pertinent info:

```
$ lsusb
Bus 001 Device 007: ID 046d:09a1 Logitech, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

When attempting to test the camera in Skype:
```
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 79
Skype Xv: No suitable overlay format found
```

I've googled around but couldn't find much info about the "No suitable overlay format found" error.

Any help would be GREATLY appreciated.

---

