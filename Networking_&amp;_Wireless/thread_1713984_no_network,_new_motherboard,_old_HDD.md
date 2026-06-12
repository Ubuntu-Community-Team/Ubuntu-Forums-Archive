---
title: "no network, new motherboard, old HDD"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2011-03-24
I have a slightly unusual situation. I have a couple of new motherboards which are VERY similar to some other motherboards I am working with (all Zotac with Nvidia ION GPUs and Intel Atom 330 CPUs). I have cloned several HDDs using a disk duplicator. I have deployed several of these to duplicate hardware simply by changing the hostname. So far so good.

The two new motherboards, which are _slightly_ different, when driven by cloned HDDs, don't recognize either of the network systems wireless or wired.

I'm trying to avoid the tedious process of freshly installing Ubuntu and the vast number of custom settings I have. The new systems boot fine, they just have no networking.

How can I force, or cajole, Ubuntu into re-scanning the hardware?
What else might be fouling things up?

---

### Post by Cheesehead on 2011-03-24
What have you tried?
What errors show up in dmesg? syslog?

A common issue with cloned HDDs is that udev has mapped MAC addresses to interfaces in /etc/udev/rules/*-persistent-net. Since the new motherboard hardware has different MACs, they get different interface names (like eth1 instead of eth0). Udev renaming the interface from eth0 to eth1 will show up in syslog ('less /var/log/syslog | grep eth0')

Then, when the system brings up interfaces per /etc/networking/interfaces, the new interfaces don't get configured because they are not on the list.

*IF* this is your problem, it's an easy fix - just edit that udev rules file.

Alternately, some software for PCI cards tracks the slot number in /etc/*.conf files. Of course, this software will also usually have an autodetect utility...but you may need to update the .conf file by hand.

---

### Post by Clive McCarthy on 2011-03-25
Thanks for the suggestions. The syslog reveals that eth0 has 'forcedeth' which is slightly amusing (if only that were possible for Qadaffi). And that it is renamed eth6.

It's not likely to be an issue with the MAC address because HDDs cloned in this manner work fine with other *identical* motherboards which obviously have different MAC addresses. There is probably something up (different) with the PCI/physical addresses of the network hardware on this *nearly identical* motherboard.

I have booted this HDD on the motherboard type (but NOT the exact board) from which the clone was made and the HDD boots & connects normally to my network.

I haven't dug into the /etc/udev/rules yet. That is next... I shall have to learn what is in the rule files because I'm not a Linux internals expert.

Is there some means of restarting the mechanism that installs all the rules? I tried restarting the network manager service but that is probably well after the trouble is set in the boot sequence.

[later] I've restarted the machine in recovery mode and have started dpkg -- I'm assuming this will reset a bunch of stuff but hopefully not all of my settings...

---

### Post by Clive McCarthy on 2011-03-25
Looks like that fixed things.

The sequence was:
press <shift> to enter grub2 menu
select **recovery** mode
select **dpkg**
wait a good while as packages are re-installed...
**sudo reboot**
system drops to tty mode without GUI (Nvidia driver has been clobbered)
re-install proprietary Nvidia driver (it's WAY faster than Nouveau)
**reboot**
system settings seem intact and networking is running. :)

Oops, spoke too soon. Wired network is UP but wireless isn't.

---

### Post by Clive McCarthy on 2011-03-25
Here is the output from dmesg and the eth0 content of syslog:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffa0000 - 000000001ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffae000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ffa0000 (usable)
[    0.000000]  modified: 000000001ffa0000 - 000000001ffae000 (ACPI data)
[    0.000000]  modified: 000000001ffae000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  modified: 000000001fff0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-000000001ffa0000
[    0.000000]  0000000000 - 001ffa0000 page 4k
[    0.000000] kernel direct mapping tables up to 1ffa0000 @ 15000-98000
[    0.000000] RAMDISK: 175b5000 - 17ff8000
[    0.000000] ACPI: RSDP 000fa810 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 1ffa0000 00040 (v01 072009 RSDT1618 20090720 MSFT 00000097)
[    0.000000] ACPI: FACP 1ffa0200 00084 (v01 072009 FACP1618 20090720 MSFT 00000097)
[    0.000000] ACPI: DSDT 1ffa04a0 070E9 (v01   NVDA NVDAACPI 00001000 INTL 20051117)
[    0.000000] ACPI: FACS 1ffae000 00040
[    0.000000] ACPI: APIC 1ffa0390 00080 (v01 072009 APIC1618 20090720 MSFT 00000097)
[    0.000000] ACPI: MCFG 1ffa0410 0003C (v01 072009 OEMMCFG  20090720 MSFT 00000097)
[    0.000000] ACPI: WDRT 1ffa0450 00047 (v01 072009 NV-WDRT  20090720 MSFT 00000097)
[    0.000000] ACPI: OEMB 1ffae040 00079 (v01 072009 OEMB1618 20090720 MSFT 00000097)
[    0.000000] ACPI: HPET 1ffaa4a0 00038 (v01 072009 OEMHPET0 20090720 MSFT 00000097)
[    0.000000] ACPI: NVHD 1ffae0c0 00284 (v01 072009  NVHDCP  20090720 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffa0000
[    0.000000]   low ram: 0 - 1ffa0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffa0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffa0
[    0.000000] On node 0 totalpages: 130863
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125888 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [92000 - 927ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1405000 s36416 r0 d20928 u65536
[    0.000000] pcpu-alloc: s36416 r0 d20928 u65536 alloc=16*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129839
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=8082fa15-6b36-4e4f-8588-c6271df90638 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2619200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00175b5000 - 0017ff8000]         RAMDISK
[    0.000000]   #4 [00009a1000 - 00009a41bf]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fdc10]   BIOS reserved
[    0.000000]   #8 [00000fdd5c - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fdc10 - 00000fdd5c]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000092000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #15 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #16 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #17 [0001401100 - 0001401130]         BOOTMEM
[    0.000000]   #18 [0001401140 - 0001402940]         BOOTMEM
[    0.000000]   #19 [0001402940 - 0001402965]         BOOTMEM
[    0.000000]   #20 [0001402980 - 00014029a7]         BOOTMEM
[    0.000000]   #21 [00014029c0 - 0001402af4]         BOOTMEM
[    0.000000]   #22 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #23 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #24 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #25 [0001402bc0 - 0001402c00]         BOOTMEM
[    0.000000]   #26 [0001402c00 - 0001402c40]         BOOTMEM
[    0.000000]   #27 [0001402c40 - 0001402c80]         BOOTMEM
[    0.000000]   #28 [0001402c80 - 0001402cc0]         BOOTMEM
[    0.000000]   #29 [0001402cc0 - 0001402d00]         BOOTMEM
[    0.000000]   #30 [0001402d00 - 0001402d40]         BOOTMEM
[    0.000000]   #31 [0001402d40 - 0001402d80]         BOOTMEM
[    0.000000]   #32 [0001402d80 - 0001402d90]         BOOTMEM
[    0.000000]   #33 [0001402dc0 - 0001402e2a]         BOOTMEM
[    0.000000]   #34 [0001402e40 - 0001402eaa]         BOOTMEM
[    0.000000]   #35 [0001405000 - 0001413000]         BOOTMEM
[    0.000000]   #36 [0001415000 - 0001423000]         BOOTMEM
[    0.000000]   #37 [0001425000 - 0001433000]         BOOTMEM
[    0.000000]   #38 [0001435000 - 0001443000]         BOOTMEM
[    0.000000]   #39 [0001404ec0 - 0001404ec4]         BOOTMEM
[    0.000000]   #40 [0001404f00 - 0001404f04]         BOOTMEM
[    0.000000]   #41 [0001404f40 - 0001404f50]         BOOTMEM
[    0.000000]   #42 [0001404f80 - 0001404f90]         BOOTMEM
[    0.000000]   #43 [0001413000 - 0001413080]         BOOTMEM
[    0.000000]   #44 [0001404fc0 - 0001404fec]         BOOTMEM
[    0.000000]   #45 [0001402ec0 - 0001404ec0]         BOOTMEM
[    0.000000]   #46 [0001443000 - 0001483000]         BOOTMEM
[    0.000000]   #47 [0001483000 - 00014a3000]         BOOTMEM
[    0.000000]   #48 [00014a3000 - 0001722740]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 496284k/523904k available (4930k kernel code, 27168k reserved, 2334k data, 684k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07a0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdffa0000   ( 511 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1599.720 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.44 BogoMIPS (lpj=6398880)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004063] Security Framework initialized
[    0.004099] AppArmor: AppArmor initialized
[    0.004104] Yama: becoming mindful.
[    0.004228] Mount-cache hash table entries: 512
[    0.004470] Initializing cgroup subsys ns
[    0.004480] Initializing cgroup subsys cpuacct
[    0.004491] Initializing cgroup subsys memory
[    0.004510] Initializing cgroup subsys devices
[    0.004516] Initializing cgroup subsys freezer
[    0.004522] Initializing cgroup subsys net_cls
[    0.004568] Atom PSE erratum detected, BIOS microcode update recommended
[    0.004579] CPU: Physical Processor ID: 0
[    0.004583] CPU: Processor Core ID: 0
[    0.004589] mce: CPU supports 5 MCE banks
[    0.004603] CPU0: Thermal monitoring enabled (TM1)
[    0.004611] using mwait in idle threads.
[    0.004623] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.004657] ... version:                3
[    0.004661] ... bit width:              40
[    0.004666] ... generic registers:      2
[    0.004671] ... value mask:             000000ffffffffff
[    0.004677] ... max period:             000000007fffffff
[    0.004682] ... fixed-purpose events:   3
[    0.004686] ... event mask:             0000000700000003
[    0.012140] ACPI: Core revision 20100428
[    0.030326] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030339] ftrace: allocating 21766 entries in 43 pages
[    0.032110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032543] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074835] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.076000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.164182]  #2
[    0.008000] Initializing CPU#2
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.256236]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.348021] Brought up 4 CPUs
[    0.348029] Total of 4 processors activated (12799.34 BogoMIPS).
[    0.349910] devtmpfs: initialized
[    0.353634] regulator: core version 0.5
[    0.353712] Time:  4:00:13  Date: 03/26/11
[    0.353802] NET: Registered protocol family 16
[    0.353830] Trying to unpack rootfs image as initramfs...
[    0.354152] EISA bus registered
[    0.354177] ACPI: bus type pci registered
[    0.354345] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.354352] PCI: not using MMCONFIG
[    0.354687] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.354691] PCI: Using configuration type 1 for base access
[    0.357130] bio: create slab <bio-0> at 0
[    0.361685] ACPI: EC: Look up EC in DSDT
[    0.366126] ACPI: Executed 1 blocks of module-level executable AML code
[    0.384689] ACPI: Interpreter enabled
[    0.384699] ACPI: (supports S0 S1 S3 S4 S5)
[    0.384756] ACPI: Using IOAPIC for interrupt routing
[    0.384883] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.390023] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.390030] PCI: Using MMCONFIG for extended config space
[    0.426953] ACPI: No dock devices found.
[    0.426966] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.428000] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.428822] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.428831] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.428838] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.428845] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.428852] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xfbffffff]
[    0.428859] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.429135] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.429267] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.429288] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.429298] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.429331] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.429341] pci 0000:00:03.2: PME# disabled
[    0.429493] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.429604] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.429650] pci 0000:00:04.0: supports D1 D2
[    0.429656] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429663] pci 0000:00:04.0: PME# disabled
[    0.429702] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.429753] pci 0000:00:04.1: supports D1 D2
[    0.429759] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429766] pci 0000:00:04.1: PME# disabled
[    0.429813] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.429857] pci 0000:00:06.0: supports D1 D2
[    0.429862] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429870] pci 0000:00:06.0: PME# disabled
[    0.429908] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
[    0.429960] pci 0000:00:06.1: supports D1 D2
[    0.429965] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429972] pci 0000:00:06.1: PME# disabled
[    0.430019] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.430064] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.430071] pci 0000:00:08.0: PME# disabled
[    0.430155] pci 0000:00:0a.0: reg 10: [mem 0xfae7c000-0xfae7cfff]
[    0.430165] pci 0000:00:0a.0: reg 14: [io  0xd080-0xd087]
[    0.430174] pci 0000:00:0a.0: reg 18: [mem 0xfae7e400-0xfae7e4ff]
[    0.430183] pci 0000:00:0a.0: reg 1c: [mem 0xfae7e000-0xfae7e00f]
[    0.430217] pci 0000:00:0a.0: supports D1 D2
[    0.430223] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430231] pci 0000:00:0a.0: PME# disabled
[    0.430270] pci 0000:00:0b.0: reg 10: [io  0xd000-0xd007]
[    0.430280] pci 0000:00:0b.0: reg 14: [io  0xcc00-0xcc03]
[    0.430289] pci 0000:00:0b.0: reg 18: [io  0xc880-0xc887]
[    0.430298] pci 0000:00:0b.0: reg 1c: [io  0xc800-0xc803]
[    0.430307] pci 0000:00:0b.0: reg 20: [io  0xc480-0xc48f]
[    0.430317] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.430562] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430574] pci 0000:00:0c.0: PME# disabled
[    0.430686] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430693] pci 0000:00:10.0: PME# disabled
[    0.430915] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430927] pci 0000:00:15.0: PME# disabled
[    0.431175] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.431186] pci 0000:00:16.0: PME# disabled
[    0.431441] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.431452] pci 0000:00:17.0: PME# disabled
[    0.431696] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.431708] pci 0000:00:18.0: PME# disabled
[    0.431836] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.431846] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431858] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.431868] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.431875] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.431882] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.431889] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.431896] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.431903] pci 0000:00:09.0:   bridge window [mem 0x40000000-0xfbffffff] (subtractive decode)
[    0.431910] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.432100] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.432119] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432132] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432151] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432224] pci 0000:03:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.432240] pci 0000:03:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.432256] pci 0000:03:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.432266] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]
[    0.432277] pci 0000:03:00.0: reg 30: [mem 0xfafe0000-0xfaffffff pref]
[    0.432350] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.432359] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.432367] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.432376] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.432573] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.432641] pci 0000:04:00.0: supports D1
[    0.432646] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.432654] pci 0000:04:00.0: PME# disabled
[    0.440035] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.440056] pci 0000:00:15.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.440070] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.440091] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.440253] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.440272] pci 0000:00:16.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.440285] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.440304] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.440463] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.440482] pci 0000:00:17.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.440495] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.440514] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.440680] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.440699] pci 0000:00:18.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.440713] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.440733] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.440814] pci_bus 0000:00: on NUMA node 0
[    0.440829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.441312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.441500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.441650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.441857] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.442027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.442200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.442370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.481451] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.482038] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.482617] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.483195] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.483777] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.484377] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.484956] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.485537] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.486115] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.486705] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.487286] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.487876] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.488475] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.489056] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.489635] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.490216] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.490804] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.491385] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.491972] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.492571] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.493152] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.493730] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.494311] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.494889] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.495473] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.496071] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.496652] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.497233] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.497814] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.498396] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.498977] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.499557] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.500176] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.500772] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.501361] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.501951] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.502542] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.503133] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.503724] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *9
[    0.504342] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.505017] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.505612] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.506204] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *9
[    0.506794] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.507384] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.507973] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.508595] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.509195] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.509790] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15
[    0.510392] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14
[    0.510519] HEST: Table is not found!
[    0.510754] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.510762] vgaarb: loaded
[    0.511180] SCSI subsystem initialized
[    0.511215] libata version 3.00 loaded.
[    0.511215] usbcore: registered new interface driver usbfs
[    0.511215] usbcore: registered new interface driver hub
[    0.511215] usbcore: registered new device driver usb
[    0.512684] ACPI: WMI: Mapper loaded
[    0.512691] PCI: Using ACPI for IRQ routing
[    0.512706] PCI: pci_cache_line_size set to 64 bytes
[    0.512870] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.512877] reserve RAM buffer: 000000001ffa0000 - 000000001fffffff 
[    0.513111] NetLabel: Initializing
[    0.513116] NetLabel:  domain hash size = 128
[    0.513120] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.513148] NetLabel:  unlabeled traffic allowed by default
[    0.513251] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.513263] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.513276] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.524048] Switching to clocksource tsc
[    0.545373] AppArmor: AppArmor Filesystem Enabled
[    0.545416] pnp: PnP ACPI init
[    0.545459] ACPI: bus type pnp registered
[    0.559963] pnp: PnP ACPI: found 13 devices
[    0.559971] ACPI: ACPI bus type pnp unregistered
[    0.559980] PnPBIOS: Disabled by ACPI PNP
[    0.560015] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.560023] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.560030] system 00:05: [io  0x4000-0x407f] has been reserved
[    0.560037] system 00:05: [io  0x4080-0x40ff] has been reserved
[    0.560044] system 00:05: [io  0x4400-0x447f] has been reserved
[    0.560051] system 00:05: [io  0x4480-0x44ff] has been reserved
[    0.560058] system 00:05: [io  0x4800-0x487f] has been reserved
[    0.560065] system 00:05: [io  0x4880-0x48ff] has been reserved
[    0.560073] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.560081] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.560088] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.560096] system 00:05: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.560104] system 00:05: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.560111] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.560127] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.560135] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.560148] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
[    0.560155] system 00:0a: [io  0x0a10-0x0a1f] has been reserved
[    0.560168] system 00:0b: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.560181] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.560189] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.560196] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.560203] system 00:0c: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.560211] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.599145] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.599152] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.599160] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.599167] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.599176] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.599181] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.599195] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.599205] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.599224] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.599231] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.599240] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.599248] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.599268] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.599272] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.599287] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.599299] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.599316] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.599321] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.599334] pci 0000:00:16.0:   bridge window [mem disabled]
[    0.599345] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.599364] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.599369] pci 0000:00:17.0:   bridge window [io  disabled]
[    0.599385] pci 0000:00:17.0:   bridge window [mem disabled]
[    0.599396] pci 0000:00:17.0:   bridge window [mem pref disabled]
[    0.599418] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.599423] pci 0000:00:18.0:   bridge window [io  disabled]
[    0.599437] pci 0000:00:18.0:   bridge window [mem disabled]
[    0.599448] pci 0000:00:18.0:   bridge window [mem pref disabled]
[    0.599482] pci 0000:00:09.0: setting latency timer to 64
[    0.600376] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.600389]   alloc irq_desc for 23 on node -1
[    0.600394]   alloc kstat_irqs on node -1
[    0.600411] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.600425] pci 0000:00:0c.0: setting latency timer to 64
[    0.600442] pci 0000:00:10.0: setting latency timer to 64
[    0.601273] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.601281]   alloc irq_desc for 22 on node -1
[    0.601285]   alloc kstat_irqs on node -1
[    0.601297] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.601310] pci 0000:00:15.0: setting latency timer to 64
[    0.602139] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.602147]   alloc irq_desc for 21 on node -1
[    0.602151]   alloc kstat_irqs on node -1
[    0.602162] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.602176] pci 0000:00:16.0: setting latency timer to 64
[    0.603005] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20
[    0.603013]   alloc irq_desc for 20 on node -1
[    0.603018]   alloc kstat_irqs on node -1
[    0.603029] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 20 (level, low) -> IRQ 20
[    0.603043] pci 0000:00:17.0: setting latency timer to 64
[    0.603905] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23
[    0.603914] pci 0000:00:18.0: PCI INT A -> Link[LRP6] -> GSI 23 (level, low) -> IRQ 23
[    0.603928] pci 0000:00:18.0: setting latency timer to 64
[    0.603940] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.603946] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.603952] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.603959] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.603965] pci_bus 0000:00: resource 8 [mem 0x40000000-0xfbffffff]
[    0.603971] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.603979] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.603985] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.603991] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.603997] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.604003] pci_bus 0000:01: resource 8 [mem 0x40000000-0xfbffffff]
[    0.604009] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.604016] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.604022] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.604028] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.604035] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.604115] NET: Registered protocol family 2
[    0.604267] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.604719] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.604847] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.604969] TCP: Hash tables configured (established 16384 bind 16384)
[    0.604975] TCP reno registered
[    0.604981] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.604995] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.605181] NET: Registered protocol family 1
[    0.679563] pci 0000:03:00.0: Boot video device
[    0.679576] PCI: CLS 64 bytes, default 64
[    0.680332] cpufreq-nforce2: No nForce2 chipset.
[    0.680408] Scanning for low memory corruption every 60 seconds
[    0.680677] audit: initializing netlink socket (disabled)
[    0.680700] type=2000 audit(1301112013.676:1): initialized
[    0.700142] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.703850] VFS: Disk quotas dquot_6.5.2
[    0.703997] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.705492] fuse init (API version 7.14)
[    0.705741] msgmni has been set to 969
[    0.706706] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.706715] io scheduler noop registered
[    0.706720] io scheduler deadline registered
[    0.706762] io scheduler cfq registered (default)
[    0.707043] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.707175]   alloc irq_desc for 40 on node -1
[    0.707180]   alloc kstat_irqs on node -1
[    0.707209] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.707451] pcieport 0000:00:15.0: setting latency timer to 64
[    0.707578]   alloc irq_desc for 41 on node -1
[    0.707583]   alloc kstat_irqs on node -1
[    0.707608] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.707827] pcieport 0000:00:16.0: setting latency timer to 64
[    0.707952]   alloc irq_desc for 42 on node -1
[    0.707956]   alloc kstat_irqs on node -1
[    0.707980] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.708187] pcieport 0000:00:17.0: setting latency timer to 64
[    0.708312]   alloc irq_desc for 43 on node -1
[    0.708316]   alloc kstat_irqs on node -1
[    0.708340] pcieport 0000:00:17.0: irq 43 for MSI/MSI-X
[    0.708543] pcieport 0000:00:18.0: setting latency timer to 64
[    0.708668]   alloc irq_desc for 44 on node -1
[    0.708672]   alloc kstat_irqs on node -1
[    0.708696] pcieport 0000:00:18.0: irq 44 for MSI/MSI-X
[    0.708943] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.709005] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.709243] intel_idle: MWAIT substates: 0x10
[    0.709248] intel_idle: v0.4 model 0x1C
[    0.709252] intel_idle: lapic_timer_reliable_states 0x6
[    0.709577] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.709600] ACPI: Power Button [PWRB]
[    0.709740] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.709749] ACPI: Power Button [PWRF]
[    0.710475] ACPI: acpi_idle yielding to intel_idle
[    0.724934] ERST: Table is not found!
[    0.725198] isapnp: Scanning for PnP cards...
[    0.725683] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.725831] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.726331] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.729501] brd: module loaded
[    0.730908] loop: module loaded
[    0.732437] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    0.732451] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    0.732508] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.732534] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.733416] Fixed MDIO Bus: probed
[    0.733510] PPP generic driver version 2.4.2
[    0.733641] tun: Universal TUN/TAP device driver, 1.6
[    0.733646] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.733861] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.734746] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.734758] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.734797] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.734804] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.734910] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.734956] ehci_hcd 0000:00:04.1: debug port 1
[    0.734968] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.735008] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfae7ec00
[    0.743300] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.743609] hub 1-0:1.0: USB hub found
[    0.743622] hub 1-0:1.0: 6 ports detected
[    0.744611] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    0.744622] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    0.744655] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.744662] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.744773] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.744816] ehci_hcd 0000:00:06.1: debug port 1
[    0.744830] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.744873] ehci_hcd 0000:00:06.1: irq 20, io mem 0xfae7e800
[    0.755298] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.755583] hub 2-0:1.0: USB hub found
[    0.755601] hub 2-0:1.0: 6 ports detected
[    0.755773] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.756656] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.756668] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    0.756702] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.756709] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.756821] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.756873] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[    0.813633] hub 3-0:1.0: USB hub found
[    0.813650] hub 3-0:1.0: 6 ports detected
[    0.814934] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    0.814947] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    0.814986] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.814994] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.815124] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.815184] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
[    0.869778] hub 4-0:1.0: USB hub found
[    0.869795] hub 4-0:1.0: 6 ports detected
[    0.869984] uhci_hcd: USB Universal Host Controller Interface driver
[    0.870239] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.870246] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.870819] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.871119] mice: PS/2 mouse device common for all mice
[    0.871556] rtc_cmos 00:07: RTC can wake from S4
[    0.871681] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.871749] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.872117] device-mapper: uevent: version 1.0.3
[    0.872532] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.872906] device-mapper: multipath: version 1.1.1 loaded
[    0.872916] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.873343] EISA: Probing bus 0 at eisa.0
[    0.873352] EISA: Cannot allocate resource for mainboard
[    0.873361] Cannot allocate resource for EISA slot 1
[    0.873369] Cannot allocate resource for EISA slot 2
[    0.873377] Cannot allocate resource for EISA slot 3
[    0.873385] Cannot allocate resource for EISA slot 4
[    0.873392] Cannot allocate resource for EISA slot 5
[    0.873400] Cannot allocate resource for EISA slot 6
[    0.873408] Cannot allocate resource for EISA slot 7
[    0.873415] Cannot allocate resource for EISA slot 8
[    0.873421] EISA: Detected 0 cards.
[    0.874245] cpuidle: using governor ladder
[    0.874657] cpuidle: using governor menu
[    0.875546] TCP cubic registered
[    0.876061] NET: Registered protocol family 10
[    0.877130] lo: Disabled Privacy Extensions
[    0.877752] NET: Registered protocol family 17
[    0.877928] Using IPI No-Shortcut mode
[    0.878221] PM: Resume from disk failed.
[    0.878250] registered taskstats version 1
[    0.879010]   Magic number: 3:318:10
[    0.879202] rtc_cmos 00:07: setting system clock to 2011-03-26 04:00:14 UTC (1301112014)
[    0.879212] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.879217] EDD information not available.
[    0.888272] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.960815] Freeing initrd memory: 10508k freed
[    1.078578] isapnp: No Plug & Play device found
[    1.078653] Freeing unused kernel memory: 684k freed
[    1.079466] Write protecting the kernel text: 4932k
[    1.079566] Write protecting the kernel read-only data: 1976k
[    1.120117] udev[99]: starting version 163
[    1.296597] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.298034] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.298054] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.298071] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.362912] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
[    1.362922] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.362981] ahci 0000:00:0b.0: version 3.0
[    1.363017] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.363113]   alloc irq_desc for 45 on node -1
[    1.363119]   alloc kstat_irqs on node -1
[    1.363139] ahci 0000:00:0b.0: irq 45 for MSI/MSI-X
[    1.363151] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    1.363284] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.363294] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    1.363304] ahci 0000:00:0b.0: setting latency timer to 64
[    1.364805] scsi0 : ahci
[    1.365248] scsi1 : ahci
[    1.365563] scsi2 : ahci
[    1.365883] scsi3 : ahci
[    1.366173] scsi4 : ahci
[    1.366474] scsi5 : ahci
[    1.367028] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 45
[    1.367037] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 45
[    1.367045] ata3: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76200 irq 45
[    1.367051] ata4: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76280 irq 45
[    1.367058] ata5: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76300 irq 45
[    1.367065] ata6: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76380 irq 45
[    1.369059] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.654316] usbcore: registered new interface driver hiddev
[    1.660783] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input3
[    1.661183] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:06.0-1/input0
[    1.668965] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:06.0-1/input1
[    1.669035] usbcore: registered new interface driver usbhid
[    1.669042] usbhid: USB HID core driver
[    1.685033] ata1: SATA link down (SStatus 0 SControl 300)
[    1.685148] ata5: SATA link down (SStatus 0 SControl 300)
[    1.685158] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.685194] ata2: SATA link down (SStatus 0 SControl 300)
[    1.685200] ata3: SATA link down (SStatus 0 SControl 300)
[    1.685235] ata6: SATA link down (SStatus 0 SControl 300)
[    1.685876] ata4.00: ATA-8: WDC WD2500AAJS-00V4A0, 05.01D05, max UDMA/133
[    1.685884] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.686741] ata4.00: configured for UDMA/133
[    1.687024] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-0 05.0 PQ: 0 ANSI: 5
[    1.687495] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.687566] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    1.687695] sd 3:0:0:0: [sda] Write Protect is off
[    1.687704] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.687805] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.688328]  sda: sda1 sda2 < sda5 >
[    1.736091] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.892036] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    2.077083] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.139617] input:   USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-2/3-2:1.0/input/input4
[    2.139831] generic-usb 0003:04D9:1603.0003: input,hidraw2: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:04.0-2/input0
[    2.163787] input:   USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-2/3-2:1.1/input/input5
[    2.163997] generic-usb 0003:04D9:1603.0004: input,hidraw3: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:04.0-2/input1
[    8.516355] udev[370]: starting version 163
[    8.557518] lp: driver loaded but no devices found
[    8.588484] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
[    8.654821] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[    8.654845] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [??? 0x00004e00-0x00004e3f flags 0x30]
[    8.654855] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.808563] Linux agpgart interface v0.103
[    8.808749] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.823034] udev[384]: renamed network interface eth0 to eth6
[    9.005801] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.145723] nvidia: module license 'NVIDIA' taints kernel.
[    9.145732] Disabling lock debugging due to kernel taint
[    9.147168] type=1400 audit(1301112022.762:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=614 comm="apparmor_parser"
[    9.148036] type=1400 audit(1301112022.762:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[    9.148546] type=1400 audit(1301112022.762:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[    9.251004] cfg80211: Calling CRDA to update world regulatory domain
[    9.547287] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[    9.547307]   alloc irq_desc for 19 on node -1
[    9.547314]   alloc kstat_irqs on node -1
[    9.547338] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    9.547361] ath9k 0000:04:00.0: setting latency timer to 64
[    9.598322] ath: EEPROM regdomain: 0x60
[    9.598331] ath: EEPROM indicates we should expect a direct regpair map
[    9.598342] ath: Country alpha2 being used: 00
[    9.598348] ath: Regpair used: 0x60
[    9.624968] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.627035] Registered led device: ath9k-phy0::radio
[    9.627106] Registered led device: ath9k-phy0::assoc
[    9.627179] Registered led device: ath9k-phy0::tx
[    9.627248] Registered led device: ath9k-phy0::rx
[    9.627274] phy0: Atheros AR9285 Rev:2 mem=0xe3320000, irq=19
[    9.677096] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    9.677239] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    9.678447] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[    9.678462] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[    9.678472] hda_intel: Disable MSI for Nvidia chipset
[    9.678554] HDA Intel 0000:00:08.0: setting latency timer to 64
[    9.686710] cfg80211: World regulatory domain updated:
[    9.686719]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.686727]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.686734]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.686740]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.686747]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.686754]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.874284] type=1400 audit(1301112023.490:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=819 comm="apparmor_parser"
[    9.878992] type=1400 audit(1301112023.494:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=820 comm="apparmor_parser"
[    9.879881] type=1400 audit(1301112023.494:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=820 comm="apparmor_parser"
[    9.880412] type=1400 audit(1301112023.494:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=820 comm="apparmor_parser"
[    9.889492] type=1400 audit(1301112023.502:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=825 comm="apparmor_parser"
[    9.892774] type=1400 audit(1301112023.506:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=824 comm="apparmor_parser"
[    9.894319] type=1400 audit(1301112023.510:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=824 comm="apparmor_parser"
[   10.561547] hda_codec: ALC662 rev1: BIOS auto-probing.
[   10.761341] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   14.030453] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 23
[   14.030472] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 23 (level, low) -> IRQ 23
[   14.031485] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 22
[   14.031497] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   14.031514] nvidia 0000:03:00.0: setting latency timer to 64
[   14.031525] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.032338] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.21  Thu Nov  4 20:24:24 PDT 2010
[   14.039089] udev[386]: renamed network interface wlan0 to wlan6
[   14.181351] ppdev: user-space parallel port driver
[   14.204108] ADDRCONF(NETDEV_UP): wlan6: link is not ready
[   19.060563] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.120022] eth6: no IPv6 routers present
[   25.462687] wlan6: authenticate with 00:0f:a3:1c:a1:f9 (try 1)
[   25.465525] wlan6: authenticated
[   25.465597] wlan6: associate with 00:0f:a3:1c:a1:f9 (try 1)
[   25.467804] wlan6: RX AssocResp from 00:0f:a3:1c:a1:f9 (capab=0x411 status=0 aid=14)
[   25.467814] wlan6: associated
[   25.468169] ADDRCONF(NETDEV_CHANGE): wlan6: link becomes ready
[   25.486148] cfg80211: Calling CRDA for country: US
[   25.501072] cfg80211: Received country IE:
[   25.501086] cfg80211: Regulatory domain: US
[   25.501093]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.501104]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[   25.501111] cfg80211: CRDA thinks this should applied:
[   25.501118] cfg80211: Regulatory domain: US
[   25.501124]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.501134]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   25.501145]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   25.501155]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.501165]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.501175]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.501185]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   25.501192] cfg80211: We intersect both of these and get:
[   25.501198] cfg80211: Regulatory domain: 98
[   25.501204]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.501214]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   25.501239] cfg80211: Current regulatory domain updated by AP to: US
[   25.501247]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.501257]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   36.088022] wlan6: no IPv6 routers present
[   70.629100] wlan6: deauthenticating from 00:0f:a3:1c:a1:f9 by local choice (reason=3)
[   70.666242] cfg80211: All devices are disconnected, going to restore regulatory settings
[   70.666258] cfg80211: Restoring regulatory settings
[   70.666271] cfg80211: Calling CRDA to update world regulatory domain
[   70.675623] cfg80211: World regulatory domain updated:
[   70.675632]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   70.675640]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   70.675647]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   70.675654]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   70.675660]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   70.675667]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.808300] wlan6: authenticate with 00:0f:a3:1c:a1:f9 (try 1)
[   71.810819] wlan6: authenticated
[   71.810865] wlan6: associate with 00:0f:a3:1c:a1:f9 (try 1)
[   71.813086] wlan6: RX AssocResp from 00:0f:a3:1c:a1:f9 (capab=0x411 status=0 aid=14)
[   71.813094] wlan6: associated
[   71.833205] cfg80211: Calling CRDA for country: US
[   71.845839] cfg80211: Received country IE:
[   71.845853] cfg80211: Regulatory domain: US
[   71.845860]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.845870]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[   71.845878] cfg80211: CRDA thinks this should applied:
[   71.845884] cfg80211: Regulatory domain: US
[   71.845889]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.845900]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   71.845910]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   71.845920]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.845930]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.845940]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.845950]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   71.845957] cfg80211: We intersect both of these and get:
[   71.845963] cfg80211: Regulatory domain: 98
[   71.845969]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.845979]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   71.846000] cfg80211: Current regulatory domain updated by AP to: US
[   71.846007]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.846018]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  117.597135] wlan6: deauthenticating from 00:0f:a3:1c:a1:f9 by local choice (reason=3)
[  117.643925] cfg80211: All devices are disconnected, going to restore regulatory settings
[  117.643943] cfg80211: Restoring regulatory settings
[  117.643956] cfg80211: Calling CRDA to update world regulatory domain
[  117.653638] cfg80211: World regulatory domain updated:
[  117.653647]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  117.653655]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.653662]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.653669]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.653676]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.653682]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  118.792393] wlan6: authenticate with 00:0f:a3:1c:a1:f9 (try 1)
[  118.794589] wlan6: authenticated
[  118.794645] wlan6: associate with 00:0f:a3:1c:a1:f9 (try 1)
[  118.796850] wlan6: RX AssocResp from 00:0f:a3:1c:a1:f9 (capab=0x411 status=0 aid=14)
[  118.796860] wlan6: associated
[  118.816143] cfg80211: Calling CRDA for country: US
[  118.828482] cfg80211: Received country IE:
[  118.828495] cfg80211: Regulatory domain: US
[  118.828501]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  118.828512]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[  118.828519] cfg80211: CRDA thinks this should applied:
[  118.828526] cfg80211: Regulatory domain: US
[  118.828531]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  118.828542]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  118.828552]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  118.828562]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  118.828572]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  118.828581]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  118.828591]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  118.828598] cfg80211: We intersect both of these and get:
[  118.828605] cfg80211: Regulatory domain: 98
[  118.828610]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  118.828621]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  118.828642] cfg80211: Current regulatory domain updated by AP to: US
[  118.828650]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  118.828660]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  164.601709] wlan6: deauthenticating from 00:0f:a3:1c:a1:f9 by local choice (reason=3)
[  164.633774] cfg80211: All devices are disconnected, going to restore regulatory settings
[  164.633789] cfg80211: Restoring regulatory settings
[  164.633800] cfg80211: Calling CRDA to update world regulatory domain
[  164.647175] cfg80211: World regulatory domain updated:
[  164.647186]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  164.647198]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  164.647209]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  164.647219]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  164.647229]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  164.647239]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  165.796145] wlan6: authenticate with 00:0f:a3:1c:a1:f9 (try 1)
[  165.798161] wlan6: authenticated
[  165.798220] wlan6: associate with 00:0f:a3:1c:a1:f9 (try 1)
[  165.800421] wlan6: RX AssocResp from 00:0f:a3:1c:a1:f9 (capab=0x411 status=0 aid=14)
[  165.800428] wlan6: associated
[  165.828812] cfg80211: Calling CRDA for country: US
[  165.840673] cfg80211: Received country IE:
[  165.840686] cfg80211: Regulatory domain: US
[  165.840693]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  165.840704]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[  165.840711] cfg80211: CRDA thinks this should applied:
[  165.840718] cfg80211: Regulatory domain: US
[  165.840724]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  165.840734]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  165.840744]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  165.840754]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  165.840763]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  165.840773]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  165.840783]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  165.840790] cfg80211: We intersect both of these and get:
[  165.840797] cfg80211: Regulatory domain: 98
[  165.840803]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  165.840813]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  165.840834] cfg80211: Current regulatory domain updated by AP to: US
[  165.840841]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  165.840852]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  211.617612] wlan6: deauthenticating from 00:0f:a3:1c:a1:f9 by local choice (reason=3)
[  211.689636] cfg80211: All devices are disconnected, going to restore regulatory settings
[  211.689651] cfg80211: Restoring regulatory settings
[  211.689661] cfg80211: Calling CRDA to update world regulatory domain
[  211.699762] cfg80211: World regulatory domain updated:
[  211.699771]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  211.699780]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  211.699786]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  211.699793]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  211.699800]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  211.699807]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  212.824799] wlan6: authenticate with 00:0f:a3:1c:a1:f9 (try 1)
[  212.826880] wlan6: authenticated
[  212.826958] wlan6: associate with 00:0f:a3:1c:a1:f9 (try 1)
[  212.829177] wlan6: RX AssocResp from 00:0f:a3:1c:a1:f9 (capab=0x411 status=0 aid=14)
[  212.829186] wlan6: associated
[  212.864632] cfg80211: Calling CRDA for country: US
[  212.873452] cfg80211: Received country IE:
[  212.873465] cfg80211: Regulatory domain: US
[  212.873471]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  212.873482]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[  212.873489] cfg80211: CRDA thinks this should applied:
[  212.873496] cfg80211: Regulatory domain: US
[  212.873542]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  212.873553]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  212.873562]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  212.873571]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  212.873580]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  212.873590]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  212.873599]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  212.873605] cfg80211: We intersect both of these and get:
[  212.873610] cfg80211: Regulatory domain: 98
[  212.873615]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  212.873625]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  212.873646] cfg80211: Current regulatory domain updated by AP to: US
[  212.873653]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  212.873662]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  258.616603] wlan6: deauthenticating from 00:0f:a3:1c:a1:f9 by local choice (reason=3)
[  258.672202] cfg80211: All devices are disconnected, going to restore regulatory settings
[  258.672218] cfg80211: Restoring regulatory settings
[  258.672229] cfg80211: Calling CRDA to update world regulatory domain
[  258.682371] cfg80211: World regulatory domain updated:
[  258.682380]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  258.682389]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  258.682395]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  258.682402]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  258.682409]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  258.682416]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```


and

```
Mar 25 18:56:42 artshow24 kernel: [    1.406927] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 18:56:42 artshow24 kernel: [    9.074844] udev[480]: renamed network interface eth0 to eth6
Mar 25 18:58:38 artshow24 kernel: [    1.390991] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 18:58:38 artshow24 kernel: [    8.966012] udev[389]: renamed network interface eth0 to eth6
Mar 25 19:00:09 artshow24 kernel: [    1.470060] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:00:09 artshow24 kernel: [    9.133571] udev[414]: renamed network interface eth0 to eth6
Mar 25 19:00:53 artshow24 kernel: [    1.453991] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:00:53 artshow24 kernel: [    9.026564] udev[410]: renamed network interface eth0 to eth6
Mar 25 19:01:57 artshow24 kernel: [    1.447947] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:01:57 artshow24 kernel: [    9.053557] udev[383]: renamed network interface eth0 to eth6
Mar 25 19:04:17 artshow24 kernel: [    1.394993] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:04:17 artshow24 kernel: [    9.087077] udev[404]: renamed network interface eth0 to eth6
Mar 25 19:05:28 artshow24 kernel: [    1.394989] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:05:28 artshow24 kernel: [    9.019185] udev[443]: renamed network interface eth0 to eth6
Mar 25 19:46:47 artshow24 kernel: [    1.419504] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:46:47 artshow24 kernel: [    9.141596] udev[420]: renamed network interface eth0 to eth6
Mar 25 19:51:49 artshow24 kernel: [    1.398025] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 19:51:49 artshow24 kernel: [    8.979102] udev[371]: renamed network interface eth0 to eth6
Mar 25 12:07:13 artshow24 kernel: [    1.362940] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:4e:9a
Mar 25 12:07:13 artshow24 kernel: [    9.334626] udev[381]: renamed network interface eth0 to eth4
Mar 25 20:13:44 artshow24 kernel: [    1.379158] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 20:13:44 artshow24 kernel: [    8.767067] udev[414]: renamed network interface eth0 to eth6
Mar 25 21:00:23 artshow24 kernel: [    1.362912] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
Mar 25 21:00:23 artshow24 kernel: [    8.823034] udev[384]: renamed network interface eth0 to eth6
```

which shows the renaming of eth0. 

Here's the result of 'lshw | grep product'

```
          product: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
          product: MCP79 Host Bridge
             product: MCP79 Memory Controller
             product: MCP79 LPC Bridge
             product: MCP79 Memory Controller
             product: MCP79 SMBus
             product: MCP79 Memory Controller
             product: MCP79 Co-processor
             product: MCP79 OHCI USB 1.1 Controller
             product: MCP79 EHCI USB 2.0 Controller
             product: MCP79 OHCI USB 1.1 Controller
             product: MCP79 EHCI USB 2.0 Controller
             product: MCP79 High Definition Audio
             product: MCP79 PCI Bridge
             product: MCP79 Ethernet
             product: MCP79 SATA Controller
             product: MCP79 PCI Express Bridge
             product: MCP79 PCI Express Bridge
                product: ION VGA
             product: MCP79 PCI Express Bridge
                product: AR9285 Wireless Network Adapter (PCI-Express)
             product: MCP79 PCI Express Bridge
             product: MCP79 PCI Express Bridge
             product: MCP79 PCI Express Bridge

```

I'm clearly hacking at things tying to nudge the system to take a fresh look at the networking hardware.

---

### Post by Clive McCarthy on 2011-03-25
My next investigation has been to edit 
[COLOR="Blue"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR]
and delete all the early entries, leaving just the _last_ two and then renaming the network devices to wlan0 and eth0.

This didn't work. I have compared the results from lshw with the entries in 70-persistent-net.rules and it seems that things line up. However it is possible I'm not interpreting the PCI addresses correctly.

[later] I gather now that they are MAC addresses so that the device names can be fixed to specific hardware. This is now really odd because the MAC addresses seem to match perfectly with what I find from '[COLOR="Green"]lshw | grep serial[/COLOR]'...

---

### Post by Cheesehead on 2011-03-25
You seem to be on the right track!
'ifconfig' can also give you the MAC addresses.

Classic udev renaming. I agree with you about fixing the name rules.
```

[    1.362912] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:31:1a:ad
[    8.823034] udev[384]: renamed network interface eth0 to eth6
[   14.039089] udev[386]: renamed network interface wlan0 to wlan6

```

You may be closer to success than you think...
```

[   25.468169] ADDRCONF(NETDEV_CHANGE): wlan6: link becomes ready

```
Your wireless was authenticating with the access point successfully.

Are you using Network Manager for these connections? Or /etc/networking/interfaces? Or something else? (if /etc/networking/interfaces, can you post it?)

After the system is running, what is the result of 'ifconfig'? Are the interfaces named correctly? If so, then it's just a normal job of configuring interfaces - you have resolved drivers and PCI addresses and udev properly.

Are any interfaces behaving properly? If not, what does 'ifconfig' reveal? If wireless is not behaving properly, what does 'iwconfig wlan0' reveal?

What happens if you try 'ifup wlan0' or 'ifup eth0'? Those error messages can also reveal much...

---

### Post by Clive McCarthy on 2011-03-25
I just ran [COLOR="Blue"]ifup eth0[/COLOR] and got:
[COLOR="blue"]Ignoring unknown interface eth0=eth0[/COLOR]
Seems like there is a definitional loop?

I'm going to double check the MAC addresses I get from ifconfig against those I have in the persistent-net.rules file. I gather that the rules file is auto generated by another set of rules. I wish I could just invoke whatever mechanism employs that.

---

### Post by Clive McCarthy on 2011-03-25
The MAC addresses all line up but neither wired nor wireless connect. :KS

I took a look at the failures in the syslog:

```
clive@artshow24:~$ less /var/log/syslog | grep fail
Mar 25 08:32:09 artshow24 kernel: [    0.873730] PM: Resume from disk failed.
Mar 25 08:32:10 artshow24 NetworkManager[871]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Mar 25 08:32:11 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:32:11 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:32:12 artshow24 gdm-session-worker[1209]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Mar 25 08:32:56 artshow24 NetworkManager[871]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Mar 25 08:32:56 artshow24 NetworkManager[871]: <warn> Activation (eth0) failed.
Mar 25 08:33:07 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:33:07 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:33:54 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:33:54 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:34:41 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:34:41 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:35:28 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 25 08:35:28 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
```

It doesn't mean anything to me. The NetworkManager is having a hard time with "supplicant_interface_acquire"  :confused:

---

### Post by Cheesehead on 2011-03-26
Hmmm. This looks like an incorrect kernel module (wrong driver) to me:
> 
Mar 25 08:32:10 artshow24 NetworkManager[871]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Mar 25 08:33:07 artshow24 NetworkManager[871]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed


The AR9285 (your wireless) has had problems in the past, most notably 9.10. It required the linux-backports-modules package, or an updated driver by another method, to fix. A quick search of the error tect can be most helpful...

Oh, congratulations! You are now officially a Linux internals expert.

---

### Post by Clive McCarthy on 2011-03-26
> **Cheesehead said:**
> Hmmm. This looks like an incorrect kernel module (wrong driver) to me:


The AR9285 (your wireless) has had problems in the past, most notably 9.10. It required the linux-backports-modules package, or an updated driver by another method, to fix. A quick search of the error tect can be most helpful...

Oh, congratulations! You are now officially a Linux internals expert.

The glory of being an "internals expert" is fading fast. What's an "error tect"? 

These new motherboards (there are two of them) are just *slight* variations on a series that I have been using for several months, without any trouble. The HDD clones all have 10.10 installed and I regularly swap the HDDs between motherboards, despite the fact that the MAC addresses will all be different.

I just booted one and ran [COLOR="Blue"]sudo lshw -C network[/COLOR] which shows that the AR9285 is the wlan hardware on all the boards. Further the network MAC address issue is solved because the board is using **eth3** and **wlan3** -- it seems that the system automatically assigns new names whenever it finds hardware with new MAC addresses. There is no need to update the udev rules manually.

Further, the fact that the MCP79 wired network won't play is a real puzzle. It is the same hardware as all the other boards. :confused:

I will play with this just a little longer and then give up, install 10.10 from a CD and redo all my custom settings.

---

### Post by Clive McCarthy on 2011-03-26
The plot thickens in two new ways:
[1] I took one of my other HDD clones and hooked it up and the machine connects to my network just fine.
[2] I booted trusted 10.10 installation CD and it shows NO network connection.

Forget WiFi I'm talking RJ45 hardware.

---

### Post by Cheesehead on 2011-03-26
That's wacky. Not what I expected at all.

---

### Post by Clive McCarthy on 2011-03-26
I have things working!:guitar:

It had _nothing_ to do with the new machines or the HDD cloning. Not the drivers either.

I restarted my WRT54GS router. I'm guessing that its DHCP leasing has a problem. Old leased ip addresses work but new leases fail. Or maybe Ubuntu tries the old ip address it finds...

The many machines on the network all continued to work just fine, many days in a row. So there has been no reason to suspect any issue with the DHCP leasing. The new machines have been begging for new addresses and are being denied...

Chessehead, thanks for your suggestions.

---

### Post by finndo on 2011-10-06
just wanted to post that I have been working with an extremely similar issue and followed MANY threads both here at Ubuntu forums and on other sites.  one thing you failed to mention (a detail) was that when you booted into recovery and ran dpkg the system connected to the internet and downloaded updates!  yet the OS when run normally could not connect. (at this time my system is still reinstalling/repairing/upgrading packages from running dpkg in recovery)

I had to replace my MB because of a bad BIOS chip and out of warranty MB, I had recently switched from Ubuntu 10.10 back to windows 7 after running Linux exclusively for 8 months +/-2 on all machines in my home, due to several issues:

1. dragon naturally speaking not running in wine and crashing my entire system when run in a virtual machine (not all the time, it works most of the time, but there is some call it makes that causes the host to lock up, not to mention inability to use it on any applications on the host!
2. I bought a new digital camera and the raw format is only readable by the company's photo editing windows only app and photoshop CS5.
3. I have a CR-48 google chrome book beta system that I gave to my wife, well in order to print she has to use google cloud print, which only runs on chrome on a windows system
4. Last reason, my Xbox 360 refuses to allow access to more than 100 folders or 100 files from any folder when connecting to a linux host. (not really a deciding factor in switching, but was an issue resolved when I switched)

on to the problem again!  I bought a new MB... moved from an AMD790GXM chipset to an AMD 990FXA, a phen 2 x4 955 to a phen 2 x6 1090t, and from an ATI 4890 to an AMD 6850.  Windows 7 would not boot (old HDD not modified for the new hardware), just sat on the windows logo, pulsating.  I tried 6 times, let it sit over night, it did reboot itself twice the first time I booted it up.  I did try a repair, no go.  which is strange, as I moved a windows vista HDD to another computer and 8 reboots later and re-verifying my COA, it was all working (nothing other than the HDD was the same internally).

so I put what I thought was a blank old 250GB HDD in to install a clean version of windows and missed the "press any key to boot from CD" and up popped my old Ubuntu 10.10 desktop happy and running.  This sounded great to me, as Windows sucks.  So I started messing around and found out that while my NIC had an IP from my router, I could not ping the gateway... my router... which assigned my NIC an IP... "destination host unreachable"

I have tried lots and lots of things suggested, including downloading and installing the driver form the chipset vendor, and even booted into recovery mode, but did not run the dpkg option.  after reading this post and running dpkg the Network adapter is working fine.  Just wanted to say thank you.

---

