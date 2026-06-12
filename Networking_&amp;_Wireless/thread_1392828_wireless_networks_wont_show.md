---
title: "wireless networks wont show"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by ryanbarry11 on 2010-01-28
hi im new to this ubuntu stuff but i use windows 7 and yesterday i downloaded the 64 bit version of ubuntu 9.10 and dual booted to it by mounting the iso with poweriso...and it installed fine but i cant connect to any internet....wen i hit the network connections tab in the top right it says wired connections in gray and then it says no connections below it and thats it it doesnt even show any wireless connections at all...i have a version wireless modeum and router and the wifi works fine with windows 7....any suggestions  on how to fix the problem

---

### Post by The Toxic Mite on 2010-01-28
Hey!

First, can you go to Applications > Accessories > Terminal, and enter the following commands please?

```

lspci -v less
sudo lshw -c network
iwconfig
dmesg

```

Post the outputs here when done :)

-TTM-

---

### Post by ryanbarry11 on 2010-01-28
ill try it in a second but when i go to hardware drivers it says none are installed its weird but i switched to kubuntu and it has the same problem

---

### Post by ryanbarry11 on 2010-01-28
> ryan@ubuntu:~$ lspci -v less
Usage: lspci [<switches>]   

Basic display modes:
-mm             Produce machine-readable output (single -m for an obsolete format)                                                                              
-t              Show bus tree                                                   

Display options:
-v              Be verbose (-vv for very verbose)
-k              Show kernel drivers handling each device
-x              Show hex-dump of the standard part of the config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-b              Bus-centric view (addresses and IRQ's as seen by the bus)       
-D              Always show domain numbers                                      

Resolving of device ID's to names:
-n              Show numeric ID's 
-nn             Show both textual and numeric ID's (names & numbers)
-q              Query the PCI ID database for unknown ID's via DNS  
-qq             As above, but re-query locally cached entries       
-Q              Query the PCI ID database for all ID's via DNS      

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots                                                                             
-d [<vendor>]:[<device>]                        Show only devices with specified ID's                                                                           

Other options:
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>       Look up kernel modules in a given file instead of default modules.pcimap                                                                        
-M              Enable `bus mapping' mode (dangerous; root only)                

PCI access options:
-A <method>     Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>  Set PCI access parameter (see `-O help' for a list)           
-G              Enable PCI access debugging                                   
-H <mode>       Use direct hardware access (<mode> = 1 or 2)                  
-F <file>       Read PCI configuration dump from a given file                 
ryan@ubuntu:~$ sudo lshw -c network                                           
  *-network UNCLAIMED                                                         
       description: Network controller                                        
       product: Broadcom Corporation                                          
       vendor: Broadcom Corporation                                           
       physical id: 0                                                         
       bus info: pci@0000:02:00.0                                             
       version: 01                                                            
       width: 64 bits                                                         
       clock: 33MHz                                                           
       capabilities: pm msi pciexpress bus_master cap_list                    
       configuration: latency=0                                               
       resources: memory:d1100000-d1103fff                                    
  *-network                                                                   
       description: Ethernet interface                                        
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter                 
       vendor: Attansic Technology Corp.                                      
       physical id: 0                                                         
       bus info: pci@0000:08:00.0                                             
       logical name: eth0                                                     
       version: c0                                                            
       serial: 00:26:22:8e:cf:16                                              
       capacity: 100MB/s                                                      
       width: 64 bits                                                         
       clock: 33MHz                                                           
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation                                 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair   
       resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)         
ryan@ubuntu:~$ iwconfig                                                         
lo        no wireless extensions.                                               

eth0      no wireless extensions.

ryan@ubuntu:~$ dmesg
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)         
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)       
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)       
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000ae60c000 (usable)         
[    0.000000]  BIOS-e820: 00000000ae60c000 - 00000000ae80c000 (ACPI NVS)       
[    0.000000]  BIOS-e820: 00000000ae80c000 - 00000000afd70000 (usable)         
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)       
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe92000 (usable)         
[    0.000000]  BIOS-e820: 00000000afe92000 - 00000000afebf000 (ACPI NVS)       
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afee2000 (usable)         
[    0.000000]  BIOS-e820: 00000000afee2000 - 00000000afef7000 (ACPI data)      
[    0.000000]  BIOS-e820: 00000000afef7000 - 00000000aff00000 (usable)         
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)       
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)       
[    0.000000] DMI 2.6 present.                                                 
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000                       
[    0.000000] MTRR default type: uncachable                                    
[    0.000000] MTRR fixed ranges enabled:                                       
[    0.000000]   00000-9FFFF write-back                                         
[    0.000000]   A0000-BFFFF uncachable                                         
[    0.000000]   C0000-FFFFF write-through                                      
[    0.000000] MTRR variable ranges enabled:                                    
[    0.000000]   0 base 0000000000 mask FF80000000 write-back                   
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back                   
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back                   
[    0.000000]   3 base 00FFF00000 mask FFFFF00000 write-protect                
[    0.000000]   4 disabled                                                     
[    0.000000]   5 disabled                                                     
[    0.000000]   6 disabled                                                     
[    0.000000]   7 disabled                                                     
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)                                                                   
[    0.000000] Scanning 1 areas for low memory corruption                       
[    0.000000] modified physical RAM map:                                       
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)          
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)        
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)          
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)        
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)        
[    0.000000]  modified: 0000000000100000 - 00000000ae60c000 (usable)          
[    0.000000]  modified: 00000000ae60c000 - 00000000ae80c000 (ACPI NVS)        
[    0.000000]  modified: 00000000ae80c000 - 00000000afd70000 (usable)          
[    0.000000]  modified: 00000000afd70000 - 00000000afdbf000 (reserved)        
[    0.000000]  modified: 00000000afdbf000 - 00000000afe92000 (usable)          
[    0.000000]  modified: 00000000afe92000 - 00000000afebf000 (ACPI NVS)        
[    0.000000]  modified: 00000000afebf000 - 00000000afee2000 (usable)          
[    0.000000]  modified: 00000000afee2000 - 00000000afef7000 (ACPI data)       
[    0.000000]  modified: 00000000afef7000 - 00000000aff00000 (usable)          
[    0.000000]  modified: 00000000f7000000 - 00000000f8000000 (reserved)        
[    0.000000]  modified: 00000000feb00000 - 00000000feb01000 (reserved)        
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)        
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)        
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)        
[    0.000000] initial memory mapped : 0 - 00c00000                             
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000           
[    0.000000] Using x86 segment limits to approximate NX protection            
[    0.000000]  0000000000 - 0000400000 page 4k                                 
[    0.000000]  0000400000 - 0037400000 page 2M                                 
[    0.000000]  0037400000 - 00377fe000 page 4k                                 
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000          
[    0.000000] RAMDISK: 37863000 - 37fef104                                     
[    0.000000] Allocated new RAMDISK: 008ad000 - 01039104                       
[    0.000000] Move RAMDISK from 0000000037863000 - 0000000037fef103 to 008ad000 - 01039103                                                                     
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)                           
[    0.000000] ACPI: XSDT afef6120 0005C (v01 ACRSYS ACRPRDCT 00000003      01000013)                                                                           
[    0.000000] ACPI: FACP afef5000 000F4 (v04 ACRSYS ACRPRDCT 00000003 1025 01000013)                                                                           
[    0.000000] ACPI: DSDT afee9000 08E28 (v01 ACRSYS ACRPRDCT 00001000 1025 01000013)                                                                           
[    0.000000] ACPI: FACS afe9c000 00040                                        
[    0.000000] ACPI: HPET afef4000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)                                                                           
[    0.000000] ACPI: APIC afef3000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)                                                                           
[    0.000000] ACPI: MCFG afef2000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)                                                                           
[    0.000000] ACPI: BOOT afee8000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)                                                                           
[    0.000000] ACPI: SLIC afee7000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)                                                                           
[    0.000000] ACPI: SSDT afee6000 000D3 (v01 AMD    PowerNow 00000001 AMD  00000001)                                                                           
[    0.000000] ACPI: Local APIC address 0xfee00000                              
[    0.000000] 1927MB HIGHMEM available.                                        
[    0.000000] 887MB LOWMEM available.                                          
[    0.000000]   mapped low ram: 0 - 377fe000                                   
[    0.000000]   low ram: 0 - 377fe000                                          
[    0.000000]   node 0 low ram: 00000000 - 377fe000                            
[    0.000000]   node 0 bootmap 00008000 - 0000ef00                             
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]     
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                    
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]                                                                    
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                                                    
[    0.000000]   #5 [00008a9000 - 00008ac26f]              BRK ==> [00008a9000 - 00008ac26f]                                                                    
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]                                                                    
[    0.000000]   #7 [00008ad000 - 0001039104]      NEW RAMDISK ==> [00008ad000 - 0001039104]                                                                    
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]                                                                    
[    0.000000] Zone PFN ranges:                                                 
[    0.000000]   DMA      0x00000000 -> 0x00001000                              
[    0.000000]   Normal   0x00001000 -> 0x000377fe                              
[    0.000000]   HighMem  0x000377fe -> 0x000aff00                              
[    0.000000] Movable zone start PFN for each node                             
[    0.000000] early_node_map[7] active PFN ranges                              
[    0.000000]     0: 0x00000000 -> 0x00000002                                  
[    0.000000]     0: 0x00000006 -> 0x0000009f                                  
[    0.000000]     0: 0x00000100 -> 0x000ae60c                                  
[    0.000000]     0: 0x000ae80c -> 0x000afd70                                  
[    0.000000]     0: 0x000afdbf -> 0x000afe92                                  
[    0.000000]     0: 0x000afebf -> 0x000afee2                                  
[    0.000000]     0: 0x000afef7 -> 0x000aff00                                  
[    0.000000] On node 0 totalpages: 719882                                     
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c103a000                                                                               
[    0.000000]   DMA zone: 32 pages used for memmap                             
[    0.000000]   DMA zone: 0 pages reserved                                     
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0                             
[    0.000000]   Normal zone: 1744 pages used for memmap                        
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31                       
[    0.000000]   HighMem zone: 3855 pages used for memmap                       
[    0.000000]   HighMem zone: 488802 pages, LIFO batch:31                      
[    0.000000] Using APIC driver default                                        
[    0.000000] Detected use of extended apic ids on hypertransport bus          
[    0.000000] ACPI: PM-Timer IO Port: 0x408                                    
[    0.000000] ACPI: Local APIC address 0xfee00000                              
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)               
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] disabled)              
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])              
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])              
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])          
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)       
[    0.000000] ACPI: IRQ0 used by override.                                     
[    0.000000] ACPI: IRQ2 used by override.                                     
[    0.000000] ACPI: IRQ9 used by override.                                     
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                    
[    0.000000] Using ACPI (MADT) for SMP configuration information              
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000                       
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs                             
[    0.000000] nr_irqs_gsi: 24                                                  
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:47100000)                                                                           
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1           
[    0.000000] PERCPU: Embedded 14 pages at c2644000, static data 35612 bytes   
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714251                                                                      
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash                      
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)            
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)   
[    0.000000] Enabling fast FPU save and restore... done.                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.            
[    0.000000] Initializing CPU#0                                               
[    0.000000] allocated 14412800 bytes of page_cgroup                          
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                                                       
[    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)              
[    0.000000] Memory: 2825484k/2882560k available (4565k kernel code, 53168k reserved, 2143k data, 540k init, 1970628k highmem)                                
[    0.000000] virtual kernel memory layout:                                    
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)                
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)                
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)                
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)                
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)                
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)                
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)                
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                      
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                                          
[    0.000000] NR_IRQS:2304 nr_irqs:424                                         
[    0.000000] Fast TSC calibration using PIT                                   
[    0.000000] Detected 1595.674 MHz processor.                                 
[    0.000012] spurious 8259A interrupt: IRQ7.                                  
[    0.001157] Console: colour VGA+ 80x25                                       
[    0.001160] console [tty0] enabled                                           
[    0.001552] hpet clockevent registered                                       
[    0.001559]   alloc irq_desc for 24 on node 0                                
[    0.001570]   alloc kstat_irqs on node 0                                     
[    0.001578] HPET: 4 timers in total, 1 timers will be used for per-cpu timer 
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.34 BogoMIPS (lpj=6382696)                                        
[    0.004037] Security Framework initialized                                   
[    0.004055] AppArmor: AppArmor initialized                                   
[    0.004064] Mount-cache hash table entries: 512                              
[    0.004230] Initializing cgroup subsys ns                                    
[    0.004235] Initializing cgroup subsys cpuacct                               
[    0.004240] Initializing cgroup subsys memory                                
[    0.004248] Initializing cgroup subsys freezer                               
[    0.004251] Initializing cgroup subsys net_cls                               
[    0.004266] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004270] CPU: L2 Cache: 512K (64 bytes/line)                              
[    0.004275] mce: CPU supports 5 MCE banks                                    
[    0.004286] using C1E aware idle routine                                     
[    0.004296] Performance Counters: AMD PMU driver.                            
[    0.004304] ... version:                 0                                   
[    0.004306] ... bit width:               48                                  
[    0.004309] ... generic counters:        4                                   
[    0.004311] ... value mask:              0000ffffffffffff                    
[    0.004314] ... max period:              00007fffffffffff                    
[    0.004316] ... fixed-purpose counters:  0                                   
[    0.004319] ... counter mask:            000000000000000f                    
[    0.004324] Checking 'hlt' instruction... OK.                                
[    0.020890] SMP alternatives: switching to UP code                           
[    0.027710] ACPI: Core revision 20090521                                     
[    0.044475] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1             
[    0.086566] CPU0: AMD Athlon(tm) Processor TF-20 stepping 02                 
[    0.088001] Brought up 1 CPUs                                                
[    0.088001] Total of 1 processors activated (3191.34 BogoMIPS).              
[    0.088001] CPU0 attaching NULL sched-domain.                                
[    0.088001] Booting paravirtualized kernel on bare hardware                  
[    0.088001] regulator: core version 0.5                                      
[    0.088001] Time: 19:26:24  Date: 01/28/10                                   
[    0.088001] NET: Registered protocol family 16                               
[    0.088001] EISA bus registered                                              
[    0.088001] ACPI: bus type pci registered                                    
[    0.088001] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15  
[    0.088001] PCI: MCFG area at f7000000 reserved in E820                      
[    0.088001] PCI: Using MMCONFIG for extended config space                    
[    0.088001] PCI: Using configuration type 1 for base access                  
[    0.088001] bio: create slab <bio-0> at 0                                    
[    0.088001] ACPI: EC: Look up EC in DSDT                                     
[    0.093268] ACPI: BIOS _OSI(Linux) query ignored                             
[    0.098058] ACPI: Interpreter enabled                                        
[    0.098063] ACPI: (supports S0 S1 S3 S4 S5)                                  
[    0.098099] ACPI: Using IOAPIC for interrupt routing                         
[    0.105948] System has AMD C1E enabled                                       
[    0.105961] Switch to broadcast mode on CPU0                                 
[    0.105961] ACPI: EC: non-query interrupt received, switching to interrupt mode                                                                              
[    0.620004] ACPI: EC: missing confirmations, switch off interrupt mode.      
[    0.972336] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62     
[    0.972339] ACPI: EC: driver started in poll mode                            
[    0.972632] ACPI: No dock devices found.                                     
[    0.973769] ACPI: PCI Root Bridge [PCI0] (0000:00)                           
[    0.973977] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold            
[    0.973981] pci 0000:00:04.0: PME# disabled                                  
[    0.974028] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold            
[    0.974032] pci 0000:00:05.0: PME# disabled                                  
[    0.974134] pci 0000:00:11.0: reg 10 io port: [0x8038-0x803f]                
[    0.974144] pci 0000:00:11.0: reg 14 io port: [0x804c-0x804f]                
[    0.974153] pci 0000:00:11.0: reg 18 io port: [0x8030-0x8037]                
[    0.974161] pci 0000:00:11.0: reg 1c io port: [0x8048-0x804b]                
[    0.974170] pci 0000:00:11.0: reg 20 io port: [0x8010-0x801f]                
[    0.974179] pci 0000:00:11.0: reg 24 32bit mmio: [0xd2306000-0xd23063ff]     
[    0.974246] pci 0000:00:12.0: reg 10 32bit mmio: [0xd2305000-0xd2305fff]     
[    0.974311] pci 0000:00:12.1: reg 10 32bit mmio: [0xd2304000-0xd2304fff]     
[    0.974397] pci 0000:00:12.2: reg 10 32bit mmio: [0xd2306400-0xd23064ff]     
[    0.974458] pci 0000:00:12.2: supports D1 D2                                 
[    0.974460] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot             
[    0.974466] pci 0000:00:12.2: PME# disabled                                  
[    0.974615] pci 0000:00:14.2: reg 10 64bit mmio: [0xd2300000-0xd2303fff]     
[    0.974665] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold            
[    0.974671] pci 0000:00:14.2: PME# disabled                                  
[    0.974901] pci 0000:01:05.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]     
[    0.974907] pci 0000:01:05.0: reg 14 io port: [0x7000-0x70ff]                
[    0.974913] pci 0000:01:05.0: reg 18 32bit mmio: [0xd2200000-0xd220ffff]     
[    0.974923] pci 0000:01:05.0: reg 24 32bit mmio: [0xd2100000-0xd21fffff]     
[    0.974940] pci 0000:01:05.0: supports D1 D2                                 
[    0.975023] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]                
[    0.975027] pci 0000:00:01.0: bridge 32bit mmio: [0xd2100000-0xd22fffff]     
[    0.975033] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.975093] pci 0000:02:00.0: reg 10 64bit mmio: [0xd1100000-0xd1103fff]     
[    0.975158] pci 0000:02:00.0: supports D1 D2                                 
[    0.975160] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold            
[    0.975166] pci 0000:02:00.0: PME# disabled                                  
[    0.975271] pci 0000:00:04.0: bridge io port: [0x3000-0x6fff]                
[    0.975276] pci 0000:00:04.0: bridge 32bit mmio: [0xd1100000-0xd20fffff]     
[    0.975281] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.975336] pci 0000:08:00.0: reg 10 64bit mmio: [0xd1000000-0xd103ffff]     
[    0.975345] pci 0000:08:00.0: reg 18 io port: [0x2000-0x207f]                
[    0.975407] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold      
[    0.975413] pci 0000:08:00.0: PME# disabled                                  
[    0.975514] pci 0000:00:05.0: bridge io port: [0x2000-0x2fff]                
[    0.975519] pci 0000:00:05.0: bridge 32bit mmio: [0xd1000000-0xd10fffff]     
[    0.975586] pci 0000:00:14.4: transparent bridge                             
[    0.975591] pci 0000:00:14.4: bridge io port: [0x1000-0x1fff]                
[    0.975615] pci_bus 0000:00: on NUMA node 0                                  
[    0.975622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]              
[    0.975796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]         
[    0.975895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]         
[    0.975993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]         
[    0.976157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]         
[    0.985572] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.985802] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.986028] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.986251] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.986473] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.986674] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.986901] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.987124] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                                                                      
[    0.987397] SCSI subsystem initialized                                       
[    0.987475] libata version 3.00 loaded.                                      
[    0.987561] usbcore: registered new interface driver usbfs                   
[    0.987580] usbcore: registered new interface driver hub                     
[    0.987608] usbcore: registered new device driver usb                        
[    0.987832] ACPI: WMI: Mapper loaded                                         
[    0.987835] PCI: Using ACPI for IRQ routing                                  
[    0.988089] Bluetooth: Core ver 2.15                                         
[    0.988120] NET: Registered protocol family 31                               
[    0.988122] Bluetooth: HCI device and connection manager initialized         
[    0.988126] Bluetooth: HCI socket layer initialized                          
[    0.988129] NetLabel: Initializing                                           
[    0.988131] NetLabel:  domain hash size = 128                                
[    0.988133] NetLabel:  protocols = UNLABELED CIPSOv4                         
[    0.988149] NetLabel:  unlabeled traffic allowed by default                  
[    0.988220] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0                      
[    0.988226] hpet0: 4 comparators, 32-bit 14.318180 MHz counter               
[    0.992028] hpet: hpet2 irq 24 for MSI                                       
[    0.993919] pnp: PnP ACPI init                                               
[    0.993945] ACPI: bus type pnp registered                                    
[    0.996030] Switched to high resolution mode on CPU 0                        
[    1.188106] pnp: PnP ACPI: found 10 devices                                  
[    1.188109] ACPI: ACPI bus type pnp unregistered                             
[    1.188113] PnPBIOS: Disabled by ACPI PNP                                    
[    1.188133] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved                                                                            
[    1.188137] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.188142] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
[    1.188152] system 00:08: ioport range 0x400-0x4cf has been reserved         
[    1.188156] system 00:08: ioport range 0x4d0-0x4d1 has been reserved         
[    1.188160] system 00:08: ioport range 0x4d6-0x4d6 has been reserved         
[    1.188163] system 00:08: ioport range 0x680-0x6ff has been reserved         
[    1.188167] system 00:08: ioport range 0x77a-0x77a has been reserved         
[    1.188171] system 00:08: ioport range 0xc00-0xc01 has been reserved         
[    1.188175] system 00:08: ioport range 0xc14-0xc14 has been reserved         
[    1.188179] system 00:08: ioport range 0xc50-0xc52 has been reserved         
[    1.188183] system 00:08: ioport range 0xc6c-0xc6c has been reserved         
[    1.188186] system 00:08: ioport range 0xc6f-0xc6f has been reserved         
[    1.188190] system 00:08: ioport range 0xcd0-0xcdb has been reserved         
[    1.188194] system 00:08: ioport range 0xfd60-0xfd63 has been reserved       
[    1.188202] system 00:09: iomem range 0xe0000-0xfffff could not be reserved  
[    1.188206] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    1.223154] AppArmor: AppArmor Filesystem Enabled                            
[    1.223225] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01              
[    1.223229] pci 0000:00:01.0:   IO window: 0x7000-0x7fff                     
[    1.223234] pci 0000:00:01.0:   MEM window: 0xd2100000-0xd22fffff            
[    1.223239] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff                                                                           
[    1.223245] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02              
[    1.223249] pci 0000:00:04.0:   IO window: 0x3000-0x6fff                     
[    1.223253] pci 0000:00:04.0:   MEM window: 0xd1100000-0xd20fffff            
[    1.223258] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff                                                                           
[    1.223264] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08              
[    1.223267] pci 0000:00:05.0:   IO window: 0x2000-0x2fff                     
[    1.223272] pci 0000:00:05.0:   MEM window: 0xd1000000-0xd10fffff            
[    1.223276] pci 0000:00:05.0:   PREFETCH window: disabled                    
[    1.223280] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09              
[    1.223318] pci 0000:00:14.4:   IO window: 0x1000-0x1fff                     
[    1.223325] pci 0000:00:14.4:   MEM window: disabled                         
[    1.223330] pci 0000:00:14.4:   PREFETCH window: disabled                    
[    1.223342] pci 0000:00:01.0: setting latency timer to 64                    
[    1.223351]   alloc irq_desc for 16 on node -1                               
[    1.223354]   alloc kstat_irqs on node -1                                    
[    1.223360] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    1.223365] pci 0000:00:04.0: setting latency timer to 64                    
[    1.223371]   alloc irq_desc for 17 on node -1                               
[    1.223373]   alloc kstat_irqs on node -1                                    
[    1.223377] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17     
[    1.223382] pci 0000:00:05.0: setting latency timer to 64                    
[    1.223392] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                   
[    1.223396] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]           
[    1.223399] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]                 
[    1.223403] pci_bus 0000:01: resource 1 mem: [0xd2100000-0xd22fffff]         
[    1.223406] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]     
[    1.223410] pci_bus 0000:02: resource 0 io:  [0x3000-0x6fff]                 
[    1.223414] pci_bus 0000:02: resource 1 mem: [0xd1100000-0xd20fffff]         
[    1.223417] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd0ffffff]     
[    1.223421] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff]                 
[    1.223424] pci_bus 0000:08: resource 1 mem: [0xd1000000-0xd10fffff]         
[    1.223428] pci_bus 0000:09: resource 0 io:  [0x1000-0x1fff]                 
[    1.223431] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]                   
[    1.223435] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]           
[    1.223482] NET: Registered protocol family 2                                
[    1.223596] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.224008] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                                             
[    1.225038] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)      
[    1.225607] TCP: Hash tables configured (established 131072 bind 65536)      
[    1.225611] TCP reno registered                                              
[    1.225725] NET: Registered protocol family 1                                
[    1.225803] Trying to unpack rootfs image as initramfs...                    
[    1.500773] Freeing initrd memory: 7728k freed                               
[    1.508140] Simple Boot Flag at 0x44 set to 0x1                              
[    1.508286] cpufreq-nforce2: No nForce2 chipset.                             
[    1.508317] Scanning for low memory corruption every 60 seconds              
[    1.508441] audit: initializing netlink socket (disabled)                    
[    1.508458] type=2000 audit(1264706785.508:1): initialized                   
[    1.519936] highmem bounce pool size: 64 pages                               
[    1.519943] HugeTLB registered 4 MB page size, pre-allocated 0 pages         
[    1.521847] VFS: Disk quotas dquot_6.5.2                                     
[    1.521917] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)       
[    1.522620] fuse init (API version 7.12)                                     
[    1.522722] msgmni has been set to 1686                                      
[    1.523008] alg: No test for stdrng (krng)                                   
[    1.523021] io scheduler noop registered                                     
[    1.523023] io scheduler anticipatory registered                             
[    1.523026] io scheduler deadline registered                                 
[    1.523073] io scheduler cfq registered (default)                            
[    1.608079] pci 0000:01:05.0: Boot video device                              
[    1.608207]   alloc irq_desc for 25 on node -1                               
[    1.608209]   alloc kstat_irqs on node -1                                    
[    1.608220] pcieport-driver 0000:00:04.0: irq 25 for MSI/MSI-X               
[    1.608228] pcieport-driver 0000:00:04.0: setting latency timer to 64        
[    1.608340]   alloc irq_desc for 26 on node -1                               
[    1.608343]   alloc kstat_irqs on node -1                                    
[    1.608349] pcieport-driver 0000:00:05.0: irq 26 for MSI/MSI-X               
[    1.608356] pcieport-driver 0000:00:05.0: setting latency timer to 64        
[    1.608439] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                  
[    1.608526] pciehp: PCI Express Hot Plug Controller Driver version: 0.4      
[    1.736134] ACPI: AC Adapter [ACAD] (on-line)                                
[    1.736202] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                             
[    1.736206] ACPI: Power Button [PWRF]                                        
[    1.736302] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                    
[    1.736305] ACPI: Power Button [PWRB]                                        
[    1.736363] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2                                                                    
[    1.736366] ACPI: Sleep Button [SLPB]                                        
[    1.736425] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0D:00/input/input3                                                           
[    2.000107] ACPI: Lid Switch [LID]                                           
[    2.000467] ACPI: processor limited to max C-state 1                         
[    2.000497] processor LNXCPU:00: registered as cooling_device0               
[    2.000501] ACPI: Processor [CPU0] (supports 8 throttling states)            
[    2.320297] ACPI: Invalid active0 threshold                                  
[    2.448113] thermal LNXTHERM:01: registered as thermal_zone0                 
[    2.448122] ACPI: Thermal Zone [THRM] (53 C)                                 
[    2.448180] isapnp: Scanning for PnP cards...                                
[    2.832788] isapnp: No Plug & Play device found                              
[    2.834175] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled          
[    2.835685] brd: module loaded                                               
[    2.836268] loop: module loaded                                              
[    2.836358] input: Macintosh mouse button emulation as /devices/virtual/input/input4                                                                         
[    2.836436] ahci 0000:00:11.0: version 3.0                                   
[    2.836486]   alloc irq_desc for 22 on node -1                               
[    2.836489]   alloc kstat_irqs on node -1                                    
[    2.836497] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22    
[    2.836542]   alloc irq_desc for 27 on node -1                               
[    2.836544]   alloc kstat_irqs on node -1                                    
[    2.836557] ahci 0000:00:11.0: irq 27 for MSI/MSI-X                          
[    2.836760] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode                                                                    
[    2.836765] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part                                                                       
[    2.837937] scsi0 : ahci                                                     
[    2.838104] scsi1 : ahci                                                     
[    2.838201] scsi2 : ahci                                                     
[    2.838292] scsi3 : ahci                                                     
[    2.838385] scsi4 : ahci                                                     
[    2.838500] scsi5 : ahci                                                     
[    2.838717] ata1: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306100 irq 27                                                                             
[    2.838722] ata2: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306180 irq 27                                                                             
[    2.838727] ata3: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306200 irq 27                                                                             
[    2.838731] ata4: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306280 irq 27                                                                             
[    2.838736] ata5: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306300 irq 27                                                                             
[    2.838741] ata6: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306380 irq 27                                                                             
[    2.839775] Fixed MDIO Bus: probed                                           
[    2.839821] PPP generic driver version 2.4.2                                 
[    2.839953] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver       
[    2.840048] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.840067] ehci_hcd 0000:00:12.2: setting latency timer to 64               
[    2.840071] ehci_hcd 0000:00:12.2: EHCI Host Controller                      
[    2.840136] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1                                                                             
[    2.840218] ehci_hcd 0000:00:12.2: debug port 1                              
[    2.840237] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2306400                 
[    2.852054] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00                
[    2.852144] usb usb1: configuration #1 chosen from 1 choice                  
[    2.852187] hub 1-0:1.0: USB hub found                                       
[    2.852198] hub 1-0:1.0: 6 ports detected                                    
[    2.852312] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver           
[    2.852365] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.852378] ohci_hcd 0000:00:12.0: setting latency timer to 64               
[    2.852382] ohci_hcd 0000:00:12.0: OHCI Host Controller                      
[    2.852417] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2                                                                             
[    2.852487] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2305000                 
[    2.912112] usb usb2: configuration #1 chosen from 1 choice                  
[    2.912146] hub 2-0:1.0: USB hub found                                       
[    2.912192] hub 2-0:1.0: 3 ports detected                                    
[    2.912248] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.912259] ohci_hcd 0000:00:12.1: setting latency timer to 64               
[    2.912264] ohci_hcd 0000:00:12.1: OHCI Host Controller                      
[    2.912300] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3                                                                             
[    2.912364] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2304000                 
[    2.972259] usb usb3: configuration #1 chosen from 1 choice                  
[    2.972289] hub 3-0:1.0: USB hub found                                       
[    2.972343] hub 3-0:1.0: 3 ports detected                                    
[    2.972406] uhci_hcd: USB Universal Host Controller Interface driver         
[    2.972511] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12                                                                           
[    2.993270] serio: i8042 KBD port at 0x60,0x64 irq 1                         
[    2.993295] serio: i8042 AUX port at 0x60,0x64 irq 12                        
[    2.993380] mice: PS/2 mouse device common for all mice                      
[    2.993550] rtc_cmos 00:04: RTC can wake from S4                             
[    2.993597] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0            
[    2.993660] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs           
[    2.993780] device-mapper: uevent: version 1.0.3                             
[    2.993930] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]                                                                 
[    2.994055] device-mapper: multipath: version 1.1.0 loaded                   
[    2.994059] device-mapper: multipath round-robin: version 1.0.0 loaded       
[    2.994252] EISA: Probing bus 0 at eisa.0                                    
[    2.994260] Cannot allocate resource for EISA slot 1                         
[    2.994263] Cannot allocate resource for EISA slot 2                         
[    2.994266] Cannot allocate resource for EISA slot 3                         
[    2.994268] Cannot allocate resource for EISA slot 4                         
[    2.994271] Cannot allocate resource for EISA slot 5                         
[    2.994273] Cannot allocate resource for EISA slot 6                         
[    2.994276] Cannot allocate resource for EISA slot 7                         
[    2.994278] Cannot allocate resource for EISA slot 8                         
[    2.994281] EISA: Detected 0 cards.                                          
[    2.994331] cpuidle: using governor ladder                                   
[    2.994334] cpuidle: using governor menu                                     
[    2.994936] TCP cubic registered                                             
[    2.995146] NET: Registered protocol family 10                               
[    2.995678] lo: Disabled Privacy Extensions                                  
[    2.996067] NET: Registered protocol family 17                               
[    2.996087] Bluetooth: L2CAP ver 2.13                                        
[    2.996089] Bluetooth: L2CAP socket layer initialized                        
[    2.996092] Bluetooth: SCO (Voice Link) ver 0.6                              
[    2.996094] Bluetooth: SCO socket layer initialized                          
[    2.996169] Bluetooth: RFCOMM TTY layer initialized                          
[    2.996173] Bluetooth: RFCOMM socket layer initialized                       
[    2.996175] Bluetooth: RFCOMM ver 1.11                                       
[    2.996198] powernow-k8: Found 1 AMD Athlon(tm) Processor TF-20 processors (1 cpu cores) (version 2.20.00)                                                   
[    2.996244] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16                 
[    2.996248] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16                  
[    2.996294] Using IPI No-Shortcut mode                                       
[    2.996367] PM: Resume from disk failed.                                     
[    2.996381] registered taskstats version 1                                   
[    2.996521]   Magic number: 10:463:446                                       
[    2.996673] rtc_cmos 00:04: setting system clock to 2010-01-28 19:26:27 UTC (1264706787)                                                                     
[    2.996677] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found             
[    2.996679] EDD information not available.                                   
[    3.011149] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5                                                               
[    3.160085] ata4: SATA link down (SStatus 0 SControl 300)                    
[    3.160120] ata6: SATA link down (SStatus 0 SControl 300)                    
[    3.160150] ata5: SATA link down (SStatus 0 SControl 300)                    
[    3.160203] ata2: SATA link down (SStatus 0 SControl 300)                    
[    3.324069] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)           
[    3.324096] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)           
[    3.326359] ata3.00: ATAPI: Optiarc DVD RW AD-7585H, KX04, max UDMA/100, ATAPI AN                                                                            
[    3.329476] ata3.00: configured for UDMA/100                                 
[    3.365292] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133    
[    3.365297] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)    
[    3.366697] ata1.00: configured for UDMA/133                                 
[    4.736179] ACPI: Battery Slot [BAT1] (battery present)                      
[    4.736433] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5                                                                     
[    4.736573] sd 0:0:0:0: Attached scsi generic sg0 type 0                     
[    4.736622] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)                                                                            
[    4.736672] sd 0:0:0:0: [sda] Write Protect is off                           
[    4.736676] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[    4.736702] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    4.736843]  sda:                                                            
[    4.739319] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7585H  KX04 PQ: 0 ANSI: 5                                                                     
[    4.748301] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray                                                                            
[    4.748305] Uniform CD-ROM driver Revision: 3.20                             
[    4.748404] sr 2:0:0:0: Attached scsi CD-ROM sr0                             
[    4.748449] sr 2:0:0:0: Attached scsi generic sg1 type 5                     
[    4.780296]  sda1 sda2 sda3                                                  
[    4.780561] sd 0:0:0:0: [sda] Attached SCSI disk                             
[    4.780581] Freeing unused kernel memory: 540k freed                         
[    4.781086] Write protecting the kernel text: 4568k                          
[    4.781125] Write protecting the kernel read-only data: 1836k                
[    5.039489] Linux agpgart interface v0.103                                   
[    5.166798] [drm] Initialized drm 1.1.0 20060810                             
[    5.190312] [drm] radeon default to kernel modesetting DISABLED.             
[    5.190779]   alloc irq_desc for 18 on node -1                               
[    5.190783]   alloc kstat_irqs on node -1                                    
[    5.190791] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18     
[    5.190797] pci 0000:01:05.0: setting latency timer to 64                    
[    5.190929] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0                                                                             
[    5.612262] acpi device:04: registered as cooling_device1                    
[    5.612438] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6                                                   
[    5.612486] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)    
[    6.519451] EXT4-fs (loop0): INFO: recovery required on readonly filesystem  
[    6.519459] EXT4-fs (loop0): write access will be enabled during recovery    
[    6.547027] EXT4-fs (loop0): barriers enabled                                
[    6.679333] kjournald2 starting: pid 369, dev loop0:8, commit interval 5 seconds                                                                             
[    6.679355] EXT4-fs (loop0): delayed allocation enabled                      
[    6.679360] EXT4-fs: file extents enabled                                    
[    6.681822] EXT4-fs: mballoc enabled                                         
[    6.681841] EXT4-fs (loop0): recovery complete                               
[    6.682057] EXT4-fs (loop0): mounted filesystem with ordered data mode       
[    7.467854] type=1505 audit(1264706791.967:2): operation="profile_load" pid=393 name=/sbin/dhclient3                                                         
[    7.468249] type=1505 audit(1264706791.971:3): operation="profile_load" pid=393 name=/usr/lib/NetworkManager/nm-dhcp-client.action                           
[    7.468460] type=1505 audit(1264706791.971:4): operation="profile_load" pid=393 name=/usr/lib/connman/scripts/dhclient-script                                
[    7.511450] type=1505 audit(1264706792.011:5): operation="profile_load" pid=394 name=/usr/lib/cups/backend/cups-pdf                                          
[    7.511913] type=1505 audit(1264706792.011:6): operation="profile_load" pid=394 name=/usr/sbin/cupsd                                                         
[    7.514406] type=1505 audit(1264706792.015:7): operation="profile_load" pid=395 name=/usr/sbin/mysqld-akonadi                                                
[    7.516906] type=1505 audit(1264706792.019:8): operation="profile_load" pid=396 name=/usr/sbin/tcpdump                                                       
[    8.376710] udev: starting version 147                                       
[    8.706157] lp: driver loaded but no devices found                           
[    9.448091] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0                                                                         
[    9.448097] shpchp 0000:00:01.0: Cannot reserve MMIO region                  
[    9.448129] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4     
[    9.499141] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141                                                                    
[    9.632587] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0                                                                             
[    9.677497] atl1c 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17   
[    9.677511] atl1c 0000:08:00.0: setting latency timer to 64                  
[    9.677561] atl1c 0000:08:00.0: PME# disabled                                
[    9.677567] atl1c 0000:08:00.0: PME# disabled                                
[    9.761003] atl1c 0000:08:00.0: version 1.0.0.1-NAPI                         
[    9.796458] acer-wmi: Acer Laptop ACPI-WMI Extras                            
[    9.876214] acer-wmi: Unable to detect available WMID devices                
[   10.730761] ip_tables: (C) 2000-2006 Netfilter Core Team                     
[   10.896524] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000                                                                      
[   10.926681] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                               
[   10.926726] HDA Intel 0000:00:14.2: setting latency timer to 64              
[   10.980772] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7                                                                 
[   11.052052] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   11.052565] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[   14.018506] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   14.271094] EXT4-fs (loop0): internal journal on loop0:8
[   15.013643] type=1505 audit(1264724799.515:9): operation="profile_replace" pid=792 name=/sbin/dhclient3
[   15.014083] type=1505 audit(1264724799.515:10): operation="profile_replace" pid=792 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.014293] type=1505 audit(1264724799.515:11): operation="profile_replace" pid=792 name=/usr/lib/connman/scripts/dhclient-script
[   15.017946] type=1505 audit(1264724799.519:12): operation="profile_replace" pid=793 name=/usr/lib/cups/backend/cups-pdf
[   15.018409] type=1505 audit(1264724799.519:13): operation="profile_replace" pid=793 name=/usr/sbin/cupsd
[   15.023314] type=1505 audit(1264724799.523:14): operation="profile_replace" pid=794 name=/usr/sbin/mysqld-akonadi
[   15.025535] type=1505 audit(1264724799.527:15): operation="profile_replace" pid=795 name=/usr/sbin/tcpdump
[   16.572535] ppdev: user-space parallel port driver
[   16.674136]   alloc irq_desc for 28 on node -1
[   16.674141]   alloc kstat_irqs on node -1
[   16.674159] atl1c 0000:08:00.0: irq 28 for MSI/MSI-X
[   16.674635] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.107896] [drm] Setting GART location based on new memory map
[   20.125276] [drm] Loading RS780/RS880 CP Microcode
[   20.126384] [drm] Loading RS780/RS880 PFP Microcode
[   20.141444] [drm] Resetting GPU
[   20.141502] [drm] writeback test succeeded in 1 usecs
[   35.000058] Clocksource tsc unstable (delta = -106029356 ns)
[  276.931129] type=1503 audit(1264725061.431:16): operation="open" pid=1573 parent=1571 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
ryan@ubuntu:~$

and i added the txt dockument with the above txt in it too
[ATTACH]145282[/ATTACH]

---

