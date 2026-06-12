---
title: "[SOLVED] Broadcom 4306 pci card problems, ubuntu server"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Hospadar on 2008-12-24
I'm trying to get my wireless card working.
It's a server install and I have no wired connection on the machine (it's an old laptop) so I really can't do anything with this machine until I get the pcmcia wifi card working.
It isn't running network manager and X or desktop environment.

It looks like the machine sees the card, but I can't acually do anything with it.
Here's the output of "lshw -C Network"
```
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:10:21:58:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```
And when I try "sudo ifdown wlan0" I get```
<luke@node:~$> sudo ifdown wlan0
[sudo] password for luke: 
ifdown: interface wlan0 not configured

```

---

### Post by ieee488 on 2008-12-24
If you have Ubuntu 8.10, this card will be detected easily. 

If you have Ubuntu 8.04, look for a post of mine about Dell Truemobile which has the same chipset. I was able to get it working with help.

---

### Post by Hospadar on 2008-12-24
Edit: Installed the broadcom firmware and things started working

---

