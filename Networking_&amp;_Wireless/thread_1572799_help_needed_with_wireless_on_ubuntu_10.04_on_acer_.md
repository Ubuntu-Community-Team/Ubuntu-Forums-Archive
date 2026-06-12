---
title: "help needed with wireless on ubuntu 10.04 on acer aspire 5520"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by flameshacker on 2010-09-11
My problem is it will work then randomly drop and I wont beable to get it back up for like 5-6 hours, and then I have to actually restart before it comes back.

Here is the output of   sudo lshw -C network


 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:56:c6:f5
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.106 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f2688000-f2688fff ioport:30f8(size=8 ) memory:f2689c00-f2689cff memory:f2689800-f268980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:c4:2d:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f2200000-f220ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Any help would be great, this problem is really annoying.

---

### Post by MaindotC on 2010-09-11
Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and post your shell outputs in [code] tags.

It sounds like you have a driver configuration issue.  I'm guessing that if you don't find your answers in the guide then you may want to consult the ath5k documentation or support forum/IRC for help configuring it, or even making sure that is the ath driver you need for your wireless card.

---

### Post by flameshacker on 2010-09-12
thanks I'll go through those now.

---

