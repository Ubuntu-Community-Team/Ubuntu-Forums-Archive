---
title: "networking issue"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by slonnnik on 2010-08-20
Hi

I have upgraded my kernel and I'm not able to find any network.
Wireles is enabled.
any help?

Thanks

---

### Post by MonteZ on 2010-08-20
After the computer restart try

dmesg |grep wlan

maybe it will give you some clues on what is wrong..

---

### Post by Iowan on 2010-08-20
**sudo lshw -C network** should reveal much about your interface...

---

### Post by slonnnik on 2010-08-23
> **MonteZ said:**
> After the computer restart try

dmesg |grep wlan

maybe it will give you some clues on what is wrong..

This doesn't work

---

### Post by slonnnik on 2010-08-23
> **Iowan said:**
> **sudo lshw -C network** should reveal much about your interface...

This shows me interface but how does it help me when I cannot find any network? 

Here is what is shows:
*-network                
       description: Ethernet interface 
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 21 
       serial: 00:17:08:2f:8e:38 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5753m-v3.56 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:30 memory:f4100000-f410ffff 
  *-network UNCLAIMED 
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:10:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f4000000-f4003fff

---

### Post by Iowan on 2010-08-23
> **slonnnik said:**
> This shows me interface but how does it help me when I cannot find any network? The results show a driver for eth0, but (as far as I can tell) none for the wireless. I (or you) would need to search the forums for "BCM4311" so see if others have had problems/solutions with that chipset - or what driver is recommended.

Is the wired connection working? It has no IP address - but maybe it isn't plugged in...

---

### Post by slonnnik on 2010-08-24
> **Iowan said:**
> The results show a driver for eth0, but (as far as I can tell) none for the wireless. I (or you) would need to search the forums for "BCM4311" so see if others have had problems/solutions with that chipset - or what driver is recommended.

Is the wired connection working? It has no IP address - but maybe it isn't plugged in...

Wired connection is not pluged in.
Wireless connection worked fine until I install new kernel.

---

