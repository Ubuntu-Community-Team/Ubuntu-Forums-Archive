---
title: "Video Card drivers"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by bjb.butler on 2007-08-04
ok i got feisty installed, all thats left are the nvidia drivers. 

i have an nvidia EN8500GT video card.  i tried installing the nvidia drivers that are in automatix, but they didn't work, it crashed my X server. does anyone know which drivers i should be using?

thanks, bj

---

### Post by ulpiano on 2007-08-05
Can you post your xorg.conf and the packages you have installed? It woluld be very useful.

---

### Post by cherryjello on 2007-08-07
This driver: 
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)

Worked for me on my vanilla install of feisty.

The only strange thing I've noticed is that my X sometimes won't start-up automatically and I'll have to reinstall the drivers and start X manually.  Otherwise working great in twin-view mode.

HTH.

---

