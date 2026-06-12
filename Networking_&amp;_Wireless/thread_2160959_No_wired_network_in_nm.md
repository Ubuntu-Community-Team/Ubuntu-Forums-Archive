---
title: "No wired network in nm"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-07-08
I have lost what little connection I had between the computer, the ethernet switch, and the silicondust tuner.

The Network Manager shows no ethernet in the Connection Information page (window or screen). It did a few days ago. I am trying to use MythTV. I had set the IP4V to Method: Link-Local only, but was told by a number of MythTV specialists that I have to have a static IP address to have more than one front end. Now the eth0 is set to DHCP Automatic. 

Questions:

By front end does that mean merely a TV that has an ethernet port? - I don't have but one computer.

How does one know what IP address numbers to put into the config file?

Where has the eth0 gone?


ark@Lexington:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.2.3.3
       logical name: wlan0
       serial: 90:f6:52:0c:2d:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.8.0-26-generic firmware=1.3 ip=192.168.1.73 link=yes multicast=yes wireless=IEEE 802.11bgn
mark@Lexington:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154362 (154.3 KB)  TX bytes:618120 (618.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:25459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3671128 (3.6 MB)  TX bytes:3671128 (3.6 MB)

wlan0     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:92f6:52ff:fe0c:2da4/64 Scope:Global
          inet6 addr: fe80::92f6:52ff:fe0c:2da4/64 Scope:Link
          inet6 addr: 2602:306:bdbf:4420:a58b:46f7:165a:1924/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156706591 (156.7 MB)  TX bytes:36810996 (36.8 MB)

---

