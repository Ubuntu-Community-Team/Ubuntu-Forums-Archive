---
title: "WiFi AP setting trouble"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by S.A.V on 2011-09-09
Hello everybody,
I'm newbie Linux Ubuntu & I need your help.
The last week I'm trying to make wifi card to work as AP but haven't success.
WiFi card is Intel Corporation PRO/Wireless 2200BG [Calexico2].
I can't switch on Master mode using** sudo iwconfig eth1 mode Master**:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
  
I think that my problem is IRQ conflict:

**uname -r**
2.6.32-33-generic 

**lspci | grep Wireless**
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

**dmesg | grep Intel**
[    0.000000]   Intel GenuineIntel
[   22.636137] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   23.225151] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 4 (level, low) -> IRQ 4
[   23.225188] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   23.616533] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.936621] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.936624] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.942642] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[B]
sudo lshw -c network[/B]
  _**-network:0             *_
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:11:d8:9f:d5:84
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5788-v3.03 ip=95.84.249.215 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources:** [COLOR=Red]irq:4[/COLOR]** memory:ff9f0000-ff9fffff
  _*-network:1 DISABLED_
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:80:86:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: **[COLOR=Red]irq:4[/COLOR]** memory:ff9ee000-ff9eefff

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:d8:9f:d5:84  
          inet addr:95.84.249.215  Bcast:95.84.249.255  Mask:255.255.254.0
          inet6 addr: fe80::211:d8ff:fe9f:d584/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7297963 (7.2 MB)  TX bytes:1285625 (1.2 MB)
          Interrupt:4 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24423 (24.4 KB)  TX bytes:24423 (24.4 KB)


**sudo ifconfig eth1 up**
**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:d8:9f:d5:84  
          inet addr:95.84.249.215  Bcast:95.84.249.255  Mask:255.255.254.0
          inet6 addr: fe80::211:d8ff:fe9f:d584/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7298461 (7.2 MB)  TX bytes:1285625 (1.2 MB)
          Interrupt:4 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:80:86:41  
          inet6 addr: fe80::20e:35ff:fe80:8641/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:18 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:4 Base address:0xa000 &#1055;&#1072;&#1084;&#1103;&#1090;&#1100;:ff9ee000-ff9eefff 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24423 (24.4 KB)  TX bytes:24423 (24.4 KB)

Does anybody know how to resolve IRQ conflict?

---

### Post by S.A.V on 2011-09-25
Hi All,
 
I thought that trouble deals with IRQ conflict but actually Linux ipw2200 does not support ability for Master mode & need to compile driver using [http://sourceforge.net/projects/ipw2200-ap/](http://sourceforge.net/projects/ipw2200-ap/).
 
I can't compile [http://sourceforge.net/projects/ipw2200-ap/](http://sourceforge.net/projects/ipw2200-ap/) because of errors for 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux.
I will appreciate for help me to correct Makefle for this kernel release.

---

