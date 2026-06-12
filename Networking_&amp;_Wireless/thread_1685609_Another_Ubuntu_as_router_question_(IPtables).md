---
title: "Another Ubuntu as router question (IPtables)"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by wesg on 2011-02-11
I'm working hard to get my Ubuntu file server act as the network's router, and so far I have DHCP spitting out IP addresses to all the devices on the network. 

Both NICs have IP addresses: 1 is static as the router IP for the network, the other is supplied by the internal DHCP server of the modem. 

Right now I can browse the network without issue, but any outgoing requests get nowhere (pinging both IP addresses for websites and the DNS name). This leads me to believe there is a problem with IPtables and routing, which is why I've supplied all the data from those commands below. 

What might my problem be?

Ifconfig
```
eth0      Link encap:Ethernet  HWaddr <removed> 
          inet addr:192.168.0.xx  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe38:3622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27339653 errors:0 dropped:49 overruns:49 frame:49
          TX packets:43586037 errors:0 dropped:0 overruns:0 carrier:18
          collisions:0 txqueuelen:1000 
          RX bytes:25632473462 (25.6 GB)  TX bytes:45971306043 (45.9 GB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr <removed>
          inet addr:192.168.1.xx  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fe0f:1534/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15610099 (15.6 MB)  TX bytes:10931310 (10.9 MB)
          Interrupt:19 

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.x     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.x     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.x     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

iptables -L
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:<port> 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:isakmp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:<range>
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  192.168.0.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by wesg on 2011-02-12
After rereading the tutorial I was using on this forum, I discovered my problem: didn't enable the masquerade rule for NAT. Did that earlier today, and now I'm surfing through my server! The convenience has already made it worth it, because of the firewall's ability to enable rules without restarting everything.

Now though, my problem is that I can't ping or access my network from the internet. I've set the firewall to accept pings, and opened a number of other ports, but I can't access any of them from my Dynamic DNS setup.

---

