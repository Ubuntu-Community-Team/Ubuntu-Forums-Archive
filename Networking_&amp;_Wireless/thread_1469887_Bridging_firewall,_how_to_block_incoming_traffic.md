---
title: "Bridging firewall, how to block incoming traffic"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Zyprexa on 2010-05-02
Im having problems with iptables not doing what i want :(

I have a ubuntu computer set up as bridge between gateway and lan, with the lan connected to eth0 and gateway on eth1.

I'm trying to get it to basically block everything incoming except for the ports i specify, but also allow outgoing traffic. I've found, tried, modified som examples i found on the web, but still it wont block incoming traffic (ie, im still able to reach my webserver)

These are the rules, and i can't figure out why it wont block:

```
#!/bin/bash

iptables -F
iptables -X

iptables -I INPUT -i eth1 -j DROP
iptables -I INPUT -i eth0 -j DROP
iptables -I OUTPUT -o eth1 -j REJECT
iptables -I OUTPUT -o eth0 -j REJECT

# connection tracking
iptables -I FORWARD -m state --state INVALID -j DROP
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT

# allow outgoing traffic
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# allow ping
iptables -A FORWARD -p icmp -i eth0 -o eth1 -j ACCEPT
# stop incoming
iptables -A FORWARD -i eth1 -o eth0 -j REJECT
```

*iptables -S* gives me
```
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -i eth0 -j DROP
-A INPUT -i eth1 -j DROP
-A FORWARD -m state --state INVALID -j DROP
-A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth0 -o eth1 -j ACCEPT
-A FORWARD -i eth0 -o eth1 -p icmp -j ACCEPT
-A FORWARD -i eth1 -o eth0 -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -o eth0 -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -o eth1 -j REJECT --reject-with icmp-port-unreachable
```

Any advice on what im doing wrong is appreciated :(

---

### Post by jpl888 on 2010-05-14
Ok well I assume you have br0 setup and both those interfaces added to it?

To get the rules you have working you will need to use the physdev option, extract from ebtables website:-

> The 2.6 standard kernel contains an iptables match module called physdev which has to be used to match the bridge's physical in and out ports. Its basic usage is simple (see the iptables man page for more details):

iptables -m physdev --physdev-in <bridge-port>
and

iptables -m physdev --physdev-out <bridge-port>

BTW I haven't done this myself, only thinking of it so there may be additional steps and considerations I haven't come across.

---

