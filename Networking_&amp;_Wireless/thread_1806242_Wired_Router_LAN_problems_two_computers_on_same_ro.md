---
title: "Wired Router LAN problems two computers on same router"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by wmccarty on 2011-07-17
Hello,

Ever since I have installed Natty 11.04 on my secondary computer, I have been having problems connecting both my computers at the same time. I use both normally so this is really annoying.

Basically what happens is that my main computer which is running 10.04 is connected to my router on a static IP route to xxx.xxx.xxx.25, when I turn on the 11.04 computer it does not recognize that it is physically connected to the router. In order to make it recognize that there is a connection I have to either reset the router, or unplug the LAN cable from my main computer. Sometimes both show connection, but when they do both connect, one is connected at the slowest speed (the 10/100 light on the router does not illuminate.) Most of the time when both connect to the router I loose the connection to the WAN/Internet.

Anyhow, I thought it might be my router, so I changed the firmware on it to an earlier version, to back when both computers were on 10.04 and both could connect at the same time. Same result.

I tried assigning a static route to the 11.04 computer, still same result.

Please help, I am not sure how to search this type of problem in the forums or by Google.

---

### Post by jmoorse on 2011-07-17
Hello!

Do both machines have wired connections directly to the router?

Please provide the output of 'ifconfig -a' and 'route -n' from both Ubuntu boxes.

Thanks

---

### Post by wmccarty on 2011-07-28
Hello sorry for the long time to reply, work has been unreal.

Okdoke so, both connect via a wire connection.

The first computer:
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:10:92:68  
          inet addr:192.168.177.25  Bcast:192.168.177.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe10:9268/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155826690 (155.8 MB)  TX bytes:19170728 (19.1 MB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:352688 (352.6 KB)  TX bytes:352688 (352.6 KB)

pan0      Link encap:Ethernet  HWaddr aa:f8:8e:80:67:29  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:19:02:2b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12522801 (12.5 MB)  TX bytes:2976352 (2.9 MB)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.177.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.177.1   0.0.0.0         UG    0      0        0 eth0

The Second computer:
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:9f:f1:be  
          inet addr:192.168.177.40  Bcast:192.168.177.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe9f:f1be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21642 (21.6 KB)  TX bytes:20507 (20.5 KB)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4190 (4.1 KB)  TX bytes:4190 (4.1 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:cc:e7:56:0e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.177.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.177.1   0.0.0.0         UG    0      0        0 eth0

Thank you! Have an excellent long weekend!

---

### Post by jmoorse on 2011-08-01
That all looks fine.  Have you tried different ethernet cables?  Also, what type of router do you have?

---

