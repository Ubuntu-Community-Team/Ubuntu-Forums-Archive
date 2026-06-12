---
title: "dns query  to false host?"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2012-12-12
hi,

this is my current setup:

inet - openwrt - ubuntu router(ur) - switch - clients

openwrt 172.16.0.1
ur eth0 172.16.0.2
ur eth1 192.168.11.1
client1 192.168.11.71

ur's resolve.conf:
nameserver 172.16.0.1

both subnets run over the same unmanaged switch, im unsure if this is safe. some postings on the web say yes, some no. i dont need routing between 172 and 192.

the idea is to get a full fledged linux(ur) for traffic shaping experiments between the network and the internet.

now to the question, if i do a ping from client1
```

ping google.de
PING google.de (173.194.69.94) 56(84) bytes of data.
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=1 ttl=49 time=50.4 m

```i can see this on ur: (eth1 is the interface connecting openwrt and ur)
```

sudo tcpdump -i eth1 icmp

11:56:14.670252 IP 172.16.0.2 > bk-in-f94.1e100.net: ICMP echo request, id 3798, seq 1, length 64

```question: shouldnt the first package go to openwrt's dnsmasq?

looking at what dnsmasq does on ur, it does...but why cant i see that with tcpdump?
```

sudo dnsmasq -C /etc/dnsmasq.conf  -d

dnsmasq: using nameserver 172.16.0.1#53
dnsmasq: read /etc/hosts - 7 addresses
dnsmasq: query[A] google.de from 192.168.11.71
dnsmasq: forwarded google.de to 172.16.0.1
dnsmasq: reply google.de is 173.194.69.94

```

---

### Post by Doug S on 2012-12-12
Since your tcpdump command includes a filter to only capture icmp packets, yes you would not see the DNS traffic. An example, still with filtering, but including DNS traffic:```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth0 icmp or port 53
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-12-12 07:45:37.010479 IP 192.168.111.101.59943 > 192.168.111.1.53: 7697+ A? google.com. (28)
2012-12-12 07:45:37.042785 IP 192.168.111.1.53 > 192.168.111.101.59943: 7697 11/13/0 A 173.194.33.1, A 173.194.33.2, A 173.194.33.3, A 173.194.33.4, A 173.194.33.5, A 173.194.33.6, A 173.194.33.7, A 173.194.33.8, A 173.194.33.9, A 173.194.33.14, A 173.194.33.0 (428)
2012-12-12 07:45:37.056921 IP 192.168.111.101 > 173.194.33.1: ICMP echo request, id 1, seq 40391, length 40
2012-12-12 07:45:37.088973 IP 173.194.33.1 > 192.168.111.101: ICMP echo reply, id 1, seq 40391, length 40
2012-12-12 07:45:38.059101 IP 192.168.111.101 > 173.194.33.1: ICMP echo request, id 1, seq 40392, length 40
2012-12-12 07:45:38.092037 IP 173.194.33.1 > 192.168.111.101: ICMP echo reply, id 1, seq 40392, length 40
```

---

### Post by KisteBecks on 2012-12-22
why did i not see that, i dont know...thx.

---

