---
title: "connectivity between two network using ubuntu as router"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by tanveer on 2010-11-28
Hi all,

I actually have two networks (192.168.100.0 and 192.168.200.0) and configured ubuntu as a router. Now the problem is I can ping both ip blocks from router machine but can't ping from one network to another using router.

Below are the details:[PHP]
~$ ifconfig | grep "inet addr"
          inet addr:192.168.100.30  Bcast:192.168.100.255  Mask:255.255.255.0
          inet addr:192.168.200.30  Bcast:192.168.200.255  Mask:255.255.255.0
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth2
192.168.200.0   0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.2.2        0.0.0.0         UG    0      0        0 eth2
~$ ping 192.168.100.5
PING 192.168.100.5 (192.168.100.5) 56(84) bytes of data.
64 bytes from 192.168.100.5: icmp_req=1 ttl=128 time=1.09 ms
64 bytes from 192.168.100.5: icmp_req=2 ttl=128 time=8.24 ms
^C
--- 192.168.100.5 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 1.093/4.670/8.247/3.577 ms

~$ ping 192.168.200.20
PING 192.168.200.20 (192.168.200.20) 56(84) bytes of data.
64 bytes from 192.168.200.20: icmp_req=1 ttl=64 time=1.16 ms
^C
--- 192.168.200.20 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.169/1.169/1.169/0.000 ms
~$ 
[/PHP]
I enabled Ip forwarding:
~$ cat /proc/sys/net/ipv4/ip_forward 
1

Now what to add as gateway in those two nics and the route command. Should I add 192.168.100.30 GW for eth1 and vice versa and the below routing commands.
~$ ip route add 192.168.100.0/24 via 192.168.200.30 dev eth1
~$ ip route add 192.168.200.0/24 via 192.168.100.30 dev eth0

thank you.

---

### Post by cybergnome on 2010-11-28
The point in having two networks with IPs as you've assigned is that they don't see each other.  Enabling routing is only one of the issues in connecting them; you need to bridge them as well.  The simpler solution for a small network is to change the IP ranges to match.

---

