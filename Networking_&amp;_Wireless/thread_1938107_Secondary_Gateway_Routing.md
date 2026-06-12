---
title: "Secondary Gateway Routing"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by hmsdexter on 2012-03-09
I am having trouble setting up a route for my connection to work.

I have an extensive wireless network linking a couple of houses.
The Internet Connection is in house1 
It is connected to a server running Ubuntu (Zentyal) 
---External IP 10.3.52.1
---Internal IP 10.0.0.1

From there I run via a two hops Ubiquiti Wireless network to house2
at house2 i have a wireless link to my work
---internal ip: 10.0.0.2
---extrnal network: 192.168.0.0/24


If I use 10.0.0.2 as my gateway on a pc, i can access the work network (192.168.0.0/16)

I set up a route in /etc/network/interfaces as
```
up route add -net 192.168.0.0/16 gw 10.0.0.2 dev eth2
```

when I ping an address at work ie 192.168.60.4 
I get:
```
From 10.0.1.3: icmp_seq=1 Redirect Host(New nexthop: 10.0.0.1)
From 10.0.1.6: icmp_seq=1 Redirect Host(New nexthop: 10.0.0.1)

```

traceroute gives me:
```
traceroute to 192.168.60.4 (192.168.60.4), 30 hops max, 60 byte packets
 1  10.0.1.6 (10.0.1.6)  12.183 ms  12.236 ms  12.342 ms
 2  10.0.1.3 (10.0.1.3)  12.572 ms  15.315 ms  15.313 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
```

---

