---
title: "[SOLVED] Color hue xvideo nvidia driver 8.10 x64"
date: 2008-12-06
forum: Multimedia Software
---

### Post by ozfinngeek on 2008-12-06
Hi,
I have an issue with the Xvideo colors via the restricted Nvidea drivers. All the colors are mapped wrong ie red is blue, but only in Xvideo. If I use the non-restricted driver, all the colors are fine, but I cannot run the TV streaming software. Bit of an issue for the main multimedia system.
Changing the Hue slider from 0 to 180 in the Nvidia Xserver gui does not seem to change the video output in any way and it just defaults back to 0 if I restart Xserver anyway. All video file types are affected. I have the same effect with both the 173 and 177 drivers.

I am currently using:
Ubuntu 8.10 x64
Nvidia 8600GT
MEA 1998FD CRT

Players tried:
Totem - gstreamer
Totem - Xine
VLC

Xserver config
Res: 1280*1024 @ 85hz
Driver: 177.80 Nvidia Restricted
Server version number: 11.0
Vendor Version number: 1.5.2 (10502000)
NV-Control Version: 1.17

I defaulted my xorg.conf when I upgraded from 8.04 to 8.10 so there is not much point in posting the file contents.

Does anyone know how I can fix this, thanks.

---

### Post by ozfinngeek on 2008-12-08
I have found the Solution in a bug report which basically says that the Totem Display settings are the global control and need to be set to 0.

See: [https://bugs.launchpad.net/debian/+source/linux-restricted-modules-2.6.24/+bug/184440](https://bugs.launchpad.net/debian/+source/linux-restricted-modules-2.6.24/+bug/184440)

Thanks to all.

As I am unsure how, please mark as solved.

---

