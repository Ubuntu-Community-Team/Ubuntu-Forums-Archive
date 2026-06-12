---
title: "No monitor with NVIDIA driver"
date: 2011-01-10
forum: Mythbuntu
---

### Post by linuxhippy on 2011-01-10
I almost got my new install of mythbuntu 10.10 working on a Dell P4 with NVIDIA video PCIE.  It was working for about 10 minutes into a show with the installed open source graphics driver.  After about 10 minutes the screen froze and the only way to reboot the system was ssh with another networked pc.  I went into /var/log/mythtv/mythfrontend.log and saw that there was a video buffering error during the "freeze".

So, I decided that I should try the proprietary NVIDIA graphics driver which was available from the mythbuntu repo.  I installed and when it rebooted could not detect my monitor (I have no TV).  The computer is running fine as I can still ssh into my system...but that's all CLI so I have no idea of how to remove the NVIDIA driver or fix my freezing problem.

I never had this happen in 10.04 on the same computer setup using the NVIDIA proprietary driver.

EDIT:

Oh, there is no xorg.conf in /etc/X11 to just comment out the NVIDIA settings.

---

### Post by 4dognight on 2011-01-10
There isnt an xorg.conf file created by default anymore. But if you have one it will use it. If you have your config file from before you can try to use it. 

Also, look in /var/log/kern.log for any other error msgs related to lack of memory. When I upgraded t 10.10 I had to allocate more memory at boot time for my nvidia driver. There was a msg in kern.log about it.

---

### Post by BicyclerBoy on 2011-01-11
We would need to see the file

/var/log/Xorg.0.log

& stdout from
dmesg

This info needs to be collected after installing nvidia driver & restarting the X server.

---

### Post by linuxhippy on 2011-01-11
there's a lot of info in each-here's dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe8cc00 (usable)
[    0.000000]  BIOS-e820: 000000003fe8cc00 - 000000003fe8ec00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe8ec00 - 000000003fe90c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe90c00 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3fe8c max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fe8cc00 (usable)
[    0.000000]  modified: 000000003fe8cc00 - 000000003fe8ec00 (ACPI NVS)
[    0.000000]  modified: 000000003fe8ec00 - 000000003fe90c00 (ACPI data)
[    0.000000]  modified: 000000003fe90c00 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 2f4e5000 - 2ff2a000
[    0.000000] ACPI: RSDP 000febf0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fccbc 0003C (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: FACP 000fccf8 00074 (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: DSDT fffc6692 02AEE (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3fe8cc00 00040
[    0.000000] ACPI: SSDT fffc92bd 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fcd6c 00072 (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 000fcdde 00028 (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: MCFG 000fce06 0003E (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: HPET 000fce44 00038 (v01 DELL    8400    00000007 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 134MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fe8c
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0003fe8c
[    0.000000] On node 0 totalpages: 261661
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3953 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 270 pages used for memmap
[    0.000000]   HighMem zone: 34176 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259615
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=c5e3167a-5b90-46c4-bd25-739a802ba71c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5235420 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (53 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [002f4e5000 - 002ff2a000]         RAMDISK
[    0.000000]   #4 [00009a3000 - 00009a6164]             BRK
[    0.000000]   #5 [00000fe720 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000fe710 - 00000fe720]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000f0000]   BIOS reserved
[    0.000000]   #8 [00000f0218 - 00000fe710]   BIOS reserved
[    0.000000]   #9 [00000f0000 - 00000f0218]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
[    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
[    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
[    0.000000]   #17 [0001801100 - 0001801154]         BOOTMEM
[    0.000000]   #18 [0001801180 - 0001804180]         BOOTMEM
[    0.000000]   #19 [0001804180 - 0001804190]         BOOTMEM
[    0.000000]   #20 [00018041c0 - 0001804dc0]         BOOTMEM
[    0.000000]   #21 [0001804dc0 - 0001804de5]         BOOTMEM
[    0.000000]   #22 [0001804e00 - 0001804e27]         BOOTMEM
[    0.000000]   #23 [0001804e40 - 0001804fc8]         BOOTMEM
[    0.000000]   #24 [0001805000 - 0001805040]         BOOTMEM
[    0.000000]   #25 [0001805040 - 0001805080]         BOOTMEM
[    0.000000]   #26 [0001805080 - 00018050c0]         BOOTMEM
[    0.000000]   #27 [00018050c0 - 0001805100]         BOOTMEM
[    0.000000]   #28 [0001805100 - 0001805140]         BOOTMEM
[    0.000000]   #29 [0001805140 - 0001805180]         BOOTMEM
[    0.000000]   #30 [0001805180 - 00018051c0]         BOOTMEM
[    0.000000]   #31 [00018051c0 - 0001805200]         BOOTMEM
[    0.000000]   #32 [0001805200 - 0001805240]         BOOTMEM
[    0.000000]   #33 [0001805240 - 0001805280]         BOOTMEM
[    0.000000]   #34 [0001805280 - 00018052c0]         BOOTMEM
[    0.000000]   #35 [00018052c0 - 00018052d0]         BOOTMEM
[    0.000000]   #36 [0001805300 - 0001805310]         BOOTMEM
[    0.000000]   #37 [0001805340 - 00018053aa]         BOOTMEM
[    0.000000]   #38 [00018053c0 - 000180542a]         BOOTMEM
[    0.000000]   #39 [0001c00000 - 0001c0e000]         BOOTMEM
[    0.000000]   #40 [0001d00000 - 0001d0e000]         BOOTMEM
[    0.000000]   #41 [0001e00000 - 0001e0e000]         BOOTMEM
[    0.000000]   #42 [0001f00000 - 0001f0e000]         BOOTMEM
[    0.000000]   #43 [0001807440 - 0001807444]         BOOTMEM
[    0.000000]   #44 [0001807480 - 0001807484]         BOOTMEM
[    0.000000]   #45 [00018074c0 - 00018074d0]         BOOTMEM
[    0.000000]   #46 [0001807500 - 0001807510]         BOOTMEM
[    0.000000]   #47 [0001807540 - 00018075e0]         BOOTMEM
[    0.000000]   #48 [0001807600 - 0001807648]         BOOTMEM
[    0.000000]   #49 [0001807680 - 000180b680]         BOOTMEM
[    0.000000]   #50 [000180b680 - 000188b680]         BOOTMEM
[    0.000000]   #51 [000188b680 - 00018cb680]         BOOTMEM
[    0.000000]   #52 [0001f0e000 - 000240c2dc]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fe8c)
[    0.000000] Memory: 1012892k/1047088k available (4931k kernel code, 33752k reserved, 2333k data, 688k init, 137784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0ebe   (4931 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3192.267 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.53 BogoMIPS (lpj=12769068)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004040] Security Framework initialized
[    0.004060] AppArmor: AppArmor initialized
[    0.004063] Yama: becoming mindful.
[    0.004135] Mount-cache hash table entries: 512
[    0.004304] Initializing cgroup subsys ns
[    0.004309] Initializing cgroup subsys cpuacct
[    0.004316] Initializing cgroup subsys memory
[    0.004327] Initializing cgroup subsys devices
[    0.004330] Initializing cgroup subsys freezer
[    0.004333] Initializing cgroup subsys net_cls
[    0.004374] CPU: Physical Processor ID: 0
[    0.004377] CPU: Processor Core ID: 0
[    0.004380] mce: CPU supports 4 MCE banks
[    0.004393] CPU0: Thermal monitoring enabled (TM1)
[    0.004398] using mwait in idle threads.
[    0.004406] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.004418] ... version:                0
[    0.004420] ... bit width:              40
[    0.004422] ... generic registers:      18
[    0.004425] ... value mask:             000000ffffffffff
[    0.004428] ... max period:             0000007fffffffff
[    0.004430] ... fixed-purpose events:   0
[    0.004432] ... event mask:             000000000003ffff
[    0.011624] ACPI: Core revision 20100428
[    0.042217] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.042224] ftrace: allocating 21756 entries in 43 pages
[    0.044068] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084651] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.088000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.176019] Brought up 2 CPUs
[    0.176025] Total of 2 processors activated (12768.55 BogoMIPS).
[    0.176430] devtmpfs: initialized
[    0.177423] regulator: core version 0.5
[    0.177450] Time: 10:50:58  Date: 01/11/11
[    0.177500] NET: Registered protocol family 16
[    0.177512] Trying to unpack rootfs image as initramfs...
[    0.177713] EISA bus registered
[    0.177728] ACPI: bus type pci registered
[    0.177832] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.177839] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.177843] PCI: Using MMCONFIG for extended config space
[    0.177846] PCI: Using configuration type 1 for base access
[    0.180741] bio: create slab <bio-0> at 0
[    0.181597] ACPI: EC: Look up EC in DSDT
[    0.202494] ACPI: Interpreter enabled
[    0.202505] ACPI: (supports S0 S1 S3 S4 S5)
[    0.202554] ACPI: Using IOAPIC for interrupt routing
[    0.240921] ACPI: No dock devices found.
[    0.240932] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.244166] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.250612] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.250619] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.250624] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.250630] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.250636] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.250761] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.250767] pci 0000:00:01.0: PME# disabled
[    0.250888] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.250895] pci 0000:00:1c.0: PME# disabled
[    0.250990] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.250997] pci 0000:00:1c.1: PME# disabled
[    0.251063] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
[    0.251127] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
[    0.251191] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
[    0.251254] pci 0000:00:1d.3: reg 20: [io  0xff20-0xff3f]
[    0.251317] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.251382] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.251389] pci 0000:00:1d.7: PME# disabled
[    0.251532] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.251540] pci 0000:00:1f.0: quirk: [io  0x0880-0x08bf] claimed by ICH6 GPIO
[    0.251547] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0c00-0c7f
[    0.251554] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 00e0-00ef
[    0.251586] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.251596] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.251605] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.251615] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.251625] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.251677] pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
[    0.251686] pci 0000:00:1f.2: reg 14: [io  0xfe10-0xfe13]
[    0.251695] pci 0000:00:1f.2: reg 18: [io  0xfe20-0xfe27]
[    0.251704] pci 0000:00:1f.2: reg 1c: [io  0xfe30-0xfe33]
[    0.251714] pci 0000:00:1f.2: reg 20: [io  0xfea0-0xfeaf]
[    0.251723] pci 0000:00:1f.2: reg 24: [mem 0xdffffc00-0xdfffffff]
[    0.251751] pci 0000:00:1f.2: PME# supported from D3hot
[    0.251757] pci 0000:00:1f.2: PME# disabled
[    0.251819] pci 0000:00:1f.3: reg 20: [io  0xece0-0xecff]
[    0.251922] pci 0000:01:00.0: reg 10: [mem 0xde000000-0xdeffffff]
[    0.251937] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.251951] pci 0000:01:00.0: reg 1c: [mem 0xdc000000-0xddffffff 64bit]
[    0.251960] pci 0000:01:00.0: reg 24: [io  0xdc80-0xdcff]
[    0.251970] pci 0000:01:00.0: reg 30: [mem 0xdfe00000-0xdfe1ffff pref]
[    0.260035] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.260044] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.260051] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdfefffff]
[    0.260058] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.260167] pci 0000:02:00.0: reg 10: [mem 0xdbff0000-0xdbffffff 64bit]
[    0.260259] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.260267] pci 0000:02:00.0: PME# disabled
[    0.260290] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.260305] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.260312] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.260319] pci 0000:00:1c.0:   bridge window [mem 0xdbf00000-0xdbffffff]
[    0.260330] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260389] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.260398] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.260405] pci 0000:00:1c.1:   bridge window [mem 0xdbe00000-0xdbefffff]
[    0.260415] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260488] pci 0000:04:00.0: reg 10: [mem 0xd5000000-0xd5ffffff]
[    0.260592] pci 0000:04:00.1: reg 10: [mem 0xd6000000-0xd6ffffff]
[    0.260687] pci 0000:04:00.2: reg 10: [mem 0xd7000000-0xd7ffffff]
[    0.260795] pci 0000:04:01.0: reg 10: [mem 0xd8000000-0xd8ffffff]
[    0.260899] pci 0000:04:01.1: reg 10: [mem 0xd9000000-0xd9ffffff]
[    0.260996] pci 0000:04:01.2: reg 10: [mem 0xda000000-0xdaffffff]
[    0.261100] pci 0000:04:02.0: reg 10: [io  0xccc0-0xccff]
[    0.261161] pci 0000:04:02.0: supports D1 D2
[    0.261199] pci 0000:04:02.1: reg 10: [io  0xccb8-0xccbf]
[    0.261259] pci 0000:04:02.1: supports D1 D2
[    0.261299] pci 0000:04:02.2: reg 10: [mem 0xdbdfb800-0xdbdfbfff]
[    0.261311] pci 0000:04:02.2: reg 14: [mem 0xdbdfc000-0xdbdfffff]
[    0.261370] pci 0000:04:02.2: supports D1 D2
[    0.261375] pci 0000:04:02.2: PME# supported from D0 D1 D2 D3hot
[    0.261382] pci 0000:04:02.2: PME# disabled
[    0.261456] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.261465] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.261473] pci 0000:00:1e.0:   bridge window [mem 0xd5000000-0xdbdfffff]
[    0.261483] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.261488] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.261493] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.261520] pci_bus 0000:00: on NUMA node 0
[    0.261535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.262041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.262637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.262911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[    0.263191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.546361] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.546775] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.547188] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.547603] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.548035] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.548451] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.548869] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.549285] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.549420] HEST: Table is not found!
[    0.549563] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.549582] vgaarb: loaded
[    0.549912] SCSI subsystem initialized
[    0.550054] libata version 3.00 loaded.
[    0.550152] usbcore: registered new interface driver usbfs
[    0.550177] usbcore: registered new interface driver hub
[    0.550221] usbcore: registered new device driver usb
[    0.550486] ACPI: WMI: Mapper loaded
[    0.550490] PCI: Using ACPI for IRQ routing
[    0.550496] PCI: pci_cache_line_size set to 64 bytes
[    0.550662] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.550667] reserve RAM buffer: 000000003fe8cc00 - 000000003fffffff 
[    0.550837] NetLabel: Initializing
[    0.550841] NetLabel:  domain hash size = 128
[    0.550844] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.550864] NetLabel:  unlabeled traffic allowed by default
[    0.550927] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.550935] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.550945] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.556230] Switching to clocksource tsc
[    0.575684] AppArmor: AppArmor Filesystem Enabled
[    0.575709] pnp: PnP ACPI init
[    0.575747] ACPI: bus type pnp registered
[    0.580803] pnp 00:01: disabling [io  0x0800-0x085f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.580811] pnp 00:01: disabling [io  0x0860-0x08ff] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.601716] pnp: PnP ACPI: found 11 devices
[    0.601721] ACPI: ACPI bus type pnp unregistered
[    0.601728] PnPBIOS: Disabled by ACPI PNP
[    0.601748] system 00:01: [io  0x0c00-0x0c7f] has been reserved
[    0.601765] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.601772] system 00:08: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.601778] system 00:08: [mem 0x01000000-0x3fe8cbff] could not be reserved
[    0.601784] system 00:08: [mem 0x000c0000-0x000fffff] could not be reserved
[    0.601791] system 00:08: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.601796] system 00:08: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.601802] system 00:08: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.601808] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.601814] system 00:08: [mem 0xffc00000-0xffffffff] has been reserved
[    0.601825] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.601830] system 00:09: [mem 0xfeda0000-0xfedacfff] has been reserved
[    0.639618] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
[    0.639626] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.639633] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.639639] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.639645] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.639652] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.639659] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdfefffff]
[    0.639665] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.639674] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.639679] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.639687] pci 0000:00:1c.0:   bridge window [mem 0xdbf00000-0xdbffffff]
[    0.639694] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
[    0.639703] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.639709] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.639716] pci 0000:00:1c.1:   bridge window [mem 0xdbe00000-0xdbefffff]
[    0.639724] pci 0000:00:1c.1:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.639734] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.639740] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.639748] pci 0000:00:1e.0:   bridge window [mem 0xd5000000-0xdbdfffff]
[    0.639754] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.639777]   alloc irq_desc for 16 on node -1
[    0.639781]   alloc kstat_irqs on node -1
[    0.639792] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.639799] pci 0000:00:01.0: setting latency timer to 64
[    0.639815] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.639822] pci 0000:00:1c.0: setting latency timer to 64
[    0.639836]   alloc irq_desc for 17 on node -1
[    0.639840]   alloc kstat_irqs on node -1
[    0.639848] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.639855] pci 0000:00:1c.1: setting latency timer to 64
[    0.639866] pci 0000:00:1e.0: setting latency timer to 64
[    0.639873] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.639877] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.639882] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.639887] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdfefffff]
[    0.639892] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.639897] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.639902] pci_bus 0000:02: resource 1 [mem 0xdbf00000-0xdbffffff]
[    0.639906] pci_bus 0000:02: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.639911] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.639916] pci_bus 0000:03: resource 1 [mem 0xdbe00000-0xdbefffff]
[    0.639921] pci_bus 0000:03: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.639926] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.639931] pci_bus 0000:04: resource 1 [mem 0xd5000000-0xdbdfffff]
[    0.639935] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.639940] pci_bus 0000:04: resource 5 [mem 0x00000000-0xffffffff]
[    0.640004] NET: Registered protocol family 2
[    0.640139] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.640591] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.641211] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.641544] TCP: Hash tables configured (established 131072 bind 65536)
[    0.641550] TCP reno registered
[    0.641557] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.641571] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.641746] NET: Registered protocol family 1
[    0.641913] pci 0000:01:00.0: Boot video device
[    0.641953] PCI: CLS 64 bytes, default 64
[    0.641992] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.641996] Simple Boot Flag at 0x7a set to 0x1
[    0.642274] cpufreq-nforce2: No nForce2 chipset.
[    0.642327] Scanning for low memory corruption every 60 seconds
[    0.642552] audit: initializing netlink socket (disabled)
[    0.642576] type=2000 audit(1294743057.636:1): initialized
[    0.655623] highmem bounce pool size: 64 pages
[    0.655633] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.658610] VFS: Disk quotas dquot_6.5.2
[    0.658742] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.660005] fuse init (API version 7.14)
[    0.660183] msgmni has been set to 1709
[    0.660685] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.660691] io scheduler noop registered
[    0.660694] io scheduler deadline registered
[    0.660723] io scheduler cfq registered (default)
[    0.660941] pcieport 0000:00:01.0: setting latency timer to 64
[    0.660981]   alloc irq_desc for 40 on node -1
[    0.660985]   alloc kstat_irqs on node -1
[    0.660999] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.661103] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.661145]   alloc irq_desc for 41 on node -1
[    0.661149]   alloc kstat_irqs on node -1
[    0.661160] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.661296] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.661340]   alloc irq_desc for 42 on node -1
[    0.661345]   alloc kstat_irqs on node -1
[    0.661357] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.661546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.661670] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.662000] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.662011] ACPI: Power Button [VBTN]
[    0.662112] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.662119] ACPI: Power Button [PWRF]
[    0.662684] ACPI: acpi_idle registered with cpuidle
[    0.692182] ERST: Table is not found!
[    0.692558] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.692697] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.693291] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.695702] brd: module loaded
[    0.696815] loop: module loaded
[    0.697173] ata_piix 0000:00:1f.1: version 2.13
[    0.697193] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.697250] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.697369] scsi0 : ata_piix
[    0.697527] scsi1 : ata_piix
[    0.697600] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.697605] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.697637]   alloc irq_desc for 20 on node -1
[    0.697641]   alloc kstat_irqs on node -1
[    0.697651] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.697674] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.697796] isapnp: Scanning for PnP cards...
[    0.753996] Freeing initrd memory: 10516k freed
[    0.760324] ata2: port disabled. ignoring.
[    0.851183] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.851300] scsi2 : ata_piix
[    0.851423] scsi3 : ata_piix
[    0.851487] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    0.851493] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    0.852105] Fixed MDIO Bus: probed
[    0.852169] PPP generic driver version 2.4.2
[    0.852271] tun: Universal TUN/TAP device driver, 1.6
[    0.852274] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.852425] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.852455]   alloc irq_desc for 21 on node -1
[    0.852459]   alloc kstat_irqs on node -1
[    0.852469] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.852491] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.852497] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.852553] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.852588] ehci_hcd 0000:00:1d.7: debug port 1
[    0.856474] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.856497] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    0.871268] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.871466] hub 1-0:1.0: USB hub found
[    0.871474] hub 1-0:1.0: 8 ports detected
[    0.871613] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.871640] uhci_hcd: USB Universal Host Controller Interface driver
[    0.871692] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.871702] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.871707] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.871763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.871793] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    0.871994] hub 2-0:1.0: USB hub found
[    0.872002] hub 2-0:1.0: 2 ports detected
[    0.872105]   alloc irq_desc for 22 on node -1
[    0.872109]   alloc kstat_irqs on node -1
[    0.872117] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.872125] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.872130] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.872185] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.872224] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    0.872413] hub 3-0:1.0: USB hub found
[    0.872420] hub 3-0:1.0: 2 ports detected
[    0.872523]   alloc irq_desc for 18 on node -1
[    0.872527]   alloc kstat_irqs on node -1
[    0.872534] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.872542] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.872547] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.872604] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.872643] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.872835] hub 4-0:1.0: USB hub found
[    0.872842] hub 4-0:1.0: 2 ports detected
[    0.872946]   alloc irq_desc for 23 on node -1
[    0.872949]   alloc kstat_irqs on node -1
[    0.872956] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.872965] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.872971] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.873027] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.873066] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    0.873264] hub 5-0:1.0: USB hub found
[    0.873271] hub 5-0:1.0: 2 ports detected
[    0.873478] PNP: No PS/2 controller found. Probing ports directly.
[    0.876289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.876300] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.876407] mice: PS/2 mouse device common for all mice
[    0.876585] rtc_cmos 00:05: RTC can wake from S4
[    0.876652] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.876682] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.876875] device-mapper: uevent: version 1.0.3
[    0.877046] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.877144] device-mapper: multipath: version 1.1.1 loaded
[    0.877149] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.877353] EISA: Probing bus 0 at eisa.0
[    0.877361] Cannot allocate resource for EISA slot 1
[    0.877366] Cannot allocate resource for EISA slot 2
[    0.877392] EISA: Detected 0 cards.
[    0.877503] cpuidle: using governor ladder
[    0.877507] cpuidle: using governor menu
[    0.878119] TCP cubic registered
[    0.878370] NET: Registered protocol family 10
[    0.879049] lo: Disabled Privacy Extensions
[    0.879553] NET: Registered protocol family 17
[    0.879619] Using IPI No-Shortcut mode
[    0.879760] PM: Resume from disk failed.
[    0.879777] registered taskstats version 1
[    0.880190]   Magic number: 11:640:830
[    0.880274] rtc_cmos 00:05: setting system clock to 2011-01-11 10:50:58 UTC (1294743058)
[    0.880279] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.880282] EDD information not available.
[    0.907567] ata1.00: ATAPI: SONY DVD-ROM DDU1615, FYS1, max UDMA/33
[    0.915480] ata1.00: configured for UDMA/33
[    1.028777] ata3.00: ATA-6: WDC WD2500JD-75HBB0, 08.02D08, max UDMA/133
[    1.028783] ata3.00: 488281250 sectors, multi 8: LBA48 
[    1.045985] ata3.00: configured for UDMA/133
[    1.051167] isapnp: No Plug & Play device found
[    1.051767] scsi 0:0:0:0: CD-ROM            SONY     DVD-ROM DDU1615  FYS1 PQ: 0 ANSI: 5
[    1.053687] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    1.053690] Uniform CD-ROM driver Revision: 3.20
[    1.053824] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.053904] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.054085] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JD-75H 08.0 PQ: 0 ANSI: 5
[    1.054248] sd 2:0:0:0: [sda] 488281250 512-byte logical blocks: (250 GB/232 GiB)
[    1.054283] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.054376] sd 2:0:0:0: [sda] Write Protect is off
[    1.054381] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.054431] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.054691]  sda: sda1 sda2 sda3 sda4
[    1.095254] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.095273] Freeing unused kernel memory: 688k freed
[    1.095782] Write protecting the kernel text: 4932k
[    1.095838] Write protecting the kernel read-only data: 1980k
[    1.122028] udev[82]: starting version 163
[    1.308109] tg3.c:v3.110 (April 9, 2010)
[    1.308142] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.308156] tg3 0000:02:00.0: setting latency timer to 64
[    1.339847] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:11:11:5b:3f:ab
[    1.339856] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.339862] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.339868] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.350074]   alloc irq_desc for 19 on node -1
[    1.350081]   alloc kstat_irqs on node -1
[    1.350093] firewire_ohci 0000:04:02.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.404027] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.404062] firewire_ohci: Added fw-ohci device 0000:04:02.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x0
[    1.608189] usbcore: registered new interface driver hiddev
[    1.608376] usbcore: registered new interface driver usbhid
[    1.608381] usbhid: USB HID core driver
[    1.627916] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2
[    1.628120] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-1/input0
[    1.659060] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    1.660957] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input3
[    1.661266] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-1/input1
[    1.904134] firewire_core: created device fw0: GUID 00023c019100189c, S400
[    6.684839] EXT3-fs (sda1): recovery required on readonly filesystem
[    6.684845] EXT3-fs (sda1): write access will be enabled during recovery
[    6.685000] EXT3-fs: barriers not enabled
[    6.952249] kjournald starting.  Commit interval 5 seconds
[    6.952277] EXT3-fs (sda1): orphan cleanup on readonly fs
[    6.952286] ext3_orphan_cleanup: deleting unreferenced inode 495975
[    6.952314] ext3_orphan_cleanup: deleting unreferenced inode 495974
[    6.952325] ext3_orphan_cleanup: deleting unreferenced inode 495973
[    6.952334] ext3_orphan_cleanup: deleting unreferenced inode 495972
[    6.952344] ext3_orphan_cleanup: deleting unreferenced inode 495964
[    6.952353] EXT3-fs (sda1): 5 orphan inodes deleted
[    6.952358] EXT3-fs (sda1): recovery complete
[    6.960856] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   19.291319] udev[293]: starting version 163
[   19.425232] Adding 1951892k swap on /dev/sda3.  Priority:-1 extents:1 across:1951892k 
[   19.449584] intel_rng: Firmware space is locked read-only. If you can't or
[   19.449589] intel_rng: don't want to disable this in firmware setup, and if
[   19.449593] intel_rng: you are certain that your system has a functional
[   19.449597] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   19.550197] lp: driver loaded but no devices found
[   19.563530] Linux agpgart interface v0.103
[   19.784399] EXT3-fs (sda1): using internal journal
[   19.801392] gameport gameport0: EMU10K1 is pci0000:04:02.1/gameport0, io 0xccb8, speed 458kHz
[   19.809527] Linux video capture interface: v2.00
[   19.825878] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.827896] dell-wmi-aio: No known WMI GUID found
[   19.845490] parport_pc 00:06: reported by Plug and Play ACPI
[   19.845555] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   19.891311] IR NEC protocol handler initialized
[   19.923722] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   19.929187] lp0: using parport0 (interrupt-driven).
[   19.952421] IR RC5(x) protocol handler initialized
[   19.956118] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   19.956716] ppdev: user-space parallel port driver
[   19.970909] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   19.970917] cx88[0]: TV tuner type 76, Radio tuner type -1
[   19.983872] IR RC6 protocol handler initialized
[   20.029526] IR JVC protocol handler initialized
[   20.062239] type=1400 audit(1294743077.679:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=538 comm="apparmor_parser"
[   20.063054] type=1400 audit(1294743077.679:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[   20.063505] type=1400 audit(1294743077.679:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[   20.064327] type=1400 audit(1294743077.683:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=552 comm="apparmor_parser"
[   20.065142] type=1400 audit(1294743077.683:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=552 comm="apparmor_parser"
[   20.065594] type=1400 audit(1294743077.683:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=552 comm="apparmor_parser"
[   20.075241] IR Sony protocol handler initialized
[   20.079182] type=1400 audit(1294743077.695:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=568 comm="apparmor_parser"
[   20.084472] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.097082] type=1400 audit(1294743077.715:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=570 comm="apparmor_parser"
[   20.142078] cx2388x alsa driver version 0.0.8 loaded
[   20.142558] lirc_dev: IR Remote Control driver registered, major 249 
[   20.145774] IR LIRC bridge handler initialized
[   20.161657] nvidia: module license 'NVIDIA' taints kernel.
[   20.161663] Disabling lock debugging due to kernel taint
[   20.162556] tuner 0-0064: chip found @ 0xc8 (cx88[0])
[   20.359252] JFS: nTxBlock = 8000, nTxLock = 64006
[   20.362969] xc5000 0-0064: creating new instance
[   20.363952] xc5000: Successfully identified at address 0x64
[   20.363956] xc5000: Firmware has not been loaded previously
[   20.363963] cx88[0]: Calling XC5000 callback
[   20.420520] Registered IR keymap rc-pinnacle-pctv-hd
[   20.420678] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/rc/rc0/input4
[   20.420770] rc0: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/rc/rc0
[   20.420776] cx88[0]/2: cx2388x 8802 Driver Manager
[   20.420797] cx88-mpeg driver manager 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.420810] cx88[0]/2: found at 0000:04:00.2, rev: 5, irq: 16, latency: 64, mmio: 0xd7000000
[   20.429929] cx88[1]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   20.429936] cx88[1]: TV tuner type 76, Radio tuner type -1
[   20.541348] RPC: Registered udp transport module.
[   20.541354] RPC: Registered tcp transport module.
[   20.541357] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   20.567106] tuner 1-0064: chip found @ 0xc8 (cx88[1])
[   20.607153] xc5000 1-0064: creating new instance
[   20.608134] xc5000: Successfully identified at address 0x64
[   20.608137] xc5000: Firmware has not been loaded previously
[   20.608143] cx88[1]: Calling XC5000 callback
[   20.610450] Registered IR keymap rc-pinnacle-pctv-hd
[   20.610798] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:04:01.2/rc/rc1/input5
[   20.610982] rc1: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:04:01.2/rc/rc1
[   20.610988] cx88[1]/2: cx2388x 8802 Driver Manager
[   20.611008] cx88-mpeg driver manager 0000:04:01.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.611022] cx88[1]/2: found at 0000:04:01.2, rev: 5, irq: 17, latency: 64, mmio: 0xda000000
[   20.611082] cx8800 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.611093] cx88[0]/0: found at 0000:04:00.0, rev: 5, irq: 16, latency: 64, mmio: 0xd5000000
[   20.611176] cx88[0]/0: registered device video0 [v4l2]
[   20.611228] cx88[0]/0: registered device vbi0
[   20.613267] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   20.635286] xc5000: firmware read 12401 bytes.
[   20.635291] xc5000: firmware uploading...
[   20.635296] cx88[0]: Calling XC5000 callback
[   20.644336] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   20.644342] cx88/2: registering cx8802 driver, type: dvb access: shared
[   20.644349] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   20.644354] cx88[0]/2: cx2388x based DVB/ATSC card
[   20.644357] cx8802_alloc_frontends() allocating 1 frontend(s)
[   20.756244] xc5000 0-0064: attaching existing instance
[   20.757245] xc5000: Successfully identified at address 0x64
[   20.757248] xc5000: Firmware has not been loaded previously
[   20.757906] cx88[0]: Calling XC5000 callback
[   20.758559] DVB: registering new adapter (cx88[0])
[   20.758565] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   21.184985] nf_conntrack version 0.5.0 (16001 buckets, 64004 max)
[   21.187693] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   21.187700] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   21.187704] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   21.306142] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   22.118235] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.118250] nvidia 0000:01:00.0: setting latency timer to 64
[   22.118257] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.119214] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   22.222680] Slow work thread pool: Starting up
[   22.237849] Slow work thread pool: Ready
[   22.238023] FS-Cache: Loaded
[   22.316653] FS-Cache: Netfs 'nfs' registered for caching
[   22.358068] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   22.486782] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.522398] type=1400 audit(1294743080.139:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=920 comm="apparmor_parser"
[   22.523150] type=1400 audit(1294743080.139:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=920 comm="apparmor_parser"
[   22.639180] svc: failed to register lockdv1 RPC service (errno 97).
[   22.640727] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.655800] NFSD: starting 90-second grace period
[   23.244511] xc5000: firmware upload complete...
[   23.836699] cx88[1]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   23.836707] cx88[1]/2: cx2388x based DVB/ATSC card
[   23.836712] cx8802_alloc_frontends() allocating 1 frontend(s)
[   23.836785] cx8800 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.836799] cx88[1]/0: found at 0000:04:01.0, rev: 5, irq: 17, latency: 64, mmio: 0xd8000000
[   23.836928] cx88[1]/0: registered device video1 [v4l2]
[   23.836981] cx88[1]/0: registered device vbi1
[   23.840846] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   23.843530] xc5000: firmware read 12401 bytes.
[   23.843535] xc5000: firmware uploading...
[   23.843539] cx88[1]: Calling XC5000 callback
[   24.085622] xc5000 1-0064: attaching existing instance
[   24.086618] xc5000: Successfully identified at address 0x64
[   24.086623] xc5000: Firmware has not been loaded previously
[   24.087289] cx88[1]: Calling XC5000 callback
[   24.087950] DVB: registering new adapter (cx88[1])
[   24.087957] DVB: registering adapter 1 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   24.215461] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   24.215470] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[   25.992011] xc5000: firmware upload complete...
[   26.586939] cx88_audio 0000:04:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.586991] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   26.587258] cx88_audio 0000:04:01.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.587301] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   26.587726] EMU10K1_Audigy 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.596245] Installing spdif_bug patch: SB Audigy 2 [SB0350b]
[   26.604557] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.236949] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   30.301168] cx88[0]: Calling XC5000 callback
[   31.552681] cx88[1]: Calling XC5000 callback
[   32.288982] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   36.860440] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   36.860543] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   36.976514] eth0: no IPv6 routers present
[   37.066564] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   37.324789] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   40.325931] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   43.338242] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   43.338309] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   43.338925] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
[   50.463657] NVRM: Xid (0001:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005

---

### Post by linuxhippy on 2011-01-11
and here's the Xorg file:

[    28.731] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    28.731] X Protocol Version 11, Revision 0
[    28.731] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    28.731] Current Operating System: Linux FreeVo 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    28.731] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=c5e3167a-5b90-46c4-bd25-739a802ba71c ro quiet splash
[    28.731] Build Date: 23 November 2010  09:54:06PM
[    28.731] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.731] Current version of pixman: 0.18.4
[    28.731] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    28.732] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.732] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 11 05:32:30 2011
[    28.732] (==) Using config file: "/etc/X11/xorg.conf"
[    28.732] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.844] (==) No Layout section.  Using the first Screen section.
[    28.845] (**) |-->Screen "Default Screen" (0)
[    28.845] (**) |   |-->Monitor "<default monitor>"
[    28.845] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    28.845] (**) |   |-->Device "Default Device"
[    28.845] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    28.845] (==) Automatically adding devices
[    28.845] (==) Automatically enabling devices
[    28.845] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.845] 	Entry deleted from font path.
[    28.845] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    28.845] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.845] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.845] (II) Loader magic: 0x81f8e00
[    28.845] (II) Module ABI versions:
[    28.845] 	X.Org ANSI C Emulation: 0.4
[    28.845] 	X.Org Video Driver: 8.0
[    28.845] 	X.Org XInput driver : 11.0
[    28.845] 	X.Org Server Extension : 4.0
[    28.847] (--) PCI:*(0:1:0:0) 10de:0422:1019:1808 rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/131072
[    28.847] (--) PCI: (0:4:0:0) 14f1:8800:11bd:0051 rev 5, Mem @ 0xd5000000/16777216
[    28.847] (--) PCI: (0:4:1:0) 14f1:8800:11bd:0051 rev 5, Mem @ 0xd8000000/16777216
[    28.847] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.847] (II) "extmod" will be loaded by default.
[    28.847] (II) "dbe" will be loaded by default.
[    28.848] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    28.848] (II) "record" will be loaded by default.
[    28.848] (II) "dri" will be loaded by default.
[    28.848] (II) "dri2" will be loaded by default.
[    28.848] (II) LoadModule: "glx"
[    28.859] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    29.649] (II) Module glx: vendor="NVIDIA Corporation"
[    29.661] 	compiled for 4.0.2, module version = 1.0.0
[    29.661] 	Module class: X.Org Server Extension
[    29.662] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    29.662] (II) Loading extension GLX
[    29.662] (II) LoadModule: "extmod"
[    29.662] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.662] (II) Module extmod: vendor="X.Org Foundation"
[    29.662] 	compiled for 1.9.0, module version = 1.0.0
[    29.662] 	Module class: X.Org Server Extension
[    29.662] 	ABI class: X.Org Server Extension, version 4.0
[    29.662] (II) Loading extension MIT-SCREEN-SAVER
[    29.662] (II) Loading extension XFree86-VidModeExtension
[    29.662] (II) Loading extension XFree86-DGA
[    29.662] (II) Loading extension DPMS
[    29.663] (II) Loading extension XVideo
[    29.663] (II) Loading extension XVideo-MotionCompensation
[    29.663] (II) Loading extension X-Resource
[    29.663] (II) LoadModule: "dbe"
[    29.663] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.663] (II) Module dbe: vendor="X.Org Foundation"
[    29.663] 	compiled for 1.9.0, module version = 1.0.0
[    29.663] 	Module class: X.Org Server Extension
[    29.663] 	ABI class: X.Org Server Extension, version 4.0
[    29.663] (II) Loading extension DOUBLE-BUFFER
[    29.663] (II) LoadModule: "record"
[    29.664] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.664] (II) Module record: vendor="X.Org Foundation"
[    29.664] 	compiled for 1.9.0, module version = 1.13.0
[    29.664] 	Module class: X.Org Server Extension
[    29.664] 	ABI class: X.Org Server Extension, version 4.0
[    29.664] (II) Loading extension RECORD
[    29.664] (II) LoadModule: "dri"
[    29.664] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.665] (II) Module dri: vendor="X.Org Foundation"
[    29.665] 	compiled for 1.9.0, module version = 1.0.0
[    29.665] 	ABI class: X.Org Server Extension, version 4.0
[    29.665] (II) Loading extension XFree86-DRI
[    29.665] (II) LoadModule: "dri2"
[    29.665] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.665] (II) Module dri2: vendor="X.Org Foundation"
[    29.665] 	compiled for 1.9.0, module version = 1.2.0
[    29.665] 	ABI class: X.Org Server Extension, version 4.0
[    29.665] (II) Loading extension DRI2
[    29.665] (II) LoadModule: "nvidia"
[    29.665] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    29.724] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.724] 	compiled for 4.0.2, module version = 1.0.0
[    29.724] 	Module class: X.Org Video Driver
[    29.759] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    29.773] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    29.774] (++) using VT number 7

[    29.797] (II) Loading sub module "fb"
[    29.797] (II) LoadModule: "fb"
[    29.798] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.798] (II) Module fb: vendor="X.Org Foundation"
[    29.798] 	compiled for 1.9.0, module version = 1.0.0
[    29.798] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.798] (II) Loading sub module "wfb"
[    29.798] (II) LoadModule: "wfb"
[    29.798] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    29.798] (II) Module wfb: vendor="X.Org Foundation"
[    29.798] 	compiled for 1.9.0, module version = 1.0.0
[    29.798] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.798] (II) Loading sub module "ramdac"
[    29.798] (II) LoadModule: "ramdac"
[    29.799] (II) Module "ramdac" already built-in
[    29.849] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    29.864] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    29.864] (==) NVIDIA(0): RGB weight 888
[    29.864] (==) NVIDIA(0): Default visual is TrueColor
[    29.864] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.864] (**) NVIDIA(0): Option "NoLogo" "True"
[    29.865] (**) NVIDIA(0): Enabling RENDER acceleration
[    29.880] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    29.880] (II) NVIDIA(0):     enabled.
[    30.870] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G86) at PCI:1:0:0 (GPU-0)
[    30.870] (--) NVIDIA(0): Memory: 524288 kBytes
[    30.870] (--) NVIDIA(0): VideoBIOS: 60.86.4a.00.75
[    30.870] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    30.870] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    30.870] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0
[    30.871] (--) NVIDIA(0):     Acer P244W (CRT-1)
[    30.871] (--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
[    30.871] (--) NVIDIA(0): Acer P244W (CRT-1): 400.0 MHz maximum pixel clock
[    30.871] (--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
[    30.871] (--) NVIDIA(0): TV encoder: NVIDIA
[    30.939] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    30.939] (==) NVIDIA(0): 
[    30.939] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    30.939] (==) NVIDIA(0):     will be used as the requested mode.
[    30.939] (==) NVIDIA(0): 
[    30.939] (II) NVIDIA(0): Validated modes:
[    30.939] (II) NVIDIA(0):     "nvidia-auto-select"
[    30.939] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    30.959] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    30.959] (--) NVIDIA(0):     option
[    30.965] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    30.965] (--) Depth 24 pixmap format is 32 bpp
[    30.965] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    30.966] (II) NVIDIA(0): Initialized GPU GART.
[    30.973] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    30.983] (II) Loading extension NV-GLX
[    34.060] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    34.078] (==) NVIDIA(0): Disabling shared memory pixmaps
[    34.078] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    34.078] (==) NVIDIA(0): Backing store disabled
[    34.078] (==) NVIDIA(0): Silken mouse enabled
[    37.079] (==) NVIDIA(0): DPMS enabled
[    37.079] (II) Loading extension NV-CONTROL
[    37.080] (II) Loading extension XINERAMA
[    37.080] (II) Loading sub module "dri2"
[    37.080] (II) LoadModule: "dri2"
[    37.080] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    37.080] (II) NVIDIA(0): [DRI2] Setup complete
[    37.080] (==) RandR enabled
[    37.080] (II) Initializing built-in extension Generic Event Extension
[    37.080] (II) Initializing built-in extension SHAPE
[    37.080] (II) Initializing built-in extension MIT-SHM
[    37.080] (II) Initializing built-in extension XInputExtension
[    37.080] (II) Initializing built-in extension XTEST
[    37.080] (II) Initializing built-in extension BIG-REQUESTS
[    37.080] (II) Initializing built-in extension SYNC
[    37.080] (II) Initializing built-in extension XKEYBOARD
[    37.080] (II) Initializing built-in extension XC-MISC
[    37.080] (II) Initializing built-in extension SECURITY
[    37.080] (II) Initializing built-in extension XINERAMA
[    37.080] (II) Initializing built-in extension XFIXES
[    37.081] (II) Initializing built-in extension RENDER
[    37.081] (II) Initializing built-in extension RANDR
[    37.081] (II) Initializing built-in extension COMPOSITE
[    37.081] (II) Initializing built-in extension DAMAGE
[    37.081] (II) Initializing built-in extension GESTURE
[    37.081] (II) Initializing extension GLX
[    37.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.146] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    37.146] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.146] (II) LoadModule: "evdev"
[    37.147] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.147] (II) Module evdev: vendor="X.Org Foundation"
[    37.147] 	compiled for 1.9.0, module version = 2.3.2
[    37.147] 	Module class: X.Org XInput Driver
[    37.147] 	ABI class: X.Org XInput driver, version 11.0
[    37.147] (**) Power Button: always reports core events
[    37.147] (**) Power Button: Device: "/dev/input/event1"
[    37.156] (II) Power Button: Found keys
[    37.156] (II) Power Button: Configuring as keyboard
[    37.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.156] (**) Option "xkb_rules" "evdev"
[    37.156] (**) Option "xkb_model" "pc105"
[    37.156] (**) Option "xkb_layout" "us"
[    37.157] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.157] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.157] (**) Power Button: always reports core events
[    37.157] (**) Power Button: Device: "/dev/input/event0"
[    37.176] (II) Power Button: Found keys
[    37.176] (II) Power Button: Configuring as keyboard
[    37.176] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.176] (**) Option "xkb_rules" "evdev"
[    37.176] (**) Option "xkb_model" "pc105"
[    37.176] (**) Option "xkb_layout" "us"
[    37.179] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    37.179] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    37.179] (**) Logitech USB Receiver: always reports core events
[    37.179] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    37.192] (II) Logitech USB Receiver: Found keys
[    37.192] (II) Logitech USB Receiver: Configuring as keyboard
[    37.192] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    37.192] (**) Option "xkb_rules" "evdev"
[    37.192] (**) Option "xkb_model" "pc105"
[    37.192] (**) Option "xkb_layout" "us"
[    37.193] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    37.193] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    37.193] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    37.193] (**) Logitech USB Receiver: always reports core events
[    37.193] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    37.208] (II) Logitech USB Receiver: Found 12 mouse buttons
[    37.208] (II) Logitech USB Receiver: Found scroll wheel(s)
[    37.208] (II) Logitech USB Receiver: Found relative axes
[    37.208] (II) Logitech USB Receiver: Found x and y relative axes
[    37.208] (II) Logitech USB Receiver: Found absolute axes
[    37.208] (II) evdev-grail: failed to open grail, no gesture support
[    37.208] (II) Logitech USB Receiver: Found keys
[    37.208] (II) Logitech USB Receiver: Configuring as mouse
[    37.208] (II) Logitech USB Receiver: Configuring as keyboard
[    37.208] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    37.208] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.208] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    37.208] (**) Option "xkb_rules" "evdev"
[    37.208] (**) Option "xkb_model" "pc105"
[    37.208] (**) Option "xkb_layout" "us"
[    37.208] (II) Logitech USB Receiver: initialized for relative axes.
[    37.208] (WW) Logitech USB Receiver: ignoring absolute axes.
[    37.209] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    37.209] (II) No input driver/identifier specified (ignoring)
[    37.211] (II) config/udev: Adding input device cx88 IR (Pinnacle PCTV HD 800i) (/dev/input/event4)
[    37.211] (**) cx88 IR (Pinnacle PCTV HD 800i): Applying InputClass "evdev keyboard catchall"
[    37.211] (**) cx88 IR (Pinnacle PCTV HD 800i): always reports core events
[    37.211] (**) cx88 IR (Pinnacle PCTV HD 800i): Device: "/dev/input/event4"
[    37.228] (II) cx88 IR (Pinnacle PCTV HD 800i): Found keys
[    37.228] (II) cx88 IR (Pinnacle PCTV HD 800i): Configuring as keyboard
[    37.228] (II) XINPUT: Adding extended input device "cx88 IR (Pinnacle PCTV HD 800i)" (type: KEYBOARD)
[    37.228] (**) Option "xkb_rules" "evdev"
[    37.228] (**) Option "xkb_model" "pc105"
[    37.228] (**) Option "xkb_layout" "us"
[    37.229] (II) config/udev: Adding input device cx88 IR (Pinnacle PCTV HD 800i) (/dev/input/event5)
[    37.230] (**) cx88 IR (Pinnacle PCTV HD 800i): Applying InputClass "evdev keyboard catchall"
[    37.230] (**) cx88 IR (Pinnacle PCTV HD 800i): always reports core events
[    37.230] (**) cx88 IR (Pinnacle PCTV HD 800i): Device: "/dev/input/event5"
[    37.244] (II) cx88 IR (Pinnacle PCTV HD 800i): Found keys
[    37.244] (II) cx88 IR (Pinnacle PCTV HD 800i): Configuring as keyboard
[    37.244] (II) XINPUT: Adding extended input device "cx88 IR (Pinnacle PCTV HD 800i)" (type: KEYBOARD)
[    37.244] (**) Option "xkb_rules" "evdev"
[    37.244] (**) Option "xkb_model" "pc105"
[    37.244] (**) Option "xkb_layout" "us"
[    39.001] (II) NVIDIA(0): Setting mode "832x624"

---

### Post by linuxhippy on 2011-01-17
I found that there was an xorg.conf file on my 10.04 install.  I copied this to my 10.10 and then had to comment out loading the nvidia module and put in the nv module.  Now I have video and am waiting for it to freeze...it's been smooth for 15 minutes!

Here's my xorg.conf file:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer P244W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
#    Driver         "nvidia"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 960x540 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by linuxhippy on 2011-01-17
looks like that xorg.conf worked as tv was good for an hour.  I then messed around with xorg.conf and found that I kept losing my monitor whenever I re-enabled nvidia but I was able to add this to the top of xorg.conf and then use nv as above:

Section "Module"
        Load    "glx"
EndSection

---

### Post by BicyclerBoy on 2011-01-17
This monitor is a 1920x1080 native res.

The VGA input will only allow up to 1680x1050 (at 60Hz only)
I strongly suggest you should use the HDMI-DVI cable that comes with the monitor.

The nvidia driver Xorg.0.log looked fine , it found the monitor & selected a video mode.
You should have changed to the max VGA res in nvidia-settings & saved it back to xorg.conf file.

The nvidia driver loaded glx module automatically. It does not need to be in the xorg.conf file. Neither does the keyboard & mouse input devices stuff.

So use nvidia driver & DVI-HDMI cable, set output resolution to 1920x1080p60 (US).
Then problem solved.

This monitor will have vertical refresh limits of 50 to 60 Hz with HDMI only.

---

### Post by linuxhippy on 2011-01-17
My picture is really clear with the VGA cable.  I have a Roku box plugged in with a HDMI-DVI cable on the same monitor to stream Netflix movies and it looks just as clear as the VGA TV.

My video card doesn't have the HDMI input, so I would have to split the DVI signal some how and then buy another cable that has DVI from the monitor and then DVI on the video card or S video.

Can the picture get clearer than what I see on my Roku box that is hooked into the DVI already...this looks as clear as the VGA mythbuntu?

---

### Post by BicyclerBoy on 2011-01-17
The only streamed TV video I have watched (missed an episode) would put me off using it for anything.

Never seen Roku or netflix  sorry.

IMO You are not going to have the best mythbuntu experience without nvidia vdpau especially with H264 material.
Cheap monitors do not have good pre-scalers etc.

Was just making sure you knew what the consequences of the connection type & video driver were.

If you're happy then that's great.

---

### Post by linuxhippy on 2011-01-17
I'll look into my wiring scheme-some kind of switching box with a knob would that would split my monitor's DVI would make switching between mythbuntu and my Roku a lot easier than it is now and it'll probably look better too!

---

### Post by BicyclerBoy on 2011-01-17
But your monitor has (2) HDMI (single link DVI-D) inputs ??

Why not just use the monitor input selector ?

You'll get PIP as well !

A DVI-D (single link) to HDMI cable is US$6

---

### Post by linuxhippy on 2011-01-18
that would make things easier, but no, my monitor is an Acer P244W that I bought last year and only has 2 inputs...1 VGA and 1 DVI-D.

---

### Post by linuxhippy on 2011-01-18
I noticed a bunch of errors in my xorg log file and then mythfrontend started closing on it's own.  I then went into system and clicked on Additional Drivers again.  It wanted to download the nvidia drivers again.  The recommended drivers I had chosen weren't working so I chose version 173 instead and those seem to be working as most of the errors in my xorg log file are gone and my monitor doesn't lose a signal on reboot.

It looks like there's an error with the recommended nvidia drivers with a monitor.

---

### Post by BicyclerBoy on 2011-01-18
FYI
The nvidia driver in 10.04 are very old.
Most people are using 256 or 260 if it does not cause regressions...
There are 3rd party ppa with easy install drivers ? i.e. pre-compiled & using dkms.

ubuntu x-swat
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

The later drivers require libvdpau as a separate package
Could also try adding the Nvidia repository

sudo add-apt-repository ppa:nvidia-vdpau/ppa

---

### Post by linuxhippy on 2011-01-18
interesting!  The recommended nvidia driver for 10.10 doesn't work on my system with just a monitor (the monitor looses it's signal) but I found that I can specify driver nvidia in xorg.conf with version 173 which is pretty old it sounds like.  I'll look into getting a more recent nvidia driver that works with a monitor using your link.

---

### Post by BicyclerBoy on 2011-01-18
Seems a lot of people are having monitor detection EDID mode validation issues..
Possibly with HDMI or HDMI audio devices.

I thought you were using 10.04 ?
I'm using 260.29.19 with 10.04 & 10.10 64 bit. Both no problems.

BUT I get my nvidia driver (pre-compiled packaged) from a MythTV ppa for convenience.

---

### Post by linuxhippy on 2011-01-18
I have 10.04 and 10.10.  My hard drive has 3 partitions...two 10 GB slices for mythbuntu installs and a 230 GB slice where I put recordings.  I've been using mythbuntu 10.04 for the last 6 months or so on sda1 and did another install of mythbuntu 10.10 on sda2.  All my recordings and backups go to sda3 so that I don't lose them.

---

### Post by nickrout on 2011-01-19
> **BicyclerBoy said:**
> 

BUT I get my nvidia driver (pre-compiled packaged) from a MythTV ppa for convenience.

which ppa do you use?

I have seen comments that with 10.10 you have to blacklist the open source nouveau driver in the initrd, otherwise it loads on boot and the nvidia driver is locked out, or something like that.

---

### Post by BicyclerBoy on 2011-01-20
Our ozzie friend over the ditch. I'm not sure how he feels about people downloading the nvidia driver ..so I do not advertise it.
Very tidy & convenient using package management for this.
The ubuntu-x team ppa is available but the lucid version is 173 ?
Maverick is up to date tho'.

If the nouveau kernel module is loaded it stops nvidia loading hence the blacklist 
added at the end of /etc/modprobe.d/blacklist.conf
# allow nVidia kernel driver
blacklist nouveau
blacklist rivatv

For me, this was not necessity on all machines.

Vaguely recall adding something to blacklist-framebuffer.conf as well for good measure.

---

