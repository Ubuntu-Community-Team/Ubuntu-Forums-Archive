---
title: "problem with 2 NIC at same network"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by lui90 on 2009-05-04
Hello everybody,
I've problem with my server which have 2 NIC connected at same network
 
example: 
eth0 192.168.1.100 
eth1 192.168.1.101
 
Gateway 192.168.1.1
 
at first I only eth0 to transfer data and it work fine, but when I make it down and connect the another interface ,eth1 , it doesn't work. 
 
At first with eth0
```

#ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
64 bytes from 192.168.1.1: seq=0 ttl=254 time=7.333 ms
64 bytes from 192.168.1.1: seq=1 ttl=254 time=7.124 ms

```
 
after when I make down eth0 
```
ifconfig eth0 down
```
 
(eth1 is up)
```

#ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
From 192.168.1.100 icmp_seq=2  Destinarion Host Unreachable
From 192.168.1.100 icmp_seq=3  Destinarion Host Unreachable
From 192.168.1.100 icmp_seq=4  Destinarion Host Unreachable

```
 
I think that it is trying to connect to eth0 and not to eth1. ¿?
 
Routing table is good
```

192.168.1.0 * 255.255.255.0 eth1
default 192.168.1.1 0.0.0.0 eth1

```
 
 
How I can resolv it ¿?
 
Another way that not be restarting /etc/init.d/networking ¿?
something like flush the cache??
 
Sorry, my english is very bad ..
 
thx.

---

### Post by Iowan on 2009-05-04
Although I've seen threads about bridging, it generally seems to be a problem when two NIC's share the same subnet - plays havoc with routing. Is there a particular reason why both NIC's *need* to be on the same subnet?

---

### Post by DGortze380 on 2009-05-04
> **lui90 said:**
> Hello everybody,
I've problem with my server which have 2 NIC connected at same network
 
example: 
eth0 192.168.1.100 
eth1 192.168.1.101
 
Gateway 192.168.1.1
 
at first I only eth0 to transfer data and it work fine, but when I make it down and connect the another interface ,eth1 , it doesn't work. 
 
At first with eth0
```

#ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
64 bytes from 192.168.1.1: seq=0 ttl=254 time=7.333 ms
64 bytes from 192.168.1.1: seq=1 ttl=254 time=7.124 ms

```
 
after when I make down eth0 
```
ifconfig eth0 down
```
 
(eth1 is up)
```

#ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
From 192.168.1.100 icmp_seq=2  Destinarion Host Unreachable
From 192.168.1.100 icmp_seq=3  Destinarion Host Unreachable
From 192.168.1.100 icmp_seq=4  Destinarion Host Unreachable

```
 
I think that it is trying to connect to eth0 and not to eth1. ¿?
 
Routing table is good
```

192.168.1.0 * 255.255.255.0 eth1
default 192.168.1.1 0.0.0.0 eth1

```
 
 
How I can resolv it ¿?
 
Another way that not be restarting /etc/init.d/networking ¿?
something like flush the cache??
 
Sorry, my english is very bad ..
 
thx.

can you post the output of

cat /etc/network/interfaces

You'll likely need a static route for eth1

Is there a reason for the two physical NICs? A Virtual NIC may serve you better with less hassle.

---

