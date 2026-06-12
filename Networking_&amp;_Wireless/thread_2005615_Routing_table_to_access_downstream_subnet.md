---
title: "Routing table to access downstream subnet"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by camper365 on 2012-06-17
I have a server with two NICs that I use to route packets from my modem (172.16.0.254) to my LAN (192.168.2.0/24).  The NICs have IP addresses 172.16.1.12 (eth2) and 192.168.1.2 (eth3).  eth3 connects to a wireless router whose address on the upstream end is 192.168.1.100 and who broadcasts to the 192.168.2.0/24 subnet.  I've attached a diagram of this.
I am trying to I can access the Internet from the 192.168.2.0/24 subnet, but I am unable to access that subnet from the server.  
The server's routing table is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     192.168.1.100   255.255.255.255 UGH   0      0        0 eth3
172.16.0.254    172.16.1.12     255.255.255.255 UGH   0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth3
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth3
0.0.0.0         172.16.0.254    0.0.0.0         UG    0      0        0 eth2

```
but I am unable to ping 192.168.2.1 (the router's local IP address).  When I have the route set up, I get
```

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2009ms

``` The first line sits there until I kill the command.
When I delete the route to 192.168.2.1 I get
```


PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 10.22.12.1 icmp_seq=1 Destination Net Unreachable
From 10.22.12.1 icmp_seq=2 Destination Net Unreachable
From 10.22.12.1 icmp_seq=3 Destination Net Unreachable

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms

```
I think 10.22.12.1 is upstream of the modem since I didn't set it up to exist, so I'm assuming the ping is attempting to be transmitted via eth2 without the route.

How should I configure the routing table so that I can access the downstream subnet from the server?

---

### Post by camper365 on 2012-06-18
bump

---

