---
title: "Dell mini 10 connects only to some networks"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by intruderukr on 2011-12-09
I have a dual-boot Win 7/ Oneric system on my Dell mini 10.
In my current network environment I'm unable to connect wirelessly.  I've reset the router, so it's not that.  My password configurations and security types are the same as other computers which are connected here.  I am able to connect to other networks I travel to, just not this one.  (Also unable to connect with windows at this network)
Here is some information about my system:
[HTML]trude@trude-Inspiron-1011:~$ sudo ifconfig -a

[sudo] password for trude: 

eth0      Link encap:Ethernet  HWaddr 00:26:b9:bd:f7:ce  

          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::226:b9ff:febd:f7ce/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:684 errors:0 dropped:0 overruns:0 frame:0

          TX packets:795 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:518541 (518.5 KB)  TX bytes:163519 (163.5 KB)

          Interrupt:43 



eth1      Link encap:Ethernet  HWaddr c4:17:fe:7f:da:e2  

          inet6 addr: fe80::c617:feff:fe7f:dae2/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:403

          TX packets:0 errors:22 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:16 errors:0 dropped:0 overruns:0 frame:0

          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)



trude@trude-Inspiron-1011:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)

03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

trude@trude-Inspiron-1011:~$ ifup eth0

ifup: failed to open statefile /var/run/network/ifstate: Permission denied

trude@trude-Inspiron-1011:~$ sudo ifup eth0

Ignoring unknown interface eth0=eth0.

trude@trude-Inspiron-1011:~$ ^C

trude@trude-Inspiron-1011:~$ 


trude@trude-Inspiron-1011:~$ sudo airmon-ng stop wlan0





Interface	Chipset		Driver



eth1		Unknown 		wl
[/HTML]

I have a good connection by ethernet.
Thanks to anyone who can help!

---

