---
title: "Wireless trouble on all my linux boxes"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by Admiral_deLorei on 2009-07-22
Hey all...I seem to be having trouble with my linux boxes in general.

I own two boxes, a Dell Latitude D630 running Ubuntu 9.04, and a little Acer Aspire One running Crunchbang Linux, which might change in the near future. They both connect to the net, but after a time the browser just hangs on loading, sometimes for 5 or so minutes. I have confirmed it is not due to being out of range of the router, as I've run my Aspire One pretty much right next to the thing. 

I have a feeling the problem is linux-related, as I'm dual-booting the Dell with Windows XP (for gaming) and it has no trouble with maintaining a connection.

The router is a Linksys WRT54G.

I'll post whatever relevant information is needed. I would just like to get this problem solved, as it can be quite annoying.

---

### Post by cariboo on 2009-07-22
What wireless device do your computers have? Could you post the output of:

```
sudo lshw -C network
```

for both systems?

---

### Post by Admiral_deLorei on 2009-07-23
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:b6:c7:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.5 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:98:e6:98
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair

```

I suppose I should have put that at first. It's a Broadcom BCM4312 card.

---

