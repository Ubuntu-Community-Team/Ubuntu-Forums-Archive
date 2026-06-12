---
title: "Ubuntu 8.10 Wireless help"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by DefConNegative5 on 2009-03-06
I'm on an Inspiron 8000, using microsoft MN-720 wireless card. I followed some instructions to install drivers and got the card working, for the most part. I go into System/Administration/Network, and it actually sees my network - so I set it up. I can also go into System/Preferences/Network Configuration to set it up. 

The only problem is it doesn't connect. In the network icon in the top right of the desktop, I see Auto Eth0 for the wired - but wirless connections is greyed out. 

What am I doing wrong? Please help! It seems like I'm so close. Here's my ifconfig results: 

eth0      Link encap:Ethernet  HWaddr 00:04:75:16:f0:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:968 (968.0 B)  TX bytes:968 (968.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:3a:6d:66:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:f4000000-f4002000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:0d:3a:6d:66:f0  
          inet addr:169.254.8.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Memory:f4000000-f4002000 


And also here is my /etc/network/interfaces

auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wireless-mode managed
wireless-key ABCDEF1234
wireless-essid default

wireless-channel 6
auto wlan0

---

### Post by N04h on 2009-03-06
Have you checked for restricted drivers or updated your system?

---

### Post by DefConNegative5 on 2009-03-10
Does anyone know what that 169.255.*.* address is? Sometimes I get it when I'm using Windows and its not a valid address from my router's DHCP, and it does not successfully connect.

---

