---
title: "Wifi disabled when card switched off during boot"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by user790 on 2009-07-12
I have an HP pavilion with ubuntu 9.04. This laptop has a physical switch that turns on/off wireless connections (wifi+bluetooth).

When I boot with the swith on, the wifi card is recognized and enabled.

However, when I boot with the switch off, the wifi is disabled, even when I turn the switch on again. Wired Nework remains in the "disconnected" mode.

My current workaround is to reboot each time I forgot to switch it back on. It's not pretty.

So I'm looking for a way to make the system somehow look again at wifi cards, either automatically when I switch it back on, or manually through the command line.

Thanks!

---

### Post by t0mppa on 2009-07-12
I'm guessing you'd have to load or reload the driver module and possibly also bring the interface up with a terminal command.

But before jumping into conclusions, it's best to find out what exactly needs to be fixed. So, just boot into the "disconnected" state and run **lshw -C network** to check if it shows the wireless interface as unclaimed or disabled. Note that if you don't enable it through the switch, it might not show up at all.

---

### Post by user790 on 2009-07-13
Here is the output when I boot with the switch off:
```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:11:55:f3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:e5:35:a7
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s

```

---

### Post by t0mppa on 2009-07-14
That looks just fine, the driver gets associated and the interface is up. How about **iwconfig** and **iwlist scan**?

---

### Post by user790 on 2009-07-14
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


```

---

### Post by t0mppa on 2009-07-14
All looks good, except no networks found on scan. Unfortunately I've never played around with the Intel cards or drivers, so not sure how to properly troubleshoot them.

Checking the post-boot (ie. from when you enable the switch) lines of *dmesg* and/or *syslog* (can be found from */var/log*) is the only thing I can think of that could give a clue as to what's going wrong. Else you're going to have to consult one of the more experienced people around here.

---

### Post by user790 on 2009-07-14
OK, interesting stuff. I was switching the modem on and off to view what appears in syslog, and suddenly I went online. It seems that switching it on/off a couple of times do the trick. That'a an acceptable workaround for me, although you still might wish to figure out what is going. For the record/debugging purposes, here is the output of dmesg after the first unsuccessfull switch.

```

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
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
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
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
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c0000 - 37fefc31
[    0.000000] Allocated new RAMDISK: 0087b000 - 00faac31
[    0.000000] Move RAMDISK from 00000000378c0000 - 0000000037fefc30 to 0087b000 - 00faac30
[    0.000000] ACPI: RSDP 000F8240, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7FED1B96, 007C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDBC6C, 00F4 (r3 HP     30CC      6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED3071, 8B87 (r1 HP     30D2      6040000 INTL 20061109)
[    0.000000] ACPI: FACS 7FEDEFC0, 0040
[    0.000000] ACPI: HPET 7FEDBD60, 0038 (r1 HP     30D2      6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDBD98, 003C (r1 HP     30D2      6040000 LOHR       5A)
[    0.000000] ACPI: TMOR 7FEDBDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
[    0.000000] ACPI: APIC 7FEDBDFA, 0068 (r1 HP     30D2      6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDBE62, 0028 (r1 HP     30D2      6040000  LTP        1)
[    0.000000] ACPI: SLIC 7FEDBE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED2D94, 02DD (r1 HP     30D2         1000 INTL 20061109)
[    0.000000] ACPI: SSDT 7FED2184, 025F (r1  HP    30D2         3000 INTL 20061109)
[    0.000000] ACPI: SSDT 7FED20DE, 00A6 (r1  HP    30D2         3000 INTL 20061109)
[    0.000000] ACPI: SSDT 7FED1C12, 04CC (r1  HP     30D2        3000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1162MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000faac31]      NEW RAMDISK ==> [000087b000 - 0000faac31]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f82e0] 000f82e0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523861
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2326 pages used for memmap
[    0.000000]   HighMem zone: 295356 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519767
[    0.000000] Kernel command line: root=UUID=b2ab3351-9ceb-4e7a-afda-f89729ff36c4 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.764 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10479680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2051916k/2095936k available (4110k kernel code, 42596k reserved, 2196k data, 532k init, 1190728k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.52 BogoMIPS (lpj=7979056)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018157] ACPI: Core revision 20080926
[    0.021093] ACPI: Checking initramfs for custom DSDT
[    0.292447] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.335169] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.336001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.97 BogoMIPS (lpj=7979951)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.420408] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.420424] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.424034] Brought up 2 CPUs
[    0.424037] Total of 2 processors activated (7979.50 BogoMIPS).
[    0.424088] CPU0 attaching sched-domain:
[    0.424091]  domain 0: span 0-1 level MC
[    0.424093]   groups: 0 1
[    0.424100] CPU1 attaching sched-domain:
[    0.424101]  domain 0: span 0-1 level MC
[    0.424104]   groups: 1 0
[    0.424171] net_namespace: 776 bytes
[    0.424171] Booting paravirtualized kernel on bare hardware
[    0.424311] Time: 21:17:19  Date: 07/14/09
[    0.424311] regulator: core version 0.5
[    0.424311] NET: Registered protocol family 16
[    0.424311] EISA bus registered
[    0.424311] ACPI: bus type pci registered
[    0.424311] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.424311] PCI: MCFG area at e0000000 reserved in E820
[    0.424311] PCI: Using MMCONFIG for extended config space
[    0.424311] PCI: Using configuration type 1 for base access
[    0.425099] ACPI: EC: Look up EC in DSDT
[    0.430666] ACPI: BIOS _OSI(Linux) query ignored
[    0.431976] ACPI: Interpreter enabled
[    0.431981] ACPI: (supports S0 S3 S4 S5)
[    0.432006] ACPI: Using IOAPIC for interrupt routing
[    0.432020] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.448564] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.448567] ACPI: EC: driver started in interrupt mode
[    0.452121] ACPI: No dock devices found.
[    0.452132] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.452226] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.452230] pci 0000:00:01.0: PME# disabled
[    0.452322] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.452389] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.452463] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8404800-0xf8404bff]
[    0.452514] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.452520] pci 0000:00:1a.7: PME# disabled
[    0.452578] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8400000-0xf8403fff]
[    0.452622] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.452627] pci 0000:00:1b.0: PME# disabled
[    0.452698] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.452702] pci 0000:00:1c.0: PME# disabled
[    0.452777] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.452781] pci 0000:00:1c.1: PME# disabled
[    0.452860] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.452865] pci 0000:00:1c.5: PME# disabled
[    0.452931] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.452999] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.453068] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.453140] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8404c00-0xf8404fff]
[    0.453191] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.453196] pci 0000:00:1d.7: PME# disabled
[    0.453355] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.453360] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.453396] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.453404] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.453412] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.453420] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.453429] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.453504] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    0.453512] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.453521] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    0.453529] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.453537] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.453545] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8404000-0xf84047ff]
[    0.453567] pci 0000:00:1f.2: PME# supported from D3hot
[    0.453572] pci 0000:00:1f.2: PME# disabled
[    0.453606] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.453632] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.453712] pci 0000:01:00.0: reg 10 32bit mmio: [0xc6000000-0xc6ffffff]
[    0.453729] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.453745] pci 0000:01:00.0: reg 1c 64bit mmio: [0xc4000000-0xc5ffffff]
[    0.453755] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.453764] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.453848] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.453852] pci 0000:00:01.0: bridge 32bit mmio: [0xc4000000-0xc6ffffff]
[    0.453857] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.453953] pci 0000:02:00.0: reg 10 64bit mmio: [0xf4000000-0xf4001fff]
[    0.454034] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.454041] pci 0000:02:00.0: PME# disabled
[    0.454125] pci 0000:00:1c.0: bridge io port: [0x4000-0x7fff]
[    0.454130] pci 0000:00:1c.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.454138] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf3ffffff]
[    0.454202] pci 0000:00:1c.1: bridge io port: [0x8000-0xbfff]
[    0.454207] pci 0000:00:1c.1: bridge 32bit mmio: [0xbc000000-0xbfffffff]
[    0.454215] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xc8000000-0xcbffffff]
[    0.454292] pci 0000:06:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.454322] pci 0000:06:00.0: reg 18 64bit mmio: [0xf8000000-0xf8000fff]
[    0.454352] pci 0000:06:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.454367] pci 0000:06:00.0: supports D1 D2
[    0.454369] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.454375] pci 0000:06:00.0: PME# disabled
[    0.454449] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.454454] pci 0000:00:1c.5: bridge 32bit mmio: [0xf8000000-0xf80fffff]
[    0.454519] pci 0000:07:09.0: reg 10 32bit mmio: [0xf8100000-0xf81007ff]
[    0.454569] pci 0000:07:09.0: supports D1 D2
[    0.454571] pci 0000:07:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454576] pci 0000:07:09.0: PME# disabled
[    0.454623] pci 0000:07:09.1: reg 10 32bit mmio: [0xf8100800-0xf81008ff]
[    0.454674] pci 0000:07:09.1: supports D1 D2
[    0.454676] pci 0000:07:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454681] pci 0000:07:09.1: PME# disabled
[    0.454724] pci 0000:07:09.2: reg 10 32bit mmio: [0xf8100c00-0xf8100cff]
[    0.454774] pci 0000:07:09.2: supports D1 D2
[    0.454776] pci 0000:07:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454781] pci 0000:07:09.2: PME# disabled
[    0.454823] pci 0000:07:09.3: reg 10 32bit mmio: [0xf8101000-0xf81010ff]
[    0.454874] pci 0000:07:09.3: supports D1 D2
[    0.454876] pci 0000:07:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454880] pci 0000:07:09.3: PME# disabled
[    0.454923] pci 0000:07:09.4: reg 10 32bit mmio: [0xf8101400-0xf81014ff]
[    0.454973] pci 0000:07:09.4: supports D1 D2
[    0.454975] pci 0000:07:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454980] pci 0000:07:09.4: PME# disabled
[    0.455031] pci 0000:00:1e.0: transparent bridge
[    0.455040] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8100000-0xf81fffff]
[    0.455078] bus 00 -> node 0
[    0.455084] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.455450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.455603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.455749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.455893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.456058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.465559] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.465682] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.465803] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.465922] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.466042] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.466162] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.466282] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.466401] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.466706] ACPI: WMI: Mapper loaded
[    0.466743] SCSI subsystem initialized
[    0.466743] libata version 3.00 loaded.
[    0.466743] usbcore: registered new interface driver usbfs
[    0.466743] usbcore: registered new interface driver hub
[    0.466743] usbcore: registered new device driver usb
[    0.466743] PCI: Using ACPI for IRQ routing
[    0.472009] Bluetooth: Core ver 2.13
[    0.472022] NET: Registered protocol family 31
[    0.472022] Bluetooth: HCI device and connection manager initialized
[    0.472022] Bluetooth: HCI socket layer initialized
[    0.472022] NET: Registered protocol family 8
[    0.472022] NET: Registered protocol family 20
[    0.472032] NetLabel: Initializing
[    0.472034] NetLabel:  domain hash size = 128
[    0.472036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472048] NetLabel:  unlabeled traffic allowed by default
[    0.472062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.472067] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.476057] AppArmor: AppArmor Filesystem Enabled
[    0.484008] pnp: PnP ACPI init
[    0.484016] ACPI: bus type pnp registered
[    0.488310] pnp: PnP ACPI: found 11 devices
[    0.488312] ACPI: ACPI bus type pnp unregistered
[    0.488315] PnPBIOS: Disabled by ACPI PNP
[    0.488323] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.488326] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.488329] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.488332] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.488335] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.488337] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.488340] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.488343] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.488350] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.488356] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.488359] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.488361] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.488364] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.488366] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.488369] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.488374] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.488376] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.500460] Switched to high resolution mode on CPU 1
[    0.504006] Switched to high resolution mode on CPU 0
[    0.523084] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.523087] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.523090] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.523094] pci 0000:00:01.0:   MEM window: 0xc4000000-0xc6ffffff
[    0.523098] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.523103] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.523106] pci 0000:00:1c.0:   IO window: 0x4000-0x7fff
[    0.523113] pci 0000:00:1c.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.523118] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.523126] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.523129] pci 0000:00:1c.1:   IO window: 0x8000-0xbfff
[    0.523136] pci 0000:00:1c.1:   MEM window: 0xbc000000-0xbfffffff
[    0.523141] pci 0000:00:1c.1:   PREFETCH window: 0x000000c8000000-0x000000cbffffff
[    0.523150] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.523153] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.523160] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf80fffff
[    0.523165] pci 0000:00:1c.5:   PREFETCH window: 0x00000088000000-0x000000880fffff
[    0.523173] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.523175] pci 0000:00:1e.0:   IO window: disabled
[    0.523182] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xf81fffff
[    0.523186] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.523202] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.523206] pci 0000:00:01.0: setting latency timer to 64
[    0.523215] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.523220] pci 0000:00:1c.0: setting latency timer to 64
[    0.523229] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.523234] pci 0000:00:1c.1: setting latency timer to 64
[    0.523243] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.523248] pci 0000:00:1c.5: setting latency timer to 64
[    0.523257] pci 0000:00:1e.0: setting latency timer to 64
[    0.523261] bus: 00 index 0 io port: [0x00-0xffff]
[    0.523263] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.523265] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.523268] bus: 01 index 1 mmio: [0xc4000000-0xc6ffffff]
[    0.523270] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.523272] bus: 01 index 3 mmio: [0x0-0x0]
[    0.523274] bus: 02 index 0 io port: [0x4000-0x7fff]
[    0.523276] bus: 02 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.523278] bus: 02 index 2 mmio: [0xf0000000-0xf3ffffff]
[    0.523280] bus: 02 index 3 mmio: [0x0-0x0]
[    0.523282] bus: 04 index 0 io port: [0x8000-0xbfff]
[    0.523284] bus: 04 index 1 mmio: [0xbc000000-0xbfffffff]
[    0.523286] bus: 04 index 2 mmio: [0xc8000000-0xcbffffff]
[    0.523288] bus: 04 index 3 mmio: [0x0-0x0]
[    0.523290] bus: 06 index 0 io port: [0xc000-0xcfff]
[    0.523292] bus: 06 index 1 mmio: [0xf8000000-0xf80fffff]
[    0.523295] bus: 06 index 2 mmio: [0x88000000-0x880fffff]
[    0.523296] bus: 06 index 3 mmio: [0x0-0x0]
[    0.523298] bus: 07 index 0 mmio: [0x0-0x0]
[    0.523300] bus: 07 index 1 mmio: [0xf8100000-0xf81fffff]
[    0.523302] bus: 07 index 2 mmio: [0x0-0x0]
[    0.523304] bus: 07 index 3 io port: [0x00-0xffff]
[    0.523306] bus: 07 index 4 mmio: [0x000000-0xffffffff]
[    0.523314] NET: Registered protocol family 2
[    0.536051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.536292] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.536619] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.536788] TCP: Hash tables configured (established 131072 bind 65536)
[    0.536790] TCP reno registered
[    0.540070] NET: Registered protocol family 1
[    0.540184] checking if image is initramfs... it is
[    1.140151] Freeing initrd memory: 7359k freed
[    1.140188] Simple Boot Flag at 0x35 set to 0x1
[    1.140332] cpufreq: No nForce2 chipset.
[    1.140465] audit: initializing netlink socket (disabled)
[    1.140489] type=2000 audit(1247606239.137:1): initialized
[    1.147649] highmem bounce pool size: 64 pages
[    1.147654] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.148932] VFS: Disk quotas dquot_6.5.1
[    1.148987] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.149572] fuse init (API version 7.10)
[    1.149650] msgmni has been set to 1698
[    1.149814] alg: No test for stdrng (krng)
[    1.149825] io scheduler noop registered
[    1.149827] io scheduler anticipatory registered
[    1.149829] io scheduler deadline registered
[    1.149842] io scheduler cfq registered (default)
[    1.150008] pci 0000:01:00.0: Boot video device
[    1.156119] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.156157] pcieport-driver 0000:00:01.0: found MSI capability
[    1.156182] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.156192] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.156205] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.156217] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.156269] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.156321] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.156356] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.156373] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.156385] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.156398] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.156474] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.156526] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.156561] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.156577] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.156589] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.156600] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.156675] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.156727] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.156762] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
[    1.156779] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.156791] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.156802] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.156888] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.157238] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.159565] ACPI: AC Adapter [ACAD] (on-line)
[    1.259465] ACPI: Battery Slot [BAT0] (battery present)
[    1.259541] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.259544] ACPI: Power Button (FF) [PWRF]
[    1.259583] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.259593] ACPI: Power Button (CM) [PWRB]
[    1.259635] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.259638] ACPI: Sleep Button (CM) [SLPB]
[    1.259679] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.262827] ACPI: Lid Switch [LID]
[    1.263363] ACPI: SSDT 7FED2A52, 027A (r1  HP    30D2         3000 INTL 20061109)
[    1.263781] ACPI: SSDT 7FED23E3, 05EA (r1  HP    30D2         3001 INTL 20061109)
[    1.266108] Monitor-Mwait will be used to enter C-1 state
[    1.266111] Monitor-Mwait will be used to enter C-2 state
[    1.266123] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.266146] processor ACPI_CPU:00: registered as cooling_device0
[    1.266150] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.266502] ACPI: SSDT 7FED2CCC, 00C8 (r1  HP    30D2         3000 INTL 20061109)
[    1.266876] ACPI: SSDT 7FED29CD, 0085 (r1  HP    30D2         3000 INTL 20061109)
[    1.267850] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.267868] processor ACPI_CPU:01: registered as cooling_device1
[    1.267872] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.286220] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.286279] isapnp: Scanning for PnP cards...
[    1.640399] isapnp: No Plug & Play device found
[    1.656226] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.657218] brd: module loaded
[    1.657504] loop: module loaded
[    1.657571] Fixed MDIO Bus: probed
[    1.657576] PPP generic driver version 2.4.2
[    1.657629] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.657656] Driver 'sd' needs updating - please use bus_type methods
[    1.657665] Driver 'sr' needs updating - please use bus_type methods
[    1.657705] ahci 0000:00:1f.2: version 3.0
[    1.657720] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.657760] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.657828] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.657831] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.657837] ahci 0000:00:1f.2: setting latency timer to 64
[    1.658063] scsi0 : ahci
[    1.658146] scsi1 : ahci
[    1.658201] scsi2 : ahci
[    1.658295] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 2299
[    1.658299] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 2299
[    1.658302] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 2299
[    1.976021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.978639] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.978644] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-10, max UDMA/100
[    1.978647] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.981335] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.981358] ata1.00: configured for UDMA/100
[    2.316018] ata2: SATA link down (SStatus 0 SControl 300)
[    2.652016] ata3: SATA link down (SStatus 0 SControl 300)
[    2.668099] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    2.668192] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.668207] sd 0:0:0:0: [sda] Write Protect is off
[    2.668209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.668233] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.668286] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.668300] sd 0:0:0:0: [sda] Write Protect is off
[    2.668302] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.668325] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.668328]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.722149] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.722188] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.722237] ata_piix 0000:00:1f.1: version 2.12
[    2.722244] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.722278] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.722348] scsi3 : ata_piix
[    2.722405] scsi4 : ata_piix
[    2.723019] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    2.723022] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    2.884421] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    2.900380] ata4.00: configured for MWDMA2
[    3.070674] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    3.081596] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.081599] Uniform CD-ROM driver Revision: 3.20
[    3.081680] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.081717] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.082375] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.082395] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.082409] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.082413] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.082471] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.086388] ehci_hcd 0000:00:1a.7: debug port 1
[    3.086395] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.086409] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[    3.100010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.100069] usb usb1: configuration #1 chosen from 1 choice
[    3.100094] hub 1-0:1.0: USB hub found
[    3.100101] hub 1-0:1.0: 4 ports detected
[    3.100202] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.100213] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.100217] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.100254] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.104153] ehci_hcd 0000:00:1d.7: debug port 1
[    3.104160] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.104172] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    3.120009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.120062] usb usb2: configuration #1 chosen from 1 choice
[    3.120085] hub 2-0:1.0: USB hub found
[    3.120091] hub 2-0:1.0: 6 ports detected
[    3.120183] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.120199] uhci_hcd: USB Universal Host Controller Interface driver
[    3.120220] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.120227] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.120230] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.120268] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.120304] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.120375] usb usb3: configuration #1 chosen from 1 choice
[    3.120398] hub 3-0:1.0: USB hub found
[    3.120404] hub 3-0:1.0: 2 ports detected
[    3.120489] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.120496] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.120500] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.120537] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.120573] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    3.120651] usb usb4: configuration #1 chosen from 1 choice
[    3.120674] hub 4-0:1.0: USB hub found
[    3.120680] hub 4-0:1.0: 2 ports detected
[    3.120759] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.120766] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.120769] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.120810] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.120837] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    3.120909] usb usb5: configuration #1 chosen from 1 choice
[    3.120932] hub 5-0:1.0: USB hub found
[    3.120937] hub 5-0:1.0: 2 ports detected
[    3.121017] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.121023] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.121027] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.121066] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.121101] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    3.121168] usb usb6: configuration #1 chosen from 1 choice
[    3.121191] hub 6-0:1.0: USB hub found
[    3.121196] hub 6-0:1.0: 2 ports detected
[    3.121276] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.121282] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.121286] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.121323] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.121351] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    3.121420] usb usb7: configuration #1 chosen from 1 choice
[    3.121443] hub 7-0:1.0: USB hub found
[    3.121449] hub 7-0:1.0: 2 ports detected
[    3.121585] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.163346] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.163351] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.164035] mice: PS/2 mouse device common for all mice
[    3.184073] rtc_cmos 00:08: RTC can wake from S4
[    3.184103] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    3.184135] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.184189] device-mapper: uevent: version 1.0.3
[    3.184267] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.184331] device-mapper: multipath: version 1.0.5 loaded
[    3.184333] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.184400] EISA: Probing bus 0 at eisa.0
[    3.184407] Cannot allocate resource for EISA slot 1
[    3.184410] Cannot allocate resource for EISA slot 2
[    3.184416] Cannot allocate resource for EISA slot 4
[    3.184418] Cannot allocate resource for EISA slot 5
[    3.184420] Cannot allocate resource for EISA slot 6
[    3.184422] Cannot allocate resource for EISA slot 7
[    3.184424] Cannot allocate resource for EISA slot 8
[    3.184426] EISA: Detected 0 cards.
[    3.184517] cpuidle: using governor ladder
[    3.184602] cpuidle: using governor menu
[    3.185091] TCP cubic registered
[    3.185180] NET: Registered protocol family 10
[    3.185591] lo: Disabled Privacy Extensions
[    3.185920] NET: Registered protocol family 17
[    3.185935] Bluetooth: L2CAP ver 2.11
[    3.185937] Bluetooth: L2CAP socket layer initialized
[    3.185940] Bluetooth: SCO (Voice Link) ver 0.6
[    3.185941] Bluetooth: SCO socket layer initialized
[    3.185971] Marking TSC unstable due to TSC halts in idle
[    3.185973] Bluetooth: RFCOMM socket layer initialized
[    3.185979] Bluetooth: RFCOMM TTY layer initialized
[    3.185981] Bluetooth: RFCOMM ver 1.10
[    3.186637] Using IPI No-Shortcut mode
[    3.186701] registered taskstats version 1
[    3.186826]   Magic number: 1:7:298
[    3.186916] rtc_cmos 00:08: setting system clock to 2009-07-14 21:17:22 UTC (1247606242)
[    3.186919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.186921] EDD information not available.
[    3.187194] Freeing unused kernel memory: 532k freed
[    3.187335] Write protecting the kernel text: 4112k
[    3.187390] Write protecting the kernel read-only data: 1524k
[    3.230366] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.542156] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.542177] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.542197] r8169 0000:06:00.0: setting latency timer to 64
[    3.542338] r8169 0000:06:00.0: irq 2298 for MSI/MSI-X
[    3.543002] eth0: RTL8101e at 0xf7c74000, 00:1b:24:e5:35:a7, XID 34200000 IRQ 2298
[    3.582441] ohci1394 0000:07:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.635181] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.639199] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    3.785189] usb 2-4: configuration #1 chosen from 1 choice
[    3.880969] PM: Starting manual resume from disk
[    3.880972] PM: Resume from partition 8:5
[    3.880973] PM: Checking hibernation image.
[    3.881111] PM: Resume from disk failed.
[    3.910682] kjournald starting.  Commit interval 5 seconds
[    3.910695] EXT3-fs: mounted filesystem with ordered data mode.
[    4.024054] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    4.258238] usb 6-1: configuration #1 chosen from 1 choice
[    4.960282] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00412c9300]
[   12.991849] udev: starting version 141
[   13.244132] cfg80211: Calling CRDA to update world regulatory domain
[   13.587861] cfg80211: World regulatory domain updated:
[   13.587864]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.587866]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.587869]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.587871]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.587873]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.587875]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.607277] Linux agpgart interface v0.103
[   13.624276] iTCO_vendor_support: vendor-support=0
[   13.744249] sdhci: Secure Digital Host Controller Interface driver
[   13.744253] sdhci: Copyright(c) Pierre Ossman
[   14.012244] sdhci-pci 0000:07:09.1: SDHCI controller found [1180:0822] (rev 22)
[   14.012261] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   14.014480] mmc0: SDHCI controller on PCI [0000:07:09.1] using PIO
[   14.038536] Linux video capture interface: v2.00
[   14.057630] ricoh-mmc: Ricoh MMC Controller disabling driver
[   14.057632] ricoh-mmc: Copyright(c) Philip Langdale
[   14.057659] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)
[   14.057677] ricoh-mmc: Controller is now disabled.
[   14.090919] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.121653] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.121790] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   14.121874] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.336348] nvidia: module license 'NVIDIA' taints kernel.
[   14.562351] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.589070] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   14.589081] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.589090] nvidia 0000:01:00.0: setting latency timer to 64
[   14.589523] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   14.602913] acpi device:06: registered as cooling_device2
[   14.603096] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input7
[   14.606778] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.672040] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.672044] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.673115] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.673125] iwlagn 0000:02:00.0: setting latency timer to 64
[   14.673197] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   14.683251] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   14.684393] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[   14.712035] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.712110] iwlagn 0000:02:00.0: irq 2297 for MSI/MSI-X
[   14.713638] usbcore: registered new interface driver uvcvideo
[   14.713662] USB Video Class driver (v0.1.0)
[   14.717489] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.958213] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.958291] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.215957] lp: driver loaded but no devices found
[   15.356315] Adding 1606460k swap on /dev/sda5.  Priority:-1 extents:1 across:1606460k
[   15.763844] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   15.872446] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   15.901710] EXT3 FS on sda3, internal journal
[   17.548483] type=1505 audit(1247599056.861:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2152
[   17.589265] type=1505 audit(1247599056.901:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2156
[   17.589360] type=1505 audit(1247599056.901:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2156
[   17.589398] type=1505 audit(1247599056.901:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2156
[   17.589433] type=1505 audit(1247599056.901:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2156
[   17.631466] type=1505 audit(1247599056.942:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2163
[   17.743644] type=1505 audit(1247599057.054:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2167
[   17.743800] type=1505 audit(1247599057.054:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2167
[   17.768037] type=1505 audit(1247599057.078:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2171
[   23.471435] ppdev: user-space parallel port driver
[   26.689422] r8169: eth0: link down
[   26.689606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.690229] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   26.786810] iwlagn: Radio disabled by HW RF Kill switch
[   27.717378] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  339.832047] usb 7-2: new full speed USB device using uhci_hcd and address 2
[  340.010237] usb 7-2: configuration #1 chosen from 1 choice
[  340.057492] Bluetooth: Generic Bluetooth USB driver ver 0.3
[  340.057670] usbcore: registered new interface driver btusb
[  347.192072] usb 1-4: new high speed USB device using ehci_hcd and address 2
[  347.337833] usb 1-4: configuration #1 chosen from 1 choice
[  347.411168] Initializing USB Mass Storage driver...
[  347.411496] scsi5 : SCSI emulation for USB Mass Storage devices
[  347.411701] usb-storage: device found at 2
[  347.411707] usb-storage: waiting for device to settle before scanning
[  347.411713] usbcore: registered new interface driver usb-storage
[  347.411720] USB Mass Storage support registered.
[  352.408338] usb-storage: device scan complete
[  352.408901] scsi 5:0:0:0: Direct-Access              USB DISK 20X     PMAP PQ: 0 ANSI: 0 CCS
[  354.426625] sd 5:0:0:0: [sdb] 1970176 512-byte hardware sectors: (1.00 GB/962 MiB)
[  354.427101] sd 5:0:0:0: [sdb] Write Protect is off
[  354.427108] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  354.427113] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  354.428729] sd 5:0:0:0: [sdb] 1970176 512-byte hardware sectors: (1.00 GB/962 MiB)
[  354.429395] sd 5:0:0:0: [sdb] Write Protect is off
[  354.429402] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  354.429408] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  354.429443]  sdb: sdb1
[  354.432332] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  354.432469] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

---

