---
title: "Realtek Gigabit Ethernet controller stuck at 100Mbps"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by ildella on 2011-01-01
Hi. I just installed Ubuntu 10.10 on a new desktop, with a gigabyte H55M mobo with this ethernet controller:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

I've read that the fact the driver loaded is, indeed, r8169 instead of r8168 can led to having the speed used to be 100 instaed of 1000Mbps but actually the 1000 is advertised as of:

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

So what can I do to let the driver load the eth0 interface at 1000 full duplex speed?

I've already tried this
[http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/](http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/)
but I think was a differenct problem: in that scenario the 1000 speed wasn't advertised. Anyway, does not work for me.

---

