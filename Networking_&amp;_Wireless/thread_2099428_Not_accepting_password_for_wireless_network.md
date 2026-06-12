---
title: "Not accepting password for wireless network"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by emilesilvis on 2012-12-29
Hello. Just installed Ubuntu 12.04 onto an old laptop (a Fujitsu AMILO Pro), and I'm having some difficulties connecting to a wireless network.

The native Ubuntu network manager picks up the wireless network. When attempting to connect I'm presented with a password prompt. Upon entering the password correctly, I'm prompted with the password again. It never accepts my password. I've tried to muck around with the wireless connection's settings, to no avail.

I've also installed Wicd Network Manager, which doesn't pick up *any *wireless networks (I find this odd).

The output of ```
sudo lshw -C network
``` is:

```
 *-network:0             
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:00:b4:9a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.2.0-35-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:d0002000-d0003fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:ca:d3:a4:65
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.117 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:7 ioport:1c00(size=256) memory:d0000400-d00004ff
```

Any help would be appreciated.

---

### Post by bodueko on 2012-12-29
First and foremost - REBOOT your wireless router
Wicd Network Manager works so possibly a problem with your installation
How were you able to download Wicd Network Manager if you could not connect over wifi?
I have witnessed kick outs like that from routers usually when the router is attacked
Alternatively set up the configuration manually instead of using DHCP and that will force it in

---

### Post by emilesilvis on 2013-01-02
> **bodueko said:**
> First and foremost - REBOOT your wireless router
Wicd Network Manager works so possibly a problem with your installation
How were you able to download Wicd Network Manager if you could not connect over wifi?
I have witnessed kick outs like that from routers usually when the router is attacked
Alternatively set up the configuration manually instead of using DHCP and that will force it in

Hi bodueko,

I will try to restart the wireless router.

I was on a wired connection when I downloaded Wicd Network Manager.

I'll report back once I've tried the above.

---

