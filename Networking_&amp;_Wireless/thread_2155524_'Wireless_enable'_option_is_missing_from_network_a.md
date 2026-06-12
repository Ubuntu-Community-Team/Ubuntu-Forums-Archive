---
title: "'Wireless enable' option is missing from network applet!"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by sahilh14 on 2013-06-18
[B]In the drop down menu, 'enable wireless' is not there.
[/B]Ubuntu version is 11.10. Laptop is hp-pavilion g6 2320 TX.
[B]
Network controller : Ralink corp. Device 3290
Ethernet controller : Realtek Semiconductor co., Ltd. Device 5229 (rev 01)

[/B]And also, when I ran the command** 'lshw -C network'**, it gave the following msg : 
[B]
*-network [B]*_UNCLAIMED_*
#some data

*-network
#some data

[B]What is network UNCLAIMED??

[/B][/B][/B]Please help me. I have gone through the forums and still haven't found a fix.[B][B][B]

Thanks[/B][/B][/B]

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by sahilh14 on 2013-06-20
> **ahallubuntu said:**
> The wireless card driver is ether not installed or blocked. 

Ubuntu 11.10 is no longer supported.

Here's a guide for installing a driver for Ralink 3290 with Ubuntu 12.04:

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)


Thanks a bunch for the reply :)

The issue is solved. :D

---

