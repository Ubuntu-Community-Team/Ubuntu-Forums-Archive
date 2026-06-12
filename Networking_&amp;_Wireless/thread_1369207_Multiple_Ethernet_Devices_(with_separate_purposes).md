---
title: "Multiple Ethernet Devices (with separate purposes)"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by XanTrax on 2009-12-31
Hi everyone,

I have three ethernet devices on my primary machine.

1. Broadcom BCM4318
2. Onboard ethernet device
3. PCI Ethernet Device

On my secondary machine (kind of like my dev machine)

1. Broadcom BCM4318
2. Onboard ethernet device

They both access the internet through the BCM4318 devices.

I would like to install a router in my room and join the two computers onto it and be able to access them through the second router in my room.  This router will of course have a different subnet or a totally different class of IP's (as to not cause any hups in the pre-existing network).
 
My only issue with this, as of now, is that when the wired ethernet device is active on either machine, it takes over as primary and my network connection dies (because this second router does not have internet access).  

I guess my question is:

How do I make the wifi0 (BCM4318) the primary source of traffic flow rather than eth0 or eth1?  I am assuming it would have to be something in the routing tables with a route to each of the gateways for the specified device.  Maybe IPTables manipulation would work too.

Does anyone have any idea?

I am trying to bridge two computers on a router with no internet access inside of a pre-existing LAN.  When I join them on the router they lose internet access because eth0 is taking over as the primary interface.

Home router: 192.168.1.0/24
Secondary Router: 10.100.100.0/24
Primary wifi0: 192.168.1.101/32
Primary eth0: 10.100.100.10/32
Secondary wifi0: 192.168.1.102/32
Secondary eth0: 10.100.100.11/32

I would like ALL traffic to go through wifi0 on both machines and if it cant reach it (ie: trying to access 10.100.100.11 from the primary ) then it will send the traffic through eth0

I am guessing its the routing table.  Anyone know?

---

