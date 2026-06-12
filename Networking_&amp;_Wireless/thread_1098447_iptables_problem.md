---
title: "iptables problem"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by poscaman on 2009-03-17
hi there. i'm setting up a linux gateway.i'm using dansguardian and squid3.
i have the following iptables.
```

iptables -F
#FireWalling Router-GateWay------#
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 5/s --limit-burst 10 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type ! echo-request -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp --dport 3128 -j ACCEPT
iptables -P INPUT DROP
#end-----------------------------#

#port-forwading for a client
iptables -t nat -A PREROUTING  -i ppp0 -s 0.0.0.0/0 -m state --state NEW -p tcp --dport 8000   -j DNAT --to-destination 172.16.0.10
iptables -t nat -A PREROUTING  -i ppp0 -s 0.0.0.0/0 -m state --state NEW -p tcp --dport 80   -j DNAT --to-destination 172.16.0.10
#END of...............

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE 
iptables -t nat -I PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -i ath0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

i'm succesfully connecting through dansguardian from local lan (eth1) but i'm totally unable to use dansguardian with (ath0) wireless clients.

what should i modify in order to enable wireless access to dansguardian?

ip ro:
```
194.219.231.61 dev ppp0  proto kernel  scope link  src 77.49.30.37 
10.10.10.13 dev tun0  proto kernel  scope link  src 10.10.10.14 
172.16.100.0/24 dev ath0  proto kernel  scope link  src 172.16.100.1 
172.16.0.0/24 dev eth1  proto kernel  scope link  src 172.16.0.1 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.100 
10.10.10.0/24 via 10.10.10.13 dev tun0 
default dev ppp0  scope link 
```

---

### Post by kevdog on 2009-03-17
Are eth1 and ath0 up at the same time?  Seems like since rules are applied in sequential order that it will never get to the ath0 rule since eth1 immediately preceeds the ath0 rule.  A way to check would be to reverse the last two statements.

---

### Post by poscaman on 2009-03-17
> **kevdog said:**
> Are eth1 and ath0 up at the same time?  Seems like since rules are applied in sequential order that it will never get to the ath0 rule since eth1 immediately preceeds the ath0 rule.  A way to check would be to reverse the last two statements.

thanks for your help. the actual problem was with dansguardian. i had to replace ```
filterip =172.16.0.1
``` with 
```
filterip =172.16.0.1
filterip = 172.16.100.1

```in dansguardian.conf

now, iptables look like:
```
iptables -F

#FireWalling Router-GateWay------#
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 5/s --limit-burst 10 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type ! echo-request -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -P INPUT DROP
#end-----------------------------#

#port-forwading for a client
iptables -t nat -A PREROUTING  -i ppp0 -s 0.0.0.0/0 -m state --state NEW -p tcp --dport 8000   -j DNAT --to-destination 172.16.0.10
iptables -t nat -A PREROUTING  -i ppp0 -s 0.0.0.0/0 -m state --state NEW -p tcp --dport 80   -j DNAT --to-destination 172.16.0.10
#END of...............

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -t nat -I PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -I PREROUTING -i ath0 -p tcp --dport 80 -j REDIRECT --to-port 8080

```

---

