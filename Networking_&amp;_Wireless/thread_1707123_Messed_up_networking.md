---
title: "Messed up networking"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by jarralad on 2011-03-14
Hello,

I am running Ubuntu 10.04 LTS. My wired networking stopped working recently. I was reading some posts on the topic and a couple suggested replacing network-manager with wicd. I did this and now I have lost my wireless networking as well !

*ifconfig* shows no eth0 interface

> 
eth1      Link encap:Ethernet  HWaddr 78:e4:00:f7:56:15  
          inet6 addr: fe80::7ae4:ff:fef7:5615/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:194
          TX packets:0 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
*lshw -C network* shows that the ethernet adaptor is unclaimed (whatever that means)

> 
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 01
       serial: 78:e4:00:f7:56:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f0503fff


When I try to connect using wifi, wicd times out after failing to validate authentication with the message "Connection Failed: Bad password" even though I know the password to be correct.

---

