---
title: "Surround Sound issue"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Time_ on 2009-11-27
Hi all.

I have a bit of a strange issue with a computer I'm setting up.  It has sound outputs on the motherboard, which run one set of speakers and seem to be working fine, and a PCI surround sound card, which is not.  That is, it happily produces stereo output, but I've been unable to convince pulseaudio that it is in fact a surround sound card - all of the output profiles are stereo outputs of various flavors, and the only output channels which show up in Volume Control are Front Left and Front Right.


Help?  



```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
~: lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 9600
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 7000 [size=16]
	Memory at fe8ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe8ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8fb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ATI Technologies Inc SB700/SB800 USB EHCI Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe8fa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Biostar Microtech Int'l Corp Device 820f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Biostar Microtech Int'l Corp Device 3700
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000e000-0000efff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ATI Technologies Inc Device 4396
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8f9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
	Subsystem: Biostar Microtech Int'l Corp Device 0017
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at feae8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Biostar Microtech Int'l Corp Device 2307
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at d800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-e0-4c-68-00-00-00-13
	Kernel driver in use: r8169
	Kernel modules: r8169

03:05.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: VIA Technologies Inc. Device 2403
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at e800 [size=32]
	I/O ports at e400 [size=128]
	Capabilities: [80] Power Management version 1
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724

```

---

### Post by Time_ on 2009-11-30
Bump?

---

