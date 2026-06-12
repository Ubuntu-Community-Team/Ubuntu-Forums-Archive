---
title: "Pinnacle PCTV Pro remote control"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by mulimans on 2007-08-22
I use Ubuntu 7.04, and with the Tv-card ' Pinnacle Hybrid PCTV pro PCI ' I almost immediately could get picture and sound (last indeed using an audio-cable from the Tv-kaart to the mainboard) 
Only I can't get the remote control working. Have Lirc installed and configured in several ways, but nothing helps. 

Below my dmesg-output. 

I don't understand much of it, but perhaps you can recommend me by means of this result. 

thanks anyway

```

$ dmesg
[    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 (Ubuntu Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000004fefa000 end: 000000004fffa000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000004fffa000 size: 0000000000003000 end: 000000004fffd000 type: 3
[    0.000000] copy_e820_map() start: 000000004fffd000 size: 0000000000001000 end: 000000004fffe000 type: 4
[    0.000000] copy_e820_map() start: 000000004fffe000 size: 0000000000002000 end: 0000000050000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fffa000 (usable)
[    0.000000]  BIOS-e820: 000000004fffa000 - 000000004fffd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004fffd000 - 000000004fffe000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fffe000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 327674) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327674
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327674
[    0.000000] On node 0 totalpages: 327674
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97531 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5650
[    0.000000] ACPI: RSDT (v001 ASUS   KIRIN-P  0x42302e31 MSFT 0x31313031) @ 0x4fffa000
[    0.000000] ACPI: FADT (v001 ASUS   KIRIN-P  0x42302e31 MSFT 0x31313031) @ 0x4fffa0b2
[    0.000000] ACPI: BOOT (v001 ASUS   KIRIN-P  0x42302e31 MSFT 0x31313031) @ 0x4fffa030
[    0.000000] ACPI: MADT (v001 ASUS   KIRIN-P  0x42302e31 MSFT 0x31313031) @ 0x4fffa058
[    0.000000] ACPI: DSDT (v001   ASUS KIRIN-P  0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] Detected 2412.061 MHz processor.
[   17.784262] Built 1 zonelists.  Total pages: 325115
[   17.784267] Kernel command line: root=UUID=bf614ba1-adf9-4bf3-8e4a-28e64e1218a0 ro quiet splash
[   17.784443] mapped APIC to ffffd000 (fee00000)
[   17.784446] mapped IOAPIC to ffffc000 (fec00000)
[   17.784450] Enabling fast FPU save and restore... done.
[   17.784453] Enabling unmasked SIMD FPU exception support... done.
[   17.784467] Initializing CPU#0
[   17.784563] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.786576] Console: colour VGA+ 80x25
[   17.787397] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.788215] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.842473] Memory: 1287836k/1310696k available (2019k kernel code, 21548k reserved, 902k data, 328k init, 393192k highmem)
[   17.842493] virtual kernel memory layout:
[   17.842494]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.842496]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.842497]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.842498]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.842499]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
[   17.842501]       .data : 0xc02f8c85 - 0xc03da6d4   ( 902 kB)
[   17.842502]       .text : 0xc0100000 - 0xc02f8c85   (2019 kB)
[   17.842505] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.902396] Calibrating delay using timer specific routine.. 4826.21 BogoMIPS (lpj=2413107)
[   17.902462] Security Framework v1.0.0 initialized
[   17.902475] SELinux:  Disabled at boot.
[   17.902498] Mount-cache hash table entries: 512
[   17.902718] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   17.902733] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   17.902737] CPU: L2 cache: 512K
[   17.902740] CPU: Hyper-Threading is disabled
[   17.902742] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
[   17.902761] Compat vDSO mapped to ffffe000.
[   17.902767] Remapping vsyscall page to ffffe000
[   17.902783] Checking 'hlt' instruction... OK.
[   17.906546] SMP alternatives: switching to UP code
[   17.906843] Freeing SMP alternatives: 9k freed
[   17.907044] Early unpacking initramfs... done
[   18.256732] ACPI: Core revision 20060707
[   18.257587] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.258735] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   18.258782] Total of 1 processors activated (4826.21 BogoMIPS).
[   18.258933] ENABLING IO-APIC IRQs
[   18.259130] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.370767] Brought up 1 CPUs
[   18.371084] Booting paravirtualized kernel on bare hardware
[   18.371180] Time: 13:26:42  Date: 07/22/107
[   18.371220] NET: Registered protocol family 16
[   18.371341] EISA bus registered
[   18.371347] ACPI: bus type pci registered
[   18.372950] PCI: PCI BIOS revision 2.10 entry at 0xf1070, last bus=2
[   18.372953] PCI: Using configuration type 1
[   18.372955] Setting up standard PCI resources
[   18.380306] ACPI: Interpreter enabled
[   18.380310] ACPI: Using IOAPIC for interrupt routing
[   18.381096] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   18.381354] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   18.381605] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   18.381891] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   18.382133] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   18.382390] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   18.382636] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   18.382909] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   18.383992] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.384000] PCI: Probing PCI hardware (bus 00)
[   18.384370] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   18.384935] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   18.384937] * this clock source is slow. If you are sure your timer does not have
[   18.384938] * this bug, please use "acpi_pm_good" to disable the workaround
[   18.384988] PCI: Enabled i801 SMBus device
[   18.384995] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   18.384999] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   18.385274] Boot video device is 0000:01:00.0
[   18.385564] PCI: Transparent bridge - 0000:00:1e.0
[   18.385595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.460972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   18.462079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   18.470571] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.470585] pnp: PnP ACPI init
[   18.473927] pnp: PnP ACPI: found 14 devices
[   18.473934] PnPBIOS: Disabled by ACPI PNP
[   18.474012] PCI: Using ACPI for IRQ routing
[   18.474016] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.482194] NET: Registered protocol family 8
[   18.482197] NET: Registered protocol family 20
[   18.482488] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   18.482492] pnp: 00:02: ioport range 0xe800-0xe81f has been reserved
[   18.482497] pnp: 00:02: ioport range 0xec00-0xec3f has been reserved
[   18.482500] pnp: 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   18.482516] pnp: 00:0d: ioport range 0xec80-0xec8f has been reserved
[   18.482520] pnp: 00:0d: ioport range 0xecc0-0xeccf has been reserved
[   18.482523] pnp: 00:0d: ioport range 0xecd0-0xecdf has been reserved
[   18.482526] pnp: 00:0d: ioport range 0xecf0-0xecff has been reserved
[   18.482931] PCI: Bridge: 0000:00:01.0
[   18.482933]   IO window: disabled.
[   18.482940]   MEM window: dd000000-dfefffff
[   18.482945]   PREFETCH window: dff00000-f7ffffff
[   18.482951] PCI: Bridge: 0000:00:1e.0
[   18.482955]   IO window: b000-bfff
[   18.482961]   MEM window: db000000-dc7fffff
[   18.482966]   PREFETCH window: disabled.
[   18.482986] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.483027] NET: Registered protocol family 2
[   18.492636] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.492887] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   18.494770] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[   18.495911] TCP: Hash tables configured (established 131072 bind 65536)
[   18.495917] TCP reno registered
[   18.498708] checking if image is initramfs... it is
[   19.130954] Freeing initrd memory: 6758k freed
[   19.131230] Simple Boot Flag at 0x3a set to 0x1
[   19.131537] audit: initializing netlink socket (disabled)
[   19.131571] audit(1187789202.542:1): initialized
[   19.131709] highmem bounce pool size: 64 pages
[   19.131798] VFS: Disk quotas dquot_6.5.1
[   19.131827] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.131898] io scheduler noop registered
[   19.131902] io scheduler anticipatory registered
[   19.131905] io scheduler deadline registered
[   19.131919] io scheduler cfq registered (default)
[   19.132265] isapnp: Scanning for PnP cards...
[   19.488542] isapnp: No Plug & Play device found
[   19.520633] Real Time Clock Driver v1.12ac
[   19.520696] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.520831] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.521768] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.522087] mice: PS/2 mouse device common for all mice
[   19.522858] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.523113] input: Macintosh mouse button emulation as /class/input/input0
[   19.523162] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.523167] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.523447] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.525499] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.525568] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.525664] EISA: Probing bus 0 at eisa.0
[   19.525700] Cannot allocate resource for EISA slot 8
[   19.525702] EISA: Detected 0 cards.
[   19.543385] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.555786] TCP cubic registered
[   19.555795] NET: Registered protocol family 1
[   19.555822] Using IPI No-Shortcut mode
[   19.555893] ACPI: (supports S0 S1 S3 S4 S5)
[   19.555953]   Magic number: 3:418:433
[   19.555967] Time: tsc clocksource has been installed.
[   19.556562] Freeing unused kernel memory: 328k freed
[   20.833001] Capability LSM initialized
[   20.888218] ACPI: Invalid PBLK length [5]
[   21.639318] usbcore: registered new interface driver usbfs
[   21.639357] usbcore: registered new interface driver hub
[   21.639395] usbcore: registered new device driver usb
[   21.640480] USB Universal Host Controller Interface driver v3.0
[   21.640543] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.640557] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.640562] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.640703] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.640731] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   21.640877] usb usb1: configuration #1 chosen from 1 choice
[   21.640915] hub 1-0:1.0: USB hub found
[   21.640926] hub 1-0:1.0: 2 ports detected
[   21.742784] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   21.742800] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.742805] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.742834] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.742862] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d400
[   21.742968] usb usb2: configuration #1 chosen from 1 choice
[   21.742999] hub 2-0:1.0: USB hub found
[   21.743009] hub 2-0:1.0: 2 ports detected
[   21.773625] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.788062] ieee1394: Initialized config rom entry `ip1394'
[   21.844612] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.844627] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.844632] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.844658] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   21.844689] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[   21.844800] usb usb3: configuration #1 chosen from 1 choice
[   21.844830] hub 3-0:1.0: USB hub found
[   21.844840] hub 3-0:1.0: 2 ports detected
[   21.862523] Floppy drive(s): fd0 is 1.44M
[   21.904712] FDC 0 is a National Semiconductor PC87306
[   21.957316] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   21.957338] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.957344] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.957391] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   21.957432] ehci_hcd 0000:00:1d.7: debug port 1
[   21.957445] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   21.957458] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc800000
[   21.961324] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.961430] usb usb4: configuration #1 chosen from 1 choice
[   21.961468] hub 4-0:1.0: USB hub found
[   21.961478] hub 4-0:1.0: 6 ports detected
[   22.071624] SCSI subsystem initialized
[   22.077750] 8139cp 0000:02:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   22.077755] 8139cp 0000:02:0d.0: Try the "8139too" driver instead.
[   22.080416] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[   22.109014] 8139too Fast Ethernet driver 0.9.28
[   22.148156] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[db000000-db0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   22.155304] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 20
[   22.155628] eth0: RealTek RTL8139 at 0xf88ce000, 00:0c:6e:16:80:39, IRQ 20
[   22.155631] eth0:  Identified 8139 chip type 'RTL-8101'
[   22.156254] libata version 2.20 loaded.
[   22.160201] ata_piix 0000:00:1f.1: version 2.10ac1
[   22.160221] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   22.160241] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.160303] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00019400 irq 14
[   22.160348] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00019408 irq 15
[   22.160372] scsi0 : ata_piix
[   22.371045] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   22.371050] ata1.00: ATA-6: ST380023A, 3.33, max UDMA/100
[   22.371054] ata1.00: 156301488 sectors, multi 16: LBA 
[   22.391015] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   22.391020] ata1.00: configured for UDMA/100
[   22.391034] scsi1 : ata_piix
[   22.864182] ata2.00: ATAPI, max UDMA/33
[   22.864186] ata2.01: ATAPI, max UDMA/33
[   23.034921] ata2.00: configured for UDMA/33
[   23.186729] ata2.01: configured for UDMA/33
[   23.186881] scsi 0:0:0:0: Direct-Access     ATA      ST380023A        3.33 PQ: 0 ANSI: 5
[   23.195505] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R5002 1S30 PQ: 0 ANSI: 5
[   23.196017] scsi 1:0:1:0: CD-ROM            ASUS     CD-S400/A        2.2N PQ: 0 ANSI: 5
[   23.221731] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   23.222368] sda: Write Protect is off
[   23.222372] sda: Mode Sense: 00 3a 00 00
[   23.223355] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.224368] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   23.224596] sda: Write Protect is off
[   23.224600] sda: Mode Sense: 00 3a 00 00
[   23.225232] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.225237]  sda: sda1 sda2 < sda5 >
[   23.271400] sd 0:0:0:0: Attached scsi disk sda
[   23.276024] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.276050] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   23.276081] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   23.290394] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.290401] Uniform CD-ROM driver Revision: 3.20
[   23.290657] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.293504] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   23.293750] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   23.412257] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603016c5ebb]
[   23.580633] Attempting manual resume
[   23.580638] swsusp: Resume From Partition 8:5
[   23.580641] PM: Checking swsusp image.
[   23.580998] PM: Resume from disk failed.
[   23.620447] kjournald starting.  Commit interval 5 seconds
[   23.620462] EXT3-fs: mounted filesystem with ordered data mode.
[   34.208458] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.524323] NET: Registered protocol family 17
[   35.973195] iTCO_vendor_support: vendor-support=0
[   35.974475] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   35.974584] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x6460)
[   35.974608] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
[   35.974645] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.989524] intel_rng: FWH not detected
[   36.283164] Linux agpgart interface v0.102 (c) Dave Jones
[   36.307875] agpgart: Detected an Intel 845G Chipset.
[   36.310940] agpgart: AGP aperture is 64M @ 0xf8000000
[   36.331252] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.358256] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.704967] parport: PnPBIOS parport detected.
[   36.705075] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   36.899047] parport0: Printer, HEWLETT-PACKARD DESKJET 815C
[   36.920923] input: PC Speaker as /class/input/input2
[   37.320394] Linux video capture interface: v2.00
[   37.371315] nvidia: module license 'NVIDIA' taints kernel.
[   37.627823] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.628157] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   37.633064] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   37.792805] saa7130/34: v4l2 driver version 0.2.14 loaded
[   37.792886] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
[   37.792897] saa7133[0]: found at 0000:02:0a.0, rev: 209, irq: 22, latency: 64, mmio: 0xdc000000
[   37.792905] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[   37.792916] saa7133[0]: board init: gpio is 600c000
[   37.909187] input: Pinnacle PCTV as /class/input/input4
[   37.909238] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   38.036606] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   38.036624] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2e 01 e5 ff ff
[   38.036639] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e7 ff 21 00 c2
[   38.036654] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff 15 0e 6c a3 eb 03 c4 72 60
[   38.036669] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.036683] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.036698] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.036713] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.104688] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   38.134638] tuner 0-004b: setting tuner address to 61
[   38.161595] tuner 0-004b: type set to tda8290+75a
[   38.228493] tuner 0-004b: setting tuner address to 61
[   38.255452] tuner 0-004b: type set to tda8290+75a
[   38.295355] saa7133[0]: registered device video0 [v4l2]
[   38.295416] saa7133[0]: registered device vbi0
[   38.295453] saa7133[0]: registered device radio0
[   38.307597] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   38.307635] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   38.329084] saa7134 ALSA driver for DMA sound loaded
[   38.329121] saa7133[0]/alsa: saa7133[0] at 0xdc000000 irq 22 registered as card -2
[   38.622896] intel8x0_measure_ac97_clock: measured 51713 usecs
[   38.622901] intel8x0: clocking to 48000
[   38.827650] lp0: using parport0 (interrupt-driven).
[   38.929687] Adding 746980k swap on /dev/disk/by-uuid/4061025c-7cc5-4e74-ae51-9a00a41c3f5c.  Priority:-1 extents:1 across:746980k
[   38.992374] EXT3 FS on sda1, internal journal
[   39.228844] NET: Registered protocol family 10
[   39.228983] lo: Disabled Privacy Extensions
[   45.066871] input: Power Button (FF) as /class/input/input5
[   45.072425] ACPI: Power Button (FF) [PWRF]
[   45.114067] input: Power Button (CM) as /class/input/input6
[   45.119540] ACPI: Power Button (CM) [PWRB]
[   45.142748] Using specific hotkey driver
[   45.172381] No dock devices found.
[   45.224742] ibm_acpi: ec object not found
[   45.360830] pcc_acpi: loading...
[   48.387897] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   48.387920] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   48.387957] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   49.589629] ppdev: user-space parallel port driver
[   50.052034] lirc_dev: IR Remote Control driver registered, at major 61 
[   50.058491] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   51.106508] lirc_serial: auto-detected active low receiver
[   51.106514] lirc_dev: lirc_register_plugin: sample_rate: 0
[   51.826785] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   62.072206] eth0: no IPv6 routers present
[   92.145432] Pinnacle PCTV: unknown key: key=0x35 raw=0x35 down=1
[   92.247278] Pinnacle PCTV: unknown key: key=0x35 raw=0x35 down=0

```

Moreover, shouldn't be there a light on the remote control irrespective if there is no contact with the card? If so, then of course it could be also a failure in the remote control, however, that seems to me not very plausible, because the rc as well as the card just came out of the cover.

---

### Post by deadgobby on 2007-08-22
[https://wiki.ubuntu.com/LircWithPinnaclePCTV?highlight=%28Pinnacle%29](https://wiki.ubuntu.com/LircWithPinnaclePCTV?highlight=%28Pinnacle%29)

Hope this helps out.

Gobby

---

### Post by mulimans on 2007-08-22
I wonder the remote control of the card is serial. I have to put the receiver in the (pci-connected) card with a little pin-plug.
This is the card: 
[IMG]http://data.icecat.biz/img/norm/low/523371-1023.jpg[/IMG]

This is the receiver (a jack connector):
[IMG]http://img291.imageshack.us/img291/6231/hpim357311tv.jpg[/IMG]

And this is a serial-port right?
[IMG]http://tbn0.google.com/images?q=tbn:d_jtMBaKdzT4dM:http://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Serial_port.jpg/250px-Serial_port.jpg[/IMG]

So, does that mean i can't use the control on my linux-system?

---

### Post by deadgobby on 2007-08-22
I have a winfast TV card and same type of hook up for the remote. I could not get the remote to work either.

---

### Post by mulimans on 2007-08-23
I wonder how this type of connection is cold so i can google some important things about it.
The type of the card-connection is cold PCI if i am right. But the connection of the receiver with that little jack in that card, how is cold that? If we know, perhaps the answer can be also found on [http://www.lirc.org/](http://www.lirc.org/)

(Sorry about the next dot-reply. I posted two times accidently, but don't know how to remove it)

---

### Post by mulimans on 2007-08-23
.

---

### Post by popeye737 on 2007-08-24
I have a Pinnacle 310i with the same Remote and IR connection.
In my dmesg I have :     ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0]]
I reach this result after having added the saa7134-dvb module.
In kaffeine adjust the sound level with the remote (Without lirc, but only the sound level works).
at this link [http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers]("http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers") they speak about remotre control for our cards (310i) but I didn't succeed into put my remote in order to work.
here [http://linux.bytesex.org/v4l2/faq.html]("http://linux.bytesex.org/v4l2/faq.html") they say that we can use the IR remote saa7134 without lirc,we have to change the keyboard map (I didn't try).

---

### Post by mulimans on 2007-09-01
Thanks popeye737,

I am trying now the way at [http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers](http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers)
But during following the instructions i got a problem:

First I did: 
$ cat /proc/bus/input/devices
witch gave me the output:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Pinnacle PCTV"
P: Phys=i2c-0/0-0047/ir0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=100003
B: KEY=108fc010 2100802 0 0 0 0 48000 2180 c0000801 9e1680 0 0 4ffc

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0051
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 ts1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

```

Then I did as they asked 
$ irrecord -H dev/input -d /dev/input/event2 /tmp/my-remote

Now LIRC should start giving me instructions to configure my keys.
But instead of that I get the output:

```

Driver `dev/input' not supported.
Supported drivers:
        pinsys

```

I tried also different sort of variants instead of for example 'dev/input', but whit everything i trie i get the same message.

Anyone any idea what to do?

---

