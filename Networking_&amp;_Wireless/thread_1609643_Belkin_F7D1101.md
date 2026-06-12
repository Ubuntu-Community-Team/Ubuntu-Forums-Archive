---
title: "Belkin F7D1101"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by Omomtia23 on 2010-10-30
Hi 
I am new to Linux and use Xubuntu 10.10, but the usb wireless adapter won't run. 
I followed the instructions on
[http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101&page=2](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101&page=2), but nothing happens.

---

### Post by P4man on 2010-10-30
nothing happens is kinda vague, I assume you managed to follow the instructions without errors or problems?

Anyway, googling around it appears the above instructions would no longer be needed as a driver would be included in the current kernel, all that is needed is the firmware. Have a look here:

[https://wiki.archlinux.org/index.php/Wireless#rtl8192s](https://wiki.archlinux.org/index.php/Wireless#rtl8192s)

Instruction are for Arch linux but should work for (x)ubuntu too I think. Just note that commands preceded by a # have to be run as root, so either put "sudo" before them or enter a root shell by typing

```
sudo -i
```

then copy paste those commands.

---

### Post by Omomtia23 on 2010-10-31
Thanks, I tried this and copied the firmware to /lib/firmware/RTL8192SU, which I found in the folder RTL8192SE of the downloadpackage from 
[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

the tar command works withouth errormessage. But the green light on the device 
still doesnt light up after restart. 
The usb adapter is listed with lsusb.
Did I use the wrong firmware?

---

### Post by P4man on 2010-10-31
can you post the output of

```
lshw -C network

```
and

```
sudo rfkill list
```

---

### Post by Omomtia23 on 2010-10-31
This is the outpur of the first command: 
lshw -C network                                 
  *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 00
       serial: 00:a0:d2:15:02:02
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
       resources: irq:18 ioport:d400(size=32)
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:0b:6a:6d:da:0e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:bc00(size=256) memory:dfffbd00-dfffbdff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:4c:00:00:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g/n

and for lsusb:


lsusb
Bus 005 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by P4man on 2010-10-31
dont forget the rfkill command

---

### Post by Omomtia23 on 2010-10-31
sudo rfkill list gives no output

---

### Post by P4man on 2010-10-31
hmm.. doesnt look too good. Can you attach the contents of /var/log/dmesg ?

---

### Post by Omomtia23 on 2010-10-31
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d6000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 base 0E0000000 mask FFC000000 write-combining
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d6000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  modified: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  modified: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000fff0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000fff0000 page 4k
[    0.000000] kernel direct mapping tables up to fff0000 @ 15000-1a000
[    0.000000] RAMDISK: 0b5f0000 - 0c034000
[    0.000000] ACPI: RSDP 000fa8c0 00014 (v00 AMI   )
[    0.000000] ACPI: RSDT 0fff0000 0002C (v01 AMIINT VIA_K7   00000010 MSFT 00000097)
[    0.000000] ACPI: FACP 0fff0030 00081 (v01 AMIINT VIA_K7   00000011 MSFT 00000097)
[    0.000000] ACPI: DSDT 0fff0120 03502 (v01    VIA    K7VT4 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 0fff8000 00040
[    0.000000] ACPI: APIC 0fff00c0 00054 (v01 AMIINT VIA_K7   00000009 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 0 - 0fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65407
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d6000
[    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64895
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=10f3ab0d-9056-4d2a-88cd-556a3213cae5 ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1310080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (41 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [000b5f0000 - 000c034000]         RAMDISK
[    0.000000]   #4 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a1000 - 00009a408d]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001201000]         BOOTMEM
[    0.000000]   #11 [0001201000 - 0001201004]         BOOTMEM
[    0.000000]   #12 [0001201040 - 0001201100]         BOOTMEM
[    0.000000]   #13 [0001201100 - 0001201118]         BOOTMEM
[    0.000000]   #14 [0001201140 - 0001201d40]         BOOTMEM
[    0.000000]   #15 [0001201d40 - 0001201d67]         BOOTMEM
[    0.000000]   #16 [0001201d80 - 0001201eb4]         BOOTMEM
[    0.000000]   #17 [0001201ec0 - 0001201f00]         BOOTMEM
[    0.000000]   #18 [0001201f00 - 0001201f40]         BOOTMEM
[    0.000000]   #19 [0001201f40 - 0001201f80]         BOOTMEM
[    0.000000]   #20 [0001201f80 - 0001201fc0]         BOOTMEM
[    0.000000]   #21 [0001201fc0 - 0001202000]         BOOTMEM
[    0.000000]   #22 [0001202000 - 0001202040]         BOOTMEM
[    0.000000]   #23 [0001202040 - 0001202080]         BOOTMEM
[    0.000000]   #24 [0001202080 - 00012020c0]         BOOTMEM
[    0.000000]   #25 [00012020c0 - 0001202100]         BOOTMEM
[    0.000000]   #26 [0001202100 - 0001202140]         BOOTMEM
[    0.000000]   #27 [0001202140 - 0001202150]         BOOTMEM
[    0.000000]   #28 [0001202180 - 00012021ea]         BOOTMEM
[    0.000000]   #29 [0001202200 - 000120226a]         BOOTMEM
[    0.000000]   #30 [0001400000 - 000140e000]         BOOTMEM
[    0.000000]   #31 [0001204280 - 0001204284]         BOOTMEM
[    0.000000]   #32 [00012042c0 - 00012042c4]         BOOTMEM
[    0.000000]   #33 [0001204300 - 0001204304]         BOOTMEM
[    0.000000]   #34 [0001204340 - 0001204344]         BOOTMEM
[    0.000000]   #35 [0001204380 - 0001204430]         BOOTMEM
[    0.000000]   #36 [0001204440 - 00012044e8]         BOOTMEM
[    0.000000]   #37 [0001202280 - 0001203280]         BOOTMEM
[    0.000000]   #38 [0001204500 - 0001224500]         BOOTMEM
[    0.000000]   #39 [0001224500 - 0001234500]         BOOTMEM
[    0.000000]   #40 [0001235000 - 0001374d80]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 238644k/262080k available (4928k kernel code, 22984k reserved, 2336k data, 684k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd07f0000 - 0xff7fe000   ( 752 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1832.812 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3665.62 BogoMIPS (lpj=7331248)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004056] Security Framework initialized
[    0.008039] AppArmor: AppArmor initialized
[    0.008043] Yama: becoming mindful.
[    0.008137] Mount-cache hash table entries: 512
[    0.008349] Initializing cgroup subsys ns
[    0.008357] Initializing cgroup subsys cpuacct
[    0.008364] Initializing cgroup subsys memory
[    0.008378] Initializing cgroup subsys devices
[    0.008383] Initializing cgroup subsys freezer
[    0.008387] Initializing cgroup subsys net_cls
[    0.008429] mce: CPU supports 4 MCE banks
[    0.008457] Performance Events: AMD PMU driver.
[    0.008486] ... version:                0
[    0.008489] ... bit width:              48
[    0.008492] ... generic registers:      4
[    0.008496] ... value mask:             0000ffffffffffff
[    0.008500] ... max period:             00007fffffffffff
[    0.008503] ... fixed-purpose events:   0
[    0.008506] ... event mask:             000000000000000f
[    0.009363] SMP alternatives: switching to UP code
[    0.018707] Freeing SMP alternatives: 24k freed
[    0.018761] ACPI: Core revision 20100428
[    0.026246] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.026259] ftrace: allocating 21758 entries in 43 pages
[    0.028176] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.029256] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071184] CPU0: AMD Sempron(tm) 2600+ stepping 01
[    0.072000] Brought up 1 CPUs
[    0.072000] Total of 1 processors activated (3665.62 BogoMIPS).
[    0.072000] devtmpfs: initialized
[    0.072000] regulator: core version 0.5
[    0.072000] Time: 13:19:15  Date: 10/31/10
[    0.072000] NET: Registered protocol family 16
[    0.072000] EISA bus registered
[    0.072000] ACPI: bus type pci registered
[    0.074301] PCI: PCI BIOS revision 2.10 entry at 0xfda71, last bus=1
[    0.074305] PCI: Using configuration type 1 for base access
[    0.075730] bio: create slab <bio-0> at 0
[    0.076664] ACPI: EC: Look up EC in DSDT
[    0.082028] ACPI: Interpreter enabled
[    0.082033] ACPI: (supports S0 S1 S4 S5)
[    0.082060] ACPI: Using IOAPIC for interrupt routing
[    0.088222] ACPI: Power Resource [URP1] (off)
[    0.088259] ACPI: Power Resource [URP2] (off)
[    0.088302] ACPI: Power Resource [FDDP] (off)
[    0.088337] ACPI: Power Resource [LPTP] (off)
[    0.088513] ACPI: No dock devices found.
[    0.088519] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.088696] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.088951] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.088955] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.088960] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.088963] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.088967] pci_root PNP0A03:00: host bridge window [mem 0x10000000-0xffdfffff] (ignored)
[    0.088971] pci_root PNP0A03:00: host bridge window [mem 0xfee01000-0xffdfffff] (ignored)
[    0.089003] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe3ffffff pref]
[    0.089094] pci 0000:00:01.0: supports D1
[    0.089125] pci 0000:00:0a.0: reg 10: [io  0xd400-0xd41f]
[    0.089185] pci 0000:00:0f.0: reg 10: [io  0xec00-0xec07]
[    0.089192] pci 0000:00:0f.0: reg 14: [io  0xe800-0xe803]
[    0.089199] pci 0000:00:0f.0: reg 18: [io  0xe400-0xe407]
[    0.089206] pci 0000:00:0f.0: reg 1c: [io  0xe000-0xe003]
[    0.089213] pci 0000:00:0f.0: reg 20: [io  0xdc00-0xdc0f]
[    0.089220] pci 0000:00:0f.0: reg 24: [io  0xd800-0xd8ff]
[    0.089284] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.089361] pci 0000:00:10.0: reg 20: [io  0xc400-0xc41f]
[    0.089386] pci 0000:00:10.0: supports D1 D2
[    0.089389] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089395] pci 0000:00:10.0: PME# disabled
[    0.089438] pci 0000:00:10.1: reg 20: [io  0xc800-0xc81f]
[    0.089462] pci 0000:00:10.1: supports D1 D2
[    0.089465] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089470] pci 0000:00:10.1: PME# disabled
[    0.089513] pci 0000:00:10.2: reg 20: [io  0xcc00-0xcc1f]
[    0.089537] pci 0000:00:10.2: supports D1 D2
[    0.089540] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089544] pci 0000:00:10.2: PME# disabled
[    0.089588] pci 0000:00:10.3: reg 20: [io  0xd000-0xd01f]
[    0.089612] pci 0000:00:10.3: supports D1 D2
[    0.089614] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089619] pci 0000:00:10.3: PME# disabled
[    0.089648] pci 0000:00:10.4: reg 10: [mem 0xdfffbe00-0xdfffbeff]
[    0.089687] pci 0000:00:10.4: supports D1 D2
[    0.089689] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089694] pci 0000:00:10.4: PME# disabled
[    0.089751] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.089801] pci 0000:00:11.5: reg 10: [io  0xc000-0xc0ff]
[    0.089842] pci 0000:00:11.5: supports D1 D2
[    0.089874] pci 0000:00:12.0: reg 10: [io  0xbc00-0xbcff]
[    0.089881] pci 0000:00:12.0: reg 14: [mem 0xdfffbd00-0xdfffbdff]
[    0.089917] pci 0000:00:12.0: supports D1 D2
[    0.089919] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089924] pci 0000:00:12.0: PME# disabled
[    0.089988] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.089995] pci 0000:01:00.0: reg 14: [io  0xa800-0xa8ff]
[    0.090001] pci 0000:01:00.0: reg 18: [mem 0xdfef0000-0xdfefffff]
[    0.090016] pci 0000:01:00.0: reg 30: [mem 0xdfec0000-0xdfedffff pref]
[    0.090034] pci 0000:01:00.0: supports D1 D2
[    0.090059] pci 0000:01:00.1: reg 10: [mem 0xb0000000-0xbfffffff pref]
[    0.090066] pci 0000:01:00.1: reg 14: [mem 0xdfee0000-0xdfeeffff]
[    0.090093] pci 0000:01:00.1: supports D1 D2
[    0.090129] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.090135] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.090140] pci 0000:00:01.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.090146] pci 0000:00:01.0:   bridge window [mem 0x9fd00000-0xdfcfffff pref]
[    0.090154] pci_bus 0000:00: on NUMA node 0
[    0.090160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.106555] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.106678] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.106797] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.106915] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.107034] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.107153] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.107272] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.107390] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.107438] HEST: Table is not found!
[    0.107586] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.107590] vgaarb: loaded
[    0.107863] SCSI subsystem initialized
[    0.108011] libata version 3.00 loaded.
[    0.108102] usbcore: registered new interface driver usbfs
[    0.108121] usbcore: registered new interface driver hub
[    0.108167] usbcore: registered new device driver usb
[    0.108386] ACPI: WMI: Mapper loaded
[    0.108390] PCI: Using ACPI for IRQ routing
[    0.108397] PCI: pci_cache_line_size set to 32 bytes
[    0.108468] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.108473] reserve RAM buffer: 000000000fff0000 - 000000000fffffff 
[    0.108635] NetLabel: Initializing
[    0.108639] NetLabel:  domain hash size = 128
[    0.108641] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.108666] NetLabel:  unlabeled traffic allowed by default
[    0.108737] Switching to clocksource tsc
[    0.123845] AppArmor: AppArmor Filesystem Enabled
[    0.123882] pnp: PnP ACPI init
[    0.123920] ACPI: bus type pnp registered
[    0.127488] pnp: PnP ACPI: found 12 devices
[    0.127492] ACPI: ACPI bus type pnp unregistered
[    0.127498] PnPBIOS: Disabled by ACPI PNP
[    0.127520] system 00:05: [io  0x0295-0x0296] has been reserved
[    0.127525] system 00:05: [io  0x03f0-0x03f1] has been reserved
[    0.127529] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.127533] system 00:05: [io  0x0400-0x040f] has been reserved
[    0.127536] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.127542] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.127546] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.164222] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.164229] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.164237] pci 0000:00:01.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.164242] pci 0000:00:01.0:   bridge window [mem 0x9fd00000-0xdfcfffff pref]
[    0.164261] pci 0000:00:01.0: setting latency timer to 64
[    0.164267] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.164270] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.164274] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.164278] pci_bus 0000:01: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.164281] pci_bus 0000:01: resource 2 [mem 0x9fd00000-0xdfcfffff pref]
[    0.164356] NET: Registered protocol family 2
[    0.164453] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.164729] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.164862] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.164987] TCP: Hash tables configured (established 8192 bind 8192)
[    0.164991] TCP reno registered
[    0.164995] UDP hash table entries: 128 (order: 0, 4096 bytes)
[    0.165011] UDP-Lite hash table entries: 128 (order: 0, 4096 bytes)
[    0.165112] NET: Registered protocol family 1
[    0.165133] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.165241] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.165255] pci 0000:01:00.0: Boot video device
[    0.165262] PCI: CLS 32 bytes, default 32
[    0.165618] cpufreq-nforce2: No nForce2 chipset.
[    0.165663] Scanning for low memory corruption every 60 seconds
[    0.165824] audit: initializing netlink socket (disabled)
[    0.165843] type=2000 audit(1288531155.160:1): initialized
[    0.177803] Trying to unpack rootfs image as initramfs...
[    0.191722] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.197314] VFS: Disk quotas dquot_6.5.2
[    0.197407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.203479] fuse init (API version 7.14)
[    0.203683] msgmni has been set to 466
[    0.211717] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.211724] io scheduler noop registered
[    0.211727] io scheduler deadline registered
[    0.211751] io scheduler cfq registered (default)
[    0.211934] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.211968] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.212263] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.212274] ACPI: Power Button [PWRB]
[    0.212353] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.212367] ACPI: Sleep Button [SLPB]
[    0.212437] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.212442] ACPI: Power Button [PWRF]
[    0.212639] ACPI: acpi_idle registered with cpuidle
[    0.215033] ERST: Table is not found!
[    0.215446] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.215575] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.215905] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.217661] brd: module loaded
[    0.218426] loop: module loaded
[    0.218882]   alloc irq_desc for 20 on node -1
[    0.218886]   alloc kstat_irqs on node -1
[    0.218902] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.219012] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.223393] isapnp: Scanning for PnP cards...
[    0.229214] Fixed MDIO Bus: probed
[    0.229273] PPP generic driver version 2.4.2
[    0.229396] tun: Universal TUN/TAP device driver, 1.6
[    0.229400] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.229551] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.229602]   alloc irq_desc for 21 on node -1
[    0.229606]   alloc kstat_irqs on node -1
[    0.229619] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.229648] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.229701] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.229802] ehci_hcd 0000:00:10.4: irq 21, io mem 0xdfffbe00
[    0.279183] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.279494] hub 1-0:1.0: USB hub found
[    0.279504] hub 1-0:1.0: 8 ports detected
[    0.279618] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.279645] uhci_hcd: USB Universal Host Controller Interface driver
[    0.279737] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.279751] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.279812] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.279845] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c400
[    0.280029] hub 2-0:1.0: USB hub found
[    0.280038] hub 2-0:1.0: 2 ports detected
[    0.280116] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.280124] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.280184] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.280207] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c800
[    0.280385] hub 3-0:1.0: USB hub found
[    0.280392] hub 3-0:1.0: 2 ports detected
[    0.280473] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.280482] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.280534] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.280560] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000cc00
[    0.280743] hub 4-0:1.0: USB hub found
[    0.280750] hub 4-0:1.0: 2 ports detected
[    0.280815] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.280824] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.280876] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.280900] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d000
[    0.281070] hub 5-0:1.0: USB hub found
[    0.281076] hub 5-0:1.0: 2 ports detected
[    0.281228] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.287529] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.287552] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.287829] mice: PS/2 mouse device common for all mice
[    0.288089] rtc_cmos 00:07: RTC can wake from S4
[    0.288158] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.288214] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.288394] device-mapper: uevent: version 1.0.3
[    0.288582] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.291422] device-mapper: multipath: version 1.1.1 loaded
[    0.291431] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.291764] EISA: Probing bus 0 at eisa.0
[    0.291808] EISA: Detected 0 cards.
[    0.299523] cpuidle: using governor ladder
[    0.299532] cpuidle: using governor menu
[    0.299990] TCP cubic registered
[    0.300232] NET: Registered protocol family 10
[    0.300689] lo: Disabled Privacy Extensions
[    0.300951] NET: Registered protocol family 17
[    0.301022] powernow-k8: Processor cpuid 681 not supported
[    0.301058] Using IPI No-Shortcut mode
[    0.301241] PM: Resume from disk failed.
[    0.301272] registered taskstats version 1
[    0.301522]   Magic number: 14:5:333
[    0.301577] tty tty54: hash matches
[    0.301689] rtc_cmos 00:07: setting system clock to 2010-10-31 13:19:15 UTC (1288531155)
[    0.301694] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.301696] EDD information not available.
[    0.309919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.894780] isapnp: No Plug & Play device found
[    0.931230] Freeing initrd memory: 10512k freed
[    0.949442] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    0.949504] Freeing unused kernel memory: 684k freed
[    0.950822] Write protecting the kernel text: 4932k
[    0.950864] Write protecting the kernel read-only data: 1976k
[    0.986294] udev[63]: starting version 163
[    1.092137] usb 5-2: not running at top speed; connect to a high speed hub
[    1.255667] Floppy drive(s): fd0 is 1.44M
[    1.287854] pata_via 0000:00:0f.1: version 0.3.4
[    1.287886] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.301482] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[    1.327294] FDC 0 is a post-1991 82077
[    1.348545] scsi0 : pata_via
[    1.358597] scsi1 : pata_via
[    1.361875] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.361880] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.362077]   alloc irq_desc for 18 on node -1
[    1.362081]   alloc kstat_irqs on node -1
[    1.362095] ne2k-pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.362787] eth0: RealTek RTL-8029 found at 0xd400, IRQ 18, 00:a0:d2:15:02:02.
[    1.362814] sata_via 0000:00:0f.0: version 2.6
[    1.362832] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.362903] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.374639] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.380860] scsi2 : sata_via
[    1.390538] scsi3 : sata_via
[    1.390654] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 20
[    1.390659] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 20
[    1.390822]   alloc irq_desc for 23 on node -1
[    1.390826]   alloc kstat_irqs on node -1
[    1.390840] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.391594] eth1: VIA Rhine II at 0xdfffbd00, 00:0b:6a:6d:da:0e, IRQ 23.
[    1.392355] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.524471] ata1.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
[    1.524478] ata1.00: 156368016 sectors, multi 16: LBA48 
[    1.532319] ata1.00: configured for UDMA/100
[    1.532517] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
[    1.532812] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.533082] sd 0:0:0:0: [sda] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.533171] sd 0:0:0:0: [sda] Write Protect is off
[    1.533175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.533214] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.533460]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.595756] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.596033] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.696786] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-M1912, TM00, max UDMA/33
[    1.696824] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-4120B, A102, max UDMA/33
[    1.704361] ata2.00: configured for UDMA/33
[    1.720240] ata2.01: configured for UDMA/33
[    1.723077] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1912 TM00 PQ: 0 ANSI: 5
[    1.725504] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.725512] Uniform CD-ROM driver Revision: 3.20
[    1.726195] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.726412] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.730948] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4120B A102 PQ: 0 ANSI: 5
[    1.735763] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.736405] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.736624] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.940011] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.668394] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.852797] Adding 746984k swap on /dev/sda7.  Priority:-1 extents:1 across:746984k 
[   13.237253] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   14.310833] udev[373]: starting version 163
[   14.773526] type=1400 audit(1288527569.966:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=408 comm="apparmor_parser"
[   14.773909] type=1400 audit(1288527569.966:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=408 comm="apparmor_parser"
[   14.774153] type=1400 audit(1288527569.966:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=408 comm="apparmor_parser"
[   15.141483] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.271136] parport_pc 00:03: reported by Plug and Play ACPI
[   15.271245] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   15.273636] Linux agpgart interface v0.103
[   15.387042] lp0: using parport0 (interrupt-driven).
[   15.403910] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   15.405893] psmouse serio1: ID: 10 00 64
[   15.475319] logips2pp: Detected unknown logitech mouse model 62
[   15.592927] ppdev: user-space parallel port driver
[   15.599443] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   15.625945] gameport gameport0: NS558 PnP Gameport is pnp00:04/gameport0, io 0x200, speed 1011kHz
[   15.650555] ieee80211_crypt: registered algorithm 'NULL'
[   15.650563] ieee80211_crypt: registered algorithm 'TKIP'
[   15.650566] ieee80211_crypt: registered algorithm 'CCMP'
[   15.650569] ieee80211_crypt: registered algorithm 'WEP'
[   15.650572] 
[   15.650573] Linux kernel driver for RTL8192 based WLAN cards
[   15.650575] Copyright (c) 2007-2008, Realsil Wlan
[   15.653909] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   15.699146] [drm] Initialized drm 1.1.0 20060810
[   15.829676] rtl819xU:EEPROM ID is invalid(is 0x0(should be 0x8129)
[   15.829681] 
[   15.829689] Dot11d_Init()
[   15.829698] End of initendpoints
[   15.830555] usbcore: registered new interface driver rtl819xU
[   16.005244] [drm] radeon defaulting to kernel modesetting.
[   16.005253] [drm] radeon kernel modesetting enabled.
[   16.005354]   alloc irq_desc for 16 on node -1
[   16.005358]   alloc kstat_irqs on node -1
[   16.005371] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.018228] [drm] initializing kernel modesetting (RV350 0x1002:0x4150).
[   16.018359] [drm] register mmio base: 0xDFEF0000
[   16.018362] [drm] register mmio size: 65536
[   16.019351] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   16.019562] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   16.019623] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   16.019632] radeon 0000:01:00.0: GTT: 64M 0xE0000000 - 0xE3FFFFFF
[   16.019638] [drm] Generation 2 PCI interface, using max accessible memory
[   16.019644] radeon 0000:01:00.0: VRAM: 128M 0xC0000000 - 0xC7FFFFFF (128M used)
[   16.019737] [drm] radeon: irq initialized.
[   16.019893] [drm] Detected VRAM RAM=128M, BAR=256M
[   16.019901] [drm] RAM width 128bits DDR
[   16.021070] [TTM] Zone  kernel: Available graphics memory: 124932 kiB.
[   16.021074] [TTM] Initializing pool allocator.
[   16.021115] [drm] radeon: 128M of VRAM memory ready
[   16.021119] [drm] radeon: 64M of GTT memory ready.
[   16.021178] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   16.021270] [drm] Loading R300 Microcode
[   16.047510] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   16.226560] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[   16.226565] 
[   16.226569] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!
[   16.226571] 
[   16.311337] rtl819xU:request firmware fail!
[   16.311340] 
[   16.311345] rtl819xU:ERR in init_firmware()
[   16.311346] 
[   16.311350] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.311352] 
[   16.311355] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.311356] 
[   16.318467] [drm] radeon: ring at 0x00000000E0000000
[   16.318493] [drm] ring test succeeded in 0 usecs
[   16.318847] [drm] radeon: ib pool ready.
[   16.318975] [drm] ib test succeeded in 0 usecs
[   16.319182] [drm] Default TV standard: PAL
[   16.319185] [drm] 27.000000000 MHz TV ref clk
[   16.319191] [drm] DFP table revision: 3
[   16.319271] [drm] Default TV standard: PAL
[   16.319273] [drm] 27.000000000 MHz TV ref clk
[   16.319311] [drm] Radeon Display Connectors
[   16.319314] [drm] Connector 0:
[   16.319316] [drm]   VGA
[   16.319320] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   16.319322] [drm]   Encoders:
[   16.319325] [drm]     CRT1: INTERNAL_DAC1
[   16.319327] [drm] Connector 1:
[   16.319329] [drm]   DVI-I
[   16.319331] [drm]   HPD1
[   16.319334] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   16.319336] [drm]   Encoders:
[   16.319338] [drm]     CRT2: INTERNAL_DAC2
[   16.319340] [drm]     DFP1: INTERNAL_TMDS1
[   16.319343] [drm] Connector 2:
[   16.319344] [drm]   S-video
[   16.319346] [drm]   Encoders:
[   16.319348] [drm]     TV1: INTERNAL_DAC2
[   16.337317] eth1: link down
[   16.343115] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.677141] [drm] fb mappable at 0xC0040000
[   16.677149] [drm] vram apper at 0xC0000000
[   16.677152] [drm] size 5242880
[   16.677154] [drm] fb depth is 24
[   16.677156] [drm]    pitch is 5120
[   16.764223] Console: switching to colour frame buffer device 160x64
[   16.790799] fb0: radeondrmfb frame buffer device
[   16.790802] drm: registered panic notifier
[   16.810447] Slow work thread pool: Starting up
[   16.810557] Slow work thread pool: Ready
[   16.810574] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   16.906413] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[   16.906418] 
[   16.906422] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!
[   16.906424] 
[   16.947871] rtl819xU:request firmware fail!
[   16.947874] 
[   16.947878] rtl819xU:ERR in init_firmware()
[   16.947880] 
[   16.947884] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.947885] 
[   16.947888] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.947890] 
[   17.234479] type=1400 audit(1288527572.426:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=744 comm="apparmor_parser"
[   17.234862] type=1400 audit(1288527572.426:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=744 comm="apparmor_parser"
[   17.235110] type=1400 audit(1288527572.426:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=744 comm="apparmor_parser"
[   17.543235] type=1400 audit(1288527572.734:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=746 comm="apparmor_parser"
[   17.549509] type=1400 audit(1288527572.742:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=746 comm="apparmor_parser"
[   17.557051] type=1400 audit(1288527572.750:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=746 comm="apparmor_parser"
[   17.676780] type=1400 audit(1288527572.870:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=750 comm="apparmor_parser"
[   17.695517]   alloc irq_desc for 22 on node -1
[   17.695523]   alloc kstat_irqs on node -1
[   17.695537] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   17.695709] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64

```

---

### Post by P4man on 2010-10-31
Turns out rtl8192su and rtl8192u are different chips requiring different firmware. Im not sure where to find it. I guess this is where I suggest you try ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Omomtia23 on 2010-10-31
Ok, thanks anyway. I might try another usb adapter with better linux compatibility..

---

### Post by pwnjangles on 2011-09-25
I don't understand why this usb works on Ubuntu 11.04 right when you plug it in but not Xubuntu 11.04 I thought they support the same hardware?

---

