---
title: "Ubuntu crashes when plugging in Line6 PodXT"
date: 2012-06-28
forum: Multimedia Software
---

### Post by cyrus_the_virus on 2012-06-28
Hi,

I have used a Line6 PodXT Live (a Guitar modeling device, which can be used as a USB sound card as well for recording) successfully with Ubuntu in the past. I used to compile the source of this driver [http://www.tanzband-scream.at/line6/]("http://www.tanzband-scream.at/line6/").

This driver has recently been added to the Linux kernel making manual compilation unnecessary. When I plug the device in, it seems to be working at first. Lsmod shows the *line6usb* module is loaded, and the device is shown in the sound configuration menu. However, after a minute or so, the system completely freezes.

Any ideas on what causes this?

Below is a fragment of my kern.log, which starts at the moment I plugged it in.
```

Jun 28 17:19:50 martijn-desktop kernel: [ 8365.432020] usb 4-2: new full-speed USB device number 3 using uhci_hcd
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.758918] line6usb: module is from the staging directory, the quality is unknown, you have been warned.
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.758923] line6usb: module is from the staging directory, the quality is unknown, you have been warned.
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.761215] line6usb driver version 0.9.1beta (revision 690)
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.761257] line6usb 4-2:1.0: Line6 PODxt Live found
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.762619] line6usb 4-2:1.0: Line6 PODxt Live now attached
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.762635] line6usb 4-2:1.1: Line6 PODxt Live found
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.763459] line6usb 4-2:1.1: Line6 PODxt Live now attached
Jun 28 17:19:51 martijn-desktop kernel: [ 8365.763490] usbcore: registered new interface driver line6usb
Jun 28 17:20:06 martijn-desktop kernel: [ 8380.810266] usb 1-6.3: USB disconnect, device number 103
Jun 28 17:20:06 martijn-desktop kernel: [ 8381.068266] usb 1-6.3: new low-speed USB device number 105 using ehci_hcd
Jun 28 17:20:06 martijn-desktop kernel: [ 8381.169167] input: RDing TEMPerV1.2 as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input116
Jun 28 17:20:06 martijn-desktop kernel: [ 8381.169329] generic-usb 0003:0C45:7401.00CA: input,hidraw5: USB HID v1.10 Keyboard [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input0
Jun 28 17:20:06 martijn-desktop kernel: [ 8381.171814] generic-usb 0003:0C45:7401.00CB: hiddev0,hidraw6: USB HID v1.10 Device [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input1
Jun 28 17:21:36 martijn-desktop kernel: [ 8471.178288] usb 1-6.3: USB disconnect, device number 105
Jun 28 17:21:36 martijn-desktop kernel: [ 8471.424296] usb 1-6.3: new low-speed USB device number 106 using ehci_hcd
Jun 28 17:21:37 martijn-desktop kernel: [ 8471.525202] input: RDing TEMPerV1.2 as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input117
Jun 28 17:21:37 martijn-desktop kernel: [ 8471.525362] generic-usb 0003:0C45:7401.00CC: input,hidraw5: USB HID v1.10 Keyboard [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input0
Jun 28 17:21:37 martijn-desktop kernel: [ 8471.527719] generic-usb 0003:0C45:7401.00CD: hiddev0,hidraw6: USB HID v1.10 Device [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input1
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.899911] BUG: unable to handle kernel paging request at 000048f4000681a4
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.900085] IP: [<ffffffff81165b7c>] __kmalloc_node_track_caller+0x13c/0x1e0
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.900255] PGD 0 
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.900305] Oops: 0000 [#1] SMP 
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.900386] CPU 3 
Jun 28 17:22:12 martijn-desktop kernel: [ 8506.900431] Modules linked in: line6usb(C) snd_hrtimer dm_crypt rfcomm bnep bluetooth parport_pc ppdev pci_stub vboxpci(O) vboxnetJun 28 17:23:29 martijn-desktop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Linux version 3.2.0-25-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 (Ubuntu 3.2.0-25.40-generic 3.2.18)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=8894ebbb-ed48-4b9c-b0f3-caee39e5a4ce ro quiet splash vt.handoff=7
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] KERNEL supported cpus:
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   Intel GenuineIntel
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffe0000 (ACPI NVS)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] DMI 2.4 present.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] DMI: System manufacturer P5K/P5K, BIOS 0704    10/30/2007
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] No AGP bridge found
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] MTRR default type: uncachable
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   00000-9FFFF write-back
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   C0000-DFFFF write-protect
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   E0000-EFFFF write-through
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   2 base 000000000 mask E00000000 write-back
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   3 base 200000000 mask FE0000000 write-back
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   4 base 220000000 mask FF0000000 write-back
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   5 disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   6 disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   7 disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] original variable MTRRs
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 0, base: 3328MB, range: 256MB, type UC
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 2, base: 0GB, range: 8GB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 3, base: 8GB, range: 512MB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 4, base: 8704MB, range: 256MB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] total RAM covered: 8192M
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Found optimal setting for mtrr clean up
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  gran_size: 64K  chunk_size: 64K   num_reg: 6    lose cover RAM: 0G
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] New variable MTRRs
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 4, base: 8GB, range: 512MB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] reg 5, base: 8704MB, range: 256MB, type WB
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  0000000000 - 00cfe00000 page 2M
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffa000-20000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  0100000000 - 0230000000 page 2M
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] kernel direct mapping tables up to 230000000 @ cff76000-cff80000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] RAMDISK: 358fa000 - 36c75000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: RSDP 00000000000fbcd0 00014 (v00 ACPIAM)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: RSDT 00000000cff80000 0003C (v01 A_M_I_ OEMRSDT  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: FACP 00000000cff80200 00084 (v02 A_M_I_ OEMFACP  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: DSDT 00000000cff805c0 08DC8 (v01  A0751 A0751059 00000059 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: FACS 00000000cff8e000 00040
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: APIC 00000000cff80390 0006C (v01 A_M_I_ OEMAPIC  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: MCFG 00000000cff80400 0003C (v01 A_M_I_ OEMMCFG  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: OEMB 00000000cff8e040 00081 (v01 A_M_I_ AMI_OEM  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: HPET 00000000cff89390 00038 (v01 A_M_I_ OEMHPET  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: OSFR 00000000cff893d0 000B0 (v01 A_M_I_ OEMOSFR  10000730 MSFT 00000097)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] No NUMA configuration found
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000230000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000230000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   NODE_DATA [000000022fffb000 - 000000022fffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Zone PFN ranges:
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00230000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00230000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] On node 0 totalpages: 2096911
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   Normal zone: 19456 pages used for memmap
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]   Normal zone: 1225728 pages, LIFO batch:31
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] nr_irqs_gsi: 40
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff8e000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cff8e000 - 00000000cffe0000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022fc00000 s83072 r8192 d23424 u524288
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061066
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Policy zone: Normal
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=8894ebbb-ed48-4b9c-b0f3-caee39e5a4ce ro quiet splash vt.handoff=7
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Checking aperture...
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] No AGP bridge found
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Memory: 8154272k/9175040k available (6570k kernel code, 787396k absent, 233372k reserved, 6633k data, 920k init)
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Console: colour dummy device 80x25
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] console [tty0] enabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] hpet clockevent registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jun 28 17:23:29 martijn-desktop kernel: [    0.000000] Detected 2405.431 MHz processor.
Jun 28 17:23:29 martijn-desktop kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4810.86 BogoMIPS (lpj=9621724)
Jun 28 17:23:29 martijn-desktop kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jun 28 17:23:29 martijn-desktop kernel: [    0.004034] Security Framework initialized
Jun 28 17:23:29 martijn-desktop kernel: [    0.004050] AppArmor: AppArmor initialized
Jun 28 17:23:29 martijn-desktop kernel: [    0.004051] Yama: becoming mindful.
Jun 28 17:23:29 martijn-desktop kernel: [    0.008332] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.011918] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.013607] Mount-cache hash table entries: 256
Jun 28 17:23:29 martijn-desktop kernel: [    0.013756] Initializing cgroup subsys cpuacct
Jun 28 17:23:29 martijn-desktop kernel: [    0.013762] Initializing cgroup subsys memory
Jun 28 17:23:29 martijn-desktop kernel: [    0.013771] Initializing cgroup subsys devices
Jun 28 17:23:29 martijn-desktop kernel: [    0.013773] Initializing cgroup subsys freezer
Jun 28 17:23:29 martijn-desktop kernel: [    0.013775] Initializing cgroup subsys blkio
Jun 28 17:23:29 martijn-desktop kernel: [    0.013782] Initializing cgroup subsys perf_event
Jun 28 17:23:29 martijn-desktop kernel: [    0.013813] CPU: Physical Processor ID: 0
Jun 28 17:23:29 martijn-desktop kernel: [    0.013815] CPU: Processor Core ID: 0
Jun 28 17:23:29 martijn-desktop kernel: [    0.013817] mce: CPU supports 6 MCE banks
Jun 28 17:23:29 martijn-desktop kernel: [    0.013825] CPU0: Thermal monitoring enabled (TM2)
Jun 28 17:23:29 martijn-desktop kernel: [    0.013830] using mwait in idle threads.
Jun 28 17:23:29 martijn-desktop kernel: [    0.016240] ACPI: Core revision 20110623
Jun 28 17:23:29 martijn-desktop kernel: [    0.020012] ftrace: allocating 27073 entries in 107 pages
Jun 28 17:23:29 martijn-desktop kernel: [    0.028402] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 28 17:23:29 martijn-desktop kernel: [    0.074729] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] PEBS disabled due to CPU errata.
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... version:                2
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... bit width:              40
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... generic registers:      2
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... value mask:             000000ffffffffff
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... max period:             000000007fffffff
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... fixed-purpose events:   3
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] ... event mask:             0000000700000003
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] Booting Node   0, Processors  #1
Jun 28 17:23:29 martijn-desktop kernel: [    0.076004] smpboot cpu 1: start_ip = 9a000
Jun 28 17:23:29 martijn-desktop kernel: [    0.164036] NMI watchdog enabled, takes one hw-pmu counter.
Jun 28 17:23:29 martijn-desktop kernel: [    0.164147]  #2
Jun 28 17:23:29 martijn-desktop kernel: [    0.164149] smpboot cpu 2: start_ip = 9a000
Jun 28 17:23:29 martijn-desktop kernel: [    0.256032] NMI watchdog enabled, takes one hw-pmu counter.
Jun 28 17:23:29 martijn-desktop kernel: [    0.256116]  #3 Ok.
Jun 28 17:23:29 martijn-desktop kernel: [    0.256117] smpboot cpu 3: start_ip = 9a000
Jun 28 17:23:29 martijn-desktop kernel: [    0.348038] NMI watchdog enabled, takes one hw-pmu counter.
Jun 28 17:23:29 martijn-desktop kernel: [    0.348063] Brought up 4 CPUs
Jun 28 17:23:29 martijn-desktop kernel: [    0.348066] Total of 4 processors activated (19243.56 BogoMIPS).
Jun 28 17:23:29 martijn-desktop kernel: [    0.351776] devtmpfs: initialized
Jun 28 17:23:29 martijn-desktop kernel: [    0.353132] EVM: security.selinux
Jun 28 17:23:29 martijn-desktop kernel: [    0.353133] EVM: security.SMACK64
Jun 28 17:23:29 martijn-desktop kernel: [    0.353135] EVM: security.capability
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] PM: Registering ACPI NVS region at cff8e000 (335872 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] print_constraints: dummy: 
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] RTC time: 17:23:19, date: 06/28/12
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] NET: Registered protocol family 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] Trying to unpack rootfs image as initramfs...
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] ACPI: bus type pci registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] PCI: not using MMCONFIG
Jun 28 17:23:29 martijn-desktop kernel: [    0.353169] PCI: Using configuration type 1 for base access
Jun 28 17:23:29 martijn-desktop kernel: [    0.354087] bio: create slab <bio-0> at 0
Jun 28 17:23:29 martijn-desktop kernel: [    0.354087] ACPI: Added _OSI(Module Device)
Jun 28 17:23:29 martijn-desktop kernel: [    0.354087] ACPI: Added _OSI(Processor Device)
Jun 28 17:23:29 martijn-desktop kernel: [    0.354087] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 28 17:23:29 martijn-desktop kernel: [    0.354087] ACPI: Added _OSI(Processor Aggregator Device)
Jun 28 17:23:29 martijn-desktop kernel: [    0.356653] ACPI: EC: Look up EC in DSDT
Jun 28 17:23:29 martijn-desktop kernel: [    0.357832] ACPI: Executed 1 blocks of module-level executable AML code
Jun 28 17:23:29 martijn-desktop kernel: [    0.361293] ACPI: SSDT 00000000cff8e0d0 001D2 (v01    AMI   CPU1PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.361579] ACPI: Dynamic OEM Table Load:
Jun 28 17:23:29 martijn-desktop kernel: [    0.361582] ACPI: SSDT           (null) 001D2 (v01    AMI   CPU1PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.361721] ACPI: SSDT 00000000cff8e2b0 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362001] ACPI: Dynamic OEM Table Load:
Jun 28 17:23:29 martijn-desktop kernel: [    0.362004] ACPI: SSDT           (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362142] ACPI: SSDT 00000000cff8e400 00143 (v01    AMI   CPU3PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362426] ACPI: Dynamic OEM Table Load:
Jun 28 17:23:29 martijn-desktop kernel: [    0.362429] ACPI: SSDT           (null) 00143 (v01    AMI   CPU3PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362570] ACPI: SSDT 00000000cff8e550 00143 (v01    AMI   CPU4PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362854] ACPI: Dynamic OEM Table Load:
Jun 28 17:23:29 martijn-desktop kernel: [    0.362857] ACPI: SSDT           (null) 00143 (v01    AMI   CPU4PM 00000001 INTL 20060113)
Jun 28 17:23:29 martijn-desktop kernel: [    0.362998] ACPI: Interpreter enabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.363002] ACPI: (supports S0 S1 S3 S4 S5)
Jun 28 17:23:29 martijn-desktop kernel: [    0.363021] ACPI: Using IOAPIC for interrupt routing
Jun 28 17:23:29 martijn-desktop kernel: [    0.363043] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 28 17:23:29 martijn-desktop kernel: [    0.363467] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 28 17:23:29 martijn-desktop kernel: [    0.411781] ACPI: No dock devices found.
Jun 28 17:23:29 martijn-desktop kernel: [    0.411784] HEST: Table not found.
Jun 28 17:23:29 martijn-desktop kernel: [    0.411788] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jun 28 17:23:29 martijn-desktop kernel: [    0.411850] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 28 17:23:29 martijn-desktop kernel: [    0.411978] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jun 28 17:23:29 martijn-desktop kernel: [    0.411981] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jun 28 17:23:29 martijn-desktop kernel: [    0.411983] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jun 28 17:23:29 martijn-desktop kernel: [    0.411986] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Jun 28 17:23:29 martijn-desktop kernel: [    0.411988] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xffffffff] (ignored)
Jun 28 17:23:29 martijn-desktop kernel: [    0.412000] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
Jun 28 17:23:29 martijn-desktop kernel: [    0.412061] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
Jun 28 17:23:29 martijn-desktop kernel: [    0.412099] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412103] pci 0000:00:01.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412141] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.412181] pci 0000:00:1a.0: reg 20: [io  0xb800-0xb81f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.412232] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.412272] pci 0000:00:1a.1: reg 20: [io  0xb880-0xb89f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.412321] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.412360] pci 0000:00:1a.2: reg 20: [io  0xbc00-0xbc1f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.412418] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.412438] pci 0000:00:1a.7: reg 10: [mem 0xfbfffc00-0xfbffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.412524] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412529] pci 0000:00:1a.7: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412551] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
Jun 28 17:23:29 martijn-desktop kernel: [    0.412575] pci 0000:00:1b.0: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 28 17:23:29 martijn-desktop kernel: [    0.412650] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412654] pci 0000:00:1b.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412672] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
Jun 28 17:23:29 martijn-desktop kernel: [    0.412737] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412741] pci 0000:00:1c.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412765] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
Jun 28 17:23:29 martijn-desktop kernel: [    0.412831] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412835] pci 0000:00:1c.4: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412855] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
Jun 28 17:23:29 martijn-desktop kernel: [    0.412920] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.412923] pci 0000:00:1c.5: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.412945] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.412985] pci 0000:00:1d.0: reg 20: [io  0xb080-0xb09f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413035] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.413075] pci 0000:00:1d.1: reg 20: [io  0xb400-0xb41f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413123] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.413162] pci 0000:00:1d.2: reg 20: [io  0xb480-0xb49f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413219] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
Jun 28 17:23:29 martijn-desktop kernel: [    0.413239] pci 0000:00:1d.7: reg 10: [mem 0xfbfff800-0xfbfffbff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413323] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.413328] pci 0000:00:1d.7: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.413346] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
Jun 28 17:23:29 martijn-desktop kernel: [    0.413404] pci 0000:00:1f.0: [8086:2918] type 0 class 0x000601
Jun 28 17:23:29 martijn-desktop kernel: [    0.413485] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Jun 28 17:23:29 martijn-desktop kernel: [    0.413531] pci 0000:00:1f.2: [8086:2921] type 0 class 0x000101
Jun 28 17:23:29 martijn-desktop kernel: [    0.413545] pci 0000:00:1f.2: reg 10: [io  0xa000-0xa007]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413553] pci 0000:00:1f.2: reg 14: [io  0x9c00-0x9c03]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413561] pci 0000:00:1f.2: reg 18: [io  0x9880-0x9887]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413569] pci 0000:00:1f.2: reg 1c: [io  0x9800-0x9803]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413576] pci 0000:00:1f.2: reg 20: [io  0x9480-0x948f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413584] pci 0000:00:1f.2: reg 24: [io  0x9400-0x940f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413627] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
Jun 28 17:23:29 martijn-desktop kernel: [    0.413641] pci 0000:00:1f.3: reg 10: [mem 0xfbfff400-0xfbfff4ff 64bit]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413661] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413693] pci 0000:00:1f.5: [8086:2926] type 0 class 0x000101
Jun 28 17:23:29 martijn-desktop kernel: [    0.413707] pci 0000:00:1f.5: reg 10: [io  0xb000-0xb007]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413715] pci 0000:00:1f.5: reg 14: [io  0xac00-0xac03]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413723] pci 0000:00:1f.5: reg 18: [io  0xa880-0xa887]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413732] pci 0000:00:1f.5: reg 1c: [io  0xa800-0xa803]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413740] pci 0000:00:1f.5: reg 20: [io  0xa480-0xa48f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413747] pci 0000:00:1f.5: reg 24: [io  0xa400-0xa40f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413820] pci 0000:01:00.0: [10de:1244] type 0 class 0x000300
Jun 28 17:23:29 martijn-desktop kernel: [    0.413829] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413839] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413850] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413857] pci 0000:01:00.0: reg 24: [io  0xcc00-0xcc7f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413864] pci 0000:01:00.0: reg 30: [mem 0xfe800000-0xfe87ffff pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.413917] pci 0000:01:00.1: [10de:0bee] type 0 class 0x000403
Jun 28 17:23:29 martijn-desktop kernel: [    0.413927] pci 0000:01:00.1: reg 10: [mem 0xfe8fc000-0xfe8fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414015] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414019] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414022] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfe8fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414026] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414063] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414071] pci 0000:00:1c.0:   bridge window [mem 0xfae00000-0xfaefffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414125] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
Jun 28 17:23:29 martijn-desktop kernel: [    0.414209] pci 0000:03:00.0: reg 24: [mem 0xfeafe000-0xfeafffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414223] pci 0000:03:00.0: reg 30: [mem 0xfeae0000-0xfeaeffff pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414272] pci 0000:03:00.0: PME# supported from D3hot
Jun 28 17:23:29 martijn-desktop kernel: [    0.414277] pci 0000:03:00.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.414306] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
Jun 28 17:23:29 martijn-desktop kernel: [    0.414329] pci 0000:03:00.1: reg 10: [io  0xdc00-0xdc07]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414343] pci 0000:03:00.1: reg 14: [io  0xd880-0xd883]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414356] pci 0000:03:00.1: reg 18: [io  0xd800-0xd807]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414369] pci 0000:03:00.1: reg 1c: [io  0xd480-0xd483]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414382] pci 0000:03:00.1: reg 20: [io  0xd400-0xd40f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414463] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun 28 17:23:29 martijn-desktop kernel: [    0.414475] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414479] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414483] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414539] pci 0000:02:00.0: [1969:1048] type 0 class 0x000200
Jun 28 17:23:29 martijn-desktop kernel: [    0.414561] pci 0000:02:00.0: reg 10: [mem 0xfe9c0000-0xfe9fffff 64bit]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414612] pci 0000:02:00.0: reg 30: [mem 0xfe9a0000-0xfe9bffff pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414665] pci 0000:02:00.0: PME# supported from D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.414670] pci 0000:02:00.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.414686] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun 28 17:23:29 martijn-desktop kernel: [    0.414695] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414700] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414738] pci 0000:05:02.0: [109e:036e] type 0 class 0x000400
Jun 28 17:23:29 martijn-desktop kernel: [    0.414756] pci 0000:05:02.0: reg 10: [mem 0xfaffe000-0xfaffefff pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414850] pci 0000:05:02.1: [109e:0878] type 0 class 0x000480
Jun 28 17:23:29 martijn-desktop kernel: [    0.414868] pci 0000:05:02.1: reg 10: [mem 0xfafff000-0xfaffffff pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414968] pci 0000:05:03.0: [1106:3044] type 0 class 0x000c00
Jun 28 17:23:29 martijn-desktop kernel: [    0.414985] pci 0000:05:03.0: reg 10: [mem 0xfebff800-0xfebfffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.414995] pci 0000:05:03.0: reg 14: [io  0xec00-0xec7f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415060] pci 0000:05:03.0: supports D2
Jun 28 17:23:29 martijn-desktop kernel: [    0.415062] pci 0000:05:03.0: PME# supported from D2 D3hot D3cold
Jun 28 17:23:29 martijn-desktop kernel: [    0.415066] pci 0000:05:03.0: PME# disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.415105] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
Jun 28 17:23:29 martijn-desktop kernel: [    0.415109] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415113] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415118] pci 0000:00:1e.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415121] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jun 28 17:23:29 martijn-desktop kernel: [    0.415123] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
Jun 28 17:23:29 martijn-desktop kernel: [    0.415144] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415320] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415354] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Jun 28 17:23:29 martijn-desktop kernel: [    0.415418]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 28 17:23:29 martijn-desktop kernel: [    0.415421]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 28 17:23:29 martijn-desktop kernel: [    0.415423] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 28 17:23:29 martijn-desktop kernel: [    0.422496] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422541] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422583] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422624] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422665] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jun 28 17:23:29 martijn-desktop kernel: [    0.422708] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422750] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] vgaarb: loaded
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] vgaarb: bridge control possible 0000:01:00.0
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] i2c-core: driver [aat2870] using legacy suspend method
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] i2c-core: driver [aat2870] using legacy resume method
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] SCSI subsystem initialized
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] libata version 3.00 loaded.
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] usbcore: registered new interface driver usbfs
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] usbcore: registered new interface driver hub
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] usbcore: registered new device driver usb
Jun 28 17:23:29 martijn-desktop kernel: [    0.422895] PCI: Using ACPI for IRQ routing
Jun 28 17:23:29 martijn-desktop kernel: [    0.429040] PCI: pci_cache_line_size set to 64 bytes
Jun 28 17:23:29 martijn-desktop kernel: [    0.429136] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jun 28 17:23:29 martijn-desktop kernel: [    0.429139] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 28 17:23:29 martijn-desktop kernel: [    0.429241] NetLabel: Initializing
Jun 28 17:23:29 martijn-desktop kernel: [    0.429243] NetLabel:  domain hash size = 128
Jun 28 17:23:29 martijn-desktop kernel: [    0.429244] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 28 17:23:29 martijn-desktop kernel: [    0.429255] NetLabel:  unlabeled traffic allowed by default
Jun 28 17:23:29 martijn-desktop kernel: [    0.429288] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jun 28 17:23:29 martijn-desktop kernel: [    0.429288] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun 28 17:23:29 martijn-desktop kernel: [    0.429288] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jun 28 17:23:29 martijn-desktop kernel: [    0.436811] Switching to clocksource hpet
Jun 28 17:23:29 martijn-desktop kernel: [    0.443334] AppArmor: AppArmor Filesystem Enabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.443366] pnp: PnP ACPI init
Jun 28 17:23:29 martijn-desktop kernel: [    0.443385] ACPI: bus type pnp registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.443475] pnp 00:00: [bus 00-ff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443477] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443479] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443481] pnp 00:00: [io  0x0d00-0xffff window]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443484] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443486] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443488] pnp 00:00: [mem 0xd0000000-0xffffffff window]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443554] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.443563] pnp 00:01: [mem 0xfed14000-0xfed19fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443622] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.443626] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.443655] pnp 00:02: [dma 4]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443657] pnp 00:02: [io  0x0000-0x000f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443659] pnp 00:02: [io  0x0081-0x0083]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443661] pnp 00:02: [io  0x0087]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443666] pnp 00:02: [io  0x0089-0x008b]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443668] pnp 00:02: [io  0x008f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443670] pnp 00:02: [io  0x00c0-0x00df]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443696] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.443707] pnp 00:03: [io  0x0070-0x0071]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443717] pnp 00:03: [irq 8]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443740] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.443748] pnp 00:04: [io  0x0061]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443773] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.443781] pnp 00:05: [io  0x00f0-0x00ff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443786] pnp 00:05: [irq 13]
Jun 28 17:23:29 martijn-desktop kernel: [    0.443814] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444090] pnp 00:06: [irq 6]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444092] pnp 00:06: [dma 2]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444094] pnp 00:06: [io  0x03f0-0x03f5]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444096] pnp 00:06: [io  0x03f7]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444148] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444176] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444178] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444180] pnp 00:07: [io  0x0290-0x0297]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444227] system 00:07: [io  0x0290-0x0297] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444231] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444313] pnp 00:08: [io  0x0010-0x001f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444316] pnp 00:08: [io  0x0022-0x003f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444317] pnp 00:08: [io  0x0044-0x004d]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444319] pnp 00:08: [io  0x0050-0x005f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444321] pnp 00:08: [io  0x0062-0x0063]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444322] pnp 00:08: [io  0x0065-0x006f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444324] pnp 00:08: [io  0x0072-0x007f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444325] pnp 00:08: [io  0x0080]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444327] pnp 00:08: [io  0x0084-0x0086]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444329] pnp 00:08: [io  0x0088]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444330] pnp 00:08: [io  0x008c-0x008e]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444332] pnp 00:08: [io  0x0090-0x009f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444334] pnp 00:08: [io  0x00a2-0x00bf]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444335] pnp 00:08: [io  0x00e0-0x00ef]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444337] pnp 00:08: [io  0x04d0-0x04d1]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444341] pnp 00:08: [io  0x0800-0x087f]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444343] pnp 00:08: [io  0x0400-0x03ff disabled]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444345] pnp 00:08: [io  0x0480-0x04bf]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444346] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444348] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444350] pnp 00:08: [mem 0xfed50000-0xfed8ffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444352] pnp 00:08: [mem 0xffa00000-0xffafffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444354] pnp 00:08: [mem 0xffb00000-0xffbfffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444356] pnp 00:08: [mem 0xffe00000-0xffefffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444357] pnp 00:08: [mem 0xfff00000-0xfffffffe]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444435] system 00:08: [io  0x04d0-0x04d1] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444437] system 00:08: [io  0x0800-0x087f] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444440] system 00:08: [io  0x0480-0x04bf] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444442] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444445] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444447] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444450] system 00:08: [mem 0xffa00000-0xffafffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444452] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444455] system 00:08: [mem 0xffe00000-0xffefffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444458] system 00:08: [mem 0xfff00000-0xfffffffe] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444461] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444517] pnp 00:09: [mem 0xfed00000-0xfed003ff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444547] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444746] pnp 00:0a: [irq 4]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444749] pnp 00:0a: [dma 0 disabled]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444751] pnp 00:0a: [io  0x03f8-0x03ff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444819] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444858] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444860] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444904] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444907] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.444911] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.444935] pnp 00:0c: [io  0x0060]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444937] pnp 00:0c: [io  0x0064]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444942] pnp 00:0c: [irq 1]
Jun 28 17:23:29 martijn-desktop kernel: [    0.444977] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.445006] pnp 00:0d: [mem 0xe0000000-0xefffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445053] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.445056] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.445199] pnp 00:0e: [mem 0x00000000-0x0009ffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445201] pnp 00:0e: [mem 0x000c0000-0x000cffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445203] pnp 00:0e: [mem 0x000e0000-0x000fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445205] pnp 00:0e: [mem 0x00100000-0xcfffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445207] pnp 00:0e: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 28 17:23:29 martijn-desktop kernel: [    0.445268] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.445271] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.445274] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.445277] system 00:0e: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 28 17:23:29 martijn-desktop kernel: [    0.445280] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 28 17:23:29 martijn-desktop kernel: [    0.445387] pnp: PnP ACPI: found 15 devices
Jun 28 17:23:29 martijn-desktop kernel: [    0.445389] ACPI: ACPI bus type pnp unregistered
Jun 28 17:23:29 martijn-desktop kernel: [    0.453315] PCI: max bus depth: 1 pci_try_num: 2
Jun 28 17:23:29 martijn-desktop kernel: [    0.453357] pci 0000:00:1c.5: BAR 15: assigned [mem 0xd0000000-0xd01fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453361] pci 0000:00:1c.5: BAR 13: assigned [io  0x1000-0x1fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453364] pci 0000:00:1c.4: BAR 15: assigned [mem 0xd0200000-0xd03fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453367] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd0400000-0xd07fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453370] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453373] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453376] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453379] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfe8fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453382] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453387] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453389] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453394] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd07fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453398] pci 0000:00:1c.0:   bridge window [mem 0xfae00000-0xfaefffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453403] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453406] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453410] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453414] pci 0000:00:1c.4:   bridge window [mem 0xd0200000-0xd03fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453419] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453422] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453427] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453430] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453437] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453439] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453444] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453447] pci 0000:00:1e.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453468] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.453472] pci 0000:00:01.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.453477] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Jun 28 17:23:29 martijn-desktop kernel: [    0.453485] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    0.453488] pci 0000:00:1c.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.453494] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    0.453498] pci 0000:00:1c.4: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.453503] pci 0000:00:1c.5: enabling device (0106 -> 0107)
Jun 28 17:23:29 martijn-desktop kernel: [    0.453507] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.453510] pci 0000:00:1c.5: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.453516] pci 0000:00:1e.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.453520] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453522] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453525] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453527] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe8fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453530] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453533] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453536] pci_bus 0000:04: resource 1 [mem 0xd0400000-0xd07fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453539] pci_bus 0000:04: resource 2 [mem 0xfae00000-0xfaefffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453542] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453545] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453548] pci_bus 0000:03: resource 2 [mem 0xd0200000-0xd03fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453551] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453554] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453557] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453560] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453562] pci_bus 0000:05: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453565] pci_bus 0000:05: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453569] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453571] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]
Jun 28 17:23:29 martijn-desktop kernel: [    0.453614] NET: Registered protocol family 2
Jun 28 17:23:29 martijn-desktop kernel: [    0.453827] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.455136] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.458744] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.459233] TCP: Hash tables configured (established 524288 bind 65536)
Jun 28 17:23:29 martijn-desktop kernel: [    0.459235] TCP reno registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.459252] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.459329] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.459480] NET: Registered protocol family 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.459509] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.459525] pci 0000:00:1a.0: PCI INT A disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459541] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 28 17:23:29 martijn-desktop kernel: [    0.459556] pci 0000:00:1a.1: PCI INT B disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459567] pci 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.459581] pci 0000:00:1a.2: PCI INT C disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459589] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.459620] pci 0000:00:1a.7: PCI INT C disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459640] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 28 17:23:29 martijn-desktop kernel: [    0.459655] pci 0000:00:1d.0: PCI INT A disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459664] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 28 17:23:29 martijn-desktop kernel: [    0.459679] pci 0000:00:1d.1: PCI INT B disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459686] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.459701] pci 0000:00:1d.2: PCI INT C disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459709] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 28 17:23:29 martijn-desktop kernel: [    0.459742] pci 0000:00:1d.7: PCI INT A disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.459766] pci 0000:01:00.0: Boot video device
Jun 28 17:23:29 martijn-desktop kernel: [    0.459793] PCI: CLS 32 bytes, default 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.459796] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun 28 17:23:29 martijn-desktop kernel: [    0.459798] Placing 64MB software IO TLB between ffff8800cbf76000 - ffff8800cff76000
Jun 28 17:23:29 martijn-desktop kernel: [    0.459800] software IO TLB at phys 0xcbf76000 - 0xcff76000
Jun 28 17:23:29 martijn-desktop kernel: [    0.460325] audit: initializing netlink socket (disabled)
Jun 28 17:23:29 martijn-desktop kernel: [    0.460333] type=2000 audit(1340904199.456:1): initialized
Jun 28 17:23:29 martijn-desktop kernel: [    0.501144] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 28 17:23:29 martijn-desktop kernel: [    0.544268] VFS: Disk quotas dquot_6.5.2
Jun 28 17:23:29 martijn-desktop kernel: [    0.544325] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 28 17:23:29 martijn-desktop kernel: [    0.544864] fuse init (API version 7.17)
Jun 28 17:23:29 martijn-desktop kernel: [    0.544954] msgmni has been set to 15926
Jun 28 17:23:29 martijn-desktop kernel: [    0.545433] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 28 17:23:29 martijn-desktop kernel: [    0.545476] io scheduler noop registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.545478] io scheduler deadline registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.545510] io scheduler cfq registered (default)
Jun 28 17:23:29 martijn-desktop kernel: [    0.545620] pcieport 0000:00:01.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.545651] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jun 28 17:23:29 martijn-desktop kernel: [    0.545695] pcieport 0000:00:1c.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.545729] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jun 28 17:23:29 martijn-desktop kernel: [    0.545784] pcieport 0000:00:1c.4: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.545817] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
Jun 28 17:23:29 martijn-desktop kernel: [    0.545873] pcieport 0000:00:1c.5: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.545908] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
Jun 28 17:23:29 martijn-desktop kernel: [    0.545982] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 28 17:23:29 martijn-desktop kernel: [    0.546004] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 28 17:23:29 martijn-desktop kernel: [    0.546058] intel_idle: MWAIT substates: 0x20
Jun 28 17:23:29 martijn-desktop kernel: [    0.546060] intel_idle: does not run on family 6 model 15
Jun 28 17:23:29 martijn-desktop kernel: [    0.546147] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 28 17:23:29 martijn-desktop kernel: [    0.546152] ACPI: Power Button [PWRB]
Jun 28 17:23:29 martijn-desktop kernel: [    0.546197] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 28 17:23:29 martijn-desktop kernel: [    0.546200] ACPI: Power Button [PWRF]
Jun 28 17:23:29 martijn-desktop kernel: [    0.547511] ERST: Table is not found!
Jun 28 17:23:29 martijn-desktop kernel: [    0.547513] GHES: HEST is not enabled!
Jun 28 17:23:29 martijn-desktop kernel: [    0.547581] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.567921] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 28 17:23:29 martijn-desktop kernel: [    0.747262] Freeing initrd memory: 19948k freed
Jun 28 17:23:29 martijn-desktop kernel: [    0.868480] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 28 17:23:29 martijn-desktop kernel: [    0.904284] Linux agpgart interface v0.103
Jun 28 17:23:29 martijn-desktop kernel: [    0.905829] brd: module loaded
Jun 28 17:23:29 martijn-desktop kernel: [    0.906571] loop: module loaded
Jun 28 17:23:29 martijn-desktop kernel: [    0.906691] ahci 0000:03:00.0: version 3.0
Jun 28 17:23:29 martijn-desktop kernel: [    0.906704] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.920051] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jun 28 17:23:29 martijn-desktop kernel: [    0.920057] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Jun 28 17:23:29 martijn-desktop kernel: [    0.920064] ahci 0000:03:00.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.920432] scsi0 : ahci
Jun 28 17:23:29 martijn-desktop kernel: [    0.920538] scsi1 : ahci
Jun 28 17:23:29 martijn-desktop kernel: [    0.920655] ata1: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.920661] ata2: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.920725] ata_piix 0000:00:1f.2: version 2.13
Jun 28 17:23:29 martijn-desktop kernel: [    0.920747] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.920753] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Jun 28 17:23:29 martijn-desktop kernel: [    0.920793] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.921063] scsi2 : ata_piix
Jun 28 17:23:29 martijn-desktop kernel: [    0.921159] scsi3 : ata_piix
Jun 28 17:23:29 martijn-desktop kernel: [    0.922054] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.922058] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.922078] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.922083] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jun 28 17:23:29 martijn-desktop kernel: [    0.922121] ata_piix 0000:00:1f.5: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.922357] scsi4 : ata_piix
Jun 28 17:23:29 martijn-desktop kernel: [    0.922458] scsi5 : ata_piix
Jun 28 17:23:29 martijn-desktop kernel: [    0.923349] ata5: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.923352] ata6: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
Jun 28 17:23:29 martijn-desktop kernel: [    0.923400] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
Jun 28 17:23:29 martijn-desktop kernel: [    0.923406] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    0.923436] pata_acpi 0000:03:00.1: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.923455] pata_acpi 0000:03:00.1: PCI INT B disabled
Jun 28 17:23:29 martijn-desktop kernel: [    0.923752] Fixed MDIO Bus: probed
Jun 28 17:23:29 martijn-desktop kernel: [    0.923775] tun: Universal TUN/TAP device driver, 1.6
Jun 28 17:23:29 martijn-desktop kernel: [    0.923776] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 28 17:23:29 martijn-desktop kernel: [    0.923830] PPP generic driver version 2.4.2
Jun 28 17:23:29 martijn-desktop kernel: [    0.923920] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 28 17:23:29 martijn-desktop kernel: [    0.923933] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.923947] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.923950] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.923997] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.924031] ehci_hcd 0000:00:1a.7: debug port 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.927915] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Jun 28 17:23:29 martijn-desktop kernel: [    0.927928] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbfffc00
Jun 28 17:23:29 martijn-desktop kernel: [    0.940022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jun 28 17:23:29 martijn-desktop kernel: [    0.940193] hub 1-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.940197] hub 1-0:1.0: 6 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.940269] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 28 17:23:29 martijn-desktop kernel: [    0.940280] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.940283] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.940326] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun 28 17:23:29 martijn-desktop kernel: [    0.940351] ehci_hcd 0000:00:1d.7: debug port 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.944248] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun 28 17:23:29 martijn-desktop kernel: [    0.944260] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbfff800
Jun 28 17:23:29 martijn-desktop kernel: [    0.960031] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun 28 17:23:29 martijn-desktop kernel: [    0.960181] hub 2-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.960185] hub 2-0:1.0: 6 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.960256] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 28 17:23:29 martijn-desktop kernel: [    0.960268] uhci_hcd: USB Universal Host Controller Interface driver
Jun 28 17:23:29 martijn-desktop kernel: [    0.960283] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    0.960289] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.960292] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.960334] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun 28 17:23:29 martijn-desktop kernel: [    0.960356] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Jun 28 17:23:29 martijn-desktop kernel: [    0.960468] hub 3-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.960474] hub 3-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.960535] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 28 17:23:29 martijn-desktop kernel: [    0.960541] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.960544] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.960587] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun 28 17:23:29 martijn-desktop kernel: [    0.960617] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Jun 28 17:23:29 martijn-desktop kernel: [    0.960729] hub 4-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.960733] hub 4-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.960793] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.960799] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.960802] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.960844] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jun 28 17:23:29 martijn-desktop kernel: [    0.960865] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
Jun 28 17:23:29 martijn-desktop kernel: [    0.960983] hub 5-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.960987] hub 5-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.961048] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 28 17:23:29 martijn-desktop kernel: [    0.961054] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.961057] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.961098] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jun 28 17:23:29 martijn-desktop kernel: [    0.961118] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
Jun 28 17:23:29 martijn-desktop kernel: [    0.961228] hub 6-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.961231] hub 6-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.961292] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 28 17:23:29 martijn-desktop kernel: [    0.961300] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.961303] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.961350] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jun 28 17:23:29 martijn-desktop kernel: [    0.961378] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Jun 28 17:23:29 martijn-desktop kernel: [    0.961490] hub 7-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.961494] hub 7-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.961558] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    0.961564] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    0.961567] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 28 17:23:29 martijn-desktop kernel: [    0.961606] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jun 28 17:23:29 martijn-desktop kernel: [    0.961626] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
Jun 28 17:23:29 martijn-desktop kernel: [    0.961735] hub 8-0:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    0.961739] hub 8-0:1.0: 2 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    0.961849] usbcore: registered new interface driver libusual
Jun 28 17:23:29 martijn-desktop kernel: [    0.961884] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.961886] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun 28 17:23:29 martijn-desktop kernel: [    0.962368] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.962471] mousedev: PS/2 mouse device common for all mice
Jun 28 17:23:29 martijn-desktop kernel: [    0.962598] rtc_cmos 00:03: RTC can wake from S4
Jun 28 17:23:29 martijn-desktop kernel: [    0.962691] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 28 17:23:29 martijn-desktop kernel: [    0.962712] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 28 17:23:29 martijn-desktop kernel: [    0.962788] device-mapper: uevent: version 1.0.3
Jun 28 17:23:29 martijn-desktop kernel: [    0.962853] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 28 17:23:29 martijn-desktop kernel: [    0.962859] cpuidle: using governor ladder
Jun 28 17:23:29 martijn-desktop kernel: [    0.962861] cpuidle: using governor menu
Jun 28 17:23:29 martijn-desktop kernel: [    0.962863] EFI Variables Facility v0.08 2004-May-17
Jun 28 17:23:29 martijn-desktop kernel: [    0.963074] TCP cubic registered
Jun 28 17:23:29 martijn-desktop kernel: [    0.963176] NET: Registered protocol family 10
Jun 28 17:23:29 martijn-desktop kernel: [    0.963600] NET: Registered protocol family 17
Jun 28 17:23:29 martijn-desktop kernel: [    0.963613] Registering the dns_resolver key type
Jun 28 17:23:29 martijn-desktop kernel: [    0.963725] PM: Hibernation image not present or could not be loaded.
Jun 28 17:23:29 martijn-desktop kernel: [    0.963736] registered taskstats version 1
Jun 28 17:23:29 martijn-desktop kernel: [    0.990400]   Magic number: 0:730:391
Jun 28 17:23:29 martijn-desktop kernel: [    0.990411] hub 3-0:1.0: hash matches
Jun 28 17:23:29 martijn-desktop kernel: [    0.990506] rtc_cmos 00:03: setting system clock to 2012-06-28 17:23:20 UTC (1340904200)
Jun 28 17:23:29 martijn-desktop kernel: [    0.990964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 28 17:23:29 martijn-desktop kernel: [    0.990966] EDD information not available.
Jun 28 17:23:29 martijn-desktop kernel: [    1.240047] ata2: SATA link down (SStatus 0 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.240084] ata1: SATA link down (SStatus 0 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.364019] usb 1-6: new high-speed USB device number 3 using ehci_hcd
Jun 28 17:23:29 martijn-desktop kernel: [    1.396074] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.396079] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.396212] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.396215] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 28 17:23:29 martijn-desktop kernel: [    1.404317] ata6.00: ATAPI: Optiarc DVD RW AD-5200S, 1.05, max UDMA/100
Jun 28 17:23:29 martijn-desktop kernel: [    1.404431] ata3.00: ATA-9: M4-CT128M4SSD2, 0309, max UDMA/100
Jun 28 17:23:29 martijn-desktop kernel: [    1.404435] ata3.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 28 17:23:29 martijn-desktop kernel: [    1.404533] ata5.00: ATA-7: SAMSUNG HD753LJ, 1AA01107, max UDMA7
Jun 28 17:23:29 martijn-desktop kernel: [    1.404536] ata5.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 28 17:23:29 martijn-desktop kernel: [    1.404542] ata4.00: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
Jun 28 17:23:29 martijn-desktop kernel: [    1.404545] ata4.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 28 17:23:29 martijn-desktop kernel: [    1.412416] ata3.00: configured for UDMA/100
Jun 28 17:23:29 martijn-desktop kernel: [    1.412419] ata5.00: configured for UDMA/133
Jun 28 17:23:29 martijn-desktop kernel: [    1.412429] ata4.00: configured for UDMA/133
Jun 28 17:23:29 martijn-desktop kernel: [    1.412543] scsi 2:0:0:0: Direct-Access     ATA      M4-CT128M4SSD2   0309 PQ: 0 ANSI: 5
Jun 28 17:23:29 martijn-desktop kernel: [    1.412691] sd 2:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
Jun 28 17:23:29 martijn-desktop kernel: [    1.412740] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 28 17:23:29 martijn-desktop kernel: [    1.412777] sd 2:0:0:0: [sda] Write Protect is off
Jun 28 17:23:29 martijn-desktop kernel: [    1.412780] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 28 17:23:29 martijn-desktop kernel: [    1.412809] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 28 17:23:29 martijn-desktop kernel: [    1.412915] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
Jun 28 17:23:29 martijn-desktop kernel: [    1.413017] sd 3:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Jun 28 17:23:29 martijn-desktop kernel: [    1.413044] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jun 28 17:23:29 martijn-desktop kernel: [    1.413068] sd 3:0:0:0: [sdb] Write Protect is off
Jun 28 17:23:29 martijn-desktop kernel: [    1.413071] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 28 17:23:29 martijn-desktop kernel: [    1.413093] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 28 17:23:29 martijn-desktop kernel: [    1.413141] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
Jun 28 17:23:29 martijn-desktop kernel: [    1.413274] sd 4:0:0:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Jun 28 17:23:29 martijn-desktop kernel: [    1.413289] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jun 28 17:23:29 martijn-desktop kernel: [    1.413321] sd 4:0:0:0: [sdc] Write Protect is off
Jun 28 17:23:29 martijn-desktop kernel: [    1.413324] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jun 28 17:23:29 martijn-desktop kernel: [    1.413342] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 28 17:23:29 martijn-desktop kernel: [    1.413843]  sda: sda1 sda2 sda3 < sda5 sda6 >
Jun 28 17:23:29 martijn-desktop kernel: [    1.414259] sd 2:0:0:0: [sda] Attached SCSI disk
Jun 28 17:23:29 martijn-desktop kernel: [    1.420182] ata6.00: configured for UDMA/100
Jun 28 17:23:29 martijn-desktop kernel: [    1.421427]  sdb: sdb1
Jun 28 17:23:29 martijn-desktop kernel: [    1.421665] sd 3:0:0:0: [sdb] Attached SCSI disk
Jun 28 17:23:29 martijn-desktop kernel: [    1.422388] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-5200S  1.05 PQ: 0 ANSI: 5
Jun 28 17:23:29 martijn-desktop kernel: [    1.423699]  sdc: sdc1
Jun 28 17:23:29 martijn-desktop kernel: [    1.423982] sd 4:0:0:0: [sdc] Attached SCSI disk
Jun 28 17:23:29 martijn-desktop kernel: [    1.424806] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Jun 28 17:23:29 martijn-desktop kernel: [    1.424811] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 28 17:23:29 martijn-desktop kernel: [    1.424968] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jun 28 17:23:29 martijn-desktop kernel: [    1.425140] sr 5:0:0:0: Attached scsi generic sg3 type 5
Jun 28 17:23:29 martijn-desktop kernel: [    1.426712] Freeing unused kernel memory: 920k freed
Jun 28 17:23:29 martijn-desktop kernel: [    1.426971] Write protecting the kernel read-only data: 12288k
Jun 28 17:23:29 martijn-desktop kernel: [    1.432140] Freeing unused kernel memory: 1604k freed
Jun 28 17:23:29 martijn-desktop kernel: [    1.436375] Freeing unused kernel memory: 1196k freed
Jun 28 17:23:29 martijn-desktop kernel: [    1.459624] Refined TSC clocksource calibration: 2405.454 MHz.
Jun 28 17:23:29 martijn-desktop kernel: [    1.459630] Switching to clocksource tsc
Jun 28 17:23:29 martijn-desktop kernel: [    1.491104] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    1.491140] pata_jmicron 0000:03:00.1: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    1.492657] scsi6 : pata_jmicron
Jun 28 17:23:29 martijn-desktop kernel: [    1.492950] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    1.492959] atl1 0000:02:00.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    1.493039] atl1 0000:02:00.0: version 2.1.3
Jun 28 17:23:29 martijn-desktop kernel: [    1.493784] scsi7 : pata_jmicron
Jun 28 17:23:29 martijn-desktop kernel: [    1.494269] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 28 17:23:29 martijn-desktop kernel: [    1.494272] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 28 17:23:29 martijn-desktop kernel: [    1.495754] Floppy drive(s): fd0 is 1.44M
Jun 28 17:23:29 martijn-desktop kernel: [    1.498046] hub 1-6:1.0: USB hub found
Jun 28 17:23:29 martijn-desktop kernel: [    1.498365] hub 1-6:1.0: 4 ports detected
Jun 28 17:23:29 martijn-desktop kernel: [    1.519740] FDC 0 is a post-1991 82077
Jun 28 17:23:29 martijn-desktop kernel: [    1.736027] usb 4-1: new full-speed USB device number 2 using uhci_hcd
Jun 28 17:23:29 martijn-desktop kernel: [    1.817008] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:29 martijn-desktop kernel: [    1.880053] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 28 17:23:29 martijn-desktop kernel: [    1.929961] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
Jun 28 17:23:29 martijn-desktop kernel: [    1.930058] generic-usb 0003:046D:C049.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1a.1-1/input0
Jun 28 17:23:29 martijn-desktop kernel: [    1.933753] generic-usb 0003:046D:C049.0002: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1a.1-1/input1
Jun 28 17:23:29 martijn-desktop kernel: [    1.933773] usbcore: registered new interface driver usbhid
Jun 28 17:23:29 martijn-desktop kernel: [    1.933775] usbhid: USB HID core driver
Jun 28 17:23:29 martijn-desktop kernel: [    1.996376] usb 1-6.1: new low-speed USB device number 4 using ehci_hcd
Jun 28 17:23:29 martijn-desktop kernel: [    2.110119] usb 1-6.1: string descriptor 0 malformed (err = -61), defaulting to 0x0409
Jun 28 17:23:29 martijn-desktop kernel: [    2.217738] input: HID 06b4:1c70 as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.1/1-6.1:1.0/input/input3
Jun 28 17:23:29 martijn-desktop kernel: [    2.217902] generic-usb 0003:06B4:1C70.0003: input,hidraw2: USB HID v1.10 Keyboard [HID 06b4:1c70] on usb-0000:00:1a.7-6.1/input0
Jun 28 17:23:29 martijn-desktop kernel: [    2.288375] usb 1-6.2: new full-speed USB device number 5 using ehci_hcd
Jun 28 17:23:29 martijn-desktop kernel: [    2.380111] firewire_core: created device fw0: GUID 001e8c00001e9af0, S400
Jun 28 17:23:29 martijn-desktop kernel: [    2.384302] input: RAPOO RAPOO 2.4G Wireless Device as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.2/1-6.2:1.0/input/input4
Jun 28 17:23:29 martijn-desktop kernel: [    2.384391] generic-usb 0003:24AE:2000.0004: input,hidraw3: USB HID v1.01 Keyboard [RAPOO RAPOO 2.4G Wireless Device] on usb-0000:00:1a.7-6.2/input0
Jun 28 17:23:29 martijn-desktop kernel: [    2.387348] input: RAPOO RAPOO 2.4G Wireless Device as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.2/1-6.2:1.1/input/input5
Jun 28 17:23:29 martijn-desktop kernel: [    2.387580] generic-usb 0003:24AE:2000.0005: input,hiddev0,hidraw4: USB HID v1.01 Mouse [RAPOO RAPOO 2.4G Wireless Device] on usb-0000:00:1a.7-6.2/input1
Jun 28 17:23:29 martijn-desktop kernel: [    2.460379] usb 1-6.3: new low-speed USB device number 6 using ehci_hcd
Jun 28 17:23:29 martijn-desktop kernel: [    2.560789] input: RDing TEMPerV1.2 as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input6
Jun 28 17:23:29 martijn-desktop kernel: [    2.560885] generic-usb 0003:0C45:7401.0006: input,hidraw5: USB HID v1.10 Keyboard [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input0
Jun 28 17:23:29 martijn-desktop kernel: [    2.563107] generic-usb 0003:0C45:7401.0007: hiddev0,hidraw6: USB HID v1.10 Device [RDing TEMPerV1.2] on usb-0000:00:1a.7-6.3/input1
Jun 28 17:23:29 martijn-desktop kernel: [    2.962509] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
Jun 28 17:23:29 martijn-desktop kernel: [    2.962512] vesafb: scrolling: redraw
Jun 28 17:23:29 martijn-desktop kernel: [    2.962514] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 28 17:23:29 martijn-desktop kernel: [    2.966712] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90012000000, using 5120k, total 5120k
Jun 28 17:23:29 martijn-desktop kernel: [    2.966878] Console: switching to colour frame buffer device 160x64
Jun 28 17:23:29 martijn-desktop kernel: [    2.966904] fb0: VESA VGA frame buffer device
Jun 28 17:23:29 martijn-desktop kernel: [    8.192788] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
Jun 28 17:23:29 martijn-desktop kernel: [    8.192791] EXT4-fs (sda6): write access will be enabled during recovery
Jun 28 17:23:29 martijn-desktop kernel: [    9.101813] EXT4-fs (sda6): orphan cleanup on readonly fs
Jun 28 17:23:29 martijn-desktop kernel: [    9.101821] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131088
Jun 28 17:23:29 martijn-desktop kernel: [    9.101886] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142272
Jun 28 17:23:29 martijn-desktop kernel: [    9.101920] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142268
Jun 28 17:23:29 martijn-desktop kernel: [    9.101949] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142267
Jun 28 17:23:29 martijn-desktop kernel: [    9.101987] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142256
Jun 28 17:23:29 martijn-desktop kernel: [    9.102012] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141984
Jun 28 17:23:29 martijn-desktop kernel: [    9.102029] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142248
Jun 28 17:23:29 martijn-desktop kernel: [    9.102041] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142266
Jun 28 17:23:29 martijn-desktop kernel: [    9.102055] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218798
Jun 28 17:23:29 martijn-desktop kernel: [    9.102084] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142257
Jun 28 17:23:29 martijn-desktop kernel: [    9.102100] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142254
Jun 28 17:23:29 martijn-desktop kernel: [    9.102113] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142264
Jun 28 17:23:29 martijn-desktop kernel: [    9.102125] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142263
Jun 28 17:23:29 martijn-desktop kernel: [    9.102138] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142202
Jun 28 17:23:29 martijn-desktop kernel: [    9.102151] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142258
Jun 28 17:23:29 martijn-desktop kernel: [    9.102163] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142260
Jun 28 17:23:29 martijn-desktop kernel: [    9.102180] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142196
Jun 28 17:23:29 martijn-desktop kernel: [    9.102193] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142255
Jun 28 17:23:29 martijn-desktop kernel: [    9.102209] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142015
Jun 28 17:23:29 martijn-desktop kernel: [    9.102222] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142249
Jun 28 17:23:29 martijn-desktop kernel: [    9.102237] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142247
Jun 28 17:23:29 martijn-desktop kernel: [    9.102249] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142185
Jun 28 17:23:29 martijn-desktop kernel: [    9.102263] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142233
Jun 28 17:23:29 martijn-desktop kernel: [    9.102278] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142186
Jun 28 17:23:29 martijn-desktop kernel: [    9.102291] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142018
Jun 28 17:23:29 martijn-desktop kernel: [    9.102304] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142245
Jun 28 17:23:29 martijn-desktop kernel: [    9.102317] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142244
Jun 28 17:23:29 martijn-desktop kernel: [    9.102330] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137045
Jun 28 17:23:29 martijn-desktop kernel: [    9.102367] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142019
Jun 28 17:23:29 martijn-desktop kernel: [    9.102379] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142242
Jun 28 17:23:29 martijn-desktop kernel: [    9.102392] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136984
Jun 28 17:23:29 martijn-desktop kernel: [    9.102405] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142017
Jun 28 17:23:29 martijn-desktop kernel: [    9.102417] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142236
Jun 28 17:23:29 martijn-desktop kernel: [    9.102430] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142214
Jun 28 17:23:29 martijn-desktop kernel: [    9.102449] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142235
Jun 28 17:23:29 martijn-desktop kernel: [    9.102461] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142234
Jun 28 17:23:29 martijn-desktop kernel: [    9.102474] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142219
Jun 28 17:23:29 martijn-desktop kernel: [    9.102486] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142232
Jun 28 17:23:29 martijn-desktop kernel: [    9.102501] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142231
Jun 28 17:23:29 martijn-desktop kernel: [    9.102516] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142230
Jun 28 17:23:29 martijn-desktop kernel: [    9.102533] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142225
Jun 28 17:23:29 martijn-desktop kernel: [    9.102548] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142223
Jun 28 17:23:29 martijn-desktop kernel: [    9.102563] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142210
Jun 28 17:23:29 martijn-desktop kernel: [    9.102578] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142213
Jun 28 17:23:29 martijn-desktop kernel: [    9.102591] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142204
Jun 28 17:23:29 martijn-desktop kernel: [    9.102603] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142212
Jun 28 17:23:29 martijn-desktop kernel: [    9.102615] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142211
Jun 28 17:23:29 martijn-desktop kernel: [    9.102628] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142192
Jun 28 17:23:29 martijn-desktop kernel: [    9.102640] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142170
Jun 28 17:23:29 martijn-desktop kernel: [    9.102656] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142129
Jun 28 17:23:29 martijn-desktop kernel: [    9.102669] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142201
Jun 28 17:23:29 martijn-desktop kernel: [    9.102682] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142197
Jun 28 17:23:29 martijn-desktop kernel: [    9.102699] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141975
Jun 28 17:23:29 martijn-desktop kernel: [    9.102712] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142193
Jun 28 17:23:29 martijn-desktop kernel: [    9.102724] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142194
Jun 28 17:23:29 martijn-desktop kernel: [    9.102736] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141821
Jun 28 17:23:29 martijn-desktop kernel: [    9.102750] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142152
Jun 28 17:23:29 martijn-desktop kernel: [    9.102763] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136851
Jun 28 17:23:29 martijn-desktop kernel: [    9.102776] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136857
Jun 28 17:23:29 martijn-desktop kernel: [    9.102788] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142151
Jun 28 17:23:29 martijn-desktop kernel: [    9.102803] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142150
Jun 28 17:23:29 martijn-desktop kernel: [    9.102815] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142149
Jun 28 17:23:29 martijn-desktop kernel: [    9.102830] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136858
Jun 28 17:23:29 martijn-desktop kernel: [    9.102843] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142148
Jun 28 17:23:29 martijn-desktop kernel: [    9.102858] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142144
Jun 28 17:23:29 martijn-desktop kernel: [    9.102873] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137162
Jun 28 17:23:29 martijn-desktop kernel: [    9.102889] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136880
Jun 28 17:23:29 martijn-desktop kernel: [    9.102922] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002824
Jun 28 17:23:29 martijn-desktop kernel: [    9.102946] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002830
Jun 28 17:23:29 martijn-desktop kernel: [    9.102971] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002834
Jun 28 17:23:29 martijn-desktop kernel: [    9.102999] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002828
Jun 28 17:23:29 martijn-desktop kernel: [    9.103030] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002832
Jun 28 17:23:29 martijn-desktop kernel: [    9.103044] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137149
Jun 28 17:23:29 martijn-desktop kernel: [    9.103060] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136886
Jun 28 17:23:29 martijn-desktop kernel: [    9.103076] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137010
Jun 28 17:23:29 martijn-desktop kernel: [    9.103089] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137634
Jun 28 17:23:29 martijn-desktop kernel: [    9.103103] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136982
Jun 28 17:23:29 martijn-desktop kernel: [    9.103116] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137620
Jun 28 17:23:29 martijn-desktop kernel: [    9.103131] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136876
Jun 28 17:23:29 martijn-desktop kernel: [    9.103166] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142101
Jun 28 17:23:29 martijn-desktop kernel: [    9.103191] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137248
Jun 28 17:23:29 martijn-desktop kernel: [    9.103220] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137262
Jun 28 17:23:29 martijn-desktop kernel: [    9.103232] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137250
Jun 28 17:23:29 martijn-desktop kernel: [    9.103245] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137156
Jun 28 17:23:29 martijn-desktop kernel: [    9.103257] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137241
Jun 28 17:23:29 martijn-desktop kernel: [    9.103269] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137163
Jun 28 17:23:29 martijn-desktop kernel: [    9.103281] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137069
Jun 28 17:23:29 martijn-desktop kernel: [    9.103293] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137087
Jun 28 17:23:29 martijn-desktop kernel: [    9.103311] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137072
Jun 28 17:23:29 martijn-desktop kernel: [    9.103323] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137046
Jun 28 17:23:29 martijn-desktop kernel: [    9.103336] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2385202
Jun 28 17:23:29 martijn-desktop kernel: [    9.103362] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2385160
Jun 28 17:23:29 martijn-desktop kernel: [    9.103379] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137011
Jun 28 17:23:29 martijn-desktop kernel: [    9.103392] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002874
Jun 28 17:23:29 martijn-desktop kernel: [    9.103423] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2002864
Jun 28 17:23:29 martijn-desktop kernel: [    9.103436] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136983
Jun 28 17:23:29 martijn-desktop kernel: [    9.103448] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137005
Jun 28 17:23:29 martijn-desktop kernel: [    9.103461] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136986
Jun 28 17:23:29 martijn-desktop kernel: [    9.103476] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136908
Jun 28 17:23:29 martijn-desktop kernel: [    9.103489] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136942
Jun 28 17:23:29 martijn-desktop kernel: [    9.103502] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136910
Jun 28 17:23:29 martijn-desktop kernel: [    9.103516] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136901
Jun 28 17:23:29 martijn-desktop kernel: [    9.103529] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136890
Jun 28 17:23:29 martijn-desktop kernel: [    9.103543] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142034
Jun 28 17:23:29 martijn-desktop kernel: [    9.103556] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136870
Jun 28 17:23:29 martijn-desktop kernel: [    9.103568] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136862
Jun 28 17:23:29 martijn-desktop kernel: [    9.103614] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136841
Jun 28 17:23:29 martijn-desktop kernel: [    9.103631] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140135
Jun 28 17:23:29 martijn-desktop kernel: [    9.103662] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140120
Jun 28 17:23:29 martijn-desktop kernel: [    9.103677] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141985
Jun 28 17:23:29 martijn-desktop kernel: [    9.103690] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136842
Jun 28 17:23:29 martijn-desktop kernel: [    9.103703] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141979
Jun 28 17:23:29 martijn-desktop kernel: [    9.103716] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136838
Jun 28 17:23:29 martijn-desktop kernel: [    9.103731] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142044
Jun 28 17:23:29 martijn-desktop kernel: [    9.103746] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142042
Jun 28 17:23:29 martijn-desktop kernel: [    9.103761] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142041
Jun 28 17:23:29 martijn-desktop kernel: [    9.103776] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142040
Jun 28 17:23:29 martijn-desktop kernel: [    9.103790] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142036
Jun 28 17:23:29 martijn-desktop kernel: [    9.103805] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142039
Jun 28 17:23:29 martijn-desktop kernel: [    9.103818] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142038
Jun 28 17:23:29 martijn-desktop kernel: [    9.103830] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142032
Jun 28 17:23:29 martijn-desktop kernel: [    9.103845] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142014
Jun 28 17:23:29 martijn-desktop kernel: [    9.103857] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142031
Jun 28 17:23:29 martijn-desktop kernel: [    9.103872] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142028
Jun 28 17:23:29 martijn-desktop kernel: [    9.103891] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142024
Jun 28 17:23:29 martijn-desktop kernel: [    9.103907] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142027
Jun 28 17:23:29 martijn-desktop kernel: [    9.103919] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142026
Jun 28 17:23:29 martijn-desktop kernel: [    9.103931] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137670
Jun 28 17:23:29 martijn-desktop kernel: [    9.103945] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142020
Jun 28 17:23:29 martijn-desktop kernel: [    9.103960] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141818
Jun 28 17:23:29 martijn-desktop kernel: [    9.103975] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141982
Jun 28 17:23:29 martijn-desktop kernel: [    9.103988] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142013
Jun 28 17:23:29 martijn-desktop kernel: [    9.104017] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132681
Jun 28 17:23:29 martijn-desktop kernel: [    9.104030] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141819
Jun 28 17:23:29 martijn-desktop kernel: [    9.104042] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132679
Jun 28 17:23:29 martijn-desktop kernel: [    9.104054] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142012
Jun 28 17:23:29 martijn-desktop kernel: [    9.104069] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142011
Jun 28 17:23:29 martijn-desktop kernel: [    9.104084] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141986
Jun 28 17:23:29 martijn-desktop kernel: [    9.104099] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141983
Jun 28 17:23:29 martijn-desktop kernel: [    9.104114] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141981
Jun 28 17:23:29 martijn-desktop kernel: [    9.104126] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141976
Jun 28 17:23:29 martijn-desktop kernel: [    9.104141] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141935
Jun 28 17:23:29 martijn-desktop kernel: [    9.104162] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141886
Jun 28 17:23:29 martijn-desktop kernel: [    9.104175] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141974
Jun 28 17:23:29 martijn-desktop kernel: [    9.104187] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141973
Jun 28 17:23:29 martijn-desktop kernel: [    9.104202] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141911
Jun 28 17:23:29 martijn-desktop kernel: [    9.104215] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141881
Jun 28 17:23:29 martijn-desktop kernel: [    9.104228] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141967
Jun 28 17:23:29 martijn-desktop kernel: [    9.104256] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141965
Jun 28 17:23:29 martijn-desktop kernel: [    9.104271] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141962
Jun 28 17:23:29 martijn-desktop kernel: [    9.104286] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141961
Jun 28 17:23:29 martijn-desktop kernel: [    9.104301] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141957
Jun 28 17:23:29 martijn-desktop kernel: [    9.104316] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141951
Jun 28 17:23:29 martijn-desktop kernel: [    9.104332] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141950
Jun 28 17:23:29 martijn-desktop kernel: [    9.104347] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141932
Jun 28 17:23:29 martijn-desktop kernel: [    9.104362] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141909
Jun 28 17:23:29 martijn-desktop kernel: [    9.104374] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141917
Jun 28 17:23:29 martijn-desktop kernel: [    9.104390] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218801
Jun 28 17:23:29 martijn-desktop kernel: [    9.104534] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141915
Jun 28 17:23:29 martijn-desktop kernel: [    9.104550] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141910
Jun 28 17:23:29 martijn-desktop kernel: [    9.104575] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141885
Jun 28 17:23:29 martijn-desktop kernel: [    9.104587] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141908
Jun 28 17:23:29 martijn-desktop kernel: [    9.104602] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141879
Jun 28 17:23:29 martijn-desktop kernel: [    9.104615] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218796
Jun 28 17:23:29 martijn-desktop kernel: [    9.104779] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218792
Jun 28 17:23:29 martijn-desktop kernel: [    9.104792] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218791
Jun 28 17:23:29 martijn-desktop kernel: [    9.104830] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141896
Jun 28 17:23:29 martijn-desktop kernel: [    9.104846] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141891
Jun 28 17:23:29 martijn-desktop kernel: [    9.104864] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141888
Jun 28 17:23:29 martijn-desktop kernel: [    9.104879] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141884
Jun 28 17:23:29 martijn-desktop kernel: [    9.104894] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218797
Jun 28 17:23:29 martijn-desktop kernel: [    9.104909] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140136
Jun 28 17:23:29 martijn-desktop kernel: [    9.104922] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141883
Jun 28 17:23:29 martijn-desktop kernel: [    9.104937] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218790
Jun 28 17:23:29 martijn-desktop kernel: [    9.104949] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141882
Jun 28 17:23:29 martijn-desktop kernel: [    9.104964] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141880
Jun 28 17:23:29 martijn-desktop kernel: [    9.104980] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140637
Jun 28 17:23:29 martijn-desktop kernel: [    9.104992] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141878
Jun 28 17:23:29 martijn-desktop kernel: [    9.105013] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141850
Jun 28 17:23:29 martijn-desktop kernel: [    9.105026] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141877
Jun 28 17:23:29 martijn-desktop kernel: [    9.105041] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141873
Jun 28 17:23:29 martijn-desktop kernel: [    9.105057] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141869
Jun 28 17:23:29 martijn-desktop kernel: [    9.105072] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141868
Jun 28 17:23:29 martijn-desktop kernel: [    9.105087] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141867
Jun 28 17:23:29 martijn-desktop kernel: [    9.105102] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141866
Jun 28 17:23:29 martijn-desktop kernel: [    9.105117] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141864
Jun 28 17:23:29 martijn-desktop kernel: [    9.105132] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141851
Jun 28 17:23:29 martijn-desktop kernel: [    9.105147] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141847
Jun 28 17:23:29 martijn-desktop kernel: [    9.105163] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141826
Jun 28 17:23:29 martijn-desktop kernel: [    9.105175] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141830
Jun 28 17:23:29 martijn-desktop kernel: [    9.105206] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132700
Jun 28 17:23:29 martijn-desktop kernel: [    9.105220] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140724
Jun 28 17:23:29 martijn-desktop kernel: [    9.105233] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132680
Jun 28 17:23:29 martijn-desktop kernel: [    9.105245] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140719
Jun 28 17:23:29 martijn-desktop kernel: [    9.105258] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1218793
Jun 28 17:23:29 martijn-desktop kernel: [    9.105409] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 403605
Jun 28 17:23:29 martijn-desktop kernel: [    9.105430] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132693
Jun 28 17:23:29 martijn-desktop kernel: [    9.105444] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132735
Jun 28 17:23:29 martijn-desktop kernel: [    9.105456] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132727
Jun 28 17:23:29 martijn-desktop kernel: [    9.105470] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397688
Jun 28 17:23:29 martijn-desktop kernel: [    9.105485] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142381
Jun 28 17:23:29 martijn-desktop kernel: [    9.105507] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142380
Jun 28 17:23:29 martijn-desktop kernel: [    9.105747] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141838
Jun 28 17:23:29 martijn-desktop kernel: [    9.105773] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 401648
Jun 28 17:23:29 martijn-desktop kernel: [    9.105795] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141831
Jun 28 17:23:29 martijn-desktop kernel: [    9.105819] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137408
Jun 28 17:23:29 martijn-desktop kernel: [    9.105840] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131956
Jun 28 17:23:29 martijn-desktop kernel: [    9.105860] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397897
Jun 28 17:23:29 martijn-desktop kernel: [    9.105881] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141825
Jun 28 17:23:29 martijn-desktop kernel: [    9.105922] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141824
Jun 28 17:23:29 martijn-desktop kernel: [    9.105947] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140657
Jun 28 17:23:29 martijn-desktop kernel: [    9.105960] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132731
Jun 28 17:23:29 martijn-desktop kernel: [    9.105973] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140137
Jun 28 17:23:29 martijn-desktop kernel: [    9.105997] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140653
Jun 28 17:23:29 martijn-desktop kernel: [    9.106013] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140633
Jun 28 17:23:29 martijn-desktop kernel: [    9.106026] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141816
Jun 28 17:23:29 martijn-desktop kernel: [    9.106055] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132203
Jun 28 17:23:29 martijn-desktop kernel: [    9.106079] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137530
Jun 28 17:23:29 martijn-desktop kernel: [    9.106315] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141815
Jun 28 17:23:29 martijn-desktop kernel: [    9.107286] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141806
Jun 28 17:23:29 martijn-desktop kernel: [    9.107315] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141659
Jun 28 17:23:29 martijn-desktop kernel: [    9.107340] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141163
Jun 28 17:23:29 martijn-desktop kernel: [    9.107395] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132704
Jun 28 17:23:29 martijn-desktop kernel: [    9.107408] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132732
Jun 28 17:23:29 martijn-desktop kernel: [    9.107432] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131304
Jun 28 17:23:29 martijn-desktop kernel: [    9.107685] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132730
Jun 28 17:23:29 martijn-desktop kernel: [    9.107710] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141149
Jun 28 17:23:29 martijn-desktop kernel: [    9.107734] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132729
Jun 28 17:23:29 martijn-desktop kernel: [    9.107756] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132721
Jun 28 17:23:29 martijn-desktop kernel: [    9.108610] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132720
Jun 28 17:23:29 martijn-desktop kernel: [    9.108636] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132708
Jun 28 17:23:29 martijn-desktop kernel: [    9.108659] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132707
Jun 28 17:23:29 martijn-desktop kernel: [    9.108680] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132692
Jun 28 17:23:29 martijn-desktop kernel: [    9.108715] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132705
Jun 28 17:23:29 martijn-desktop kernel: [    9.108728] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132701
Jun 28 17:23:29 martijn-desktop kernel: [    9.108741] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136960
Jun 28 17:23:29 martijn-desktop kernel: [    9.108754] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132694
Jun 28 17:23:29 martijn-desktop kernel: [    9.108766] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132691
Jun 28 17:23:29 martijn-desktop kernel: [    9.108779] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136963
Jun 28 17:23:29 martijn-desktop kernel: [    9.108810] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132685
Jun 28 17:23:29 martijn-desktop kernel: [    9.108837] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132684
Jun 28 17:23:29 martijn-desktop kernel: [    9.108849] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132678
Jun 28 17:23:29 martijn-desktop kernel: [    9.108865] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137217
Jun 28 17:23:29 martijn-desktop kernel: [    9.108878] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132677
Jun 28 17:23:29 martijn-desktop kernel: [    9.108893] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132676
Jun 28 17:23:29 martijn-desktop kernel: [    9.108908] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141160
Jun 28 17:23:29 martijn-desktop kernel: [    9.108923] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141159
Jun 28 17:23:29 martijn-desktop kernel: [    9.108941] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141151
Jun 28 17:23:29 martijn-desktop kernel: [    9.108956] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141115
Jun 28 17:23:29 martijn-desktop kernel: [    9.110100] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 136196
Jun 28 17:23:29 martijn-desktop kernel: [    9.111393] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140929
Jun 28 17:23:29 martijn-desktop kernel: [    9.111419] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141125
Jun 28 17:23:29 martijn-desktop kernel: [    9.111447] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141119
Jun 28 17:23:29 martijn-desktop kernel: [    9.111470] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141118
Jun 28 17:23:29 martijn-desktop kernel: [    9.111493] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141113
Jun 28 17:23:29 martijn-desktop kernel: [    9.111565] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141107
Jun 28 17:23:29 martijn-desktop kernel: [    9.111581] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141112
Jun 28 17:23:29 martijn-desktop kernel: [    9.111593] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141111
Jun 28 17:23:29 martijn-desktop kernel: [    9.111606] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141038
Jun 28 17:23:29 martijn-desktop kernel: [    9.111622] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140907
Jun 28 17:23:29 martijn-desktop kernel: [    9.111638] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140923
Jun 28 17:23:29 martijn-desktop kernel: [    9.111654] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140928
Jun 28 17:23:29 martijn-desktop kernel: [    9.111672] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140870
Jun 28 17:23:29 martijn-desktop kernel: [    9.111685] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140906
Jun 28 17:23:29 martijn-desktop kernel: [    9.111701] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141937
Jun 28 17:23:29 martijn-desktop kernel: [    9.111714] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141936
Jun 28 17:23:29 martijn-desktop kernel: [    9.111726] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140881
Jun 28 17:23:29 martijn-desktop kernel: [    9.111743] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140879
Jun 28 17:23:29 martijn-desktop kernel: [    9.111758] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140869
Jun 28 17:23:29 martijn-desktop kernel: [    9.111774] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140728
Jun 28 17:23:29 martijn-desktop kernel: [    9.112287] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140762
Jun 28 17:23:29 martijn-desktop kernel: [    9.112306] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140761
Jun 28 17:23:29 martijn-desktop kernel: [    9.112324] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140759
Jun 28 17:23:29 martijn-desktop kernel: [    9.113734] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131445
Jun 28 17:23:29 martijn-desktop kernel: [    9.115126] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 401693
Jun 28 17:23:29 martijn-desktop kernel: [    9.115953] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 141120
Jun 28 17:23:29 martijn-desktop kernel: [    9.115978] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140725
Jun 28 17:23:29 martijn-desktop kernel: [    9.115994] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140394
Jun 28 17:23:29 martijn-desktop kernel: [    9.116014] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140712
Jun 28 17:23:29 martijn-desktop kernel: [    9.116029] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140722
Jun 28 17:23:29 martijn-desktop kernel: [    9.116043] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138965
Jun 28 17:23:29 martijn-desktop kernel: [    9.116057] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140714
Jun 28 17:23:29 martijn-desktop kernel: [    9.116913] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138956
Jun 28 17:23:29 martijn-desktop kernel: [    9.116938] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140690
Jun 28 17:23:29 martijn-desktop kernel: [    9.116962] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140689
Jun 28 17:23:29 martijn-desktop kernel: [    9.117912] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138635
Jun 28 17:23:29 martijn-desktop kernel: [    9.117941] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138932
Jun 28 17:23:29 martijn-desktop kernel: [    9.117964] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138631
Jun 28 17:23:29 martijn-desktop kernel: [    9.117987] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140638
Jun 28 17:23:29 martijn-desktop kernel: [    9.118010] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140654
Jun 28 17:23:29 martijn-desktop kernel: [    9.118070] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140612
Jun 28 17:23:29 martijn-desktop kernel: [    9.118093] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140652
Jun 28 17:23:29 martijn-desktop kernel: [    9.119882] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140009
Jun 28 17:23:29 martijn-desktop kernel: [    9.119915] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138641
Jun 28 17:23:29 martijn-desktop kernel: [    9.119941] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140023
Jun 28 17:23:29 martijn-desktop kernel: [    9.119969] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140647
Jun 28 17:23:29 martijn-desktop kernel: [    9.119992] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140648
Jun 28 17:23:29 martijn-desktop kernel: [    9.120005] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140646
Jun 28 17:23:29 martijn-desktop kernel: [    9.120025] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140645
Jun 28 17:23:29 martijn-desktop kernel: [    9.120038] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140644
Jun 28 17:23:29 martijn-desktop kernel: [    9.120050] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140642
Jun 28 17:23:29 martijn-desktop kernel: [    9.120062] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140643
Jun 28 17:23:29 martijn-desktop kernel: [    9.120080] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140641
Jun 28 17:23:29 martijn-desktop kernel: [    9.120679] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131937
Jun 28 17:23:29 martijn-desktop kernel: [    9.120704] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140632
Jun 28 17:23:29 martijn-desktop kernel: [    9.120723] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140631
Jun 28 17:23:29 martijn-desktop kernel: [    9.120746] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140397
Jun 28 17:23:29 martijn-desktop kernel: [    9.120765] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138927
Jun 28 17:23:29 martijn-desktop kernel: [    9.120784] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140393
Jun 28 17:23:29 martijn-desktop kernel: [    9.120804] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131962
Jun 28 17:23:29 martijn-desktop kernel: [    9.120827] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140111
Jun 28 17:23:29 martijn-desktop kernel: [    9.120851] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137655
Jun 28 17:23:29 martijn-desktop kernel: [    9.122626] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 669592
Jun 28 17:23:29 martijn-desktop kernel: [    9.123636] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 659722
Jun 28 17:23:29 martijn-desktop kernel: [    9.123663] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 669585
Jun 28 17:23:29 martijn-desktop kernel: [    9.123683] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 656297
Jun 28 17:23:29 martijn-desktop kernel: [    9.123704] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 669584
Jun 28 17:23:29 martijn-desktop kernel: [    9.123738] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140395
Jun 28 17:23:29 martijn-desktop kernel: [    9.124471] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 139470
Jun 28 17:23:29 martijn-desktop kernel: [    9.124496] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140388
Jun 28 17:23:29 martijn-desktop kernel: [    9.126234] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1216870
Jun 28 17:23:29 martijn-desktop kernel: [    9.126432] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1216951
Jun 28 17:23:29 martijn-desktop kernel: [    9.126446] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1216950
Jun 28 17:23:29 martijn-desktop kernel: [    9.126672] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140391
Jun 28 17:23:29 martijn-desktop kernel: [    9.126693] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140185
Jun 28 17:23:29 martijn-desktop kernel: [    9.126713] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140113
Jun 28 17:23:29 martijn-desktop kernel: [    9.126732] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1216714
Jun 28 17:23:29 martijn-desktop kernel: [    9.126752] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140180
Jun 28 17:23:29 martijn-desktop kernel: [    9.126770] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140179
Jun 28 17:23:29 martijn-desktop kernel: [    9.126789] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140178
Jun 28 17:23:29 martijn-desktop kernel: [    9.126808] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140165
Jun 28 17:23:29 martijn-desktop kernel: [    9.126835] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140160
Jun 28 17:23:29 martijn-desktop kernel: [    9.126849] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140146
Jun 28 17:23:29 martijn-desktop kernel: [    9.126862] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140145
Jun 28 17:23:29 martijn-desktop kernel: [    9.126876] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140144
Jun 28 17:23:29 martijn-desktop kernel: [    9.126889] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137663
Jun 28 17:23:29 martijn-desktop kernel: [    9.126902] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137661
Jun 28 17:23:29 martijn-desktop kernel: [    9.126915] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137660
Jun 28 17:23:29 martijn-desktop kernel: [    9.126928] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138926
Jun 28 17:23:29 martijn-desktop kernel: [    9.126941] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140040
Jun 28 17:23:29 martijn-desktop kernel: [    9.126957] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140112
Jun 28 17:23:29 martijn-desktop kernel: [    9.126969] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140108
Jun 28 17:23:29 martijn-desktop kernel: [    9.126982] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140107
Jun 28 17:23:29 martijn-desktop kernel: [    9.126998] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 139036
Jun 28 17:23:29 martijn-desktop kernel: [    9.127011] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140106
Jun 28 17:23:29 martijn-desktop kernel: [    9.127027] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140071
Jun 28 17:23:29 martijn-desktop kernel: [    9.127044] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140060
Jun 28 17:23:29 martijn-desktop kernel: [    9.127060] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140053
Jun 28 17:23:29 martijn-desktop kernel: [    9.127075] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140050
Jun 28 17:23:29 martijn-desktop kernel: [    9.127092] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140045
Jun 28 17:23:29 martijn-desktop kernel: [    9.127107] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140007
Jun 28 17:23:29 martijn-desktop kernel: [    9.127122] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138914
Jun 28 17:23:29 martijn-desktop kernel: [    9.127137] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 140017
Jun 28 17:23:29 martijn-desktop kernel: [    9.127152] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138648
Jun 28 17:23:29 martijn-desktop kernel: [    9.127168] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 139984
Jun 28 17:23:29 martijn-desktop kernel: [    9.127185] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 139967
Jun 28 17:23:29 martijn-desktop kernel: [    9.127203] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131970
Jun 28 17:23:29 martijn-desktop kernel: [    9.127219] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138934
Jun 28 17:23:29 martijn-desktop kernel: [    9.128736] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 407488
Jun 28 17:23:29 martijn-desktop kernel: [    9.128780] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 139325
Jun 28 17:23:29 martijn-desktop kernel: [    9.128801] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138972
Jun 28 17:23:29 martijn-desktop kernel: [    9.128820] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138933
Jun 28 17:23:29 martijn-desktop kernel: [    9.128839] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138937
Jun 28 17:23:29 martijn-desktop kernel: [    9.128858] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138963
Jun 28 17:23:29 martijn-desktop kernel: [    9.128876] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137708
Jun 28 17:23:29 martijn-desktop kernel: [    9.129135] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138954
Jun 28 17:23:29 martijn-desktop kernel: [    9.129157] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137703
Jun 28 17:23:29 martijn-desktop kernel: [    9.129176] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138936
Jun 28 17:23:29 martijn-desktop kernel: [    9.129195] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138923
Jun 28 17:23:29 martijn-desktop kernel: [    9.129213] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138928
Jun 28 17:23:29 martijn-desktop kernel: [    9.129236] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138922
Jun 28 17:23:29 martijn-desktop kernel: [    9.129255] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137433
Jun 28 17:23:29 martijn-desktop kernel: [    9.129277] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138925
Jun 28 17:23:29 martijn-desktop kernel: [    9.129292] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131629
Jun 28 17:23:29 martijn-desktop kernel: [    9.129306] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131588
Jun 28 17:23:29 martijn-desktop kernel: [    9.129318] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138921
Jun 28 17:23:29 martijn-desktop kernel: [    9.129334] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138917
Jun 28 17:23:29 martijn-desktop kernel: [    9.129953] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137758
Jun 28 17:23:29 martijn-desktop kernel: [    9.129977] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138920
Jun 28 17:23:29 martijn-desktop kernel: [    9.130001] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138916
Jun 28 17:23:29 martijn-desktop kernel: [    9.130024] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138596
Jun 28 17:23:29 martijn-desktop kernel: [    9.130044] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138618
Jun 28 17:23:29 martijn-desktop kernel: [    9.130067] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138913
Jun 28 17:23:29 martijn-desktop kernel: [    9.130088] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138912
Jun 28 17:23:29 martijn-desktop kernel: [    9.130110] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138905
Jun 28 17:23:29 martijn-desktop kernel: [    9.130134] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138842
Jun 28 17:23:29 martijn-desktop kernel: [    9.130155] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138841
Jun 28 17:23:29 martijn-desktop kernel: [    9.130177] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138769
Jun 28 17:23:29 martijn-desktop kernel: [    9.130201] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138765
Jun 28 17:23:29 martijn-desktop kernel: [    9.130225] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138681
Jun 28 17:23:29 martijn-desktop kernel: [    9.130248] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138677
Jun 28 17:23:29 martijn-desktop kernel: [    9.130261] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138675
Jun 28 17:23:29 martijn-desktop kernel: [    9.130275] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138664
Jun 28 17:23:29 martijn-desktop kernel: [    9.131474] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142973
Jun 28 17:23:29 martijn-desktop kernel: [    9.131502] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138646
Jun 28 17:23:29 martijn-desktop kernel: [    9.131527] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137820
Jun 28 17:23:29 martijn-desktop kernel: [    9.131552] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138584
Jun 28 17:23:29 martijn-desktop kernel: [    9.131583] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138589
Jun 28 17:23:29 martijn-desktop kernel: [    9.131603] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138595
Jun 28 17:23:29 martijn-desktop kernel: [    9.131615] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137566
Jun 28 17:23:29 martijn-desktop kernel: [    9.131628] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138573
Jun 28 17:23:29 martijn-desktop kernel: [    9.131655] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137823
Jun 28 17:23:29 martijn-desktop kernel: [    9.131671] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137801
Jun 28 17:23:29 martijn-desktop kernel: [    9.131687] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137756
Jun 28 17:23:29 martijn-desktop kernel: [    9.131702] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131998
Jun 28 17:23:29 martijn-desktop kernel: [    9.131716] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137591
Jun 28 17:23:29 martijn-desktop kernel: [    9.131732] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137627
Jun 28 17:23:29 martijn-desktop kernel: [    9.131745] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142966
Jun 28 17:23:29 martijn-desktop kernel: [    9.131760] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137608
Jun 28 17:23:29 martijn-desktop kernel: [    9.131773] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 142963
Jun 28 17:23:29 martijn-desktop kernel: [    9.131786] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 143014
Jun 28 17:23:29 martijn-desktop kernel: [    9.131799] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137590
Jun 28 17:23:29 martijn-desktop kernel: [    9.131814] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137430
Jun 28 17:23:29 martijn-desktop kernel: [    9.132042] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137427
Jun 28 17:23:29 martijn-desktop kernel: [    9.132063] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137415
Jun 28 17:23:29 martijn-desktop kernel: [    9.132087] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137428
Jun 28 17:23:29 martijn-desktop kernel: [    9.132114] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137424
Jun 28 17:23:29 martijn-desktop kernel: [    9.132133] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137419
Jun 28 17:23:29 martijn-desktop kernel: [    9.132157] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131963
Jun 28 17:23:29 martijn-desktop kernel: [    9.132176] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 401478
Jun 28 17:23:29 martijn-desktop kernel: [    9.133541] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132222
Jun 28 17:23:29 martijn-desktop kernel: [    9.133571] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 393928
Jun 28 17:23:29 martijn-desktop kernel: [    9.133592] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131933
Jun 28 17:23:29 martijn-desktop kernel: [    9.133612] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137671
Jun 28 17:23:29 martijn-desktop kernel: [    9.133632] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137621
Jun 28 17:23:29 martijn-desktop kernel: [    9.133655] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397900
Jun 28 17:23:29 martijn-desktop kernel: [    9.133668] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137147
Jun 28 17:23:29 martijn-desktop kernel: [    9.133685] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131965
Jun 28 17:23:29 martijn-desktop kernel: [    9.133700] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131972
Jun 28 17:23:29 martijn-desktop kernel: [    9.133715] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397687
Jun 28 17:23:29 martijn-desktop kernel: [    9.133728] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397466
Jun 28 17:23:29 martijn-desktop kernel: [    9.133744] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 397461
Jun 28 17:23:29 martijn-desktop kernel: [    9.133756] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396894
Jun 28 17:23:29 martijn-desktop kernel: [    9.133770] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 395992
Jun 28 17:23:29 martijn-desktop kernel: [    9.134715] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 395444
Jun 28 17:23:29 martijn-desktop kernel: [    9.136494] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 394525
Jun 28 17:23:29 martijn-desktop kernel: [    9.136519] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 394348
Jun 28 17:23:29 martijn-desktop kernel: [    9.138301] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 393977
Jun 28 17:23:29 martijn-desktop kernel: [    9.138325] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 393962
Jun 28 17:23:29 martijn-desktop kernel: [    9.138347] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131958
Jun 28 17:23:29 martijn-desktop kernel: [    9.138366] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131930
Jun 28 17:23:29 martijn-desktop kernel: [    9.138385] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131897
Jun 28 17:23:29 martijn-desktop kernel: [    9.138404] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131907
Jun 28 17:23:29 martijn-desktop kernel: [    9.138430] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131923
Jun 28 17:23:29 martijn-desktop kernel: [    9.138443] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131901
Jun 28 17:23:29 martijn-desktop kernel: [    9.138455] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131896
Jun 28 17:23:29 martijn-desktop kernel: [    9.138468] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131895
Jun 28 17:23:29 martijn-desktop kernel: [    9.138480] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137802
Jun 28 17:23:29 martijn-desktop kernel: [    9.138492] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131686
Jun 28 17:23:29 martijn-desktop kernel: [    9.138506] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131787
Jun 28 17:23:29 martijn-desktop kernel: [    9.138519] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131682
Jun 28 17:23:29 martijn-desktop kernel: [    9.138531] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131911
Jun 28 17:23:29 martijn-desktop kernel: [    9.138544] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131590
Jun 28 17:23:29 martijn-desktop kernel: [    9.138557] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 137803
Jun 28 17:23:29 martijn-desktop kernel: [    9.138569] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131913
Jun 28 17:23:29 martijn-desktop kernel: [    9.138582] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131386
Jun 28 17:23:29 martijn-desktop kernel: [    9.138596] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131338
Jun 28 17:23:29 martijn-desktop kernel: [    9.138609] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131290
Jun 28 17:23:29 martijn-desktop kernel: [    9.138622] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131211
Jun 28 17:23:29 martijn-desktop kernel: [    9.138646] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131226
Jun 28 17:23:29 martijn-desktop kernel: [    9.138904] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131996
Jun 28 17:23:29 martijn-desktop kernel: [    9.138926] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1966097
Jun 28 17:23:29 martijn-desktop kernel: [    9.138939] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1966096
Jun 28 17:23:29 martijn-desktop kernel: [    9.138950] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1966095
Jun 28 17:23:29 martijn-desktop kernel: [    9.138960] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1966094
Jun 28 17:23:29 martijn-desktop kernel: [    9.138970] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1966093
Jun 28 17:23:29 martijn-desktop kernel: [    9.138979] EXT4-fs (sda6): 466 orphan inodes deleted
Jun 28 17:23:29 martijn-desktop kernel: [    9.138982] EXT4-fs (sda6): recovery complete
Jun 28 17:23:29 martijn-desktop kernel: [    9.167018] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 17:23:29 martijn-desktop kernel: [    9.649542] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 28 17:23:29 martijn-desktop kernel: [    9.669147] lp: driver loaded but no devices found
Jun 28 17:23:29 martijn-desktop kernel: [    9.695016] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Jun 28 17:23:29 martijn-desktop kernel: [    9.817150] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 28 17:23:29 martijn-desktop kernel: [    9.827573] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jun 28 17:23:29 martijn-desktop kernel: [    9.853035] Linux video capture interface: v2.00
Jun 28 17:23:29 martijn-desktop kernel: [    9.861588] IR NEC protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.865662] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 28 17:23:29 martijn-desktop kernel: [    9.868926] bttv: driver version 0.9.19 loaded
Jun 28 17:23:29 martijn-desktop kernel: [    9.868929] bttv: using 8 buffers with 2080k (520 pages) each for capture
Jun 28 17:23:29 martijn-desktop kernel: [    9.868979] bttv: Bt8xx card found (0)
Jun 28 17:23:29 martijn-desktop kernel: [    9.868994] bttv 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [    9.869005] bttv: 0: Bt878 (rev 17) at 0000:05:02.0, irq: 18, latency: 64, mmio: 0xfaffe000
Jun 28 17:23:29 martijn-desktop kernel: [    9.869412] bttv: 0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
Jun 28 17:23:29 martijn-desktop kernel: [    9.869415] bttv: 0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
Jun 28 17:23:29 martijn-desktop kernel: [    9.869511] bttv: 0: i2c: checking for MSP34xx @ 0x80... 
Jun 28 17:23:29 martijn-desktop kernel: [    9.872344] IR RC5(x) protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.879756] IR RC6 protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.882694] not found
Jun 28 17:23:29 martijn-desktop kernel: [    9.882699] bttv: 0: pinnacle/mt: id=1 info="PAL / mono" radio=no
Jun 28 17:23:29 martijn-desktop kernel: [    9.882702] bttv: 0: tuner type=33
Jun 28 17:23:29 martijn-desktop kernel: [    9.882872] IR JVC protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.886074] IR Sony protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.892468] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 28 17:23:29 martijn-desktop kernel: [    9.892537] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Jun 28 17:23:29 martijn-desktop kernel: [    9.892567] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    9.907118] nvidia: module license 'NVIDIA' taints kernel.
Jun 28 17:23:29 martijn-desktop kernel: [    9.907122] Disabling lock debugging due to kernel taint
Jun 28 17:23:29 martijn-desktop kernel: [    9.918618] i2c-core: driver [msp3400] using legacy suspend method
Jun 28 17:23:29 martijn-desktop kernel: [    9.918621] i2c-core: driver [msp3400] using legacy resume method
Jun 28 17:23:29 martijn-desktop kernel: [    9.925741] IR MCE Keyboard/mouse protocol handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.933585] lirc_dev: IR Remote Control driver registered, major 249 
Jun 28 17:23:29 martijn-desktop kernel: [    9.933776] IR LIRC bridge handler initialized
Jun 28 17:23:29 martijn-desktop kernel: [    9.948356] hda_codec: ALC883: BIOS auto-probing.
Jun 28 17:23:29 martijn-desktop kernel: [    9.956236] bttv: 0: audio absent, no audio device found!
Jun 28 17:23:29 martijn-desktop kernel: [    9.958717] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Jun 28 17:23:29 martijn-desktop kernel: [    9.962471] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jun 28 17:23:29 martijn-desktop kernel: [    9.962548] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jun 28 17:23:29 martijn-desktop kernel: [    9.962610] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jun 28 17:23:29 martijn-desktop kernel: [    9.962672] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jun 28 17:23:29 martijn-desktop kernel: [    9.962735] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jun 28 17:23:29 martijn-desktop kernel: [    9.962802] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Jun 28 17:23:29 martijn-desktop kernel: [    9.962863] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Jun 28 17:23:29 martijn-desktop kernel: [    9.963118] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:23:29 martijn-desktop kernel: [    9.963121] hda_intel: Disabling MSI
Jun 28 17:23:29 martijn-desktop kernel: [    9.963168] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 28 17:23:29 martijn-desktop kernel: [    9.963277] type=1400 audit(1340897009.466:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=621 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.963656] type=1400 audit(1340897009.466:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=621 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.963875] type=1400 audit(1340897009.466:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=621 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.965198] type=1400 audit(1340897009.470:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=818 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.965646] type=1400 audit(1340897009.470:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=818 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.965869] type=1400 audit(1340897009.470:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=818 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [    9.967198] i2c-core: driver [tuner] using legacy suspend method
Jun 28 17:23:29 martijn-desktop kernel: [    9.967201] i2c-core: driver [tuner] using legacy resume method
Jun 28 17:23:29 martijn-desktop kernel: [    9.996544] tda9887 0-0043: creating new instance
Jun 28 17:23:29 martijn-desktop kernel: [    9.996547] tda9887 0-0043: tda988[5/6/7] found
Jun 28 17:23:29 martijn-desktop kernel: [    9.997183] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
Jun 28 17:23:29 martijn-desktop kernel: [   10.010050] Chip ID is not zero. It is not a TEA5767
Jun 28 17:23:29 martijn-desktop kernel: [   10.010056] tuner 0-0060: Tuner -1 found with type(s) Radio TV.
Jun 28 17:23:29 martijn-desktop kernel: [   10.068989] mt20xx 0-0060: microtune: companycode=4d54 part=04 rev=04
Jun 28 17:23:29 martijn-desktop kernel: [   10.120081] mt20xx 0-0060: microtune MT2032 found, OK
Jun 28 17:23:29 martijn-desktop kernel: [   10.130057] bttv: 0: registered device video0
Jun 28 17:23:29 martijn-desktop kernel: [   10.130103] bttv: 0: registered device vbi0
Jun 28 17:23:29 martijn-desktop kernel: [   10.130142] bttv: 0: Setting PLL: 28636363 => 35468950 (needs up to 100ms)
Jun 28 17:23:29 martijn-desktop kernel: [   10.164034] bttv: PLL set ok
Jun 28 17:23:29 martijn-desktop kernel: [   10.176102] snd_bt87x 0000:05:02.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 28 17:23:29 martijn-desktop kernel: [   10.177978] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
Jun 28 17:23:29 martijn-desktop kernel: [   10.324365] init: failsafe main process (1063) killed by TERM signal
Jun 28 17:23:29 martijn-desktop kernel: [   10.398633] type=1400 audit(1340897009.902:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1133 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [   10.401922] type=1400 audit(1340897009.906:9): apparmor="STATUS" operation="profile_load" name="/opt/extras.ubuntu.com/unity-lens-sshsearch/unity-lens-sshsearch.py" pid=1134 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [   10.403521] type=1400 audit(1340897009.906:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1141 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [   10.403723] type=1400 audit(1340897009.906:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1136 comm="apparmor_parser"
Jun 28 17:23:29 martijn-desktop kernel: [   10.409868] ppdev: user-space parallel port driver
Jun 28 17:23:29 martijn-desktop kernel: [   10.421531] Bluetooth: Core ver 2.16
Jun 28 17:23:29 martijn-desktop kernel: [   10.422530] NET: Registered protocol family 31
Jun 28 17:23:29 martijn-desktop kernel: [   10.422534] Bluetooth: HCI device and connection manager initialized
Jun 28 17:23:29 martijn-desktop kernel: [   10.422537] Bluetooth: HCI socket layer initialized
Jun 28 17:23:29 martijn-desktop kernel: [   10.422540] Bluetooth: L2CAP socket layer initialized
Jun 28 17:23:29 martijn-desktop kernel: [   10.422570] Bluetooth: SCO socket layer initialized
Jun 28 17:23:29 martijn-desktop kernel: [   10.431539] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 28 17:23:29 martijn-desktop kernel: [   10.431542] Bluetooth: BNEP filters: protocol multicast
Jun 28 17:23:30 martijn-desktop kernel: [   10.519869] atl1 0000:02:00.0: irq 45 for MSI/MSI-X
Jun 28 17:23:30 martijn-desktop kernel: [   10.519978] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
Jun 28 17:23:30 martijn-desktop kernel: [   10.520920] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 28 17:23:30 martijn-desktop kernel: [   10.521782] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 28 17:23:30 martijn-desktop kernel: [   10.529111] Bluetooth: RFCOMM TTY layer initialized
Jun 28 17:23:30 martijn-desktop kernel: [   10.529116] Bluetooth: RFCOMM socket layer initialized
Jun 28 17:23:30 martijn-desktop kernel: [   10.529118] Bluetooth: RFCOMM ver 1.11
Jun 28 17:23:30 martijn-desktop kernel: [   10.738180] vboxdrv: Found 4 processor cores.
Jun 28 17:23:30 martijn-desktop kernel: [   10.738834] vboxdrv: fAsync=0 offMin=0x42f offMax=0x13f77
Jun 28 17:23:30 martijn-desktop kernel: [   10.738912] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 28 17:23:30 martijn-desktop kernel: [   10.738914] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 28 17:23:30 martijn-desktop kernel: [   10.749426] vboxpci: IOMMU not found (not registered)
Jun 28 17:23:30 martijn-desktop kernel: [   10.856108] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 28 17:23:30 martijn-desktop kernel: [   10.880070] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 28 17:23:30 martijn-desktop kernel: [   10.904047] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 28 17:23:30 martijn-desktop kernel: [   10.928079] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 28 17:23:30 martijn-desktop kernel: [   10.928219] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Jun 28 17:23:30 martijn-desktop kernel: [   10.928416] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
Jun 28 17:23:30 martijn-desktop kernel: [   10.928528] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
Jun 28 17:23:30 martijn-desktop kernel: [   10.928664] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
Jun 28 17:23:30 martijn-desktop kernel: [   10.929250] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 28 17:23:30 martijn-desktop kernel: [   10.929265] nvidia 0000:01:00.0: setting latency timer to 64
Jun 28 17:23:30 martijn-desktop kernel: [   10.929272] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 28 17:23:30 martijn-desktop kernel: [   10.929521] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
Jun 28 17:23:31 martijn-desktop kernel: [   11.567654] Adding 975868k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:975868k SS
Jun 28 17:23:40 martijn-desktop kernel: [   20.672033] eth0: no IPv6 routers present
Jun 28 17:23:46 martijn-desktop kernel: [   27.479660] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=192.168.0.1 DST=192.168.0.4 LEN=327 TOS=0x00 PREC=0x00 TTL=64 ID=58514 PROTO=UDP SPT=1900 DPT=33104 LEN=307 
Jun 28 17:23:49 martijn-desktop kernel: [   29.723079] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=69.171.248.16 DST=192.168.0.4 LEN=439 TOS=0x08 PREC=0x40 TTL=86 ID=28626 DF PROTO=TCP SPT=80 DPT=56153 WINDOW=181 RES=0x00 ACK PSH URGP=0 
Jun 28 17:23:49 martijn-desktop kernel: [   30.006578] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=61 TOS=0x00 PREC=0x00 TTL=118 ID=11526 DF PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK PSH URGP=0 
Jun 28 17:23:51 martijn-desktop kernel: [   31.925248] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=30465 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 
Jun 28 17:23:52 martijn-desktop kernel: [   32.925304] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=8760 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 
Jun 28 17:23:53 martijn-desktop kernel: [   33.925409] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=20049 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 
Jun 28 17:23:54 martijn-desktop kernel: [   34.925287] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=29725 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 
Jun 28 17:23:55 martijn-desktop kernel: [   35.925309] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=8381 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 
Jun 28 17:23:56 martijn-desktop kernel: [   36.941001] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:8b:d0:a8:00:24:01:71:10:17:08:00 SRC=64.4.44.86 DST=192.168.0.4 LEN=41 TOS=0x00 PREC=0x00 TTL=118 ID=18290 PROTO=TCP SPT=1863 DPT=53841 WINDOW=64990 RES=0x00 ACK URGP=0 



```

---

