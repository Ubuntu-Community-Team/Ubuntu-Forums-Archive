---
title: "Adding Computers/Devices to subnetwork"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-01-15
I have my sub-network (network that's behind another network, see [http://img205.imageshack.us/img205/3482/icsmu9.png](http://img205.imageshack.us/img205/3482/icsmu9.png)) that has my Xbox, [NSLU2](http://bestwikiever.wikidot.com/NSLU2), and computers; one of which that's wireless apapter links to my wireless network... The computers on this subnetwork are wired into my DLink router.

If I would want to add more computers/devices  to this network,would that be what a hub/switch/second router would be for (I plug it into the Dlink router and then plug the other devices into it?)

What's the difference between a router, hub, and a switch?

---

### Post by wmdiem on 2009-01-15
you want a hub.
If I recall:
A router is smart a hub is not, I.e., a router reads ip addresses and figures out where they need to go. A hub just forwards stuff to all the computers hooked up to it, and lets them sort it out. A switch is a little smarter than a hub so it only forwards stuff where it needs to go, but it does it using mac addresses, not ip (its basically a fast hub, but complete overkill in most home use).

---

### Post by RealG187 on 2009-01-16
My router has DHCP disabled (The one computer assigns the DHCP) so is my router like a hub/switch since it lets the computer decides where the information goes...

---

### Post by cariboo on 2009-01-16
Most hubs are Limited to 100Mb, you may want to go with a 1000Gb switch to future proof your self. I've been using  a 100Mb switch for about 10 years, and the thing just won't die. :(

Jim

---

### Post by capscrew on 2009-01-16
A hub connects all devices to a common wire.  This can cause traffic slowdown in heavy use situations.  A switch allows one to one traffic between devices.  A router is a device to connect 2 or more networks.  Most routers also have the capacity to provide other network services such as DHCP and DNS.

---

### Post by Iowan on 2009-01-16
> **capscrew said:**
> A router is a device to connect 2 or more networks. You could read "network" as "subnet".  You could also think of the router as *separating* subnets.  For example, a 2-port router (if such exists) has port 1 as 192.168.0.1; port 2 is 192.168.1.1;  Traffic from machine 192.168.0.111 bound for 192.168.0.112 does not pass through the router - no reason to leave the subnet. Traffic from machine 192.168.0.111 bound for 192.168.1.111 goes in port 1 and comes out port 2.

My example was originally a 4-port router with internet - but NAT (Network Address Translation) was gonna get messy.

---

### Post by capscrew on 2009-01-16
Iowan,

192.168.0.0/24 and 192.168.1.0/24 are two distict networks.  Most call them subnets but in actuality they are not subnets of any larger network.

It's all semantics anyway.

---

### Post by RealG187 on 2009-01-16
This is all confusing.

I have two networks. A wireless one and a wired one. The internet is on the wireless.

My IBM PC is connected to both networks and links the wired network to the wireless one (internet) so I think my IBM PC is a hub (has DHCP and an IP of 192.168.0.1 for ICS)

---

### Post by capscrew on 2009-01-16
RealG187,

The PC is not a hub.  A hub is a specific physical piece of equipment to connect all it's ports to a common wire.  

Bridging your wireless and ethernet interfaces is one way of doing the same thing via software.

---

### Post by RealG187 on 2009-01-17
the PC connects all the computers there to a common wire, or should I say wireless?

If instead of using that PC to connect my other network, if I used a wire (a really long wire, which is why I use wireless) would that make the second router a hub?

But would a hub be used to connect the two networks (ex those machines to the internet) and a switch to connect those machines to each other (that is not even acessing the first router with the internet)

---

