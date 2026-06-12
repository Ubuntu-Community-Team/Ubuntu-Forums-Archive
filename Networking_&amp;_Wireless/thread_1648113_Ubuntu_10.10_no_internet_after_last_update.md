---
title: "Ubuntu 10.10 no internet after last update"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by kelesh on 2010-12-18
Hi,
This is my first post here, and i hope to find solution to my problem. I did all the thing i found on internet about it, but it is still there.

So, i have windows 7 and ubuntu on same machine, it's Acer aspire 7736. First it was just the 7, then i installed ubuntu 10.10 beta, then updated a month before this moment and never use it sins yesterday. Everything was working fine, i just cant get the sound to work, but this is another thing.
When i ran the Ubuntu yesterday the updates was unable to install, Firefox is not working(waiting for google.com, for example), [COLOR=DarkSlateGray]but[/COLOR] i can log in to skype with no problem at all, the torrents are working great...
I will post all the info i have for the moment and see what you can propose.

[HTML]

timmon@timmon-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:26:2d:89:a6:f1  
          
inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          
inet6 addr: fe80::226:2dff:fe89:a6f1/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          
RX packets:279 errors:399 dropped:0 overruns:0 frame:399
          
TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:50658 (50.6 KB)  TX bytes:72099 (72.0 KB)
          
Interrupt:16 

lo        Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

timmon@timmon-laptop:~$ sudo lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, fast devsel, latency 0
    
Capabilities: [e0] Vendor Specific Information: Len=0a <?>
    
Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    
I/O behind bridge: 00002000-00002fff
    
Memory behind bridge: f4000000-f40fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    
Capabilities: [88] Subsystem: Acer Incorporated [ALI] Device 0296
    
Capabilities: [80] Power Management version 3
    
Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    
Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    
Capabilities: [140] Root Complex Link
    
Kernel driver in use: pcieport
    
Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1800 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1820 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at f4504800 (32-bit, non-prefetchable) [size=1K]
    
Capabilities: [50] Power Management version 2
    
Capabilities: [58] Debug port: BAR=1 offset=00a0
    
Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, fast devsel, latency 0, IRQ 45
    
Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
    
Capabilities: [50] Power Management version 2
    
Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    
Capabilities: [100] Virtual Channel
    
Capabilities: [130] Root Complex Link
    
Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    
Flags: bus master, fast devsel, latency 0
    
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    
I/O behind bridge: 00004000-00004fff
    
Memory behind bridge: f4100000-f41fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    
Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    
Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0296
    
Capabilities: [a0] Power Management version 2
    
Capabilities: [100] Virtual Channel
    
Capabilities: [180] Root Complex Link
    
Kernel driver in use: pcieport
    
Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    
I/O behind bridge: 00005000-00005fff
    
Memory behind bridge: f4200000-f42fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    
Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    
Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0296
    
Capabilities: [a0] Power Management version 2
    
Capabilities: [100] Virtual Channel
    
Capabilities: [180] Root Complex Link
    
Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    
Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    
Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    
Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0296
    
Capabilities: [a0] Power Management version 2
    
Capabilities: [100] Virtual Channel
    
Capabilities: [180] Root Complex Link
    
Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 0296
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1840 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1860 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1880 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    
Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f4504c00 (32-bit, non-prefetchable) [size=1K]
    
Capabilities: [50] Power Management version 2
    
Capabilities: [58] Debug port: BAR=1 offset=00a0
    
Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    
Flags: bus master, fast devsel, latency 0
    
Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    
Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0296

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, medium devsel, latency 0
    
Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    
Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 0296
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 18f0 [size=8]
    I/O ports at 18e4 [size=4]
    
I/O ports at 18e8 [size=8]
    
I/O ports at 18e0 [size=4]
    
I/O ports at 18c0 [size=32]
    
Memory at f4504000 (32-bit, non-prefetchable) [size=2K]
    
Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
    
Capabilities: [70] Power Management version 3
    
Capabilities: [a8] SATA HBA v1.0
    
Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    
Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: medium devsel, IRQ 10
    Memory at c0400000 (64-bit, non-prefetchable) [size=256]
    
I/O ports at 1c00 [size=32]
    
Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650] (prog-if 00 [VGA controller])
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, fast devsel, latency 0, IRQ 46
    
Memory at d0000000 (32-bit, prefetchable) [size=256M]
    
I/O ports at 2000 [size=256]
    
Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
    
[virtual] Expansion ROM at f4020000 [disabled] [size=128K]
    
Capabilities: [50] Power Management version 3
    
Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    
Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    
Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
    
Subsystem: Acer Incorporated [ALI] Device 0296
    
Flags: bus master, fast devsel, latency 0, IRQ 47
    
Memory at f4010000 (32-bit, non-prefetchable) [size=16K]
    
Capabilities: [50] Power Management version 3
    
Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    
Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    
Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
    
Subsystem: Acer Incorporated [ALI] Device 0207
    
Flags: bus master, fast devsel, latency 0, IRQ 48
    
Memory at f4100000 (64-bit, non-prefetchable) [size=64K]
    
Capabilities: [48] Power Management version 3
    
Capabilities: [40] Vital Product Data
    
Capabilities: [60] Vendor Specific Information: Len=6c <?>
    
Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    
Capabilities: [cc] Express Endpoint, MSI 00
    
Capabilities: [100] Advanced Error Reporting
    
Capabilities: [13c] Virtual Channel
    
Capabilities: [160] Device Serial Number 00-26-2d-ff-fe-89-a6-f1
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: tg3
    Kernel modules: tg3

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e01f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    
Memory at f4200000 (64-bit, non-prefetchable) [size=64K]
    
Capabilities: [40] Power Management version 2
    
Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    
Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    
Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    
Kernel driver in use: ath9k
    
Kernel modules: ath9k



timmon@timmon-laptop:~$[/HTML]Somebody said that this info is needed. 
Sorry for the mess, but it was in one line when i opened it in windows, so i added enter where i think it have to be new line.

[[IMG]http://img585.imageshack.us/img585/7184/capturefe.jpg[/IMG]]("http://img585.imageshack.us/i/capturefe.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is from windows 7 local internet connections.

On default, before i do anything on the network in ubuntu it was Automatic DHCP.

I have router, but i never had to do any manual adjustments on windows or ubuntu before. They just found my internet connection and everything worked great.

I use cable internet.


I could use some help from you, because so far i was unable to find any solution for this internet thing. I want to update ubuntu and start using it more often, as my primary OS...

Thanks in advance!

(Sorry for my english!)

---

### Post by VietCanada on 2010-12-18
I had a problem with my connection through 10.10 despite my windows 7 working. I opened a CLI in Windows, entered ipconfig. I found that my Ubuntu connection was different in all the details. I corrected it to match the ipconfig details and was online.

I mention this because I'm curious as to why your ip address is 192.168.1.7
the last number as 1 connects you to your router I think but I would expect your ip add to end with 2 not 7.

So compare your windows 7 connection to your Ubuntu connection. 

BTW It looks like your first info says your ip address ends in a 3 but the second info you post it ends in a 7.

---

### Post by kelesh on 2010-12-18
I will try it first thing in the morning.

Thanks for the reply!

By the way, there is 3 laptops using the same router, so i guess that windows must use different 192.168.1.* addresses... But i will try to get the same settings from my windows to my ubuntu.

---

### Post by kelesh on 2010-12-20
OK!
So, i entered the same settings from Windows to Ubuntu and still no internet. I tried with Automatic and Manual, i tried adding different settings, everything with no luck.

And screenshots...
The second is from Windows.

Please help me, i really like to use it as i use my win, even more...

---

### Post by kelesh on 2010-12-20
The interesting thing is that my Skype is working, but i cant browse the web and update manager is not working.... What may be the problem?

---

### Post by grahammechanical on 2010-12-20
I note from your ifconfig listing that eth0 is UP and RUNNING. This is good. It tells me that you have a connection to the router. Have you tried setting the Method under the IPv6 Settings tab to Ignore? Can you run nm-tool and check that you have the same Gateway and DNS addresses as in Windows?

As for sound if you go to Sound Preferences make sure that sound has not been set to Mute. It has happened to me after an update. Although this has not happened recently.

Regards.

---

### Post by kelesh on 2010-12-20
Ip6 is set to Ignore. I was thinking to add the information from windows for it and see what will happen.

As for the nm-tool, is this what i have to write in terminal, just "sudo nm-tool"?

---

