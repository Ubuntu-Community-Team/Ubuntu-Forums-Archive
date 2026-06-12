---
title: "3D is okay, but dragging window is sluggish."
date: 2009-09-09
forum: Multimedia Software
---

### Post by nikeairj on 2009-09-09
I have a GeForce2 MX 400 PCI video card installed in my machine. I used the Hardware Drivers to install the video driver for me. It installed the nvidia version 96 driver. I can play OpenGL games (tested with SuperTux with OpenGL checked and getting around 80 fps). Firefox page scrolling works great. Windows resizing could be better. When I have my desktop on top and if I try to make a selection rectangle from corner to corner, it's real slow and sluggish. If I move the window around, the movement is also sluggish. If I ALT+TAB to a different window, it chokes a bit before redrawing the window. It also chokes for about 2-3 seconds when I switch to a different desktop view. Scrolling in VIM is horrible, too. When I had GeForce 6600GT AGP card, everything was working just fine.

I have 2.5 GB RAM, AMD Athlon XP 2500+, 120GB HDD, and a motherboard with nforce2 chipset. 

I'm not sure how to fix this. I tried searching for a solution, but I haven't gotten any luck. I hope someone out there knows how to fix this. Thanks in advance, guys!

---

### Post by nikeairj on 2009-09-11
Hate to do this, but... bump.

---

### Post by dernob on 2009-09-12
The 96 driver from nvidia (which is suitable for your MX card) is from a time where there was not so much accelerated drawing techniques. If you have compiz working disable it. 

You should also try the 2D-only open-source "nv" driver.

The 6600 uses the much newer 180 driver, thats why you didn't had any problems with it.

---

