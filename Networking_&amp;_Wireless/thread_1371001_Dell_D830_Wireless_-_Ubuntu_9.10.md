---
title: "Dell D830 Wireless - Ubuntu 9.10"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by sputrniq on 2010-01-02
Using Wicd Network Manager and flipping the wireless switch,
I can, sometimes get the WiFi light on my laptop light panel.

Yet, I can't seem to get a wireless connection.

The closest I've come so far, is following these instructions:

[http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/](http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/)

Using Google Chrome it just "resolves host" or can't find the
web page.

This is the configuration info I get from Terminal:

administrator@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:cb:8e:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f9ffe000-f9ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:d1:74:14
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5755m-v3.29 ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:30 memory:f9bf0000-f9bfffff

Anyone?

Thanx


= = = = =
[I]In case someone finds the thread: Wifi works and is stable using 14.10. 
Mörgæs 2014-12-19[/I]

---

