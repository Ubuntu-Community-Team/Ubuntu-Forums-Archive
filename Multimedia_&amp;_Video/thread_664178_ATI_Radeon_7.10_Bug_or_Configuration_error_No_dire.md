---
title: "ATI Radeon 7.10 Bug or Configuration error? No direct render"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by transporter_ii on 2008-01-10
Posted on this before, but got no help. I'm going to try and keep it simple this time. I really just want to know if this is even possible to do or if I'm wasting my time.

 I have two Ubuntu systems. A 6.06 and a 7.10. The 6.06 system has an ATI Radeon 7000 in it. It works very well...so well I ordered one for my 7.10 system because I thought for sure it would work in Linux (same model but dual head, and brand new out of the box). The new, but basically identical card will not "direct render" in 7.10.

Here is a breakdown of differences between 6.06 and 7.10:

Working 6.06:

xorg.conf  - driver = "ati"
direct rendering: yes
Opengl version string: 1.2 (Mesa 6.4.1)
OpenGL vendor string: Tungsten Graphics, Inc.

Not working 7.10:

xorg.conf  - driver = "ati"
direct rendering: No 
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL vendor string:  Mesa project: [www.mesa3d.org](www.mesa3d.org)

I have configured the xorg.conf file very similar between the two boards. 

What I would like to know is, is there actually a bug introduced between 6.06 vs 7.10, OpenGL 1.2 vs 1.4, or Tungsten Graphics vs mesa3d.org, or did I just configure something wrong, because I'd rather not be spending any more time on something that is just impossible to do.

I would almost like to try formating 7.10 and installing 6.06 to find out for sure, but 7.10 has some SATA drivers that I need.

Transporter_ii

---

### Post by transporter_ii on 2008-01-13
Well, I have spent almost a week on this now, for a 30.00 card, but I can most certainly say there is a bug in the ATI driver between 6.06 LTS and 7.10. Just to test this, I installed 6.06 on my system on a slave IDE drive. It took me a day or so of editing the xorg.conf file, but I have direct rendering enabled and games like X-moto work out of 6.06 LTS (my only complaint is that it is a little dark, but otherwise fine).

Keep in mind, this is the exact same system, same video card and everything, just two version of Ubuntu. And I have tried using the exact same xorg.conf file between 6.06 and 7.10, too. Result, direct rendering in 6.06 but not in 7.10.

This seems to be the problem between the two versions of Ubuntu:

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "radeon"
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.

-=-=-=-=

from 6.06 LTS

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:04.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:04:04.0
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.24.0



I have read hundreds of posts on the Internet about this bug, as it seems tons of people have it, but I have yet to see a real solution.

Transporter_ii

---

### Post by fiatguy85 on 2008-03-08
I was having this problem in Gutsy, and found that the fglrx kernel module had to be removed to stop giving me that exact error.  So if you have tried the proprietary driver at somepoint try removing the kernel module:

sudo modprobe -r fglrx
sudo depmod

---

