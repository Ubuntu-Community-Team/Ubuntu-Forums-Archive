---
title: "Digi-TV issue"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by frokki on 2007-12-01
I have Nebula Digi-TV PCI card that works, but sometimes it freezes and doesn't display TV until I reboot my system.

When this error occurs, dmesg gives me infinite amount of lines like this:
```
[ 3982.978628] mt352_read_register: readreg error (reg=13, ret==-121)
[ 3982.979271] mt352_read_register: readreg error (reg=14, ret==-121)
[ 3982.979903] mt352_read_register: readreg error (reg=15, ret==-121)
[ 3982.980538] mt352_read_register: readreg error (reg=16, ret==-121)
[ 3982.981179] mt352_read_register: readreg error (reg=17, ret==-121)

```

Help appreciated!

---

### Post by frokki on 2007-12-02
UPDATE: No, it doesn't work at all anymore. 

This is a 48 hours old clean install of Kubuntu Gutsy, and Mythtv + Nebula worked just fine until last night. Rebooting doesn't do the trick, neither did physical resetting of the card. I'm pretty sure that the card works perfectly, and this has to be a driver issue. I've been googling for hours but haven't come up with anything reasonable. Thousands of virtual kisses for ANY reply! Thanks!

And here's the complete dmesg print:
```
frokki@breeze:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4020
[    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524000
[    0.000000] On node 0 totalpages: 524000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEE3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 602F (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: SRAT 7FEE92C0, 0090 (r1 AMD    HAMMER          1 AMD         1)
[    0.000000] ACPI: MCFG 7FEE93C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE9200, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Built 1 zonelists.  Total pages: 519907
[    0.000000] Kernel command line: root=UUID=1015e003-d5ed-4c79-a552-c79daa214786 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2550.617 MHz processor.
[   20.912573] spurious 8259A interrupt: IRQ7.
[   20.914637] Console: colour VGA+ 80x25
[   20.914866] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.915132] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.963102] Memory: 2066720k/2096000k available (2015k kernel code, 28144k reserved, 916k data, 364k init, 1178496k highmem)
[   20.963110] virtual kernel memory layout:
[   20.963111]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   20.963112]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.963113]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.963114]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.963114]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   20.963115]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   20.963116]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   20.963119] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.963144] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.043070] Calibrating delay using timer specific routine.. 5104.47 BogoMIPS (lpj=10208955)
[   21.043087] Security Framework v1.0.0 initialized
[   21.043091] SELinux:  Disabled at boot.
[   21.043100] Mount-cache hash table entries: 512
[   21.043177] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   21.043183] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.043184] CPU: L2 Cache: 512K (64 bytes/line)
[   21.043186] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   21.043193] Compat vDSO mapped to ffffe000.
[   21.043200] Checking 'hlt' instruction... OK.
[   21.059135] SMP alternatives: switching to UP code
[   21.059251] Freeing SMP alternatives: 11k freed
[   21.059426] Early unpacking initramfs... done
[   21.283967] ACPI: Core revision 20070126
[   21.284021] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.287736] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[   21.287748] Total of 1 processors activated (5104.47 BogoMIPS).
[   21.287875] ENABLING IO-APIC IRQs
[   21.288045] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   21.434670] Brought up 1 CPUs
[   21.434745] Booting paravirtualized kernel on bare hardware
[   21.434778] Time: 20:10:50  Date: 11/02/107
[   21.434792] NET: Registered protocol family 16
[   21.434839] EISA bus registered
[   21.434846] ACPI: bus type pci registered
[   21.439252] PCI: PCI BIOS revision 3.00 entry at 0xfa430, last bus=5
[   21.439254] PCI: Using configuration type 1
[   21.439255] Setting up standard PCI resources
[   21.441624] ACPI: EC: Look up EC in DSDT
[   21.445830] ACPI: Interpreter enabled
[   21.445832] ACPI: (supports S0 S1 S3 S4 S5)
[   21.445842] ACPI: Using IOAPIC for interrupt routing
[   21.451959] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.451963] PCI: Probing PCI hardware (bus 00)
[   21.452371] PCI: Transparent bridge - 0000:00:09.0
[   21.452586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.452771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   21.494561] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.494693] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   21.494818] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   21.494946] ACPI: PCI Interrupt Link [LNK4] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   21.495070] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.495196] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   21.495320] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.495446] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   21.495570] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   21.495694] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.495820] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   21.495944] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   21.496071] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.496202] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   21.496334] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   21.496466] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.496603] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   21.496736] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   21.496868] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   21.497000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   21.497088] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   21.497225] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   21.497361] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   21.497497] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   21.497633] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   21.497769] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   21.497905] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   21.498041] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   21.498177] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   21.498318] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   21.498459] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   21.498602] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   21.498670] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.498679] pnp: PnP ACPI init
[   21.498684] ACPI: bus type pnp registered
[   21.501953] pnp: PnP ACPI: found 13 devices
[   21.501954] ACPI: ACPI bus type pnp unregistered
[   21.501957] PnPBIOS: Disabled by ACPI PNP
[   21.501986] PCI: Using ACPI for IRQ routing
[   21.501989] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.553865] NET: Registered protocol family 8
[   21.553866] NET: Registered protocol family 20
[   21.553901] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   21.553903] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   21.553906] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   21.553908] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   21.553910] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   21.553912] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   21.553914] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   21.553920] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.553923] pnp: 00:0c: iomem range 0xcea00-0xcffff has been reserved
[   21.553925] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   21.553928] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   21.553930] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   21.554517] Time: tsc clocksource has been installed.
[   21.584066] PCI: Bridge: 0000:00:09.0
[   21.584067]   IO window: a000-afff
[   21.584070]   MEM window: fde00000-fdefffff
[   21.584072]   PREFETCH window: fdf00000-fdffffff
[   21.584074] PCI: Bridge: 0000:00:0b.0
[   21.584075]   IO window: 9000-9fff
[   21.584078]   MEM window: fdd00000-fddfffff
[   21.584080]   PREFETCH window: fdc00000-fdcfffff
[   21.584082] PCI: Bridge: 0000:00:0c.0
[   21.584083]   IO window: 8000-8fff
[   21.584085]   MEM window: fdb00000-fdbfffff
[   21.584087]   PREFETCH window: fda00000-fdafffff
[   21.584089] PCI: Bridge: 0000:00:0d.0
[   21.584091]   IO window: 7000-7fff
[   21.584093]   MEM window: fd900000-fd9fffff
[   21.584095]   PREFETCH window: fd800000-fd8fffff
[   21.584097] PCI: Bridge: 0000:00:0e.0
[   21.584099]   IO window: 6000-6fff
[   21.584101]   MEM window: fa000000-fcffffff
[   21.584103]   PREFETCH window: d0000000-dfffffff
[   21.584108] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.584114] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   21.584118] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   21.584122] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   21.584126] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   21.584134] NET: Registered protocol family 2
[   21.622465] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.622533] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   21.623249] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.623487] TCP: Hash tables configured (established 131072 bind 65536)
[   21.623489] TCP reno registered
[   21.634506] checking if image is initramfs... it is
[   22.074223] Freeing initrd memory: 7060k freed
[   22.074446] audit: initializing netlink socket (disabled)
[   22.074454] audit(1196626250.992:1): initialized
[   22.074491] highmem bounce pool size: 64 pages
[   22.075521] VFS: Disk quotas dquot_6.5.1
[   22.075551] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.075604] io scheduler noop registered
[   22.075606] io scheduler anticipatory registered
[   22.075607] io scheduler deadline registered
[   22.075616] io scheduler cfq registered (default)
[   22.085937] Switched to high resolution mode on CPU 0
[   30.064028] 0000:00:02.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   30.064039] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   30.064045] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   30.064049] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   30.064055] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   30.064059] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   30.064065] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   30.064069] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   30.064075] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   30.064081] Boot video device is 0000:05:00.0
[   30.064127] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.064142] assign_interrupt_mode Found MSI capability
[   30.064144] Allocate Port Service[0000:00:0b.0:pcie00]
[   30.064180] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   30.064195] assign_interrupt_mode Found MSI capability
[   30.064196] Allocate Port Service[0000:00:0c.0:pcie00]
[   30.064230] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.064244] assign_interrupt_mode Found MSI capability
[   30.064246] Allocate Port Service[0000:00:0d.0:pcie00]
[   30.064281] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   30.064294] assign_interrupt_mode Found MSI capability
[   30.064296] Allocate Port Service[0000:00:0e.0:pcie00]
[   30.064363] isapnp: Scanning for PnP cards...
[   30.416947] isapnp: No Plug & Play device found
[   30.430782] Real Time Clock Driver v1.12ac
[   30.430837] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.430906] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.431011] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.431313] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.431714] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.431830] input: Macintosh mouse button emulation as /class/input/input0
[   30.431872] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   30.431874] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   30.683649] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.683722] mice: PS/2 mouse device common for all mice
[   30.683787] EISA: Probing bus 0 at eisa.0
[   30.683792] Cannot allocate resource for EISA slot 1
[   30.683802] Cannot allocate resource for EISA slot 6
[   30.683803] Cannot allocate resource for EISA slot 7
[   30.683805] Cannot allocate resource for EISA slot 8
[   30.683806] EISA: Detected 0 cards.
[   30.683860] TCP cubic registered
[   30.683870] NET: Registered protocol family 1
[   30.683883] Using IPI No-Shortcut mode
[   30.683991]   Magic number: 3:923:193
[   30.684017]   hash matches device ttys5
[   30.684075]   hash matches device device:1f
[   30.684222] Freeing unused kernel memory: 364k freed
[   30.753499] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.839430] AppArmor: AppArmor initialized<5>audit(1196626260.492:2):  type=1505 info="AppArmor initialized" pid=1242
[   31.843908] fuse init (API version 7.8)
[   31.847228] Failure registering capabilities with primary security module.
[   31.860278] ACPI: Fan [FAN] (on)
[   31.863243] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.864052] ACPI: Thermal Zone [THRM] (43 C)
[   32.259538] usbcore: registered new interface driver usbfs
[   32.259554] usbcore: registered new interface driver hub
[   32.259566] usbcore: registered new device driver usb
[   32.260012] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.260260] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   32.260267] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   32.260275] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.260277] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   32.260363] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   32.260374] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[   32.276485] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.276489] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.294800] SCSI subsystem initialized
[   32.297888] libata version 2.21 loaded.
[   32.316137] usb usb1: configuration #1 chosen from 1 choice
[   32.316155] hub 1-0:1.0: USB hub found
[   32.316162] hub 1-0:1.0: 10 ports detected
[   32.371663] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   32.417523] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   32.417530] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   32.417537] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   32.417540] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   32.417556] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   32.417574] ehci_hcd 0000:00:02.1: debug port 1
[   32.417577] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   32.417584] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfeb00000
[   32.417588] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.417641] usb usb2: configuration #1 chosen from 1 choice
[   32.417656] hub 2-0:1.0: USB hub found
[   32.417663] hub 2-0:1.0: 10 ports detected
[   32.510205] FDC 0 is a post-1991 82077
[   32.521150] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   32.521164] NFORCE-CK804: chipset revision 162
[   32.521166] NFORCE-CK804: not 100% native mode: will probe irqs later
[   32.521170] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   32.521175]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   32.521182]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   32.521187] Probing IDE interface ide0...
[   33.256166] hda: HL-DT-ST DVDRAM GSA-4160B, ATAPI CD/DVD-ROM drive
[   33.367966] hub 2-0:1.0: over-current change on port 7
[   33.471830] hub 2-0:1.0: over-current change on port 8
[   33.592531] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   33.596270] Probing IDE interface ide1...
[   33.879327] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   34.102026] usb 1-4: configuration #1 chosen from 1 choice
[   34.112926] usbcore: registered new interface driver hiddev
[   34.128244] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /class/input/input2
[   34.128332] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:02.0-4
[   34.128342] usbcore: registered new interface driver usbhid
[   34.128344] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.168386] sata_nv 0000:00:07.0: version 3.4
[   34.168671] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   34.168677] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   34.168680] sata_nv 0000:00:07.0: Using ADMA mode
[   34.168704] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   34.168768] scsi0 : sata_nv
[   34.168798] scsi1 : sata_nv
[   34.168837] ata1: SATA max UDMA/133 cmd 0xf883c480 ctl 0xf883c4a0 bmdma 0x0001d400 irq 18
[   34.168840] ata2: SATA max UDMA/133 cmd 0xf883c580 ctl 0xf883c5a0 bmdma 0x0001d408 irq 18
[   34.176430] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   34.176436] Uniform CD-ROM driver Revision: 3.20
[   34.478588] ata1: SATA link down (SStatus 0 SControl 300)
[   34.790203] ata2: SATA link down (SStatus 0 SControl 300)
[   34.790496] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   34.790503] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   34.790506] sata_nv 0000:00:08.0: Using ADMA mode
[   34.790533] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   34.790584] scsi2 : sata_nv
[   34.790737] scsi3 : sata_nv
[   34.790845] ata3: SATA max UDMA/133 cmd 0xf883e480 ctl 0xf883e4a0 bmdma 0x0001c000 irq 19
[   34.790848] ata4: SATA max UDMA/133 cmd 0xf883e580 ctl 0xf883e5a0 bmdma 0x0001c008 irq 19
[   35.257632] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.265802] ata3.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   35.265804] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   35.281790] ata3.00: configured for UDMA/133
[   35.749026] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   35.757171] ata4.00: ATA-7: WDC WD1600JS-00NCB1, 10.02E02, max UDMA/133
[   35.757173] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   35.765159] ata4.00: configured for UDMA/133
[   35.765220] scsi 2:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   35.765225] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   35.765465] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600JS-00N 10.0 PQ: 0 ANSI: 5
[   35.765469] ata4: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   35.766543] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   35.766549] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
[   35.820879] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   35.826454] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   35.826460] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   35.826488] skge 1.11 addr 0xfdef8000 irq 21 chip Yukon-Lite rev 9
[   35.826570] skge eth0: addr 00:01:29:d1:a1:db
[   35.827562] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   35.827565] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   35.827569] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   35.827574] forcedeth: using HIGHDMA
[   35.836510] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   35.836528] sd 2:0:0:0: [sda] Write Protect is off
[   35.836530] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.836539] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.836574] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   35.836580] sd 2:0:0:0: [sda] Write Protect is off
[   35.836582] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.836590] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.836593]  sda: sda1 sda2 sda3 < sda5 >
[   35.865183] sd 2:0:0:0: [sda] Attached SCSI disk
[   35.865648] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   35.865655] sd 3:0:0:0: [sdb] Write Protect is off
[   35.865657] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.865665] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.865687] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   35.865692] sd 3:0:0:0: [sdb] Write Protect is off
[   35.865694] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.865703] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.865705]  sdb: sdb2 < sdb5 sdb6 >
[   35.878515] sd 3:0:0:0: [sdb] Attached SCSI disk
[   35.880965] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   35.880980] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   36.071467] Attempting manual resume
[   36.071470] swsusp: Resume From Partition 8:21
[   36.071471] PM: Checking swsusp image.
[   36.071583] PM: Resume from disk failed.
[   36.105170] kjournald starting.  Commit interval 5 seconds
[   36.105177] EXT3-fs: mounted filesystem with ordered data mode.
[   36.344748] eth1: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:0a.0
[   37.095422] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0001292000030e93]
[   41.721642] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   41.721676] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   42.241322] Linux video capture interface: v2.00
[   42.242798] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.247337] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.654119] input: PC Speaker as /class/input/input3
[   42.768030] irda_init()
[   42.768042] NET: Registered protocol family 23
[   42.836999] bttv: driver version 0.9.17 loaded
[   42.837002] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   42.837038] bttv: Bt8xx card found (0).
[   42.837228] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   42.837234] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 22
[   42.837242] bttv0: Bt878 (rev 17) at 0000:01:07.0, irq: 22, latency: 32, mmio: 0xfdfff000
[   42.837248] bttv0: detected: Nebula Electronics DigiTV [card=104], PCI subsystem ID is 0071:0101
[   42.837251] bttv0: using: Nebula Electronics DigiTV [card=104,autodetected]
[   42.837276] bttv0: gpio: en=00000000, out=00000000 in=00ffffcf [init]
[   42.837545] bttv0: using tuner=-1
[   42.837565] bttv0: registered device video0
[   42.837583] bttv0: registered device vbi0
[   42.837598] bttv0: PLL: 28636363 => 35468950 .<6>Linux agpgart interface v0.102 (c) Dave Jones
[   42.852465] . ok
[   42.868282] bttv0: add subdevice "dvb0"
[   42.873179] input: bttv IR (card=104) as /class/input/input4
[   43.036905] nvidia: module license 'NVIDIA' taints kernel.
[   43.289156] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   43.289160] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   43.289174] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   43.320399] bt878: AUDIO driver version 0.0.0 loaded
[   43.611330] intel8x0_measure_ac97_clock: measured 54784 usecs
[   43.611332] intel8x0: clocking to 46958
[   43.612184] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   43.612191] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   43.612342] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.01  Wed Sep  5 19:12:23 PDT 2007
[   43.612902] bt878: Bt878 AUDIO function found (0).
[   43.612915] ACPI: PCI Interrupt 0000:01:07.1[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 22
[   43.612920] bt878_probe: card id=[0x1010071],[ Nebula Electronics DigiTV ] has DVB functions.
[   43.612925] bt878(0): Bt878 (rev 17) at 01:07.1, irq: 22, latency: 32, memory: 0xfdffe000
[   43.617607] DVB: registering new adapter (bttv0).
[   43.863558] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   44.535968] loop: module loaded
[   44.569770] lp: driver loaded but no devices found
[   44.675880] Adding 6072528k swap on /dev/sdb5.  Priority:-1 extents:1 across:6072528k
[   45.144407] EXT3 FS on sda2, internal journal
[   45.727763] kjournald starting.  Commit interval 5 seconds
[   45.732882] EXT3 FS on sdb6, internal journal
[   45.732885] EXT3-fs: mounted filesystem with ordered data mode.
[   45.781992] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   45.783925] SGI XFS Quota Management subsystem
[   45.833036] XFS mounting filesystem sda5
[   45.956513] Ending clean XFS mount for filesystem: sda5
[   46.823337] No dock devices found.
[   46.904273] input: Power Button (FF) as /class/input/input5
[   46.907167] ACPI: Power Button (FF) [PWRF]
[   46.933597] input: Power Button (CM) as /class/input/input6
[   46.936491] ACPI: Power Button (CM) [PWRB]
[   47.098729] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[   47.103288] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   48.102032] skge eth1: enabling interface
[   48.905101] NET: Registered protocol family 10
[   48.905166] lo: Disabled Privacy Extensions
[   48.905197] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   49.865996] ppdev: user-space parallel port driver
[   50.604744] audit(1196619080.045:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5075 profile="/usr/sbin/cupsd"
[   54.310129] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   54.310133] apm: overridden by ACPI.
[   56.735525] Failure registering capabilities with primary security module.
[   60.492651] Bluetooth: Core ver 2.11
[   60.492683] NET: Registered protocol family 31
[   60.492685] Bluetooth: HCI device and connection manager initialized
[   60.492687] Bluetooth: HCI socket layer initialized
[   60.514275] Bluetooth: L2CAP ver 2.8
[   60.514278] Bluetooth: L2CAP socket layer initialized
[   60.564004] Bluetooth: RFCOMM socket layer initialized
[   60.564100] Bluetooth: RFCOMM TTY layer initialized
[   60.564102] Bluetooth: RFCOMM ver 1.8
[   61.462308] NET: Registered protocol family 17
[   74.199758] eth0: no IPv6 routers present
[   86.001094] mt352_read_register: readreg error (reg=0, ret==-121)
[   87.036242] mt352_read_register: readreg error (reg=0, ret==-121)
[   87.909457] mt352_read_register: readreg error (reg=0, ret==-121)
[   88.708214] mt352_read_register: readreg error (reg=0, ret==-121)
[   89.705743] mt352_read_register: readreg error (reg=0, ret==-121)
[   91.016484] mt352_read_register: readreg error (reg=0, ret==-121)
[   91.952612] mt352_read_register: readreg error (reg=0, ret==-121)
[   92.973992] mt352_read_register: readreg error (reg=0, ret==-121)
[   94.066285] mt352_read_register: readreg error (reg=0, ret==-121)
[   95.256401] mt352_read_register: readreg error (reg=0, ret==-121)
[   96.499588] mt352_read_register: readreg error (reg=0, ret==-121)
[   97.814771] mt352_read_register: readreg error (reg=0, ret==-121)
[   99.939487] mt352_read_register: readreg error (reg=0, ret==-121)
[  101.382195] mt352_read_register: readreg error (reg=0, ret==-121)
[  102.876542] mt352_read_register: readreg error (reg=0, ret==-121)
[  104.410847] mt352_read_register: readreg error (reg=0, ret==-121)
[  105.985746] mt352_read_register: readreg error (reg=0, ret==-121)
[  107.603931] mt352_read_register: readreg error (reg=0, ret==-121)
[  109.249501] mt352_read_register: readreg error (reg=0, ret==-121)
[  110.923652] mt352_read_register: readreg error (reg=0, ret==-121)
[  112.629767] mt352_read_register: readreg error (reg=0, ret==-121)
[  114.347869] mt352_read_register: readreg error (reg=0, ret==-121)
[  116.081958] mt352_read_register: readreg error (reg=0, ret==-121)
[  117.832655] mt352_read_register: readreg error (reg=0, ret==-121)
[  119.598068] mt352_read_register: readreg error (reg=0, ret==-121)
[  121.380099] mt352_read_register: readreg error (reg=0, ret==-121)

```

---

### Post by frokki on 2007-12-20
No help nowhere yet.

Except this one random person whom I emailed personally, after discovering from some mailing list that he had this same problem with same hardware for over a year ago. It was caused by electrical interference, that occured when he shut down his digital amplifier connected to PC. However, I haven't had my card to work yet, disconnecting the TV-out cable seems to make it last longer (from few hours to few days instead of few minutes), but that is not something I want to do, because like most people, I prefer to use my TV and sofa when watching TV...

I wonder if some kind of UPS would help with the interference? (If that's even the cause..)

---

### Post by frokki on 2007-12-22
News again:

It wasn't electrical noise or anything like that - it was kopete!
[https://bugs.kde.org/show_bug.cgi?id=126286](https://bugs.kde.org/show_bug.cgi?id=126286)

Any ideas how can I prevent kopete trying to use my tv-card as a webcam?

---

### Post by frokki on 2008-03-16
> **frokki said:**
> News again:

It wasn't electrical noise or anything like that - it was kopete!
[https://bugs.kde.org/show_bug.cgi?id=126286](https://bugs.kde.org/show_bug.cgi?id=126286)

Any ideas how can I prevent kopete trying to use my tv-card as a webcam?I'm quite keen to enclose my own threads, but the best solution was to buy a logitech quickcam and let kopete use it instead of my tv-card. :)

---

