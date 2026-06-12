---
title: "Error in configuring ad-hoc network"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by nuwanr on 2009-09-01
Hi, 
I get the following error when i try to setup an ad-hoc network.
I use kubuntu on lenovoT60. 

nuwan@nuwan-laptop:~/cexample$ sudo iwconfig eth0 mode ad-hoc
[sudo] password for nuwan:
Error for wireless request "Set Mode" (8B06) :
SET failed on device eth0 ; Operation not supported.

what is the possible error for this?

my network card details are as follows 
=====================
*-network
description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:16:41:ae:c6:bc
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.5-1 ip=192.168.1.2 latency=

thanks
nuwanr

---

