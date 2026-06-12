---
title: "Slow ethernet connection with AR8152 &amp; ubuntu 12.10"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by paolone919191 on 2013-04-21
Hi,

I bought a brand new netbook: it's an emachines 355 series.

Wifi and ethernet works OOB, but the last one is really slow (less than 10 mbit).

that's the lspci -nn result:
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)

```

that's the lshw -C network
```
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:a8:63:9f
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)

```

Can someone help me please? In windows 7 the card works ok (100 mbit)...

I tried to recompile manually the atl1c kernel module, but nothing changed...

---

### Post by praseodym on 2013-04-21
Please install "ethtool" and show
```

sudo ethtool eth0
ifconfig -a
cat /etc/resolv.conf
```

---

