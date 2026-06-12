---
title: "Router Ubuntu Not forwarding packets !"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by ritazreiby on 2013-06-14
i have set a router using ubuntu.
we have dhcpv6 running and radvd smoothly.
the IPV6 Lan behind the eth1 have the prefix 2a00:1580:8000:6::/64
the router is linked to a gateway with the adress 2a00:1580:8000::1/48 through the interface  eth2 hat has the address 2a00:1580:8000::2/48

the router is accessing the ipv6 internet.(and pinging the gateway)
the hosts can ping both the interface eth1 and eth2 of the router. but they can't reach the gateway.
we have added a route by default to the gateway through eth2.

and IPv6 forwarding is set to 1...

No clue what to do... please help !! 


our routing table look like this :

Destination                    Next Hop                   Flag Met Ref Use If
64:ff9b::/96                   ::                         U    1024 0     0 nat64
2a00:1580:8000:6::/64          ::                         U    256 0     0 eth1
2a00:1580:8000:6::/64          ::                         U    1024 0     0 eth1
2a00:1580:8000::/48            ::                         U    256 0     2 eth2
fe80::/64                      ::                         U    256 0     0 eth1
fe80::/64                      ::                         U    256 0     0 eth2
fe80::/64                      ::                         U    256 0     0 nat64
::/0                           2a00:1580:8000::1          UG   1024 0     0 eth2

---

