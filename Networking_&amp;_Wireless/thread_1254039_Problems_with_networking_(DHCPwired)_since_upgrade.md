---
title: "Problems with networking (DHCP/wired) since upgrade to Jaunty"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Mike Brennan on 2009-08-30
I've been running Ubuntu on a home network since July 2008 with no problems. Until last weekend, I was still running 8.04 (hardy). I decided to upgrade last Sunday, so I upgraded to 8.10, then the following day went ahead and upgraded to Jaunty.

Since then I have been having serious problems connecting to my home network (dhcp, wired connection). With Gnome Network Manager, the network applet would often have "connected" checked, but I would be unable to connect to anything. Unchecking that, waiting a moment, then checking it to connect again would sometimes work, sometimes not. Once connected, everything would be fine until I suspend or reboot. Upon coming back up again, it would fail to connect again, and it would be a hit or miss affair trying things to get it to connect -- including restarting NetworkManager (would sometimes work, but not always) or just restarting my Gnome session.

I've seen other threads with people having problems with dhcp and suggestions to comment out the relevant portions of /etc/dhcp3/dhclient.conf referencing "rfc3442". I've done that, but it hasn't helped.

I've also tried removing network-manager and replacing it with wicd, but I'm still experiencing problems. Also tried switching from dhclient to dhcpcd, but that made no difference.

If I boot with an 8.04 live CD, it connects to the network seamlessly with no problems, so it's not some hardware problem that just started happening. It's clearly something wrong with the software that started happening with either Intrepid or Jaunty. (I don't know which since I upgraded to Jaunty immediately after Intrepid.)

This is a big problem for me, and is very frustrating. I don't want to have to reinstall 8.04, but I'm starting to think I may have to do that. Hopefully, someone can help me resolve this so I won't have to.

Any suggestions?

---

### Post by uylug on 2009-08-30
Could you provide additional info, such as the output of ifconfig, ping to your gateway, running dhclient, something?

---

### Post by Mike Brennan on 2009-08-30
OK, here's what ifconfig outputs when successfully connected:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:88:90:bc  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe88:90bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14666 errors:29 dropped:0 overruns:0 carrier:29
          collisions:4606 txqueuelen:100 
          RX bytes:19974330 (19.9 MB)  TX bytes:2129977 (2.1 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:911001 (911.0 KB)  TX bytes:911001 (911.0 KB)

```

Here's what I got when I was unable to connect:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:88:90:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16099 errors:33 dropped:0 overruns:0 carrier:33
          collisions:6119 txqueuelen:1000 
          RX bytes:21359879 (21.3 MB)  TX bytes:2565925 (2.5 MB)
          Memory:fdfc0000-fdfe0000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:88:90:bc  
          inet addr:169.254.7.180  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:965012 (965.0 KB)  TX bytes:965012 (965.0 KB)

```

Here's what dhclient output when unable to connect:
```

$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 15764
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:09:88:90:bc
Sending on   LPF/eth0/00:1d:09:88:90:bc
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
Trying recorded lease 192.168.1.3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

On a successful connection:
```

$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 17592
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:09:88:90:bc
Sending on   LPF/eth0/00:1d:09:88:90:bc
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 33272 seconds.

```

Ping when unable to connect:
```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.7.180 icmp_seq=1 Destination Host Unreachable
From 169.254.7.180 icmp_seq=2 Destination Host Unreachable
From 169.254.7.180 icmp_seq=3 Destination Host Unreachable
From 169.254.7.180 icmp_seq=4 Destination Host Unreachable
From 169.254.7.180 icmp_seq=5 Destination Host Unreachable
From 169.254.7.180 icmp_seq=6 Destination Host Unreachable
From 169.254.7.180 icmp_seq=7 Destination Host Unreachable
From 169.254.7.180 icmp_seq=8 Destination Host Unreachable
From 169.254.7.180 icmp_seq=9 Destination Host Unreachable
From 169.254.7.180 icmp_seq=10 Destination Host Unreachable
From 169.254.7.180 icmp_seq=11 Destination Host Unreachable
From 169.254.7.180 icmp_seq=12 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
14 packets transmitted, 0 received, +12 errors, 100% packet loss, time 13074ms
, pipe 3

```

Another instance (while actively trying to connect with wicd, but failing):
```

$ ping 192.168.1.1
connect: Network is unreachable

```

Ping after successfully connecting:
```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=5.61 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.34 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.28 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.44 ms
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 2.285/2.906/5.619/1.214 ms

```

Is any of that helpful?

Thanks.

---

### Post by Iowan on 2009-08-31
**avahi** seems to be stepping in to "help" sometimes.  It must be useful - or it wouldn't have been included ... but it seems to foretell problems. The **avahi** address (169.254.X.X) usually puts the machine in a subnet by itself. Dunno if DHCP is too slow, or what triggers it (or if removing **avahi** would fix the root-cause of the problem).

---

### Post by Mike Brennan on 2009-08-31
> **Iowan said:**
> **avahi** seems to be stepping in to "help" sometimes.  It must be useful - or it wouldn't have been included ... but it seems to foretell problems. The **avahi** address (169.254.X.X) usually puts the machine in a subnet by itself. Dunno if DHCP is too slow, or what triggers it (or if removing **avahi** would fix the root-cause of the problem).

I think Avahi may be kicking in to do zeroconf when dhcp fails to connect to the network -- though I am by no means an expert in this and don't have a good understanding of what's going on.

I'm not sure what Avahi may be providing me if I don't need zeroconf, so I don't what the implications are of removing it.

What does that "MULTICAST" mean in my ifconfig output for eth0? I was just poking around on the [Avahi website]("http://avahi.org/wiki/Avah4users#Troubleshooting") and I see it says you can tell Avahi to ignore certain network interfaces via:
```
ifconfig eth0 -multicast
```

What are the implications of that? Does that just mean I can't broadcast services on the network? I don't to do that, but I don't know if there are other implications to this.

Thanks.

---

