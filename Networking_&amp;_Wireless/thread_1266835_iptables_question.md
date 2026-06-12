---
title: "iptables question"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by MAKAPOH on 2009-09-15
Hello!

I am have 3 interfaces:
eth0 - ISP Network 10.126.1.0/24 10.126.1.244
eth0:1 - Alias in ISP Network 10.126.1.234
eth3 - home network 192.168.1.0/24 192.168.1.100

how to forward all packets from 192.168.1.7 to eth0:1 and from eth0:1 to 192.168.1.7? All packets from other hosts 192.168.1.* should be forwarded to eth0

> *nat
:OUTPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -i eth0:1 -j DNAT --to-destination 192.168.1.7
-A POSTROUTING -o eth0 -j MASQUERADE
-A POSTROUTING -o eth0:1 -j MASQUERADE
-A POSTROUTING -s 192.168.1.7 -j SNAT --to-source 10.126.1.234
COMMIT

*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i eth3 -o eth0 -j ACCEPT
-A FORWARD -i eth3 -o eth0:1 -j ACCEPT
COMMIT


---

### Post by fwre01 on 2009-09-15
Hi MAKAPOH. iptables doesnt allow you to use an alias in a NAT rule like that. 

You still need the alias eth0:1 for arp reasons, but your rules must look like this, - or at least these worked for me - I havent written the filter rules, i just left those open

```
iptables -t nat -A POSTROUTING -s 192.168.1.7 -o eth0 -j SNAT --to-source 10.126.1.234
iptables -t nat -A PREROUTING -d 10.126.1.234 -j DNAT --to-destination 192.168.1.7
iptables -t nat -A POSTROUTING -s ! 192.168.1.7 -o eth0 -j MASQUERADE
```

The top two rules acheive the static bi-directional NAT and the third line achieves the Port Address Translation on eth0 for everything except .7

---

