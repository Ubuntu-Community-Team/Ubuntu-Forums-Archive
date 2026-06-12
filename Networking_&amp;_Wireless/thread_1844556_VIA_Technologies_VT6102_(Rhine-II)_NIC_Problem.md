---
title: "VIA Technologies VT6102 (Rhine-II) NIC Problem"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by lovricbot on 2011-09-15
I have a problem with VIA rhine II card, i'm a noob and i'm having problems connecting to the internet. Using Ubuntu 10.04. It seems that Ubuntu is recognizing the card, but internet connection cannot be established. I've tried changing the settings for eth0 connection(setting DHCP to manual), but that didn't solve the problem. Here's what lscpi command gives back:
> 00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

and here is what ifconfig -a gives:
> eth0      Link encap:Ethernet  HWaddr 00:11:09:86:1f:f3  
          inet6 addr: fe80::211:9ff:fe86:1ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38799 (38.7 KB)  TX bytes:26982 (26.9 KB)
          Interrupt:23 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:24:01:61:13:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xd000 

eth1:avahi Link encap:Ethernet  HWaddr 00:24:01:61:13:8b  
          inet addr:169.254.5.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34456 (34.4 KB)  TX bytes:34456 (34.4 KB)



From what i understand ip adress cannot be obtained. Thank you in advance. Via ljubav.;)

---

