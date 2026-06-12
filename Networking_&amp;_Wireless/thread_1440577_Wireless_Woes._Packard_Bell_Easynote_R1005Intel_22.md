---
title: "Wireless Woes. Packard Bell Easynote R1005/Intel 2200BG/Ubuntu 9.10"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by RiversideAndy on 2010-03-27
Hi, looking for some help to get my mini pci intel 2200 BG wireless card working with Ubuntu. I've tried fiddling around for days now, using the vast knowledge available on the forum, but am getting nowhere. Just moved over from Windows and loving Ubuntu, but have very little knowlegde of Linux/Ubuntu. I deliberately bought a "supported out of the box" wireless card from ebay to try and minimise the chances of having a wireless problem, but here we are.

After playing about with commands in terminal for days, I have put a fresh install of Ubuntu 9.10 on and eagerly await some help from you clever people. I have managed to get online by plugging in my trusty Netgear USB Dongle which worked immediately.

Well impressed with how fast Ubuntu is compared to Windows. Can't think of any reason to ever use it again!

I have included some info below for your perusal in accordance with the **HOWTO post a Wireless issue (ticket)** instructions.

Many thanks in advance

Andy




daddy@daddy-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
daddy@daddy-laptop:~$ 


daddy@daddy-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daddy@daddy-laptop:~$ 

daddy@daddy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:89:90:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:73:88:d9  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe73:88d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5536220 (5.5 MB)  TX bytes:1237094 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-73-88-D9-37-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

daddy@daddy-laptop:~$ 

daddy@daddy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BTHomeHub2-HFGP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:8B:5D:82:2E:9A   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daddy@daddy-laptop:~$ 

daddy@daddy-laptop:~$ lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
via                    40192  2 
drm                   160032  3 via
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_via82xx            23576  2 
snd_via82xx_modem      11204  0 
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
gameport               11368  1 snd_via82xx
snd_ac97_codec        101216  2 snd_via82xx,snd_via82xx_modem
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         6940  1 snd_via82xx
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
rtl8187                50624  0 
mac80211              181140  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
snd_rawmidi            22176  2 snd_mpu401_uart,snd_seq_midi
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    59204  16 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_via82xx,snd_via82xx_modem,snd_pcm
parport                35340  2 ppdev,lp
shpchp                 32272  0 
ipw2200               140292  0 
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
i2c_viapro              7344  0 
via_ircc               24016  0 
irda                  189564  1 via_ircc
crc_ccitt               1852  1 irda
via_rhine              22212  0 
mii                     5212  1 via_rhine
via_agp                 7932  1 
agpgart                34988  2 drm,via_agp
daddy@daddy-laptop:~$ 

[    0.000000] RAMDISK: 148e8000 - 15032d91
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 1bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 1bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 1bffffc0 00040
[    0.000000] ACPI: APIC 1bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1bfef000
[    0.000000]   low ram: 0 - 1bfef000
[    0.000000]   node 0 low ram: 00000000 - 1bfef000
[    0.000000]   node 0 bootmap 00008000 - 0000b800
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001bfef000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [00148e8000 - 0015032d91]          RAMDISK ==> [00148e8000 - 0015032d91]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b11bc]              BRK ==> [00008ae000 - 00008b11bc]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001bfef
[    0.000000]   HighMem  0x0001bfef -> 0x0001bfef
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bfef
[    0.000000] On node 0 totalpages: 114570
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 864 pages used for memmap
[    0.000000]   Normal zone: 109711 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1c000000 (gap: 1c000000:e3f80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1382000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113674
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=b7ce5ae7-62d3-4dff-b238-1617eaacc94e ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2293420 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 436352k/458684k available (4578k kernel code, 21664k reserved, 2146k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdc7ef000 - 0xff7fe000   ( 560 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbfef000   ( 447 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.779 MHz processor.
[    0.001471] Console: colour VGA+ 80x25
[    0.001477] console [tty0] enabled
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.55 BogoMIPS (lpj=5971116)
[    0.004043] Security Framework initialized
[    0.004078] AppArmor: AppArmor initialized
[    0.004089] Mount-cache hash table entries: 512
[    0.004270] Initializing cgroup subsys ns
[    0.004279] Initializing cgroup subsys cpuacct
[    0.004284] Initializing cgroup subsys memory
[    0.004297] Initializing cgroup subsys freezer
[    0.004300] Initializing cgroup subsys net_cls
[    0.004323] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004327] CPU: L2 cache: 1024K
[    0.004334] mce: CPU supports 5 MCE banks
[    0.004346] CPU0: Thermal monitoring enabled (TM1)
[    0.004359] Performance Counters: p6 PMU driver.
[    0.004380] ... version:                 0
[    0.004382] ... bit width:               32
[    0.004385] ... generic counters:        2
[    0.004387] ... value mask:              00000000ffffffff
[    0.004390] ... max period:              000000007fffffff
[    0.004393] ... fixed-purpose counters:  0
[    0.004396] ... counter mask:            0000000000000003
[    0.004402] Checking 'hlt' instruction... OK.
[    0.021163] SMP alternatives: switching to UP code
[    0.028020] Freeing SMP alternatives: 20k freed
[    0.028136] weird, boot CPU (#0) not listed by the BIOS.
[    0.028141] SMP motherboard not detected.
[    0.136022] SMP disabled
[    0.136197] Brought up 1 CPUs
[    0.136201] Total of 1 processors activated (2985.55 BogoMIPS).
[    0.136218] CPU0 attaching NULL sched-domain.
[    0.136552] Booting paravirtualized kernel on bare hardware
[    0.136825] regulator: core version 0.5
[    0.136866] Time: 19:27:30  Date: 03/27/10
[    0.136938] NET: Registered protocol family 16
[    0.137126] EISA bus registered
[    0.137308] PCI: PCI BIOS revision 2.10 entry at 0xe9b04, last bus=1
[    0.137311] PCI: Using configuration type 1 for base access
[    0.138685] bio: create slab <bio-0> at 0
[    0.138764] ACPI: Interpreter disabled.
[    0.138941] SCSI subsystem initialized
[    0.138993] libata version 3.00 loaded.
[    0.139085] usbcore: registered new interface driver usbfs
[    0.139102] usbcore: registered new interface driver hub
[    0.139134] usbcore: registered new device driver usb
[    0.139274] PCI: Probing PCI hardware
[    0.139279] PCI: Probing PCI hardware (bus 00)
[    0.139338] pci 0000:00:00.0: reg 10 32bit mmio: [0xa0000000-0xa1ffffff]
[    0.139712] pci 0000:00:01.0: supports D1
[    0.139758] pci 0000:00:06.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.139815] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.139821] pci 0000:00:06.0: PME# disabled
[    0.139895] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.139928] pci 0000:00:10.0: supports D1 D2
[    0.139931] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.139937] pci 0000:00:10.0: PME# disabled
[    0.139997] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.140021] pci 0000:00:10.1: supports D1 D2
[    0.140024] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140030] pci 0000:00:10.1: PME# disabled
[    0.140090] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.140124] pci 0000:00:10.2: supports D1 D2
[    0.140127] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140132] pci 0000:00:10.2: PME# disabled
[    0.140172] pci 0000:00:10.3: reg 10 32bit mmio: [0xf0000000-0xf00000ff]
[    0.140226] pci 0000:00:10.3: supports D1 D2
[    0.140229] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140235] pci 0000:00:10.3: PME# disabled
[    0.140316] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.140325] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.140330] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.140411] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.140491] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.140547] pci 0000:00:11.5: supports D1 D2
[    0.140589] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.140684] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.140693] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.140743] pci 0000:00:12.0: supports D1 D2
[    0.140746] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140752] pci 0000:00:12.0: PME# disabled
[    0.140819] pci 0000:01:00.0: reg 10 32bit mmio: [0x90000000-0x93ffffff]
[    0.140828] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.140852] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.140875] pci 0000:01:00.0: supports D1 D2
[    0.140921] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.140927] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.140934] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.141532] pci 0000:00:11.0: VIA IRQ router [1106:3177]
[    0.141764] Bluetooth: Core ver 2.15
[    0.141814] NET: Registered protocol family 31
[    0.141817] Bluetooth: HCI device and connection manager initialized
[    0.141821] Bluetooth: HCI socket layer initialized
[    0.141824] NetLabel: Initializing
[    0.141827] NetLabel:  domain hash size = 128
[    0.141829] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.141850] NetLabel:  unlabeled traffic allowed by default
[    0.144581] pnp: PnP ACPI: disabled
[    0.144596] PnPBIOS: Scanning system for PnP BIOS support...
[    0.144709] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    0.144713] PnPBIOS: PnP BIOS version 1.0, entry 0xeb000:0x3536, dseg 0xeb000
[    0.144723] PNPBIOS fault.. attempting recovery.
[    0.144726] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.144729] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.144732] PnPBIOS: Check with your vendor for an updated BIOS
[    0.144736] PnPBIOS: dev_node_info: unexpected status 0x3a
[    0.144738] PnPBIOS: Unable to get node info.  Aborting.
[    0.145012] AppArmor: AppArmor Filesystem Enabled
[    0.145064] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.145069] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.145076] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.145082] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.145103] pci 0000:00:01.0: setting latency timer to 64
[    0.145111] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.145115] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.145119] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.145122] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.145126] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.145183] NET: Registered protocol family 2
[    0.145328] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.145696] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.145876] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.146083] TCP: Hash tables configured (established 16384 bind 16384)
[    0.146088] TCP reno registered
[    0.146219] NET: Registered protocol family 1
[    0.146327] Trying to unpack rootfs image as initramfs...
[    0.434649] Freeing initrd memory: 7467k freed
[    0.445632] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.445759] cpufreq-nforce2: No nForce2 chipset.
[    0.445788] Scanning for low memory corruption every 60 seconds
[    0.445991] audit: initializing netlink socket (disabled)
[    0.446044] type=2000 audit(1269718050.443:1): initialized
[    0.457912] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.459821] VFS: Disk quotas dquot_6.5.2
[    0.459897] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.460695] fuse init (API version 7.12)
[    0.460798] msgmni has been set to 867
[    0.461080] alg: No test for stdrng (krng)
[    0.461096] io scheduler noop registered
[    0.461099] io scheduler anticipatory registered
[    0.461101] io scheduler deadline registered
[    0.461155] io scheduler cfq registered (default)
[    0.461180] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.461265] pci 0000:01:00.0: Boot video device
[    0.461388] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.461420] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.461581] isapnp: Scanning for PnP cards...
[    0.815628] isapnp: No Plug & Play device found
[    0.817016] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.818461] brd: module loaded
[    0.819079] loop: module loaded
[    0.819181] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.819938] pata_via 0000:00:11.1: version 0.3.4
[    0.820158] scsi0 : pata_via
[    0.820283] scsi1 : pata_via
[    0.820330] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.820334] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.820825] Fixed MDIO Bus: probed
[    0.820871] PPP generic driver version 2.4.2
[    0.820992] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.821018] PCI: setting IRQ 10 as level-triggered
[    0.821024] ehci_hcd 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.821077] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.821115] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.821169] ehci_hcd 0000:00:10.3: irq 10, io mem 0xf0000000
[    0.831980] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.832108] usb usb1: configuration #1 chosen from 1 choice
[    0.832148] hub 1-0:1.0: USB hub found
[    0.832160] hub 1-0:1.0: 6 ports detected
[    0.832233] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.832259] uhci_hcd: USB Universal Host Controller Interface driver
[    0.832309] PCI: setting IRQ 11 as level-triggered
[    0.832314] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.832349] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.832354] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.832365] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.832410] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.832437] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.832535] usb usb2: configuration #1 chosen from 1 choice
[    0.832568] hub 2-0:1.0: USB hub found
[    0.832578] hub 2-0:1.0: 2 ports detected
[    0.832638] PCI: setting IRQ 7 as level-triggered
[    0.832644] uhci_hcd 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.832685] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.832727] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.832753] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.832872] usb usb3: configuration #1 chosen from 1 choice
[    0.832905] hub 3-0:1.0: USB hub found
[    0.832914] hub 3-0:1.0: 2 ports detected
[    0.832970] PCI: setting IRQ 5 as level-triggered
[    0.832976] uhci_hcd 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.833005] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.833011] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.833023] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.833064] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.833090] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.833185] usb usb4: configuration #1 chosen from 1 choice
[    0.833218] hub 4-0:1.0: USB hub found
[    0.833226] hub 4-0:1.0: 2 ports detected
[    0.833344] PNP: No PS/2 controller found. Probing ports directly.
[    0.845644] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.851365] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.851374] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.851378] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.851381] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.851385] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.851455] mice: PS/2 mouse device common for all mice
[    0.851580] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.851610] rtc0: alarms up to one day, 114 bytes nvram
[    0.851751] device-mapper: uevent: version 1.0.3
[    0.851868] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.851965] device-mapper: multipath: version 1.1.0 loaded
[    0.851980] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.852144] EISA: Probing bus 0 at eisa.0
[    0.852153] Cannot allocate resource for EISA slot 1
[    0.852186] EISA: Detected 0 cards.
[    0.852244] cpuidle: using governor ladder
[    0.852247] cpuidle: using governor menu
[    0.852878] TCP cubic registered
[    0.853093] NET: Registered protocol family 10
[    0.853665] lo: Disabled Privacy Extensions
[    0.854058] NET: Registered protocol family 17
[    0.854083] Bluetooth: L2CAP ver 2.13
[    0.854085] Bluetooth: L2CAP socket layer initialized
[    0.854089] Bluetooth: SCO (Voice Link) ver 0.6
[    0.854092] Bluetooth: SCO socket layer initialized
[    0.854149] Bluetooth: RFCOMM TTY layer initialized
[    0.854154] Bluetooth: RFCOMM socket layer initialized
[    0.854156] Bluetooth: RFCOMM ver 1.11
[    0.854182] Using IPI No-Shortcut mode
[    0.854267] PM: Resume from disk failed.
[    0.854292] registered taskstats version 1
[    0.854417]   Magic number: 2:951:496
[    0.854530] rtc_cmos rtc_cmos: setting system clock to 2010-03-27 19:27:31 UTC (1269718051)
[    0.854535] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.854537] EDD information not available.
[    0.859886] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.984638] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    0.984643] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.000498] ata1.00: configured for UDMA/100
[    1.000699] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    1.000884] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.000941] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.001003] sd 0:0:0:0: [sda] Write Protect is off
[    1.001007] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.001039] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.001210]  sda: sda1 sda2 < sda5 >
[    1.055459] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.143989] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.164409] ata2.00: ATAPI: _NEC DVD+/-RW ND-6650A, 1.62, max UDMA/33
[    1.180283] ata2.00: configured for UDMA/33
[    1.197986] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6650A 1.62 PQ: 0 ANSI: 5
[    1.223994] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.223999] Uniform CD-ROM driver Revision: 3.20
[    1.224102] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.224166] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.224196] Freeing unused kernel memory: 540k freed
[    1.224677] Write protecting the kernel text: 4580k
[    1.224725] Write protecting the kernel read-only data: 1840k
[    1.328411] usb 1-3: configuration #1 chosen from 1 choice
[    1.383677] Linux agpgart interface v0.103
[    1.387461] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.426886] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xa0000000
[    1.456317] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.456402] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
[    1.456426] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
[    1.456448] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:01:00.0
[    1.475553] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:89:90:42, IRQ 11.
[    1.476276] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    2.683232] PM: Starting manual resume from disk
[    2.683239] PM: Resume from partition 8:5
[    2.683242] PM: Checking hibernation image.
[    2.683465] PM: Resume from disk failed.
[    2.733076] EXT4-fs (sda1): barriers enabled
[    2.769405] kjournald2 starting: pid 308, dev sda1:8, commit interval 5 seconds
[    2.769453] EXT4-fs (sda1): delayed allocation enabled
[    2.769458] EXT4-fs: file extents enabled
[    2.774849] EXT4-fs: mballoc enabled
[    2.774871] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.852401] type=1505 audit(1269718054.497:2): operation="profile_load" pid=332 name=/usr/share/gdm/guest-session/Xsession
[    3.855781] type=1505 audit(1269718054.497:3): operation="profile_load" pid=333 name=/sbin/dhclient3
[    3.856651] type=1505 audit(1269718054.501:4): operation="profile_load" pid=333 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.857113] type=1505 audit(1269718054.501:5): operation="profile_load" pid=333 name=/usr/lib/connman/scripts/dhclient-script
[    3.943497] type=1505 audit(1269718054.585:6): operation="profile_load" pid=334 name=/usr/bin/evince
[    3.957738] type=1505 audit(1269718054.601:7): operation="profile_load" pid=334 name=/usr/bin/evince-previewer
[    3.966281] type=1505 audit(1269718054.609:8): operation="profile_load" pid=334 name=/usr/bin/evince-thumbnailer
[    3.984727] type=1505 audit(1269718054.629:9): operation="profile_load" pid=336 name=/usr/lib/cups/backend/cups-pdf
[    3.985732] type=1505 audit(1269718054.629:10): operation="profile_load" pid=336 name=/usr/sbin/cupsd
[   18.563934] udev: starting version 147
[   18.574139] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k 
[   18.772039] irda_init()
[   18.772072] NET: Registered protocol family 23
[   18.778501] lib80211: common routines for IEEE802.11 drivers
[   18.778506] lib80211_crypt: registered algorithm 'NULL'
[   18.850205] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.850211] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.864001] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.926144] EXT4-fs (sda1): internal journal on sda1:8
[   18.934357] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.934367] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.934505] ipw2200 0000:00:06.0: enabling device (0000 -> 0002)
[   18.934516] ipw2200 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   18.934526] ipw2200 0000:00:06.0: setting latency timer to 64
[   18.934655] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.934661] ipw2200: Error allocating IRQ 0
[   18.934726] ipw2200: probe of 0000:00:06.0 failed with error -16
[   19.067319] cfg80211: Calling CRDA to update world regulatory domain
[   19.148475] cfg80211: World regulatory domain updated:
[   19.148481]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.148486]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.148490]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.148494]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.148497]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.148501]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.159106] lp: driver loaded but no devices found
[   19.169464] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.293182] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
[   19.293231] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.2
[   19.293243] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
[   19.299744] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   19.649996] __ratelimit: 3 callbacks suppressed
[   19.650003] type=1505 audit(1269718070.292:12): operation="profile_replace" pid=748 name=/usr/share/gdm/guest-session/Xsession
[   19.652492] type=1505 audit(1269718070.296:13): operation="profile_replace" pid=749 name=/sbin/dhclient3
[   19.653346] type=1505 audit(1269718070.296:14): operation="profile_replace" pid=749 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.653811] type=1505 audit(1269718070.296:15): operation="profile_replace" pid=749 name=/usr/lib/connman/scripts/dhclient-script
[   19.663957] type=1505 audit(1269718070.308:16): operation="profile_replace" pid=750 name=/usr/bin/evince
[   19.680525] type=1505 audit(1269718070.324:17): operation="profile_replace" pid=750 name=/usr/bin/evince-previewer
[   19.690845] type=1505 audit(1269718070.332:18): operation="profile_replace" pid=750 name=/usr/bin/evince-thumbnailer
[   19.721008] type=1505 audit(1269718070.364:19): operation="profile_replace" pid=752 name=/usr/lib/cups/backend/cups-pdf
[   19.722017] type=1505 audit(1269718070.364:20): operation="profile_replace" pid=752 name=/usr/sbin/cupsd
[   19.726262] type=1505 audit(1269718070.368:21): operation="profile_replace" pid=753 name=/usr/sbin/tcpdump
[   19.827250] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
[   19.827285] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.2
[   19.827299] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
[   19.827453] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.957245] eth0: link down
[   19.957313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.990650] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb3, caps: 0xa04713/0x0
[   20.015765] phy0: Selected rate control algorithm 'minstrel'
[   20.016631] phy0: hwaddr 00:1b:2f:73:88:d9, RTL8187vB (default) V1 + rtl8225z2
[   20.053702] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input2
[   20.183051] rtl8187: Customer ID is 0xFF
[   20.183145] Registered led device: rtl8187-phy0::tx
[   20.183176] Registered led device: rtl8187-phy0::rx
[   20.183215] usbcore: registered new interface driver rtl8187
[   20.635088] ppdev: user-space parallel port driver
[   22.236802] [drm] Initialized drm 1.1.0 20060810
[   22.241201] pci 0000:01:00.0: found PCI INT A -> IRQ 11
[   22.241222] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:10.0
[   22.241242] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:12.0
[   22.241498] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   22.246255] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   22.246286] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   22.246296] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   22.246383] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   27.393263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.671106] wlan0: authenticate with AP 00:8b:5d:82:2e:9a
[   61.673223] wlan0: authenticated
[   61.673226] wlan0: associate with AP 00:8b:5d:82:2e:9a
[   61.676197] wlan0: RX AssocResp from 00:8b:5d:82:2e:9a (capab=0x431 status=0 aid=1)
[   61.676205] wlan0: associated
[   61.680660] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.719296] padlock: VIA PadLock not detected.
[   72.378118] wlan0: no IPv6 routers present
daddy@daddy-laptop:~$ 


daddy@daddy-laptop:~$ sudo lshw -C network
[sudo] password for daddy: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: memory:1c000000-1c000fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:89:90:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1b:2f:73:88:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg
daddy@daddy-laptop:~$ 


daddy@daddy-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:8B:5D:82:2E:9A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-HFGP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c73175187
                    Extra: Last beacon: 19548ms ago
                    IE: Unknown: 000F4254486F6D65487562322D48464750
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
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
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010020000000

daddy@daddy-laptop:~$ 

daddy@daddy-laptop:~$ lsb_release -d
Description:    Ubuntu 9.10
daddy@daddy-laptop:~$ 
daddy@daddy-laptop:~$ 
daddy@daddy-laptop:~$ uname -mr
2.6.31-20-generic i686
daddy@daddy-laptop:~$ 
daddy@daddy-laptop:~$ 
daddy@daddy-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for daddy: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-27
Wow! *dmesg* has given you two possible solutions:> ipw2200 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
PnPBIOS: Check with your vendor for an updated BIOSHere is how to use a boot parameter, such as pci=biosirq: [http://ubuntuforums.org/showpost.php?p=8990468&postcount=4](http://ubuntuforums.org/showpost.php?p=8990468&postcount=4)

If that doesn't fix it, we have other options. You might check on a BIOS update.

---

### Post by RiversideAndy on 2010-03-27
Many thanks for the speedy reply

Added the boot parameter successfully but adapter still not available. Checked BIOS, already running latest version.

dmesg gives

[    0.000000] kernel direct mapping tables up to 1bfef000 @ 7000-c000
[    0.000000] RAMDISK: 148e8000 - 15032d91
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 1bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 1bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 1bffffc0 00040
[    0.000000] ACPI: APIC 1bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1bfef000
[    0.000000]   low ram: 0 - 1bfef000
[    0.000000]   node 0 low ram: 00000000 - 1bfef000
[    0.000000]   node 0 bootmap 00008000 - 0000b800
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001bfef000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [00148e8000 - 0015032d91]          RAMDISK ==> [00148e8000 - 0015032d91]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b11bc]              BRK ==> [00008ae000 - 00008b11bc]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001bfef
[    0.000000]   HighMem  0x0001bfef -> 0x0001bfef
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bfef
[    0.000000] On node 0 totalpages: 114570
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 864 pages used for memmap
[    0.000000]   Normal zone: 109711 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1c000000 (gap: 1c000000:e3f80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1382000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113674
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=b7ce5ae7-62d3-4dff-b238-1617eaacc94e ro pci=biosirq quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2293420 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 436352k/458684k available (4578k kernel code, 21664k reserved, 2146k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdc7ef000 - 0xff7fe000   ( 560 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbfef000   ( 447 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.559 MHz processor.
[    0.001475] Console: colour VGA+ 80x25
[    0.001480] console [tty0] enabled
[    0.001546] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.11 BogoMIPS (lpj=5970236)
[    0.001574] Security Framework initialized
[    0.001609] AppArmor: AppArmor initialized
[    0.001620] Mount-cache hash table entries: 512
[    0.001803] Initializing cgroup subsys ns
[    0.001811] Initializing cgroup subsys cpuacct
[    0.001817] Initializing cgroup subsys memory
[    0.001829] Initializing cgroup subsys freezer
[    0.001832] Initializing cgroup subsys net_cls
[    0.001855] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001859] CPU: L2 cache: 1024K
[    0.001866] mce: CPU supports 5 MCE banks
[    0.001878] CPU0: Thermal monitoring enabled (TM1)
[    0.001890] Performance Counters: p6 PMU driver.
[    0.001911] ... version:                 0
[    0.001914] ... bit width:               32
[    0.001916] ... generic counters:        2
[    0.001919] ... value mask:              00000000ffffffff
[    0.001922] ... max period:              000000007fffffff
[    0.001924] ... fixed-purpose counters:  0
[    0.001927] ... counter mask:            0000000000000003
[    0.001933] Checking 'hlt' instruction... OK.
[    0.017162] SMP alternatives: switching to UP code
[    0.024021] Freeing SMP alternatives: 20k freed
[    0.024138] weird, boot CPU (#0) not listed by the BIOS.
[    0.024141] SMP motherboard not detected.
[    0.132022] SMP disabled
[    0.132197] Brought up 1 CPUs
[    0.132201] Total of 1 processors activated (2985.11 BogoMIPS).
[    0.132220] CPU0 attaching NULL sched-domain.
[    0.132553] Booting paravirtualized kernel on bare hardware
[    0.132827] regulator: core version 0.5
[    0.152688] Time: 23:18:54  Date: 03/27/10
[    0.152765] NET: Registered protocol family 16
[    0.152952] EISA bus registered
[    0.153134] PCI: PCI BIOS revision 2.10 entry at 0xe9b04, last bus=1
[    0.153138] PCI: Using configuration type 1 for base access
[    0.154511] bio: create slab <bio-0> at 0
[    0.154588] ACPI: Interpreter disabled.
[    0.154766] SCSI subsystem initialized
[    0.154816] libata version 3.00 loaded.
[    0.154908] usbcore: registered new interface driver usbfs
[    0.154925] usbcore: registered new interface driver hub
[    0.154957] usbcore: registered new device driver usb
[    0.155098] PCI: Probing PCI hardware
[    0.155102] PCI: Probing PCI hardware (bus 00)
[    0.155162] pci 0000:00:00.0: reg 10 32bit mmio: [0xa0000000-0xa1ffffff]
[    0.155535] pci 0000:00:01.0: supports D1
[    0.155582] pci 0000:00:06.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.155639] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.155645] pci 0000:00:06.0: PME# disabled
[    0.155719] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.155752] pci 0000:00:10.0: supports D1 D2
[    0.155755] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155761] pci 0000:00:10.0: PME# disabled
[    0.155821] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.155854] pci 0000:00:10.1: supports D1 D2
[    0.155857] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155863] pci 0000:00:10.1: PME# disabled
[    0.155923] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.155956] pci 0000:00:10.2: supports D1 D2
[    0.155959] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155965] pci 0000:00:10.2: PME# disabled
[    0.156009] pci 0000:00:10.3: reg 10 32bit mmio: [0xf0000000-0xf00000ff]
[    0.156064] pci 0000:00:10.3: supports D1 D2
[    0.156068] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156073] pci 0000:00:10.3: PME# disabled
[    0.156155] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.156164] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.156170] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.156250] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.156330] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.156386] pci 0000:00:11.5: supports D1 D2
[    0.156428] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.156523] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.156533] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.156583] pci 0000:00:12.0: supports D1 D2
[    0.156586] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156592] pci 0000:00:12.0: PME# disabled
[    0.156659] pci 0000:01:00.0: reg 10 32bit mmio: [0x90000000-0x93ffffff]
[    0.156667] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.156692] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.156714] pci 0000:01:00.0: supports D1 D2
[    0.156761] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.156767] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.156773] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.157373] pci 0000:00:11.0: VIA IRQ router [1106:3177]
[    0.157602] Bluetooth: Core ver 2.15
[    0.157653] NET: Registered protocol family 31
[    0.157656] Bluetooth: HCI device and connection manager initialized
[    0.157661] Bluetooth: HCI socket layer initialized
[    0.157664] NetLabel: Initializing
[    0.157666] NetLabel:  domain hash size = 128
[    0.157668] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.157689] NetLabel:  unlabeled traffic allowed by default
[    0.160411] pnp: PnP ACPI: disabled
[    0.160427] PnPBIOS: Scanning system for PnP BIOS support...
[    0.160539] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    0.160543] PnPBIOS: PnP BIOS version 1.0, entry 0xeb000:0x3536, dseg 0xeb000
[    0.160553] PNPBIOS fault.. attempting recovery.
[    0.160556] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.160559] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.160562] PnPBIOS: Check with your vendor for an updated BIOS
[    0.160566] PnPBIOS: dev_node_info: unexpected status 0x3a
[    0.160568] PnPBIOS: Unable to get node info.  Aborting.
[    0.160838] AppArmor: AppArmor Filesystem Enabled
[    0.160893] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.160898] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.160905] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.160912] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.160933] pci 0000:00:01.0: setting latency timer to 64
[    0.160940] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.160944] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.160948] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.160952] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.160955] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.161012] NET: Registered protocol family 2
[    0.161156] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.161526] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.161703] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.161912] TCP: Hash tables configured (established 16384 bind 16384)
[    0.161916] TCP reno registered
[    0.162049] NET: Registered protocol family 1
[    0.162158] Trying to unpack rootfs image as initramfs...
[    0.449462] Freeing initrd memory: 7467k freed
[    0.460394] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.460521] cpufreq-nforce2: No nForce2 chipset.
[    0.460550] Scanning for low memory corruption every 60 seconds
[    0.460749] audit: initializing netlink socket (disabled)
[    0.460802] type=2000 audit(1269731933.460:1): initialized
[    0.472670] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.474584] VFS: Disk quotas dquot_6.5.2
[    0.474662] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.475433] fuse init (API version 7.12)
[    0.475535] msgmni has been set to 867
[    0.475817] alg: No test for stdrng (krng)
[    0.475833] io scheduler noop registered
[    0.475836] io scheduler anticipatory registered
[    0.475838] io scheduler deadline registered
[    0.475892] io scheduler cfq registered (default)
[    0.475917] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.476002] pci 0000:01:00.0: Boot video device
[    0.476143] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.476176] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.476337] isapnp: Scanning for PnP cards...
[    0.830387] isapnp: No Plug & Play device found
[    0.831769] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.833232] brd: module loaded
[    0.833852] loop: module loaded
[    0.833955] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.834715] pata_via 0000:00:11.1: version 0.3.4
[    0.834914] scsi0 : pata_via
[    0.835039] scsi1 : pata_via
[    0.835086] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.835090] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.835582] Fixed MDIO Bus: probed
[    0.835630] PPP generic driver version 2.4.2
[    0.835747] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.835773] PCI: setting IRQ 10 as level-triggered
[    0.835779] ehci_hcd 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.835832] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.835871] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.835924] ehci_hcd 0000:00:10.3: irq 10, io mem 0xf0000000
[    0.844079] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.844208] usb usb1: configuration #1 chosen from 1 choice
[    0.844247] hub 1-0:1.0: USB hub found
[    0.844259] hub 1-0:1.0: 6 ports detected
[    0.844333] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.844358] uhci_hcd: USB Universal Host Controller Interface driver
[    0.844408] PCI: setting IRQ 11 as level-triggered
[    0.844413] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.844448] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.844453] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.844463] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.844508] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.844535] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.844634] usb usb2: configuration #1 chosen from 1 choice
[    0.844667] hub 2-0:1.0: USB hub found
[    0.844676] hub 2-0:1.0: 2 ports detected
[    0.844735] PCI: setting IRQ 7 as level-triggered
[    0.844740] uhci_hcd 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.844782] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.844823] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.844850] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.844966] usb usb3: configuration #1 chosen from 1 choice
[    0.844998] hub 3-0:1.0: USB hub found
[    0.845008] hub 3-0:1.0: 2 ports detected
[    0.845063] PCI: setting IRQ 5 as level-triggered
[    0.845068] uhci_hcd 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.845098] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.845104] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.845116] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.845158] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.845183] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.845278] usb usb4: configuration #1 chosen from 1 choice
[    0.845310] hub 4-0:1.0: USB hub found
[    0.845319] hub 4-0:1.0: 2 ports detected
[    0.845436] PNP: No PS/2 controller found. Probing ports directly.
[    0.857627] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.863396] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.863405] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.863409] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.863413] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.863417] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.863487] mice: PS/2 mouse device common for all mice
[    0.863613] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.863643] rtc0: alarms up to one day, 114 bytes nvram
[    0.863784] device-mapper: uevent: version 1.0.3
[    0.863904] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.864002] device-mapper: multipath: version 1.1.0 loaded
[    0.864006] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.864176] EISA: Probing bus 0 at eisa.0
[    0.864185] Cannot allocate resource for EISA slot 1
[    0.864218] EISA: Detected 0 cards.
[    0.864277] cpuidle: using governor ladder
[    0.864280] cpuidle: using governor menu
[    0.864911] TCP cubic registered
[    0.865126] NET: Registered protocol family 10
[    0.865702] lo: Disabled Privacy Extensions
[    0.866083] NET: Registered protocol family 17
[    0.866107] Bluetooth: L2CAP ver 2.13
[    0.866110] Bluetooth: L2CAP socket layer initialized
[    0.866114] Bluetooth: SCO (Voice Link) ver 0.6
[    0.866116] Bluetooth: SCO socket layer initialized
[    0.866169] Bluetooth: RFCOMM TTY layer initialized
[    0.866174] Bluetooth: RFCOMM socket layer initialized
[    0.866176] Bluetooth: RFCOMM ver 1.11
[    0.866202] Using IPI No-Shortcut mode
[    0.866286] PM: Resume from disk failed.
[    0.866312] registered taskstats version 1
[    0.866454]   Magic number: 2:722:353
[    0.866568] rtc_cmos rtc_cmos: setting system clock to 2010-03-27 23:18:54 UTC (1269731934)
[    0.866573] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.866575] EDD information not available.
[    0.872209] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.000765] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    1.000770] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.016623] ata1.00: configured for UDMA/100
[    1.016831] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    1.017013] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.017070] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.017132] sd 0:0:0:0: [sda] Write Protect is off
[    1.017136] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.017168] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.017342]  sda: sda1 sda2 < sda5 >
[    1.065428] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.156119] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.180561] ata2.00: ATAPI: _NEC DVD+/-RW ND-6650A, 1.62, max UDMA/33
[    1.196434] ata2.00: configured for UDMA/33
[    1.198580] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6650A 1.62 PQ: 0 ANSI: 5
[    1.201403] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.201409] Uniform CD-ROM driver Revision: 3.20
[    1.201511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.201576] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.201605] Freeing unused kernel memory: 540k freed
[    1.202092] Write protecting the kernel text: 4580k
[    1.202141] Write protecting the kernel read-only data: 1840k
[    1.312724] usb 1-3: configuration #1 chosen from 1 choice
[    1.359653] Linux agpgart interface v0.103
[    1.363439] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.404499] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xa0000000
[    1.415362] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.415443] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
[    1.415467] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
[    1.415488] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:01:00.0
[    1.425099] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:89:90:42, IRQ 11.
[    1.425818] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    2.620669] PM: Starting manual resume from disk
[    2.620676] PM: Resume from partition 8:5
[    2.620679] PM: Checking hibernation image.
[    2.622395] PM: Resume from disk failed.
[    2.671946] EXT4-fs (sda1): barriers enabled
[    2.694063] kjournald2 starting: pid 316, dev sda1:8, commit interval 5 seconds
[    2.694110] EXT4-fs (sda1): delayed allocation enabled
[    2.694115] EXT4-fs: file extents enabled
[    2.699515] EXT4-fs: mballoc enabled
[    2.699537] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.762838] type=1505 audit(1269731937.393:2): operation="profile_load" pid=340 name=/usr/share/gdm/guest-session/Xsession
[    3.766211] type=1505 audit(1269731937.397:3): operation="profile_load" pid=341 name=/sbin/dhclient3
[    3.767061] type=1505 audit(1269731937.397:4): operation="profile_load" pid=341 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.767523] type=1505 audit(1269731937.397:5): operation="profile_load" pid=341 name=/usr/lib/connman/scripts/dhclient-script
[    3.854083] type=1505 audit(1269731937.485:6): operation="profile_load" pid=342 name=/usr/bin/evince
[    3.868316] type=1505 audit(1269731937.497:7): operation="profile_load" pid=342 name=/usr/bin/evince-previewer
[    3.876721] type=1505 audit(1269731937.509:8): operation="profile_load" pid=342 name=/usr/bin/evince-thumbnailer
[    3.895161] type=1505 audit(1269731937.525:9): operation="profile_load" pid=344 name=/usr/lib/cups/backend/cups-pdf
[    3.896172] type=1505 audit(1269731937.525:10): operation="profile_load" pid=344 name=/usr/sbin/cupsd
[   18.626423] udev: starting version 147
[   18.641140] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k 
[   18.795743] irda_init()
[   18.795772] NET: Registered protocol family 23
[   18.801930] lib80211: common routines for IEEE802.11 drivers
[   18.801935] lib80211_crypt: registered algorithm 'NULL'
[   18.892652] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.892658] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.911747] EXT4-fs (sda1): internal journal on sda1:8
[   18.942020] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.942026] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.942136] ipw2200 0000:00:06.0: enabling device (0000 -> 0002)
[   18.942148] ipw2200 0000:00:06.0: can't find IRQ for PCI INT A
[   18.942158] ipw2200 0000:00:06.0: setting latency timer to 64
[   18.969323] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.969332] ipw2200: Error allocating IRQ 0
[   18.969425] ipw2200: probe of 0000:00:06.0 failed with error -16
[   18.969531] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.144167] lp: driver loaded but no devices found
[   19.195930] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
[   19.195960] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.2
[   19.195972] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
[   19.212162] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   19.212692] cfg80211: Calling CRDA to update world regulatory domain
[   19.275990] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.290655] cfg80211: World regulatory domain updated:
[   19.290662]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.290667]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.290671]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.290675]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.290678]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.290682]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.531345] phy0: Selected rate control algorithm 'minstrel'
[   19.532215] phy0: hwaddr 00:1b:2f:73:88:d9, RTL8187vB (default) V1 + rtl8225z2
[   19.715742] rtl8187: Customer ID is 0xFF
[   19.715826] Registered led device: rtl8187-phy0::tx
[   19.715850] Registered led device: rtl8187-phy0::rx
[   19.715888] usbcore: registered new interface driver rtl8187
[   19.729471] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
[   19.729506] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.2
[   19.729520] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
[   19.729674] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.976249] __ratelimit: 3 callbacks suppressed
[   19.976256] type=1505 audit(1269731953.607:12): operation="profile_replace" pid=785 name=/usr/share/gdm/guest-session/Xsession
[   19.992881] type=1505 audit(1269731953.623:13): operation="profile_replace" pid=790 name=/sbin/dhclient3
[   19.993739] type=1505 audit(1269731953.623:14): operation="profile_replace" pid=790 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.994208] type=1505 audit(1269731953.623:15): operation="profile_replace" pid=790 name=/usr/lib/connman/scripts/dhclient-script
[   20.011862] type=1505 audit(1269731953.643:16): operation="profile_replace" pid=792 name=/usr/bin/evince
[   20.037885] type=1505 audit(1269731953.667:17): operation="profile_replace" pid=792 name=/usr/bin/evince-previewer
[   20.051080] type=1505 audit(1269731953.683:18): operation="profile_replace" pid=792 name=/usr/bin/evince-thumbnailer
[   20.069711] type=1505 audit(1269731953.699:19): operation="profile_replace" pid=809 name=/usr/lib/cups/backend/cups-pdf
[   20.076233] type=1505 audit(1269731953.707:20): operation="profile_replace" pid=809 name=/usr/sbin/cupsd
[   20.079592] type=1505 audit(1269731953.711:21): operation="profile_replace" pid=811 name=/usr/sbin/tcpdump
[   20.242690] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb3, caps: 0xa04713/0x0
[   20.306420] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input2
[   20.569505] ppdev: user-space parallel port driver
[   22.159512] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.162347] eth0: link down
[   22.162410] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.480503] [drm] Initialized drm 1.1.0 20060810
[   23.484900] pci 0000:01:00.0: found PCI INT A -> IRQ 11
[   23.484923] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:10.0
[   23.484942] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:12.0
[   23.485190] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   23.490031] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.490060] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   23.490070] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   23.490161] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   40.333575] wlan0: authenticate with AP 00:8b:5d:82:2e:9a
[   40.335942] wlan0: authenticated
[   40.335946] wlan0: associate with AP 00:8b:5d:82:2e:9a
[   40.338582] wlan0: RX AssocResp from 00:8b:5d:82:2e:9a (capab=0x431 status=0 aid=1)
[   40.338587] wlan0: associated
[   40.341191] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.384126] padlock: VIA PadLock not detected.
[   50.638122] wlan0: no IPv6 routers present
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-27
Please change the GRUB parameter to:```
GRUB_CMDLINE_LINUX="acpi=force irqpoll"
```Reboot and let us know.

---

### Post by RiversideAndy on 2010-03-27
Getting there, adapter now shows in network manager although marked disabled and greyed out. Enable wireless checkbox also greyed out. Sysem seems to have become slower and more unstable on reboot...

lshw - C network gives

daddy@daddy-laptop:~$ sudo lshw -C network
[sudo] password for daddy: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth1
       version: 05
       serial: 00:15:00:28:ec:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:19 memory:1c000000-1c000fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:89:90:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:e200(size=256) memory:d0000000-d00000ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1b:2f:73:88:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg



Spotted "wireless=radio off" so tried:
daddy@daddy-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-27
Do things improve if you unplug the USB wireless?

---

### Post by RiversideAndy on 2010-03-27
Touchpad and keyboard intermittent on reboot, system hangs. Boots OK from hard shutdown...

---

### Post by RiversideAndy on 2010-03-27
"Do things improve if you unplug the USB wireless?""""""""""""

Yes, much. Now on wired connection.

Wireless networks still show disconnected

lshw -C network gives:

daddy@daddy-laptop:~$ sudo lshw -C network
[sudo] password for daddy: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth1
       version: 05
       serial: 00:15:00:28:ec:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:19 memory:1c000000-1c000fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:89:90:42
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.68 latency=128 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e200(size=256) memory:d0000000-d00000ff
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-27
> Wireless networks still show disconnected> ip=192.168.1.68 Network Manager is designed to disconnect the wireless if you have the wired connected.

---

### Post by RiversideAndy on 2010-03-27
Unplugged to no avail. Booted with cable unplugged to no avail.

Is this significant? There is no hard switch for wireless...

"wireless=radio off"

---

### Post by chili555 on 2010-03-27
It means either that there is a soft switch, Fn+F4, for example, or that the kernel doesn't recognize the radio condition; sometimes an ACPI issue. Oops!

Wouldn't it be a lot easier to just enjoy your trusty Netgear?

---

### Post by RiversideAndy on 2010-03-28
I could, but it's really annoying having an "appendage" sticking out the side of the laptop. It's been beaten and bent so many times that it is bound to stop working soon!

---

### Post by chili555 on 2010-03-28
Let's take a look at:```
dmesg | grep -e ACPI -e -i error
```Thanks.

---

### Post by RiversideAndy on 2010-03-28
Results as below, many thanks

daddy@daddy-laptop:~$ dmesg | grep -e ACPI -e -i error
grep: error: No such file or directory
daddy@daddy-laptop:~$ dmesg | grep -e ACPI -e -i error
grep: error: No such file or directory
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-28
Sorry.```
dmesg | grep -e ACPI -e Error
```

---

### Post by RiversideAndy on 2010-03-28
daddy@daddy-laptop:~$ dmesg | grep -e ACPI -e Error
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.000000]  modified: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  modified: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 1bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 1bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 1bffffc0 00040
[    0.000000] ACPI: APIC 1bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.028015] ACPI: Core revision 20090521
[    0.084001] ACPI: bus type pci registered
[    0.084001] ACPI: EC: Look up EC in DSDT
[    0.088743] ACPI: Interpreter enabled
[    0.088758] ACPI: (supports S0 S1 S3 S4 S5)
[    0.088791] ACPI: Using IOAPIC for interrupt routing
[    0.089070] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.118583] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    0.118587] ACPI: EC: driver started in interrupt mode
[    0.118790] ACPI: No dock devices found.
[    0.118987] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.120682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.137561] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.137715] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[    0.137865] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.138014] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[    0.138141] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.138268] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.138395] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.138522] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.138664] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[    0.138831] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[    0.139075] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[    0.139162] ACPI Warning: \_SB_.PCI0.ALKD._CRS: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    0.139171] ACPI Error (uteval-0313): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db8137e0), AE_TYPE
[    0.139182] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 20090521 uteval-319
[    0.139190] ACPI Exception: AE_TYPE, Evaluating _CRS 20090521 pci_link-280
[    0.139195] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[    0.139876] ACPI: WMI: Mapper loaded
[    0.139879] PCI: Using ACPI for IRQ routing
[    0.142867] pnp: PnP ACPI init
[    0.142906] ACPI: bus type pnp registered
[    0.150790] pnp: PnP ACPI: found 9 devices
[    0.150794] ACPI: ACPI bus type pnp unregistered
[    0.150802] PnPBIOS: Disabled by ACPI PNP
[    0.507252] ACPI: AC Adapter [AC] (on-line)
[    0.507359] ACPI: Power Button [PWRF]
[    0.513495] ACPI: Lid Switch [LID]
[    0.513571] ACPI: Sleep Button [SBTN]
[    0.513903] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.513942] ACPI: Processor [CPU0] (supports 16 throttling states)
[    0.533910] ACPI: Thermal Zone [TZ0] (0 C)
[    0.893096] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    0.893169] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.893173] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.920974] ACPI Error (uteval-0313): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db8137e0), AE_TYPE
[    0.920986] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 20090521 uteval-319
[    0.920994] ACPI Exception: AE_TYPE, Evaluating _CRS 20090521 pci_link-280
[    0.921000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.932428] ACPI Error (uteval-0313): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db8137e0), AE_TYPE
[    0.932439] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 20090521 uteval-319
[    0.932447] ACPI Exception: AE_TYPE, Evaluating _CRS 20090521 pci_link-280
[    0.932453] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.932874] ACPI Error (uteval-0313): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db8137e0), AE_TYPE
[    0.932885] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 20090521 uteval-319
[    0.932892] ACPI Exception: AE_TYPE, Evaluating _CRS 20090521 pci_link-280
[    0.932898] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.933297] ACPI Error (uteval-0313): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db8137e0), AE_TYPE
[    0.933307] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 20090521 uteval-319
[    0.933314] ACPI Exception: AE_TYPE, Evaluating _CRS 20090521 pci_link-280
[    0.933320] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.996267] ACPI: Battery Slot [BAT0] (battery present)
[    1.604143] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[    1.654842] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[    1.654850] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[   10.901002] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   10.901219] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[   10.901223] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   11.419649] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   13.063087] ACPI: I/O resource vt596_smbus [0x1400-0x1407] conflicts with ACPI region SM06 [0x1406-0x1406]
[   13.063095] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.232115] pci 0000:01:00.0: power state changed by ACPI to D0
daddy@daddy-laptop:~$

---

### Post by chili555 on 2010-03-28
Man! There are a lot of troubling things here, for example:> ACPI Warning: \_SB_.PCI0.ALKD._CRS: Return type mismatch
ACPI: Unable to set IRQ for PCI Interrupt Link
ACPI Error (uteval-0313): Return object type is incorrectAnd more. It now suggests:> ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or [COLOR="Red"]acpi=off[/COLOR]In my experience, this sometimes helps and sometimes hurts. You could try and we can easily reverse it. I suggest removing the previous options in GRUB and substituting acpi=off.

Do you have any IRQ options in your BIOS? How are they set? Please see attached.

---

### Post by RiversideAndy on 2010-03-28
With ACPI=off

daddy@daddy-laptop:~$ dmesg | grep -e ACPI -e Error
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.000000]  modified: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  modified: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.138744] ACPI: Interpreter disabled.
[    0.144514] pnp: PnP ACPI: disabled
[   11.593706] ipw2200: Error allocating IRQ 0
daddy@daddy-laptop:~$

---

### Post by RiversideAndy on 2010-03-28
Very limited options in BIOS. No ACPI options.

---

### Post by chili555 on 2010-03-28
I am sorry I could not be more help. I have no more ammo.

---

### Post by RiversideAndy on 2010-03-28
With pci=noapci

daddy@daddy-laptop:~$ dmesg | grep -e ACPI -e Error
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.000000]  modified: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[    0.000000]  modified: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 1bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 1bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 1bffffc0 00040
[    0.000000] ACPI: APIC 1bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.138759] ACPI: Interpreter disabled.
[    0.144518] pnp: PnP ACPI: disabled
[   11.633238] ipw2200: Error allocating IRQ 0
daddy@daddy-laptop:~$

---

