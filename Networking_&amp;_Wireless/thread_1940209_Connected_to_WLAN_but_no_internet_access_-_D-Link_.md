---
title: "Connected to WLAN but no internet access - D-Link  DWA-131 adapter on Ubuntu 11.10"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by mndmdvrantm on 2012-03-13
I recently (two days ago) installed Ubuntu 11.10, and I now dual-boot alongside Windows 7.  I've had a perfectly fine internet connection up until now. When I opened firefox today, I couldn't reach any websites -- firefox kept loading and loading and would, after a while, determine that the server could not be found. Pidgin would not sign in and screenshots and reviews in Ubuntu Software Center similarly would not load. I checked my network settings and noticed that I was still connected to my wireless network. I booted into Windows 7 and found I could connect to the wireless network and retain internet connectivity.

Here's all the data that I'm supposed to provide you with (according to [http://ubuntuforums.org/showthread.php?t=982880](http://ubuntuforums.org/showthread.php?t=982880) anyway). I've tried to gather only the relevant information to the best of my ability.

 4x Intel Core2 Quad CPU Q8200 @ 2.33GHz
  4121MB/4GB RAM
  
** lspci:**
 ```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```**lsusb:**
 ```
Bus 001 Device 003: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
```**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:31:e0:e4  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:43 Base address:0x2000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:148 errors:0 dropped:0 overruns:0 frame:0
            TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:11760 (11.7 KB)  TX bytes:11760 (11.7 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:26:5a:ee:60:ef  
            inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
            inet6 addr: fe80::226:5aff:feee:60ef/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:1212 errors:0 dropped:70 overruns:0 frame:0
            TX packets:3825 errors:0 dropped:1 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:534558 (534.5 KB)  TX bytes:2796822697 (2.7 GB)

```**iwconfig wlan0:**
```
wlan0     IEEE 802.11bgn  ESSID:"fourthirtynine"  Nickname:"rtl_wifi"
            Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:A3:88:C2   
            Bit Rate:300 Mb/s   Sensitivity:0/0  
            Retry:off   RTS thr:off   Fragment thr:off
            Power Management:off
            Link Quality=87/100  Signal level=70/100  Noise level=0/100
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```**lsmod:**
```
Module                  Size  Used by
  nls_iso8859_1          12617  1 
  nls_cp437              12751  1 
  vfat                   17308  1 
  fat                    55577  1 vfat
  rfcomm                 38408  0 
  bnep                   17923  2 
  bluetooth             148839  10 rfcomm,bnep
  pci_stub               12550  1 
  vboxpci                22882  0 
  vboxnetadp             13328  0 
  vboxnetflt             27211  0 
  vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
  binfmt_misc            17292  1 
  vesafb                 13489  1 
  nvidia              10390874  40 
  joydev                 17393  0 
  snd_usb_audio         100930  1 
  snd_usbmidi_lib        24558  1 snd_usb_audio
  gspca_sonixj           32391  0 
  gspca_main             27610  1 gspca_sonixj
  videodev               85626  1 gspca_main
  hid_microsoft          12728  0 
  ppdev                  12849  0 
  r8712u                163310  0 
  usbhid                 41905  0 
  hid                    77367  2 hid_microsoft,usbhid
  snd_hda_codec_realtek   254163  1 
  snd_hda_intel          28358  2 
  snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
  snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
  snd_pcm                80435  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
  snd_seq_midi           13132  0 
  snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
  parport_pc             32114  1 
  snd_seq_midi_event     14475  1 snd_seq_midi
  snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
  psmouse                63474  0 
  serio_raw              12990  0 
  snd_timer              28932  2 snd_pcm,snd_seq
  snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
  snd                    55902  17 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  soundcore              12600  1 snd
  snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
  lp                     17455  0 
  parport                40930  3 ppdev,parport_pc,lp
  usb_storage            44173  2 
  uas                    17699  0 
  r8169                  47200  0 

```**sudo lshw -C network:**
```
*-network               
         description: Ethernet interface
         product: RTL8111/8168B PCI Express Gigabit Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:03:00.0
         logical name: eth0
         version: 02
         serial: 00:24:1d:31:e0:e4
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:43 ioport:d000(size=256) memory:e5010000-e5010fff memory:e5000000-e500ffff memory:e5020000-e502ffff
    *-network
         description: Wireless interface
         physical id: 1
         bus info: usb@1:2
         logical name: wlan0
         serial: 00:26:5a:ee:60:ef
         capabilities: ethernet physical wireless
         configuration: broadcast=yes driver=r8712u ip=192.168.1.3 multicast=yes wireless=IEEE 802.11bgn

```**iwlist scan:**
```
lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Scan completed :
            Cell 01 - Address: 00:22:3F:A3:88:C2
                      ESSID:"fourthirtynine"
                      Protocol:IEEE 802.11bgn
                      Mode:Master
                      Frequency:2.462 GHz (Channel 11)
                      Encryption key:on
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                      Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : CCMP
                          Pairwise Ciphers (1) : CCMP
                          Authentication Suites (1) : PSK
                      IE: Unknown: DD0E0050F204104A0001101044000102
                      Signal level=100/100  

```**lsb_release -d:**
 ```
Description:          Ubuntu 11.10
```    **uname -mr:**
  
```
3.0.0-16-generic-pae i686
```**sudo /etc/init.d/networking restart:**```

  
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
   * Reconfiguring network interfaces...                                                             [ OK ] 

```

---

### Post by mndmdvrantm on 2012-03-13
Completely forgot about **dmesg:**
```
[    0.000000] Initializing cgroup subsys cpuset 
 [    0.000000] Initializing cgroup subsys cpu 
 [    0.000000] Linux version 3.0.0-16-generic-pae (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 (Ubuntu 3.0.0-16.29-generic-pae 3.0.20) 
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
 [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
 [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable) 
 [    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS) 
 [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data) 
 [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved) 
 [    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved) 
 [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved) 
 [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable) 
 [    0.000000] NX (Execute Disable) protection: active 
 [    0.000000] DMI 2.4 present. 
 [    0.000000] DMI: Gigabyte Technology Co., Ltd. G31M-ES2L/G31M-S2L, BIOS F7 01/15/2009 
 [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved) 
 [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable) 
 [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000 
 [    0.000000] MTRR default type: uncachable 
 [    0.000000] MTRR fixed ranges enabled: 
 [    0.000000]   00000-9FFFF write-back 
 [    0.000000]   A0000-BFFFF uncachable 
 [    0.000000]   C0000-CCFFF write-protect 
 [    0.000000]   CD000-EFFFF uncachable 
 [    0.000000]   F0000-FFFFF write-through 
 [    0.000000] MTRR variable ranges enabled: 
 [    0.000000]   0 base 000000000 mask F00000000 write-back 
 [    0.000000]   1 base 0C0000000 mask FC0000000 uncachable 
 [    0.000000]   2 base 100000000 mask FC0000000 write-back 
 [    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable 
 [    0.000000]   4 disabled 
 [    0.000000]   5 disabled 
 [    0.000000]   6 disabled 
 [    0.000000]   7 disabled 
 [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
 [    0.000000] original variable MTRRs 
 [    0.000000] reg 0, base: 0GB, range: 4GB, type WB 
 [    0.000000] reg 1, base: 3GB, range: 1GB, type UC 
 [    0.000000] reg 2, base: 4GB, range: 1GB, type WB 
 [    0.000000] reg 3, base: 3071MB, range: 1MB, type UC 
 [    0.000000] total RAM covered: 4095M 
 [    0.000000] Found optimal setting for mtrr clean up 
 [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 4      lose cover RAM: 0G 
 [    0.000000] New variable MTRRs 
 [    0.000000] reg 0, base: 0GB, range: 2GB, type WB 
 [    0.000000] reg 1, base: 2GB, range: 1GB, type WB 
 [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC 
 [    0.000000] reg 3, base: 4GB, range: 1GB, type WB 
 [    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved) 
 [    0.000000] found SMP MP-table at [c00f5200] f5200 
 [    0.000000] initial memory mapped : 0 - 02000000 
 [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384 
 [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000 
 [    0.000000]  0000000000 - 0000200000 page 4k 
 [    0.000000]  0000200000 - 0037a00000 page 2M 
 [    0.000000]  0037a00000 - 0037bfe000 page 4k 
 [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000 
 [    0.000000] RAMDISK: 365f2000 - 372f1000 
 [    0.000000] ACPI: RSDP 000f6bf0 00014 (v00 GBT   ) 
 [    0.000000] ACPI: RSDT bfee3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101) 
 [    0.000000] ACPI: FACP bfee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101) 
 [    0.000000] ACPI: DSDT bfee3180 040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C) 
 [    0.000000] ACPI: FACS bfee0000 00040 
 [    0.000000] ACPI: HPET bfee73c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098) 
 [    0.000000] ACPI: MCFG bfee7440 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101) 
 [    0.000000] ACPI: APIC bfee72c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101) 
 [    0.000000] ACPI: SSDT bfee7da0 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311) 
 [    0.000000] ACPI: Local APIC address 0xfee00000 
 [    0.000000] 4228MB HIGHMEM available. 
 [    0.000000] 891MB LOWMEM available. 
 [    0.000000]   mapped low ram: 0 - 37bfe000 
 [    0.000000]   low ram: 0 - 37bfe000 
 [    0.000000] Zone PFN ranges: 
 [    0.000000]   DMA      0x00000010 -> 0x00001000 
 [    0.000000]   Normal   0x00001000 -> 0x00037bfe 
 [    0.000000]   HighMem  0x00037bfe -> 0x00140000 
 [    0.000000] Movable zone start PFN for each node 
 [    0.000000] early_node_map[3] active PFN ranges 
 [    0.000000]     0: 0x00000010 -> 0x0000009f 
 [    0.000000]     0: 0x00000100 -> 0x000bfee0 
 [    0.000000]     0: 0x00100000 -> 0x00140000 
 [    0.000000] On node 0 totalpages: 1048175 
 [    0.000000] free_area_init_node: node 0, pgdat c17f6500, node_mem_map f3df2200 
 [    0.000000]   DMA zone: 32 pages used for memmap 
 [    0.000000]   DMA zone: 0 pages reserved 
 [    0.000000]   DMA zone: 3951 pages, LIFO batch:0 
 [    0.000000]   Normal zone: 1752 pages used for memmap 
 [    0.000000]   Normal zone: 222502 pages, LIFO batch:31 
 [    0.000000]   HighMem zone: 8457 pages used for memmap 
 [    0.000000]   HighMem zone: 811481 pages, LIFO batch:31 
 [    0.000000] Using APIC driver default 
 [    0.000000] ACPI: PM-Timer IO Port: 0x408 
 [    0.000000] ACPI: Local APIC address 0xfee00000 
 [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
 [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled) 
 [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled) 
 [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled) 
 [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1]) 
 [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
 [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
 [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1]) 
 [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
 [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23 
 [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
 [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
 [    0.000000] ACPI: IRQ0 used by override. 
 [    0.000000] ACPI: IRQ2 used by override. 
 [    0.000000] ACPI: IRQ9 used by override. 
 [    0.000000] Using ACPI (MADT) for SMP configuration information 
 [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
 [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs 
 [    0.000000] nr_irqs_gsi: 40 
 [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000 
 [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000 
 [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000 
 [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000) 
 [    0.000000] Booting paravirtualized kernel on bare hardware 
 [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1 
 [    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u524288 
 [    0.000000] pcpu-alloc: s29952 r0 d23296 u524288 alloc=1*2097152 
 [    0.000000] pcpu-alloc: [0] 0 1 2 3  
 [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1037934 
 [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=40fbd1ea-0731-4278-b305-3d117486dc25 ro quiet splash vt.handoff=7 
 [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes) 
 [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
 [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
 [    0.000000] Initializing CPU#0 
 [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240 
 [    0.000000] allocated 20971264 bytes of page_cgroup 
 [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups 
 [    0.000000] Initializing HighMem for node 0 (00037bfe:00140000) 
 [    0.000000] Memory: 4106988k/5242880k available (5527k kernel code, 85712k reserved, 2670k data, 720k init, 3279752k highmem) 
 [    0.000000] virtual kernel memory layout: 
 [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB) 
 [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB) 
 [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB) 
 [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB) 
 [    0.000000]       .init : 0xc1802000 - 0xc18b6000   ( 720 kB) 
 [    0.000000]       .data : 0xc1565ebc - 0xc1801880   (2670 kB) 
 [    0.000000]       .text : 0xc1000000 - 0xc1565ebc   (5527 kB) 
 [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok. 
 [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1 
 [    0.000000] Hierarchical RCU implementation. 
 [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled. 
 [    0.000000] NR_IRQS:2304 nr_irqs:712 16 
 [    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000 
 [    0.000000] vt handoff: transparent VT on vt#7 
 [    0.000000] Console: colour dummy device 80x25 
 [    0.000000] console [tty0] enabled 
 [    0.000000] hpet clockevent registered 
 [    0.000000] Fast TSC calibration using PIT 
 [    0.000000] Detected 2333.632 MHz processor. 
 [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4667.26 BogoMIPS (lpj=9334528) 
 [    0.004007] pid_max: default: 32768 minimum: 301 
 [    0.004028] Security Framework initialized 
 [    0.004041] AppArmor: AppArmor initialized 
 [    0.004042] Yama: becoming mindful. 
 [    0.004092] Mount-cache hash table entries: 512 
 [    0.004208] Initializing cgroup subsys cpuacct 
 [    0.004214] Initializing cgroup subsys memory 
 [    0.004221] Initializing cgroup subsys devices 
 [    0.004223] Initializing cgroup subsys freezer 
 [    0.004225] Initializing cgroup subsys net_cls 
 [    0.004227] Initializing cgroup subsys blkio 
 [    0.004233] Initializing cgroup subsys perf_event 
 [    0.004262] CPU: Physical Processor ID: 0 
 [    0.004264] CPU: Processor Core ID: 0 
 [    0.004266] mce: CPU supports 6 MCE banks 
 [    0.004274] CPU0: Thermal monitoring enabled (TM2) 
 [    0.004277] using mwait in idle threads. 
 [    0.008190] ACPI: Core revision 20110413 
 [    0.011487] ftrace: allocating 25674 entries in 51 pages 
 [    0.012044] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
 [    0.012393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
 [    0.053898] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a 
 [    0.056003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver. 
 [    0.056003] ... version:                2 
 [    0.056003] ... bit width:              40 
 [    0.056003] ... generic registers:      2 
 [    0.056003] ... value mask:             000000ffffffffff 
 [    0.056003] ... max period:             000000007fffffff 
 [    0.056003] ... fixed-purpose events:   3 
 [    0.056003] ... event mask:             0000000700000003 
 [    0.056003] CPU 1 irqstacks, hard=f74ac000 soft=f74ae000 
 [    0.056003] Booting Node   0, Processors  #1 
 [    0.056003] smpboot cpu 1: start_ip = 9b000 
 [    0.008000] Initializing CPU#1 
 [    0.144100] CPU 2 irqstacks, hard=f74e0000 soft=f74e2000 
 [    0.144103]  #2 
 [    0.144104] smpboot cpu 2: start_ip = 9b000 
 [    0.008000] Initializing CPU#2 
 [    0.236083] CPU 3 irqstacks, hard=f74ec000 soft=f74ee000 
 [    0.236085]  #3 Ok. 
 [    0.236087] smpboot cpu 3: start_ip = 9b000 
 [    0.008000] Initializing CPU#3 
 [    0.328026] Brought up 4 CPUs 
 [    0.328029] Total of 4 processors activated (18667.20 BogoMIPS). 
 [    0.329966] devtmpfs: initialized 
 [    0.329966] PM: Registering ACPI NVS region at bfee0000 (12288 bytes) 
 [    0.332268] print_constraints: dummy:  
 [    0.332291] Time: 21:23:48  Date: 03/13/12 
 [    0.332327] NET: Registered protocol family 16 
 [    0.332336] Trying to unpack rootfs image as initramfs... 
 [    0.332447] EISA bus registered 
 [    0.332473] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it 
 [    0.332476] ACPI: bus type pci registered 
 [    0.332533] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xc0000000-0xcfffffff] (base 0xc0000000) 
 [    0.332536] PCI: MMCONFIG at [mem 0xc0000000-0xcfffffff] reserved in E820 
 [    0.332538] PCI: Using MMCONFIG for extended config space 
 [    0.332540] PCI: Using configuration type 1 for base access 
 [    0.333474] bio: create slab <bio-0> at 0 
 [    0.333474] ACPI: EC: Look up EC in DSDT 
 [    0.338200] ACPI: SSDT bfee74c0 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311) 
 [    0.338399] ACPI: Dynamic OEM Table Load: 
 [    0.338402] ACPI: SSDT   (null) 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311) 
 [    0.338536] ACPI: SSDT bfee7980 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311) 
 [    0.338725] ACPI: Dynamic OEM Table Load: 
 [    0.338728] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311) 
 [    0.338863] ACPI: SSDT bfee7ae0 00152 (v01  PmRef  Cpu2Ist 00003000 INTL 20040311) 
 [    0.339052] ACPI: Dynamic OEM Table Load: 
 [    0.339055] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu2Ist 00003000 INTL 20040311) 
 [    0.339189] ACPI: SSDT bfee7c40 00152 (v01  PmRef  Cpu3Ist 00003000 INTL 20040311) 
 [    0.339379] ACPI: Dynamic OEM Table Load: 
 [    0.339382] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu3Ist 00003000 INTL 20040311) 
 [    0.339520] ACPI: Interpreter enabled 
 [    0.339530] ACPI: (supports S0 S3 S4 S5) 
 [    0.339549] ACPI: Using IOAPIC for interrupt routing 
 [    0.343417] ACPI: No dock devices found. 
 [    0.343420] HEST: Table not found. 
 [    0.343425] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug 
 [    0.343476] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff]) 
 [    0.343586] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] 
 [    0.343589] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] 
 [    0.343591] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] 
 [    0.343594] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] 
 [    0.343596] pci_root PNP0A03:00: host bridge window [mem 0xbff00000-0xfebfffff] 
 [    0.343609] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600 
 [    0.343650] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604 
 [    0.343688] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold 
 [    0.343691] pci 0000:00:01.0: PME# disabled 
 [    0.343730] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403 
 [    0.343744] pci 0000:00:1b.0: reg 10: [mem 0xe5100000-0xe5103fff 64bit] 
 [    0.343808] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
 [    0.343811] pci 0000:00:1b.0: PME# disabled 
 [    0.343829] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604 
 [    0.343892] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
 [    0.343895] pci 0000:00:1c.0: PME# disabled 
 [    0.343914] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604 
 [    0.343977] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
 [    0.343981] pci 0000:00:1c.1: PME# disabled 
 [    0.344002] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03 
 [    0.344057] pci 0000:00:1d.0: reg 20: [io  0xe000-0xe01f] 
 [    0.344085] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03 
 [    0.344132] pci 0000:00:1d.1: reg 20: [io  0xe100-0xe11f] 
 [    0.344160] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03 
 [    0.344206] pci 0000:00:1d.2: reg 20: [io  0xe200-0xe21f] 
 [    0.344234] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03 
 [    0.344270] pci 0000:00:1d.3: reg 20: [io  0xe300-0xe31f] 
 [    0.344304] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03 
 [    0.344320] pci 0000:00:1d.7: reg 10: [mem 0xe5104000-0xe51043ff] 
 [    0.344401] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604 
 [    0.344458] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601 
 [    0.344534] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f) 
 [    0.344537] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f) 
 [    0.344581] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101 
 [    0.344594] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007] 
 [    0.344601] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003] 
 [    0.344609] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007] 
 [    0.344617] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003] 
 [    0.344625] pci 0000:00:1f.2: reg 20: [io  0xf000-0xf00f] 
 [    0.344657] pci 0000:00:1f.2: PME# supported from D3hot 
 [    0.344660] pci 0000:00:1f.2: PME# disabled 
 [    0.344672] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05 
 [    0.344719] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f] 
 [    0.344783] pci 0000:01:00.0: [10de:0622] type 0 class 0x000300 
 [    0.344794] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff] 
 [    0.344804] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref] 
 [    0.344815] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit] 
 [    0.344822] pci 0000:01:00.0: reg 24: [io  0xc000-0xc07f] 
 [    0.344829] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref] 
 [    0.344885] pci 0000:00:01.0: PCI bridge to [bus 01-01] 
 [    0.344888] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff] 
 [    0.344891] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe3ffffff] 
 [    0.344895] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref] 
 [    0.344932] pci 0000:00:1c.0: PCI bridge to [bus 02-02] 
 [    0.344936] pci 0000:00:1c.0:   bridge window [io  0xb000-0xbfff] 
 [    0.344940] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled) 
 [    0.344946] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled) 
 [    0.344998] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200 
 [    0.345014] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff] 
 [    0.345041] pci 0000:03:00.0: reg 18: [mem 0xe5010000-0xe5010fff 64bit pref] 
 [    0.345058] pci 0000:03:00.0: reg 20: [mem 0xe5000000-0xe500ffff 64bit pref] 
 [    0.345070] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0000ffff pref] 
 [    0.345132] pci 0000:03:00.0: supports D1 D2 
 [    0.345134] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
 [    0.345139] pci 0000:03:00.0: PME# disabled 
 [    0.352041] pci 0000:00:1c.1: PCI bridge to [bus 03-03] 
 [    0.352046] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff] 
 [    0.352050] pci 0000:00:1c.1:   bridge window [mem 0xe4000000-0xe4ffffff] 
 [    0.352055] pci 0000:00:1c.1:   bridge window [mem 0xe5000000-0xe50fffff 64bit pref] 
 [    0.352119] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode) 
 [    0.352128] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff] 
 [    0.352131] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled) 
 [    0.352137] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled) 
 [    0.352140] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode) 
 [    0.352142] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode) 
 [    0.352145] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode) 
 [    0.352148] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode) 
 [    0.352150] pci 0000:00:1e.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode) 
 [    0.352166] pci_bus 0000:00: on NUMA node 0 
 [    0.352174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
 [    0.352353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT] 
 [    0.352396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT] 
 [    0.352446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT] 
 [    0.352546]  pci0000:00: Requesting ACPI _OSC control (0x1d) 
 [    0.352549]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d 
 [    0.352551] ACPI _OSC control for PCIe not granted, disabling ASPM 
 [    0.359457] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
 [    0.359505] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
 [    0.359551] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
 [    0.359597] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
 [    0.359644] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
 [    0.359691] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
 [    0.359738] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
 [    0.359785] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
 [    0.359900] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none 
 [    0.359903] vgaarb: loaded 
 [    0.359904] vgaarb: bridge control possible 0000:01:00.0 
 [    0.360131] SCSI subsystem initialized 
 [    0.360177] libata version 3.00 loaded. 
 [    0.360177] usbcore: registered new interface driver usbfs 
 [    0.360177] usbcore: registered new interface driver hub 
 [    0.360177] usbcore: registered new device driver usb 
 [    0.360177] PCI: Using ACPI for IRQ routing 
 [    0.365842] PCI: pci_cache_line_size set to 64 bytes 
 [    0.365903] reserve RAM buffer: 000000000009f800 - 000000000009ffff  
 [    0.365906] reserve RAM buffer: 00000000bfee0000 - 00000000bfffffff  
 [    0.366003] NetLabel: Initializing 
 [    0.366005] NetLabel:  domain hash size = 128 
 [    0.366006] NetLabel:  protocols = UNLABELED CIPSOv4 
 [    0.366017] NetLabel:  unlabeled traffic allowed by default 
 [    0.366059] HPET: 3 timers in total, 0 timers will be used for per-cpu timer 
 [    0.366063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
 [    0.366068] hpet0: 3 comparators, 64-bit 14.318180 MHz counter 
 [    0.380049] Switching to clocksource hpet 
 [    0.383788] Switched to NOHz mode on CPU #0 
 [    0.383875] Switched to NOHz mode on CPU #1 
 [    0.383878] Switched to NOHz mode on CPU #2 
 [    0.383935] Switched to NOHz mode on CPU #3 
 [    0.387180] AppArmor: AppArmor Filesystem Enabled 
 [    0.387212] pnp: PnP ACPI init 
 [    0.387228] ACPI: bus type pnp registered 
 [    0.387317] pnp 00:00: [bus 00-ff] 
 [    0.387320] pnp 00:00: [io  0x0cf8-0x0cff] 
 [    0.387322] pnp 00:00: [io  0x0000-0x0cf7 window] 
 [    0.387325] pnp 00:00: [io  0x0d00-0xffff window] 
 [    0.387327] pnp 00:00: [mem 0x000a0000-0x000bffff window] 
 [    0.387329] pnp 00:00: [mem 0x000c0000-0x000dffff window] 
 [    0.387332] pnp 00:00: [mem 0xbff00000-0xfebfffff window] 
 [    0.387387] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active) 
 [    0.387449] pnp 00:01: [io  0x0010-0x001f] 
 [    0.387452] pnp 00:01: [io  0x0022-0x003f] 
 [    0.387453] pnp 00:01: [io  0x0044-0x005f] 
 [    0.387455] pnp 00:01: [io  0x0062-0x0063] 
 [    0.387457] pnp 00:01: [io  0x0065-0x006f] 
 [    0.387459] pnp 00:01: [io  0x0074-0x007f] 
 [    0.387461] pnp 00:01: [io  0x0091-0x0093] 
 [    0.387463] pnp 00:01: [io  0x00a2-0x00bf] 
 [    0.387465] pnp 00:01: [io  0x00e0-0x00ef] 
 [    0.387466] pnp 00:01: [io  0x04d0-0x04d1] 
 [    0.387468] pnp 00:01: [io  0x0290-0x029f] 
 [    0.387470] pnp 00:01: [io  0x0800-0x087f] 
 [    0.387472] pnp 00:01: [io  0x0290-0x0294] 
 [    0.387474] pnp 00:01: [io  0x0880-0x088f] 
 [    0.387533] system 00:01: [io  0x04d0-0x04d1] has been reserved 
 [    0.387536] system 00:01: [io  0x0290-0x029f] has been reserved 
 [    0.387538] system 00:01: [io  0x0800-0x087f] has been reserved 
 [    0.387541] system 00:01: [io  0x0290-0x0294] has been reserved 
 [    0.387544] system 00:01: [io  0x0880-0x088f] has been reserved 
 [    0.387547] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active) 
 [    0.387559] pnp 00:02: [dma 4] 
 [    0.387561] pnp 00:02: [io  0x0000-0x000f] 
 [    0.387563] pnp 00:02: [io  0x0080-0x0090] 
 [    0.387565] pnp 00:02: [io  0x0094-0x009f] 
 [    0.387567] pnp 00:02: [io  0x00c0-0x00df] 
 [    0.387595] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active) 
 [    0.387642] pnp 00:03: [irq 0 disabled] 
 [    0.387652] pnp 00:03: [irq 8] 
 [    0.387654] pnp 00:03: [mem 0xfed00000-0xfed003ff] 
 [    0.387681] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active) 
 [    0.387707] pnp 00:04: [io  0x0070-0x0073] 
 [    0.387734] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active) 
 [    0.387743] pnp 00:05: [io  0x0061] 
 [    0.387769] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active) 
 [    0.387778] pnp 00:06: [io  0x00f0-0x00ff] 
 [    0.387783] pnp 00:06: [irq 13] 
 [    0.387813] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active) 
 [    0.388048] pnp 00:07: [io  0x03f8-0x03ff] 
 [    0.388054] pnp 00:07: [irq 4] 
 [    0.388111] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active) 
 [    0.388280] pnp 00:08: [io  0x0378-0x037f] 
 [    0.388285] pnp 00:08: [irq 7] 
 [    0.388331] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active) 
 [    0.388438] pnp 00:09: [io  0x0400-0x04cf] 
 [    0.388482] system 00:09: [io  0x0400-0x04cf] has been reserved 
 [    0.388485] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active) 
 [    0.388671] pnp 00:0a: [mem 0xc0000000-0xcfffffff] 
 [    0.388728] system 00:0a: [mem 0xc0000000-0xcfffffff] has been reserved 
 [    0.388731] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active) 
 [    0.388878] pnp 00:0b: [mem 0x000cde00-0x000cffff] 
 [    0.388880] pnp 00:0b: [mem 0x000f0000-0x000f7fff] 
 [    0.388882] pnp 00:0b: [mem 0x000f8000-0x000fbfff] 
 [    0.388884] pnp 00:0b: [mem 0x000fc000-0x000fffff] 
 [    0.388889] pnp 00:0b: [mem 0xbfee0000-0xbfefffff] 
 [    0.388891] pnp 00:0b: [mem 0x00000000-0x0009ffff] 
 [    0.388893] pnp 00:0b: [mem 0x00100000-0xbfedffff] 
 [    0.388895] pnp 00:0b: [mem 0xfec00000-0xfec00fff] 
 [    0.388897] pnp 00:0b: [mem 0xfed13000-0xfed1dfff] 
 [    0.388899] pnp 00:0b: [mem 0xfed20000-0xfed8ffff] 
 [    0.388901] pnp 00:0b: [mem 0xfee00000-0xfee00fff] 
 [    0.388903] pnp 00:0b: [mem 0xffb00000-0xffb7ffff] 
 [    0.388905] pnp 00:0b: [mem 0xfff00000-0xffffffff] 
 [    0.388907] pnp 00:0b: [mem 0x000e0000-0x000effff] 
 [    0.388967] system 00:0b: [mem 0x000cde00-0x000cffff] has been reserved 
 [    0.388970] system 00:0b: [mem 0x000f0000-0x000f7fff] could not be reserved 
 [    0.388973] system 00:0b: [mem 0x000f8000-0x000fbfff] could not be reserved 
 [    0.388975] system 00:0b: [mem 0x000fc000-0x000fffff] could not be reserved 
 [    0.388978] system 00:0b: [mem 0xbfee0000-0xbfefffff] could not be reserved 
 [    0.388981] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved 
 [    0.388983] system 00:0b: [mem 0x00100000-0xbfedffff] could not be reserved 
 [    0.388986] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved 
 [    0.388989] system 00:0b: [mem 0xfed13000-0xfed1dfff] has been reserved 
 [    0.388991] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved 
 [    0.388994] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved 
 [    0.388997] system 00:0b: [mem 0xffb00000-0xffb7ffff] has been reserved 
 [    0.389000] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved 
 [    0.389002] system 00:0b: [mem 0x000e0000-0x000effff] has been reserved 
 [    0.389006] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active) 
 [    0.389025] pnp 00:0c: [mem 0xffb80000-0xffbfffff] 
 [    0.389065] pnp 00:0c: Plug and Play ACPI device, IDs INT0800 (active) 
 [    0.389071] pnp: PnP ACPI: found 13 devices 
 [    0.389072] ACPI: ACPI bus type pnp unregistered 
 [    0.389076] PnPBIOS: Disabled by ACPI PNP 
 [    0.425102] PCI: max bus depth: 1 pci_try_num: 2 
 [    0.425142] pci 0000:00:1c.0: BAR 14: assigned [mem 0xe5200000-0xe53fffff] 
 [    0.425147] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe5400000-0xe55fffff 64bit pref] 
 [    0.425152] pci 0000:01:00.0: BAR 6: assigned [mem 0xe3000000-0xe307ffff pref] 
 [    0.425155] pci 0000:00:01.0: PCI bridge to [bus 01-01] 
 [    0.425158] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff] 
 [    0.425161] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe3ffffff] 
 [    0.425165] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref] 
 [    0.425169] pci 0000:00:1c.0: PCI bridge to [bus 02-02] 
 [    0.425172] pci 0000:00:1c.0:   bridge window [io  0xb000-0xbfff] 
 [    0.425177] pci 0000:00:1c.0:   bridge window [mem 0xe5200000-0xe53fffff] 
 [    0.425181] pci 0000:00:1c.0:   bridge window [mem 0xe5400000-0xe55fffff 64bit pref] 
 [    0.425187] pci 0000:03:00.0: BAR 6: assigned [mem 0xe5020000-0xe502ffff pref] 
 [    0.425190] pci 0000:00:1c.1: PCI bridge to [bus 03-03] 
 [    0.425193] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff] 
 [    0.425197] pci 0000:00:1c.1:   bridge window [mem 0xe4000000-0xe4ffffff] 
 [    0.425201] pci 0000:00:1c.1:   bridge window [mem 0xe5000000-0xe50fffff 64bit pref] 
 [    0.425206] pci 0000:00:1e.0: PCI bridge to [bus 04-04] 
 [    0.425209] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff] 
 [    0.425213] pci 0000:00:1e.0:   bridge window [mem disabled] 
 [    0.425217] pci 0000:00:1e.0:   bridge window [mem pref disabled] 
 [    0.425237] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    0.425241] pci 0000:00:01.0: setting latency timer to 64 
 [    0.425248] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    0.425252] pci 0000:00:1c.0: setting latency timer to 64 
 [    0.425261] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
 [    0.425265] pci 0000:00:1c.1: setting latency timer to 64 
 [    0.425271] pci 0000:00:1e.0: setting latency timer to 64 
 [    0.425274] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7] 
 [    0.425276] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff] 
 [    0.425279] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff] 
 [    0.425281] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff] 
 [    0.425283] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff] 
 [    0.425286] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff] 
 [    0.425288] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe3ffffff] 
 [    0.425290] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref] 
 [    0.425293] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff] 
 [    0.425295] pci_bus 0000:02: resource 1 [mem 0xe5200000-0xe53fffff] 
 [    0.425297] pci_bus 0000:02: resource 2 [mem 0xe5400000-0xe55fffff 64bit pref] 
 [    0.425300] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff] 
 [    0.425302] pci_bus 0000:03: resource 1 [mem 0xe4000000-0xe4ffffff] 
 [    0.425305] pci_bus 0000:03: resource 2 [mem 0xe5000000-0xe50fffff 64bit pref] 
 [    0.425307] pci_bus 0000:04: resource 0 [io  0xa000-0xafff] 
 [    0.425310] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7] 
 [    0.425312] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff] 
 [    0.425314] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff] 
 [    0.425316] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff] 
 [    0.425319] pci_bus 0000:04: resource 8 [mem 0xbff00000-0xfebfffff] 
 [    0.425356] NET: Registered protocol family 2 
 [    0.425430] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
 [    0.425648] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
 [    0.425996] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
 [    0.426168] TCP: Hash tables configured (established 131072 bind 65536) 
 [    0.426170] TCP reno registered 
 [    0.426173] UDP hash table entries: 512 (order: 2, 16384 bytes) 
 [    0.426182] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes) 
 [    0.426274] NET: Registered protocol family 1 
 [    0.426392] pci 0000:01:00.0: Boot video device 
 [    0.426399] PCI: CLS 32 bytes, default 64 
 [    0.426797] audit: initializing netlink socket (disabled) 
 [    0.426806] type=2000 audit(1331673827.420:1): initialized 
 [    0.452044] highmem bounce pool size: 64 pages 
 [    0.452049] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
 [    0.465033] VFS: Disk quotas dquot_6.5.2 
 [    0.465101] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
 [    0.465800] fuse init (API version 7.16) 
 [    0.465890] msgmni has been set to 1615 
 [    0.466445] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
 [    0.466492] io scheduler noop registered 
 [    0.466494] io scheduler deadline registered 
 [    0.466508] io scheduler cfq registered (default) 
 [    0.466606] pcieport 0000:00:01.0: setting latency timer to 64 
 [    0.466635] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X 
 [    0.466676] pcieport 0000:00:1c.0: setting latency timer to 64 
 [    0.466708] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X 
 [    0.466761] pcieport 0000:00:1c.1: setting latency timer to 64 
 [    0.466793] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X 
 [    0.466867] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
 [    0.466889] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
 [    0.466964] intel_idle: MWAIT substates: 0x22220 
 [    0.466966] intel_idle: does not run on family 6 model 23 
 [    0.467035] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 
 [    0.467039] ACPI: Power Button [PWRB] 
 [    0.467088] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 
 [    0.467091] ACPI: Power Button [PWRF] 
 [    0.467116] ACPI: acpi_idle registered with cpuidle 
 [    0.469357] ERST: Table is not found! 
 [    0.469420] isapnp: Scanning for PnP cards... 
 [    0.469454] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled 
 [    0.489785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
 [    0.617651] Freeing initrd memory: 13308k freed 
 [    0.822257] isapnp: No Plug & Play device found 
 [    0.896510] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
 [    0.896750] Linux agpgart interface v0.103 
 [    0.898037] brd: module loaded 
 [    0.898598] loop: module loaded 
 [    0.898747] ata_piix 0000:00:1f.2: version 2.13 
 [    0.898767] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
 [    0.898772] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
 [    0.898800] ata_piix 0000:00:1f.2: setting latency timer to 64 
 [    0.899106] scsi0 : ata_piix 
 [    0.899212] scsi1 : ata_piix 
 [    0.899689] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14 
 [    0.899692] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15 
 [    0.900044] Fixed MDIO Bus: probed 
 [    0.900067] PPP generic driver version 2.4.2 
 [    0.900104] tun: Universal TUN/TAP device driver, 1.6 
 [    0.900106] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
 [    0.900192] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
 [    0.900211] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
 [    0.900222] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
 [    0.900225] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
 [    0.900257] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
 [    0.900272] ehci_hcd 0000:00:1d.7: using broken periodic workaround 
 [    0.904146] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
 [    0.904163] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe5104000 
 [    0.920012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
 [    0.920131] hub 1-0:1.0: USB hub found 
 [    0.920136] hub 1-0:1.0: 8 ports detected 
 [    0.920215] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
 [    0.920227] uhci_hcd: USB Universal Host Controller Interface driver 
 [    0.920245] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
 [    0.920250] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
 [    0.920253] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
 [    0.920284] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
 [    0.920305] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000 
 [    0.920410] hub 2-0:1.0: USB hub found 
 [    0.920414] hub 2-0:1.0: 2 ports detected 
 [    0.920470] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
 [    0.920475] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
 [    0.920478] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
 [    0.920510] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
 [    0.920539] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100 
 [    0.920644] hub 3-0:1.0: USB hub found 
 [    0.920647] hub 3-0:1.0: 2 ports detected 
 [    0.920705] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
 [    0.920710] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
 [    0.920713] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
 [    0.920744] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
 [    0.920775] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200 
 [    0.920880] hub 4-0:1.0: USB hub found 
 [    0.920883] hub 4-0:1.0: 2 ports detected 
 [    0.920937] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
 [    0.920942] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
 [    0.920945] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
 [    0.920975] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
 [    0.921004] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300 
 [    0.921113] hub 5-0:1.0: USB hub found 
 [    0.921117] hub 5-0:1.0: 2 ports detected 
 [    0.921224] i8042: PNP: No PS/2 controller found. Probing ports directly. 
 [    0.921621] serio: i8042 KBD port at 0x60,0x64 irq 1 
 [    0.921627] serio: i8042 AUX port at 0x60,0x64 irq 12 
 [    0.921747] mousedev: PS/2 mouse device common for all mice 
 [    0.921885] rtc_cmos 00:04: RTC can wake from S4 
 [    0.921968] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0 
 [    0.921990] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs 
 [    0.922061] device-mapper: uevent: version 1.0.3 
 [    0.922132] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL] 
 [    0.922160] EISA: Probing bus 0 at eisa.0 
 [    0.922162] EISA: Cannot allocate resource for mainboard 
 [    0.922164] Cannot allocate resource for EISA slot 1 
 [    0.922166] Cannot allocate resource for EISA slot 2 
 [    0.922168] Cannot allocate resource for EISA slot 3 
 [    0.922169] Cannot allocate resource for EISA slot 4 
 [    0.922171] Cannot allocate resource for EISA slot 5 
 [    0.922173] Cannot allocate resource for EISA slot 6 
 [    0.922175] Cannot allocate resource for EISA slot 7 
 [    0.922176] Cannot allocate resource for EISA slot 8 
 [    0.922178] EISA: Detected 0 cards. 
 [    0.922185] cpufreq-nforce2: No nForce2 chipset. 
 [    0.922188] cpuidle: using governor ladder 
 [    0.922190] cpuidle: using governor menu 
 [    0.922191] EFI Variables Facility v0.08 2004-May-17 
 [    0.922476] TCP cubic registered 
 [    0.922608] NET: Registered protocol family 10 
 [    0.923178] NET: Registered protocol family 17 
 [    0.923191] Registering the dns_resolver key type 
 [    0.923211] Using IPI No-Shortcut mode 
 [    0.923279] PM: Hibernation image not present or could not be loaded. 
 [    0.923292] registered taskstats version 1 
 [    0.935223]   Magic number: 4:10:399 
 [    0.935306] rtc_cmos 00:04: setting system clock to 2012-03-13 21:23:48 UTC (1331673828) 
 [    0.940048] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 [    0.940050] EDD information not available. 
 [    1.073477] ata1.01: HPA detected: current 1250261615, native 1250263728 
 [    1.073484] ata1.01: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133 
 [    1.073488] ata1.01: 1250261615 sectors, multi 16: LBA48 NCQ (depth 0/32) 
 [    1.080189] ata2.01: ATAPI: HL-DT-ST BDDVDRW GGC-H20L, 1.03, max UDMA/133 
 [    1.080741] ata1.01: configured for UDMA/133 
 [    1.080873] scsi 0:0:1:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5 
 [    1.080992] sd 0:0:1:0: [sda] 1250261615 512-byte logical blocks: (640 GB/596 GiB) 
 [    1.081025] sd 0:0:1:0: Attached scsi generic sg0 type 0 
 [    1.081041] sd 0:0:1:0: [sda] Write Protect is off 
 [    1.081044] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
 [    1.081065] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 [    1.096121] ata2.01: configured for UDMA/133 
 [    1.101856] scsi 1:0:1:0: CD-ROM            HL-DT-ST BDDVDRW GGC-H20L 1.03 PQ: 0 ANSI: 5 
 [    1.107420] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray 
 [    1.107423] cdrom: Uniform CD-ROM driver Revision: 3.20 
 [    1.107548] sr 1:0:1:0: Attached scsi CD-ROM sr0 
 [    1.107615] sr 1:0:1:0: Attached scsi generic sg1 type 5 
 [    1.137770]  sda: sda1 sda2 sda3 < sda5 sda6 > 
 [    1.138147] sd 0:0:1:0: [sda] Attached SCSI disk 
 [    1.138258] Freeing unused kernel memory: 720k freed 
 [    1.138457] Write protecting the kernel text: 5528k 
 [    1.138548] Write protecting the kernel read-only data: 2244k 
 [    1.138550] NX-protecting the kernel data: 4712k 
 [    1.155054] udevd[93]: starting version 173 
 [    1.178960] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
 [    1.178979] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    1.179016] r8169 0000:03:00.0: setting latency timer to 64 
 [    1.179071] r8169 0000:03:00.0: irq 43 for MSI/MSI-X 
 [    1.179575] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xf8412000, 00:24:1d:31:e0:e4, XID 1c4000c0 IRQ 43 
 [    1.232031] usb 1-1: new high speed USB device number 2 using ehci_hcd 
 [    1.369487] usbcore: registered new interface driver uas 
 [    1.370171] Initializing USB Mass Storage driver... 
 [    1.370311] scsi2 : usb-storage 1-1:1.0 
 [    1.370436] usbcore: registered new interface driver usb-storage 
 [    1.370438] USB Mass Storage support registered. 
 [    1.424034] Refined TSC clocksource calibration: 2333.332 MHz. 
 [    1.424039] Switching to clocksource tsc 
 [    1.480016] usb 1-2: new high speed USB device number 3 using ehci_hcd 
 [    1.520512] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null) 
 [    1.780018] usb 1-6: new high speed USB device number 5 using ehci_hcd 
 [    1.913320] scsi3 : usb-storage 1-6:1.0 
 [    2.080012] usb 1-8: new high speed USB device number 7 using ehci_hcd 
 [    2.213520] hub 1-8:1.0: USB hub found 
 [    2.213835] hub 1-8:1.0: 4 ports detected 
 [    2.368735] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0 
 [    2.369235] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0 
 [    2.369730] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0 
 [    2.370232] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0 
 [    2.452021] usb 4-1: new low speed USB device number 2 using uhci_hcd 
 [    2.800234] sd 2:0:0:0: Attached scsi generic sg2 type 0 
 [    2.800379] sd 2:0:0:1: Attached scsi generic sg3 type 0 
 [    2.800504] sd 2:0:0:2: Attached scsi generic sg4 type 0 
 [    2.800631] sd 2:0:0:3: Attached scsi generic sg5 type 0 
 [    2.805975] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
 [    2.806596] sd 2:0:0:1: [sdc] Attached SCSI removable disk 
 [    2.807220] sd 2:0:0:2: [sdd] Attached SCSI removable disk 
 [    2.807843] sd 2:0:0:3: [sde] Attached SCSI removable disk 
 [    2.912866] scsi 3:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4 
 [    2.936012] usb 5-1: new low speed USB device number 2 using uhci_hcd 
 [    3.028311] sd 3:0:0:0: Attached scsi generic sg6 type 0 
 [    3.028850] sd 3:0:0:0: [sdf] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB) 
 [    3.029723] sd 3:0:0:0: [sdf] Test WP failed, assume Write Enabled 
 [    3.030598] sd 3:0:0:0: [sdf] Asking for cache data failed 
 [    3.030600] sd 3:0:0:0: [sdf] Assuming drive cache: write through 
 [    3.032222] sd 3:0:0:0: [sdf] Test WP failed, assume Write Enabled 
 [    3.033098] sd 3:0:0:0: [sdf] Asking for cache data failed 
 [    3.033101] sd 3:0:0:0: [sdf] Assuming drive cache: write through 
 [    3.033655]  sdf: sdf1 
 [    3.035471] sd 3:0:0:0: [sdf] Test WP failed, assume Write Enabled 
 [    3.036348] sd 3:0:0:0: [sdf] Asking for cache data failed 
 [    3.036351] sd 3:0:0:0: [sdf] Assuming drive cache: write through 
 [    3.036354] sd 3:0:0:0: [sdf] Attached SCSI disk 
 [    3.240348] usb 1-8.3: new full speed USB device number 8 using ehci_hcd 
 [   14.953835] udevd[295]: starting version 173 
 [   14.993601] lp: driver loaded but no devices found 
 [   15.005508] nvidia: module license 'NVIDIA' taints kernel. 
 [   15.005512] Disabling lock debugging due to kernel taint 
 [   15.007185] intel_rng: FWH not detected 
 [   15.031565] leds_ss4200: no LED devices found 
 [   15.043670] type=1400 audit(1331634242.602:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=368 comm="apparmor_parser" 
 [   15.044123] type=1400 audit(1331634242.606:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=368 comm="apparmor_parser" 
 [   15.044362] type=1400 audit(1331634242.606:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=368 comm="apparmor_parser" 
 [   15.051551] parport_pc 00:08: reported by Plug and Play ACPI 
 [   15.051596] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
 [   15.073483] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   15.073530] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X 
 [   15.073554] HDA Intel 0000:00:1b.0: setting latency timer to 64 
 [   15.089245] Adding 4191228k swap on /dev/sda6.  Priority:-1 extents:1 across:4191228k  
 [   15.148210] lp0: using parport0 (interrupt-driven). 
 [   15.226727] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2 
 [   15.226928] generic-usb 0003:046D:C051.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-1/input0 
 [   15.226972] usbcore: registered new interface driver usbhid 
 [   15.226974] usbhid: USB HID core driver 
 [   15.235051] r8712u: module is from the staging directory, the quality is unknown, you have been warned. 
 [   15.236623] r8712u: DriverVersion: v7_0.20100831 
 [   15.236638] r8712u: register rtl8712_netdev_ops to netdev_ops 
 [   15.236640] r8712u: USB_SPEED_HIGH with 4 endpoints 
 [   15.237956] r8712u: Boot from EFUSE: Autoload OK 
 [   15.253830] ppdev: user-space parallel port driver 
 [   15.289399] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3 
 [   15.289504] microsoft 0003:045E:00F9.0001: input,hidraw1: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.2-1/input0 
 [   15.289903] Linux video capture interface: v2.00 
 [   15.290375] gspca: v2.13.0 registered 
 [   15.291957] input: sonixj as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.3/input/input4 
 [   15.292217] usbcore: registered new interface driver sonixj 
 [   15.297196] usbcore: registered new interface driver snd-usb-audio 
 [   15.379830] microsoft 0003:045E:00F9.0002: fixing up Microsoft Wireless Receiver Model 1028 report descriptor 
 [   15.430982] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input5 
 [   15.431113] microsoft 0003:045E:00F9.0002: input,hidraw2: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.2-1/input1 
 [   15.772853] r8712u: CustomerID = 0x0000 
 [   15.772856] r8712u: MAC Address from efuse = 00:26:5a:ee:60:ef 
 [   15.773563] usbcore: registered new interface driver r8712u 
 [   16.105031] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   16.105039] nvidia 0000:01:00.0: setting latency timer to 64 
 [   16.105044] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem 
 [   16.105150] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011 
 [   16.203600] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro 
 [   16.375055] vesafb: mode is 1280x1024x32, linelength=5120, pages=0 
 [   16.375058] vesafb: scrolling: redraw 
 [   16.375060] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0 
 [   16.376799] vesafb: framebuffer at 0xe1000000, mapped to 0xf8500000, using 5120k, total 5120k 
 [   16.376971] Console: switching to colour frame buffer device 160x64 
 [   16.377005] fb0: VESA VGA frame buffer device 
 [   18.403081] type=1400 audit(1331634245.962:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=981 comm="apparmor_parser" 
 [   18.403557] type=1400 audit(1331634245.962:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=981 comm="apparmor_parser" 
 [   18.544914] r8169 0000:03:00.0: eth0: link down 
 [   18.545078] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   18.547011] type=1400 audit(1331634246.106:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1000 comm="apparmor_parser" 
 [   18.547364] type=1400 audit(1331634246.106:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1001 comm="apparmor_parser" 
 [   18.547753] type=1400 audit(1331634246.106:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1001 comm="apparmor_parser" 
 [   18.547993] type=1400 audit(1331634246.106:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1001 comm="apparmor_parser" 
 [   18.550003] type=1400 audit(1331634246.110:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1004 comm="apparmor_parser" 
 [   18.598979] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin" 
 [   18.665315] init: failsafe main process (925) killed by TERM signal 
 [   18.665737] init: apport pre-start process (1058) terminated with status 1 
 [   18.678018] init: apport post-stop process (1106) terminated with status 1 
 [   18.994365] vboxdrv: Found 4 processor cores. 
 [   18.994477] vboxdrv: fAsync=0 offMin=0x3db offMax=0x174c 
 [   18.994530] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'. 
 [   18.994532] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000). 
 [   19.081238] vboxpci: IOMMU not found (not registered) 
 [   19.276488] r8712u: 1 RCR=0x153f00e 
 [   19.277230] r8712u: 2 RCR=0x553f00e 
 [   19.384417] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   19.421364] Bluetooth: Core ver 2.16 
 [   19.421394] NET: Registered protocol family 31 
 [   19.421395] Bluetooth: HCI device and connection manager initialized 
 [   19.421398] Bluetooth: HCI socket layer initialized 
 [   19.421399] Bluetooth: L2CAP socket layer initialized 
 [   19.421584] Bluetooth: SCO socket layer initialized 
 [   19.423344] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [   19.423347] Bluetooth: BNEP filters: protocol multicast 
 [   19.426792] Bluetooth: RFCOMM TTY layer initialized 
 [   19.426797] Bluetooth: RFCOMM socket layer initialized 
 [   19.426798] Bluetooth: RFCOMM ver 1.11 
 [   20.291529] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0 
 [   20.547180] init: plymouth-stop pre-start process (1514) terminated with status 1 
 [   22.711410] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0 
 [   30.389428] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 [   30.389724] r8712u: [r8712_got_addbareq_event_callback] mac = 00:22:3f:a3:88:c2, seq = 0, tid = 0 
 [   41.304006] wlan0: no IPv6 routers present 
 [  966.188017] usb 1-3: new high speed USB device number 9 using ehci_hcd 
 [  966.324704] scsi4 : usb-storage 1-3:1.0 
 [  967.324598] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS 
 [  967.428602] sd 4:0:0:0: Attached scsi generic sg7 type 0 
 [  967.638716] sd 4:0:0:0: [sdg] 4030464 512-byte logical blocks: (2.06 GB/1.92 GiB) 
 [  967.639209] sd 4:0:0:0: [sdg] Write Protect is off 
 [  967.639212] sd 4:0:0:0: [sdg] Mode Sense: 23 00 00 00 
 [  967.639710] sd 4:0:0:0: [sdg] No Caching mode page present 
 [  967.639713] sd 4:0:0:0: [sdg] Assuming drive cache: write through 
 [  967.642084] sd 4:0:0:0: [sdg] No Caching mode page present 
 [  967.642087] sd 4:0:0:0: [sdg] Assuming drive cache: write through 
 [  967.643026]  sdg: sdg1 
 [  967.644959] sd 4:0:0:0: [sdg] No Caching mode page present 
 [  967.644963] sd 4:0:0:0: [sdg] Assuming drive cache: write through 
 [  967.644966] sd 4:0:0:0: [sdg] Attached SCSI removable disk 
 [ 2483.017170] sdg: detected capacity change from 2063597568 to 0 
 [ 2486.256066] usb 1-3: USB disconnect, device number 9 
 [ 2606.064014] usb 1-3: new high speed USB device number 10 using ehci_hcd 
 [ 2606.200745] scsi5 : usb-storage 1-3:1.0 
 [ 2607.200640] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS 
 [ 2607.308419] sd 5:0:0:0: Attached scsi generic sg7 type 0 
 [ 2607.514634] sd 5:0:0:0: [sdg] 4030464 512-byte logical blocks: (2.06 GB/1.92 GiB) 
 [ 2607.515127] sd 5:0:0:0: [sdg] Write Protect is off 
 [ 2607.515130] sd 5:0:0:0: [sdg] Mode Sense: 23 00 00 00 
 [ 2607.515627] sd 5:0:0:0: [sdg] No Caching mode page present 
 [ 2607.515630] sd 5:0:0:0: [sdg] Assuming drive cache: write through 
 [ 2607.518127] sd 5:0:0:0: [sdg] No Caching mode page present 
 [ 2607.518130] sd 5:0:0:0: [sdg] Assuming drive cache: write through 
 [ 2607.519069]  sdg: sdg1 
 [ 2607.521003] sd 5:0:0:0: [sdg] No Caching mode page present 
 [ 2607.521007] sd 5:0:0:0: [sdg] Assuming drive cache: write through 
 [ 2607.521011] sd 5:0:0:0: [sdg] Attached SCSI removable disk 
 [ 2715.016568] sdg: detected capacity change from 2063597568 to 0 
 [ 2716.027837] usb 1-3: USB disconnect, device number 10 
 [ 4861.168025] usb 1-3: new high speed USB device number 11 using ehci_hcd 
 [ 4861.304807] scsi6 : usb-storage 1-3:1.0 
 [ 4862.304703] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS 
 [ 4862.442033] sd 6:0:0:0: Attached scsi generic sg7 type 0 
 [ 4862.648693] sd 6:0:0:0: [sdg] 4030464 512-byte logical blocks: (2.06 GB/1.92 GiB) 
 [ 4862.649186] sd 6:0:0:0: [sdg] Write Protect is off 
 [ 4862.649189] sd 6:0:0:0: [sdg] Mode Sense: 23 00 00 00 
 [ 4862.649685] sd 6:0:0:0: [sdg] No Caching mode page present 
 [ 4862.649689] sd 6:0:0:0: [sdg] Assuming drive cache: write through 
 [ 4862.652072] sd 6:0:0:0: [sdg] No Caching mode page present 
 [ 4862.652075] sd 6:0:0:0: [sdg] Assuming drive cache: write through 
 [ 4862.653003]  sdg: sdg1 
 [ 4862.654935] sd 6:0:0:0: [sdg] No Caching mode page present 
 [ 4862.654938] sd 6:0:0:0: [sdg] Assuming drive cache: write through 
 [ 4862.654941] sd 6:0:0:0: [sdg] Attached SCSI removable disk 

```

---

### Post by kurt18947 on 2012-03-13
Hi

You can use "code" tags -the # symbol in the tool bar - to make long text files readable.  I'm using 12.04 and it looks like a new Network Manager was installed. If 11.10 got a Network Manager upgrade as well,  I wonder if it would be worthwhile to  delete and reinstall your network connection.  I removed an Atheros adapter and installed a Dlink DWA-131.  I had to restart and redo the network connection in order for the Dlink to work.  I don't know if deleting your current network connection, restarting your machine and reinstalling your network connection will help or not but it's pretty quick and simple to do.

---

### Post by mndmdvrantm on 2012-03-15
> **kurt18947 said:**
> You can use &quot;code&quot; tags -the # symbol in the tool bar - to make long text files readable. Oh, ok. Thanks for pointing that out. I always thought the code tags only put text in a more readable format, not necessarily shortening huge blocks of text.  > **kurt18947 said:**
> I'm using 12.04 and it looks like a new Network Manager was installed. If 11.10 got a Network Manager upgrade as well,  I wonder if it would be worthwhile to  delete and reinstall your network connection.I removed an Atheros adapter and installed a Dlink DWA-131.  I had to restart and redo the network connection in order for the Dlink to work.  I don't know if deleting your current network connection, restarting your machine and reinstalling your network connection will help or not but it's pretty quick and simple to do. Turns out I did get a network manager update, so I decided to see if that was the problem by booting the Ubuntu 11.10 live CD (which had the working version of network manager installed), but I didn't have an internet connection running 'vanilla' 11.10 either.  I also followed your instructions, which didn't fix the problem either.  Somewhat embarrasingly, in the end the problem was easily solved by simply removing the adapter, shutting down, turning the machine off at the powerpoint, booting back into ubuntu and inserting the adapter again. I'm not sure how I could have overlooked such an easy solution, but I appreciate your help anyway.

---

### Post by kurt18947 on 2012-03-15
heh, I think I might know how to fix your problem.  There's an issue with 8192SU chipsets not disconnecting when going into suspend mode.  When the system un-suspends, it wants to restart the network.  It can't restart the network because it didn't disconnect prior to suspending.  Here is a fix that has worked for me and it's still necessary in 12.04.

```
sudo gedit /etc/pm/config.d/config
```A new empty file will open.  Add this one line:

```
SUSPEND_MODULES="r8712u"
```Save, exit and restart.  Then suspend and resume.  Does it work as expected?

---

### Post by mndmdvrantm on 2012-03-16
> in the end the problem was easily solved by simply removing the adapter, shutting down, turning the machine off at the powerpoint, booting back into ubuntu and inserting the adapter again. 
The problem occured again today, and this "solution" of mine didn't work for me this second time around.

> **kurt18947 said:**
> Save, exit and restart.  Then suspend and resume.  Does it work as expected?
Not at all, unfortunately.

---

### Post by kurt18947 on 2012-03-17
Wotta pain.  I don't have any further suggestions.  Would it be possible to boot a live CD/USB?  Your Dlink should be found and work correctly in a live session.  It is working correctly in Windows?  Wondering about hardware ailments.

---

### Post by mndmdvrantm on 2012-03-17
> **kurt18947 said:**
> Wotta pain.  I don't have any further suggestions.  Would it be possible to boot a live CD/USB?  Your Dlink should be found and work correctly in a live session.  It is working correctly in Windows?  Wondering about hardware ailments.
Yes, I mentioned that here:
> **mndmdvrantm said:**
> Turns out I did get a network manager  update, so I decided to see if that was the problem by booting the  Ubuntu 11.10 live CD (which had the "working" (at the time) version of  network manager installed), but I didn't have an internet connection  running 'vanilla' 11.10 either. 
At the moment I'm logged into my Windows 7 installation, so the adapter is definitely working under Windows. 

I've found Ubuntu to be pretty dreadful lately, what with the buggy-as-hell and uncustomisable Unity desktop environment (and my experiences with *gnome-session-fallback* as well as running GNOME 3 in Ubuntu weren't exactly stellar, either). Not only am I now looking into other desktop environments (got my eye on KDE at the moment), but since I haven't completely migrated to Ubuntu from Win7, I'm considering simply installing a different distro (Linux Mint, perhaps) in order to start from square one again (hoping my adapter will work) - and it would also satisfy my curiosity in terms of testing different distros to see which one I like best (and then ultimately stick with that one for some time). I *would *wait until stable 12.04 is released, but I hear that Unity hasn't really made any great strides since the current version.

I might also just head out and buy a different adapter that I know works for sure if I get these problems after installing Mint (or after simply just reinstalling Ubuntu if it comes to it). Is there a list of works-out-of-the-box Linux-compatible hardware that you or any one else could point me to?

---

### Post by kurt18947 on 2012-03-17
If you asked me
```
Is there a list of works-out-of-the-box Linux-compatible hardware that you or any one else could point me to?  
```   
One choice I'd mention would be the Dlink DWA-131; mine has been perfect so I'm not much help there.  The only other choice that's been perfect for me since 9.x is TrendNet's TEW-424UB v3.x.  It's G speed only and none too fast at that but has been perfect re plug-n-play.                                                                                                              

You can give Mint a try.   The current version is based on 11.10 so I'm not sure if your hardware experience will be much different but if you have a good internet connection it doesn't take all that long to download.  Another distro I'd consider is PCLinuxOS.  I found it as easy to install/use as Ubuntu but it doesn't use a Debian/Ubuntu code base AFAIK.  I didn't care for the Xfce version but thought the LXDE was pretty well done.  Uses .rpm packages but does so using Synaptic so package management is a lot like Ubuntu.  The only weirdness I found was having to install a package in order to install a printer.  The package was something like tasks-printing or printing-tasks or similar.

---

### Post by mndmdvrantm on 2012-03-17
> **kurt18947 said:**
> You can give Mint a try.   The current version is based on 11.10 so I'm not sure if your hardware experience will be much different but if you have a good internet connection it doesn't take all that long to download.  Another distro I'd consider is PCLinuxOS.  I found it as easy to install/use as Ubuntu but it doesn't use a Debian/Ubuntu code base AFAIK.  I didn't care for the Xfce version but thought the LXDE was pretty well done.  Uses .rpm packages but does so using Synaptic so package management is a lot like Ubuntu.  The only weirdness I found was having to install a package in order to install a printer.  The package was something like tasks-printing or printing-tasks or similar.
I downloaded Mint 12 KDE last night and ran it off a live USB, and I was much more impressed with the KDE desktop than Unity or GNOME - although, as I had expected, I connected to my network but couldn't get an internet connection. However after some minor googling, I learnt that Mint and Mint KDE are pretty much just rebranded versions of Ubuntu and Kubuntu respectively. I was originally concerned that Canonical's dropping of support (or whatever exactly Canonical's decision was) for Kubuntu would mean that it would no longer be developed, but I quickly discovered that Kubuntu would continue to be released on a regular schedule as usual. In that case (as well as the fact that Kubuntu forums are way more active than the KDE section of Mint forums, and there's also Kubuntu support to be found here at Ubuntu forums), I don't really see any reason for me to use Mint KDE over Kubuntu.

I might try PCLinuxOS, but I don't expect that less-used distribution to be any more compatible with my wireless adapter than a more mainstream distro like Ubuntu or its derivatives. Looks like I'm just going to have to find a more compatible adapter.

---

### Post by BertN45 on 2012-03-18
Why not try the 12.04 beta. It is relatively stable and it has better and more drivers. My problem with the wifi driver disappeared too.

---

### Post by kurt18947 on 2012-03-18
Just for grins, what does you dmesg look like? Does a section match the output listed in the bug report?

rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! 

If not, you have something else going on.

---

