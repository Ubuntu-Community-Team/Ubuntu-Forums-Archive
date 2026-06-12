---
title: "Wireless down"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by jason31 on 2009-08-01
Wireless was working fine until a few days ago. Now I get the following output. Any ideas on how to fix this....??

user@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:3b:98:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.2.24 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:50:f1:02
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:2a:33:8a:5b:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
user@ubuntu:~$

---

### Post by nixscripter on 2009-08-02
I don't see anything wrong. How are you trying to restart wireless?

---

