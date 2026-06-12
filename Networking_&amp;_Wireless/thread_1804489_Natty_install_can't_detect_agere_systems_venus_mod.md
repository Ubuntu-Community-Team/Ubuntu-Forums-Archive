---
title: "Natty install can't detect agere systems venus modem (internal)"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by just_joel on 2011-07-14
Hi,

I'm trying to upgrade my mother and sister from Fedora Core 6 to Kubuntu 11.04.  Everything is fine but the (hardware, not winmodem) modem, a Lucent (Agere) Venus modem.  (Yes, my mum and sister are stuck on dialup!)  The modem works great under Fedora Core 6.  Under Kubuntu 11.04, however, wvdialconf can't find it at all (which it can no problem under Fedora 6), and scanModem sees that there's a problem but doesn't seem to point me in any useful directions.  I have spent all day scanning the forums, trying out everything I could think of (checking permissions, playing around with setserial, checking for IRQ conflicts, looking for an ACPI kernel setting to change, etc.) and coming up with absolutely nothing.  System log shows the modem identified as /dev/ttyS4 with no obvious problems I can see.

--------------------------
lspci -vv gives me this:
--------------------------

01:08.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
        Subsystem: Actiontec Electronics Inc Device 0500
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0 (63000ns min, 3500ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        Region 1: I/O ports at e800 [size=256]
        Region 2: I/O ports at e400 [size=256]
        Region 3: I/O ports at ecb8 [size=8]
        Capabilities: [f8] Power Management version 2
               Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA             
                      PME(D0-,D1-,D2+,D3hot+,D3cold+)
               Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: serial

----------------------------
wvdialconf gives me this:
----------------------------

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyS4<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS4<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS4<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S5   S6   S7   S8   S9   
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17  
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25  
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

---------------------------------------------
scanModem provides this dmesg.txt file:
---------------------------------------------

           CPU0       
  0:         50   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  4:         12   IO-APIC-edge    
  6:          3   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:       6724   IO-APIC-edge      ata_piix
 15:       8184   IO-APIC-edge      ata_piix
 16:        367   IO-APIC-fasteoi   uhci_hcd:usb2, i915, Ensoniq AudioPCI
 17:         95   IO-APIC-fasteoi 
 18:       1026   IO-APIC-fasteoi   uhci_hcd:usb4, eth0
 19:       2194   IO-APIC-fasteoi   uhci_hcd:usb3
 23:       7937   IO-APIC-fasteoi   ehci_hcd:usb1
NMI:          0   Non-maskable interrupts
LOC:     179732   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
IWI:          0   IRQ work interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          7   Machine check polls
ERR:          0
MIS:          0

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe71000 (usable)
[    0.000000]  BIOS-e820: 000000007fe71000 - 000000007fe73000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe73000 - 000000007fe94000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe94000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Dell Computer Corporation OptiPlex GX60                /06P791, BIOS A08 06/07/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fe71 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
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
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35d3e000 - 36e97000
[    0.000000] ACPI: RSDP 000feba0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fd4f8 00038 (v01 DELL    GX60    00000008 ASL  00000061)
[    0.000000] ACPI: FACP 000fd530 00074 (v01 DELL    GX60    00000008 ASL  00000061)
[    0.000000] ACPI: DSDT fffd7499 02616 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 7fe71000 00040
[    0.000000] ACPI: SSDT fffd9bec 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fd5a4 0006C (v01 DELL    GX60    00000008 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd610 00028 (v01 DELL    GX60    00000008 ASL  00000061)
[    0.000000] ACPI: ASF! 000fd638 00067 (v16 DELL    GX60    00000008 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fe71
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0007fe71
[    0.000000] On node 0 totalpages: 523777
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4d3e200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2317 pages used for memmap
[    0.000000]   HighMem zone: 294246 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:7ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519684
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=f43f0b87-ae53-45d1-a7ac-348723a6591a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10477460 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe71)
[    0.000000] Memory: 2040304k/2095556k available (5188k kernel code, 54804k reserved, 2540k data, 700k init, 1186252k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2390.826 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4781.65 BogoMIPS (lpj=9563304)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004070] Security Framework initialized
[    0.004109] AppArmor: AppArmor initialized
[    0.004113] Yama: becoming mindful.
[    0.004217] Mount-cache hash table entries: 512
[    0.004543] Initializing cgroup subsys ns
[    0.004555] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004562] Initializing cgroup subsys cpuacct
[    0.004574] Initializing cgroup subsys memory
[    0.004593] Initializing cgroup subsys devices
[    0.004598] Initializing cgroup subsys freezer
[    0.004602] Initializing cgroup subsys net_cls
[    0.004606] Initializing cgroup subsys blkio
[    0.004690] CPU0: Hyper-Threading is disabled
[    0.004698] mce: CPU supports 4 MCE banks
[    0.004715] CPU0: Thermal monitoring enabled (TM1)
[    0.005624] SMP alternatives: switching to UP code
[    0.020755] ACPI: Core revision 20110112
[    0.047102] ftrace: allocating 23640 entries in 47 pages
[    0.048176] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048496] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.090455] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[    0.092004] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.092004] ... version:                0
[    0.092004] ... bit width:              40
[    0.092004] ... generic registers:      18
[    0.092004] ... value mask:             000000ffffffffff
[    0.092004] ... max period:             0000007fffffffff
[    0.092004] ... fixed-purpose events:   0
[    0.092004] ... event mask:             000000000003ffff
[    0.092004] Brought up 1 CPUs
[    0.092004] Total of 1 processors activated (4781.65 BogoMIPS).
[    0.092004] devtmpfs: initialized
[    0.093581] print_constraints: dummy: 
[    0.093618] Time:  0:22:06  Date: 07/15/11
[    0.093722] NET: Registered protocol family 16
[    0.094007] EISA bus registered
[    0.094035] ACPI: bus type pci registered
[    0.114117] PCI: PCI BIOS revision 2.10 entry at 0xfbdd9, last bus=1
[    0.114123] PCI: Using configuration type 1 for base access
[    0.116628] bio: create slab <bio-0> at 0
[    0.117907] ACPI: EC: Look up EC in DSDT
[    0.136232] ACPI: Interpreter enabled
[    0.136248] ACPI: (supports S0 S1 S3 S4 S5)
[    0.136287] ACPI: Using IOAPIC for interrupt routing
[    0.170265] ACPI: No dock devices found.
[    0.170272] HEST: Table not found.
[    0.170281] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.173876] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.180906] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.180913] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.180918] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.180923] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    0.180927] pci_root PNP0A03:00: host bridge window [mem 0xfef00000-0xffafffff] (ignored)
[    0.180952] pci 0000:00:00.0: [8086:2560] type 0 class 0x000600
[    0.180967] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.181047] pci 0000:00:02.0: [8086:2562] type 0 class 0x000300
[    0.181069] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.181081] pci 0000:00:02.0: reg 14: [mem 0xff680000-0xff6fffff]
[    0.181198] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
[    0.181253] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
[    0.181296] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
[    0.181350] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
[    0.181392] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
[    0.181447] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
[    0.181503] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
[    0.181531] pci 0000:00:1d.7: reg 10: [mem 0xffa00000-0xffa003ff]
[    0.181627] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.181634] pci 0000:00:1d.7: PME# disabled
[    0.181658] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.181712] pci 0000:00:1f.0: [8086:24c0] type 0 class 0x000601
[    0.181718] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.181721] * this clock source is slow. If you are sure your timer does not have
[    0.181724] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.181822] pci 0000:00:1f.1: [8086:24cb] type 0 class 0x000101
[    0.181842] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.181855] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.181867] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.181880] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.181893] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.181906] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.181943] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
[    0.181997] pci 0000:00:1f.3: reg 20: [io  0xdc80-0xdc9f]
[    0.182074] pci 0000:01:07.0: [1274:1371] type 0 class 0x000401
[    0.182096] pci 0000:01:07.0: reg 10: [io  0xecc0-0xecff]
[    0.182171] pci 0000:01:07.0: supports D2
[    0.182175] pci 0000:01:07.0: PME# supported from D0 D2 D3hot
[    0.182181] pci 0000:01:07.0: PME# disabled
[    0.182205] pci 0000:01:08.0: [11c1:0480] type 0 class 0x000780
[    0.182227] pci 0000:01:08.0: reg 10: [mem 0xff8ffc00-0xff8ffcff]
[    0.182239] pci 0000:01:08.0: reg 14: [io  0xe800-0xe8ff]
[    0.182252] pci 0000:01:08.0: reg 18: [io  0xe400-0xe4ff]
[    0.182264] pci 0000:01:08.0: reg 1c: [io  0xecb8-0xecbf]
[    0.182314] pci 0000:01:08.0: supports D2
[    0.182317] pci 0000:01:08.0: PME# supported from D2 D3hot D3cold
[    0.182323] pci 0000:01:08.0: PME# disabled
[    0.182350] pci 0000:01:0c.0: [8086:1229] type 0 class 0x000200
[    0.182372] pci 0000:01:0c.0: reg 10: [mem 0xff8fe000-0xff8fefff]
[    0.182384] pci 0000:01:0c.0: reg 14: [io  0xec40-0xec7f]
[    0.182396] pci 0000:01:0c.0: reg 18: [mem 0xff8c0000-0xff8dffff]
[    0.182452] pci 0000:01:0c.0: supports D1 D2
[    0.182455] pci 0000:01:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182461] pci 0000:01:0c.0: PME# disabled
[    0.182497] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.182506] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.182512] pci 0000:00:1e.0:   bridge window [mem 0xff800000-0xff9fffff]
[    0.182520] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.182525] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.182529] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.182543] pci_bus 0000:00: on NUMA node 0
[    0.182553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.183037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.271709] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.272128] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.272516] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.272899] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.273281] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.273666] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.274047] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.274435] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.274756] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.274771] vgaarb: loaded
[    0.275243] SCSI subsystem initialized
[    0.275405] libata version 3.00 loaded.
[    0.275529] usbcore: registered new interface driver usbfs
[    0.275569] usbcore: registered new interface driver hub
[    0.275679] usbcore: registered new device driver usb
[    0.276054] wmi: Mapper loaded
[    0.276060] PCI: Using ACPI for IRQ routing
[    0.276068] PCI: pci_cache_line_size set to 64 bytes
[    0.276146] reserve RAM buffer: 000000007fe71000 - 000000007fffffff 
[    0.276411] NetLabel: Initializing
[    0.276418] NetLabel:  domain hash size = 128
[    0.276421] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.276440] NetLabel:  unlabeled traffic allowed by default
[    0.290669] AppArmor: AppArmor Filesystem Enabled
[    0.290743] pnp: PnP ACPI init
[    0.290784] ACPI: bus type pnp registered
[    0.297709] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.297717] pnp 00:00: [mem 0x00100000-0x00ffffff]
[    0.297721] pnp 00:00: [mem 0x01000000-0x7fe70fff]
[    0.297725] pnp 00:00: [mem 0x000c0000-0x000fffff]
[    0.297729] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.297732] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.297736] pnp 00:00: [mem 0xffb00000-0xffbfffff]
[    0.297740] pnp 00:00: [mem 0xffc00000-0xffffffff]
[    0.297858] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.297867] system 00:00: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.297874] system 00:00: [mem 0x01000000-0x7fe70fff] could not be reserved
[    0.297879] system 00:00: [mem 0x000c0000-0x000fffff] could not be reserved
[    0.297885] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.297890] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.297896] system 00:00: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.297901] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved
[    0.297910] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.301600] pnp 00:01: [bus 00-ff]
[    0.301608] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.301612] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.301616] pnp 00:01: [io  0x0d00-0xffff window]
[    0.301620] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.301624] pnp 00:01: [mem 0x00000000 window]
[    0.301628] pnp 00:01: [mem 0xc0000000-0xfebfffff window]
[    0.301632] pnp 00:01: [mem 0xfef00000-0xffafffff window]
[    0.301734] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.304282] pnp 00:02: [io  0x0080-0x009f]
[    0.304290] pnp 00:02: [io  0x0000-0x001f]
[    0.304293] pnp 00:02: [io  0x00c0-0x00df]
[    0.304297] pnp 00:02: [dma 4]
[    0.304390] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.304519] pnp 00:03: [io  0x00f0-0x00ff]
[    0.304540] pnp 00:03: [irq 13]
[    0.304627] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.304752] pnp 00:04: [io  0x0061]
[    0.304843] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.304976] pnp 00:05: [io  0x0070-0x007f]
[    0.304994] pnp 00:05: [irq 8]
[    0.305083] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.308200] pnp 00:06: [io  0x03f0-0x03f5]
[    0.308206] pnp 00:06: [io  0x03f7]
[    0.308223] pnp 00:06: [irq 6]
[    0.308227] pnp 00:06: [dma 2]
[    0.308553] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.313479] pnp 00:07: [io  0x03f8-0x03ff]
[    0.313498] pnp 00:07: [irq 4]
[    0.313778] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.318518] pnp 00:08: [io  0x0378-0x037f]
[    0.318524] pnp 00:08: [io  0x0778-0x077f]
[    0.318541] pnp 00:08: [irq 7]
[    0.318546] pnp 00:08: [dma 0 disabled]
[    0.319147] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.320953] pnp 00:09: [io  0x0060]
[    0.320959] pnp 00:09: [io  0x0064]
[    0.320962] pnp 00:09: [io  0x0062-0x0063]
[    0.320967] pnp 00:09: [io  0x0065-0x006f]
[    0.320978] pnp 00:09: [io  0x00e0-0x00ef]
[    0.320982] pnp 00:09: [io  0x0800-0x085f]
[    0.320986] pnp 00:09: [io  0x0c00-0x0c7f]
[    0.320989] pnp 00:09: [io  0x0860-0x08ff]
[    0.321128] system 00:09: [io  0x0800-0x085f] has been reserved
[    0.321135] system 00:09: [io  0x0c00-0x0c7f] has been reserved
[    0.321139] system 00:09: [io  0x0860-0x08ff] has been reserved
[    0.321148] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.321960] pnp: PnP ACPI: found 10 devices
[    0.321966] ACPI: ACPI bus type pnp unregistered
[    0.321973] PnPBIOS: Disabled by ACPI PNP
[    0.362596] Switching to clocksource acpi_pm
[    0.362675] pci 0000:00:1f.1: BAR 5: assigned [mem 0x80000000-0x800003ff]
[    0.362686] pci 0000:00:1f.1: BAR 5: set to [mem 0x80000000-0x800003ff] (PCI address [0x80000000-0x800003ff])
[    0.362693] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.362699] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.362707] pci 0000:00:1e.0:   bridge window [mem 0xff800000-0xff9fffff]
[    0.362713] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.362735] pci 0000:00:1e.0: setting latency timer to 64
[    0.362742] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.362746] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.362750] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.362754] pci_bus 0000:01: resource 1 [mem 0xff800000-0xff9fffff]
[    0.362758] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.362763] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.362838] NET: Registered protocol family 2
[    0.362975] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363516] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.363516] Switched to NOHz mode on CPU #0
[    0.363516] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.363516] TCP: Hash tables configured (established 131072 bind 65536)
[    0.363516] TCP reno registered
[    0.363516] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.363516] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.363710] NET: Registered protocol family 1
[    0.363753] pci 0000:00:02.0: Boot video device
[    0.363873] pci 0000:01:0c.0: Firmware left e100 interrupts enabled; disabling
[    0.363884] PCI: CLS 64 bytes, default 64
[    0.364076] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.364082] Simple Boot Flag at 0x7a set to 0x1
[    0.364364] cpufreq-nforce2: No nForce2 chipset.
[    0.364724] audit: initializing netlink socket (disabled)
[    0.364749] type=2000 audit(1310689325.360:1): initialized
[    0.375901] Trying to unpack rootfs image as initramfs...
[    0.393157] highmem bounce pool size: 64 pages
[    0.393170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.403888] VFS: Disk quotas dquot_6.5.2
[    0.404110] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.405955] fuse init (API version 7.16)
[    0.406270] msgmni has been set to 1668
[    0.412434] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.412575] io scheduler noop registered
[    0.412580] io scheduler deadline registered
[    0.412648] io scheduler cfq registered (default)
[    0.412928] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.412988] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.413323] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.413339] ACPI: Power Button [VBTN]
[    0.413482] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.413494] ACPI: Power Button [PWRF]
[    0.413714] ACPI: acpi_idle registered with cpuidle
[    0.451249] ERST: Table is not found!
[    0.456598] isapnp: Scanning for PnP cards...
[    0.462330] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.482765] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.612163] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.636619] serial 0000:01:08.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.657039] 0000:01:08.0: ttyS4 at I/O 0xe800 (irq = 17) is a 16550A
[    0.724700] Linux agpgart interface v0.103
[    0.724822] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    0.724862] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.724966] agpgart-intel 0000:00:00.0: detected 1024K stolen memory
[    0.725185] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    0.732542] brd: module loaded
[    0.734188] loop: module loaded
[    0.734489] i2c-core: driver [adp5520] using legacy suspend method
[    0.734495] i2c-core: driver [adp5520] using legacy resume method
[    0.734747] ata_piix 0000:00:1f.1: version 2.13
[    0.734765] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.734798] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.734880] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.740258] scsi0 : ata_piix
[    0.740595] scsi1 : ata_piix
[    0.740725] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.740732] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.741625] Fixed MDIO Bus: probed
[    0.741730] PPP generic driver version 2.4.2
[    0.741897] tun: Universal TUN/TAP device driver, 1.6
[    0.741903] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.742216] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.742298] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.742339] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.742346] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.742512] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.742579] ehci_hcd 0000:00:1d.7: debug port 1
[    0.746469] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.752129] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa00000
[    0.768340] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.768734] hub 1-0:1.0: USB hub found
[    0.768751] hub 1-0:1.0: 6 ports detected
[    0.768923] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.768961] uhci_hcd: USB Universal Host Controller Interface driver
[    0.769080] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.769097] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.769103] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.769260] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.769317] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.769679] hub 2-0:1.0: USB hub found
[    0.769696] hub 2-0:1.0: 2 ports detected
[    0.769883] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.769900] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.769906] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.770083] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.770158] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.770514] hub 3-0:1.0: USB hub found
[    0.770528] hub 3-0:1.0: 2 ports detected
[    0.770686] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.770701] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.770707] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.770858] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.770920] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.771277] hub 4-0:1.0: USB hub found
[    0.771292] hub 4-0:1.0: 2 ports detected
[    0.771540] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.778083] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.778113] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.784635] mousedev: PS/2 mouse device common for all mice
[    0.828755] rtc_cmos 00:05: RTC can wake from S4
[    0.828921] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.828962] rtc0: alarms up to one day, 242 bytes nvram
[    0.829189] device-mapper: uevent: version 1.0.3
[    0.829472] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.829693] device-mapper: multipath: version 1.2.0 loaded
[    0.829701] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.829930] EISA: Probing bus 0 at eisa.0
[    0.829975] EISA: Detected 0 cards.
[    0.836096] cpuidle: using governor ladder
[    0.836104] cpuidle: using governor menu
[    0.836639] TCP cubic registered
[    0.837041] NET: Registered protocol family 10
[    0.838194] NET: Registered protocol family 17
[    0.838260] Registering the dns_resolver key type
[    0.838346] Using IPI No-Shortcut mode
[    0.838727] PM: Hibernation image not present or could not be loaded.
[    0.838760] registered taskstats version 1
[    0.839021]   Magic number: 3:950:354
[    0.839032] input event0: hash matches
[    0.839188] rtc_cmos 00:05: setting system clock to 2011-07-15 00:22:06 UTC (1310689326)
[    0.839195] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.839198] EDD information not available.
[    0.909127] ata1.00: ATA-7: Maxtor 6E040L0, NAR61HA0, max UDMA/100
[    0.909134] ata1.00: 78165360 sectors, multi 8: LBA 
[    0.909264] ata2.00: ATAPI: JLMS DVD-ROM XJ-HD166, DD05, max UDMA/33
[    0.909816] ata2.00: configured for UDMA/33
[    0.916290] ata1.00: configured for UDMA/100
[    1.152112] isapnp: No Plug & Play device found
[    1.152167] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.152495] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    1.152949] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.153564] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.153662] scsi 1:0:0:0: CD-ROM            JLMS     DVD-ROM XJ-HD166 DD05 PQ: 0 ANSI: 5
[    1.154319] sd 0:0:0:0: [sda] Write Protect is off
[    1.154328] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.154667] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.155045] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.155054] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.155342] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.155547] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.205696]  sda: sda1 sda2 < sda5 >
[    1.206765] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.372105] Refined TSC clocksource calibration: 2391.136 MHz.
[    1.372116] Switching to clocksource tsc
[    1.601518] Freeing initrd memory: 17764k freed
[    1.634018] Freeing unused kernel memory: 700k freed
[    1.635227] Write protecting the kernel text: 5192k
[    1.635276] Write protecting the kernel read-only data: 2148k
[    1.712151] <30>udev[67]: starting version 167
[    1.928092] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.239424] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.239431] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.239506] e100 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.365898] Floppy drive(s): fd0 is 1.44M
[    2.373031] e100 0000:01:0c.0: PME# disabled
[    2.374006] e100 0000:01:0c.0: eth0: addr 0xff8fe000, irq 18, MAC addr 00:0d:56:87:23:b2
[    2.379739] usbcore: registered new interface driver uas
[    2.384182] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    2.419788] FDC 0 is a post-1991 82077
[    2.491004] Initializing USB Mass Storage driver...
[    2.496473] scsi2 : usb-storage 1-2:1.0
[    2.499571] usbcore: registered new interface driver usb-storage
[    2.499578] USB Mass Storage support registered.
[    2.564213] [drm] Initialized drm 1.1.0 20060810
[    2.612076] hub 3-2:1.0: USB hub found
[    2.612962] hub 3-2:1.0: 3 ports detected
[    2.775765] input: ARROW STRONG USB 3D Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    2.776744] generic-usb 0003:0461:4D03.0001: input,hidraw0: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.1-1/input0
[    2.777534] usbcore: registered new interface driver usbhid
[    2.777542] usbhid: USB HID core driver
[    2.782820] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.782835] i915 0000:00:02.0: setting latency timer to 64
[    2.809454] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.809462] [drm] Driver supports precise vblank timestamp query.
[    2.823911] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.824321] [drm] initialized overlay support
[    2.957949] Console: switching to colour frame buffer device 160x64
[    2.958006] fb0: inteldrmfb frame buffer device
[    2.958009] drm: registered panic notifier
[    2.958236] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.966906] usb 3-2.1: new full speed USB device using uhci_hcd and address 4
[    3.115031] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.1/3-2.1:1.0/input/input3
[    3.115389] generic-usb 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2.1/input0
[    3.125031] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.1/3-2.1:1.1/input/input4
[    3.125361] generic-usb 0003:413C:2010.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2.1/input1
[    3.500984] scsi 2:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[    3.506220] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.506596] sd 2:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
[    3.507233] sd 2:0:0:0: [sdb] Write Protect is off
[    3.507244] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.508343] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.508352] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.511969] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.511979] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.524970]  sdb: sdb1
[    3.528212] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.528221] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.528230] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    3.810780] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.257379] Adding 520188k swap on /dev/sda5.  Priority:-1 extents:1 across:520188k 
[   10.376104] <30>udev[291]: starting version 167
[   10.483538] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.495938] lp: driver loaded but no devices found
[   11.299720] type=1400 audit(1310689336.954:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=378 comm="apparmor_parser"
[   11.338641] type=1400 audit(1310689336.994:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=378 comm="apparmor_parser"
[   11.339310] type=1400 audit(1310689336.994:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=378 comm="apparmor_parser"
[   12.454729] intel_rng: FWH not detected
[   12.569010] parport_pc 00:08: reported by Plug and Play ACPI
[   12.569073] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   12.625600] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.804547] lp0: using parport0 (interrupt-driven).
[   14.721151] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.644835] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.304261] ppdev: user-space parallel port driver
[   16.402634] type=1400 audit(1310689342.058:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=638 comm="apparmor_parser"
[   16.409065] type=1400 audit(1310689342.066:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
[   16.409748] type=1400 audit(1310689342.066:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
[   16.466864] type=1400 audit(1310689342.122:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=644 comm="apparmor_parser"
[   16.479275] type=1400 audit(1310689342.134:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=644 comm="apparmor_parser"
[   16.506427] type=1400 audit(1310689342.162:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=650 comm="apparmor_parser"
[   16.507093] type=1400 audit(1310689342.162:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=650 comm="apparmor_parser"
[   16.538583] type=1400 audit(1310689342.194:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam" pid=652 comm="apparmor_parser"
[   16.539264] type=1400 audit(1310689342.194:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam///usr/sbin/mysqld" pid=652 comm="apparmor_parser"
[   16.580207] type=1400 audit(1310689342.238:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=656 comm="apparmor_parser"
[   17.463838] ENS1371 0000:01:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.174449] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   40.664431] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1456.944525] usb 1-2: USB disconnect, address 2
[ 1590.524063] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 1590.783023] scsi3 : usb-storage 1-2:1.0
[ 1591.786081] scsi 3:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[ 1591.794150] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1591.795351] sd 3:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
[ 1591.795973] sd 3:0:0:0: [sdb] Write Protect is off
[ 1591.795983] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1591.797596] sd 3:0:0:0: [sdb] No Caching mode page present
[ 1591.797608] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1591.801471] sd 3:0:0:0: [sdb] No Caching mode page present
[ 1591.801483] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1591.962692]  sdb: sdb1
[ 1591.966316] sd 3:0:0:0: [sdb] No Caching mode page present
[ 1591.966327] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1591.966336] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1702.471346] usb 1-2: USB disconnect, address 5

Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
dm_crypt               22463  0 
snd_ens1371            24722  2 
gameport               15027  1 snd_ens1371
snd_ac97_codec        105614  1 snd_ens1371
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  0 
snd                    55295  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73312  0 
snd_page_alloc         14073  1 snd_pcm
joydev                 17322  0 
serio_raw              12990  0 
parport_pc             32111  1 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  450944  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
drm_kms_helper         40745  1 i915
drm                   180037  2 i915,drm_kms_helper
usb_storage            43946  0 
uas                    17676  0 
floppy                 60032  0 
e100                   40108  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

---

