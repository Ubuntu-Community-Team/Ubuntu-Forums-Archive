---
title: "Yet Another No Sound Thread"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by jfrickmann on 2006-06-13
I have used five different Linux distros since 1999 and have always managed to get everything to work. Until I tried sound in XUbuntu:(  I have read various wikis, howtos, surfed Google and read threads in this forum without any succes.

So pleeeaaase help!

Kernel version:

Linux version 2.6.15-23-k7 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006

/proc/asound/cards:

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650E at 0xe400, irq 11
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 5

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v:

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
        Subsystem: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [c0] Power Management version 2

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d8000000-e7ffffff
        Capabilities: [80] Power Management version 2

0000:00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: AOPEN Inc.: Unknown device 01b7
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d000 [size=256]
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d400 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d800 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dc00 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at ea001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: AOPEN Inc.: Unknown device 030f
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at e000 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: AOPEN Inc.: Unknown device 01b6
        Flags: medium devsel, IRQ 11
        I/O ports at e400 [size=256]
        Capabilities: [c0] Power Management version 2

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01) (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd: Unknown device 2062
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
        Subsystem: C.P. Technology Co. Ltd: Unknown device 2063
        Flags: 66MHz, medium devsel
        Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

```
dmesg:
```
[4294667.296000] Linux version 2.6.15-23-k7 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 131056
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126960 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AOPEN                                 ) @ 0x000f7940
[4294667.296000] ACPI: RSDT (v001 AOPEN  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[4294667.296000] ACPI: FADT (v001 AOPEN  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[4294667.296000] ACPI: DSDT (v001 AOPEN  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda4 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (014c3000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1827.212 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.414000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.415000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.433000] Memory: 507764k/524224k available (2094k kernel code, 15920k reserved, 597k data, 332k init, 0k highmem)
[4294670.433000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.493000] Calibrating delay using timer specific routine.. 3655.31 BogoMIPS (lpj=1827655)
[4294670.493000] Security Framework v1.0.0 initialized
[4294670.493000] SELinux:  Disabled at boot.
[4294670.493000] Mount-cache hash table entries: 512
[4294670.493000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.493000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.493000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.493000] CPU: L2 Cache: 512K (64 bytes/line)
[4294670.493000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000020 00000000 00000000 00000000
[4294670.493000] mtrr: v2.0 (20020519)
[4294670.493000] Enabling fast FPU save and restore... done.
[4294670.493000] Enabling unmasked SIMD FPU exception support... done.
[4294670.493000] Checking 'hlt' instruction... OK.
[4294670.497000] SMP alternatives: switching to UP code
[4294670.497000] checking if image is initramfs... it is
[4294671.085000] Freeing initrd memory: 6765k freed
[4294671.101000] ACPI: Looking for DSDT ... not found!
[4294671.103000] ACPI: setting ELCR to 0200 (from 0e00)
[4294671.105000] CPU0: AMD Athlon(tm) XP 2500+ stepping 00
[4294671.105000] SMP motherboard not detected.
[4294671.105000] Local APIC not detected. Using dummy APIC emulation.
[4294671.105000] Brought up 1 CPUs
[4294671.105000] NET: Registered protocol family 16
[4294671.105000] EISA bus registered
[4294671.105000] ACPI: bus type pci registered
[4294671.110000] PCI: PCI BIOS revision 2.10 entry at 0xfb390, last bus=1
[4294671.110000] PCI: Using configuration type 1
[4294671.110000] ACPI: Subsystem revision 20051216
[4294671.118000] ACPI: Interpreter enabled
[4294671.118000] ACPI: Using PIC for interrupt routing
[4294671.118000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.118000] PCI: Probing PCI hardware (bus 00)
[4294671.119000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.122000] PCI quirk: region 4000-407f claimed by vt8235 PM
[4294671.122000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[4294671.122000] Boot video device is 0000:01:00.0
[4294671.122000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.146000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294671.146000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294671.147000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294671.147000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294671.147000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.148000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.148000] ACPI: PCI Interrupt Link [LNK0] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.149000] ACPI: PCI Interrupt Link [LNK1] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.152000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.152000] pnp: PnP ACPI init
[4294671.158000] pnp: PnP ACPI: found 15 devices
[4294671.158000] PnPBIOS: Disabled by ACPI PNP
[4294671.158000] PCI: Using ACPI for IRQ routing
[4294671.158000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.179000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[4294671.179000] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
[4294671.179000] PCI: Bridge: 0000:00:01.0
[4294671.179000]   IO window: c000-cfff
[4294671.179000]   MEM window: e8000000-e9ffffff
[4294671.179000]   PREFETCH window: d8000000-e7ffffff
[4294671.179000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.180000] audit: initializing netlink socket (disabled)
[4294671.180000] audit(1150243838.178:1): initialized
[4294671.180000] VFS: Disk quotas dquot_6.5.1
[4294671.180000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.180000] Initializing Cryptographic API
[4294671.180000] io scheduler noop registered
[4294671.180000] io scheduler anticipatory registered
[4294671.180000] io scheduler deadline registered
[4294671.180000] io scheduler cfq registered
[4294671.180000] isapnp: Scanning for PnP cards...
[4294671.537000] isapnp: No Plug & Play device found
[4294671.552000] Real Time Clock Driver v1.12
[4294671.552000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.552000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.553000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.553000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.553000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.553000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.555000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.555000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.556000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.556000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.556000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.556000] mice: PS/2 mouse device common for all mice
[4294671.556000] EISA: Probing bus 0 at eisa.0
[4294671.556000] Cannot allocate resource for EISA slot 4
[4294671.556000] Cannot allocate resource for EISA slot 5
[4294671.556000] EISA: Detected 0 cards.
[4294671.556000] NET: Registered protocol family 2
[4294671.566000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)[4294671.566000] TCP established hash table entries: 32768 (order: 6, 393216 bytes)
[4294671.567000] TCP bind hash table entries: 32768 (order: 6, 393216 bytes)
[4294671.567000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.567000] TCP reno registered
[4294671.568000] TCP bic registered
[4294671.568000] NET: Registered protocol family 1
[4294671.568000] NET: Registered protocol family 8
[4294671.568000] NET: Registered protocol family 20
[4294671.568000] Using IPI No-Shortcut mode
[4294671.568000] ACPI wakeup devices:
[4294671.568000] SLPB PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 MC97 UAR1 ECP1
[4294671.568000] ACPI: (supports S0 S1 S4 S5)
[4294671.568000] Freeing unused kernel memory: 332k freed
[4294671.581000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.620000] vga16fb: initializing
[4294671.620000] vga16fb: mapped to 0xc00a0000
[4294671.719000] Console: switching to colour frame buffer device 80x25
[4294671.719000] fb0: VGA16 VGA frame buffer device
[4294672.830000] Capability LSM initialized
[4294672.861000] ACPI: Fan [FAN] (on)
[4294672.864000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294672.866000] ACPI: Thermal Zone [THRM] (30 C)
[4294673.370000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.370000] **** SET: Misaligned resource pointer: dfef5ce2 Type 07 Len 0
[4294673.371000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294673.371000] PCI: setting IRQ 10 as level-triggered
[4294673.371000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294673.371000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 10
[4294673.371000] VP_IDE: chipset revision 6
[4294673.371000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.371000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294673.371000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:pio
[4294673.371000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:pio
[4294673.371000] Probing IDE interface ide0...
[4294673.757000] hda: Maxtor 6Y120P0, ATA DISK drive
[4294674.369000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.371000] Probing IDE interface ide1...
[4294675.165000] hdc: Hewlett-Packard CD-Writer Plus 9100b, ATAPI CD/DVD-ROM drive
[4294675.471000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.479000] hda: max request size: 128KiB
[4294675.487000] hda: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(133)
[4294675.488000] hda: cache flushes supported
[4294675.488000]  hda: hda1 hda2 hda3 hda4
[4294675.505000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[4294675.505000] Uniform CD-ROM driver Revision: 3.20
[4294675.752000] usbcore: registered new driver usbfs
[4294675.752000] usbcore: registered new driver hub
[4294675.754000] USB Universal Host Controller Interface driver v2.3
[4294675.755000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294675.755000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294675.755000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.755000] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000d400
[4294675.756000] hub 1-0:1.0: USB hub found
[4294675.756000] hub 1-0:1.0: 2 ports detected
[4294675.857000] **** SET: Misaligned resource pointer: dfef57a2 Type 07 Len 0
[4294675.857000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294675.857000] PCI: setting IRQ 11 as level-triggered
[4294675.857000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294675.857000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294675.858000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.858000] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000d800
[4294675.858000] hub 2-0:1.0: USB hub found
[4294675.858000] hub 2-0:1.0: 2 ports detected
[4294675.959000] **** SET: Misaligned resource pointer: dfef5622 Type 07 Len 0
[4294675.959000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294675.959000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294675.959000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294675.959000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.959000] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000dc00
[4294675.960000] hub 3-0:1.0: USB hub found
[4294675.960000] hub 3-0:1.0: 2 ports detected
[4294676.063000] **** SET: Misaligned resource pointer: dfef54a2 Type 07 Len 0
[4294676.063000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294676.063000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294676.063000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294676.064000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.064000] ehci_hcd 0000:00:10.3: irq 10, io mem 0xea001000
[4294676.064000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.064000] hub 4-0:1.0: USB hub found
[4294676.064000] hub 4-0:1.0: 6 ports detected
[4294676.214000] Attempting manual resume
[4294676.223000] ReiserFS: hda4: found reiserfs format "3.6" with standard journal
[4294676.747000] ReiserFS: hda4: using ordered data mode
[4294676.761000] ReiserFS: hda4: journal params: device hda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294676.763000] ReiserFS: hda4: checking transaction log (hda4)
[4294676.786000] ReiserFS: hda4: Using r5 hash to sort names
[4294681.029000] irda_init()
[4294681.029000] NET: Registered protocol family 23
[4294681.081000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294681.081000] 8139cp: pci dev 0000:00:05.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294681.081000] 8139cp: Try the "8139too" driver instead.
[4294681.129000] 8139too Fast Ethernet driver 0.9.27
[4294681.129000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294681.129000] eth0: RealTek RTL8139 at 0xe08fa000, 00:01:80:41:31:47, IRQ 11
[4294681.129000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294681.179000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294681.209000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294681.224000] Linux agpgart interface v0.101 (c) Dave Jones
[4294681.247000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[4294681.255000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294681.665000] parport: PnPBIOS parport detected.
[4294681.665000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294681.793000] Floppy drive(s): fd0 is 1.44M
[4294681.847000] FDC 0 is a post-1991 82077
[4294681.878000] input: PC Speaker as /class/input/input1
[4294681.980000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294681.980000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294682.076000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294682.086000] logips2pp: Detected unknown logitech mouse model 62
[4294682.155000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[4294682.388000] ts: Compaq touchscreen protocol output
[4294683.225000] lp0: using parport0 (interrupt-driven).
[4294683.349000] NET: Registered protocol family 17
[4294683.450000] Adding 1004052k swap on /dev/hda2.  Priority:-1 extents:1 across:1004052k
[4294685.903000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.903000] md: bitmap version 4.39
[4294686.176000] NET: Registered protocol family 10
[4294686.176000] lo: Disabled Privacy Extensions
[4294686.176000] IPv6 over IPv4 tunneling driver
[4294686.453000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294687.085000] cdrom: open failed.
[4294696.142000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[4294696.142000] ReiserFS: hda1: using ordered data mode
[4294696.146000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294696.148000] ReiserFS: hda1: checking transaction log (hda1)
[4294696.163000] ReiserFS: hda1: Using r5 hash to sort names
[4294696.183000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[4294696.934000] eth0: no IPv6 routers present
[4294703.092000] ReiserFS: hda3: using ordered data mode
[4294703.111000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294703.113000] ReiserFS: hda3: checking transaction log (hda3)
[4294703.170000] ReiserFS: hda3: Using r5 hash to sort names
[4294708.896000] pcc_acpi: loading...
[4294708.910000] ACPI: Power Button (FF) [PWRF]
[4294708.910000] ACPI: Power Button (CM) [PWRB]
[4294708.910000] ACPI: Sleep Button (CM) [SLPB]
[4294708.962000] ibm_acpi: ec object not found
[4294712.218000] [drm] Initialized drm 1.0.1 20051102
[4294712.229000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294712.229000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294713.158000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294713.158000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294713.158000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294713.341000] ppdev: user-space parallel port driver
[4294713.567000] [drm] Setting GART location based on new memory map
[4294713.567000] [drm] Loading R200 Microcode
[4294713.567000] [drm] writeback test succeeded in 1 usecs
[4294713.685000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294713.686000] apm: overridden by ACPI.
[4294726.933000] DMA write timed out
[4294796.950000] parport0: FIFO is stuck
[4294796.990000] parport0: BUSY timeout (1) in compat_write_block_pio
...

```

[aadebug.sh]("http://alsa.opensrc.org/index.php?page=aadebug")
```
ALSA Audio Debug v0.1.0 - Tue Jun 13 22:05:20 EDT 2006
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux pingu 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_seq_dummy           4164  0
snd_seq_oss            37696  0
snd_seq_midi            9888  0
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mpu401              7112  1
snd_via82xx            31192  3
snd_ac97_codec         98912  1 snd_via82xx
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  3 snd_pcm_oss
snd_pcm                96772  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  2 snd_seq,snd_pcm
snd_page_alloc         11592  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8896  2 snd_mpu401,snd_via82xx
snd_rawmidi            27552  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60068  16 snd_seq_oss,snd_seq,snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650E at 0xe400, irq 11
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 5
 17: [0- 1]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
 40: [1- 0]: raw midi
 32: [1- 0]: ctl
cat: /proc/asound/hwdep: No such file or directory
00-00: VIA 8235 : VIA 8235 : playback 4 : capture 1
00-01: VIA 8235 : VIA 8235 : playback 1 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0
Client  62 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  72 : "MPU-401 UART MIDI" [Kernel]
  Port   0 : "MPU-401 UART MIDI" (RWeX)

Dev Snd ---------------------------------------------------
controlC0  midiC1D0  pcmC0D0p  pcmC0D1p  timer
controlC1  pcmC0D0c  pcmC0D1c  seq

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) XP 2500+
cpu MHz         : 1827.212

RAM -------------------------------------------------------
MemTotal:       515016 kB
SwapTotal:     1004052 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
```
Lots of data and still not a clue! It all looks fine to me:confused: 

/Jesper

---

### Post by caldevil on 2006-06-13
What happens when you try to play a sound file? Does it give any error or you just cannot listen anything?

---

### Post by jfrickmann on 2006-06-13
No error messages. Everything works perfect except for the lack of sound! And yes, I have turned up the volume. Sound worked until Sunday under Gentoo.

/Jesper

---

### Post by caldevil on 2006-06-13
Well, I had similar problem some time ago and it was related to turning up the volume. I have to specifically use alsamix and turn on the volume.

---

### Post by jfrickmann on 2006-06-14
Yes, the muted mixer is a classic. But that is not the case here!

Jesper

---

### Post by VinnyM69 on 2006-06-14
I had a problem with low volume and it ended up being caused by running an app called Streamtuner which was using XMMS to play MP3 files. I'd set the sound volume in XMMS and that seems to override all other sound settings.  After quitting that application and trying to use another application to play MP3's (amaroK) my sound volume was very low even after turning the volume up all the way.  I went back into XMMS and raised the volume in it back to normal and then my sound level was back to normal in all my other sound playback applications.  It seems XMMS overides all other sound/muting levels.

Don't know if this is your problem or not, but it's something to be aware of.

;)

---

### Post by jfrickmann on 2006-06-14
My face is red - Moving the jack from the blue to the green plug on my PC helped :rolleyes: Funny thing is, the blue one must have worked with Gentoo :confused: 

Jesper

---

