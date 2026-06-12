---
title: "no internet access on ubuntu"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by samirafk222 on 2011-04-14
[SIZE=3]hi 
i want to have internet access on ubuntu..but i have the access on win7.
laptop>>win 7
run vmware on laptop for ubuntu.
win7 have internet access but on ubuntu i have not the ping of name such  as ping yahoo.com/google.com, ...but the ping 4.2.2.4/8.8.8.8 of this work correctly , ... what  can i do ?my 7 and ubuntu connect bridge via vmware and i have pppoe  confige on modem for access to internet
lpz help me.

[/SIZE]

---

### Post by dandnsmith on 2011-04-14
You're describing a failure to perform DNS resolution (name lookup) - you need to check the connection details for the DNS settings. You might get some help as to what it should be from your Win7 connection settings.

---

### Post by samirafk222 on 2011-04-14
> **dandnsmith said:**
> You're describing a failure to perform DNS resolution (name lookup) - you need to check the connection details for the DNS settings. You might get some help as to what it should be from your Win7 connection settings.
 
 
Windows IP Configuration
   Host Name . . . . . . . . . . . . : Samira-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
Wireless LAN adapter Wireless Network Connection 2:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 00-26-C7-5E-CF-0F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Wireless Network Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Intel(R) WiFi Link 1000 BGN
   Physical Address. . . . . . . . . : 00-26-C7-5E-CF-0E
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Ethernet adapter Bluetooth Network Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 78-DD-08-A6-6D-22
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Ethernet adapter Local Area Connection:
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8168D/8111D Family PCI-E Gigabit Ethernet NIC (NDIS 6.20)
   Physical Address. . . . . . . . . : 60-EB-69-27-BD-F5
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d1e:b0af:c111:97e6%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.2(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, April 14, 2011 3:11:35 PM
   Lease Expires . . . . . . . . . . : Friday, April 15, 2011 4:17:31 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 241232745
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-14-C6-F4-DB-60-EB-69-27-BD-F5
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Tunnel adapter isatap.{86723F30-7CBB-4451-A236-C83280B42F45}:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Teredo Tunneling Pseudo-Interface:
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:242f:2380:3f57:fefd(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::242f:2380:3f57:fefd%14(Preferred) 
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
Tunnel adapter isatap.{4A125C22-482A-4DC2-B291-CC11B11BBD0A}:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter isatap.{16DEE575-9CBD-4C20-A33B-E67D2C64DE24}:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #7
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

 
that is the rsult of running ipconfig/all on win7(laptop) 
 
 
Realtek RTL8168D/8111D IS MY NIC on win7
 
AND LSO WIN-7
 
C:\Users\Samira>NSLOOKUP
Default Server:  UnKnown
Address:  192.168.1.1
but when type nslookup of ubuntu dont show anythings
and type yahoo.com nothing resolved

---

### Post by dandnsmith on 2011-04-14
OK, try (in a terminal window)
[i]ifconfig
nslookup [www.google.be](www.google.be)
 nslookup 4.2.2.4
route[/i]
You should get some output for each of these commands

---

### Post by samirafk222 on 2011-04-14
Thx for you reply
that is solved.
that was a problem or bug of vmware .with virtual box and the same settings my problem is solved...and have ping yahoo.com

---

### Post by dandnsmith on 2011-04-15
Glad to hear you've a workaround.

---

### Post by FractalFragger on 2011-04-15
well my question is that i will be installing 11.04 tonight and need to know what issues am i gonna face with network adapter drivers and where would i get them from??? 
 
i have a Belkin Wireless N USB Adapter 
and a Broadcom Fast Ethernet Port
 
Any assistance would be great thanks

---

