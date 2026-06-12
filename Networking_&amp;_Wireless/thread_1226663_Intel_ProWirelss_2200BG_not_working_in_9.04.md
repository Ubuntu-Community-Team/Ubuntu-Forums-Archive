---
title: "Intel Pro/Wirelss 2200BG not working in 9.04"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by mwsherman on 2009-07-29
Hi.

I'm attempting to get Ubuntu 9.04 to work on a Dell Latitude D610. This is the first time Ubuntu is being installed on this machine. Everything appears to be working great, except that I cannot get Ubuntu to properly load the wireless drivers, and it appears the hardware is Intel 2200 (I have no documentation to prove this, but see below).

Searches of the forums and the internet have gotten me nowhere, as a lot of the information seems contradictory. I've seen bug reports with this chipset that are 9.04 specific, so should I use an older version of Ubuntu? I considered using ndiswrapper, but cannot find the version of the drivers known to work per the ndiswapper wiki. I've also seen other users state that ndiswrapper should not be required for this chipset, as it should work with Ubuntu out of the box. 

The wireless was working on Windows on this machine, and if I can't get wireless in Ubuntu going on this machine I'll have to switch back :(.

Wired networking is working (I'm using it to post this!). Maybe the non-functional wireless is a symptom of a bigger problem? Are there any good diagnostics I can run to make sure everything is physically A-OK?

And, yes, I have tried Fn+F2 to turn the wireless on and off. Other Fn features appear to be working, but nothing happens when I do this wireless one.

I appreciate any help I can get. Sorry for the verbosity of the commands below, but I'd rather be safe than leave something important out.

sudo lspci -v
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec38 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: dfd00000-dfdfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: d3c00000-dfcfffff
	Capabilities: [50] Subsystem: Dell Device 0182

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ed00 [size=256]
	I/O ports at ec40 [size=64]
	Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
	Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Device 5423
	Flags: medium devsel, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at ec80 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Dell Device 0182
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Device 0182
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

03:01.0 Non-VGA unclassified device: Texas Instruments PCI6515 Cardbus Controller
	!!! Invalid class 0000 for header type 02
	Subsystem: Dell Device 0182
	Flags: bus master, medium devsel, latency 64
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	I/O window 0: 00000000-00000003 [disabled]
	I/O window 1: 00000000-00000003 [disabled]
	16-bit legacy interface ports at 0001

03:01.5 Display controller: Texas Instruments PCI6515 SmartCard Controller
	Subsystem: Dell Device 0182
	Flags: medium devsel, IRQ 5
	Memory at d3c00000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Memory at d3cfe000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [44] Power Management version 2

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2321
	Flags: medium devsel, IRQ 17
	Memory at dbcff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel modules: ipw2200


```

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```

sudo iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:13:07:12
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.29a ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 UNCLAIMED
       description: Network controller
       product: PCI6515 Cardbus Controller
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=176 maxlatency=3 mingnt=64
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:2e:54:60:2a:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Thank you, Ubuntu community, for reading this far :)

---

### Post by mwsherman on 2009-07-30
I've now tried 8.04 and 8.10 live CDs, and still did not get out of the box wireless support. I didn't dig too deeply into them, but neither had wireless network available through network manager.

I've thought about trying to use ndiswrapper, but isn't there something crazy that has to be done if the driver is already part of the kernel?

I've also noticed that the PCI6515 Cardbus Controller (which is listed in the lshw -C network command in the original post) causes this error at bootup:

```

[    0.586407] pci 0000:03:01.0: ignoring class 207 (doesn't match header type 02)

```

I have no idea if these issues are related or not, but this computer's user doesn't plan on using cards with the machine so it's not a big deal if it doesn't work.


Any help would be appreciated. I'm trying to introduce a new user to Ubuntu, and it would be very discouraging if we had to abandon this plan because of wireless...

Thanks for any help.

---

### Post by bhclardy on 2009-07-30
hey I had the same issue with my dell 700m. i had upgraded in 2 steps from 8.04 to 9.04. tried a fresh install for 9.04 with no luck.  reinstalled 8.04 (which had worked fine previously) and again no wireless.  so at that point i loaded up my windows xp partition to see if the wireless would work there and surprisingly it was not functional there either.

HOWEVER

I was able to reenable the wireless in windows, which fixed it in ubuntu 8.04. i assume there is a hardware switch that is soft ware enabled, that got gimped in the upgrade process.  I have since (as in about an hour ago) upgraded in 2 steps back to 9.04 and voila, flawless performance, and I couldn't be happier. 

I dont have the linux kungfu to figure that out from a command line, but if you have a windows partition on that drive you might try that manuever.


hope that helps. 

mods< possible lead and or bug fix here. 

thanks.

---

### Post by mwsherman on 2009-07-30
> **bhclardy said:**
> 

I was able to reenable the wireless in windows, which fixed it in ubuntu 8.04. i assume there is a hardware switch that is soft ware enabled, that got gimped in the upgrade process.  I have since (as in about an hour ago) upgraded in 2 steps back to 9.04 and voila, flawless performance, and I couldn't be happier. 



Wow. That is completely insane. Windows is currently not on the PC, and frankly, if I have to install Windows I'm probably going to give up on getting this machine working in Ubuntu. I've already spent quite a bit of time on it, and would be glad to just have it working. 

Does anyone have the command line "kung-fu" to tell me how I might check for something like this? Anyone have any other ideas before this computer becomes a windows PC?

Thanks for your response. I will at least run a live CD if I have to switch to Windows to see if your solution works. It is fascinating.

---

### Post by martinbaselier on 2009-07-30
Is this a clean normal ubuntu install? Not any unofficial variation of it?
The ipw2200 has been working out of the box for years now. I've got one myself and something is strange about your output.

The ipw2200 is normally attached to eth1 and not to pan0. If the hardware switch is turned off, it should still show the wireless capabilities of the card, it only shows radio off then.

---

### Post by mwsherman on 2009-07-30
> **martinbaselier said:**
> Is this a clean normal ubuntu install? Not any unofficial variation of it?
The ipw2200 has been working out of the box for years now. I've got one myself and something is strange about your output.


This is a clean Ubuntu 9.04 Install, right off the CD.

> **martinbaselier said:**
> 
The ipw2200 is normally attached to eth1 and not to pan0. If the hardware switch is turned off, it should still show the wireless capabilities of the card, it only shows radio off then.

So that means that the hardware switch is on? Is there anything that would make the wireless device give the strange information? Could it be old firmware? Could the hardware be borked? Is there any sort of diagnostic I can run on the card?

Thanks.

---

### Post by martinbaselier on 2009-07-30
Your dell laptop looks quite similar to my TM8100:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c8100000-c81fffff
	Prefetchable memory behind bridge: d0000000-d7ffffff
	Capabilities: [88] Subsystem: Acer Incorporated [ALI] Device 0070
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: oss_hdaudio
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0070
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0070
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0070
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at c8004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c8200000-c82fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c8120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at c8214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at c8200000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at c8215000 (32-bit, non-prefetchable) [size=2K]
	Memory at c8210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:09.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 18
	Memory at c8216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=08, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:09.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, slow devsel, latency 33, IRQ 10
	Memory at c8217000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=08, subordinate=08, sec-latency=36
	I/O window 1: 00000000-00000003
	16-bit legacy interface ports at 0001
	Kernel modules: yenta_socket

06:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: slow devsel, IRQ 11
	Memory at c8218000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

06:09.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: stepping, slow devsel
	Memory at c8219000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Bus: primary=00, secondary=00, subordinate=00, sec-latency=0
	I/O window 0: 00000000-00000003 [disabled]
	I/O window 1: 00000000-00000003 [disabled]
	16-bit legacy interface ports at 0001
	Kernel modules: yenta_socket


```
The only mayor difference I can spot is the intel graphics card. I've read some issues with it and wireless cards. If you check the multimedia & video forum, there's a sticky thread about intel graphics. You might take a look at that. 

I can't really think of any of the available diagnostic tools, which might help you at this moment.
dmesg | grep ipw2200
might show something. 

Here's my output for reference:
```

[   38.258112] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   38.258116] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   38.258348] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   38.259111] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   38.259161] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[   38.461230] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)

```

---

### Post by mwsherman on 2009-07-30
> **martinbaselier said:**
> 
dmesg | grep ipw2200
might show something. 


Indeed it does:

```

[   10.047972] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.047976] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   10.049630] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.051509] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.051550] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   10.192791] ipw2200: Unable to load ucode: -22
[   10.192804] ipw2200: Unable to load firmware: -22
[   10.192807] ipw2200: failed to register network device
[   10.201669] ipw2200 0000:03:03.0: PCI INT A disabled
[   10.201685] ipw2200: probe of 0000:03:03.0 failed with error -5

```

I have no idea exactly what this means, but it's clearly not happy.

I also looked in the multimedia area, and looked around that sticky thread about wireless. The problems with Intel integrated graphics and wireless are related to updates a user can make to improve the performance of their intel integrated graphics. And the wireless problems seem to be related to an upgrade to a future kernel version.

Can anything be discerned from the messages above?

Thank you for your help. It is very much appreciated.

---

### Post by martinbaselier on 2009-07-30
Your firmware isn't loaded. Now you know the cause of the problem. :) Isn't that nice. 

I guess 
ls /lib/firmware/ipw2200-bss.fw
will show nothing

sudo apt-get install linux-firmware
will solve that. 

how did I find out?

dpkg -S ipw2200-bss.fw
linux-firmware: /lib/firmware/ipw2200-bss.fw

---

### Post by mwsherman on 2009-07-31
> **martinbaselier said:**
> 

I guess 
ls /lib/firmware/ipw2200-bss.fw
will show nothing


The plot thickens. No idea what's going on now. This is what I get, and there is certainly already firmware there...

```

xxxxxxx@xxxxlaptop:/lib/firmware$ ls ipw*
ipw2100-1.3.fw    ipw2100-1.3-p.fw  ipw2200-ibss.fw
ipw2100-1.3-i.fw  ipw2200-bss.fw    ipw2200-sniffer.fw

```

Just to see what would happen, I tried to install the package. It was already installed, but I don't know if these other messages are of some relevance:

```

xxxxxxx@xxxxlaptop:/lib/firmware$ sudo apt-get install linux-firmware
[sudo] password for xxxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Should I try apt-get autoremove? I have no idea what to try other than that.

I greatly appreciate the help. Thank you so much!

---

### Post by martinbaselier on 2009-07-31
You could trie a reinstall
sudo apt-get install linux-firmware --reinstall

The kernel headers are needed for compiling things related to the kernel. So you could remove them, but that won't make much difference for the issue. 

I can't tell why the firmware won't load. I searched a bit with google, but I could not really find much more information about it.

---

### Post by Cuba71 on 2009-07-31
Have you tried loading the Windows driver for that device?
It's a simple operation provided you have/can find the driver files (.inf and .sys)
Let me know if you want to know how

---

### Post by mwsherman on 2009-08-03
> **Cuba71 said:**
> Have you tried loading the Windows driver for that device?
It's a simple operation provided you have/can find the driver files (.inf and .sys)
Let me know if you want to know how

Seeing as this device works natively with Linux, and also seeing that it appears the problem is not with the driver, but at a lower level (firmware), I don't see how this could possibly help. Furthermore, the versions of the driver known to work with ndiswrapper don't seem to be provided by Intel anymore--once native support for this chipset appeared, it seems the ndiswrapper crowd stopped bothering playing with it.

If I was to use .inf and .sys files with ndiswrapper, what versions of windows can they come from. 2000? XP? Vista?


> **martinbaselier said:**
> You could trie a reinstall
sudo apt-get install linux-firmware --reinstall

I can't tell why the firmware won't load. I searched a bit with google, but I could not really find much more information about it.

I tried reinstalling the firmware and it did nothing. However, at one point, on some random restart, the wireless appeared to be half working. Since, then I have not been able to reproduce this behavior. Here's what happened:

I booted up (on a restart) with the ethernet cable unplugged. For some reasons, the cardbus error I talked about earlier did not appear!

> **mwsherman said:**
> 

I've also noticed that the PCI6515 Cardbus Controller (which is listed in the lshw -C network command in the original post) causes this error at bootup:

```

[    0.586407] pci 0000:03:01.0: ignoring class 207 (doesn't match header type 02)

```

Once I was in Ubuntu, I was able to attempt to connect to a wireless network with network manager--normally wireless is not an option through network manager on this machine. I was, however, unable to sucessfully connect to a wireless network for reasons I could not determine. I fired up the console and tried lshw -C network, and the machine hung.

I'm guessing this Texas Instruments PCI cardbus has something to do with the problems, and it is possible the wireless dysfunctionality is a symptom of an underlying problem with the cardbus. See some of my older posts for lshw information about the cardbus.

Any ideas of things to try now? I'm trying to reproduce the situation where the wireless half worked, but have failed. If I can do it again, I'll post as much system info as I can here.

Searching for the error "ipw2200: Unable to load ucode: -22" give some interesting google results, but I'm not sure if they're relevant so I'll refrain from posting them here.

Thanks for everyone for their help and suggestions!

---

### Post by mwsherman on 2009-08-04
I've spent a few hours trying to recreate the one time the computer recogized the wireless device. I have failed.

Does anyone have any ideas at all about how to get the wireless working? I'm out of ideas, and this is about to become a windows machine, sadly.

Thanks.

---

### Post by lswb on 2009-08-04
I've had good results with the ipw2200 I installed in my laptop with 8.04, 8.10, and 9.04 (In 8.10 it was one of the few things I could count on working :) ) As a matter of fact, it is a ipw2200 originally sold by Dell, though my laptop is a Gateway.

It looks like there may be some kind of hardware problem either with the adapter itself or with something else that is keeping the driver from loading. BTW, the pan0 interface is not related to wifi, it is created by the bluetooth service.

Try verifying that the driver is loaded, " lsmod|grep ipw" on my system returns
```

$ lsmod|grep ipw
ipw2200               143128  0 
libipw                 29616  1 ipw2200
lib80211                6448  3 lib80211_crypt_wep,ipw2200,libipw

```


You might try opening up the cover where the adapter installs and make sure it is seated properly.

---

### Post by mwsherman on 2009-08-05
> **lswb said:**
> 
It looks like there may be some kind of hardware problem either with the adapter itself or with something else that is keeping the driver from loading. BTW, the pan0 interface is not related to wifi, it is created by the bluetooth service.

Try verifying that the driver is loaded, " lsmod|grep ipw" on my system returns
```

$ lsmod|grep ipw
ipw2200               143128  0 
libipw                 29616  1 ipw2200
lib80211                6448  3 lib80211_crypt_wep,ipw2200,libipw

```


You might try opening up the cover where the adapter installs and make sure it is seated properly.

Here's what I got from lsmod:
```

xxxxxx@xxxxx-laptop:~$ sudo lsmod|grep ipw
ipw2200               151112  0 
ieee80211              38344  1 ipw220

```

I have no idea what this means...

I got as far into the laptop as I could trying to find the physical adapter to play with it, but I couldn't find anything. It might be integrated into the motherboard?

Also, the user stated they had no wireless specific problems with windows, so I'm assuming the hardware is OK. However, are there are any good hardware diagnostics I can run (either in Ubuntu or on a bootable CD) that could help me eliminate physical issues with the hardware as causing the problems? Unfortunately, the bios on this machine lacks diagnostics.

Thanks for your response. I hope the lsmod output is useful...

---

### Post by lswb on 2009-08-05
Looking for an answer to your problem I couldn't find anything definitive but I did see a few posts that claimed unloading and reloading the ipw2200 module helped their D610. Why this is so I have no ide, but if you want to try it,

sudo modprobe -r ipw2000
(wait a few seconds, then)
sudo modprobe ipw2200

It might be helpful to first open a separate terminal and run "tail -F /var/log/syslog" to watch for any log messages while trying.

---

### Post by mwsherman on 2009-08-10
> **lswb said:**
> Looking for an answer to your problem I couldn't find anything definitive but I did see a few posts that claimed unloading and reloading the ipw2200 module helped their D610. 

Thanks for the tip. Sorry it's been so long to respond, I've been away from the machine.

Unloading and reloading the module did not work, wireless is still not available in network manager, and modprobe did not return any error messages. Here's what was in the tail -F syslog terminal. The first line is from unloading the module, the rest is from attempting to reload it:

```

Aug 10 01:12:37 xxxxxxx-laptop kernel: [ 1513.074638] ieee80211_crypt: unregistered algorithm 'NULL'
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.020293] ieee80211_crypt: registered algorithm 'NULL'
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.030621] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.030628] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.048460] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.048467] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.048574] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.049782] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.049860] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.099624] ipw2200: Unable to load ucode: -22
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.099647] ipw2200: Unable to load firmware: -22
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.099653] ipw2200: failed to register network device
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.105398] ipw2200 0000:03:03.0: PCI INT A disabled
Aug 10 01:12:45 xxxxxxx-laptop kernel: [ 1521.105426] ipw2200: probe of 0000:03:03.0 failed with error -5

```

Does this shed any light on what might be happening? Some of the output in here looks familiar from other sniffing, see some of my older posts.

Thanks for reading. I appreciate everyone's time.

---

### Post by mwsherman on 2009-08-10
After examing and googling some more, I think the problem might stem not from the wireless adapter, but from the cardbus controller. The Cardbus controller in the D610 as listed in lshw:

```

  *-network:0 UNCLAIMED
       description: Network controller
       product: PCI6515 Cardbus Controller
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=176 maxlatency=3 mingnt=64

```

Why do I think this is the culprit instead of the actual network card? Because this error appears at startup:

```

[    0.586407] pci 0000:03:01.0: ignoring class 207 (doesn't match header type 02)

```

Is there anything I can do about this? I'm way beyond my knowledge here, so I might be barking to an entirely weird place. Is there a better forum to post on for help if I want to try to work out the problems with this controller?

Thanks.

---

### Post by astrader on 2009-09-09
I have a Dell Latitude D610 also with what I suspect is the same 2195 / 2200 wireless card.  I got my wireless working in 9.04 by setting the wireless card to be "On" on bootup in BIOS.  I am not technically knowledgeable about any of the other things posted, so sorry if this was already ruled out somewhere.  Just thought I'd share for you and any other people looking at this post (like I was yesterday).

---

