---
title: "lost video drivers after update can't restore X"
date: 2009-03-11
forum: Multimedia Software
---

### Post by imneal on 2009-03-11
Hello, 

I had everything running smoothly with the default restricted driver for my ASUS M3N78 motherboard Nvidia GeForce 8300 on board video.  However, the flash was running funky, so I decided to install the driver that was posted on NVidia's website.  After which ubuntu loaded, but the screen was blank.   I tried the "fix X server" command in recovery mode and it didn't work, so I loaded ubuntu normally and got into the root terminal with Alt+F1  and  tried "sudo dpkg-reconfigure -phigh xserver-xorg"  to no avail.

I also tried to copy my xorg.conf.backup to xorg.conf, and that didn't work.  

How can I restore the default video drivers in ubuntu from the root terminal? All I need is some video.  

Thanks, 

Neal

---

