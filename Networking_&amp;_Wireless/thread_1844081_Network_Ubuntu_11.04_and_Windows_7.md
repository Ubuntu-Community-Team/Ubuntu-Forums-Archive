---
title: "Network Ubuntu 11.04 and Windows 7"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by axelsword on 2011-09-14
Hello!

I would like to enable a simple file sharing between two laptops. One has Ubuntu 11.04. The other has MS Windows 7 Professional.

I am using a cable to connect computers directly. Do I need a switch or a router?

I have tried different solutions by other people, but the closest I got was I saw the win machine from Ubuntu, in file explorer sidepane selecting "Network" - Windows network - workgroup_name (in my case "TVGS").

I installed samba from Ubuntu software center, changed workgroup on linux from "Turn off pc (right upper corner)" - System Settings - Samba.

Please help.

---

### Post by cap10Ibraim on 2011-09-14
make sure to enable network discovery and file sharing in windows 7 
from the network and sharing control panel
did you ping from one device to another ?

---

### Post by axelsword on 2011-09-16
Sorry, I am a noob because I don't know the address to ping.

On Ubuntu 11.04 it shows that I am not connected to any wired network at all.
The ifconfig gives follwing result:

```
leo@leo-TravelMate-2410:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:e2:62:e1  
          inet6 addr: fe80::20a:e4ff:fee2:62e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4401 (4.4 KB)  TX bytes:5228 (5.2 KB)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:1d:98:8b  
          inet addr:10.17.10.21  Bcast:10.17.15.255  Mask:255.255.248.0
          inet6 addr: fe80::214:a4ff:fe1d:988b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6667405 (6.6 MB)  TX bytes:295422 (295.4 KB)
```Yes, on Win 7 network discovery and file sharing is set to enabled.
Right now I don't have DHCP on Win 7. It has IP 192.255.0.2, subnet mask 255.255.255.0, gateway 1.1.1.1

---

