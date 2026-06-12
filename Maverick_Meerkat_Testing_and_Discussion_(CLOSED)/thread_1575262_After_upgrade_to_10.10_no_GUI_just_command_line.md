---
title: "After upgrade to 10.10 no GUI just command line"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Detosx on 2010-09-15
I upgraded from 10.04 to 10.10. On reboot I found grub needed to be reinstalled, found a Youtube tutorial for reinstalling grub2 from the 10.04 live CD, no problem. I then found that rather than booting to the login screen I just got command line. I logged in from there and found... still command line, no GUI. I read somewhere about problems with the Catalyst driver for ATI graphics cards and I tried various commands from various forums to remove it but it wasn't found. I then removed the graphics card, hoping the motherboards GMA950 would work but no; I think the problem is I am using 64bit which I don't think the old GMA950 would recognise. I'm sorry to be vague, at this point, but I am away from that computer at the moment. What to try next? Any suggestions welcome!

---

### Post by dannyboy79 on 2010-09-15
this is a very common solution to no GUI but have you tried logging into command line. then issuing

sudo service stop gdm
startx

if that fails, it should at least show you whether you have a problem with your gnome desktop, a graphics driver issue or what. Have you tried using vesa to at least get into a GUI so can more easily troubleshoot if you so desire. good luck

---

### Post by jfernyhough on 2010-09-15
You will need to remove your old xorg.conf:

$ sudo rm /etc/X11/xorg.conf

then reboot.

---

### Post by mik9dt on 2010-09-15
> **jfernyhough said:**
> You will need to remove your old xorg.conf:

$ sudo rm /etc/X11/xorg.conf

then reboot.

This fixed things for me, thanks a lot for the heads up!

---

### Post by Detosx on 2010-09-15
> **jfernyhough said:**
> You will need to remove your old xorg.conf:

$ sudo rm /etc/X11/xorg.conf

then reboot.Thanks for the suggestions! I got 'cannot remove /etc/X11/xorg.conf, no such file or directory'.

In Recovery Mode, in safe graphics mode I get 'fault at address (nil) 
Caught signal 11
Segmentation fault

---

### Post by Detosx on 2010-09-15
From here - [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) - I tried 

sudo apt-get remove --purge fglrx 

then was able to use recovery mode to boot into Safe Graphics Mode. Mighty relieved!

---

