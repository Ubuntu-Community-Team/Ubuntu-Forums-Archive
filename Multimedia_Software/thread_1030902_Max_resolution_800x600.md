---
title: "Max resolution 800x600"
date: 2009-01-04
forum: Multimedia Software
---

### Post by jchando on 2009-01-04
I have been looking over several of the forums where this seems to be a common question and have tried most of the sugestions without any luck getting the resolution to the monitors' 1024x768 limit
I have tried editing xorg.conf and running xrandr command and neither has worked
any sugestions

Ubuntu 8.10 on a 500Mhz P3 
Video card - Creative Labs CT6700
Monitor - NEC MultiSync LCD 1530v

---

### Post by wolfen69 on 2009-01-04
try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot.

---

### Post by jchando on 2009-01-05
Ran the command and it reset the xorg.conf file, still limited to 800x600 resolution

---

