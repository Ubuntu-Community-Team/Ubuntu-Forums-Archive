---
title: "Trying to Install WUSB100 on Ubuntu 10.04"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by lov255 on 2010-08-10
Warning I am a noob to this.  Back about 13 years ago I used to fool around with a shell account over the internet.  But that was for only a few years.

I have spent all day trying to find information on how to install the drivers for the Linksys/Cisco WUSB100 wireless USB adapter.

It is going on my Dell Latitude C830, running Ubuntu 10.04, Intel Chipset.

Everything I have read suggests that the rt2870 driver is needed

Any help that can be provided would really help a lot.

I have the ndiswrapper and when I do dmesg | grep -e rt2 -e rt3, I get couldn't prepare driver 'rt2870' and another line that says it can not load it

lsub returns:
Bus 002 Device 002: 046d:c521 Logitech, Inc.  Mx 620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1727:0078 Linksys
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

