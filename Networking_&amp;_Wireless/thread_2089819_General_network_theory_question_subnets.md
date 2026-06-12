---
title: "General network theory question subnets"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by mushy365 on 2012-11-30
My modem is built into my router, I don't want to mess with it. However, i want to have a webserver. Now, if im going to allow traffic to this server i want to make sure this server or the outside traffic have no access to the rest of my network. 
 
I am not an expert, but is subnetting a logical answer? I heard conputers on different subnets cannot speak with each other unless its through a router. 
 
So i have my router to which my server, ubuntu desktop and two laptops are connected. 
 
Router: 192.168.1.254
Desktop: 192.168.1.100
Broadcast:192.168.1.255
Windows laptop1: 192.168.1.64
Windows laptop2: 192.168.1.50
 
If i give my server a static ip say 192.168.2.100
then a subnet mask of 255.255.0.0
Would that allow it to be basically in a network of its own, so if someone got access to it, the rest of the computers on the network would be safe?
 
Also would i need to edit the router/dhcp server to assign a ip on a different subnet?

---

### Post by slickymaster on 2012-11-30
Two PC's on different subnets would NOT be able to ping each other unless there is a layer 3 device (i.e. a router), but two PC's in the same VLAN on different Subnets CAN IN FACT ping each other because they are in the same Layer 2 broadcast domain. 
Don't assume that just because you have 2 different subnets that you also have 2 separate VLANs

Subnet - is a range of IP addresses determined by part of an address (often called the network address) and a subnet mask (netmask). For example, if the netmask is 255.255.255.0 (or /24 for short), and the network address is 192.168.10.0, then that defines a range of IP addresses 192.168.10.0 through 192.168.10.255. Shorthand for writing that is 192.168.10.0/24.

VLAN - A good way to think of this is "switch partitioning." Let's say you have an 8 port switch that is VLAN-able. You can assign 4 ports to one VLAN (say VLAN 1) and 4 ports to another VLAN (say VLAN 2). VLAN 1 won't see any of VLAN 2's traffic and vice versa, logically, you now have two separate switches.

---

### Post by SeijiSensei on 2012-11-30
Does the router have a "DMZ" option?  That's designed precisely for this situation.

---

### Post by mushy365 on 2012-11-30
Not sure if it has a DMZ option, was going to mention that in my op. Think it stands for a demilitarised zone? 
 
Say it did not have this option. What are my options. I did not really understand the first reply. How do i know or make sure they are on two different vlans? 
 
Like i said my setup is 
 
internet ------(modem/router/dhcp) ----------- Desktop
**************************----------- Server
**************************------------Windows 
 
all connected to the one router. Would assigning the server a different subnet and different ip address i.e 192.168.2  as opposed to 192.168.1   be enough or what else can i do?

---

### Post by SeijiSensei on 2012-11-30
No, since by default the router wouldn't know about the other network.  Some routers let you set up "static routes."  If yours does, you could define a route for 192.168.2.0/24 and make the server be the route's gateway.

And, yes, it stands for "Demilitarised Zone" like in Korea.

---

### Post by slickymaster on 2012-11-30
Since SeijiSensei already answered both your questions, let me only give you a link to a tutorial/explanation about DMZ's and how to build one, that can help you in case you're planning on follow that path.

[What is a DMZ and how do I build one?]("http://forums.windowsecurity.com/viewtopic.php?t=5653&start=0&postdays=0&postorder=asc&highlight=&sid=5d9a9c02a5936889206ea05327018820")

---

