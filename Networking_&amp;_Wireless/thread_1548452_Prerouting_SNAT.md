---
title: "Prerouting SNAT?"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by YesWeCan on 2010-08-08
This is either a challenging question that will be fun to answer or I am going about this the wrong way.

I want to SNAT incoming packets on one of my two NICs.

This is because I have different subnets on each NIC. Both NICs subnets have gateways (routers) attached.
eth1 connects only to a router and is used for a gateway to the public internet. This router is the default gateway for my Ubuntu server.
eth0 connects to a set of PCs on a LAN and also to a gateway to another subnet - let's call this subnet Z.

The problem is...if I try to make an SSH connection to the server on eth0 from subnet Z I get no response. I can SSH from the public internet via eth1. I can SSH from a PC on the eth0 LAN.

I have correct port-forwards set up in each router and I have checked my servers firewall.

What I suspect is happening is that the subnet Z PC has a source IP address that the server tries to reply to via the eth1 default gateway. This is because the source address is not in the eth0 subnet range.

Any thoughts?

---

### Post by YesWeCan on 2010-08-08
I should say that what I am trying to do is to have two independent means of remote SSH access to the server. So if one NIC route is broken or down for maintenance I can still log on to the server from the public internet by the other route. I would use different SSH port numbers for each route.

---

### Post by YesWeCan on 2010-08-11
I have done some more reading and Googling. Creating a custom routing table and "marking" packets may be part of the solution.

I have come to realize that I don't properly understand how IP routing works. It seems there are routing tables that pre-exist in the kernel (local, main, default) and it is the "main" table that is shown by 'route -n'. Routing determines the route packets take between NICs and the local application "switchboard".

"IP tables" seems to be something considerably different from "routing tables" although it is able to affect routing too. It seems to facilitate modifying IP packet contents, tracking "connections" and adding new routing.

What I am confused about is the flow diagrams I see describing IP tables behaviour. The flow diagrams suggest that packets enter PREROUTING, then go to either INPUT or OUTPUT and then POSTROUTING. But this is not what I observe when I log packets at each stage. For example, I notice that when an SSH connection is made from an external client that one entry is logged in PREROUTING and then multiple INPUT and OUTPUT entries. Why isn't there one PREROUTING entry for every INPUT entry as a flow diagram suggests? I am starting to wonder whether the PREROUTING and POSTROUTING are different again in nature from INPUT and OUTPUT in that they are only accessed when an initial "connection" is being established. IOW the first time a packet arrives from somewhere it is processed by PREROUTING but all subsequent packets that are part of that connection do not get logged. However, all packets get logged in INPUT and OUTPUT.

The other thing I am unclear about is the relationship between IP tables rules and kernel routing table rules. Which happen when and what order?

For my specific problem I have a situation where I want to make an SSH connection from another client through a specific NIC and router, that is not the default gw as defined in the kernel main routing table. I can make a connection if the client is on the same subnet as the NIC. I cannot make the connection if the client is on a different subnet from the NIC (via a router). Clearly the problem is to do with the routing and the default gw. But when I log in IP tables I can see the client SYN packets in PREROUTING but nothing at all gets logged after that. So what does that mean - that PREROUTING somehow drops the packets before they reach the SSH server application? But I haven't told IP tables to drop anything in PREROUTING. Or is it that the "connection" is a separate thing from packet flow and SYN and ACK are not actually routed packets at all but something dealt with separately?

I have read quite quite a few tutorials now and I still don't get it. Can anyone help the penny to drop for me?

---

