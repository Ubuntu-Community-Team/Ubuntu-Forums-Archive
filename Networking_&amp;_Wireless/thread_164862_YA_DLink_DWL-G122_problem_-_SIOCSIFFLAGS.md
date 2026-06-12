---
title: "YA DLink DWL-G122 problem - SIOCSIFFLAGS"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by dante.regis on 2006-04-23
Hello there,

this is my first post here onuUbuntuforums.org, and I hope the first of many both getting and giving help. I have tried my best not to post on a subject that is so full of threads like this one, but for this specific question I did not find any answer here.

Thing is, after lot's of reinstalls and work I managed to get Dapper to show my DWL-122 on the network interfaces list. Only I can't get it up. When I type 

```

sudo ifconfig eth1 up

```

I get this: 
```

SIOCSIFFLAGS: No such file or directory

```

I remember seeing somewhere that this could be a firmware problem, and recommended to type dmesg. I indeed found some problems on it I don't really know what it means (noob) but I do know that there's a problem on the last few lines. This is the complete dmesg.

```

[4294667.296000] Linux version 2.6.15-20-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu3)) #1 PREEMPT Tue Apr 4 17:48:51 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[4294667.296000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001ff00000 - 000000001ff80000 (usable)
[4294667.296000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 130944
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126848 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6da0
[4294667.296000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x1fefa607
[4294667.296000] ACPI: FADT (v001 TOSCPL BTR20    0x06040000 PTL  0x00000001) @ 0x1fefef64
[4294667.296000] ACPI: BOOT (v001 TOSCPL $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
[4294667.296000] ACPI: DSDT (v001 COMPAL BTR20    0x06040000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01401000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1994.248 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.253000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.254000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.271000] Memory: 508592k/523776k available (1973k kernel code, 14580k reserved, 601k data, 288k init, 0k highmem)
[4294670.271000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.331000] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=1995015)
[4294670.331000] Security Framework v1.0.0 initialized
[4294670.331000] SELinux:  Disabled at boot.
[4294670.331000] Mount-cache hash table entries: 512
[4294670.331000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.331000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.331000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.331000] CPU: L2 cache: 512K
[4294670.331000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[4294670.331000] mtrr: v2.0 (20020519)
[4294670.331000] CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[4294670.331000] Enabling fast FPU save and restore... done.
[4294670.331000] Enabling unmasked SIMD FPU exception support... done.
[4294670.331000] Checking 'hlt' instruction... OK.
[4294670.335000] checking if image is initramfs... it is
[4294671.046000] Freeing initrd memory: 6388k freed
[4294671.062000] ACPI: Looking for DSDT ... not found!
[4294671.065000] ACPI: setting ELCR to 0200 (from 0820)
[4294671.071000] NET: Registered protocol family 16
[4294671.071000] EISA bus registered
[4294671.071000] ACPI: bus type pci registered
[4294671.081000] PCI: PCI BIOS revision 2.10 entry at 0xfd990, last bus=2
[4294671.081000] PCI: Using configuration type 1
[4294671.081000] ACPI: Subsystem revision 20051216
[4294671.087000] ACPI: Interpreter enabled
[4294671.087000] ACPI: Using PIC for interrupt routing
[4294671.088000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.088000] PCI: Probing PCI hardware (bus 00)
[4294671.111000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294671.111000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[4294671.111000] Boot video device is 0000:01:00.0
[4294671.112000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.112000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[4294671.117000] ACPI: PCI Interrupt Link [LNKA] (IRQs *5)
[4294671.117000] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[4294671.117000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[4294671.118000] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[4294671.118000] ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
[4294671.118000] ACPI: PCI Interrupt Link [LNKH] (IRQs 5) *11
[4294671.122000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[4294671.162000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.162000] pnp: PnP ACPI init
[4294671.187000] pnp: PnP ACPI: found 11 devices
[4294671.187000] PnPBIOS: Disabled by ACPI PNP
[4294671.187000] PCI: Using ACPI for IRQ routing
[4294671.187000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.192000] pnp: 00:01: ioport range 0xfe00-0xfe01 has been reserved
[4294671.193000] PCI: Bridge: 0000:00:01.0
[4294671.193000]   IO window: 3000-3fff
[4294671.193000]   MEM window: e8000000-e80fffff
[4294671.193000]   PREFETCH window: f0000000-f7ffffff
[4294671.193000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[4294671.193000]   IO window: 00004400-000044ff
[4294671.193000]   IO window: 00004800-000048ff
[4294671.193000]   PREFETCH window: 30000000-31ffffff
[4294671.193000]   MEM window: 34000000-35ffffff
[4294671.193000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[4294671.193000]   IO window: 00004c00-00004cff
[4294671.193000]   IO window: 00001400-000014ff
[4294671.193000]   PREFETCH window: 32000000-33ffffff
[4294671.193000]   MEM window: 36000000-37ffffff
[4294671.193000] PCI: Bridge: 0000:00:1e.0
[4294671.193000]   IO window: 4000-4fff
[4294671.193000]   MEM window: e8100000-e81fffff
[4294671.193000]   PREFETCH window: 30000000-33ffffff
[4294671.193000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.193000] **** SET: Misaligned resource pointer: dfe4c5c2 Type 07 Len 0
[4294671.193000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[4294671.193000] PCI: setting IRQ 5 as level-triggered
[4294671.193000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[4294671.193000] **** SET: Misaligned resource pointer: dfe4c5c2 Type 07 Len 0
[4294671.193000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294671.193000] PCI: setting IRQ 11 as level-triggered
[4294671.193000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294671.193000] Simple Boot Flag at 0x36 set to 0x1
[4294671.194000] audit: initializing netlink socket (disabled)
[4294671.194000] audit(1145806809.193:1): initialized
[4294671.194000] VFS: Disk quotas dquot_6.5.1
[4294671.194000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.194000] Initializing Cryptographic API
[4294671.194000] io scheduler noop registered
[4294671.194000] io scheduler anticipatory registered
[4294671.194000] io scheduler deadline registered
[4294671.194000] io scheduler cfq registered
[4294671.194000] isapnp: Scanning for PnP cards...
[4294671.552000] isapnp: No Plug & Play device found
[4294671.571000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294671.573000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.575000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.576000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.576000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.577000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.579000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.579000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.581000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294671.581000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294671.582000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.582000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.582000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.582000] ACPI: bus type ide registered
[4294671.582000] mice: PS/2 mouse device common for all mice
[4294671.583000] EISA: Probing bus 0 at eisa.0
[4294671.583000] Cannot allocate resource for EISA slot 1
[4294671.583000] Cannot allocate resource for EISA slot 2
[4294671.583000] Cannot allocate resource for EISA slot 3
[4294671.583000] Cannot allocate resource for EISA slot 4
[4294671.583000] EISA: Detected 0 cards.
[4294671.583000] NET: Registered protocol family 2
[4294671.592000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294671.592000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.592000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.592000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.592000] TCP reno registered
[4294671.592000] TCP bic registered
[4294671.592000] NET: Registered protocol family 1
[4294671.592000] NET: Registered protocol family 8
[4294671.592000] NET: Registered protocol family 20
[4294671.592000] Using IPI Shortcut mode
[4294671.593000] ACPI wakeup devices:
[4294671.593000] PWBN RTLN USB1 USB2 AC97
[4294671.593000] ACPI: (supports S0 S3 S4 S5)
[4294671.593000] Freeing unused kernel memory: 288k freed
[4294671.625000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.676000] vga16fb: initializing
[4294671.676000] vga16fb: mapped to 0xc00a0000
[4294671.816000] Console: switching to colour frame buffer device 80x25
[4294671.816000] fb0: VGA16 VGA frame buffer device
[4294672.990000] Capability LSM initialized
[4294673.034000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294673.721000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294673.721000] ICH2: chipset revision 5
[4294673.721000] ICH2: not 100% native mode: will probe irqs later
[4294673.721000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[4294673.722000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[4294673.722000] Probing IDE interface ide0...
[4294673.986000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[4294674.598000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.598000] Probing IDE interface ide1...
[4294675.270000] hdc: TOSHIBA DVD-ROM SD-R2212, ATAPI CD/DVD-ROM drive
[4294675.882000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.890000] hda: max request size: 128KiB
[4294675.940000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[4294675.940000] hda: cache flushes supported
[4294675.940000]  hda: hda1 hda2 hda3 < hda5 >
[4294675.993000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.993000] Uniform CD-ROM driver Revision: 3.20
[4294676.399000] usbcore: registered new driver usbfs
[4294676.400000] usbcore: registered new driver hub
[4294676.402000] USB Universal Host Controller Interface driver v2.3
[4294676.402000] **** SET: Misaligned resource pointer: dfcad502 Type 07 Len 0
[4294676.402000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294676.402000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294676.402000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294676.402000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[4294676.403000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294676.403000] uhci_hcd 0000:00:1f.2: irq 5, io base 0x00001820
[4294676.403000] hub 1-0:1.0: USB hub found
[4294676.403000] hub 1-0:1.0: 2 ports detected
[4294676.504000] **** SET: Misaligned resource pointer: dfcad202 Type 07 Len 0
[4294676.504000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[4294676.504000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[4294676.504000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294676.504000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[4294676.504000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294676.504000] uhci_hcd 0000:00:1f.4: irq 5, io base 0x00001840
[4294676.504000] hub 2-0:1.0: USB hub found
[4294676.505000] hub 2-0:1.0: 2 ports detected
[4294676.710000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294676.773000] Attempting manual resume
[4294676.821000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294676.821000] EXT3-fs: write access will be enabled during recovery.
[4294677.091000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[4294677.215000] usbcore: registered new driver hiddev
[4294677.237000] input: Topro USB Mouse as /class/input/input1
[4294677.237000] input: USB HID v1.10 Mouse [Topro USB Mouse] on usb-0000:00:1f.2-2
[4294677.237000] usbcore: registered new driver usbhid
[4294677.237000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294679.178000] EXT3-fs: hda2: orphan cleanup on readonly fs
[4294679.178000] kjournald starting.  Commit interval 5 seconds
[4294679.278000] ext3_orphan_cleanup: deleting unreferenced inode 2118152
[4294679.444000] EXT3-fs: hda2: 1 orphan inode deleted
[4294679.444000] EXT3-fs: recovery complete.
[4294679.452000] EXT3-fs: mounted filesystem with ordered data mode.
[4294690.742000] ts: Compaq touchscreen protocol output
[4294693.046000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294693.086000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294693.307000] hw_random: cannot enable RNG, aborting
[4294693.308000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.314000] agpgart: Detected an Intel i845 Chipset.
[4294693.317000] agpgart: AGP aperture is 64M @ 0xec000000
[4294693.599000] input: PS/2 Mouse as /class/input/input2
[4294693.618000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[4294693.949000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[4294693.949000] Yenta: CardBus bridge found at 0000:02:00.0 [1179:ff00]
[4294693.949000] Yenta O2: res at 0x94/0xD4: ca/00
[4294693.949000] Yenta O2: enabling read prefetch/write burst
[4294694.071000] Yenta: ISA IRQ mask 0x0498, PCI irq 5
[4294694.071000] Socket status: 30000006
[4294694.071000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[4294694.071000] cs: IO port probe 0x4000-0x4fff: clean.
[4294694.072000] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe81fffff
[4294694.072000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[4294694.093000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294694.093000] Yenta: CardBus bridge found at 0000:02:00.1 [1179:ff00]
[4294694.215000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[4294694.215000] Socket status: 30000006
[4294694.215000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[4294694.215000] cs: IO port probe 0x4000-0x4fff: clean.
[4294694.216000] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe81fffff
[4294694.216000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[4294694.347000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294694.347000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294694.361000] input: PC Speaker as /class/input/input4
[4294694.465000] ieee1394: Initialized config rom entry `ip1394'
[4294694.505000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294694.505000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294694.767000] parport: PnPBIOS parport detected.
[4294694.767000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294694.794000] Real Time Clock Driver v1.12
[4294694.811000] Floppy drive(s): fd0 is 1.44M
[4294694.837000] FDC 0 is a post-1991 82077
[4294694.866000] ieee80211_crypt: registered algorithm 'NULL'
[4294694.868000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294694.868000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294694.906000] islusb: suitable configuration found for net2280 + PCI device
[4294695.337000] usbcore: registered new driver islusb
[4294695.492000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[4294695.494000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294695.495000] cs: IO port probe 0x820-0x8ff: clean.
[4294695.496000] cs: IO port probe 0xc00-0xcf7: clean.
[4294695.497000] cs: IO port probe 0xa00-0xaff: clean.
[4294695.537000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[4294695.539000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294695.540000] cs: IO port probe 0x820-0x8ff: clean.
[4294695.541000] cs: IO port probe 0xc00-0xcf7: clean.
[4294695.542000] cs: IO port probe 0xa00-0xaff: clean.
[4294695.543000] intel8x0_measure_ac97_clock: measured 58240 usecs
[4294695.543000] intel8x0: clocking to 48000
[4294695.548000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294695.548000] **** SET: Misaligned resource pointer: d95c17c2 Type 07 Len 0
[4294695.548000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294695.548000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294695.587000] **** SET: Misaligned resource pointer: d95c17c2 Type 07 Len 0
[4294695.587000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294695.587000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4294695.619000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e8105000-e81057ff]  Max Packet=[2048]
[4294695.627000] e100: eth0: e100_probe: addr 0xe8104000, irq 11, MAC addr 00:02:3F:77:61:1F
[4294696.129000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294696.413000] islusb: Request firmware for 'isl3890usb' failed: -2
[4294696.413000] islusb: unable to boot device
[4294696.417000] islusb: Request firmware for 'isl3890usb' failed: -2
[4294696.417000] islusb: unable to boot device
[4294696.611000] lp0: using parport0 (interrupt-driven).
[4294696.697000] SCSI subsystem initialized
[4294696.708000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294696.708000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294696.708000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294696.786000] fuse init (API version 7.3)
[4294696.846000] Adding 827308k swap on /dev/hda5.  Priority:-1 extents:1 across:827308k
[4294696.968000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f2620000409]
[4294697.043000] EXT3 FS on hda2, internal journal
[4294697.165000] NET: Registered protocol family 17
[4294697.293000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294697.293000] md: bitmap version 4.39
[4294697.969000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294699.873000] NET: Registered protocol family 10
[4294699.873000] lo: Disabled Privacy Extensions
[4294699.873000] IPv6 over IPv4 tunneling driver
[4294700.936000] ACPI: AC Adapter [ACAD] (on-line)
[4294700.959000] ACPI: Battery Slot [BAT1] (battery present)
[4294701.056000] ACPI: Power Button (FF) [PWRF]
[4294701.056000] ACPI: Lid Switch [LID]
[4294701.056000] ACPI: Power Button (CM) [PWBN]
[4294701.204000] ibm_acpi: ec object not found
[4294701.232000] pcc_acpi: loading...
[4294710.705000] eth0: no IPv6 routers present
[4294715.257000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294715.257000] apm: overridden by ACPI.
[4294715.672000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294715.672000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294715.672000] ide: failed opcode was: 0xec
[4294715.735000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294715.735000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294715.735000] ide: failed opcode was: 0xec
[4294716.426000] Bluetooth: Core ver 2.8
[4294716.426000] NET: Registered protocol family 31
[4294716.426000] Bluetooth: HCI device and connection manager initialized
[4294716.426000] Bluetooth: HCI socket layer initialized
[4294716.547000] Bluetooth: L2CAP ver 2.8
[4294716.547000] Bluetooth: L2CAP socket layer initialized
[4294716.575000] Bluetooth: RFCOMM socket layer initialized
[4294716.575000] Bluetooth: RFCOMM TTY layer initialized
[4294716.575000] Bluetooth: RFCOMM ver 1.7
[4295234.564000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4295234.776000] ISO 9660 Extensions: RRIP_1991A
[4295340.799000] islusb: Request firmware for 'isl3890usb' failed: -2
[4295340.799000] islusb: unable to boot device
[4295934.129000] e100: eth0: e100_watchdog: link down
[4295935.430000] usb 2-2: USB disconnect, address 2
[4295938.483000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4295938.483000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4295938.483000] ide: failed opcode was: 0xec
[4295938.508000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4295938.508000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4295938.508000] ide: failed opcode was: 0xec
[4295938.611000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4295938.611000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4295938.611000] ide: failed opcode was: 0xef
[4296173.966000] atkbd.c: Unknown key pressed (translated set 2, code 0x9e on isa0060/serio0).
[4296173.966000] atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
[4296173.980000] atkbd.c: Unknown key released (translated set 2, code 0x9e on isa0060/serio0).
[4296173.980000] atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
[4297754.129000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4297754.329000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4297754.329000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4297754.329000] ide: failed opcode was: 0xef
[4297754.801000] usb 1-2: USB disconnect, address 2
[4297755.020000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4297755.020000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4297755.020000] ide: failed opcode was: 0xec
[4297755.038000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4297755.038000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4297755.038000] ide: failed opcode was: 0xec
[4297755.444000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[4297755.633000] input: Topro USB Mouse as /class/input/input5
[4297755.633000] input: USB HID v1.10 Mouse [Topro USB Mouse] on usb-0000:00:1f.4-2
[4297761.861000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[4297761.984000] islusb: suitable configuration found for net2280 + PCI device
[4297762.714000] islusb: Request firmware for 'isl3890usb' failed: -2
[4297762.714000] islusb: unable to boot device
[4297762.720000] islusb: Request firmware for 'isl3890usb' failed: -2
[4297762.721000] islusb: unable to boot device
[4297782.934000] islusb: Request firmware for 'isl3890usb' failed: -2
[4297782.934000] islusb: unable to boot device
[4297941.751000] atkbd.c: Unknown key pressed (translated set 2, code 0x9f on isa0060/serio0).
[4297941.751000] atkbd.c: Use 'setkeycodes e01f <keycode>' to make it known.
[4297941.762000] atkbd.c: Unknown key released (translated set 2, code 0x9f on isa0060/serio0).
[4297941.762000] atkbd.c: Use 'setkeycodes e01f <keycode>' to make it known.

```

More info on the problem:
Card:
```

Model: DWL-G122       H/W Ver.: A1       F/W Ver.: 3.2.0
P/N DWLG122NA.A1

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETINVEST"
          Mode:Auto  Channel=0  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I don't know what this sit0 is about, but I do have CiscoVPN client installed on the laptop.

ifconfig -a [PS: my ubuntu is brazilian portuguese, and ifconfig was translated. so this is my best effort to get it back to what it REALLY was on english. Of course, I am only translating, so some words may be synonims of the real english config]
```

eth0       Encapsulamento do Link: Ethernet  HW Address 00:02:3F:77:61:1F
          inet adr.: 192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 adr: fe80::202:3fff:fe77:611f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrics:1
          RX packets:18341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12408 errors:0 dropped:0 overruns:0 carrier:0
          colisions:0 txqueuelen:1000
          RX bytes:20990021 (20.0 MiB)  TX bytes:1243191 (1.1 MiB)

eth1       Encapsulamento do Link: Ethernet  HW Address 00:3D:B4:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metrics:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo         Encapsulamento do Link: Local Loopback
          inet adr.: 127.0.0.1  Mask:255.0.0.0
          inet6 adr: ::1/128 Scope:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          RX packets:467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:0
          RX bytes:68357 (66.7 KiB)  TX bytes:68357 (66.7 KiB)

sit0       Encapsulamento do Link: IPv6 over IPv4
          NOARP  MTU:1480  Metrics:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

So, does anyone have any idea on what may be going on? Just to remember, since it is a long post, When I type 

```

sudo ifconfig eth1 up

```

I get this: 
```

SIOCSIFFLAGS: No such file or directory

```

Thanks a lot for your pacience and help,

Dante.

---

### Post by dante.regis on 2006-04-23
just a small addition: 

when I restart my network, this is what I get:
```

sudo /etc/init.d/networking restart

```

```

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:02:3f:77:61:1f
Sending on   LPF/eth0/00:02:3f:77:61:1f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:3d:b4:00:00:00
Sending on   LPF/eth1/00:3d:b4:00:00:00
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:02:3f:77:61:1f
Sending on   LPF/eth0/00:02:3f:77:61:1f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 1622 seconds.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:3d:b4:00:00:00
Sending on   LPF/eth1/00:3d:b4:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                                     [ ok ]

```

---

