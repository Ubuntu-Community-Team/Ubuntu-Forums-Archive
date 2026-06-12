---
title: "What is bridging nics exactly?"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-06
[http://2stech.ca/index.php/linux/linuxtutotials/tutorials/208-creating-bridged-interfaces](http://2stech.ca/index.php/linux/linuxtutotials/tutorials/208-creating-bridged-interfaces)

I did that but then I lost all internet. Network manager went to unmanaged connections. And I had no connection to the router.

I share the internet to another PC with a 2nd nic. 
And on the router I have another LAN. The shared internet computer can reach that other lan, but the other LAN can not reach the shared internet computer. 

Any way to  make that work?


So I undid bridging.

```
scott@scott-P5QC:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42529 (42.5 KB)  TX bytes:17164 (17.1 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:169.254.9.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1878721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1878721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:366107901 (366.1 MB)  TX bytes:366107901 (366.1 MB)

scott@scott-P5QC:~$ ping 169.254.9.111
PING 169.254.9.111 (169.254.9.111) 56(84) bytes of data.
64 bytes from 169.254.9.111: icmp_req=1 ttl=64 time=0.042 ms
64 bytes from 169.254.9.111: icmp_req=2 ttl=64 time=0.034 ms
64 bytes from 169.254.9.111: icmp_req=3 ttl=64 time=0.032 ms
^C
--- 169.254.9.111 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.032/0.036/0.042/0.004 ms
scott@scott-P5QC:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 22119
scott@scott-P5QC:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46177 (46.1 KB)  TX bytes:17164 (17.1 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:169.254.9.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5193026 errors:0 dropped:30 overruns:30 frame:30
          TX packets:9683677 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:4948732746 (4.9 GB)  TX bytes:11331764751 (11.3 GB)
          Interrupt:45 

eth2      Link encap:Ethernet  HWaddr 00:50:ba:ac:3c:f0  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:feac:3cf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1532675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1983424 errors:57 dropped:0 overruns:54 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:442731179 (442.7 MB)  TX bytes:1802141834 (1.8 GB)
          Interrupt:16 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1879940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1879940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:366204465 (366.2 MB)  TX bytes:366204465 (366.2 MB)

scott@scott-P5QC:~$ 

```

I commented out the br0 and restarted the network and it was working again.

```
auto lo
iface lo inet loopback

#auto br0
#iface br0 inet dhcp
#        bridge_ports eth0  eth2
#        bridge_stp off
#        bridge_fd 0
#        bridge_maxwait 0
```

---

### Post by Cheesehead on 2013-01-06
Bridging makes multiple NICs appear to be the same interface.

For example, your router may have an ethernet and wireless interfaces. They are bridged together so both look like the same IP address to your LAN....That's how they can be effective gateways.

Bridging is, however, not an effective way to share a single network connection between multiple machines. Not the right tool at all.

Instead, take a look at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by sdowney717 on 2013-01-07
Thanks, I did this share to other computers for the second nic.

Here is an image of the current LAN setup
[IMG]https://lh5.googleusercontent.com/-uChF5IIApj8/UOrFVvJYMiI/AAAAAAAAEV0/lyAJAvYks9k/s1024/lan.jpeg[/IMG]

I did this so I can get gigabyte lan between ubuntu PC and second win7 pc

I can not ping from first win7 to second win7 but second win7 can ping first win7 pc.

Ubuntu pc has 2 nic, 100mb/s ethernet nic to router, gigabyte nic direct to gigabyte nic in win7 pc. Ubuntu PC has "share this connection to other pc" on. that nic is eth2 and is 10.42.0.1

2nd Win7 pc is assigned 10.42.0.19

What I want is the win7 pc on second router to ping the other win7 pc on the gigabyte lan.

The ubuntu PC can ping both win7 pc's. The first win7 pc can ping ubuntu pc but not the second win7 pc The second win7 pc can ping the ubuntu pc and the first win7 pc

This is the route command in ubuntu pc

```
scott@scott-P5QC:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth2
10.42.0.0       0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
scott@scott-P5QC:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         wr850g.hr.cox.n 0.0.0.0         UG    0      0        0 eth2
10.42.0.0       *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth2
scott@scott-P5QC:~$ 
```

---

