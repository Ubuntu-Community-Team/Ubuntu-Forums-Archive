---
title: "Minecraft low performance"
date: 2011-06-11
forum: Multimedia Software
---

### Post by PohyCZek on 2011-06-11
Hello,

i've downloaded minecraft and wanted to play it on Ubuntu 11.04, but performance is really bad. I'm getting about 1-5FPS.
On Windows game run just fine. I think it's issue of GPU driver. I tried to install the fglrx driver from synaptic, but when i rebooted unity said that i don't have 3D acceleration so i didn't even tried to run Minecraft. I also downloaded driver from AMD website, but when i tried to install it through terminal it said this: 
> root@IRIS:/home/david/Downloads# sh ati-driver-installer-9-3-x86.x86_64.run 
Created directory fglrx-install.qvkxsj
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.qvkxsj


So, can you help me with this please?

My hardware is:
Pentium 4 @ 3.4Ghz
ATI Radeon x1650 AGP 256MB VRAM
1.5GB RAM

---

### Post by RaumTrug on 2011-06-11
look here, it explains: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

you've got a very old ati-driver version, but it won't support the kernel and x-server that comes with ubuntu 11.04. you'd have to either use a way old version of ubuntu (in link above it's said 8.04 works o.k.), or stay with the default driver (you've already noticed its performance isn't quite as good as the ati driver...but maybe there's another problem somewhere...have you tested other 3d progs?), or get a new gfx-card.

---

