---
title: "Network manager and wicd not seeing wireless networks..."
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by killabee44 on 2009-11-28
Ok guys,

I installed Karmic on a Thinkpad T43. I installed WICD because of issues I had in the past with network manager and also because I like the applet better.

The wired network works with WICD. No problem there. It will not see the wireless networks though. 

It gives the error: "No wireless networks found"

So, I then installed network manager. It would not run at all. After much searching the forums I changed:

 /etc/NetworkManager/nm-system-settings.conf with this:

[main]
plugins=keyfile

[ifupdown]
managed=true

Then the wired network worked, but not the wireless, and still no icon in the taskbar, so I did: 

nm-applet &

Result was that the icon showed up in the taskbar and Network manager worked great... until I rebooted. Then no icon again. So I would have to do a "nm-applet &" after every reboot or else the network would not work. 

My question is, does anyone know a way to get Wicd working with wireless (which I prefer), or a way to make network manager stay on after a reboot?

Thanks!


PS. Here is more info (the following was while wicd was installed):

Lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)                                                 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

Lsusb:


```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:10:**:**:**:**
          inet addr:192.168.105.137  Bcast:192.168.105.255  Mask:255.255.255.0
          inet6 addr: ****::***:****:fece:c193/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3080416 (3.0 MB)  TX bytes:231470 (231.4 KB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet6 addr: ****::***:ceff:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:21949 (21.9 KB)
          Interrupt:21 Base address:0xe000 Memory:90301000-90301fff

eth1:avahi Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:169.254.6.49  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xe000 Memory:90301000-90301fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

```

iwconfig:```


lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```

iwconfig wlan0:
```

wlan0     No such device
```

lsmod:```


Module                  Size  Used by
nls_iso8859_1           3740  0      
nls_cp437               5372  0      
vfat                   10716  0      
fat                    51452  1 vfat 
usb_storage            52576  0      
binfmt_misc             8356  1      
vboxnetflt             84840  0      
vboxnetadp             78344  0      
vboxdrv               121160  1 vboxnetflt
dm_crypt               12928  0           
snd_intel8x0           30168  4           
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0               
snd_mixer_oss          16028  1 snd_pcm_oss   
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0                                        
snd_seq_oss            28576  0                                        
snd_seq_midi            6432  0                                        
snd_rawmidi            22208  1 snd_seq_midi                           
iptable_filter          3100  0                                        
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
pcmcia                 36808  0                                        
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                                                                       
snd_timer              22276  2 snd_pcm,snd_seq                                 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq                                                                      
ip_tables              11692  1 iptable_filter                                  
yenta_socket           24200  1                                                 
joydev                 10272  0                                                 
snd                    59204  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device         
rsrc_nonstatic         11644  1 yenta_socket                                    
x_tables               16544  1 ip_tables                                       
ipw2200               140292  0                                                 
soundcore               7264  1 snd                                             
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic              
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
thinkpad_acpi          67108  0
psmouse                56500  0
led_class               4096  1 thinkpad_acpi
nsc_ircc               20976  0
irda                  189564  1 nsc_ircc
ppdev                   6688  0
serio_raw               5280  0
crc_ccitt               1852  1 irda
nvram                   7528  1 thinkpad_acpi
parport_pc             31940  1
lp                      8964  0
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0
xor                    15620  1 dm_raid45
fbcon                  36640  72
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  2
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
tg3                   109600  0
floppy                 54916  0
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
ramzswap                8880  1
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap

```

dmesg:

 ```
                                          
[    0.000000] Initializing cgroup subsys cpuset                                
[    0.000000] Initializing cgroup subsys cpu                                   
[    0.000000] Linux version 2.6.31-15-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 (Ubuntu 2.6.31-15.50-generic)                                                          
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)         
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)       
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)       
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)       
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)         
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f6f5000 (ACPI data)      
[    0.000000]  BIOS-e820: 000000003f6f5000 - 000000003f700000 (ACPI NVS)       
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)       
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)       
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)       
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)       
[    0.000000] DMI present.                                                     
[    0.000000] last_pfn = 0x3f6e0 max_arch_pfn = 0x100000                       
[    0.000000] MTRR default type: uncachable                                    
[    0.000000] MTRR fixed ranges enabled:                                       
[    0.000000]   00000-9FFFF write-back                                         
[    0.000000]   A0000-BFFFF uncachable                                         
[    0.000000]   C0000-CFFFF write-protect                                      
[    0.000000]   D0000-DBFFF uncachable                                         
[    0.000000]   DC000-DFFFF write-back                                         
[    0.000000]   E0000-FFFFF write-protect                                      
[    0.000000] MTRR variable ranges enabled:                                    
[    0.000000]   0 base 000000000 mask FC0000000 write-back                     
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable                     
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable                     
[    0.000000]   3 disabled                                                     
[    0.000000]   4 disabled                                                     
[    0.000000]   5 disabled                                                     
[    0.000000]   6 disabled                                                     
[    0.000000]   7 disabled                                                     
[    0.000000] PAT not supported by CPU.                                        
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)                                                                   
[    0.000000] Scanning 1 areas for low memory corruption                       
[    0.000000] modified physical RAM map:                                       
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)          
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)        
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)          
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)        
[    0.000000]  modified: 00000000000d0000 - 00000000000d4000 (reserved)        
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)        
[    0.000000]  modified: 0000000000100000 - 000000003f6e0000 (usable)          
[    0.000000]  modified: 000000003f6e0000 - 000000003f6f5000 (ACPI data)       
[    0.000000]  modified: 000000003f6f5000 - 000000003f700000 (ACPI NVS)        
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)        
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)        
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)        
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)        
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)        
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)        
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)        
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)        
[    0.000000] initial memory mapped : 0 - 00c00000                             
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000           
[    0.000000] Using x86 segment limits to approximate NX protection            
[    0.000000]  0000000000 - 0000400000 page 4k                                 
[    0.000000]  0000400000 - 0037400000 page 2M                                 
[    0.000000]  0037400000 - 00377fe000 page 4k                                 
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000          
[    0.000000] RAMDISK: 2f162000 - 2f967850                                     
[    0.000000] ACPI: RSDP 000f6bb0 00024 (v02 IBM   )                           
[    0.000000] ACPI: XSDT 3f6e73b2 0005C (v01 IBM    TP-70    00001170  LTP 00000000)                                                                           
[    0.000000] ACPI: FACP 3f6e7500 000F4 (v03 IBM    TP-70    00001170 IBM  00000001)                                                                           
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 20090521 tbfadt-527                                                                      
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 20090521 tbfadt-558                                        
[    0.000000] ACPI: DSDT 3f6e76e7 0D748 (v01 IBM    TP-70    00001170 MSFT 0100000E)                                                                           
[    0.000000] ACPI: FACS 3f6f6000 00040                                        
[    0.000000] ACPI: SSDT 3f6e76b4 00033 (v01 IBM    TP-70    00001170 MSFT 0100000E)                                                                           
[    0.000000] ACPI: ECDT 3f6f4e2f 00052 (v01 IBM    TP-70    00001170 IBM  00000001)                                                                           
[    0.000000] ACPI: TCPA 3f6f4e81 00032 (v01 IBM    TP-70    00001170 PTL  00000001)                                                                           
[    0.000000] ACPI: APIC 3f6f4eb3 0005A (v01 IBM    TP-70    00001170 IBM  00000001)                                                                           
[    0.000000] ACPI: MCFG 3f6f4f0d 0003E (v01 IBM    TP-70    00001170 IBM  00000001)                                                                           
[    0.000000] ACPI: BOOT 3f6f4fd8 00028 (v01 IBM    TP-70    00001170  LTP 00000001)                                                                           
[    0.000000] ACPI: Local APIC address 0xfee00000                              
[    0.000000] 126MB HIGHMEM available.                                         
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
[    0.000000]   #4 [002f162000 - 002f967850]          RAMDISK ==> [002f162000 - 002f967850]                                                                    
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]                                                                    
[    0.000000]   #6 [00008a9000 - 00008ac128]              BRK ==> [00008a9000 - 00008ac128]                                                                    
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]                                                                    
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]                                                                    
[    0.000000] Zone PFN ranges:                                                 
[    0.000000]   DMA      0x00000000 -> 0x00001000                              
[    0.000000]   Normal   0x00001000 -> 0x000377fe                              
[    0.000000]   HighMem  0x000377fe -> 0x0003f6e0                              
[    0.000000] Movable zone start PFN for each node                             
[    0.000000] early_node_map[3] active PFN ranges                              
[    0.000000]     0: 0x00000000 -> 0x00000002                                  
[    0.000000]     0: 0x00000006 -> 0x0000009f                                  
[    0.000000]     0: 0x00000100 -> 0x0003f6e0                                  
[    0.000000] On node 0 totalpages: 259707                                     
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000000                                                                               
[    0.000000]   DMA zone: 32 pages used for memmap                             
[    0.000000]   DMA zone: 0 pages reserved                                     
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0                             
[    0.000000]   Normal zone: 1744 pages used for memmap                        
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31                       
[    0.000000]   HighMem zone: 254 pages used for memmap                        
[    0.000000]   HighMem zone: 32228 pages, LIFO batch:7                        
[    0.000000] Using APIC driver default                                        
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                   
[    0.000000] ACPI: Local APIC address 0xfee00000                              
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
[    0.000000] nr_irqs_gsi: 24                                                  
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)                                                                           
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1           
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes   
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257677                                                                      
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=23ea8106-4e82-4050-8f36-b9329e902c02 ro quiet splash                   
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)            
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)   
[    0.000000] Enabling fast FPU save and restore... done.                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.            
[    0.000000] Initializing CPU#0                                               
[    0.000000] allocated 5196160 bytes of page_cgroup                           
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                                                       
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6e0)              
[    0.000000] Memory: 1008264k/1039232k available (4566k kernel code, 30172k reserved, 2142k data, 540k init, 129928k highmem)                                 
[    0.000000] virtual kernel memory layout:                                    
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)                
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)                
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)                
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)                
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)                
[    0.000000]       .data : 0xc0575b44 - 0xc078d3c8   (2142 kB)                
[    0.000000]       .text : 0xc0100000 - 0xc0575b44   (4566 kB)                
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                      
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1                                                                          
[    0.000000] NR_IRQS:2304 nr_irqs:256                                         
[    0.000000] Extended CMOS year: 2000                                         
[    0.000000] Fast TSC calibration using PIT                                   
[    0.000000] Detected 1994.991 MHz processor.                                 
[    0.001883] Console: colour VGA+ 80x25                                       
[    0.001887] console [tty0] enabled                                           
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.98 BogoMIPS (lpj=7979964)                                        
[    0.004028] Security Framework initialized                                   
[    0.004052] AppArmor: AppArmor initialized                                   
[    0.004059] Mount-cache hash table entries: 512                              
[    0.004186] Initializing cgroup subsys ns                                    
[    0.004191] Initializing cgroup subsys cpuacct                               
[    0.004195] Initializing cgroup subsys memory                                
[    0.004203] Initializing cgroup subsys freezer                               
[    0.004206] Initializing cgroup subsys net_cls                               
[    0.004221] CPU: L1 I cache: 32K, L1 D cache: 32K                            
[    0.004224] CPU: L2 cache: 2048K                                             
[    0.004230] mce: CPU supports 5 MCE banks                                    
[    0.004238] CPU0: Thermal monitoring enabled (TM1)                           
[    0.004246] Performance Counters: p6 PMU driver.                             
[    0.004253] ... version:                 0                                   
[    0.004254] ... bit width:               32                                  
[    0.004256] ... generic counters:        2                                   
[    0.004258] ... value mask:              00000000ffffffff                    
[    0.004260] ... max period:              000000007fffffff                    
[    0.004262] ... fixed-purpose counters:  0                                   
[    0.004264] ... counter mask:            0000000000000003                    
[    0.004269] Checking 'hlt' instruction... OK.                                
[    0.020784] SMP alternatives: switching to UP code                           
[    0.026983] Freeing SMP alternatives: 19k freed                              
[    0.026991] ACPI: Core revision 20090521                                     
[    0.048451] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1             
[    0.091235] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08        
[    0.092001] Brought up 1 CPUs                                                
[    0.092001] Total of 1 processors activated (3989.98 BogoMIPS).              
[    0.092001] CPU0 attaching NULL sched-domain.                                
[    0.092001] Booting paravirtualized kernel on bare hardware                  
[    0.092001] regulator: core version 0.5                                      
[    0.092001] Time:  2:37:45  Date: 11/28/09                                   
[    0.092001] NET: Registered protocol family 16                               
[    0.092001] EISA bus registered                                              
[    0.092001] ACPI: bus type pci registered                                    
[    0.092001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255 
[    0.092001] PCI: MCFG area at e0000000 reserved in E820                      
[    0.092001] PCI: Using MMCONFIG for extended config space                    
[    0.092001] PCI: Using configuration type 1 for base access                  
[    0.092001] bio: create slab <bio-0> at 0                                    
[    0.092001] ACPI: EC: EC description table is found, configuring boot EC     
[    0.098849] ACPI: EC: non-query interrupt received, switching to interrupt mode                                                                              
[    0.109174] ACPI: Interpreter enabled                                        
[    0.109179] ACPI: (supports S0 S3 S4 S5)                                     
[    0.109204] ACPI: Using IOAPIC for interrupt routing                         
[    0.124550] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62    
[    0.124553] ACPI: EC: driver started in interrupt mode                       
[    0.124594] ACPI: Power Resource [PUBS] (on)                                 
[    0.129039] ACPI: ACPI Dock Station Driver: 3 docks/bays found               
[    0.129062] ACPI: PCI Root Bridge [PCI0] (0000:00)                           
[    0.129142] pci 0000:00:02.0: reg 10 32bit mmio: [0x90080000-0x900fffff]     
[    0.129147] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]                
[    0.129152] pci 0000:00:02.0: reg 18 32bit mmio: [0xb0000000-0xbfffffff]     
[    0.129157] pci 0000:00:02.0: reg 1c 32bit mmio: [0x90000000-0x9003ffff]     
[    0.129187] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]         
[    0.129324] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold            
[    0.129329] pci 0000:00:1c.0: PME# disabled                                  
[    0.129418] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold            
[    0.129423] pci 0000:00:1c.2: PME# disabled                                  
[    0.129489] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]                
[    0.129554] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]                
[    0.129618] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]                
[    0.129681] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]                
[    0.129748] pci 0000:00:1d.7: reg 10 32bit mmio: [0x90040000-0x900403ff]     
[    0.129810] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold            
[    0.129816] pci 0000:00:1d.7: PME# disabled                                  
[    0.129922] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]                
[    0.129930] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]                
[    0.129938] pci 0000:00:1e.2: reg 18 32bit mmio: [0x90040800-0x900409ff]     
[    0.129947] pci 0000:00:1e.2: reg 1c 32bit mmio: [0x90040400-0x900404ff]     
[    0.129986] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold            
[    0.129991] pci 0000:00:1e.2: PME# disabled                                  
[    0.130030] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]                
[    0.130038] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]                
[    0.130089] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold            
[    0.130094] pci 0000:00:1e.3: PME# disabled                                  
[    0.130185] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000               
[    0.130193] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO                                                                          
[    0.130198] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO   
[    0.130203] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f       
[    0.130207] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef       
[    0.130250] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]                    
[    0.130258] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]                    
[    0.130266] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]                    
[    0.130274] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]                    
[    0.130283] pci 0000:00:1f.2: reg 20 io port: [0x1810-0x181f]                
[    0.130318] pci 0000:00:1f.2: PME# supported from D3hot                      
[    0.130322] pci 0000:00:1f.2: PME# disabled                                  
[    0.130384] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]                
[    0.130498] pci 0000:02:00.0: reg 10 64bit mmio: [0x90100000-0x9010ffff]     
[    0.130595] pci 0000:02:00.0: PME# supported from D3hot D3cold               
[    0.130601] pci 0000:02:00.0: PME# disabled                                  
[    0.130671] pci 0000:00:1c.0: bridge 32bit mmio: [0x90100000-0x901fffff]     
[    0.130734] pci 0000:00:1c.2: bridge io port: [0x3000-0x3fff]                
[    0.130739] pci 0000:00:1c.2: bridge 32bit mmio: [0x90200000-0x902fffff]     
[    0.130748] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xc0000000-0xc00fffff]
[    0.130801] pci 0000:04:00.0: reg 10 32bit mmio: [0x90300000-0x90300fff]     
[    0.130831] pci 0000:04:00.0: supports D1 D2                                 
[    0.130833] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold      
[    0.130839] pci 0000:04:00.0: PME# disabled                                  
[    0.130894] pci 0000:04:02.0: reg 10 32bit mmio: [0x90301000-0x90301fff]     
[    0.130970] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold            
[    0.130976] pci 0000:04:02.0: PME# disabled                                  
[    0.131042] pci 0000:00:1e.0: transparent bridge                             
[    0.131047] pci 0000:00:1e.0: bridge io port: [0x4000-0x7fff]                
[    0.131052] pci 0000:00:1e.0: bridge 32bit mmio: [0x90300000-0x9fffffff]     
[    0.131060] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.131105] pci_bus 0000:00: on NUMA node 0                                  
[    0.131110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]              
[    0.131225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]         
[    0.131293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]         
[    0.131365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]         
[    0.135441] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.135624] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.135804] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.135985] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.136173] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.136355] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.136534] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.136716] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)        
[    0.136925] SCSI subsystem initialized                                       
[    0.136971] libata version 3.00 loaded.                                      
[    0.137041] usbcore: registered new interface driver usbfs                   
[    0.137057] usbcore: registered new interface driver hub                     
[    0.137087] usbcore: registered new device driver usb                        
[    0.137212] ACPI: WMI: Mapper loaded                                         
[    0.137214] PCI: Using ACPI for IRQ routing                                  
[    0.137291] Expanded resource reserved due to conflict with Adapter ROM      
[    0.137373] Bluetooth: Core ver 2.15                                         
[    0.137397] NET: Registered protocol family 31                               
[    0.137399] Bluetooth: HCI device and connection manager initialized         
[    0.137403] Bluetooth: HCI socket layer initialized                          
[    0.137405] NetLabel: Initializing                                           
[    0.137407] NetLabel:  domain hash size = 128                                
[    0.137408] NetLabel:  protocols = UNLABELED CIPSOv4                         
[    0.137422] NetLabel:  unlabeled traffic allowed by default                  
[    0.137565] hpet clockevent registered                                       
[    0.137569] HPET: 3 timers in total, 0 timers will be used for per-cpu timer 
[    0.137576] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                          
[    0.137581] hpet0: 3 comparators, 64-bit 14.318180 MHz counter               
[    0.141782] pnp: PnP ACPI init                                               
[    0.141804] ACPI: bus type pnp registered                                    
[    0.145580] pnp: PnP ACPI: found 14 devices                                  
[    0.145583] ACPI: ACPI bus type pnp unregistered                             
[    0.145586] PnPBIOS: Disabled by ACPI PNP                                    
[    0.145603] system 00:00: iomem range 0x0-0x9ffff could not be reserved      
[    0.145606] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved  
[    0.145610] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved  
[    0.145613] system 00:00: iomem range 0xc8000-0xcbfff has been reserved      
[    0.145616] system 00:00: iomem range 0xcc000-0xcffff could not be reserved  
[    0.145619] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved  
[    0.145622] system 00:00: iomem range 0xdc000-0xdffff could not be reserved  
[    0.145625] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved  
[    0.145629] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved  
[    0.145632] system 00:00: iomem range 0xe8000-0xebfff could not be reserved  
[    0.145635] system 00:00: iomem range 0xec000-0xeffff could not be reserved  
[    0.145638] system 00:00: iomem range 0xf0000-0xfffff could not be reserved  
[    0.145641] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved                                                                              
[    0.145645] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved                                                                            
[    0.145653] system 00:02: ioport range 0x1000-0x107f has been reserved       
[    0.145656] system 00:02: ioport range 0x1180-0x11bf has been reserved       
[    0.145659] system 00:02: ioport range 0x15e0-0x15ef has been reserved       
[    0.145662] system 00:02: ioport range 0x1600-0x1641 has been reserved       
[    0.145665] system 00:02: ioport range 0x1644-0x167f has been reserved       
[    0.145668] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.145672] system 00:02: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.145675] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.145678] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.145681] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.180352] AppArmor: AppArmor Filesystem Enabled                            
[    0.180402] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02              
[    0.180405] pci 0000:00:1c.0:   IO window: disabled                          
[    0.180412] pci 0000:00:1c.0:   MEM window: 0x90100000-0x901fffff            
[    0.180417] pci 0000:00:1c.0:   PREFETCH window: disabled                    
[    0.180422] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03              
[    0.180426] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff                     
[    0.180433] pci 0000:00:1c.2:   MEM window: 0x90200000-0x902fffff            
[    0.180438] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0000000-0x000000c00fffff                                                                           
[    0.180448] pci 0000:04:00.0: CardBus bridge, secondary bus 0000:05          
[    0.180451] pci 0000:04:00.0:   IO window: 0x004000-0x0040ff                 
[    0.180457] pci 0000:04:00.0:   IO window: 0x004400-0x0044ff                 
[    0.180464] pci 0000:04:00.0:   PREFETCH window: 0xc8000000-0xcbffffff       
[    0.180470] pci 0000:04:00.0:   MEM window: 0x94000000-0x97ffffff            
[    0.180477] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04              
[    0.180481] pci 0000:00:1e.0:   IO window: 0x4000-0x7fff                     
[    0.180487] pci 0000:00:1e.0:   MEM window: 0x90300000-0x9fffffff            
[    0.180493] pci 0000:00:1e.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff                                                                           
[    0.180511]   alloc irq_desc for 20 on node -1                               
[    0.180513]   alloc kstat_irqs on node -1                                    
[    0.180520] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20     
[    0.180528] pci 0000:00:1c.0: setting latency timer to 64                    
[    0.180536]   alloc irq_desc for 22 on node -1                               
[    0.180538]   alloc kstat_irqs on node -1                                    
[    0.180541] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22     
[    0.180547] pci 0000:00:1c.2: setting latency timer to 64                    
[    0.180555] pci 0000:00:1e.0: setting latency timer to 64                    
[    0.180565]   alloc irq_desc for 16 on node -1                               
[    0.180567]   alloc kstat_irqs on node -1                                    
[    0.180574] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    0.180583] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                   
[    0.180586] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]           
[    0.180589] pci_bus 0000:02: resource 1 mem: [0x90100000-0x901fffff]         
[    0.180592] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]                 
[    0.180595] pci_bus 0000:03: resource 1 mem: [0x90200000-0x902fffff]         
[    0.180598] pci_bus 0000:03: resource 2 pref mem [0xc0000000-0xc00fffff]     
[    0.180600] pci_bus 0000:04: resource 0 io:  [0x4000-0x7fff]                 
[    0.180603] pci_bus 0000:04: resource 1 mem: [0x90300000-0x9fffffff]         
[    0.180606] pci_bus 0000:04: resource 2 pref mem [0xc8000000-0xcfffffff]     
[    0.180609] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]                   
[    0.180612] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]           
[    0.180614] pci_bus 0000:05: resource 0 io:  [0x4000-0x40ff]                 
[    0.180617] pci_bus 0000:05: resource 1 io:  [0x4400-0x44ff]                 
[    0.180620] pci_bus 0000:05: resource 2 pref mem [0xc8000000-0xcbffffff]     
[    0.180623] pci_bus 0000:05: resource 3 mem: [0x94000000-0x97ffffff]         
[    0.180660] NET: Registered protocol family 2                                
[    0.180751] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.181058] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                                             
[    0.182066] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)      
[    0.182713] TCP: Hash tables configured (established 131072 bind 65536)      
[    0.182716] TCP reno registered                                              
[    0.182830] NET: Registered protocol family 1                                
[    0.182916] Trying to unpack rootfs image as initramfs...                    
[    0.416507] Freeing initrd memory: 8214k freed                               
[    0.423170] Simple Boot Flag at 0x35 set to 0x1                              
[    0.423273] cpufreq-nforce2: No nForce2 chipset.                             
[    0.423306] Scanning for low memory corruption every 60 seconds              
[    0.423449] audit: initializing netlink socket (disabled)                    
[    0.423482] type=2000 audit(1259375865.420:1): initialized                   
[    0.432321] highmem bounce pool size: 64 pages                               
[    0.432328] HugeTLB registered 4 MB page size, pre-allocated 0 pages         
[    0.433759] VFS: Disk quotas dquot_6.5.2                                     
[    0.433815] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)       
[    0.434363] fuse init (API version 7.12)                                     
[    0.434447] msgmni has been set to 1732                                      
[    0.434644] alg: No test for stdrng (krng)                                   
[    0.434656] io scheduler noop registered                                     
[    0.434658] io scheduler anticipatory registered                             
[    0.434660] io scheduler deadline registered                                 
[    0.434700] io scheduler cfq registered (default)                            
[    0.434715] pci 0000:00:02.0: Boot video device                              
[    0.434935]   alloc irq_desc for 24 on node -1                               
[    0.434938]   alloc kstat_irqs on node -1                                    
[    0.434951] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X               
[    0.434963] pcieport-driver 0000:00:1c.0: setting latency timer to 64        
[    0.435110]   alloc irq_desc for 25 on node -1                               
[    0.435112]   alloc kstat_irqs on node -1                                    
[    0.435121] pcieport-driver 0000:00:1c.2: irq 25 for MSI/MSI-X               
[    0.435131] pcieport-driver 0000:00:1c.2: setting latency timer to 64        
[    0.435241] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                  
[    0.435330] pciehp: PCI Express Hot Plug Controller Driver version: 0.4      
[    0.435788] ACPI: AC Adapter [AC] (on-line)                                  
[    0.435860] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                             
[    0.435864] ACPI: Power Button [PWRF]                                        
[    0.435915] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1                                                                      
[    0.436452] ACPI: Lid Switch [LID]                                           
[    0.436495] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2                                                                    
[    0.436501] ACPI: Sleep Button [SLPB]                                        
[    0.438326] Marking TSC unstable due to TSC halts in idle                    
[    0.438353] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                  
[    0.438377] processor LNXCPU:00: registered as cooling_device0               
[    0.438381] ACPI: Processor [CPU0] (supports 8 throttling states)            
[    0.442380] Switched to high resolution mode on CPU 0                        
[    0.444041] thermal LNXTHERM:01: registered as thermal_zone0                 
[    0.444049] ACPI: Thermal Zone [THM0] (60 C)                                 
[    0.444094] isapnp: Scanning for PnP cards...                                
[    0.798875] isapnp: No Plug & Play device found                              
[    0.799943] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled          
[    0.800886] serial 00:0a: activated                                          
[    0.801000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A                
[    0.801110]   alloc irq_desc for 23 on node -1                               
[    0.801112]   alloc kstat_irqs on node -1                                    
[    0.801120] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23  
[    0.801127] serial 0000:00:1e.3: PCI INT B disabled                          
[    0.802016] brd: module loaded                                               
[    0.802456] loop: module loaded                                              
[    0.802526] input: Macintosh mouse button emulation as /devices/virtual/input/input3                                                                         
[    0.802597] ahci 0000:00:1f.2: version 3.0                                   
[    0.802618] ahci: probe of 0000:00:1f.2 failed with error -22                
[    0.802655] ata_piix 0000:00:1f.2: version 2.13                              
[    0.802664] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]                     
[    0.834549] ACPI: Battery Slot [BAT0] (battery present)                      
[    0.956029] ata_piix 0000:00:1f.2: setting latency timer to 64               
[    0.956104] scsi0 : ata_piix                                                 
[    0.956179] scsi1 : ata_piix                                                 
[    0.957068] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14  
[    0.957071] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15  
[    0.957880] Fixed MDIO Bus: probed                                           
[    0.957916] PPP generic driver version 2.4.2                                 
[    0.957995] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver       
[    0.958478] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0         
[    0.958486]   alloc irq_desc for 19 on node -1                               
[    0.958489]   alloc kstat_irqs on node -1                                    
[    0.958494] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.958508] ehci_hcd 0000:00:1d.7: setting latency timer to 64               
[    0.958512] ehci_hcd 0000:00:1d.7: EHCI Host Controller                      
[    0.958568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                                                             
[    0.962473] ehci_hcd 0000:00:1d.7: debug port 1                              
[    0.962480] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported    
[    0.962495] ehci_hcd 0000:00:1d.7: irq 19, io mem 0x90040000                 
[    0.976018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                
[    0.976098] usb usb1: configuration #1 chosen from 1 choice                  
[    0.976129] hub 1-0:1.0: USB hub found                                       
[    0.976136] hub 1-0:1.0: 8 ports detected                                    
[    0.976204] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver           
[    0.976223] uhci_hcd: USB Universal Host Controller Interface driver         
[    0.976569] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0         
[    0.976575] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.976581] uhci_hcd 0000:00:1d.0: setting latency timer to 64               
[    0.976585] uhci_hcd 0000:00:1d.0: UHCI Host Controller                      
[    0.976615] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                                                             
[    0.976647] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820                
[    0.976733] usb usb2: configuration #1 chosen from 1 choice                  
[    0.976759] hub 2-0:1.0: USB hub found                                       
[    0.976766] hub 2-0:1.0: 2 ports detected                                    
[    0.977368] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0         
[    0.977373]   alloc irq_desc for 17 on node -1                               
[    0.977375]   alloc kstat_irqs on node -1                                    
[    0.977379] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.977386] uhci_hcd 0000:00:1d.1: setting latency timer to 64               
[    0.977389] uhci_hcd 0000:00:1d.1: UHCI Host Controller                      
[    0.977417] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                                                             
[    0.977449] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840                
[    0.977520] usb usb3: configuration #1 chosen from 1 choice                  
[    0.977545] hub 3-0:1.0: USB hub found                                       
[    0.977552] hub 3-0:1.0: 2 ports detected                                    
[    0.977599]   alloc irq_desc for 18 on node -1                               
[    0.977601]   alloc kstat_irqs on node -1                                    
[    0.977605] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.977612] uhci_hcd 0000:00:1d.2: setting latency timer to 64               
[    0.977615] uhci_hcd 0000:00:1d.2: UHCI Host Controller                      
[    0.977646] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                                                             
[    0.977678] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860                
[    0.977748] usb usb4: configuration #1 chosen from 1 choice                  
[    0.977776] hub 4-0:1.0: USB hub found                                       
[    0.977782] hub 4-0:1.0: 2 ports detected                                    
[    0.977823] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.977829] uhci_hcd 0000:00:1d.3: setting latency timer to 64               
[    0.977833] uhci_hcd 0000:00:1d.3: UHCI Host Controller                      
[    0.977859] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5                                                                             
[    0.977882] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880                
[    0.977953] usb usb5: configuration #1 chosen from 1 choice                  
[    0.977981] hub 5-0:1.0: USB hub found                                       
[    0.977987] hub 5-0:1.0: 2 ports detected                                    
[    0.978081] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12                                                                             
[    0.985086] serio: i8042 KBD port at 0x60,0x64 irq 1                         
[    0.985091] serio: i8042 AUX port at 0x60,0x64 irq 12                        
[    0.985144] mice: PS/2 mouse device common for all mice                      
[    0.985244] rtc_cmos 00:06: RTC can wake from S4                             
[    0.985274] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0            
[    0.985306] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs    
[    0.985403] device-mapper: uevent: version 1.0.3                             
[    0.985482] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com                                                                 
[    0.985552] device-mapper: multipath: version 1.1.0 loaded                   
[    0.985555] device-mapper: multipath round-robin: version 1.0.0 loaded       
[    0.985659] EISA: Probing bus 0 at eisa.0                                    
[    0.985666] Cannot allocate resource for EISA slot 1                         
[    0.985668] Cannot allocate resource for EISA slot 2                         
[    0.985670] Cannot allocate resource for EISA slot 3                         
[    0.985672] Cannot allocate resource for EISA slot 4                         
[    0.985674] Cannot allocate resource for EISA slot 5                         
[    0.985676] Cannot allocate resource for EISA slot 6                         
[    0.985678] Cannot allocate resource for EISA slot 7                         
[    0.985685] EISA: Detected 0 cards.                                          
[    0.985765] cpuidle: using governor ladder                                   
[    0.985825] cpuidle: using governor menu                                     
[    0.986281] TCP cubic registered                                             
[    0.986434] NET: Registered protocol family 10                               
[    0.986843] lo: Disabled Privacy Extensions                                  
[    0.987137] NET: Registered protocol family 17                               
[    0.987154] Bluetooth: L2CAP ver 2.13                                        
[    0.987156] Bluetooth: L2CAP socket layer initialized                        
[    0.987159] Bluetooth: SCO (Voice Link) ver 0.6                              
[    0.987161] Bluetooth: SCO socket layer initialized                          
[    0.987193] Bluetooth: RFCOMM TTY layer initialized                          
[    0.987196] Bluetooth: RFCOMM socket layer initialized                       
[    0.987198] Bluetooth: RFCOMM ver 1.11                                       
[    0.987329] P-state transition latency capped at 20 uS                       
[    0.987647] Using IPI No-Shortcut mode                                       
[    0.987705] PM: Resume from disk failed.                                     
[    0.987717] registered taskstats version 1                                   
[    0.987815]   Magic number: 1:924:612                                        
[    0.987837] tty tty: hash matches                                            
[    0.987895] rtc_cmos 00:06: setting system clock to 2009-11-28 02:37:46 UTC (1259375866)                                                                     
[    0.987905] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found             
[    0.987906] EDD information not available.                                   
[    0.990490] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4                                                               
[    1.120706] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0J04, max UDMA/33                                                                             
[    1.121230] ata1.00: ATA-6: HTS548060M9AT00, MGBOA5HA, max UDMA/100          
[    1.121233] ata1.00: 117210240 sectors, multi 16: LBA                        
[    1.121246] ata1.00: applying bridge limits                                  
[    1.136057] Clocksource tsc unstable (delta = -135934090 ns)                 
[    1.136615] ata2.00: configured for UDMA/33                                  
[    1.137058] ata1.00: configured for UDMA/100                                 
[    1.137183] scsi 0:0:0:0: Direct-Access     ATA      HTS548060M9AT00  MGBO PQ: 0 ANSI: 5                                                                     
[    1.137291] sd 0:0:0:0: Attached scsi generic sg0 type 0                     
[    1.137330] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)                                                                          
[    1.137503] sd 0:0:0:0: [sda] Write Protect is off                           
[    1.137507] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[    1.137532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    1.137651]  sda:                                                            
[    1.141692] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0J04 PQ: 0 ANSI: 5                                                                     
[    1.152703] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray    
[    1.152706] Uniform CD-ROM driver Revision: 3.20                             
[    1.152779] sr 1:0:0:0: Attached scsi CD-ROM sr0                             
[    1.152818] sr 1:0:0:0: Attached scsi generic sg1 type 5                     
[    1.163470]  sda1 sda2 sda3 sda4 < sda5 >                                    
[    1.191011] sd 0:0:0:0: [sda] Attached SCSI disk                             
[    1.191027] Freeing unused kernel memory: 540k freed                         
[    1.191334] Write protecting the kernel text: 4568k                          
[    1.191369] Write protecting the kernel read-only data: 1836k                
[    1.284645] ramzswap: disk size set to 254356 kB                             
[    1.343960] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input5                                                             
[    1.344067] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)    
[    1.373666] Linux agpgart interface v0.103                                   
[    1.377149] agpgart-intel 0000:00:00.0: Intel 915GM Chipset                  
[    1.377781] agpgart-intel 0000:00:00.0: detected 7932K stolen memory         
[    1.382522] Floppy drive(s): fd0 is 1.44M                                    
[    1.387090] tg3.c:v3.99 (April 20, 2009)                                     
[    1.387108] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    1.387119] tg3 0000:02:00.0: setting latency timer to 64                    
[    1.392136] tg3 0000:02:00.0: PME# disabled                                  
[    1.409017] FDC 0 is a National Semiconductor PC87306                        
[    1.419245] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000    
[    1.453223] Adding 254352k swap on /dev/ramzswap0.  Priority:100 extents:1 across:254352k SSD                                                                
[    1.526651] eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:10:c6:ce:c1:93                                                            
[    1.526657] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])                                                                           
[    1.526660] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]         
[    1.526662] eth0: dma_rwctrl[76180000] dma_mask[64-bit]                      
[    1.527050] [drm] Initialized drm 1.1.0 20060810                             
[    1.541446] i915 0000:00:02.0: power state changed by ACPI to D0             
[    1.541460] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16    
[    1.541466] i915 0000:00:02.0: setting latency timer to 64                   
[    1.555283] i2c-adapter i2c-1: unable to read EDID block.                    
[    1.555288] i915 0000:00:02.0: LVDS-1: no EDID data                          
[    1.876500] [drm] DAC-6: set mode 640x480 0                                  
[    1.965870] i2c-adapter i2c-1: unable to read EDID block.                    
[    1.965873] i915 0000:00:02.0: LVDS-1: no EDID data                          
[    2.006425] [drm] TV-12: set mode NTSC 480i 0                                
[    2.131290] [drm] fb0: inteldrmfb frame buffer device                        
[    2.131301] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.193819] render error detected, EIR: 0x00000010                           
[    2.193822] page table error                                                 
[    2.193823]   PGTBL_ER: 0x00000100                                           
[    2.193827] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking   
[    2.193834] render error detected, EIR: 0x00000010                           
[    2.193836] page table error                                                 
[    2.193837]   PGTBL_ER: 0x00000100                                           
[    2.209841] [drm] LVDS-8: set mode 1024x768 16                               
[    2.233762] Console: switching to colour frame buffer device 128x48          
[    2.636779] xor: automatically using best checksumming function: pIII_sse    
[    2.656007]    pIII_sse  :  5183.000 MB/sec                                  
[    2.656010] xor: using function: pIII_sse (5183.000 MB/sec)                  
[    2.659198] device-mapper: dm-raid45: initialized v0.2594b                   
[    2.903478] PM: Starting manual resume from disk                             
[    2.903482] PM: Resume from partition 8:5                                    
[    2.903484] PM: Checking hibernation image.                                  
[    2.903671] PM: Resume from disk failed.                                     
[    2.926120] EXT4-fs (sda2): barriers enabled                                 
[    2.948943] kjournald2 starting: pid 414, dev sda2:8, commit interval 5 seconds                                                                              
[    2.948954] EXT4-fs (sda2): delayed allocation enabled                       
[    2.948957] EXT4-fs: file extents enabled                                    
[    2.949755] EXT4-fs: mballoc enabled                                         
[    2.949772] EXT4-fs (sda2): mounted filesystem with ordered data mode        
[    5.417737] Adding 2056280k swap on /dev/sda5.  Priority:-1 extents:1 across:2056280k                                                                        
[    5.754310] udev: starting version 147                                       
[    6.108601] lp: driver loaded but no devices found                           
[    6.203461] parport_pc 00:0b: reported by Plug and Play ACPI                 
[    6.203518] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]              
[    6.238014] Non-volatile memory driver v1.3                                  
[    6.292305] lp0: using parport0 (interrupt-driven).                          
[    6.455114] ppdev: user-space parallel port driver                           
[    6.512023] irda_init()                                                      
[    6.512033] NET: Registered protocol family 23                               
[    6.545976] nsc-ircc 00:0c: activated                                        
[    6.545981] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.                                                                            
[    6.546035] nsc-ircc, chip->init                                             
[    6.546048] nsc-ircc, Found chip at base=0x02e                               
[    6.546086] nsc-ircc, driver loaded (Dag Brattli)                            
[    6.546707] IrDA: Registered device irda0                                    
[    6.546709] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500    
[    7.059035] thinkpad_acpi: ThinkPad ACPI Extras v0.23                        
[    7.059038] thinkpad_acpi: http://ibm-acpi.sf.net/                           
[    7.059041] thinkpad_acpi: ThinkPad BIOS 70ET57WW (1.17 ), EC 70HT26WW-1.03  
[    7.059043] thinkpad_acpi: IBM ThinkPad T43, model 1872J13                   
[    7.065956] Registered led device: tpacpi::thinklight                        
[    7.065987] Registered led device: tpacpi::power                             
[    7.066003] Registered led device: tpacpi::standby                           
[    7.069353] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode                                                              
[    7.069517] input: ThinkPad Extra Buttons as /devices/virtual/input/input6   
[    7.089959] lib80211: common routines for IEEE802.11 drivers                 
[    7.089963] lib80211_crypt: registered algorithm 'NULL'                      
[    7.411959] ieee80211: 802.11 data/management/control stack, git-1.1.13      
[    7.411963] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>                                                                  
[    7.561640] intel_rng: FWH not detected                                      
[    7.588637] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0                                                                          
[    7.588642] serio: Synaptics pass-through port at isa0060/serio1/input0      
[    7.627847] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7                                                                 
[    7.676813] EXT4-fs (sda2): internal journal on sda2:8                       
[    7.751599] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq                                                                              
[    7.751603] ipw2200: Copyright(c) 2003-2006 Intel Corporation                
[    7.751685]   alloc irq_desc for 21 on node -1                               
[    7.751688]   alloc kstat_irqs on node -1                                    
[    7.751696] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    7.751766] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection   
[    7.751818] ipw2200 0000:04:02.0: firmware: requesting ipw2200-bss.fw        
[    8.268637] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)                                                                       
[    8.268703] yenta_cardbus 0000:04:00.0: CardBus bridge found [1014:0528]     
[    8.268730] yenta_cardbus 0000:04:00.0: Using INTVAL to route CSC interrupts to PCI                                                                          
[    8.268732] yenta_cardbus 0000:04:00.0: Routing CardBus interrupts to PCI    
[    8.268739] yenta_cardbus 0000:04:00.0: TI: mfunc 0x01d21002, devctl 0x64    
[    8.360461] ip_tables: (C) 2000-2006 Netfilter Core Team                     
[    8.500580] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c30, PCI irq 16      
[    8.500586] yenta_cardbus 0000:04:00.0: Socket status: 30000007              
[    8.500593] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff                                                                
[    8.500597] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x7fff: clean.                                                                            
[    8.501481] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0x90300000 - 0x9fffffff                                                     
[    8.501484] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xc8000000 - 0xcfffffff                                                     
[    8.662036] EXT4-fs (sda3): barriers enabled                                 
[    8.664512] kjournald2 starting: pid 805, dev sda3:8, commit interval 5 seconds                                                                              
[    8.664893] EXT4-fs (sda3): internal journal on sda3:8                       
[    8.664897] EXT4-fs (sda3): delayed allocation enabled                       
[    8.664900] EXT4-fs: file extents enabled                                    
[    8.665964] EXT4-fs: mballoc enabled                                         
[    8.665977] EXT4-fs (sda3): mounted filesystem with ordered data mode        
[    8.980806] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.                                                                              
[    8.982699] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7                                                               
[    8.983494] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.                                                                              
[    8.984184] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.                                                                              
[    8.985029] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.                                                                              
[    9.057918] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                                                               
[    9.057948] Intel ICH 0000:00:1e.2: setting latency timer to 64              
[    9.984037] intel8x0_measure_ac97_clock: measured 55463 usecs (2672 samples) 
[    9.984041] intel8x0: clocking to 48000                                      
[   10.228402] psmouse serio2: ID: 10 00 64                                     
[   11.949520] type=1505 audit(1259393877.460:2): operation="profile_load" pid=954 name=/sbin/dhclient3                                                         
[   11.950158] type=1505 audit(1259393877.460:3): operation="profile_load" pid=954 name=/usr/lib/NetworkManager/nm-dhcp-client.action                           
[   11.950505] type=1505 audit(1259393877.460:4): operation="profile_load" pid=954 name=/usr/lib/connman/scripts/dhclient-script                                
[   12.909878] type=1505 audit(1259393878.420:5): operation="profile_load" pid=966 name=/usr/lib/cups/backend/cups-pdf                                          
[   12.910628] type=1505 audit(1259393878.420:6): operation="profile_load" pid=966 name=/usr/sbin/cupsd                                                         
[   13.000184] type=1505 audit(1259393878.512:7): operation="profile_load" pid=976 name=/usr/sbin/mysqld-akonadi                                                
[   13.425556] type=1505 audit(1259393878.937:8): operation="profile_load" pid=981 name=/usr/sbin/tcpdump                                                       
[   13.629226] IBM TrackPoint firmware: 0x0e, buttons: 3/3                      
[   13.853648] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8                                                               
[   14.141181] tg3 0000:02:00.0: PME# disabled                                  
[   14.322379] ADDRCONF(NETDEV_UP): eth0: link is not ready                     
[   17.269584] tg3: eth0: Link is up at 1000 Mbps, full duplex.                 
[   17.269588] tg3: eth0: Flow control is on for TX and on for RX.              
[   17.269783] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                
[   18.918933] [drm] DAC-6: set mode 640x480 0                                  
[   19.024023] [drm] DAC-6: set mode 640x480 0                                  
[   19.131729] i2c-adapter i2c-1: unable to read EDID block.                    
[   19.131732] i915 0000:00:02.0: LVDS-1: no EDID data                          
[   19.172385] [drm] TV-12: set mode NTSC 480i 0                                
[   19.283327] vboxdrv: Trying to deactivate the NMI watchdog permanently...    
[   19.283332] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance                                                                 
[   19.283334] vboxdrv: counter framework which can generate NMIs is active. You have to prevent                                                                
[   19.283335] vboxdrv: the usage of hardware performance counters by           
[   19.283337] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid       
[   19.283341] vboxdrv: Found 1 processor cores.                                
[   19.283452] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.                                                                               
[   19.283454] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).                                                                           
[   19.345909] [drm] TV-12: set mode NTSC 480i 0                                
[   19.499865] [drm] DAC-6: set mode 640x480 0                                  
[   19.614550] [drm] DAC-6: set mode 640x480 0                                  
[   19.861469] i2c-adapter i2c-1: unable to read EDID block.                    
[   19.861474] i915 0000:00:02.0: LVDS-1: no EDID data                          
[   19.940199] [drm] TV-12: set mode NTSC 480i 0                                
[   20.091597] [drm] TV-12: set mode NTSC 480i 0                                
[   24.552025] eth1: no IPv6 routers present                                    
[   27.812027] eth0: no IPv6 routers present
[   40.273542] [drm] DAC-6: set mode 640x480 0
[   40.378661] [drm] DAC-6: set mode 640x480 0
[   40.447149] i2c-adapter i2c-1: unable to read EDID block.
[   40.447153] i915 0000:00:02.0: LVDS-1: no EDID data
[   40.488268] [drm] TV-12: set mode NTSC 480i 0
[   40.629115] [drm] TV-12: set mode NTSC 480i 0
[   40.985402] [drm] DAC-6: set mode 640x480 0
[   41.090672] [drm] DAC-6: set mode 640x480 0
[   41.160171] i2c-adapter i2c-1: unable to read EDID block.
[   41.160175] i915 0000:00:02.0: LVDS-1: no EDID data
[   41.201312] [drm] TV-12: set mode NTSC 480i 0
[   41.342627] [drm] TV-12: set mode NTSC 480i 0
[ 1282.940092] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 1283.074561] usb 1-4: configuration #1 chosen from 1 choice
[ 1283.155662] Initializing USB Mass Storage driver...
[ 1283.155774] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1283.155924] usbcore: registered new interface driver usb-storage
[ 1283.155928] USB Mass Storage support registered.
[ 1283.156460] usb-storage: device found at 2
[ 1283.156462] usb-storage: waiting for device to settle before scanning
[ 1288.156239] usb-storage: device scan complete
[ 1288.156978] scsi 2:0:0:0: Direct-Access     Flash    LUXIO_USB2.0     8.20 PQ: 0 ANSI: 2
[ 1288.157776] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1288.180455] sd 2:0:0:0: [sdb] 65478656 512-byte logical blocks: (33.5 GB/31.2 GiB)
[ 1288.184224] sd 2:0:0:0: [sdb] Write Protect is off
[ 1288.184228] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1288.184230] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1288.191885] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1288.191891]  sdb: sdb1
[ 1288.819223] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1288.819234] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1612.850901] usb 1-4: USB disconnect, address 2



```


sudo lshw -C network:

```
*-network                         
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation                            
       physical id: 0                                          
       bus info: pci@0000:02:00.0                              
       logical name: eth0                                      
       version: 11
       serial: 00:10:c6:ce:c1:93
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751m-v3.46a ip=192.168.105.137 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:16 memory:90100000-9010ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:79:74:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:21 memory:90301000-90301fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

vboxnet0  Interface doesn't support scanning.


```

lsb_release -d:

```
iwlist: unknown command `wlan0' (check 'iwlist --help').
alex@alext43:~$ lsb_release -d
Description:    Ubuntu 9.10
```

uname -mr:

```
2.6.31-15-generic i686

```

sudo /etc/init.d/networking restart:
```


 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1566
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:c6:ce:c1:93
Sending on   LPF/eth0/00:10:c6:ce:c1:93
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.105.105 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 2131
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:79:74:0e
Sending on   LPF/eth1/00:13:ce:79:74:0e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.105.105 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]
```

iwlist scan wlan0:
```
iwlist: unknown command `wlan0' (check 'iwlist --help').

```

lsmod | grep "wlan_module_name":

(I received no output from the above command)..

If you guys need anything else plz let me know. Thanks.

---

### Post by killabee44 on 2009-11-28
I am wondering why WICD does not see the wireless network at all..

I was digging around the same area where the file I adjusted in order to get network manager to see the wireless was located and found a wicd folder.

It is located in: /etc/wicd

There are three files inside. Their names and contents are: 


manager-settings.conf

```
[Settings]
wireless_interface = wlan0
pref_width = 426
window_width = 512
prefer_wired = False
flush_tool = 0
backend = external
global_dns_dom = None
always_show_wired_interface = False
sudo_app = 0
global_dns_1 = None
global_dns_2 = None
global_dns_3 = None
use_global_dns = False
link_detect_tool = 0
dhcp_client = 0
window_height = 451
wired_connect_mode = 1
debug_mode = 0
pref_height = 384
wired_interface = eth0
signal_display_type = 0
global_search_dom = None
auto_reconnect = True
wpa_driver = wext

```


wired-settings.conf
```

[wired-default]
afterscript = None
broadcast = None
dns3 = None
postdisconnectscript = None
search_domain = None
dns_domain = None
lastused = True
use_static_dns = False
default = 1
netmask = None
gateway = None
dns2 = None
beforescript = None
predisconnectscript = None
ip = None
dns1 = None
use_global_dns = False

[wired]
afterscript = None
broadcast = None
dns3 = None
dns2 = None
search_domain = None
dns_domain = None
lastused = False
use_static_dns = False
default = 0
netmask = None
gateway = None
postdisconnectscript = None
beforescript = None
predisconnectscript = None
ip = None
dns1 = None
use_global_dns = False
```


And, Wireless-settings.conf, but that one is empty. There must be the problem. It should not be empty maybe? Hopefully someone knows wicd configs and can shed some light..

---

### Post by killabee44 on 2009-11-28
Ok, I figured it out.. It turned out to be something easy. In the Wicd controll panel gui I needed to change the setting under wireless to eth1. 

I can't remember what it had before, but that is why it wouldn't see any of the networks.

:)

---

### Post by Bucky Ball on 2009-11-28
You don't have wlan0?

You may have also discovered this. Wicd removes Network Manager but I don't think Network Manager removes wicd if then reinstall and both won't exist functionally on the same machine. One or the other, not both. Consequently, to use Network Manager again I think you would need to manually uninstall wicd. 

Just a thought ...

And this:

[http://hardware4linux.info/component/13902/](http://hardware4linux.info/component/13902/)

... and this:

[http://hardware4linux.info/module/tg3/](http://hardware4linux.info/module/tg3/)

---

### Post by killabee44 on 2009-11-28
No wlan0. It seems that this laptop sees the wired network as eth0 and wireless as eth1.

---

