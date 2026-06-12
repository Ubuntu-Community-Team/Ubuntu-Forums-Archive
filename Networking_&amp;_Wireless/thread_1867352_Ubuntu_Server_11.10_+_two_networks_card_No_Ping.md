---
title: "Ubuntu Server 11.10 + two networks card No Ping"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by adoniasv on 2011-10-22
Why dont ping second card????

This is my estructure:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205190&stc=1&d=1319325246[/IMG]

IfConfig
[PHP]
root@tecnic:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:f4:cb:fc:20
          inet addr:200.83.185.43  Bcast:200.83.185.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fecb:fc20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5133244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:313275517 (313.2 MB)  TX bytes:17876 (17.8 KB)
          Interrupt:22 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0d:60:95:bc:76
          inet addr:172.30.52.158  Bcast:172.30.52.191  Mask:255.255.255.192
          inet6 addr: fe80::20d:60ff:fe95:bc76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12535087 (12.5 MB)  TX bytes:70088095 (70.0 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32145 (32.1 KB)  TX bytes:32145 (32.1 KB)
[/PHP]Route
[PHP]
root@tecnic:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.52.128   *               255.255.255.192 U     0      0        0 eth1
200.83.185.0    *               255.255.255.0   U     0      0        0 eth0
default         172.30.52.190   0.0.0.0         UG    100    0        0 eth1
default         200.83.185.1    0.0.0.0         UG    100    0        0 eth0
[/PHP]/etc/resolv.cof
[PHP]
domain xxxx
search xxxx
nameserver 200.83.1.4
nameserver 190.160.0.14
nameserver 172.17.169.41
nameserver 172.17.41.52
[/PHP]IpTables
[PHP]
root@tecnic:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
[/PHP]
Ping result from intranet client

[PHP]
root@Intranet-Client:~# ping 172.30.52.158
PING 172.30.52.158 (172.30.52.158) 56(84) bytes of data.
64 bytes from 172.30.52.158: icmp_req=1 ttl=64 time=0.078 ms
64 bytes from 172.30.52.158: icmp_req=2 ttl=64 time=0.025 ms
64 bytes from 172.30.52.158: icmp_req=3 ttl=64 time=0.020 ms
--- 172.30.52.158 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.020/0.038/0.078/0.023 ms
[/PHP]Ping result from internet client

[PHP]
root@Internet-Client:~# ping 200.83.185.43
Destination Host Unreachable
[/PHP]

thxx for you help

---

### Post by adoniasv on 2011-10-22
pufff SOLVED w/ ** ip route**

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

---

