---
title: "Marvell 88e8056 - sky2 and sk98lin doesn't work."
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by jarecki0909 on 2010-11-07
Hi I'm new on this forum and new user of UBUNTU.
 
I've got problem with Marvell 88e8056 ethernet card integrated on motherboard of Lenovo M57p (9018-CTO) station.

My kernel - 2.6.32 - customised for Marvell modules now. Distro Lucid Lynx 10.04.
My card isn't working at all on standard system module "sky2", but also on "sk98lin" - dowloaded from Marvell support - 2.6.-Fedora.

Tried to fix by merging module sk98lin in kernel, and setting as external module didn't work either.
 
Now it's marked as external module - sky2 and skge also.

Strange thing now is :

standard "modprobe sk98lin" doesn't change anything card still invisible...but after I choose "install" option on "install.sh" script of driver "modprobe sk98lin" does exist as "eth0" device of my system ( I haven't tried if it actually work ... but it is visible and that is a progress )...cool ... but after restart everything back to normal - after "modprobe sk98lin" card is still invisible till next "install" on "install.sh" script.
Any tip to get it working ?? Please help I haven't got a clue how to fix it.
 
Thank you in advance.

---

### Post by mathia on 2011-03-30
Hi,
 
 **[B]Installing Marvell Yukon driver on Ubuntu**:[/B]
 
 Please install the following driver as follows:
 [http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "e.g. 88E8056 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - v10.87.3.3
 
  $ sudo bash ./install.sh
 
 and let me know if it works.
 
 Have a lot of fun ...:razz:

---

