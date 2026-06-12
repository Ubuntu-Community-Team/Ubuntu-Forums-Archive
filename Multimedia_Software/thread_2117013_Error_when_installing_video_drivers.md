---
title: "Error when installing video drivers"
date: 2013-02-17
forum: Multimedia Software
---

### Post by lamero on 2013-02-17
When i try to install the driver "ati-driver-installer-9-3-x86.x86_64.run" in the terminal with: 
sh /path/ati-driver-installer-9-3-x86.x86_64.run i get that error: 
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.5.0-23-generic; make sure that the version is being
correctly set by --iscurrentdistro

PS. by path i mean the path to the file :)

---

### Post by Bucky Ball on 2013-02-17
*Thread moved to **Multimedia & Video**.*

---

### Post by Mark Phelps on 2013-02-17
Do you know for certain that your video chipset and Ubuntu version will work with this version of the drivers?

What Ubuntu version are you running?

What AMD video chipset version are you using?

---

### Post by lamero on 2013-02-17
I'm using ubuntu 12.10. The video is ATI radeon 9600 family and i have downloaded the drivers from AMD site that are for ubuntu but i have no idea if they will work together. I tried to find for what version of ubuntu are the drivers but i couldn't find that.

ps. Sorry for my poor english and thnx for moving my topic in the right section.

---

### Post by Yellow Pasque on 2013-02-17
Catalyst 9-3 will not work with Ubuntu >= 9.04

The open-source radeon driver is installed by default.

---

