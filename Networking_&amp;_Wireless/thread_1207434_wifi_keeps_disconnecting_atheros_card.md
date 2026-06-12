---
title: "wifi keeps disconnecting atheros card"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by Slyder0244 on 2009-07-08
my issue is that my wifi keeps dropping out every few minutes and if i'm lucky every 20 or so minutes it happens more when i connect to my router a d-link DI-524 with wpa2 encryption and happens less but still happens when i connect to my neighbor's open wifi spot this laptop use to have an internal broadcom wifi card which i removed as it broke and i'm trying to use a pcmcia card that i have which is an airlink AWLC-4030-II superg

if there is anymore info you need please let me know and thank you in advance for the help


1) laptop model: HP/Compaq nx6110

2) lspci ```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

lsusb ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lspci -nn | grep 'Wireless Brand' 03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

3) ifconfig ```
eth0      Link encap:Ethernet  HWaddr 00:14:c2:d5:b8:6c                                                                       
          inet6 addr: fe80::214:c2ff:fed5:b86c/64 Scope:Link                                                                  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                                  
          RX packets:14547 errors:4294967232 dropped:0 overruns:0 frame:4294967256                                            
          TX packets:9528 errors:4294967256 dropped:0 overruns:0 carrier:4294967288                                           
          collisions:4294967288 txqueuelen:1000                                                                               
          RX bytes:18733848 (18.7 MB)  TX bytes:992847 (992.8 KB)                                                             
          Interrupt:16                                                                                                        

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                             
          RX bytes:20707 (20.7 KB)  TX bytes:20707 (20.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:3c:a4:cf
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe3c:a4cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12065762 (12.0 MB)  TX bytes:1214372 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-3C-A4-CF-34-63-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig ```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Generic Network"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:13:46:85:AD:38
          Bit Rate=24 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=82/100  Signal level:-36 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

4) lsmod ```
Module                  Size  Used by
aes_i586               15744  1      
aes_generic            35880  1 aes_i586
arc4                    9856  2         
ecb                    10752  2         
ath5k                 107008  0         
mac80211              217464  1 ath5k   
led_class              12036  1 ath5k   
cfg80211               38288  2 ath5k,mac80211
i915                   65668  2               
drm                    96296  3 i915          
binfmt_misc            16776  1               
ppdev                  15620  0               
bridge                 56340  0               
stp                    10500  1 bridge        
bnep                   20224  2               
input_polldev          11912  0               
lp                     17156  0               
parport                42220  2 ppdev,lp      
joydev                 18368  0               
pcmcia                 44748  0               
snd_intel8x0           37532  3               
snd_ac97_codec        112292  1 snd_intel8x0  
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0               
snd_mixer_oss          22656  1 snd_pcm_oss   
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0                                        
snd_seq_oss            37760  0                                        
snd_seq_midi           14336  0                                        
snd_rawmidi            29696  1 snd_seq_midi                           
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi               
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq                                          
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           32396  2                                                           
rsrc_nonstatic         19328  1 yenta_socket                                              
psmouse                61972  0                                                           
iTCO_wdt               19108  0                                                           
iTCO_vendor_support    11652  1 iTCO_wdt                                                  
pcspkr                 10496  0                                                           
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                         
soundcore              15200  1 snd
serio_raw              13316  0
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25360  0
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
output                 11008  1 video
intel_agp              34108  1
agpgart                42696  3 drm,intel_agp
b44                    35984  0
ohci1394               38576  0
ssb                    41220  1 b44
mii                    13312  1 b44
ieee1394               94660  1 ohci1394
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

5) dmesg ```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00                                                                           
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                                                         
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)                                                       
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7d0000 (usable)                                                         
[    0.000000]  BIOS-e820: 000000002f7d0000 - 000000002f7efc00 (reserved)                                                       
[    0.000000]  BIOS-e820: 000000002f7efc00 - 000000002f7fb000 (ACPI NVS)                                                       
[    0.000000]  BIOS-e820: 000000002f7fb000 - 000000002f800000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)                                                       
[    0.000000] DMI 2.3 present.                                                                                                 
[    0.000000] last_pfn = 0x2f7d0 max_arch_pfn = 0x100000                                                                       
[    0.000000] Scanning 2 areas for low memory corruption                                                                       
[    0.000000] modified physical RAM map:                                                                                       
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                                                          
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                                                        
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)                                                          
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)                                                        
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)                                                          
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                                        
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                                                        
[    0.000000]  modified: 0000000000100000 - 000000002f7d0000 (usable)                                                          
[    0.000000]  modified: 000000002f7d0000 - 000000002f7efc00 (reserved)                                                        
[    0.000000]  modified: 000000002f7efc00 - 000000002f7fb000 (ACPI NVS)                                                        
[    0.000000]  modified: 000000002f7fb000 - 000000002f800000 (reserved)                                                        
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)                                                        
[    0.000000]  modified: 00000000fec00000 - 00000000fec02000 (reserved)                                                        
[    0.000000]  modified: 00000000fed20000 - 00000000fed9b000 (reserved)                                                        
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)                                                        
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)                                                        
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)                                                        
[    0.000000] kernel direct mapping tables up to 2f7d0000 @ 10000-16000                                                        
[    0.000000] RAMDISK: 2f08a000 - 2f7bf752                                                                                     
[    0.000000] ACPI: RSDP 000FE270, 0014 (r0 HP    )                                                                            
[    0.000000] ACPI: RSDT 2F7EFC84, 0030 (r1 HP     099C     21110520 HP          1)                                            
[    0.000000] ACPI: FACP 2F7EFC00, 0084 (r2 HP     099C            2 HP          1)                                            
[    0.000000] ACPI: DSDT 2F7EFD4C, 7D58 (r1 HP       DAU00     10000 MSFT  100000E)                                            
[    0.000000] ACPI: FACS 2F7FAE80, 0040                                                                                        
[    0.000000] ACPI: APIC 2F7EFCB4, 005A (r1 HP     099C            1 HP          1)                                            
[    0.000000] ACPI: MCFG 2F7EFD10, 003C (r1 HP     099C            1 HP          1)                                            
[    0.000000] ACPI: Local APIC address 0xfec01000                                                                              
[    0.000000] 0MB HIGHMEM available.                                                                                           
[    0.000000] 759MB LOWMEM available.                                                                                          
[    0.000000]   mapped low ram: 0 - 2f7d0000                                                                                   
[    0.000000]   low ram: 00000000 - 2f7d0000                                                                                   
[    0.000000]   bootmap 00012000 - 00017efc                                                                                    
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002f7d0000]                                                     
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                    
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]                                    
[    0.000000]   #4 [002f08a000 - 002f7bf752]          RAMDISK ==> [002f08a000 - 002f7bf752]                                    
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]                                    
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                    
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                    
[    0.000000]   #8 [0000012000 - 0000018000]          BOOTMAP ==> [0000012000 - 0000018000]                                    
[    0.000000] Zone PFN ranges:                                                                                                 
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                              
[    0.000000]   Normal   0x00001000 -> 0x0002f7d0                                                                              
[    0.000000]   HighMem  0x0002f7d0 -> 0x0002f7d0                                                                              
[    0.000000] Movable zone start PFN for each node                                                                             
[    0.000000] early_node_map[4] active PFN ranges                                                                              
[    0.000000]     0: 0x00000000 -> 0x00000002                                                                                  
[    0.000000]     0: 0x00000006 -> 0x00000007                                                                                  
[    0.000000]     0: 0x00000010 -> 0x00000092                                                                                  
[    0.000000]     0: 0x00000100 -> 0x0002f7d0                                                                                  
[    0.000000] On node 0 totalpages: 194389                                                                                     
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000                                               
[    0.000000]   DMA zone: 32 pages used for memmap                                                                             
[    0.000000]   DMA zone: 0 pages reserved                                                                                     
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0                                                                             
[    0.000000]   Normal zone: 1488 pages used for memmap                                                                        
[    0.000000]   Normal zone: 188928 pages, LIFO batch:31                                                                       
[    0.000000]   HighMem zone: 0 pages used for memmap                                                                          
[    0.000000]   Movable zone: 0 pages used for memmap                                                                          
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                                                                   
[    0.000000] ACPI: Local APIC address 0xfec01000                                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                               
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
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs                                                                             
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                                                
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000                                                
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000                                                
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000                                                
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000                                                
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:b0800000)                                           
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                                   
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1                                                                        
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192869                                      
[    0.000000] Kernel command line: root=UUID=f49baed3-71a2-4b0b-9447-4ee52ca90d42 ro quiet splash                              
[    0.000000] Enabling fast FPU save and restore... done.                                                                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                            
[    0.000000] Initializing CPU#0                                                                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                            
[    0.000000] Fast TSC calibration using PIT                                                                                   
[    0.000000] Detected 1396.551 MHz processor.                                                                                 
[    0.004000] Console: colour VGA+ 80x25                                                                                       
[    0.004000] console [tty0] enabled                                                                                           
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                                 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                                   
[    0.004000] allocated 3890240 bytes of page_cgroup                                                                           
[    0.004000] please try cgroup_disable=memory option if you don't want                                                        
[    0.004000] Scanning for low memory corruption every 60 seconds                                                              
[    0.004000] Memory: 751616k/778048k available (4110k kernel code, 25812k reserved, 2196k data, 532k init, 0k highmem)        
[    0.004000] virtual kernel memory layout:                                                                                    
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                                
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                                
[    0.004000]     vmalloc : 0xeffd0000 - 0xff3fe000   ( 244 MB)                                                                
[    0.004000]     lowmem  : 0xc0000000 - 0xef7d0000   ( 759 MB)                                                                
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)                                                                
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)                                                                
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)                                                                
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                      
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1                                          
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2793.10 BogoMIPS (lpj=5586204)        
[    0.004037] Security Framework initialized                                                                                   
[    0.004047] SELinux:  Disabled at boot.                                                                                      
[    0.004074] AppArmor: AppArmor initialized                                                                                   
[    0.004083] Mount-cache hash table entries: 512                                                                              
[    0.004247] Initializing cgroup subsys ns                                                                                    
[    0.004253] Initializing cgroup subsys cpuacct                                                                               
[    0.004256] Initializing cgroup subsys memory                                                                                
[    0.004263] Initializing cgroup subsys freezer                                                                               
[    0.004282] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                            
[    0.004285] CPU: L2 cache: 1024K                                                                                             
[    0.004299] Checking 'hlt' instruction... OK.                                                                                
[    0.020915] SMP alternatives: switching to UP code                                                                           
[    0.160631] Freeing SMP alternatives: 18k freed                                                                              
[    0.160636] ACPI: Core revision 20080926                                                                                     
[    0.165429] ACPI: Checking initramfs for custom DSDT                                                                         
[    0.596609] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                             
[    0.638017] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08                                                
[    0.640002] Brought up 1 CPUs                                                                                                
[    0.640002] Total of 1 processors activated (2793.10 BogoMIPS).                                                              
[    0.640002] CPU0 attaching NULL sched-domain.                                                                                
[    0.640002] net_namespace: 776 bytes                                                                                         
[    0.640002] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.                                       
[    0.640002] Booting paravirtualized kernel on bare hardware                                                                  
[    0.640002] Time:  4:51:08  Date: 07/08/09                                                                                   
[    0.640002] regulator: core version 0.5                                                                                      
[    0.640002] NET: Registered protocol family 16                                                                               
[    0.640002] EISA bus registered                                                                                              
[    0.640002] ACPI: bus type pci registered                                                                                    
[    0.640002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                 
[    0.640002] PCI: MCFG area at e0000000 reserved in E820                                                                      
[    0.640002] PCI: Using MMCONFIG for extended config space                                                                    
[    0.640002] PCI: Using configuration type 1 for base access                                                                  
[    0.640002] ACPI: EC: Look up EC in DSDT                                                                                     
[    0.666923] ACPI: EC: non-query interrupt received, switching to interrupt mode                                              
[    0.680216] ACPI: Interpreter enabled                                                                                        
[    0.680224] ACPI: (supports S0 S3 S4 S5)                                                                                     
[    0.680246] ACPI: Using IOAPIC for interrupt routing                                                                         
[    0.693123] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62                                                    
[    0.693126] ACPI: EC: driver started in interrupt mode                                                                       
[    0.693391] ACPI: No dock devices found.                                                                                     
[    0.693406] ACPI: PCI Root Bridge [C002] (0000:00)                                                                           
[    0.693505] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0400000-0xd047ffff]                                                     
[    0.693512] pci 0000:00:02.0: reg 14 io port: [0x7000-0x7007]                                                                
[    0.693518] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]                                                     
[    0.693524] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0480000-0xd04bffff]                                                     
[    0.693558] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0500000-0xd057ffff]                                                     
[    0.693675] pci 0000:00:1d.0: reg 20 io port: [0x2000-0x201f]                                                                
[    0.693739] pci 0000:00:1d.1: reg 20 io port: [0x2020-0x203f]                                                                
[    0.693806] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]                                                                
[    0.693870] pci 0000:00:1d.3: reg 20 io port: [0x2060-0x207f]                                                                
[    0.693938] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0580000-0xd05803ff]                                                     
[    0.693987] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                            
[    0.693994] pci 0000:00:1d.7: PME# disabled                                                                                  
[    0.694095] pci 0000:00:1e.2: reg 10 io port: [0x2100-0x21ff]                                                                
[    0.694104] pci 0000:00:1e.2: reg 14 io port: [0x2200-0x223f]                                                                
[    0.694113] pci 0000:00:1e.2: reg 18 32bit mmio: [0xd0581000-0xd05811ff]                                                     
[    0.694123] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xd0582000-0xd05820ff]                                                     
[    0.694153] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold                                                            
[    0.694159] pci 0000:00:1e.2: PME# disabled                                                                                  
[    0.694200] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]                                                                
[    0.694209] pci 0000:00:1e.3: reg 14 io port: [0x2500-0x257f]                                                                
[    0.694251] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold                                                            
[    0.694256] pci 0000:00:1e.3: PME# disabled                                                                                  
[    0.694358] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000                                                               
[    0.694369] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO                                          
[    0.694374] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO                                                   
[    0.694401] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]                                                                    
[    0.694410] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]                                                                    
[    0.694418] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]                                                                    
[    0.694427] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]                                                                    
[    0.694436] pci 0000:00:1f.1: reg 20 io port: [0x2580-0x258f]                                                                
[    0.694527] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0000000-0xd0000fff]                                                     
[    0.694542] pci 0000:02:06.0: supports D1 D2                                                                                 
[    0.694545] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold                                                      
[    0.694551] pci 0000:02:06.0: PME# disabled                                                                                  
[    0.694604] pci 0000:02:06.2: reg 10 32bit mmio: [0xd0001000-0xd00017ff]                                                     
[    0.694615] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0004000-0xd0007fff]                                                     
[    0.694670] pci 0000:02:06.2: supports D1 D2                                                                                 
[    0.694672] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot                                                             
[    0.694679] pci 0000:02:06.2: PME# disabled                                                                                  
[    0.694745] pci 0000:02:0e.0: reg 10 32bit mmio: [0xd0008000-0xd0009fff]                                                     
[    0.694794] pci 0000:02:0e.0: supports D1 D2                                                                                 
[    0.694797] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot D3cold                                                      
[    0.694803] pci 0000:02:0e.0: PME# disabled                                                                                  
[    0.694843] pci 0000:00:1e.0: transparent bridge                                                                             
[    0.694852] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd03fffff]                                                     
[    0.694895] bus 00 -> node 0                                                                                                 
[    0.694904] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]                                                              
[    0.695397] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]                                                         
[    0.733996] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)                                                                    
[    0.734306] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)                                                                    
[    0.734612] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)                                                                    
[    0.734921] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)                                                                    
[    0.735220] ACPI: PCI Interrupt Link [C0EE] (IRQs 10 11) *0, disabled.                                                       
[    0.735515] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 11) *0, disabled.                                                       
[    0.735826] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)                                                                    
[    0.736128] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.                                                       
[    0.736343] ACPI: Power Resource [C1C5] (on)                                                                                 
[    0.736485] ACPI: Power Resource [C244] (off)                                                                                
[    0.736619] ACPI: Power Resource [C245] (off)                                                                                
[    0.736752] ACPI: Power Resource [C246] (off)                                                                                
[    0.736883] ACPI: Power Resource [C247] (off)                                                                                
[    0.736999] ACPI: WMI: Mapper loaded                                                                                         
[    0.737246] SCSI subsystem initialized                                                                                       
[    0.737299] libata version 3.00 loaded.                                                                                      
[    0.737360] usbcore: registered new interface driver usbfs                                                                   
[    0.737383] usbcore: registered new interface driver hub                                                                     
[    0.737418] usbcore: registered new device driver usb                                                                        
[    0.737575] PCI: Using ACPI for IRQ routing                                                                                  
[    0.737695] Bluetooth: Core ver 2.13                                                                                         
[    0.737695] NET: Registered protocol family 31                                                                               
[    0.737695] Bluetooth: HCI device and connection manager initialized                                                         
[    0.737695] Bluetooth: HCI socket layer initialized                                                                          
[    0.737695] NET: Registered protocol family 8                                                                                
[    0.737695] NET: Registered protocol family 20                                                                               
[    0.737695] NetLabel: Initializing                                                                                           
[    0.737695] NetLabel:  domain hash size = 128                                                                                
[    0.737695] NetLabel:  protocols = UNLABELED CIPSOv4                                                                         
[    0.737695] NetLabel:  unlabeled traffic allowed by default                                                                  
[    0.737695] hpet clockevent registered                                                                                       
[    0.737695] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                                                 
[    0.737695] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                                          
[    0.737695] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                                                               
[    0.740101] AppArmor: AppArmor Filesystem Enabled                                                                            
[    0.740110] pnp: PnP ACPI init                                                                                               
[    0.740110] ACPI: bus type pnp registered                                                                                    
[    0.752037] pnp: PnP ACPI: found 11 devices                                                                                  
[    0.752040] ACPI: ACPI bus type pnp unregistered                                                                             
[    0.752045] PnPBIOS: Disabled by ACPI PNP                                                                                    
[    0.752059] system 00:00: iomem range 0x0-0x9ffff could not be reserved                                                      
[    0.752063] system 00:00: iomem range 0xe0000-0xfffff could not be reserved                                                  
[    0.752067] system 00:00: iomem range 0x100000-0x2f7fffff could not be reserved                                              
[    0.752078] system 00:08: ioport range 0x500-0x57f has been reserved                                                         
[    0.752083] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved                                                
[    0.752087] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved                                                
[    0.752093] system 00:09: ioport range 0x4d0-0x4d1 has been reserved                                                         
[    0.752097] system 00:09: ioport range 0x1000-0x107f has been reserved                                                       
[    0.752101] system 00:09: ioport range 0x1100-0x113f has been reserved                                                       
[    0.752104] system 00:09: ioport range 0x1200-0x121f has been reserved                                                       
[    0.752108] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved                                                
[    0.752112] system 00:09: iomem range 0xfec00000-0xfec000ff has been reserved                                                
[    0.752116] system 00:09: iomem range 0xfed20000-0xff41ffff could not be reserved                                            
[    0.752120] system 00:09: iomem range 0xfed90000-0xfed9afff has been reserved                                                
[    0.752127] system 00:0a: iomem range 0xfeda0000-0xfedbffff has been reserved                                                
[    0.752130] system 00:0a: iomem range 0xfec01000-0xfec01fff has been reserved                                                
[    0.786892] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03                                                          
[    0.786896] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff                                                                 
[    0.786903] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff                                                                 
[    0.786910] pci 0000:02:06.0:   PREFETCH window: 0x30000000-0x33ffffff                                                       
[    0.786917] pci 0000:02:06.0:   MEM window: 0x34000000-0x37ffffff                                                            
[    0.786923] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02                                                              
[    0.786927] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff                                                                     
[    0.786935] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd03fffff                                                            
[    0.786941] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff                                           
[    0.786961] pci 0000:00:1e.0: setting latency timer to 64                                                                    
[    0.786978] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                     
[    0.786986] bus: 00 index 0 io port: [0x00-0xffff]                                                                           
[    0.786989] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                                      
[    0.786992] bus: 02 index 0 io port: [0x3000-0x3fff]                                                                         
[    0.786996] bus: 02 index 1 mmio: [0xd0000000-0xd03fffff]                                                                    
[    0.786999] bus: 02 index 2 mmio: [0x30000000-0x33ffffff]                                                                    
[    0.787002] bus: 02 index 3 io port: [0x00-0xffff]                                                                           
[    0.787004] bus: 02 index 4 mmio: [0x000000-0xffffffff]                                                                      
[    0.787007] bus: 03 index 0 io port: [0x3000-0x30ff]                                                                         
[    0.787010] bus: 03 index 1 io port: [0x3400-0x34ff]                                                                         
[    0.787013] bus: 03 index 2 mmio: [0x30000000-0x33ffffff]                                                                    
[    0.787016] bus: 03 index 3 mmio: [0x34000000-0x37ffffff]                                                                    
[    0.787029] NET: Registered protocol family 2                                                                                
[    0.787176] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                                
[    0.787525] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                             
[    0.788775] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                                      
[    0.789637] TCP: Hash tables configured (established 131072 bind 65536)                                                      
[    0.789642] TCP reno registered                                                                                              
[    0.789855] NET: Registered protocol family 1                                                                                
[    0.790058] checking if image is initramfs... it is                                                                          
[    1.240013] Switched to high resolution mode on CPU 0                                                                        
[    1.654589] Freeing initrd memory: 7381k freed                                                                               
[    1.654682] cpufreq: No nForce2 chipset.                                                                                     
[    1.654927] audit: initializing netlink socket (disabled)                                                                    
[    1.654957] type=2000 audit(1247028668.652:1): initialized                                                                   
[    1.665320] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                                         
[    1.667044] VFS: Disk quotas dquot_6.5.1                                                                                     
[    1.667119] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                                       
[    1.667933] fuse init (API version 7.10)                                                                                     
[    1.668062] msgmni has been set to 1482                                                                                      
[    1.668310] alg: No test for stdrng (krng)                                                                                   
[    1.668326] io scheduler noop registered                                                                                     
[    1.668329] io scheduler anticipatory registered                                                                             
[    1.668332] io scheduler deadline registered                                                                                 
[    1.668352] io scheduler cfq registered (default)                                                                            
[    1.668372] pci 0000:00:02.0: Boot video device                                                                              
[    1.677265] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                  
[    1.677277] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                      
[    1.679037] ACPI: AC Adapter [C172] (on-line)                                                                                
[    1.721568] ACPI: Battery Slot [C174] (battery present)                                                                      
[    1.721850] ACPI: Battery Slot [C173] (battery absent)                                                                       
[    1.721943] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                        
[    1.721947] ACPI: Power Button (FF) [PWRF]                                                                                   
[    1.722019] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1                               
[    1.722022] ACPI: Sleep Button (CM) [C1E8]                                                                                   
[    1.722084] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2                                      
[    1.722179] ACPI: Lid Switch [C1E9]                                                                                          
[    1.722495] fan PNP0C0B:00: registered as cooling_device0                                                                    
[    1.722502] ACPI: Fan [C248] (off)                                                                                           
[    1.722776] fan PNP0C0B:01: registered as cooling_device1                                                                    
[    1.722783] ACPI: Fan [C249] (off)                                                                                           
[    1.723052] fan PNP0C0B:02: registered as cooling_device2                                                                    
[    1.723059] ACPI: Fan [C24A] (off)                                                                                           
[    1.723327] fan PNP0C0B:03: registered as cooling_device3                                                                    
[    1.723334] ACPI: Fan [C24B] (off)                                                                                           
[    1.723960] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                                                                  
[    1.723984] processor ACPI_CPU:00: registered as cooling_device4                                                             
[    1.723988] ACPI: Processor [C000] (supports 8 throttling states)                                                            
[    1.742299] thermal LNXTHERM:01: registered as thermal_zone0                                                                 
[    1.754381] ACPI: Thermal Zone [TZ1] (57 C)                                                                                  
[    1.765116] thermal LNXTHERM:02: registered as thermal_zone1                                                                 
[    1.773196] ACPI: Thermal Zone [TZ2] (46 C)                                                                                  
[    1.778337] thermal LNXTHERM:03: registered as thermal_zone2                                                                 
[    1.786684] ACPI: Thermal Zone [TZ3] (28 C)                                                                                  
[    1.788474] thermal LNXTHERM:04: registered as thermal_zone3                                                                 
[    1.792375] ACPI: Thermal Zone [TZ4] (61 C)                                                                                  
[    1.792435] isapnp: Scanning for PnP cards...                                                                                
[    2.146362] isapnp: No Plug & Play device found                                                                              
[    2.147776] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                            
[    2.148287] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22                                                  
[    2.148296] serial 0000:00:1e.3: PCI INT B disabled                                                                          
[    2.149145] brd: module loaded                                                                                               
[    2.149537] loop: module loaded                                                                                              
[    2.149636] Fixed MDIO Bus: probed                                                                                           
[    2.149644] PPP generic driver version 2.4.2                                                                                 
[    2.149723] input: Macintosh mouse button emulation as /devices/virtual/input/input3                                         
[    2.149760] Driver 'sd' needs updating - please use bus_type methods                                                         
[    2.149772] Driver 'sr' needs updating - please use bus_type methods                                                         
[    2.149871] ata_piix 0000:00:1f.1: version 2.12                                                                              
[    2.149885] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                
[    2.149938] ata_piix 0000:00:1f.1: setting latency timer to 64                                                               
[    2.150064] scsi0 : ata_piix                                                                                                 
[    2.150185] scsi1 : ata_piix                                                                                                 
[    2.151028] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14                                                  
[    2.151032] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15                                                  
[    2.432661] ata1.00: ATA-7: Hitachi HTS541612J9AT00, SBDOA70H, max UDMA/100                                                  
[    2.432665] ata1.00: 234441648 sectors, multi 16: LBA48                                                                      
[    2.432721] ata1.01: ATAPI: SONY CD-RW/DVD-ROM CRX835E, KPK4, max MWDMA2                                                     
[    2.448611] ata1.00: configured for UDMA/100                                                                                 
[    2.464407] ata1.01: configured for MWDMA2                                                                                   
[    2.464742] ata2: port disabled. ignoring.                                                                                   
[    2.464893] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5                                     
[    2.465025] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)                                          
[    2.465049] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.465052] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.465085] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.465163] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)                                          
[    2.465181] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.465184] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.465214] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.465219]  sda: sda1 sda2 sda3                                                                                             
[    2.903763] sd 0:0:0:0: [sda] Attached SCSI disk                                                                             
[    2.903825] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                                     
[    2.904473] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX835E   KPK4 PQ: 0 ANSI: 5                                     
[    2.907307] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray                                                     
[    2.907311] Uniform CD-ROM driver Revision: 3.20                                                                             
[    2.907418] sr 0:0:1:0: Attached scsi CD-ROM sr0                                                                             
[    2.907473] sr 0:0:1:0: Attached scsi generic sg1 type 5                                                                     
[    2.908240] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                       
[    2.908272] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                                
[    2.908305] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                               
[    2.908310] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                                      
[    2.908397] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                             
[    2.912317] ehci_hcd 0000:00:1d.7: debug port 1                                                                              
[    2.912325] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported                                                    
[    2.912348] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000                                                                 
[    2.928009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                                
[    2.928097] usb usb1: configuration #1 chosen from 1 choice                                                                  
[    2.928133] hub 1-0:1.0: USB hub found                                                                                       
[    2.928144] hub 1-0:1.0: 8 ports detected                                                                                    
[    2.928293] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                           
[    2.928314] uhci_hcd: USB Universal Host Controller Interface driver                                                         
[    2.928349] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                                
[    2.928360] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                               
[    2.928364] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                                      
[    2.928420] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                             
[    2.928447] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000                                                                
[    2.928547] usb usb2: configuration #1 chosen from 1 choice                                                                  
[    2.928582] hub 2-0:1.0: USB hub found                                                                                       
[    2.928590] hub 2-0:1.0: 2 ports detected                                                                                    
[    2.928695] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                
[    2.928703] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                               
[    2.928707] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                                      
[    2.928756] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                             
[    2.928793] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020                                                                
[    2.928889] usb usb3: configuration #1 chosen from 1 choice                                                                  
[    2.928920] hub 3-0:1.0: USB hub found                                                                                       
[    2.928928] hub 3-0:1.0: 2 ports detected                                                                                    
[    2.929029] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                
[    2.929037] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                               
[    2.929041] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                                      
[    2.929095] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                             
[    2.929131] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040                                                                
[    2.929229] usb usb4: configuration #1 chosen from 1 choice                                                                  
[    2.929260] hub 4-0:1.0: USB hub found                                                                                       
[    2.929268] hub 4-0:1.0: 2 ports detected                                                                                    
[    2.929373] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19                                                
[    2.929381] uhci_hcd 0000:00:1d.3: setting latency timer to 64                                                               
[    2.929385] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                                                      
[    2.929444] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5                                             
[    2.929479] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060                                                                
[    2.929574] usb usb5: configuration #1 chosen from 1 choice                                                                  
[    2.929606] hub 5-0:1.0: USB hub found                                                                                       
[    2.929616] hub 5-0:1.0: 2 ports detected                                                                                    
[    2.929792] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12                                           
[    2.931588] i8042.c: Detected active multiplexing controller, rev 1.1.                                                       
[    2.932295] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                         
[    2.932302] serio: i8042 AUX0 port at 0x60,0x64 irq 12                                                                       
[    2.932305] serio: i8042 AUX1 port at 0x60,0x64 irq 12                                                                       
[    2.932308] serio: i8042 AUX2 port at 0x60,0x64 irq 12                                                                       
[    2.932312] serio: i8042 AUX3 port at 0x60,0x64 irq 12                                                                       
[    2.932522] mice: PS/2 mouse device common for all mice                                                                      
[    2.932733] rtc_cmos 00:05: RTC can wake from S4                                                                             
[    2.932783] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                                                            
[    2.932819] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs                                                    
[    2.932904] device-mapper: uevent: version 1.0.3                                                                             
[    2.933044] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com                                 
[    2.933105] device-mapper: multipath: version 1.0.5 loaded                                                                   
[    2.933109] device-mapper: multipath round-robin: version 1.0.0 loaded                                                       
[    2.933212] EISA: Probing bus 0 at eisa.0                                                                                    
[    2.933223] Cannot allocate resource for EISA slot 1                                                                         
[    2.933226] Cannot allocate resource for EISA slot 2                                                                         
[    2.933229] Cannot allocate resource for EISA slot 3                                                                         
[    2.933245] Cannot allocate resource for EISA slot 7                                                                         
[    2.933252] EISA: Detected 0 cards.                                                                                          
[    2.933330] cpuidle: using governor ladder                                                                                   
[    2.933407] cpuidle: using governor menu                                                                                     
[    2.934060] TCP cubic registered                                                                                             
[    2.934192] NET: Registered protocol family 10                                                                               
[    2.934706] lo: Disabled Privacy Extensions                                                                                  
[    2.935102] NET: Registered protocol family 17                                                                               
[    2.935127] Bluetooth: L2CAP ver 2.11                                                                                        
[    2.935129] Bluetooth: L2CAP socket layer initialized                                                                        
[    2.935132] Bluetooth: SCO (Voice Link) ver 0.6                                                                              
[    2.935134] Bluetooth: SCO socket layer initialized                                                                          
[    2.935172] Bluetooth: RFCOMM socket layer initialized                                                                       
[    2.935181] Bluetooth: RFCOMM TTY layer initialized                                                                          
[    2.935184] Bluetooth: RFCOMM ver 1.10                                                                                       
[    2.935234] Using IPI No-Shortcut mode                                                                                       
[    2.935333] registered taskstats version 1                                                                                   
[    2.935462]   Magic number: 1:367:868                                                                                        
[    2.935578] rtc_cmos 00:05: setting system clock to 2009-07-08 04:51:10 UTC (1247028670)                                     
[    2.935582] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                             
[    2.935585] EDD information not available.                                                                                   
[    2.935959] Freeing unused kernel memory: 532k freed                                                                         
[    2.936145] Write protecting the kernel text: 4112k                                                                          
[    2.936199] Write protecting the kernel read-only data: 1524k                                                                
[    2.973963] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4                               
[    3.615842] ohci1394 0000:02:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22                                                
[    3.665674] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0001000-d00017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]                                                                                                                             
[    3.677247] b44 0000:02:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                     
[    3.736104] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0                                                   
[    3.736137] b44.c:v2.0                                                                                                       
[    3.756927] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:c2:d5:b8:6c                                                  
[    3.990459] Marking TSC unstable due to TSC halts in idle                                                                    
[    4.110702] PM: Starting manual resume from disk                                                                             
[    4.110707] PM: Resume from partition 8:2                                                                                    
[    4.110709] PM: Checking hibernation image.                                                                                  
[    4.110907] PM: Resume from disk failed.                                                                                     
[    4.113646] EXT3-fs: INFO: recovery required on readonly filesystem.                                                         
[    4.113651] EXT3-fs: write access will be enabled during recovery.                                                           
[    4.948915] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[718b5000291142a6]                                                  
[    9.966006] kjournald starting.  Commit interval 5 seconds                                                                   
[    9.966031] EXT3-fs: sda3: orphan cleanup on readonly fs                                                                     
[    9.966037] ext3_orphan_cleanup: deleting unreferenced inode 109230                                                          
[   10.027428] ext3_orphan_cleanup: deleting unreferenced inode 351519                                                          
[   10.046653] ext3_orphan_cleanup: deleting unreferenced inode 351517                                                          
[   10.068532] ext3_orphan_cleanup: deleting unreferenced inode 107762                                                          
[   10.078200] ext3_orphan_cleanup: deleting unreferenced inode 203648                                                          
[   10.096627] ext3_orphan_cleanup: deleting unreferenced inode 105103                                                          
[   10.096635] EXT3-fs: sda3: 6 orphan inodes deleted                                                                           
[   10.096637] EXT3-fs: recovery complete.                                                                                      
[   10.139472] EXT3-fs: mounted filesystem with ordered data mode.                                                              
[   17.723205] udev: starting version 141                                                                                       
[   17.895921] Linux agpgart interface v0.103                                                                                   
[   17.925301] agpgart-intel 0000:00:00.0: Intel 915GM Chipset                                                                  
[   17.925704] agpgart-intel 0000:00:00.0: detected 7932K stolen memory                                                         
[   17.929330] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000                                                    
[   17.985165] intel_rng: FWH not detected                                                                                      
[   18.233396] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5                             
[   18.256269] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)                                                   
[   18.416685] input: PC Speaker as /devices/platform/pcspkr/input/input6                                                       
[   18.469956] iTCO_vendor_support: vendor-support=0                                                                            
[   18.688055] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                                                  
[   18.688240] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)                                                  
[   18.688350] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                             
[   18.742973] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:099c]                                                     
[   18.742999] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions                                              
[   18.743006] yenta_cardbus 0000:02:06.0: Using INTVAL to route CSC interrupts to PCI                                          
[   18.743010] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI                                                    
[   18.743017] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01aa1b22, devctl 0x64                                                    
[   18.834634] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                          
[   18.945378] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21                                               
[   18.945498] Intel ICH 0000:00:1e.2: setting latency timer to 64                                                              
[   18.973350] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0cf8, PCI irq 18                                                      
[   18.973356] yenta_cardbus 0000:02:06.0: Socket status: 30000006                                                              
[   18.973361] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06                                    
[   18.973372] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff                                
[   18.973377] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.                                            
[   18.973662] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff                     
[   18.973667] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff                     
[   19.236060] Clocksource tsc unstable (delta = -246098756 ns)                                                                 
[   19.319059] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.                                              
[   19.320805] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.                                              
[   19.321553] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.                                              
[   19.322162] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.                                              
[   19.322962] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.                                              
[   19.690082] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000                                     
[   19.690090] serio: Synaptics pass-through port at isa0060/serio4/input0                                                      
[   19.732402] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7                                 
[   19.868033] intel8x0_measure_ac97_clock: measured 55346 usecs                                                                
[   19.868037] intel8x0: clocking to 48000                                                                                      
[   20.062017] lp: driver loaded but no devices found                                                                           
[   20.140411] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k                                          
[   20.688125] EXT3 FS on sda3, internal journal                                                                                
[   21.828875] type=1505 audit(1247043089.392:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1959                                                                                                                
[   21.900341] type=1505 audit(1247043089.464:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1963
[   21.900570] type=1505 audit(1247043089.464:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1963      
[   21.900654] type=1505 audit(1247043089.464:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1963                                                                                                        
[   21.900721] type=1505 audit(1247043089.464:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1963                                                                                                             
[   22.110911] type=1505 audit(1247043089.672:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1968                                                                                                                       
[   22.111251] type=1505 audit(1247043089.672:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1968      
[   22.151673] type=1505 audit(1247043089.712:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1972    
[   24.491035] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                                     
[   24.491040] Bluetooth: BNEP filters: protocol multicast                                                                      
[   24.504569] Bridge firewalling registered                                                                                    
[   25.999776] ppdev: user-space parallel port driver                                                                           
[   27.444809] [drm] Initialized drm 1.1.0 20060810                                                                             
[   27.476956] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                     
[   27.476967] pci 0000:00:02.0: setting latency timer to 64                                                                    
[   27.477187] [drm] Initialized i915 1.6.0 20080730 on minor 0                                                                 
[   27.589608] [drm:i915_setparam] *ERROR* unknown parameter 4                                                                  
[   27.589643] [drm:i915_getparam] *ERROR* Unknown parameter 6                                                                  
[   28.927193] [drm:i915_getparam] *ERROR* Unknown parameter 6                                                                  
[   29.442471] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                     
[   33.816204] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                  
[   33.816209] b44: eth0: Flow control is off for TX and off for RX.                                                            
[   33.816571] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                
[   44.552223] eth0: no IPv6 routers present                                                                                    
[   76.024754] [drm:i915_getparam] *ERROR* Unknown parameter 6                                                                  
[  613.284134] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0                                          
[  613.284194] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]                                                         
[  613.341756] cfg80211: Calling CRDA to update world regulatory domain                                                         
[  613.415801] cfg80211: World regulatory domain updated:                                                                       
[  613.415807]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                               
[  613.415811]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[  613.415815]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[  613.415819]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[  613.415822]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[  613.415826]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[  613.523573] ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)                                                           
[  613.523587] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                               
[  613.523704] ath5k_pci 0000:03:00.0: registered as 'phy0'                                                                     
[  613.612603] phy0: Selected rate control algorithm 'pid'                                                                      
[  613.664145] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)                                                     
[  618.470874] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                    
[  622.249193] wlan0: direct probe to AP 00:15:e9:7f:68:fe try 1                                                                
[  622.448092] wlan0: direct probe to AP 00:15:e9:7f:68:fe try 2                                                                
[  622.648087] wlan0: direct probe to AP 00:15:e9:7f:68:fe try 3                                                                
[  622.649761] wlan0 direct probe responded                                                                                     
[  622.649766] wlan0: authenticate with AP 00:15:e9:7f:68:fe                                                                    
[  622.652559] wlan0: authenticated                                                                                             
[  622.652564] wlan0: associate with AP 00:15:e9:7f:68:fe                                                                       
[  622.655094] wlan0: RX AssocResp from 00:15:e9:7f:68:fe (capab=0x421 status=0 aid=2)                                          
[  622.655097] wlan0: associated                                                                                                
[  622.655772] wlan0: disassociating by local choice (reason=3)                                                                 
[  622.676896] wlan0: deauthenticated                                                                                           
[  630.860483] wlan0: authenticate with AP 00:13:46:85:ad:38                                                                    
[  630.865230] wlan0: authenticated                                                                                             
[  630.865239] wlan0: associate with AP 00:13:46:85:ad:38                                                                       
[  630.869551] wlan0: RX AssocResp from 00:13:46:85:ad:38 (capab=0x431 status=0 aid=1)                                          
[  630.869555] wlan0: associated                                                                                                
[  630.871282] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                               
[  631.000959] padlock: VIA PadLock not detected.                                                                               
[  641.052024] wlan0: no IPv6 routers present                                                                                   
[ 1382.360087] wlan0: No ProbeResp from current AP 00:13:46:85:ad:38 - assume out of range                                      
[ 1382.515982] ath5k phy0: noise floor calibration failed (2412MHz)                                                             
[ 1384.288659] wlan0: authenticate with AP 00:13:46:85:ad:38                                                                    
[ 1384.295239] wlan0: authenticated                                                                                             
[ 1384.295251] wlan0: associate with AP 00:13:46:85:ad:38                                                                       
[ 1384.305066] wlan0: RX ReassocResp from 00:13:46:85:ad:38 (capab=0x431 status=0 aid=1)                                        
[ 1384.305071] wlan0: associated                                                                                                
[ 1985.377639] ath5k phy0: noise floor calibration failed (2417MHz)                                                             
[ 1989.354347] ath5k phy0: noise floor calibration timeout (2417MHz)                                                            
[ 1990.316047] wlan0: No ProbeResp from current AP 00:13:46:85:ad:38 - assume out of range                                      
[ 1992.242410] wlan0: authenticate with AP 00:13:46:85:ad:38                                                                    
[ 1992.244281] wlan0: authenticated                                                                                             
[ 1992.244285] wlan0: associate with AP 00:13:46:85:ad:38                                                                       
[ 1992.247369] wlan0: RX ReassocResp from 00:13:46:85:ad:38 (capab=0x431 status=0 aid=1)                                        
[ 1992.247373] wlan0: associated                                                                                                
[ 2150.312373] wlan0: disassociating by local choice (reason=3)                                                                 
[ 2162.590003] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0                                                   
[ 2162.625985] ath5k_pci 0000:03:00.0: PCI INT A disabled                                                                       
[ 2213.000113] b44: eth0: Link is down.                                                                                         
[ 2221.000200] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                  
[ 2221.000205] b44: eth0: Flow control is off for TX and off for RX.                                                            
[ 2280.000113] b44: eth0: Link is down.                                                                                         
[ 2341.572219] b44: eth0: powering down PHY                                                                                     
[ 2344.033627] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                     
[ 2353.000244] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                  
[ 2353.000249] b44: eth0: Flow control is off for TX and off for RX.                                                            
[ 2353.000618] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                
[ 2361.348092] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0                                          
[ 2361.348153] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]                                                         
[ 2361.350865] ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)
[ 2361.350880] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2361.350983] ath5k_pci 0000:03:00.0: registered as 'phy1'
[ 2361.445901] phy1: Selected rate control algorithm 'pid'
[ 2361.447249] ath5k phy1: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[ 2363.536025] eth0: no IPv6 routers present
[ 2365.477017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2374.635186] wlan0: authenticate with AP 00:13:46:85:ad:38
[ 2374.637166] wlan0: authenticated
[ 2374.637171] wlan0: associate with AP 00:13:46:85:ad:38
[ 2374.640296] wlan0: RX AssocResp from 00:13:46:85:ad:38 (capab=0x431 status=0 aid=1)
[ 2374.640300] wlan0: associated
[ 2374.640982] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2385.168068] wlan0: no IPv6 routers present

```

6) sudo lshw -C network  ```
*-network                                         
       description: AR5001-0000-0000                
       product: Wireless LAN Reference Card         
       vendor: Atheros Communications, Inc.         
       physical id: 0                               
       version: 00                                  
       slot: Socket 0                               
       resources: irq:18                            
  *-network                                         
       description: Ethernet interface              
       product: BCM4401-B0 100Base-TX               
       vendor: Broadcom Corporation                 
       physical id: e                               
       bus info: pci@0000:02:0e.0                   
       logical name: eth0                           
       version: 02                                  
       serial: 00:14:c2:d5:b8:6c                    
       size: 100MB/s                                
       capacity: 100MB/s                            
       width: 32 bits                               
       clock: 33MHz                                 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s                                                                                    
  *-network                                                                                                                     
       description: Wireless interface                                                                                          
       product: Atheros AR5001X+ Wireless Network Adapter                                                                       
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:14:a5:3c:a4:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.2.100 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:2a:fb:a0:48:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

7) iwlist scan ```
lo        Interface doesn't support scanning.                                                                                   

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:85:AD:38
                    ESSID:"Generic Network"   
                    Mode:Master               
                    Channel:2                 
                    Frequency:2.417 GHz (Channel 2)
                    Quality=84/100  Signal level:-34 dBm  Noise level=-88 dBm
                    Encryption key:on                                        
                    IE: Unknown: 000F47656E65726963204E6574776F726B          
                    IE: Unknown: 010882848B0C12961824                        
                    IE: Unknown: 030102                                      
                    IE: Unknown: 0706555349010B1B                            
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000000fa64181
                    Extra: Last beacon: 100ms ago


```

8) Description:    Ubuntu 9.04

9) 2.6.28-13-generic i686

10) sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...Ignoring unknown interface wlan0=wlan0.
                                                                                                                         [ OK ]

---

