---
title: "Looking for best practice (Routing/bridge/tunnel)?"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by mvip on 2009-02-16
Hello fellow Ubuntuists,

I'm turning to the community to ask about the best practice for a network setup. I have an 8.04 LTS machine sitting as a router with VMware Server running. What I want to achieve is illustrated in the attached diagram.

I have three interfaces set up
[LIST]
[*]eth0 -- Physical network (192.168.10.1)
[*]eth0:0 -- VMware network (192.168.11.1)
[*]eth1 -- Internet
[/LIST]

If it wasn't for the eth0:0, this would have been dead simple, but I want to make sure that eth0 and eth0:0 cannot communicate with each other, but both can both access the internet. Some of the VMware guests will be accessed over the internet through some straight forward port-forwarding.

According to my research, there are basically three ways to do this (with the combination of a firewall); standard routing, bridging or tunneling. I just want to reach out to the community to see what the best practice is.

---

### Post by mvip on 2009-02-16
Sorry for replying to my own thread, but maybe the easiest (and possibly best) solution is to set a strict subnet (255.255.255.255) on eth0 and eth0:0 and then block the traffic between the two subnets with iptables rule.

---

