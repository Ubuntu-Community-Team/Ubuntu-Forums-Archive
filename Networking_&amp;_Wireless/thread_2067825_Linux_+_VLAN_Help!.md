---
title: "Linux + VLAN Help!"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by Brandoo_NZ on 2012-10-07
Hi,

I've got a Ubuntu based router using Shorewall connected to a Level1 switch.

I've set up a VLAN on the switch to tag ports 16 to 24 (VID=2).

The default VLAN on the switch has all ports set to untag.


I've configured the Ubuntu router VLAN interface (eth.2) and assigned an IP address.

The router is plugged in to switch port 3.


When I plug a machine in to a VLAN 2 port and try and ping the Ubuntu interface I get no response - neither ends can see on another.

When I look at the traffic flow, nothing comes in from the VLAN 2, but I can see the router tagging outgoing traffic.


Can anyone give me some tips here please :)

---

