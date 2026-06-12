---
title: "Simple Dual Wan Question, Redundancy ONLY"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by thefix0r on 2010-12-22
I recently added a second interface to my Ubuntu 9.10 server, I now have a dsl AND Cable connection for it, Im not trying to load balance or anything sophisitcated, heres my problem.
 
The machines networked, I put static entries in my dhcp servers and both interfaces are up and live with dhcp, and Ive tried with dhcp and static, same problem occurs. 
 
But my problem is that services will only respond on one interface at a time, not both.
 
Anyone know what the heck is going on here?



Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
12.12.12.0      *               255.255.255.0   U     0      0        0 eth2
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
default         12.12.12.1      0.0.0.0         UG    100    0        0 eth2
default         10.10.1.1       0.0.0.0         UG    100    0        0 eth1

Should I make them static and remove both gateways?

root@ubuntu:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:xx.xx.xx.xx.xx <---REDACTED
          inet addr:10.10.1.105  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::202:b3ff:fecc:8610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:385295 (385.2 KB)  TX bytes:517667 (517.6 KB)

eth2      Link encap:Ethernet  HWaddr 00:xx.xx.xx.xx.xx <--REDACTED 
          inet addr:12.12.12.105  Bcast:12.12.12.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fecc:8611/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:143167 (143.1 KB)  TX bytes:99817 (99.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:108493 (108.4 KB)  TX bytes:108493 (108.4 KB)

---

### Post by thefix0r on 2010-12-22
Bump, Ive tried with static ips and a single gateway and still cant get to my machine from both interfaces, only one at a time. Any ideas?

---

