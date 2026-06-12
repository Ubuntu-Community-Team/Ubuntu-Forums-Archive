---
title: "Frustrated Newbie"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by entropy51 on 2010-11-07
Hi All,

I apologize for asking some basic questions, but I just installed Ubuntu and I can't connect to the internet.

First some details about my system.

OS:  Ubuntu Studio 10.10 (maverick)
Processor: AMD Phenom II x4 965 (64 bit)
Motherboard: Asus M4A785TD-M EVO (with on-board LAN)
Router: Belkin F5D8235-4 v1 (I am using a wired connection)

I now have 3 operating systems installed on this computer (Win XP, Win 7, and Ubuntu Studio).  I have no trouble connecting to the internet with the other OS's, but when I boot into Ubuntu, it doesn't work.  My gut feeling is that my LAN hardware is not installed or there is a driver problem, but I really don't even know where to start.

Another thread suggested running sudo /sbin/ifconfig but I don't know how to read it.  here are the results:

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Matric:1
RX packets:988 errors:0 dropped:0 overruns:0 frame:0 
TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:75448 (75.4 KB) TX bytes:75448 (75.4 KB)

Any help would be greatly appreciated.  I am excited to start using this new OS.

---

### Post by P4man on 2010-11-07
lets see what network controller you have in there. Its very rare you need a driver for a wired network card, but it does happen. Can you open a terminal (application > accessories > terminal) and type in

```
lspci
```

The line or lines starting with "Ethernet controller" is what Id like to see.

---

### Post by entropy51 on 2010-11-07
Update:

I've been poking around and noticed under "network tools" that my network device is "loopback interface" and I have no other options to select.  How do I add my hardware so it shows up here?

---

### Post by P4man on 2010-11-07
Please read my post above.
Loopback isnt a network card, its a virtual interface. A fake one.

---

### Post by entropy51 on 2010-11-07
Here's what I have:

a2@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:06.0 Multimedia controller: ATI Technologies Inc Device 4d50

I don't see "eithernet controller"  Perhaps that the problem?  :-)

---

### Post by P4man on 2010-11-07
yes, that would be part of the problem.
Can you check in your bios how your network controller is configured? If you have a choice between ON, OFF and AUTO make sure you select ON.

If thats already the case, open a file browser (in places) and browse to 

/var/log/

there is a log file called dmesg. Copy it to an usb stick or something and post the contents here. Please use [code] tags as it will be long.

---

### Post by entropy51 on 2010-11-07
My onboard LAN controller is "enabled"  hoever, my onboard LAN boot ROM is "disabled".

I need to run an errand, but I will be back later to continue troubleshooting.

Thank you so much for your help.

---

### Post by P4man on 2010-11-07
You can leave lan boot rom disabled, thats something else (to allow booting over the network). Ill await your dmesg.

---

### Post by entropy51 on 2010-11-08
ok, here's the dmesg file:



[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=47dcaefa-c9e0-4209-b8b8-659b67d5905a ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 16000-19000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 18000-1a000
[    0.000000] RAMDISK: 37006000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fb4f0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff90100 00054 (v01 091009 XSDT1549 20090910 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90290 000F4 (v03 091009 FACP1549 20090910 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20100428/tbfadt-557)
[    0.000000] ACPI: DSDT 00000000cff90450 0D100 (v01  A1391 A1391001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 0007C (v01 091009 APIC1549 20090910 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90410 0003C (v01 091009 OEMMCFG  20090910 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 00072 (v01 091009 OEMB1549 20090910 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9f450 00038 (v01 091009 OEMHPET  20090910 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff9f490 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880100200000-ffff8801037fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982814
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [19000 - 197ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966686
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=47dcaefa-c9e0-4209-b8b8-659b67d5905a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 1034000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] early_res array is doubled to 128 at [19800 - 1a7ff]
[    0.000000] Subtract (59 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037006000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18340]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009ec00 - 00000e3bd0]   BIOS reserved
[    0.000000]   #7 [00000e3d74 - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e3bd0 - 00000e3d74]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #12 [0000018000 - 0000019000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18340 - 0001d19340]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17410]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103800000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19340 - 0001d31340]         BOOTMEM
[    0.000000]   #21 [0001d31340 - 0001d34340]         BOOTMEM
[    0.000000]   #22 [0001d35000 - 0001d36000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #25 [0001d176c0 - 0001d178f0]         BOOTMEM
[    0.000000]   #26 [0001d17900 - 0001d17968]         BOOTMEM
[    0.000000]   #27 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #28 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #29 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #30 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #31 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #32 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #33 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #34 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #35 [0001d17d80 - 0001d17da0]         BOOTMEM
[    0.000000]   #36 [0001d17dc0 - 0001d17de0]         BOOTMEM
[    0.000000]   #37 [0001d17e00 - 0001d17e6a]         BOOTMEM
[    0.000000]   #38 [0001d17e80 - 0001d17eea]         BOOTMEM
[    0.000000]   #39 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #40 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #42 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #43 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #44 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #45 [0001d17f00 - 0001d17f08]         BOOTMEM
[    0.000000]   #46 [0001d17f40 - 0001d17f48]         BOOTMEM
[    0.000000]   #47 [0001d17f80 - 0001d17f98]         BOOTMEM
[    0.000000]   #48 [0001d17fc0 - 0001d17ff0]         BOOTMEM
[    0.000000]   #49 [0001d34340 - 0001d34460]         BOOTMEM
[    0.000000]   #50 [0001d34480 - 0001d344c8]         BOOTMEM
[    0.000000]   #51 [0001d34500 - 0001d34548]         BOOTMEM
[    0.000000]   #52 [0001d36000 - 0001d3e000]         BOOTMEM
[    0.000000]   #53 [0020000000 - 0024000000]         BOOTMEM
[    0.000000]   #54 [0001d34580 - 0001d345a0]         BOOTMEM
[    0.000000]   #55 [0001f5e000 - 0005f5e000]         BOOTMEM
[    0.000000]   #56 [0001d3e000 - 0001d5e000]         BOOTMEM
[    0.000000]   #57 [0001d5e000 - 0001d9e000]         BOOTMEM
[    0.000000]   #58 [000001a800 - 0000022800]         BOOTMEM
[    0.000000] Memory: 3713828k/4718592k available (5708k kernel code, 787336k absent, 217428k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:728
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3399.938 MHz processor.
[    0.020007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6799.86 BogoMIPS (lpj=33999330)
[    0.020010] pid_max: default: 32768 minimum: 301
[    0.020026] Security Framework initialized
[    0.020039] AppArmor: AppArmor initialized
[    0.020040] Yama: becoming mindful.
[    0.020345] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021436] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.021909] Mount-cache hash table entries: 256
[    0.021993] Initializing cgroup subsys ns
[    0.021995] Initializing cgroup subsys cpuacct
[    0.021998] Initializing cgroup subsys memory
[    0.022003] Initializing cgroup subsys devices
[    0.022005] Initializing cgroup subsys freezer
[    0.022006] Initializing cgroup subsys net_cls
[    0.022023] tseg: 0000000000
[    0.022033] CPU: Physical Processor ID: 0
[    0.022034] CPU: Processor Core ID: 0
[    0.022035] mce: CPU supports 6 MCE banks
[    0.022042] Performance Events: AMD PMU driver.
[    0.022045] ... version:                0
[    0.022046] ... bit width:              48
[    0.022047] ... generic registers:      4
[    0.022048] ... value mask:             0000ffffffffffff
[    0.022049] ... max period:             00007fffffffffff
[    0.022050] ... fixed-purpose events:   0
[    0.022051] ... event mask:             000000000000000f
[    0.023192] ACPI: Core revision 20100428
[    0.038988] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038992] ftrace: allocating 22680 entries in 89 pages
[    0.040051] Setting APIC routing to flat
[    0.040345] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.144441] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 03
[    0.150000] Booting Node   0, Processors  #1 #2 #3
[    0.650004] Brought up 4 CPUs
[    0.650006] Total of 4 processors activated (27201.14 BogoMIPS).
[    0.651705] devtmpfs: initialized
[    0.651705] regulator: core version 0.5
[    0.651705] Time: 18:43:47  Date: 11/08/10
[    0.651705] NET: Registered protocol family 16
[    0.651705] node 0 link 0: io port [1000, ffffff]
[    0.651705] TOM: 00000000d0000000 aka 3328M
[    0.651705] Fam 10h mmconf [e0000000, efffffff]
[    0.651705] node 0 link 0: mmio [a0000, bffff]
[    0.651705] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.651705] node 0 link 0: mmio [f0000000, fe6fffff]
[    0.651705] node 0 link 0: mmio [fe700000, fe8fffff]
[    0.651705] node 0 link 0: mmio [fe900000, ffefffff]
[    0.651705] TOM2: 0000000130000000 aka 4864M
[    0.651705] bus: [00, 07] on node 0 link 0
[    0.651705] bus: 00 index 0 [io  0x0000-0xffff]
[    0.651705] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.651705] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.651705] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.651705] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.651705] ACPI: bus type pci registered
[    0.651705] Trying to unpack rootfs image as initramfs...
[    0.651705] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.651705] PCI: not using MMCONFIG
[    0.651705] PCI: Using configuration type 1 for base access
[    0.651705] PCI: Using configuration type 1 for extended access
[    0.651705] bio: create slab <bio-0> at 0
[    0.651705] ACPI: EC: Look up EC in DSDT
[    0.652542] ACPI: Executed 3 blocks of module-level executable AML code
[    0.732176] ACPI: Interpreter enabled
[    0.732180] ACPI: (supports S0 S1 S3 S4 S5)
[    0.732198] ACPI: Using IOAPIC for interrupt routing
[    0.732247] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.734480] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.756007] ACPI Warning: Incorrect checksum in table [OEMB] - 0x8B, should be 0x86 (20100428/tbutils-314)
[    0.756098] ACPI: No dock devices found.
[    0.756101] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.756217] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.756445] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.756446] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.756448] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.756449] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.756451] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.756452] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.756536] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.756538] pci 0000:00:07.0: PME# disabled
[    0.756567] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.756569] pci 0000:00:0a.0: PME# disabled
[    0.756609] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.756614] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.756620] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.756625] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.756631] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.756637] pci 0000:00:11.0: reg 24: [mem 0xfe6ffc00-0xfe6fffff]
[    0.756652] pci 0000:00:11.0: set SATA to AHCI mode
[    0.756691] pci 0000:00:12.0: reg 10: [mem 0xfe6fe000-0xfe6fefff]
[    0.756739] pci 0000:00:12.1: reg 10: [mem 0xfe6fd000-0xfe6fdfff]
[    0.756798] pci 0000:00:12.2: reg 10: [mem 0xfe6ff800-0xfe6ff8ff]
[    0.756844] pci 0000:00:12.2: supports D1 D2
[    0.756845] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.756849] pci 0000:00:12.2: PME# disabled
[    0.756875] pci 0000:00:13.0: reg 10: [mem 0xfe6fc000-0xfe6fcfff]
[    0.756922] pci 0000:00:13.1: reg 10: [mem 0xfe6fb000-0xfe6fbfff]
[    0.756980] pci 0000:00:13.2: reg 10: [mem 0xfe6ff400-0xfe6ff4ff]
[    0.757026] pci 0000:00:13.2: supports D1 D2
[    0.757028] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.757031] pci 0000:00:13.2: PME# disabled
[    0.757126] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.757131] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.757137] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.757142] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.757148] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.757202] pci 0000:00:14.2: reg 10: [mem 0xfe6f4000-0xfe6f7fff 64bit]
[    0.757240] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.757243] pci 0000:00:14.2: PME# disabled
[    0.757335] pci 0000:00:14.5: reg 10: [mem 0xfe6fa000-0xfe6fafff]
[    0.757451] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.757454] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.757457] pci 0000:01:05.0: reg 18: [mem 0xfe8f0000-0xfe8fffff]
[    0.757462] pci 0000:01:05.0: reg 24: [mem 0xfe700000-0xfe7fffff]
[    0.757471] pci 0000:01:05.0: supports D1 D2
[    0.757483] pci 0000:01:05.1: reg 10: [mem 0xfe8e8000-0xfe8ebfff]
[    0.757498] pci 0000:01:05.1: supports D1 D2
[    0.757532] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.757535] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.757537] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.757540] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.757583] pci 0000:02:00.0: reg 10: [mem 0xfe9ff800-0xfe9fffff]
[    0.757591] pci 0000:02:00.0: reg 14: [mem 0xfe9ff400-0xfe9ff47f]
[    0.757612] pci 0000:02:00.0: reg 20: [mem 0xfe9ff000-0xfe9ff07f]
[    0.757619] pci 0000:02:00.0: reg 24: [mem 0xfe9fec00-0xfe9fec7f]
[    0.770017] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.770021] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.770024] pci 0000:00:07.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.770027] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.770073] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.770086] pci 0000:03:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit pref]
[    0.770095] pci 0000:03:00.0: reg 20: [mem 0xfbff8000-0xfbffbfff 64bit pref]
[    0.770100] pci 0000:03:00.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
[    0.770128] pci 0000:03:00.0: supports D1 D2
[    0.770129] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.770133] pci 0000:03:00.0: PME# disabled
[    0.790018] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.790022] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.790024] pci 0000:00:0a.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.790027] pci 0000:00:0a.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.790088] pci 0000:04:06.0: reg 10: [mem 0xfeb00000-0xfebfffff]
[    0.790095] pci 0000:04:06.0: reg 14: [mem 0xfc000000-0xfdffffff pref]
[    0.790196] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.790200] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.790203] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.790207] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfdffffff pref]
[    0.790209] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.790210] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.790212] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.790213] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.790215] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.790216] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.790236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.790402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.790456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.790498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.790554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.793841] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.793928] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.794013] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.794096] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.794179] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.794263] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
[    0.794346] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 *10 11 12 14 15)
[    0.794429] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.794460] HEST: Table is not found!
[    0.794510] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.794512] vgaarb: loaded
[    0.794595] SCSI subsystem initialized
[    0.794612] libata version 3.00 loaded.
[    0.794612] usbcore: registered new interface driver usbfs
[    0.794612] usbcore: registered new interface driver hub
[    0.794612] usbcore: registered new device driver usb
[    0.794612] ACPI: WMI: Mapper loaded
[    0.794612] PCI: Using ACPI for IRQ routing
[    0.794612] PCI: pci_cache_line_size set to 64 bytes
[    0.794612] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.794612] reserve RAM buffer: 00000000cff90000 - 00000000cfffffff 
[    0.794612] NetLabel: Initializing
[    0.794612] NetLabel:  domain hash size = 128
[    0.794612] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.794612] NetLabel:  unlabeled traffic allowed by default
[    0.794612] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.794612] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.794612] Switching to clocksource tsc
[    0.795177] AppArmor: AppArmor Filesystem Enabled
[    0.795177] pnp: PnP ACPI init
[    0.795177] ACPI: bus type pnp registered
[    0.798381] pnp: PnP ACPI: found 14 devices
[    0.798382] ACPI: ACPI bus type pnp unregistered
[    0.798393] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.798395] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.798399] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.798400] system 00:0a: [io  0x040b] has been reserved
[    0.798402] system 00:0a: [io  0x04d6] has been reserved
[    0.798403] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.798405] system 00:0a: [io  0x0c14] has been reserved
[    0.798406] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.798408] system 00:0a: [io  0x0c52] has been reserved
[    0.798409] system 00:0a: [io  0x0c6c] has been reserved
[    0.798411] system 00:0a: [io  0x0c6f] has been reserved
[    0.798412] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.798414] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.798415] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.798417] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.798419] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.798420] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.798422] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.798423] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
[    0.798425] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.798427] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.798428] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.798430] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.798432] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.798433] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.798435] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.798438] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.798439] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.798441] system 00:0b: [io  0x0300-0x030f] has been reserved
[    0.798442] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.798445] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.798448] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.798450] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    0.798451] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.798453] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.798455] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.803768] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.803770] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.803773] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.803775] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.803778] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.803779] pci 0000:00:07.0:   bridge window [io  disabled]
[    0.803781] pci 0000:00:07.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.803783] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.803785] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.803787] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.803789] pci 0000:00:0a.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.803791] pci 0000:00:0a.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.803793] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.803794] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.803799] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.803802] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfdffffff pref]
[    0.803815]   alloc irq_desc for 19 on node 0
[    0.803816]   alloc kstat_irqs on node 0
[    0.803820] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.803823] pci 0000:00:07.0: setting latency timer to 64
[    0.803826]   alloc irq_desc for 18 on node 0
[    0.803827]   alloc kstat_irqs on node 0
[    0.803830] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.803832] pci 0000:00:0a.0: setting latency timer to 64
[    0.803838] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.803839] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.803841] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.803842] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.803843] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.803845] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.803846] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.803848] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
[    0.803849] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.803851] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.803852] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.803854] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.803855] pci_bus 0000:03: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.803857] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.803858] pci_bus 0000:04: resource 2 [mem 0xfc000000-0xfdffffff pref]
[    0.803860] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.803861] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.803862] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.803864] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.803865] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.803867] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.803890] NET: Registered protocol family 2
[    0.803990] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.804818] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.806867] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.807124] TCP: Hash tables configured (established 524288 bind 65536)
[    0.807126] TCP reno registered
[    0.807133] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.807158] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.807244] NET: Registered protocol family 1
[    0.807254] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.937733] Freeing initrd memory: 16296k freed
[    0.972937] pci 0000:01:05.0: Boot video device
[    0.972948] PCI: CLS 64 bytes, default 64
[    0.973667] PCI-DMA: Disabling AGP.
[    0.973755] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.973756] PCI-DMA: using GART IOMMU.
[    0.973759] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.976743] Scanning for low memory corruption every 60 seconds
[    0.976824] audit: initializing netlink socket (disabled)
[    0.976836] type=2000 audit(1289241826.970:1): initialized
[    0.984950] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.985826] VFS: Disk quotas dquot_6.5.2
[    0.985858] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.986218] fuse init (API version 7.14)
[    0.986262] msgmni has been set to 7414
[    0.987760] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.987762] io scheduler noop registered
[    0.987764] io scheduler deadline registered
[    0.987787] io scheduler cfq registered (default)
[    0.987894] pcieport 0000:00:07.0: setting latency timer to 64
[    0.987911]   alloc irq_desc for 40 on node 0
[    0.987912]   alloc kstat_irqs on node 0
[    0.987918] pcieport 0000:00:07.0: irq 40 for MSI/MSI-X
[    0.987978] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.987992]   alloc irq_desc for 41 on node 0
[    0.987992]   alloc kstat_irqs on node 0
[    0.987995] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    0.988041] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.988054] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.988153] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.988156] ACPI: Power Button [PWRB]
[    0.988181] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.988182] ACPI: Power Button [PWRF]
[    0.988384] ACPI: acpi_idle registered with cpuidle
[    0.991852] ERST: Table is not found!
[    0.991976] Linux agpgart interface v0.103
[    0.991978] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.992075] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.992290] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.992879] brd: module loaded
[    0.993157] loop: module loaded
[    0.993296]   alloc irq_desc for 16 on node 0
[    0.993297]   alloc kstat_irqs on node 0
[    0.993301] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.993320] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.993511] Fixed MDIO Bus: probed
[    0.993530] PPP generic driver version 2.4.2
[    0.993555] tun: Universal TUN/TAP device driver, 1.6
[    0.993556] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.993605] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.993631]   alloc irq_desc for 17 on node 0
[    0.993632]   alloc kstat_irqs on node 0
[    0.993634] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.993653] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.993678] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.993706] ehci_hcd 0000:00:12.2: debug port 1
[    0.993723] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe6ff800
[    1.012917] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.013006] hub 1-0:1.0: USB hub found
[    1.013013] hub 1-0:1.0: 6 ports detected
[    1.013094] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.013104] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.013123] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.013145] ehci_hcd 0000:00:13.2: debug port 1
[    1.013162] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe6ff400
[    1.032919] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.032988] hub 2-0:1.0: USB hub found
[    1.032994] hub 2-0:1.0: 6 ports detected
[    1.033051] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.033082] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.033094] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.033114] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.033135] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe6fe000
[    1.084096] hub 3-0:1.0: USB hub found
[    1.084102] hub 3-0:1.0: 3 ports detected
[    1.084178] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.084188] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.084207] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.084221] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe6fd000
[    1.144097] hub 4-0:1.0: USB hub found
[    1.144102] hub 4-0:1.0: 3 ports detected
[    1.144177] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.144189] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.144209] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.144228] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe6fc000
[    1.204101] hub 5-0:1.0: USB hub found
[    1.204106] hub 5-0:1.0: 3 ports detected
[    1.204187] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.204197] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.204217] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.204230] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe6fb000
[    1.264095] hub 6-0:1.0: USB hub found
[    1.264100] hub 6-0:1.0: 3 ports detected
[    1.264177] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.264189] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.264211] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.264224] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe6fa000
[    1.324097] hub 7-0:1.0: USB hub found
[    1.324102] hub 7-0:1.0: 2 ports detected
[    1.324162] uhci_hcd: USB Universal Host Controller Interface driver
[    1.324222] PNP: No PS/2 controller found. Probing ports directly.
[    1.324565] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.324570] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.324626] mice: PS/2 mouse device common for all mice
[    1.324683] rtc_cmos 00:03: RTC can wake from S4
[    1.324703] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.324724] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.324785] device-mapper: uevent: version 1.0.3
[    1.324828] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.324908] device-mapper: multipath: version 1.1.1 loaded
[    1.324910] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.325063] cpuidle: using governor ladder
[    1.325064] cpuidle: using governor menu
[    1.325218] TCP cubic registered
[    1.325284] NET: Registered protocol family 10
[    1.325500] lo: Disabled Privacy Extensions
[    1.325613] NET: Registered protocol family 17
[    1.325654] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor (4 cpu cores) (version 2.20.00)
[    1.325681] powernow-k8:    0 : pstate 0 (3400 MHz)
[    1.325682] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.325683] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.325684] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.326209] PM: Resume from disk failed.
[    1.326215] registered taskstats version 1
[    1.326405]   Magic number: 2:226:746
[    1.326459] rtc_cmos 00:03: setting system clock to 2010-11-08 18:43:48 UTC (1289241828)
[    1.326461] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.326462] EDD information not available.
[    1.326500] Freeing unused kernel memory: 908k freed
[    1.326669] Write protecting the kernel read-only data: 10240k
[    1.326760] Freeing unused kernel memory: 416k freed
[    1.326914] Freeing unused kernel memory: 1644k freed
[    1.337794] udev[139]: starting version 163
[    1.361830] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.361837] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    1.369916] scsi0 : pata_atiixp
[    1.371696] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.371714] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.371751] r8169 0000:03:00.0: setting latency timer to 64
[    1.371780]   alloc irq_desc for 42 on node 0
[    1.371781]   alloc kstat_irqs on node 0
[    1.371791] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.372351] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc900110b8000, 90:e6:ba:6c:61:a1, XID 083000c0 IRQ 42
[    1.372889] [drm] Initialized drm 1.1.0 20060810
[    1.391694] [drm] radeon defaulting to kernel modesetting.
[    1.391696] [drm] radeon kernel modesetting enabled.
[    1.417033] scsi1 : pata_atiixp
[    1.417963] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.417965] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.418001] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.418004] radeon 0000:01:05.0: setting latency timer to 64
[    1.419190] [drm] initializing kernel modesetting (RS880 0x1002:0x9710).
[    1.419202] ahci 0000:00:11.0: version 3.0
[    1.419212]   alloc irq_desc for 22 on node 0
[    1.419214]   alloc kstat_irqs on node 0
[    1.419224] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.419332] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.419334] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.419542] scsi2 : ahci
[    1.419596] scsi3 : ahci
[    1.419636] scsi4 : ahci
[    1.419679] [drm] register mmio base: 0xFE8F0000
[    1.419680] [drm] register mmio size: 65536
[    1.420246] ATOM BIOS: B43106
[    1.420257] [drm] Clocks initialized !
[    1.420268] radeon 0000:01:05.0: VRAM: 368M 0xC0000000 - 0xD6FFFFFF (368M used)
[    1.420270] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[    1.422381] [drm] Detected VRAM RAM=368M, BAR=256M
[    1.422385] [drm] RAM width 32bits DDR
[    1.422429] scsi5 : ahci
[    1.422545] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 22
[    1.422548] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 22
[    1.422550] ata5: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 22
[    1.422553] ata6: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 22
[    1.422606] [TTM] Zone  kernel: Available graphics memory: 1899520 kiB.
[    1.422607] [TTM] Initializing pool allocator.
[    1.422623] [drm] radeon: 368M of VRAM memory ready
[    1.422624] [drm] radeon: 512M of GTT memory ready.
[    1.422660] [drm] radeon: irq initialized.
[    1.422662] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.423206] [drm] Loading RS780 Microcode
[    1.460818] [drm] ring test succeeded in 1 usecs
[    1.460893] [drm] radeon: ib pool ready.
[    1.460937] [drm] ib test succeeded in 0 usecs
[    1.460938] [drm] Enabling audio support
[    1.460943] failed to evaluate ATIF got AE_BAD_PARAMETER
[    1.460944] radeon 0000:01:05.0: Error during ACPI methods call
[    1.460962] [drm] Unknown TV standard; defaulting to NTSC
[    1.461025] [drm] Radeon Display Connectors
[    1.461026] [drm] Connector 0:
[    1.461027] [drm]   VGA
[    1.461029] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    1.461030] [drm]   Encoders:
[    1.461031] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.461032] [drm] Connector 1:
[    1.461032] [drm]   HDMI-A
[    1.461033] [drm]   HPD3
[    1.461034] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    1.461035] [drm]   Encoders:
[    1.461040] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    1.550015] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x0
[    1.564599] [drm] radeon: power management initialized
[    1.692518] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    1.703151] [drm] fb mappable at 0xD0141000
[    1.703153] [drm] vram apper at 0xD0000000
[    1.703154] [drm] size 9216000
[    1.703154] [drm] fb depth is 24
[    1.703155] [drm]    pitch is 7680
[    1.749098] Console: switching to colour frame buffer device 240x75
[    1.768078] fb0: radeondrmfb frame buffer device
[    1.768079] drm: registered panic notifier
[    1.768081] Slow work thread pool: Starting up
[    1.768138] Slow work thread pool: Ready
[    1.768142] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[    1.770886] ata4: SATA link down (SStatus 0 SControl 300)
[    1.771719] ata6: SATA link down (SStatus 0 SControl 300)
[    1.879155] hub 4-2:1.0: USB hub found
[    1.881126] hub 4-2:1.0: 4 ports detected
[    1.950036] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.950800] ata3.00: ATA-8: WDC WD1001FALS-00E8B0, 05.00K05, max UDMA/133
[    1.950802] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.950863] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.951370] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S223L, SB02, max UDMA/100
[    1.951692] ata3.00: configured for UDMA/133
[    1.952085] ata5.00: configured for UDMA/100
[    1.972630] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    1.972733] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.972737] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.972812] sd 2:0:0:0: [sda] Write Protect is off
[    1.972814] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.972837] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.972959]  sda:
[    1.973287] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223L  SB02 PQ: 0 ANSI: 5
[    1.977673] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.977675] Uniform CD-ROM driver Revision: 3.20
[    1.977739] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.977769] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.978361]  sda1 sda2 < sda5 sda6 sda7 >
[    2.020100] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.032564] firewire_core: created device fw0: GUID 001e8c0000b5c769, S400
[    2.202520] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.413119] usbcore: registered new interface driver hiddev
[    2.413197] usbcore: registered new interface driver usbhid
[    2.413199] usbhid: USB HID core driver
[    2.419312] input: MLK 2.4GHz wireless combo sets as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input2
[    2.419364] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK 2.4GHz wireless combo sets] on usb-0000:00:12.1-3/input0
[    2.427174] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
[    2.427557] input: MLK 2.4GHz wireless combo sets as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input3
[    2.427635] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK 2.4GHz wireless combo sets] on usb-0000:00:12.1-3/input1
[    2.503184] usb 4-2.2: new full speed USB device using ohci_hcd and address 4
[    2.639224] hub 4-2.2:1.0: USB hub found
[    2.641195] hub 4-2.2:1.0: 4 ports detected
[    7.901601] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   13.381604] udev[483]: starting version 163
[   13.407595] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [bus b00-b0f 64bit pref disabled]
[   13.407598] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.422841] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.424246] lp: driver loaded but no devices found
[   13.431619] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   13.447365] EDAC amd64_edac:  Ver: 3.3.0 Sep 19 2010
[   13.456770] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   13.456777] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.456778]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.456779]  (Note that use of the override may cause unknown side effects.)
[   13.456793] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   13.465850] parport_pc 00:06: reported by Plug and Play ACPI
[   13.465902] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.474172] ppdev: user-space parallel port driver
[   13.505073] type=1400 audit(1289259840.673:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=775 comm="apparmor_parser"
[   13.505248] type=1400 audit(1289259840.673:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=775 comm="apparmor_parser"
[   13.505347] type=1400 audit(1289259840.673:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=775 comm="apparmor_parser"
[   13.507641] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.542651] lp0: using parport0 (interrupt-driven).
[   13.584431] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.584469] HDA Intel 0000:01:05.1: setting latency timer to 64
[   14.071212] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   14.217448] type=1400 audit(1289259841.383:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=992 comm="apparmor_parser"
[   14.217627] type=1400 audit(1289259841.383:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=992 comm="apparmor_parser"
[   14.217728] type=1400 audit(1289259841.383:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=992 comm="apparmor_parser"
[   14.237744] type=1400 audit(1289259841.403:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=996 comm="apparmor_parser"
[   14.239991] type=1400 audit(1289259841.403:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=991 comm="apparmor_parser"
[   14.255352] type=1400 audit(1289259841.423:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=995 comm="apparmor_parser"
[   14.255579] type=1400 audit(1289259841.423:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=995 comm="apparmor_parser"

---

### Post by entropy51 on 2010-11-16
I figured it out, just needed to configure my internal hardware.

Thanks!

---

### Post by goldcaddy77 on 2011-02-11
> **entropy51 said:**
> I figured it out, just needed to configure my internal hardware.

Thanks!

Entropy, what did you mean by this?  What was your solution?

Thanks,

Dan

---

