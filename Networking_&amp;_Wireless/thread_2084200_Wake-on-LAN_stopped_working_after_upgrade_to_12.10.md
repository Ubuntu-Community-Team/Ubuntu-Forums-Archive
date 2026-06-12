---
title: "Wake-on-LAN stopped working after upgrade to 12.10"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by Epistaxis on 2012-11-14
I am running Ubuntu 12.10 on an old Dell PowerEdge 1400, which I use mainly as a remote server. It has been through several OS version upgrades. Prior to 12.04, I configured wake-on-LAN (WOL) and was able to turn on the computer remotely with a magic packet after it had been turned off by 'sudo halt'. When I upgraded to 12.04, this didn't work anymore but it did work normally when it was turned off with 'sudo poweroff' instead. In 12.10, I have tried all sorts of different shutdown commands but WOL does not work after any of them.

Based on the WOL wiki page, I have tried 'sudo ethtool -s eth0 wol g' (yes, I'm sure eth0 is the correct adapter), but it didn't help, probably because that was already set. Here is the output of 'sudo ethtool eth0':

```

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

Please help me diagnose this problem and restore WOL to this machine.

---

