---
title: "Need Suggestion on Ubuntu-as-router"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Macsloverd on 2011-01-22
Here is the interesting story:

I'm living in an old building (kinda 100+ years old) in the Netherlands and it is converted into a building of appartments, within this building, I am the only one who have internet access (ADSL) - once I registered with an ISP with this address, others can't - lucky me. So my neighbor shares my internet connection, later on, more neighbors are sharing my connection. So I decided to build a Ubuntu based router for everybody. I managed to get an old IBM rack Xeon server (P4 Xeon 3.0GHz x2, 4GB ECC DDR, 2 hot-swap SCSIs @ RAID 1, 4 x GBE), so I planned this:


INTERNET====UBUNTU------GBE Switch-----wired neighbors
                             [COLOR=White]----------------------[/COLOR]|
                             [COLOR=White]----------------------[/COLOR]|_______GBE 802.11n 300Mbps WiFi Router as AP

the rack has 4 Gigabite Ethernet NICs, so I decide make a bond0 (RR)=eth0+eth1 and connet bond0 to INTERNET (btw, my ADSL is a commercial connection, 8 public IPs / 20Mbps down / 1Mbps up), eth2 to a gigabit switch for people who does not have good wireless reception and eth3 to a gigabit wireless router with 300Mbps 11n connection.

Typical usage of this connection are web and youtube, sometimes skype. About 15 simultaneous connection MAX.

As nowadays all computers are GBE NICs so my idea is to get all connections gigabit - at least the bottleneck would not be the router. For the wifi connection, the only (and chippest) GB Lan wifi router I can get is a linksys one with 11n.

My questions are:

* Is this router a efficient one? In other words, what makes a router a good router?
* I still can add a 4 ports GBE PCIX NIC, so is it neccesary to make bond0 (RR)=eth0+eth1+eth5+eth6 to do more load balancing?

Any suggestion is appreciated!
Thanks in advance!

---

