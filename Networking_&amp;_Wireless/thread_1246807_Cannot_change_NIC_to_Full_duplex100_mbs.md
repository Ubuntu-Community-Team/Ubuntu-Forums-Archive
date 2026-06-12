---
title: "Cannot change NIC to Full duplex/100 mbs"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by veli on 2009-08-22
Hi Guys,

I' trying out BPL (broadband over power lines). The ISP should provide transfer rates of up to 768 kbs download. I tested the connection and the maximum I could get is around 400 kbs. Then I checked the eth0 settings and found out the network is set up to half duplex. I tried to change to full duplex by the commands:

sudo ethtool -s eth0 autoneg off
sudo ethtool -s eth0 duplex full

But this didn't work, cannot connect to internet if autoneg is off. Are they any other means to change to full duplex? 

Here is some info:

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000037 (55)
	Link detected: yes

Thanks,

---

