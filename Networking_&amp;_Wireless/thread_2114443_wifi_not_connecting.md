---
title: "wifi not connecting"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by dapolls on 2013-02-10
Hi!
 
Over the past few days I've been having some problems connecting to my wifi network. Its very strange because it was working fine, then all of a sudden it stopped working. My HP mini netbook can connect to other wifi signals and my smartphone can connect to the home signal. so its not aproblem with the router or the laptop, just some connection to the router and laptop that isnt working. the laptop doesnt even pick up the signal, nor does it work when i use my smartphone as a hotspot or tether my smartphone to the pc.
 
im a noob with ubuntu, but i've run the following commands to try and get an idea to whats going on
 
sarah@sarah-HP-Mini:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:199
Rx invalid nwid:0 invalid crypt:0 invalid misc:0
eth2 no wireless extensions.
 
sarah@sarah-HP-Mini:~$ sudo iwconfig eth2
eth2 no wireless extensions.
 
sarah@sarah-HP-Mini:~$ sudo iwconfig eth2 ap any
Error for wireless request "Set AP Address" (8B14) :
SET failed on device eth2 ; Operation not supported.
 
sarah@sarah-HP-Mini:~$ sudo lshw -C network
*-network 
description: Wireless interface
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth1
version: 01
serial: 00:23:4e:70:da:64
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:16 memory:feafc000-feafffff
*-network
description: Ethernet interface
product: 88E8040 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:22:64:78:ce:11
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:42 memory:febfc000-febfffff ioport:ec00(size=256)
*-network
description: Ethernet interface
physical id: 1
bus info: usb@1:1
logical name: eth2
serial: 52:ea:d6:04:ea:75
capabilities: ethernet physical
configuration: broadcast=yes driver=ipheth link=yes multicast=yes
 
 
any help would be greatly appreciated! i need this widi for working from home.
 
thanks!

---

### Post by dapolls on 2013-02-10
Please help!!

---

### Post by dapolls on 2013-02-13
Can somebody please help me??

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by dapolls on 2013-02-15
thanks for the reply ahallubuntu!

the wireless card is working. right now i'm connected to my school's wifi network using the same laptop.

also, the router back home is also working because it works on other computers as well as on smartphones.

so there is a mis communication between the computer and the router. anybody know how to fix it?

thanks!!

---

### Post by jmontgom10 on 2013-02-16
I am having an incredibly similar problem. I am using a Broadcom 4313 card, but otherwise I'm in the same boat. This seems to be a problem that a recent update caused because I've noticed an explosion of posts like these within the past few days.

---

