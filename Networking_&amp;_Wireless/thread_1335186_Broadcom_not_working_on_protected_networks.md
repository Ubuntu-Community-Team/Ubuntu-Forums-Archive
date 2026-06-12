---
title: "Broadcom not working on protected networks"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by rapsioux on 2009-11-23
Hello, I have karmic on a HP pavilion dv5 with a broadcom bcm4312. I can connect unprotected networks but when I connect to a wpa or a wep network, internet doesn't work. It's not a dns problem because I've already tried to ping web directions without response but I can ping my router and access its configuration.

I've tried using wicd, b43-fwcutter, compiling source from restricted drivers but nothing works.. When I use the broadcom STA driver it list all the networks and I can connect but I only get internet with unprotected ones. I also can connect through ethernet.

I've searched a lot but there are many problems with broadcom cards, I've tried everything but maybe you could help me with my problem.

This is what lshw -C network lists:

*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:de200000-de203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:f6:8f:1e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.129 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:6000(size=256) memory:d4010000-d4010fff(prefetchable) memory:d4000000-d400ffff(prefetchable) memory:d4020000-d402ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:00:6a:91:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.128 multicast=yes wireless=IEEE 802.11bg

Thank you

---

### Post by Bunnybugs on 2009-11-23
Go to Synaptic Packagemanager (System>Administration>Synaptic), search for WPA, and WEP... Look wich codecs are available, and if they are installed...

If not, mark them for installation!

---

### Post by rapsioux on 2009-11-23
Thank you for your help but that doesnt work. I dont know anything more I could do :/

---

### Post by Bunnybugs on 2009-11-24
> **rapsioux said:**
> Thank you for your help but that doesnt work. I dont know anything more I could do :/


Did you check the Hardware Drivers? (System>Administration>Hardware Drivers), Check there if you'll need a specific driver for your adapter. And if so, Activate that driver!

---

### Post by rapsioux on 2009-11-24
> **Bunnybugs said:**
> Did you check the Hardware Drivers? (System>Administration>Hardware Drivers), Check there if you'll need a specific driver for your adapter. And if so, Activate that driver!

Yes, I said that I have restricted drivers from broadcom activated, and with them I can connect networks, but if it's protected I can't manage to connect to the internet. The network manager displays it's connected but it doesnt loads anything and doesnt pings any ip.

---

### Post by Sami00Sami on 2009-12-29
I have used this tip in 8.10 and will try it in 9.10 when I upgrade to it. It's howto to manually install binary drivers provided by broadcomm itself.

[http://www.superjoesoftware.com/articles/dell-1525-debian-wireless](http://www.superjoesoftware.com/articles/dell-1525-debian-wireless)

---

