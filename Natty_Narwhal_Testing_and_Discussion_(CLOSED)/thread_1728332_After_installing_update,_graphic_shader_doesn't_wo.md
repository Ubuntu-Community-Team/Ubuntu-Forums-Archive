---
title: "After installing update, graphic shader doesn't work"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by landon418 on 2011-04-13
I have had to reinstall ubuntu 3 times! Here is the screenshot [http://img203.imageshack.us/i/screenshotnk.png/](http://img203.imageshack.us/i/screenshotnk.png/) When I go to restricted drivers, only the nvidia 3d driver is there, not the proprietary driver. I am now scared to update :(

---

### Post by cariboo on 2011-04-13
What graphics card does your system have?

---

### Post by landon418 on 2011-04-16
I have a NVIDIA 5 FX 5500, yes i know it is old :p

---

### Post by landon418 on 2011-04-16
bump help asap :cry:

---

### Post by Harry33 on 2011-04-16
Nvidia graphics driver version 173.14.28 (released on 2010.10.18 ) supports FX 5500 series cards.

So install manually (with Synaptic) these package (in Natty repos):
nvidia-glx_173.14.28-0ubuntu6
nvidia-settings

---

### Post by landon418 on 2011-04-16
said error
nvidia-glx-173:
Depends: nvidia-173 but it is not going to be installed

when i tried to install nvidia-173 it was going to remove my gnome desktop and a bunch of xorg stuff! I did this before and it messed up my computer. Monitor quit working

---

