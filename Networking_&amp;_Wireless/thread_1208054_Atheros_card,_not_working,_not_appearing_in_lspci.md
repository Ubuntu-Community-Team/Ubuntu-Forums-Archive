---
title: "Atheros card, not working, not appearing in lspci"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by calsaverini on 2009-07-08
I don't understand this very much, but I think my card wasn't even detected by the instalation. 

I'm using Ubuntu 9.04 64 bits. 
```

calsaverini@mnemosyne:~$ uname -a
Linux mnemosyne 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

```

I just finish a fresh install 30 minutes ago, and did nothing except for an update and tried to install madwifi when I saw my wireless wasn't working. I know my card is an Atheros 5007, which gave me some trouble to install in previous versions but was working ok on Debian Lenny.

When I try to check on my pci devices I can't find any wireless cards:
```

calsaverini@mnemosyne:~$ **lspci**
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
07:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
07:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
07:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
07:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

When I try iwconfig:
```

calsaverini@mnemosyne:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

No ath0 or wifi0 interfaces appear. On Debian Lenny I had a ath0 interface that was automatically detected on install. 

Another command someone told me to post here as well:
```

calsaverini@mnemosyne:~$ **sudo lshw -C Network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:07:07.0
       logical name: eth0
       version: 10
       serial: 00:1b:fc:05:3d:f5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.104 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:53:6b:c8:cc:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
calsaverini@mnemosyne:~$ 

```
Anyone knows what happened?

When I was installing Ubuntu I connected the ethernet cable on my wired ethernet card. Will this preclude him from searching for a wifi interface? I hope not.:icon_frown:

---

### Post by enzo_b_w on 2009-08-09
I have a D-Link WDA-1320 card (Atheros chipset) with the exact same problems.  I too can't find the card with lspci, etc.  Any ideas?  
I am running jaunty jackalope on an AMD 64 bit cpu.  Could the 64 bit be the problem?

---

