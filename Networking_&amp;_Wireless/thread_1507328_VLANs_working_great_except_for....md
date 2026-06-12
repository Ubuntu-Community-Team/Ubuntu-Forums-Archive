---
title: "VLANs working great except for..."
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by Rural on 2010-06-11
So this is interesting. I have a Linux server, switch, and router that are all working great with two VLANs (the default and VLAN 5). The server is visible on both VLANs, mostly for performance reasons, but also to provide DHCPd service. (Yes, I know that I can have the router forward DHCP traffic from one network to the other, but using VLANs on the server seems so much simpler.)

Everything is as you'd expect, all the hosts can ping the server, router, and hosts on their subnet. DHCP works great. Everything is wonderful...except for one thing:

Hosts can't ping (or otherwise access) the server via the non-local subnet.

In more detail: The subnet on the default VLAN is 192.168.40.0/24. The other subnet, 192.168.41.1/24, is on VLAN 5. The server is on both subnets. A host on 192.168.41.0/24, can't ping the server at its address on 192.168.40.0/24. Likewise, a host on 192.168.40.0/24 can't ping the server at its address on 192.168.41.0/24. Everything else works. Pings from hosts to other hosts on either subnet, or either of the router's interfaces work great.

I've done some forensics and discovered something interesting: While running tcpdump on the server, I can see that pings from a subnet to the server's address on the other subnet are received just fine, but no reply is sent. This makes me think that the problem is a configuration issue, or maybe even a feature, of the Linux server.

Any ideas?

---

