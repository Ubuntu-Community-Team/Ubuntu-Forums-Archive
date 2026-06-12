---
title: "Proxim B11FNF-USB"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by gsk3 on 2009-04-10
Hi everyone,
  I've got a Proxim 802.11 USB card that I need to get working.  This is an Athlon 64 box running 32-bit Desktop Intrepid.  

**lsusb -v** shows it as:
Bus 001 Device 004: ID 0bb2:0304 Ambit Microsystems Corp

ifconfig only shows eth0 (the wired port built into the motherboard), and iwconfig shows:
lo     no wireless extensions.
eth0     no wireless extensions.
pan0     no wireless extensions.

From some Googling (which returned sadly little), it appears that this card will work with the **prism_usb** driver.  However, **lsmod** and **dmesg** turn up nothing useful in that department.  **find / -name prism_usb*** also turns up nothing, despite the kernel config file that Ubutnu seems to have used (/boot/config-2.6.27-11-generic) seeming to have Prism support turned on (not sure if it's USB-specific or not).

**lshw -C network** returns:
*-network DISABLED
description:Ethernet interface
physical id:1
logical name: pan0
capabilities ethernet physical

Is prism_usb the right one?  If so, how do I go about finding where the package was installed to (if even a package was installed by default)?  If there's no package installed by default, is there a package to be downloaded, or must I go find the code somewhere and install it from scratch.

Sorry about the questions, and thanks in advance.

---

### Post by gsk3 on 2009-04-10
Update with a slightly stupider question:
It turns out the driver I should have been looking for was prism2_usb.  I have loaded that:
**modprobe prism2_usb**
prism2usb_init: prism2usb.o: 0.2.9 Loaded
prism2usb_init: devinfo is: prism2usb
usbcore: registered new interface driver prism2_usb

But still no dice with **ifconfig**.  I tried adding it to /etc/modules and restarting, also to no avail.

**lsmod | grep -e "prism2_usb"**
Module          Size     Used_By
prism2_usb     80260     0
p80211         38536     1 prism2_usb
usbcore       149360    10 prism2_usb,[....]

ifconfig, iwconfig, and lshc return the same as before.

Thanks for any help you can give!

---

