---
title: "Configuring Hathway(cable internet) on ubu 8.10"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by dinesh_ddt on 2009-08-04
Hi guys,

Installed 8.10 successfully on my lap. its cool. but sux without net.
so help me configuring my internet connection..

i typed ipconfig /all in windows and got this


[B]C:\Users\Dinesh>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Dinesh-Laptop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Dell Wireless 1395 WLAN Mini-Card
   Physical Address. . . . . . . . . : 00-23-4E-1A-E0-9A
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8040 PCI-E Fast Ethernet
 Controller
   Physical Address. . . . . . . . . : 00-21-9B-F2-27-A5
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b013:6298:a422:2515%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 116.75.121.191(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Lease Obtained. . . . . . . . . . : 04 August 2009 20:44:35
   Lease Expires . . . . . . . . . . : 05 August 2009 20:47:32
   Default Gateway . . . . . . . . . : 116.75.112.1
   DHCP Server . . . . . . . . . . . : 202.88.156.20
   DNS Servers . . . . . . . . . . . : 202.88.156.8
                                       202.88.156.6
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{058FE8C5-0283-449C-93ED-3C70DA424
533}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:cf2e:3096:2f:1f24:8bb4:8640(Prefer
red)
   Link-local IPv6 Address . . . . . : fe80::2f:1f24:8bb4:8640%10(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 12:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 13:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{EF26D505-447E-42D3-8506-5AF4DBC53
1A2}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 15:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 20:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 21:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:744b:79bf::744b:79bf(Preferred)
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 202.88.156.8
                                       202.88.156.6
   NetBIOS over Tcpip. . . . . . . . : Disabled[/B]


As I'm a n00b plz give me step by step guideline to set up d connection..
Thanks in advance..!! :D

---

### Post by superprash2003 on 2009-08-04
do you require any username/password for this connection? or just need to setup static ip?

---

