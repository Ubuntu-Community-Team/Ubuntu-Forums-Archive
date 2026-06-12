---
title: "Connectionproblem with iptables + NAT"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by -=)Crazyjoe(=- on 2009-01-15
Hi everyone!

Currently I'm working on replacing my Zyxel Routers routing capability with my Ubuntu 8.04 Server. At the moment the two NICs installed in the server work as a bridge (br0) because they need to replace a switch and have to forward VOIP traffic. eth0 (Realtek Gigabit) is connected with the LAN, eth1 (Netgear Fast Ethernet) is connected with the Zyxel Router. The Bridge is not anonymous (IP and Netmask assigned) because I need to access services on the server.

After setting up the Zyxel for complete bridging I created a PPPoE interface (ppp0) over the bridge interface (br0) using *pppoeconf*, which is functioning perfectly. The problem now lies with *iptables* and NAT, which doesn't work at all!
Traffic that hast to go unaltered to the server (INPUT chain, default policy REJECT) works, but if I try to map this traffic to another port on the server using DNAT connection to the server fails. The same applies to masquerading the outgoing traffic of the LAN which is also completely ignored (Internetconnection out of the LAN doesn't work).

First I thought there's somewhere a mistake in the little "overblown" routing script, so I flushed all the tables and added only the absolut basic functionalty:
```

iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ! ppp0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i br0 -j ACCEPT
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

```

Still with this minimal configuration access from LAN PCs to the Internet is not possible. And yes, "ip_forward" is activated. I'm really confused and don't know what the problem is... :(

---

### Post by superprash2003 on 2009-01-15
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

