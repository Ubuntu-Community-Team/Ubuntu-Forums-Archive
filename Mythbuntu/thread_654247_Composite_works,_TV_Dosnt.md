---
title: "Composite works, TV Dosnt"
date: 2007-12-30
forum: Mythbuntu
---

### Post by kdikes on 2007-12-30
I'll just start by saying im a full on windows geek, linux tho is completely foregen to me.  Ive googled for hours, and cant find a guide that i can read and understand... is there any sort of linux for windows users book/guide/wiki/whatever? =)

Got latest release of mythbuntu installed, without a hitch. Was impressed by the ease of install.  Seems to have picked up my bt878 card, after a few hours of poking around and figuring it out as i go, managed to get composite and svideo in working wonderfully.  However try as i might i cannot seem to get the cable tv working properly. (No STB).  Ive tried every possible setting in vein trying to get this to work...

All i get is static, its an odd static tho, its not random and is very patterened, even tried over the air stuff, again, same static, dosnt change.

Card works in windows, oddly enough, it gives the same odd 'patterened' static untill i detect channels, then, after it detects channels, if i go to a channel that dosnt have anything on it, i get the normal random static that i would expect to

Thank you.

---

### Post by superm1 on 2007-12-31
> **kdikes said:**
> I'll just start by saying im a full on windows geek, linux tho is completely foregen to me.  Ive googled for hours, and cant find a guide that i can read and understand... is there any sort of linux for windows users book/guide/wiki/whatever? =)

Got latest release of mythbuntu installed, without a hitch. Was impressed by the ease of install.  Seems to have picked up my bt878 card, after a few hours of poking around and figuring it out as i go, managed to get composite and svideo in working wonderfully.  However try as i might i cannot seem to get the cable tv working properly. (No STB).  Ive tried every possible setting in vein trying to get this to work...

All i get is static, its an odd static tho, its not random and is very patterened, even tried over the air stuff, again, same static, dosnt change.

Card works in windows, oddly enough, it gives the same odd 'patterened' static untill i detect channels, then, after it detects channels, if i go to a channel that dosnt have anything on it, i get the normal random static that i would expect to

Thank you.
Make sure that you chose the correct channel layout (us-cable vs atsc etc).  If you are using cable you need to explicitly choose cable in mythtv-setup.

---

### Post by kdikes on 2008-01-01
Tried every combonation of channel layouts humanly possible.  (Im in the us)

If s-video and composite in works, should i assume the cable part of the card works as well? or is there a chance its not installed properly and coud be a driver-type issue?

---

### Post by superm1 on 2008-01-01
With the bt878 cards, there is a slight possibility that the tuner side of the card was not properly autodetected.  To check look at dmesg for bt878 related items.

---

### Post by kdikes on 2008-01-02
I dont know what im looking for :confused:

Thank you for all your help so far =) I feel like im in the right direction

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000feff0000 - 00000000feff0400 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3b20
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7DB0 checksum 0
[    0.000000] ACPI: RSDP 000F7DB0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEF3040, 0034 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 3FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT 3FEF3180, 639A (r1 NVIDIA NVDAACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEF0000, 0040
[    0.000000] ACPI: HPET 3FEF9640, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 3FEF96C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 3FEF9580, 006E (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000)
[    0.000000] Built 1 zonelists.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=46bf8a78-c2fc-4e84-824b-7729242e87de ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.339 MHz processor.
[   13.473544] spurious 8259A interrupt: IRQ7.
[   13.474518] Console: colour VGA+ 80x25
[   13.474890] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.475470] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.494572] Memory: 1026360k/1047488k available (2015k kernel code, 20420k reserved, 916k data, 364k init, 129984k highmem)
[   13.494582] virtual kernel memory layout:
[   13.494583]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.494584]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.494585]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.494587]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.494588]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.494589]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   13.494590]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   13.494593] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.494626] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.494756] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   13.494761] hpet0: 3 32-bit timers, 25000000 Hz
[   13.575681] Calibrating delay using timer specific routine.. 4022.65 BogoMIPS (lpj=8045300)
[   13.575701] Security Framework v1.0.0 initialized
[   13.575707] SELinux:  Disabled at boot.
[   13.575718] Mount-cache hash table entries: 512
[   13.575823] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[   13.575830] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.575833] CPU: L2 Cache: 128K (64 bytes/line)
[   13.575835] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001
[   13.575844] Compat vDSO mapped to ffffe000.
[   13.575853] Checking 'hlt' instruction... OK.
[   13.591771] SMP alternatives: switching to UP code
[   13.591960] Freeing SMP alternatives: 11k freed
[   13.592210] Early unpacking initramfs... done
[   13.898543] ACPI: Core revision 20070126
[   13.898613] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.902170] CPU0: AMD Mobile AMD Sempron(tm) Processor 3300+ stepping 02
[   13.902187] Total of 1 processors activated (4022.65 BogoMIPS).
[   13.902438] ENABLING IO-APIC IRQs
[   13.902672] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.047119] Brought up 1 CPUs
[   14.047231] Booting paravirtualized kernel on bare hardware
[   14.047296] Time: 22:48:26  Date: 00/02/108
[   14.047317] NET: Registered protocol family 16
[   14.047390] EISA bus registered
[   14.047393] ACPI: bus type pci registered
[   14.068970] PCI: PCI BIOS revision 3.00 entry at 0xfa850, last bus=4
[   14.068972] PCI: Using configuration type 1
[   14.068974] Setting up standard PCI resources
[   14.071771] ACPI: EC: Look up EC in DSDT
[   14.076883] ACPI: Interpreter enabled
[   14.076886] ACPI: (supports S0 S1 S4 S5)
[   14.076899] ACPI: Using IOAPIC for interrupt routing
[   14.086195] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.086203] PCI: Probing PCI hardware (bus 00)
[   14.086756] PCI: Transparent bridge - 0000:00:04.0
[   14.087019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.087262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   14.140845] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   14.141014] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.141180] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.141344] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.141509] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.141674] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.141839] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.142005] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[   14.142169] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.142335] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.142501] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   14.142666] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   14.142831] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   14.143009] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.143176] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   14.143348] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   14.143517] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.143682] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   14.143851] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.

---

### Post by kdikes on 2008-01-02
[   14.144050] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   14.144240] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   14.144430] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   14.144619] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   14.144808] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   14.144997] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   14.145186] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   14.145376] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[   14.145565] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   14.145755] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   14.145945] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   14.146135] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   14.146325] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   14.146515] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   14.146705] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   14.146894] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   14.147088] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   14.147281] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   14.147473] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   14.147621] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.147632] pnp: PnP ACPI init
[   14.147642] ACPI: bus type pnp registered
[   14.152921] pnp: PnP ACPI: found 15 devices
[   14.152924] ACPI: ACPI bus type pnp unregistered
[   14.152928] PnPBIOS: Disabled by ACPI PNP
[   14.152973] PCI: Using ACPI for IRQ routing
[   14.152977] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.207664] NET: Registered protocol family 8
[   14.207666] NET: Registered protocol family 20
[   14.207730] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   14.207733] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   14.207735] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   14.207738] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   14.207741] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   14.207744] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   14.207746] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   14.207749] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   14.207752] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   14.207755] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   14.207758] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   14.207761] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   14.207772] pnp: 00:0d: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   14.207777] pnp: 00:0e: iomem range 0xf0000-0xfffff could not be reserved
[   14.207780] pnp: 00:0e: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   14.207783] pnp: 00:0e: iomem range 0x3fef0000-0x3fefffff could not be reserved
[   14.207786] pnp: 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   14.210885] Time: tsc clocksource has been installed.
[   14.210896] Switched to high resolution mode on CPU 0
[   14.237979] PCI: Bridge: 0000:00:04.0
[   14.237982]   IO window: c000-cfff
[   14.237985]   MEM window: fde00000-fdefffff
[   14.237989]   PREFETCH window: fdf00000-fdffffff
[   14.237994] PCI: Bridge: 0000:00:09.0
[   14.237996]   IO window: b000-bfff
[   14.237999]   MEM window: fdd00000-fddfffff
[   14.238001]   PREFETCH window: fa000000-fbffffff
[   14.238004] PCI: Bridge: 0000:00:0b.0
[   14.238006]   IO window: a000-afff
[   14.238009]   MEM window: fdc00000-fdcfffff
[   14.238011]   PREFETCH window: fdb00000-fdbfffff
[   14.238014] PCI: Bridge: 0000:00:0c.0
[   14.238016]   IO window: 9000-9fff
[   14.238019]   MEM window: fda00000-fdafffff
[   14.238021]   PREFETCH window: fd900000-fd9fffff
[   14.238031] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.238040] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   14.238047] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   14.238054] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   14.238066] NET: Registered protocol family 2
[   14.274808] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.274917] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   14.276078] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.276466] TCP: Hash tables configured (established 131072 bind 65536)
[   14.276469] TCP reno registered
[   14.286868] checking if image is initramfs... it is
[   14.886405] Freeing initrd memory: 7552k freed
[   14.886717] audit: initializing netlink socket (disabled)
[   14.886728] audit(1199314106.108:1): initialized
[   14.886777] highmem bounce pool size: 64 pages
[   14.888151] VFS: Disk quotas dquot_6.5.1
[   14.888192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.888272] io scheduler noop registered
[   14.888274] io scheduler anticipatory registered
[   14.888276] io scheduler deadline registered
[   14.888290] io scheduler cfq registered (default)
[   14.888320] Boot video device is 0000:02:00.0
[   14.888392] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   14.888417] assign_interrupt_mode Found MSI capability
[   14.888419] Allocate Port Service[0000:00:09.0:pcie00]
[   14.888474] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   14.888498] assign_interrupt_mode Found MSI capability
[   14.888500] Allocate Port Service[0000:00:0b.0:pcie00]
[   14.888548] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   14.888572] assign_interrupt_mode Found MSI capability
[   14.888574] Allocate Port Service[0000:00:0c.0:pcie00]
[   14.888665] isapnp: Scanning for PnP cards...
[   15.241361] isapnp: No Plug & Play device found
[   15.278622] Real Time Clock Driver v1.12ac
[   15.278779] hpet_resources: 0xfeff0000 is busy
[   15.278796] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.278892] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.279793] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.280393] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.280570] input: Macintosh mouse button emulation as /class/input/input0
[   15.280631] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.283856] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.283862] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.284013] mice: PS/2 mouse device common for all mice
[   15.284102] EISA: Probing bus 0 at eisa.0
[   15.284108] Cannot allocate resource for EISA slot 1
[   15.284111] Cannot allocate resource for EISA slot 2
[   15.284127] EISA: Detected 0 cards.
[   15.284202] TCP cubic registered
[   15.284211] NET: Registered protocol family 1
[   15.284230] Using IPI No-Shortcut mode
[   15.284386]   Magic number: 8:240:855
[   15.284444]   hash matches device ptyv7
[   15.284451]   hash matches device ptysa
[   15.284728] Freeing unused kernel memory: 364k freed
[   15.317519] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.484750] AppArmor: AppArmor initialized<5>audit(1199314107.608:2):  type=1505 info="AppArmor initialized" pid=1185
[   16.491060] fuse init (API version 7.8)
[   16.495890] Failure registering capabilities with primary security module.
[   16.500087] ACPI: Fan [FAN] (on)
[   16.504802] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.506019] ACPI: Thermal Zone [THRM] (25 C)
[   17.143314] usbcore: registered new interface driver usbfs
[   17.143336] usbcore: registered new interface driver hub
[   17.143352] usbcore: registered new device driver usb
[   17.144574] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   17.144585] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   17.144595] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   17.144598] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   17.144769] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   17.144795] ehci_hcd 0000:00:02.1: debug port 1
[   17.144799] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   17.144809] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfe02e000
[   17.144817] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.144902] usb usb1: configuration #1 chosen from 1 choice
[   17.144924] hub 1-0:1.0: USB hub found
[   17.144930] hub 1-0:1.0: 8 ports detected
[   17.156051] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.185765] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.185770] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.233843] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   17.246356] SCSI subsystem initialized
[   17.250907] libata version 2.21 loaded.
[   17.252227] sata_nv 0000:00:08.0: version 3.4
[   17.252566] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   17.252576] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   17.252612] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.252676] scsi0 : sata_nv
[   17.259034] scsi1 : sata_nv
[   17.259122] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001d800 irq 17
[   17.259125] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001d808 irq 17
[   17.463157] FDC 0 is a post-1991 82077
[   17.726407] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   17.734587] ata1.00: ATA-7: WDC WD800JD-22MSA1, 10.01E01, max UDMA/133
[   17.734590] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.742554] ata1.00: configured for UDMA/133
[   18.053983] ata2: SATA link down (SStatus 0 SControl 300)
[   18.064368] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-22MS 10.0 PQ: 0 ANSI: 5
[   18.067881] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   18.067893] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 18
[   18.067903] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.067907] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.068146] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   18.068164] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfe02f000
[   18.077527] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.077539] sd 0:0:0:0: [sda] Write Protect is off
[   18.077541] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.077553] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.077602] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.077610] sd 0:0:0:0: [sda] Write Protect is off
[   18.077612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.077622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.077626]  sda: sda1 sda2 < sda5 >
[   18.110785] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.114972] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.123983] usb usb2: configuration #1 chosen from 1 choice
[   18.124005] hub 2-0:1.0: USB hub found
[   18.124014] hub 2-0:1.0: 8 ports detected
[   18.225960] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[   18.225979] NFORCE-MCP61: chipset revision 162
[   18.225981] NFORCE-MCP61: not 100% native mode: will probe irqs later
[   18.225987] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[   18.225994]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   18.226004] Probing IDE interface ide0...
[   18.277856] Attempting manual resume
[   18.277859] swsusp: Resume From Partition 8:5
[   18.277861] PM: Checking swsusp image.
[   18.278009] PM: Resume from disk failed.
[   18.311987] kjournald starting.  Commit interval 5 seconds
[   18.311998] EXT3-fs: mounted filesystem with ordered data mode.
[   19.240574] hdb: SAMSUNG CDRW/DVD SM-352B, ATAPI CD/DVD-ROM drive
[   19.329859] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.350364] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   19.350376] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 19
[   19.350382] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   19.350388] forcedeth: using HIGHDMA
[   19.867983] eth0: forcedeth.c: subsystem: 01565:2505 bound to 0000:00:07.0
[   22.971650] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   22.971672] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   23.726265] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.731838] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.961446] Linux video capture interface: v2.00
[   23.992782] bttv: driver version 0.9.17 loaded
[   23.992785] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   23.992835] bttv: Bt8xx card found (0).
[   23.993162] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   23.993172] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   23.993182] bttv0: Bt848 (rev 18) at 0000:01:08.0, irq: 20, latency: 16, mmio: 0xfdfff000
[   23.993190] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   23.993220] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   24.065938] input: PC Speaker as /class/input/input2
[   24.179664] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[   24.179669] bttv0: using tuner=-1
[   24.179671] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   24.185556] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   24.190350] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   24.192953] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   24.193472] bttv0: registered device video0
[   24.193496] bttv0: registered device vbi0
[   24.193814] hdb: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   24.193821] Uniform CD-ROM driver Revision: 3.20
[   24.398865] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   24.398870] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 16
[   24.398886] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   24.605619] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   24.795986] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   24.799234] parport_pc 00:0a: reported by Plug and Play ACPI
[   24.799281] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   26.532477] lp0: using parport0 (interrupt-driven).
[   26.781213] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   27.013085] EXT3 FS on sda1, internal journal
[   28.707907] No dock devices found.
[   28.823882] input: Power Button (FF) as /class/input/input4
[   28.827670] ACPI: Power Button (FF) [PWRF]
[   28.857863] input: Power Button (CM) as /class/input/input5
[   28.861619] ACPI: Power Button (CM) [PWRB]
[   28.891796] input: Sleep Button (CM) as /class/input/input6
[   28.895546] ACPI: Sleep Button (CM) [SLPB]
[   31.474265] NET: Registered protocol family 10
[   31.474352] lo: Disabled Privacy Extensions
[   40.419181] Linux agpgart interface v0.102 (c) Dave Jones
[   40.444425] [drm] Initialized drm 1.1.0 20060810
[   40.452063] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   40.452069] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 20
[   40.456090] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   42.781564] [drm] Setting GART location based on new memory map
[   42.781801] [drm] Loading R300 Microcode
[   42.781825] [drm] writeback test succeeded in 1 usecs
[   43.111564] NET: Registered protocol family 17
[   55.582095] eth0: no IPv6 routers present

---

### Post by theacoustician on 2008-01-03
> [ 23.961446] Linux video capture interface: v2.00
[ 23.992782] bttv: driver version 0.9.17 loaded
[ 23.992785] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 23.992835] bttv: Bt8xx card found (0).
[ 23.993162] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[ 23.993172] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[ 23.993182] bttv0: Bt848 (rev 1 at 0000:01:08.0, irq: 20, latency: 16, mmio: 0xfdfff000
[ 23.993190] bttv0: using: *** UNKNOWN/GENERIC *** [card=0,autodetected]
[ 23.993220] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[ 24.065938] input: PC Speaker as /class/input/input2
[ 24.179664] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[ 24.179669] bttv0: using tuner=-1
[ 24.179671] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 24.185556] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 24.190350] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 24.192953] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 24.193472] bttv0: registered device video0
[ 24.193496] bttv0: registered device vbi0
 That's the important part right there.  It looks like the card wasn't fully configured properly.  What make/model card are you using?

---

### Post by kdikes on 2008-01-03
i honestly dont know exsact make/model =(  Ive got 5 or 6 bt 848 and 878 cards floating around, but i dont see anything else identifying past that.

ive got a couple .tar's that supposedly have drivers inside. Ive been digging pretty hard but have yet to find any documentation that can tell me how to use them.  :confused:


I was considering buying another tuner card just to take the unknown variable out of the picture for ease of learning.  Being as im so noob, would that be a route to consider?

---

### Post by superm1 on 2008-01-03
> **kdikes said:**
> i honestly dont know exsact make/model =(  Ive got 5 or 6 bt 848 and 878 cards floating around, but i dont see anything else identifying past that.

ive got a couple .tar's that supposedly have drivers inside. Ive been digging pretty hard but have yet to find any documentation that can tell me how to use them.  :confused:


I was considering buying another tuner card just to take the unknown variable out of the picture for ease of learning.  Being as im so noob, would that be a route to consider?
You already have all the drivers possible for these cards on your system.  It is just a matter of setting a parameter for which tuner is in your card.

Here is a list of all the different "known" boards: [http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv)

If yours is not on the list, that doesn't mean it won't work, but just that you may have to research what tuner number it uses.

Aside from that , I would highly recommend that you go with a hauppauge pvr-150 or 500 instead.  It is a night and day difference in quality, performance and ease.

---

### Post by kdikes on 2008-01-03
Okay, so i noticed in 
[ 23.993190] bttv0: using: *** UNKNOWN/GENERIC *** [card=0,autodetected]
the card=0, i can only assume that is what im looking for and thats what i need to change... the only question is... how? =)

As soon as the wallet fattens up i'll definatly be purchasing a pvr-150/500. 
I cant thank you enough for your help =)  My faith in linux has been restored.
Tried Suse a few months ago, every time i had a question i was just shot down and belittled.  Just poking around the ubuntu forums, the community seem to be much nicer and actually helpfull.

---

### Post by theacoustician on 2008-01-03
> **superm1 said:**
> You already have all the drivers possible for these cards on your system.  It is just a matter of setting a parameter for which tuner is in your card.

Here is a list of all the different "known" boards: [http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv)

If yours is not on the list, that doesn't mean it won't work, but just that you may have to research what tuner number it uses.

Aside from that , I would highly recommend that you go with a hauppauge pvr-150 or 500 instead.  It is a night and day difference in quality, performance and ease.

Given that we are approximately 1 year away from full analog shutdown, I would not be recommending analog cards to people if they're buying new.  Since Feb 17, 2009  is a hard shutoff for all US Linux users, I'd start weening people off now and get the driver support for whatever ATSC/QAM card the community can support.  In fact, I wouldn't be a bit surprised to see some cable companies jump the gun a bit because they're currently starving for bandwidth and they'd love to dump their analog tier.  OTA will last until the cutoff date though.

kdikes - start here [http://wiki.linuxhelp.net/index.php/Bttv_Setup](http://wiki.linuxhelp.net/index.php/Bttv_Setup) .  Scroll down to the Debian section and follow that.  That's a good start point and about all I can suggest without knowing what tuner card you have.

---

### Post by superm1 on 2008-01-03
> **theacoustician said:**
> Given that we are approximately 1 year away from full analog shutdown, I would not be recommending analog cards to people if they're buying new.  Since Feb 17, 2009  is a hard shutoff for all US Linux users, I'd start weening people off now and get the driver support for whatever ATSC/QAM card the community can support.  In fact, I wouldn't be a bit surprised to see some cable companies jump the gun a bit because they're currently starving for bandwidth and they'd love to dump their analog tier.  OTA will last until the cutoff date though.

kdikes - start here [http://wiki.linuxhelp.net/index.php/Bttv_Setup](http://wiki.linuxhelp.net/index.php/Bttv_Setup) .  Scroll down to the Debian section and follow that.  That's a good start point and about all I can suggest without knowing what tuner card you have.
Well i'll agree and disagree to this.

I know a lot of midwestern cable companies are advertising the fact that even after the big analog/digital switch they will still provide service "to your older tvs"

Nonetheless, you can always output using a digital cable box to an analog source (such as the pvr-xxx cards).

---

### Post by kdikes on 2008-01-03
Right on, thanks for the replys

Gona run with that link and see what i can pull up, wish me luck =)

---

### Post by theacoustician on 2008-01-03
> **superm1 said:**
> Well i'll agree and disagree to this.

I know a lot of midwestern cable companies are advertising the fact that even after the big analog/digital switch they will still provide service "to your older tvs"

Nonetheless, you can always output using a digital cable box to an analog source (such as the pvr-xxx cards).
Fair enough, but after attending TelcoTV this year, I don't think you'll see many cable companies stick with that for long.  What a small town telco can offer in a triple pack (IPTV, VOIP, Internet) with what's coming out on the market now and what will be coming out in 08 is phenominal.  I can't give too many details, but for cable companies to offer comparable packages, analog MUST be dumped.

I would at least think it prudent to put up a sticky with a warning about analog tuner cards so people can make informed decisions when building a Myth system.  Sorry to hijack the thread.

---

### Post by kdikes on 2008-01-03
Okay, seem to be having a permissions issue, how do i go about opening and saving this file?

If i open it with kedit, its blank, if i try to save it, just says cant create backup, then unable to write file

edit: Dont worry about hijacking thread =)  All info is usefull info

and... how do i go about showing my apperciation for the help ive been reciving? Any sort of donation thing in place? Or just stick with it, learn it so i can later teach it? =)

---

### Post by theacoustician on 2008-01-03
> **kdikes said:**
> Okay, seem to be having a permissions issue, how do i go about opening and saving this file?

If i open it with kedit, its blank, if i try to save it, just says cant create backup, then unable to write file

edit: Dont worry about hijacking thread =)  All info is usefull info

and... how do i go about showing my apperciation for the help ive been reciving? Any sort of donation thing in place? Or just stick with it, learn it so i can later teach it? =)

Open the command line up and 
> 
kdesu kedit *your_document*

That should give you super user under kedit.  Be careful what you do and make sure to save a backup of any file _before_ you edit it so you can un-fubar any oopses. Good luck.

As for the thanks, there's a little badge looking thing to click at the bottom of each message.  I think getting others turned onto Ubuntu or helping others later on once you learn a few things are just as good.

---

