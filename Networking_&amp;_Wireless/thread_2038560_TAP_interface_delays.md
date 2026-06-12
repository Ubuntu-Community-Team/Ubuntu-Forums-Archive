---
title: "TAP interface delays"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by TheGrave on 2012-08-06
I have a strange issue with the tap interface. Initially everything  works fine, then it stops for a while, then traffic is returned with  huge delay. No iptables rules, apart from this all other network interfaces run fine.

```

64 bytes from 192.168.100.11: icmp_req=135 ttl=64 time=1.21 ms
64 bytes from 192.168.100.11: icmp_req=136 ttl=64 time=7.49 ms
64 bytes from 192.168.100.11: icmp_req=137 ttl=64 time=6.34 ms
From 192.168.100.100 icmp_seq=182 Destination Host Unreachable
From 192.168.100.100 icmp_seq=183 Destination Host Unreachable
From 192.168.100.100 icmp_seq=184 Destination Host Unreachable
From 192.168.100.100 icmp_seq=185 Destination Host Unreachable
From 192.168.100.100 icmp_seq=186 Destination Host Unreachable
From 192.168.100.100 icmp_seq=187 Destination Host Unreachable
From 192.168.100.100 icmp_seq=188 Destination Host Unreachable
From 192.168.100.100 icmp_seq=189 Destination Host Unreachable
From 192.168.100.100 icmp_seq=190 Destination Host Unreachable
From 192.168.100.100 icmp_seq=191 Destination Host Unreachable
From 192.168.100.100 icmp_seq=192 Destination Host Unreachable
From 192.168.100.100 icmp_seq=193 Destination Host Unreachable
From 192.168.100.100 icmp_seq=194 Destination Host Unreachable
From 192.168.100.100 icmp_seq=195 Destination Host Unreachable
From 192.168.100.100 icmp_seq=196 Destination Host Unreachable
From 192.168.100.100 icmp_seq=197 Destination Host Unreachable
From 192.168.100.100 icmp_seq=198 Destination Host Unreachable
From 192.168.100.100 icmp_seq=199 Destination Host Unreachable
From 192.168.100.100 icmp_seq=200 Destination Host Unreachable
From 192.168.100.100 icmp_seq=201 Destination Host Unreachable
From 192.168.100.100 icmp_seq=202 Destination Host Unreachable
From 192.168.100.100 icmp_seq=203 Destination Host Unreachable
From 192.168.100.100 icmp_seq=204 Destination Host Unreachable
From 192.168.100.100 icmp_seq=205 Destination Host Unreachable
From 192.168.100.100 icmp_seq=206 Destination Host Unreachable
From 192.168.100.100 icmp_seq=207 Destination Host Unreachable
From 192.168.100.100 icmp_seq=208 Destination Host Unreachable
From 192.168.100.100 icmp_seq=209 Destination Host Unreachable
From 192.168.100.100 icmp_seq=210 Destination Host Unreachable
From 192.168.100.100 icmp_seq=211 Destination Host Unreachable
From 192.168.100.100 icmp_seq=212 Destination Host Unreachable
From 192.168.100.100 icmp_seq=213 Destination Host Unreachable
From 192.168.100.100 icmp_seq=214 Destination Host Unreachable
64 bytes from 192.168.100.11: icmp_req=138 ttl=64 time=80236 ms
64 bytes from 192.168.100.11: icmp_req=139 ttl=64 time=79228 ms
64 bytes from 192.168.100.11: icmp_req=140 ttl=64 time=78220 ms
64 bytes from 192.168.100.11: icmp_req=141 ttl=64 time=77212 ms

```

The content of /etc/network/interfaces is:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.3

auto tap0
iface tap0 inet static
address 192.168.100.100
netmask 255.255.255.0
pre-up tunctl -t tap0
up ifconfig tap0 up
down ifconfig tap0 down

```

Interface is attached to a dynagen instance. Traffic from vmnet interfaces flow without any issues towards the same process so I'm positive the problem should be with the tap interface configuration. Any ideas what might be causing this?

---

