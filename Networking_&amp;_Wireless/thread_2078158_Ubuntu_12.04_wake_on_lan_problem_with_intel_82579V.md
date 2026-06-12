---
title: "Ubuntu 12.04 wake on lan problem with intel 82579V Gigabit LAN Controller"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by IrishAdam on 2012-10-30
Hi,

I cant seem to get wake on LAN working after shutting down ubuntu 12.04. I have a Asus Sabertooth z77 motherboard with a Intel 82579V Gigabit LAN Controller and have wake on pci/pcie enabled in the bios. I dual boot Windows 7 on the same machine and I can make it wake up after I shut down from windows.

I use the Wake On Lan app on my galaxy nexus to send the packet to the mac address of the Ethernet port, I can see network activity on the router and the light on the motherboard port flashes. As I said, this works fine when I shutdown from windows.

Here is the output from sudo ethtool eth0


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
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000001 (1)
			       drv
	Link detected: yes


Any ideas?

Adam

---

### Post by IrishAdam on 2012-11-19
Ok, there is nothing wrong with the intel 8259V under ubuntu, I just wasn't doing it right.

I updated the Bios and read fordem's post here [http://forum1.netgear.com/showthread.php?t=73323](http://forum1.netgear.com/showthread.php?t=73323)
He describes why, what I was doing worked sometimes.


It makes sense when you actually think about it, don't send the magic packet to the ip of the machine, broadcast it over x.x.x.255.

Works great now

---

