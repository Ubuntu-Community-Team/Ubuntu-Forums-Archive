---
title: "Trouble getting cheap RTL8192CU USB wifi to work with 10.04"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by H4T on 2013-06-03
I grabbed a cheap USB wifi dongle from Amazon ([http://www.amazon.com/gp/product/B004HYHZJY/ref=oh_details_o03_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B004HYHZJY/ref=oh_details_o03_s00_i00?ie=UTF8&psc=1)) and have been trying to get it to work with a fresh Ubuntu 10.04 installation with no luck.

When I go to the wireless network icon at the top right of the screen, I see no wireless networks listed (even though I'm connected to one on m Windows laptop to write this post). 

My Linux skills are minimal, I really don't know how to troubleshoot this issue. Where do I start?

---

### Post by praseodym on 2013-06-03
Hi,

you know that Ubuntu 10.04 desktop edition is outdated? I recommend installing 12.04.

The driver can be updated according to this (for 10.04 if you want to try it, not working with 12.04!):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/33/30/2844083-rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 

```
Reboot and check:
```

lsmod
iwconfig
sudo iwlist scan
```

---

### Post by H4T on 2013-06-03
I'm using LinuxCNC, which is based on 10.04. Fraid I have no choice in the matter :P

Ah, so I need to get an active internet connection to install the drivers, correct? I'll need to haul it back home to do that, haha. It's sitting in a room with no wired connections available.

---

### Post by praseodym on 2013-06-03
Yes, you should have a wired connection for the installation.

---

