---
title: "Laptop (HP Pavilion zx5000) sound problems in DD"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by BlackOcellaris on 2006-06-19
I originally had Breezy installed and loved it.  Now I feel I've made a huge mistake by upgrading to DD as I've had nothing but problems.  I've worked most of them out, but the sound problem still lingers.

I did a upgrade through the packet manager to update my system from 5.10 to 6.06.  And then the sound just stopped working.  It works when I start up my system and login.  But after I open a file with sound (mp3, video, etc...) it just stops.  No support from headphones or anything.

I've gone through the forums and the wiki, maybe I missed something, but frustration has led me here to post.  Thank you if anyone can help.

aplay -l
> 
harvey@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/version
> 
harvey@ubuntu:~$ cat /proc/version
Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006


dsmesg
> 
harvey@ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff70000 - 000000001ff7d000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff7d000 - 000000001ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6570
[17179569.184000] On node 0 totalpages: 130928
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126832 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6600
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1ff79158
[17179569.184000] ACPI: FADT (v001 HP     Chinook  0x06040000 ATI  0x000f4240) @ 0x1ff7ce7d
[17179569.184000] ACPI: SSDT (v001 PTLTD  ACPIPST1 0x06040000  LTP 0x00000001) @ 0x1ff7cef1
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1ff7cfa6
[17179569.184000] ACPI: DSDT (v001     HP    SB200 0x06040000 INTL 0x20030509) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro vga=771 quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 3067.062 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour dummy device 80x25
[17179570.648000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.648000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.660000] Memory: 508340k/523712k available (1976k kernel code, 14796k reserved, 606k data, 288k init, 0k highmem)
[17179570.660000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.740000] Calibrating delay using timer specific routine.. 6137.82 BogoMIPS (lpj=12275645)
[17179570.740000] Security Framework v1.0.0 initialized
[17179570.740000] SELinux:  Disabled at boot.
[17179570.740000] Mount-cache hash table entries: 512
[17179570.740000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.740000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.740000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.740000] CPU: L2 cache: 512K
[17179570.740000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179570.740000] mtrr: v2.0 (20020519)
[17179570.740000] CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
[17179570.740000] Enabling fast FPU save and restore... done.
[17179570.740000] Enabling unmasked SIMD FPU exception support... done.
[17179570.740000] Checking 'hlt' instruction... OK.
[17179570.756000] checking if image is initramfs... it is
[17179571.208000] Freeing initrd memory: 6614k freed
[17179571.220000] ACPI: Looking for DSDT ... not found!
[17179572.052000] ENABLING IO-APIC IRQs
[17179572.052000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.196000] NET: Registered protocol family 16
[17179572.196000] EISA bus registered
[17179572.196000] ACPI: bus type pci registered
[17179572.196000] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
[17179572.196000] PCI: Using configuration type 1
[17179572.196000] ACPI: Subsystem revision 20051216
[17179572.196000] ACPI: Interpreter enabled
[17179572.196000] ACPI: Using IOAPIC for interrupt routing
[17179572.196000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.196000] PCI: Probing PCI hardware (bus 00)
[17179572.196000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.224000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179572.224000] Boot video device is 0000:01:05.0
[17179572.224000] PCI: Transparent bridge - 0000:00:14.4
[17179572.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179572.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179572.224000] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 10 11) *0, disabled.
[17179572.228000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 10 11) *0, disabled.
[17179572.228000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 10 11) *0, disabled.
[17179572.228000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 10 11) *0, disabled.
[17179572.232000] ACPI: Embedded Controller [EC0] (gpe 6) interrupt mode.
[17179572.272000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.272000] pnp: PnP ACPI init
[17179572.296000] pnp: PnP ACPI: found 9 devices
[17179572.296000] PnPBIOS: Disabled by ACPI PNP
[17179572.296000] PCI: Using ACPI for IRQ routing
[17179572.296000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.300000] pnp: 00:06: ioport range 0x200-0x20f has been reserved
[17179572.300000] pnp: 00:06: ioport range 0xc14-0xc14 has been reserved
[17179572.300000] pnp: 00:06: ioport range 0xc50-0xc52 has been reserved
[17179572.300000] pnp: 00:06: ioport range 0xc6c-0xc6c has been reserved
[17179572.300000] PCI: Bridge: 0000:00:01.0
[17179572.300000]   IO window: 9000-9fff
[17179572.300000]   MEM window: e8100000-e81fffff
[17179572.300000]   PREFETCH window: f0000000-f7ffffff
[17179572.300000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179572.300000]   IO window: 0000a800-0000a8ff
[17179572.300000]   IO window: 0000ac00-0000acff
[17179572.300000]   PREFETCH window: 40000000-41ffffff
[17179572.300000]   MEM window: 46000000-47ffffff
[17179572.300000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[17179572.300000]   IO window: 00001400-000014ff
[17179572.300000]   IO window: 00001800-000018ff
[17179572.300000]   PREFETCH window: 42000000-43ffffff
[17179572.300000]   MEM window: 48000000-49ffffff
[17179572.300000] PCI: Bridge: 0000:00:14.4
[17179572.300000]   IO window: a000-afff
[17179572.300000]   MEM window: e8200000-e82fffff
[17179572.300000]   PREFETCH window: 40000000-43ffffff
[17179572.300000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179572.300000] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 16 (level, low) -> IRQ 193
[17179572.300000] audit: initializing netlink socket (disabled)
[17179572.300000] audit(1150715913.300:1): initialized
[17179572.300000] VFS: Disk quotas dquot_6.5.1
[17179572.300000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.300000] Initializing Cryptographic API
[17179572.300000] io scheduler noop registered
[17179572.300000] io scheduler anticipatory registered
[17179572.300000] io scheduler deadline registered
[17179572.300000] io scheduler cfq registered
[17179572.300000] isapnp: Scanning for PnP cards...
[17179572.656000] isapnp: No Plug & Play device found
[17179572.668000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.676000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.680000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.680000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.684000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.684000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.688000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.688000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.688000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 5 (level, low) -> IRQ 5
[17179572.688000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179572.688000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.688000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.688000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.688000] mice: PS/2 mouse device common for all mice
[17179572.692000] EISA: Probing bus 0 at eisa.0
[17179572.692000] Cannot allocate resource for EISA slot 1
[17179572.692000] Cannot allocate resource for EISA slot 8
[17179572.692000] EISA: Detected 0 cards.
[17179572.692000] NET: Registered protocol family 2
[17179572.732000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.732000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.732000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.732000] TCP: Hash tables configured (established 32768 bind 32768)
[17179572.732000] TCP reno registered
[17179572.732000] TCP bic registered
[17179572.732000] NET: Registered protocol family 1
[17179572.732000] NET: Registered protocol family 8
[17179572.732000] NET: Registered protocol family 20
[17179572.732000] Using IPI Shortcut mode
[17179572.732000] ACPI wakeup devices:
[17179572.732000] ELAN USB0 USB1 USB2 KBC0 MSE0
[17179572.732000] ACPI: (supports S0 S3 S4 S5)
[17179572.732000] Freeing unused kernel memory: 288k freed
[17179572.768000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.772000] vesafb: framebuffer at 0xf0000000, mapped to 0xe0880000, using 937k, total 65536k
[17179572.772000] vesafb: mode is 800x600x8, linelength=800, pages=127
[17179572.772000] vesafb: protected mode interface info at c000:541a
[17179572.772000] vesafb: scrolling: redraw
[17179572.772000] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[17179572.772000] vesafb: Mode is VGA compatible
[17179572.788000] Console: switching to colour frame buffer device 100x37
[17179572.788000] fb0: VESA VGA frame buffer device
[17179573.824000] Capability LSM initialized
[17179573.908000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179573.916000] ACPI: Thermal Zone [THRM] (61 C)
[17179574.388000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179574.388000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179574.388000] ATIIXP: chipset revision 0
[17179574.388000] ATIIXP: not 100% native mode: will probe irqs later
[17179574.388000]     ide0: BM-DMA at 0x8060-0x8067, BIOS settings: hda:DMA, hdb:pio
[17179574.388000]     ide1: BM-DMA at 0x8068-0x806f, BIOS settings: hdc:DMA, hdd:pio
[17179574.388000] Probing IDE interface ide0...
[17179574.676000] hda: IC25N060ATMR04-0, ATA DISK drive
[17179575.348000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.368000] Probing IDE interface ide1...
[17179576.104000] hdc: HL-DT-ST DVD+RW GCA-4040N, ATAPI CD/DVD-ROM drive
[17179576.440000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.448000] hda: max request size: 1024KiB
[17179576.456000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.456000] hda: cache flushes supported
[17179576.456000]  hda: hda1 hda2 < hda5 >
[17179576.524000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179576.524000] Uniform CD-ROM driver Revision: 3.20
[17179576.892000] usbcore: registered new driver usbfs
[17179576.892000] usbcore: registered new driver hub
[17179576.892000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.892000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.892000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179576.892000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179576.892000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xe8001000
[17179576.900000] hub 1-0:1.0: USB hub found
[17179576.900000] hub 1-0:1.0: 3 ports detected
[17179576.936000] ieee1394: Initialized config rom entry `ip1394'
[17179577.004000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179577.004000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179577.004000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179577.004000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xe8002000
[17179577.012000] hub 2-0:1.0: USB hub found
[17179577.012000] hub 2-0:1.0: 3 ports detected
[17179577.116000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179577.116000] ohci_hcd 0000:02:07.0: OHCI Host Controller
[17179577.116000] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 3
[17179577.116000] ohci_hcd 0000:02:07.0: irq 193, io mem 0xe8206000
[17179577.116000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.116000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179577.176000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[e8208000-e82087ff]  Max Packet=[2048]
[17179577.192000] hub 3-0:1.0: USB hub found
[17179577.192000] hub 3-0:1.0: 3 ports detected
[17179577.296000] ACPI: PCI Interrupt 0000:02:07.1[B] -> GSI 18 (level, low) -> IRQ 209
[17179577.296000] ohci_hcd 0000:02:07.1: OHCI Host Controller
[17179577.296000] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 4
[17179577.296000] ohci_hcd 0000:02:07.1: irq 209, io mem 0xe8207000
[17179577.328000] hub 4-0:1.0: USB hub found
[17179577.328000] hub 4-0:1.0: 2 ports detected
[17179577.432000] ACPI: PCI Interrupt 0000:02:07.2[C] -> GSI 19 (level, low) -> IRQ 201
[17179577.432000] ehci_hcd 0000:02:07.2: EHCI Host Controller
[17179577.456000] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
[17179577.456000] ehci_hcd 0000:02:07.2: irq 201, io mem 0xe8208c00
[17179577.456000] ehci_hcd 0000:02:07.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.456000] hub 5-0:1.0: USB hub found
[17179577.456000] hub 5-0:1.0: 5 ports detected
[17179577.704000] Attempting manual resume
[17179577.760000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179577.760000] EXT3-fs: write access will be enabled during recovery.
[17179578.448000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[413f02005e5a003d]
[17179583.636000] EXT3-fs: hda1: orphan cleanup on readonly fs
[17179583.636000] ext3_orphan_cleanup: deleting unreferenced inode 6504601
[17179583.636000] EXT3-fs: hda1: 1 orphan inode deleted
[17179583.636000] EXT3-fs: recovery complete.
[17179583.636000] kjournald starting.  Commit interval 5 seconds
[17179583.668000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.964000] input: PS/2 Mouse as /class/input/input1
[17179596.964000] Real Time Clock Driver v1.12
[17179596.980000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.984000] agpgart: Detected Ati IGP9100/M chipset
[17179596.984000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[17179596.988000] agpgart: AGP aperture is 32M @ 0xea000000
[17179597.004000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179597.004000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006b]
[17179597.004000] Yenta: Enabling burst memory read transactions
[17179597.004000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179597.004000] Yenta: Routing CardBus interrupts to PCI
[17179597.004000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[17179597.020000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.188000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 5 (level, low) -> IRQ 5
[17179597.236000] Yenta: ISA IRQ mask 0x0ed8, PCI irq 185
[17179597.236000] Socket status: 30000086
[17179597.236000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #06
[17179597.236000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179597.236000] cs: IO port probe 0xa000-0xafff: clean.
[17179597.236000] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[17179597.236000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179597.244000] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 16 (level, low) -> IRQ 193
[17179597.244000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006b]
[17179597.244000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179597.244000] Yenta: Routing CardBus interrupts to PCI
[17179597.244000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[17179597.280000] input: PC Speaker as /class/input/input3
[17179597.304000] 8139too Fast Ethernet driver 0.9.27
[17179597.476000] Yenta: ISA IRQ mask 0x0ed8, PCI irq 193
[17179597.476000] Socket status: 30000006
[17179597.476000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179597.476000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179597.476000] cs: IO port probe 0xa000-0xafff: clean.
[17179597.476000] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[17179597.476000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179597.484000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.488000] ts: Compaq touchscreen protocol output
[17179597.576000] parport: PnPBIOS parport detected.
[17179597.576000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[17179597.712000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179597.712000] eth0: RealTek RTL8139 at 0xe0adc800, 00:02:3f:6b:49:22, IRQ 201
[17179597.712000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179597.716000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 5 (level, low) -> IRQ 5
[17179597.720000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179598.840000] eth0: link down
[17179599.204000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[17179599.204000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
[17179599.208000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.208000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[17179599.208000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
[17179599.208000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.912000] NET: Registered protocol family 17
[17179600.508000] floppy0: no floppy controllers found
[17179600.844000] lp0: using parport0 (interrupt-driven).
[17179600.916000] SCSI subsystem initialized
[17179600.936000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179600.936000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179600.936000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179600.996000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1 across:1510068k
[17179601.096000] EXT3 FS on hda1, internal journal
[17179601.244000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179601.244000] md: bitmap version 4.39
[17179601.948000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179602.616000] cdrom: open failed.
[17179603.448000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179603.568000] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[17179603.568000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179603.576000] ndiswrapper: using irq 209
[17179604.844000] wlan0: vendor: ''
[17179604.844000] wlan0: ndiswrapper ethernet device 00:90:4b:4d:07:f4 using driver bcmwl5, 14E4:4320:103C:12F4.5.conf
[17179604.844000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179607.024000] NET: Registered protocol family 10
[17179607.028000] lo: Disabled Privacy Extensions
[17179607.028000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179607.028000] IPv6 over IPv4 tunneling driver
[17179610.660000] ACPI: AC Adapter [ACAD] (on-line)
[17179610.744000] ACPI: Battery Slot [BAT1] (battery present)
[17179610.816000] ACPI: Power Button (FF) [PWRF]
[17179610.816000] ACPI: Lid Switch [LID]
[17179610.816000] ACPI: Power Button (CM) [PWRB]
[17179610.924000] ibm_acpi: ec object not found
[17179610.956000] pcc_acpi: loading...
[17179611.056000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179611.504000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179617.576000] ppdev: user-space parallel port driver
[17179617.596000] wlan0: no IPv6 routers present
[17179618.556000] [drm] Initialized drm 1.0.1 20051102
[17179618.568000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179618.572000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179619.476000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179619.476000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179619.476000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
[17179619.780000] [drm] Setting GART location based on new memory map
[17179619.780000] [drm] Loading R200 Microcode
[17179619.780000] [drm] writeback test succeeded in 1 usecs
[17179620.480000] apm: BIOS not found.
[17179621.016000] Bluetooth: Core ver 2.8
[17179621.016000] NET: Registered protocol family 31
[17179621.016000] Bluetooth: HCI device and connection manager initialized
[17179621.016000] Bluetooth: HCI socket layer initialized
[17179621.032000] Bluetooth: L2CAP ver 2.8
[17179621.032000] Bluetooth: L2CAP socket layer initialized
[17179621.036000] Bluetooth: RFCOMM socket layer initialized
[17179621.036000] Bluetooth: RFCOMM TTY layer initialized
[17179621.036000] Bluetooth: RFCOMM ver 1.7


lspci
> 
harvey@ubuntu:~$ lspci
d0000:00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
0000:02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
0000:02:07.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


---

