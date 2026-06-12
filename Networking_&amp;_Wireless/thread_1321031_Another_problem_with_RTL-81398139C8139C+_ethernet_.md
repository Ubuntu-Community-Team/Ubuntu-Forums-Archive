---
title: "Another problem with RTL-8139/8139C/8139C+ ethernet network card. PLEASE HELP!"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by baroš on 2009-11-09
[SIZE=3]Hello everyone. This is my first post and I am **new to Ubuntu**. I hope you can help me solve my problem.

Problem description: 
I am using Linux Ubuntu distribution trying to connect multiple PC (four PC's mesh topology) via wired Ethernet network card for my University project. Of course I encountered multiple **problems with Realtek** **Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**. I have read multiple posts and found many discussion but nothing was helpful. **The card doesn't work properly**.  One PC  has one **onboard network card nVidia Corporation CK804 Ethernet Controller  which works fine **and I am using it to connect to Internet. I am using other three Realtek cards to establish LAN connections between PC's(they don't work). **I don't now what is going on** is it 8139cp, 8139too drivers, getting the IPv6 address, 10 Mbps half duplex connection, no link detection. or something else. I have tried many things like removing drivers, loading them again(no success not working), forcing the cards to work on 100 Mbps FD(success), but can not get pass the no link detected. I even managed to get one of the Realtek cards to work (don't know how) and noticed that the card works if it has IPv6 address. Below I am listing command lines and results so that you can analyze it and help me to get my network card working.

[FONT=Courier New][SIZE=2][SIZE=3]zagreb@zagreb-desktop:~$ uname -a
Linux zagreb-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

zagreb@zagreb-desktop:~$ lspci | grep Eth
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

zagreb@zagreb-desktop:~$ lsmod | grep 8139
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp

zagreb@zagreb-desktop:~$ dmesg | grep 8139
[    5.683721] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.683750] 8139cp 0000:01:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.683761] 8139cp 0000:01:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.683768] 8139cp 0000:01:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.686312] 8139too Fast Ethernet driver 0.9.28
[    5.686634] 8139too 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    5.687663] eth0: RealTek RTL8139 at 0xac00, 00:30:4f:45:c6:d6, IRQ 19
[    5.687666] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.687890] 8139too 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    5.688700] eth1: RealTek RTL8139 at 0xa800, 00:30:4f:45:cb:09, IRQ 16
[    5.688702] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.688913] 8139too 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    5.689750] eth2: RealTek RTL8139 at 0xa400, 00:30:4f:45:cb:11, IRQ 17
[    5.689753] eth2:  Identified 8139 chip type 'RTL-8100B/8139D'

zagreb@zagreb-desktop:~$ sudo lshw -c network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 10
       serial: 00:30:4f:45:c6:d6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 10
       serial: 00:30:4f:45:cb:09
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth2
       version: 10
       serial: 00:30:4f:45:cb:11
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:a5:bf:3b:71:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

zagreb@zagreb-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no
zagreb@zagreb-desktop:~$ sudo ethtool eth1
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no
zagreb@zagreb-desktop:~$ sudo ethtool eth2
Settings for eth2:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

zagreb@zagreb-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:4f:45:c6:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:30:4f:45:cb:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa800 

eth2      Link encap:Ethernet  HWaddr 00:30:4f:45:cb:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xa400 

eth3      Link encap:Ethernet  HWaddr 00:01:29:fd:8d:69  
          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fefd:8d69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5082 errors:18 dropped:0 overruns:0 frame:18
          TX packets:587 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1224435 (1.2 MB)  TX bytes:60661 (60.6 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/SIZE]          
[/SIZE][/FONT]
[/SIZE]

---

### Post by SnappyU on 2009-12-17
Care to elaborate what exactly you are doing and what is failing?

eg,
You connect PC with 8139 ethernet to a router and is fails to do a DHCP request or something?

Network diagrams show the links and the failure points would be good.

---

