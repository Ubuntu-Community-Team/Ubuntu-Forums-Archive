---
title: "Wake On Lan (WOL) on Intel Pro 1000 (e1000e)"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by kunalkishore on 2008-12-22
Hi all,
I couldn't find solution in any of the posts related to wol on ubuntu. I am on Ubuntu-8.04.2 hardy running on Intel DG33FB mobo having onboard Intel Pro 1000 network card. The problem is I am able to wake my PC when I shut down Windows XP which is another OS running on the mobo. But this doesn't happen when i do the same on Ubuntu. 

ethtool eth0 gives following:
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

Please suggest any solution.
Thanks in advance.

---

