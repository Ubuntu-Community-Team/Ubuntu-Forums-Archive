---
title: "route -6 and tunnel setup"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Wordan on 2009-03-09
Hi, i've reached a sticking point and need a nudge to get this working. I have little experience with routing in linux and ipv6. Any help would be greatly apreacated. I want to get to grips with linux routing but finding it hard to get started.

I have set up a tunnel with go6 and connecting using the **tspc** package. Also using **radvd** package for router advertising on local network.

Computers on the local network are getting global addresses, but the gateway doesn't seam to be routing.

Here is ifconfig and route -6 on a host on the local network:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:05:b8:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:213 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:05:c7:d5  
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:XXXX:XXXX:XXXX:21b:fcff:fe05:c7d5/64 Scope:Global
          inet6 addr: fe80::21b:fcff:fe05:c7d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160366242 (152.9 MB)  TX bytes:14075011 (13.4 MB)
          Interrupt:214 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119090 (116.2 KB)  TX bytes:119090 (116.2 KB)

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
::1/128                        ::                         Un   0   1    13 lo
2001:XXXX:XXXX:XXXX:21b:fcff:fe05:c7d5/128 ::                         Un   0   1  5643 lo
2001:XXXX:XXXX:XXXX::/64           ::                         UAe  256 0    58 eth1
fe80::21b:fcff:fe05:c7d5/128   ::                         Un   0   1   337 lo
fe80::/64                      ::                         U    256 0     0 eth1
ff00::/8                       ::                         U    256 0     0 eth1
::/0                           fe80::213:46ff:fe3b:7a75   UGDAe 1024 0     0 eth1
::/0                           ::                         !n   -1  1     1 lo

```

And on the router:
```
eth0      Link encap:Ethernet  HWaddr 00:13:46:3b:7a:75  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:XXXX:XXXX:XXXX::1/64 Scope:Global
          inet6 addr: fe80::213:46ff:fe3b:7a75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29278 (28.5 KB)  TX bytes:42954 (41.9 KB)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4608 (4.5 KB)  TX bytes:4608 (4.5 KB)

tun       Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2001:XXXX:XXXX:XXXX::3055/128 Scope:Global
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:416 (416.0 B)  TX bytes:152 (152.0 B)

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2001:XXXX:XXXX:XXXX::3055/128      ::                         U    256 0     0 tun
2001:XXXX:XXXX:XXXX::/64           ::                         U    256 0     1 eth0
2000::/3                       ::                         U    1   0     0 tun
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 tun
::/0                           2001:XXXX:XXXX:XXXX::3055      UG   1   0     0 eth0
::/0                           ::                         !n   -1  1    41 lo
::1/128                        ::                         Un   0   1     7 lo
2001:XXXX:XXXX:XXXX::/128          ::                         Un   0   2     0 lo
2001:XXXX:XXXX:XXXX::1/128         ::                         Un   0   1   200 lo
2001:XXXX:XXXX:XXXX::3055/128      ::                         Un   0   1     0 lo
fe80::/128                     ::                         Un   0   2     0 lo
fe80::213:46ff:fe3b:7a75/128   ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 0     0 eth0
ff00::/8                       ::                         U    256 0     0 tun
::/0                           ::                         !n   -1  1    41 lo

```

Can anyone know what should try? Thanks!
Server/gateway/router whatever is running Ubuntu 8.04 server.

---

### Post by unhot on 2009-03-26
I'm having a (i think) similar problem with tspc -

2009/03/26 13:26:26 tspc: tspSetupTunnel: tspGetCapabilities error 2: SOCKET_ERROR
2009/03/26 13:26:26 tspc: tspSetupTunnel: if you are using udp, there is probably no udp listener at broker.freenet6.net
2009/03/26 13:29:36 tspc: tspConnect: Not able to connect to service port 3653
2009/03/26 13:29:36 tspc: tspMain: All transports failed, quitting
2009/03/26 13:29:36 tspc: tspMain: Error is 2: SOCKET_ERROR
2009/03/26 13:29:36 tspc: tspMain: TSP session done

---

