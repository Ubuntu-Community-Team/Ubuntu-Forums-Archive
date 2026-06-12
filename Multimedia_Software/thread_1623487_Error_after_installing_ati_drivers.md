---
title: "Error after installing ati drivers"
date: 2010-11-16
forum: Multimedia Software
---

### Post by davidtuti on 2010-11-16
Hi,

Recently I've installed Kubuntu 10.10 and after install it, I've installed ati drivers ati driver 10.10.
Everything is ok but after install the drivers and reboot, I try to execute CCC with amdcccle and it says me:

XIO:  fatal IO error 11 (Recurso temporalmente no disponible) on X server ""
      after 785 requests (784 known processed) with 0 events remaining.


Could you help me please?
Many thanks and sorry for my english!

---

### Post by Yellow Pasque on 2010-11-16
Remove the driver: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then, do a clean install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

WARNING - KDE 4.5.x desktop effects/compositing (KWin) does not work well with Catalyst if you use the OpenGL renderer.

---

