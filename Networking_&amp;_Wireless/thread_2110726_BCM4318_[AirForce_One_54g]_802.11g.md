---
title: "BCM4318 [AirForce One 54g] 802.11g"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by bajones27 on 2013-01-31
I just installed ubuntu on my laptop, I was previously running windows, but my wireless connection is not working. I can't even turn it on anymore. The button is always dimmed and pressing it does nothing. Any help on getting it working again would be appreciated.

---

### Post by ahallubuntu on 2013-01-31
What version of Ubuntu?

What make/model laptop?

Open a terminal and type:

sudo lshw -C network
lspci
uname -r
iwconfig

---

### Post by bajones27 on 2013-01-31
Thanks for the quick reply!

**12.04 LTS**



hp pavillion zv6000


bradley@MonsterAttack:~$ sudo lshw -C network
[sudo] password for bradley: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=wl latency=64
       resources: irq:9 memory:b0204000-b0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:70:ee:65
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:b020a400-b020a4ff
bradley@MonsterAttack:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bradley@MonsterAttack:~$ uname -r
3.2.0-36-generic-pae
bradley@MonsterAttack:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bradley@MonsterAttack:~$

---

### Post by Bucky Ball on 2013-01-31
Can you update with a cable and check Additional Drivers? If nothing there, you might try installing:

b43-fwcutter
firmware-b43-installer

... from Software Centre and restarting.

This is your card:

BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

You have a driver installed already but possibly wrong one.

---

### Post by bajones27 on 2013-01-31
I installed 

b43-fwcutter
firmware-b43-installer

and restarted

but it didn't help. The button to start the modem is still inactive.

---

### Post by Bucky Ball on 2013-01-31
> **bajones27 said:**
>  The button to start the modem is still inactive.

The modem? You mean wireless card in the computer?

---

### Post by bajones27 on 2013-02-01
ya. the wireless card remains inactive.

---

