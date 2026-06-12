---
title: "how do I set up dual wan linux router"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by jewfromdahood on 2011-08-09
I want to make a dual wan router with firewall (I was thinking of using firestarter) and dhcp. I need VoIP phones to pass through it as well as SSH. could someone point me to the documentation. I need the firewall to be easily modified as we will be adding more devices down the road that need to be opened.

---

### Post by jewfromdahood on 2011-08-10
I'll be using Ubuntu 11.04 x64 for it. I figured out everything almost except how to fuse the two internets together. I'm using Time warner business class and and a airband (telecom) line. (for business of course). Is there a way I can auto-load balance them. the down speed on the airband is 5Mbps, and time warner is 35 Mbps, both have 5Mbps upload. I want to be able to utilize both completely, but in case one of them goes down to automatically switch to the one that is working.

---

### Post by jewfromdahood on 2011-08-16
Hi could someone point me to documentation for my Linux box to become a dual-wan router. And I want to slap in a D-link Xtreme N Pci-E adapter as my wireless router just died. If that d-link won't work with Linux will someone point me to the best PCI-E wireless N adapter. I am looking to have a system with two ISPs (airband and timewarner business Class) to have time warner as the primary, and airbadn as the secondary back up. Wireless needs to only be on N/G for when friends and clients with older laptops come over. with WPA2 encryption using AES.

---

### Post by jewfromdahood on 2011-08-16
bump!

---

### Post by jewfromdahood on 2011-08-16
Hi I need some help. And the usual router docs will not help I have a linux box (Hp Proliant Dl180 G6 server) I want to turn into a router. It has a couple spare parts my office had lying around that I threw in and they said I could have to build the new router for the office. It natively has 2 Intel 82576 gigabit ports, Which I want to bring in my timewarner business Class on the eth0 and eth1 to have airband. TWBC has 35 Mbps down/5mbps up. Airband has 5mbps up and down. I also threw in a Intel PCI-E server card with 4 gigabit ports also using the Intel 82576. Designated Eth2-eth5. I want wired functionality on each port to act like most routers that have 4 ports on the back. Needs to have firewall and VoIP phones through it all (have a seperate PoE switch for that). I have webmin installed on it already as well. It needs DHCP, but will be above the range for the static IPs. also need VPN functionality.
Also was wondering is it possible I can make a wifi network to be put in using a PCI-E wi-fi "N" card that will use WPA2 and AES encryption? 
I want to use this to make the entire LAN true Gigabit backbone as currently the dual-wan cisco VPN router we use is only 10/100.
This Linux router is basically to protect the internal Windows network.
Please Help.
I want to do something like Pfsense can do, but this server needs to do a bit more than what it can offer

---

### Post by jewfromdahood on 2011-08-16
I have been trying for days to figure this out
I did the packet forwarding for ipv4 and such. Now in webmin 1.560 I try to add new interfaces as I have two built in NIC (Intel 82576) I want to use for the dual-wan setup. and an Intel Server adapter with another 4 NIC I want to configure for the router. 3 of them I want programmed to connect to the 192.168.0.1 subnet. the other I want to connect to the 192.168.1.1 subnet so my PoE switch for my phones are separated from from the rest of the network. But for some reason I can't seem to figure out how to get it to work Could someone please help me out :confused: Could someone please help me figure this out as I want to get a true 1Gb/s backbone for the network here as we are running on a 100Mb/s backbone. And it is getting quite congested. Please help as soon as possible... Thank you!

---

### Post by jewfromdahood on 2011-08-16
Ok so I figured out how to get it on the 192.168.0.1 subnet however, How do I make able to switch between two WAN's easily in case one fails? As well as how do I set the firewalls and port forwarding? Is there a way I can turn on UPnP? And how do I get the second subnet working?

---

### Post by jewfromdahood on 2011-08-17
bump!

---

### Post by jewfromdahood on 2011-08-17
bump please anyone?

---

