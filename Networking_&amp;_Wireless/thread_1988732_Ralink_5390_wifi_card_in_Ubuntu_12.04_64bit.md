---
title: "Ralink 5390 wifi card in Ubuntu 12.04 64bit"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by DoctorChe on 2012-05-28
I just upgraded Ubuntu to 12.04 and now wifi dosn't work.

Some info:

 lshw -C network
>   *-network               
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: RTL8111/8168B PCI Express Gigabit Ethernet controller
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Realtek Semiconductor Co., Ltd.
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:01:00.0
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: eth0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 06
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 68:b5:99:e1:6d:69
       &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 100Mbit/s
       capacity: 1Gbit/s
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.2.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:40 ioport:2000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:d0004000-d0004fff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:d0000000-d0003fff
  *-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Network controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Ralink corp.
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:02:00.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress bus_master cap_list
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=rt2860 latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:17 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:d0100000-d010ffff
  *-network &#1042;&#1067;&#1050;&#1051;&#1070;&#1063;&#1045;&#1053;&#1054; [COLOR="Red"]DISABLED[/COLOR]
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 2
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: ra0
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: ethernet physical wireless
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA


iwconfig
> lo        no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

ifconfig
> eth0      Link encap:Ethernet  HWaddr 68:b5:99:e1:6d:69  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6ab5:99ff:fee1:6d69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6249737 (6.2 MB)  TX bytes:1903142 (1.9 MB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22755 (22.7 KB)  TX bytes:22755 (22.7 KB)

sudo modprobe rt5390sta
> nothing...

sudo iwlist wlan0 scan
> wlan0     Interface doesn't support scanning.

rfkill list all
> 0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

dmesg | grep rt5
> [   17.117433] rt5390sta: module license 'unspecified' taints kernel.

uname -r
> 3.2.0-24-generic

---

### Post by DoctorChe on 2012-05-29
Can somebody help me?

---

### Post by joshyuCMU on 2012-06-01
I want to know this too!! I have followed every step of downloading the driver and compilling it (sudo make -> sudo make install -> modprobe blah) but it doesn't quite work. It shows connected to the wifi spot but I can't go to any website or ping them. Help would be greatly appreciated!!

---

