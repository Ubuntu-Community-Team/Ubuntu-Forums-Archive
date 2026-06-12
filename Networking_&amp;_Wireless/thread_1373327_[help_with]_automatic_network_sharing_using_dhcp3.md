---
title: "[help with] automatic network sharing using dhcp3"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by gwydionwaters on 2010-01-05
hey all
i am trying to share networking over a lan to my xbox from my wifi connection. i have no control over the router, it is the landlords. i am running kde.

i can get network connectivity but the xbox can't get to the internet, it claims the dns cant resolve the server (xbox live) host names.

here is my dhcpd.conf
```
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 192.168.0.1;
option domain-name-servers 8.8.4.4, 8.8.8.8;

subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.100;
} 
```if config gives this for eth0 (my lan port)

```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:70:77:f0  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe70:77f0/64 Scope:Link      
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1      
          RX packets:1753 errors:0 dropped:0 overruns:0 frame:0   
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0  
          collisions:0 txqueuelen:1000                            
          RX bytes:137004 (137.0 KB)  TX bytes:46727 (46.7 KB)    
          Interrupt:20 Base address:0x2000       
```route -n gives
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```and my client (xbox)
receives the ip 10.0.0.10 and subnet 255.255.255.0 and gateway 10.0.0.1
dns servers are what i have them set to

my lan connection settings in network config for kde are
```

restrict to interface: eth0
ip settings: automatic

```any ideas what to try?

---

