---
title: "wire network not working"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by xnonamex on 2009-09-03
Hi,
lets start with the fact that i'm new with linux, and don't know almost anything about it!
I installed ubuntu 9.04 and the wire conection is not working! on win everything is working fine. i tried to install it seweral times. once it worked fine, i isntalled all the updates, restarted and it didn't work again!
what could be the problem and how should i fix it??
tnx,
xnonamex.

P.S I hawe Toshiba Satellite A210-16F notebook

---

### Post by Iowan on 2009-09-03
Open a terminal (Applications>Accessories>Terminal). Post results of: ```
ifconfig -a
lshw -C network
```

---

### Post by xnonamex on 2009-09-04
eth0      Link encap:Ethernet  HWaddr 00:1b:38:47:fd:2d       
          inet6 addr: fe80::21b:38ff:fe47:fd2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:245 (245.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:251 Base address:0x4000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2080 (2.0 KB)  TX bytes:2080 (2.0 KB)



pan0      Link encap:Ethernet  HWaddr 2e:2d:6a:db:aa:4a 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:1c:26:be:5d:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-1C-26-BE-5D-F1-00-00-00-00-00-00-00-00-00-00
  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
------------------------------------------------------------------------------------------------

xnonamex@PC1:~$
 lshw -c network
WARNING: you should run this program as super-user.

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:47:fd:2d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes

  *-network 
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1c:26:be:5d:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:2d:6a:db:aa:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-09-04
post output of **sudo dhclient eth0** , your wired connection doesnt seem to be getting an ip

---

### Post by xnonamex on 2009-09-04
xnonamex@PC1:~$ sudo dhclient eth0
[sudo] password for xnonamex: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:38:47:fd:2d
Sending on   LPF/eth0/00:1b:38:47:fd:2d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10


hmmm strange... i installed service pack for windows, and when i launched ubuntu first time after that - wired network was working fine... restart - and again nothing!

---

### Post by Iowan on 2009-09-04
Haven't solved many problems with [this]("http://ubuntuforums.org/showthread.php?t=1156441") lately, but you can give it a try...

---

### Post by xnonamex on 2009-09-06
hmmm... didn't help... tried few times... but mby i'm doing it wrong... :???:

i can get it working by booting win vista, then restart->boot ubuntu... but when i restart and boot ubuntu, not working, i have to boot vista again and then again ubuntu... 
when i boot vista, then ubuntu all 5 lights (power,ethernet, dsl,internet, activity) are kept on, but when i boot ubuntu, than rr, and ubuntu again only power, ethernet and dsl keeps on... 

how can vista effect network connections for ubuntu?!

---

