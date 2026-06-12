---
title: "wirless network problems"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by maloy on 2009-06-01
hi guys.

I'm having problems with my wireless network connection.  my laptop has a built-in wlan card but neither windows nor xubuntu detects it.  So I took my laptop for repair and it was diagnosed by the technician as having the wrong driver.  the laptop still detects the device but only describes it as "network controller"  

here is the info:

noel14@maloy:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED
       description: Network controller
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc. 
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:2b:05:f0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

my driver for the wlan card is ralink RT2500 but, as I said, isn't detected by the computer.  I bought a PCI card which has the rtl8180 chipset, which I also have problem installing.

Any help is appreciated. Thanks.

---

