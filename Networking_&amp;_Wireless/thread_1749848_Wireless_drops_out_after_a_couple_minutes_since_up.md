---
title: "Wireless drops out after a couple minutes since upgrading to 11.04"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by JHolmes763 on 2011-05-04
Since upgrading to 11.04 (from 10.10), I'm having wireless issues. My wireless will connect and work for a few minutes and then drops out. After a minute, I get prompted to enter my password again, but even after doing so, it never reconnects. If I choose "cancel" and click on the wireless icon on the top taskbar, it shows "Wireless Networks - disconnected" and no SSIDs are shown. 

This is a desktop machine with PCI wireless card. 

The only solution I've found is to reboot. 

Wireless worked flawlessly in 10.10 on the LiveCD and after a full installation without having to install anything. 

Wireless also works fine for all of my other devices off of the same AP. 

Below are two blocks with the results from the suggested troubleshooting commands to run. One is the results from when the wireless was working and the second is for after the wireless dropped out. I cut out some stuff that was the same, like the beginning output from dmesg. 

Looking for any advice on a solution. Thank you. 

-John Holmes

Wireless Working:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)
01:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller (rev a1)
05:00.0 PCI bridge: Device 1b21:1080 (rev 01)
06:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 IDE interface: Marvell Technology Group Ltd. Device 91b0 (rev 11)
08:00.1 IDE interface: Marvell Technology Group Ltd. Device 91a4 (rev 11)
09:00.0 USB Controller: Device 1b21:1042

$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 002 Device 003: ID 045e:076c Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:68:83:78  
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2128 (2.1 KB)  TX bytes:2128 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:0a:42:34:8c  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:aff:fe42:348c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2334776 (2.3 MB)  TX bytes:812328 (812.3 KB)

$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"HolmesWIFI"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:69:06:F6:47   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:75   Missed beacon:0

$ lsmod
Module                  Size  Used by
aesni_intel            55161  1 
cryptd                 20510  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            38279  2 aesni_intel,aes_x86_64
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vesafb                 13761  1 
ppdev                  17113  0 
parport_pc             36959  0 
snd_hda_codec_hdmi     28103  4 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336693  1 
psmouse                73535  0 
joydev                 17606  0 
snd_hda_intel          33211  2 
nvidia              10709116  40 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
rt61pci                27888  0 
rt2x00pci              14322  1 rt61pci
snd_seq_midi_event     14899  1 snd_seq_midi
rt2x00lib              49235  2 rt61pci,rt2x00pci
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  2 rt2x00pci,rt2x00lib
eeepc_wmi              19323  0 
sparse_keymap          13898  1 eeepc_wmi
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt61pci
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xhci_hcd               77643  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  2 rt61pci,firewire_core
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 

$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=84ad4e15-b2f6-4f97-8a34-d9880340855b ro splash vga=771 quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df453000 (usable)
[    0.000000]  BIOS-e820: 00000000df453000 - 00000000df4a7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df4a7000 - 00000000df5da000 (reserved)
[    0.000000]  BIOS-e820: 00000000df5da000 - 00000000df5eb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df5eb000 - 00000000df602000 (reserved)
[    0.000000]  BIOS-e820: 00000000df602000 - 00000000df604000 (usable)
[    0.000000]  BIOS-e820: 00000000df604000 - 00000000df605000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000df605000 - 00000000df60d000 (reserved)
[    0.000000]  BIOS-e820: 00000000df60d000 - 00000000df617000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df617000 - 00000000df642000 (reserved)
[    0.000000]  BIOS-e820: 00000000df642000 - 00000000df685000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df685000 - 00000000df800000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8P67 LE, BIOS 1003 02/11/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 21F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fceb0] fceb0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000df800000
[    0.000000]  0000000000 - 00df800000 page 2M
[    0.000000] kernel direct mapping tables up to df800000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f800000
[    0.000000]  0100000000 - 021f800000 page 2M
[    0.000000] kernel direct mapping tables up to 21f800000 @ df7f6000-df800000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000df49e068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000df4a5dc0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000df49e140 07C79 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000df60ef80 00040
[    0.000000] ACPI: APIC 00000000df4a5eb8 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000df4a5f30 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000df4a6038 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000df4a6078 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f800000
[    0.000000]   NODE_DATA [000000021f7fb000 - 000000021f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217600000-ffff88021e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000df453
[    0.000000]     0: 0x000df602 -> 0x000df604
[    0.000000]     0: 0x000df685 -> 0x000df800
[    0.000000]     0: 0x00100000 -> 0x0021f800
[    0.000000] On node 0 totalpages: 2092381
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 896520 pages, LIFO batch:31
[    0.000000]   Normal zone: 16100 pages used for memmap
[    0.000000]   Normal zone: 1161500 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df453000 - 00000000df4a7000
[    0.000000] PM: Registered nosave memory: 00000000df4a7000 - 00000000df5da000
[    0.000000] PM: Registered nosave memory: 00000000df5da000 - 00000000df5eb000
[    0.000000] PM: Registered nosave memory: 00000000df5eb000 - 00000000df602000
[    0.000000] PM: Registered nosave memory: 00000000df604000 - 00000000df605000
[    0.000000] PM: Registered nosave memory: 00000000df605000 - 00000000df60d000
[    0.000000] PM: Registered nosave memory: 00000000df60d000 - 00000000df617000
[    0.000000] PM: Registered nosave memory: 00000000df617000 - 00000000df642000
[    0.000000] PM: Registered nosave memory: 00000000df642000 - 00000000df685000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at df800000 (gap: df800000:1f51c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800df200000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061939
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=84ad4e15-b2f6-4f97-8a34-d9880340855b ro splash vga=771 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8159916k/8904704k available (5940k kernel code, 535180k absent, 209608k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 3399.713 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6799.42 BogoMIPS (lpj=33997130)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000018] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000027] Yama: becoming mindful.
[    0.000541] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001756] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002234] Mount-cache hash table entries: 256
[    0.002296] Initializing cgroup subsys ns
[    0.002298] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.002300] Initializing cgroup subsys cpuacct
[    0.002302] Initializing cgroup subsys memory
[    0.002306] Initializing cgroup subsys devices
[    0.002307] Initializing cgroup subsys freezer
[    0.002308] Initializing cgroup subsys net_cls
[    0.002309] Initializing cgroup subsys blkio
[    0.002327] CPU: Physical Processor ID: 0
[    0.002328] CPU: Processor Core ID: 0
[    0.002332] mce: CPU supports 9 MCE banks
[    0.002341] CPU0: Thermal monitoring enabled (TM1)
[    0.002347] using mwait in idle threads.
[    0.004008] ACPI: Core revision 20110112
[    0.014021] ftrace: allocating 24314 entries in 96 pages
[    0.020521] Setting APIC routing to flat
[    0.020847] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.120786] CPU0: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz stepping 07
[    0.238221] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.238225] ... version:                3
[    0.238226] ... bit width:              48
[    0.238227] ... generic registers:      8
[    0.238227] ... value mask:             0000ffffffffffff
[    0.238228] ... max period:             000000007fffffff
[    0.238229] ... fixed-purpose events:   3
[    0.238230] ... event mask:             00000007000000ff
[    0.238502] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.777902] Brought up 4 CPUs
[    0.777904] Total of 4 processors activated (27197.01 BogoMIPS).
[    0.779183] devtmpfs: initialized
[    0.779760] print_constraints: dummy: 
[    0.779783] Time: 20:15:11  Date: 05/04/11
[    0.779800] NET: Registered protocol family 16
[    0.779857] ACPI: bus type pci registered
[    0.779860] Trying to unpack rootfs image as initramfs...
[    0.779901] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.779903] PCI: not using MMCONFIG
[    0.779904] PCI: Using configuration type 1 for base access
[    0.779921] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.779922] mtrr: probably your BIOS does not setup all CPUs.
[    0.779923] mtrr: corrected configuration.
[    0.780304] bio: create slab <bio-0> at 0
[    0.781036] ACPI: EC: Look up EC in DSDT
[    0.781669] ACPI: Executed 1 blocks of module-level executable AML code
[    0.783184] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    0.783188] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110112/nsinit-349)
[    0.783369] ACPI: SSDT 00000000df60dc18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.783569] ACPI: Dynamic OEM Table Load:
[    0.783571] ACPI: SSDT           (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.783593] ACPI: SSDT 00000000df60ee18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.783757] ACPI: Dynamic OEM Table Load:
[    0.783758] ACPI: SSDT           (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.784052] ACPI: Interpreter enabled
[    0.784054] ACPI: (supports S0 S1 S3 S4 S5)
[    0.784066] ACPI: Using IOAPIC for interrupt routing
[    0.784080] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.784127] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.793750] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.796590] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.796673] ACPI: No dock devices found.
[    0.796674] HEST: Table not found.
[    0.796676] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.796799] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.796936] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.796937] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.796939] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.796940] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
[    0.796941] pci_root PNP0A08:00: host bridge window [mem 0xe4000000-0xffffffff]
[    0.796948] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.796972] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.796989] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.796991] pci 0000:00:01.0: PME# disabled
[    0.797027] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.797048] pci 0000:00:16.0: reg 10: [mem 0xfa408000-0xfa40800f 64bit]
[    0.797103] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.797106] pci 0000:00:16.0: PME# disabled
[    0.797133] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.797152] pci 0000:00:1a.0: reg 10: [mem 0xfa407000-0xfa4073ff]
[    0.797219] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.797222] pci 0000:00:1a.0: PME# disabled
[    0.797241] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.797254] pci 0000:00:1b.0: reg 10: [mem 0xfa400000-0xfa403fff 64bit]
[    0.797302] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.797305] pci 0000:00:1b.0: PME# disabled
[    0.797321] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.797378] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.797381] pci 0000:00:1c.0: PME# disabled
[    0.797400] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    0.797456] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.797459] pci 0000:00:1c.2: PME# disabled
[    0.797479] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.797535] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.797538] pci 0000:00:1c.3: PME# disabled
[    0.797557] pci 0000:00:1c.4: [8086:244e] type 1 class 0x000604
[    0.797613] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.797616] pci 0000:00:1c.4: PME# disabled
[    0.797634] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    0.797690] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.797693] pci 0000:00:1c.5: PME# disabled
[    0.797712] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    0.797768] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.797771] pci 0000:00:1c.6: PME# disabled
[    0.797790] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.797852] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.797855] pci 0000:00:1c.7: PME# disabled
[    0.797878] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.797897] pci 0000:00:1d.0: reg 10: [mem 0xfa406000-0xfa4063ff]
[    0.797963] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.797966] pci 0000:00:1d.0: PME# disabled
[    0.797986] pci 0000:00:1f.0: [8086:1c46] type 0 class 0x000601
[    0.798090] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    0.798106] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.798112] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.798119] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.798125] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.798131] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.798138] pci 0000:00:1f.2: reg 24: [mem 0xfa405000-0xfa4057ff]
[    0.798166] pci 0000:00:1f.2: PME# supported from D3hot
[    0.798168] pci 0000:00:1f.2: PME# disabled
[    0.798182] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.798195] pci 0000:00:1f.3: reg 10: [mem 0xfa404000-0xfa4040ff 64bit]
[    0.798214] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.798257] pci 0000:01:00.0: [10de:0dc4] type 0 class 0x000300
[    0.798264] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
[    0.798272] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.798280] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.798285] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.798291] pci 0000:01:00.0: reg 30: [mem 0xfa000000-0xfa07ffff pref]
[    0.798323] pci 0000:01:00.1: [10de:0be9] type 0 class 0x000403
[    0.798330] pci 0000:01:00.1: reg 10: [mem 0xfa080000-0xfa083fff]
[    0.817827] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.817830] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.817832] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfa0fffff]
[    0.817834] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf3ffffff 64bit pref]
[    0.817876] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.817879] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.817882] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.817888] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.817928] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.817931] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.817934] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.817939] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.817979] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.817982] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.817985] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.817990] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.818043] pci 0000:05:00.0: [1b21:1080] type 1 class 0x000604
[    0.818145] pci 0000:00:1c.4: PCI bridge to [bus 05-06] (subtractive decode)
[    0.818148] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.818151] pci 0000:00:1c.4:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.818156] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.818158] pci 0000:00:1c.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.818159] pci 0000:00:1c.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.818160] pci 0000:00:1c.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.818162] pci 0000:00:1c.4:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
[    0.818163] pci 0000:00:1c.4:   bridge window [mem 0xe4000000-0xffffffff] (subtractive decode)
[    0.818222] pci 0000:06:02.0: [1814:0301] type 0 class 0x000280
[    0.818252] pci 0000:06:02.0: reg 10: [mem 0xfa300000-0xfa307fff]
[    0.818400] pci 0000:06:03.0: [1106:3044] type 0 class 0x000c00
[    0.818430] pci 0000:06:03.0: reg 10: [mem 0xfa308000-0xfa3087ff]
[    0.818446] pci 0000:06:03.0: reg 14: [io  0xd000-0xd07f]
[    0.818556] pci 0000:06:03.0: supports D2
[    0.818557] pci 0000:06:03.0: PME# supported from D2 D3hot D3cold
[    0.818563] pci 0000:06:03.0: PME# disabled
[    0.818635] pci 0000:05:00.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.818643] pci 0000:05:00.0:   bridge window [io  0xd000-0xdfff]
[    0.818648] pci 0000:05:00.0:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.818657] pci 0000:05:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.818658] pci 0000:05:00.0:   bridge window [io  0xd000-0xdfff] (subtractive decode)
[    0.818660] pci 0000:05:00.0:   bridge window [mem 0xfa300000-0xfa3fffff] (subtractive decode)
[    0.818661] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.818662] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.818664] pci 0000:05:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.818665] pci 0000:05:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.818666] pci 0000:05:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.818668] pci 0000:05:00.0:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
[    0.818669] pci 0000:05:00.0:   bridge window [mem 0xe4000000-0xffffffff] (subtractive decode)
[    0.818738] pci 0000:07:00.0: [10ec:8168] type 0 class 0x000200
[    0.818756] pci 0000:07:00.0: reg 10: [io  0xc000-0xc0ff]
[    0.818788] pci 0000:07:00.0: reg 18: [mem 0xf4104000-0xf4104fff 64bit pref]
[    0.818808] pci 0000:07:00.0: reg 20: [mem 0xf4100000-0xf4103fff 64bit pref]
[    0.818865] pci 0000:07:00.0: supports D1 D2
[    0.818866] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.818870] pci 0000:07:00.0: PME# disabled
[    0.837817] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.837821] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.837824] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.837829] pci 0000:00:1c.5:   bridge window [mem 0xf4100000-0xf41fffff 64bit pref]
[    0.837887] pci 0000:08:00.0: [1b4b:91b0] type 0 class 0x000101
[    0.837904] pci 0000:08:00.0: reg 10: [io  0xb090-0xb097]
[    0.837915] pci 0000:08:00.0: reg 14: [io  0xb080-0xb083]
[    0.837927] pci 0000:08:00.0: reg 18: [io  0xb070-0xb077]
[    0.837938] pci 0000:08:00.0: reg 1c: [io  0xb060-0xb063]
[    0.837950] pci 0000:08:00.0: reg 20: [io  0xb050-0xb05f]
[    0.837961] pci 0000:08:00.0: reg 24: [mem 0xfa221000-0xfa2217ff]
[    0.837973] pci 0000:08:00.0: reg 30: [mem 0xfa210000-0xfa21ffff pref]
[    0.838008] pci 0000:08:00.0: PME# supported from D3hot
[    0.838012] pci 0000:08:00.0: PME# disabled
[    0.838047] pci 0000:08:00.1: [1b4b:91a4] type 0 class 0x000101
[    0.838063] pci 0000:08:00.1: reg 10: [io  0xb040-0xb047]
[    0.838074] pci 0000:08:00.1: reg 14: [io  0xb030-0xb033]
[    0.838086] pci 0000:08:00.1: reg 18: [io  0xb020-0xb027]
[    0.838097] pci 0000:08:00.1: reg 1c: [io  0xb010-0xb013]
[    0.838108] pci 0000:08:00.1: reg 20: [io  0xb000-0xb00f]
[    0.838120] pci 0000:08:00.1: reg 24: [mem 0xfa220000-0xfa22000f]
[    0.838131] pci 0000:08:00.1: reg 30: [mem 0xfa200000-0xfa20ffff pref]
[    0.838166] pci 0000:08:00.1: PME# supported from D3hot
[    0.838170] pci 0000:08:00.1: PME# disabled
[    0.857802] pci 0000:00:1c.6: PCI bridge to [bus 08-08]
[    0.857805] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.857808] pci 0000:00:1c.6:   bridge window [mem 0xfa200000-0xfa2fffff]
[    0.857813] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.857879] pci 0000:09:00.0: [1b21:1042] type 0 class 0x000c03
[    0.857907] pci 0000:09:00.0: reg 10: [mem 0xfa100000-0xfa107fff 64bit]
[    0.858027] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.858032] pci 0000:09:00.0: PME# disabled
[    0.877785] pci 0000:00:1c.7: PCI bridge to [bus 09-09]
[    0.877789] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
[    0.877792] pci 0000:00:1c.7:   bridge window [mem 0xfa100000-0xfa1fffff]
[    0.877797] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.877831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.877907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.877927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.877946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.877962] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.877979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.877996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4.BR16._PRT]
[    0.878029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.878046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    0.878062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
[    0.878139]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.878272]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.880703] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.880731] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.880757] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.880783] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.880810] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.880836] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.880862] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.880888] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.880948] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.880951] vgaarb: loaded
[    0.881042] SCSI subsystem initialized
[    0.881072] libata version 3.00 loaded.
[    0.881095] usbcore: registered new interface driver usbfs
[    0.881100] usbcore: registered new interface driver hub
[    0.881111] usbcore: registered new device driver usb
[    0.881224] wmi: Mapper loaded
[    0.881225] PCI: Using ACPI for IRQ routing
[    0.881227] PCI: pci_cache_line_size set to 64 bytes
[    0.881304] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.881306] reserve RAM buffer: 00000000df453000 - 00000000dfffffff 
[    0.881308] reserve RAM buffer: 00000000df604000 - 00000000dfffffff 
[    0.881309] reserve RAM buffer: 00000000df800000 - 00000000dfffffff 
[    0.881310] reserve RAM buffer: 000000021f800000 - 000000021fffffff 
[    0.881361] NetLabel: Initializing
[    0.881362] NetLabel:  domain hash size = 128
[    0.881363] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.881369] NetLabel:  unlabeled traffic allowed by default
[    0.881394] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.881398] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.883409] Switching to clocksource hpet
[    0.886830] AppArmor: AppArmor Filesystem Enabled
[    0.886844] pnp: PnP ACPI init
[    0.886854] ACPI: bus type pnp registered
[    0.886944] pnp 00:00: [bus 00-ff]
[    0.886945] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.886946] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.886947] pnp 00:00: [io  0x0d00-0xffff window]
[    0.886949] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.886950] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.886951] pnp 00:00: [mem 0xe4000000-0xffffffff window]
[    0.886952] pnp 00:00: [mem 0x00000000 window]
[    0.886988] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.887023] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.887024] pnp 00:01: [mem 0xe0000000-0xe3ffffff]
[    0.887025] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.887026] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.887027] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.887056] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.887058] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.887059] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.887061] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.887062] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.887064] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.887106] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.887107] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.887108] pnp 00:02: [io  0x0290-0x029f]
[    0.887109] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.887132] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.887134] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.887143] pnp 00:03: [dma 4]
[    0.887144] pnp 00:03: [io  0x0000-0x000f]
[    0.887145] pnp 00:03: [io  0x0081-0x0083]
[    0.887145] pnp 00:03: [io  0x0087]
[    0.887146] pnp 00:03: [io  0x0089-0x008b]
[    0.887147] pnp 00:03: [io  0x008f]
[    0.887148] pnp 00:03: [io  0x00c0-0x00df]
[    0.887160] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.887166] pnp 00:04: [io  0x0070-0x0071]
[    0.887172] pnp 00:04: [irq 8]
[    0.887185] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.887190] pnp 00:05: [io  0x0061]
[    0.887202] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.887211] pnp 00:06: [io  0x0010-0x001f]
[    0.887212] pnp 00:06: [io  0x0022-0x003f]
[    0.887213] pnp 00:06: [io  0x0044-0x005f]
[    0.887214] pnp 00:06: [io  0x0063]
[    0.887215] pnp 00:06: [io  0x0065]
[    0.887216] pnp 00:06: [io  0x0067-0x006f]
[    0.887217] pnp 00:06: [io  0x0072-0x007f]
[    0.887218] pnp 00:06: [io  0x0080]
[    0.887218] pnp 00:06: [io  0x0084-0x0086]
[    0.887220] pnp 00:06: [io  0x0088]
[    0.887221] pnp 00:06: [io  0x008c-0x008e]
[    0.887222] pnp 00:06: [io  0x0090-0x009f]
[    0.887223] pnp 00:06: [io  0x00a2-0x00bf]
[    0.887224] pnp 00:06: [io  0x00e0-0x00ef]
[    0.887225] pnp 00:06: [io  0x04d0-0x04d1]
[    0.887256] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.887258] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.887262] pnp 00:07: [io  0x00f0-0x00ff]
[    0.887266] pnp 00:07: [irq 13]
[    0.887278] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.887442] pnp 00:08: [io  0x03f8-0x03ff]
[    0.887445] pnp 00:08: [irq 4]
[    0.887446] pnp 00:08: [dma 0 disabled]
[    0.887474] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.887557] pnp 00:09: [io  0x0400-0x0453]
[    0.887558] pnp 00:09: [io  0x0458-0x047f]
[    0.887559] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.887560] pnp 00:09: [io  0x0500-0x057f]
[    0.887561] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.887562] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.887563] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.887564] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.887590] system 00:09: [io  0x0400-0x0453] has been reserved
[    0.887591] system 00:09: [io  0x0458-0x047f] has been reserved
[    0.887593] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.887594] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.887596] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.887597] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.887599] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.887600] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.887623] pnp 00:0a: [io  0x0454-0x0457]
[    0.887647] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.887649] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.887713] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.887733] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.887769] Switched to NOHz mode on CPU #0
[    0.887827] Switched to NOHz mode on CPU #3
[    0.887832] pnp: PnP ACPI: found 12 devices
[    0.887833] ACPI: ACPI bus type pnp unregistered
[    0.887851] Switched to NOHz mode on CPU #2
[    0.887877] Switched to NOHz mode on CPU #1
[    0.893228] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.893230] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.893232] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfa0fffff]
[    0.893233] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf3ffffff 64bit pref]
[    0.893236] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.893237] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.893241] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.893243] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.893248] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.893249] pci 0000:00:1c.2:   bridge window [io  disabled]
[    0.893253] pci 0000:00:1c.2:   bridge window [mem disabled]
[    0.893256] pci 0000:00:1c.2:   bridge window [mem pref disabled]
[    0.893260] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.893261] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.893265] pci 0000:00:1c.3:   bridge window [mem disabled]
[    0.893268] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.893273] pci 0000:05:00.0: PCI bridge to [bus 06-06]
[    0.893276] pci 0000:05:00.0:   bridge window [io  0xd000-0xdfff]
[    0.893283] pci 0000:05:00.0:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.893288] pci 0000:05:00.0:   bridge window [mem pref disabled]
[    0.893296] pci 0000:00:1c.4: PCI bridge to [bus 05-06]
[    0.893298] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.893302] pci 0000:00:1c.4:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.893305] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.893310] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.893312] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.893316] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.893319] pci 0000:00:1c.5:   bridge window [mem 0xf4100000-0xf41fffff 64bit pref]
[    0.893324] pci 0000:00:1c.6: PCI bridge to [bus 08-08]
[    0.893326] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.893330] pci 0000:00:1c.6:   bridge window [mem 0xfa200000-0xfa2fffff]
[    0.893332] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.893337] pci 0000:00:1c.7: PCI bridge to [bus 09-09]
[    0.893338] pci 0000:00:1c.7:   bridge window [io  disabled]
[    0.893342] pci 0000:00:1c.7:   bridge window [mem 0xfa100000-0xfa1fffff]
[    0.893345] pci 0000:00:1c.7:   bridge window [mem pref disabled]
[    0.893356] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.893358] pci 0000:00:01.0: setting latency timer to 64
[    0.893364] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.893367] pci 0000:00:1c.0: setting latency timer to 64
[    0.893374] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.893377] pci 0000:00:1c.2: setting latency timer to 64
[    0.893383] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.893386] pci 0000:00:1c.3: setting latency timer to 64
[    0.893390] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.893393] pci 0000:00:1c.4: setting latency timer to 64
[    0.893398] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.893403] pci 0000:05:00.0: setting latency timer to 64
[    0.893408] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.893411] pci 0000:00:1c.5: setting latency timer to 64
[    0.893416] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.893418] pci 0000:00:1c.6: setting latency timer to 64
[    0.893423] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.893426] pci 0000:00:1c.7: setting latency timer to 64
[    0.893428] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.893430] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.893431] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.893432] pci_bus 0000:00: resource 7 [mem 0x000c8000-0x000dffff]
[    0.893433] pci_bus 0000:00: resource 8 [mem 0xe4000000-0xffffffff]
[    0.893434] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.893435] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfa0fffff]
[    0.893437] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf3ffffff 64bit pref]
[    0.893438] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.893439] pci_bus 0000:05: resource 1 [mem 0xfa300000-0xfa3fffff]
[    0.893440] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.893441] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.893443] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.893444] pci_bus 0000:05: resource 7 [mem 0x000c8000-0x000dffff]
[    0.893445] pci_bus 0000:05: resource 8 [mem 0xe4000000-0xffffffff]
[    0.893446] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    0.893447] pci_bus 0000:06: resource 1 [mem 0xfa300000-0xfa3fffff]
[    0.893448] pci_bus 0000:06: resource 4 [io  0xd000-0xdfff]
[    0.893449] pci_bus 0000:06: resource 5 [mem 0xfa300000-0xfa3fffff]
[    0.893459] pci_bus 0000:06: resource 8 [io  0x0000-0x0cf7]
[    0.893460] pci_bus 0000:06: resource 9 [io  0x0d00-0xffff]
[    0.893461] pci_bus 0000:06: resource 10 [mem 0x000a0000-0x000bffff]
[    0.893462] pci_bus 0000:06: resource 11 [mem 0x000c8000-0x000dffff]
[    0.893464] pci_bus 0000:06: resource 12 [mem 0xe4000000-0xffffffff]
[    0.893465] pci_bus 0000:07: resource 0 [io  0xc000-0xcfff]
[    0.893466] pci_bus 0000:07: resource 2 [mem 0xf4100000-0xf41fffff 64bit pref]
[    0.893467] pci_bus 0000:08: resource 0 [io  0xb000-0xbfff]
[    0.893468] pci_bus 0000:08: resource 1 [mem 0xfa200000-0xfa2fffff]
[    0.893470] pci_bus 0000:09: resource 1 [mem 0xfa100000-0xfa1fffff]
[    0.893485] NET: Registered protocol family 2
[    0.893642] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.894294] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.895164] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.895260] TCP: Hash tables configured (established 524288 bind 65536)
[    0.895261] TCP reno registered
[    0.895271] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.895296] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.895355] NET: Registered protocol family 1
[    1.150100] Freeing initrd memory: 12828k freed
[    1.153308] pci 0000:01:00.0: Boot video device
[    1.153367] PCI: CLS 64 bytes, default 64
[    1.153368] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.153370] Placing 64MB software IO TLB between ffff8800db051000 - ffff8800df051000
[    1.153371] software IO TLB at phys 0xdb051000 - 0xdf051000
[    1.153643] audit: initializing netlink socket (disabled)
[    1.153649] type=2000 audit(1304540111.010:1): initialized
[    1.161883] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.162803] VFS: Disk quotas dquot_6.5.2
[    1.162831] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.163153] fuse init (API version 7.16)
[    1.163197] msgmni has been set to 15962
[    1.163320] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.163332] io scheduler noop registered
[    1.163333] io scheduler deadline registered
[    1.163353] io scheduler cfq registered (default)
[    1.163411] pcieport 0000:00:01.0: setting latency timer to 64
[    1.163429] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.163466] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.163501] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.163555] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.163590] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.163643] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.163678] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.163731] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.163765] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    1.163819] pcieport 0000:00:1c.6: setting latency timer to 64
[    1.163854] pcieport 0000:00:1c.6: irq 45 for MSI/MSI-X
[    1.163906] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.163941] pcieport 0000:00:1c.7: irq 46 for MSI/MSI-X
[    1.164002] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.164004] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.164005] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.164006] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.164018] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.164022] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.164034] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    1.164037] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    1.164048] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.164051] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    1.164064] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    1.164065] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    1.164068] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    1.164080] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    1.164082] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    1.164083] pci 0000:08:00.1: Signaling PME through PCIe PME interrupt
[    1.164085] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    1.164097] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    1.164099] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    1.164102] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    1.164110] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.164122] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.164146] intel_idle: MWAIT substates: 0x1120
[    1.164147] intel_idle: v0.4 model 0x2A
[    1.164148] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.164211] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.164214] ACPI: Power Button [PWRB]
[    1.164237] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.164239] ACPI: Power Button [PWRF]
[    1.164336] ACPI: acpi_idle yielding to intel_idle
[    1.165307] ERST: Table is not found!
[    1.165348] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.185879] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.354588] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.354740] Linux agpgart interface v0.103
[    1.355348] brd: module loaded
[    1.355599] loop: module loaded
[    1.355638] i2c-core: driver [adp5520] using legacy suspend method
[    1.355639] i2c-core: driver [adp5520] using legacy resume method
[    1.355700] pata_acpi 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.355715] pata_acpi 0000:08:00.0: setting latency timer to 64
[    1.355725] pata_acpi 0000:08:00.0: PCI INT A disabled
[    1.355733] pata_acpi 0000:08:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.355744] pata_acpi 0000:08:00.1: setting latency timer to 64
[    1.355751] pata_acpi 0000:08:00.1: PCI INT B disabled
[    1.355896] Fixed MDIO Bus: probed
[    1.355910] PPP generic driver version 2.4.2
[    1.355928] tun: Universal TUN/TAP device driver, 1.6
[    1.355929] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.355971] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.355981] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.355994] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.355996] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.356017] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.356050] ehci_hcd 0000:00:1a.0: debug port 2
[    1.359939] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.359950] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfa407000
[    1.383117] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.383186] hub 1-0:1.0: USB hub found
[    1.383189] hub 1-0:1.0: 2 ports detected
[    1.383225] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.383233] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.383236] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.383254] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.383284] ehci_hcd 0000:00:1d.0: debug port 2
[    1.387175] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.387178] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfa406000
[    1.403103] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.403158] hub 2-0:1.0: USB hub found
[    1.403160] hub 2-0:1.0: 2 ports detected
[    1.403195] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.403201] uhci_hcd: USB Universal Host Controller Interface driver
[    1.403255] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.405787] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.405790] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.405848] mousedev: PS/2 mouse device common for all mice
[    1.405909] rtc_cmos 00:04: RTC can wake from S4
[    1.405941] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.405963] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.406013] device-mapper: uevent: version 1.0.3
[    1.406053] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.406084] device-mapper: multipath: version 1.2.0 loaded
[    1.406086] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.406188] cpuidle: using governor ladder
[    1.406269] cpuidle: using governor menu
[    1.406384] TCP cubic registered
[    1.406445] NET: Registered protocol family 10
[    1.406676] NET: Registered protocol family 17
[    1.406685] Registering the dns_resolver key type
[    1.407303] PM: Hibernation image not present or could not be loaded.
[    1.407307] registered taskstats version 1
[    1.407597]   Magic number: 11:135:295
[    1.407602] tty tty28: hash matches
[    1.407705] rtc_cmos 00:04: setting system clock to 2011-05-04 20:15:11 UTC (1304540111)
[    1.407707] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.407707] EDD information not available.
[    1.408587] Freeing unused kernel memory: 956k freed
[    1.408657] Write protecting the kernel read-only data: 10240k
[    1.409220] Freeing unused kernel memory: 184k freed
[    1.411602] Freeing unused kernel memory: 1444k freed
[    1.421276] <30>udev[68]: starting version 167
[    1.436808] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.436823] r8169 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.436856] r8169 0000:07:00.0: setting latency timer to 64
[    1.436860] r8169 0000:07:00.0: (unregistered net_device): unknown MAC, using family default
[    1.436916] r8169 0000:07:00.0: irq 47 for MSI/MSI-X
[    1.437099] r8169 0000:07:00.0: eth0: RTL8168b/8111b at 0xffffc90005788000, bc:ae:c5:68:83:78, XID 0c200000 IRQ 47
[    1.442291] ahci 0000:00:1f.2: version 3.0
[    1.442304] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.442330] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    1.446914] firewire_ohci 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.463328] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x30 impl SATA mode
[    1.463330] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.463333] ahci 0000:00:1f.2: setting latency timer to 64
[    1.483462] scsi0 : ahci
[    1.483588] scsi1 : ahci
[    1.483689] scsi2 : ahci
[    1.483792] scsi3 : ahci
[    1.483900] scsi4 : ahci
[    1.484016] scsi5 : ahci
[    1.484213] ata1: DUMMY
[    1.484215] ata2: DUMMY
[    1.484217] ata3: DUMMY
[    1.484218] ata4: DUMMY
[    1.484221] ata5: SATA max UDMA/133 abar m2048@0xfa405000 port 0xfa405300 irq 48
[    1.484224] ata6: SATA max UDMA/133 abar m2048@0xfa405000 port 0xfa405380 irq 48
[    1.523167] firewire_ohci: Added fw-ohci device 0000:06:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    1.702957] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.832869] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.832893] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.834060] ata5.00: ATA-8: ST31000520AS, CC32, max UDMA/133
[    1.834064] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.834555] ata6.00: ATAPI: Optiarc DVD RW AD-7260S, 1.03, max UDMA/100
[    1.835439] ata5.00: configured for UDMA/133
[    1.835642] scsi 4:0:0:0: Direct-Access     ATA      ST31000520AS     CC32 PQ: 0 ANSI: 5
[    1.835714] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.835753] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.835924] sd 4:0:0:0: [sda] Write Protect is off
[    1.835925] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.835998] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.836498] ata6.00: configured for UDMA/100
[    1.838367] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.03 PQ: 0 ANSI: 5
[    1.840455] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.840456] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.840499] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.840524] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.853457] hub 1-1:1.0: USB hub found
[    1.853588] hub 1-1:1.0: 6 ports detected
[    1.897203]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.897742] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.972716] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.022721] firewire_core: created device fw0: GUID 001fc600000d75d6, S400
[    2.123143] hub 2-1:1.0: USB hub found
[    2.123216] hub 2-1:1.0: 8 ports detected
[    2.152580] Refined TSC clocksource calibration: 3399.621 MHz.
[    2.152582] Switching to clocksource tsc
[    2.294673] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.294675] EXT4-fs (sda5): write access will be enabled during recovery
[    2.402553] usb 2-1.1: new low speed USB device using ehci_hcd and address 3
[    2.533105] input: Microsoft Microsoft® Comfort Mouse 4500 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    2.533152] generic-usb 0003:045E:076C.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft® Comfort Mouse 4500] on usb-0000:00:1d.0-1.1/input0
[    2.533159] usbcore: registered new interface driver usbhid
[    2.533159] usbhid: USB HID core driver
[    2.592430] usb 2-1.2: new low speed USB device using ehci_hcd and address 4
[    2.792184] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
[    2.792234] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.0-1.2/input0
[    2.803190] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input4
[    2.803226] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.0-1.2/input1
[    3.297905] EXT4-fs (sda5): orphan cleanup on readonly fs
[    3.297909] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524292
[    3.297945] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524291
[    3.297950] EXT4-fs (sda5): 2 orphan inodes deleted
[    3.297951] EXT4-fs (sda5): recovery complete
[    3.681486] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   18.304531] <30>udev[302]: starting version 167
[   18.314878] xhci_hcd 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.314895] xhci_hcd 0000:09:00.0: setting latency timer to 64
[   18.314898] xhci_hcd 0000:09:00.0: xHCI Host Controller
[   18.314932] xhci_hcd 0000:09:00.0: new USB bus registered, assigned bus number 3
[   18.318552] lp: driver loaded but no devices found
[   18.327005] Adding 16382972k swap on /dev/sda4.  Priority:-1 extents:1 across:16382972k 
[   18.351942] nvidia: module license 'NVIDIA' taints kernel.
[   18.351944] Disabling lock debugging due to kernel taint
[   18.366789] cfg80211: Calling CRDA to update world regulatory domain
[   18.370569] type=1400 audit(1304561728.459:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=365 comm="apparmor_parser"
[   18.370954] type=1400 audit(1304561728.459:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=365 comm="apparmor_parser"
[   18.371196] type=1400 audit(1304561728.459:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=365 comm="apparmor_parser"
[   18.371872] type=1400 audit(1304561728.469:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=537 comm="apparmor_parser"
[   18.372256] type=1400 audit(1304561728.469:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=537 comm="apparmor_parser"
[   18.372499] type=1400 audit(1304561728.469:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=537 comm="apparmor_parser"
[   18.378491] xhci_hcd 0000:09:00.0: irq 19, io mem 0xfa100000
[   18.378545] xhci_hcd 0000:09:00.0: irq 49 for MSI/MSI-X
[   18.378547] xhci_hcd 0000:09:00.0: irq 50 for MSI/MSI-X
[   18.378549] xhci_hcd 0000:09:00.0: irq 51 for MSI/MSI-X
[   18.378551] xhci_hcd 0000:09:00.0: irq 52 for MSI/MSI-X
[   18.378553] xhci_hcd 0000:09:00.0: irq 53 for MSI/MSI-X
[   18.384145] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   18.384195] xHCI xhci_add_endpoint called for root hub
[   18.384196] xHCI xhci_check_bandwidth called for root hub
[   18.384211] hub 3-0:1.0: USB hub found
[   18.384213] hub 3-0:1.0: 4 ports detected
[   18.389009] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[   18.405218] rt61pci 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.409233] cfg80211: World regulatory domain updated:
[   18.409234] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.409236] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.409237] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.409238] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.409239] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.409240] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.414322] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.414323] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414324] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.414325] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414326] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.414327] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414328] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.414329] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414330] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.414331] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414332] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.414333] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414333] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.414334] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414335] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.414336] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414337] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.414338] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414339] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.414340] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414341] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.414342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414343] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.414344] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414345] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.414346] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.414346] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.414348] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.417264] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.417482] Registered led device: rt61pci-phy0::radio
[   18.417489] Registered led device: rt61pci-phy0::assoc
[   18.423622] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.423657] HDA Intel 0000:00:1b.0: irq 54 for MSI/MSI-X
[   18.423674] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.525499] hda_codec: ALC892: BIOS auto-probing.
[   18.531403] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.531464] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.531465] hda_intel: Disable MSI for Nvidia chipset
[   18.531525] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.681318] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr
[   18.737119] type=1400 audit(1304561728.829:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=786 comm="apparmor_parser"
[   18.737565] type=1400 audit(1304561728.829:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=786 comm="apparmor_parser"
[   18.738230] type=1400 audit(1304561728.829:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=784 comm="apparmor_parser"
[   18.739054] type=1400 audit(1304561728.829:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd" pid=787 comm="apparmor_parser"
[   18.862643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.067049] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   20.392031] ppdev: user-space parallel port driver
[   20.779914] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.779920] nvidia 0000:01:00.0: setting latency timer to 64
[   20.779923] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.780024] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   20.882868] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90007e80000, using 512k, total 512k
[   20.882870] vesafb: mode is 800x600x8, linelength=800, pages=0
[   20.882871] vesafb: scrolling: redraw
[   20.882872] vesafb: Pseudocolor: size=0:6:6:6, shift=0:0:0:0
[   20.882937] Console: switching to colour frame buffer device 100x37
[   20.882944] fb0: VESA VGA frame buffer device
[   20.900578] r8169 0000:07:00.0: eth0: link down
[   20.900881] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.900890] device eth0 entered promiscuous mode
[   21.003160] ioremap error for 0xdf49e000-0xdf49f000, requested 0x10, got 0x0
[   21.609313] wlan0: authenticate with 00:23:69:06:f6:47 (try 1)
[   21.610426] wlan0: authenticated
[   21.610573] wlan0: associate with 00:23:69:06:f6:47 (try 1)
[   21.612144] wlan0: RX AssocResp from 00:23:69:06:f6:47 (capab=0x411 status=0 aid=4)
[   21.612146] wlan0: associated
[   21.612612] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.612641] cfg80211: Calling CRDA for country: TW
[   21.614249] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   21.614251] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614252] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   21.614253] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614254] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   21.614255] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614256] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   21.614257] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614258] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   21.614259] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614260] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   21.614261] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614262] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   21.614263] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614264] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   21.614265] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614266] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   21.614267] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614268] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   21.614269] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614269] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   21.614270] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   21.614271] cfg80211: Disabling freq 2467 MHz
[   21.614272] cfg80211: Disabling freq 2472 MHz
[   21.614273] cfg80211: Disabling freq 2484 MHz
[   21.614274] cfg80211: Regulatory domain changed to country: TW
[   21.614274] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.614275] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.614276] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   21.614277] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   21.634923] vboxdrv: Found 4 processor cores.
[   21.635027] vboxdrv: fAsync=0 offMin=0x165 offMax=0xb85
[   21.635112] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.635113] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   22.399478] padlock_aes: VIA PadLock not detected.
[   24.750017] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   25.183281] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   32.561374] wlan0: no IPv6 routers present

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 00
       serial: 00:0c:0a:42:34:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.1.109 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa300000-fa307fff

$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:06:F6:47
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"HolmesWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006de8b99151
                    Extra: Last beacon: 1090ms ago
                    IE: Unknown: 000A486F6C6D657357494649
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A88000236906F6471021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
          Cell 02 - Address: 00:22:6B:03:C0:2C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"@HomeC02C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f16f9f67ad
                    Extra: Last beacon: 14170ms ago
                    IE: Unknown: 000940486F6D6543303243
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4301000000
          Cell 03 - Address: 00:90:4B:CF:02:3E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"viewsonic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f170b6f6c6
                    Extra: Last beacon: 14150ms ago
                    IE: Unknown: 000976696577736F6E6963
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

$ lsb_release -d
Description:	Ubuntu 11.04

$ uname -mr
2.6.38-8-generic x86_64

```

Wireless not working:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)
01:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller (rev a1)
05:00.0 PCI bridge: Device 1b21:1080 (rev 01)
06:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 IDE interface: Marvell Technology Group Ltd. Device 91b0 (rev 11)
08:00.1 IDE interface: Marvell Technology Group Ltd. Device 91a4 (rev 11)
09:00.0 USB Controller: Device 1b21:1042

$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 002 Device 003: ID 045e:076c Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:68:83:78  
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85136 (85.1 KB)  TX bytes:85136 (85.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:0a:42:34:8c  
          inet6 addr: fe80::20c:aff:fe42:348c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2683456 (2.6 MB)  TX bytes:846811 (846.8 KB)

$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off     

$ lsmod
Module                  Size  Used by
aesni_intel            55161  0 
cryptd                 20510  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            38279  2 aesni_intel,aes_x86_64
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vesafb                 13761  1 
ppdev                  17113  0 
parport_pc             36959  0 
snd_hda_codec_hdmi     28103  4 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336693  1 
psmouse                73535  0 
joydev                 17606  0 
snd_hda_intel          33211  2 
nvidia              10709116  40 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
rt61pci                27888  0 
rt2x00pci              14322  1 rt61pci
snd_seq_midi_event     14899  1 snd_seq_midi
rt2x00lib              49235  2 rt61pci,rt2x00pci
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  2 rt2x00pci,rt2x00lib
eeepc_wmi              19323  0 
sparse_keymap          13898  1 eeepc_wmi
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt61pci
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xhci_hcd               77643  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  2 rt61pci,firewire_core
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 

$ dmesg
...
[  256.923525] irq 18: nobody cared (try booting with the "irqpoll" option)
[  256.923528] Pid: 2103, comm: npviewer.bin Tainted: P            2.6.38-8-generic #42-Ubuntu
[  256.923529] Call Trace:
[  256.923530]  <IRQ>  [<ffffffff810d511b>] ? __report_bad_irq.clone.2+0x2b/0xa0
[  256.923535]  [<ffffffff810d551a>] ? note_interrupt+0x19a/0x1e0
[  256.923537]  [<ffffffff810d640d>] ? handle_fasteoi_irq+0xdd/0x110
[  256.923539]  [<ffffffff8100e9c2>] ? handle_irq+0x22/0x40
[  256.923542]  [<ffffffff815caebd>] ? do_IRQ+0x5d/0xe0
[  256.923543]  [<ffffffff815c3213>] ? ret_from_intr+0x0/0x15
[  256.923544]  <EOI> 
[  256.923545] handlers:
[  256.923545] [<ffffffffa0c74ea0>] (rt61pci_interrupt+0x0/0x90 [rt61pci])
[  256.923550] Disabling IRQ #18
[  260.472341] ieee80211 phy0: wlan0: No probe response from AP 00:23:69:06:f6:47 after 500ms, disconnecting.
[  262.532417] cfg80211: All devices are disconnected, going to restore regulatory settings
[  262.532422] cfg80211: Restoring regulatory settings
[  262.532426] cfg80211: Calling CRDA to update world regulatory domain
[  262.534752] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  262.534754] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534755] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  262.534756] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534757] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  262.534758] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534759] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  262.534760] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534761] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  262.534762] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534762] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  262.534763] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534764] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  262.534765] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534766] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  262.534767] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534768] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  262.534769] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534770] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  262.534771] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534772] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  262.534773] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534774] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  262.534775] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534776] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  262.534777] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534777] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  262.534779] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  262.534780] cfg80211: World regulatory domain updated:
[  262.534780] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  262.534782] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  262.534783] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  262.534784] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  262.534784] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  262.534785] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 00
       serial: 00:0c:0a:42:34:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 latency=32 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa300000-fa307fff

$ iwlist scan

wlan0     No scan results

```

---

### Post by sheds on 2011-05-05
Hi man.

Paste the output of the following command, to see if any devices are having problems.

rfkill list all

rfkill -> tool for enabling and disabling wireless devices

Also, try to use wicd and remove the network manager that used to work on 10.xx, doesn't work that well in 11.04, at least from my experience.

---

### Post by JHolmes763 on 2011-05-05
Same result whether wireless was working or not:

```
$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by JHolmes763 on 2011-05-05
Also, I have wicd installed:

```
wicd is already the newest version.
```

Not sure if there's anything I have to do after installation to use/configure it, though. Everything looks the same.

Edit to add: Okay, so I found the WICD configuration GUI. I checked "Automatically connect to this network" for my SSID and supplied the WPA password under properties. 

Wireless is still working... we'll see how long this lasts. :)

---

### Post by JKoder on 2011-05-05
I had this problem also.
My fix was to disable Bluetooth ( from startup ) .

Since then everything is just great with my wireles. No more disconnections !

You can also try it

---

### Post by JHolmes763 on 2011-05-05
Thanks for the help. I disabled BlueTooth Manager from the Startup Applications list, but that did not change anything. Wireless still dropped out about a minute after logging in. 


I see "WICD Network Manager Tray" listed in the startup applications, but I do not see anything in the tray area. Just the normal wireless icon. If I log in using the "Ubuntu Classic" interface, then I see the WICD icon. Wireless still drops out in either interface after several minutes, though. 

The time it drops out is random. It's been up for 10 minutes right now, which is very long compared to other reboots. 

Thanks again for any further help.

---

### Post by JHolmes763 on 2011-05-05
So it lasted for 17 minutes that time. Looking at dmesg, this pops up every time the wireless fails. Can anyone translate into a solution?

```
[  992.696554] irq 18: nobody cared (try booting with the "irqpoll" option)
[  992.696557] Pid: 0, comm: swapper Tainted: P            2.6.38-8-generic #42-Ubuntu
[  992.696558] Call Trace:
[  992.696559]  <IRQ>  [<ffffffff810d511b>] ? __report_bad_irq.clone.2+0x2b/0xa0
[  992.696565]  [<ffffffff810d551a>] ? note_interrupt+0x19a/0x1e0
[  992.696566]  [<ffffffff810d640d>] ? handle_fasteoi_irq+0xdd/0x110
[  992.696569]  [<ffffffff8100e9c2>] ? handle_irq+0x22/0x40
[  992.696571]  [<ffffffff815caebd>] ? do_IRQ+0x5d/0xe0
[  992.696573]  [<ffffffff815c3213>] ? ret_from_intr+0x0/0x15
[  992.696573]  <EOI>  [<ffffffff8133685a>] ? intel_idle+0xca/0x120
[  992.696577]  [<ffffffff81336839>] ? intel_idle+0xa9/0x120
[  992.696579]  [<ffffffff814a3bda>] ? cpuidle_idle_call+0xaa/0x1b0
[  992.696582]  [<ffffffff8100a266>] ? cpu_idle+0xa6/0xf0
[  992.696583]  [<ffffffff815a9205>] ? rest_init+0x75/0x80
[  992.696586]  [<ffffffff81acac8b>] ? start_kernel+0x3f5/0x400
[  992.696588]  [<ffffffff81aca388>] ? x86_64_start_reservations+0x132/0x136
[  992.696589]  [<ffffffff81aca253>] ? zap_identity_mappings+0x3e/0x41
[  992.696591]  [<ffffffff81aca458>] ? x86_64_start_kernel+0xcc/0xdb
[  992.696592] handlers:
[  992.696592] [<ffffffffa0ce0ea0>] (rt61pci_interrupt+0x0/0x90 [rt61pci])
[  992.696597] Disabling IRQ #18
[  996.045282] ieee80211 phy0: wlan0: No probe response from AP 00:23:69:06:f6:47 after 500ms, disconnecting.
[  998.154924] cfg80211: All devices are disconnected, going to restore regulatory settings
[  998.154930] cfg80211: Restoring regulatory settings
[  998.154934] cfg80211: Calling CRDA to update world regulatory domain
```

---

### Post by JHolmes763 on 2011-05-05
Okay... this time IRQ #19 "failed" and wireless has been up for nearly 30 minutes. 

```
[  413.692699] irq 19: nobody cared (try booting with the "irqpoll" option)
[  413.692702] Pid: 0, comm: swapper Tainted: P            2.6.38-8-generic #42-Ubuntu
[  413.692703] Call Trace:
[  413.692704]  <IRQ>  [<ffffffff810d511b>] ? __report_bad_irq.clone.2+0x2b/0xa0
[  413.692710]  [<ffffffff810d551a>] ? note_interrupt+0x19a/0x1e0
[  413.692711]  [<ffffffff810d640d>] ? handle_fasteoi_irq+0xdd/0x110
[  413.692714]  [<ffffffff8100e9c2>] ? handle_irq+0x22/0x40
[  413.692716]  [<ffffffff815caebd>] ? do_IRQ+0x5d/0xe0
[  413.692718]  [<ffffffff815c3213>] ? ret_from_intr+0x0/0x15
[  413.692718]  <EOI>  [<ffffffff8133685a>] ? intel_idle+0xca/0x120
[  413.692722]  [<ffffffff81336839>] ? intel_idle+0xa9/0x120
[  413.692724]  [<ffffffff814a3bda>] ? cpuidle_idle_call+0xaa/0x1b0
[  413.692726]  [<ffffffff8100a266>] ? cpu_idle+0xa6/0xf0
[  413.692728]  [<ffffffff815a9205>] ? rest_init+0x75/0x80
[  413.692731]  [<ffffffff81acac8b>] ? start_kernel+0x3f5/0x400
[  413.692733]  [<ffffffff81aca388>] ? x86_64_start_reservations+0x132/0x136
[  413.692734]  [<ffffffff81aca253>] ? zap_identity_mappings+0x3e/0x41
[  413.692736]  [<ffffffff81aca458>] ? x86_64_start_kernel+0xcc/0xdb
[  413.692737] handlers:
[  413.692737] [<ffffffffa0049060>] (irq_handler+0x0/0x3e0 [firewire_ohci])
[  413.692744] Disabling IRQ #19
```

I can't believe that anything was really fixed, though. Maybe I should just never reboot?? :D

---

### Post by JHolmes763 on 2011-05-05
Well, it lasted 35 minutes that time, then IRQ #18 failed and wireless dropped out. Here's the log. The "queue_write_tx_frame" messages at the end are new. I have not seen them before:

```

[ 1912.754433] irq 18: nobody cared (try booting with the "irqpoll" option)
[ 1912.754439] Pid: 2430, comm: npviewer.bin Tainted: P            2.6.38-8-generic #42-Ubuntu
[ 1912.754442] Call Trace:
[ 1912.754444]  <IRQ>  [<ffffffff810d511b>] ? __report_bad_irq.clone.2+0x2b/0xa0
[ 1912.754457]  [<ffffffff810d551a>] ? note_interrupt+0x19a/0x1e0
[ 1912.754462]  [<ffffffff8106d589>] ? __do_softirq+0xf9/0x1c0
[ 1912.754465]  [<ffffffff810d640d>] ? handle_fasteoi_irq+0xdd/0x110
[ 1912.754470]  [<ffffffff8100e9c2>] ? handle_irq+0x22/0x40
[ 1912.754475]  [<ffffffff815caebd>] ? do_IRQ+0x5d/0xe0
[ 1912.754479]  [<ffffffff815c3213>] ? ret_from_intr+0x0/0x15
[ 1912.754481]  <EOI>  [<ffffffff810486b0>] ? sysenter_dispatch+0x7/0x2e
[ 1912.754486] handlers:
[ 1912.754488] [<ffffffffa00b0ea0>] (rt61pci_interrupt+0x0/0x90 [rt61pci])
[ 1912.754496] Disabling IRQ #18
[ 1916.824158] ieee80211 phy0: wlan0: No probe response from AP 00:23:69:06:f6:47 after 500ms, disconnecting.
[ 1920.873777] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1920.873783] cfg80211: Restoring regulatory settings
[ 1920.873787] cfg80211: Calling CRDA to update world regulatory domain
[ 1920.877475] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877479] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877482] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877485] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877487] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877492] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877495] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877497] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877500] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877502] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877505] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877507] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877510] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877512] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877515] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877517] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877519] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877522] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877524] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877527] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877529] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877531] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877534] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877537] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877539] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877542] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1920.877545] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1920.877548] cfg80211: World regulatory domain updated:
[ 1920.877549] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1920.877552] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1920.877555] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1920.877558] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1920.877560] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1920.877563] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1937.192071] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1937.430826] r8169 0000:07:00.0: eth0: link down
[ 1937.431543] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1937.929404] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1937.929406] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1940.578956] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1940.578959] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1944.334958] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1944.334961] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1946.443472] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1946.443474] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1949.782438] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1949.782441] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1951.849705] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1951.849707] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1953.929829] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1953.929832] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1957.307291] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1957.307294] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1959.334503] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1959.334506] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1961.383608] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1961.383611] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1964.780753] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1964.780756] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1966.829287] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1966.829290] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1968.868924] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1968.868927] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1972.246559] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1972.246561] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1977.192012] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1977.192014] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1979.272135] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1979.272138] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1982.619642] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1982.619645] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1987.574786] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1987.574789] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1989.614910] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1989.614912] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1993.021912] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1993.021915] Please file bug report to http://rt2x00.serialmonkey.com.
[ 1997.957531] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 1997.957534] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2000.037054] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2000.037057] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2003.405115] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2003.405118] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2005.432315] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2005.432317] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2007.512441] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2007.512444] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2010.939867] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2010.939870] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2011.045877] show_signal_msg: 27 callbacks suppressed
[ 2011.045883] midori[2407]: segfault at 3fb7ffffff0 ip 00007f7e56b6e49f sp 00007fffe81fbff8 error 4 in libc-2.13.so[7f7e56a3f000+18a000]
[ 2011.155415] npviewer.bin[2489]: segfault at e734b0a4 ip 00000000f5fe6cb0 sp 00000000e89f4070 error 4 in libflashplayer.so[f5d33000+b5f000]
[ 2015.825090] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2015.825093] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2017.875206] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2017.875209] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2021.232586] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2021.232589] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2026.197814] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2026.197817] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2028.237861] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2028.237864] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2031.615336] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2031.615338] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2036.580593] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2036.580596] Please file bug report to http://rt2x00.serialmonkey.com.
[ 2038.610753] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0.
[ 2038.610756] Please file bug report to http://rt2x00.serialmonkey.com.

```

---

### Post by JHolmes763 on 2011-05-05
I tried booting with the "irqpoll" option set in /etc/default/grub, but wireless would not work at all then. Starting WICD and doing a scan resulted in "no wireless networks found".

---

### Post by zilmar on 2011-05-05
Why don't you try to install the drive from 10.10?
I had a similar problem, installed bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb and everything worked fine.

---

### Post by JHolmes763 on 2011-05-19
I tried compiling various older drivers, but I kept getting errors. I just went back to 10.10 for this machine. 11.04 works fine on my laptops and netbook, however.

---

### Post by Blastwizard on 2011-05-30
I think it is the same problem I have, the wireless drops after a few seconds or minutes, but it doesn't happen when the netbook is on AC power, I suspect a problem with the ACPI not giving enough power to wireless.

---

### Post by mrmcgibby on 2011-06-25
I am having the precisely the same problem.  I'll be trying bluetooth and so forth.

---

### Post by mrmcgibby on 2011-06-29
I have reported the OP problem (and mine) as a bug.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803708)

---

