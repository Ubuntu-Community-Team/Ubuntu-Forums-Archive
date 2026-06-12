---
title: "Wireless card/usb that works with Ubuntu?"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Cam42 on 2009-07-04
I just built my Grandma a new computer, with Ubuntu installed. the problem is, that her wireless USB deal will not work. Anyone know if there are any card (PCI or USB) that will work with Ubuntu?

---

### Post by riccardo on 2009-07-05
Hi there,

I use Xubuntu 9.04... on this laptop and the usb dongle I have borrowed just works!  It is an eBay special ... which I think Ibought from China direct.  On the outside is the brandname "Sagem" and the model "XG 760A"... and the identification from lsusb command is:

lsusb
Bus 003 Device 002: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 15d9:0a37  
Bus 002 Device 003: ID 079b:004a Sagem XG-760A
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Where my device is bus 002  device  003.

PLease let me know if you want more information.

riccardo

---

### Post by desnaike on 2009-07-05
I purchased an Edimax ew7727In pci adapter from newegg works with jaunty.mandriva,linuxmint7,opensuse11/11.1 out of the box.

---

