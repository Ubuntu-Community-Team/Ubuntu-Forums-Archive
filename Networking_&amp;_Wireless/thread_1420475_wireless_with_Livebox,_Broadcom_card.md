---
title: "wireless with Livebox, Broadcom card"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Zordkhan on 2010-03-03
I'm very new to Ubuntu, and had problems getting wireless working on my laptop. 

1) First I realized that my Broadcom wireless card had no driver in Ubuntu, so I had to download and install that specially. 

Following information on these forums, I went to the System - Synaptics Package Manager - scroll down the (long!) list of packages for "bcmwl-kernel-source" and installed it. 

I knew this was successful when I saw that when left-clicking on the networking icon in the panel, I saw that my wireless network, and the neighbours', were all now detected by the card. 

2) Then by trial and error I associated the wireless with my livebox. 

- click on network icon
- select desired wireless network
- key in password carefully
- ENSURE you have a WIRED connection to the Livebox (e.g. the USB cable) and CONNECT it.
- press the easy pairing button on the Livebox, and click to OK the password you have keyed in
- wait until the association has been made
- then you can disconnect the wired internet and use the internet via wireless. 

The first time I did this, the wireless icon indicated that the association was successful, but when I actually tried to browse the net in Firefox, no pages were available. (My livebox does NOT use a MAC filter - I checked that). But afterwards I could browse too - I don't understand what happened.

My only remaining wireless problem is that it seems I need to use the easy pairing every time I start up the computer and the work session. Once done, the wireless works fine, but shouldn't it be automatic for subsequent sessions? 

You might need the following information, the output from ifconfig and route:
 
richard@Crusoe2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:9a:97:dd  
          inet6 addr: fe80::217:31ff:fe9a:97dd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1848277 (1.8 MB)  TX bytes:228583 (228.5 KB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:31:30:3e:9a  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe30:3e9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4643934 (4.6 MB)  TX bytes:469366 (469.3 KB)
          Interrupt:18 Memory:dfffa000-dfffc000 

richard@Crusoe2:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         livebox.home    0.0.0.0         UG    100    0        0 wlan0

 Thanks, 
Richard alias Zordkhan

---

### Post by Zordkhan on 2010-03-03
No - I was wrong. I really did connect to the internet via wireless this morning as described above - but later in the same day I can't do it. What is happening?

---

