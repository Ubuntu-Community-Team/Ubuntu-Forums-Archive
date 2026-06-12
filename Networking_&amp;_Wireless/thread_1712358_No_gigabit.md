---
title: "No gigabit"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by arnobeck on 2011-03-22
Hello,
I have installed Ubuntu lucid on my Fit-pc2i.
The 2 ports detect as 1000Mbits ports which is right, but when I transfer something to or from the fit-pc2i, I only get 100Mbits of bandwidth.
Could you help me to fix this ?
I bought this fit-pc2i to be a gigabit router, but it seems limited to 100Mbits.
Thanks for your help

PS : here is the ethtool result : 
$ ethtool eth1
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

---

