---
title: "Two interfaces with same mac."
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by lethall1 on 2012-07-12
Hi all.
After system upgrade i have some problems with my network cards:

***#ifconfig***
> bond0     Link encap:Ethernet  HWaddr **00:15:17:27:68:98**  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:fe27:6898/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:2160712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4866124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878077059 (878.0 MB)  TX bytes:6044698826 (6.0 GB)

eth0      Link encap:Ethernet  HWaddr **00:15:17:27:68:98**  
          UP BROADCAST RUNNING PROMISC SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2151049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4859721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:877221577 (877.2 MB)  TX bytes:6043709947 (6.0 GB)
          Interrupt:17 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.252
          inet6 addr: fe80::2d0:43ff:fe7a:c8ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:919057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:727478499 (727.4 MB)  TX bytes:189766297 (189.7 MB)

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:862944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:862944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276073705 (5.2 GB)  TX bytes:5276073705 (5.2 GB)

rename4   Link encap:Ethernet  HWaddr **00:15:17:27:68:98**  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:9663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:855482 (855.4 KB)  TX bytes:988879 (988.8 KB)But my ***/etc/netwirk/interfaces*** looks like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
   bond-master bond0

auto eth2
iface eth2 inet manual
   bond-master bond0

auto bond0
iface bond0 inet static
address 192.168.1.1
netmask 255.255.255.0
bond_mode 0
bond_miimon 100
bond-downdelay 200
bond-updelay 200
bond-slaves none***cat /etc/udev/rules.d/70-persistent-net.rules***
> # PCI device 0x8086:0x1076 (e1000)
SUBSYSTEM=="net", ACTION=="add",  DRIVERS=="?*", ATTR{address}=="00:15:17:27:68:98", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

...

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:17:27:68:98",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"i have 3 network cards inside
***lshw***
> *-network:0
                &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface
                &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: 82557/8/9/0/1 Ethernet Pro 100
                &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corporation
                &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 08
                &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 00:d0:43:7a:c8:ee
                &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 100Mbit/s
                capacity: 100Mbit/s
                &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
                &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
                &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=92.60.91.118  latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII  speed=100Mbit/s
                &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:16 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e1a40000-e1a40fff ioport:1440(size=64) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e1900000-e19fffff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f8000000-f80fffff
           *-network:1
                &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface
                &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: RTL-8169 Gigabit Ethernet
                &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Realtek Semiconductor Co., Ltd.
                &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 1
                bus info: pci@0000:03:01.0
                logical name: eth0
                &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 10
                &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 00:15:17:27:68:98
                &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 100Mbit/s
                capacity: 1Gbit/s
                &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
                &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 66MHz
                 &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm bus_master cap_list rom ethernet physical  tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                 &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes  driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A  latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII  promiscuous=yes slave=yes speed=100Mbit/s
                &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:17 ioport:1000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e1a41000-e1a410ff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f8100000-f811ffff
           *-network:2
                &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface
                &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: 82541GI Gigabit Ethernet Controller
                &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corporation
                &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 2
                bus info: pci@0000:03:02.0
                logical name: rename4
                &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 05
                &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 00:15:17:27:68:98
                &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 100Mbit/s
                capacity: 1Gbit/s
                &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
                &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 66MHz
                 &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm pcix bus_master cap_list rom ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                 &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes driver=e1000  driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A latency=32  link=yes mingnt=255 multicast=yes port=twisted pair slave=yes  speed=100Mbit/s
                &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:18 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e1a20000-e1a3ffff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e1a00000-e1a1ffff ioport:1400(size=64) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f8120000-f813ffff

yes, i have installed bonding (long time ago), using this man page[ https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding")
But as you can see, there is 2 adapters with different MAC addresses
I have 2 adapters with the same mac T_T

cat /proc/net/bonding/bond0 
> Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200

Slave Interface: eth0
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:15:17:27:68:98
Slave queue ID: 0

Slave Interface: rename4
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:15:17:27:68:98
Slave queue ID: 0What the strange things happens? How do i rename interface with the same mac? Why does rename4 interface appeared? What i need to to do fix it?
Thanks a lot.

---

### Post by lethall1 on 2012-07-12
Solved by changing network card.

---

