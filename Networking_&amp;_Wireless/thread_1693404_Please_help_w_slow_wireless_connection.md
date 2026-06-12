---
title: "Please help w/ slow wireless connection"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by pablidito on 2011-02-22
Hi, I am a newbie to this forum, so please forgive me if I'm not posting in the right place or if I'm not providing enough information.  Ok, now that I have provided my disclaimer, here is my problem.  I have installed Ubuntu 10.10 on my Dell Latitude D830 laptop using the Wubi installer.  Everything seems to be working fine except for my wireless connection.  When I plug in my wired connection and test on speedtest.net I get download speeds of 20MB/second.  However, when I switch to my wireless connection, I barely break 1MB/second.  I have an Intel PRO/Wireless 3945ABG wireless adapter.  I have scoured this forum, Google, everywhere I can think of to find a solution and none seem to work for me.  I love Ubuntu but this might be a deal breaker...  

ANY suggestions would be most welcome...thanks in advance!

---

### Post by whatthefunk on 2011-02-22
My guess is a driver problem.  Type this into a terminal and post the output here:

```
sudo lshw -C network
```

This should tell us what driver your using with your wireless adapter.

---

### Post by pablidito on 2011-02-22
Thanks for the reply.  Here is the output:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:11:23:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-25-generic firmware=15.32.2.9 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f6cff000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b1:ba:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f69f0000-f69fffff

---

### Post by whatthefunk on 2011-02-22
[http://sourceforge.net/projects/ipw3945/](http://sourceforge.net/projects/ipw3945/)

The driver should be there.

---

