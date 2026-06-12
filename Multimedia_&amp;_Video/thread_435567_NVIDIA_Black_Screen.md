---
title: "NVIDIA Black Screen"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Soad123 on 2007-05-07
Have just installed the NVIDIA driver using ENVY and it asked me to reboot now all I get is a black screen

---

### Post by Nythain on 2007-05-07
hit control+alt+f1 to go to a console login... then type /etc/init.d/gdm start or startx and tell us what it says... could be as simple as a driver module/kernel mismatch, or a line could be wrong in your xorg.conf

---

### Post by dajhorn on 2007-05-10
There is a regression in Ubuntu Feisty that causes the screen to go black on many laptops that are using the closed nvidia drivers.  Check the bug reports for the nvidia-glx package for details.

The kludge is to change

  Driver "nvidia"

to

  Driver "nv"

in the /etc/X11/xorg.conf file, or use the upstream driver package.

---

