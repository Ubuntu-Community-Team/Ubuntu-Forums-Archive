---
title: "No internet connectivity NEED HELP ASAP PLEASE"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by KFwLsKvVAs on 2009-04-06
Hello all,

In the beginning I had ubuntu 8.10 installed on this HP DV2000 Entertainment PC laptop right...

Everything was gravy; internet worked for both wireless and ethernet, things were good.  Then it started acting strange, freezing up or randomly shutting off.  Took it in to a place, they diagnosed it as a bad hard drive.  So I got a new hard drive, reinstalled, and set to updating and whatnot.  

BUT when I plugged in the ethernet cable, it would not connect.  The little icon thing had two green circles, and it would seem like it was connecting, but then after a minute or so it would just say "network cable has been disconnected".  In addition, the network manager showed both up and down traffic when the ethernet cable was plugged in regardless of whether it was trying to connect to the network.  I worked on it for a good 4 or 5 hours trying different settings (and I'm not a linux genius so I don't know how much of that time was wasted changing irrelevant settings) but nothing seemed to work.  So now I'm posting from my other laptop, and I have no idea what is wrong with it or how to fix it.  My girlfriend needs the laptop for school so I need to get this fixed as soon as possible.  I will post all of the relevant results of the common commands that I know are useful (hopefully) and maybe somebody can help me out.  

results of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:d3:a4:2b:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59058 (59.0 KB)  TX bytes:2422 (2.4 KB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23760 (23.7 KB)  TX bytes:23760 (23.7 KB)


results of iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

results of lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by superprash2003 on 2009-04-06
type **sudo dhclient eth0 **in your terminal and post output

---

### Post by KFwLsKvVAs on 2009-04-07
Sorry for delay, computer kept freezing and so brought it back to be serviced.  Will post results when computer is returned.

---

