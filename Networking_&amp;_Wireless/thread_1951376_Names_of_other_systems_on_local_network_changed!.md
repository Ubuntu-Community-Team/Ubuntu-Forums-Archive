---
title: "Names of other systems on local network changed!"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by jcobban on 2012-04-02
I have two computers running Ubuntu on the local network connected to a router.  The router (at 192.168.2.1) sees both systems (as well as my TV set, isn't technology wonderful!) and recognizes them by name "jcobban-laptop" and "linux-server".  However if I try to use those names, for example in a ping, I get "unknown host".  The names used to work, they just stopped working recently.

jcobban@linux-server:~$ ping jcobban-laptop
ping: unknown host jcobban-laptop
jcobban@linux-server:~$ ping 192.168.2.14
PING 192.168.2.14 (192.168.2.14) 56(84) bytes of data.
64 bytes from 192.168.2.14: icmp_req=1 ttl=64 time=1.53 ms
...

When I ask the router it tells me that jcobban-laptop has IP address 192.168.2.14 assigned by DHCP and linux-server has address 192.168.2.103 by DHCP.  (The TV set has 192.168.2.10 by DHCP.)

jcobban@linux-server:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
jcobban@linux-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:ca:32:52  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:feca:3252/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:328015719 (328.0 MB)  TX bytes:24877415 (24.8 MB)
          Interrupt:17 
jcobban@linux-server:~$ nslookup jcobban-laptop
Server:		192.168.2.1
Address:	192.168.2.1#53

** server can't find jcobban-laptop: NXDOMAIN

However if, following the obscure advice in a post response, I tack ".local" onto the name it works!

jcobban@linux-server:~$ ping jcobban-laptop.local
PING jcobban-laptop.local (192.168.2.14) 56(84) bytes of data.
64 bytes from 37L4247D28-05 (192.168.2.14): icmp_req=1 ttl=64 time=2.70 ms
64 bytes from 37L4247D28-05 (192.168.2.14): icmp_req=2 ttl=64 time=0.601 ms
...

My presumption is that the microcode in the router got changed some time, although I do not recall updating it in at least a year.

---

