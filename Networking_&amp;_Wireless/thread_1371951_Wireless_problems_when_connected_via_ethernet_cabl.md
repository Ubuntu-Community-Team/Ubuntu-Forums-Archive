---
title: "Wireless problems when connected via ethernet cable"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by alex389 on 2010-01-04
So I have a weird issue that I was wondering if anyone could help me with.  I am using a Linksys WRT54GL router for my house and I have most of the computers connected wirelessly to it.  The weird issue I have is that when I connected a computer running Ubuntu (9.10) to the router directly with an ethernet cable, it kills the wireless for all of the other computers in the house.  As soon as I disconnect the cable, the wireless works fine.  I've had this problem with multiple ethernet cables, two different Linksys WRT54GL routers and two different computers running Ubuntu 9.10.  I've tried different firmware for the router also.  However, the problem occurs regardless of what components I use.  Basically, the only thing constant here seems to be that it only happens when my router is connected directly via ethernet cable to a computer running Ubuntu 9.10.  I haven't noticed any other times when this problem would come up, and it works fine as soon as I disconnect it.  I'm not an expert at Linux or networking, but it seems like maybe this is some issue with my networking settings.  Does anyone have a clue why this could be happening?

---

### Post by slooksterpsv on 2010-01-04
When you wire in, what IP address is your ubuntu getting:
Open Terminal, type in the following, then copy and paste it back here:
[php]ifconfig[/php]

On a machine that is wireless to the router, type in, in a command prompt (if they're running Windows):
[php]ipconfig /all[/php]

and return the results here as well.

EDIT: Also, what port are you plugging your computer into? It's not an uplink port or the internet port is it?

---

### Post by alex389 on 2010-01-04
I am plugging my computer into one of the ports number 1-4.  It's not the internet or uplink port, and the same port works fine when that computer runs windows.

Here is what I get in Ubuntu, connected via ethernet, when I do ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:1c:23:92:fd:35  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe92:fd35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:602985 (602.9 KB)  TX bytes:131565 (131.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:19:d2:75:5f:7d  
          inet6 addr: fe80::219:d2ff:fe75:5f7d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10598 (10.5 KB)  TX bytes:6469 (6.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-75-5F-7D-37-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by alex389 on 2010-01-04
Here is what I am getting on a Windows computer, connected wirelessly, using ipconfig /all.

Windows IP Configuration

   Host Name . . . . . . . . . . . . : MARINA-LAPTOP
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Dell Wireless 1395 WLAN Mini-Card
   Physical Address. . . . . . . . . : 00-22-69-A1-BB-94
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.106(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, January 03, 2010 11:37:23 AM
   Lease Expires . . . . . . . . . . : Monday, January 04, 2010 11:37:23 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8040 PCI-E Fast Ethernet
 Controller
   Physical Address. . . . . . . . . : 00-21-9B-F0-D4-7D
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

---

### Post by alex389 on 2010-01-04
The one thing I forgot to mention is that this problem isn't always consistent.  Sometimes, it only happens after the Ubuntu computer (connected via ethernet) is connected for some amount of time.  In the output I pasted above, I had the Ubuntu computer connected by wire and the Windows computer connected wirelessly, but for some reason, the router did not drop the wireless that time.  Sometimes it happens as soon as I plug in the Ubuntu computer, and other times it works fine for hours and then stops working randomly.  Unfortunately, I couldn't reproduce the issue just now, but hopefully the above information may still help.

---

### Post by alex389 on 2010-01-05
So does anyone have a clue why this issue could be happening or how to fix it?

---

