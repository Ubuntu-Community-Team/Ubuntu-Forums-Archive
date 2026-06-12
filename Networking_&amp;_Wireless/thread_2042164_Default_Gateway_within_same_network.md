---
title: "Default Gateway within same network"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by hl2x on 2012-08-14
Hello everybody,

in my network, I have multiple systems sharing a virutal router ip via keepalived. This IP - let's call it 105 - is only assigned to the MASTER of this cluster. Every other system in the routed network will use 105 as default gateway.

Now here is my problem: the systems that are BACKUP in the cluster may also want to access hosts in this network. Since they have an interface and an IP in the net, they will directly talk to the other hosts. But: the other hosts reply to 105 as gateway, which results in ambiguous packet routes. Since the MASTER is also a firewall, it will not recognize that the incoming packets may belong to a connection and drops them.

So what I need is a configuration for every node in the cluster that expresses something like: if you don't have IP 105, use 105 as default gateway for the network (although you are already participant in this network).

Is this possible?

---

