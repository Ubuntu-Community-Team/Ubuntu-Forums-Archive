---
title: "NVIDIA GEForce 6200 LE"
date: 2013-01-17
forum: Multimedia Software
---

### Post by jim1112 on 2013-01-17
I have a MSI motherboard with unichrome graphics chip. I am running Ubuntu 12.04. If recently installed a NVIDIA GEForce 6200 LE graphics card. I have installed drivers from geforce website, undated headers and updated grub. When I boot with monitor connected to NVIDIA card I get the "black screen." All I can do is shut the computer down and startup with the monitor connected the the unichrome graphics which now only has 640x480 since the upgrade. I'm not really sure what step to take next. Any suggestions would certainly be welcome. Thanks, Jim

---

### Post by ManamiVixen on 2013-01-17
As far as I'm aware of, the oldest Nvidia video card Ubuntu 12.04 supports is the 8400. Need to upgrade. Also check to see if your bios is set to use the card and not onboard. :)

---

### Post by jim1112 on 2013-01-18
Thanks!!! The video card is now working!! Only have 640x480 resolution, but I'll update grub and see where that gets me. Thanks again, Jim

---

### Post by ManamiVixen on 2013-01-18
Here's something! Looks like a patched driver was released for 12.04 Take a look.
[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

