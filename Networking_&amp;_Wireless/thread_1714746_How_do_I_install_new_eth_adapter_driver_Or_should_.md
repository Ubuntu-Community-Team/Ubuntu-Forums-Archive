---
title: "How do I install new eth adapter driver? Or should I?"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by ronti69 on 2011-03-25
I am a newbie running Ubuntu 10.10 (LOVE it) and just got an ASUS NX1101 10/100/1000 card (PCI). Put it in and Ubuntu recognized it right away, but it reports it's a 10/100 card, and it does not let me set up wake on land (which the card is supposed to support). 
The card came with linux drivers. Should I install them? If so, how?
The card comes with instructions to install the driver in RedHat, Madrake, kernel 2.6.x
, bigmem and smp. Have no idea what any of those are.

Oh, one more thing: they system is wired to a 10/100 router. Does that matter? Will it automatically be configured to a 10/100/1000 when I save enough for a Gigabit router?

Thanks!

Here's what ethtool reports:

Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on

root@HTPC:/home/gustavo# ethtool -s eth1 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

---

### Post by gordintoronto on 2011-03-25
Wake on LAN is a BIOS function.

If the card works, you should not try to install a driver.

If your router is 10/100, of course the card can't work faster. I would be surprised if your computer is fast enough that "1000" would actually do anything faster than "100."

---

