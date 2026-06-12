---
title: "Wireless working but wired not working"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by tech291083 on 2012-06-24
Hi Friends,
 
I use a router - Netgear WGR614v6. I have 2 pcs at home. One is a new laptop with Win 7 on it and another is a desktop pc with a dual-boot configuration ie Win 7 and Fedora 16 (or sometimes Ubuntu or some other Linux distro)
 
I use this router to connect to the internet. I use laptop as a wireless connection and pc as a wired connection with an ethernet cable going into the back of the router and pc. For the last few days whenever I connect both the devices ie laptop via wireless and pc via LAN port, the router starts resetting itself and I can not surf the net at all. If I disconnect LAN connection then, the wireless connection (laptop) works without any problmes whatsoever. Why so? Both of them ie laptop and pc are well protected with all the latest updates and internet security software of a reputed brand. There is no virus problem as such. I have tried all the 4 LAN ports, but the problem was still there as it was earlier.

---

### Post by tech291083 on 2012-06-24
Following is the output to a command called **ipconfig /all** in Win 7 laptop.
 
 
```
 
Windows IP Configuration
   Host Name . . . . . . . . . . . . : John-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
Wireless LAN adapter Wireless Network Connection 2:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 64-27-37-72-CD-45
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Wireless Network Connection:
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Broadcom 802.11n Network Adapter
   Physical Address. . . . . . . . . : 64-27-37-72-CD-45
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::ddd6:a951:cc94:47b7%12(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.2(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 23 June 2012 11:10:26 PM
   Lease Expires . . . . . . . . . . : 24 June 2012 11:10:26 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 392439607
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-16-B7-90-1B-DC-0E-A1-54-5F-79
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Ethernet adapter Local Area Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Broadcom NetLink (TM) Gigabit Ethernet
   Physical Address. . . . . . . . . : DC-0E-A1-54-5F-79
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Teredo Tunneling Pseudo-Interface:
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fd:1087:9e4:3f57:fefd(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::1087:9e4:3f57:fefd%16(Preferred) 
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
Tunnel adapter isatap.{50042460-F728-4618-9D67-808C9ED9C76F}:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


```

---

