---
title: "problem with ati rage 3d II card"
date: 2008-11-26
forum: Multimedia Software
---

### Post by 123456789123456789123456 on 2008-11-26
My friend is running xubuntu 8.04, not connected to internet at the moment.  He has a built in video card on his motherboard, running with an amd processor, the video card he tells me is a ati rage 3d II with dvd support.  xubuntu is using the default vga driver, and is not allowing full graphical support, as such as resolution, and so forth.  Is there a way to get xubuntu to use the free ati driver for that card?

---

### Post by gabril on 2008-12-04
There is! but he is in need of an internet connection! 

the command is:

$ sudo aptitude install xserver-xorg-driver-ati

then edit the xorg.conf file so that under device there is a ""Driver"    "ati""

---

