---
title: "Problems with Hamachi Login"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by calazans on 2009-09-29
I am having problems with Hamachi. After downloading and installing Hamachi (hamachi-0.9.9.9.20-lnx) in Ubuntu (9.04, with all recent patches and updates) everything worked fine for some weeks. I could enter networks, pinging machines, connect from anywhere to my Ubuntu machine, from both LInux and Windows machines. 

This week, after a usual Ubuntu packages automatic update Hamachi stopped working, meaning that it won't login anymore. 

After studying several posts and trying several fixing procedures, nothing worked so far. Things I tried already:
1) Reinstalling hamachi, using several posts telling step by step how to install it correctly in Ubuntu
2) Editing routing tables to add the hamachi IP number manually to the routing table

Features of the problem:
1) Tuncfg works fine
2) Hamachi-init (with and without -f) works fine
3) Hamachi start works fine
4) Hamachi login (before the above problem described in 3 appeared) give the message
Logging in ... failed

The failed word appears after a while

5) There is no firewall installed.

The failed part appeared after a while.

My current configurations:
calazans>ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1a:d8:94  
          inet addr:10.32.175.48  Bcast:10.32.175.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe1a:d894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:348416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:44228405 (44.2 MB)  TX bytes:6337083 (6.3 MB)
          Memory:e3200000-e3220000 

ham0      Link encap:Ethernet  HWaddr aa:2f:8b:5e:ce:08  
          inet addr:5.218.39.14  Bcast:5.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a82f:8bff:fe5e:ce08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:68361 (68.3 KB)

ham1      Link encap:Ethernet  HWaddr 6e:98:0d:02:3e:47  
          inet6 addr: fe80::6c98:dff:fe02:3e47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12324 (12.3 KB)  TX bytes:12324 (12.3 KB)
calazans> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1a:d8:94  
          inet addr:10.32.175.48  Bcast:10.32.175.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe1a:d894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:348802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:44269721 (44.2 MB)  TX bytes:6341123 (6.3 MB)
          Memory:e3200000-e3220000 

ham0      Link encap:Ethernet  HWaddr aa:2f:8b:5e:ce:08  
          inet addr:5.218.39.14  Bcast:5.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a82f:8bff:fe5e:ce08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:68361 (68.3 KB)

ham1      Link encap:Ethernet  HWaddr 6e:98:0d:02:3e:47  
          inet6 addr: fe80::6c98:dff:fe02:3e47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

ham2      Link encap:Ethernet  HWaddr 3a:1c:09:95:d8:0b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12324 (12.3 KB)  TX bytes:12324 (12.3 KB)

pan0      Link encap:Ethernet  HWaddr 46:de:c9:67:a7:29  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

calazans> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.32.175.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         5.218.39.14     255.0.0.0       UG    0      0        0 ham0
0.0.0.0         10.32.175.250   0.0.0.0         UG    0      0        0 eth0

---

