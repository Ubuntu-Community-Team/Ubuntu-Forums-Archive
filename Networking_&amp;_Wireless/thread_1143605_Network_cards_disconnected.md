---
title: "Network cards disconnected?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by wzcocoon on 2009-04-30
Hello their,

I just upgraded to 9.04 and it detect my network cards but under it says disconnected. any idea on how can I connect them and let them be connected always? I have 2 cards and both are disconnected. thanks for your help

---

### Post by Iowan on 2009-04-30
As I recall, "disconnected" usually indicates driver issue - what kind of cards?

---

### Post by wzcocoon on 2009-05-01
The first one is a 
[LIST]D-Link System RTL8139 Ethernet[/LIST]
and the second one is a 
[LIST]Micro-Star International VT6102 [Rhine-II][/LIST]
I will really appreciated if you could help me with this. 

Thank you.

---

### Post by wzcocoon on 2009-05-03
:confused: I am relatively sure it is a driver problem but I am not sure where to start. I have those two network cards that are recognized by ubuntu but I cannot connect them can you help me please.

The first one is a

    * D-Link System RTL8139 Ethernet

and the second one is a

    * Micro-Star International VT6102 [Rhine-II]

I will really appreciated if you could help me with this.
Thank you.

---

### Post by RedSingularity on 2009-05-03
Are they wireless or wired?

---

### Post by Iowan on 2009-05-03
A quick Google search (I'm not familiar with them, either) shows them to be 10/100 (wired) cards. It also revealed several sites for drivers, but I'm not sure which ones work with/for Ubuntu.

What are results of **lshw -C network**?

---

### Post by wzcocoon on 2009-05-05
I am copying it back by hand so I hope I will not miss a line.

*-network:0
   description: Ethernet interface
   product: RTL8139 Ethernet
   vendor: D-Link System Ink
   physical id: 9
   bus info: pci@0000:00:09.0
   logical name: eth0
   version: 10
   serial: 00:40:05:0f:c4:92
   width: 32 bits
   clock: 33MHz
   capabilities: bus_master cap_list ethernet physical
   configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

*-network:1
   description: Ethernet interface
   product: VT6102 [Rhine-II]
   vendor: VIA Technologies, Inc.
   physical id: 12
   bus info: pci@0000:00:12.0
   logical name: eth1
   version: 78
   serial: 00:16:17:75:02:03
   width: 32 bits
   clock: 33MHz
   capabilities: bus_master cap_list ethernet physical
   configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via-rhine multicast=yes

*-network:DESABLED
   description: Ethernet interface
   physical id: 2
   logical name: pan0
   serial: la:91:18:8b:36:f0
   capabilities: ethernet physical
   configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

