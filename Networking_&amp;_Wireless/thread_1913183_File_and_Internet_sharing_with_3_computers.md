---
title: "File and Internet sharing with 3 computers"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by nislink on 2012-01-22
Goal: File sharing and Internet access on all 3 computers. 2 have windows 7 and the third Ubuntu 11.04.  

Problem: No internet access in the room where the computers are except for a wireless signal. Only 2 wireless adapters. 

What I have done so far: 
- Installed a wireless adapter on one windows 7 PC (W71) and the Ubuntu PC (U1).
- Hooked the second windows 7 PC (W72) up to the Ubuntu PC with an Ethernet cable, and set the Ethernet adapter to shared on the Ubuntu PC. 
- W72 obtains an IP address of 10.42.43.98 with a gateway of 10.42.43.1 (which is U1's Ethernet IP address.)
- At this point all PC's can access the internet.
- W71 is unable to ping W72 by IP or computer name (this is expected)
- W72 can ping W71 by IP, but not by computer name. (I solved this by editing the host file on W72 to route the pc name to W71's IP address)
- At this point all PC's have internet. W72 and U1 have access to all files on all PC's, but W71 can only access U1's files. 

Question: What can I do to make W72's files accessible to W71?

Additional Info: The wireless network subnet is 192.168.1.X (Gateway: 192.168.1.1, U1: 192.168.1.3, W71: 192.168.1.5)

Possible solution: If I hook a switch up to U1, then run ethernet cables to W71 and W72 would the DHCP created by setting U1's ethernet adapter to shared be able to assign IP's to both computers? I've never used internet connection sharing in Ubuntu before. If this would work I could actually eliminate W71's wireless adapter.

---

### Post by nislink on 2012-01-23
Update: I did not have ethernet cables long enough to try hooking all PC's up to the Ubuntu PC via a switch. I did, however, find an additional wireless router. 
- I hooked the wireless router up to the Ubuntu PC via the internet port on the router. 
- The Ubuntu PC assigned the router an IP address of 10.42.43.25. At this point I was unable to configure the router as it had the same internal IP address of the other router, so I unhooked it and assigned the router an internal IP of 10.10.24.1. 
- W72 is hooked up to the 2nd wireless router via an ethernet cable. 
- I then connected W71 to the 2nd wireless router via a wireless connection. 
- The problem with this is that there is now a firewall between the windows 7 PC's and the Ubuntu PC. This means that the W7 PC's can access files on U1, but not the other way around. 
- I can live with this setup as I don't share files between Ubuntu and Windows much. The main thing I need to work between these PC's is synergy so I don't have to use two keyboards and mice. This can be accomplished by forwarding the syngery port on the router to W72's internal IP address and setting synergy's server address to the routers external IP.  

- This does actually give me some added security from the wireless network that I am connecting to as it is not mine. I am still open to suggestions on the best way to accomplish this. I don't want to buy another wireless adapter, but as I have mentioned I have access to a switch and a wireless router.

Other thoughts: I may have an additional ethernet card I could put in U1. That would allow me to loop back to U1 from the router and put it inside the network.

---

### Post by catsrules on 2012-01-25
I would replace the ubuntu computer with a wireless bridge. that way you don't need to have 1 computer on to give internet to the other equipment. It would also allow you to put the Ubuntu comptuer back on the network with other other computers.

The router you have now might even support bridging, but you will probably loose your firewall. And if it where me I would want my network separated from the other network if I don't have control over it.

Also make sure you wireless isn't on the same channel of the other wireless, so the don't interfere with one another and cause performance issues.

---

