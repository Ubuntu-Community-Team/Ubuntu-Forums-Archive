---
title: "Realtek RTL8111/8168B Problems"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by JoeGoldman on 2013-03-10
Hi Crew,

 There is plenty of threads about the Realtek RTL8111/8168B ethernet chipsets. I have read all that seem relevant, my issue seems to not have shown it's ugly head.

 Basically, I removed the r8169 driver and updated it with the r8168 driver as recommended, v8.035.00 to be exact (latest on realtek website).

 The connection is solid, comes up quick and doesn't die, which is the expected fix, but it still seems to be connecting itself at only 10mbps. Is there another fix to this? If I can't fix this easily I'm just gonna get a PCI gigabit adapter but I'd rather have a proper fix.

 lspci:
```

$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
02:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

ethtool:
```

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```


Using a Billion 7800N on the other end of a CAT6 cable. Exact same cable/port/router connects at gigabit speeds to my previous motherboard (new one today) running Ubuntu 12.04, to Mac OSX and Win 7.

Thanks for any help in advance!

---

### Post by varunendra on 2013-03-10
Were you having problems with the native r8169 driver ? It's been long since I heard of any.

As for the speed, what if you force a higher one, like 100Mb/s -
```
 sudo mii-tool -F 100baseTx-FD eth0
```
If successful, you may also try -
```
 sudo mii-tool -F 1000baseTx-FD eth0
```

---

### Post by JoeGoldman on 2013-03-10
> **varunendra said:**
> Were you having problems with the native r8169 driver ? It's been long since I heard of any.

As for the speed, what if you force a higher one, like 100Mb/s -
```
 sudo mii-tool -F 100baseTx-FD eth0
```
If successful, you may also try -
```
 sudo mii-tool -F 100baseTx-FD eth0
```

Hi varunendra,

 using 8169 on 12.04.2, it would take a long time to initiate the ethernet connection after boot, it would then start dropping out and was only at 10Mb/s.
 using 8168 on now 12.04.1 (had to go back due to other hardware compatibility), I installed r8168 straight away thinking i'd experience the same issues, but still it persists at 10baseT.

 Issuing the mii-tool command kills the interface until reboot (or possibly another command I could use? but don't know mii-tool that well).

 I think my best bet is to just look at work tomorrow for a gigabit adapter, or buy one for like $10-15 with a decent chipset. I won't mind playing a bit more to get this to work but I've exhausted my knowledge on the matter.

Thanks,
Joe

---

### Post by varunendra on 2013-03-10
> **JoeGoldman said:**
>  Issuing the mii-tool command kills the interface until reboot (or possibly another command I could use? but don't know mii-tool that well).

You can use -
```
sudo mii-tool -r eth0
```
..to restart autonegotiation. Take a look at **man mii-tool** to get details of its usage.

But if both drivers and even a changed kernel version are having same issue, then I'd assume the problem to be either external or hardware related. But obviously this is just a quick assumption without any research on the issue.

Maybe look in the BIOS for any related settings ?

---

### Post by JoeGoldman on 2013-03-10
G'day,

 Thanks for that. Still definitely having the issue.

 I believe its driver related. I might have to do a Win7 install on a spare HDD to triple confirm though.

 Cable and switch are 100% fine, used multiple other devices on them both with no issues at full gigabit.

 I'd be happy just to get 100mb/s back right now lol. Any other suggestions, please let me know and i'll try them :).

Thanks,
Joe

---

### Post by omgubunt1 on 2013-03-10
First i would recommend you to try a bios update for your motherboard. You never know.
I was having severe problems with my Ubuntu 10.04 server and this but since 12.04.2 64bit server update(fresh install) all smooth here so you might need a bios update.

---

