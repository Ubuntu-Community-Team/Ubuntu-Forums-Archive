---
title: "Wireless BM4311 Disabled/Ubunutu 10.10/HP Pavilion 2423"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by Rafa_Akd on 2011-04-23
Hi there, I have a HP Pavilion 2423 and Im having problems with my wireless configuration on Ubuntu 10.10. I installed Broadcom STA wireless driver via Additional Drivers and it says that it's activated and currently in use but at wireless network it says that wireless is disabled. I've been looking around but haven found any solutions.

Here is some information about my wireless card

```
rafa@rafapabon:~$ lspci -nn | grep Broadcom
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

``````
rafa@rafapabon:~$ sudo lshw -C network
[sudo] password for rafa: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:7c:a5:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:d4000000-d4003fff

```Thanks for taking the time and read my post

---

### Post by josephmills on 2011-04-23
hi there could you please press ctrl+alt+t then put ```
dmesg | grep b43
``` in then paste the outcome here thanks

---

