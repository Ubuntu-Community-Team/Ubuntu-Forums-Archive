---
title: "Jaunty / Agere Systems ET-131x PCI-E Ethernet Controller"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by jkounis on 2009-10-01
Well, I've almost migrated my entire laptop from Vista to Ubuntu, with one exception: my Gigabit Ethernet Expresscard (Agere Systems ET-131x)

Ubuntu recognizes the card each time I boot. The kernel module appears to be loaded, but it doesn't provide any network connectivity. Pings return "Destination Host Unreachable."

I can use the built-in 100MBps eth0 connection, but the 1GBps Expresscard refuses to work.

There is one more unusual symptom: each time I reboot, the interface number increases by 1. When I first plugged in the card, it was eth1. Now we're up to eth17 as I try to troubleshoot the problem.

Here's my configuration (I set up a static IP address and route to eliminate DHCP as being a problem):

```
 ifconfig eth17:
 eth17     Link encap:Ethernet  HWaddr 00:05:3d:00:02:f5  
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:3dff:fe00:2f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3114 (3.1 KB)  TX bytes:4270 (4.2 KB)
          Interrupt:16 

```
I tried adding a default route. It doesn't make a difference. It fails either way:

```
john@john-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     255.255.255.0   UG    0      0        0 eth17
192.168.1.0     *               255.255.255.0   U     0      0        0 eth17
```

```
john@john-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth18
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth18
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth18
```

The module appears to be loaded:

```
lsmod | grep et131
et131x                102664  0 

```
I have tried using the et131x kernel module that comes with Ubuntu Jaunty 9.04. I have also downloded the source for the et131x module from the Universe Repositories and recompiled and installed it. Finally, I downloaded the source for et131x-1.2.3.3 from [http://sourceforge.net/projects/et131x/files/](http://sourceforge.net/projects/et131x/files/).

All three of these procedures render a usable module that appears to work, but I still have no network connectivity:

```
ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
From 192.168.1.25 icmp_seq=1 Destination Host Unreachable
From 192.168.1.25 icmp_seq=2 Destination Host Unreachable
From 192.168.1.25 icmp_seq=3 Destination Host Unreachable
From 192.168.1.25 icmp_seq=4 Destination Host Unreachable
From 192.168.1.25 icmp_seq=5 Destination Host Unreachable
From 192.168.1.25 icmp_seq=6 Destination Host Unreachable
From 192.168.1.25 icmp_seq=7 Destination Host Unreachable
From 192.168.1.25 icmp_seq=8 Destination Host Unreachable
From 192.168.1.25 icmp_seq=9 Destination Host Unreachable

```

I get the same error on other machines if I try to ping the problem machine:

```
ping 192.168.1.25
PING 192.168.1.25 (192.168.1.25) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=5 Destination Host Unreachable
From 192.168.1.4 icmp_seq=6 Destination Host Unreachable
From 192.168.1.4 icmp_seq=7 Destination Host Unreachable
From 192.168.1.4 icmp_seq=8 Destination Host Unreachable
From 192.168.1.4 icmp_seq=9 Destination Host Unreachable
```


I'm really stumped about what to do. If I reboot to Vista, the network adapter works fine, so it's not a hardware issue.

Any ideas?

Thanks

---

