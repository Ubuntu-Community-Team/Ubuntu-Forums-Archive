---
title: "Streamzap Remote not initializing for lirc."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by gu014 on 2007-04-29
Hello,
I am trying to install a streamzap remote using the lirc modules for use under mythtv.  I have followed the instructions at
[https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty")

I have slected the 'streamzap' module as i should and when i execute /etc/init.d/lirc start i receive the following:

```
sudo /etc/init.d/lirc start
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.
```

The command ```
sudo lsmod | grep lirc

```

Produces nothing.

Here is dmesg:
```
[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=418ddd56-20ea-498f-818c-0207acc0ef11 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f8160
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee92c0
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee9200
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261856
[    0.000000] On node 0 totalpages: 261759
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254236 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257094
[    0.000000] Kernel command line: root=UUID=418ddd56-20ea-498f-818c-0207acc0ef11 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   38.887247] Console: colour VGA+ 80x25
[   38.887957] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   38.889050] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   38.889153] Checking aperture...
[   38.889156] CPU 0: aperture @ 868000000 size 32 MB
[   38.889158] Aperture too small (32 MB)
[   38.894140] No AGP bridge found
[   38.905469] Memory: 1019364k/1047424k available (2217k kernel code, 27672k reserved, 1162k data, 304k init)
[   38.983938] Calibrating delay using timer specific routine.. 4021.00 BogoMIPS (lpj=8042015)
[   38.983995] Security Framework v1.0.0 initialized
[   38.984001] SELinux:  Disabled at boot.
[   38.984025] Mount-cache hash table entries: 256
[   38.984172] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.984174] CPU: L2 Cache: 512K (64 bytes/line)
[   38.984177] CPU 0/0 -> Node 0
[   38.984197] SMP alternatives: switching to UP code
[   38.984500] Early unpacking initramfs... done
[   39.310383] ACPI: Core revision 20060707
[   39.312717] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   39.358524] Using local APIC timer interrupts.
[   39.408236] result 12558061
[   39.408238] Detected 12.558 MHz APIC timer.
[   39.411453] Brought up 1 CPUs
[   39.411493] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   39.411496] time.c: Detected 2009.287 MHz processor.
[   39.411749] Time: 18:30:09  Date: 03/29/107
[   39.411782] NET: Registered protocol family 16
[   39.411853] ACPI: bus type pci registered
[   39.411859] PCI: Using configuration type 1
[   39.418849] ACPI: Interpreter enabled
[   39.418852] ACPI: Using IOAPIC for interrupt routing
[   39.419388] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   39.419392] PCI: Probing PCI hardware (bus 00)
[   39.422080] PCI: Transparent bridge - 0000:00:09.0
[   39.422140] Boot video device is 0000:02:00.0
[   39.422342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   39.488142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   39.490125] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   39.490440] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   39.490749] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   39.491056] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   39.491379] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   39.491693] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   39.492001] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   39.492310] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   39.492626] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   39.492935] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   39.493245] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   39.493556] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   39.493866] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   39.494184] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   39.494506] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   39.494830] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   39.495187] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   39.495545] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   39.495894] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   39.496242] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   39.496510] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   39.496876] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   39.497244] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   39.497607] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   39.497970] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   39.498332] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   39.498695] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   39.499057] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   39.499425] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   39.499799] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   39.500172] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   39.500544] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   39.503027] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.503041] pnp: PnP ACPI init
[   39.509484] pnp: PnP ACPI: found 14 devices
[   39.509535] PCI: Using ACPI for IRQ routing
[   39.509539] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   39.509613] NET: Registered protocol family 8
[   39.509614] NET: Registered protocol family 20
[   39.510111] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   39.510114] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   39.510117] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   39.510120] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   39.510123] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   39.510126] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   39.510383] PCI: Bridge: 0000:00:09.0
[   39.510386]   IO window: 9000-afff
[   39.510389]   MEM window: fdf00000-fdffffff
[   39.510392]   PREFETCH window: d8000000-dfffffff
[   39.510395] PCI: Bridge: 0000:00:0b.0
[   39.510397]   IO window: 8000-8fff
[   39.510400]   MEM window: fa000000-fcffffff
[   39.510403]   PREFETCH window: c0000000-cfffffff
[   39.510405] PCI: Bridge: 0000:00:0c.0
[   39.510407]   IO window: 7000-7fff
[   39.510410]   MEM window: fde00000-fdefffff
[   39.510412]   PREFETCH window: fdd00000-fddfffff
[   39.510415] PCI: Bridge: 0000:00:0d.0
[   39.510417]   IO window: 6000-6fff
[   39.510420]   MEM window: fdc00000-fdcfffff
[   39.510422]   PREFETCH window: fdb00000-fdbfffff
[   39.510424] PCI: Bridge: 0000:00:0e.0
[   39.510426]   IO window: 5000-5fff
[   39.510429]   MEM window: fda00000-fdafffff
[   39.510432]   PREFETCH window: fd900000-fd9fffff
[   39.510438] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   39.510445] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   39.510450] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   39.510455] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   39.510460] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   39.510496] NET: Registered protocol family 2
[   39.547325] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   39.547547] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   39.548980] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   39.549709] TCP: Hash tables configured (established 131072 bind 65536)
[   39.549713] TCP reno registered
[   39.559376] checking if image is initramfs... it is
[   40.168225] Freeing initrd memory: 7313k freed
[   40.174059] audit: initializing netlink socket (disabled)
[   40.174072] audit(1177871410.244:1): initialized
[   40.174205] VFS: Disk quotas dquot_6.5.1
[   40.174223] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   40.174271] io scheduler noop registered
[   40.174273] io scheduler anticipatory registered
[   40.174275] io scheduler deadline registered
[   40.174286] io scheduler cfq registered (default)
[   48.164509] 0000:00:02.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   48.164523] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   48.164530] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   48.164535] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   48.164542] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   48.164547] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   48.164554] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   48.164559] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   48.164566] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   48.164767] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   48.164785] assign_interrupt_mode Found MSI capability
[   48.164789] Allocate Port Service[0000:00:0b.0:pcie00]
[   48.164848] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   48.164864] assign_interrupt_mode Found MSI capability
[   48.164867] Allocate Port Service[0000:00:0c.0:pcie00]
[   48.164920] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   48.164937] assign_interrupt_mode Found MSI capability
[   48.164939] Allocate Port Service[0000:00:0d.0:pcie00]
[   48.164988] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   48.165005] assign_interrupt_mode Found MSI capability
[   48.165007] Allocate Port Service[0000:00:0e.0:pcie00]
[   48.186500] Real Time Clock Driver v1.12ac
[   48.186539] Linux agpgart interface v0.102 (c) Dave Jones
[   48.186542] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   48.186645] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   48.186783] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   48.187197] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   48.187385] mice: PS/2 mouse device common for all mice
[   48.187850] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   48.188061] input: Macintosh mouse button emulation as /class/input/input0
[   48.188089] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   48.188093] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   48.188251] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   48.191250] serio: i8042 KBD port at 0x60,0x64 irq 1
[   48.191255] serio: i8042 AUX port at 0x60,0x64 irq 12
[   48.191341] TCP cubic registered
[   48.191348] NET: Registered protocol family 1
[   48.191463] ACPI: (supports S0 S1 S3 S4 S5)
[   48.191510]   Magic number: 3:554:545
[   48.191608] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   48.191680] Freeing unused kernel memory: 304k freed
[   48.264479] input: AT Translated Set 2 keyboard as /class/input/input1
[   49.372483] Capability LSM initialized
[   49.402420] ACPI: Fan [FAN] (on)
[   49.405829] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   49.407090] ACPI: Thermal Zone [THRM] (40 C)
[   49.852390] usbcore: registered new interface driver usbfs
[   49.852414] usbcore: registered new interface driver hub
[   49.852434] usbcore: registered new device driver usb
[   49.853149] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   49.853558] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   49.853567] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   49.853581] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.853584] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   49.853723] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   49.853738] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   49.893054] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   49.912499] usb usb1: configuration #1 chosen from 1 choice
[   49.912527] hub 1-0:1.0: USB hub found
[   49.912537] hub 1-0:1.0: 10 ports detected
[   49.948098] SCSI subsystem initialized
[   49.953157] libata version 2.20 loaded.
[   49.964686] ieee1394: Initialized config rom entry `ip1394'
[   50.018845] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   50.018854] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   50.018868] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   50.018871] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   50.018894] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   50.018923] ehci_hcd 0000:00:02.1: debug port 1
[   50.018926] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   50.018937] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   50.018942] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.019023] usb usb2: configuration #1 chosen from 1 choice
[   50.019045] hub 2-0:1.0: USB hub found
[   50.019052] hub 2-0:1.0: 10 ports detected
[   50.062528] Floppy drive(s): fd0 is 1.44M
[   50.104364] FDC 0 is a post-1991 82077
[   50.128656] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   50.128677] NFORCE-CK804: chipset revision 162
[   50.128679] NFORCE-CK804: not 100% native mode: will probe irqs later
[   50.128684] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   50.128693]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   50.128701]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   50.128708] Probing IDE interface ide0...
[   50.865213] hda: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
[   50.969030] hub 2-0:1.0: over-current change on port 9
[   51.072884] hub 2-0:1.0: over-current change on port 10
[   51.480376] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   51.536460] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   51.536959] Probing IDE interface ide1...
[   51.685224] usb 1-1: configuration #1 chosen from 1 choice
[   52.110737] sata_nv 0000:00:07.0: version 3.3
[   52.111299] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   52.111307] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   52.111319] sata_nv 0000:00:07.0: Using ADMA mode
[   52.111334] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   52.111417] ata1: SATA max UDMA/133 cmd 0xffffc2000002e480 ctl 0xffffc2000002e4a0 bmdma 0x000000000001d400 irq 21
[   52.111467] ata2: SATA max UDMA/133 cmd 0xffffc2000002e580 ctl 0xffffc2000002e5a0 bmdma 0x000000000001d408 irq 21
[   52.111477] scsi0 : sata_nv
[   52.423199] ata1: SATA link down (SStatus 0 SControl 300)
[   52.423212] scsi1 : sata_nv
[   52.734810] ata2: SATA link down (SStatus 0 SControl 300)
[   52.736032] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   52.736040] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   52.736051] sata_nv 0000:00:08.0: Using ADMA mode
[   52.736065] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   52.736126] ata3: SATA max UDMA/133 cmd 0xffffc20000030480 ctl 0xffffc200000304a0 bmdma 0x000000000001c000 irq 20
[   52.736170] ata4: SATA max UDMA/133 cmd 0xffffc20000030580 ctl 0xffffc200000305a0 bmdma 0x000000000001c008 irq 20
[   52.736181] scsi2 : sata_nv
[   53.206235] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   53.214362] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   53.214366] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   53.214369] ata3.00: 488397168 sectors, multi 16: LBA48 
[   53.222354] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   53.222356] ata3.00: configured for UDMA/133
[   53.222364] scsi3 : sata_nv
[   53.533809] ata4: SATA link down (SStatus 0 SControl 300)
[   53.533907] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   53.533914] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   53.540430] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   53.540435] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   53.540440] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   53.540449] forcedeth: using HIGHDMA
[   53.552319] hda: ATAPI 63X DVD-ROM drive, 1725kB Cache, UDMA(66)
[   53.552327] Uniform CD-ROM driver Revision: 3.20
[   53.558912] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   53.558924] sda: Write Protect is off
[   53.558926] sda: Mode Sense: 00 3a 00 00
[   53.558939] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.558985] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   53.558993] sda: Write Protect is off
[   53.558995] sda: Mode Sense: 00 3a 00 00
[   53.559006] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.559011]  sda: sda1 sda2 sda3
[   53.579088] sd 2:0:0:0: Attached scsi disk sda
[   53.583073] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   53.761613] Attempting manual resume
[   53.761617] swsusp: Resume From Partition 8:2
[   53.761619] PM: Checking swsusp image.
[   53.761734] PM: Resume from disk failed.
[   53.790028] kjournald starting.  Commit interval 5 seconds
[   53.790038] EXT3-fs: mounted filesystem with ordered data mode.
[   54.061620] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:0a.0
[   54.061754] sata_sil 0000:01:08.0: version 2.2
[   54.062042] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   54.062050] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   54.062071] sata_sil 0000:01:08.0: Applying R_ERR on DMA activate FIS errata fix
[   54.062124] ata5: SATA max UDMA/100 cmd 0xffffc20000034080 ctl 0xffffc2000003408a bmdma 0xffffc20000034000 irq 16
[   54.062150] ata6: SATA max UDMA/100 cmd 0xffffc200000340c0 ctl 0xffffc200000340ca bmdma 0xffffc20000034008 irq 16
[   54.062175] ata7: SATA max UDMA/100 cmd 0xffffc20000034280 ctl 0xffffc2000003428a bmdma 0xffffc20000034200 irq 16
[   54.062201] ata8: SATA max UDMA/100 cmd 0xffffc200000342c0 ctl 0xffffc200000342ca bmdma 0xffffc20000034208 irq 16
[   54.062213] scsi4 : sata_sil
[   54.376768] ata5: SATA link down (SStatus 0 SControl 310)
[   54.376785] scsi5 : sata_sil
[   54.688369] ata6: SATA link down (SStatus 0 SControl 310)
[   54.688386] scsi6 : sata_sil
[   54.999979] ata7: SATA link down (SStatus 0 SControl 310)
[   54.999996] scsi7 : sata_sil
[   55.311588] ata8: SATA link down (SStatus 0 SControl 310)
[   55.312354] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   55.312363] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   55.365554] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fdffe000-fdffe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   55.370961] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   55.370967] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   55.370998] skge 1.9 addr 0xfdff8000 irq 18 chip Yukon-Lite rev 9
[   55.371088] skge eth1: addr 00:01:29:d4:fc:ff
[   56.645991] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200004b4b1]
[   60.400191] skge eth1: enabling interface
[   61.786685] NET: Registered protocol family 17
[   62.017055] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.019876] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.156172] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   62.156203] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   62.306996] Linux video capture interface: v2.00
[   62.342966] ivtv:  ==================== START INIT IVTV ====================
[   62.342970] ivtv:  version 0.10.1 (tagged release) loading
[   62.342972] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 
[   62.342974] ivtv:  In case of problems please include the debug info between
[   62.342976] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   62.342978] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   62.343084] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   62.343124] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   62.343133] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   62.574873] input: PC Speaker as /class/input/input2
[   62.657038] irda_init()
[   62.657057] NET: Registered protocol family 23
[   62.717509] nvidia: module license 'NVIDIA' taints kernel.
[   63.078269] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   63.293471] ivtv0: Encoder revision: 0x02050032
[   63.293474] ivtv0: Recommended firmware version is 0x02060039.
[   63.315096] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   63.355662] tveeprom 2-0050: Hauppauge model 26152, rev C599, serial# 8961500
[   63.355665] tveeprom 2-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   63.355668] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   63.355670] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   63.355673] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   63.355675] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[   63.355678] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   63.355680] ivtv0: reopen i2c bus for IR-blaster support
[   63.426732] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   63.577676] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   66.454508] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   66.536044] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   66.576312] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   66.576626] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   66.576960] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   66.577169] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   66.577382] tuner 2-0061: type set to 50 (TCL 2002N)
[   66.898443] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   66.898534] ivtv:  ======================  NEXT CARD  ======================
[   66.898537] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   66.898873] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   66.898881] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   66.898891] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   67.531062] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   67.747922] ivtv1: Encoder revision: 0x02050032
[   67.747926] ivtv1: Recommended firmware version is 0x02060039.
[   67.756024] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   67.778017] cx25840 3-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #1)
[   72.623712] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   72.728755] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   72.800186] tveeprom 3-0050: Hauppauge model 26132, rev F1B2, serial# 9851812
[   72.800190] tveeprom 3-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   72.800194] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[   72.800196] tveeprom 3-0050: audio processor is CX25841 (idx 35)
[   72.800199] tveeprom 3-0050: decoder processor is CX25841 (idx 28)
[   72.800201] tveeprom 3-0050: has no radio, has IR receiver, has IR transmitter
[   72.800204] ivtv1: Autodetected Hauppauge WinTV PVR-150
[   72.800206] ivtv1: reopen i2c bus for IR-blaster support
[   72.848139] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   72.974034] cx25840 3-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #1)
[   75.817074] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   75.878040] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   75.932291] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   75.932622] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   75.932953] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   75.933173] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   75.933377] tuner 3-0061: type set to 50 (TCL 2002N)
[   76.250782] ivtv1: Initialized Hauppauge WinTV PVR-150, card #1
[   76.250923] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   76.250932] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   76.251090] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   76.252266] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   76.252270] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 22
[   76.252295] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   76.322805] ivtv:  ====================  END INIT IVTV  ====================
[   76.636822] intel8x0_measure_ac97_clock: measured 54708 usecs
[   76.636827] intel8x0: clocking to 46893
[   76.749286] fuse init (API version 7.8)
[   76.802766] lp: driver loaded but no devices found
[   76.873630] Adding 1951888k swap on /dev/disk/by-uuid/f5ad62fa-22ff-4077-b81b-37cc7a2ee0e7.  Priority:-1 extents:1 across:1951888k
[   76.969031] EXT3 FS on sda1, internal journal
[   77.199319] NET: Registered protocol family 10
[   77.199419] lo: Disabled Privacy Extensions
[   77.199738] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   77.234934] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   77.235084] SGI XFS Quota Management subsystem
[   77.289374] XFS mounting filesystem sda3
[   77.374826] Ending clean XFS mount for filesystem: sda3
[   82.638708] No dock devices found.
[   82.698573] Using specific hotkey driver
[   82.715837] ibm_acpi: ec object not found
[   82.767814] input: Power Button (FF) as /class/input/input4
[   82.771769] ACPI: Power Button (FF) [PWRF]
[   82.798189] input: Power Button (CM) as /class/input/input5
[   82.802067] ACPI: Power Button (CM) [PWRB]
[   82.883996] pcc_acpi: loading...
[   83.066349] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   83.071056] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   88.166507] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 2:00.0] forgot to specify physical device; fix it!
[   88.168991] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 2:00.0] forgot to specify physical device; fix it!
[   88.171414] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 2:00.0] forgot to specify physical device; fix it!
[   88.850508] ppdev: user-space parallel port driver
[   99.704454] Bluetooth: Core ver 2.11
[   99.704508] NET: Registered protocol family 31
[   99.704510] Bluetooth: HCI device and connection manager initialized
[   99.704513] Bluetooth: HCI socket layer initialized
[   99.859508] Bluetooth: L2CAP ver 2.8
[   99.859512] Bluetooth: L2CAP socket layer initialized
[   99.881640] Bluetooth: RFCOMM socket layer initialized
[   99.881654] Bluetooth: RFCOMM TTY layer initialized
[   99.881656] Bluetooth: RFCOMM ver 1.8
[  102.504416] eth0: no IPv6 routers present
```

Judging by the above errors it appears that the i2c module is being used somehow??

I do not know where to go from here so i was hoping someone might be able to offer any suggestion.  Any help would be appreciated.  Thank you.

---

