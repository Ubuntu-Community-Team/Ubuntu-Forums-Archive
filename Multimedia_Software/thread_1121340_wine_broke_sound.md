---
title: "wine broke sound"
date: 2009-04-09
forum: Multimedia Software
---

### Post by Ketara on 2009-04-09
I'm not really sure what info I should give for this, since I'm not really understanding how this could happen. I'm running Intrepid.

I was having some really spectacularly bad ping with a game in wine, and thought it might be audio related. So I went into winecfg and tried it with the different audio drivers.

I tried the oss driver last, and I didn't get any sound at all, and still had bad ping. I figured the issue wasn't audio and gave up for the time being. However, after closing wine I realized that I didn't have any sound at all, except for some very fine static noises when sound attempted to play.

So I went back into winecfg and changed the audio settings back to what they were before I'd played with them (alsa driver), but still had no sound.

I know the sound card didn't fail, because everything works perfectly fine on a liveCD. Something I did in wineconfig broke the sound in the entire system.

Help would be appreciated.

Also, some outputs:

ryan@Balthazar:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 255
	Memory at f2200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f2486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f2488000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f2487000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30e0 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f2480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory behind bridge: f2100000-f21fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 30f8 [size=8]
	I/O ports at 30ec [size=4]
	I/O ports at 30f0 [size=8]
	I/O ports at 30e8 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f2484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2000000-f20fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0000000-f1ffffff
	Prefetchable memory behind bridge: 00000000f2600000-00000000f27fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath5k, ath_pci

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f2100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f2100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

---

### Post by Ketara on 2009-04-09
As an update, I reinstalled the kernel files as described in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and it has not changed anything.

---

### Post by Ketara on 2009-04-10
I'd just like to throw out here that this is slightly serious, as I will need sound on this machine for work tomorrow.

---

### Post by Ketara on 2009-04-10
Ugh, nevermind, fixed it. Somehow wine changed a PCM setting in volume control.

---

