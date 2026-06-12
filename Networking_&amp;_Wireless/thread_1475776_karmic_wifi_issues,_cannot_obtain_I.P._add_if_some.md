---
title: "karmic wifi issues, cannot obtain I.P. add if someone else is on the network"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by mo.reina on 2010-05-07
i have a strange problem... ever since i've installed karmic i can't login to my home network if my roommate (who uses a mac) is already logged... he has to logout, wait for me to login, then log himself in... on Hardy this problem didn't exist....

output of lshw -C network:
```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:0e:c8:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=1.11.216.114 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:fe0fe000-fe0fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:c6:2f:85:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:31 ioport:b800(size=256) memory:fe1ff000-fe1fffff memory:fe1c0000-fe1dffff(prefetchable)

```

anyone know anything about this?

---

### Post by Iowan on 2010-05-07
Your network uses the 1.11.X.X network?  Is address static or DHCP? Does your machine get the address your roommate had?

---

### Post by mo.reina on 2010-05-10
nope, network is on the usual 192.168.x.x

i'm assuming my machine tries to lock on to a static i.p. address, otherwise there shouldn't be any reason that it can't connect if my roommate is on... though my settings are on DHCP, connecting to other networks isn't a problem.

---

### Post by mo.reina on 2010-05-11
just re-checked my i.p. address, and now the network is using 1.11.x.x.... i'm not totally sure what's going on here, it was 192.168.x.x last night....

---

