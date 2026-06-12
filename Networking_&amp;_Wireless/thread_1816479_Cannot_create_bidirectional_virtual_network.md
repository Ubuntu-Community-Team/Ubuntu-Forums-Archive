---
title: "Cannot create bidirectional virtual network"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-08-02
Hello everyone. I am trying to create a virtual network using Windows 7 Ultimate as the virtual machine and Ubuntu 10.04 as the host. I can currently ssh and telnet from the virtual windows machine to my ubuntu host. But i cannot ssh and telnet from the ubuntu host to the windows 7 virtual machine. I don't understand how it could work one way but not the other. 

I ran the ipconfig /all command from the virtual windows machine to give you details about the network from the virtual side. 

```

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\virtual7>ipconfig

Windows IP Configuration


Ethernet adapter NAT:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::1af:a96c:462:13dd%16
   IPv4 Address. . . . . . . . . . . : 10.0.4.15
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.0.4.2

Ethernet adapter VBOXNET0:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::1de3:5526:3435:174b%13
   IPv4 Address. . . . . . . . . . . : 192.168.56.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Ethernet adapter Bridged eth0:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::d9d7:28b7:29c8:1b68%11
   IPv4 Address. . . . . . . . . . . : 192.168.137.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.{C935FDC0-ECB5-487A-9AB6-193F73560883}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{2C8B8523-13C9-4EA0-8EDC-88D1EC9BE3EF}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{04CFEB1C-ADBD-4C67-B768-4B86D1C20EA8}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter 6TO4 Adapter:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

C:\Users\virtual7>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : virtual7-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter NAT:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter #3
   Physical Address. . . . . . . . . : 08-00-27-89-EB-25
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::1af:a96c:462:13dd%16(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.0.4.15(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 02 August 2011 06:15:51
   Lease Expires . . . . . . . . . . : 03 August 2011 06:15:51
   Default Gateway . . . . . . . . . : 10.0.4.2
   DHCP Server . . . . . . . . . . . : 10.0.4.2
   DHCPv6 IAID . . . . . . . . . . . : 386400295
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-B2-4E-4E-08-00-27-69-BA-94

   DNS Servers . . . . . . . . . . . : 149.254.230.7
                                       149.254.192.126
                                       8.8.8.8
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VBOXNET0:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter #2
   Physical Address. . . . . . . . . : 08-00-27-B3-4F-0C
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::1de3:5526:3435:174b%13(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.56.101(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 02 August 2011 06:11:54
   Lease Expires . . . . . . . . . . : 02 August 2011 07:12:00
   Default Gateway . . . . . . . . . :
   DHCP Server . . . . . . . . . . . : 192.168.56.100
   DHCPv6 IAID . . . . . . . . . . . : 302514215
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-B2-4E-4E-08-00-27-69-BA-94

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bridged eth0:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter
   Physical Address. . . . . . . . . : 08-00-27-69-BA-94
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d9d7:28b7:29c8:1b68%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.137.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 235405351
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-B2-4E-4E-08-00-27-69-BA-94

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%2
                                       fec0:0:0:ffff::2%2
                                       fec0:0:0:ffff::3%2
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{C935FDC0-ECB5-487A-9AB6-193F73560883}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{2C8B8523-13C9-4EA0-8EDC-88D1EC9BE3EF}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{04CFEB1C-ADBD-4C67-B768-4B86D1C20EA8}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter 6TO4 Adapter:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

C:\Users\virtual7>

```

I have also included a screen shot of the network. 

Thanks, 
SlashWannabe94

---

### Post by jmoorse on 2011-08-02
You should communicate between the hosts with the 192.168.56.x network.  You should be able to reach the Windows guest via 192.168.56.101 from the ubuntu box.

Your virtual nic is set to NAT.  If you really want to communicate with 192.168.1.x addressing set it to bridged.

---

### Post by slashwannabe94 on 2011-08-11
I have fixed it now. thanks for the suggestion though man :)

---

