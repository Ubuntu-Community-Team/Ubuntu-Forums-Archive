---
title: "edubuntu 12.04 Broadcom wifi error Samsung RV520"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by alexkurzin on 2012-05-03
I just upgraded to Ubuntu 12.04, and WiFi is not working
My laptop is samsung rv520, running Ubuntu 12.04. When I go into  the additional drivers section of system settings, the drivers show up,  but when i click activate, it comes up with this error: 

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

sudo lshw -C network
 *-network               
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: BCM4313 802.11b/g/n Wireless LAN Controller
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Broadcom Corporation
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:02:00.0
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: eth1
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 01
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: b4:74:9f:cf:e4:16
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress bus_master cap_list ethernet physical wireless
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.101 latency=0 multicast=yes wireless=IEEE 802.11
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:16 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f3200000-f3203fff
  *-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: RTL8111/8168B PCI Express Gigabit Ethernet controller
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Realtek Semiconductor Co., Ltd.
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:03:00.0
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: eth0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 06
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: e8:11:32:58:e0:ac
       &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 100Mbit/s
       capacity: 1Gbit/s
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.30 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:42 ioport:2000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f3104000-f3104fff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f3100000-f3103fff

---

### Post by bkratz on 2012-05-03
You probably just need to blacklist some competitive drivers ( brcmsmac and bcma) since you are using the STA driver (wl). anyway, more information can be found here.[FONT=monospace]

[http://ubuntuforums.org/showpost.php?p=11703305&postcount=3](http://ubuntuforums.org/showpost.php?p=11703305&postcount=3)


[/FONT]

---

