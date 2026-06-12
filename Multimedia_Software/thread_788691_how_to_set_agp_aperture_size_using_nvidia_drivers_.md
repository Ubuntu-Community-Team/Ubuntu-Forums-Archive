---
title: "how to set agp aperture size using nvidia drivers on Ubuntu 8.04 64-bit"
date: 2008-05-10
forum: Multimedia Software
---

### Post by linuxed on 2008-05-10
Each time I boot the following is displayed in my log files.

[   14.011806] Checking aperture...
[   14.011808] CPU 0: aperture @ 61e4000000 size 32 MB
[   14.011810] Aperture too small (32 MB)
[   14.017878] No AGP bridge found
[   14.038132] Memory: 1278712k/1309568k available (2466k kernel code, 30452k reserved, 1309k data, 316k init)

The following is displayed in my 'Nvidia X Server Settings' window.

[http://img151.imageshack.us/my.php?image=nvidiars9.png](http://img151.imageshack.us/my.php?image=nvidiars9.png)

I've manually set the framebuffer size in my bios to 256mb.  The video card is integrated into the motherboard so it shares memory with the ram, but I have plenty of memory installed to be able to allocate 256mb for the video card.  The Nvidia Settings window detects 512mb of video memory which is incorrect.  My logs say that the aperture size is 32mb.  I've tried adding the 'Option' 'VideoRam' '262144' setting to my /etc/X11/xorg.conf file which didn't help.  Any ideas how I can manually configure the aperture size or frame buffer?

---

### Post by linuxed on 2008-05-10
When I open the 'Screen and Graphics' window the Video Memory box is grayed out.  How can I manually specify the video memory while using the nvidia drivers?

[http://img373.imageshack.us/my.php?image=screenprefsen7.png](http://img373.imageshack.us/my.php?image=screenprefsen7.png)

---

