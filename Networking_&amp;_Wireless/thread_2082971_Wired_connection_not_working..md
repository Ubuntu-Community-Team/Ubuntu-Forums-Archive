---
title: "Wired connection not working."
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by pradeepbhadani on 2012-11-11
I installed ubuntu 12.10 . 
Wireless connection is working fine.It connects automatically.

But wired connection is not working.
When i plug my LAN cable in port ,there is no light on port.

I searched a lot on internet , but got no solution. 
While installing ubuntu my LAN cable was attached.

How to resolve this??

---

### Post by Abhinav Kumar on 2012-11-11
> **pradeepbhadani said:**
> I installed ubuntu 12.10 . 
Wireless connection is working fine.It connects automatically.

But wired connection is not working.
When i plug my LAN cable in port ,there is no light on port.

I searched a lot on internet , but got no solution. 
While installing ubuntu my LAN cable was attached.

How to resolve this??
Hi,

Can you please the output of
```

sudo lshw -C network

```

Regards,
Abhinav

---

### Post by pradeepbhadani on 2012-11-11
Hi Abhinav,

Below is the output of command :

:~$ sudo lshw -C network
[sudo] password for pradeep: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 08:3e:8e:1e:fb:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by AntonPhibes on 2012-11-15
I wonder if you're experiencing the same issue I was.

I upgraded from 12.04 to 12.10 and today was experiencing the same thing where Wireless was connecting fine but Wired would not.

It wasn't until I plugged in my AC Adapter that the Wired adapter turned on and connected which pointed me to power settings being the culprit.

Hope this helps.

Thanks

---

