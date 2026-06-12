---
title: "Ubuntu as router for MAC ? Avahi vs Dhcp"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by kttshin on 2009-09-17
Hello,

I setup Ubuntu+MAC OSX connection for file sharing and available services advertising as it was described
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)
It works nicely.
I would like to make my Ubuntu machine as internet router for my MAC as well, but here curiosities begin: eth0 has no IP address, dhcp3-server conflicts with Avahi. Should I remove Avahi? I have Flash media server on my Ubuntu machine, so it's important to have it.

This is my ifconfig dump;

eth0      Link encap:Ethernet  HWaddr 00:1b:38:0a:dd:26  
          inet6 addr: fe80::xxb:xxff:fe0a:dd26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5572 (5.5 KB)  TX bytes:5948 (5.9 KB)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:0a:dd:26  
          inet addr:169.254.XXX..XX  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KB)  TX bytes:1284 (1.2 KB)

wimax1    Link encap:Ethernet  HWaddr 00:24:90:83:5b:15  
          inet addr:XX.XXX.XXX.135  Bcast:89.XXX.XXX.XXX  Mask:255.255.255.0
          inet6 addr: fe80::224:90ff:fe83:5b15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1386  Metric:1
          RX packets:17720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:14928610 (14.9 MB)  TX bytes:5114526 (5.1 MB)

Thank you in advance.

Kioshin

---

