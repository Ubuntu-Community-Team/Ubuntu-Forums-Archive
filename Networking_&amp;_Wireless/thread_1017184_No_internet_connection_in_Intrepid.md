---
title: "No internet connection in Intrepid"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by thedonpsx on 2008-12-20
Hi everyone.
After around 20 mins of normal web useage (no p2p apps running etc), I loose all internet connection. I do not belive I loose the wireless connection (by that I mean the small graphic in the top of the dekstop still shows a connection). This is not a problem to do with my wireless router, as the same problem occurs when connecting to two different routers (both with different ISPs), as well as a large university wireless network. The problem can be resolved by restarting the system, although, this does not always work. I have turned off the one firewall I have running (Lokkit).
Below is the output of lspci. Please tell me if you require any more information. 
Many thanks, and merry Christmas to you all

---

### Post by thedonpsx on 2008-12-20
Sorry, here is said output.
The system I as using is a Toshiba Equium A210 - 17I, again many thanks


00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by albinootje on 2008-12-20
> **thedonpsx said:**
> 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


Is this about wifi or wired connection ?
What's the output of this :
```
lshw -C network
```
Do you use Ndiswrapper ?

---

### Post by thedonpsx on 2008-12-20
I believe so, but I am not quite sure (I am not the most of experienced ubuntu users i am afraid)
The output is:
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:8a:b8:5b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:16:44:70:07:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:0c:ec:26:0b:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by albinootje on 2008-12-20
Hmm, difficult :(
Perhaps you can try wicd as an alternative for network-manager.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by thedonpsx on 2008-12-20
I know it is very strange, also, the wireless has now stopped working in vista, which is very strange

---

