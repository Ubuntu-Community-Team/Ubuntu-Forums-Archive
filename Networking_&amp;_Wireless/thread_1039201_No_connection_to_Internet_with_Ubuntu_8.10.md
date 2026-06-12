---
title: "No connection to Internet with Ubuntu 8.10"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Maurizio74 on 2009-01-14
[COLOR="blue"]Hi,

at home, I have an Asus Notebook connected with a ADSL Router, that normally I use to surf on Internet on Windows. Some days ago, Ubuntu 8.10 was installed in dual boot, but now I can't go on Internet neither ping the router:[/COLOR]
ping 192.168.1.254
connect: Network is unreachable 

[COLOR="blue"]Some informations on my hardware:[/COLOR]

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
03:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

[COLOR="Blue"]The output of the dmesg comand, with some more info (result of ifconfig -a and lspci -vvv) in attachment

Thank you for possible help.
Ciao everybody.
Maurizio

p.s. I first time used this set up of Ubuntu on my Notebook with a wireless router and with no problem for internet [/COLOR]

---

### Post by superprash2003 on 2009-01-14
well the problem is you arent getting an ip address.. try typing this in the terminal and then try connecting.. if you still have problems then post ifconfig output again.. is 192.168.1.254 your router ip?
type the following
sudo dhclient eth0 
 or
sudo dhclient eth1

depending on whether eth0 or eth1 is connected to router..

---

### Post by Maurizio74 on 2009-01-15
[COLOR="Blue"]Still down, I show you the results[/COLOR]

rosandra@rosandra-laptop:~$ sudo dhclient eth0
[sudo] password for rosandra: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:15:f2:b6:53:74
Sending on   LPF/eth0/00:15:f2:b6:53:74
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------------------------------------------------------

rosandra@rosandra-laptop:~$ 
sudo dhclient eth1
[sudo] password for rosandra: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:00:46:f3:6c
Sending on   LPF/eth1/00:15:00:46:f3:6c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------------------------------------------------------

rosandra@rosandra-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:b6:53:74  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:8512 (8.5 KB)  Byte TX:320 (320.0 B)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:15:00:46:f3:6c  
          inet6 addr: fe80::215:ff:fe46:f36c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:627 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:22 Indirizzo base:0xe000 Memoria:fa9ff000-fa9fffff 

eth1:avahi Link encap:Ethernet  HWaddr 00:15:00:46:f3:6c  
          inet addr:169.254.6.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Indirizzo base:0xe000 Memoria:fa9ff000-fa9fffff 

lo        Link encap:Loopback locale  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:73572 (73.5 KB)  Byte TX:73572 (73.5 KB)

----------------------------------------------------------
 
rosandra@rosandra-laptop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 169.254.6.208 icmp_seq=1 Destination Host Unreachable
From 169.254.6.208 icmp_seq=2 Destination Host Unreachable
From 169.254.6.208 icmp_seq=3 Destination Host Unreachable
From 169.254.6.208 icmp_seq=5 Destination Host Unreachable
From 169.254.6.208 icmp_seq=6 Destination Host Unreachable
From 169.254.6.208 icmp_seq=7 Destination Host Unreachable
From 169.254.6.208 icmp_seq=9 Destination Host Unreachable
From 169.254.6.208 icmp_seq=10 Destination Host Unreachable
....

----------------------------------------------------------

rosandra@rosandra-laptop:~$ ping 169.254.6.208
PING 169.254.6.208 (169.254.6.208) 56(84) bytes of data.
64 bytes from 169.254.6.208: icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from 169.254.6.208: icmp_seq=2 ttl=64 time=0.043 ms
64 bytes from 169.254.6.208: icmp_seq=3 ttl=64 time=0.044 ms
64 bytes from 169.254.6.208: icmp_seq=4 ttl=64 time=0.046 ms
64 bytes from 169.254.6.208: icmp_seq=5 ttl=64 time=0.046 ms
64 bytes from 169.254.6.208: icmp_seq=6 ttl=64 time=0.046 ms
....

----------------------------------------------------------

[COLOR="blue"]Yes, 192.168.1.254 is the ip-address of my router (at list in windows) and 192.168.1.137 is the notebook... 
In your opinion what is 169.254.6.208?

Tks
Maurizio[/COLOR]

---

### Post by superprash2003 on 2009-01-15
thats automatic private ip when your router doesnt give you an ip address.. you could try doing this - [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html) .. except for ip address use 192.168.1.138 and for gateway use 192.168.1.254

---

### Post by Maurizio74 on 2009-01-19
> **superprash2003 said:**
> thats automatic private ip when your router doesnt give you an ip address.. you could try doing this - [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html) .. except for ip address use 192.168.1.138 and for gateway use 192.168.1.254

[COLOR="Navy"]Thank you
I resolved with a static ip-address, as your link shows

What was the problem?
I think some DHCP confilct in giving the same ip-address that my PC normally uses with XP. In fact, if I try to assign the same value (192.168.1.138 ) to the static ip-address, it doesn't work. It works if I assign another one (192.168.1.138 )[/COLOR]

---

