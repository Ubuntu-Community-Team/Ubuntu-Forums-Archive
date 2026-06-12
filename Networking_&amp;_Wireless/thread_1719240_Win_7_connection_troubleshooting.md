---
title: "Win 7 connection troubleshooting?"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by Neil_Mac on 2011-04-01
Hi!
I installed Gadmin-Samba and a eth1. Setup the info in gadmin for waht I could follow and then shared the bub folder in win7. Have direct cable between the 2 nics, they see each other, however Win 7 says "unidentified network" (with a bench) and no connection established. In Ubuntu  Places/network folder it has "Windows Netork" folder, but its empty.
What am I missing?
Thanks!

---

### Post by P_i_n_k on 2011-04-01
Is the cable you have directly connecting the two machines a "cross over" cable? 
If not are you sure that the interfaces in both machines are capable of auto detecting the cable type and dealing with it?

On the Windows box, Open a command prompt. 
What is the output from running the command below?
```
ipconfig /all
```On the Ubuntu box open a command prompt.
What is the output from running the command below?
```
sudo ifconfig -a
```I'd guess I'd start with those first of all then someone might be able to give more help.

---

### Post by Neil_Mac on 2011-04-01
Ubuntu;

eth0      Link encap:Ethernet  HWaddr 00:15:f2:7f:14:e9  
          inet addr:199.126.214.49  Bcast:199.126.215.255  Mask:255.255.252.0
          inet6 addr: fe80::215:f2ff:fe7f:14e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2368136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2124209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2589 txqueuelen:1000 
          RX bytes:2120445840 (2.1 GB)  TX bytes:340360752 (340.3 MB)
          Interrupt:21 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:50:bf:06:53:36  
          inet6 addr: fe80::250:bfff:fe06:5336/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41614 (41.6 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:16 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

------------------------------------------
Win7 box
Using standard black cable (have a yellow but use that on ubuntu to HUB for internet)
-------------------------------------------
Microsoft Windows [Version 6.1.7600] 
Copyright (c) 2009 Microsoft Corporation.  All rights reserved. 
 
C:\Users\NeilMac>ipconfig /all 
 
Windows IP Configuration 
 
   Host Name . . . . . . . . . . . . : Graphics3D 
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid 
   IP Routing Enabled. . . . . . . . : No 
   WINS Proxy Enabled. . . . . . . . : No 
 
Ethernet adapter Local Area Connection 2: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet 
 NIC 
   Physical Address. . . . . . . . . : 00-50-BF-27-45-6E 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
 
Ethernet adapter Local Area Connection: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : NVIDIA nForce 10/100 Mbps Ethernet 
   Physical Address. . . . . . . . . : 70-71-BC-16-9C-60 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
   Link-local IPv6 Address . . . . . : fe80::d037:e058:c831:5dde%11(Deprecated) 
 
   Autoconfiguration IPv4 Address. . : 169.254.93.222(Deprecated) 
   Subnet Mask . . . . . . . . . . . : 255.255.0.0 
   Default Gateway . . . . . . . . . : 
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1 
                                       fec0:0:0:ffff::2%1 
                                       fec0:0:0:ffff::3%1 
   NetBIOS over Tcpip. . . . . . . . : Enabled 
 
Tunnel adapter isatap.{4B8A0AA0-5BFF-4A89-BA37-1AC8FCFED6FA}: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 13: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter isatap.{2B77133D-5EE2-4849-BAE6-53840AB62629}: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes

---

### Post by P_i_n_k on 2011-04-02
> **Neil_Mac said:**
> Ubuntu;

**eth0**      Link encap:Ethernet  HWaddr 00:15:f2:7f:14:e9  
          **inet addr:199.126.214.49**  Bcast:199.126.215.255  Mask:255.255.252.0
          inet6 addr: fe80::215:f2ff:fe7f:14e9/64 Scope:Link
          **UP** BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
**eth1**      Link encap:Ethernet  HWaddr 00:50:bf:06:53:36  
          **inet6 addr: fe80::250:bfff:fe06:5336/64** Scope:Link
          **UP** BROADCAST MULTICAST  MTU:1500  Metric:1

From the above we can see you have two network interfaces. One (eth0) is connected correctly to some external network and has been assigned a valid IP address for its purpose.

The other (eth1) believes it has a physical connection (UP) but has only been assigned an auto configuration local IP version 6 address.

          > **Neil_Mac said:**
> 
------------------------------------------
Win7 box
Using standard black cable (have a yellow but use that on ubuntu to HUB for internet)
-------------------------------------------

**Ethernet adapter Local Area Connection 2**: 
 
   **Media State . . . . . . . . . . . : Media disconnected **
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet 
 NIC 
   Physical Address. . . . . . . . . : 00-50-BF-27-45-6E 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
 
**Ethernet adapter Local Area Connection: **
 
   **Media State . . . . . . . . . . . : Media disconnected **
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : NVIDIA nForce 10/100 Mbps Ethernet 
   Physical Address. . . . . . . . . : 70-71-BC-16-9C-60 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
   **Link-local IPv6 Address . . . . . : fe80::d037:e058:c831:5dde%11(Deprecated) **
 
   **Autoconfiguration IPv4 Address. . : 169.254.93.222(Deprecated) **
   Subnet Mask . . . . . . . . . . . : 255.255.0.0 
   Default Gateway . . . . . . . . . : 
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1 
                                       fec0:0:0:ffff::2%1 
                                       fec0:0:0:ffff::3%1 
   NetBIOS over Tcpip. . . . . . . . : Enabled 
 

From this we can see that on the windows machine you also have two network interfaces, one is on board (Local Area Connection - Nforce) and does not believe it has a correct physical connection (Media disconnected). However it has still given itself an auto configuration local link IP version 4 and IP Version 6 address.

You appear to be using the on board network interface on the windows 7 machine currently.

This leads me to believe that you are connecting the two machines directly and are not using a cross over cable and your network cards do not both support auto cable detection.

However in your original post you say "They can see each other", what do you mean by this statement? I ask because you also say that you cannot see each machine in the other machine's network folder.

I suspect that you need to get your hands on a cross over cable to connect both machines or you need to have a Hub/Switch to connect both machines to each other via. I.E. plug one machine into one port of a switch and then the other machine also plugged in to that switch.

You need to establish a valid TCP/IP connection first before you get into the windows sharing/samba side of things.

It looks like you have some form of connection there, but windows is definitely not happy with it (Media disconnected).

Some more detail on how you've got this wired up physically would be of benefit.

Do you know what I mean when I say a Cross Over cable?
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

Hope this is of some help.

---

### Post by Neil_Mac on 2011-04-02
Yes thats why I mentioned the yellow cable, Black was standard and the colored ones were crossovers. Dont recall the color codes for all yellow cable. I switched them to see if it made a diff but still the same, unidentified network.

I opened up my Win7 eth and gave it a 192.168... address (been a long time since I did this), maybe that will give some direction, however dont see anything happening.

Thanks!

(I can ping the other eth, it has a 127.0.0.1 address (ubuntu), maybe one of them needs a DHCP signal ??)

---

