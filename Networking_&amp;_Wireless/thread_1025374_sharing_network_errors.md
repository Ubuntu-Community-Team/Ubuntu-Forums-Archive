---
title: "sharing network errors"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by poboy975 on 2008-12-30
hi, ok I've looked and haven't beena able to find a solution that works for me. I have a dell inspirion 5150 laptop with ubuntu intrepid installed. I can connect wirelessly to my internet. I want to share that connection through the wired cable to desktop computer. I tried the firestarter and dhcp3-server setup i found on here. but desktop just wont see the laptop. 
my lspci output is :
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

my ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:17:2b:cb  
          inet6 addr: fe80::20f:1fff:fe17:2bcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202046 (202.0 KB)  TX bytes:2879591 (2.8 MB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:1f:17:2b:cb  
          inet addr:169.254.5.54  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7458384 (7.4 MB)  TX bytes:7458384 (7.4 MB)

wlan1     Link encap:Ethernet  HWaddr 00:90:4b:2f:64:b6  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe2f:64b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1221271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1183242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:884284711 (884.2 MB)  TX bytes:762357316 (762.3 MB)
          Interrupt:18 Memory:faffc000-faffe000 
I'm sure its something simple, but I havent been able to figure it out. when I try to add new connection in network manager, nothing happens...I go through the setup of a wired connection. but it doesnt save it. no new connection appears. btw, my desktop is ubuntu hardy, I also need it to cononect to this laptop. I have it setup for dhcp on wired connection. but nothing ever happens. it doesnt connect. or even able to ping laptop. I would appreciate any help you can give me. thanks

---

### Post by Iowan on 2008-12-30
You've seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?

---

### Post by poboy975 on 2008-12-30
yeah, I have gone through the setup there as well. I can now ping the linux laptop from the linux desktop. I can see the windows shares on the windows desktop from the linux desktop. I cannot see the windows share from the laptop. I can ping the linux and windows desktoips from the laptop. but no internet on either the linux desktop nor the windows desktop. only on laptop still. not sure what I'm doing wrong

---

### Post by Rohan Kapoor on 2008-12-30
> **poboy975 said:**
> yeah, I have gone through the setup there as well. I can now ping the linux laptop from the linux desktop. I can see the windows shares on the windows desktop from the linux desktop. I cannot see the windows share from the laptop. I can ping the linux and windows desktoips from the laptop. but no internet on either the linux desktop nor the windows desktop. only on laptop still. not sure what I'm doing wrong
Are you using a crossover cable between the two computers? Between any two computers you need a crossover cable, unless their is a router/hub, or switch in between them.

---

