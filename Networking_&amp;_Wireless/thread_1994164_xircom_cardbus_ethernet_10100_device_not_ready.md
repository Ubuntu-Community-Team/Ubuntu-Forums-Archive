---
title: "xircom cardbus ethernet 10/100 device not ready"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by nb42 on 2012-06-02
So I just set up lubuntu on an old old Dell Latitude CSx. It has a built in modem/network card of some sort, and I have an Ethernet adapter for it that is connected to an Ethernet cable. Clicking the network icon in the toolbar, it shows "Wired Network Device Not Ready". What could be causing this? How can I get it to connect?


running ifconfig in the terminal...
NB@latcsx:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:a4:a7:70:84  
          inet6 addr: fe80::210:a4ff:fea7:7084/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1515 errors:0 dropped:1392 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103943 (103.9 KB)  TX bytes:348 (348.0 B)
          Interrupt:11 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31840 (31.8 KB)  TX bytes:31840 (31.8 KB)

And these are the PCI devices (from System Information)
-PCI Devices-
Host bridge		: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
PCI bridge		: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
CardBus bridge		: Texas Instruments PCI1225 (rev 01)
CardBus bridge		: Texas Instruments PCI1225 (rev 01)
Bridge		: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
IDE interface		: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
USB controller		: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
Bridge		: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
VGA compatible controller		: Neomagic Corporation NM2360 [MagicMedia 256ZX] (prog-if 00 [VGA controller])
Multimedia audio controller		: Neomagic Corporation NM2360 [MagicMedia 256ZX Audio]
Ethernet controller		: Xircom Cardbus Ethernet 10/100 (rev 03)
Serial controller		: Xircom Cardbus Ethernet + 56k Modem (rev 03) (prog-if 02 [16550])

---

