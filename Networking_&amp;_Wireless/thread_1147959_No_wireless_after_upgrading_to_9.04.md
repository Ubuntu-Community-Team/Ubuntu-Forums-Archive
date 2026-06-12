---
title: "No wireless after upgrading to 9.04"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by ali999 on 2009-05-03
Hi

I just recently used the online update process to get the new ubuntu 9.04. Everything seems to be working fine except for the fact that I have no wireless. After running sudo lshw -C network, i noticed that my wireless is unclaimed. The help option tells me to install ndisgtk however this is rather impossible with no internet. It is pretty difficult for me to run a wire up to this comp. Any suggestions please?

Thanks in advance.

---

### Post by RedSingularity on 2009-05-03
What is your "lspci" output?

---

### Post by ali999 on 2009-05-03
below are the outputs for the lspci and lshw.

lspci:
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, fast devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: intel-agp 

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 	I/O behind bridge: 0000d000-0000dfff 	Memory behind bridge: f8000000-fbffffff 	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff 	Capabilities: <access denied> 	Kernel driver in use: pcieport-driver 	Kernel modules: shpchp 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Defini00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, fast devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: intel-agp  
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 	I/O behind bridge: 0000d000-0000dfff 	Memory behind bridge: f8000000-fbffffff 	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff 	Capabilities: <access denied> 	Kernel driver in use: pcieport-driver 	Kernel modules: shpchp  
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 2624 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K] 	Capabilities: <access denied> 	Kernel driver in use: HDA Intel 	Kernel modules: snd-hda-intel  
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	I/O ports at ff00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 19 	I/O ports at fe00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at fd00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 16 	I/O ports at fc00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K] 	Capabilities: <access denied> 	Kernel driver in use: ehci_hcd 	Kernel modules: ehci-hcd  
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32 	I/O behind bridge: 0000e000-0000efff 	Memory behind bridge: fde00000-fdefffff 	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff 	Capabilities: <access denied>  
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: iTCO_wdt, intel-rng  
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at 01f0 [size=8] 	I/O ports at 03f4 [size=1] 	I/O ports at 0170 [size=8] 	I/O ports at 0374 [size=1] 	I/O ports at fb00 [size=16] 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 	I/O ports at fa00 [size=8] 	I/O ports at f900 [size=4] 	I/O ports at f800 [size=8] 	I/O ports at f700 [size=4] 	I/O ports at f600 [size=16] 	Capabilities: <access denied> 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: medium devsel, IRQ 15 	I/O ports at 0500 [size=32] 	Kernel modules: i2c-i801  
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1) 	Subsystem: ASUSTeK Computer Inc. Device 827a 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fa000000 (32-bit, non-prefetchable) [size=16M] 	Memory at d0000000 (64-bit, prefetchable) [size=256M] 	Memory at f8000000 (64-bit, non-prefetchable) [size=32M] 	I/O ports at df00 [size=128] 	[virtual] Expansion ROM at fb000000 [disabled] [size=512K] 	Capabilities: <access denied> 	Kernel driver in use: nvidia 	Kernel modules: nvidia, nvidiafb  
02:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 	Subsystem: D-Link System Inc Device 3a16 	Flags: bus master, medium devsel, latency 32, IRQ 15 	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K] 	Capabilities: <access denied> 	Kernel modules: ath_pci  
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 	Subsystem: Elitegroup Computer Systems Device 8139 	Flags: bus master, medium devsel, latency 32, IRQ 20 	I/O ports at ee00 [size=256] 	Memory at fdeff000 (32-bit, non-prefetchable) [size=256] 	Capabilities: <access denied> 	Kernel driver in use: 8139too 	Kernel modules: 8139too, 8139cp tion Audio Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 2624 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K] 	Capabilities: <access denied> 	Kernel driver in use: HDA Intel 	Kernel modules: snd-hda-intel  
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	I/O ports at ff00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 19 	I/O ports at fe00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at fd00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 16 	I/O ports at fc00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K] 	Capabilities: <access denied> 	Kernel driver in use: ehci_hcd 	Kernel modules: ehci-hcd  
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32 	I/O behind bridge: 0000e000-0000efff 	Memory behind bridge: fde00000-fdefffff 	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff 	Capabilities: <access denied>  
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: iTCO_wdt, intel-rng  
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at 01f0 [size=8] 	I/O ports at 03f4 [size=1] 	I/O ports at 0170 [size=8] 	I/O ports at 0374 [size=1] 	I/O ports at fb00 [size=16] 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 	I/O ports at fa00 [size=8] 	I/O ports at f900 [size=4] 	I/O ports at f800 [size=8] 	I/O ports at f700 [size=4] 	I/O ports at f600 [size=16] 	Capabilities: <access denied> 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: medium devsel, IRQ 15 	I/O ports at 0500 [size=32] 	Kernel modules: i2c-i801  
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1) 	Subsystem: ASUSTeK Computer Inc. Device 827a 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fa000000 (32-bit, non-prefetchable) [size=16M] 	Memory at d0000000 (64-bit, prefetchable) [size=256M] 	Memory at f8000000 (64-bit, non-prefetchable) [size=32M] 	I/O ports at df00 [size=128] 	[virtual] Expansion ROM at fb000000 [disabled] [size=512K] 	Capabilities: <access denied> 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, fast devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: intel-agp  
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 	I/O behind bridge: 0000d000-0000dfff 	Memory behind bridge: f8000000-fbffffff 	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff 	Capabilities: <access denied> 	Kernel driver in use: pcieport-driver 	Kernel modules: shpchp 
 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 2624 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K] 	Capabilities: <access denied> 	Kernel driver in use: HDA Intel 	Kernel modules: snd-hda-intel  
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	I/O ports at ff00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 19 	I/O ports at fe00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at fd00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 16 	I/O ports at fc00 [size=32] 	Kernel driver in use: uhci_hcd 	Kernel modules: uhci-hcd  
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 23 	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K] 	Capabilities: <access denied> 	Kernel driver in use: ehci_hcd 	Kernel modules: ehci-hcd  
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01) 	Flags: bus master, fast devsel, latency 0 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32 	I/O behind bridge: 0000e000-0000efff 	Memory behind bridge: fde00000-fdefffff 	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff 	Capabilities: <access denied>  
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0 	Capabilities: <access denied> 	Kernel modules: iTCO_wdt, intel-rng  
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, medium devsel, latency 0, IRQ 18 	I/O ports at 01f0 [size=8] 	I/O ports at 03f4 [size=1] 	I/O ports at 0170 [size=8] 	I/O ports at 0374 [size=1] 	I/O ports at fb00 [size=16] 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO]) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 	I/O ports at fa00 [size=8] 	I/O ports at f900 [size=4] 	I/O ports at f800 [size=8] 	I/O ports at f700 [size=4] 	I/O ports at f600 [size=16] 	Capabilities: <access denied> 	Kernel driver in use: ata_piix 	Kernel modules: ata_piix, ata_generic, pata_acpi  
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 	Subsystem: Elitegroup Computer Systems Device 1b76 	Flags: medium devsel, IRQ 15 	I/O ports at 0500 [size=32] 	Kernel modules: i2c-i801  
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1) 	Subsystem: ASUSTeK Computer Inc. Device 827a 	Flags: bus master, fast devsel, latency 0, IRQ 16 	Memory at fa000000 (32-bit, non-prefetchable) [size=16M] 	Memory at d0000000 (64-bit, prefetchable) [size=256M] 	Memory at f8000000 (64-bit, non-prefetchable) [size=32M] 	I/O ports at df00 [size=128] 	[virtual] Expansion ROM at fb000000 [disabled] [size=512K] 	Capabilities: <access denied> 	Kernel driver in use: nvidia 	Kernel modules: nvidia, nvidiafb  
02:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 	Subsystem: D-Link System Inc Device 3a16 	Flags: bus master, medium devsel, latency 32, IRQ 15 	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K] 	Capabilities: <access denied> 	Kernel modules: ath_pci  
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 	Subsystem: Elitegroup Computer Systems Device 8139 	Flags: bus master, medium devsel, latency 32, IRQ 20 	I/O ports at ee00 [size=256] 	Memory at fdeff000 (32-bit, non-prefetchable) [size=256] 	Capabilities: <access denied> 	Kernel driver in use: 8139too 	Kernel modules: 8139too, 8139cp 	Kernel driver in use: nvidia 	Kernel modules: nvidia, nvidiafb  
02:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 	Subsystem: D-Link System Inc Device 3a16 	Flags: bus master, medium devsel, latency 32, IRQ 15 	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K] 	Capabilities: <access denied> 	Kernel modules: ath_pci  
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 	Subsystem: Elitegroup Computer Systems Device 8139 	Flags: bus master, medium devsel, latency 32, IRQ 20 	I/O ports at ee00 [size=256] 	Memory at fdeff000 (32-bit, non-prefetchable) [size=256] 	Capabilities: <access denied> 	Kernel driver in use: 8139too 	Kernel modules: 8139too, 8139cp 


lshw: 
> *-network:0 UNCLAIMED           description: Ethernet controller        product: AR2413 802.11bg NIC        vendor: Atheros Communications Inc.        physical id: 2        bus info: pci@0000:02:02.0        version: 01        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list        configuration: latency=32 maxlatency=28 mingnt=10 
  *-network:1        description: Ethernet interface        product: RTL-8139/8139C/8139C+        vendor: Realtek Semiconductor Co., Ltd.        physical id: 5        bus info: pci@0000:02:05.0        logical name: eth0        version: 10        serial: 00:1b:b9:7f:f5:98        size: 10MB/s        capacity: 100MB/s        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
  *-network DISABLED        description: Ethernet interface        physical id: 1        logical name: pan0        serial: 2e:bd:18:fe:42:31        capabilities: ethernet physical        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 


sorry for the formatting being really bad...i had to copy the output into office and then reboot to windows so i could post it online.

---

### Post by ali999 on 2009-05-04
so anybody willing to help me here? its for stupid reasons like this that linux can never replace windows.

---

### Post by RedSingularity on 2009-05-04
Ok, have you gone to System>Admin>hardware drivers to see if it is activated?

---

### Post by Joren on 2009-05-04
Have you installed the wireless with Ndiswrapper? In that case you're ndiswrapper is probable downgraded from 1.54 to 1.53. That happened to me after each regular upgrade with 8.10.

type:
```
ndiswrapper -v
```

see if it is 1.54. I freshly installed 9.04 and I got wireless with a very low signal and connection dropping all the time and slow internet. The I blacklisted the drivers and installed the windows driver with ndiswrapper via the terminal. Works the best!

goodluck

---

### Post by ali999 on 2009-05-04
can't install ndiswrapper because i need internet for that, and i don't have a wired connection running up here. if nothing works i just might have to go back to 8.10.

---

### Post by ali999 on 2009-05-04
well....now i feel like a complete dumbass, turns out it was just not activated as shadow suggested. seems like this would be the first thing i'd check but the update process did so well with everything else, never suspected the wireless would just be disabled.

---

