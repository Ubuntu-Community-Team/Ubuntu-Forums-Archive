---
title: "Iptables rules, forward between two interfaces"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by dunsscoto on 2011-08-23
Hi everyone, i have a some difficulties in configuring my ubuntu server firewall ... 
My situation is this:

eth0 -> internet
eth1 -> lan1
eth2 -> lan2

I want that clients from lan1 can't communicate with clients from lan2, except for some specific services. E.g. i want that clients in lan1 can ssh into client in lan2, but only that. Any other comunication is forbidden.

So, i add this rules to iptables:
```
#Block all traffic between lan, but permit traffic to internet
iptables -I FORWARD -i eth1 -o ! eth0 -j DROP
iptables -I FORWARD -i eth2 -o ! eth0 -j DROP
# Accept ssh traffic from lan1 to client 192.168.20.2 in lan2
iptables -A FORWARD -i eth1 -o eth2 -p tcp --dport 22 -d 192.168.20.2 -j ACCEPT

```

This didn't works. Doing iptables -L FORWARD -v i see:
```
Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    33   144 DROP       all  --  eth1 !eth0   anywhere             anywhere
    0     0 DROP       all  --  eth2 !eth0   anywhere             anywhere
23630   20M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  eth1   any     anywhere             anywhere
  175  9957 ACCEPT     all  --  eth1 any     anywhere             anywhere
  107  6420 ACCEPT     all  --  eth2 any     anywhere             anywhere
    0     0 ACCEPT     all  --  pptp+  any     anywhere             anywhere
    0     0 ACCEPT     all  --  tun+   any     anywhere             anywhere
    0     0 ACCEPT     tcp  --  eth1 eth2  anywhere             server2.lan tcp dpt:ssh

```

All packets are dropped, and the count of packets for the last rule is 0 ... 

How i have to modify my configuration? Thank you.

Regards
Duns

---

