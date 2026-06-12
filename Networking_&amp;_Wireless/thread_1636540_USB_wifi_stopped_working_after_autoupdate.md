---
title: "USB wifi stopped working after autoupdate"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by uliz on 2010-12-03
Hi all, I'm using a A-link WLAN USB card with rtl8188 chipset on a Ubuntu 10.10 system. It worked out of the box with nm-applet until yesterdays autoupdate. Kernel was updated from 2.6.35-22 to -23, but wlan wouldn't work when booting to -22 anymore either. 

Here's a list of stuff changed, I would suspect that this could have something to do with bind9-host, dnsutils or libdns66. Can I just get the old versions back somehow or is there a more reasonable solution?  

```
Install: linux-image-2.6.35-23-generic:i386 (2.6.35-23.41), linux-headers-2.6.35-23:i386 (2.6.35-23.41), linux-headers-2.6.35-23-generic:i386 (2.6.35-23.41)

Upgrade: libpurple0:i386 (2.7.3-1ubuntu3.1, 2.7.3-1ubuntu3.2), libqt4-opengl:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), gwibber-service:i386 (2.32.0.2-0ubuntu1, 2.32.2-0ubuntu1), libutouch-grail1:i386 (1.0.15-0ubuntu1, 1.0.16-0ubuntu1), bind9-host:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), linux-headers-generic:i386 (2.6.35.22.23, 2.6.35.23.25), smbclient:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), icedtea6-plugin:i386 (6b20-1.9.1-1ubuntu3, 6b20-1.9.2-0ubuntu1), dnsutils:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), linux-image-generic:i386 (2.6.35.22.23, 2.6.35.23.25), libqt4-dbus:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), libdns66:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), icedtea-6-jre-cacao:i386 (6b20-1.9.1-1ubuntu3, 6b20-1.9.2-0ubuntu1), linux-libc-dev:i386 (2.6.35-1022.35, 2.6.35-1023.41), libsmbclient:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), libisccc60:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), libvlc5:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), samba-common-bin:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), liblwres60:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), vlc-nox:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), libqtcore4:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), openjdk-6-jre-headless:i386 (6b20-1.9.1-1ubuntu3, 6b20-1.9.2-0ubuntu1), update-inetd:i386 (4.36, 4.36ubuntu0.1), openjdk-6-jre:i386 (6b20-1.9.1-1ubuntu3, 6b20-1.9.2-0ubuntu1), openjdk-6-jre-lib:i386 (6b20-1.9.1-1ubuntu3, 6b20-1.9.2-0ubuntu1), libbind9-60:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), libqt4-svg:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), libwbclient0:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), libqt4-xml:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), vlc:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), libqt4-network:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), vlc-plugin-notify:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), libldap-2.4-2:i386 (2.4.23-0ubuntu3.3, 2.4.23-0ubuntu3.4), libisccfg60:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), libqtgui4:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), libpurple-bin:i386 (2.7.3-1ubuntu3.1, 2.7.3-1ubuntu3.2), vlc-plugin-pulse:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), vlc-data:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), samba-common:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), winbind:i386 (3.5.4~dfsg-1ubuntu8, 3.5.4~dfsg-1ubuntu8.1), gwibber:i386 (2.32.0.2-0ubuntu1, 2.32.2-0ubuntu1), libisc60:i386 (9.7.1.dfsg.P2-2, 9.7.1.dfsg.P2-2ubuntu0.1), libqt4-script:i386 (4.7.0-0ubuntu4, 4.7.0-0ubuntu4.2), libvlccore4:i386 (1.1.4-1ubuntu1, 1.1.4-1ubuntu1.1), linux-generic:i386 (2.6.35.22.23, 2.6.35.23.25)
```

Also, dmesg gives the following:

```

uli@acer:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/driver$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6df000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6df000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6df000 (ACPI NVS)
[    0.000000]  modified: 000000007f6df000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7e10] f7e10
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375aa000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 013ea6bd
[    0.000000] Move RAMDISK from 00000000375aa000 - 0000000037fef6bc to 009a5000 - 013ea6bc
[    0.000000] ACPI: RSDP 000f7ca0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f6d1dee 0008C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 7f6dbc3a 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6d34b1 08715 (v02 INTEL  CRESTLNE 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 7f6defc0 00040
[    0.000000] ACPI: HPET 7f6dbd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6dbd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7f6dbda2 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 7f6dbdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 7f6dbdfa 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: APIC 7f6dbf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f6dbfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f6d31d4 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d3009 001CB (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d2406 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d2360 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d1e7a 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521823
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c13ec200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517745
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=cf6ff5bd-96c6-49e0-b394-85c1b396c820 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (53 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a41d8]             BRK
[    0.000000]   #4 [00000f7e20 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7e10 - 00000f7e20]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009fee5 - 00000f7e10]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009fee5]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a5000 - 00013eb000]     NEW RAMDISK
[    0.000000]   #13 [00013eb000 - 00013ec000]         BOOTMEM
[    0.000000]   #14 [00013ec000 - 00023dc000]         BOOTMEM
[    0.000000]   #15 [00023dc000 - 00023dc004]         BOOTMEM
[    0.000000]   #16 [00023dc040 - 00023dc100]         BOOTMEM
[    0.000000]   #17 [00023dc100 - 00023dc154]         BOOTMEM
[    0.000000]   #18 [00023dc180 - 00023df180]         BOOTMEM
[    0.000000]   #19 [00023df180 - 00023df1ec]         BOOTMEM
[    0.000000]   #20 [00023df200 - 00023e5200]         BOOTMEM
[    0.000000]   #21 [00023e5200 - 00023e5225]         BOOTMEM
[    0.000000]   #22 [00023e5240 - 00023e5267]         BOOTMEM
[    0.000000]   #23 [00023e5280 - 00023e5424]         BOOTMEM
[    0.000000]   #24 [00023e5440 - 00023e5480]         BOOTMEM
[    0.000000]   #25 [00023e5480 - 00023e54c0]         BOOTMEM
[    0.000000]   #26 [00023e54c0 - 00023e5500]         BOOTMEM
[    0.000000]   #27 [00023e5500 - 00023e5540]         BOOTMEM
[    0.000000]   #28 [00023e5540 - 00023e5580]         BOOTMEM
[    0.000000]   #29 [00023e5580 - 00023e55c0]         BOOTMEM
[    0.000000]   #30 [00023e55c0 - 00023e5600]         BOOTMEM
[    0.000000]   #31 [00023e5600 - 00023e5640]         BOOTMEM
[    0.000000]   #32 [00023e5640 - 00023e5680]         BOOTMEM
[    0.000000]   #33 [00023e5680 - 00023e56c0]         BOOTMEM
[    0.000000]   #34 [00023e56c0 - 00023e5700]         BOOTMEM
[    0.000000]   #35 [00023e5700 - 00023e5740]         BOOTMEM
[    0.000000]   #36 [00023e5740 - 00023e5780]         BOOTMEM
[    0.000000]   #37 [00023e5780 - 00023e57c0]         BOOTMEM
[    0.000000]   #38 [00023e57c0 - 00023e57d0]         BOOTMEM
[    0.000000]   #39 [00023e5800 - 00023e586a]         BOOTMEM
[    0.000000]   #40 [00023e5880 - 00023e58ea]         BOOTMEM
[    0.000000]   #41 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #42 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #43 [00023e7900 - 00023e7904]         BOOTMEM
[    0.000000]   #44 [00023e7940 - 00023e7944]         BOOTMEM
[    0.000000]   #45 [00023e7980 - 00023e7988]         BOOTMEM
[    0.000000]   #46 [00023e79c0 - 00023e79c8]         BOOTMEM
[    0.000000]   #47 [00023e7a00 - 00023e7aa8]         BOOTMEM
[    0.000000]   #48 [00023e7ac0 - 00023e7b28]         BOOTMEM
[    0.000000]   #49 [00023e7b40 - 00023ebb40]         BOOTMEM
[    0.000000]   #50 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #51 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #52 [000260e000 - 0003002700]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2040436k/2087744k available (4930k kernel code, 46856k reserved, 2334k data, 684k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.005 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.01 BogoMIPS (lpj=6384020)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004037] Security Framework initialized
[    0.004059] AppArmor: AppArmor initialized
[    0.004061] Yama: becoming mindful.
[    0.004132] Mount-cache hash table entries: 512
[    0.004304] Initializing cgroup subsys ns
[    0.004310] Initializing cgroup subsys cpuacct
[    0.004316] Initializing cgroup subsys memory
[    0.004327] Initializing cgroup subsys devices
[    0.004330] Initializing cgroup subsys freezer
[    0.004332] Initializing cgroup subsys net_cls
[    0.004368] CPU: Physical Processor ID: 0
[    0.004371] CPU: Processor Core ID: 0
[    0.004374] mce: CPU supports 6 MCE banks
[    0.004384] CPU0: Thermal monitoring handled by SMI
[    0.004389] using mwait in idle threads.
[    0.004399] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004407] PEBS disabled due to CPU errata.
[    0.004416] ... version:                2
[    0.004419] ... bit width:              40
[    0.004421] ... generic registers:      2
[    0.004424] ... value mask:             000000ffffffffff
[    0.004426] ... max period:             000000007fffffff
[    0.004429] ... fixed-purpose events:   3
[    0.004431] ... event mask:             0000000700000003
[    0.009166] ACPI: Core revision 20100428
[    0.024013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024024] ftrace: allocating 21766 entries in 43 pages
[    0.028069] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032266] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071955] CPU0: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[    0.072000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.160018] Brought up 2 CPUs
[    0.160022] Total of 2 processors activated (6384.35 BogoMIPS).
[    0.160517] devtmpfs: initialized
[    0.161291] regulator: core version 0.5
[    0.161328] Time: 15:05:05  Date: 12/03/10
[    0.161380] NET: Registered protocol family 16
[    0.161411] Trying to unpack rootfs image as initramfs...
[    0.161554] EISA bus registered
[    0.161565] ACPI: bus type pci registered
[    0.161667] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.161672] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.161675] PCI: Using MMCONFIG for extended config space
[    0.161677] PCI: Using configuration type 1 for base access
[    0.168455] bio: create slab <bio-0> at 0
[    0.170669] ACPI: EC: Look up EC in DSDT
[    0.176468] ACPI: BIOS _OSI(Linux) query ignored
[    0.178211] ACPI: SSDT 7f6d2d09 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.178888] ACPI: Dynamic OEM Table Load:
[    0.178893] ACPI: SSDT (null) 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.179310] ACPI: SSDT 7f6d2665 0061F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.179962] ACPI: Dynamic OEM Table Load:
[    0.179967] ACPI: SSDT (null) 0061F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.180550] ACPI: SSDT 7f6d2f41 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.181212] ACPI: Dynamic OEM Table Load:
[    0.181217] ACPI: SSDT (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.181417] ACPI: SSDT 7f6d2c84 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.182064] ACPI: Dynamic OEM Table Load:
[    0.182069] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.192036] ACPI: Interpreter enabled
[    0.192044] ACPI: (supports S0 S3 S4 S5)
[    0.192080] ACPI: Using IOAPIC for interrupt routing
[    0.208564] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.208973] ACPI: No dock devices found.
[    0.208980] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.209793] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.211370] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.211375] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.211379] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.211383] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.211386] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.211390] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.211395] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.211398] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.211495] pci 0000:00:02.0: reg 10: [mem 0xfc000000-0xfc0fffff 64bit]
[    0.211507] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.211514] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.211570] pci 0000:00:02.1: reg 10: [mem 0xfc100000-0xfc1fffff 64bit]
[    0.211715] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
[    0.211797] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
[    0.211877] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.211957] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.211964] pci 0000:00:1a.7: PME# disabled
[    0.212030] pci 0000:00:1b.0: reg 10: [mem 0xfc200000-0xfc203fff 64bit]
[    0.212108] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.212114] pci 0000:00:1b.0: PME# disabled
[    0.212238] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.212244] pci 0000:00:1c.0: PME# disabled
[    0.212375] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.212382] pci 0000:00:1c.1: PME# disabled
[    0.212509] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.212515] pci 0000:00:1c.2: PME# disabled
[    0.212599] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.212678] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.212764] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.212843] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.212922] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.212930] pci 0000:00:1d.7: PME# disabled
[    0.213131] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.213137] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.213145] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0068 (mask 0007)
[    0.213214] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.213224] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.213234] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.213244] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.213255] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.213333] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
[    0.213344] pci 0000:00:1f.2: reg 14: [io  0x18d4-0x18d7]
[    0.213354] pci 0000:00:1f.2: reg 18: [io  0x18d8-0x18df]
[    0.213364] pci 0000:00:1f.2: reg 1c: [io  0x18d0-0x18d3]
[    0.213374] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.213384] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.213439] pci 0000:00:1f.2: PME# supported from D3hot
[    0.213445] pci 0000:00:1f.2: PME# disabled
[    0.213485] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.213516] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.213731] pci 0000:02:00.0: reg 10: [mem 0xf6000000-0xf600ffff 64bit]
[    0.213856] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.213864] pci 0000:02:00.0: PME# disabled
[    0.220074] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.220082] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.220089] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.220100] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.220179] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.220186] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.220193] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.220204] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.220282] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.220288] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.220295] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.220306] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.220418] pci 0000:00:1e.0: PCI bridge to [bus 0f-0f] (subtractive decode)
[    0.220426] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.220433] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.220444] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.220448] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.220451] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.220487] pci_bus 0000:00: on NUMA node 0
[    0.220502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.220855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.220976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.221091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.221273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.221319] ACPI Warning for \_SB_.PCI0.PCIB._PRT: Return Package has no elements (empty) (20100428/nspredef-456)
[    0.237968] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[    0.238107] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    0.238246] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.238382] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.238515] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    0.238647] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.238779] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    0.238912] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    0.238974] HEST: Table is not found!
[    0.239086] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.239108] vgaarb: loaded
[    0.239332] SCSI subsystem initialized
[    0.239454] libata version 3.00 loaded.
[    0.239528] usbcore: registered new interface driver usbfs
[    0.239545] usbcore: registered new interface driver hub
[    0.239577] usbcore: registered new device driver usb
[    0.240184] ACPI: WMI: Mapper loaded
[    0.240187] PCI: Using ACPI for IRQ routing
[    0.240191] PCI: pci_cache_line_size set to 64 bytes
[    0.240376] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.240380] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff 
[    0.240509] NetLabel: Initializing
[    0.240512] NetLabel:  domain hash size = 128
[    0.240514] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.240530] NetLabel:  unlabeled traffic allowed by default
[    0.240577] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.240586] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.240593] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244038] Switching to clocksource tsc
[    0.259187] AppArmor: AppArmor Filesystem Enabled
[    0.259210] pnp: PnP ACPI init
[    0.259239] ACPI: bus type pnp registered
[    0.264675] pnp: PnP ACPI: found 10 devices
[    0.264679] ACPI: ACPI bus type pnp unregistered
[    0.264685] PnPBIOS: Disabled by ACPI PNP
[    0.264703] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.264707] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.264711] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.264715] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.264719] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.264723] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.264727] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.264738] system 00:06: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.264747] system 00:08: [io  0x0800-0x080f] has been reserved
[    0.264751] system 00:08: [io  0x1000-0x107f] has been reserved
[    0.264755] system 00:08: [io  0x1180-0x11bf] has been reserved
[    0.264759] system 00:08: [io  0xfe00] has been reserved
[    0.264763] system 00:08: [mem 0xff800000-0xff800fff] has been reserved
[    0.301465] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80000000-0x800000ff]
[    0.301476] pci 0000:00:1f.3: BAR 0: set to [mem 0x80000000-0x800000ff] (PCI address [0x80000000-0x800000ff]
[    0.301481] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.301487] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.301496] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.301504] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.301515] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.301520] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.301528] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.301535] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.301545] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.301550] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.301558] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.301565] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.301575] pci 0000:00:1e.0: PCI bridge to [bus 0f-0f]
[    0.301578] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.301586] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.301592] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.301621]   alloc irq_desc for 16 on node -1
[    0.301624]   alloc kstat_irqs on node -1
[    0.301635] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.301643] pci 0000:00:1c.0: setting latency timer to 64
[    0.301657]   alloc irq_desc for 17 on node -1
[    0.301660]   alloc kstat_irqs on node -1
[    0.301665] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.301672] pci 0000:00:1c.1: setting latency timer to 64
[    0.301686]   alloc irq_desc for 18 on node -1
[    0.301688]   alloc kstat_irqs on node -1
[    0.301693] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.301700] pci 0000:00:1c.2: setting latency timer to 64
[    0.301712] pci 0000:00:1e.0: setting latency timer to 64
[    0.301718] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.301721] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.301725] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.301728] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.301731] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.301735] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.301738] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.301741] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.301745] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.301748] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.301751] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.301754] pci_bus 0000:0f: resource 4 [io  0x0000-0xffff]
[    0.301757] pci_bus 0000:0f: resource 5 [mem 0x00000000-0xffffffff]
[    0.301816] NET: Registered protocol family 2
[    0.301916] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.302270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.302965] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.303371] TCP: Hash tables configured (established 131072 bind 65536)
[    0.303374] TCP reno registered
[    0.303381] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.303402] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.303543] NET: Registered protocol family 1
[    0.303570] pci 0000:00:02.0: Boot video device
[    0.303828] PCI: CLS 64 bytes, default 64
[    0.303874] Simple Boot Flag at 0x36 set to 0x1
[    0.304118] cpufreq-nforce2: No nForce2 chipset.
[    0.304157] Scanning for low memory corruption every 60 seconds
[    0.304305] audit: initializing netlink socket (disabled)
[    0.304320] type=2000 audit(1291388705.300:1): initialized
[    0.318249] highmem bounce pool size: 64 pages
[    0.318257] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.320352] VFS: Disk quotas dquot_6.5.2
[    0.320442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.321273] fuse init (API version 7.14)
[    0.321406] msgmni has been set to 1683
[    0.321922] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.321926] io scheduler noop registered
[    0.321929] io scheduler deadline registered
[    0.321947] io scheduler cfq registered (default)
[    0.322105] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.322171]   alloc irq_desc for 40 on node -1
[    0.322174]   alloc kstat_irqs on node -1
[    0.322191] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.322327] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.322386]   alloc irq_desc for 41 on node -1
[    0.322389]   alloc kstat_irqs on node -1
[    0.322401] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.322535] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.322593]   alloc irq_desc for 42 on node -1
[    0.322596]   alloc kstat_irqs on node -1
[    0.322607] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.322760] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.322891] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.323026] intel_idle: MWAIT substates: 0x1110
[    0.323029] intel_idle: does not run on family 6 model 15
[    0.324314] ACPI: AC Adapter [ADP1] (on-line)
[    0.324407] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.325420] ACPI: Lid Switch [LID0]
[    0.325492] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.325499] ACPI: Sleep Button [SLPB]
[    0.325579] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.325583] ACPI: Power Button [PWRF]
[    0.325949] ACPI: acpi_idle registered with cpuidle
[    0.329783] Monitor-Mwait will be used to enter C-1 state
[    0.339784] Monitor-Mwait will be used to enter C-2 state
[    0.339801] Marking TSC unstable due to TSC halts in idle
[    0.343403] Switching to clocksource hpet
[    0.363024] thermal LNXTHERM:01: registered as thermal_zone0
[    0.363039] ACPI: Thermal Zone [TZS0] (56 C)
[    0.370026] thermal LNXTHERM:02: registered as thermal_zone1
[    0.370039] ACPI: Thermal Zone [TZS1] (54 C)
[    0.370179] ERST: Table is not found!
[    0.370588] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.372675] brd: module loaded
[    0.373465] loop: module loaded
[    0.373748] ata_piix 0000:00:1f.1: version 2.13
[    0.373769]   alloc irq_desc for 19 on node -1
[    0.373772]   alloc kstat_irqs on node -1
[    0.373783] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.373846] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.373959] scsi0 : ata_piix
[    0.374074] scsi1 : ata_piix
[    0.374963] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.374968] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.375425] Fixed MDIO Bus: probed
[    0.375471] PPP generic driver version 2.4.2
[    0.375538] tun: Universal TUN/TAP device driver, 1.6
[    0.375541] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.375666] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.375698]   alloc irq_desc for 20 on node -1
[    0.375701]   alloc kstat_irqs on node -1
[    0.375709] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.375735] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.375740] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.375787] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.375823] ehci_hcd 0000:00:1a.7: debug port 1
[    0.379715] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.379742] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc404800
[    0.383833] isapnp: Scanning for PnP cards...
[    0.433259] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.433483] hub 1-0:1.0: USB hub found
[    0.433490] hub 1-0:1.0: 4 ports detected
[    0.433609]   alloc irq_desc for 23 on node -1
[    0.433612]   alloc kstat_irqs on node -1
[    0.433621] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.433654] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.433659] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.433719] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.433761] ehci_hcd 0000:00:1d.7: debug port 1
[    0.437666] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.437698] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    0.485355] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.485575] hub 2-0:1.0: USB hub found
[    0.485583] hub 2-0:1.0: 6 ports detected
[    0.485703] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.485727] uhci_hcd: USB Universal Host Controller Interface driver
[    0.485784] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.485796] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.485801] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.485856] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.485894] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
[    0.486066] hub 3-0:1.0: USB hub found
[    0.486072] hub 3-0:1.0: 2 ports detected
[    0.486158]   alloc irq_desc for 21 on node -1
[    0.486162]   alloc kstat_irqs on node -1
[    0.486171] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.486180] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.486185] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.486233] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.486280] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.486443] hub 4-0:1.0: USB hub found
[    0.486449] hub 4-0:1.0: 2 ports detected
[    0.486540] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.486549] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.486554] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.486598] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.486631] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.486792] hub 5-0:1.0: USB hub found
[    0.486798] hub 5-0:1.0: 2 ports detected
[    0.486881] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.486890] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.486895] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.486947] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.486992] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    0.487145] hub 6-0:1.0: USB hub found
[    0.487151] hub 6-0:1.0: 2 ports detected
[    0.487234] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.487243] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.487247] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.487299] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.487346] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.487506] hub 7-0:1.0: USB hub found
[    0.487511] hub 7-0:1.0: 2 ports detected
[    0.487686] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.501489] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.508769] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.508783] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.508844] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.508881] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.508913] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.509104] mice: PS/2 mouse device common for all mice
[    0.509378] rtc_cmos 00:09: RTC can wake from S4
[    0.509439] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.509479] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.509636] device-mapper: uevent: version 1.0.3
[    0.511325] Freeing initrd memory: 10520k freed
[    0.519070] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.519197] device-mapper: multipath: version 1.1.1 loaded
[    0.519201] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.519378] EISA: Probing bus 0 at eisa.0
[    0.519388] Cannot allocate resource for EISA slot 1
[    0.519393] Cannot allocate resource for EISA slot 2
[    0.519396] Cannot allocate resource for EISA slot 3
[    0.519399] Cannot allocate resource for EISA slot 4
[    0.519421] EISA: Detected 0 cards.
[    0.519590] cpuidle: using governor ladder
[    0.519702] cpuidle: using governor menu
[    0.520198] TCP cubic registered
[    0.520384] NET: Registered protocol family 10
[    0.520891] lo: Disabled Privacy Extensions
[    0.521220] NET: Registered protocol family 17
[    0.522036] Using IPI No-Shortcut mode
[    0.522152] PM: Resume from disk failed.
[    0.522169] registered taskstats version 1
[    0.522578]   Magic number: 6:365:82
[    0.522694] rtc_cmos 00:09: setting system clock to 2010-12-03 15:05:06 UTC (1291388706)
[    0.522699] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.522701] EDD information not available.
[    0.570616] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.613430] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[    0.629327] ata1.00: configured for UDMA/33
[    0.765035] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.782444] isapnp: No Plug & Play device found
[    0.831040] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    0.842110] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.842114] Uniform CD-ROM driver Revision: 3.20
[    0.842253] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.842336] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.842421] Freeing unused kernel memory: 684k freed
[    0.842915] Write protecting the kernel text: 4932k
[    0.842986] Write protecting the kernel read-only data: 1976k
[    0.868124] udev[85]: starting version 163
[    1.008639] ahci 0000:00:1f.2: version 3.0
[    1.008666] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.008730]   alloc irq_desc for 43 on node -1
[    1.008733]   alloc kstat_irqs on node -1
[    1.008748] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.008850] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.008854] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.008862] ahci 0000:00:1f.2: setting latency timer to 64
[    1.036169] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.047617] ACPI: Battery Slot [BAT0] (battery present)
[    1.060128] tg3.c:v3.110 (April 9, 2010)
[    1.060197] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.060210] tg3 0000:02:00.0: setting latency timer to 64
[    1.081162] scsi2 : ahci
[    1.087241] Initializing USB Mass Storage driver...
[    1.087340] scsi3 : ahci
[    1.096009] scsi5 : ahci
[    1.096253] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 43
[    1.096259] ata4: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 43
[    1.096264] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 43
[    1.096381] scsi4 : usb-storage 1-1:1.0
[    1.096483] usbcore: registered new interface driver usb-storage
[    1.096486] USB Mass Storage support registered.
[    1.120284] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1d:72:12:bd:6c
[    1.120291] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.120295] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.120299] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.416069] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.416073] ata5: SATA link down (SStatus 0 SControl 300)
[    1.416105] ata4: SATA link down (SStatus 0 SControl 300)
[    1.417128] ata3.00: unexpected _GTF length (8)
[    1.417505] ata3.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC31P, max UDMA/133
[    1.417510] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.418735] ata3.00: unexpected _GTF length (8)
[    1.419118] ata3.00: configured for UDMA/133
[    1.432220] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
[    1.432453] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.432489] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.432578] sd 2:0:0:0: [sda] Write Protect is off
[    1.432583] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.432616] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.432989]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.494308] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.620046] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    2.102606] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.103310] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.105578] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.520594] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.344713] udev[395]: starting version 163
[   15.389061] lp: driver loaded but no devices found
[   15.444898] Adding 1195004k swap on /dev/sda7.  Priority:-1 extents:1 across:1195004k 
[   15.633590] Linux agpgart interface v0.103
[   15.681125] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   15.681871] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   15.779256] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   15.801699] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   15.810164] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.859121] Linux video capture interface: v2.00
[   15.865245] ieee80211_crypt: registered algorithm 'NULL'
[   15.865250] ieee80211_crypt: registered algorithm 'TKIP'
[   15.865254] ieee80211_crypt: registered algorithm 'CCMP'
[   15.865257] ieee80211_crypt: registered algorithm 'WEP'
[   15.865259] 
[   15.865260] Linux kernel driver for RTL8192 based WLAN cards
[   15.865262] Copyright (c) 2007-2008, Realsil Wlan
[   15.866172] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0102)
[   15.903303] acer-wmi: Acer Laptop ACPI-WMI Extras
[   15.907041] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[   15.907045] ==>RtInPipes:3  
[   15.907049] ==>RtOutPipes:4  6  13  
[   15.907054] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   15.907057] 1  1  0  0  2  2  2  2  2  
[   15.923229] acer-wmi: Brightness must be controlled by generic video driver
[   15.940713] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input4
[   15.940807] usbcore: registered new interface driver uvcvideo
[   15.940810] USB Video Class driver (v0.1.0)
[   15.945786] type=1400 audit(1291381521.921:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=675 comm="apparmor_parser"
[   15.946706] type=1400 audit(1291381521.921:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=675 comm="apparmor_parser"
[   15.947208] type=1400 audit(1291381521.921:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=675 comm="apparmor_parser"
[   15.957721] [drm] Initialized drm 1.1.0 20060810
[   16.041731] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.041739] i915 0000:00:02.0: setting latency timer to 64
[   16.066880]   alloc irq_desc for 44 on node -1
[   16.066886]   alloc kstat_irqs on node -1
[   16.066899] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   16.066916] [drm] set up 7M of stolen space
[   16.173618] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.173949] [drm] initialized overlay support
[   16.263311] Dot11d_Init()
[   16.264202] usbcore: registered new interface driver rtl819xU
[   16.404372] type=1400 audit(1291381522.377:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=813 comm="apparmor_parser"
[   16.417734] type=1400 audit(1291381522.393:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=815 comm="apparmor_parser"
[   16.431178] type=1400 audit(1291381522.405:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=815 comm="apparmor_parser"
[   16.439157] type=1400 audit(1291381522.413:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=815 comm="apparmor_parser"
[   16.454168] type=1400 audit(1291381522.429:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=818 comm="apparmor_parser"
[   16.456060] type=1400 audit(1291381522.429:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=818 comm="apparmor_parser"
[   16.462624] type=1400 audit(1291381522.437:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=820 comm="apparmor_parser"
[   16.522578] udev[402]: renamed network interface wlan0 to wlan1
[   16.572283]   alloc irq_desc for 45 on node -1
[   16.572289]   alloc kstat_irqs on node -1
[   16.572311] tg3 0000:02:00.0: irq 45 for MSI/MSI-X
[   16.667168] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04711/0xa04000/0x0
[   16.720477] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[   16.743198] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.752344] Skipping EDID probe due to cached edid
[   16.848276] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.848279] 
[   16.848787] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.848789] 
[   16.858254] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.858256] 
[   16.858439] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.858441] 
[   16.858444] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.858446] 
[   16.885565] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.885569] 
[   16.885815] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.885817] 
[   16.895709] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.895712] 
[   16.895945] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.895947] 
[   16.895951] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.895952] 
[   17.044510] Console: switching to colour frame buffer device 160x50
[   17.049338] fb0: inteldrmfb frame buffer device
[   17.049340] drm: registered panic notifier
[   17.049345] Slow work thread pool: Starting up
[   17.049492] Slow work thread pool: Ready
[   17.076247] acpi device:03: registered as cooling_device2
[   17.076611] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.076692] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.076744] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.077790]   alloc irq_desc for 22 on node -1
[   17.077794]   alloc kstat_irqs on node -1
[   17.077805] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.077881]   alloc irq_desc for 46 on node -1
[   17.077883]   alloc kstat_irqs on node -1
[   17.077898] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.077942] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.136087] Skipping EDID probe due to cached edid
[   17.140016] hda_codec: ALC268: BIOS auto-probing.
[   17.933164] Skipping EDID probe due to cached edid
[   18.063296] ppdev: user-space parallel port driver
[   18.241154] Skipping EDID probe due to cached edid
[   19.313001] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   19.468063] Skipping EDID probe due to cached edid
[   19.780040] Skipping EDID probe due to cached edid
[   20.112043] Skipping EDID probe due to cached edid
[   20.424047] Skipping EDID probe due to cached edid
[   22.174686] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   28.849088] Skipping EDID probe due to cached edid
[   29.160058] Skipping EDID probe due to cached edid
[   29.472045] Skipping EDID probe due to cached edid
[   29.784059] Skipping EDID probe due to cached edid
[   30.884191] Skipping EDID probe due to cached edid
[   31.328053] Skipping EDID probe due to cached edid
[   35.866881] Skipping EDID probe due to cached edid
[  101.825653] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  101.825659] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  101.825909] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  112.737020] eth0: no IPv6 routers present
[  260.567321] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  260.567326] 
[  260.567662] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  260.567666] 
[  260.585334] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  260.585339] 
[  260.585551] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  260.585555] 
[  260.585560] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  260.585563] 
[  275.724928] tg3 0000:02:00.0: eth0: Link is down
[  299.631556] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  299.631566] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  302.362831] lo: Disabled Privacy Extensions
[  396.916158] Skipping EDID probe due to cached edid
[  397.072879] tg3 0000:02:00.0: eth0: Link is down
[  397.220134] Skipping EDID probe due to cached edid
[  398.208082] Skipping EDID probe due to cached edid
[  398.520075] Skipping EDID probe due to cached edid
[  398.832076] Skipping EDID probe due to cached edid
[  399.144077] Skipping EDID probe due to cached edid
[  404.792090] Skipping EDID probe due to cached edid
[  405.108080] Skipping EDID probe due to cached edid
[  405.424088] Skipping EDID probe due to cached edid
[  405.736078] Skipping EDID probe due to cached edid
[  406.756071] Skipping EDID probe due to cached edid
[  408.105094] Skipping EDID probe due to cached edid
[  411.656060] Skipping EDID probe due to cached edid
[  425.817198] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  425.817207] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  426.493182] lo: Disabled Privacy Extensions
[  734.876839] usb 2-5: USB disconnect, address 2
[  734.888049] rtl819xU:=============>wlan driver to be removed
[  734.888053] 
[  734.898183] rtl819xU:wlan driver removed
[  734.898186] 
[  737.537049] usb 2-5: new high speed USB device using ehci_hcd and address 3
[  737.605399] hub 2-0:1.0: unable to enumerate USB device on port 5
[  737.872093] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  738.016103] usb 7-1: not running at top speed; connect to a high speed hub
[  738.047544] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  738.047551] ==>RtInPipes:3  
[  738.047558] ==>RtOutPipes:4  6  13  
[  738.047569] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  738.047574] 1  1  0  0  2  2  2  2  2  
[  739.123110] Dot11d_Init()
[  739.154438] udev[528]: renamed network interface wlan0 to wlan1
[  739.213592] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  739.213597] 
[  739.214098] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  739.214103] 
[  739.263097] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  739.263101] 
[  739.264163] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  739.264166] 
[  739.264170] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  739.264172] 
[  739.330094] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  739.330097] 
[  739.331095] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  739.331097] 
[  739.395102] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  739.395106] 
[  739.396162] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  739.396164] 
[  739.396169] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  739.396171] 
[  758.801122] usb 7-1: USB disconnect, address 2
[  758.820069] rtl819xU:=============>wlan driver to be removed
[  758.820075] 
[  758.830259] rtl819xU:wlan driver removed
[  758.830262] 
[  766.940066] usb 2-5: new high speed USB device using ehci_hcd and address 4
[  767.076878] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  767.076884] ==>RtInPipes:3  
[  767.076892] ==>RtOutPipes:4  6  13  
[  767.076903] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  767.076908] 1  1  0  0  2  2  2  2  2  
[  767.306258] Dot11d_Init()
[  767.344088] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  767.344091] 
[  767.344254] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  767.344257] 
[  767.362276] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  767.362280] 
[  767.362558] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  767.362561] 
[  767.362566] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  767.362568] 
[  767.391907] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  767.391911] 
[  767.392529] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  767.392532] 
[  767.410262] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  767.410266] 
[  767.410499] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  767.410500] 
[  767.410504] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  767.410505] 
[  775.733039] usb 2-5: USB disconnect, address 4
[  775.744505] rtl819xU:=============>wlan driver to be removed
[  775.744509] 
[  775.755722] rtl819xU:wlan driver removed
[  775.755726] 
[  775.993065] usb 2-5: new high speed USB device using ehci_hcd and address 5
[  776.137358] usb 2-5: device descriptor read/all, error -71
[  776.198790] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[  776.198808] hub 2-0:1.0: hub_port_status failed (err = -32)
[  776.400103] hub 2-0:1.0: unable to enumerate USB device on port 5
[  787.088080] usb 2-5: new high speed USB device using ehci_hcd and address 7
[  787.223726] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  787.223733] ==>RtInPipes:3  
[  787.223741] ==>RtOutPipes:4  6  13  
[  787.223751] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  787.223757] 1  1  0  0  2  2  2  2  2  
[  787.463720] Dot11d_Init()
[  787.489261] udev[528]: renamed network interface wlan0 to wlan1
[  787.509221] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  787.509223] 
[  787.509464] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  787.509465] 
[  787.524725] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  787.524728] 
[  787.525188] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  787.525191] 
[  787.525195] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  787.525197] 
[  787.551237] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  787.551241] 
[  787.551610] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  787.551613] 
[  787.562907] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  787.562910] 
[  787.563094] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  787.563096] 
[  787.563100] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  787.563101] 
[ 1056.689573] tg3 0000:02:00.0: eth0: Link is down
[ 1072.335267] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 1072.335277] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[ 1109.724991] EXT3-fs: barriers not enabled
[ 1109.728541] kjournald starting.  Commit interval 5 seconds
[ 1109.728888] EXT3-fs (sda3): using internal journal
[ 1109.728894] EXT3-fs (sda3): mounted filesystem with ordered data mode
[ 1153.477860] tg3 0000:02:00.0: eth0: Link is down
[ 1513.128841] audit_printk_skb: 9 callbacks suppressed
[ 1513.128846] type=1400 audit(1291383018.600:15): apparmor="DENIED" operation="capable" parent=9536 profile="/sbin/dhclient3" pid=9542 comm="dhclient" capability=12  capname="net_admin"
[ 1513.209734] type=1400 audit(1291383018.680:16): apparmor="DENIED" operation="capable" parent=9536 profile="/sbin/dhclient3" pid=9542 comm="dhclient" capability=12  capname="net_admin"
[ 1595.500339] lo: Disabled Privacy Extensions
[ 1745.901728] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 1745.901739] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
uli@acer:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/driver$ 


```

I'm pretty much clueless here :(

---

### Post by reefmaker on 2010-12-14
Have you tried installing RutilT WLAN Manager?

---

