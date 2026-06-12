---
title: "loopback stops working after some uptime"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by BillG618 on 2012-08-05
This just started like 4 or 5 days ago. I'm running Ubuntu 12.04 desktop, and after about 12 hours of uptime it seems the loopback device just stops working. If I do an ifconfig, it looks like it's still there, but if I ping localhost or 127.0.0.1, both fail. Also, pinging known DNS addresses ([www.google.com](www.google.com)) fail. But pinging by IP works fine.

The rest of the networking features seem unphased. I can still reach the Samba share from my Windows machine. Also, I run an Apache server that is still reachable from the outside world. Looking at the resources monitor, the CPU and memory usage appear normal when this happens.

If I restart the machine, everything is fine again. For about 12 hours, until it happens again. Any ideas on what could be causing this or how to diagnose it? Thanks.

Disclaimer: Please excuse my n00b-ishness. I'm a long-time Windows guy that just started using Ubuntu 6 months ago.

---

### Post by BillG618 on 2012-08-08
Bump.

Additionally, this is happening on an nforce ethernet port built into my motherboard. Below is some diagnostic info I collected. Does any of it look out of the ordinary?

[HTML]~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:1b:fc:64:dc:82 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.132/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::21b:fcff:fe64:dc82/64 scope link 
       valid_lft forever preferred_lft forever

~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

~$ getent hosts localhost
127.0.0.1       localhost

~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
^C
--- 127.0.0.1 ping statistics ---
572 packets transmitted, 0 received, 100% packet loss, time 575551ms


~$ ping6 ::1
PING ::1(::1) 56 data bytes
64 bytes from ::1: icmp_seq=1 ttl=64 time=0.020 ms
64 bytes from ::1: icmp_seq=2 ttl=64 time=0.023 ms
64 bytes from ::1: icmp_seq=3 ttl=64 time=0.025 ms
64 bytes from ::1: icmp_seq=4 ttl=64 time=0.021 ms
64 bytes from ::1: icmp_seq=5 ttl=64 time=0.028 ms
64 bytes from ::1: icmp_seq=6 ttl=64 time=0.025 ms
64 bytes from ::1: icmp_seq=7 ttl=64 time=0.023 ms
64 bytes from ::1: icmp_seq=8 ttl=64 time=0.026 ms
64 bytes from ::1: icmp_seq=9 ttl=64 time=0.021 ms
64 bytes from ::1: icmp_seq=10 ttl=64 time=0.028 ms
^C
--- ::1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8998ms
rtt min/avg/max/mdev = 0.020/0.024/0.028/0.002 ms

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:64:dc:82  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe64:dc82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5537467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7700200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2390500721 (2.3 GB)  TX bytes:8274946292 (8.2 GB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1441430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1441430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2084259522 (2.0 GB)  TX bytes:2084259522 (2.0 GB)

[/HTML]

---

