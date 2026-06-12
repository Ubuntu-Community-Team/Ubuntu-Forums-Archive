---
title: "Problem with OpenVPN / Route"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by xMaximex on 2008-12-22
Hi,

I have a route problem with OpenVPN.

Here's my config:

Server:
```
eth0      Link encap:Ethernet  HWaddr 00:40:63:c1:a0:8f
          inet addr:192.168.0.125  Bcast:192.168.0.127  Mask:255.255.255.128

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.10.10.1  P-t-P:10.10.10.2  Mask:255.255.255.255
```

Client:
```
eth1      Link encap:Ethernet  HWaddr 00:c0:f0:2c:ae:91
          inet addr:192.168.2.19  Bcast:192.168.2.255  Mask:255.255.255.0

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.10.10.26  P-t-P:10.10.10.25  Mask:255.255.255.255
```


Routing table on server:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.2      *               255.255.255.255 UH    0      0        0 tun0
X.X.X.X         *               255.255.255.252 U     0      0        0 eth1
192.168.0.0     *               255.255.255.128 U     0      0        0 eth0
192.168.2.0     10.10.10.2      255.255.255.0   UG    0      0        0 tun0
10.10.10.0      10.10.10.2      255.255.255.0   UG    0      0        0 tun0
default         X.X.X.X         0.0.0.0         UG    100    0        0 eth1
```

Routing table on client:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.25     *               255.255.255.255 UH    0      0        0 tun0
localnet        *               255.255.255.248 U     0      0        0 eth0
192.168.0.0     10.10.10.25     255.255.255.128 UG    0      0        0 tun0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
10.10.10.0      10.10.10.25     255.255.255.0   UG    0      0        0 tun0
default         X.X.X.X         0.0.0.0         UG    100    0        0 eth0
```

Both can ping other's OVPN IP (10.10.10.X) so the tunnel is up and working.

Client can ping server:
```
PING 192.168.0.125 (192.168.0.125) 56(84) bytes of data.
64 bytes from 192.168.0.125: icmp_seq=1 ttl=64 time=66.7 ms
64 bytes from 192.168.0.125: icmp_seq=2 ttl=64 time=93.9 ms
64 bytes from 192.168.0.125: icmp_seq=3 ttl=64 time=63.7 ms
64 bytes from 192.168.0.125: icmp_seq=4 ttl=64 time=61.4 ms

--- 192.168.0.125 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 61.431/71.501/93.993/13.124 ms
```

Server can't ping client:
```
PING 192.168.2.19 (192.168.2.19) 56(84) bytes of data.

--- 192.168.2.19 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

Traceroute from client to server:
```
traceroute to 192.168.2.19 (192.168.2.19), 30 hops max, 40 byte packets
 1  192.168.2.19 (192.168.2.19)  0.203 ms  0.062 ms  0.051 ms
```

Traceroute from server to client:
```
traceroute to 192.168.2.19 (192.168.2.19), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
```


There's no iptables rules on client side. I double checked those on server's side but nothing seems to be a problem.

Can someone help me with this ? It's driving me crazy

---

### Post by mpokrywka on 2008-12-22
Use tcpdump to check where packets go:
**sudo tcpdump -ni eth0**

---

### Post by xMaximex on 2009-01-06
tcpdump -ni tun0 on the server while I ping the client:

```
PING 192.168.2.19 (192.168.2.19) 56(84) bytes of data.

--- 192.168.2.19 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3010ms

```

```
tcpdump: listening on tun0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
12:53:47.999171 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.1 > 192.168.2.19: ICMP echo request, id 17963, seq 1, length 64
12:53:49.009045 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.1 > 192.168.2.19: ICMP echo request, id 17963, seq 2, length 64
12:53:50.009106 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.1 > 192.168.2.19: ICMP echo request, id 17963, seq 3, length 64
12:53:51.009139 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.1 > 192.168.2.19: ICMP echo request, id 17963, seq 4, length 64

```

tcpdump -ni tun0 on the client while I ping the server:

```
PING 192.168.0.125 (192.168.0.125) 56(84) bytes of data.
64 bytes from 192.168.0.125: icmp_seq=1 ttl=64 time=203 ms
64 bytes from 192.168.0.125: icmp_seq=2 ttl=64 time=213 ms
64 bytes from 192.168.0.125: icmp_seq=3 ttl=64 time=185 ms
64 bytes from 192.168.0.125: icmp_seq=4 ttl=64 time=190 ms

```

```
listening on tun0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
12:56:37.878569 IP 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 1, length 64
12:56:38.082195 IP 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 1, length 64
12:56:38.877529 IP 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 2, length 64
12:56:39.090533 IP 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 2, length 64
12:56:39.877344 IP 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 3, length 64
12:56:40.062280 IP 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 3, length 64
12:56:40.877428 IP 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 4, length 64
12:56:41.068072 IP 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 4, length 64

```

EDIT: I forgot to paste the server's tcpdump output while client ping it:

```
12:55:19.010861 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 1, length 64
12:55:19.011001 IP (tos 0x0, ttl 64, id 16689, offset 0, flags [none], proto ICMP (1), length 84) 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 1, length 64
12:55:20.013466 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 2, length 64
12:55:20.013560 IP (tos 0x0, ttl 64, id 16690, offset 0, flags [none], proto ICMP (1), length 84) 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 2, length 64
12:55:21.012579 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 3, length 64
12:55:21.012672 IP (tos 0x0, ttl 64, id 16691, offset 0, flags [none], proto ICMP (1), length 84) 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 3, length 64
12:55:22.013762 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.10.10.26 > 192.168.0.125: ICMP echo request, id 27170, seq 4, length 64
12:55:22.013869 IP (tos 0x0, ttl 64, id 16692, offset 0, flags [none], proto ICMP (1), length 84) 192.168.0.125 > 10.10.10.26: ICMP echo reply, id 27170, seq 4, length 64

```

---

### Post by xMaximex on 2009-01-08
I found the problem.

I needed to add the file /etc/openvpn/ccd/"clientCommonName"

echo "iroute 192.168.2.0 255.255.255.0" > /etc/openvpn/ccd/"clientCommonName"

Along with "client-config-dir ccd" in /etc/openvpn/server.conf

And it works !

---

