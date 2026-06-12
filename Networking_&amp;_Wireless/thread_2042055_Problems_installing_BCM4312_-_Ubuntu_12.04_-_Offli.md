---
title: "Problems installing BCM4312 - Ubuntu 12.04 - Offline"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by carmonalucas on 2012-08-13
Hi, I'm sorry for my poor english, hope you understand me.

I'm trying to install de Broadcom BCM4312 802.11b/g and i'm following some steps from a forum. 

This forum tell me to do something like this:

[B]The driver to install is for Broadcom (BCM4306/3- BCM4311- BCM4312- BCM4318).
-The necessary files are:

b43-fwcutter_i386.deb
wl_apsta-3.130.20.0.o
broadcom-wl-4.150.10.5.tar.bz2

It should have all these files in a folder, and therefore there must be positioned from the terminal in the same folder.

-start installing the deb packet..  There are two ways: via terminal or manually (double click "b43-fwcutter_i386.deb"), we will see via terminal:

$ sudo dpkg -i b43-fwcutter_i386.deb

-Now extract and install the drivers:

$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
(or manually with the right click and click extract here)

$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
-------[/B]
I have the three files and I'm positioned on the same folder in the terminal. But I do the first command and it throw me an error like "dpkg: error processing b43-fwcutter_i386.deb".
So I try to do it manually, double click on  b43-fwcutter_i386.deb and at the ubuntu software center appears this:
**"please install "b43-fwcutter" via your normal software channels. Only install this file if you trust the origin."**
and i can't install it offline..
So, I couldn't install the drivers.

Hope you can help me. Thanks you so much.

**Lucas**

---

### Post by Bucky Ball on 2012-08-13
You need b43-fwcutter and firmware-b43-installer. Both in the repos. Install. 

As for your other .deb files, just install them by double clicking, disregard that warning. 

Can you plug an ethernet cable in? If so, you probably don't need to do any of this. Plug in a cable, get updates, check 'Additional Drivers'.

---

### Post by Toz on 2012-08-13
@carmonalucas,
Please don't create duplicate posts for the same issue. Creating a new thread such as this one is sufficient to have your issue addressed. I have removed the other post.

---

