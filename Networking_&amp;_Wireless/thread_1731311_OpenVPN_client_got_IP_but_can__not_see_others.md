---
title: "OpenVPN client got IP but can  not see others"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by vncoder on 2011-04-17
Hello all,

   I am trying to setup a ethernet bridge between my two locations.

   I've successfully connected my openvpn client to the server to get an IP. The route entry added correctly to the client(I believe). However, the server and the client can not see each other. I am using this configuration
 
   Whenever I try to ping from the client to the server or vice versa, I get Host Unreachable. Both using Ubuntu 10.10 with all the patches/software updates installed.

  
Route Table (Cut Down version)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     *               255.255.255.0   U     0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 tap0
default         192.168.3.1     0.0.0.0         UG    100    0        0 eth0



tap0      Link encap:Ethernet  HWaddr 0e:30:a6:b9:21:44
          inet addr:10.1.1.50  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c30:a6ff:feb9:2144/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:78 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:991 (991.0 B)



Anyone has any idea where I could look on why I can not see (ping/traceroute, etc) between the two network segments?


Robert

---

