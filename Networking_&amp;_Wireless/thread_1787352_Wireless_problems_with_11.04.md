---
title: "Wireless problems with 11.04"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by pookieman123 on 2011-06-21
Hi

I just installed 11.04 on my laptop VGN-A197VP. I had it working fine when the machine had it's hard disk in it, since then I installed a CF (IDE) drive - it's only 4GB, but I managed to install ubuntu fine once I did the minimal installation then I chose ubuntu desktop, admittedly I have no space, but that's ok.

Anyway my wireless won't connect, during the installation I had to turn my WPA security off, after which the installation managed to connect and pull down the files it needed. I've since put WPA 2 back on and now although ubuntu seems to function fine, I see no networks.

I'm fairly new, but I've managed to get the following information using a variety of commands I googled. Incidently I have confirmed the physical wi-fi switch is on.

These are results of some diagnostics I ran:

nmtool

> 
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        08:00:46:DB:0F:85

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unmanaged
  Default:           no
  HW Address:        00:0E:35:1E:C1:B6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

lshw
> 
  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:1e:c1:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:7 memory:ff6fd000-ff6fdfff
  *-network:1
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 00
       serial: 08:00:46:db:0f:85
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:9 memory:ff6c0000-ff6dffff memory:ff6a0000-ff6bffff ioport:dc00(size=64) memory:ff680000-ff69ffff
lsmod:

> Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
rfcomm                 38125  8 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                896428  2 
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ipw2200               145664  0 
ttm                    65184  1 radeon
sco                    17779  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
libipw                 46641  1 ipw2200
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
tifm_sd                17415  0 
pcmcia                 39671  0 
binfmt_misc            13213  1 
btusb                  18160  2 
cfg80211              156212  2 ipw2200,libipw
drm                   180037  4 radeon,ttm,drm_kms_helper
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
tifm_7xx1              12898  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  2 tifm_sd,tifm_7xx1
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sony_laptop            34432  0 
i2c_algo_bit           13184  1 radeon
asus_laptop            19298  0 
lib80211               14570  2 ipw2200,libipw
serio_raw              12990  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
sparse_keymap          13666  1 asus_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
e1000                 101089  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
uas                    17676  0 
rfkill

> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
So as far as I can tell, there is a wireless adaptor, it's turned on, it's got a driver which is loaded and it's not physically disabled, so what is going on?? Why can't I see any networks?

thanks in advance for any help really appreciate it.

more info

> lspci:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:01.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:01.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:03.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:04.0 USB Controller: NEC Corporation USB (rev 43)
02:04.1 USB Controller: NEC Corporation USB (rev 43)
02:04.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
> 
ifconfig:

eth0      Link encap:Ethernet  HWaddr 08:00:46:db:0f:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:1e:c1:b6  
          inet6 addr: fe80::20e:35ff:fe1e:c1b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:44109 (44.1 KB)
          Interrupt:7 Memory:ff6fd000-ff6fdfff 

eth1:avahi Link encap:Ethernet  HWaddr 00:0e:35:1e:c1:b6  
          inet addr:169.254.8.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 Memory:ff6fd000-ff6fdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3928 (3.9 KB)  TX bytes:3928 (3.9 KB)


I then ran

 > sudo iwconfig eth1 mode Managed
  sudo iwconfig eth1 essid "pookies"
  iwconfig eth1


and got

 > iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"pookies"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by pookieman123 on 2011-06-21
More info

dmesg

> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc  version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11  03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff40000 (usable)
[    0.000000]  BIOS-e820: 000000002ff40000 - 000000002ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff50000 - 0000000030000000 (ACPI NVS)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Sony Corporation VGN-A197VP(GB), BIOS R0080F1 09/28/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x2ff40 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002ff40000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002fc00000 page 2M
[    0.000000]  002fc00000 - 002ff40000 page 4k
[    0.000000] kernel direct mapping tables up to 2ff40000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 2ebb0000 - 2f7e8000
[    0.000000] ACPI: RSDP 000f53f0 00014 (v00 SONY  )
[    0.000000] ACPI: RSDT 2ff40000 0002C (v01   SONY       F1 20040928 MSFT 00000097)
[    0.000000] ACPI: FACP 2ff40200 00084 (v02   SONY       F1 20040928 MSFT 00000097)
[    0.000000] ACPI: DSDT 2ff40500 03B58 (v01   SONY       F1 20040928 MSFT 0100000D)
[    0.000000] ACPI: FACS 2ff50000 00040
[    0.000000] ACPI: OEMB 2ff50040 00053 (v01   SONY       F1 20040928 MSFT 00000097)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2ff40000
[    0.000000]   low ram: 0 - 2ff40000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002ff40
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002ff40
[    0.000000] On node 0 totalpages: 196303
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map ef93f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190817 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:d0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @ee400000 s28800 r0 d24448 u4194304
[    0.000000] pcpu-alloc: s28800 r0 d24448 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194768
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic  root=UUID=422e78c4-cc28-4137-a994-e2c293fbef9e ro splash quiet  vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3928000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 752480k/785664k available (5188k kernel code, 32732k reserved, 2540k data, 700k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf0740000 - 0xff7fe000   ( 240 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xeff40000   ( 767 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=ee006000 soft=ee008000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1694.527 MHz processor.
[    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3389.05 BogoMIPS (lpj=6778108)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008037] Security Framework initialized
[    0.008063] AppArmor: AppArmor initialized
[    0.008066] Yama: becoming mindful.
[    0.008139] Mount-cache hash table entries: 512
[    0.008304] Initializing cgroup subsys ns
[    0.008309] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008312] Initializing cgroup subsys cpuacct
[    0.008318] Initializing cgroup subsys memory
[    0.008332] Initializing cgroup subsys devices
[    0.008335] Initializing cgroup subsys freezer
[    0.008338] Initializing cgroup subsys net_cls
[    0.008341] Initializing cgroup subsys blkio
[    0.008388] mce: CPU supports 5 MCE banks
[    0.008399] CPU0: Thermal monitoring enabled (TM2)
[    0.009165] SMP alternatives: switching to UP code
[    0.018344] Freeing SMP alternatives: 20k freed
[    0.018352] ACPI: Core revision 20110112
[    0.021682] ACPI: setting ELCR to 0200 (from 02b8)
[    0.023666] ftrace: allocating 23640 entries in 47 pages
[    0.028086] weird, boot CPU (#0) not listed by the BIOS.
[    0.028091] SMP motherboard not detected.
[    0.028094] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.032001] SMP disabled
[    0.032001] Performance Events: p6 PMU driver.
[    0.032001] ... version:                0
[    0.032001] ... bit width:              32
[    0.032001] ... generic registers:      2
[    0.032001] ... value mask:             00000000ffffffff
[    0.032001] ... max period:             000000007fffffff
[    0.032001] ... fixed-purpose events:   0
[    0.032001] ... event mask:             0000000000000003
[    0.032001] Brought up 1 CPUs
[    0.032001] Total of 1 processors activated (3389.05 BogoMIPS).
[    0.032001] devtmpfs: initialized
[    0.032001] print_constraints: dummy: 
[    0.032001] Time:  6:06:24  Date: 06/21/11
[    0.032001] NET: Registered protocol family 16
[    0.032001] EISA bus registered
[    0.032001] ACPI: bus type pci registered
[    0.032008] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.032011] PCI: Using configuration type 1 for base access
[    0.033327] bio: create slab <bio-0> at 0
[    0.034602] ACPI: EC: Look up EC in DSDT
[    0.038541] ACPI: Interpreter enabled
[    0.038549] ACPI: (supports S0 S3 S4 S5)
[    0.038577] ACPI: Using PIC for interrupt routing
[    0.044246] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.044389] ACPI: No dock devices found.
[    0.044392] HEST: Table not found.
[    0.044397] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.044488] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.044680] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.044684] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.044688] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.044692] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.044695] pci_root PNP0A03:00: host bridge window [mem 0x30000000-0xffffffff] (ignored)
[    0.044711] pci 0000:00:00.0: [8086:3340] type 0 class 0x000600
[    0.044720] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.044760] pci 0000:00:01.0: [8086:3341] type 1 class 0x000604
[    0.044818] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
[    0.044863] pci 0000:00:1d.0: reg 20: [io  0xe800-0xe81f]
[    0.044897] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
[    0.044941] pci 0000:00:1d.1: reg 20: [io  0xe880-0xe89f]
[    0.044975] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
[    0.045020] pci 0000:00:1d.2: reg 20: [io  0xec00-0xec1f]
[    0.045067] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
[    0.045089] pci 0000:00:1d.7: reg 10: [mem 0xff7ffc00-0xff7fffff]
[    0.045170] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.045176] pci 0000:00:1d.7: PME# disabled
[    0.045194] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.045237] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
[    0.045316] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
[    0.045330] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.045341] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.045351] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.045362] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.045373] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.045383] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.045412] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
[    0.045456] pci 0000:00:1f.3: reg 20: [io  0x0540-0x055f]
[    0.045494] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
[    0.045510] pci 0000:00:1f.5: reg 10: [io  0xee00-0xeeff]
[    0.045520] pci 0000:00:1f.5: reg 14: [io  0xe000-0xe03f]
[    0.045530] pci 0000:00:1f.5: reg 18: [mem 0xff7ff800-0xff7ff9ff]
[    0.045540] pci 0000:00:1f.5: reg 1c: [mem 0xff7ff400-0xff7ff4ff]
[    0.045578] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.045583] pci 0000:00:1f.5: PME# disabled
[    0.045600] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
[    0.045616] pci 0000:00:1f.6: reg 10: [io  0xe400-0xe4ff]
[    0.045627] pci 0000:00:1f.6: reg 14: [io  0xe080-0xe0ff]
[    0.045679] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.045684] pci 0000:00:1f.6: PME# disabled
[    0.045710] pci 0000:01:00.0: [1002:4e50] type 0 class 0x000300
[    0.045726] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.045734] pci 0000:01:00.0: reg 14: [io  0xc800-0xc8ff]
[    0.045743] pci 0000:01:00.0: reg 18: [mem 0xff5f0000-0xff5fffff]
[    0.045768] pci 0000:01:00.0: reg 30: [mem 0xff5c0000-0xff5dffff pref]
[    0.045788] pci 0000:01:00.0: supports D1 D2
[    0.045822] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.045827] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.045831] pci 0000:00:01.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.045836] pci 0000:00:01.0:   bridge window [mem 0xce900000-0xde9fffff pref]
[    0.045863] pci 0000:02:01.0: [104c:ac8e] type 2 class 0x000607
[    0.045881] pci 0000:02:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.045901] pci 0000:02:01.0: supports D1 D2
[    0.045903] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
[    0.045909] pci 0000:02:01.0: PME# disabled
[    0.045928] pci 0000:02:01.2: [104c:802e] type 0 class 0x000c00
[    0.045945] pci 0000:02:01.2: reg 10: [mem 0xff6fe800-0xff6fefff]
[    0.045956] pci 0000:02:01.2: reg 14: [mem 0xff6f8000-0xff6fbfff]
[    0.046012] pci 0000:02:01.2: supports D1 D2
[    0.046014] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.046019] pci 0000:02:01.2: PME# disabled
[    0.046037] pci 0000:02:01.3: [104c:ac8f] type 0 class 0x000180
[    0.046054] pci 0000:02:01.3: reg 10: [mem 0xff6ff000-0xff6fffff]
[    0.046116] pci 0000:02:01.3: supports D1 D2
[    0.046119] pci 0000:02:01.3: PME# supported from D0 D1 D2 D3hot
[    0.046124] pci 0000:02:01.3: PME# disabled
[    0.046146] pci 0000:02:02.0: [8086:4220] type 0 class 0x000280
[    0.046163] pci 0000:02:02.0: reg 10: [mem 0xff6fd000-0xff6fdfff]
[    0.046227] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.046231] pci 0000:02:02.0: PME# disabled
[    0.046251] pci 0000:02:03.0: [8086:1076] type 0 class 0x000200
[    0.046271] pci 0000:02:03.0: reg 10: [mem 0xff6c0000-0xff6dffff]
[    0.046281] pci 0000:02:03.0: reg 14: [mem 0xff6a0000-0xff6bffff]
[    0.046292] pci 0000:02:03.0: reg 18: [io  0xdc00-0xdc3f]
[    0.046324] pci 0000:02:03.0: reg 30: [mem 0xff680000-0xff69ffff pref]
[    0.046347] pci 0000:02:03.0: PME# supported from D0 D3hot D3cold
[    0.046352] pci 0000:02:03.0: PME# disabled
[    0.046372] pci 0000:02:04.0: [1033:0035] type 0 class 0x000c03
[    0.046388] pci 0000:02:04.0: reg 10: [mem 0xff6f7000-0xff6f7fff]
[    0.046447] pci 0000:02:04.0: supports D1 D2
[    0.046450] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.046455] pci 0000:02:04.0: PME# disabled
[    0.046472] pci 0000:02:04.1: [1033:0035] type 0 class 0x000c03
[    0.046489] pci 0000:02:04.1: reg 10: [mem 0xff6fc000-0xff6fcfff]
[    0.046548] pci 0000:02:04.1: supports D1 D2
[    0.046550] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.046555] pci 0000:02:04.1: PME# disabled
[    0.046572] pci 0000:02:04.2: [1033:00e0] type 0 class 0x000c03
[    0.046589] pci 0000:02:04.2: reg 10: [mem 0xff6fe400-0xff6fe4ff]
[    0.046648] pci 0000:02:04.2: supports D1 D2
[    0.046651] pci 0000:02:04.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.046656] pci 0000:02:04.2: PME# disabled
[    0.046700] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.046706] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.046711] pci 0000:00:1e.0:   bridge window [mem 0xff600000-0xff6fffff]
[    0.046717] pci 0000:00:1e.0:   bridge window [mem 0xdea00000-0xdeafffff pref]
[    0.046720] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.046724] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.046761] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.046774] pci_bus 0000:00: on NUMA node 0
[    0.046778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.046884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.046924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.050432] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9)
[    0.050509] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9)
[    0.050582] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9)
[    0.050655] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 9)
[    0.050727] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9)
[    0.050800] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9) *0, disabled.
[    0.050874] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9)
[    0.050947] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9)
[    0.051082] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.051089] vgaarb: loaded
[    0.051371] SCSI subsystem initialized
[    0.051432] libata version 3.00 loaded.
[    0.051500] usbcore: registered new interface driver usbfs
[    0.051516] usbcore: registered new interface driver hub
[    0.051547] usbcore: registered new device driver usb
[    0.051679] wmi: Mapper loaded
[    0.051681] PCI: Using ACPI for IRQ routing
[    0.051685] PCI: pci_cache_line_size set to 64 bytes
[    0.051762] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.051766] reserve RAM buffer: 000000002ff40000 - 000000002fffffff 
[    0.051908] NetLabel: Initializing
[    0.051911] NetLabel:  domain hash size = 128
[    0.051912] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.051929] NetLabel:  unlabeled traffic allowed by default
[    0.062346] AppArmor: AppArmor Filesystem Enabled
[    0.062405] pnp: PnP ACPI init
[    0.062446] ACPI: bus type pnp registered
[    0.062610] pnp 00:00: [bus 00-ff]
[    0.062615] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.062618] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.062621] pnp 00:00: [io  0x0d00-0xffff window]
[    0.062625] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.062628] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.062632] pnp 00:00: [mem 0x30000000-0xffffffff window]
[    0.062717] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.062769] pnp 00:01: [dma 4]
[    0.062772] pnp 00:01: [io  0x0000-0x000f]
[    0.062775] pnp 00:01: [io  0x0081-0x0083]
[    0.062778] pnp 00:01: [io  0x0087]
[    0.062781] pnp 00:01: [io  0x0089-0x008b]
[    0.062789] pnp 00:01: [io  0x008f]
[    0.062792] pnp 00:01: [io  0x00c0-0x00df]
[    0.062830] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.062845] pnp 00:02: [io  0x0070-0x0071]
[    0.062851] pnp 00:02: [irq 8]
[    0.062888] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.062930] pnp 00:03: [io  0x0060]
[    0.062933] pnp 00:03: [io  0x0064]
[    0.062936] pnp 00:03: [irq 1]
[    0.062980] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.063039] pnp 00:04: [irq 12]
[    0.063079] pnp 00:04: Plug and Play ACPI device, IDs SNY9009 PNP0f13 (active)
[    0.063091] pnp 00:05: [io  0x0061]
[    0.063129] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.063141] pnp 00:06: [io  0x00f0-0x00ff]
[    0.063144] pnp 00:06: [irq 13]
[    0.063182] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.063198] pnp 00:07: [io  0x0010-0x001f]
[    0.063200] pnp 00:07: [io  0x0022-0x003f]
[    0.063203] pnp 00:07: [io  0x0044-0x005f]
[    0.063206] pnp 00:07: [io  0x0063]
[    0.063209] pnp 00:07: [io  0x0065]
[    0.063211] pnp 00:07: [io  0x0067-0x006f]
[    0.063214] pnp 00:07: [io  0x0072-0x007f]
[    0.063217] pnp 00:07: [io  0x0080]
[    0.063219] pnp 00:07: [io  0x0084-0x0086]
[    0.063222] pnp 00:07: [io  0x0088]
[    0.063225] pnp 00:07: [io  0x008c-0x008e]
[    0.063228] pnp 00:07: [io  0x0090-0x009f]
[    0.063230] pnp 00:07: [io  0x00a2-0x00bf]
[    0.063233] pnp 00:07: [io  0x00e0-0x00ef]
[    0.063236] pnp 00:07: [io  0x04d0-0x04d1]
[    0.063239] pnp 00:07: [io  0xfe00-0xfe01]
[    0.063340] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.063344] system 00:07: [io  0xfe00-0xfe01] has been reserved
[    0.063348] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.063433] pnp 00:08: [mem 0xff800000-0xffbfffff]
[    0.063437] pnp 00:08: [mem 0xffc00000-0xffffffff]
[    0.063498] system 00:08: [mem 0xff800000-0xffbfffff] has been reserved
[    0.063503] system 00:08: [mem 0xffc00000-0xffffffff] has been reserved
[    0.063507] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.063679] pnp 00:09: [io  0x0400-0x047f]
[    0.063683] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.063686] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.063689] pnp 00:09: [io  0x0500-0x053f]
[    0.063692] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.063695] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.063758] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.063762] system 00:09: [io  0x0500-0x053f] has been reserved
[    0.063766] system 00:09: [mem 0xfec00000-0xfec00fff] has been reserved
[    0.063770] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.063774] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.064147] pnp 00:0a: Plug and Play ACPI device, IDs SNY6001 (disabled)
[    0.064412] pnp: PnP ACPI: found 11 devices
[    0.064415] ACPI: ACPI bus type pnp unregistered
[    0.064420] PnPBIOS: Disabled by ACPI PNP
[    0.101534] Switching to clocksource acpi_pm
[    0.101585] pci 0000:00:1f.1: BAR 5: assigned [mem 0x30000000-0x300003ff]
[    0.101594] pci 0000:00:1f.1: BAR 5: set to [mem 0x30000000-0x300003ff] (PCI address [0x30000000-0x300003ff])
[    0.101599] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.101603] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.101608] pci 0000:00:01.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.101613] pci 0000:00:01.0:   bridge window [mem 0xce900000-0xde9fffff pref]
[    0.101624] pci 0000:02:01.0: BAR 15: assigned [mem 0x34000000-0x37ffffff pref]
[    0.101630] pci 0000:02:01.0: BAR 16: assigned [mem 0x38000000-0x3bffffff]
[    0.101633] pci 0000:02:01.0: BAR 0: assigned [mem 0xff600000-0xff600fff]
[    0.101640] pci 0000:02:01.0: BAR 0: set to [mem 0xff600000-0xff600fff] (PCI address [0xff600000-0xff600fff])
[    0.101644] pci 0000:02:01.0: BAR 13: assigned [io  0xd000-0xd0ff]
[    0.101647] pci 0000:02:01.0: BAR 14: assigned [io  0xd400-0xd4ff]
[    0.101651] pci 0000:02:01.0: CardBus bridge to [bus 03-06]
[    0.101654] pci 0000:02:01.0:   bridge window [io  0xd000-0xd0ff]
[    0.101659] pci 0000:02:01.0:   bridge window [io  0xd400-0xd4ff]
[    0.101665] pci 0000:02:01.0:   bridge window [mem 0x34000000-0x37ffffff pref]
[    0.101670] pci 0000:02:01.0:   bridge window [mem 0x38000000-0x3bffffff]
[    0.101675] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.101679] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.101686] pci 0000:00:1e.0:   bridge window [mem 0xff600000-0xff6fffff]
[    0.101691] pci 0000:00:1e.0:   bridge window [mem 0xdea00000-0xdeafffff pref]
[    0.101711] pci 0000:00:1e.0: setting latency timer to 64
[    0.101843] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
[    0.101847] PCI: setting IRQ 9 as level-triggered
[    0.101852] pci 0000:02:01.0: PCI INT A -> Link[LNKF] -> GSI 9 (level, low) -> IRQ 9
[    0.101860] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.101863] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.101867] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.101870] pci_bus 0000:01: resource 1 [mem 0xff500000-0xff5fffff]
[    0.101874] pci_bus 0000:01: resource 2 [mem 0xce900000-0xde9fffff pref]
[    0.101877] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.101881] pci_bus 0000:02: resource 1 [mem 0xff600000-0xff6fffff]
[    0.101884] pci_bus 0000:02: resource 2 [mem 0xdea00000-0xdeafffff pref]
[    0.101888] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.101891] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.101894] pci_bus 0000:03: resource 0 [io  0xd000-0xd0ff]
[    0.101898] pci_bus 0000:03: resource 1 [io  0xd400-0xd4ff]
[    0.101901] pci_bus 0000:03: resource 2 [mem 0x34000000-0x37ffffff pref]
[    0.101905] pci_bus 0000:03: resource 3 [mem 0x38000000-0x3bffffff]
[    0.101960] NET: Registered protocol family 2
[    0.102049] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.102406] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.103926] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.103926] Switched to NOHz mode on CPU #0
[    0.103926] TCP: Hash tables configured (established 131072 bind 65536)
[    0.103926] TCP reno registered
[    0.103926] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.103926] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.103926] NET: Registered protocol family 1
[    0.103926] pci 0000:01:00.0: Boot video device
[    0.103926] PCI: CLS 64 bytes, default 64
[    0.104127] cpufreq-nforce2: No nForce2 chipset.
[    0.104331] audit: initializing netlink socket (disabled)
[    0.104354] type=2000 audit(1308636384.100:1): initialized
[    0.116505] Trying to unpack rootfs image as initramfs...
[    0.136333] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.144407] VFS: Disk quotas dquot_6.5.2
[    0.144513] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.145529] fuse init (API version 7.16)
[    0.145656] msgmni has been set to 1469
[    0.152257] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.152291] io scheduler noop registered
[    0.152293] io scheduler deadline registered
[    0.152318] io scheduler cfq registered (default)
[    0.152537] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.152576] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.152933] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.153596] ACPI: AC Adapter [ACAD] (on-line)
[    0.153701] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.153713] ACPI: Power Button [PWRB]
[    0.153779] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.153928] ACPI: Lid Switch [LID]
[    0.154100] ACPI: acpi_idle registered with cpuidle
[    0.155110] Marking TSC unstable due to TSC halts in idle
[    0.167613] thermal LNXTHERM:00: registered as thermal_zone0
[    0.167618] ACPI: Thermal Zone [ATF0] (63 C)
[    0.167664] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.167770] ERST: Table is not found!
[    0.167901] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.169558] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    0.169566] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    0.169574] serial 0000:00:1f.6: PCI INT B disabled
[    0.169733] Linux agpgart interface v0.103
[    0.169869] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    0.188299] ACPI: Battery Slot [BAT1] (battery absent)
[    0.188338] isapnp: Scanning for PnP cards...
[    0.248467] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.250223] brd: module loaded
[    0.251047] loop: module loaded
[    0.251181] i2c-core: driver [adp5520] using legacy suspend method
[    0.251184] i2c-core: driver [adp5520] using legacy resume method
[    0.251336] ata_piix 0000:00:1f.1: version 2.13
[    0.251350] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.251492] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 7
[    0.251495] PCI: setting IRQ 7 as level-triggered
[    0.251502] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 7 (level, low) -> IRQ 7
[    0.251555] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.256409] scsi0 : ata_piix
[    0.260271] scsi1 : ata_piix
[    0.262354] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.262358] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.263048] Fixed MDIO Bus: probed
[    0.263103] PPP generic driver version 2.4.2
[    0.263198] tun: Universal TUN/TAP device driver, 1.6
[    0.263201] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.263323] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.263453] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 3
[    0.263456] PCI: setting IRQ 3 as level-triggered
[    0.263463] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 3 (level, low) -> IRQ 3
[    0.263485] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.263490] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.263558] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.263603] ehci_hcd 0000:00:1d.7: debug port 1
[    0.267497] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.267509] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xff7ffc00
[    0.292047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.292291] hub 1-0:1.0: USB hub found
[    0.292298] hub 1-0:1.0: 6 ports detected
[    0.292423] ehci_hcd 0000:02:04.2: PCI INT C -> Link[LNKC] -> GSI 7 (level, low) -> IRQ 7
[    0.292449] ehci_hcd 0000:02:04.2: EHCI Host Controller
[    0.292507] ehci_hcd 0000:02:04.2: new USB bus registered, assigned bus number 2
[    0.339630] ehci_hcd 0000:02:04.2: irq 7, io mem 0xff6fe400
[    0.408039] ehci_hcd 0000:02:04.2: USB 2.0 started, EHCI 1.00
[    0.408307] hub 2-0:1.0: USB hub found
[    0.408313] hub 2-0:1.0: 5 ports detected
[    0.408453] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.408654] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    0.408661] ohci_hcd 0000:02:04.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.408685] ohci_hcd 0000:02:04.0: OHCI Host Controller
[    0.408749] ohci_hcd 0000:02:04.0: new USB bus registered, assigned bus number 3
[    0.408774] ohci_hcd 0000:02:04.0: irq 9, io mem 0xff6f7000
[    0.424630] ata1.00: CFA: CF CARD 4GB, Ver6.01K, max UDMA/133
[    0.424635] ata1.00: 7372512 sectors, multi 1: LBA 
[    0.424642] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.432312] ata2.00: ATAPI: SONY    DVD RW DW-U55A, 2.5b, max UDMA/33
[    0.436454] ata1.00: configured for UDMA/33
[    0.513681] ata2.00: configured for UDMA/33
[    0.580334] hub 3-0:1.0: USB hub found
[    0.580344] hub 3-0:1.0: 3 ports detected
[    0.580460] ohci_hcd 0000:02:04.1: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    0.580486] ohci_hcd 0000:02:04.1: OHCI Host Controller
[    0.580549] ohci_hcd 0000:02:04.1: new USB bus registered, assigned bus number 4
[    0.580578] ohci_hcd 0000:02:04.1: irq 9, io mem 0xff6fc000
[    0.768410] hub 4-0:1.0: USB hub found
[    0.768420] hub 4-0:1.0: 2 ports detected
[    0.768533] uhci_hcd: USB Universal Host Controller Interface driver
[    0.768628] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.768642] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.768648] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.768714] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.768749] uhci_hcd 0000:00:1d.0: irq 9, io base 0x0000e800
[    0.768927] hub 5-0:1.0: USB hub found
[    0.768933] hub 5-0:1.0: 2 ports detected
[    0.769181] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 4
[    0.769185] PCI: setting IRQ 4 as level-triggered
[    0.769190] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 4 (level, low) -> IRQ 4
[    0.769198] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.769202] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.769270] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.769298] uhci_hcd 0000:00:1d.1: irq 4, io base 0x0000e880
[    0.769460] hub 6-0:1.0: USB hub found
[    0.769465] hub 6-0:1.0: 2 ports detected
[    0.769543] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 7 (level, low) -> IRQ 7
[    0.769554] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.769558] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.769610] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.769634] uhci_hcd 0000:00:1d.2: irq 7, io base 0x0000ec00
[    0.769789] hub 7-0:1.0: USB hub found
[    0.769794] hub 7-0:1.0: 2 ports detected
[    0.769960] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.776242] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.776259] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.776482] mousedev: PS/2 mouse device common for all mice
[    0.776665] rtc_cmos 00:02: RTC can wake from S4
[    0.776735] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.776755] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.776909] device-mapper: uevent: version 1.0.3
[    0.777026] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.779234] device-mapper: multipath: version 1.2.0 loaded
[    0.779238] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.779370] EISA: Probing bus 0 at eisa.0
[    0.779409] EISA: Detected 0 cards.
[    0.784134] cpuidle: using governor ladder
[    0.784189] cpuidle: using governor menu
[    0.784555] TCP cubic registered
[    0.784749] NET: Registered protocol family 10
[    0.785445] NET: Registered protocol family 17
[    0.785484] Registering the dns_resolver key type
[    0.785784] Using IPI No-Shortcut mode
[    0.785965] PM: Hibernation image not present or could not be loaded.
[    0.785980] registered taskstats version 1
[    0.786262]   Magic number: 15:276:115
[    0.786409] rtc_cmos 00:02: setting system clock to 2011-06-21 06:06:24 UTC (1308636384)
[    0.786414] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.786416] EDD information not available.
[    0.840820] isapnp: No Plug & Play device found
[    0.840938] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.841321] scsi 0:0:0:0: Direct-Access     ATA      CF CARD 4GB      Ver6 PQ: 0 ANSI: 5
[    0.841529] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.841747] sd 0:0:0:0: [sda] 7372512 512-byte logical blocks: (3.77 GB/3.51 GiB)
[    0.841816] sd 0:0:0:0: [sda] Write Protect is off
[    0.841820] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.841850] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    0.843114] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DW-U55A   2.5b PQ: 0 ANSI: 5
[    0.844944]  sda: sda1 sda2 < sda5 >
[    0.845309] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.886212] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.886219] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.886444] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.886572] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.006572] Freeing initrd memory: 12512k freed
[    1.025895] Freeing unused kernel memory: 700k freed
[    1.026848] Write protecting the kernel text: 5192k
[    1.026900] Write protecting the kernel read-only data: 2148k
[    1.053290] <30>udev[64]: starting version 167
[    1.136048] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    1.346415] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.346420] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.346472] e1000 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    1.367793] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.786577] e1000 0000:02:03.0: eth0: (PCI:33MHz:32-bit) 08:00:46:db:0f:85
[    1.786585] e1000 0000:02:03.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.786738] firewire_ohci 0000:02:01.2: PCI INT C -> Link[LNKH] -> GSI 3 (level, low) -> IRQ 3
[    1.840077] firewire_ohci: Added fw-ohci device 0000:02:01.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.340191] firewire_core: created device fw0: GUID 0800460301a680bd, S400
[   10.096531] Adding 784380k swap on /dev/sda5.  Priority:-1 extents:1 across:784380k 
[   10.152773] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.183891] <30>udev[273]: starting version 167
[   10.276230] lp: driver loaded but no devices found
[   10.421809] type=1400 audit(1308636394.132:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=362  comm="apparmor_parser"
[   10.431077] type=1400 audit(1308636394.140:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=362  comm="apparmor_parser"
[   10.431702] type=1400 audit(1308636394.140:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=362 comm="apparmor_parser"
[   10.646233] intel_rng: FWH not detected
[   10.806148] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.851994] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.190159] lib80211: common routines for IEEE802.11 drivers
[   11.190165] lib80211_crypt: registered algorithm 'NULL'
[   11.293235] asus_laptop: Asus Laptop Support version 0.42
[   11.293331] asus_laptop: Error calling CWAP(1)
[   11.293335] asus_laptop:   SE model detected
[   11.293362] asus_laptop: Error setting bluetooth status to 1
[   11.293366] asus_laptop: Error setting wlan status to 1
[   11.306207] type=1400 audit(1308636395.016:5): apparmor="STATUS"  operation="profile_load" name="/usr/share/gdm/guest-session/Xsession"  pid=592 comm="apparmor_parser"
[   11.310297] type=1400 audit(1308636395.020:6): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=593  comm="apparmor_parser"
[   11.313116] type=1400 audit(1308636395.024:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593  comm="apparmor_parser"
[   11.313752] type=1400 audit(1308636395.024:8): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=593  comm="apparmor_parser"
[   11.321560] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input3
[   11.372324] type=1400 audit(1308636395.084:9): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince" pid=594  comm="apparmor_parser"
[   11.404614] type=1400 audit(1308636395.116:10): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-previewer" pid=594  comm="apparmor_parser"
[   11.422074] type=1400 audit(1308636395.132:11): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=594  comm="apparmor_parser"
[   11.470926] sony-laptop: Sony Programmable IO Control Driver v0.6.
[   11.470944] sony-laptop: detected Type2 model
[   11.472336] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input4
[   11.554833] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:10/SNY6001:00/input/input5
[   11.555088] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[   11.556183] sony-laptop: device allocated minor is 56
[   11.556509] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   11.565701] sony-laptop: Sony Notebook Control Driver v0.6.
[   11.679570] yenta_cardbus 0000:02:01.0: CardBus bridge found [104d:818f]
[   11.679588] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   11.679592] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   11.679598] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01001b22, devctl 0x64
[   11.885922] Bluetooth: Core ver 2.15
[   11.903512] NET: Registered protocol family 31
[   11.903516] Bluetooth: HCI device and connection manager initialized
[   11.903520] Bluetooth: HCI socket layer initialized
[   11.984532] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0c20, PCI irq 9
[   11.984538] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   11.984544] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   11.984557] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0xd000-0xdfff]
[   11.984561] pcmcia_socket pcmcia_socket0: cs: IO port probe  0xd000-0xdfff: excluding 0xd000-0xd0ff 0xd400-0xd4ff 0xdc00-0xdc3f
[   12.027538] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xff600000-0xff6fffff]
[   12.027544] pcmcia_socket pcmcia_socket0: cs: memory probe  0xff600000-0xff6fffff: excluding 0xff600000-0xff60ffff  0xff680000-0xff6dffff 0xff6f0000-0xff6fffff
[   12.027563] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xdea00000-0xdeafffff pref]
[   12.027567] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdea00000-0xdeafffff: excluding 0xdea00000-0xdeafffff
[   12.047360] [drm] Initialized drm 1.1.0 20060810
[   12.054695] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   12.061373] usbcore: registered new interface driver btusb
[   12.073570] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[   12.073576] PCI: setting IRQ 5 as level-triggered
[   12.073583] tifm_7xx1 0000:02:01.3: PCI INT B -> Link[LNKG] -> GSI 5 (level, low) -> IRQ 5
[   12.116042] tifm_core: MMC/SD card detected in socket 0:0
[   12.142686] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   12.160797] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
[   12.161257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.161916] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.162638] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xe0000-0xfffff
[   12.162707] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   12.162776] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   12.162847] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.180081] Bluetooth: L2CAP ver 2.15
[   12.180087] Bluetooth: L2CAP socket layer initialized
[   12.213014] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.213018] Bluetooth: BNEP filters: protocol multicast
[   12.214920] cfg80211: Calling CRDA to update world regulatory domain
[   12.237650] Bluetooth: SCO (Voice Link) ver 0.6
[   12.237654] Bluetooth: SCO socket layer initialized
[   12.287265] cfg80211: World regulatory domain updated:
[   12.287271] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.287275] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.287279] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.287282] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.287286] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.287290] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.306352] libipw: 802.11 data/management/control stack, git-1.1.13
[   12.306357] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   12.407004] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   12.407009] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   12.407183] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 7 (level, low) -> IRQ 7
[   12.411213] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   12.608134] [drm] radeon defaulting to kernel modesetting.
[   12.608139] [drm] radeon kernel modesetting enabled.
[   12.608370] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[   12.608378] radeon 0000:01:00.0: PCI INT A -> Link[LNKE] -> GSI 9 (level, low) -> IRQ 9
[   12.613957] [drm] initializing kernel modesetting (RV350 0x1002:0x4E50).
[   12.614015] [drm] register mmio base: 0xFF5F0000
[   12.614018] [drm] register mmio size: 65536
[   12.614151] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.614156] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614159] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.614163] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614166] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.614170] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614173] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.614177] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614180] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.614184] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614187] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.614191] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614194] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.614198] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614201] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.614205] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614208] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.614212] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614215] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.614219] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614222] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.614226] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614229] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.614233] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.614236] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.614239] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.615495] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   12.621536] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   12.621557] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   12.621598] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   12.621648] radeon 0000:01:00.0: GTT: 256M 0xE0000000 - 0xEFFFFFFF
[   12.621653] [drm] Generation 2 PCI interface, using max accessible memory
[   12.621660] radeon 0000:01:00.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (64M used)
[   12.621676] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.621678] [drm] Driver supports precise vblank timestamp query.
[   12.621698] [drm] radeon: irq initialized.
[   12.622388] [drm] Detected VRAM RAM=128M, BAR=128M
[   12.622394] [drm] RAM width 128bits DDR
[   12.632854] [TTM] Zone  kernel: Available graphics memory: 382856 kiB.
[   12.632858] [TTM] Initializing pool allocator.
[   12.632885] [drm] radeon: 64M of VRAM memory ready
[   12.632889] [drm] radeon: 256M of GTT memory ready.
[   12.632932] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   12.634160] radeon 0000:01:00.0: WB disabled
[   12.636683] [drm] Loading R300 Microcode
[   12.642740] [drm] radeon: ring at 0x00000000E0001000
[   12.642765] [drm] ring test succeeded in 1 usecs
[   12.642991] [drm] radeon: ib pool ready.
[   12.643107] [drm] ib test succeeded in 0 usecs
[   12.648556] [drm] Panel ID String: 1920X1200 WUXGA         
[   12.648560] [drm] Panel Size 1920x1200
[   12.648883] [drm] Radeon Display Connectors
[   12.648886] [drm] Connector 0:
[   12.648888] [drm]   VGA
[   12.648891] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   12.648894] [drm]   Encoders:
[   12.648896] [drm]     CRT1: INTERNAL_DAC1
[   12.648898] [drm] Connector 1:
[   12.648900] [drm]   DVI-D
[   12.648901] [drm]   HPD1
[   12.648904] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   12.648906] [drm]   Encoders:
[   12.648908] [drm]     DFP1: INTERNAL_TMDS1
[   12.648910] [drm] Connector 2:
[   12.648912] [drm]   LVDS
[   12.648914] [drm]   Encoders:
[   12.648916] [drm]     LCD1: INTERNAL_LVDS
[   12.648918] [drm] Connector 3:
[   12.648919] [drm]   S-video
[   12.648921] [drm]   Encoders:
[   12.648923] [drm]     TV1: INTERNAL_DAC2
[   12.726369] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[   12.726407] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.814637] [drm] fb mappable at 0xD0040000
[   12.814641] [drm] vram apper at 0xD0000000
[   12.814643] [drm] size 9216000
[   12.814646] [drm] fb depth is 24
[   12.814648] [drm]    pitch is 7680
[   12.816376] Console: switching to colour frame buffer device 240x75
[   12.816470] fb0: radeondrmfb frame buffer device
[   12.816472] drm: registered panic notifier
[   12.816486] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   13.552037] intel8x0_measure_ac97_clock: measured 55393 usecs (2669 samples)
[   13.552042] intel8x0: clocking to 48000
[   15.171994] Bluetooth: RFCOMM TTY layer initialized
[   15.172188] Bluetooth: RFCOMM socket layer initialized
[   15.172191] Bluetooth: RFCOMM ver 1.11
[   15.802945] ppdev: user-space parallel port driver
[   15.852937] audit_printk_skb: 9 callbacks suppressed
[   15.852942] type=1400 audit(1308636399.564:15): apparmor="STATUS"  operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf"  pid=1009 comm="apparmor_parser"
[   15.857454] type=1400 audit(1308636399.568:16): apparmor="STATUS"  operation="profile_replace" name="/usr/sbin/cupsd" pid=1009  comm="apparmor_parser"
[   39.201217] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   76.212329] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   84.928028] eth1: no IPv6 routers present
[ 3968.152038] eth1: no IPv6 routers present


---

### Post by pookieman123 on 2011-06-21
finally i did this

> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:26:B8:EC:F4:D4
                    ESSID:"pookies"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-46 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 272ms ago

there are other networks list but I can see mine 'pookies'

so if i can see it why can't i connect?

---

### Post by pookieman123 on 2011-06-21
Anybody???

---

### Post by pookieman123 on 2011-06-22
All solved found answer here.. 

[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

why this happened I don't know but it works perfectly now..

---

