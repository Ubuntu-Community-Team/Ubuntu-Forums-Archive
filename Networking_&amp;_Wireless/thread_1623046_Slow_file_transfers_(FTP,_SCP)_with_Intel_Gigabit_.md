---
title: "Slow file transfers (FTP, SCP) with Intel Gigabit or Atheros WLAN"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by skinnersbane on 2010-11-16
Thank you to anyone who reads this.

I have been looking for solutions to this, but to no avail.

I just installed ubuntu as my primary OS, but I have the disk with XP on it and I don't want to go back, but I need faster network connectivity.

I have a T60p with Intel Gigabit jacked into my Gigabit router which also has my desktop (running XP) and my NAS.

If I FTP files from my NAS (or SCP), I get transfer speeds around 250-500 KB/s (which is not very fast).  On this same switch, from my XP desktop I get transfer speeds around 12 MB/s.  I get the same speeds using my 802.11n card (Atheros) as with the ethernet NIC (250-500 KB/s).  The drivers for the ethernet card and the atheros card are e1000e and ath9k respectively.

I have disabled IPv6.

Since the problem occurs using either interface, I am just going to concentrate on fixing it for the Ethernet interface (since I believe it to be a systemwide problem).

```

skinnersbane@albert:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
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
	MDI-X: off
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

```

Clearly my card is running at Gigabit, but why the bad transfer speeds?  I am using filezilla for FTP (technically FTPES).  I closed every other program.  My CPU utilization does seem high and I wonder if this is part of the problem.

I had no problems with throughput using either interface in Windows XP just one week ago.

Thanks for any help.

---

### Post by skinnersbane on 2010-11-16
OK, also worth noting, when I am jacked into ethernet on campus of a large university (we have a nice fat pipe), my speedtest.net results show bandwidth around 30-40 Mbps.  This is SLOW.  My XP machine would be able to max this out over Gigabit (well over 100 Mbps).  When I was using XP, BitTorrent would fly (for downloading something like Ubuntu).

I know this isn't the most precise measurement, but I feel it's pretty indicative of some problem with my machine.

---

