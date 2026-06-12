---
title: "Need Serious Help: Channel tuning problem"
date: 2008-04-30
forum: Mythbuntu
---

### Post by rbrown3 on 2008-04-30
Greetings:

   Things were going very well with my Mythbuntu installation (aside from a few circumstances when the system would hang as described in my previous post). 


   Unfortunately, recently two channels that I watched without problems suddenly stopped coming through. 


   I do not know what caused this. One second the channels were coming in without problems, the next I was seeing snow. I restarted my machine. The problem persists. I re- configured my tuner. The channels never returned.

   The channels are not scrambled channels, and another DVR system that I had built previously tunes into them without problems. I am using the same input source for the two DVRs, so it isn't that.

   I went through the configuration of the Myth backend, thinking maybe that somehow the channel setting was "off". This doesn't appear to be the problem at all.

   I even tried changing TV cards, thinking that somehow my card's tuning system was broken. That wasn't the problem, either.

   Has anyone seen this kind of problem before??? More important: does anyone know how I can fix this problem???

  Thanks in advance for any advice...

---

### Post by rbrown3 on 2008-05-02
Folks:

   I really *do* need help with this problem!

   Surely someone out there has some insights???

---

### Post by Dumdideldum on 2008-05-02
what does /var/log/mythbackend.log say or dmesg ?

Any suspicious error message ?

---

### Post by rbrown3 on 2008-05-06
Greetings:

   There seems to be no file named /var/log/mythbackend.log. It is apparently not being generated. How do I turn this on?

   The dmesg command seems to work, though. It gives an awful lot of information, Whatshould I be looking for there?

  dmesg output is below:

dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=155df5b6-35be-4108-8750-d8dbde5f98b6 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfedf800 (usable)
[    0.000000]  BIOS-e820: 00000000cfedf800 - 00000000cfee0000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851679) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7CD0 checksum 0
[    0.000000] ACPI: RSDP 000F7CD0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT CFEE3040, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CFEE3180, 437B (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: MCFG CFEE7640, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE7540, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT CFEE76C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT CFEE7B50, 02F1 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851679) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   851679
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048189
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1142 pages reserved
[    0.000000]   DMA zone: 2800 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833303 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfedf000 - 00000000cfee0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1030023
[    0.000000] Kernel command line: root=UUID=155df5b6-35be-4108-8750-d8dbde5f98b6 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   43.452622] time.c: Detected 2004.588 MHz processor.
[   43.453823] Console: colour VGA+ 80x25
[   43.453841] Checking aperture...
[   43.453849] Calgary: detecting Calgary via BIOS EBDA area
[   43.453851] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   43.453853] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   43.487531] Placing software IO TLB between 0x104f000 - 0x504f000
[   43.523118] Memory: 4045900k/4980736k available (2274k kernel code, 146856k reserved, 1181k data, 296k init)
[   43.523159] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   43.602385] Calibrating delay using timer specific routine.. 4012.23 BogoMIPS (lpj=8024461)
[   43.602415] Security Framework v1.0.0 initialized
[   43.602421] SELinux:  Disabled at boot.
[   43.602786] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   43.604996] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   43.606046] Mount-cache hash table entries: 256
[   43.606179] CPU: L1 I cache: 32K, L1 D cache: 32K
[   43.606183] CPU: L2 cache: 1024K
[   43.606185] CPU 0/0 -> Node 0
[   43.606187] using mwait in idle threads.
[   43.606189] CPU: Physical Processor ID: 0
[   43.606190] CPU: Processor Core ID: 0
[   43.606196] CPU0: Thermal monitoring enabled (TM2)
[   43.606206] SMP alternatives: switching to UP code
[   43.606492] Early unpacking initramfs... done
[   43.963570] ACPI: Core revision 20070126
[   43.963607] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   44.028737] Using local APIC timer interrupts.
[   44.078547] result 12528666
[   44.078548] Detected 12.528 MHz APIC timer.
[   44.081683] SMP alternatives: switching to SMP code
[   44.081763] Booting processor 1/2 APIC 0x1
[   44.091880] Initializing CPU#1
[   44.169480] Calibrating delay using timer specific routine.. 4009.38 BogoMIPS (lpj=8018771)
[   44.169487] CPU: L1 I cache: 32K, L1 D cache: 32K
[   44.169488] CPU: L2 cache: 1024K
[   44.169491] CPU 1/1 -> Node 0
[   44.169492] CPU: Physical Processor ID: 0
[   44.169494] CPU: Processor Core ID: 1
[   44.169499] CPU1: Thermal monitoring enabled (TM2)
[   44.169700] Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[   44.169745] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   44.193463] Brought up 2 CPUs
[   44.221966] migration_cost=12
[   44.222137] NET: Registered protocol family 16
[   44.222216] ACPI: bus type pci registered
[   44.222222] PCI: Using configuration type 1
[   44.223315] ACPI: EC: Look up EC in DSDT
[   44.227677] ACPI: Interpreter enabled
[   44.227682] ACPI: (supports S0 S3 S4 S5)
[   44.227703] ACPI: Using IOAPIC for interrupt routing
[   44.233481] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   44.233488] PCI: Probing PCI hardware (bus 00)
[   44.234032] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   44.234036] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   44.234775] PCI: Transparent bridge - 0000:00:1e.0
[   44.234828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   44.234979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   44.235054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   44.235136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   44.248152] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 9 *10 11 12 14 15)
[   44.248248] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 9 10 11 12 14 15)
[   44.248348] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 *10 11 12 14 15)
[   44.248441] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 10 *11 12 14 15)
[   44.248535] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 9 10 *11 12 14 15)
[   44.248629] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 9 10 11 12 14 15) *0, disabled.
[   44.248724] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 *9 10 11 12 14 15)
[   44.248819] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 9 10 11 12 14 15) *0, disabled.
[   44.248912] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.248926] pnp: PnP ACPI init
[   44.248934] ACPI: bus type pnp registered
[   44.252009] pnp: PnP ACPI: found 16 devices
[   44.252011] ACPI: ACPI bus type pnp unregistered
[   44.252066] PCI: Using ACPI for IRQ routing
[   44.252068] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   44.252166] NET: Registered protocol family 8
[   44.252168] NET: Registered protocol family 20
[   44.252185] PCI-GART: No AMD northbridge found.
[   44.252243] pnp: 00:0c: ioport range 0x400-0x4bf could not be reserved
[   44.252249] pnp: 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
[   44.252253] pnp: 00:0f: iomem range 0xd4e00-0xd7fff has been reserved
[   44.252256] pnp: 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   44.252258] pnp: 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   44.252261] pnp: 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   44.252536] PCI: Bridge: 0000:00:01.0
[   44.252539]   IO window: d000-dfff
[   44.252542]   MEM window: f8000000-fbffffff
[   44.252545]   PREFETCH window: d0000000-dfffffff
[   44.252549] PCI: Bridge: 0000:00:1c.0
[   44.252551]   IO window: c000-cfff
[   44.252555]   MEM window: fde00000-fdefffff
[   44.252559]   PREFETCH window: fdc00000-fdcfffff
[   44.252563] PCI: Bridge: 0000:00:1c.1
[   44.252566]   IO window: b000-bfff
[   44.252570]   MEM window: fdb00000-fdbfffff
[   44.252573]   PREFETCH window: fda00000-fdafffff
[   44.252578] PCI: Bridge: 0000:00:1e.0
[   44.252580]   IO window: a000-afff
[   44.252584]   MEM window: fdd00000-fddfffff
[   44.252588]   PREFETCH window: f4000000-f7ffffff
[   44.252602] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.252607] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.252621] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.252626] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   44.252641] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   44.252645] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   44.252654] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   44.252664] NET: Registered protocol family 2
[   44.253350] Time: tsc clocksource has been installed.
[   44.293392] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   44.294785] TCP established hash table entries: 524288 (order: 11, 12582912 bytes)
[   44.301162] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   44.301698] TCP: Hash tables configured (established 524288 bind 65536)
[   44.301702] TCP reno registered
[   44.313407] checking if image is initramfs... it is
[   45.020071] Freeing initrd memory: 7962k freed
[   45.024177] audit: initializing netlink socket (disabled)
[   45.024196] audit(1210049743.492:1): initialized
[   45.026018] VFS: Disk quotas dquot_6.5.1
[   45.026065] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   45.026145] io scheduler noop registered
[   45.026147] io scheduler anticipatory registered
[   45.026149] io scheduler deadline registered
[   45.026234] io scheduler cfq registered (default)
[   45.027255] Boot video device is 0000:01:00.0
[   45.027375] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   45.027405] assign_interrupt_mode Found MSI capability
[   45.027408] Allocate Port Service[0000:00:01.0:pcie00]
[   45.027481] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   45.027515] assign_interrupt_mode Found MSI capability
[   45.027517] Allocate Port Service[0000:00:1c.0:pcie00]
[   45.027551] Allocate Port Service[0000:00:1c.0:pcie02]
[   45.027616] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   45.027651] assign_interrupt_mode Found MSI capability
[   45.027653] Allocate Port Service[0000:00:1c.1:pcie00]
[   45.027677] Allocate Port Service[0000:00:1c.1:pcie02]
[   45.047746] Real Time Clock Driver v1.12ac
[   45.047832] Linux agpgart interface v0.102 (c) Dave Jones
[   45.047834] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.047926] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.048076] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.048547] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.049178] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.049291] input: Macintosh mouse button emulation as /class/input/input0
[   45.049364] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   45.051730] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.051734] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.051882] mice: PS/2 mouse device common for all mice
[   45.052001] TCP cubic registered
[   45.052096] NET: Registered protocol family 1
[   45.052566] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   45.052574] Freeing unused kernel memory: 296k freed
[   45.078165] input: AT Translated Set 2 keyboard as /class/input/input1
[   46.191606] AppArmor: AppArmor initialized<5>audit(1210049744.660:2):  type=1505 info="AppArmor initialized" pid=1175
[   46.196229] fuse init (API version 7.8)
[   46.199896] Failure registering capabilities with primary security module.
[   46.233285] ACPI: Fan [FAN] (on)
[   46.237208] ACPI: SSDT CFEE7AC0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   46.237321] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   46.237330] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   46.238267] ACPI: Thermal Zone [THRM] (40 C)
[   46.632004] usbcore: registered new interface driver usbfs
[   46.632027] usbcore: registered new interface driver hub
[   46.632051] usbcore: registered new device driver usb
[   46.632637] USB Universal Host Controller Interface driver v3.0
[   46.632714] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.632724] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   46.632727] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   46.632831] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   46.632857] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[   46.632959] usb usb1: configuration #1 chosen from 1 choice
[   46.632986] hub 1-0:1.0: USB hub found
[   46.632992] hub 1-0:1.0: 2 ports detected
[   46.666975] SCSI subsystem initialized
[   46.670724] libata version 2.21 loaded.
[   46.730510] Floppy drive(s): fd0 is 1.44M
[   46.737506] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   46.737520] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   46.737523] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   46.737551] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   46.737579] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[   46.737671] usb usb2: configuration #1 chosen from 1 choice
[   46.737698] hub 2-0:1.0: USB hub found
[   46.737704] hub 2-0:1.0: 2 ports detected
[   46.752927] FDC 0 is a post-1991 82077
[   46.845244] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   46.845257] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   46.845260] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   46.845289] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   46.845315] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fd00
[   46.845412] usb usb3: configuration #1 chosen from 1 choice
[   46.845435] hub 3-0:1.0: USB hub found
[   46.845441] hub 3-0:1.0: 2 ports detected
[   46.953021] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   46.953032] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   46.953035] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   46.953058] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   46.953084] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fc00
[   46.953175] usb usb4: configuration #1 chosen from 1 choice
[   46.953198] hub 4-0:1.0: USB hub found
[   46.953204] hub 4-0:1.0: 2 ports detected
[   47.060845] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   47.060857] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   47.060860] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   47.060882] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   47.060908] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fb00
[   47.060997] usb usb5: configuration #1 chosen from 1 choice
[   47.061020] hub 5-0:1.0: USB hub found
[   47.061026] hub 5-0:1.0: 2 ports detected
[   47.084713] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   47.170103] ahci 0000:00:1f.2: version 2.2
[   47.170128] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   47.247875] usb 2-2: configuration #1 chosen from 1 choice
[   48.174959] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   48.174963] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[   48.174967] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   48.175666] scsi0 : ahci
[   48.175888] scsi1 : ahci
[   48.176056] scsi2 : ahci
[   48.176211] scsi3 : ahci
[   48.176357] scsi4 : ahci
[   48.176509] scsi5 : ahci
[   48.176715] ata1: SATA max UDMA/133 cmd 0xffffc20001432100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.176719] ata2: SATA max UDMA/133 cmd 0xffffc20001432180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.176722] ata3: SATA max UDMA/133 cmd 0xffffc20001432200 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.176726] ata4: SATA max UDMA/133 cmd 0xffffc20001432280 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.176729] ata5: SATA max UDMA/133 cmd 0xffffc20001432300 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.176733] ata6: SATA max UDMA/133 cmd 0xffffc20001432380 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   48.662139] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   48.679842] ata1.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   48.679846] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   48.680577] ata1.00: configured for UDMA/133
[   48.993594] ata2: SATA link down (SStatus 0 SControl 300)
[   49.476805] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   49.496075] ata3.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   49.496078] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   49.496799] ata3.00: configured for UDMA/133
[   49.808261] ata4: SATA link down (SStatus 0 SControl 300)
[   50.119749] ata5: SATA link down (SStatus 0 SControl 300)
[   50.431239] ata6: SATA link down (SStatus 0 SControl 300)
[   50.431336] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   50.431733] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   50.432053] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.432341] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   50.432570] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   50.432576] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   50.432822] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   50.432857] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   50.432863] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[   50.436748] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.437088] usb usb6: configuration #1 chosen from 1 choice
[   50.437245] hub 6-0:1.0: USB hub found
[   50.437252] hub 6-0:1.0: 4 ports detected
[   50.730761] usb 2-2: USB disconnect, address 2
[   50.970349] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   51.133606] usb 2-2: configuration #1 chosen from 1 choice
[   51.437616] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   51.437620] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   51.437626] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   51.437730] scsi6 : ahci
[   51.437983] scsi7 : ahci
[   51.438151] ata7: SATA max UDMA/133 cmd 0xffffc20001434100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   51.438156] ata8: SATA max UDMA/133 cmd 0xffffc20001434180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   51.753079] ata7: SATA link down (SStatus 0 SControl 300)
[   52.064570] ata8: SATA link down (SStatus 0 SControl 300)
[   52.065186] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   52.065428] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   52.065435] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   52.067454] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   52.067492] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   52.067500] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[   52.071375] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   52.071477] usb usb7: configuration #1 chosen from 1 choice
[   52.071500] hub 7-0:1.0: USB hub found
[   52.071507] hub 7-0:1.0: 6 ports detected
[   52.077937] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   52.077949] sd 0:0:0:0: [sda] Write Protect is off
[   52.077952] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.077964] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.078013] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   52.078021] sd 0:0:0:0: [sda] Write Protect is off
[   52.078023] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.078035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.078039]  sda: sda1 sda2
[   52.110786] sd 0:0:0:0: [sda] Attached SCSI disk
[   52.110837] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   52.110845] sd 2:0:0:0: [sdb] Write Protect is off
[   52.110847] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   52.110859] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.110893] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   52.110900] sd 2:0:0:0: [sdb] Write Protect is off
[   52.110902] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   52.110914] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.110916]  sdb: sdb1
[   52.126894] sd 2:0:0:0: [sdb] Attached SCSI disk
[   52.129783] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   52.129801] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   52.176656] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   52.176664] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   52.176703] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   52.176755] scsi8 : pata_jmicron
[   52.176805] scsi9 : pata_jmicron
[   52.176832] ata9: PATA max UDMA/100 cmd 0x000000000001cf00 ctl 0x000000000001ce02 bmdma 0x000000000001cb00 irq 17
[   52.176836] ata10: PATA max UDMA/100 cmd 0x000000000001cd00 ctl 0x000000000001cc02 bmdma 0x000000000001cb08 irq 17
[   52.293562] Attempting manual resume
[   52.293565] swsusp: Resume From Partition 8:2
[   52.293567] PM: Checking swsusp image.
[   52.293731] PM: Resume from disk failed.
[   52.335407] kjournald starting.  Commit interval 5 seconds
[   52.335413] EXT3-fs: mounted filesystem with ordered data mode.
[   52.516315] ata9.00: ATAPI: Memorex DVD+-RAM 530L v1, 5M64, max UDMA/66
[   52.708020] ata9.00: configured for UDMA/66
[   52.879765] scsi 8:0:0:0: CD-ROM            Memorex  DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 5
[   52.879823] scsi 8:0:0:0: Attached scsi generic sg2 type 5
[   52.879881] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   52.879889] PCI: Setting latency timer of device 0000:04:01.0 to 64
[   52.932969] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   54.213132] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20002459b7]
[   56.382333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.461087] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.577248] iTCO_vendor_support: vendor-support=0
[   56.739971] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   56.739985] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   56.740237] sky2 0000:03:00.0: v1.18 addr 0xfdbfc000 irq 17 Yukon-EC Ultra (0xb4) rev 2
[   56.740593] sky2 eth0: addr 00:15:58:91:4a:91
[   56.842409] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   56.881843] Linux video capture interface: v2.00
[   56.914968] irda_init()
[   56.914982] NET: Registered protocol family 23
[   56.978591] ivtv:  ==================== START INIT IVTV ====================
[   56.978596] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   56.978680] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   56.978726] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.995482] lirc_dev: IR Remote Control driver registered, at major 61 
[   56.997356] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   56.997360] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   56.997408] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   56.997413] lirc_dev: lirc_register_plugin: sample_rate: 0
[   56.997445] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   56.997491] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<2:3> initialized
[   56.997504] usbcore: registered new interface driver lirc_imon
[   57.071897] nvidia: module license 'NVIDIA' taints kernel.
[   57.399748] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   57.399752] Uniform CD-ROM driver Revision: 3.20
[   57.400006] sr 8:0:0:0: Attached scsi CD-ROM sr0
[   57.572839] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   57.576426] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
[   57.576484] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   57.576750] parport_pc 00:09: reported by Plug and Play ACPI
[   57.576797] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   57.577559] input: PC Speaker as /class/input/input3
[   57.653066] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139633085999552 bytes)
[   57.871067] ivtv0: Encoder revision: 0x02050032
[   57.871070] ivtv0: Recommended firmware version is 0x02060039.
[   57.928950] tveeprom 0-0050: Hauppauge model 32062, rev C199, serial# 8276176
[   57.928954] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   57.928957] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   57.928959] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[   57.928961] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   57.928963] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   57.928966] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   57.950551] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   57.998660] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   58.144943] msp3400 0-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #0)
[   58.144946] msp3400 0-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[   58.146097] tuner 0-0061: type set to 50 (TCL 2002N)
[   58.421546] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   58.424494] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   58.426132] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   58.426987] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   58.475784] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[   58.475811] ivtv:  ====================  END INIT IVTV  ====================
[   58.482180] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   58.482189] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   58.482271] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9639  Mon Apr 16 20:18:26 PDT 2007
[   58.483212] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   58.483453] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   58.697694] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   59.011018] lp0: using parport0 (interrupt-driven).
[   59.202157] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k
[   59.627271] EXT3 FS on sda1, internal journal
[   60.303539] kjournald starting.  Commit interval 5 seconds
[   60.311212] EXT3 FS on sdb1, internal journal
[   60.311215] EXT3-fs: mounted filesystem with ordered data mode.
[   61.427585] input: Power Button (FF) as /class/input/input4
[   61.427602] ACPI: Power Button (FF) [PWRF]
[   61.427639] input: Power Button (CM) as /class/input/input5
[   61.427654] ACPI: Power Button (CM) [PWRB]
[   61.524556] No dock devices found.
[   63.842175] sky2 eth0: enabling interface
[   64.198109] NET: Registered protocol family 10
[   64.198218] lo: Disabled Privacy Extensions
[   64.198273] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.700323] sky2 eth0: speed/duplex mismatch<3>sky2 eth0: speed/duplex mismatch<3>sky2 eth0: speed/duplex mismatch<3>sky2 eth0: speed/duplex mismatchNVRM: RmInitAdapter failed! (0x23:0xffffffff:678)
[   71.629953] NVRM: rm_init_adapter(0) failed
[   72.684032] sky2 eth0: Link is up at 100 Mbps, half duplex, flow control rx
[   72.689004] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   74.825844] NET: Registered protocol family 17
[   75.682397] NVRM: RmInitAdapter failed! (0x23:0xffffffff:678)
[   75.682412] NVRM: rm_init_adapter(0) failed
[   79.716128] NVRM: RmInitAdapter failed! (0x23:0xffffffff:678)
[   79.716143] NVRM: rm_init_adapter(0) failed
[   84.380387] mtrr: no more MTRRs available
[   86.476194] eth0: no IPv6 routers present
[  114.779942] mtrr: no more MTRRs available
[  120.470146] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[  149.920209] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[  157.830633] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[  180.237314] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[  184.941305] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[  247.293172] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[  254.815727] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[  361.599817] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[  427.963872] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[  434.970079] NVRM: RmInitAdapter failed! (0x23:0xffffffff:678)
[  434.970092] NVRM: rm_init_adapter(0) failed
[  711.984380] NVRM: RmInitAdapter failed! (0x23:0xffffffff:678)
[  711.984395] NVRM: rm_init_adapter(0) failed
[  807.003490] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
r

---

### Post by rbrown3 on 2008-05-06
Some more information:


   Where previously, I had used the channels provided by Data- Direct to set my channels, earlier this morning I tried simply scanning the channels to see what would happen.


   The scan was pretty telling: it seems that the first scan detected the two channels. Subsequent scans, however, somehow stopped "seeing" them.


   My Windows- based "reference" machine still detects and displays the two channels somehow, yet my Mythbuntu system cannot consistently detect them! This continues to be true despite swapping cables, TV Cards, and graphic boards (granted the graphic boards shouldn't effect a TV card's ability to tune into a channel, but I was willing to try anything).

   So two questions: (1) how does one get the Mythbackend to generate the log file referenced in a previous reply, and (2) what part of the dmesg output should I be concentrating on in order to gain clues as to what is going wrong???

---

### Post by larsolav on 2008-05-06
According to the post ["How to get help"]("http://ubuntuforums.org/showthread.php?t=736528") the above location of the logs was cut off one directory...
> The log files for MythTV can be found in /var/log/mythtv/.
If you think your problem is backend specific, you can find the log files for mythbackend in /var/log/mythtv/mythbackend.log.
The frontend logs to /var/log/mythtv/mythfrontend.log. If you're using Mythwelcome, /var/log/mythtv/mythwelcome.log is the right place.

The other stuff I don't know about. But maybe your log files may tell you something.

Cheers!

---

### Post by rbrown3 on 2008-05-06
Actually:


   My point in asking about the logs was that, for some reason, my Mythbackend is not generating them.


   As I stated in my previous post (where I entered the dmesg info following Dumdideldum's advice), there *is no* mythbackend.log file on my system. 


   What I am asking is: how do I get Mythbackend to generate the log so that I can look at it???

---

### Post by gazer22 on 2008-05-06
I'd first recommend "delete all capture cards" and "delete all video sources" from mythtv-setup, then go back and re-add the capture card (the PVR-250), your video source (SchedulesDirect in the US), and then make sure that the Input Connection links your video source to the tuner.

Don't re-scan for channels.

Make sure that the "Channel Frequency Table" is set correctly for your cable system (probably 'us-cable') - under mythtv-setup's General -> "Locale Settings" and that the "Channel Frequency Table" under the Video Source configuration is "default."

As for your mythtv logs, they should be in the /var/log/mythtv directory by default.  Otherwise:
```
sudo find / -name 'mythbackend.log' -print
```

---

### Post by little_penguin on 2008-05-07
Logging is switched on in the frontend (type mythtv or mythfrontend in the terminal) and assuming you're using the default G.A.N.T. menu:

Utilities/Setup -> Setup -> General

then navigate through the pages to where you can enter the path you want the logfile to be written to.

Regards,
little_penguin

---

### Post by milhouse on 2008-05-07
One thing to try is to change the cable feed to your tuner so that you are getting a stronger signal.  Every spliter will attenuate the signal and you might have been on the edge in terms of signal quality as far as your tuner was concerned.

This probably isn't it, as I don't think analog signals don't behave in a binary there/gone fashion.  My digital tuner definitely acts like this though.  One day I had 3 stations.  The next I didn't.  Subsequent searches would never find the channels.  I ended up having to rewire the coax in my house to minimize splitting increasing the signal strength.  Your other DVR box may have a more sensitive tuner or better signal which could explain why it still sees those stations.

Just a suggestion.  Should be easy to test and eliminate as a potential source.

---

### Post by rbrown3 on 2008-05-09
Greetings:


  It turns out that I was looking in the wrong directory. The suggested directory:


>what does /var/log/mythbackend.log say or dmesg ?
>
>Any suspicious error message ?


is actually: /var/log/mythtv/mythbackend.log.


Looking through the log, I didn't see anything really suspicious, except for some strange ioctl() errors that appeared when I changed channels. Of course, my first thought was that these errors were occurring when I changed to the channels in question, but as it turned out they occurred regardless of the channel I changed to. Consequently, I don't think they were significant.

In response to gazer22: that was the first thing I did before coming here. I removed the card information and re- configured everything, using the SchedulesDirect information to set up my channels. Nothing changed.

In response to milhouse: A good suggestion, except that my setup doesn't use splitters at all. I have a cable- compatible multi- output box that slightly amplifies the signal coming in so that it compensates for any loss a splitter might have introduced. The output from this box can go into my Windows- based <g- aaaak!> DVR, or into my MythTV box. Using the *exact same* output in the Windows box, I get the two channels. In the MythTV box the channels are completely gone. My Windows- based box also uses PVR-250 cards. I swapped cards between the Windows and Myth box; cards that worked on the Windows box don't display the channels on the Myth box. Even more weird: these channels are  actually network channels which normally are unscrambled, commercial channels. All other channels of their type come up without problems.

I suspect, based on what I described above, that there may be something wrong with how I set up the Myth box. Something in my setup probably isn't right.

A question: does anyone know exactly what the difference is between the different cable settings? There are three choices for  channel table settings associated with cable: (1) us-cable, (2) us-cable-hrc, and (3) us-cable-irc.

What exactly does the "hrc" and "irc" mean, and how do these things differ from "regular" us-cable?

---

### Post by gazer22 on 2008-05-09
> **rbrown3 said:**
> A question: does anyone know exactly what the difference is between the different cable settings? There are three choices for  channel table settings associated with cable: (1) us-cable, (2) us-cable-hrc, and (3) us-cable-irc.

What exactly does the "hrc" and "irc" mean, and how do these things differ from "regular" us-cable?

[http://www.naval.com/help/tv-freq.htm]("http://www.naval.com/help/tv-freq.htm")

Minor differences between std & hrc (channels 5 & 6).  Bigger differences with irc.

I had some pretty major tuning issues, but it came down to a bad card.  (old PVR-350).  Replaced it with a newer -150, and things are better.

Strange thing is that the -350 was working fine in windows as of 2 months ago.

---

### Post by rbrown3 on 2008-05-10
Interesting.

   Channels 5 and 6 are the channels I am haviing prolems with.

   I think I will look into my channel table settings...

---

