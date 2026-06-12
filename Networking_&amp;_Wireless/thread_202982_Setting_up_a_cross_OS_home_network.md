---
title: "Setting up a cross OS home network"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by blitz091 on 2006-06-24
Hi, im very new to linux and i was wondering if someone could help me with this situation.

My current setup is like this:

A Windows running computer connected to a WRT54G Linksys router
A Linux running computer connected to a WMP54G Linksys PCI card

What im trying to do is establish an internet connection on the Linux PC, and possibly have a type of shared folder between the two computer. 
The internet connection is the prioity here.

I have been trying for a few days now to set this up (ive tried changing the protection to WEP, changing the Linux network set-up to Static IP, many unsuccesful attempts). I have been doing searches for solutions and im not quite sure which ones apply to my situation.

It would be great if someone could explain to me how to set this all up.

---

### Post by Beltonius on 2006-06-24
I'm having a very similar issue.

I have several machines running XP Home (and my laptop with Pro) networked together with a Linksys WRT54G as a router and another linksys router configured to act as a switch. My laptop is the only computer on the wireless. The network has internet access through the DSL modem that the router connects to directly. 

I've just configured one of the computers to dual-boot XP Home and Ubuntu 6.06. If windows runs, it has no problem accessing the internet/network (it is connected to the switch, not the router), but the moment I boot it with Ubuntu, no luck whatsoever. The router acts as a DHCP server, and as far as I can tell, the Ubuntu machine gets an IP assigned to it. I do have it configured to use DHCP If I ping that IP from my laptop it times out. If I try and ping other computers on the network from the Ubuntu machine, all requests time out. 

If I try "ifup eth0" I am informed that eth0 is already configured.

Under Network Tools it claims the device is active, but says the link speed is not available. 

Any help would be greatly appreciated!

---

### Post by Beltonius on 2006-06-24
According to Device manager, my PCI NIC is a:

21x4x DEC-Tulip compatible 10/100 Ethernet

Vendor: Davidom Semiconductor, Inc

---

### Post by Beltonius on 2006-06-25
Also, I've run "dhclient eth0" and after 6 DHCPDISCOVER's on eth0 to 255.255.255.255 port 67 to yield "No DHCPOFFERS received" and "No working leases in persistent database - sleeping."

---

