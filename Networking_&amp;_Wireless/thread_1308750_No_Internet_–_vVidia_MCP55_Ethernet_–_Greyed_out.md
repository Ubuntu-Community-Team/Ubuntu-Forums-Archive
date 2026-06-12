---
title: "No Internet – vVidia MCP55 Ethernet – Greyed out"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Fighter77 on 2009-10-31
I dual boot Vista 32 bit and Ubuntu 9.10

My Vista Network Connection – works OK – details:
--------------------------------------------------------------------
Connection-specific DNS Suffix
Description 				NVIDIA nForce Networking Controller#2
Physical Address			00-1A-92-61-AF-DA
DHCP Enabled			Yes
Ipv4 IP Address			10.0.0.1
Ipv4 Subnet Mask			255.255.255.0
Ipv4 Default Gateway		10.0.0.138
Ipv4 DHCP Server			10.0.0.138
Ipv4 DNS Server			10.0.0.0.138
Ipv4 WINS Server
NetBIOS over Tcpip Enabled	Yes
Link-local Ipv6 Address		fe80::645b:4f75:2008:9570%9
Ipv6 Default Gateway
Ipv6 DNS Server
--------------------------------------------------------


On bootup,to Ubuntu -  no Internet Connection Icon. Re set manually using ip4 setting gives:

-----------------------------------------------------------------
Active Network Connections
Auto eth1 (default)
Hardware Address:		00:1A:92:61:AF:DA
Driver:				forcedeth
Speed:			100Mb/s
Security:			None
IP Address:			10.0.0.1
Broadcast Address:		10.0.0.255
Subnet Mask:		255.255.255.0
Default Route:		10.0.0.138


Terminal gives:
---------------------------------
Ifconfig eth1
Link encap:Ethernet     Hwaddr   00:1a:92:61:af:da
Inet    addr: 10.0.0.1    Bcast: 10.0.0.255    Mask:255.255.255.0
Inet 6 addr:    fe80::21a:92ff:fe61:afda/64    Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overrunns:0 frame:0
TX packets:0 errors:0 dropped:0 overrunns:0 carrier:0
Collisions:0 txqueuelen:1000
RX bytes:0  (0.0B)    TX bytes:4646 (4.6 KB)
Interrupt:32 Base address:0x4000

----------------------------------


Now in Ubuntu ( after resetting the ip4 settings above) The Internet Icon the [ Wired Network vVidia MCP55 Ethernets] –  are still Greyed out but the Auto eth1 is now Black and says I am now connected to the Internet. However I am not as I am unable to Ping or get a URL in Firefox.
Reinstalling, rebooting & turning off my Firewall does not fix the problem.

I ran “lspci” in Terminal, however the info provided did not give me any clues as to why Ubuntu cannot “see/find” the Ethernets.
Help please.

---

### Post by Fighter77 on 2009-11-02
I installed 9.10 on my Laptop & both Wired & Wireless connected instantly.
Therefore the problem must be with the “Drivers” of the [NVIDIA nForce Networking Controller]
I do not know how to fix this problem yet, Will post if I am successful.

---

### Post by Fighter77 on 2009-11-02
No Internet – nVidia MCP55 Ethernet [nVidia nForce Networking Controller]  – Greyed out

Updating [ nVidia nForce Networking Controller ] from the Original;
Driver Date - 21/06/2006
Driver Version - 6.2.0.126
To
Driver Date - 1/08/2008
Driver Version - 67.8.9.0

Did not fix the problem.

---

