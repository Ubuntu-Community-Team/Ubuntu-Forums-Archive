---
title: "Cluster Setup: LAN to Internet via Gateway"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by fexar on 2013-02-13
I've set up a Beowulf Linux cluster (9 nodes) running Ubuntu 12.04 LTS. The machines are networked on an internal LAN through a switch, and routed through one of the machines to a university-wide network for Internet access. The internet works fine, but some proprietary software requires network licenses to run and the license requests aren't getting routed. I'm relatively inexperienced with iptables and firewalls, although I've tried to read numerous tutorials on these matters to no avail.

Right now my iptables has no rules specified. On the gateway machine, eth0 is the device connecting to the 'net and eth1 is to the LAN. I have the license server addresses and ports, but I can't figure out how to route requests from the LAN to the license server and back. Any pointers on what I should be doing? Thanks.

Edit: To clarify, my iptables has one user-defined rule to enable routing:

```
Chain PREROUTING (policy ACCEPT 69 packets, 4934 bytes)
 pkts bytes target     prot opt in     out     source            destination

Chain INPUT (policy ACCEPT 11 packets, 1092 bytes)
 pkts bytes target     prot opt in     out     source            destination

Chain OUTPUT (policy ACCEPT 2 packets, 124 bytes)
 pkts bytes target     prot opt in     out     source            destination

Chain POSTROUTING (policy ACCEPT 2 packets, 124 bytes)
 pkts bytes target     prot opt in     out     source            destination
    0     0 MASQUERADE  all  --  any    eth0                      anywhere
```

---

### Post by fexar on 2013-02-13
I've tried adding the following rules and I can see packets/bytes going through the udp protocol when I try to launch the software, but it is still not connecting to the license server. Is there a rule I need to enable to receive the response from the license server?

```
sudo iptables -t nat -A POSTROUTING -p tcp -o eth0 -j MASQUERADE --to-ports <port#>
sudo iptables -t nat -A POSTROUTING -p udp -o eth0 -j MASQUERADE --to-ports <port#>
```

---

### Post by fexar on 2013-02-14
Issue has been resolved.

Just in case anyone refers to this later:

The only iptables rule needing set is (without any security)

[FONT=Courier New]sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE[/FONT]

I was resolving Google's DNS servers (8.8.8.8 and 8.8.4.4) when I should have been using the University network DNS servers as the licenses were trying to resolve addresses not in the public domain. Lesson learned: CHECK YOUR DNS nameservers.

---

