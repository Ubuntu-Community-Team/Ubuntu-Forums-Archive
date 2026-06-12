---
title: "Can't see Wireless Connectins after entering a command - BCM 4322"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jschille on 2010-05-11
Hello!

Lately I have been forced to use a different kernel because after entering the command
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic


```
I have lost the ability to see wireless connections, in fact the wireless connections do not even come up.

My computer recognizes I have the Broadcom STA drivers installed and are working properly, just lost the ability to see and connect to wireless networks.  Any help would be greatly appreciated.

```

 *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:f7:92:be
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff

```

---

### Post by jschille on 2010-05-11
/bumping for love

---

### Post by pdc on 2010-05-12
I suspect you have several posts running on the same topic?

download and run this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

it will analyse your wireless; make recommendations;

post it back here if you want further help;

---

