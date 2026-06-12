---
title: "Ubuntu 10.10 32 bits: trying to configure the net"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by videoclocknet on 2011-05-16
[SIZE=1]Hi![/SIZE]
        [SIZE=1]I've installed Ubuntu 10.10 32 bits today in my laptop. It works correctly  except the network.[/SIZE]
[SIZE=1]
[/SIZE]
        [SIZE=1]When I plug the ethernet wire, Ubuntu says connection established and the net appears as correct, but when I open firefox or do a ping, no site works.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]It happens the same with Wifi. I write the password, Ubuntu accepts it and it appears as connection established, but trying to connect to a host the same behaviour.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]I've tried booting from Ubuntu 11.04 32 bits live CD and it happens the same with ethernet and Wifi.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]Can you help me to get the net working?[/SIZE]
        [SIZE=1]Thanks in advance[/SIZE]
[SIZE=1]
[/SIZE]

---

### Post by josephmills on 2011-05-16
> **videoclocknet said:**
> [SIZE=1]Hi![/SIZE]
        [SIZE=1]I've installed Ubuntu 10.10 32 bits today in my laptop. It works correctly  except the network.[/SIZE]
[SIZE=1]
[/SIZE]
        [SIZE=1]When I plug the ethernet wire, Ubuntu says connection established and the net appears as correct, but when I open firefox or do a ping, no site works.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]It happens the same with Wifi. I write the password, Ubuntu accepts it and it appears as connection established, but trying to connect to a host the same behaviour.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]I've tried booting from Ubuntu 11.04 32 bits live CD and it happens the same with ethernet and Wifi.[/SIZE]
        [SIZE=1]
[/SIZE]
[SIZE=1]Can you help me to get the net working?[/SIZE]
        [SIZE=1]Thanks in advance[/SIZE]
[SIZE=1]
[/SIZE]
Hi there and welcome to Ubuntu Forums lets see a some more info about you computer please open your terminal (ctrl+alt+t) and type in ```
lspci -nn -k
``` and paste here thanks

---

### Post by videoclocknet on 2011-05-16
Thanks for your answer!

That's the output

```

casa@casa:~$ lspci -nn -k
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Acer Incorporated [ALI] Realtek ALC268 audio codec [1025:011f]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 2400 XT [1002:94c8]
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: radeon
    Kernel modules: radeon
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:011c]
    Kernel driver in use: tg3
    Kernel modules: tg3
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation PRO/Wireless 4965 AG or AGN [8086:1101]
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
    Subsystem: Acer Incorporated [ALI] Device [1025:011f]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
casa@casa:~$ 



```

---

### Post by josephmills on 2011-05-16
could we please see a ```
dmesg 
``` thanks for using code brackets:p

---

### Post by videoclocknet on 2011-05-16
Hi Joseph again.

Sorry for the time between replies (I have to boot from a different live cd in which I can use the network)

I suspect that it isn't a driver issue, because If I write an incorrect pasword to connect the wifi network, it doesn't tell me "Connection established".

I'm gonna upload the dmesg output in some minutes.

Thanks,

videoclocknet

---

### Post by videoclocknet on 2011-05-16
That's the dmesg output

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedf000 - 0000000080000000 (reserved)
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
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
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
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  modified: 000000007fed0000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  modified: 000000007fedf000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7d60] f7d60
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ac000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 013e8d7c
[    0.000000] Move RAMDISK from 00000000375ac000 - 0000000037fefd7b to 009a5000 - 013e8d7b
[    0.000000] ACPI: RSDP 000f7bf0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7fed16a0 0008C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 7fedbbd7 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fed2bda 08F89 (v02 INTEL  CRESTLNE 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fedefc0 00040
[    0.000000] ACPI: HPET 7fedbccb 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedbd03 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7fedbd3f 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 7fedbd71 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 7fedbd97 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: ASF! 7fedbf0d 00063 (v32 OEMID  OEMTBL   06040000 PTL  00000001)
[    0.000000] ACPI: APIC 7fedbf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fedbfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fed28fd 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed1cb8 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed1c12 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed172c 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c13ea200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294340 pages, LIFO batch:31
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
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519777
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=fb3702d2-f3eb-4d83-877b-c8be136fcc98 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (52 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a41d8]             BRK
[    0.000000]   #4 [00000f7d70 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7d60 - 00000f7d70]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009ff35 - 00000f7d60]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009ff35]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a5000 - 00013e9000]     NEW RAMDISK
[    0.000000]   #13 [00013e9000 - 00013ea000]         BOOTMEM
[    0.000000]   #14 [00013ea000 - 00023ea000]         BOOTMEM
[    0.000000]   #15 [00023ea000 - 00023ea004]         BOOTMEM
[    0.000000]   #16 [00023ea040 - 00023ea100]         BOOTMEM
[    0.000000]   #17 [00023ea100 - 00023ea154]         BOOTMEM
[    0.000000]   #18 [00023ea180 - 00023ed180]         BOOTMEM
[    0.000000]   #19 [00023ed180 - 00023ed1f0]         BOOTMEM
[    0.000000]   #20 [00023ed200 - 00023f3200]         BOOTMEM
[    0.000000]   #21 [00023f3200 - 00023f3225]         BOOTMEM
[    0.000000]   #22 [00023f3240 - 00023f3267]         BOOTMEM
[    0.000000]   #23 [00023f3280 - 00023f3408]         BOOTMEM
[    0.000000]   #24 [00023f3440 - 00023f3480]         BOOTMEM
[    0.000000]   #25 [00023f3480 - 00023f34c0]         BOOTMEM
[    0.000000]   #26 [00023f34c0 - 00023f3500]         BOOTMEM
[    0.000000]   #27 [00023f3500 - 00023f3540]         BOOTMEM
[    0.000000]   #28 [00023f3540 - 00023f3580]         BOOTMEM
[    0.000000]   #29 [00023f3580 - 00023f35c0]         BOOTMEM
[    0.000000]   #30 [00023f35c0 - 00023f3600]         BOOTMEM
[    0.000000]   #31 [00023f3600 - 00023f3640]         BOOTMEM
[    0.000000]   #32 [00023f3640 - 00023f3680]         BOOTMEM
[    0.000000]   #33 [00023f3680 - 00023f36c0]         BOOTMEM
[    0.000000]   #34 [00023f36c0 - 00023f3700]         BOOTMEM
[    0.000000]   #35 [00023f3700 - 00023f3740]         BOOTMEM
[    0.000000]   #36 [00023f3740 - 00023f3780]         BOOTMEM
[    0.000000]   #37 [00023f3780 - 00023f3790]         BOOTMEM
[    0.000000]   #38 [00023f37c0 - 00023f382a]         BOOTMEM
[    0.000000]   #39 [00023f3840 - 00023f38aa]         BOOTMEM
[    0.000000]   #40 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #41 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #42 [00023f58c0 - 00023f58c4]         BOOTMEM
[    0.000000]   #43 [00023f5900 - 00023f5904]         BOOTMEM
[    0.000000]   #44 [00023f5940 - 00023f5948]         BOOTMEM
[    0.000000]   #45 [00023f5980 - 00023f5988]         BOOTMEM
[    0.000000]   #46 [00023f59c0 - 00023f5a68]         BOOTMEM
[    0.000000]   #47 [00023f5a80 - 00023f5ae8]         BOOTMEM
[    0.000000]   #48 [00023f5b00 - 00023f9b00]         BOOTMEM
[    0.000000]   #49 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #50 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #51 [000260e000 - 000300c700]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2048532k/2095936k available (4928k kernel code, 46952k reserved, 2336k data, 684k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.484 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4388.96 BogoMIPS (lpj=8777936)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004027] Security Framework initialized
[    0.004042] AppArmor: AppArmor initialized
[    0.004044] Yama: becoming mindful.
[    0.004092] Mount-cache hash table entries: 512
[    0.004216] Initializing cgroup subsys ns
[    0.004220] Initializing cgroup subsys cpuacct
[    0.004225] Initializing cgroup subsys memory
[    0.004233] Initializing cgroup subsys devices
[    0.004235] Initializing cgroup subsys freezer
[    0.004237] Initializing cgroup subsys net_cls
[    0.004263] CPU: Physical Processor ID: 0
[    0.004265] CPU: Processor Core ID: 0
[    0.004267] mce: CPU supports 6 MCE banks
[    0.004275] CPU0: Thermal monitoring handled by SMI
[    0.004278] using mwait in idle threads.
[    0.004285] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004291] PEBS disabled due to CPU errata.
[    0.004297] ... version:                2
[    0.004299] ... bit width:              40
[    0.004300] ... generic registers:      2
[    0.004302] ... value mask:             000000ffffffffff
[    0.004304] ... max period:             000000007fffffff
[    0.004305] ... fixed-purpose events:   3
[    0.004307] ... event mask:             0000000700000003
[    0.008570] ACPI: Core revision 20100428
[    0.020010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020015] ftrace: allocating 21758 entries in 43 pages
[    0.024046] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024399] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064605] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[    0.068000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.156015] Brought up 2 CPUs
[    0.156018] Total of 2 processors activated (8777.93 BogoMIPS).
[    0.156676] devtmpfs: initialized
[    0.156941] regulator: core version 0.5
[    0.156975] Time: 20:51:41  Date: 05/16/11
[    0.157013] NET: Registered protocol family 16
[    0.157034] Trying to unpack rootfs image as initramfs...
[    0.157137] EISA bus registered
[    0.157145] ACPI: bus type pci registered
[    0.157220] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157224] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.157226] PCI: Using MMCONFIG for extended config space
[    0.157228] PCI: Using configuration type 1 for base access
[    0.164258] bio: create slab <bio-0> at 0
[    0.166002] ACPI: EC: Look up EC in DSDT
[    0.170249] ACPI: BIOS _OSI(Linux) query ignored
[    0.171618] ACPI: SSDT 7fed25bb 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.172161] ACPI: Dynamic OEM Table Load:
[    0.172165] ACPI: SSDT (null) 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.172482] ACPI: SSDT 7fed1f17 0061F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.172987] ACPI: Dynamic OEM Table Load:
[    0.172991] ACPI: SSDT (null) 0061F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.173410] ACPI: SSDT 7fed2835 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.173922] ACPI: Dynamic OEM Table Load:
[    0.173925] ACPI: SSDT (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.174074] ACPI: SSDT 7fed2536 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.174575] ACPI: Dynamic OEM Table Load:
[    0.174578] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.188119] ACPI: Interpreter enabled
[    0.188125] ACPI: (supports S0 S3 S4 S5)
[    0.188149] ACPI: Using IOAPIC for interrupt routing
[    0.408677] Freeing initrd memory: 10512k freed
[    0.600639] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.600973] ACPI: No dock devices found.
[    0.600979] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.601604] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.602789] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.602792] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.602795] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.602798] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.602801] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.602803] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.602807] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.602809] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.602902] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.602906] pci 0000:00:01.0: PME# disabled
[    0.602997] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.603064] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.603130] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.603196] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.603202] pci 0000:00:1a.7: PME# disabled
[    0.603249] pci 0000:00:1b.0: reg 10: [mem 0xfc400000-0xfc403fff 64bit]
[    0.603313] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.603319] pci 0000:00:1b.0: PME# disabled
[    0.603423] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.603428] pci 0000:00:1c.0: PME# disabled
[    0.603535] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.603540] pci 0000:00:1c.1: PME# disabled
[    0.603647] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.603652] pci 0000:00:1c.2: PME# disabled
[    0.603722] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.603789] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.603856] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.603922] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.603988] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.603994] pci 0000:00:1d.7: PME# disabled
[    0.604176] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.604181] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.604187] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0068 (mask 0007)
[    0.604245] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.604254] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.604262] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.604270] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.604278] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.604344] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.604352] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.604360] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.604369] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.604377] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.604385] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.604430] pci 0000:00:1f.2: PME# supported from D3hot
[    0.604435] pci 0000:00:1f.2: PME# disabled
[    0.604469] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.604495] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.604589] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.604603] pci 0000:01:00.0: reg 18: [mem 0xfc000000-0xfc00ffff 64bit]
[    0.604612] pci 0000:01:00.0: reg 20: [io  0x2000-0x20ff]
[    0.604626] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.604657] pci 0000:01:00.0: supports D1 D2
[    0.612014] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.612018] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.612021] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.612026] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.612185] pci 0000:02:00.0: reg 10: [mem 0xf6000000-0xf600ffff 64bit]
[    0.612294] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.612300] pci 0000:02:00.0: PME# disabled
[    0.620057] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.620062] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.620068] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.620076] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.620205] pci 0000:04:00.0: reg 10: [mem 0xf8000000-0xf8001fff 64bit]
[    0.620327] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.620335] pci 0000:04:00.0: PME# disabled
[    0.628023] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.628028] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.628033] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.628042] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.628106] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.628111] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.628117] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.628125] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.628209] pci 0000:0f:06.0: reg 10: [mem 0xfc100000-0xfc100fff]
[    0.628240] pci 0000:0f:06.0: supports D1 D2
[    0.628242] pci 0000:0f:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.628248] pci 0000:0f:06.0: PME# disabled
[    0.628296] pci 0000:0f:06.1: reg 10: [mem 0xfc102000-0xfc1027ff]
[    0.628306] pci 0000:0f:06.1: reg 14: [mem 0xfc104000-0xfc107fff]
[    0.628377] pci 0000:0f:06.1: supports D1 D2
[    0.628379] pci 0000:0f:06.1: PME# supported from D0 D1 D2 D3hot
[    0.628385] pci 0000:0f:06.1: PME# disabled
[    0.628432] pci 0000:0f:06.2: reg 10: [mem 0xfc101000-0xfc101fff]
[    0.628510] pci 0000:0f:06.2: supports D1 D2
[    0.628512] pci 0000:0f:06.2: PME# supported from D0 D1 D2 D3hot
[    0.628517] pci 0000:0f:06.2: PME# disabled
[    0.628564] pci 0000:0f:06.3: reg 10: [mem 0xfc102800-0xfc1028ff]
[    0.628642] pci 0000:0f:06.3: supports D1 D2
[    0.628644] pci 0000:0f:06.3: PME# supported from D0 D1 D2 D3hot
[    0.628650] pci 0000:0f:06.3: PME# disabled
[    0.628721] pci 0000:00:1e.0: PCI bridge to [bus 0f-10] (subtractive decode)
[    0.628727] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.628732] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.628741] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.628743] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.628746] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.628804] pci_bus 0000:10: [bus 10-13] partially hidden behind transparent bridge 0000:0f [bus 0f-10]
[    0.628837] pci_bus 0000:00: on NUMA node 0
[    0.628841] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.629063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.629162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.629249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.629336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.629466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    4.228481] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    4.228585] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    4.228687] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    4.228787] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[    4.228888] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    4.228988] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 *11)
[    4.229088] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    4.229188] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    4.229234] HEST: Table is not found!
[    4.229337] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    4.229343] vgaarb: loaded
[    4.229512] SCSI subsystem initialized
[    4.229523] libata version 3.00 loaded.
[    4.229523] usbcore: registered new interface driver usbfs
[    4.229523] usbcore: registered new interface driver hub
[    4.229523] usbcore: registered new device driver usb
[    4.229523] ACPI: WMI: Mapper loaded
[    4.229523] PCI: Using ACPI for IRQ routing
[    4.229523] PCI: pci_cache_line_size set to 64 bytes
[    4.229523] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    4.229523] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    4.229523] NetLabel: Initializing
[    4.229523] NetLabel:  domain hash size = 128
[    4.229523] NetLabel:  protocols = UNLABELED CIPSOv4
[    4.229523] NetLabel:  unlabeled traffic allowed by default
[    4.229523] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    4.229523] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    4.229523] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    4.236022] Switching to clocksource tsc
[    4.246946] AppArmor: AppArmor Filesystem Enabled
[    4.246961] pnp: PnP ACPI init
[    4.246979] ACPI: bus type pnp registered
[    4.448045] pnp: PnP ACPI: found 11 devices
[    4.448048] ACPI: ACPI bus type pnp unregistered
[    4.448052] PnPBIOS: Disabled by ACPI PNP
[    4.448065] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    4.448068] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    4.448071] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    4.448074] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    4.448077] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    4.448080] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    4.448083] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    4.448091] system 00:06: [mem 0xfed00000-0xfed003ff] has been reserved
[    4.448097] system 00:08: [io  0x0800-0x080f] has been reserved
[    4.448100] system 00:08: [io  0x1000-0x107f] has been reserved
[    4.448103] system 00:08: [io  0x1180-0x11bf] has been reserved
[    4.448106] system 00:08: [io  0xfe00] has been reserved
[    4.448109] system 00:08: [mem 0xff800000-0xff800fff] has been reserved
[    4.484164] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    4.484168] pci 0000:00:1e.0: BAR 13: assigned [io  0x6000-0x6fff]
[    4.484171] pci 0000:00:1f.3: BAR 0: assigned [mem 0x84000000-0x840000ff]
[    4.484178] pci 0000:00:1f.3: BAR 0: set to [mem 0x84000000-0x840000ff] (PCI address [0x84000000-0x840000ff]
[    4.484182] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc020000-0xfc03ffff pref]
[    4.484185] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    4.484188] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    4.484192] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfc0fffff]
[    4.484196] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    4.484201] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    4.484205] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    4.484211] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    4.484217] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    4.484225] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    4.484228] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    4.484235] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    4.484240] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    4.484249] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    4.484252] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    4.484259] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    4.484264] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    4.484274] pci 0000:0f:06.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    4.484277] pci 0000:0f:06.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    4.484279] pci 0000:0f:06.0: BAR 13: assigned [io  0x6000-0x60ff]
[    4.484282] pci 0000:0f:06.0: BAR 14: assigned [io  0x6400-0x64ff]
[    4.484285] pci 0000:0f:06.0: CardBus bridge to [bus 10-13]
[    4.484287] pci 0000:0f:06.0:   bridge window [io  0x6000-0x60ff]
[    4.484293] pci 0000:0f:06.0:   bridge window [io  0x6400-0x64ff]
[    4.484299] pci 0000:0f:06.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    4.484306] pci 0000:0f:06.0:   bridge window [mem 0x88000000-0x8bffffff]
[    4.484312] pci 0000:00:1e.0: PCI bridge to [bus 0f-10]
[    4.484316] pci 0000:00:1e.0:   bridge window [io  0x6000-0x6fff]
[    4.484323] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    4.484328] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    4.484343]   alloc irq_desc for 16 on node -1
[    4.484345]   alloc kstat_irqs on node -1
[    4.484351] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.484355] pci 0000:00:01.0: setting latency timer to 64
[    4.484366] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.484371] pci 0000:00:1c.0: setting latency timer to 64
[    4.484383]   alloc irq_desc for 17 on node -1
[    4.484384]   alloc kstat_irqs on node -1
[    4.484388] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.484394] pci 0000:00:1c.1: setting latency timer to 64
[    4.484405]   alloc irq_desc for 18 on node -1
[    4.484406]   alloc kstat_irqs on node -1
[    4.484410] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.484415] pci 0000:00:1c.2: setting latency timer to 64
[    4.484425] pci 0000:00:1e.0: setting latency timer to 64
[    4.484438]   alloc irq_desc for 22 on node -1
[    4.484440]   alloc kstat_irqs on node -1
[    4.484444] pci 0000:0f:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.484451] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    4.484453] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    4.484456] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    4.484458] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfc0fffff]
[    4.484461] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    4.484463] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    4.484466] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    4.484468] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    4.484471] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    4.484473] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    4.484475] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    4.484478] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    4.484480] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    4.484483] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    4.484485] pci_bus 0000:0f: resource 0 [io  0x6000-0x6fff]
[    4.484487] pci_bus 0000:0f: resource 1 [mem 0xfc100000-0xfc1fffff]
[    4.484490] pci_bus 0000:0f: resource 2 [mem 0x80000000-0x83ffffff pref]
[    4.484492] pci_bus 0000:0f: resource 4 [io  0x0000-0xffff]
[    4.484494] pci_bus 0000:0f: resource 5 [mem 0x00000000-0xffffffff]
[    4.484497] pci_bus 0000:10: resource 0 [io  0x6000-0x60ff]
[    4.484499] pci_bus 0000:10: resource 1 [io  0x6400-0x64ff]
[    4.484501] pci_bus 0000:10: resource 2 [mem 0x80000000-0x83ffffff pref]
[    4.484504] pci_bus 0000:10: resource 3 [mem 0x88000000-0x8bffffff]
[    4.484539] NET: Registered protocol family 2
[    4.484604] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.484877] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.485346] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.485553] TCP: Hash tables configured (established 131072 bind 65536)
[    4.485555] TCP reno registered
[    4.485558] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    4.485567] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    4.485637] NET: Registered protocol family 1
[    4.485812] pci 0000:01:00.0: Boot video device
[    4.485876] PCI: CLS 64 bytes, default 64
[    4.485899] Simple Boot Flag at 0x36 set to 0x1
[    4.486074] cpufreq-nforce2: No nForce2 chipset.
[    4.486101] Scanning for low memory corruption every 60 seconds
[    4.486205] audit: initializing netlink socket (disabled)
[    4.486214] type=2000 audit(1305579105.484:1): initialized
[    4.496345] highmem bounce pool size: 64 pages
[    4.496350] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.497829] VFS: Disk quotas dquot_6.5.2
[    4.497893] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.498474] fuse init (API version 7.14)
[    4.498565] msgmni has been set to 1703
[    4.501038] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.501042] io scheduler noop registered
[    4.501044] io scheduler deadline registered
[    4.501057] io scheduler cfq registered (default)
[    4.501174] pcieport 0000:00:01.0: setting latency timer to 64
[    4.501202]   alloc irq_desc for 40 on node -1
[    4.501204]   alloc kstat_irqs on node -1
[    4.501213] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    4.501291] pcieport 0000:00:1c.0: setting latency timer to 64
[    4.501339]   alloc irq_desc for 41 on node -1
[    4.501341]   alloc kstat_irqs on node -1
[    4.501350] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    4.501453] pcieport 0000:00:1c.1: setting latency timer to 64
[    4.501502]   alloc irq_desc for 42 on node -1
[    4.501504]   alloc kstat_irqs on node -1
[    4.501513] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    4.501617] pcieport 0000:00:1c.2: setting latency timer to 64
[    4.501665]   alloc irq_desc for 43 on node -1
[    4.501667]   alloc kstat_irqs on node -1
[    4.501676] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    4.501796] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.501912] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.502010] intel_idle: MWAIT substates: 0x22220
[    4.502012] intel_idle: does not run on family 6 model 15
[    4.502840] ACPI: AC Adapter [ADP1] (on-line)
[    4.502903] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    4.504500] ACPI: Lid Switch [LID0]
[    4.504545] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    4.504550] ACPI: Sleep Button [SLPB]
[    4.504610] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.504614] ACPI: Power Button [PWRF]
[    4.504876] ACPI: acpi_idle registered with cpuidle
[    4.507491] Monitor-Mwait will be used to enter C-1 state
[    4.507512] Monitor-Mwait will be used to enter C-2 state
[    4.507530] Monitor-Mwait will be used to enter C-3 state
[    4.507535] Marking TSC unstable due to TSC halts in idle
[    4.507569] Switching to clocksource hpet
[    5.723075] thermal LNXTHERM:01: registered as thermal_zone0
[    5.723084] ACPI: Thermal Zone [TZS0] (56 C)
[    5.727871] thermal LNXTHERM:02: registered as thermal_zone1
[    5.727878] ACPI: Thermal Zone [TZS1] (60 C)
[    5.727962] ERST: Table is not found!
[    5.727998] isapnp: Scanning for PnP cards...
[    5.736576] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    5.738229] brd: module loaded
[    5.738765] loop: module loaded
[    5.738947] ata_piix 0000:00:1f.1: version 2.13
[    5.738958]   alloc irq_desc for 19 on node -1
[    5.738960]   alloc kstat_irqs on node -1
[    5.738966] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.739004] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.739077] scsi0 : ata_piix
[    5.739147] scsi1 : ata_piix
[    5.739810] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    5.739813] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    5.740139] Fixed MDIO Bus: probed
[    5.740174] PPP generic driver version 2.4.2
[    5.740211] tun: Universal TUN/TAP device driver, 1.6
[    5.740213] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.740286] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.740303]   alloc irq_desc for 20 on node -1
[    5.740305]   alloc kstat_irqs on node -1
[    5.740310] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    5.740320] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.740325] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.740360] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.740391] ehci_hcd 0000:00:1a.7: debug port 1
[    5.744266] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    5.744282] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc404800
[    5.761015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.761160] hub 1-0:1.0: USB hub found
[    5.761165] hub 1-0:1.0: 4 ports detected
[    5.761246]   alloc irq_desc for 23 on node -1
[    5.761248]   alloc kstat_irqs on node -1
[    5.761253] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.761263] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.761267] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.761303] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.761332] ehci_hcd 0000:00:1d.7: debug port 1
[    5.765205] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    5.765220] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    5.781013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.781116] hub 2-0:1.0: USB hub found
[    5.781121] hub 2-0:1.0: 6 ports detected
[    5.781197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.781212] uhci_hcd: USB Universal Host Controller Interface driver
[    5.781229] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.781236] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.781240] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.781273] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.781332] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001800
[    5.781446] hub 3-0:1.0: USB hub found
[    5.781450] hub 3-0:1.0: 2 ports detected
[    5.781516]   alloc irq_desc for 21 on node -1
[    5.781518]   alloc kstat_irqs on node -1
[    5.781522] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.781529] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.781532] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.781563] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.781602] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    5.781760] hub 4-0:1.0: USB hub found
[    5.781764] hub 4-0:1.0: 2 ports detected
[    5.781830] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.781836] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.781840] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.781877] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.781903] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    5.782017] hub 5-0:1.0: USB hub found
[    5.782020] hub 5-0:1.0: 2 ports detected
[    5.782085] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.782092] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.782095] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.782130] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.782166] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001860
[    5.782278] hub 6-0:1.0: USB hub found
[    5.782282] hub 6-0:1.0: 2 ports detected
[    5.782374] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.782381] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.782385] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.782415] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.782453] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    5.782567] hub 7-0:1.0: USB hub found
[    5.782571] hub 7-0:1.0: 2 ports detected
[    5.782705] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.794424] i8042.c: Detected active multiplexing controller, rev 1.1.
[    5.801933] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.801946] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.801973] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.801996] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.802018] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.802112] mice: PS/2 mouse device common for all mice
[    5.802514] rtc_cmos 00:09: RTC can wake from S4
[    5.802558] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    5.802590] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    5.802682] device-mapper: uevent: version 1.0.3
[    5.802775] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    5.802834] device-mapper: multipath: version 1.1.1 loaded
[    5.802837] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.802939] EISA: Probing bus 0 at eisa.0
[    5.802946] Cannot allocate resource for EISA slot 1
[    5.802948] Cannot allocate resource for EISA slot 2
[    5.802950] Cannot allocate resource for EISA slot 3
[    5.802952] Cannot allocate resource for EISA slot 4
[    5.802955] Cannot allocate resource for EISA slot 5
[    5.802957] Cannot allocate resource for EISA slot 6
[    5.802967] EISA: Detected 0 cards.
[    5.803120] cpuidle: using governor ladder
[    5.803222] cpuidle: using governor menu
[    5.803529] TCP cubic registered
[    5.803655] NET: Registered protocol family 10
[    5.804015] lo: Disabled Privacy Extensions
[    5.804258] NET: Registered protocol family 17
[    5.804869] Using IPI No-Shortcut mode
[    5.804944] PM: Resume from disk failed.
[    5.804958] registered taskstats version 1
[    5.805392]   Magic number: 11:656:902
[    5.805468] rtc_cmos 00:09: setting system clock to 2011-05-16 20:51:47 UTC (1305579107)
[    5.805471] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.805473] EDD information not available.
[    5.828285] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.916661] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[    5.933273] ata1.00: configured for UDMA/33
[    6.083421] isapnp: No Plug & Play device found
[    6.087126] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.088706] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    6.099857] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.099861] Uniform CD-ROM driver Revision: 3.20
[    6.100011] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.100082] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.100173] Freeing unused kernel memory: 684k freed
[    6.100555] Write protecting the kernel text: 4932k
[    6.100601] Write protecting the kernel read-only data: 1976k
[    6.116671] udev[87]: starting version 163
[    6.195797] tg3.c:v3.110 (April 9, 2010)
[    6.195858] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.195869] tg3 0000:02:00.0: setting latency timer to 64
[    6.208968] sdhci: Secure Digital Host Controller Interface driver
[    6.208971] sdhci: Copyright(c) Pierre Ossman
[    6.210459] sdhci-pci 0000:0f:06.3: SDHCI controller found [104c:803c] (rev 0)
[    6.210478] sdhci-pci 0000:0f:06.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.210544] Registered led device: mmc0::
[    6.212142] mmc0: SDHCI controller on PCI [0000:0f:06.3] using PIO
[    6.224560] ahci 0000:00:1f.2: version 3.0
[    6.224578] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.224626]   alloc irq_desc for 44 on node -1
[    6.224628]   alloc kstat_irqs on node -1
[    6.224640] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    6.224713] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    6.224717] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ccc 
[    6.224723] ahci 0000:00:1f.2: setting latency timer to 64
[    6.225118] firewire_ohci 0000:0f:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.238732] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1d:72:05:1a:c9
[    6.238736] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    6.238739] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    6.238742] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    6.245869] scsi2 : ahci
[    6.264036] ACPI: Battery Slot [BAT0] (battery present)
[    6.270182] scsi3 : ahci
[    6.279737] scsi4 : ahci
[    6.279983] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 44
[    6.279987] ata4: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 44
[    6.279991] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 44
[    6.281071] firewire_ohci: Added fw-ohci device 0000:0f:06.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    6.600116] ata5: SATA link down (SStatus 0 SControl 300)
[    6.780247] firewire_core: created device fw0: GUID 000ae4074161e9f7, S400
[    6.824119] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.824153] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.825465] ata3.00: unexpected _GTF length (8)
[    6.825484] ata4.00: unexpected _GTF length (8)
[    6.825825] ata3.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    6.825831] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.825837] ata4.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    6.825844] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.827368] ata3.00: unexpected _GTF length (8)
[    6.827388] ata4.00: unexpected _GTF length (8)
[    6.827759] ata3.00: configured for UDMA/100
[    6.827766] ata4.00: configured for UDMA/100
[    6.827953] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    6.828100] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.828247] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    6.828359] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    6.828371] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    6.828416] sd 3:0:0:0: [sdb] Write Protect is off
[    6.828419] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.828421] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    6.828447] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.828479] sd 2:0:0:0: [sda] Write Protect is off
[    6.828482] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.828505] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.828652]  sda:
[    6.828762]  sdb: sdb1 < sdb5 >
[    7.245150] sd 3:0:0:0: [sdb] Attached SCSI disk
[    7.247053]  sda1 sda2
[    7.256044] sd 2:0:0:0: [sda] Attached SCSI disk
[    7.587451] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   17.563265] udev[379]: starting version 163
[   17.592190] lp: driver loaded but no devices found
[   17.657160] Adding 3417084k swap on /dev/sda1.  Priority:-1 extents:1 across:3417084k 
[   17.743562] acpi device:03: registered as cooling_device2
[   17.743878] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   17.743957] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.797047] Linux agpgart interface v0.103
[   17.888093] acer-wmi: Acer Laptop ACPI-WMI Extras
[   17.909194] irda_init()
[   17.909207] NET: Registered protocol family 23
[   17.912712] yenta_cardbus 0000:0f:06.0: CardBus bridge found [1025:011f]
[   17.912737] yenta_cardbus 0000:0f:06.0: Using CSCINT to route CSC interrupts to PCI
[   17.912740] yenta_cardbus 0000:0f:06.0: Routing CardBus interrupts to PCI
[   17.912747] yenta_cardbus 0000:0f:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   17.912994] Linux video capture interface: v2.00
[   17.916512] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   17.925087] cfg80211: Calling CRDA to update world regulatory domain
[   17.926121] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input5
[   17.926455] usbcore: registered new interface driver uvcvideo
[   17.926458] USB Video Class driver (v0.1.0)
[   17.946252] type=1400 audit(1305579119.635:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=682 comm="apparmor_parser"
[   17.946920] type=1400 audit(1305579119.635:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=682 comm="apparmor_parser"
[   17.948433] type=1400 audit(1305579119.635:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=682 comm="apparmor_parser"
[   17.951178] [drm] Initialized drm 1.1.0 20060810
[   17.955539] acer-wmi: Brightness must be controlled by generic video driver
[   17.956075] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   17.961346] cfg80211: World regulatory domain updated:
[   17.961349]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.961352]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961355]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.961358]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.961360]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961363]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.991616] nsc-ircc 00:0a: activated
[   17.991621] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   17.991666] nsc-ircc, chip->init
[   17.991680] nsc-ircc, Found chip at base=0x02e
[   17.991721] nsc-ircc, driver loaded (Dag Brattli)
[   17.992306] IrDA: Registered device irda0
[   17.992369] nsc-ircc, Found dongle: Supports SIR Mode only
[   17.992426] nsc-ircc, chip->init
[   17.992440] nsc-ircc, Found chip at base=0x02e
[   17.992479] nsc-ircc, driver loaded (Dag Brattli)
[   17.992483] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.057187] [drm] radeon defaulting to kernel modesetting.
[   18.057190] [drm] radeon kernel modesetting enabled.
[   18.057256] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.057263] radeon 0000:01:00.0: setting latency timer to 64
[   18.058799] [drm] initializing kernel modesetting (RV610 0x1002:0x94C8).
[   18.061124] [drm] register mmio base: 0xFC000000
[   18.061126] [drm] register mmio size: 65536
[   18.061273] ATOM BIOS: Wistron/Acer
[   18.061286] [drm] Clocks initialized !
[   18.061297] radeon 0000:01:00.0: VRAM: 256M 0x00000000 - 0x0FFFFFFF (256M used)
[   18.061300] radeon 0000:01:00.0: GTT: 512M 0x10000000 - 0x2FFFFFFF
[   18.062342] [drm] Detected VRAM RAM=256M, BAR=256M
[   18.062346] [drm] RAM width 64bits DDR
[   18.062428] [TTM] Zone  kernel: Available graphics memory: 436548 kiB.
[   18.062430] [TTM] Zone highmem: Available graphics memory: 1029864 kiB.
[   18.062433] [TTM] Initializing pool allocator.
[   18.062452] [drm] radeon: 256M of VRAM memory ready
[   18.062454] [drm] radeon: 512M of GTT memory ready.
[   18.062521]   alloc irq_desc for 45 on node -1
[   18.062524]   alloc kstat_irqs on node -1
[   18.062537] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.062545] radeon 0000:01:00.0: radeon: using MSI.
[   18.062583] [drm] radeon: irq initialized.
[   18.062586] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   18.063036] [drm] Loading RV610 Microcode
[   18.073347] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   18.073350] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   18.073413] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.073423] iwlagn 0000:04:00.0: setting latency timer to 64
[   18.073455] iwlagn 0000:04:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   18.133926] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   18.134072]   alloc irq_desc for 46 on node -1
[   18.134074]   alloc kstat_irqs on node -1
[   18.134129] iwlagn 0000:04:00.0: irq 46 for MSI/MSI-X
[   18.144873] yenta_cardbus 0000:0f:06.0: ISA IRQ mask 0x0cf0, PCI irq 22
[   18.144880] yenta_cardbus 0000:0f:06.0: Socket status: 30000006
[   18.144884] pci_bus 0000:0f: Raising subordinate bus# of parent bus (#0f) from #10 to #13
[   18.144895] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [io  0x6000-0x6fff]
[   18.144898] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff: excluding 0x6000-0x60ff 0x6400-0x64ff
[   18.152468] iwlagn 0000:04:00.0: loaded firmware version 228.61.2.24
[   18.154922] 
[   18.154927] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [mem 0xfc100000-0xfc1fffff]
[   18.154931] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc100000-0xfc1fffff: excluding 0xfc100000-0xfc10ffff
[   18.154947] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   18.154950] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   18.160057] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.160148]   alloc irq_desc for 47 on node -1
[   18.160150]   alloc kstat_irqs on node -1
[   18.160172] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   18.160236] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.160636] [drm] ring test succeeded in 0 usecs
[   18.160828] [drm] radeon: ib pool ready.
[   18.160908] [drm] ib test succeeded in 0 usecs
[   18.160910] [drm] Enabling audio support
[   18.161710] [drm] Default TV standard: NTSC
[   18.161714] [drm] Default TV standard: NTSC
[   18.161856] [drm] Default TV standard: NTSC
[   18.163133] [drm] Radeon Display Connectors
[   18.163135] [drm] Connector 0:
[   18.163137] [drm]   LVDS
[   18.163140] [drm]   DDC: 0xac0 0xac0 0xac4 0xac4 0xac8 0xac8 0xacc 0xacc
[   18.163141] [drm]   Encoders:
[   18.163143] [drm]     LCD1: INTERNAL_LVTM1
[   18.163145] [drm] Connector 1:
[   18.163146] [drm]   DIN
[   18.163147] [drm]   Encoders:
[   18.163149] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   18.163151] [drm] Connector 2:
[   18.163152] [drm]   VGA
[   18.163154] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   18.163156] [drm]   Encoders:
[   18.163158] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   18.163159] [drm] Connector 3:
[   18.163161] [drm]   DVI-I
[   18.163162] [drm]   HPD1
[   18.163165] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   18.163166] [drm]   Encoders:
[   18.163168] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   18.179389] tifm_7xx1 0000:0f:06.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.189012] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.219365] hda_codec: ALC268: BIOS auto-probing.
[   18.228692] [drm] Internal thermal controller without fan control
[   18.228732] [drm] radeon: power management initialized
[   18.298512] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   18.300791] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   18.301774] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.302575] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.303454] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   18.303508] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   18.303562] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   18.303616] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.405986] type=1400 audit(1305579120.095:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=920 comm="apparmor_parser"
[   18.406023] type=1400 audit(1305579120.095:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=921 comm="apparmor_parser"
[   18.406730] type=1400 audit(1305579120.095:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=921 comm="apparmor_parser"
[   18.407096] type=1400 audit(1305579120.095:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=921 comm="apparmor_parser"
[   18.409543] type=1400 audit(1305579120.099:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=922 comm="apparmor_parser"
[   18.410007] type=1400 audit(1305579120.099:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=924 comm="apparmor_parser"
[   18.410829] type=1400 audit(1305579120.099:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=924 comm="apparmor_parser"
[   18.571747]   alloc irq_desc for 48 on node -1
[   18.571750]   alloc kstat_irqs on node -1
[   18.571767] tg3 0000:02:00.0: irq 48 for MSI/MSI-X
[   18.605949] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.723062] [drm] fb mappable at 0xD0141000
[   18.723065] [drm] vram apper at 0xD0000000
[   18.723067] [drm] size 5300224
[   18.723069] [drm] fb depth is 24
[   18.723071] [drm]    pitch is 5888
[   18.737220] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04713/0x204000/0x0
[   18.791727] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   18.874568] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.140429] Console: switching to colour frame buffer device 180x56
[   19.144552] fb0: radeondrmfb frame buffer device
[   19.144553] drm: registered panic notifier
[   19.144556] Slow work thread pool: Starting up
[   19.144601] Slow work thread pool: Ready
[   19.144607] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   19.255500] ppdev: user-space parallel port driver
[   20.250165] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   20.250168] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[   20.250333] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.828808] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   24.101385] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   30.512040] eth0: no IPv6 routers present
[   36.182468] wlan0: authenticate with 00:01:38:c6:61:bf (try 1)
[   36.184622] wlan0: authenticated
[   36.184645] wlan0: associate with 00:01:38:c6:61:bf (try 1)
[   36.186823] wlan0: RX AssocResp from 00:01:38:c6:61:bf (capab=0x431 status=0 aid=3)
[   36.186827] wlan0: associated
[   36.213801] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.226290] cfg80211: Calling CRDA for country: ES
[   36.229620] cfg80211: Received country IE:
[   36.229623] cfg80211: Regulatory domain: ES
[   36.229624]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.229627]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2000 mBm)
[   36.229629] cfg80211: CRDA thinks this should applied:
[   36.229631] cfg80211: Regulatory domain: ES
[   36.229632]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.229635]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.229637]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.229639]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.229641]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   36.229643] cfg80211: We intersect both of these and get:
[   36.229645] cfg80211: Regulatory domain: 98
[   36.229646]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.229648]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.229652] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   36.229655] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   36.229657] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   36.229659] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   36.229661] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   36.229664] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   36.229666] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   36.229668] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   36.229670] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   36.229673] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   36.229675] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   36.229677] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   36.229679] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   36.229681] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   36.229684] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   36.229686] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   36.229688] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   36.229690] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   36.229692] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   36.229696] cfg80211: Current regulatory domain updated by AP to: ES
[   36.229698]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.229700]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   46.648147] wlan0: no IPv6 routers present
[   95.069087] wlan0: deauthenticating from 00:01:38:c6:61:bf by local choice (reason=3)
[   95.198348] cfg80211: All devices are disconnected, going to restore regulatory settings
[   95.198357] cfg80211: Restoring regulatory settings
[   95.198362] cfg80211: Calling CRDA to update world regulatory domain
[   95.202129] cfg80211: World regulatory domain updated:
[   95.202132]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   95.202135]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.202138]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   95.202141]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   95.202143]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.202146]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  104.154468] wlan0: authenticate with 00:01:38:c6:61:bf (try 1)
[  104.156330] wlan0: authenticated
[  104.156382] wlan0: associate with 00:01:38:c6:61:bf (try 1)
[  104.158577] wlan0: RX AssocResp from 00:01:38:c6:61:bf (capab=0x431 status=0 aid=3)
[  104.158581] wlan0: associated
[  104.195432] cfg80211: Calling CRDA for country: ES
[  104.202135] cfg80211: Received country IE:
[  104.202139] cfg80211: Regulatory domain: ES
[  104.202142]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  104.202146]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2000 mBm)
[  104.202148] cfg80211: CRDA thinks this should applied:
[  104.202151] cfg80211: Regulatory domain: ES
[  104.202153]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  104.202157]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  104.202160]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  104.202163]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  104.202167]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  104.202169] cfg80211: We intersect both of these and get:
[  104.202172] cfg80211: Regulatory domain: 98
[  104.202174]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  104.202177]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  104.202183] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[  104.202187] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[  104.202190] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[  104.202193] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[  104.202196] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[  104.202200] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[  104.202203] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[  104.202206] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[  104.202209] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[  104.202213] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[  104.202216] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[  104.202219] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[  104.202222] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[  104.202226] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[  104.202229] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[  104.202232] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[  104.202235] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[  104.202238] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[  104.202242] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[  104.202247] cfg80211: Current regulatory domain updated by AP to: ES
[  104.202249]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  104.202253]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)


```

---

### Post by videoclocknet on 2011-05-16
I have to add that I had similar problems in the past with Windows XP (the same laptop and the same router) and I could solve it with the info from some people in the next forum

[http://www.networking-forum.com/viewtopic.php?f=42&t=21365&p=136363#p136363](http://www.networking-forum.com/viewtopic.php?f=42&t=21365&p=136363#p136363)

So, can it be the DNS servers the reason?

If you need more info, let me know.

Regards

---

### Post by videoclocknet on 2011-05-17
Hey people!

I've got it! I've added the following DNS servers in "Network Connection":
8.8.8.8
8.8.4.4

And it works like a charm now!

Regards.

---

