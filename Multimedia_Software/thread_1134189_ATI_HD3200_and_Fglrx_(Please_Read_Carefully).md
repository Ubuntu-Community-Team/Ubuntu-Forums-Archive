---
title: "ATI HD3200 and Fglrx (Please Read Carefully)"
date: 2009-04-23
forum: Multimedia Software
---

### Post by coldReactive on 2009-04-23
Okay, so I did the following...
> **BubuXP said:**
> From this thread:
[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)


I have same GPU as your and all is working fine in Jaunty with fglrx.


How I resolved:

Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here

BUT, xorg-driver-fglrx is already installed by default! How can I install something that I already have installed?!

[img]http://i42.tinypic.com/ffcy9e.png[/img]

The Fglrx won't activate in hardware drivers dialog because jockey-backend crashes every single time.

---

### Post by coldReactive on 2009-04-23
Somehow, it fixed itself, and asked me to reboot.

---

