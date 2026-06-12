---
title: "New instal, network not working"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by HBOCB on 2010-03-14
Hi,
I have just done a new install and have no network (LAN) connection.
My network card blinks as if there is activity but the corresponding diode on my router is not active.
I have checked the ethernet cable by switching with a valid connection to a WinXP system; like this I know that all the router ports are good.
The network configuration module does not indicate a wired connection.
Having read many posts, I have done these tests:
          charles@charles-desktop:~$ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:80:ad:73:23:5b   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           Packets reçus:0 erreurs:0 :0 overruns:0 frame:0    
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 lg file transmission:1000               
           Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)     
           Interruption:10 Adresse de base:0xb800               
 

 lo        Link encap:Boucle locale   
           inet adr:127.0.0.1  Masque:255.0.0.0
           adr inet6: ::1/128 Scope:Hôte        
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           Packets reçus:44 erreurs:0 :0 overruns:0 frame:0
           TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 lg file transmission:0                   
           Octets reçus:2640 (2.6 KB) Octets transmis:2640 (2.6 KB)
 

 charles@charles-desktop:~$ sudo dhclient eth0
 [sudo] password for charles:                  
 Internet Systems Consortium DHCP Client V3.1.2
 Copyright 2004-2008 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 

 Listening on LPF/eth0/00:80:ad:73:23:5b
 Sending on   LPF/eth0/00:80:ad:73:23:5b
 Sending on   Socket/fallback
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.
 charles@charles-desktop:~$ sudo ifconfig eth0 up
 charles@charles-desktop:~$ lspci -nn
 00:00.0 Host bridge [0600]: Intel Corporation 440LX/EX - 82443LX/EX Host bridge [8086:7180] (rev 03)
 00:01.0 PCI bridge [0604]: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge [8086:7181] (rev 03)
 00:04.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
 00:04.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
 00:04.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
 00:04.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
 00:09.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 08)
 00:0b.0 Ethernet controller [0200]: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet [1282:9102] (rev 31)
 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV6 [Vanta/Vanta LT] [10de:002c] (rev 11)
 charles@charles-desktop:~$
 
I have also tried sudo ifdown eth0 and sudo ifup eth0 but receive error message : interface eth0 not configured

Can anyone help as it is my first experience with linux systems. Thank you in advance;)

Charles

---

### Post by Iowan on 2010-03-15
Is thread actually [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), or do you need to mark it  as unsolved?

---

### Post by HBOCB on 2010-03-16
Yes, solved, was hardware problem
Thanks

---

