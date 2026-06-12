---
title: "Wireless network drops out randomly"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by yarninc on 2009-12-06
Hello.

I have been using Ubuntu 9.04 for about 3 months. I have 2 users set up and during this time we have suffered from the wireless network connection drops out. It seems that once the network drops out, the only way i can get it back is to reboot. (tried switching users etc).

The wireless network consists of whatever wireless device is inside my E-Systems 3089 Laptop, then I am connecting to my Netgear WGT624. I use a 64 bit shared key security. Before using Ubuntu I was using XP for years with the same hardware and I never saw this problem, so I am sure that the hardware is good. I also have windows PC's that still connect to the Netgear after the problem occurs.

When the network drops out, I have no detected networks in my network connections tab. To me, it looks like the driver has crashed or powered down.

I would like to begin investigating this problem, but dont know where to start. What are the methods / tools I need. I dont even know how to work out what driver is being used!! Usually I am very technical with this stuff, but I think being new to the OS is the issue. (I mainly want to understand this even if I cant fix it).

I have copied some results from the Terminal after the issue occus:-

ANY HELP APPRECIATED. ;)

yarninc@Laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

yarninc@Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:5a:e2:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380 (380.0 B)  TX bytes:380 (380.0 B)

yarninc@Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=10 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

