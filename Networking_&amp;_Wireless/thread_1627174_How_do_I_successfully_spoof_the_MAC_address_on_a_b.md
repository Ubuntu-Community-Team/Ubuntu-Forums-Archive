---
title: "How do I successfully spoof the MAC address on a broadcom wifi card"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by SusurAce on 2010-11-21
I have two identical laptops (hp touchsmart tm2's) running ubuntu 10.04.  I want to be able to access them using a vpn (neorouter), but this causes problems as they have the same mac address and so neorouter thinks they are the same machine.  

I have tried every way I (and google) can think of to change the mac address but once the mac address is changed the wifi card will no longer connect.

I have searched through ubuntuforums as thoroughly but any posts on this issue are at least a year old, and no seemed to find an answer.

Has anyone successfully managed to change the mac address on a Broadcom card (using broadcom sta driver). 


Just in-case it helps, here is my ifconfig readout:


eth1      Link encap:Ethernet  HWaddr c4:17:fe:10:76:72  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fe10:7672/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36222 errors:0 dropped:0 overruns:0 frame:10
          TX packets:40814 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6830072 (6.8 MB)  TX bytes:7340630 (7.3 MB)
          Interrupt:17 


And the content of lshw -c network:


  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:10:76:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.108 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:e2400000-e2403fff

ALL suggestions welcome! I can not stress that enough.  I am going crazy over here!

---

### Post by nutpants on 2012-11-01
bump
as i am looking to do this also

---

