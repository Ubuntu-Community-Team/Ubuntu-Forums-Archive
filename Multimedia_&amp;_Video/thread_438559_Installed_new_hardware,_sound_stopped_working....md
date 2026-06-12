---
title: "Installed new hardware, sound stopped working..."
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by whein on 2007-05-09
Well, I had everything working great.  Had MythTv setup with a PVR-350 card and all was well with the world.  Then I got adventurous and installed two PVR-150 cards as well.  Somehow this made all sound except the pc case speaker stop working.  Nothing pops up an error message when I go to play sound with Myth or XMMS or Mplayer or Xine or a handful of other applications.  Just nothing comes out of the speakers.  I checked that all my volume controls were enabled and unmuted and at max volume.   I've run some diagnostic commands suggested in other threads, but I don't know enough to make heads or tails of 'em.  They're pasted below.  I'm trying to use the built-in sound hardware on the motherboard, the nvidia CK804 chip.  Suggestions?  Other places to look?  Thanks in advance for any help!
-Will
```
whein@MythTvBox2:~$ cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xfe02c000, irq 22

```
```
whein@MythTvBox2:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
05:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:08.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
05:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```
```
whein@MythTvBox2:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=c8bd0fad-0724-4fc6-99b5-563aef26fce3 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
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
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f7800
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fee9a40
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee9c80
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee9980
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
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
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
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257094
[    0.000000] Kernel command line: root=UUID=c8bd0fad-0724-4fc6-99b5-563aef26fce3 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   29.350350] Console: colour VGA+ 80x25
[   29.350944] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.351388] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   29.351482] Checking aperture...
[   29.351485] CPU 0: aperture @ f34000000 size 32 MB
[   29.351486] Aperture too small (32 MB)
[   29.356413] No AGP bridge found
[   29.365048] Memory: 1019852k/1047424k available (2217k kernel code, 27184k reserved, 1162k data, 304k init)
[   29.443165] Calibrating delay using timer specific routine.. 4423.09 BogoMIPS (lpj=8846181)
[   29.443215] Security Framework v1.0.0 initialized
[   29.443220] SELinux:  Disabled at boot.
[   29.443242] Mount-cache hash table entries: 256
[   29.443368] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.443370] CPU: L2 Cache: 1024K (64 bytes/line)
[   29.443373] CPU 0/0 -> Node 0
[   29.443375] CPU: Physical Processor ID: 0
[   29.443376] CPU: Processor Core ID: 0
[   29.443393] SMP alternatives: switching to UP code
[   29.443636] Early unpacking initramfs... done
[   29.723098] ACPI: Core revision 20060707
[   29.725396] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.793913] Using local APIC timer interrupts.
[   29.839133] result 12558084
[   29.839134] Detected 12.558 MHz APIC timer.
[   29.843108] SMP alternatives: switching to SMP code
[   29.843175] Booting processor 1/2 APIC 0x1
[   29.854174] Initializing CPU#1
[   29.931577] Calibrating delay using timer specific routine.. 4420.67 BogoMIPS (lpj=8841355)
[   29.931583] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.931585] CPU: L2 Cache: 1024K (64 bytes/line)
[   29.931587] CPU 1/1 -> Node 0
[   29.931589] CPU: Physical Processor ID: 0
[   29.931590] CPU: Processor Core ID: 1
[   29.931694] AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
[   29.935581] CPU 1: Syncing TSC to CPU 0.
[   29.934955] CPU 1: synchronized TSC with CPU 0 (last diff -76 cycles, maxerr 536 cycles)
[   29.934964] Brought up 2 CPUs
[   29.935005] Disabling vsyscall due to use of PM timer
[   29.935008] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   29.935010] time.c: Detected 2210.219 MHz processor.
[   30.690437] migration_cost=287
[   30.690719] Time:  0:37:37  Date: 04/10/107
[   30.690755] NET: Registered protocol family 16
[   30.690825] ACPI: bus type pci registered
[   30.690830] PCI: Using configuration type 1
[   30.698051] ACPI: Interpreter enabled
[   30.698053] ACPI: Using IOAPIC for interrupt routing
[   30.698584] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.698587] PCI: Probing PCI hardware (bus 00)
[   30.701058] PCI: Transparent bridge - 0000:00:09.0
[   30.701256] Boot video device is 0000:01:00.0
[   30.701312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.771125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   30.773034] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 10 11)
[   30.773356] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.773679] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 10 11)
[   30.773999] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.774327] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.774652] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 *10 11)
[   30.774971] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.775292] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 *4 5 7 10 11)
[   30.775618] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 10 11)
[   30.775941] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 10 *11)
[   30.776263] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 *7 10 11)
[   30.776587] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 10 11)
[   30.776914] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.777245] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 *10 11)
[   30.777580] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 10 *11)
[   30.777911] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 10 11) *0, disabled.
[   30.778278] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   30.778643] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   30.779008] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   30.779369] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   30.779648] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   30.780022] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   30.780397] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   30.780769] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   30.781142] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   30.781517] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   30.781893] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   30.782265] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   30.782672] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   30.783053] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   30.783435] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   30.783817] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   30.890373] ACPI: Power Resource [PFAN] (off)
[   30.890470] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.890478] pnp: PnP ACPI init
[   30.897163] pnp: PnP ACPI: found 14 devices
[   30.897206] PCI: Using ACPI for IRQ routing
[   30.897210] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.897274] NET: Registered protocol family 8
[   30.897276] NET: Registered protocol family 20
[   30.897718] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   30.897721] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   30.897723] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   30.897726] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   30.897729] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   30.897731] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   30.897976] PCI: Bridge: 0000:00:09.0
[   30.897978]   IO window: 9000-9fff
[   30.897982]   MEM window: fdf00000-fdffffff
[   30.897984]   PREFETCH window: d4000000-dfffffff
[   30.897987] PCI: Bridge: 0000:00:0b.0
[   30.897988]   IO window: 6000-6fff
[   30.897991]   MEM window: fdb00000-fdbfffff
[   30.897994]   PREFETCH window: fda00000-fdafffff
[   30.897996] PCI: Bridge: 0000:00:0c.0
[   30.897998]   IO window: 7000-7fff
[   30.898000]   MEM window: fdd00000-fddfffff
[   30.898003]   PREFETCH window: fdc00000-fdcfffff
[   30.898005] PCI: Bridge: 0000:00:0d.0
[   30.898007]   IO window: 8000-8fff
[   30.898009]   MEM window: fd900000-fd9fffff
[   30.898012]   PREFETCH window: fde00000-fdefffff
[   30.898016] PCI: Bridge: 0000:00:0e.0
[   30.898018]   IO window: a000-afff
[   30.898021]   MEM window: fa000000-fcffffff
[   30.898023]   PREFETCH window: c0000000-cfffffff
[   30.898029] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   30.898036] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.898041] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   30.898045] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.898050] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   30.898089] NET: Registered protocol family 2
[   30.934272] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   30.934494] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   30.935536] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   30.936028] TCP: Hash tables configured (established 131072 bind 65536)
[   30.936031] TCP reno registered
[   30.950319] checking if image is initramfs... it is
[   31.475328] Freeing initrd memory: 6824k freed
[   31.479638] audit: initializing netlink socket (disabled)
[   31.479651] audit(1178757458.072:1): initialized
[   31.479821] VFS: Disk quotas dquot_6.5.1
[   31.479839] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   31.479880] io scheduler noop registered
[   31.479882] io scheduler anticipatory registered
[   31.479884] io scheduler deadline registered
[   31.479896] io scheduler cfq registered (default)
[   31.479931] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   31.479938] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.479943] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   31.479950] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.479955] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   31.479961] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.479966] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   31.479972] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.480118] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   31.480135] assign_interrupt_mode Found MSI capability
[   31.480138] Allocate Port Service[0000:00:0b.0:pcie00]
[   31.480195] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   31.480211] assign_interrupt_mode Found MSI capability
[   31.480213] Allocate Port Service[0000:00:0c.0:pcie00]
[   31.480267] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   31.480282] assign_interrupt_mode Found MSI capability
[   31.480284] Allocate Port Service[0000:00:0d.0:pcie00]
[   31.480337] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   31.480352] assign_interrupt_mode Found MSI capability
[   31.480354] Allocate Port Service[0000:00:0e.0:pcie00]
[   31.502538] Real Time Clock Driver v1.12ac
[   31.502585] Linux agpgart interface v0.102 (c) Dave Jones
[   31.502587] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.502700] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.503163] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.503343] mice: PS/2 mouse device common for all mice
[   31.503895] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.504032] input: Macintosh mouse button emulation as /class/input/input0
[   31.504063] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.504067] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.504223] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   31.506636] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.506643] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.506790] TCP cubic registered
[   31.506799] NET: Registered protocol family 1
[   31.506916] ACPI: (supports S0 S3 S4 S5)
[   31.506961]   Magic number: 7:321:607
[   31.507022]   hash matches device ptyae
[   31.507082] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   31.507160] Freeing unused kernel memory: 304k freed
[   31.530191] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.663330] Capability LSM initialized
[   32.897065] ACPI: Transitioning device [FAN] to D3
[   32.897069] ACPI: Transitioning device [FAN] to D3
[   32.897072] ACPI: Fan [FAN] (off)
[   32.901661] ACPI: Invalid passive threshold
[   32.902996] ACPI: Thermal Zone [THRM] (28 C)
[   33.277400] usbcore: registered new interface driver usbfs
[   33.277424] usbcore: registered new interface driver hub
[   33.277447] usbcore: registered new device driver usb
[   33.316740] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.317195] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   33.317203] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   33.317234] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.317237] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   33.317370] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   33.317386] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02a000
[   33.321823] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   33.338754] Floppy drive(s): fd0 is 1.44M
[   33.369915] FDC 0 is a post-1991 82077
[   33.379754] usb usb1: configuration #1 chosen from 1 choice
[   33.379911] hub 1-0:1.0: USB hub found
[   33.379920] hub 1-0:1.0: 10 ports detected
[   33.485955] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   33.485965] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   33.485978] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   33.485981] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   33.486149] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   33.486178] ehci_hcd 0000:00:02.1: debug port 1
[   33.486181] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   33.486191] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   33.486196] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.486634] usb usb2: configuration #1 chosen from 1 choice
[   33.486789] hub 2-0:1.0: USB hub found
[   33.486797] hub 2-0:1.0: 10 ports detected
[   33.598710] SCSI subsystem initialized
[   33.600381] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   33.600390] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   33.600396] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   33.600405] forcedeth: using HIGHDMA
[   33.603504] libata version 2.20 loaded.
[   34.124765] eth0: forcedeth.c: subsystem: 0147b:1c1a bound to 0000:00:0a.0
[   34.124804] sata_nv 0000:00:07.0: version 3.3
[   34.125281] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   34.125288] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   34.125298] sata_nv 0000:00:07.0: Using ADMA mode
[   34.125313] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   34.125385] ata1: SATA max UDMA/133 cmd 0xffffc2000001c480 ctl 0xffffc2000001c4a0 bmdma 0x000000000001d400 irq 20
[   34.125426] ata2: SATA max UDMA/133 cmd 0xffffc2000001c580 ctl 0xffffc2000001c5a0 bmdma 0x000000000001d408 irq 20
[   34.125435] scsi0 : sata_nv
[   34.136112] usb 1-8: new full speed USB device using ohci_hcd and address 2
[   34.343461] usb 1-8: configuration #1 chosen from 1 choice
[   34.439914] ata1: SATA link down (SStatus 0 SControl 300)
[   34.439926] scsi1 : sata_nv
[   34.751707] ata2: SATA link down (SStatus 0 SControl 300)
[   34.752820] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   34.752824] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   34.752834] sata_nv 0000:00:08.0: Using ADMA mode
[   34.752848] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   34.752898] ata3: SATA max UDMA/133 cmd 0xffffc2000001e480 ctl 0xffffc2000001e4a0 bmdma 0x000000000001e800 irq 23
[   34.752938] ata4: SATA max UDMA/133 cmd 0xffffc2000001e580 ctl 0xffffc2000001e5a0 bmdma 0x000000000001e808 irq 23
[   34.752945] scsi2 : sata_nv
[   35.067500] ata3: SATA link down (SStatus 0 SControl 300)
[   35.067506] scsi3 : sata_nv
[   35.379295] ata4: SATA link down (SStatus 0 SControl 300)
[   35.380008] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   35.380027] NFORCE-CK804: chipset revision 242
[   35.380029] NFORCE-CK804: not 100% native mode: will probe irqs later
[   35.380032] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   35.380036] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   35.380044]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:DMA
[   35.380051]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:DMA
[   35.380057] Probing IDE interface ide0...
[   35.671196] hda: WDC AC21200H, ATA DISK drive
[   35.951012] hdb: ST3120026A, ATA DISK drive
[   36.007961] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.013560] Probing IDE interface ide1...
[   36.302762] hdc: ST3120026A, ATA DISK drive
[   36.750468] hdd: LITE-ON DVDRW LH-20A1H, ATAPI CD/DVD-ROM drive
[   36.807575] ide1 at 0x170-0x177,0x376 on irq 15
[   36.832026] hda: max request size: 128KiB
[   36.832031] hda: 2503872 sectors (1281 MB) w/128KiB Cache, CHS=2484/16/63, DMA
[   36.832061]  hda:
[   36.842979] hdb: max request size: 512KiB
[   36.843337] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   36.843452] hdb: cache flushes supported
[   36.843479]  hdb: hdb1 hdb2 hdb3
[   36.863272] hdc: max request size: 512KiB
[   36.863414] hdc: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[   36.863532] hdc: cache flushes supported
[   36.863546]  hdc: hdc1 hdc2 hdc3
[   36.886554] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   36.886559] Uniform CD-ROM driver Revision: 3.20
[   37.316281] Attempting manual resume
[   37.316284] swsusp: Resume From Partition 3:66
[   37.316286] PM: Checking swsusp image.
[   37.316438] PM: Resume from disk failed.
[   37.343673] kjournald starting.  Commit interval 5 seconds
[   37.343683] EXT3-fs: mounted filesystem with ordered data mode.
[   45.651960] NET: Registered protocol family 10
[   45.652057] lo: Disabled Privacy Extensions
[   46.959941] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   46.959963] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   46.977539] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.994556] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.010367] parport: PnPBIOS parport detected.
[   47.010414] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   47.034699] Linux video capture interface: v2.00
[   47.158162] lirc_dev: IR Remote Control driver registered, at major 61 
[   47.219909] ivtv:  ==================== START INIT IVTV ====================
[   47.219913] ivtv:  version 0.10.1 (tagged release) loading
[   47.219915] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 
[   47.219917] ivtv:  In case of problems please include the debug info between
[   47.219918] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   47.219920] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   47.220014] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   47.220563] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   47.220571] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   47.220581] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   47.233525] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   47.234012] 
[   47.234013] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.25 $
[   47.234016] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   47.273439] input: PC Speaker as /class/input/input2
[   47.335716] nvidia: module license 'NVIDIA' taints kernel.
[   47.742658] input: ImExPS/2 Logitech MX Mouse as /class/input/input3
[   47.775243] usb 1-8: reset full speed USB device using ohci_hcd and address 2
[   47.899658] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   47.973256] lirc_dev: lirc_register_plugin: sample_rate: 0
[   47.979140] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb1:2
[   47.979158] usbcore: registered new interface driver lirc_mceusb2
[   48.115018] ivtv0: Encoder revision: 0x02050032
[   48.115021] ivtv0: Recommended firmware version is 0x02060039.
[   48.177538] tveeprom 2-0050: Hauppauge model 26582, rev E6B2, serial# 9710896
[   48.177541] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   48.177544] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   48.177546] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   48.177549] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   48.177551] tveeprom 2-0050: has no radio, has no IR receiver, has no IR transmitter
[   48.177554] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   48.204176] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   48.239040] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   51.377029] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   51.509791] usb 2-2: configuration #1 chosen from 1 choice
[   51.612917] usbcore: registered new interface driver libusual
[   51.729895] Initializing USB Mass Storage driver...
[   51.729959] scsi4 : SCSI emulation for USB Mass Storage devices
[   51.730013] usbcore: registered new interface driver usb-storage
[   51.730016] USB Mass Storage support registered.
[   51.730122] usb-storage: device found at 3
[   51.730124] usb-storage: waiting for device to settle before scanning
[   53.045592] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   53.174043] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   53.238464] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   53.238636] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   53.238829] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   53.238906] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   53.239106] tuner 2-0061: type set to 50 (TCL 2002N)
[   53.625916] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   53.625981] ivtv:  ======================  NEXT CARD  ======================
[   53.625984] ivtv1: Autodetected Hauppauge card (cx23415 based)
[   53.626367] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   53.626374] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   53.626383] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   54.256053] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   54.289200] ivtv1: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   54.514817] ivtv1: Encoder revision: 0x02050032
[   54.514818] ivtv1: Recommended firmware version is 0x02060039.
[   54.522830] ivtv1: Decoder revision: 0x02020023
[   54.529476] tuner 3-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   54.529497] tda9887 3-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   54.533968] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   54.623309] tveeprom 3-0050: Hauppauge model 48132, rev K268, serial# 7683258
[   54.623312] tveeprom 3-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   54.623315] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[   54.623317] tveeprom 3-0050: audio processor is MSP4448 (idx 27)
[   54.623319] tveeprom 3-0050: decoder processor is SAA7115 (idx 19)
[   54.623322] tveeprom 3-0050: has radio, has IR receiver, has no IR transmitter
[   54.623324] ivtv1: Autodetected Hauppauge WinTV PVR-350
[   54.684343] saa7115 3-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #1)
[   54.923355] saa7127 3-0044: saa7129 found @ 0x88 (ivtv i2c driver #1)
[   54.955035] msp3400 3-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #1)
[   54.955039] msp3400 3-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[   54.955201] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   54.955370] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   54.955558] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   54.955638] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   54.955838] ivtv1: Registered device radio1 for encoder radio
[   54.955854] ivtv1: Registered device video17 for decoder MPEG (1 MB)
[   54.955897] ivtv1: Registered device vbi9 for decoder VBI (1 MB)
[   54.956218] ivtv1: Registered device vbi17 for decoder VOUT
[   54.956235] ivtv1: Registered device video49 for decoder YUV (1 MB)
[   55.039492] ivtv1: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[   55.146433] tuner 3-0061: type set to 47 (LG NTSC (TAPE series))
[   55.495385] ivtv1: Initialized Hauppauge WinTV PVR-350, card #1
[   55.495454] ivtv:  ======================  NEXT CARD  ======================
[   55.495457] ivtv2: Autodetected Hauppauge card (cx23416 based)
[   55.495543] ACPI: PCI Interrupt 0000:05:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   55.495552] ivtv2: Unreasonably low latency timer, setting to 64 (was 32)
[   56.053790] eth0: no IPv6 routers present
[   56.127002] ivtv2: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   56.345618] ivtv2: Encoder revision: 0x02050032
[   56.345620] ivtv2: Recommended firmware version is 0x02060039.
[   56.353457] tuner 4-0061: chip found @ 0xc2 (ivtv i2c driver #2)
[   56.375346] cx25840 4-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #2)
[   56.729749] usb-storage: device scan complete
[   56.731117] scsi 4:0:0:0: Direct-Access     OCZ      ET1208AD         1.0  PQ: 0 ANSI: 2
[   56.757460] SCSI device sda: 2007040 512-byte hdwr sectors (1028 MB)
[   56.759331] sda: Write Protect is off
[   56.759334] sda: Mode Sense: 00 00 00 00
[   56.759335] sda: assuming drive cache: write through
[   56.762706] SCSI device sda: 2007040 512-byte hdwr sectors (1028 MB)
[   56.764327] sda: Write Protect is off
[   56.764329] sda: Mode Sense: 00 00 00 00
[   56.764330] sda: assuming drive cache: write through
[   56.764334]  sda: sda1
[   56.836986] sd 4:0:0:0: Attached scsi removable disk sda
[   56.848020] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   61.168581] cx25840 4-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   61.272428] wm8775 4-001b: chip found @ 0x36 (ivtv i2c driver #2)
[   61.352246] tveeprom 4-0050: Hauppauge model 26582, rev E6B2, serial# 9782146
[   61.352249] tveeprom 4-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   61.352252] tveeprom 4-0050: TV standards NTSC(M) (eeprom 0x08)
[   61.352254] tveeprom 4-0050: audio processor is CX25843 (idx 37)
[   61.352256] tveeprom 4-0050: decoder processor is CX25843 (idx 30)
[   61.352259] tveeprom 4-0050: has no radio, has no IR receiver, has no IR transmitter
[   61.352261] ivtv2: Autodetected Hauppauge WinTV PVR-150
[   61.426041] ivtv2: Registered device video2 for encoder MPEG (4 MB)
[   61.426356] ivtv2: Registered device video34 for encoder YUV (2 MB)
[   61.426680] ivtv2: Registered device vbi2 for encoder VBI (1 MB)
[   61.426901] ivtv2: Registered device video26 for encoder PCM audio (1 MB)
[   61.427099] tuner 4-0061: type set to 50 (TCL 2002N)
[   61.816875] ivtv2: Initialized Hauppauge WinTV PVR-150, card #2
[   61.816921] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   61.816930] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   61.817082] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007
[   61.817509] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   61.817515] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 22
[   61.817547] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   61.818408] ivtv:  ====================  END INIT IVTV  ====================
[   62.154124] intel8x0_measure_ac97_clock: measured 54750 usecs
[   62.154128] intel8x0: clocking to 46929
[   62.236072] lp0: using parport0 (interrupt-driven).
[   62.282002] Adding 1662716k swap on /dev/disk/by-uuid/43adaeec-5870-4734-827d-4a30fb675767.  Priority:-1 extents:1 across:1662716k
[   62.301565] Adding 1461904k swap on /dev/disk/by-uuid/c618db7c-7f23-4d81-ba06-61550adbae79.  Priority:-2 extents:1 across:1461904k
[   62.441025] EXT3 FS on hdc1, internal journal
[   62.588711] kjournald starting.  Commit interval 5 seconds
[   62.588682] EXT3 FS on hdb1, internal journal
[   62.588687] EXT3-fs: mounted filesystem with ordered data mode.
[   62.638567] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   62.638794] SGI XFS Quota Management subsystem
[   62.680978] XFS mounting filesystem hdb3
[   62.757147] Ending clean XFS mount for filesystem: hdb3
[   62.799602] XFS mounting filesystem hdc3
[   62.895468] Ending clean XFS mount for filesystem: hdc3
[   65.086176] Using specific hotkey driver
[   65.142494] No dock devices found.
[   65.177770] ibm_acpi: ec object not found
[   65.227290] input: Power Button (FF) as /class/input/input4
[   65.227311] ACPI: Power Button (FF) [PWRF]
[   65.227344] input: Power Button (CM) as /class/input/input5
[   65.227357] ACPI: Power Button (CM) [PWRB]
[   65.332307] pcc_acpi: loading...
[   65.509154] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   65.509042] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   65.509046] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   65.509048] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   65.509050] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   74.505658] ppdev: user-space parallel port driver
[   75.114015] NVRM: Xid (0001:00): 6, PE0000 0784 9be3bb7e 00000000 ffff8b38 02000040
[   84.536153] Bluetooth: Core ver 2.11
[   84.536195] NET: Registered protocol family 31
[   84.536197] Bluetooth: HCI device and connection manager initialized
[   84.536200] Bluetooth: HCI socket layer initialized
[   84.589320] Bluetooth: L2CAP ver 2.8
[   84.589324] Bluetooth: L2CAP socket layer initialized
[   84.591418] Bluetooth: RFCOMM socket layer initialized
[   84.591428] Bluetooth: RFCOMM TTY layer initialized
[   84.591430] Bluetooth: RFCOMM ver 1.8
[   85.588521] apache2[5801] general protection rip:2b9db1a4dab0 rsp:7ffff9060090 error:0
[   89.399674] ISO 9660 Extensions: Microsoft Joliet Level 3
[   89.454581] ISO 9660 Extensions: RRIP_1991A
[  250.179153] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.221328] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.251832] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.339745] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.391708] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.464077] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.519533] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.591510] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.651468] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.723438] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.787362] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.863367] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.931296] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  250.987268] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
[  251.059276] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c

```

---

### Post by whein on 2007-05-09
more diagnostic output

```
whein@MythTvBox2:~$ lsmod
Module                  Size  Used by
isofs                  38628  1 
nls_iso8859_1           6528  1 
nls_cp437               8192  2 
vfat                   16256  1 
fat                    58672  1 vfat
udf                    86664  0 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16480  1 
cpufreq_powersave       3072  0 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  1 
cpufreq_stats           8416  0 
cpufreq_userspace       6176  0 
freq_table              6336  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
dev_acpi               17028  0 
video                  19080  0 
battery                12040  0 
button                 10016  0 
container               6144  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
dock                   11992  0 
sbs                    17856  0 
i2c_ec                  6784  1 sbs
ac                      6920  0 
xfs                   533448  2 
lp                     15048  0 
sg                     40616  0 
sd_mod                 25092  2 
msp3400                34080  0 
saa7127                14484  0 
saa7115                17808  0 
wm8775                  8076  0 
usb_storage            80448  1 
libusual               22184  1 usb_storage
cx25840                28176  0 
tuner                  67368  0 
snd_intel8x0           38952  4 
snd_ac97_codec        117720  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
nvidia               7761464  22 
serio_raw               9092  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
pcspkr                  4736  0 
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lirc_mceusb2           16004  0 
ivtv                  143696  0 
lirc_dev               18504  1 lirc_mceusb2
i2c_algo_bit            9608  1 ivtv
snd                    68904  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
cx2341x                13828  1 ivtv
tveeprom               19216  1 ivtv
videodev               29824  1 ivtv
v4l2_common            28800  7 msp3400,saa7115,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            14980  2 ivtv,videodev
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
k8temp                  7552  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
i2c_nforce2             7680  0 
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
psmouse                43536  0 
i2c_core               26624  12 i2c_ec,msp3400,saa7127,saa7115,wm8775,cx25840,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
ipv6                  307072  20 
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  2 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_cd                 35104  1 
cdrom                  40744  1 ide_cd
ide_disk               18304  8 
ata_generic            10628  0 
amd74xx                16944  0 [permanent]
sata_nv                24196  0 
libata                137000  2 ata_generic,sata_nv
scsi_mod              166968  4 sg,sd_mod,usb_storage,libata
floppy                 67944  0 
forcedeth              48776  0 
generic                 6532  0 [permanent]
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  6 usb_storage,libusual,lirc_mceusb2,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

---

### Post by whein on 2007-05-10
/bump
anyone?

---

### Post by whein on 2007-05-14
:oops:
Ok, not entirely my fault, but wound up being a hardware problem.  Silly me I figured I could unplug the cable that said FP_AUDIO and it would only disable the front panel audio, not completely disable ALL onboard audio (especially the ones hard soldered to the motherboard...)  Stupid design if you ask me.
Unfortunately my motherboard has crap near the PCI slots.  One of them has a trio of electrolytic capacitors and the one fo them has the evil FP_AUDIO connector.  So my PVR-150 cards only fit in 1 of the 3 slots without mechanical interference.  Wound up desoldering the RCA connectors from one of them so it would fit in slot2.  Luckily the PVR-350 *just* fits in slot3 above the FP_AUDIO connector mentioned above when the cable is plugged in.  grr...  But everything works now.  :T
For the record:
ABIT KN8 Ultra Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard
-Will

---

