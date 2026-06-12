---
title: "Samsung N210 Wireless on 11.10 - 1MB Connection Speed."
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by jonnohudski on 2011-11-06
Hi everyone, I am a noob to Ubuntu, and have just installed 11.10 on my wifes Samsung N210. I Have updated the driver following Chlli555's instructions and now the wireless does not keep dropping out.

BUT, I am only geting a reported 1MB connection speed.

Any ideas how I can increase this?

Here are the answers to the Wireless Sticky.

lspci and lsusb























terri@terri-N150-N210-N220:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
terri@terri-N150-N210-N220:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 004 Device 002: ID 0a5c:219b Broadcom Corp. Bluetooth 2.1 Device
terri@terri-N150-N210-N220:~$ 

lspci -nn

 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]




ifconfig and iwconfig

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:54:44:7a:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:319 (319.0 B)  TX bytes:319 (319.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:9a:95:7e  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe9a:957e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f82f8000-f82f8100 

terri@terri-N150-N210-N220:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"BTHomeHub2-ZTT7"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:24:17:64:B5:63   
          Bit Rate=1 Mb/s   
          Retry on   RTS throff   Fragment throff
          Power Management period:0us  mode:All packets received
          Link Quality=93/100  Signal level=-54 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





terri@terri-N150-N210-N220:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:b6:9a:95:7e  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe9a:957e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f82f8000-f82f8100 




terri@terri-N150-N210-N220:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
snd_seq_midi           13132  0 
serio_raw              12990  0 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r8192e_pci            234281  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
i915                  505108  3 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
mac80211              272785  2 rtl8192se,rtlwifi
drm_kms_helper         32889  1 i915
cfg80211              172392  2 rtlwifi,mac80211
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 





[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. N150/N210/N220             /N150/N210/N220             , BIOS 05JI.M039.20100109.JIP 01/09/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2038M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7dd0] f7dd0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365f2000 - 372f1000
[    0.000000] ACPI: RSDP 000f7da0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f5b8e27 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5bfc92 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5ba08f 05B7F (v01  INTEL BEARG31A 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f5c2fc0 00040
[    0.000000] ACPI: MCFG 7f5bfd86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7f5bfdc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7f5bfdfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5bfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f5bfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f5b942f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b9389 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8e93 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5b0
[    0.000000] On node 0 totalpages: 521533
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f5602200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292022 pages, LIFO batch:31
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
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u2097152
[    0.000000] pcpu-alloc: s26240 r0 d22912 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=da0a74da-65e6-4fa4-898e-f6924e3a525e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8346112 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5b0)
[    0.000000] Memory: 2037872k/2086592k available (5329k kernel code, 48260k reserved, 2589k data, 696k init, 1177288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.511 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.02 BogoMIPS (lpj=6650044)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.004066] Security Framework initialized
[    0.004100] AppArmor: AppArmor initialized
[    0.004105] Yama: becoming mindful.
[    0.004221] Mount-cache hash table entries: 512
[    0.004477] Initializing cgroup subsys cpuacct
[    0.008019] Initializing cgroup subsys memory
[    0.008037] Initializing cgroup subsys devices
[    0.008043] Initializing cgroup subsys freezer
[    0.008049] Initializing cgroup subsys net_cls
[    0.008055] Initializing cgroup subsys blkio
[    0.008071] Initializing cgroup subsys perf_event
[    0.008127] CPU: Physical Processor ID: 0
[    0.008133] CPU: Processor Core ID: 0
[    0.008139] mce: CPU supports 5 MCE banks
[    0.008154] CPU0: Thermal monitoring handled by SMI
[    0.008164] using mwait in idle threads.
[    0.011678] ACPI: Core revision 20110413
[    0.024030] ftrace: allocating 24885 entries in 49 pages
[    0.028097] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028511] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070659] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.072003] APIC calibration not consistent with PM-Timer: 291ms instead of 100ms
[    0.072003] APIC delta adjusted to PM-Timer: 1039048 (303399
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f44a4000 soft=f44a6000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.160038] Brought up 2 CPUs
[    0.160048] Total of 2 processors activated (6649.92 BogoMIPS).
[    0.160569] devtmpfs: initialized
[    0.160569] PM: Registering ACPI NVS region at 7f5c0000 (12288 bytes)
[    0.166649] print_constraints: dummy: 
[    0.166693] Time: 16:52:06  Date: 11/06/11
[    0.166782] NET: Registered protocol family 16
[    0.166884] Trying to unpack rootfs image as initramfs...
[    0.167187] EISA bus registered
[    0.167213] ACPI: bus type pci registered
[    0.167387] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.167399] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.167406] PCI: Using MMCONFIG for extended config space
[    0.167412] PCI: Using configuration type 1 for base access
[    0.170825] bio: create slab <bio-0> at 0
[    0.174510] ACPI: EC: Look up EC in DSDT
[    0.187594] ACPI: SSDT 7f5b9db8 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.188506] ACPI: Dynamic OEM Table Load:
[    0.188518] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.189054] ACPI: SSDT 7f5b968e 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.189873] ACPI: Dynamic OEM Table Load:
[    0.189884] ACPI: SSDT   (null) 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.190719] ACPI: SSDT 7f5b9fbb 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.191573] ACPI: Dynamic OEM Table Load:
[    0.191584] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.191900] ACPI: SSDT 7f5b9d33 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.192750] ACPI: Dynamic OEM Table Load:
[    0.192761] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.193648] ACPI: Interpreter enabled
[    0.193648] ACPI: (supports S0 S3 S4 S5)
[    0.193648] ACPI: Using IOAPIC for interrupt routing
[    0.209106] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.209600] ACPI: No dock devices found.
[    0.209609] HEST: Table not found.
[    0.209620] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.212402] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.212426] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4422e8o, AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.212452] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.212475] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.216594] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.216606] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.216616] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.216625] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.216635] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.216644] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.216654] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.216663] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.216699] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.216773] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.216794] pci 0000:00:02.0: reg 10: [mem 0xf0300000-0xf037ffff]
[    0.216808] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.216822] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.216836] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.216894] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.216913] pci 0000:00:02.1: reg 10: [mem 0xf0380000-0xf03fffff]
[    0.217060] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.217099] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.217216] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.217228] pci 0000:00:1b.0: PME# disabled
[    0.217273] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.217391] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.217402] pci 0000:00:1c.0: PME# disabled
[    0.217451] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.217568] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.217580] pci 0000:00:1c.1: PME# disabled
[    0.217627] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.217743] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.217755] pci 0000:00:1c.2: PME# disabled
[    0.217805] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.217922] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.217933] pci 0000:00:1c.3: PME# disabled
[    0.217984] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.218067] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.218131] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.218209] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.218269] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.218346] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.218414] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.218492] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.218568] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.218605] pci 0000:00:1d.7: reg 10: [mem 0xf0604000-0xf06043ff]
[    0.218727] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.218739] pci 0000:00:1d.7: PME# disabled
[    0.218778] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.218895] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.219020] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.219090] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.219126] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.219147] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.219168] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.219188] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.219209] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.219230] pci 0000:00:1f.2: reg 24: [mem 0xf0604400-0xf06047ff]
[    0.219290] pci 0000:00:1f.2: PME# supported from D3hot
[    0.219301] pci 0000:00:1f.2: PME# disabled
[    0.219333] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.219415] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.219582] pci 0000:05:00.0: [10ec:8192] type 0 class 0x000280
[    0.219616] pci 0000:05:00.0: reg 10: [io  0x2000-0x20ff]
[    0.219641] pci 0000:05:00.0: reg 14: [mem 0xf0100000-0xf0103fff]
[    0.219781] pci 0000:05:00.0: supports D1 D2
[    0.219788] pci 0000:05:00.0: PME# supported from D1 D2 D3hot
[    0.219801] pci 0000:05:00.0: PME# disabled
[    0.224089] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.224105] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.224118] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.224135] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.224230] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.224242] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.224254] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.224271] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.224560] pci 0000:09:00.0: [11ab:4354] type 0 class 0x000200
[    0.224777] pci 0000:09:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.224883] pci 0000:09:00.0: reg 18: [io  0x3000-0x30ff]
[    0.225535] pci 0000:09:00.0: supports D1 D2
[    0.225543] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.225576] pci 0000:09:00.0: PME# disabled
[    0.225900] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.225913] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.225927] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.225945] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.226036] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.226048] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0000] (disabled)
[    0.226060] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.226076] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.226193] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.226205] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.226218] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.226233] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.226244] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.226253] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.226263] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.226272] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.226282] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.226292] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.226302] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.226311] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.226361] pci_bus 0000:00: on NUMA node 0
[    0.226376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.226645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.226793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.226933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.227076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.227209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.227637] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.227659] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4422e8o, AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.227698]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.227897] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.227919] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4422e8o, AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.227960]  pci0000:00: ACPI _OSC request failed (AE_ALREADY_EXISTS), returned control mask: 0x1d
[    0.227968] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.240756] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.240924] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.241086] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.241246] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.241435] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.241614] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.241790] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.241962] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.242287] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.242318] vgaarb: loaded
[    0.242323] vgaarb: bridge control possible 0000:00:02.0
[    0.242991] SCSI subsystem initialized
[    0.243151] libata version 3.00 loaded.
[    0.243289] usbcore: registered new interface driver usbfs
[    0.243328] usbcore: registered new interface driver hub
[    0.243433] usbcore: registered new device driver usb
[    0.243731] PCI: Using ACPI for IRQ routing
[    0.244317] PCI: pci_cache_line_size set to 64 bytes
[    0.244543] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.244552] reserve RAM buffer: 000000007f5b0000 - 000000007fffffff 
[    0.244867] NetLabel: Initializing
[    0.244874] NetLabel:  domain hash size = 128
[    0.244879] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.244913] NetLabel:  unlabeled traffic allowed by default
[    0.245043] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.245058] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.245072] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.248872] Switching to clocksource hpet
[    0.250318] Switched to NOHz mode on CPU #0
[    0.250394] Switched to NOHz mode on CPU #1
[    0.268695] AppArmor: AppArmor Filesystem Enabled
[    0.268761] pnp: PnP ACPI init
[    0.268809] ACPI: bus type pnp registered
[    0.270944] pnp 00:00: [bus 00-3f]
[    0.270954] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.270963] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.270972] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.270980] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.270989] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.270997] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.271006] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.271014] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.271022] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.271031] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.271039] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.271048] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.271056] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.271064] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.271073] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.271081] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.271090] pnp 00:00: [mem 0x80000000-0xf7ffffff window]
[    0.271098] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.271106] pnp 00:00: [mem 0x00000000 window]
[    0.271114] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.271306] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.272645] pnp 00:01: [io  0x0010-0x001f]
[    0.272654] pnp 00:01: [io  0x0024-0x0025]
[    0.272662] pnp 00:01: [io  0x0028-0x0029]
[    0.272669] pnp 00:01: [io  0x002c-0x002d]
[    0.272677] pnp 00:01: [io  0x0030-0x0031]
[    0.272684] pnp 00:01: [io  0x0034-0x0035]
[    0.272691] pnp 00:01: [io  0x0038-0x0039]
[    0.272698] pnp 00:01: [io  0x003c-0x003d]
[    0.272706] pnp 00:01: [io  0x0072-0x0077]
[    0.272713] pnp 00:01: [io  0x0080]
[    0.272720] pnp 00:01: [io  0x0090-0x009f]
[    0.272727] pnp 00:01: [io  0x00a4-0x00a5]
[    0.272734] pnp 00:01: [io  0x00a8-0x00a9]
[    0.272742] pnp 00:01: [io  0x00ac-0x00ad]
[    0.272749] pnp 00:01: [io  0x00b0-0x00b5]
[    0.272756] pnp 00:01: [io  0x00b8-0x00b9]
[    0.272764] pnp 00:01: [io  0x00bc-0x00bd]
[    0.272771] pnp 00:01: [io  0x0800-0x080f]
[    0.272779] pnp 00:01: [io  0x1000-0x107f]
[    0.272786] pnp 00:01: [io  0x1180-0x11bf]
[    0.272793] pnp 00:01: [io  0x002e-0x002f]
[    0.272801] pnp 00:01: [io  0x04d0-0x04d1]
[    0.272808] pnp 00:01: [io  0xfe00]
[    0.272815] pnp 00:01: [io  0x164e-0x174c]
[    0.272823] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.272831] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.272839] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.272847] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.273086] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.273098] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.273108] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.273118] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.273127] system 00:01: [io  0xfe00] has been reserved
[    0.273136] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.273147] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.273158] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.273168] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.273178] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.273190] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.273234] pnp 00:02: [io  0x0000-0x000f]
[    0.273242] pnp 00:02: [io  0x0081-0x008f]
[    0.273249] pnp 00:02: [io  0x00c0-0x00df]
[    0.273257] pnp 00:02: [dma 4]
[    0.273350] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.273406] pnp 00:03: [io  0x00f0-0x00fe]
[    0.273429] pnp 00:03: [irq 13]
[    0.273520] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.273641] pnp 00:04: [io  0x0070-0x0071]
[    0.273658] pnp 00:04: [irq 8]
[    0.273753] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.273788] pnp 00:05: [io  0x0061]
[    0.273889] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.273976] pnp 00:06: [io  0x0060]
[    0.273984] pnp 00:06: [io  0x0064]
[    0.274000] pnp 00:06: [irq 1]
[    0.274098] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.274139] pnp 00:07: [irq 12]
[    0.274236] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.274686] pnp 00:08: [mem 0xff800000-0xffffffff]
[    0.274816] pnp 00:08: Plug and Play ACPI device, IDs INT0800 (active)
[    0.275341] pnp: PnP ACPI: found 9 devices
[    0.275349] ACPI: ACPI bus type pnp unregistered
[    0.275360] PnPBIOS: Disabled by ACPI PNP
[    0.315595] PCI: max bus depth: 1 pci_try_num: 2
[    0.315702] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.315718] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.315733] pci 0000:00:1c.3: BAR 13: assigned [io  0x4000-0x4fff]
[    0.315747] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.315760] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80600000-0x807fffff]
[    0.315775] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.315789] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.315803] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.315814] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.315824] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.315838] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.315851] pci 0000:00:1c.0:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.315867] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.315877] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.315891] pci 0000:00:1c.1:   bridge window [mem 0x80600000-0x807fffff]
[    0.315904] pci 0000:00:1c.1:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.315922] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.315932] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.315948] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.315962] pci 0000:00:1c.2:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.315980] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.315990] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.316045] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff]
[    0.316059] pci 0000:00:1c.3:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.316075] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.316082] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.316094] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.316104] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.316159] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.316173] pci 0000:00:1c.0: setting latency timer to 64
[    0.316189] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.316212] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.316226] pci 0000:00:1c.1: setting latency timer to 64
[    0.316255] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.316267] pci 0000:00:1c.2: setting latency timer to 64
[    0.316284] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.316305] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.316319] pci 0000:00:1c.3: setting latency timer to 64
[    0.316337] pci 0000:00:1e.0: setting latency timer to 64
[    0.316349] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.316357] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.316366] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.316375] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.316384] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.316393] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.316402] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.316410] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.316419] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.316428] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.316437] pci_bus 0000:05: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.316446] pci_bus 0000:07: resource 0 [io  0x5000-0x5fff]
[    0.316455] pci_bus 0000:07: resource 1 [mem 0x80600000-0x807fffff]
[    0.316464] pci_bus 0000:07: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.316473] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.316482] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.316491] pci_bus 0000:09: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.316501] pci_bus 0000:0b: resource 0 [io  0x4000-0x4fff]
[    0.316509] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.316518] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.316528] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.316537] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.316545] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.316554] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.316563] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.316572] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.316581] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.316590] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.316692] NET: Registered protocol family 2
[    0.316878] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.317540] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.318652] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.319139] TCP: Hash tables configured (established 131072 bind 65536)
[    0.319150] TCP reno registered
[    0.319168] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.319195] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.319482] NET: Registered protocol family 1
[    0.319528] pci 0000:00:02.0: Boot video device
[    0.319762] PCI: CLS 32 bytes, default 64
[    0.319775] Simple Boot Flag at 0x36 set to 0x1
[    0.320715] audit: initializing netlink socket (disabled)
[    0.320740] type=2000 audit(1320598326.316:1): initialized
[    0.380618] highmem bounce pool size: 64 pages
[    0.380636] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.396633] VFS: Disk quotas dquot_6.5.2
[    0.396837] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.399201] fuse init (API version 7.16)
[    0.399535] msgmni has been set to 1680
[    0.400757] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.400874] io scheduler noop registered
[    0.400881] io scheduler deadline registered
[    0.400942] io scheduler cfq registered (default)
[    0.401263] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.401364] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.401516] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.401599] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.401744] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.401828] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.401967] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.402056] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.402293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.402371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.402545] intel_idle: MWAIT substates: 0x20220
[    0.402562] intel_idle: v0.4 model 0x1C
[    0.402568] intel_idle: lapic_timer_reliable_states 0x2
[    0.402586] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.403011] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.403405] ACPI: AC Adapter [ADP1] (off-line)
[    0.403899] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.404132] ACPI: Lid Switch [LID0]
[    0.404276] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.404292] ACPI: Power Button [PWRB]
[    0.404428] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.404440] ACPI: Sleep Button [SLPB]
[    0.404573] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.404587] ACPI: Power Button [PWRF]
[    0.404681] ACPI: acpi_idle yielding to intel_idle
[    0.416421] thermal LNXTHERM:00: registered as thermal_zone0
[    0.416431] ACPI: Thermal Zone [TZ00] (51 C)
[    0.416511] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.416582] ERST: Table is not found!
[    0.416767] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.417278] isapnp: Scanning for PnP cards...
[    0.454819] ACPI: Battery Slot [BAT1] (battery present)
[    0.772487] isapnp: No Plug & Play device found
[    0.905501] Freeing initrd memory: 13308k freed
[    0.932839] Linux agpgart interface v0.103
[    0.933000] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    0.933207] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.933469] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.933684] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.936632] brd: module loaded
[    0.938038] loop: module loaded
[    0.939114] Fixed MDIO Bus: probed
[    0.939178] PPP generic driver version 2.4.2
[    0.939282] tun: Universal TUN/TAP device driver, 1.6
[    0.939287] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.939480] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.939544] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.939577] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.939585] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.939671] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.939707] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.939725] ehci_hcd 0000:00:1d.7: debug port 1
[    0.943621] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.943659] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    0.956056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.956340] hub 1-0:1.0: USB hub found
[    0.956352] hub 1-0:1.0: 8 ports detected
[    0.956510] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.956543] uhci_hcd: USB Universal Host Controller Interface driver
[    0.956613] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.956627] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.956635] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.956726] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.956767] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.957049] hub 2-0:1.0: USB hub found
[    0.957060] hub 2-0:1.0: 2 ports detected
[    0.957188] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.957201] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.957208] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.957293] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.957353] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.957624] hub 3-0:1.0: USB hub found
[    0.957634] hub 3-0:1.0: 2 ports detected
[    0.957755] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.957768] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.957775] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.957871] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.957926] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.958196] hub 4-0:1.0: USB hub found
[    0.958206] hub 4-0:1.0: 2 ports detected
[    0.958333] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.958346] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.958354] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.958441] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.958495] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.958785] hub 5-0:1.0: USB hub found
[    0.958796] hub 5-0:1.0: 2 ports detected
[    0.959021] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.009186] i8042: Detected active multiplexing controller, rev 1.1
[    1.032226] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.032247] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.032321] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.032389] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.032460] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.032733] mousedev: PS/2 mouse device common for all mice
[    1.034347] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.034390] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.034631] device-mapper: uevent: version 1.0.3
[    1.034815] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.034892] EISA: Probing bus 0 at eisa.0
[    1.034897] EISA: Cannot allocate resource for mainboard
[    1.034903] Cannot allocate resource for EISA slot 1
[    1.034908] Cannot allocate resource for EISA slot 2
[    1.034912] Cannot allocate resource for EISA slot 3
[    1.034916] Cannot allocate resource for EISA slot 4
[    1.034921] Cannot allocate resource for EISA slot 5
[    1.034925] Cannot allocate resource for EISA slot 6
[    1.034930] Cannot allocate resource for EISA slot 7
[    1.034934] Cannot allocate resource for EISA slot 8
[    1.034939] EISA: Detected 0 cards.
[    1.034957] cpufreq-nforce2: No nForce2 chipset.
[    1.035084] cpuidle: using governor ladder
[    1.035292] cpuidle: using governor menu
[    1.035297] EFI Variables Facility v0.08 2004-May-17
[    1.035931] TCP cubic registered
[    1.036303] NET: Registered protocol family 10
[    1.037645] NET: Registered protocol family 17
[    1.037689] Registering the dns_resolver key type
[    1.037735] Using IPI No-Shortcut mode
[    1.037949] PM: Hibernation image not present or could not be loaded.
[    1.037973] registered taskstats version 1
[    1.058374]   Magic number: 3:517:893
[    1.058520] rtc_cmos 00:04: setting system clock to 2011-11-06 16:52:07 UTC (1320598327)
[    1.059286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.059292] EDD information not available.
[    1.059562] Freeing unused kernel memory: 696k freed
[    1.059986] Write protecting the kernel text: 5332k
[    1.060164] Write protecting the kernel read-only data: 2188k
[    1.094569] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.100853] udevd[82]: starting version 173
[    1.361228] sky2: driver version 1.28
[    1.361376] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.361436] sky2 0000:09:00.0: setting latency timer to 64
[    1.361576] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.362236] sky2 0000:09:00.0: irq 44 for MSI/MSI-X
[    1.384146] usb 1-8: new high speed USB device number 3 using ehci_hcd
[    1.387538] sky2 0000:09:00.0: eth0: addr 00:24:54:44:7a:bc
[    1.399887] ahci 0000:00:1f.2: version 3.0
[    1.399920] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.400712] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.400861] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.400875] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.400888] ahci 0000:00:1f.2: setting latency timer to 64
[    1.406005] scsi0 : ahci
[    1.409792] scsi1 : ahci
[    1.412717] scsi2 : ahci
[    1.415319] scsi3 : ahci
[    1.415809] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 45
[    1.415823] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 45
[    1.415834] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 45
[    1.415845] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 45
[    1.732163] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.732203] ata2: SATA link down (SStatus 0 SControl 300)
[    1.736086] ata3: SATA link down (SStatus 0 SControl 300)
[    1.736123] ata4: SATA link down (SStatus 0 SControl 300)
[    1.772075] usb 4-2: new full speed USB device number 2 using uhci_hcd
[    1.778610] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    1.778626] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.780698] ata1.00: configured for UDMA/133
[    1.780961] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.781468] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.781605] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.781867] sd 0:0:0:0: [sda] Write Protect is off
[    1.781878] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.781996] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.880893]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.882241] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.385310] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
[    3.385319] EXT4-fs (sda7): write access will be enabled during recovery
[   11.863100] EXT4-fs (sda7): recovery complete
[   11.864988] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   22.956397] udevd[303]: starting version 173
[   23.008239] Adding 2084860k swap on /dev/sda8.  Priority:-1 extents:1 across:2084860k 
[   23.045023] lp: driver loaded but no devices found
[   23.150442] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   23.307880] [drm] Initialized drm 1.1.0 20060810
[   23.322298] cfg80211: Calling CRDA to update world regulatory domain
[   23.509963] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.509978] i915 0000:00:02.0: setting latency timer to 64
[   23.550519] rtl8192se 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.550538] rtl8192se 0000:05:00.0: setting latency timer to 64
[   23.550638] rtl8192se 0000:05:00.0: PCI INT A disabled
[   23.610336] type=1400 audit(1320598350.047:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=465 comm="apparmor_parser"
[   23.619873] type=1400 audit(1320598350.055:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=465 comm="apparmor_parser"
[   23.620854] type=1400 audit(1320598350.059:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=465 comm="apparmor_parser"
[   23.622659] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   23.666074] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   23.666090] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   23.666098] [drm] Driver supports precise vblank timestamp query.
[   23.726330] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+memowns=io+mem
[   23.808776] ieee80211_crypt: registered algorithm 'NULL'
[   23.808786] ieee80211_crypt: registered algorithm 'TKIP'
[   23.808794] ieee80211_crypt: registered algorithm 'CCMP'
[   23.808801] ieee80211_crypt: registered algorithm 'WEP'
[   23.808825] 
[   23.808827] Linux kernel driver for RTL8192 based WLAN cards
[   23.808834] Copyright (c) 2007-2008, Realsil Wlan
[   23.808917] rtl819xE 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.808938] rtl819xE 0000:05:00.0: setting latency timer to 64
[   23.916817] Dot11d_Init()
[   23.917282] IRQ 16
[   24.133845] [drm] initialized overlay support
[   24.304998] fbcon: inteldrmfb (fb0) is primary device
[   24.312112] Console: switching to colour frame buffer device 128x37
[   24.312187] fb0: inteldrmfb frame buffer device
[   24.312193] drm: registered panic notifier
[   24.313798] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[   24.352750] acpi device:04: registered as cooling_device2
[   24.354935] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   24.378362] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[   24.378592] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.461585] Bluetooth: Core ver 2.16
[   24.461730] NET: Registered protocol family 31
[   24.461736] Bluetooth: HCI device and connection manager initialized
[   24.461744] Bluetooth: HCI socket layer initialized
[   24.461749] Bluetooth: L2CAP socket layer initialized
[   24.593481] Linux video capture interface: v2.00
[   24.618428] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   24.649186] input: WebCam SCB-0340N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[   24.649539] usbcore: registered new interface driver uvcvideo
[   24.649547] USB Video Class driver (v1.1.0)
[   24.671362] Bluetooth: SCO socket layer initialized
[   24.695404] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   24.699722] usbcore: registered new interface driver btusb
[   24.746594] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.746704] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   24.746770] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.820395] hda_codec: ALC269: BIOS auto-probing.
[   24.892797] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   24.893045] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   25.436399] cfg80211: World regulatory domain updated:
[   25.436410] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.436420] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.436430] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.436439] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.436449] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.436458] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.368681] ppdev: user-space parallel port driver
[   26.375282] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000
[   26.398675] type=1400 audit(1320598352.835:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=830 comm="apparmor_parser"
[   26.400597] type=1400 audit(1320598352.839:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=830 comm="apparmor_parser"
[   26.494630] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   26.652682] sky2 0000:09:00.0: eth0: enabling interface
[   26.653817] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.870030] type=1400 audit(1320598353.307:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=895 comm="apparmor_parser"
[   26.883569] type=1400 audit(1320598353.319:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=896 comm="apparmor_parser"
[   26.885343] type=1400 audit(1320598353.323:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=896 comm="apparmor_parser"
[   26.886227] type=1400 audit(1320598353.323:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=896 comm="apparmor_parser"
[   26.910367] type=1400 audit(1320598353.347:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=899 comm="apparmor_parser"
[   27.464616] init: failsafe main process (851) killed by TERM signal
[   27.478618] init: apport pre-start process (936) terminated with status 1
[   27.577485] init: apport post-stop process (970) terminated with status 1
[   27.822260] Bluetooth: RFCOMM TTY layer initialized
[   27.822277] Bluetooth: RFCOMM socket layer initialized
[   27.822284] Bluetooth: RFCOMM ver 1.11
[   27.827714] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.827723] Bluetooth: BNEP filters: protocol multicast
[   28.081582] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.377694] init: anacron main process (961) killed by TERM signal
[   29.052217] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=600
[   30.116063] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.116075] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.236088] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.236097] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.356073] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.356087] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.476081] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.476094] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.596065] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.596079] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.716080] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   30.716093] rtl819xE:Nic is disabled! Can't tx packet len=82 qidx=6!!!
[   31.183150] init: plymouth-stop pre-start process (1318) terminated with status 1
[   44.472404] Linking with BTHomeHub2-ZTT7,channel:11, qos:1, myHT:1, networkHT:1
[   44.472458] ===>ieee80211_associate_procedure_wq(), chan:11
[   44.488797] =================>ieee80211_authentication_req():auth->algorithm is 0
[   44.488945] Linking with BTHomeHub2-ZTT7,channel:11, qos:1, myHT:1, networkHT:1
[   44.488978] ===>ieee80211_associate_procedure_wq(), chan:11
[   44.504794] =================>ieee80211_authentication_req():auth->algorithm is 0
[   44.509222] Associated successfully
[   44.509229] Using G rates:108
[   44.509232] Successfully associated, ht enabled
[   44.524918] ============>normal associate
[   44.525444] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.575923] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[   44.575937] =====>to send ADDBARSP
[   44.680080] alg name:CCMP
[   44.680642] alg name:TKIP
[   44.864801] DHCP pkt src port:68, dest port:67!!
[   47.560178] DHCP pkt src port:68, dest port:67!!
[   47.572109] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[   47.572127] =====>to send ADDBARSP
[   54.279442] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[   54.279458] =====>to send ADDBARSP
[   55.208251] ===>u4bAcParam:a42b, 
[   55.360050] wlan0: no IPv6 routers present
[   89.005024] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  125.348081] ===>u4bAcParam:a42b, ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  329.006441] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  449.007122] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  557.513183] ===========>RemovePeerTS,00:24:17:64:b5:63
[  557.513196] ====>remove Tx_TS_admin_list
[  557.514396] ===>ieee80211_associate_procedure_wq(), chan:11
[  557.528765] =================>ieee80211_authentication_req():auth->algorithm is 0
[  557.532931] Associated successfully
[  557.532938] Using G rates:108
[  557.532942] Successfully associated, ht enabled
[  557.548948] ============>normal associate
[  557.606504] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[  557.606526] =====>to send ADDBARSP
[  557.711145] alg name:CCMP
[  557.711792] alg name:TKIP
[  558.212310] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  689.006586] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  809.005322] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  810.342156] ===========>RemovePeerTS,00:24:17:64:b5:63
[  810.342165] ====>remove Tx_TS_admin_list
[  810.342945] ===>ieee80211_associate_procedure_wq(), chan:11
[  810.356796] =================>ieee80211_authentication_req():auth->algorithm is 0
[  810.361393] Associated successfully
[  810.361403] Using G rates:108
[  810.361409] Successfully associated, ht enabled
[  810.376948] ============>normal associate
[  810.538797] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[  810.538818] =====>to send ADDBARSP
[  810.642836] alg name:CCMP
[  810.643449] alg name:TKIP
[  810.716293] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  973.190361] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[  973.230989] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[  973.231006] =====>to send ADDBARSP
[  973.979916] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  975.044285] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1053.545721] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 1053.545740] =====>to send ADDBARSP
[ 1093.280228] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1289.006838] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1290.341504] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 1290.341516] ====>remove Tx_TS_admin_list
[ 1290.342628] ===>ieee80211_associate_procedure_wq(), chan:11
[ 1290.356841] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1290.361561] Associated successfully
[ 1290.361572] Using G rates:108
[ 1290.361578] Successfully associated, ht enabled
[ 1290.376968] ============>normal associate
[ 1290.391472] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 1290.391493] =====>to send ADDBARSP
[ 1290.495627] alg name:CCMP
[ 1290.496391] alg name:TKIP
[ 1291.676409] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1410.341363] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 1410.341375] ====>remove Tx_TS_admin_list
[ 1410.342386] ===>ieee80211_associate_procedure_wq(), chan:11
[ 1410.356841] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1410.361354] Associated successfully
[ 1410.361364] Using G rates:108
[ 1410.361370] Successfully associated, ht enabled
[ 1410.377001] ============>normal associate
[ 1410.405769] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 1410.405790] =====>to send ADDBARSP
[ 1410.510441] alg name:CCMP
[ 1410.511051] alg name:TKIP
[ 1411.916332] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1649.005471] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1769.007152] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1879.354152] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 1879.354167] ====>remove Tx_TS_admin_list
[ 1879.355648] ===>ieee80211_associate_procedure_wq(), chan:11
[ 1879.372753] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1879.377018] Associated successfully
[ 1879.377026] Using G rates:108
[ 1879.377030] Successfully associated, ht enabled
[ 1879.379823] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 1879.379842] =====>to send ADDBARSP
[ 1879.392952] ============>normal associate
[ 1879.508909] alg name:CCMP
[ 1879.509520] alg name:TKIP
[ 1880.354408] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 1880.392404] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 1880.392424] =====>to send ADDBARSP
[ 1880.852326] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2009.006110] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2093.646187] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 2093.646199] ====>remove Tx_TS_admin_list
[ 2093.647332] ===>ieee80211_associate_procedure_wq(), chan:11
[ 2093.660813] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 2093.665191] Associated successfully
[ 2093.665199] Using G rates:108
[ 2093.665205] Successfully associated, ht enabled
[ 2093.680966] ============>normal associate
[ 2093.731426] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2093.731440] =====>to send ADDBARSP
[ 2093.836755] alg name:CCMP
[ 2093.837369] alg name:TKIP
[ 2095.280393] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2173.146959] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2173.146978] =====>to send ADDBARSP
[ 2173.436221] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2369.007140] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2489.006476] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2490.341394] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 2490.341406] ====>remove Tx_TS_admin_list
[ 2490.342570] ===>ieee80211_associate_procedure_wq(), chan:11
[ 2490.356839] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 2490.361195] Associated successfully
[ 2490.361207] Using G rates:108
[ 2490.361213] Successfully associated, ht enabled
[ 2490.376956] ============>normal associate
[ 2490.435033] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2490.435054] =====>to send ADDBARSP
[ 2490.538608] alg name:CCMP
[ 2490.539221] alg name:TKIP
[ 2492.072344] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2610.341462] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 2610.341474] ====>remove Tx_TS_admin_list
[ 2610.342490] ===>ieee80211_associate_procedure_wq(), chan:11
[ 2610.356838] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 2610.361118] Associated successfully
[ 2610.361130] Using G rates:108
[ 2610.361136] Successfully associated, ht enabled
[ 2610.376954] ============>normal associate
[ 2610.448522] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2610.448542] =====>to send ADDBARSP
[ 2610.552827] alg name:CCMP
[ 2610.553354] alg name:TKIP
[ 2612.312347] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2730.341555] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 2730.341567] ====>remove Tx_TS_admin_list
[ 2730.342550] ===>ieee80211_associate_procedure_wq(), chan:11
[ 2730.356841] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 2730.361136] Associated successfully
[ 2730.361147] Using G rates:108
[ 2730.361153] Successfully associated, ht enabled
[ 2730.376976] ============>normal associate
[ 2730.463217] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2730.463239] =====>to send ADDBARSP
[ 2730.548289] ===>u4bAcParam:a42b, alg name:CCMP
[ 2730.568537] alg name:TKIP
[ 2785.630455] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 2785.670290] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 2785.670307] =====>to send ADDBARSP
[ 2786.485447] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2786.660299] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2902.892332] ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3089.006761] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3209.006950] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3210.341381] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 3210.341393] ====>remove Tx_TS_admin_list
[ 3210.342515] ===>ieee80211_associate_procedure_wq(), chan:11
[ 3210.356876] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 3210.361113] Associated successfully
[ 3210.361123] Using G rates:108
[ 3210.361130] Successfully associated, ht enabled
[ 3210.376958] ============>normal associate
[ 3210.418732] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 3210.418754] =====>to send ADDBARSP
[ 3210.523062] alg name:CCMP
[ 3210.523593] alg name:TKIP
[ 3211.508321] ===>u4bAcParam:a42b, 
[ 3213.878550] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 3213.878601] ieee80211: TsStartAddBaProcess()==>BA timer is already added
[ 3213.918632] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 3213.918653] =====>to send ADDBARSP
[ 3215.516263] ===>u4bAcParam:a42b, ===>u4bAcParam:a42b, LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3449.007129] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3569.006642] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3688.793144] ===========>RemovePeerTS,00:24:17:64:b5:63
[ 3688.793160] ====>remove Tx_TS_admin_list
[ 3688.794489] ===>ieee80211_associate_procedure_wq(), chan:11
[ 3688.809844] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 3688.814222] Associated successfully
[ 3688.814230] Using G rates:108
[ 3688.814234] Successfully associated, ht enabled
[ 3688.828919] ============>normal associate
[ 3688.940775] ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 3688.940799] =====>to send ADDBARSP
[ 3689.045629] alg name:CCMP
[ 3689.046262] alg name:TKIP
[ 3690.464275] ===>u4bAcParam:a42b, ====================>rx ADDBAREQ from :00:24:17:64:b5:63
[ 3691.850128] =====>to send ADDBARSP
[ 3694.472421] ===>u4bAcParam:a42b, ===>u4bAcParam:a42b, 






I cannot get the output from sudo lshw, it al appears on 1 line and I have to <ctrl>-c to get out of it.



terri@terri-N150-N210-N220:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:64:B5:63
                    ESSID:"BTHomeHub2-ZTT7"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=89/100  Signal level=-59 dBm  Noise level=-114 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 9ms ago

terri@terri-N150-N210-N220:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
terri@terri-N150-N210-N220:~$ ^C
terri@terri-N150-N210-N220:~$ clear

terri@terri-N150-N210-N220:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:64:B5:63
                    ESSID:"BTHomeHub2-ZTT7"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=89/100  Signal level=-53 dBm  Noise level=-114 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 37ms ago




terri@terri-N150-N210-N220:~$ lsb_release -d
Description:    Ubuntu 11.10
terri@terri-N150-N210-N220:~$ uname -mr
3.0.0-12-generic i686


Any more then I'll post the answers.


Oh and also, not sure its related, but I am now getting the occasional panic when I shut down.

---

