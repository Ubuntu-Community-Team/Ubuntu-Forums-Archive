---
title: "Has my wireless died?"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Odemia on 2009-11-11
[FONT=Arial][COLOR=Black]When I booted my laptop today the wireless would not work.  After working on the problem for a while now I am frustrated and need advice.  Take a look and let me know what else I can try.

Laptop in question is MSI U210 Wind with the RaLink rt3090 chipset.  I am using the [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") (ppa:markus-tisoft/rt3090) to install the rt3090-dkms package.  Everything was working (for several weeks) with the network manager in Ubuntu 8.10, Kubuntu 9.04 and Kubuntu 9.10.  I have booted into all 3 and can't get any of them to show any essids.
[/COLOR][/FONT]
Basically I have narrowed the issue down to the wireless chipset not seeing any networks in the area.
```
$ iwlist ra0 scan
ra0       No scan results

```
iwlist commands appear ineffective.  What else can I try?

Below is more thorough info.
```
$ uname -mr
2.6.31-14-generic i686

$ lspci -nn | grep RaLink
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

$ iwconfig ra0
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod | grep rt3090sta
rt3090sta             722896  1

$ cat /proc/modules | grep rt3090sta
rt3090sta 722896 1 - Live 0xf815d000 (P)

$ sudo lshw -C network                                        
[sudo] password for <user>:                                                  
  *-network                                                               
       description: Wireless interface                                    
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 00:24:21:cb:41:57
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:24:21:6f:fa:50
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:fdf00000-fdf1ffff(prefetchable)



``````
$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu   
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)                                        
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)   
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fb0000 (usable)   
[    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077fe0000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 0000000077fe0000 - 0000000078000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved) 
[    0.000000] DMI present.                                               
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.                                                                      
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)                                                       
[    0.000000] last_pfn = 0x77fb0 max_arch_pfn = 0x100000                 
[    0.000000] MTRR default type: uncachable                              
[    0.000000] MTRR fixed ranges enabled:                                 
[    0.000000]   00000-9FFFF write-back                                   
[    0.000000]   A0000-BFFFF uncachable                                   
[    0.000000]   C0000-CFFFF write-protect                                
[    0.000000]   D0000-EFFFF uncachable                                   
[    0.000000]   F0000-FFFFF write-protect                                
[    0.000000] MTRR variable ranges enabled:                              
[    0.000000]   0 base 0000000000 mask FF80000000 write-back             
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
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)    
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)  
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)  
[    0.000000]  modified: 0000000000100000 - 0000000077fb0000 (usable)    
[    0.000000]  modified: 0000000077fb0000 - 0000000077fbe000 (ACPI data) 
[    0.000000]  modified: 0000000077fbe000 - 0000000077fe0000 (ACPI NVS)  
[    0.000000]  modified: 0000000077fe0000 - 0000000078000000 (reserved)  
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)  
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)  
[    0.000000] initial memory mapped : 0 - 00c00000                       
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000     
[    0.000000] Using x86 segment limits to approximate NX protection      
[    0.000000]  0000000000 - 0000400000 page 4k                           
[    0.000000]  0000400000 - 0037400000 page 2M                           
[    0.000000]  0037400000 - 00377fe000 page 4k                           
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000  
[    0.000000] RAMDISK: 37853000 - 37feffdd                               
[    0.000000] Allocated new RAMDISK: 008ad000 - 01049fdd                 
[    0.000000] Move RAMDISK from 0000000037853000 - 0000000037feffdc to 008ad000 - 01049fdc                                                         
[    0.000000] ACPI: RSDP 000f9fd0 00024 (v02 ACPIAM)                     
[    0.000000] ACPI: XSDT 77fb0100 00064 (v01 MSI_NB MEGABOOK 20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: FACP 77fb0290 000F4 (v03 071409 FACP1025 20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: DSDT 77fb0610 059AF (v01  MPSA0 MPSA0B12 00000000 INTL 20051117)                                                               
[    0.000000] ACPI: FACS 77fbe000 00040                                  
[    0.000000] ACPI: APIC 77fb0390 0006C (v01 071409 APIC1025 20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: MCFG 77fb0400 0003C (v01 071409 OEMMCFG  20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: SLIC 77fb0440 00176 (v01 MSI_NB MEGABOOK 20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: WDRT 77fb05c0 00047 (v01 071409 OEMWDRT  20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: OEMB 77fbe040 00071 (v01 071409 OEMB1025 20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: HPET 77fb5fc0 00038 (v01 071409 OEMHPET  20090714 MSFT 00000097)                                                               
[    0.000000] ACPI: SSDT 77fb6000 00108 (v01 A M I  POWERNOW 00000001 AMD  00000001)                                                               
[    0.000000] ACPI: Local APIC address 0xfee00000                        
[    0.000000] 1031MB HIGHMEM available.                                  
[    0.000000] 887MB LOWMEM available.                                    
[    0.000000]   mapped low ram: 0 - 377fe000                             
[    0.000000]   low ram: 0 - 377fe000                                    
[    0.000000]   node 0 low ram: 00000000 - 377fe000                      
[    0.000000]   node 0 bootmap 00011000 - 00017f00                       
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]                                                                         
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                        
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                        
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                        
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]                                                        
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]                                                        
[    0.000000]   #5 [00008a9000 - 00008ac16f]              BRK ==> [00008a9000 - 00008ac16f]                                                        
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]                                                        
[    0.000000]   #7 [00008ad000 - 0001049fdd]      NEW RAMDISK ==> [00008ad000 - 0001049fdd]                                                        
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]                                                        
[    0.000000] found SMP MP-table at [c00ff780] ff780                     
[    0.000000] Zone PFN ranges:                                           
[    0.000000]   DMA      0x00000010 -> 0x00001000                        
[    0.000000]   Normal   0x00001000 -> 0x000377fe                        
[    0.000000]   HighMem  0x000377fe -> 0x00077fb0                        
[    0.000000] Movable zone start PFN for each node                       
[    0.000000] early_node_map[2] active PFN ranges                        
[    0.000000]     0: 0x00000010 -> 0x0000009f                            
[    0.000000]     0: 0x00000100 -> 0x00077fb0                            
[    0.000000] On node 0 totalpages: 491327                               
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c104a200                                                                   
[    0.000000]   DMA zone: 32 pages used for memmap                       
[    0.000000]   DMA zone: 0 pages reserved                               
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0                       
[    0.000000]   Normal zone: 1744 pages used for memmap                  
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31                 
[    0.000000]   HighMem zone: 2064 pages used for memmap                 
[    0.000000]   HighMem zone: 262050 pages, LIFO batch:31                
[    0.000000] Using APIC driver default                                  
[    0.000000] Detected use of extended apic ids on hypertransport bus    
[    0.000000] ACPI: PM-Timer IO Port: 0x808                              
[    0.000000] ACPI: Local APIC address 0xfee00000                        
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)         
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)        
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)        
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)        
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])    
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23                                                                       
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level) 
[    0.000000] ACPI: IRQ0 used by override.                               
[    0.000000] ACPI: IRQ2 used by override.                               
[    0.000000] ACPI: IRQ9 used by override.                               
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs              
[    0.000000] Using ACPI (MADT) for SMP configuration information        
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000                     
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs                       
[    0.000000] nr_irqs_gsi: 24                                            
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000                                                                    
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 78000000:68000000)                                                               
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1     
[    0.000000] PERCPU: Embedded 14 pages at c1f54000, static data 35612 bytes                                                                       
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487487                                                          
[    0.000000] Kernel command line: root=UUID=0c445192-4fff-449a-8dfe-6dc497d84b91 ro quiet splash                                                  
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)      
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                                                     
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                                                       
[    0.000000] Enabling fast FPU save and restore... done.                
[    0.000000] Enabling unmasked SIMD FPU exception support... done.      
[    0.000000] Initializing CPU#0                                         
[    0.000000] allocated 9828480 bytes of page_cgroup                     
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                                           
[    0.000000] Initializing HighMem for node 0 (000377fe:00077fb0)        
[    0.000000] Memory: 1922716k/1965760k available (4565k kernel code, 41692k reserved, 2143k data, 540k init, 1056456k highmem)                    
[    0.000000] virtual kernel memory layout:                              
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)          
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)          
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)          
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)          
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)          
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)          
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)          
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                          
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                                                              
[    0.000000] NR_IRQS:2304 nr_irqs:440                                   
[    0.000000] Extended CMOS year: 2000                                   
[    0.000000] Fast TSC calibration using PIT                             
[    0.000000] Detected 1595.959 MHz processor.                           
[    0.000774] Console: colour VGA+ 80x25                                 
[    0.000779] console [tty0] enabled                                     
[    0.001005] hpet clockevent registered                                 
[    0.001010] HPET: 4 timers in total, 0 timers will be used for per-cpu timer                                                                     
[    0.001019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.91 BogoMIPS (lpj=6383836)                            
[    0.001045] Security Framework initialized                             
[    0.001071] AppArmor: AppArmor initialized                             
[    0.001081] Mount-cache hash table entries: 512                        
[    0.001254] Initializing cgroup subsys ns                              
[    0.001259] Initializing cgroup subsys cpuacct                         
[    0.001264] Initializing cgroup subsys memory                          
[    0.001272] Initializing cgroup subsys freezer                         
[    0.001275] Initializing cgroup subsys net_cls                         
[    0.001292] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                                                    
[    0.001295] CPU: L2 Cache: 512K (64 bytes/line)                        
[    0.001300] mce: CPU supports 5 MCE banks                              
[    0.001312] using C1E aware idle routine                               
[    0.001322] Performance Counters: AMD PMU driver.                      
[    0.001330] ... version:                 0                             
[    0.001332] ... bit width:               48                            
[    0.001335] ... generic counters:        4                             
[    0.001337] ... value mask:              0000ffffffffffff              
[    0.001340] ... max period:              00007fffffffffff              
[    0.001342] ... fixed-purpose counters:  0                             
[    0.001345] ... counter mask:            000000000000000f              
[    0.001350] Checking 'hlt' instruction... OK.                          
[    0.016931] SMP alternatives: switching to UP code                     
[    0.024010] ACPI: Core revision 20090521                               
[    0.036406] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1       
[    0.077316] CPU0: AMD Athlon(tm) Neo Processor MV-40 stepping 02       
[    0.080001] Brought up 1 CPUs                                          
[    0.080001] Total of 1 processors activated (3191.91 BogoMIPS).        
[    0.080001] CPU0 attaching NULL sched-domain.                          
[    0.080001] Booting paravirtualized kernel on bare hardware            
[    0.080001] regulator: core version 0.5                                
[    0.080001] Time: 23:45:27  Date: 11/11/09                             
[    0.080001] NET: Registered protocol family 16                         
[    0.080001] EISA bus registered                                        
[    0.080001] ACPI: bus type pci registered                              
[    0.080001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                                     
[    0.080001] PCI: MCFG area at e0000000 reserved in E820                
[    0.080001] PCI: Using MMCONFIG for extended config space              
[    0.080001] PCI: Using configuration type 1 for base access            
[    0.080001] bio: create slab <bio-0> at 0                              
[    0.080001] ACPI: EC: Enabling special treatment for EC from MSI.      
[    0.080001] ACPI: EC: Look up EC in DSDT                               
[    0.084299] ACPI: Interpreter enabled                                  
[    0.084306] ACPI: (supports S0 S1 S3 S4 S5)                            
[    0.084336] ACPI: Using IOAPIC for interrupt routing                   
[    0.087716] ACPI: EC: non-query interrupt received, switching to interrupt mode                                                                  
[    0.102708] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62                                                                         
[    0.102711] ACPI: EC: driver started in interrupt mode                 
[    0.102991] ACPI: No dock devices found.                               
[    0.104244] ACPI: PCI Root Bridge [PCI0] (0000:00)                     
[    0.104368] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold      
[    0.104372] pci 0000:00:04.0: PME# disabled                            
[    0.104408] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold      
[    0.104411] pci 0000:00:05.0: PME# disabled                            
[    0.104472] pci 0000:00:12.0: reg 10 io port: [0xc000-0xc007]          
[    0.104480] pci 0000:00:12.0: reg 14 io port: [0xb000-0xb003]          
[    0.104489] pci 0000:00:12.0: reg 18 io port: [0xa000-0xa007]          
[    0.104497] pci 0000:00:12.0: reg 1c io port: [0x9000-0x9003]          
[    0.104505] pci 0000:00:12.0: reg 20 io port: [0x8000-0x800f]          
[    0.104514] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe7ffc00-0xfe7fffff]                                                                         
[    0.104534] pci 0000:00:12.0: set SATA to AHCI mode                    
[    0.104579] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe7fe000-0xfe7fefff]                                                                         
[    0.104641] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe7fd000-0xfe7fdfff]                                                                         
[    0.104702] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe7fc000-0xfe7fcfff]                                                                         
[    0.104763] pci 0000:00:13.3: reg 10 32bit mmio: [0xfe7fb000-0xfe7fbfff]                                                                         
[    0.104824] pci 0000:00:13.4: reg 10 32bit mmio: [0xfe7fa000-0xfe7fafff]                                                                         
[    0.104905] pci 0000:00:13.5: reg 10 32bit mmio: [0xfe7ff800-0xfe7ff8ff]                                                                         
[    0.104962] pci 0000:00:13.5: supports D1 D2                           
[    0.104965] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot       
[    0.104970] pci 0000:00:13.5: PME# disabled                            
[    0.105020] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]            
[    0.105114] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe7f4000-0xfe7f7fff]                                                                         
[    0.105161] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold      
[    0.105166] pci 0000:00:14.2: PME# disabled                            
[    0.105380] pci 0000:01:05.0: reg 10 64bit mmio: [0xf0000000-0xf7ffffff]                                                                         
[    0.105387] pci 0000:01:05.0: reg 18 64bit mmio: [0xfe9f0000-0xfe9fffff]                                                                         
[    0.105393] pci 0000:01:05.0: reg 20 io port: [0xd000-0xd0ff]          
[    0.105398] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe800000-0xfe8fffff]                                                                         
[    0.105411] pci 0000:01:05.0: supports D1 D2                           
[    0.105434] pci 0000:01:05.2: reg 10 64bit mmio: [0xfe9e8000-0xfe9ebfff]                                                                         
[    0.105473] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]          
[    0.105477] pci 0000:00:01.0: bridge 32bit mmio: [0xfe800000-0xfe9fffff]                                                                         
[    0.105482] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]                                                                    
[    0.105537] pci 0000:02:00.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]                                                                         
[    0.105673] pci 0000:00:04.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]                                                                         
[    0.105714] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]          
[    0.105731] pci 0000:03:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]                                                                         
[    0.105744] pci 0000:03:00.0: reg 20 64bit mmio: [0xfdff8000-0xfdffbfff]                                                                         
[    0.105752] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]   
[    0.105785] pci 0000:03:00.0: supports D1 D2                           
[    0.105788] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105793] pci 0000:03:00.0: PME# disabled                            
[    0.105861] pci 0000:00:05.0: bridge io port: [0xe000-0xefff]          
[    0.105865] pci 0000:00:05.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]                                                                         
[    0.105870] pci 0000:00:05.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]                                                                    
[    0.105932] pci 0000:00:14.4: transparent bridge                       
[    0.105955] pci_bus 0000:00: on NUMA node 0                            
[    0.105961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]        
[    0.106134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]   
[    0.106285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]   
[    0.106374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]   
[    0.111523] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.111651] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.111780] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.111912] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.112111] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.112237] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.     
[    0.112365] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.112493] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                          
[    0.112712] SCSI subsystem initialized                                 
[    0.112793] libata version 3.00 loaded.                                
[    0.112882] usbcore: registered new interface driver usbfs             
[    0.112903] usbcore: registered new interface driver hub               
[    0.112930] usbcore: registered new device driver usb                  
[    0.113143] ACPI: WMI: Mapper loaded                                   
[    0.113145] PCI: Using ACPI for IRQ routing                            
[    0.113367] Bluetooth: Core ver 2.15                                   
[    0.113399] NET: Registered protocol family 31                         
[    0.113402] Bluetooth: HCI device and connection manager initialized   
[    0.113406] Bluetooth: HCI socket layer initialized                    
[    0.113408] NetLabel: Initializing                                     
[    0.113410] NetLabel:  domain hash size = 128                          
[    0.113412] NetLabel:  protocols = UNLABELED CIPSOv4                   
[    0.113431] NetLabel:  unlabeled traffic allowed by default            
[    0.113467] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0                 
[    0.113474] hpet0: 4 comparators, 32-bit 14.318180 MHz counter         
[    0.117973] pnp: PnP ACPI init                                         
[    0.118004] ACPI: bus type pnp registered                              
[    0.120025] Switched to high resolution mode on CPU 0                  
[    0.126684] pnp: PnP ACPI: found 13 devices                            
[    0.126687] ACPI: ACPI bus type pnp unregistered                       
[    0.126691] PnPBIOS: Disabled by ACPI PNP                              
[    0.126706] system 00:01: iomem range 0x78000000-0x7fffffff has been reserved                                                                    
[    0.126715] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved                                                                
[    0.126719] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved                                                                    
[    0.126728] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved   
[    0.126732] system 00:0a: ioport range 0x40b-0x40b has been reserved   
[    0.126736] system 00:0a: ioport range 0x4d6-0x4d6 has been reserved   
[    0.126740] system 00:0a: ioport range 0xb00-0xb0f has been reserved   
[    0.126744] system 00:0a: ioport range 0xc00-0xc01 has been reserved   
[    0.126748] system 00:0a: ioport range 0xc14-0xc14 has been reserved   
[    0.126752] system 00:0a: ioport range 0xc50-0xc51 has been reserved   
[    0.126755] system 00:0a: ioport range 0xc52-0xc52 has been reserved   
[    0.126759] system 00:0a: ioport range 0xc6c-0xc6c has been reserved   
[    0.126763] system 00:0a: ioport range 0xc6f-0xc6f has been reserved   
[    0.126767] system 00:0a: ioport range 0xcd0-0xcd1 has been reserved   
[    0.126771] system 00:0a: ioport range 0xcd2-0xcd3 has been reserved   
[    0.126775] system 00:0a: ioport range 0xcd4-0xcd5 has been reserved   
[    0.126779] system 00:0a: ioport range 0xcd6-0xcd7 has been reserved   
[    0.126783] system 00:0a: ioport range 0xcd8-0xcdf has been reserved   
[    0.126787] system 00:0a: ioport range 0x800-0x89f has been reserved   
[    0.126791] system 00:0a: ioport range 0xb10-0xb1f has been reserved   
[    0.126795] system 00:0a: ioport range 0x900-0x90f has been reserved   
[    0.126799] system 00:0a: ioport range 0x910-0x91f has been reserved   
[    0.126803] system 00:0a: ioport range 0xfe00-0xfefe has been reserved 
[    0.126807] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved                                                                    
[    0.126814] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved                                                                    
[    0.126821] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.126825] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved                                                                      
[    0.126829] system 00:0c: iomem range 0x100000-0x77ffffff could not be reserved                                                                  
[    0.126834] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved                                                                
[    0.161552] AppArmor: AppArmor Filesystem Enabled                      
[    0.161590] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01        
[    0.161594] pci 0000:00:01.0:   IO window: 0xd000-0xdfff               
[    0.161598] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe9fffff      
[    0.161603] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff                                                               
[    0.161608] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02        
[    0.161611] pci 0000:00:04.0:   IO window: disabled                    
[    0.161615] pci 0000:00:04.0:   MEM window: 0xfea00000-0xfeafffff      
[    0.161619] pci 0000:00:04.0:   PREFETCH window: disabled              
[    0.161626] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03        
[    0.161630] pci 0000:00:05.0:   IO window: 0xe000-0xefff               
[    0.161634] pci 0000:00:05.0:   MEM window: 0xfeb00000-0xfebfffff      
[    0.161639] pci 0000:00:05.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff                                                               
[    0.161644] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04        
[    0.161647] pci 0000:00:14.4:   IO window: disabled                    
[    0.161656] pci 0000:00:14.4:   MEM window: disabled                   
[    0.161661] pci 0000:00:14.4:   PREFETCH window: disabled              
[    0.161676] pci 0000:00:04.0: setting latency timer to 64              
[    0.161682] pci 0000:00:05.0: setting latency timer to 64              
[    0.161692] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]             
[    0.161696] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]     
[    0.161700] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]           
[    0.161703] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe9fffff]   
[    0.161707] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]                                                                         
[    0.161710] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]   
[    0.161714] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]           
[    0.161718] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]   
[    0.161721] pci_bus 0000:03: resource 2 pref mem [0xfdf00000-0xfdffffff]                                                                         
[    0.161725] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]             
[    0.161728] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]     
[    0.161775] NET: Registered protocol family 2                          
[    0.161897] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                                                    
[    0.162315] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                                 
[    0.163305] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.163836] TCP: Hash tables configured (established 131072 bind 65536)
[    0.163839] TCP reno registered                                        
[    0.163968] NET: Registered protocol family 1                          
[    0.164080] Trying to unpack rootfs image as initramfs...              
[    0.445131] Freeing initrd memory: 7795k freed                         
[    0.452895] cpufreq-nforce2: No nForce2 chipset.                       
[    0.452927] Scanning for low memory corruption every 60 seconds        
[    0.453053] audit: initializing netlink socket (disabled)              
[    0.453072] type=2000 audit(1257983126.452:1): initialized             
[    0.464483] highmem bounce pool size: 64 pages                         
[    0.464490] HugeTLB registered 4 MB page size, pre-allocated 0 pages   
[    0.466228] VFS: Disk quotas dquot_6.5.2                               
[    0.466301] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.467009] fuse init (API version 7.12)                               
[    0.467107] msgmni has been set to 1708                                
[    0.467328] alg: No test for stdrng (krng)                             
[    0.467341] io scheduler noop registered                               
[    0.467344] io scheduler anticipatory registered                       
[    0.467346] io scheduler deadline registered                           
[    0.467400] io scheduler cfq registered (default)                      
[    0.596047] pci 0000:01:05.0: Boot video device                        
[    0.596172]   alloc irq_desc for 24 on node -1                         
[    0.596175]   alloc kstat_irqs on node -1                              
[    0.596185] pcieport-driver 0000:00:04.0: irq 24 for MSI/MSI-X         
[    0.596192] pcieport-driver 0000:00:04.0: setting latency timer to 64  
[    0.596284]   alloc irq_desc for 25 on node -1                         
[    0.596286]   alloc kstat_irqs on node -1                              
[    0.596292] pcieport-driver 0000:00:05.0: irq 25 for MSI/MSI-X         
[    0.596297] pcieport-driver 0000:00:05.0: setting latency timer to 64  
[    0.596380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5            
[    0.596694] pciehp 0000:00:04.0:pcie04: HPC vendor_id 1002 device_id 7914 ss_vid 0 ss_did 0                                                      
[    0.596734] pciehp 0000:00:04.0:pcie04: service driver pciehp loaded   
[    0.596749] pciehp 0000:00:05.0:pcie04: HPC vendor_id 1002 device_id 7915 ss_vid 0 ss_did 0                                                      
[    0.596777] pciehp 0000:00:05.0:pcie04: service driver pciehp loaded   
[    0.596786] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.603320] ACPI: AC Adapter [ADP1] (on-line)                          
[    0.603393] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                 
[    0.603398] ACPI: Power Button [PWRF]                                  
[    0.603471] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:14/PNP0C09:00/PNP0C0D:00/input/input1                          
[    0.606551] ACPI: Lid Switch [LID0]                                    
[    0.606613] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2                                                        
[    0.606617] ACPI: Power Button [PWRB]                                  
[    0.606927] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])            
[    0.606958] processor LNXCPU:00: registered as cooling_device0         
[    0.606962] ACPI: Processor [CPU0] (supports 8 throttling states)      
[    0.621385] thermal LNXTHERM:01: registered as thermal_zone0           
[    0.621394] ACPI: Thermal Zone [THRM] (40 C)                           
[    0.621450] isapnp: Scanning for PnP cards...                          
[    0.981797] isapnp: No Plug & Play device found                        
[    0.983770] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled    
[    0.985328] brd: module loaded                                         
[    0.985885] loop: module loaded                                        
[    0.985978] input: Macintosh mouse button emulation as /devices/virtual/input/input3                                                             
[    0.986053] ahci 0000:00:12.0: version 3.0                             
[    0.986076]   alloc irq_desc for 22 on node -1                         
[    0.986079]   alloc kstat_irqs on node -1                              
[    0.986087] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                                                        
[    0.986227] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode                                                         
[    0.986232] ahci 0000:00:12.0: flags: 64bit ncq sntf ilck led clo pmp pio                                                                        
[    0.987406] scsi0 : ahci                                               
[    0.987556] scsi1 : ahci                                               
[    0.987621] scsi2 : ahci                                               
[    0.987696] scsi3 : ahci                                               
[    0.987834] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22                                                                 
[    0.987839] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22                                                                 
[    0.987844] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22                                                                 
[    0.987848] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22                                                                 
[    0.989051] Fixed MDIO Bus: probed                                     
[    0.989099] PPP generic driver version 2.4.2                           
[    0.989243] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.989275]   alloc irq_desc for 19 on node -1                         
[    0.989278]   alloc kstat_irqs on node -1                              
[    0.989285] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19                                                                    
[    0.989307] ehci_hcd 0000:00:13.5: EHCI Host Controller                
[    0.989374] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1                                                                 
[    0.989422] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround                                                                
[    0.989443] ehci_hcd 0000:00:13.5: debug port 1                        
[    0.989462] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe7ff800           
[    1.000282] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00          
[    1.000407] usb usb1: configuration #1 chosen from 1 choice            
[    1.000444] hub 1-0:1.0: USB hub found                                 
[    1.000455] hub 1-0:1.0: 10 ports detected                             
[    1.000575] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver     
[    1.000598]   alloc irq_desc for 16 on node -1                         
[    1.000601]   alloc kstat_irqs on node -1                              
[    1.000607] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                    
[    1.000619] ohci_hcd 0000:00:13.0: OHCI Host Controller                
[    1.000656] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2                                                                 
[    1.000686] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe7fe000           
[    1.060082] usb usb2: configuration #1 chosen from 1 choice            
[    1.060114] hub 2-0:1.0: USB hub found                                 
[    1.060128] hub 2-0:1.0: 2 ports detected                              
[    1.060181]   alloc irq_desc for 17 on node -1                         
[    1.060184]   alloc kstat_irqs on node -1                              
[    1.060189] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                    
[    1.060200] ohci_hcd 0000:00:13.1: OHCI Host Controller                
[    1.060240] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3                                                                 
[    1.060267] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe7fd000           
[    1.120080] usb usb3: configuration #1 chosen from 1 choice            
[    1.120111] hub 3-0:1.0: USB hub found                                 
[    1.120125] hub 3-0:1.0: 2 ports detected                              
[    1.120176]   alloc irq_desc for 18 on node -1                         
[    1.120179]   alloc kstat_irqs on node -1                              
[    1.120184] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                                    
[    1.120194] ohci_hcd 0000:00:13.2: OHCI Host Controller                
[    1.120238] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4                                                                 
[    1.120266] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe7fc000           
[    1.140088] ACPI: Battery Slot [BAT1] (battery present)                
[    1.180084] usb usb4: configuration #1 chosen from 1 choice            
[    1.180115] hub 4-0:1.0: USB hub found                                 
[    1.180130] hub 4-0:1.0: 2 ports detected                              
[    1.180182] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                    
[    1.180193] ohci_hcd 0000:00:13.3: OHCI Host Controller                
[    1.180230] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5                                                                 
[    1.180250] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe7fb000           
[    1.240091] usb usb5: configuration #1 chosen from 1 choice            
[    1.240123] hub 5-0:1.0: USB hub found                                 
[    1.240137] hub 5-0:1.0: 2 ports detected                              
[    1.240189] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                                    
[    1.240200] ohci_hcd 0000:00:13.4: OHCI Host Controller                
[    1.240242] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6                                                                 
[    1.240265] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe7fa000           
[    1.300081] usb usb6: configuration #1 chosen from 1 choice            
[    1.300113] hub 6-0:1.0: USB hub found                                 
[    1.300128] hub 6-0:1.0: 2 ports detected                              
[    1.300191] uhci_hcd: USB Universal Host Controller Interface driver   
[    1.300307] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12                                                               
[    1.308142] ata1: SATA link down (SStatus 0 SControl 300)              
[    1.308206] ata4: SATA link down (SStatus 0 SControl 300)              
[    1.308237] ata2: SATA link down (SStatus 0 SControl 300)              
[    1.326758] serio: i8042 KBD port at 0x60,0x64 irq 1                   
[    1.326764] serio: i8042 AUX port at 0x60,0x64 irq 12                  
[    1.326834] mice: PS/2 mouse device common for all mice                
[    1.326970] rtc_cmos 00:03: RTC can wake from S4                       
[    1.327013] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0      
[    1.327045] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs                                                                        
[    1.327182] device-mapper: uevent: version 1.0.3                       
[    1.327307] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com                                                     
[    1.328077] device-mapper: multipath: version 1.1.0 loaded             
[    1.328081] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    1.328252] EISA: Probing bus 0 at eisa.0                              
[    1.328291] Cannot allocate resource for EISA slot 8                   
[    1.328294] EISA: Detected 0 cards.                                    
[    1.328387] cpuidle: using governor ladder                             
[    1.328454] cpuidle: using governor menu                               
[    1.329069] TCP cubic registered                                       
[    1.329282] NET: Registered protocol family 10                         
[    1.329846] lo: Disabled Privacy Extensions                            
[    1.330210] NET: Registered protocol family 17                         
[    1.330232] Bluetooth: L2CAP ver 2.13                                  
[    1.330234] Bluetooth: L2CAP socket layer initialized                  
[    1.330237] Bluetooth: SCO (Voice Link) ver 0.6                        
[    1.330239] Bluetooth: SCO socket layer initialized                    
[    1.330277] Bluetooth: RFCOMM TTY layer initialized                    
[    1.330281] Bluetooth: RFCOMM socket layer initialized                 
[    1.330283] Bluetooth: RFCOMM ver 1.11                                 
[    1.330300] powernow-k8: Found 1 AMD Athlon(tm) Neo Processor MV-40 processors (1 cpu cores) (version 2.20.00)                                   
[    1.330344] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16           
[    1.330348] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16            
[    1.330653] Using IPI No-Shortcut mode                                 
[    1.330738] PM: Resume from disk failed.                               
[    1.330753] registered taskstats version 1                             
[    1.330916]   Magic number: 1:534:807                                  
[    1.330972] misc snapshot: hash matches                                
[    1.331042] rtc_cmos 00:03: setting system clock to 2009-11-11 23:45:28 UTC (1257983128)                                                         
[    1.331047] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found       
[    1.331049] EDD information not available.                             
[    1.348035] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4                                                   
[    1.476038] ata3: softreset failed (device not ready)                  
[    1.476042] ata3: applying SB600 PMP SRST workaround and retrying      
[    1.484039] usb 1-6: new high speed USB device using ehci_hcd and address 2                                                                      
[    1.627278] usb 1-6: configuration #1 chosen from 1 choice             
[    1.640091] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)     
[    1.695858] ata3.00: ATA-8: TOSHIBA MK2555GSX, FG001A, max UDMA/100    
[    1.695862] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)                                                                        
[    1.695886] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd       
[    1.696689] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd       
[    1.696693] ata3.00: configured for UDMA/100                           
[    1.696824] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5                                                         
[    1.696962] sd 2:0:0:0: Attached scsi generic sg0 type 0               
[    1.697010] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)                                                                
[    1.697060] sd 2:0:0:0: [sda] Write Protect is off                     
[    1.697063] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                  
[    1.697090] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                              
[    1.697233]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >         
[    1.834073] sd 2:0:0:0: [sda] Attached SCSI disk                       
[    1.834095] Freeing unused kernel memory: 540k freed                   
[    1.834604] Write protecting the kernel text: 4568k                    
[    1.834643] Write protecting the kernel read-only data: 1836k          
[    2.039267] Linux agpgart interface v0.103                             
[    2.134207] acpi device:06: registered as cooling_device1              
[    2.134344] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03/input/input5                                       
[    2.134396] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)                                                                        
[    2.222838] [drm] Initialized drm 1.1.0 20060810                       
[    2.246037] [drm] radeon default to kernel modesetting DISABLED.       
[    2.246383] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                                         
[    2.246521] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0                                                                 
[    2.251569] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded            
[    2.251590] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                                       
[    2.251625] r8169 0000:03:00.0: setting latency timer to 64            
[    2.251662]   alloc irq_desc for 26 on node -1                         
[    2.251665]   alloc kstat_irqs on node -1                              
[    2.251679] r8169 0000:03:00.0: irq 26 for MSI/MSI-X                   
[    2.258495] Initializing USB Mass Storage driver...                    
[    2.261442] eth0: RTL8168d/8111d at 0xf82f2000, 00:24:21:6f:fa:50, XID 281000c0 IRQ 26                                                           
[    2.265319] scsi4 : SCSI emulation for USB Mass Storage devices        
[    2.265419] usbcore: registered new interface driver usb-storage       
[    2.265424] USB Mass Storage support registered.                       
[    2.266085] usb-storage: device found at 2                             
[    2.266088] usb-storage: waiting for device to settle before scanning  
[    3.288612] PM: Starting manual resume from disk                       
[    3.288618] PM: Resume from partition 8:10                             
[    3.288621] PM: Checking hibernation image.                            
[    3.288770] PM: Resume from disk failed.                               
[    3.338839] kjournald starting.  Commit interval 5 seconds             
[    3.338857] EXT3-fs: mounted filesystem with writeback data mode.      
[    4.196610] type=1505 audit(1257983131.364:2): operation="profile_load" pid=401 name=/sbin/dhclient3                                             
[    4.196981] type=1505 audit(1257983131.364:3): operation="profile_load" pid=401 name=/usr/lib/NetworkManager/nm-dhcp-client.action               
[    4.197191] type=1505 audit(1257983131.364:4): operation="profile_load" pid=401 name=/usr/lib/connman/scripts/dhclient-script                    
[    4.239623] type=1505 audit(1257983131.404:5): operation="profile_load" pid=403 name=/usr/lib/cups/backend/cups-pdf                              
[    4.240104] type=1505 audit(1257983131.408:6): operation="profile_load" pid=403 name=/usr/sbin/cupsd                                             
[    4.256801] type=1505 audit(1257983131.424:7): operation="profile_load" pid=404 name=/usr/sbin/mysqld-akonadi                                    
[    4.264716] type=1505 audit(1257983131.432:8): operation="profile_load" pid=405 name=/usr/sbin/tcpdump                                           
[    5.473951] Adding 4915848k swap on /dev/sda10.  Priority:-1 extents:1 across:4915848k                                                           
[    6.214444] udev: starting version 147                                 
[    7.264758] usb-storage: device scan complete                          
[    7.266859] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS                                                     
[    7.267336] sd 4:0:0:0: Attached scsi generic sg1 type 0               
[    7.278354] sd 4:0:0:0: [sdb] Attached SCSI removable disk             
[    7.631932] rt3090sta: module license 'unspecified' taints kernel.     
[    7.631938] Disabling lock debugging due to kernel taint               
[    7.635818] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                      
[    7.635858] rt2860 0000:02:00.0: setting latency timer to 64           
[    7.636269]                                                            
[    7.636270]                                                            
[    7.636271] === pAd = f8649000, size = 487256 ===                      
[    7.636272]                                                            
[    7.636275] <-- RTMPAllocAdapterBlock, Status=0                        
[    7.636278] pAd->CSRBaseAddress =0xf8100000, csr_addr=0xf8100000!      
[    7.647975] input: PC Speaker as /devices/platform/pcspkr/input/input6 
[    7.650521] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0                                                                 
[    7.655500] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                                                         
[    7.675890] lp: driver loaded but no devices found                     
[    7.680925] ip_tables: (C) 2000-2006 Netfilter Core Team               
[    7.682426] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141                                                        
[    8.696990] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000                                                          
[    8.782608] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7                                                     
[    9.125976] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                   
[    9.357301] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...                                                                  
[    9.357459] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8                                                           
[    9.361107] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                                                   
[   12.262846] EXT3 FS on sda6, internal journal                          
[   13.039673] kjournald starting.  Commit interval 5 seconds             
[   13.039902] EXT3 FS on sda5, internal journal                          
[   13.039908] EXT3-fs: mounted filesystem with writeback data mode.      
[   14.048648] kjournald starting.  Commit interval 5 seconds             
[   14.049244] EXT3 FS on sda7, internal journal                          
[   14.049250] EXT3-fs: mounted filesystem with writeback data mode.      
[   16.408299] kjournald starting.  Commit interval 5 seconds             
[   16.414445] EXT3 FS on sda8, internal journal                          
[   16.414452] EXT3-fs: mounted filesystem with writeback data mode.      
[   17.526919] kjournald starting.  Commit interval 5 seconds             
[   17.527221] EXT3 FS on sda9, internal journal                          
[   17.527228] EXT3-fs: mounted filesystem with writeback data mode.      
[   17.777456] RX DESC f65cb000  size = 2048                              
[   17.777922] <-- RTMPAllocTxRxRingMemory, Status=0                      
[   17.812711] PhyMode=9, DesiredPhyMode=9                                
[   17.813102] Key1Str is Invalid key length(0) or Type(0)                
[   17.813130] Key2Str is Invalid key length(0) or Type(0)                
[   17.813158] Key3Str is Invalid key length(0) or Type(0)                
[   17.813187] Key4Str is Invalid key length(0) or Type(0)                
[   17.813733] 1. Phy Mode = 9                                            
[   17.813736] 2. Phy Mode = 9                                            
[   17.813739] NVM is Efuse and its size =2d[2d0-2fc]                     
[   17.814838] 3. Phy Mode = 9                                            
[   17.818221] RTMPSetPhyMode: channel is out of range, use first channel=1                                                                         
[   17.819279] MCS Set = ff 00 00 00 01                                   
[   17.858515] <==== rt28xx_init, Status=0                                
[   17.858609] 0x1300 = 00064300                                          
[   17.858621]  AUX_CTRL = 0x                             c02             
[   17.858626]  Read AUX_CTRL = 0xc02                                     
[   17.858629]  Write AUX_CTRL = 0x1c02                                   
[   17.858632]  OSC_CTRL = 0x3ff11                                        
[   17.875552] ====> rt30xx Read PowerLevelMode =  0x3.                   
[   17.875557] ====> rt30xx F Write 0x83 Command = 0x3.                   
[   17.903520] type=1505 audit(1257983145.068:9): operation="profile_replace" pid=1008 name=/sbin/dhclient3                                         
[   17.903909] type=1505 audit(1257983145.068:10): operation="profile_replace" pid=1008 name=/usr/lib/NetworkManager/nm-dhcp-client.action          
[   17.904187] type=1505 audit(1257983145.072:11): operation="profile_replace" pid=1008 name=/usr/lib/connman/scripts/dhclient-script               
[   17.908969] type=1505 audit(1257983145.076:12): operation="profile_replace" pid=1010 name=/usr/lib/cups/backend/cups-pdf                         
[   17.909431] type=1505 audit(1257983145.076:13): operation="profile_replace" pid=1010 name=/usr/sbin/cupsd                                        
[   17.911795] type=1505 audit(1257983145.076:14): operation="profile_replace" pid=1011 name=/usr/sbin/mysqld-akonadi                               
[   17.913953] type=1505 audit(1257983145.080:15): operation="profile_replace" pid=1012 name=/usr/sbin/tcpdump                                      
[   18.522930] r8169: eth0: link down                                     
[   18.523220] ADDRCONF(NETDEV_UP): eth0: link is not ready               
[   22.340331] [drm] Setting GART location based on new memory map        
[   22.340968] [drm] Loading RS690/RS740 Microcode                        
[   22.340991] [drm] Num pipes: 1                                         
[   22.340999] [drm] writeback test succeeded in 1 usecs                  
[   22.909872] ppdev: user-space parallel port driver                     
[   27.928032] ra0: no IPv6 routers present                               
[   39.000045] Clocksource tsc unstable (delta = -249986683 ns)           
[   43.479233] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).                                                        
[   43.479244] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   43.486405] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).                                                       
[   43.486416] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   43.801296] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).                                                        
[   43.801302] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   43.811273] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).                                                       
[   43.811278] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   43.980525] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).                                                        
[   43.980530] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   43.988722] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).                                                       
[   43.988727] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   44.377988] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).                                                        
[   44.377994] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   44.388009] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).                                                       
[   44.388015] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   44.593288] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   44.593299] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   44.603851] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   44.603862] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[ 1970.806587] r8169: eth0: link up
[ 1970.807144] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1981.140030] eth0: no IPv6 routers present
[ 3098.036267] udev: starting version 147
[ 3098.977695] type=1505 audit(1257986226.144:16): operation="profile_replace" pid=3895 name=/sbin/dhclient3
[ 3098.978073] type=1505 audit(1257986226.144:17): operation="profile_replace" pid=3895 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 3098.978286] type=1505 audit(1257986226.144:18): operation="profile_replace" pid=3895 name=/usr/lib/connman/scripts/dhclient-script
[ 3098.987179] type=1505 audit(1257986226.152:19): operation="profile_replace" pid=3897 name=/usr/lib/cups/backend/cups-pdf
[ 3098.987645] type=1505 audit(1257986226.152:20): operation="profile_replace" pid=3897 name=/usr/sbin/cupsd
[ 3099.003892] type=1505 audit(1257986226.168:21): operation="profile_replace" pid=3898 name=/usr/sbin/mysqld-akonadi
[ 3099.006760] type=1505 audit(1257986226.172:22): operation="profile_replace" pid=3899 name=/usr/sbin/tcpdump
[ 3099.322811] type=1505 audit(1257986226.488:23): operation="profile_replace" pid=3936 name=/sbin/dhclient3
[ 3099.323002] type=1505 audit(1257986226.488:24): operation="profile_replace" pid=3936 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 3099.323106] type=1505 audit(1257986226.488:25): operation="profile_replace" pid=3936 name=/usr/lib/connman/scripts/dhclient-script
[ 3106.055852] __ratelimit: 12 callbacks suppressed
[ 3106.055857] type=1505 audit(1257986233.220:30): operation="profile_replace" pid=4081 name=/usr/lib/cups/backend/cups-pdf
[ 3106.061725] type=1505 audit(1257986233.228:31): operation="profile_replace" pid=4081 name=/usr/sbin/cupsd
```

---

### Post by raygj on 2009-11-11
this post may help you
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

### Post by Odemia on 2009-11-12
Interesting, I did not know that wireless chip sets have Country Code registers.  Unfortunately for me I get:

```
$ sudo iw reg get
nl80211 not found.
$ sudo iw reg set US
nl80211 not found.
```

libnl1 is installed, I tried a few other iw commands and they all return the same thing.  Based on my quick research I am thinking that the wireless driver (rt3090-dkms) probably doesn't support nl80211.

I also tried adding the following to /etc/modprobe.d/dkms.conf:
```
options wl ieee80211_regdom=US
```
and running
```
$ sudo modprobe -r rt3090sta
$ sudo modprove rt3090sta
```

/var/log/messages still
```
Nov 12 01:53:51 ku-910 kernel: [29304.409842]
Nov 12 01:53:51 ku-910 kernel: [29304.409845]
Nov 12 01:53:51 ku-910 kernel: [29304.409848] === pAd = f9fe9000, size = 487256 ===
Nov 12 01:53:51 ku-910 kernel: [29304.409851]
Nov 12 01:53:51 ku-910 kernel: [29304.409857] <-- RTMPAllocAdapterBlock, Status=0
Nov 12 01:53:51 ku-910 kernel: [29304.409863] pAd->CSRBaseAddress =0xf8820000, csr_addr=0xf8820000!
Nov 12 01:56:29 ku-910 kernel: [29462.537960] r8169: eth0: link up
```

---

### Post by sir4taye on 2009-11-13
Try reverting to kernel ending in 13 or upgrading to prerelease 15. I lost my wireless on 14 as well.

---

### Post by Odemia on 2009-11-15
Have been away and unable to pursue this.  But am back now and trying to get it resolved.

@raygj: is there something other than "sudo iw reg get" I could use to confirm the problem has to do with the country code?  I see nothing in dmesg or syslog that could confirm this.

@sir4taye: The wireless was working fine with 2.6.31-14.  Also I forget the kernel version numbers but but wireless has also stopped working with my 9.04 install (separate / partition, but they share a /home partition).  I will try a different kernel when I get a chance but I really think that is a long shot.

---

### Post by Odemia on 2009-11-16
Installed jaunty(2.6.28-11) on a spare partition.  It is definitely not a kernel version issue.  I was previously able to get ndiswrapper, source, and the dkms drivers working with 2.6.28-11 and now I can't get any of them to work.

I even tryied setting the 'CountryCode' in /etc/Wireless/RT2860STA/RT2860STA.dat.  Despite it's name this is the config file for the rt3090sta driver.

Still no luck.  I am considering borrowing a usb drive with windows installed so I can try booting and installing some windows drivers.  I am really starting to grasp at straws to either fix the problem or diagnose it as a hardware failure once and for all.

---

