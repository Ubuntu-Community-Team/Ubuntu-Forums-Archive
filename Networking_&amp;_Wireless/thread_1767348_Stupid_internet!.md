---
title: "Stupid internet!"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by jakejw93 on 2011-05-25
So i have made a couple of threads in the past couple of weeks about internet problems with no reply..

So because my internet was playing up a lot on 11.04 i reverted back to 10.10 in the hope that would work - by the way it never ¬_¬

I've set my MTU to 1492 and also turned ipv6 off, please help anyone!!?!

BTW internet runs perfect on my windows 7 partition..

---

### Post by novinick on 2011-05-25
these threads?
 11.04 wired problem [http://ubuntuforums.org/showthread.php?t=1755660](http://ubuntuforums.org/showthread.php?t=1755660) 
Internet problems [http://ubuntuforums.org/showthread.php?t=1753208](http://ubuntuforums.org/showthread.php?t=1753208)  

first , on previous old and crappy computer, was it functional , this internet?

 second , what type of internet do you have , cable , uk adsl or somesort of wireles access ?

---

### Post by novinick on 2011-05-25
can you post output of commands


```
lspci -knn
ifconfig -a
route -n
```and this one is big
```
dmesg
```

---

### Post by jakejw93 on 2011-05-25
> **novinick said:**
> these threads?
 11.04 wired problem [http://ubuntuforums.org/showthread.php?t=1755660](http://ubuntuforums.org/showthread.php?t=1755660) 
Internet problems [http://ubuntuforums.org/showthread.php?t=1753208](http://ubuntuforums.org/showthread.php?t=1753208)  

first , on previous old and crappy computer, was it functional , this internet?

 second , what type of internet do you have , cable , uk adsl or somesort of wireles access ?

Those are the threads yes!
And nope, i recall it being perfectly normal..and also when I updated hardware it worked OKAY for a bit, then it started playin up...and i use Cable as well



> **novinick said:**
> can you post output of commands


```
lspci -knn
ifconfig -a
route -n
```and this one is big
```
dmesg
```

jakeward@jakejw93:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0100] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8445]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c5c] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel modules: iTCO_wdt
00:1f.2 IDE interface [0101]: Intel Corporation Cougar Point 4 port SATA IDE Controller [8086:1c00] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation Cougar Point 2 port SATA IDE Controller [8086:1c08] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
    Kernel driver in use: ata_piix
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8432]
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 PCI bridge [0604]: Device [1b21:1080] (rev 01)


jakeward@jakejw93:~$ ipconfig -a
No command 'ipconfig' found, did you mean:
 Command 'tpconfig' from package 'tpconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found

What the hell???

jakeward@jakejw93:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-29-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #51-Ubuntu SMP Fri Apr 15 18:57:47 UTC 2011 (Ubuntu 2.6.35-29.51-generic-pae 2.6.35.12)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf53d000 (usable)
[    0.000000]  BIOS-e820: 00000000bf53d000 - 00000000bf58f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf58f000 - 00000000bf5af000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5af000 - 00000000bf5c0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5c0000 - 00000000bf5d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5d4000 - 00000000bf5d6000 (usable)
[    0.000000]  BIOS-e820: 00000000bf5d6000 - 00000000bf5d7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf5d7000 - 00000000bf5df000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5df000 - 00000000bf5e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5e9000 - 00000000bf642000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf642000 - 00000000bf685000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf685000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x13f800 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 13F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf53d000 (usable)
[    0.000000]  modified: 00000000bf53d000 - 00000000bf58f000 (ACPI NVS)
[    0.000000]  modified: 00000000bf58f000 - 00000000bf5af000 (reserved)
[    0.000000]  modified: 00000000bf5af000 - 00000000bf5c0000 (ACPI NVS)
[    0.000000]  modified: 00000000bf5c0000 - 00000000bf5d4000 (reserved)
[    0.000000]  modified: 00000000bf5d4000 - 00000000bf5d6000 (usable)
[    0.000000]  modified: 00000000bf5d6000 - 00000000bf5d7000 (ACPI data)
[    0.000000]  modified: 00000000bf5d7000 - 00000000bf5df000 (reserved)
[    0.000000]  modified: 00000000bf5df000 - 00000000bf5e9000 (ACPI NVS)
[    0.000000]  modified: 00000000bf5e9000 - 00000000bf642000 (reserved)
[    0.000000]  modified: 00000000bf642000 - 00000000bf685000 (ACPI NVS)
[    0.000000]  modified: 00000000bf685000 - 00000000bf800000 (usable)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000013f800000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00fcdc0] fcdc0
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 375b3000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a08000 - 01444fa6
[    0.000000] Move RAMDISK from 00000000375b3000 - 0000000037feffa5 to 00a08000 - 01444fa5
[    0.000000] ACPI: RSDP 000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT bf587068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP bf58ea28 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT bf587140 078E5 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS bf5e0f80 00040
[    0.000000] ACPI: APIC bf58eb20 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT bf58eb98 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG bf58eca0 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET bf58ece0 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4220MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0013f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf53d
[    0.000000]     0: 0x000bf5d4 -> 0x000bf5d6
[    0.000000]     0: 0x000bf685 -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x0013f800
[    0.000000] On node 0 totalpages: 1044040
[    0.000000] free_area_init_node: node 0, pgdat c0842d00, node_mem_map c1446200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8441 pages used for memmap
[    0.000000]   HighMem zone: 807363 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bf800000 (gap: bf800000:3f51c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3e00000 s39872 r0 d21568 u524288
[    0.000000] pcpu-alloc: s39872 r0 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1033815
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=e8c5b799-dfab-4d66-b569-675376afea1b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 26173120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (60 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009ff65c]   TEXT DATA BSS
[    0.000000]   #3 [0000a00000 - 0000a07206]             BRK
[    0.000000]   #4 [00000fcdd0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fcdc0 - 00000fcdd0]    MP-table mpf
[    0.000000]   #6 [000009ec00 - 00000fca90]   BIOS reserved
[    0.000000]   #7 [00000fcd44 - 00000fcdc0]   BIOS reserved
[    0.000000]   #8 [00000fca90 - 00000fcd44]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [0000a08000 - 0001445000]     NEW RAMDISK
[    0.000000]   #13 [0001445000 - 0001446000]         BOOTMEM
[    0.000000]   #14 [0001446000 - 0003c36000]         BOOTMEM
[    0.000000]   #15 [0003c36000 - 0003c36004]         BOOTMEM
[    0.000000]   #16 [0003c36040 - 0003c36100]         BOOTMEM
[    0.000000]   #17 [0003c36100 - 0003c361a8]         BOOTMEM
[    0.000000]   #18 [0003c361c0 - 0003c391c0]         BOOTMEM
[    0.000000]   #19 [0003c391c0 - 0003c394d8]         BOOTMEM
[    0.000000]   #20 [0003c39500 - 0003c45500]         BOOTMEM
[    0.000000]   #21 [0003c45500 - 0003c4552d]         BOOTMEM
[    0.000000]   #22 [0003c45540 - 0003c4556f]         BOOTMEM
[    0.000000]   #23 [0003c45580 - 0003c4582c]         BOOTMEM
[    0.000000]   #24 [0003c45840 - 0003c45880]         BOOTMEM
[    0.000000]   #25 [0003c45880 - 0003c458c0]         BOOTMEM
[    0.000000]   #26 [0003c458c0 - 0003c45900]         BOOTMEM
[    0.000000]   #27 [0003c45900 - 0003c45940]         BOOTMEM
[    0.000000]   #28 [0003c45940 - 0003c45980]         BOOTMEM
[    0.000000]   #29 [0003c45980 - 0003c459c0]         BOOTMEM
[    0.000000]   #30 [0003c459c0 - 0003c45a00]         BOOTMEM
[    0.000000]   #31 [0003c45a00 - 0003c45a40]         BOOTMEM
[    0.000000]   #32 [0003c45a40 - 0003c45a80]         BOOTMEM
[    0.000000]   #33 [0003c45a80 - 0003c45ac0]         BOOTMEM
[    0.000000]   #34 [0003c45ac0 - 0003c45b00]         BOOTMEM
[    0.000000]   #35 [0003c45b00 - 0003c45b40]         BOOTMEM
[    0.000000]   #36 [0003c45b40 - 0003c45b80]         BOOTMEM
[    0.000000]   #37 [0003c45b80 - 0003c45bc0]         BOOTMEM
[    0.000000]   #38 [0003c45bc0 - 0003c45c00]         BOOTMEM
[    0.000000]   #39 [0003c45c00 - 0003c45c40]         BOOTMEM
[    0.000000]   #40 [0003c45c40 - 0003c45c80]         BOOTMEM
[    0.000000]   #41 [0003c45c80 - 0003c45cc0]         BOOTMEM
[    0.000000]   #42 [0003c45cc0 - 0003c45cd0]         BOOTMEM
[    0.000000]   #43 [0003c45d00 - 0003c45d6e]         BOOTMEM
[    0.000000]   #44 [0003c45d80 - 0003c45dee]         BOOTMEM
[    0.000000]   #45 [0003e00000 - 0003e0f000]         BOOTMEM
[    0.000000]   #46 [0003e80000 - 0003e8f000]         BOOTMEM
[    0.000000]   #47 [0003f00000 - 0003f0f000]         BOOTMEM
[    0.000000]   #48 [0003f80000 - 0003f8f000]         BOOTMEM
[    0.000000]   #49 [0003c47e00 - 0003c47e04]         BOOTMEM
[    0.000000]   #50 [0003c47e40 - 0003c47e44]         BOOTMEM
[    0.000000]   #51 [0003c47e80 - 0003c47e90]         BOOTMEM
[    0.000000]   #52 [0003c47ec0 - 0003c47ed0]         BOOTMEM
[    0.000000]   #53 [0003c47f00 - 0003c47f98]         BOOTMEM
[    0.000000]   #54 [0003c47fc0 - 0003c47ff8]         BOOTMEM
[    0.000000]   #55 [0003c48000 - 0003c4c000]         BOOTMEM
[    0.000000]   #56 [0003c4c000 - 0003ccc000]         BOOTMEM
[    0.000000]   #57 [0003ccc000 - 0003d0c000]         BOOTMEM
[    0.000000]   #58 [0003c45e00 - 0003c46140]         BOOTMEM
[    0.000000]   #59 [0003f8f000 - 0005884ec0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0013f800)
[    0.000000] Memory: 4088848k/5234688k available (5097k kernel code, 87312k reserved, 2437k data, 708k init, 3263216k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085c000 - 0xc090d000   ( 708 kB)
[    0.000000]       .data : 0xc05fa46a - 0xc085b948   (2437 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05fa46a   (5097 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3291.723 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6583.44 BogoMIPS (lpj=13166892)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000016] Security Framework initialized
[    0.000025] AppArmor: AppArmor initialized
[    0.000026] Yama: becoming mindful.
[    0.000056] Mount-cache hash table entries: 512
[    0.000120] Initializing cgroup subsys ns
[    0.000122] Initializing cgroup subsys cpuacct
[    0.000125] Initializing cgroup subsys memory
[    0.000129] Initializing cgroup subsys devices
[    0.000130] Initializing cgroup subsys freezer
[    0.000132] Initializing cgroup subsys net_cls
[    0.000148] CPU: Physical Processor ID: 0
[    0.000149] CPU: Processor Core ID: 0
[    0.000152] mce: CPU supports 9 MCE banks
[    0.000162] CPU0: Thermal monitoring enabled (TM1)
[    0.000168] using mwait in idle threads.
[    0.000171] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.000175] ... version:                3
[    0.000176] ... bit width:              48
[    0.000177] ... generic registers:      8
[    0.000178] ... value mask:             0000ffffffffffff
[    0.000179] ... max period:             000000007fffffff
[    0.000180] ... fixed-purpose events:   3
[    0.000181] ... event mask:             00000007000000ff
[    0.002250] ACPI: Core revision 20100428
[    0.007421] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.007423] ftrace: allocating 22410 entries in 44 pages
[    0.013580] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.013913] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.053585] CPU0: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz stepping 07
[    0.160402] Booting Node   0, Processors  #1
[    0.170756] Initializing CPU#1
[    0.268469]  #2
[    0.278686] Initializing CPU#2
[    0.376436]  #3 Ok.
[    0.386653] Initializing CPU#3
[    0.484363] Brought up 4 CPUs
[    0.484364] Total of 4 processors activated (26332.88 BogoMIPS).
[    0.485696] devtmpfs: initialized
[    0.486400] regulator: core version 0.5
[    0.486423] Time: 20:12:30  Date: 05/25/11
[    0.486444] NET: Registered protocol family 16
[    0.486498] Trying to unpack rootfs image as initramfs...
[    0.486502] EISA bus registered
[    0.486507] ACPI: bus type pci registered
[    0.486549] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.486551] PCI: not using MMCONFIG
[    0.498955] PCI: Using configuration type 1 for base access
[    0.499450] bio: create slab <bio-0> at 0
[    0.500287] ACPI: EC: Look up EC in DSDT
[    0.501265] ACPI: Executed 1 blocks of module-level executable AML code
[    0.503660] ACPI Error (psargs-0359): [RAMB] Namespace lookup failure, AE_NOT_FOUND
[    0.503664] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20100428/nsinit-349)
[    0.505196] ACPI: SSDT bf5dfc18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.505454] ACPI: Dynamic OEM Table Load:
[    0.505456] ACPI: SSDT (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.505492] ACPI: SSDT bf5e0e18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.505706] ACPI: Dynamic OEM Table Load:
[    0.505708] ACPI: SSDT (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.506396] ACPI: Interpreter enabled
[    0.506399] ACPI: (supports S0 S1 S3 S4 S5)
[    0.506414] ACPI: Using IOAPIC for interrupt routing
[    0.506447] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.506532] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.506534] PCI: Using MMCONFIG for extended config space
[    0.506729] ACPI: BIOS _OSI(Linux) query ignored
[    0.511319] ACPI: No dock devices found.
[    0.511322] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.511565] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.511840] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.511842] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.511843] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.511845] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c8000-0x000dffff] conflicts with Video ROM [mem 0x000c0000-0x000ccbff]
[    0.511847] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.511893] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.511895] pci 0000:00:01.0: PME# disabled
[    0.511950] pci 0000:00:16.0: reg 10: [mem 0xfb107000-0xfb10700f 64bit]
[    0.511992] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.511995] pci 0000:00:16.0: PME# disabled
[    0.512039] pci 0000:00:1a.0: reg 10: [mem 0xfb106000-0xfb1063ff]
[    0.512090] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.512093] pci 0000:00:1a.0: PME# disabled
[    0.512124] pci 0000:00:1b.0: reg 10: [mem 0xfb100000-0xfb103fff 64bit]
[    0.512162] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.512165] pci 0000:00:1b.0: PME# disabled
[    0.512233] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.512236] pci 0000:00:1c.0: PME# disabled
[    0.512308] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.512310] pci 0000:00:1c.1: PME# disabled
[    0.512379] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.512382] pci 0000:00:1c.2: PME# disabled
[    0.512450] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.512453] pci 0000:00:1c.3: PME# disabled
[    0.512521] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.512524] pci 0000:00:1c.4: PME# disabled
[    0.512592] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.512595] pci 0000:00:1c.5: PME# disabled
[    0.512637] pci 0000:00:1d.0: reg 10: [mem 0xfb105000-0xfb1053ff]
[    0.512688] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.512691] pci 0000:00:1d.0: PME# disabled
[    0.512800] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    0.512804] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    0.512809] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    0.512813] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    0.512817] pci 0000:00:1f.2: reg 20: [io  0xf090-0xf09f]
[    0.512822] pci 0000:00:1f.2: reg 24: [io  0xf080-0xf08f]
[    0.512861] pci 0000:00:1f.3: reg 10: [mem 0xfb104000-0xfb1040ff 64bit]
[    0.512873] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.512906] pci 0000:00:1f.5: reg 10: [io  0xf070-0xf077]
[    0.512910] pci 0000:00:1f.5: reg 14: [io  0xf060-0xf063]
[    0.512914] pci 0000:00:1f.5: reg 18: [io  0xf050-0xf057]
[    0.512919] pci 0000:00:1f.5: reg 1c: [io  0xf040-0xf043]
[    0.512923] pci 0000:00:1f.5: reg 20: [io  0xf030-0xf03f]
[    0.512928] pci 0000:00:1f.5: reg 24: [io  0xf020-0xf02f]
[    0.512982] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.512989] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.512996] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.513000] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.513004] pci 0000:01:00.0: reg 30: [mem 0xfb000000-0xfb01ffff pref]
[    0.520235] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.520237] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.520239] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfb0fffff]
[    0.520242] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.520284] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.520287] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.520290] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.520295] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.520337] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.520340] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.520343] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.520348] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.520421] pci 0000:04:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.520443] pci 0000:04:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.520459] pci 0000:04:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.520511] pci 0000:04:00.0: supports D1 D2
[    0.520512] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520517] pci 0000:04:00.0: PME# disabled
[    0.528240] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.528244] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.528247] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528252] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.528294] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.528298] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528301] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528306] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528445] pci 0000:00:1c.4: PCI bridge to [bus 06-07] (subtractive decode)
[    0.528448] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528451] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528457] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528458] pci 0000:00:1c.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.528459] pci 0000:00:1c.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.528461] pci 0000:00:1c.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.528462] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.528574] pci 0000:06:00.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.528583] pci 0000:06:00.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.528588] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528597] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528599] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528600] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528602] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528603] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528604] pci 0000:06:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.528606] pci 0000:06:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.528607] pci 0000:06:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.528608] pci 0000:06:00.0:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.528661] pci 0000:00:1c.5: PCI bridge to [bus 08-08]
[    0.528664] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528667] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528672] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528700] pci_bus 0000:00: on NUMA node 0
[    0.528703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.528814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.528852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.528887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.528922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.528964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4.BR16._PRT]
[    0.532141] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532206] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532276] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.532339] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.532403] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.532466] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.532529] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.532593] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.532621] HEST: Table is not found!
[    0.532665] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.532667] vgaarb: loaded
[    0.532748] SCSI subsystem initialized
[    0.532809] libata version 3.00 loaded.
[    0.532835] usbcore: registered new interface driver usbfs
[    0.532841] usbcore: registered new interface driver hub
[    0.532854] usbcore: registered new device driver usb
[    0.532969] ACPI: WMI: Mapper loaded
[    0.532970] PCI: Using ACPI for IRQ routing
[    0.532972] PCI: pci_cache_line_size set to 64 bytes
[    0.533030] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.533031] reserve RAM buffer: 00000000bf53d000 - 00000000bfffffff 
[    0.533034] reserve RAM buffer: 00000000bf5d6000 - 00000000bfffffff 
[    0.533036] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.533037] reserve RAM buffer: 000000013f800000 - 000000013fffffff 
[    0.533087] NetLabel: Initializing
[    0.533088] NetLabel:  domain hash size = 128
[    0.533088] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.533095] NetLabel:  unlabeled traffic allowed by default
[    0.533116] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.533120] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.535132] Switching to clocksource tsc
[    0.540757] AppArmor: AppArmor Filesystem Enabled
[    0.540765] pnp: PnP ACPI init
[    0.540775] ACPI: bus type pnp registered
[    0.542738] pnp: PnP ACPI: found 13 devices
[    0.542740] ACPI: ACPI bus type pnp unregistered
[    0.542742] PnPBIOS: Disabled by ACPI PNP
[    0.542748] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.542750] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.542752] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.542753] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.542755] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.542758] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.542762] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.542765] system 00:0a: [io  0x0400-0x0453] has been reserved
[    0.542766] system 00:0a: [io  0x0458-0x047f] has been reserved
[    0.542768] system 00:0a: [io  0x0500-0x057f] has been reserved
[    0.542769] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.542771] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.542773] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.542774] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.542778] system 00:0b: [io  0x0454-0x0457] has been reserved
[    0.578031] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.578034] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.578036] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfb0fffff]
[    0.578038] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.578041] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.578042] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.578046] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.578048] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.578054] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.578054] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.578058] pci 0000:00:1c.1:   bridge window [mem disabled]
[    0.578061] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.578066] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.578068] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.578072] pci 0000:00:1c.2:   bridge window [mem disabled]
[    0.578076] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.578081] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.578082] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.578086] pci 0000:00:1c.3:   bridge window [mem disabled]
[    0.578089] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.578094] pci 0000:06:00.0: PCI bridge to [bus 07-07]
[    0.578095] pci 0000:06:00.0:   bridge window [io  disabled]
[    0.578101] pci 0000:06:00.0:   bridge window [mem disabled]
[    0.578106] pci 0000:06:00.0:   bridge window [mem pref disabled]
[    0.578115] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.578116] pci 0000:00:1c.4:   bridge window [io  disabled]
[    0.578120] pci 0000:00:1c.4:   bridge window [mem disabled]
[    0.578123] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.578128] pci 0000:00:1c.5: PCI bridge to [bus 08-08]
[    0.578129] pci 0000:00:1c.5:   bridge window [io  disabled]
[    0.578133] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.578136] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    0.578147]   alloc irq_desc for 16 on node -1
[    0.578148]   alloc kstat_irqs on node -1
[    0.578152] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.578154] pci 0000:00:01.0: setting latency timer to 64
[    0.578160]   alloc irq_desc for 17 on node -1
[    0.578161]   alloc kstat_irqs on node -1
[    0.578163] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578166] pci 0000:00:1c.0: setting latency timer to 64
[    0.578173] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.578176] pci 0000:00:1c.1: setting latency timer to 64
[    0.578183]   alloc irq_desc for 18 on node -1
[    0.578184]   alloc kstat_irqs on node -1
[    0.578186] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.578189] pci 0000:00:1c.2: setting latency timer to 64
[    0.578196]   alloc irq_desc for 19 on node -1
[    0.578197]   alloc kstat_irqs on node -1
[    0.578198] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.578201] pci 0000:00:1c.3: setting latency timer to 64
[    0.578208] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578211] pci 0000:00:1c.4: setting latency timer to 64
[    0.578217] pci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578222] pci 0000:06:00.0: setting latency timer to 64
[    0.578229] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.578232] pci 0000:00:1c.5: setting latency timer to 64
[    0.578235] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.578237] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.578238] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.578239] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.578241] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.578242] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfb0fffff]
[    0.578243] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.578245] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.578246] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.578247] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.578249] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.578250] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.578251] pci_bus 0000:06: resource 7 [mem 0xc0000000-0xffffffff]
[    0.578252] pci_bus 0000:07: resource 8 [io  0x0000-0x0cf7]
[    0.578254] pci_bus 0000:07: resource 9 [io  0x0d00-0xffff]
[    0.578255] pci_bus 0000:07: resource 10 [mem 0x000a0000-0x000bffff]
[    0.578256] pci_bus 0000:07: resource 11 [mem 0xc0000000-0xffffffff]
[    0.578279] NET: Registered protocol family 2
[    0.578310] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.578411] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.578612] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.578713] TCP: Hash tables configured (established 131072 bind 65536)
[    0.578715] TCP reno registered
[    0.578716] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.578720] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.578759] NET: Registered protocol family 1
[    0.832154] pci 0000:01:00.0: Boot video device
[    0.832162] PCI: CLS 64 bytes, default 64
[    0.832340] cpufreq-nforce2: No nForce2 chipset.
[    0.832355] Scanning for low memory corruption every 60 seconds
[    0.832415] audit: initializing netlink socket (disabled)
[    0.832422] type=2000 audit(1306354350.676:1): initialized
[    0.838548] highmem bounce pool size: 64 pages
[    0.838551] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.839281] VFS: Disk quotas dquot_6.5.2
[    0.839312] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.839609] fuse init (API version 7.14)
[    0.839654] msgmni has been set to 1612
[    0.861832] Freeing initrd memory: 10484k freed
[    0.864363] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.864365] io scheduler noop registered
[    0.864366] io scheduler deadline registered
[    0.864372] io scheduler cfq registered (default)
[    0.864431] pcieport 0000:00:01.0: setting latency timer to 64
[    0.864446]   alloc irq_desc for 40 on node -1
[    0.864447]   alloc kstat_irqs on node -1
[    0.864452] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.864490] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.864521]   alloc irq_desc for 41 on node -1
[    0.864522]   alloc kstat_irqs on node -1
[    0.864527] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.864580] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.864611]   alloc irq_desc for 42 on node -1
[    0.864612]   alloc kstat_irqs on node -1
[    0.864617] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.864669] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.864699]   alloc irq_desc for 43 on node -1
[    0.864700]   alloc kstat_irqs on node -1
[    0.864706] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.864757] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.864788]   alloc irq_desc for 44 on node -1
[    0.864788]   alloc kstat_irqs on node -1
[    0.864794] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.864846] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.864876]   alloc irq_desc for 45 on node -1
[    0.864877]   alloc kstat_irqs on node -1
[    0.864883] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    0.864940] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.864952] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.865003] intel_idle: MWAIT substates: 0x1120
[    0.865004] intel_idle: v0.4 model 0x2A
[    0.865005] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.865072] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.865075] ACPI: Power Button [PWRB]
[    0.865100] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.865102] ACPI: Power Button [PWRF]
[    0.865268] ACPI: acpi_idle yielding to intel_idle
[    0.866962] ERST: Table is not found!
[    0.866973] isapnp: Scanning for PnP cards...
[    0.867090] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.867185] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.867473] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.868077] brd: module loaded
[    0.868350] loop: module loaded
[    0.868452] ata_piix 0000:00:1f.2: version 2.13
[    0.868462]   alloc irq_desc for 20 on node -1
[    0.868463]   alloc kstat_irqs on node -1
[    0.868467] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.868470] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.024197] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
[    1.024203] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.024240] scsi0 : ata_piix
[    1.024279] scsi1 : ata_piix
[    1.025078] ata1: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 20
[    1.025080] ata2: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 20
[    1.025092] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.025095] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.025122] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.025149] scsi2 : ata_piix
[    1.025181] scsi3 : ata_piix
[    1.026096] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 20
[    1.026099] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 20
[    1.026265] Fixed MDIO Bus: probed
[    1.026282] PPP generic driver version 2.4.2
[    1.026302] tun: Universal TUN/TAP device driver, 1.6
[    1.026303] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.026346] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.026356]   alloc irq_desc for 23 on node -1
[    1.026357]   alloc kstat_irqs on node -1
[    1.026360] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.026368] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.026370] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.026389] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.026410] ehci_hcd 0000:00:1a.0: debug port 2
[    1.030290] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.030300] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfb106000
[    1.044061] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.044128] hub 1-0:1.0: USB hub found
[    1.044131] hub 1-0:1.0: 2 ports detected
[    1.044166] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.044172] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.044175] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.044190] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.044209] ehci_hcd 0000:00:1d.0: debug port 2
[    1.048077] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.048080] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfb105000
[    1.060056] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.060112] hub 2-0:1.0: USB hub found
[    1.060114] hub 2-0:1.0: 2 ports detected
[    1.060146] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.060152] uhci_hcd: USB Universal Host Controller Interface driver
[    1.060201] PNP: No PS/2 controller found. Probing ports directly.
[    1.062782] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.062785] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.062823] mice: PS/2 mouse device common for all mice
[    1.062880] rtc_cmos 00:05: RTC can wake from S4
[    1.062897] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.062921] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.062971] device-mapper: uevent: version 1.0.3
[    1.063027] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.063078] device-mapper: multipath: version 1.1.1 loaded
[    1.063079] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.063134] EISA: Probing bus 0 at eisa.0
[    1.063135] EISA: Cannot allocate resource for mainboard
[    1.063136] Cannot allocate resource for EISA slot 1
[    1.063137] Cannot allocate resource for EISA slot 2
[    1.063138] Cannot allocate resource for EISA slot 3
[    1.063139] Cannot allocate resource for EISA slot 4
[    1.063140] Cannot allocate resource for EISA slot 5
[    1.063141] Cannot allocate resource for EISA slot 6
[    1.063142] Cannot allocate resource for EISA slot 7
[    1.063143] Cannot allocate resource for EISA slot 8
[    1.063144] EISA: Detected 0 cards.
[    1.063276] cpuidle: using governor ladder
[    1.063376] cpuidle: using governor menu
[    1.063512] TCP cubic registered
[    1.063577] NET: Registered protocol family 10
[    1.063741] lo: Disabled Privacy Extensions
[    1.063837] NET: Registered protocol family 17
[    1.064399] Using IPI No-Shortcut mode
[    1.064434] PM: Resume from disk failed.
[    1.064440] registered taskstats version 1
[    1.064660]   Magic number: 11:163:246
[    1.064704] rtc_cmos 00:05: setting system clock to 2011-05-25 20:12:31 UTC (1306354351)
[    1.064705] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.064706] EDD information not available.
[    1.221077] isapnp: No Plug & Play device found
[    1.368084] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.388125] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.388285] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.391448] ata4.00: ATA-7: MAXTOR STM3250310AS, 4.AAA, max UDMA/133
[    1.391451] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.391559] ata3.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    1.391561] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.407430] ata4.00: configured for UDMA/133
[    1.407567] ata3.00: configured for UDMA/133
[    1.407744] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    1.407828] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.407857] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.407910] sd 2:0:0:0: [sda] Write Protect is off
[    1.407911] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.407928] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408021] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR STM325031 4.AA PQ: 0 ANSI: 5
[    1.408032]  sda:
[    1.408112] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.408188] sd 3:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.408377] sd 3:0:0:0: [sdb] Write Protect is off
[    1.408379] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.408448] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408691]  sdb: sda1 sda2 sda3 sda4 < sdb1
[    1.418239] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.433455]  sda5 >
[    1.433674] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.433752] Freeing unused kernel memory: 708k freed
[    1.433941] Write protecting the kernel text: 5100k
[    1.434059] Write protecting the kernel read-only data: 2016k
[    1.443857] udev[106]: starting version 163
[    1.456942] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.456959] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.456997] r8169 0000:04:00.0: setting latency timer to 64
[    1.457004] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
[    1.457073]   alloc irq_desc for 46 on node -1
[    1.457074]   alloc kstat_irqs on node -1
[    1.457086] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
[    1.457345] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xf8466000, f4:6d:04:04:d6:4d, XID 0c900800 IRQ 46
[    1.460018] hub 1-1:1.0: USB hub found
[    1.460111] hub 1-1:1.0: 4 ports detected
[    1.575012] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.703446] hub 2-1:1.0: USB hub found
[    1.703545] hub 2-1:1.0: 6 ports detected
[    1.775242] usb 1-1.3: new high speed USB device using ehci_hcd and address 3
[    1.787968] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.787970] EXT4-fs (sda1): write access will be enabled during recovery
[    1.879481] Initializing USB Mass Storage driver...
[    1.879615] scsi4 : usb-storage 1-1.3:1.0
[    1.879692] usbcore: registered new interface driver usb-storage
[    1.879693] USB Mass Storage support registered.
[    1.975009] usb 2-1.1: new low speed USB device using ehci_hcd and address 3
[    2.096068] usbcore: registered new interface driver hiddev
[    2.104380] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    2.104472] generic-usb 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1/input0
[    2.104480] usbcore: registered new interface driver usbhid
[    2.104481] usbhid: USB HID core driver
[    2.158955] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
[    2.253754] scsi5 : usb-storage 2-1.2:1.0
[    2.324667] usb 2-1.3: new low speed USB device using ehci_hcd and address 5
[    2.421358] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
[    2.421405] generic-usb 0003:192F:0616.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.3/input0
[    2.880472] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF RW 0814 PQ: 0 ANSI: 0
[    2.881609] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader Combo 0814 PQ: 0 ANSI: 0
[    2.882311] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.882410] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    2.886223] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    2.887648] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    3.252866] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS0C PQ: 0 ANSI: 0
[    3.255982] sr0: scsi3-mmc drive: 47x/125x writer cd/rw xa/form2 cdda tray
[    3.255984] Uniform CD-ROM driver Revision: 3.20
[    3.256064] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.256110] sr 5:0:0:0: Attached scsi generic sg4 type 5
[    4.751192] EXT4-fs (sda1): recovery complete
[    4.751824] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   14.488477] Adding 4174844k swap on /dev/sda5.  Priority:-1 extents:1 across:4174844k 
[   14.557397] udev[401]: starting version 163
[   14.562927] lp: driver loaded but no devices found
[   14.582692] Linux agpgart interface v0.103
[   14.615086] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input4
[   14.627790] nvidia: module license 'NVIDIA' taints kernel.
[   14.627792] Disabling lock debugging due to kernel taint
[   14.639197] parport_pc 00:03: reported by Plug and Play ACPI
[   14.639245] parport0: PC-style at 0x378, irq 5 [PCSPP]
[   14.649039] ppdev: user-space parallel port driver
[   14.677806]   alloc irq_desc for 22 on node -1
[   14.677808]   alloc kstat_irqs on node -1
[   14.677812] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.677842]   alloc irq_desc for 47 on node -1
[   14.677843]   alloc kstat_irqs on node -1
[   14.677850] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   14.677868] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.724455] hda_codec: ALC887-VD: BIOS auto-probing.
[   14.728806] Too many connections
[   14.735558] lp0: using parport0 (interrupt-driven).
[   14.973638] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.973644] nvidia 0000:01:00.0: setting latency timer to 64
[   14.973647] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.973712] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   14.993823] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.994696] type=1400 audit(1306350765.430:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=626 comm="apparmor_parser"
[   14.994703] type=1400 audit(1306350765.430:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=695 comm="apparmor_parser"
[   14.995079] type=1400 audit(1306350765.430:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"
[   14.995087] type=1400 audit(1306350765.430:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[   14.995304] type=1400 audit(1306350765.430:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"
[   14.995314] type=1400 audit(1306350765.430:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[   15.086760] type=1400 audit(1306350765.522:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=870 comm="apparmor_parser"
[   15.086859] type=1400 audit(1306350765.522:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=871 comm="apparmor_parser"
[   15.087243] type=1400 audit(1306350765.522:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=871 comm="apparmor_parser"
[   15.087535] type=1400 audit(1306350765.526:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=871 comm="apparmor_parser"
[   16.304064] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   19.954525] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.227242] ISO 9660 Extensions: Microsoft Joliet Level 3
[   24.255365] ISOFS: changing to secondary root
[   33.222574] r8169 0000:04:00.0: eth0: link up
[   33.222608] r8169 0000:04:00.0: eth0: link up
[   34.240671] r8169: WARNING! Changing of MTU on this NIC may lead to frame reception errors!
[   71.962573] r8169 0000:04:00.0: eth0: link up
[   80.476040] r8169 0000:04:00.0: eth0: link up
[   98.510206] r8169 0000:04:00.0: eth0: link up
[  100.836396] r8169 0000:04:00.0: eth0: link up
[  168.189336] r8169 0000:04:00.0: eth0: link up
[  173.396661] r8169 0000:04:00.0: eth0: link up
[  174.711663] r8169 0000:04:00.0: eth0: link up
[  176.534252] r8169 0000:04:00.0: eth0: link up
[  177.166294] r8169 0000:04:00.0: eth0: link up
[  177.661393] r8169 0000:04:00.0: eth0: link up
[  178.872461] r8169 0000:04:00.0: eth0: link up
[  179.935698] r8169 0000:04:00.0: eth0: link up
[  183.221531] r8169 0000:04:00.0: eth0: link up
[  184.188408] r8169 0000:04:00.0: eth0: link up
[  185.007762] r8169 0000:04:00.0: eth0: link up
[  185.571342] r8169 0000:04:00.0: eth0: link up
[  190.291684] r8169 0000:04:00.0: eth0: link up
[  241.232605] r8169 0000:04:00.0: eth0: link up
[  243.578805] r8169 0000:04:00.0: eth0: link up
[  247.899463] r8169 0000:04:00.0: eth0: link up
[  295.335035] r8169 0000:04:00.0: eth0: link up
[  299.812590] r8169 0000:04:00.0: eth0: link up
[  305.243449] r8169 0000:04:00.0: eth0: link up
[  308.576893] r8169 0000:04:00.0: eth0: link up
[  311.266825] r8169 0000:04:00.0: eth0: link up

---

### Post by novinick on 2011-05-25
hi
you typed 'iPconfig' with small letter 'p' which is windows conmand of similar funcionality
on unixes is 'iFconfig' with small letter  'f' and somewhat diferent options

other logs are enough to point out to
r8169 adapter which is the one culprit of restarting connection

as refered in this  thread , minutes a go

**Networking issues with r8169 Gigabit Ethernet on 11.04**
[http://ubuntuforums.org/showthread.php?t=1766962](http://ubuntuforums.org/showthread.php?t=1766962)

wew craked it by shutting down power :KS

---

### Post by jakejw93 on 2011-05-25
> **novinick said:**
> hi
you typed 'iPconfig' with small letter 'p' which is windows conmand of similar funcionality
on unixes is 'iFconfig' with small letter  'f' and somewhat diferent options

other logs are enough to point out to
r8169 adapter which is the one culprit of restarting connection

as refered in this  thread , minutes a go

**Networking issues with r8169 Gigabit Ethernet on 11.04**
[http://ubuntuforums.org/showthread.php?t=1766962](http://ubuntuforums.org/showthread.php?t=1766962)

wew craked it by shutting down power :KS

jakeward@jakejw93:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f4:6d:04:04:d6:4d  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:7044 errors:0 dropped:7044 overruns:0 frame:7044
          TX packets:6957 errors:0 dropped:39 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5836531 (5.8 MB)  TX bytes:1530224 (1.5 MB)
          Interrupt:46 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3244 (3.2 KB)  TX bytes:3244 (3.2 KB)

And in that thread he uses an ethernet card where as mine is just on my motherboard, i have no ethernet card... does that make a difference?

---

### Post by novinick on 2011-05-25
it is only maters the r8169 
and [10ec:8168] not the physical layout and wether is on mobo or as pci card. ;)

```
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8432]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by jakejw93 on 2011-05-25
> **novinick said:**
> it is only maters the r8169 
and [10ec:8168] not the physical layout and wether is on mobo or as pci card. ;)

```
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8432]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

So what you are saying (from other thread) is to shut down my computer for 10 minutes, unplug (everything or just the power?) turn it back on and boot into Ubuntu???

---

### Post by novinick on 2011-05-25
hi

 -shut it down normaly
-then pull the power plug on computer only (from wall socket? )
(so that theres no stand by power on mobo)
-live the router/cable modem powered on
-do not unplug ethernet cables , no need, i think

-wait 5 or 10  mins
-reboot in ubuntu first

---

### Post by jakejw93 on 2011-05-25
> **novinick said:**
> hi

 -shut it down normaly
-then pull the power plug on computer only (from wall socket? )
(so that theres no stand by power on mobo)
-live the router/cable modem powered on
-do not unplug ethernet cables , no need, i think

-wait 5 or 10  mins
-reboot in ubuntu first

Okay so i've done what you said, not too sure if its working yet....will try a youtube upload or something since i could not previously do that and will inform you of how it went :)

---

### Post by novinick on 2011-05-25
okay ;)

send again dmesg after 30mins or so

```

dmesg

```
(the long one listing)

---

### Post by jakejw93 on 2011-05-25
> **novinick said:**
> okay ;)

send again dmesg after 30mins or so

```

dmesg

```(the long one listing)

[http://www.youtube.com/watch?v=WxxUO1CQ66U](http://www.youtube.com/watch?v=WxxUO1CQ66U)

The result of good internet!!


jakeward@jakejw93:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-29-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #51-Ubuntu SMP Fri Apr 15 18:57:47 UTC 2011 (Ubuntu 2.6.35-29.51-generic-pae 2.6.35.12)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf53d000 (usable)
[    0.000000]  BIOS-e820: 00000000bf53d000 - 00000000bf58f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf58f000 - 00000000bf5af000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5af000 - 00000000bf5c0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5c0000 - 00000000bf5d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5d4000 - 00000000bf5d6000 (usable)
[    0.000000]  BIOS-e820: 00000000bf5d6000 - 00000000bf5d7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf5d7000 - 00000000bf5df000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5df000 - 00000000bf5e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5e9000 - 00000000bf642000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf642000 - 00000000bf685000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf685000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x13f800 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 13F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf53d000 (usable)
[    0.000000]  modified: 00000000bf53d000 - 00000000bf58f000 (ACPI NVS)
[    0.000000]  modified: 00000000bf58f000 - 00000000bf5af000 (reserved)
[    0.000000]  modified: 00000000bf5af000 - 00000000bf5c0000 (ACPI NVS)
[    0.000000]  modified: 00000000bf5c0000 - 00000000bf5d4000 (reserved)
[    0.000000]  modified: 00000000bf5d4000 - 00000000bf5d6000 (usable)
[    0.000000]  modified: 00000000bf5d6000 - 00000000bf5d7000 (ACPI data)
[    0.000000]  modified: 00000000bf5d7000 - 00000000bf5df000 (reserved)
[    0.000000]  modified: 00000000bf5df000 - 00000000bf5e9000 (ACPI NVS)
[    0.000000]  modified: 00000000bf5e9000 - 00000000bf642000 (reserved)
[    0.000000]  modified: 00000000bf642000 - 00000000bf685000 (ACPI NVS)
[    0.000000]  modified: 00000000bf685000 - 00000000bf800000 (usable)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000013f800000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00fcdc0] fcdc0
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 375b3000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a08000 - 01444fa6
[    0.000000] Move RAMDISK from 00000000375b3000 - 0000000037feffa5 to 00a08000 - 01444fa5
[    0.000000] ACPI: RSDP 000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT bf587068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP bf58ea28 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT bf587140 078E5 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS bf5e0f80 00040
[    0.000000] ACPI: APIC bf58eb20 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT bf58eb98 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG bf58eca0 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET bf58ece0 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4220MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0013f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf53d
[    0.000000]     0: 0x000bf5d4 -> 0x000bf5d6
[    0.000000]     0: 0x000bf685 -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x0013f800
[    0.000000] On node 0 totalpages: 1044040
[    0.000000] free_area_init_node: node 0, pgdat c0842d00, node_mem_map c1446200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8441 pages used for memmap
[    0.000000]   HighMem zone: 807363 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bf800000 (gap: bf800000:3f51c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3e00000 s39872 r0 d21568 u524288
[    0.000000] pcpu-alloc: s39872 r0 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1033815
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=e8c5b799-dfab-4d66-b569-675376afea1b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 26173120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (60 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009ff65c]   TEXT DATA BSS
[    0.000000]   #3 [0000a00000 - 0000a07206]             BRK
[    0.000000]   #4 [00000fcdd0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fcdc0 - 00000fcdd0]    MP-table mpf
[    0.000000]   #6 [000009ec00 - 00000fca90]   BIOS reserved
[    0.000000]   #7 [00000fcd44 - 00000fcdc0]   BIOS reserved
[    0.000000]   #8 [00000fca90 - 00000fcd44]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [0000a08000 - 0001445000]     NEW RAMDISK
[    0.000000]   #13 [0001445000 - 0001446000]         BOOTMEM
[    0.000000]   #14 [0001446000 - 0003c36000]         BOOTMEM
[    0.000000]   #15 [0003c36000 - 0003c36004]         BOOTMEM
[    0.000000]   #16 [0003c36040 - 0003c36100]         BOOTMEM
[    0.000000]   #17 [0003c36100 - 0003c361a8]         BOOTMEM
[    0.000000]   #18 [0003c361c0 - 0003c391c0]         BOOTMEM
[    0.000000]   #19 [0003c391c0 - 0003c394d8]         BOOTMEM
[    0.000000]   #20 [0003c39500 - 0003c45500]         BOOTMEM
[    0.000000]   #21 [0003c45500 - 0003c4552d]         BOOTMEM
[    0.000000]   #22 [0003c45540 - 0003c4556f]         BOOTMEM
[    0.000000]   #23 [0003c45580 - 0003c4582c]         BOOTMEM
[    0.000000]   #24 [0003c45840 - 0003c45880]         BOOTMEM
[    0.000000]   #25 [0003c45880 - 0003c458c0]         BOOTMEM
[    0.000000]   #26 [0003c458c0 - 0003c45900]         BOOTMEM
[    0.000000]   #27 [0003c45900 - 0003c45940]         BOOTMEM
[    0.000000]   #28 [0003c45940 - 0003c45980]         BOOTMEM
[    0.000000]   #29 [0003c45980 - 0003c459c0]         BOOTMEM
[    0.000000]   #30 [0003c459c0 - 0003c45a00]         BOOTMEM
[    0.000000]   #31 [0003c45a00 - 0003c45a40]         BOOTMEM
[    0.000000]   #32 [0003c45a40 - 0003c45a80]         BOOTMEM
[    0.000000]   #33 [0003c45a80 - 0003c45ac0]         BOOTMEM
[    0.000000]   #34 [0003c45ac0 - 0003c45b00]         BOOTMEM
[    0.000000]   #35 [0003c45b00 - 0003c45b40]         BOOTMEM
[    0.000000]   #36 [0003c45b40 - 0003c45b80]         BOOTMEM
[    0.000000]   #37 [0003c45b80 - 0003c45bc0]         BOOTMEM
[    0.000000]   #38 [0003c45bc0 - 0003c45c00]         BOOTMEM
[    0.000000]   #39 [0003c45c00 - 0003c45c40]         BOOTMEM
[    0.000000]   #40 [0003c45c40 - 0003c45c80]         BOOTMEM
[    0.000000]   #41 [0003c45c80 - 0003c45cc0]         BOOTMEM
[    0.000000]   #42 [0003c45cc0 - 0003c45cd0]         BOOTMEM
[    0.000000]   #43 [0003c45d00 - 0003c45d6e]         BOOTMEM
[    0.000000]   #44 [0003c45d80 - 0003c45dee]         BOOTMEM
[    0.000000]   #45 [0003e00000 - 0003e0f000]         BOOTMEM
[    0.000000]   #46 [0003e80000 - 0003e8f000]         BOOTMEM
[    0.000000]   #47 [0003f00000 - 0003f0f000]         BOOTMEM
[    0.000000]   #48 [0003f80000 - 0003f8f000]         BOOTMEM
[    0.000000]   #49 [0003c47e00 - 0003c47e04]         BOOTMEM
[    0.000000]   #50 [0003c47e40 - 0003c47e44]         BOOTMEM
[    0.000000]   #51 [0003c47e80 - 0003c47e90]         BOOTMEM
[    0.000000]   #52 [0003c47ec0 - 0003c47ed0]         BOOTMEM
[    0.000000]   #53 [0003c47f00 - 0003c47f98]         BOOTMEM
[    0.000000]   #54 [0003c47fc0 - 0003c47ff8]         BOOTMEM
[    0.000000]   #55 [0003c48000 - 0003c4c000]         BOOTMEM
[    0.000000]   #56 [0003c4c000 - 0003ccc000]         BOOTMEM
[    0.000000]   #57 [0003ccc000 - 0003d0c000]         BOOTMEM
[    0.000000]   #58 [0003c45e00 - 0003c46140]         BOOTMEM
[    0.000000]   #59 [0003f8f000 - 0005884ec0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0013f800)
[    0.000000] Memory: 4088848k/5234688k available (5097k kernel code, 87312k reserved, 2437k data, 708k init, 3263216k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085c000 - 0xc090d000   ( 708 kB)
[    0.000000]       .data : 0xc05fa46a - 0xc085b948   (2437 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05fa46a   (5097 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3291.898 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6583.79 BogoMIPS (lpj=13167592)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000016] Security Framework initialized
[    0.000024] AppArmor: AppArmor initialized
[    0.000025] Yama: becoming mindful.
[    0.000055] Mount-cache hash table entries: 512
[    0.000119] Initializing cgroup subsys ns
[    0.000121] Initializing cgroup subsys cpuacct
[    0.000124] Initializing cgroup subsys memory
[    0.000128] Initializing cgroup subsys devices
[    0.000130] Initializing cgroup subsys freezer
[    0.000131] Initializing cgroup subsys net_cls
[    0.000147] CPU: Physical Processor ID: 0
[    0.000148] CPU: Processor Core ID: 0
[    0.000151] mce: CPU supports 9 MCE banks
[    0.000161] CPU0: Thermal monitoring enabled (TM1)
[    0.000168] using mwait in idle threads.
[    0.000171] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.000175] ... version:                3
[    0.000176] ... bit width:              48
[    0.000177] ... generic registers:      8
[    0.000178] ... value mask:             0000ffffffffffff
[    0.000179] ... max period:             000000007fffffff
[    0.000180] ... fixed-purpose events:   3
[    0.000181] ... event mask:             00000007000000ff
[    0.002254] ACPI: Core revision 20100428
[    0.007426] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.007428] ftrace: allocating 22410 entries in 44 pages
[    0.013587] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.013917] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.053591] CPU0: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz stepping 07
[    0.160401] Booting Node   0, Processors  #1
[    0.170757] Initializing CPU#1
[    0.268470]  #2
[    0.278687] Initializing CPU#2
[    0.376438]  #3 Ok.
[    0.386655] Initializing CPU#3
[    0.484366] Brought up 4 CPUs
[    0.484368] Total of 4 processors activated (26333.22 BogoMIPS).
[    0.485700] devtmpfs: initialized
[    0.486403] regulator: core version 0.5
[    0.486426] Time: 21:17:46  Date: 05/25/11
[    0.486447] NET: Registered protocol family 16
[    0.486501] Trying to unpack rootfs image as initramfs...
[    0.486506] EISA bus registered
[    0.486510] ACPI: bus type pci registered
[    0.486553] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.486555] PCI: not using MMCONFIG
[    0.498964] PCI: Using configuration type 1 for base access
[    0.499459] bio: create slab <bio-0> at 0
[    0.500295] ACPI: EC: Look up EC in DSDT
[    0.501273] ACPI: Executed 1 blocks of module-level executable AML code
[    0.503668] ACPI Error (psargs-0359): [RAMB] Namespace lookup failure, AE_NOT_FOUND
[    0.503671] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20100428/nsinit-349)
[    0.505207] ACPI: SSDT bf5dfc18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.505465] ACPI: Dynamic OEM Table Load:
[    0.505467] ACPI: SSDT (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.505503] ACPI: SSDT bf5e0e18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.505716] ACPI: Dynamic OEM Table Load:
[    0.505718] ACPI: SSDT (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.506406] ACPI: Interpreter enabled
[    0.506409] ACPI: (supports S0 S1 S3 S4 S5)
[    0.506424] ACPI: Using IOAPIC for interrupt routing
[    0.506458] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.506543] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.506544] PCI: Using MMCONFIG for extended config space
[    0.506739] ACPI: BIOS _OSI(Linux) query ignored
[    0.511328] ACPI: No dock devices found.
[    0.511330] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.511576] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.511850] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.511852] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.511853] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.511855] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c8000-0x000dffff] conflicts with Video ROM [mem 0x000c0000-0x000ccbff]
[    0.511857] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.511903] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.511905] pci 0000:00:01.0: PME# disabled
[    0.511960] pci 0000:00:16.0: reg 10: [mem 0xfb107000-0xfb10700f 64bit]
[    0.512002] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.512005] pci 0000:00:16.0: PME# disabled
[    0.512049] pci 0000:00:1a.0: reg 10: [mem 0xfb106000-0xfb1063ff]
[    0.512099] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.512103] pci 0000:00:1a.0: PME# disabled
[    0.512133] pci 0000:00:1b.0: reg 10: [mem 0xfb100000-0xfb103fff 64bit]
[    0.512170] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.512173] pci 0000:00:1b.0: PME# disabled
[    0.512242] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.512245] pci 0000:00:1c.0: PME# disabled
[    0.512316] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.512319] pci 0000:00:1c.1: PME# disabled
[    0.512387] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.512390] pci 0000:00:1c.2: PME# disabled
[    0.512458] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.512461] pci 0000:00:1c.3: PME# disabled
[    0.512529] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.512532] pci 0000:00:1c.4: PME# disabled
[    0.512600] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.512603] pci 0000:00:1c.5: PME# disabled
[    0.512644] pci 0000:00:1d.0: reg 10: [mem 0xfb105000-0xfb1053ff]
[    0.512696] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.512699] pci 0000:00:1d.0: PME# disabled
[    0.512807] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    0.512812] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    0.512816] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    0.512820] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    0.512825] pci 0000:00:1f.2: reg 20: [io  0xf090-0xf09f]
[    0.512829] pci 0000:00:1f.2: reg 24: [io  0xf080-0xf08f]
[    0.512868] pci 0000:00:1f.3: reg 10: [mem 0xfb104000-0xfb1040ff 64bit]
[    0.512880] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.512912] pci 0000:00:1f.5: reg 10: [io  0xf070-0xf077]
[    0.512917] pci 0000:00:1f.5: reg 14: [io  0xf060-0xf063]
[    0.512921] pci 0000:00:1f.5: reg 18: [io  0xf050-0xf057]
[    0.512926] pci 0000:00:1f.5: reg 1c: [io  0xf040-0xf043]
[    0.512930] pci 0000:00:1f.5: reg 20: [io  0xf030-0xf03f]
[    0.512934] pci 0000:00:1f.5: reg 24: [io  0xf020-0xf02f]
[    0.512989] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.512996] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.513003] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.513006] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.513010] pci 0000:01:00.0: reg 30: [mem 0xfb000000-0xfb01ffff pref]
[    0.520234] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.520237] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.520239] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfb0fffff]
[    0.520241] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.520282] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.520286] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.520289] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.520294] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.520336] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.520339] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.520342] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.520347] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.520420] pci 0000:04:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.520443] pci 0000:04:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.520459] pci 0000:04:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.520512] pci 0000:04:00.0: supports D1 D2
[    0.520513] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520517] pci 0000:04:00.0: PME# disabled
[    0.528239] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.528243] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.528246] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528251] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.528293] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.528297] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528300] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528305] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528447] pci 0000:00:1c.4: PCI bridge to [bus 06-07] (subtractive decode)
[    0.528450] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528453] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528458] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528460] pci 0000:00:1c.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.528461] pci 0000:00:1c.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.528462] pci 0000:00:1c.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.528464] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.528576] pci 0000:06:00.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.528586] pci 0000:06:00.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.528591] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528600] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528601] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528603] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528604] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528605] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.528607] pci 0000:06:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.528608] pci 0000:06:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.528610] pci 0000:06:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.528611] pci 0000:06:00.0:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.528663] pci 0000:00:1c.5: PCI bridge to [bus 08-08]
[    0.528666] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528669] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528674] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.528702] pci_bus 0000:00: on NUMA node 0
[    0.528706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.528815] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.528854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.528889] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.528925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.528966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4.BR16._PRT]
[    0.532144] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532210] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532279] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.532342] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.532406] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.532469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.532532] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.532596] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.532624] HEST: Table is not found!
[    0.532668] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.532670] vgaarb: loaded
[    0.532751] SCSI subsystem initialized
[    0.532812] libata version 3.00 loaded.
[    0.532839] usbcore: registered new interface driver usbfs
[    0.532845] usbcore: registered new interface driver hub
[    0.532857] usbcore: registered new device driver usb
[    0.532973] ACPI: WMI: Mapper loaded
[    0.532974] PCI: Using ACPI for IRQ routing
[    0.532976] PCI: pci_cache_line_size set to 64 bytes
[    0.533034] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.533035] reserve RAM buffer: 00000000bf53d000 - 00000000bfffffff 
[    0.533038] reserve RAM buffer: 00000000bf5d6000 - 00000000bfffffff 
[    0.533040] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.533041] reserve RAM buffer: 000000013f800000 - 000000013fffffff 
[    0.533091] NetLabel: Initializing
[    0.533092] NetLabel:  domain hash size = 128
[    0.533092] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.533099] NetLabel:  unlabeled traffic allowed by default
[    0.533120] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.533124] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.535137] Switching to clocksource tsc
[    0.540748] AppArmor: AppArmor Filesystem Enabled
[    0.540756] pnp: PnP ACPI init
[    0.540765] ACPI: bus type pnp registered
[    0.542727] pnp: PnP ACPI: found 13 devices
[    0.542728] ACPI: ACPI bus type pnp unregistered
[    0.542730] PnPBIOS: Disabled by ACPI PNP
[    0.542737] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.542739] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.542740] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.542742] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.542743] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.542747] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.542751] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.542754] system 00:0a: [io  0x0400-0x0453] has been reserved
[    0.542755] system 00:0a: [io  0x0458-0x047f] has been reserved
[    0.542757] system 00:0a: [io  0x0500-0x057f] has been reserved
[    0.542758] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.542760] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.542762] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.542763] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.542767] system 00:0b: [io  0x0454-0x0457] has been reserved
[    0.578017] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.578020] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.578022] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfb0fffff]
[    0.578024] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.578027] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.578028] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.578032] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.578035] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.578040] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.578041] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.578045] pci 0000:00:1c.1:   bridge window [mem disabled]
[    0.578048] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.578053] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.578055] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.578059] pci 0000:00:1c.2:   bridge window [mem disabled]
[    0.578062] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.578067] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.578068] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.578072] pci 0000:00:1c.3:   bridge window [mem disabled]
[    0.578075] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.578080] pci 0000:06:00.0: PCI bridge to [bus 07-07]
[    0.578081] pci 0000:06:00.0:   bridge window [io  disabled]
[    0.578088] pci 0000:06:00.0:   bridge window [mem disabled]
[    0.578093] pci 0000:06:00.0:   bridge window [mem pref disabled]
[    0.578102] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.578103] pci 0000:00:1c.4:   bridge window [io  disabled]
[    0.578107] pci 0000:00:1c.4:   bridge window [mem disabled]
[    0.578110] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.578115] pci 0000:00:1c.5: PCI bridge to [bus 08-08]
[    0.578116] pci 0000:00:1c.5:   bridge window [io  disabled]
[    0.578120] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.578122] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    0.578134]   alloc irq_desc for 16 on node -1
[    0.578135]   alloc kstat_irqs on node -1
[    0.578139] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.578142] pci 0000:00:01.0: setting latency timer to 64
[    0.578148]   alloc irq_desc for 17 on node -1
[    0.578149]   alloc kstat_irqs on node -1
[    0.578151] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578154] pci 0000:00:1c.0: setting latency timer to 64
[    0.578161] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.578164] pci 0000:00:1c.1: setting latency timer to 64
[    0.578170]   alloc irq_desc for 18 on node -1
[    0.578171]   alloc kstat_irqs on node -1
[    0.578173] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.578176] pci 0000:00:1c.2: setting latency timer to 64
[    0.578183]   alloc irq_desc for 19 on node -1
[    0.578184]   alloc kstat_irqs on node -1
[    0.578186] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.578189] pci 0000:00:1c.3: setting latency timer to 64
[    0.578195] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578198] pci 0000:00:1c.4: setting latency timer to 64
[    0.578204] pci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.578209] pci 0000:06:00.0: setting latency timer to 64
[    0.578217] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.578220] pci 0000:00:1c.5: setting latency timer to 64
[    0.578223] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.578224] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.578225] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.578226] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.578228] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.578229] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfb0fffff]
[    0.578230] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.578232] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.578233] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.578235] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.578236] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.578237] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.578238] pci_bus 0000:06: resource 7 [mem 0xc0000000-0xffffffff]
[    0.578240] pci_bus 0000:07: resource 8 [io  0x0000-0x0cf7]
[    0.578241] pci_bus 0000:07: resource 9 [io  0x0d00-0xffff]
[    0.578242] pci_bus 0000:07: resource 10 [mem 0x000a0000-0x000bffff]
[    0.578243] pci_bus 0000:07: resource 11 [mem 0xc0000000-0xffffffff]
[    0.578264] NET: Registered protocol family 2
[    0.578296] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.578398] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.578599] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.578699] TCP: Hash tables configured (established 131072 bind 65536)
[    0.578700] TCP reno registered
[    0.578702] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.578706] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.578745] NET: Registered protocol family 1
[    0.832154] pci 0000:01:00.0: Boot video device
[    0.832163] PCI: CLS 64 bytes, default 64
[    0.832340] cpufreq-nforce2: No nForce2 chipset.
[    0.832357] Scanning for low memory corruption every 60 seconds
[    0.832413] audit: initializing netlink socket (disabled)
[    0.832420] type=2000 audit(1306358266.676:1): initialized
[    0.838556] highmem bounce pool size: 64 pages
[    0.838558] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.839288] VFS: Disk quotas dquot_6.5.2
[    0.839319] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.839616] fuse init (API version 7.14)
[    0.839660] msgmni has been set to 1612
[    0.861827] Freeing initrd memory: 10484k freed
[    0.864352] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.864355] io scheduler noop registered
[    0.864356] io scheduler deadline registered
[    0.864362] io scheduler cfq registered (default)
[    0.864422] pcieport 0000:00:01.0: setting latency timer to 64
[    0.864436]   alloc irq_desc for 40 on node -1
[    0.864438]   alloc kstat_irqs on node -1
[    0.864443] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.864481] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.864512]   alloc irq_desc for 41 on node -1
[    0.864513]   alloc kstat_irqs on node -1
[    0.864518] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.864571] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.864602]   alloc irq_desc for 42 on node -1
[    0.864603]   alloc kstat_irqs on node -1
[    0.864608] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.864660] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.864691]   alloc irq_desc for 43 on node -1
[    0.864692]   alloc kstat_irqs on node -1
[    0.864697] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.864748] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.864779]   alloc irq_desc for 44 on node -1
[    0.864780]   alloc kstat_irqs on node -1
[    0.864785] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.864837] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.864868]   alloc irq_desc for 45 on node -1
[    0.864869]   alloc kstat_irqs on node -1
[    0.864874] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    0.864932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.864943] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.864995] intel_idle: MWAIT substates: 0x1120
[    0.864996] intel_idle: v0.4 model 0x2A
[    0.864997] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.865064] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.865067] ACPI: Power Button [PWRB]
[    0.865093] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.865094] ACPI: Power Button [PWRF]
[    0.865260] ACPI: acpi_idle yielding to intel_idle
[    0.866953] ERST: Table is not found!
[    0.866964] isapnp: Scanning for PnP cards...
[    0.867082] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.867177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.867465] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.868067] brd: module loaded
[    0.868341] loop: module loaded
[    0.868442] ata_piix 0000:00:1f.2: version 2.13
[    0.868452]   alloc irq_desc for 20 on node -1
[    0.868453]   alloc kstat_irqs on node -1
[    0.868456] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.868460] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.024201] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
[    1.024207] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.024244] scsi0 : ata_piix
[    1.024283] scsi1 : ata_piix
[    1.025084] ata1: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 20
[    1.025085] ata2: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 20
[    1.025098] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.025101] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.025127] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.025154] scsi2 : ata_piix
[    1.025186] scsi3 : ata_piix
[    1.026101] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 20
[    1.026104] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 20
[    1.026270] Fixed MDIO Bus: probed
[    1.026286] PPP generic driver version 2.4.2
[    1.026307] tun: Universal TUN/TAP device driver, 1.6
[    1.026308] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.026351] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.026361]   alloc irq_desc for 23 on node -1
[    1.026362]   alloc kstat_irqs on node -1
[    1.026365] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.026373] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.026375] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.026394] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.026416] ehci_hcd 0000:00:1a.0: debug port 2
[    1.030283] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.030293] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfb106000
[    1.044061] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.044128] hub 1-0:1.0: USB hub found
[    1.044131] hub 1-0:1.0: 2 ports detected
[    1.044165] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.044172] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.044174] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.044190] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.044208] ehci_hcd 0000:00:1d.0: debug port 2
[    1.048099] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.048102] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfb105000
[    1.060055] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.060111] hub 2-0:1.0: USB hub found
[    1.060113] hub 2-0:1.0: 2 ports detected
[    1.060145] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.060151] uhci_hcd: USB Universal Host Controller Interface driver
[    1.060200] PNP: No PS/2 controller found. Probing ports directly.
[    1.062780] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.062783] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.062819] mice: PS/2 mouse device common for all mice
[    1.062876] rtc_cmos 00:05: RTC can wake from S4
[    1.062893] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.062916] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.062966] device-mapper: uevent: version 1.0.3
[    1.063023] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.063073] device-mapper: multipath: version 1.1.1 loaded
[    1.063074] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.063129] EISA: Probing bus 0 at eisa.0
[    1.063130] EISA: Cannot allocate resource for mainboard
[    1.063131] Cannot allocate resource for EISA slot 1
[    1.063132] Cannot allocate resource for EISA slot 2
[    1.063133] Cannot allocate resource for EISA slot 3
[    1.063134] Cannot allocate resource for EISA slot 4
[    1.063135] Cannot allocate resource for EISA slot 5
[    1.063136] Cannot allocate resource for EISA slot 6
[    1.063137] Cannot allocate resource for EISA slot 7
[    1.063138] Cannot allocate resource for EISA slot 8
[    1.063139] EISA: Detected 0 cards.
[    1.063271] cpuidle: using governor ladder
[    1.063371] cpuidle: using governor menu
[    1.063506] TCP cubic registered
[    1.063572] NET: Registered protocol family 10
[    1.063734] lo: Disabled Privacy Extensions
[    1.063830] NET: Registered protocol family 17
[    1.064393] Using IPI No-Shortcut mode
[    1.064429] PM: Resume from disk failed.
[    1.064434] registered taskstats version 1
[    1.064656]   Magic number: 11:819:298
[    1.064698] rtc_cmos 00:05: setting system clock to 2011-05-25 21:17:47 UTC (1306358267)
[    1.064700] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.064701] EDD information not available.
[    1.221079] isapnp: No Plug & Play device found
[    1.368088] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.388128] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.388285] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.391477] ata4.00: ATA-7: MAXTOR STM3250310AS, 4.AAA, max UDMA/133
[    1.391479] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.391608] ata3.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    1.391610] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.407470] ata4.00: configured for UDMA/133
[    1.407609] ata3.00: configured for UDMA/133
[    1.407775] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    1.407858] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.407887] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.407931] sd 2:0:0:0: [sda] Write Protect is off
[    1.407933] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.407952] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408034] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR STM325031 4.AA PQ: 0 ANSI: 5
[    1.408055]  sda:
[    1.408109] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.408208] sd 3:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.408388] sd 3:0:0:0: [sdb] Write Protect is off
[    1.408391] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.408441] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408640]  sdb: sdb1
[    1.415473] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.419267]  sda1 sda2 sda3 sda4 < sda5 >
[    1.439613] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.439686] Freeing unused kernel memory: 708k freed
[    1.439889] Write protecting the kernel text: 5100k
[    1.439990] Write protecting the kernel read-only data: 2016k
[    1.449727] udev[106]: starting version 163
[    1.463622] hub 1-1:1.0: USB hub found
[    1.463727] hub 1-1:1.0: 4 ports detected
[    1.470134] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.470152] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.470192] r8169 0000:04:00.0: setting latency timer to 64
[    1.470199] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
[    1.470268]   alloc irq_desc for 46 on node -1
[    1.470269]   alloc kstat_irqs on node -1
[    1.470282] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
[    1.470536] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xf8466000, f4:6d:04:04:d6:4d, XID 0c900800 IRQ 46
[    1.575061] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.703679] hub 2-1:1.0: USB hub found
[    1.703785] hub 2-1:1.0: 6 ports detected
[    1.775194] usb 1-1.3: new high speed USB device using ehci_hcd and address 3
[    1.875513] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.876801] Initializing USB Mass Storage driver...
[    1.876876] scsi4 : usb-storage 1-1.3:1.0
[    1.877036] usbcore: registered new interface driver usb-storage
[    1.877045] USB Mass Storage support registered.
[    1.975139] usb 2-1.1: new low speed USB device using ehci_hcd and address 3
[    2.163086] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
[    2.258078] scsi5 : usb-storage 2-1.2:1.0
[    2.327029] usb 2-1.3: new low speed USB device using ehci_hcd and address 5
[    2.876613] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF RW 0814 PQ: 0 ANSI: 0
[    2.877710] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader Combo 0814 PQ: 0 ANSI: 0
[    2.878004] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.878085] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    2.881943] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    2.883327] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    3.256237] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS0C PQ: 0 ANSI: 0
[    3.259217] sr0: scsi3-mmc drive: 47x/125x writer cd/rw xa/form2 cdda tray
[    3.259219] Uniform CD-ROM driver Revision: 3.20
[    3.259279] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.259311] sr 5:0:0:0: Attached scsi generic sg4 type 5
[   10.715912] Adding 4174844k swap on /dev/sda5.  Priority:-1 extents:1 across:4174844k 
[   10.734895] udev[383]: starting version 163
[   10.748606] Linux agpgart interface v0.103
[   10.771254] nvidia: module license 'NVIDIA' taints kernel.
[   10.771256] Disabling lock debugging due to kernel taint
[   10.779290] lp: driver loaded but no devices found
[   10.786992] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input2
[   10.807994] usbcore: registered new interface driver hiddev
[   10.817136] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input3
[   10.817179] generic-usb 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1/input0
[   10.820114] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input4
[   10.820164] generic-usb 0003:192F:0616.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.3/input0
[   10.820174] usbcore: registered new interface driver usbhid
[   10.820175] usbhid: USB HID core driver
[   10.835138] parport_pc 00:03: reported by Plug and Play ACPI
[   10.835185] parport0: PC-style at 0x378, irq 5 [PCSPP]
[   10.838492] ppdev: user-space parallel port driver
[   10.860891]   alloc irq_desc for 22 on node -1
[   10.860893]   alloc kstat_irqs on node -1
[   10.860897] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.860927]   alloc irq_desc for 47 on node -1
[   10.860928]   alloc kstat_irqs on node -1
[   10.860935] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   10.860952] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.871992] type=1400 audit(1306354677.304:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=631 comm="apparmor_parser"
[   10.871999] type=1400 audit(1306354677.304:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=608 comm="apparmor_parser"
[   10.872374] type=1400 audit(1306354677.304:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
[   10.872382] type=1400 audit(1306354677.304:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=608 comm="apparmor_parser"
[   10.872579] type=1400 audit(1306354677.304:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=631 comm="apparmor_parser"
[   10.872589] type=1400 audit(1306354677.304:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=608 comm="apparmor_parser"
[   10.907101] hda_codec: ALC887-VD: BIOS auto-probing.
[   10.911330] Too many connections
[   10.930622] lp0: using parport0 (interrupt-driven).
[   11.118312] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.118318] nvidia 0000:01:00.0: setting latency timer to 64
[   11.118322] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.118378] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   11.205103] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.397524] type=1400 audit(1306354677.832:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=933 comm="apparmor_parser"
[   11.397639] type=1400 audit(1306354677.832:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=934 comm="apparmor_parser"
[   11.398022] type=1400 audit(1306354677.832:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=934 comm="apparmor_parser"
[   11.398229] type=1400 audit(1306354677.832:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=934 comm="apparmor_parser"
[   11.911160] r8169 0000:04:00.0: eth0: link up
[   11.911165] r8169 0000:04:00.0: eth0: link up
[   12.914297] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   13.030071] r8169: WARNING! Changing of MTU on this NIC may lead to frame reception errors!
[   14.640132] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.541121] ISO 9660 Extensions: Microsoft Joliet Level 3
[   25.584484] ISOFS: changing to secondary root

Don't know what that will show you now....but thanks a lot mate. Seriously thank you!!!

---

### Post by novinick on 2011-05-25
glad it is working
:popcorn: 
have fun playing games , nice demo video btw ;) i'll got it down by download helper


new listing is showing only one message of activating connection
while previous listing was all over the place:

```
[   33.222574] r8169 0000:04:00.0: eth0: link up
[   33.222608] r8169 0000:04:00.0: eth0: link up
[   34.240671] r8169: WARNING! Changing of MTU on this NIC may lead to frame reception errors!
[   71.962573] r8169 0000:04:00.0: eth0: link up <---- another 
[   80.476040] r8169 0000:04:00.0: eth0: link up <---- another 
[   98.510206] r8169 0000:04:00.0: eth0: link up <---- another 
[  100.836396] r8169 0000:04:00.0: eth0: link up<---- another 
[  168.189336] r8169 0000:04:00.0: eth0: link up<----yet another ... et cetera...
[  173.396661] r8169 0000:04:00.0: eth0: link up
[  174.711663] r8169 0000:04:00.0: eth0: link up
[  176.534252] r8169 0000:04:00.0: eth0: link up
[  177.166294] r8169 0000:04:00.0: eth0: link up
[  177.661393] r8169 0000:04:00.0: eth0: link up
```now we got it running (on two forum threads)
 hope this will show clues what was really messed up  :confused:

perhaps now you may or should revert your mtu setting ? dunno ?
[   34.240671] r8169: WARNING! Changing of MTU on this NIC may lead to frame reception errors!

from

> I've set my MTU to 1492 and also turned ipv6 off, please help anyone!!?!to what was it before
and ipv6 leave it turned off

---

