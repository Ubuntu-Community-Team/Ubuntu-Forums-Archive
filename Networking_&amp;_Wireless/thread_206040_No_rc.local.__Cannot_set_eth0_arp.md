---
title: "No rc.local.  Cannot set eth0 arp"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by fopetesl on 2006-06-29
Breezy.
I am 'upgrading' from MDK10 to Breezy.
   [COLOR="Green"]eth0 static 192.168.1.20 netmask 25.255.0.0 broadcast 192.168.255.255[/COLOR]
to communicate with a mini controller via crossover which has fixed IP: 192.168.1.6.

I am using a similar NIC and the same network cable with both machines.

The Mandrake machine works fine but Breezy ping gives me message:
```
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data
From 192.168.1.20 icmp_seq=2 Destination Host Unreachable
.
.
```

Breezy pings DHCP server without problem:
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
64 bytes from 192.168.1.1 icmp_seq=2 ttl-255 time=2.30 mS
.
.
```

In the Mandrake machine there is an [COLOR="Blue"]rc.local[/COLOR] with the last lines:
```
/sbin/ifconfig eth0 192.168.1.20 netmask 255.255.0.0
/sbin/arp -s 192.168.1.6 00:04:a3:00:a9:f9
/bin/ping -c 4 192.168.1.6
```If I comment out the 'arp' line above I get the same failure from the Mandrake machine.

I have no [COLOR="Blue"]rc.local[/COLOR], where do I put the [COLOR="Blue"]arp[/COLOR] instruction?](*,)

---

