---
title: "cannot connect to Internet(Destination Host Prohibited)"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by ranjeetsih on 2011-09-24
I cannot connect to internet.
it happened after a restart.
$ ping 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Prohibited
...
...
From 192.168.1.2 icmp_seq=9 Destination Host Prohibited
^C
--- 4.2.2.2 ping statistics ---
9 packets transmitted, 0 received, +9 errors, 100% packet loss,

i am able to connect to devices on my local network.

Following are some logs that probably can help troubleshoot this issue.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:bf:97:45:d9:46  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2bf:97ff:fe45:d946/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:765 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:43921 (43.9 KB)  TX bytes:54495 (54.4 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88178 (88.1 KB)  TX bytes:88178 (88.1 KB)

wlan0     Link encap:Ethernet  HWaddr 90:00:4e:bb:c9:bb  
          inet6 addr: fe80::9200:4eff:febb:c9bb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3102 (3.1 KB)  TX bytes:22601 (22.6 KB)
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=128 time=0.465 ms
...
...
64 bytes from 192.168.1.1: icmp_req=5 ttl=128 time=0.478 ms
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 0.465/0.571/0.747/0.118 ms

$ iptables -L
iptables v1.4.10: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
jagjeet@jagjeet-VPCYB25AG:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

Please help to troubleshoot this issue.

---

### Post by An Sanct on 2011-09-24
If you are using Oneiric, there is a small problem with the network manager, that prevents some cards to work properly.

Please tell us your Ubuntu version?

---

### Post by ranjeetsih on 2011-09-25
Its 11.04.

I think problem was caused by a dhcp server i was running on one of my fedora boxes.
Problem is not seen after i removed that dhcp server.

Thanks

---

