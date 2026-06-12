---
title: "wireless not detected on ubuntu 9.10 karmic koala"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by 24dhruv on 2009-12-19
i have got 

[COLOR="Blue"][CENTER]broadcom 4312 wireless device[/CENTER][/COLOR]


 having 

[COLOR="Blue"][CENTER]amd turion 64 processor[/CENTER][/COLOR]

 on 

[COLOR="Blue"][CENTER]hp pavilion 6000 series laptop[/CENTER]
[/COLOR]
 i want to make it work in 

[COLOR="Blue"][RIGHT][CENTER]ubuntu 9.10 karmic koala[/CENTER][/RIGHT][/COLOR]

---

### Post by Avidanis on 2009-12-19
Type the following  into a console and copy and paste the output so we can see if your network card is being recognized . 

sudo lshw -C network

You will get a warning that this command should be run as super-user if you type it and enter without the sudo.The output should look similar to the following ....

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b0:c2:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:fe5fe000-fe5fffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:8d:d8:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg

---

