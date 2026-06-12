---
title: "Network card cannot set to 1000"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by daniele75 on 2012-06-19
Hello all.
I've this strange (very strange) problem.

Version is:

Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

I've installed ntop and I'm using it to monitor network.

Onboard there are two 10/100/1000 cards


05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 01)

One card is configured as eth0 with an ip address and the other is configured as promisc to monitor traffic.

Both are connected to a cisco 6513 switch.

First of them go properly to 1000baseT-FD, while the other (the one used for monitoring) go only to 100BaseTx.

I've tried to:

- change cables
- invert connections (connect eth0 to switchport where is connected eth1 and viceversa)
- change switchports
- set speed and duplex with mii-tool and ethtool

But I can't solve this problem.

eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 100baseTx-FD, link ok

network cards are identical

Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

Any suggestion will be greatly appreciated.
Thanks
Daniele

---

