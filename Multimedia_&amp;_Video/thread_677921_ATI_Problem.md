---
title: "ATI Problem"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Strike_105x on 2008-01-25
My system is videoboard: ATI 9600 XT motherboard: Asus K8V-X-SE S-754, 1GB DDR 400, 80 GB SATA Maxtor Hdd, IDE 40 FB seagate HDD
My problem is i tried to install drivers for ati drivers like this (enabled restricted drivers) the commands i righted in the terminal:

sudo apt-get update     
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

after that i righted sudo aticonfig --initial it looked like it worked (i think)
and after that: sudo aticonfig --overlay-type=Xv -here i got an error because of this i tried:

kdesu kate /etc/X11/xorg.conf

but the file was blank actually it doesent exist in the etc/X11/ dir there is no xorg.conf 

can someone pls tell me what am i supose to do ?

---

### Post by acoustibop on 2008-01-25
After installing the driver, you need to reboot before doing sudo aticonfig --initial, Strike_105x.

The previous /etc/X11/xorg.conf should be in the X11 folder with the name xorg.conf.fglrx-0.

---

### Post by Yellow Pasque on 2008-01-25
Hi Strike_105x.
Use this to recreate your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```
If you uninstalled the driver, reinstall as you did, except this time, run:
```
sudo aticonfig --initial -f --overlay-type=Xv
```

---

