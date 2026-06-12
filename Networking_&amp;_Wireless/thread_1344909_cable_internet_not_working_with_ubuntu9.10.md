---
title: "cable internet not working with ubuntu9.10"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by sudhir k yadav on 2009-12-03
Hi there,
  i am using  ubuntu9.10 in dual boot with window vista.i am using a cable internet provided by a Internet service provider (ISP) in india (nivyahbroadband). **There is no modem,just simple cable wire going into my LAN card**. My ISP has configured my net connection in vista with user name and password. As my ISP has no idea about how to confure it in ubuntu9.10, i had to do it myself. i had tried everything available on net to configure it but the end result was zero. i am great fan of ubuntu but due to this silly reason i have to boot everytime in vista to surf. I am very much adamant to solve this problem.
 
 
    My network specification:
  Device name- WAN miniport(pppoe)
  Device type-PPPOE
  Server type: PPP
  transports- TCP/IP
  Authentication- MD5CHAP
  compression-none
  ppp multi-link framing-off
  server Ipv4 address-111.125.195.14
  Discription - nivyahbroadband
   
   **My ip address is not static. According to my ISP, it is a DHCP which assign me ip addresses.****when i ran ipconfig /all command in vista, i get the following details.** 
 
 
    
 
 
     Microsoft Windows [Version 6.0.6000]
  Copyright (c) 2006 Microsoft Corporation.  All rights reserved.
   
  C:\Users\Sudhir>ipconfig /all
   
  Windows IP Configuration
   
     Host Name . . . . . . . . . . . . : Sudhir-PC
     Primary Dns Suffix  . . . . . . . :
     Node Type . . . . . . . . . . . . : Hybrid
     IP Routing Enabled. . . . . . . . : No
     WINS Proxy Enabled. . . . . . . . : No
   
  PPP adapter nivyahbroadband:
   
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : nivyahbroadband
     Physical Address. . . . . . . . . :
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
     IPv4 Address. . . . . . . . . . . : 183.87.24.72(Preferred)
     Subnet Mask . . . . . . . . . . . : 255.255.255.255
     Default Gateway . . . . . . . . . : 0.0.0.0
     DNS Servers . . . . . . . . . . . : 121.241.40.26
                                                      111.125.192.11
     NetBIOS over Tcpip. . . . . . . . : Disabled
   
  Wireless LAN adapter Wireless Network Connection:
   
     Media State . . . . . . . . . . . : Media disconnected
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : Intel(R) PRO/Wireless 3945ABG Network Connection
     Physical Address. . . . . . . . . : 00-1B-77-E4-27-2C
     DHCP Enabled. . . . . . . . . . . : Yes
     Autoconfiguration Enabled . . . . : Yes
   
  Ethernet adapter Local Area Connection:
   
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : Marvell Yukon 88E8039 PCI-E Fast Ethernet  Controller
     Physical Address. . . . . . . . . : 00-1A-80-1F-51-9B
     DHCP Enabled. . . . . . . . . . . : Yes
     Autoconfiguration Enabled . . . . : Yes
     Link-local IPv6 Address . . . . . : fe80::e95e:8aa8:e6d3:bd63%8(Preferred)
     Autoconfiguration IPv4 Address. . : 169.254.189.99(Preferred)
     Subnet Mask . . . . . . . . . . . : 255.255.0.0
     Default Gateway . . . . . . . . . : 0.0.0.0
     DHCPv6 IAID . . . . . . . . . . . : 201333376
     DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                                      fec0:0:0:ffff::2%1
                                                     fec0:0:0:ffff::3%1
     NetBIOS over Tcpip. . . . . . . . : Enabled
   
  Tunnel adapter Local Area Connection* 7:
   
     Media State . . . . . . . . . . . : Media disconnected
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : isatap.{DBCE0B85-B102-4E53-9208-9A2B6E007566}
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
   
  Tunnel adapter Local Area Connection* 13:
   
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : isatap.{795661A5-9B68-423E-B407-ABCAF09A80B8}
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
     Link-local IPv6 Address . . . . . : fe80::5efe:169.254.189.99%17(Preferred)
     Default Gateway . . . . . . . . . :
     DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                                    fec0:0:0:ffff::2%1
                                                      fec0:0:0:ffff::3%1
     NetBIOS over Tcpip. . . . . . . . : Disabled
   
  Tunnel adapter Local Area Connection* 14:
   
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
     Link-local IPv6 Address . . . . . : fe80::200:5efe:183.87.24.72%28(Preferred)
   
     Default Gateway . . . . . . . . . :
     DNS Servers . . . . . . . . . . . : 121.241.40.26
                                                    111.125.192.11
     NetBIOS over Tcpip. . . . . . . . : Disabled
   
  Tunnel adapter Local Area Connection* 15:
   
     Media State . . . . . . . . . . . : Media disconnected
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : 6TO4 Adapter
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
   
  Tunnel adapter Local Area Connection* 16:
   
     Media State . . . . . . . . . . . : Media disconnected
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : 6TO4 Adapter
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
   
  Tunnel adapter Local Area Connection* 17:
   
     Connection-specific DNS Suffix  . :
     Description . . . . . . . . . . . : Microsoft 6to4 Adapter #3
     Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
     DHCP Enabled. . . . . . . . . . . : No
     Autoconfiguration Enabled . . . . : Yes
     Temporary IPv6 Address. . . . . . : 2002:b757:1848::b757:1848(Preferred)
     Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
     DNS Servers . . . . . . . . . . . : 121.241.40.26
                                                     111.125.192.11
     NetBIOS over Tcpip. . . . . . . . : Disabled
   
   
   
  ** when i ran the command ifconfig -a in ubuntu, i am unable to get any ip address.**
 
 
     
  sudhir@sudhir-laptop:~$ ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:1a:80:1f:51:9b  
            inet6 addr: fe80::21a:80ff:fe1f:519b/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:471 errors:0 dropped:0 overruns:0 frame:0
            TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:57008 (57.0 KB)  TX bytes:44221 (44.2 KB)
            Interrupt:16 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:82 errors:0 dropped:0 overruns:0 frame:0
            TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:7279 (7.2 KB)  TX bytes:7279 (7.2 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1b:77:e4:27:2c  
            BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-E4-27-2C-00-00-00-00-00-00-00-00-00-00  
            [NO FLAGS]  MTU:0  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  **my routing table was as follows:**
  sudhir@sudhir-laptop:~$ route -n
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
   
  sudhir@sudhir-laptop:~$ sudo lshw -C network
    *-network               
         description: Ethernet interface
         product: 88E8039 PCI-E Fast Ethernet Controller
         vendor: Marvell Technology Group Ltd.
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 14
         serial: 00:1a:80:1f:51:9b
         size: 100MB/s
         capacity: 100MB/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=169.254.189.99 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
         resources: irq:28 memory:f6000000-f6003fff ioport:2000(size=256)
    *-network DISABLED
         description: Wireless interface
         product: PRO/Wireless 3945ABG [Golan] Network Connection
         vendor: Intel Corporation
         physical id: 0
         bus info: pci@0000:06:00.0
         logical name: wmaster0
         version: 02
         serial: 00:1b:77:e4:27:2c
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
         configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
         resources: irq:30 memory:fa000000-fa000fff
   
  **since i didn't have any static IP address, i had configured pppoeconf with user name and password provided by my ISP.when i tried to conncet to internet using code: sudo pon dsl-provider,i got following error**
  [EMAIL="sudhir@sudhir-laptop"][COLOR=blue]sudhir@sudhir-laptop[/COLOR][/EMAIL]: sudo pon dsl-provider
  Plugin rp-pppoe.so loaded.
  RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
   
  ** then i had tried to connect using command : sudo dhclient eth0 but i was unable to get any IP to connect.**
 
 
    sudhir@sudhir-laptop:~$ sudo dhclient eth0
  Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/00:1a:80:1f:51:9b
  Sending on   LPF/eth0/00:1a:80:1f:51:9b
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.
   
  **Even i had tried code: sudo dhclient eth0 after editing   /etc/network/interfaces,where have made following enteries:**
  auto eth0
  iface eth0 inet dhclient
   
  But no luck.
   
  can anyone help me with this. I will really appreciate your help. 

   
  thanks.
  sudhir

---

