---
title: "PRoblems with Nokia n70 and Kmobile"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by pfwd.tech on 2007-09-30
Hi i have read a few threads which seem to be hitting brick wall with this.  I too am not sure how to get this to work.  
I have a Nokia N70 and would like to access my images/video and SMS.  I can't get see a usb device when i run dmesg.  This is what i get:
```
[    0.000000] copy_e820_map() start: 000000007ffe0000 size: 0000000000020000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff90000 (usable)
[    0.000000]  BIOS-e820: 000000007ff90000 - 000000007ff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff9e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524176) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524176
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524176
[    0.000000] On node 0 totalpages: 524176
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292497 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa980
[    0.000000] ACPI: RSDT (v001 KOZIRO FRONTIER 0x01000730 MSFT 0x00000097) @ 0x7ff90000
[    0.000000] ACPI: FADT (v002 MSTEST OEMFACP  0x01000730 MSFT 0x00000097) @ 0x7ff90200
[    0.000000] ACPI: MADT (v001 MSTEST OEMAPIC  0x01000730 MSFT 0x00000097) @ 0x7ff90390
[    0.000000] ACPI: MCFG (v001 MSTEST OEMMCFG  0x01000730 MSFT 0x00000097) @ 0x7ff90400
[    0.000000] ACPI: SLIC (v001 KOZIRO FRONTIER 0x01000730 MSFT 0x00000097) @ 0x7ff90440
[    0.000000] ACPI: OEMB (v001 MSTEST AMI_OEM  0x01000730 MSFT 0x00000097) @ 0x7ff9e040
[    0.000000] ACPI: HPET (v001 MSTEST OEMHPET  0x01000730 MSFT 0x00000097) @ 0x7ff99550
[    0.000000] ACPI: DSDT (v001  A0545 A0545000 0x00000000 INTL 0x20060113) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] Detected 2135.188 MHz processor.
[   24.346947] Built 1 zonelists.  Total pages: 520081
[   24.346950] Kernel command line: root=UUID=6a4e07f4-1b96-43f8-94ea-b5064dd33d84 ro quiet splash
[   24.347062] mapped APIC to ffffd000 (fee00000)
[   24.347063] mapped IOAPIC to ffffc000 (fec00000)
[   24.347066] Enabling fast FPU save and restore... done.
[   24.347067] Enabling unmasked SIMD FPU exception support... done.
[   24.347073] Initializing CPU#0
[   24.347113] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   24.347863] Console: colour VGA+ 80x25
[   24.348059] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.348285] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.407032] Memory: 2067640k/2096704k available (1993k kernel code, 27728k reserved, 900k data, 328k init, 1179200k highmem)
[   24.407039] virtual kernel memory layout:
[   24.407040]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   24.407041]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.407042]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.407043]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.407044]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   24.407044]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   24.407045]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   24.407048] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.407159] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.407163] hpet0: 3 64-bit timers, 14318180 Hz
[   24.408166] Using HPET for base-timer
[   24.487060] Calibrating delay using timer specific routine.. 4273.14 BogoMIPS (lpj=8546288)
[   24.487091] Security Framework v1.0.0 initialized
[   24.487096] SELinux:  Disabled at boot.
[   24.487108] Mount-cache hash table entries: 512
[   24.487211] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   24.487217] monitor/mwait feature present.
[   24.487218] using mwait in idle threads.
[   24.487222] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.487223] CPU: L2 cache: 2048K
[   24.487225] CPU: Physical Processor ID: 0
[   24.487226] CPU: Processor Core ID: 0
[   24.487228] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   24.487235] Compat vDSO mapped to ffffe000.
[   24.487238] Remapping vsyscall page to ffffe000
[   24.487247] Checking 'hlt' instruction... OK.
[   24.503126] SMP alternatives: switching to UP code
[   24.503415] Early unpacking initramfs... done
[   24.751007] ACPI: Core revision 20060707
[   24.751206] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.782907] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
[   24.782921] SMP alternatives: switching to SMP code
[   24.782976] Booting processor 1/1 eip 3000
[   24.793306] Initializing CPU#1
[   24.870567] Calibrating delay using timer specific routine.. 4270.17 BogoMIPS (lpj=8540348)
[   24.870572] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   24.870575] monitor/mwait feature present.
[   24.870578] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.870579] CPU: L2 cache: 2048K
[   24.870581] CPU: Physical Processor ID: 0
[   24.870582] CPU: Processor Core ID: 1
[   24.870583] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   24.870977] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
[   24.870992] Total of 2 processors activated (8543.31 BogoMIPS).
[   24.871130] ENABLING IO-APIC IRQs
[   24.871290] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.034358] checking TSC synchronization across 2 CPUs: passed.
[    0.003993] Brought up 2 CPUs
[    0.184888] migration_cost=30
[    0.185090] Booting paravirtualized kernel on bare hardware
[    0.185149] Time: 10:56:17  Date: 08/30/107
[    0.185168] NET: Registered protocol family 16
[    0.185229] EISA bus registered
[    0.185232] ACPI: bus type pci registered
[    0.185340] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.185341] PCI: Using configuration type 1
[    0.185342] Setting up standard PCI resources
[    0.198256] ACPI: Interpreter enabled
[    0.198258] ACPI: Using IOAPIC for interrupt routing
[    0.198822] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.198828] PCI: Probing PCI hardware (bus 00)
[    0.199520] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.199524] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.199692] Boot video device is 0000:01:00.0
[    0.200226] PCI: Transparent bridge - 0000:00:1e.0
[    0.200278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.218787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.219032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.222998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.223569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.223819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.226663] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.226886] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.227115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.227335] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.227555] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.227777] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.227998] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.228217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.228309] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.228318] pnp: PnP ACPI init
[    0.232086] pnp: PnP ACPI: found 15 devices
[    0.232089] PnPBIOS: Disabled by ACPI PNP
[    0.232123] PCI: Using ACPI for IRQ routing
[    0.232125] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.242271] NET: Registered protocol family 8
[    0.242273] NET: Registered protocol family 20
[    0.242863] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[    0.243088] PCI: Bridge: 0000:00:01.0
[    0.243090]   IO window: 7000-9fff
[    0.243093]   MEM window: ff700000-ff7fffff
[    0.243096]   PREFETCH window: bfe00000-dfdfffff
[    0.243099] PCI: Bridge: 0000:00:1c.0
[    0.243100]   IO window: disabled.
[    0.243103]   MEM window: disabled.
[    0.243106]   PREFETCH window: dfe00000-dfefffff
[    0.243110] PCI: Bridge: 0000:00:1c.3
[    0.243112]   IO window: b000-bfff
[    0.243116]   MEM window: ff900000-ff9fffff
[    0.243119]   PREFETCH window: disabled.
[    0.243123] PCI: Bridge: 0000:00:1c.4
[    0.243125]   IO window: a000-afff
[    0.243129]   MEM window: ff800000-ff8fffff
[    0.243131]   PREFETCH window: disabled.
[    0.243135] PCI: Bridge: 0000:00:1e.0
[    0.243136]   IO window: disabled.
[    0.243139]   MEM window: disabled.
[    0.243142]   PREFETCH window: disabled.
[    0.243154] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.243157] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.243171] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.243175] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.243189] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.243193] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.243206] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    0.243210] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.243219] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.243238] NET: Registered protocol family 2
[    0.287901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.287989] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.288363] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.288535] TCP: Hash tables configured (established 131072 bind 65536)
[    0.288537] TCP reno registered
[    0.302033] checking if image is initramfs... it is
[    0.791384] Freeing initrd memory: 6788k freed
[    0.791837] audit: initializing netlink socket (disabled)
[    0.791848] audit(1191149777.460:1): initialized
[    0.791920] highmem bounce pool size: 64 pages
[    0.791980] VFS: Disk quotas dquot_6.5.1
[    0.791994] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.792030] io scheduler noop registered
[    0.792032] io scheduler anticipatory registered
[    0.792033] io scheduler deadline registered
[    0.792041] io scheduler cfq registered (default)
[    0.955568] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.955596] assign_interrupt_mode Found MSI capability
[    0.955598] Allocate Port Service[0000:00:01.0:pcie00]
[    0.955663] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.955696] assign_interrupt_mode Found MSI capability
[    0.955698] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.955723] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.955798] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.955831] assign_interrupt_mode Found MSI capability
[    0.955833] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.955856] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.955932] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.955966] assign_interrupt_mode Found MSI capability
[    0.955967] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.955990] Allocate Port Service[0000:00:1c.4:pcie02]
[    0.956110] isapnp: Scanning for PnP cards...
[    1.308492] isapnp: No Plug & Play device found
[    1.324440] Real Time Clock Driver v1.12ac
[    1.324562] hpet_resources: 0xfed00000 is busy
[    1.324577] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.324681] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.325119] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.325290] mice: PS/2 mouse device common for all mice
[    1.325714] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.325827] input: Macintosh mouse button emulation as /class/input/input0
[    1.325856] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.325859] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.326046] PNP: No PS/2 controller found. Probing ports directly.
[    1.328427] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.328430] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.328518] EISA: Probing bus 0 at eisa.0
[    1.328539] Cannot allocate resource for EISA slot 7
[    1.328540] Cannot allocate resource for EISA slot 8
[    1.328542] EISA: Detected 0 cards.
[    1.358631] TCP cubic registered
[    1.358638] NET: Registered protocol family 1
[    1.358654] Starting balanced_irq
[    1.358659] Using IPI No-Shortcut mode
[    1.358746] ACPI: (supports S0 S1 S3 S4 S5)
[    1.358781]   Magic number: 7:224:933
[    1.358953] Freeing unused kernel memory: 328k freed
[    1.362252] Time: tsc clocksource has been installed.
[    2.512800] Capability LSM initialized
[    2.542903] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[    2.543290] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[    2.543359] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.543365] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.814687] usbcore: registered new interface driver usbfs
[    2.814704] usbcore: registered new interface driver hub
[    2.814722] usbcore: registered new device driver usb
[    2.815299] USB Universal Host Controller Interface driver v3.0
[    2.815329] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.815337] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    2.815340] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.815429] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.815453] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[    2.815524] usb usb1: configuration #1 chosen from 1 choice
[    2.815542] hub 1-0:1.0: USB hub found
[    2.815546] hub 1-0:1.0: 2 ports detected
[    2.846358] SCSI subsystem initialized
[    2.874216] libata version 2.20 loaded.
[    2.920495] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[    2.920505] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    2.920508] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.920527] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.920551] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e000
[    2.920620] usb usb2: configuration #1 chosen from 1 choice
[    2.920641] hub 2-0:1.0: USB hub found
[    2.920645] hub 2-0:1.0: 2 ports detected
[    2.932910] Floppy drive(s): fd0 is 1.44M
[    2.952001] FDC 0 is a post-1991 82077
[    3.028161] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.028170] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.028174] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.028195] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.028220] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000d480
[    3.028303] usb usb3: configuration #1 chosen from 1 choice
[    3.028335] hub 3-0:1.0: USB hub found
[    3.028339] hub 3-0:1.0: 2 ports detected
[    3.135987] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[    3.135995] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.135999] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.136018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.136043] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d800
[    3.136127] usb usb4: configuration #1 chosen from 1 choice
[    3.136149] hub 4-0:1.0: USB hub found
[    3.136155] hub 4-0:1.0: 2 ports detected
[    3.164068] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.243862] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    3.243870] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.243873] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.243893] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.243917] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d880
[    3.244001] usb usb5: configuration #1 chosen from 1 choice
[    3.244025] hub 5-0:1.0: USB hub found
[    3.244030] hub 5-0:1.0: 2 ports detected
[    3.338878] usb 1-1: configuration #1 chosen from 1 choice
[    3.352069] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[    3.352079] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.352083] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.352106] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.352133] ehci_hcd 0000:00:1a.7: debug port 1
[    3.352139] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.352144] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xffaffc00
[    3.356013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.356065] usb usb6: configuration #1 chosen from 1 choice
[    3.356084] hub 6-0:1.0: USB hub found
[    3.356088] hub 6-0:1.0: 4 ports detected
[    3.463544] r8169 Gigabit Ethernet driver 2.2LK loaded
[    3.463567] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[    3.463590] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    3.463753] eth0: RTL8168b/8111b at 0xf8874000, 00:1a:92:cb:2d:07, IRQ 17
[    3.470561] ahci 0000:02:00.0: version 2.1
[    3.470576] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.470583] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.470586] ACPI: PCI Interrupt 0000:02:00.0[A] -> <6>ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.470590] GSI 16 (level, low) -> IRQ 16
[    3.470606] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.470630] ehci_hcd 0000:00:1d.7: debug port 1
[    3.470634] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.470639] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaff800
[    3.474511] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.474565] usb usb7: configuration #1 chosen from 1 choice
[    3.474584] hub 7-0:1.0: USB hub found
[    3.474588] hub 7-0:1.0: 6 ports detected
[    3.740601] usb 1-1: USB disconnect, address 2
[    3.740747] usbcore: registered new interface driver libusual
[    4.110958] usb 6-1: new high speed USB device using ehci_hcd and address 2
[    4.248741] usb 6-1: configuration #1 chosen from 1 choice
[    4.251722] Initializing USB Mass Storage driver...
[    4.472009] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    4.472019] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.472022] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.472098] ata1: SATA max UDMA/133 cmd 0xf88b8100 ctl 0x00000000 bmdma 0x00000000 irq 16
[    4.472157] ata2: SATA max UDMA/133 cmd 0xf88b8180 ctl 0x00000000 bmdma 0x00000000 irq 16
[    4.472163] scsi0 : ahci
[    4.678326] usb 7-2: new high speed USB device using ehci_hcd and address 3
[    4.786198] ata1: SATA link down (SStatus 0 SControl 300)
[    4.786210] scsi1 : ahci
[    4.818543] usb 7-2: configuration #1 chosen from 1 choice
[    4.818868] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.818896] usb-storage: device found at 2
[    4.818898] usb-storage: waiting for device to settle before scanning
[    4.818924] scsi3 : SCSI emulation for USB Mass Storage devices
[    4.818951] usb-storage: device found at 3
[    4.818952] usb-storage: waiting for device to settle before scanning
[    4.818958] usbcore: registered new interface driver usb-storage
[    4.818960] USB Mass Storage support registered.
[    5.058193] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.095734] ata2: SATA link down (SStatus 0 SControl 300)
[    5.096658] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[    5.096664] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 18
[    5.096682] PCI: Setting latency timer of device 0000:02:00.1 to 64
[    5.096708] ata3: PATA max UDMA/100 cmd 0x0001ac00 ctl 0x0001a882 bmdma 0x0001a400 irq 18
[    5.096730] ata4: PATA max UDMA/100 cmd 0x0001a800 ctl 0x0001a482 bmdma 0x0001a408 irq 18
[    5.096740] scsi4 : pata_jmicron
[    5.235551] usb 3-1: configuration #1 chosen from 1 choice
[    5.245941] usbcore: registered new interface driver hiddev
[    5.261558] input: Logitech USB Receiver as /class/input/input1
[    5.261566] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1
[    5.261719] ata3.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[    5.261723] ata3.00: ATA-7: Maxtor 6L200P0, BAH41G10, max UDMA/133
[    5.261725] ata3.00: 398297088 sectors, multi 0: LBA48 
[    5.275786] ata3.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[    5.275789] ata3.00: configured for UDMA/100
[    5.275797] scsi5 : pata_jmicron
[    5.292534] input: Logitech USB Receiver as /class/input/input2
[    5.292562] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[    5.292572] usbcore: registered new interface driver usbhid
[    5.292575] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.444433] ATA: abnormal status 0x7F on port 0x0001a807
[    5.444529] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAH4 PQ: 0 ANSI: 5
[    5.446702] ata_piix 0000:00:1f.2: version 2.10ac1
[    5.446706] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    5.446725] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[    5.446738] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.446758] ata5: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 17
[    5.446777] ata6: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 17
[    5.446783] scsi6 : ata_piix
[    5.612278] ATA: abnormal status 0x7F on port 0x0001ec07
[    5.612289] scsi7 : ata_piix
[    5.776252] ATA: abnormal status 0x7F on port 0x0001e807
[    5.777282] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    5.777298] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[    5.777309] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    5.777328] ata7: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001c880 irq 17
[    5.777349] ata8: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c888 irq 17
[    5.777354] scsi8 : ata_piix
[    5.944904] ATA: abnormal status 0x7F on port 0x0001d407
[    5.944913] scsi9 : ata_piix
[    6.422038] ata8.00: ATAPI, max UDMA/66
[    6.586125] ata8.00: configured for UDMA/66
[    6.587684] scsi 9:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170S  1.00 PQ: 0 ANSI: 5
[    6.595548] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[    6.597792] sda: Write Protect is off
[    6.597794] sda: Mode Sense: 00 3a 00 00
[    6.597809] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.597844] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[    6.597851] sda: Write Protect is off
[    6.597853] sda: Mode Sense: 00 3a 00 00
[    6.597863] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.597866]  sda: sda1 sda2 sda3
[    6.631564] sd 4:0:0:0: Attached scsi disk sda
[    6.634420] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    6.634437] sr 9:0:0:0: Attached scsi generic sg1 type 5
[    6.641097] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.641100] Uniform CD-ROM driver Revision: 3.20
[    6.641133] sr 9:0:0:0: Attached scsi CD-ROM sr0
[    6.896508] Attempting manual resume
[    6.896511] swsusp: Resume From Partition 8:1
[    6.896512] PM: Checking swsusp image.
[    6.896685] PM: Resume from disk failed.
[    6.914254] kjournald starting.  Commit interval 5 seconds
[    6.914262] EXT3-fs: mounted filesystem with ordered data mode.
[    9.833824] usb-storage: device scan complete
[    9.833845] usb-storage: device scan complete
[    9.834551] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[    9.835702] sd 2:0:0:0: Attached scsi disk sdb
[    9.835736] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.869168] scsi 3:0:0:0: Direct-Access     WD       2500JB External  0108 PQ: 0 ANSI: 0
[    9.870274] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[    9.871152] sdc: Write Protect is off
[    9.871154] sdc: Mode Sense: 03 00 00 00
[    9.871155] sdc: assuming drive cache: write through
[    9.872021] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[    9.872899] sdc: Write Protect is off
[    9.872901] sdc: Mode Sense: 03 00 00 00
[    9.872902] sdc: assuming drive cache: write through
[    9.872904]  sdc: sdc1
[    9.873560] sd 3:0:0:0: Attached scsi disk sdc
[    9.873582] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   13.265192] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.267686] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.418599] Linux agpgart interface v0.102 (c) Dave Jones
[   13.420533] agpgart: Detected an Intel 965G Chipset.
[   13.431755] agpgart: AGP aperture is 256M @ 0x0
[   13.474796] iTCO_vendor_support: vendor-support=0
[   13.499711] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   13.499820] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
[   13.499857] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.660280] parport: PnPBIOS parport detected.
[   13.660380] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.802419] input: PC Speaker as /class/input/input3
[   13.973787] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   13.973802] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.533115] fuse init (API version 7.8)
[   14.556182] lp0: using parport0 (interrupt-driven).
[   14.576255] Adding 1052248k swap on /dev/disk/by-uuid/798109f5-3f05-ac74-d7ad-e85dde4b05a0.  Priority:-1 extents:1 across:1052248k
[   14.689936] EXT3 FS on sda2, internal journal
[   14.873032] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   14.928713] NTFS volume version 3.1.
[   16.215534] NET: Registered protocol family 17
[   20.080190] Using specific hotkey driver
[   20.163550] ibm_acpi: ec object not found
[   20.214227] input: Power Button (FF) as /class/input/input4
[   20.214248] ACPI: Power Button (FF) [PWRF]
[   20.214297] input: Power Button (CM) as /class/input/input5
[   20.214310] ACPI: Power Button (CM) [PWRB]
[   20.260850] No dock devices found.
[   20.330558] pcc_acpi: loading...
[   23.827965] r8169: eth0: link up
[   23.827974] r8169: eth0: link up
[   25.946019] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   25.950080] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   25.950168] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   25.968750] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.394902] ppdev: user-space parallel port driver
[   26.923364] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.923367] apm: disabled - APM is not SMP safe.
[   27.233450] [fglrx] total      GART = 130023424
[   27.233456] [fglrx] free       GART = 114032640
[   27.233459] [fglrx] max single GART = 114032640
[   27.233461] [fglrx] total      LFB  = 268304384
[   27.233464] [fglrx] free       LFB  = 250474496
[   27.233466] [fglrx] max single LFB  = 250474496
[   27.233468] [fglrx] total      Inv  = 268435456
[   27.233470] [fglrx] free       Inv  = 268435456
[   27.233473] [fglrx] max single Inv  = 268435456
[   27.233475] [fglrx] total      TIM  = 0
[   27.304604] NET: Registered protocol family 10
[   27.304696] lo: Disabled Privacy Extensions
[   27.525423] Bluetooth: Core ver 2.11
[   27.525473] NET: Registered protocol family 31
[   27.525476] Bluetooth: HCI device and connection manager initialized
[   27.525479] Bluetooth: HCI socket layer initialized
[   27.539590] Bluetooth: L2CAP ver 2.8
[   27.539594] Bluetooth: L2CAP socket layer initialized
[   27.654786] Bluetooth: RFCOMM socket layer initialized
[   27.654794] Bluetooth: RFCOMM TTY layer initialized
[   27.654796] Bluetooth: RFCOMM ver 1.8
[   39.467970] eth0: no IPv6 routers present
[ 1154.250489] usb 4-1: new full speed USB device using uhci_hcd and address 2

```
And Kmobile can't find the device.  
Any ideas?  has any one accomplished this?

---

### Post by pfwd.tech on 2007-10-05
Bumb anyone else have a problem with this?

---

