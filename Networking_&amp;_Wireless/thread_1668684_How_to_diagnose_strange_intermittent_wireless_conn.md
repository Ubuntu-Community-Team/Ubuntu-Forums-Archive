---
title: "How to diagnose strange intermittent wireless connectivity issues"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by aspz on 2011-01-16
Hi,

Just recently I've been having strange connectivity problems with my wireless network. The connection has previously worked fine and haven't had any problems with it. I haven't installed anything that would have affect it as far as I know.

My question is, how do I go about testing the network to see where the problem lies? I'm running Ubuntu 10.10 with a Netgear WG111v2 wireless adapter and my guess is it is some strange configuration problem or a rogue application is eating up packets because the system works fine when I boot it up into Windows. 

When I try to ping my router I'll usually get something like 98% packet loss. However in the output below, the network sprang to life half way through my pings so it went up to 63%. What other tools can I try to find out what's going on?

```

alex@obsidian:~/dev $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:4e:03:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8157 (8.1 KB)  TX bytes:8157 (8.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:c4:af:f4  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fec4:aff4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99562 (99.5 KB)  TX bytes:22556 (22.5 KB)

alex@obsidian:~/dev $ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
alex@obsidian:~/dev $ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=4 ttl=255 time=2.39 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=255 time=7.91 ms
64 bytes from 192.168.0.1: icmp_req=23 ttl=255 time=4.69 ms
64 bytes from 192.168.0.1: icmp_req=24 ttl=255 time=5.90 ms
64 bytes from 192.168.0.1: icmp_req=26 ttl=255 time=2.89 ms
64 bytes from 192.168.0.1: icmp_req=27 ttl=255 time=2.22 ms
64 bytes from 192.168.0.1: icmp_req=28 ttl=255 time=1.85 ms
64 bytes from 192.168.0.1: icmp_req=29 ttl=255 time=2.97 ms
64 bytes from 192.168.0.1: icmp_req=30 ttl=255 time=3.84 ms
64 bytes from 192.168.0.1: icmp_req=31 ttl=255 time=6.84 ms
64 bytes from 192.168.0.1: icmp_req=32 ttl=255 time=1.97 ms
64 bytes from 192.168.0.1: icmp_req=33 ttl=255 time=1.85 ms
^C
--- 192.168.0.1 ping statistics ---
33 packets transmitted, 12 received, 63% packet loss, time 32081ms
rtt min/avg/max/mdev = 1.855/3.781/7.914/2.007 ms

```


Thanks!

---

### Post by aspz on 2011-01-25
Ok, so it's been a week and in that time I have switched ISPs and got a new wireless router.

Unfortunately, I still get the same issue which strongly suggests it is something with my setup. Perhaps it is a signal strength issue though I've never had this problem before. The problem only started 2 weeks ago and only exists on my Ubuntu installation (Windows is fine).

How can I find out what is going on? I know linux has many tools for working with wireless networks but which can I use to effectively diagnose the problem?

Thanks,

Alex

---

