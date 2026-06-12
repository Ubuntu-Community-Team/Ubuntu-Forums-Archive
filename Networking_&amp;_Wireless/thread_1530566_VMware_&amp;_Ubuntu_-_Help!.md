---
title: "VMware &amp; Ubuntu - Help!"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by impendingVOID on 2010-07-13
I have a guest machine running Kubuntu 10.04, the IP address is 192.168.104.171

The guest OS is server 2008, it has two interfaces, Bridged:192.168.104.180 and Host-Only:10.0.0.10.

There are several client clients in the 10.0.0.x address range.

Server2008 has Routing and Remote access enabled. I have Lan routing enabled.

I can ping Kubuntu from any Windows client and Server 2008

I can ping the Bridged interface in Server 2008 from Kubuntu.

I cannot ping the Host only interface from Kubuntu.

I want to be able to ping the 10.0.0.x network from kubuntu, going *through* the Bridged interface.

I am unsure if this is a problem with Kubuntu not knowing how to handle 10.0.0.x addresses (Like a DNS problem) OR if it a problem with Server2008 not passing requests through to the 10.0.0.x address.

Any ideas on how to solve this problem?

Cheers,

Mark.

---

