---
title: "Marvell Yukon drop outs fix"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by wvn on 2009-06-19
After spending endless days trying to tuckle the "network drops" issue with all the marvell yukon cards and the native **[COLOR="Red"]sky2[/COLOR]** kernel driver i came to the following conclusions:

1. Do not even try to compile the sk98lin driver from marvell. It wont install because the driver itself is outdated.
2. The sky2 driver has 15 bugs reported and apparently still open since initial 2.6.x kernel release

**[COLOR="#ff0000"]THE SOLUTION[/COLOR]**

Open a terminal 
sudo su

**ethtool -s eth0 autoneg off**

You can use this command ethtool eth0 to find out the current status of your ethe card b4 and after you execute the autoneg command.

A nice little workaround but i would still like a permanent fix in the kernel.

cya

> Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	[COLOR="#ff0000"]Supports auto-negotiation: Yes[/COLOR]
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	[COLOR="#ff0000"]Auto-negotiation: off[/COLOR]
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

---

