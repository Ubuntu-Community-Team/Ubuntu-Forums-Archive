---
title: "OpenVPN routing problem between tun &amp; tap devices"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by tiburcillo on 2009-11-03
Hi all,

I'm having a problem creating a route between different networks terminating on one Ubuntu machine with openVPN installed.
Here's a quick overview of the network.

My machine is connected as a OpenVPN Client (tap) to Network 10.0.0.0/24 (IP addr = 10.0.0.142)
My machine is serving the OpenVPN (tun) network 192.168.10.0/24 (IP addr = 192.168.10.1)
My machine is connected to the Internet via a regular network card with network 172.17.1.128/25 (IP addr = 172.17.1.136).

Here's my the output of route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.2    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.10.0    192.168.10.2    255.255.255.192 UG    0      0        0 tun0
172.17.1.128    0.0.0.0         255.255.255.128 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tap0
0.0.0.0         172.17.1.129    0.0.0.0         UG    100    0        0 eth0
```

I've enabled packet forwarding: cat /proc/sys/net/ipv4/ip_forward outputs "1"

Currently i'm not using the 192.168.10.2 network. I'm trying to reach a computer in the physical network (172.17.1.x) from a pc in the 10.0.0.0 network.
On that _(windows)_ machine i've added the following route to make that possible:
```
route add 172.17.1.128 mask 255.255.255.128 10.0.0.142
```

When i ping a machine in my server's network (e.g. 172.17.1.144) i can't find a route to the destination. If i ping to the ip address of the physical network (172.17.1.136) than it works... 
```

Running as user "root" and group "root". This could be dangerous.
Capturing on Pseudo-device that captures on all interfaces
  6.313354   10.0.0.141 -> 172.17.1.144 ICMP Echo (ping) request
  6.313371   10.0.0.141 -> 172.17.1.144 ICMP Echo (ping) request
 13.862967   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 13.862983 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 14.862636   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 14.862652 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 15.864315   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 15.864330 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 16.870349   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 16.870364 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply

```
There's no firewall enabled on the ubuntu server. Am I missing something here?

---

### Post by iponeverything on 2009-11-03
> **tiburcillo said:**
> Hi all,

When i ping a machine in my server's network (e.g. 172.17.1.144) i can't find a route to the destination. If i ping to the ip address of the physical network (172.17.1.136) than it works... 
```

Running as user "root" and group "root". This could be dangerous.
Capturing on Pseudo-device that captures on all interfaces
  6.313354   10.0.0.141 -> 172.17.1.144 ICMP Echo (ping) request
  6.313371   10.0.0.141 -> 172.17.1.144 ICMP Echo (ping) request
 13.862967   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 13.862983 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 14.862636   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 14.862652 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 15.864315   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 15.864330 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply
 16.870349   10.0.0.141 -> 172.17.1.136 ICMP Echo (ping) request
 16.870364 172.17.1.136 -> 10.0.0.141   ICMP Echo (ping) reply

```
There's no firewall enabled on the ubuntu server. Am I missing something here?

Does the host at 172.17.1.144 have a route to the 10.0.0.0/24 network via 172.17.1.136? --------- 172.17.1.136 knows about 10.0.0.0/24 because it's directly connected.

---

