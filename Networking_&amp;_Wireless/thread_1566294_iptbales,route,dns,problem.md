---
title: "iptbales,route,dns,problem"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by jakob_kh on 2010-09-02
HI!
I have a problem with complete understanding of iptables, routing and dns. I wish someone would help me with it.

So, I am running [SIZE=2]Ubuntu 10.04[/SIZE] and use it as an Internet gateway. I have 3 interfaces: 
[SIZE=2]eth0[/SIZE] address [SIZE=2]172.16.0.1[/SIZE] looks into the first local subnetwork[SIZE=2] 172.16.0.0/24.[/SIZE]
[SIZE=2]eth1[/SIZE] address [SIZE=2]192.168.0.1[/SIZE]  looks into the second  local subnetwork [SIZE=2]192.168.0.0/24[/SIZE].
and the third one [SIZE=2]wimax0[/SIZE] looks into Internet, address is assigned by [SIZE=2]dhcp [/SIZE]of provider

[SIZE=2]I want all subnetworks be able to see each other and have an access to the Internet.[/SIZE]

Here is a result of route:
```

[SIZE=2]server:~$ route[/SIZE]
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.0.0    *               255.255.255.0 U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
10.151.0.0      *               255.255.240.0   U     0      0        0 wimax0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         localhost       0.0.0.0         UG    0      0        0 wimax0

```for iptables I have a script executing on boot up

```

#!/bin/sh

iptables -F
iptables -t nat -F

iptables -t nat -A POSTROUTING   -o wimax0 -j MASQUERADE

iptables -t nat -A POSTROUTING  -s 192.168.0.0/24 -d 172.16.0.0/24 -o eth0 -j SNAT --to-source 172.16.0.1

iptables -t nat -A POSTROUTING  -s 172.16.0.0/24 -d 192.168.0.0/24 -o eth1 -j SNAT --to-source 192.168.0.1

```As a result my subnetworks have an access to the Internet and ping each other. But they can't communicate via tcp/ip. 
And I have a problem with dns because. I can ping from one subnet to another only with explicit IP. (not a name of pc).

Thanks in advance for any help or hint.

---

### Post by clrg on 2010-09-02
ICMP uses IP, but don't tell anyone.

---

### Post by BkkBonanza on 2010-09-02
I don't see why you would set up SNAT between your two subnets but not to the wimax0 (internet)? You should have no SNAT within your own address spaces and should have SNAT to the internet where it is needed.

As an example here is my router setup script which is run during init.
```

#!/bin/bash

WANIF=eth0
LANIF=eth1
WANIP="`/sbin/ifconfig $WANIF | grep 'inet addr' | awk '{print $LANIF}' | sed -e 's/.*://'`"

echo "1" > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A POSTROUTING -o $WANIF -j MASQUERADE
iptables -t nat -A POSTROUTING -o $WANIF -j SNAT --to $WANIP
iptables -A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $LANIF -o $WANIF -j ACCEPT

service dnsmasq restart
```

Note, I use dnsmasq to handle dhcp/dns within my network. Since you have a second subnet you would add a couple more lines for LANIF2 similar to LANIF.

---

