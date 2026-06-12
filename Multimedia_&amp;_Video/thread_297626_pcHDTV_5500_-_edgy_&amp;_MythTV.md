---
title: "pcHDTV 5500 - edgy &amp; MythTV"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Bouncelot on 2006-11-11
Hello, hello
I recently bought a pcHDTV 5500 and am trying to get it running with a fresh edgy install.

I know nothing of receiver cards, this is my first. I am a little lost, all the HOWTO's seem to require some base knowledge that I am missing. The intent is to get the card installed and configured to work with MythTV, using an analog cable input (Rogers Cable).

I installed the latest drivers from the pcHDTV site, and they appear to be loading fine (see dmesg output below). Scanning channels in Myth says there is no signal. I have verified that the cable coming in is fine.
I have no idea what to try next...

any help would be appreciated.

dmesg:
> [17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[17179569.184000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262140
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32764 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5f90
[17179569.184000] ACPI: RSDT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x3fffc000
[17179569.184000] ACPI: FADT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x3fffc0b2
[17179569.184000] ACPI: BOOT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x3fffc030
[17179569.184000] ACPI: MADT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x3fffc058
[17179569.184000] ACPI: DSDT (v001   ASUS A7V8X    0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash noapic irqpoll
[17179569.184000] Misrouted IRQ fixup and polling support enabled
[17179569.184000] This may significantly impact system performance
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2166.841 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.480000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.480000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.516000] Memory: 1029564k/1048560k available (1910k kernel code, 18292k reserved, 1070k data, 308k init, 131056k highmem)
[17179571.516000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.596000] Calibrating delay using timer specific routine.. 4343.08 BogoMIPS (lpj=8686165)
[17179571.596000] Security Framework v1.0.0 initialized
[17179571.596000] SELinux:  Disabled at boot.
[17179571.596000] Mount-cache hash table entries: 512
[17179571.596000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.596000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.596000] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[17179571.596000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.596000] CPU: L2 Cache: 512K (64 bytes/line)
[17179571.596000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179571.596000] Checking 'hlt' instruction... OK.
[17179571.612000] SMP alternatives: switching to UP code
[17179571.612000] Freeing SMP alternatives: 16k freed
[17179571.612000] checking if image is initramfs... it is
[17179572.052000] Freeing initrd memory: 5523k freed
[17179572.052000] ACPI: Core revision 20060707
[17179572.052000] ACPI: Looking for DSDT ... not found!
[17179572.056000] ACPI: setting ELCR to 0200 (from 0808)
[17179572.056000] CPU0: AMD # stepping 00
[17179572.056000] Total of 1 processors activated (4343.08 BogoMIPS).
[17179572.160000] Brought up 1 CPUs
[17179572.160000] migration_cost=0
[17179572.160000] NET: Registered protocol family 16
[17179572.160000] EISA bus registered
[17179572.160000] ACPI: bus type pci registered
[17179572.160000] PCI: PCI BIOS revision 2.10 entry at 0xf1730, last bus=1
[17179572.160000] PCI: Using configuration type 1
[17179572.160000] Setting up standard PCI resources
[17179572.172000] ACPI: Interpreter enabled
[17179572.172000] ACPI: Using PIC for interrupt routing
[17179572.172000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.172000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.172000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.172000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.176000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14)
[17179572.176000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[17179572.176000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.176000] PCI: Probing PCI hardware (bus 00)
[17179572.176000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.176000] PCI quirk: region e400-e47f claimed by vt8235 PM
[17179572.176000] PCI quirk: region e800-e80f claimed by vt8235 SMB
[17179572.176000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179572.176000] Boot video device is 0000:01:00.0
[17179572.176000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.180000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179572.184000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.184000] pnp: PnP ACPI init
[17179572.184000] pnp: PnP ACPI: found 11 devices
[17179572.184000] PnPBIOS: Disabled by ACPI PNP
[17179572.184000] PCI: Using ACPI for IRQ routing
[17179572.184000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.188000] spurious 8259A interrupt: IRQ7.
[17179572.192000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[17179572.192000] pnp: 00:02: ioport range 0xe800-0xe81f could not be reserved
[17179572.192000] pnp: 00:0a: ioport range 0x290-0x291 has been reserved
[17179572.192000] pnp: 00:0a: ioport range 0x370-0x372 has been reserved
[17179572.192000] PCI: Bridge: 0000:00:01.0
[17179572.192000]   IO window: disabled.
[17179572.192000]   MEM window: ee000000-ef5fffff
[17179572.192000]   PREFETCH window: ef700000-f7ffffff
[17179572.192000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.192000] NET: Registered protocol family 2
[17179572.232000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.232000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.232000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.232000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.232000] TCP reno registered
[17179572.232000] Simple Boot Flag at 0x3a set to 0x1
[17179572.236000] audit: initializing netlink socket (disabled)
[17179572.236000] audit(1163264045.236:1): initialized
[17179572.236000] highmem bounce pool size: 64 pages
[17179572.236000] VFS: Disk quotas dquot_6.5.1
[17179572.236000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.236000] Initializing Cryptographic API
[17179572.236000] io scheduler noop registered
[17179572.236000] io scheduler anticipatory registered
[17179572.236000] io scheduler deadline registered
[17179572.236000] io scheduler cfq registered (default)
[17179572.236000] isapnp: Scanning for PnP cards...
[17179572.588000] isapnp: No Plug & Play device found
[17179572.608000] Real Time Clock Driver v1.12ac
[17179572.608000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.612000] mice: PS/2 mouse device common for all mice
[17179572.612000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.612000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.612000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.612000] PNP: No PS/2 controller found. Probing ports directly.
[17179572.620000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.620000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.620000] EISA: Probing bus 0 at eisa.0
[17179572.620000] EISA: Detected 0 cards.
[17179572.620000] TCP bic registered
[17179572.620000] NET: Registered protocol family 1
[17179572.620000] NET: Registered protocol family 8
[17179572.620000] NET: Registered protocol family 20
[17179572.620000] Using IPI No-Shortcut mode
[17179572.620000] ACPI: (supports S0 S1 S4 S5)
[17179572.620000] Freeing unused kernel memory: 308k freed
[17179573.264000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.372000] Capability LSM initialized
[17179574.684000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179574.684000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179574.684000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179574.684000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179574.684000] VP_IDE: chipset revision 6
[17179574.684000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.684000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179574.684000]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:DMA
[17179574.684000]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:pio
[17179574.684000] Probing IDE interface ide0...
[17179575.100000] hda: Maxtor 6E040L0, ATA DISK drive
[17179575.384000] hdb: IC35L040AVER07-0, ATA DISK drive
[17179575.444000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.468000] Probing IDE interface ide1...
[17179576.332000] hdc: Pioneer DVD-ROM ATAPIModel DVD-115 0122, ATAPI CD/DVD-ROM drive
[17179576.672000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.676000] hda: max request size: 128KiB
[17179576.688000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[17179576.688000] hda: cache flushes supported
[17179576.688000]  hda: hda1 hda2 < hda5 >
[17179576.716000] hdb: max request size: 128KiB
[17179576.716000] hdb: 80418240 sectors (41174 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(33)
[17179576.716000] hdb: cache flushes not supported
[17179576.716000]  hdb: hdb1
[17179576.740000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179576.740000] Uniform CD-ROM driver Revision: 3.20
[17179577.020000] usbcore: registered new driver usbfs
[17179577.020000] usbcore: registered new driver hub
[17179577.020000] USB Universal Host Controller Interface driver v3.0
[17179577.020000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 3
[17179577.020000] PCI: setting IRQ 3 as level-triggered
[17179577.020000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[17179577.020000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179577.020000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179577.020000] uhci_hcd 0000:00:10.0: irq 3, io base 0x0000d800
[17179577.020000] usb usb1: configuration #1 chosen from 1 choice
[17179577.020000] hub 1-0:1.0: USB hub found
[17179577.020000] hub 1-0:1.0: 2 ports detected
[17179577.124000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[17179577.124000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179577.124000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179577.128000] uhci_hcd 0000:00:10.1: irq 3, io base 0x0000d400
[17179577.128000] usb usb2: configuration #1 chosen from 1 choice
[17179577.128000] hub 2-0:1.0: USB hub found
[17179577.128000] hub 2-0:1.0: 2 ports detected
[17179577.232000] PCI: Enabling device 0000:00:10.2 (0014 -> 0015)
[17179577.232000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[17179577.232000] PCI: Via IRQ fixup for 0000:00:10.2, from 243 to 3
[17179577.232000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179577.232000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179577.232000] uhci_hcd 0000:00:10.2: irq 3, io base 0x0000d000
[17179577.232000] usb usb3: configuration #1 chosen from 1 choice
[17179577.232000] hub 3-0:1.0: USB hub found
[17179577.232000] hub 3-0:1.0: 2 ports detected
[17179577.348000] PCI: Enabling device 0000:00:10.3 (0014 -> 0016)
[17179577.348000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[17179577.348000] PCI: Via IRQ fixup for 0000:00:10.3, from 243 to 3
[17179577.348000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179577.348000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179577.348000] ehci_hcd 0000:00:10.3: irq 3, io mem 0xe8800000
[17179577.348000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.348000] usb usb4: configuration #1 chosen from 1 choice
[17179577.348000] hub 4-0:1.0: USB hub found
[17179577.352000] hub 4-0:1.0: 6 ports detected
[17179577.504000] Attempting manual resume
[17179577.536000] kjournald starting.  Commit interval 5 seconds
[17179577.536000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.480000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179578.660000] usb 2-2: configuration #1 chosen from 1 choice
[17179578.664000] hub 2-2:1.0: USB hub found
[17179578.668000] hub 2-2:1.0: 2 ports detected
[17179579.008000] usb 2-2.2: new low speed USB device using uhci_hcd and address 3
[17179579.160000] usb 2-2.2: configuration #1 chosen from 1 choice
[17179579.976000] usb 2-2.1: new low speed USB device using uhci_hcd and address 4
[17179580.124000] usb 2-2.1: configuration #1 chosen from 1 choice
[17179586.904000] Linux video capture interface: v1.00
[17179587.352000] Floppy drive(s): fd0 is 1.44M
[17179587.380000] FDC 0 is a post-1991 82077
[17179587.540000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.552000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.708000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.712000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179587.716000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179587.788000] input: PC Speaker as /class/input/input1
[17179587.908000] irda_init()
[17179587.908000] NET: Registered protocol family 23
[17179587.944000] b44.c:v1.00 (Apr 7, 2006)
[17179587.944000] PCI: Enabling device 0000:00:09.0 (0004 -> 0006)
[17179587.944000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179587.944000] PCI: setting IRQ 11 as level-triggered
[17179587.944000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179587.948000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:e0:18:a6:18:d4
[17179588.552000] cx2388x dvb driver version 0.0.5 loaded
[17179588.552000] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[17179588.552000] TV tuner 64 at 0x1fe, Radio tuner -1 at 0x1fe
[17179588.604000] cx2388x alsa driver version 0.0.5 loaded
[17179588.672000] usbcore: registered new driver hiddev
[17179588.676000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[17179588.676000] PCI: Enabling device 0000:00:0b.2 (0014 -> 0016)
[17179588.680000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179588.680000] PCI: setting IRQ 10 as level-triggered
[17179588.680000] ACPI: PCI Interrupt 0000:00:0b.2[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179588.680000] cx88[0]/2: found at 0000:00:0b.2, rev: 5, irq: 10, latency: 32, mmio: 0xea000000
[17179588.680000] cx88[0]/2: cx2388x based dvb card
[17179588.980000] DVB: registering new adapter (cx88[0]).
[17179588.980000] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[17179588.980000] PCI: Enabling device 0000:00:0b.1 (0014 -> 0016)
[17179588.980000] ACPI: PCI Interrupt 0000:00:0b.1[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179589.004000] input: Logitech USB Receiver as /class/input/input2
[17179589.004000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.1-2.2
[17179589.032000] cx2388x v4l2 driver version 0.0.5 loaded
[17179589.072000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.092000] input: Logitech USB Receiver as /class/input/input3
[17179589.092000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.1-2.2
[17179589.100000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[17179589.100000] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[17179589.100000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179589.100000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 10, latency: 32, mmio: 0xec000000
[17179589.128000] input: Logitech Desktop USB stand as /class/input/input4
[17179589.128000] input,hiddev97: USB HID v1.10 Keyboard [Logitech Desktop USB stand] on usb-0000:00:10.1-2.1
[17179589.128000] usbcore: registered new driver usbhid
[17179589.128000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.172000] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[17179589.176000] tuner 1-0061: type set to 64 (LG TDVS-H062F/TUA6034)
[17179589.256000] tda9887 1-0043: chip found @ 0x86 (cx88[0])
[17179589.260000] cx88[0]/0: registered device video0 [v4l2]
[17179589.260000] cx88[0]/0: registered device vbi0
[17179589.268000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179589.268000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179589.268000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179589.516000] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[17179589.520000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 15
[17179589.520000] PCI: setting IRQ 15 as level-triggered
[17179592.204000] irq 15: nobody cared (try booting with the "irqpoll" option)
[17179592.204000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179592.204000]  <c0149448> __do_IRQ+0xf8/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179592.204000]  <c010408a> common_interrupt+0x1a/0x20  <c0149307> handle_IRQ_event+0x17/0x60
[17179592.204000]  <c01493ed> __do_IRQ+0x9d/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179592.204000]  <c010408a> common_interrupt+0x1a/0x20  <c026494f> eisa_set_level_irq+0x7f/0x90
[17179592.204000]  <c0110107> acpi_register_gsi+0x47/0x60  <c02181f5> acpi_pci_irq_enable+0x133/0x1da
[17179592.204000]  <c0217feb> acpi_pci_allocate_irq+0x0/0x4d  <c02655a4> pcibios_enable_device+0x14/0x20
[17179592.204000]  <c01ec134> pci_enable_device_bars+0x24/0x60  <c01ec186> pci_enable_device+0x16/0x40
[17179592.204000]  <f8aec4a4> snd_via82xx_probe+0xf4/0x1030 [snd_via82xx]  <c01edc33> pci_match_device+0x13/0xe0
[17179592.204000]  <c01edd76> pci_device_probe+0x56/0x80  <c0245f44> driver_probe_device+0x44/0xc0
[17179592.204000]  <c02460c2> __driver_attach+0x82/0x90  <c02458bb> bus_for_each_dev+0x3b/0x60
[17179592.204000]  <c0245e86> driver_attach+0x16/0x20  <c0246040> __driver_attach+0x0/0x90
[17179592.204000]  <c024552c> bus_add_driver+0x8c/0x140  <c02462f1> driver_register+0x41/0xa0
[17179592.204000]  <c01edf17> __pci_register_driver+0x47/0x70  <c013cda8> sys_init_module+0x148/0x19c0
[17179592.204000]  <f8ae1000> tda9887_fixup_std+0x0/0x580 [tda9887]  <c0128330> __request_region+0x0/0x90
[17179592.204000]  <c0102fbb> sysenter_past_esp+0x54/0x79
[17179592.204000] handlers:
[17179592.204000] [<c02528e0>] (ide_intr+0x0/0x1f0)
[17179592.204000] Disabling IRQ #15
[17179592.208000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKF] -> GSI 15 (level, low) -> IRQ 15
[17179592.208000] PCI: Via IRQ fixup for 0000:00:11.5, from 255 to 15
[17179592.208000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179592.220000] cx2388x blackbird driver version 0.0.5 loaded
[17179592.388000] ts: Compaq touchscreen protocol output
[17179592.984000] lp: driver loaded but no devices found
[17179593.008000] Adding 1662688k swap on /dev/disk/by-uuid/83d74a4a-dbd9-4553-b261-0d82360ac5b0.  Priority:-1 extents:1 across:1662688k
[17179593.072000] EXT3 FS on hda1, internal journal
[17179593.204000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179593.204000] b44: eth0: Flow control is off for TX and off for RX.
[17179593.664000] NET: Registered protocol family 10
[17179593.664000] lo: Disabled Privacy Extensions
[17179593.668000] IPv6 over IPv4 tunneling driver
[17179594.440000] NET: Registered protocol family 17
[17179598.692000] ACPI: Power Button (FF) [PWRF]
[17179598.692000] ACPI: Power Button (CM) [PWRB]
[17179598.804000] ibm_acpi: ec object not found
[17179598.840000] pcc_acpi: loading...
[17179601.152000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179601.152000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179601.152000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179604.296000] eth0: no IPv6 routers present
[17179605.540000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.540000] apm: overridden by ACPI.
[17179618.592000] Bluetooth: Core ver 2.8
[17179618.592000] NET: Registered protocol family 31
[17179618.592000] Bluetooth: HCI device and connection manager initialized
[17179618.592000] Bluetooth: HCI socket layer initialized
[17179618.900000] Bluetooth: L2CAP ver 2.8
[17179618.900000] Bluetooth: L2CAP socket layer initialized
[17179619.012000] Bluetooth: RFCOMM socket layer initialized
[17179619.012000] Bluetooth: RFCOMM TTY layer initialized
[17179619.012000] Bluetooth: RFCOMM ver 1.7
[17179948.328000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17180696.640000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

---

### Post by theyost on 2006-12-19
In case someone else comes across this problem...

[http://linuxtv.org/irc/linuxtv/index.php?date=2006-09-28]("http://linuxtv.org/irc/linuxtv/index.php?date=2006-09-28")

(run a text search for "edgy")

---

