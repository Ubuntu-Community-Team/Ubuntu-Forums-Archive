---
title: "No WLan connection after upgrade to 12.04.1"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by martinilinski on 2012-10-21
Hallo,
I just have upgraded to a Ubuntu 12.04.1. Since then my wireless lan doesn't work. If I start the system the nm-applet shows "connection established" and the menu of the applet shows that I am connected to the network, but if I try to ping my router or the internet, it isn't possible.
Output of ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:ad:7d:69  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fead:7d69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1553527 (1.5 MB)  TX bytes:41925 (41.9 KB)

Wired connection does work. Can anybody help me? Thanks

---

### Post by ahallubuntu on 2012-10-21
What's the output of

```
sudo lshw -C network
```

?

---

### Post by martinilinski on 2012-10-21
!

---

### Post by martinilinski on 2012-10-22
martin@martef:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:86:52:2c:8c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=1.5.1-k firmware=0.3-0 latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:47 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:ad:7d:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965  driverversion=3.2.0-31-generic firmware=228.61.2.24 ip=192.168.1.33  latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:df2fe000-df2fffff

---

