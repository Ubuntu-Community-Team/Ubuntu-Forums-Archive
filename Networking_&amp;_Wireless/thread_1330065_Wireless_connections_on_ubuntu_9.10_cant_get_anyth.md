---
title: "Wireless connections on ubuntu 9.10?? cant get anything to work"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Craig_at_union on 2009-11-18
Hey i'm new to ubuntu and i cant get wireless to work on 9.10.. I dont know how to set up a connection so that i can get on.. I have no idea where to start. Can someone please help

---

### Post by t0mppa on 2009-11-18
You can use the Network Manager, i.e., the default program for setting up connections, by clicking its icon at the top right corner of your desktop (see the screenshot). Just pick your network from there and if it's encrypted, you'll be prompted for your password.

If you cannot see any networks there, then the drivers for your card aren't working properly and you should instead open up terminal (Applications / Accessories / Terminal), run **lshw -C network** and post back with the results to let us know what wireless chip you have and which driver is currently associated with it.

---

### Post by Craig_at_union on 2009-11-18
Here is the info I got from doing that.
 
 
Network
Description:Network Controller
product:BCM4312 802.11 b/g
vendor:Broadcom Corporation
physical id:0
bus info:pci@0000:0c:00.0
version:01
width:64 bits
clock:33 MHz
Capabilities:bus_master cap_list
configuration:driver=b43-pci-bridge latency=0
resources: irq:17 memory:f69fc000:f69fffff
 
 
 
 
Network
Descritpion: Ethernet interface
product:88E8040 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd
Physical id:0
bus info:pci@0000:09:0.0
logical name:etho
version:13
serial:oo:23:ae:33:26:f8
width:64 bits
clock:33 MHz
capabilities:bus_master cap_list ethernet physical
configuration:broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
resources:irq:29 memory:f28fc0000-f68fffff ioport:de00(size=256)
 
 
 
 
please help!!!

---

### Post by eremyja on 2009-11-18
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

download the file for you architecture

---

### Post by t0mppa on 2009-11-19
Like eremyja said, the STA driver will probably work best for you. If you're intimidated by having to compile it manually, you can also install it through the proprietary driver utility (System / Administration / Hardware Drivers), if it's displayed there (it isn't always there on Karmic for some reason) or install the *bcmwl-kernel-source* package with Synaptic or apt-get.

---

