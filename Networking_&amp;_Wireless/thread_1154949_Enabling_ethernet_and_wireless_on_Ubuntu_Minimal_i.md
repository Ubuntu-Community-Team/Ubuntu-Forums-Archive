---
title: "Enabling ethernet and wireless on Ubuntu Minimal install?"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Kareeser on 2009-05-10
Hey everybody,

I have a freshly installed Ubuntu installed with the Minimal CD onto a USB stick. With the intention of booting up as a recovery console on other computers.

I don't have a desktop environment, and I need the network to autoconfigure at least the ethernet upon bootup.

Except on the test system, whenever I boot from the usb drive and run "ifconfig", the only device that shows up is the loopback device. eth0 and eth1 are absent.

If I run iwconfig, the program exits with a segmentation fault.

I know the drivers in the test system are compiled into the kernel, both ipw2200 and b44, so what else needs to be done before I can get online? How do install CD's autoconfigure?

---

