---
title: "Server 12.04 Dual NIC Crossover Issues"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by Aenigmatic on 2012-07-02
I'm setting up two servers with two NICs each. eth0 will be used for LAN/WAN connections and eth1 will be used for server-to-server (crossover) DRBD replication.

DRBD is setup and running fine, if I go through the LAN. However, I want to reduce LAN load and just go directly to the other server via crossover. As far as I know, everything is setup correctly, but I cannot get the crossover connection to work at the same time as the LAN connection.

Network Specifics:
```
**eth0:** (LAN)
Network: 10.0.0.*
Netmask: 255.255.255.0
Gateway: 10.0.0.150
DNS: 10.0.0.100

**eth1:** (Crossover)
Network: 192.168.1.1 and 192.168.1.2
Netmask: 255.255.255.252
Gateway: Other machine 
```Output of route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.150      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.252 U     1      0        0 eth1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

Output of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:67:46:3a:bb  
          inet addr:10.0.0.170  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:67ff:fe46:3abb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9086329 (9.0 MB)  TX bytes:1667500 (1.6 MB)
          Interrupt:19 Memory:c2500000-c2520000 

eth1      Link encap:Ethernet  HWaddr 00:1e:67:46:3a:ba  
          inet addr:192.168.1.1  Bcast:192.168.1.3  Mask:255.255.255.252
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:500809 (500.8 KB)  TX bytes:302767 (302.7 KB)
          Interrupt:16 Memory:c2300000-c2320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:450847 (450.8 KB)  TX bytes:450847 (450.8 KB)

```

IPTables is set to allow everything. UFW is disabled. Both servers cannot ping each other via crossover when eth0 is plugged in/active but can if I disable eth0 and eth1 becomes default.

Any ideas?

---

