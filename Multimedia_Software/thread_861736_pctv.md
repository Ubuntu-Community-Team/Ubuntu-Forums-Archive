---
title: "pctv"
date: 2008-07-16
forum: Multimedia Software
---

### Post by dmm1983 on 2008-07-16
i want to run my pctv dual dvb-t diversity stick its made by pinnacle.
i run 8.04 kubuntu.
a nice how to would be nice

---

### Post by xc3RnbFO8P on 2008-07-16
In Terminal:
> lsusb
Show the output.

---

### Post by voodoo_doctor on 2008-08-24
I was wondering about the same thing. Here is what I get from lsusb:

Bus 003 Device 004: ID 2304:022c Pinnacle Systems, Inc. [hex]

Ubuntu version: 8.04.1

---

### Post by dmm1983 on 2009-04-10
sorry its taken so long i am now using atm 9.04, but heres my output
deborah@newt:~$ lsusb
Bus 001 Device 004: ID 2304:0229 Pinnacle Systems, Inc. [hex]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by xc3RnbFO8P on 2009-04-10
What is the output of **dmesg** in Terminal?

---

### Post by dmm1983 on 2009-04-10
here we go with the whole lot

```
deborah@newt:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 (Ubuntu 2.6.28-11.40-generic)                                                                                       
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)                
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)                  
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f6ea000 (ACPI data)               
[    0.000000]  BIOS-e820: 000000003f6ea000 - 000000003f700000 (ACPI NVS)                
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)                
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)                
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)                
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)                
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)                
[    0.000000] DMI present.                                                              
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.       
[    0.000000] last_pfn = 0x3f6e0 max_arch_pfn = 0x100000                                
[    0.000000] Scanning 0 areas for low memory corruption                                
[    0.000000] modified physical RAM map:                                                
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                 
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)                   
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)                 
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)                 
[    0.000000]  modified: 0000000000100000 - 000000003f6e0000 (usable)                   
[    0.000000]  modified: 000000003f6e0000 - 000000003f6ea000 (ACPI data)                
[    0.000000]  modified: 000000003f6ea000 - 000000003f700000 (ACPI NVS)                 
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)                 
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)                 
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)                 
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)                 
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)                 
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000                 
[    0.000000] RAMDISK: 378c3000 - 37fefc55                                              
[    0.000000] Allocated new RAMDISK: 00881000 - 00fadc55                                
[    0.000000] Move RAMDISK from 00000000378c3000 - 0000000037fefc54 to 00881000 - 00fadc54                                                                                       
[    0.000000] ACPI: RSDP 000F7A10, 0014 (r0 PTLTD )                                     
[    0.000000] ACPI: RSDT 3F6E5E2D, 003C (r1 PTLTD    RSDT    6040000  LTP        0)     
[    0.000000] ACPI: FACP 3F6E9E78, 0084 (r2 INTEL  ALVISO    6040000 LOHR       5F)     
[    0.000000] ACPI: DSDT 3F6E6246, 3C32 (r1 INTEL  ALVISO    6040000 MSFT  100000E)     
[    0.000000] ACPI: FACS 3F6FAFC0, 0040                                                 
[    0.000000] ACPI: APIC 3F6E9EFC, 0068 (r1 INTEL  ALVISO    6040000 LOHR       5F)     
[    0.000000] ACPI: BOOT 3F6E9FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)     
[    0.000000] ACPI: MCFG 3F6E9F9C, 003C (r1 INTEL  ALVISO    6040000 LOHR       5F)     
[    0.000000] ACPI: SSDT 3F6E6064, 01DE (r1  PmRef  Cpu0Cst     3001 INTL 20030224)     
[    0.000000] ACPI: SSDT 3F6E5E69, 01FB (r1  PmRef    CpuPm     3000 INTL 20030224)     
[    0.000000] ACPI: Local APIC address 0xfee00000                                       
[    0.000000] 130MB HIGHMEM available.                                                  
[    0.000000] 883MB LOWMEM available.                                                   
[    0.000000]   mapped low ram: 0 - 373fe000                                            
[    0.000000]   low ram: 00000000 - 373fe000                                            
[    0.000000]   bootmap 00012000 - 00018e80                                             
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]              
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                                      
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                                      
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                                      
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]                                                                                      
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]                                                                                      
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]                                                                                      
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                                                                      
[    0.000000]   #7 [0000881000 - 0000fadc55]      NEW RAMDISK ==> [0000881000 - 0000fadc55]                                                                                      
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]                                                                                      
[    0.000000] Zone PFN ranges:                                                          
[    0.000000]   DMA      0x00000010 -> 0x00001000                                       
[    0.000000]   Normal   0x00001000 -> 0x000373fe                                       
[    0.000000]   HighMem  0x000373fe -> 0x0003f6e0                                       
[    0.000000] Movable zone start PFN for each node                                      
[    0.000000] early_node_map[2] active PFN ranges                                       
[    0.000000]     0: 0x00000010 -> 0x0000009f                                           
[    0.000000]     0: 0x00000100 -> 0x0003f6e0                                           
[    0.000000] On node 0 totalpages: 259695                                              
[    0.000000] free_area_init_node: node 0, pgdat c06d0f00, node_mem_map c1000200        
[    0.000000]   DMA zone: 32 pages used for memmap                                      
[    0.000000]   DMA zone: 0 pages reserved                                              
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0                                      
[    0.000000]   Normal zone: 1736 pages used for memmap                                 
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31                                
[    0.000000]   HighMem zone: 262 pages used for memmap                                 
[    0.000000]   HighMem zone: 33244 pages, LIFO batch:7                                 
[    0.000000]   Movable zone: 0 pages used for memmap                                   
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                            
[    0.000000] ACPI: Local APIC address 0xfee00000                                       
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                        
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)                       
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                       
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                       
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                   
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23            
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                  
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)               
[    0.000000] ACPI: IRQ0 used by override.                                              
[    0.000000] ACPI: IRQ2 used by override.                                              
[    0.000000] ACPI: IRQ9 used by override.                                              
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                             
[    0.000000] Using ACPI (MADT) for SMP configuration information                       
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs                                      
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000         
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000         
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000         
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)    
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                            
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                                 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257665                                                                                        
[    0.000000] Kernel command line: root=UUID=5aca5dba-fba5-42df-a780-7afafce25233 ro quiet splash                                                                                
[    0.000000] Enabling fast FPU save and restore... done.                               
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                     
[    0.000000] Initializing CPU#0                                                        
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                     
[    0.000000] Fast TSC calibration using PIT                                            
[    0.000000] Detected 1496.332 MHz processor.                                          
[    0.004000] Console: colour VGA+ 80x25                                                
[    0.004000] console [tty0] enabled                                                    
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)          
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)            
[    0.004000] allocated 5195840 bytes of page_cgroup                                    
[    0.004000] please try cgroup_disable=memory option if you don't want                 
[    0.004000] Scanning for low memory corruption every 60 seconds                       
[    0.004000] Memory: 1009236k/1039232k available (4126k kernel code, 29164k reserved, 2208k data, 532k init, 134024k highmem)                                                   
[    0.004000] virtual kernel memory layout:                                             
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                         
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                         
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)                         
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)                         
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)                         
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)                         
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)                         
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                                        
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1   
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.66 BogoMIPS (lpj=5985328)                                                          
[    0.004048] Security Framework initialized                                            
[    0.004063] SELinux:  Disabled at boot.                                               
[    0.004098] AppArmor: AppArmor initialized                                            
[    0.004111] Mount-cache hash table entries: 512                                       
[    0.004334] Initializing cgroup subsys ns                                             
[    0.004342] Initializing cgroup subsys cpuacct                                        
[    0.004345] Initializing cgroup subsys memory                                         
[    0.004351] Initializing cgroup subsys freezer                                        
[    0.004375] CPU: L1 I cache: 32K, L1 D cache: 32K                                     
[    0.004378] CPU: L2 cache: 1024K                                                      
[    0.004398] Checking 'hlt' instruction... OK.                                         
[    0.020890] SMP alternatives: switching to UP code                                    
[    0.152022] ACPI: Core revision 20080926                                              
[    0.154651] ACPI: Checking initramfs for custom DSDT                                  
[    0.551375] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                      
[    0.591074] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08         
[    0.592002] Brought up 1 CPUs                                                         
[    0.592002] Total of 1 processors activated (2992.66 BogoMIPS).                       
[    0.592002] CPU0 attaching NULL sched-domain.                                         
[    0.592002] net_namespace: 776 bytes                                                  
[    0.592002] Booting paravirtualized kernel on bare hardware                           
[    0.592002] Time:  8:37:30  Date: 04/09/09                                            
[    0.592002] regulator: core version 0.5                                               
[    0.592002] NET: Registered protocol family 16                                        
[    0.592002] EISA bus registered                                                       
[    0.592002] ACPI: bus type pci registered                                             
[    0.592002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255          
[    0.592002] PCI: MCFG area at e0000000 reserved in E820                               
[    0.592002] PCI: Using MMCONFIG for extended config space                             
[    0.592002] PCI: Using configuration type 1 for base access                           
[    0.592002] ACPI: EC: Look up EC in DSDT                                              
[    0.596065] ACPI: EC: non-query interrupt received, switching to interrupt mode       
[    0.604273] ACPI: EC: GPE storm detected, transactions will use polling mode          
[    0.634254] ACPI: Interpreter enabled                                                 
[    0.634258] ACPI: (supports S0 S3 S4 S5)                                              
[    0.634281] ACPI: Using IOAPIC for interrupt routing                                  
[    0.688678] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62             
[    0.688681] ACPI: EC: driver started in interrupt mode                                
[    0.688807] ACPI: No dock devices found.                                              
[    0.688819] ACPI: PCI Root Bridge [PCI0] (0000:00)                                    
[    0.688912] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0080000-0xb00fffff]              
[    0.688918] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]                         
[    0.688924] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]              
[    0.688930] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0000000-0xb003ffff]              
[    0.688963] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]                  
[    0.689075] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]                         
[    0.689137] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]                         
[    0.689199] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]                         
[    0.689263] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]                         
[    0.689333] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0040000-0xb00403ff]              
[    0.689383] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                     
[    0.689390] pci 0000:00:1d.7: PME# disabled                                           
[    0.689489] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]                         
[    0.689498] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]                         
[    0.689507] pci 0000:00:1e.2: reg 18 32bit mmio: [0xb0040800-0xb00409ff]              
[    0.689516] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xb0040400-0xb00404ff]              
[    0.689546] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold                     
[    0.689551] pci 0000:00:1e.2: PME# disabled                                           
[    0.689591] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]                         
[    0.689600] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]                         
[    0.689641] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold                     
[    0.689646] pci 0000:00:1e.3: PME# disabled                                           
[    0.689744] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000                        
[    0.689752] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO   
[    0.689757] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO            
[    0.689783] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]                             
[    0.689792] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]                             
[    0.689801] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]                             
[    0.689810] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]                             
[    0.689818] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]                         
[    0.689896] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]                         
[    0.689984] pci 0000:06:05.0: reg 10 32bit mmio: [0xb0100000-0xb010ffff]              
[    0.690090] pci 0000:06:07.0: reg 10 io port: [0x3000-0x30ff]                         
[    0.690100] pci 0000:06:07.0: reg 14 32bit mmio: [0xb0110000-0xb01100ff]              
[    0.690151] pci 0000:06:07.0: supports D1 D2                                          
[    0.690153] pci 0000:06:07.0: PME# supported from D1 D2 D3hot D3cold                  
[    0.690159] pci 0000:06:07.0: PME# disabled                                           
[    0.690211] pci 0000:06:09.0: reg 10 32bit mmio: [0x000000-0x000fff]                  
[    0.690225] pci 0000:06:09.0: supports D1 D2                                          
[    0.690227] pci 0000:06:09.0: PME# supported from D0 D1 D2 D3hot D3cold               
[    0.690233] pci 0000:06:09.0: PME# disabled                                           
[    0.690282] pci 0000:00:1e.0: transparent bridge                                      
[    0.690287] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]                         
[    0.690293] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]              
[    0.690335] bus 00 -> node 0                                                          
[    0.690343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                       
[    0.690820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]                  
[    0.695865] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)                             
[    0.695995] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)                             
[    0.696127] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)                             
[    0.696253] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)                             
[    0.696376] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)                             
[    0.696498] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)                             
[    0.696621] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.                
[    0.696747] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)                             
[    0.696989] ACPI: WMI: Mapper loaded                                                  
[    0.697213] SCSI subsystem initialized                                                
[    0.697261] libata version 3.00 loaded.                                               
[    0.697316] usbcore: registered new interface driver usbfs                            
[    0.697336] usbcore: registered new interface driver hub                              
[    0.697367] usbcore: registered new device driver usb                                 
[    0.697502] PCI: Using ACPI for IRQ routing                                           
[    0.697617] Bluetooth: Core ver 2.13                                                  
[    0.697617] NET: Registered protocol family 31                                        
[    0.697617] Bluetooth: HCI device and connection manager initialized                  
[    0.697617] Bluetooth: HCI socket layer initialized                                   
[    0.697617] NET: Registered protocol family 8                                         
[    0.697617] NET: Registered protocol family 20                                        
[    0.697617] NetLabel: Initializing                                                    
[    0.697617] NetLabel:  domain hash size = 128                                         
[    0.697617] NetLabel:  protocols = UNLABELED CIPSOv4                                  
[    0.697617] NetLabel:  unlabeled traffic allowed by default                           
[    0.697617] hpet clockevent registered                                                
[    0.697617] HPET: 3 timers in total, 0 timers will be used for per-cpu timer          
[    0.697617] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                   
[    0.697617] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                        
[    0.700091] AppArmor: AppArmor Filesystem Enabled                                     
[    0.700100] pnp: PnP ACPI init                                                        
[    0.700100] ACPI: bus type pnp registered                                             
[    0.713479] pnp: PnP ACPI: found 8 devices                                            
[    0.713482] ACPI: ACPI bus type pnp unregistered                                      
[    0.713487] PnPBIOS: Disabled by ACPI PNP                                             
[    0.713506] system 00:04: ioport range 0x800-0x80f has been reserved                  
[    0.713509] system 00:04: ioport range 0x1000-0x107f has been reserved                
[    0.713513] system 00:04: ioport range 0x1180-0x11bf has been reserved                
[    0.713516] system 00:04: ioport range 0x1200-0x1200 has been reserved                
[    0.713519] system 00:04: ioport range 0x1204-0x1204 has been reserved                
[    0.713524] system 00:04: iomem range 0xe0000000-0xefffffff has been reserved         
[    0.713527] system 00:04: iomem range 0xf0000000-0xf0003fff has been reserved         
[    0.713531] system 00:04: iomem range 0xf0004000-0xf0004fff has been reserved         
[    0.713535] system 00:04: iomem range 0xf0005000-0xf0005fff has been reserved         
[    0.713538] system 00:04: iomem range 0xf0008000-0xf000bfff has been reserved         
[    0.713542] system 00:04: iomem range 0xfec18000-0xfec180ff has been reserved         
[    0.713545] system 00:04: iomem range 0xfed20000-0xfed8ffff has been reserved         
[    0.748306] pci 0000:06:09.0: CardBus bridge, secondary bus 0000:07                   
[    0.748309] pci 0000:06:09.0:   IO window: 0x003400-0x0034ff                          
[    0.748316] pci 0000:06:09.0:   IO window: 0x003800-0x0038ff                          
[    0.748323] pci 0000:06:09.0:   PREFETCH window: 0x50000000-0x53ffffff                
[    0.748329] pci 0000:06:09.0:   MEM window: 0x58000000-0x5bffffff                     
[    0.748336] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06                       
[    0.748340] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff                              
[    0.748347] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff                     
[    0.748353] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff    
[    0.748370] pci 0000:00:1e.0: setting latency timer to 64                             
[    0.748387] pci 0000:06:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22              
[    0.748395] bus: 00 index 0 io port: [0x00-0xffff]                                    
[    0.748398] bus: 00 index 1 mmio: [0x000000-0xffffffff]                               
[    0.748401] bus: 06 index 0 io port: [0x3000-0x3fff]                                  
[    0.748404] bus: 06 index 1 mmio: [0xb0100000-0xb01fffff]                             
[    0.748407] bus: 06 index 2 mmio: [0x50000000-0x53ffffff]                             
[    0.748409] bus: 06 index 3 io port: [0x00-0xffff]                                    
[    0.748412] bus: 06 index 4 mmio: [0x000000-0xffffffff]                               
[    0.748415] bus: 07 index 0 io port: [0x3400-0x34ff]                                  
[    0.748418] bus: 07 index 1 io port: [0x3800-0x38ff]                                  
[    0.748420] bus: 07 index 2 mmio: [0x50000000-0x53ffffff]                             
[    0.748423] bus: 07 index 3 mmio: [0x58000000-0x5bffffff]                             
[    0.748435] NET: Registered protocol family 2                                         
[    0.748571] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)         
[    0.748887] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)      
[    0.750062] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)               
[    0.750909] TCP: Hash tables configured (established 131072 bind 65536)               
[    0.750914] TCP reno registered                                                       
[    0.751142] NET: Registered protocol family 1                                         
[    0.751331] checking if image is initramfs... it is                                   
[    1.200060] Switched to high resolution mode on CPU 0                                 
[    1.559274] Freeing initrd memory: 7347k freed                                        
[    1.559339] Simple Boot Flag at 0x37 set to 0x1                                       
[    1.559380] cpufreq: No nForce2 chipset.                                              
[    1.559583] audit: initializing netlink socket (disabled)                             
[    1.559611] type=2000 audit(1239266250.556:1): initialized                            
[    1.569369] highmem bounce pool size: 64 pages                                        
[    1.569377] HugeTLB registered 4 MB page size, pre-allocated 0 pages                  
[    1.570997] VFS: Disk quotas dquot_6.5.1                                              
[    1.571068] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                
[    1.571820] fuse init (API version 7.10)                                              
[    1.571924] msgmni has been set to 1724                                               
[    1.572158] alg: No test for stdrng (krng)                                            
[    1.572173] io scheduler noop registered                                              
[    1.572176] io scheduler anticipatory registered                                      
[    1.572178] io scheduler deadline registered                                          
[    1.572198] io scheduler cfq registered (default)                                     
[    1.572214] pci 0000:00:02.0: Boot video device                                       
[    1.598061] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                           
[    1.598073] pciehp: PCI Express Hot Plug Controller Driver version: 0.4               
[    1.610749] ACPI: AC Adapter [ADP1] (off-line)                                        
[    2.185603] ACPI: Battery Slot [BAT0] (battery present)                               
[    2.185692] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0 
[    2.185695] ACPI: Power Button (FF) [PWRF]                                            
[    2.185752] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1                                                                                        
[    2.197959] ACPI: Lid Switch [LID0]                                                   
[    2.198016] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2                                                                                 
[    2.198022] ACPI: Sleep Button (CM) [SLPB]                                            
[    2.210744] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                           
[    2.210776] processor ACPI_CPU:00: registered as cooling_device0                      
[    2.210780] ACPI: Processor [CPU0] (supports 8 throttling states)                     
[    2.422340] thermal LNXTHERM:01: registered as thermal_zone0                          
[    2.500776] ACPI: Thermal Zone [TZS0] (35 C)                                          
[    2.542946] thermal LNXTHERM:02: registered as thermal_zone1                          
[    2.570239] ACPI: Thermal Zone [TZS1] (19 C)                                          
[    2.570292] isapnp: Scanning for PnP cards...                                         
[    2.924219] isapnp: No Plug & Play device found                                       
[    2.925540] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                     
[    2.925935] serial 0000:00:1e.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21           
[    2.925944] serial 0000:00:1e.3: PCI INT B disabled                                   
[    2.926764] brd: module loaded                                                        
[    2.927153] loop: module loaded                                                       
[    2.927243] Fixed MDIO Bus: probed                                                    
[    2.927253] PPP generic driver version 2.4.2                                          
[    2.927320] input: Macintosh mouse button emulation as /devices/virtual/input/input3  
[    2.927358] Driver 'sd' needs updating - please use bus_type methods                  
[    2.927369] Driver 'sr' needs updating - please use bus_type methods                  
[    2.927459] ata_piix 0000:00:1f.1: version 2.12                                       
[    2.927472] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16         
[    2.927519] ata_piix 0000:00:1f.1: setting latency timer to 64                        
[    2.927636] scsi0 : ata_piix                                                          
[    2.927742] scsi1 : ata_piix                                                          
[    2.928573] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14           
[    2.928577] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15           
[    3.292631] ata1.00: ATA-6: ST960821A, 3.01, max UDMA/100                             
[    3.292634] ata1.00: 117210240 sectors, multi 16: LBA48                               
[    3.292681] ata1.01: ATAPI: Slimtype DVDRW SSM-8515S, GS06, max UDMA/33               
[    3.308606] ata1.00: configured for UDMA/100                                          
[    3.348411] ata1.01: configured for UDMA/33                                           
[    3.349659] ata2: port disabled. ignoring.                                            
[    3.349801] scsi 0:0:0:0: Direct-Access     ATA      ST960821A        3.01 PQ: 0 ANSI: 5                                                                                       
[    3.349924] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB) 
[    3.349947] sd 0:0:0:0: [sda] Write Protect is off                                    
[    3.349950] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                 
[    3.349981] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                            
[    3.350053] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB) 
[    3.350070] sd 0:0:0:0: [sda] Write Protect is off                                    
[    3.350073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                 
[    3.350102] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                            
[    3.350106]  sda: sda1 sda2 sda3 < sda5 sda6 >                                        
[    3.416994] sd 0:0:0:0: [sda] Attached SCSI disk                                      
[    3.417049] sd 0:0:0:0: Attached scsi generic sg0 type 0                              
[    3.418830] scsi 0:0:1:0: CD-ROM            Slimtype DVDRW SSM-8515S  GS06 PQ: 0 ANSI: 5                                                                                       
[    3.428310] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray     
[    3.428315] Uniform CD-ROM driver Revision: 3.20                                      
[    3.428424] sr 0:0:1:0: Attached scsi CD-ROM sr0                                      
[    3.428469] sr 0:0:1:0: Attached scsi generic sg1 type 5                              
[    3.429189] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                
[    3.429219] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23         
[    3.429254] ehci_hcd 0000:00:1d.7: setting latency timer to 64                        
[    3.429258] ehci_hcd 0000:00:1d.7: EHCI Host Controller                               
[    3.429339] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1      
[    3.433251] ehci_hcd 0000:00:1d.7: debug port 1                                       
[    3.433259] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported             
[    3.433279] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000                          
[    3.448011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                         
[    3.448126] usb usb1: configuration #1 chosen from 1 choice                           
[    3.448163] hub 1-0:1.0: USB hub found                                                
[    3.448175] hub 1-0:1.0: 8 ports detected                                             
[    3.448318] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                    
[    3.448338] uhci_hcd: USB Universal Host Controller Interface driver                  
[    3.448370] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23         
[    3.448378] uhci_hcd 0000:00:1d.0: setting latency timer to 64                        
[    3.448382] uhci_hcd 0000:00:1d.0: UHCI Host Controller                               
[    3.448437] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2      
[    3.448464] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820                         
[    3.448552] usb usb2: configuration #1 chosen from 1 choice                           
[    3.448583] hub 2-0:1.0: USB hub found                                                
[    3.448592] hub 2-0:1.0: 2 ports detected                                             
[    3.448705] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17         
[    3.448713] uhci_hcd 0000:00:1d.1: setting latency timer to 64                        
[    3.448717] uhci_hcd 0000:00:1d.1: UHCI Host Controller                               
[    3.448763] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3      
[    3.448798] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840                         
[    3.448886] usb usb3: configuration #1 chosen from 1 choice                           
[    3.448919] hub 3-0:1.0: USB hub found                                                
[    3.448927] hub 3-0:1.0: 2 ports detected                                             
[    3.449018] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18         
[    3.449025] uhci_hcd 0000:00:1d.2: setting latency timer to 64                        
[    3.449029] uhci_hcd 0000:00:1d.2: UHCI Host Controller                               
[    3.449075] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4      
[    3.449109] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860                         
[    3.449200] usb usb4: configuration #1 chosen from 1 choice                           
[    3.449229] hub 4-0:1.0: USB hub found                                                
[    3.449237] hub 4-0:1.0: 2 ports detected                                             
[    3.449335] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19         
[    3.449342] uhci_hcd 0000:00:1d.3: setting latency timer to 64                        
[    3.449347] uhci_hcd 0000:00:1d.3: UHCI Host Controller                               
[    3.449402] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5      
[    3.449442] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880                         
[    3.449530] usb usb5: configuration #1 chosen from 1 choice                           
[    3.449560] hub 5-0:1.0: USB hub found                                                
[    3.449571] hub 5-0:1.0: 2 ports detected                                             
[    3.449717] usbcore: registered new interface driver libusual                         
[    3.449768] usbcore: registered new interface driver usbserial                        
[    3.449781] USB Serial support registered for generic                                 
[    3.449798] usbcore: registered new interface driver usbserial_generic                
[    3.449800] usbserial: USB Serial Driver core                                         
[    3.449856] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12    
[    3.450168] i8042.c: Detected active multiplexing controller, rev 1.1.                
[    3.450245] serio: i8042 KBD port at 0x60,0x64 irq 1                                  
[    3.450252] serio: i8042 AUX0 port at 0x60,0x64 irq 12                                
[    3.450255] serio: i8042 AUX1 port at 0x60,0x64 irq 12                                
[    3.450258] serio: i8042 AUX2 port at 0x60,0x64 irq 12                                
[    3.450261] serio: i8042 AUX3 port at 0x60,0x64 irq 12                                
[    3.450457] mice: PS/2 mouse device common for all mice                               
[    3.450646] rtc_cmos 00:05: RTC can wake from S4                                      
[    3.450689] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                     
[    3.450724] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs             
[    3.450807] device-mapper: uevent: version 1.0.3                                      
[    3.450952] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]                                                                                   
[    3.451008] device-mapper: multipath: version 1.0.5 loaded                            
[    3.451011] device-mapper: multipath round-robin: version 1.0.0 loaded                
[    3.451116] EISA: Probing bus 0 at eisa.0                                             
[    3.451124] Cannot allocate resource for EISA slot 1                                  
[    3.451127] Cannot allocate resource for EISA slot 2                                  
[    3.451130] Cannot allocate resource for EISA slot 3                                  
[    3.451153] EISA: Detected 0 cards.                                                   
[    3.451227] cpuidle: using governor ladder                                            
[    3.451311] cpuidle: using governor menu                                              
[    3.451915] TCP cubic registered                                                      
[    3.452059] NET: Registered protocol family 10                                        
[    3.452538] lo: Disabled Privacy Extensions                                           
[    3.452897] NET: Registered protocol family 17                                        
[    3.452921] Bluetooth: L2CAP ver 2.11                                                 
[    3.452923] Bluetooth: L2CAP socket layer initialized                                 
[    3.452927] Bluetooth: SCO (Voice Link) ver 0.6                                       
[    3.452929] Bluetooth: SCO socket layer initialized                                   
[    3.452973] Bluetooth: RFCOMM socket layer initialized                                
[    3.452981] Bluetooth: RFCOMM TTY layer initialized                                   
[    3.452984] Bluetooth: RFCOMM ver 1.10                                                
[    3.453040] Using IPI No-Shortcut mode                                                
[    3.453141] registered taskstats version 1                                            
[    3.453279]   Magic number: 5:91:624                                                  
[    3.453390] rtc_cmos 00:05: setting system clock to 2009-04-09 08:37:33 UTC (1239266253)                                                                                       
[    3.453394] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                      
[    3.453396] EDD information not available.                                            
[    3.453760] Freeing unused kernel memory: 532k freed                                  
[    3.453904] Write protecting the kernel text: 4128k                                   
[    3.453952] Write protecting the kernel read-only data: 1532k                         
[    3.456959] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4                                                                                 
[    3.944458] usb 2-1: new low speed USB device using uhci_hcd and address 2            
[    4.112759] Marking TSC unstable due to TSC halts in idle                             
[    4.120167] usb 2-1: configuration #1 chosen from 1 choice                            
[    4.173389] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)                    
[    4.173432] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too                                                                      
[    4.177012] 8139too Fast Ethernet driver 0.9.28                                       
[    4.177066] 8139too 0000:06:07.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20          
[    4.178400] eth0: RealTek RTL8139 at 0x3000, 00:0a:e4:f1:62:b8, IRQ 20                
[    4.178403] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'                        
[    4.420658] usbcore: registered new interface driver hiddev                           
[    4.436238] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5                                                                         
[    4.436562] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0                                               
[    4.436588] usbcore: registered new interface driver usbhid                           
[    4.436592] usbhid: v2.6:USB HID core driver                                          
[    4.790498] PM: Starting manual resume from disk                                      
[    4.790503] PM: Resume from partition 8:6                                             
[    4.790505] PM: Checking hibernation image.                                           
[    4.790718] PM: Resume from disk failed.                                              
[    4.814649] EXT4-fs: barriers enabled                                                 
[    4.830035] kjournald2 starting.  Commit interval 5 seconds                           
[    4.830048] EXT4-fs: delayed allocation enabled                                       
[    4.830050] EXT4-fs: file extents enabled                                             
[    4.831421] EXT4-fs: mballoc enabled                                                  
[    4.831427] EXT4-fs: mounted filesystem with ordered data mode.                       
[   10.578181] udev: starting version 140                                                
[   10.968479] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6                                                                               
[   11.004626] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)            
[   11.305588] ath_hal: module license 'Proprietary' taints kernel.                      
[   11.307522] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.324362] wlan: 0.9.4                                                               
[   11.335647] ath_pci: 0.9.4                                                            
[   11.335707] ath_pci 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21          
[   12.117866] ath_rate_sample: 1.2 (0.9.4)                                              
[   12.123492] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps                              
[   12.123502] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps                                                                 
[   12.123515] wifi0: H/W encryption support: WEP AES AES_CCM TKIP                       
[   12.123520] wifi0: mac 7.8 phy 4.5 radio 5.6                                          
[   12.123527] wifi0: Use hw queue 1 for WME_AC_BE traffic                               
[   12.123529] wifi0: Use hw queue 0 for WME_AC_BK traffic                               
[   12.123532] wifi0: Use hw queue 2 for WME_AC_VI traffic                               
[   12.123534] wifi0: Use hw queue 3 for WME_AC_VO traffic                               
[   12.123537] wifi0: Use hw queue 8 for CAB traffic                                     
[   12.123539] wifi0: Use hw queue 9 for beacons                                         
[   12.731385] Linux agpgart interface v0.103                                            
[   12.751476] acer-wmi: Acer Laptop ACPI-WMI Extras                                     
[   12.753669] Registered led device: acer-wmi::mail                                     
[   12.761636] acer-wmi: software RFKILL enabled                                         
[   12.776197] input: PC Speaker as /devices/platform/pcspkr/input/input7                
[   12.830907] intel_rng: FWH not detected                                               
[   12.831800] wifi0: Atheros 5212: mem=0xb0100000, irq=21                               
[   12.869604] agpgart-intel 0000:00:00.0: Intel 915GM Chipset                           
[   12.869952] agpgart-intel 0000:00:00.0: detected 7932K stolen memory                  
[   12.874433] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000             
[   12.982673] yenta_cardbus 0000:06:09.0: CardBus bridge found [1025:006a]              
[   12.982702] yenta_cardbus 0000:06:09.0: Using CSCINT to route CSC interrupts to PCI   
[   12.982706] yenta_cardbus 0000:06:09.0: Routing CardBus interrupts to PCI             
[   12.982712] yenta_cardbus 0000:06:09.0: TI: mfunc 0x00001022, devctl 0x44             
[   13.008312] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                                                                            
[   13.011253] iTCO_vendor_support: vendor-support=0                                     
[   13.013580] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                           
[   13.013754] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)           
[   13.013868] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                      
[   13.175249] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21        
[   13.175338] Intel ICH 0000:00:1e.2: setting latency timer to 64                       
[   13.213434] yenta_cardbus 0000:06:09.0: ISA IRQ mask 0x0cf8, PCI irq 22               
[   13.213440] yenta_cardbus 0000:06:09.0: Socket status: 30000006                       
[   13.213445] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a                                                                                      
[   13.213456] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff                                                                                  
[   13.213460] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.     
[   13.213731] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff                                                                       
[   13.213735] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff                                                                       
[   13.559489] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.       
[   13.561243] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7                                                                                 
[   13.561976] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.       
[   13.562581] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.       
[   13.563369] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.       
[   13.696160] Clocksource tsc unstable (delta = -371325151 ns)                          
[   13.832274] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000                                                                                       
[   13.866203] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8                                                                                   
[   14.000038] intel8x0_measure_ac97_clock: measured 55319 usecs                         
[   14.000042] intel8x0: clocking to 48000                                               
[   14.182877] lp: driver loaded but no devices found                                    
[   14.217151] input: Acer hotkey driver as /devices/virtual/input/input9                
[   14.225930] Acer Travelmate hotkey driver v0.5.34                                     
[   14.311039] Adding 979924k swap on /dev/sda6.  Priority:-1 extents:1 across:979924k   
[   14.330143] EXT4 FS on sda1, internal journal on sda1:8                               
[   14.599179] EXT4-fs: barriers enabled                                                 
[   14.609879] kjournald2 starting.  Commit interval 5 seconds                           
[   14.610117] EXT4 FS on sda2, internal journal on sda2:8                               
[   14.610121] EXT4-fs: delayed allocation enabled                                       
[   14.610123] EXT4-fs: file extents enabled                                             
[   14.611039] EXT4-fs: mballoc enabled                                                  
[   14.611045] EXT4-fs: mounted filesystem with ordered data mode.                       
[   14.643367] EXT4-fs: barriers enabled                                                 
[   14.658221] kjournald2 starting.  Commit interval 5 seconds                           
[   14.658494] EXT4 FS on sda5, internal journal on sda5:8                               
[   14.658497] EXT4-fs: delayed allocation enabled                                       
[   14.658499] EXT4-fs: file extents enabled                                             
[   14.659370] EXT4-fs: mballoc enabled                                                  
[   14.659375] EXT4-fs: mounted filesystem with ordered data mode.                       
[   15.231417] type=1505 audit(1239266265.274:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1763                                                  
[   15.231624] type=1505 audit(1239266265.274:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1763                                                        
[   15.231711] type=1505 audit(1239266265.274:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1763                          
[   15.231771] type=1505 audit(1239266265.274:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1763                               
[   15.429456] type=1505 audit(1239266265.474:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1768                                         
[   15.429790] type=1505 audit(1239266265.474:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1768                                                        
[   15.470817] type=1505 audit(1239266265.514:8): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=1772                                               
[   15.516530] type=1505 audit(1239266265.562:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1776                                                      
[   18.732725] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                              
[   18.732729] Bluetooth: BNEP filters: protocol multicast                               
[   18.766553] Bridge firewalling registered                                             
[   20.162458] ppdev: user-space parallel port driver                                    
[   22.900966] [drm] Initialized drm 1.1.0 20060810                                      
[   22.931996] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16              
[   22.932018] pci 0000:00:02.0: setting latency timer to 64                             
[   22.932655] [drm] Initialized i915 1.6.0 20080730 on minor 0                          
[   22.935556] [drm:i915_setparam] *ERROR* unknown parameter 4                           
[   22.935585] [drm:i915_getparam] *ERROR* Unknown parameter 6                           
[   23.955613] eth0: link down                                                           
[   23.955947] ADDRCONF(NETDEV_UP): eth0: link is not ready                              
[   24.387330] [drm:i915_getparam] *ERROR* Unknown parameter 6                           
[   34.852161] ath0: no IPv6 routers present                                             
[   61.240511] CPU0 attaching NULL sched-domain.                                         
[   61.240616] CPU0 attaching NULL sched-domain.                                         
[   67.212712] CPU0 attaching NULL sched-domain.                                         
[   67.212887] CPU0 attaching NULL sched-domain.                                         
[ 1548.052035] ACPI: EC: missing confirmations, switch off interrupt mode.               
[10149.536735] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0                                                                               
[10149.563344] mtrr: no MTRR for c0000000,10000000 found                                 
[10150.018563] [drm:i915_setparam] *ERROR* unknown parameter 4                           
[10150.032086] [drm:i915_getparam] *ERROR* Unknown parameter 6                           
[10151.150184] [drm:i915_getparam] *ERROR* Unknown parameter 6                           
[10163.397474] CPU0 attaching NULL sched-domain.                                         
[10163.397856] CPU0 attaching NULL sched-domain.                                         
[71273.663852] end_request: I/O error, dev sr0, sector 12608700                          
[71273.941996] UDF-fs: Partition marked readonly; forcing readonly mount                 
[71274.018113] UDF-fs INFO UDF: Mounting volume 'HS30AAW1', timestamp 2009/02/12 02:14 (1000)                                                                                     
[78582.754117] end_request: I/O error, dev sr0, sector 12608700                          
[78582.996553] UDF-fs: Partition marked readonly; forcing readonly mount                 
[78583.064558] UDF-fs INFO UDF: Mounting volume 'HS30AAW1', timestamp 2009/02/12 02:14 (1000)                                                                                     
[90116.776048] usb 1-8: new high speed USB device using ehci_hcd and address 3           
[90116.909262] usb 1-8: configuration #1 chosen from 1 choice                            
[90118.227336] dib0700: loaded with support for 8 different device-types                 
[90118.227500] dvb-usb: found a 'Pinnacle PCTV Dual DVB-T Diversity Stick' in cold state, will try to load a firmware                                                             
[90118.227506] usb 1-8: firmware: requesting dvb-usb-dib0700-1.20.fw                     
[90118.483240] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'         
[90118.758845] dib0700: firmware started successfully.                                   
[90119.260070] dvb-usb: found a 'Pinnacle PCTV Dual DVB-T Diversity Stick' in warm state.
[90119.260141] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[90119.260379] DVB: registering new adapter (Pinnacle PCTV Dual DVB-T Diversity Stick)
[90119.626848] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[90119.856477] DiB0070: successfully identified
[90119.856486] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[90119.856726] DVB: registering new adapter (Pinnacle PCTV Dual DVB-T Diversity Stick)
[90120.107146] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[90120.371855] DiB0070: successfully identified
[90120.371866] dvb-usb: Pinnacle PCTV Dual DVB-T Diversity Stick successfully initialized and connected.
[90120.372029] usbcore: registered new interface driver dvb_usb_dib0700
[90385.733548] usb 1-8: USB disconnect, address 3
[90385.902891] dvb-usb: Pinnacle PCTV Dual DVB-T Diversity Stick successfully deinitialized and disconnected.
[90389.316047] usb 1-5: new high speed USB device using ehci_hcd and address 4
[90389.507591] usb 1-5: configuration #1 chosen from 1 choice
[90389.508829] dvb-usb: found a 'Pinnacle PCTV Dual DVB-T Diversity Stick' in cold state, will try to load a firmware
[90389.508837] usb 1-5: firmware: requesting dvb-usb-dib0700-1.20.fw
[90389.591555] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[90389.870997] dib0700: firmware started successfully.
[90390.372062] dvb-usb: found a 'Pinnacle PCTV Dual DVB-T Diversity Stick' in warm state.
[90390.373373] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[90390.373670] DVB: registering new adapter (Pinnacle PCTV Dual DVB-T Diversity Stick)
[90390.759217] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[90391.024124] DiB0070: successfully identified
[90391.024134] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[90391.024394] DVB: registering new adapter (Pinnacle PCTV Dual DVB-T Diversity Stick)
[90391.356049] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[90391.621012] DiB0070: successfully identified
[90391.621022] dvb-usb: Pinnacle PCTV Dual DVB-T Diversity Stick successfully initialized and connected.
[90933.463296] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[90933.463303] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[90933.463307] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
```

---

### Post by xc3RnbFO8P on 2009-04-10
Do you got Kaffeine or Me-Tv installed?

---

### Post by dmm1983 on 2009-04-10
kaffeine why??

---

### Post by xc3RnbFO8P on 2009-04-10
To watch TV :)

---

### Post by dmm1983 on 2009-04-10
well trying to

---

### Post by xc3RnbFO8P on 2009-04-10
Just install Kaffeine and scan channels.

---

### Post by soapBAR2 on 2009-04-10
Since you're using DVB, you can get the channels.conf (a list of broadcasters with all the frequency and tuning minutea) file specific to your area with

```
sudo apt-get install dvb-utils
```

This package is a godsend - it comes with just about every tool to do just about anything with DVB. The channels.conf resides in /usr/share/dvb/dvb-X/YY-CITYNAME, where X is your DVB service (DVB-T for terrestrial - ie, free-to-air, DVB-S for satellite, DVB-C for cable), YY is your country's 2 letter code (eg, Australia is AU), and CITYNAME is of course your local tower's broadcast point. Then, using a player with good DVB support, you can open the channels.conf and step through the programs. I use MPlayer, mplayer dvb://PATH/CHANNELS.CONF. Works a treat.

You can also sling the broadcast across a network using Kaffeine (easiest, but limited to kaffeine clients), VLC (good, but limited interlacing, and you'll have to script your own changer using VLC's many interfaces), MPlayer (insanely complex, but best picture and low loads), Myth (never got it working, but you might have better luck), or some fifth alternative (look into DVBstream, it's got just enough functionality to work as a TV server).

---

### Post by dmm1983 on 2009-04-11
i still cant get any channels 
i have tried the above

---

### Post by xc3RnbFO8P on 2009-04-11
Did you use Kaffeine?

---

### Post by dmm1983 on 2009-04-11
yes still nothing

---

### Post by xc3RnbFO8P on 2009-04-11
In Kaffeine, DVB> Configure DVB> DVB Device ,is there 1 or 2 devices? 
and in Source do you have the au- channels?

---

### Post by dmm1983 on 2009-04-11
comes up as 0.0 devices
and yes i do get au-xx

---

### Post by xc3RnbFO8P on 2009-04-11
What kind of antenna are you using.
Some transmitters use vertical other use horizontal signal,
do you have free view to the transmitter (mast).

---

### Post by dmm1983 on 2009-04-11
it come with 2 passive mini-rod antennas

---

### Post by xc3RnbFO8P on 2009-04-11
> it come with 2 passive mini-rod antennas
Do you know where the transmitter is?
Did try to use the antenna horizontal?


Tasmania

Hobart, Launceston and King Island
1 January &#8211; 30 June 2013
[http://www.digitalready.gov.au/rolloutmap.aspx]("http://www.digitalready.gov.au/rolloutmap.aspx")

---

### Post by dmm1983 on 2009-04-11
yes i do where i live there is 2 
yes i tried horizontal

---

### Post by xc3RnbFO8P on 2009-04-11
There is no Digital TV until 2013, see post #20

---

### Post by dmm1983 on 2009-04-11
So not even standard channels either then

---

### Post by xc3RnbFO8P on 2009-04-11
> So not even standard channels either then
No its digital only

---

### Post by soapBAR2 on 2009-04-11
> **Ringi said:**
> Do you know where the transmitter is?
Did try to use the antenna horizontal?
Tasmania

Hobart, Launceston and King Island
1 January &#8211; 30 June 2013
[http://www.digitalready.gov.au/rolloutmap.aspx]("http://www.digitalready.gov.au/rolloutmap.aspx")


```

# FORMAT:
# Title | Frequency | Bandwidth
# Australia / Tasmania / Hobart
# ABC VHF 8
T 191625000 7MHz 
# SBS VHF 9a
T 205500000 7MHz
# SCT VHF 10
T 212500000 7MHz
# WIN VHF 7
T 184500000 7MHz
# TDT VHF 11
T 219500000 7MHz

```

There's all you need.

I can't imagine that this is a hardware issue - I think it may be a reception issue? Remember, digital reception is something you either get or you don't - it's not like analogue, where the signal degrades to nothing in low reception areas. 

The problem might be the crappy antennas that come with USB DVB sticks, or you might live in a bad area. Have you tried tuning in with a regular set-top box? If you haven't, try it (if you haven't got one, ask your neighbours, see if they get a digital signal). I can't tell you if you'll get a signal or not, but if you live in a valley, or beside a mountain, or something of that nature, you'll run into troubles.

To get feedback on your tuning attempts, try VLC - it's a bit of a pain to re-format the text to what VLC likes, but it will tell you what the problem is. If you get a loop of "unable to get signal lock - tuning again" in your VLC message box, it's a reception issue. Here, I'll post the first channel from my VLC TV playlist, just take my numbers and put your own in, then save it as PLAYLIST.M3U and open it with VLC (see below).

```
#EXTM3U
#EXTVLCOPT:dvb-adapter=0
#EXTVLCOPT:dvb-frequency=226500000
#EXTVLCOPT:dvb-inversion=2
#EXTVLCOPT:dvb-fec=9
#EXTVLCOPT:dvb-bandwidth=7
#EXTVLCOPT:dvb-guard=16
#EXTVLCOPT:dvb-transmission=8
#EXTVLCOPT:program=579
dvb://

```

****IMPORTANT***** If you're doing it with playlists (as above), open VLC with --m3u-extvlcopt from command line (see below) (sorry, couldn't find the option in VLC's GUI preferences menu). When you have VLC open, click Tools-> Messages (or CTRL+M) to show the message console.

```
vlc --m3u-extvlcopt
```

EDIT:

> **Ringi said:**
> There is no Digital TV until 2013, see post #20

Don't give up! Digital rollout in Australia has been around for years - I've been using digital for a few years now. The 2013 is the date that analogue will shut down.

---

### Post by dmm1983 on 2009-04-11
Thanks for the help even though we do have a couple of tdt which is ten and abc2... 
oh wel looks like i have to wait

---

### Post by dmm1983 on 2009-04-15
i have it partly working in mythtv.
thanks all for your help
it was greatly appreciated

---

### Post by dmm1983 on 2009-04-20
i got it to completely work for mythtv by founding a page by accident and cant found it a again now

---

