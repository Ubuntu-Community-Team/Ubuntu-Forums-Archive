---
title: "[SOLVED] WPA Security Troubles"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2009-01-04
Hello UF!

I had some trouble in the past with the wireless, so to eliminate confusion, I disabled the wireless security settings in my router.  

With your help, I got my wireless internet up and running on my Ubuntu laptop.  I have decided to re-enable the security settings on my router to protect my wireless network from wardrivers and crappy neighbors.  

Now, I am unable to connect to my (now) WPA2 wireless network.  I would like your help in troubleshooting my problem.    

My system:
Dell Inspiron 1721
AMD TL-60 @ 2.0 Ghz
2 GB DDR2 667
250 GB HDD
Dell 1505 Draft 802.11N wlan mini card
Broadcom BCM4328 10/100 network controller


PS - **PLEASE DO NOT** point me to several web pages for help.  I am a newbie, and still learning, so link after link, page after page of different codes and commands can be a little confusing and frustrating.

---

### Post by ToyotaGuy23 on 2009-01-04
A little more information:
[B]
My lspci says:[/B]
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

[B]
My iwconfig says:[/B]

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.

Except for the smileys.  I have no idea where they came from.

---

### Post by Noel96 on 2009-01-04
A couple of thoughts.

Have you tried using other password protocols. I remember reading somewhere that WEP often worked when WPA did not.

I'm assuming that you can still access your router through a wired line.

---

### Post by ToyotaGuy23 on 2009-01-04
That is correct, I can connect through a wired connection.

So far I have tried WPA and WPA2, both personal.
I will try WEP and report back.

---

### Post by ToyotaGuy23 on 2009-01-04
Apparently, my card won't get along with WPA or WPA2 personal in Ubuntu.

GOOD NEWS:  WEP works just fine.  

I am debating on MAC filtering, but I'm still on the fence.

Thank you so much!

---

