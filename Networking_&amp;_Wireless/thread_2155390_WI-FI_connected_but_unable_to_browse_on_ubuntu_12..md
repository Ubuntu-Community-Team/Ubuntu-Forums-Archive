---
title: "WI-FI connected but unable to browse on ubuntu 12.04 lts using hp mini"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by rikki1913 on 2013-06-18
titel: WI-FI connects but no browsing on Ubuntu 12.04 LTS using HP Mini netbook

Hello experts,

I am posting because I cannot browse the internet on wi-fi anymore, which used to work fine, while WICD does connect to my network. Also, I am able to use the same wi-fi network on my cellphone. I have searched on google extensively (using my cellphone) for a solution, tried some things, and still nothing. Also, I don't know much about internet or linux in general. So I'm hoping someone here can figure out the problem.

The sticky-topic said to post as much information as I can, so I added below the result of recommended commands. I am kind of desperate, so any help is greatly appreciated.

I am using the HP Mini netbook.

```

$ ping -c5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4033ms

bloed@bloed-HP-Mini-110-3000:~$ ping -c5 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.106 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.059 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.067 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.059/0.073/0.106/0.017 ms
bloed@bloed-HP-Mini-110-3000:~$ ping -c5 www.google.com
ping: unknown host www.google.com
bloed@bloed-HP-Mini-110-3000:~$ ping -c3 74.125.47.99
PING 74.125.47.99 (74.125.47.99) 56(84) bytes of data.

--- 74.125.47.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms



```

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


```

```

$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. PCI Express Card Reader (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 1004:61c5 LG Electronics, Inc. 

```

```

$ lspci -nn | grep "Wireless Brand"
bloed@bloed-HP-Mini-110-3000:~$

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:48:7c:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:392793 (392.7 KB)  TX bytes:392793 (392.7 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:3f:bc:49  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe3f:bc49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80880 (80.8 KB)  TX bytes:411646 (411.6 KB)



```

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bagijnestraat"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 7A:2B:C1:CC:4D:08   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

eth0      no wireless extensions.


```

```

$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55605  1 vfat
cdc_ether              13312  0 
usbnet                 25214  1 cdc_ether
cdc_acm                22277  0 
usb_storage            39646  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158479  10 rfcomm,bnep
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                86520  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28931  2 snd_pcm,snd_seq
ath9k                 117356  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436493  1 ath9k
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  423564  3 
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
wmi                    18744  1 hp_wmi
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
rts_pstor             353252  0 
cfg80211              178877  3 ath9k,mac80211,ath
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 


```

```

dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-41-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66-Ubuntu SMP Thu Apr 25 03:50:20 UTC 2013 (Ubuntu 3.2.0-41.66-generic-pae 3.2.42)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  BIOS-e820: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5f7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5f7000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Mini 110-3000                /148A, BIOS F.06 05/26/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask 0FFE00000 write-protect
[    0.000000]   1 base 000000000 mask 0E0000000 write-back
[    0.000000]   2 base 020000000 mask 0E0000000 write-back
[    0.000000]   3 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 364dc000 - 37266000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 3f5f6120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 3f5f5000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 3f5e6000 0B13E (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 3f589000 00040
[    0.000000] ACPI: HPET 3f5f4000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 3f5f3000 00078 (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 3f5f2000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 3f5e5000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 3f5e4000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 3f5e3000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e2000 001F7 (v02  PmRef  Cpu0Tst 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e1000 00064 (v02  PmRef  Cpu1Tst 00003000 INTL 20051117)
[    0.000000] ACPI: WDAT 3f5e0000 00194 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f43f
[    0.000000]     0: 0x0003f5f7 -> 0x0003f600
[    0.000000] On node 0 totalpages: 259031
[    0.000000] free_area_init_node: node 0, pgdat c186d8c0, node_mem_map f740d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 245 pages used for memmap
[    0.000000]   HighMem zone: 30549 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73cf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257002
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-41-generic-pae root=UUID=599594ce-dc4d-4c2a-80dd-f95783ca2332 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4153088 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f600)
[    0.000000] Memory: 998628k/1038336k available (5830k kernel code, 37496k reserved, 2853k data, 744k init, 123176k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc187c000 - 0xc1936000   ( 744 kB)
[    0.000000]       .data : 0xc15b1abc - 0xc187b100   (2853 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b1abc   (5830 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f5c0a000 soft=f5c0c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.726 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.45 BogoMIPS (lpj=6650904)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004071] Security Framework initialized
[    0.004110] AppArmor: AppArmor initialized
[    0.004115] Yama: becoming mindful.
[    0.004238] Mount-cache hash table entries: 512
[    0.004506] Initializing cgroup subsys cpuacct
[    0.004522] Initializing cgroup subsys memory
[    0.004540] Initializing cgroup subsys devices
[    0.004546] Initializing cgroup subsys freezer
[    0.004552] Initializing cgroup subsys blkio
[    0.004566] Initializing cgroup subsys perf_event
[    0.004611] Disabled fast string operations
[    0.004620] CPU: Physical Processor ID: 0
[    0.004624] CPU: Processor Core ID: 0
[    0.004631] mce: CPU supports 5 MCE banks
[    0.004643] CPU0: Thermal monitoring handled by SMI
[    0.004652] using mwait in idle threads.
[    0.011422] ACPI: Core revision 20110623
[    0.028030] ftrace: allocating 26115 entries in 52 pages
[    0.036101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036613] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078420] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.080004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.080004] ... version:                3
[    0.080004] ... bit width:              40
[    0.080004] ... generic registers:      2
[    0.080004] ... value mask:             000000ffffffffff
[    0.080004] ... max period:             000000007fffffff
[    0.080004] ... fixed-purpose events:   3
[    0.080004] ... event mask:             0000000700000003
[    0.080004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.080004] CPU 1 irqstacks, hard=f5d12000 soft=f5d14000
[    0.080004] Booting Node   0, Processors  #1
[    0.080004] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.168074] NMI watchdog enabled, takes one hw-pmu counter.
[    0.168155] Brought up 2 CPUs
[    0.168163] Total of 2 processors activated (6650.76 BogoMIPS).
[    0.168733] devtmpfs: initialized
[    0.168733] EVM: security.selinux
[    0.168733] EVM: security.SMACK64
[    0.168733] EVM: security.capability
[    0.168733] PM: Registering ACPI NVS region at 3f4bf000 (1048576 bytes)
[    0.172719] print_constraints: dummy: 
[    0.172777] RTC time:  5:37:09, date: 06/18/13
[    0.172871] NET: Registered protocol family 16
[    0.172897] Trying to unpack rootfs image as initramfs...
[    0.173388] EISA bus registered
[    0.173435] ACPI: bus type pci registered
[    0.173675] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.173687] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.173694] PCI: Using MMCONFIG for extended config space
[    0.173701] PCI: Using configuration type 1 for base access
[    0.188596] bio: create slab <bio-0> at 0
[    0.188598] ACPI: Added _OSI(Module Device)
[    0.188607] ACPI: Added _OSI(Processor Device)
[    0.188615] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.188623] ACPI: Added _OSI(Processor Aggregator Device)
[    0.194808] ACPI: EC: Look up EC in DSDT
[    0.200526] ACPI: Executed 1 blocks of module-level executable AML code
[    0.206805] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.208216] ACPI: SSDT 3f494c98 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.209628] ACPI: Dynamic OEM Table Load:
[    0.209641] ACPI: SSDT   (null) 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.210073] ACPI: SSDT 3f493e18 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.211435] ACPI: Dynamic OEM Table Load:
[    0.211448] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.276980] ACPI: SSDT 3f494f18 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.278376] ACPI: Dynamic OEM Table Load:
[    0.278388] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.278782] ACPI: SSDT 3f492f18 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.280186] ACPI: Dynamic OEM Table Load:
[    0.280199] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.660659] ACPI: Interpreter enabled
[    0.660688] ACPI: (supports S0 S3 S4 S5)
[    0.660775] ACPI: Using IOAPIC for interrupt routing
[    0.679217] ACPI: Power Resource [FN00] (on)
[    0.680612] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.681164] ACPI: No dock devices found.
[    0.681172] HEST: Table not found.
[    0.681187] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.682583] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.682610] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.682616] _OSC request data:1 8 1f 
[    0.682632] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.684960] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.684972] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.684982] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.684995] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.685033] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.685118] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.685141] pci 0000:00:02.0: reg 10: [mem 0x54180000-0x541fffff]
[    0.685155] pci 0000:00:02.0: reg 14: [io  0x30c0-0x30c7]
[    0.685170] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.685185] pci 0000:00:02.0: reg 1c: [mem 0x54000000-0x540fffff]
[    0.685258] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.685279] pci 0000:00:02.1: reg 10: [mem 0x54100000-0x5417ffff]
[    0.685443] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.685482] pci 0000:00:1b.0: reg 10: [mem 0x54200000-0x54203fff 64bit]
[    0.685631] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.685645] pci 0000:00:1b.0: PME# disabled
[    0.685698] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.685852] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.685864] pci 0000:00:1c.0: PME# disabled
[    0.685918] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.686071] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.686083] pci 0000:00:1c.1: PME# disabled
[    0.686144] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.686233] pci 0000:00:1d.0: reg 20: [io  0x3080-0x309f]
[    0.686306] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.686389] pci 0000:00:1d.1: reg 20: [io  0x3060-0x307f]
[    0.686461] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.686542] pci 0000:00:1d.2: reg 20: [io  0x3040-0x305f]
[    0.686615] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.686697] pci 0000:00:1d.3: reg 20: [io  0x3020-0x303f]
[    0.686786] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.687473] pci 0000:00:1d.7: reg 10: [mem 0x54204400-0x542047ff]
[    0.691384] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.691399] pci 0000:00:1d.7: PME# disabled
[    0.691444] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.691586] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.691794] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.691832] pci 0000:00:1f.2: reg 10: [io  0x30b8-0x30bf]
[    0.691853] pci 0000:00:1f.2: reg 14: [io  0x30cc-0x30cf]
[    0.691874] pci 0000:00:1f.2: reg 18: [io  0x30b0-0x30b7]
[    0.691896] pci 0000:00:1f.2: reg 1c: [io  0x30c8-0x30cb]
[    0.691918] pci 0000:00:1f.2: reg 20: [io  0x30a0-0x30af]
[    0.692068] pci 0000:00:1f.2: reg 24: [mem 0x54204000-0x542043ff]
[    0.692150] pci 0000:00:1f.2: PME# supported from D3hot
[    0.692163] pci 0000:00:1f.2: PME# disabled
[    0.692212] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.692304] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.692532] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.692604] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.692727] pci 0000:01:00.0: reg 18: [mem 0x50004000-0x50004fff 64bit pref]
[    0.692808] pci 0000:01:00.0: reg 20: [mem 0x50000000-0x50003fff 64bit pref]
[    0.693136] pci 0000:01:00.0: supports D1 D2
[    0.693145] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693169] pci 0000:01:00.0: PME# disabled
[    0.693373] pci 0000:01:00.1: [10ec:5288] type 0 class 0x00ff00
[    0.693448] pci 0000:01:00.1: reg 10: [mem 0x53000000-0x5300ffff]
[    0.693983] pci 0000:01:00.1: supports D1 D2
[    0.693991] pci 0000:01:00.1: PME# supported from D1 D2 D3hot D3cold
[    0.694012] pci 0000:01:00.1: PME# disabled
[    0.694255] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.694270] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.694282] pci 0000:00:1c.0:   bridge window [mem 0x53000000-0x53ffffff]
[    0.694300] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.694441] pci 0000:02:00.0: [168c:002b] type 0 class 0x000280
[    0.694499] pci 0000:02:00.0: reg 10: [mem 0x52000000-0x5200ffff 64bit]
[    0.694739] pci 0000:02:00.0: supports D1
[    0.694748] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.694763] pci 0000:02:00.0: PME# disabled
[    0.700121] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.700138] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.700152] pci 0000:00:1c.1:   bridge window [mem 0x52000000-0x52ffffff]
[    0.700169] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.700302] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.700329] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.700339] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.700349] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.700359] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.700397] pci_bus 0000:00: on NUMA node 0
[    0.700413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.700866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.701153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.701352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.701807] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.701831] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.701837] _OSC request data:1 1f 1f 
[    0.701853]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.702063] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.702087] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.702093] _OSC request data:1 0 1d 
[    0.702109]  pci0000:00: ACPI _OSC request failed (AE_TYPE), returned control mask: 0x1d
[    0.702116] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.711175] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.711387] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.711592] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.711816] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.712074] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.712302] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.712534] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.712755] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.713248] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.713280] vgaarb: loaded
[    0.713286] vgaarb: bridge control possible 0000:00:02.0
[    0.713806] i2c-core: driver [aat2870] using legacy suspend method
[    0.713813] i2c-core: driver [aat2870] using legacy resume method
[    0.714071] SCSI subsystem initialized
[    0.714270] libata version 3.00 loaded.
[    0.714478] usbcore: registered new interface driver usbfs
[    0.714528] usbcore: registered new interface driver hub
[    0.714652] usbcore: registered new device driver usb
[    0.715052] PCI: Using ACPI for IRQ routing
[    0.725754] PCI: pci_cache_line_size set to 64 bytes
[    0.725934] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.725944] reserve RAM buffer: 000000003f43f000 - 000000003fffffff 
[    0.725953] reserve RAM buffer: 000000003f600000 - 000000003fffffff 
[    0.726341] NetLabel: Initializing
[    0.726348] NetLabel:  domain hash size = 128
[    0.726354] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.726387] NetLabel:  unlabeled traffic allowed by default
[    0.726607] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.726622] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.726638] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.732664] Switching to clocksource hpet
[    0.755294] AppArmor: AppArmor Filesystem Enabled
[    0.755381] pnp: PnP ACPI init
[    0.755442] ACPI: bus type pnp registered
[    0.757632] pnp 00:00: [bus 00-ff]
[    0.757644] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.757653] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.757661] pnp 00:00: [io  0x0d00-0xffff window]
[    0.757670] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.757679] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.757688] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.757697] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.757705] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.757714] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.757723] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.757732] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.757740] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.757749] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.757758] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.757767] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.757776] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.757785] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.757794] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.757992] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.758447] pnp 00:01: [io  0x002e-0x002f]
[    0.758456] pnp 00:01: [io  0x004e-0x004f]
[    0.758464] pnp 00:01: [io  0x0061]
[    0.758476] pnp 00:01: [io  0x0070]
[    0.758483] pnp 00:01: [io  0x0080]
[    0.758490] pnp 00:01: [io  0x0092]
[    0.758497] pnp 00:01: [io  0x00b2-0x00b3]
[    0.758505] pnp 00:01: [io  0x0063]
[    0.758512] pnp 00:01: [io  0x0065]
[    0.758519] pnp 00:01: [io  0x0067]
[    0.758526] pnp 00:01: [io  0x0600-0x060f]
[    0.758533] pnp 00:01: [io  0x0610]
[    0.758541] pnp 00:01: [io  0x0800-0x080f]
[    0.758548] pnp 00:01: [io  0x0810-0x0817]
[    0.758556] pnp 00:01: [io  0x0400-0x047f]
[    0.758563] pnp 00:01: [io  0x0500-0x053f]
[    0.758572] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.758580] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.758588] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.758596] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.758605] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.758613] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.758621] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.758831] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.758842] system 00:01: [io  0x0610] has been reserved
[    0.758852] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.758862] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.758872] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.758881] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.758893] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.758904] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.758914] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.758925] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.758935] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.758946] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.758957] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.758969] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.759007] pnp 00:02: [io  0x0000-0x001f]
[    0.759015] pnp 00:02: [io  0x0081-0x0091]
[    0.759023] pnp 00:02: [io  0x0093-0x009f]
[    0.759031] pnp 00:02: [io  0x00c0-0x00df]
[    0.759039] pnp 00:02: [dma 4]
[    0.759143] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.759227] pnp 00:03: [io  0x0070-0x0077]
[    0.759337] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.759559] pnp 00:04: [irq 0 disabled]
[    0.759584] pnp 00:04: [irq 8]
[    0.759592] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.759700] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.759742] pnp 00:05: [io  0x00f0]
[    0.759758] pnp 00:05: [irq 13]
[    0.759867] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.759907] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.760053] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.760127] pnp 00:07: [io  0x0060]
[    0.760135] pnp 00:07: [io  0x0064]
[    0.760151] pnp 00:07: [irq 1]
[    0.760264] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.760329] pnp 00:08: [irq 12]
[    0.760453] pnp 00:08: Plug and Play ACPI device, IDs SYN1e33 SYN1e00 SYN0002 PNP0f13 (active)
[    0.760714] pnp: PnP ACPI: found 9 devices
[    0.760721] ACPI: ACPI bus type pnp unregistered
[    0.760730] PnPBIOS: Disabled by ACPI PNP
[    0.802807] PCI: max bus depth: 1 pci_try_num: 2
[    0.802868] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.802880] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.802895] pci 0000:00:1c.0:   bridge window [mem 0x53000000-0x53ffffff]
[    0.802910] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.802928] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.802940] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.802956] pci 0000:00:1c.1:   bridge window [mem 0x52000000-0x52ffffff]
[    0.802971] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.802988] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.803054] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.803069] pci 0000:00:1c.0: setting latency timer to 64
[    0.803101] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.803113] pci 0000:00:1c.1: setting latency timer to 64
[    0.803131] pci 0000:00:1e.0: setting latency timer to 64
[    0.803144] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.803153] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.803162] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.803171] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.803181] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.803190] pci_bus 0000:01: resource 1 [mem 0x53000000-0x53ffffff]
[    0.803200] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.803209] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.803218] pci_bus 0000:02: resource 1 [mem 0x52000000-0x52ffffff]
[    0.803228] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.803238] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.803247] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.803256] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.803265] pci_bus 0000:03: resource 7 [mem 0x40000000-0xfebfffff]
[    0.803381] NET: Registered protocol family 2
[    0.803595] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.804511] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.805602] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.806133] TCP: Hash tables configured (established 131072 bind 65536)
[    0.806147] TCP reno registered
[    0.806161] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.806184] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.806448] NET: Registered protocol family 1
[    0.806494] pci 0000:00:02.0: Boot video device
[    0.806544] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.806573] pci 0000:00:1d.0: PCI INT A disabled
[    0.806616] pci 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.806645] pci 0000:00:1d.1: PCI INT C disabled
[    0.806666] pci 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.806694] pci 0000:00:1d.2: PCI INT B disabled
[    0.806733] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.806762] pci 0000:00:1d.3: PCI INT D disabled
[    0.806785] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.820110] pci 0000:00:1d.7: PCI INT A disabled
[    0.820178] PCI: CLS 64 bytes, default 64
[    0.820191] Simple Boot Flag at 0x44 set to 0x1
[    0.821273] audit: initializing netlink socket (disabled)
[    0.821300] type=2000 audit(1371533829.816:1): initialized
[    0.858270] Freeing initrd memory: 13864k freed
[    0.879495] highmem bounce pool size: 64 pages
[    0.879508] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.884373] VFS: Disk quotas dquot_6.5.2
[    0.884522] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.885973] fuse init (API version 7.17)
[    0.886227] msgmni has been set to 1736
[    0.887113] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.887186] io scheduler noop registered
[    0.887193] io scheduler deadline registered
[    0.887213] io scheduler cfq registered (default)
[    0.887475] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.887560] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.887695] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.887769] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.887968] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.888072] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.888235] intel_idle: MWAIT substates: 0x20220
[    0.888252] intel_idle: v0.4 model 0x1C
[    0.888256] intel_idle: lapic_timer_reliable_states 0x2
[    0.888262] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.889414] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.890777] ACPI: AC Adapter [AC] (on-line)
[    0.891014] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.891027] ACPI: Power Button [PWRB]
[    0.891149] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.892797] ACPI: Lid Switch [LID0]
[    0.892966] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.892977] ACPI: Power Button [PWRF]
[    0.904328] ACPI Warning: For \_TZ_.THRM._AL0: Return Package has no elements (empty) (20110623/nspredef-463)
[    0.904346] ACPI: [Package] has zero elements (f5d225c0)
[    0.904351] ACPI: Invalid active0 threshold
[    0.908518] thermal LNXTHERM:00: registered as thermal_zone0
[    0.908525] ACPI: Thermal Zone [THRM] (29 C)
[    0.908579] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.908606] ACPI: Battery Slot [BAT0] (battery present)
[    0.908711] ERST: Table is not found!
[    0.908715] GHES: HEST is not enabled!
[    0.908853] isapnp: Scanning for PnP cards...
[    0.908996] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.951390] ACPI: Battery Slot [BAT0] (battery present)
[    1.263323] isapnp: No Plug & Play device found
[    1.289183] Linux agpgart interface v0.103
[    1.289360] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.289589] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.289870] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.290133] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.294377] brd: module loaded
[    1.296627] loop: module loaded
[    1.297000] ahci 0000:00:1f.2: version 3.0
[    1.297027] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.297125] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.297194] ahci: SSS flag set, parallel bus scan disabled
[    1.297242] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.297251] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.297262] ahci 0000:00:1f.2: setting latency timer to 64
[    1.298640] scsi0 : ahci
[    1.298891] scsi1 : ahci
[    1.299104] scsi2 : ahci
[    1.299310] scsi3 : ahci
[    1.299784] ata1: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204100 irq 42
[    1.299793] ata2: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204180 irq 42
[    1.299799] ata3: DUMMY
[    1.299803] ata4: DUMMY
[    1.301149] Fixed MDIO Bus: probed
[    1.301217] tun: Universal TUN/TAP device driver, 1.6
[    1.301222] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.301380] PPP generic driver version 2.4.2
[    1.301663] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.301709] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.301754] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.301763] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.301884] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.301927] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.301946] ehci_hcd 0000:00:1d.7: debug port 1
[    1.305838] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.305878] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x54204400
[    1.320037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.320437] hub 1-0:1.0: USB hub found
[    1.320450] hub 1-0:1.0: 8 ports detected
[    1.320636] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.320675] uhci_hcd: USB Universal Host Controller Interface driver
[    1.320724] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.320743] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.320751] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.320887] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.320930] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00003080
[    1.321275] hub 2-0:1.0: USB hub found
[    1.321287] hub 2-0:1.0: 2 ports detected
[    1.321440] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.321458] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.321465] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.321592] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.321653] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[    1.322000] hub 3-0:1.0: USB hub found
[    1.322012] hub 3-0:1.0: 2 ports detected
[    1.322154] uhci_hcd 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.322171] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.322179] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.322321] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.322380] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003040
[    1.322718] hub 4-0:1.0: USB hub found
[    1.322730] hub 4-0:1.0: 2 ports detected
[    1.322873] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.322890] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.322897] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.323026] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.323083] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00003020
[    1.323428] hub 5-0:1.0: USB hub found
[    1.323440] hub 5-0:1.0: 2 ports detected
[    1.323725] usbcore: registered new interface driver libusual
[    1.323831] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.331137] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.331157] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.331540] mousedev: PS/2 mouse device common for all mice
[    1.332066] rtc_cmos 00:03: RTC can wake from S4
[    1.332282] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.332325] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.332465] device-mapper: uevent: version 1.0.3
[    1.332682] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.332782] EISA: Probing bus 0 at eisa.0
[    1.332789] EISA: Cannot allocate resource for mainboard
[    1.332796] Cannot allocate resource for EISA slot 1
[    1.332802] Cannot allocate resource for EISA slot 2
[    1.332808] Cannot allocate resource for EISA slot 3
[    1.332813] Cannot allocate resource for EISA slot 4
[    1.332819] Cannot allocate resource for EISA slot 5
[    1.332824] Cannot allocate resource for EISA slot 6
[    1.332830] Cannot allocate resource for EISA slot 7
[    1.332835] Cannot allocate resource for EISA slot 8
[    1.332840] EISA: Detected 0 cards.
[    1.332858] cpufreq-nforce2: No nForce2 chipset.
[    1.333046] cpuidle: using governor ladder
[    1.333336] cpuidle: using governor menu
[    1.333342] EFI Variables Facility v0.08 2004-May-17
[    1.333911] TCP cubic registered
[    1.334207] NET: Registered protocol family 10
[    1.335501] NET: Registered protocol family 17
[    1.335514] Registering the dns_resolver key type
[    1.335557] Using IPI No-Shortcut mode
[    1.335952] PM: Hibernation image not present or could not be loaded.
[    1.335978] registered taskstats version 1
[    1.352601]   Magic number: 1:461:618
[    1.352751] rtc_cmos 00:03: setting system clock to 2013-06-18 05:37:11 UTC (1371533831)
[    1.353589] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.353595] EDD information not available.
[    1.458157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.632146] usb 1-8: new high-speed USB device number 2 using ehci_hcd
[    1.788098] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.789176] ata1.00: unexpected _GTF length (4)
[    1.821079] ata1.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
[    1.821093] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.822530] ata1.00: unexpected _GTF length (4)
[    1.822810] ata1.00: configured for UDMA/133
[    1.823126] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.823485] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.823659] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.823892] sd 0:0:0:0: [sda] Write Protect is off
[    1.823902] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.824048] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.867717]  sda: sda1 sda2 < sda5 >
[    1.868847] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.140143] ata2: SATA link down (SStatus 0 SControl 300)
[    2.140462] Freeing unused kernel memory: 744k freed
[    2.141014] Write protecting the kernel text: 5832k
[    2.141061] Write protecting the kernel read-only data: 2384k
[    2.141067] NX-protecting the kernel data: 4408k
[    2.183163] udevd[93]: starting version 175
[    2.427717] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.427791] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.427861] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
[    2.427892] r8169 0000:01:00.0: setting latency timer to 64
[    2.433088] r8169 0000:01:00.0: irq 43 for MSI/MSI-X
[    2.434817] r8169 0000:01:00.0: eth0: RTL8101e at 0xf8436000, 00:21:cc:48:7c:d5, XID 04000000 IRQ 43
[    2.656660] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.344717] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.386078] udevd[314]: starting version 175
[   15.452955] Adding 1035260k swap on /dev/sda5.  Priority:-1 extents:1 across:1035260k 
[   15.475695] lp: driver loaded but no devices found
[   15.676142] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.738224] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   15.804511] type=1400 audit(1371533845.949:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=408 comm="apparmor_parser"
[   15.805988] type=1400 audit(1371533845.949:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=408 comm="apparmor_parser"
[   15.806814] type=1400 audit(1371533845.949:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=408 comm="apparmor_parser"
[   15.811590] cfg80211: Calling CRDA to update world regulatory domain
[   15.837634] Initializing Realtek PCIE storage driver...
[   15.837727] rts_pstor 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.845239] Resource length: 0x10000
[   15.845311] Original address: 0x53000000, remapped address: 0xf8660000
[   15.845326] pci->irq = 17
[   15.845334] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 17
[   15.845379] rts_pstor 0000:01:00.1: setting latency timer to 64
[   15.888630] [drm] Initialized drm 1.1.0 20060810
[   15.972508] wmi: Mapper loaded
[   15.975979] i915 0000:00:02.0: power state changed by ACPI to D0
[   15.976046] i915 0000:00:02.0: power state changed by ACPI to D0
[   15.976064] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.976076] i915 0000:00:02.0: setting latency timer to 64
[   16.071320] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[   16.076095] rts_pstor: waiting for device to settle before scanning
[   16.130851] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   16.130869] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.130876] [drm] Driver supports precise vblank timestamp query.
[   16.148651] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.148679] ath9k 0000:02:00.0: setting latency timer to 64
[   16.220367] ath: EEPROM regdomain: 0x60
[   16.220376] ath: EEPROM indicates we should expect a direct regpair map
[   16.220388] ath: Country alpha2 being used: 00
[   16.220393] ath: Regpair used: 0x60
[   16.220403] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.220415] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220423] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.220434] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220443] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.220454] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220462] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.220472] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220480] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.220490] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220499] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.220510] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220519] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.220530] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220538] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.220549] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220557] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.220568] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220576] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.220587] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220596] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.220606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220615] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.220625] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220633] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.220643] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.220652] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.220662] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.224378] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   16.264189] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.325655] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.329063] Registered led device: ath9k-phy0
[   16.329092] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf86a0000, irq=17
[   16.375143] Linux video capture interface: v2.00
[   16.377349] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b1eb)
[   16.397988] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input4
[   16.398268] usbcore: registered new interface driver uvcvideo
[   16.398277] USB Video Class driver (1.1.1)
[   16.637739] [drm] initialized overlay support
[   16.669108] fbcon: inteldrmfb (fb0) is primary device
[   16.669271] Console: switching to colour frame buffer device 128x37
[   16.669348] fb0: inteldrmfb frame buffer device
[   16.669355] drm: registered panic notifier
[   16.704566] acpi device:20: registered as cooling_device2
[   16.705237] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   16.705536] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   16.705731] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.705829] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.705962] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.706025] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.789401] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.791004] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.080626] rts_pstor: device scan complete
[   17.082449] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.082656] Bad LUN (0:1)
[   17.082932] Bad target number (1:0)
[   17.083178] Bad target number (2:0)
[   17.083423] Bad target number (3:0)
[   17.083665] Bad target number (4:0)
[   17.083931] Bad target number (5:0)
[   17.084264] Bad target number (6:0)
[   17.084492] Bad target number (7:0)
[   17.087562] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   17.088112] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   17.158118] input: HP WMI hotkeys as /devices/virtual/input/input8
[   17.164895] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.164907] cfg80211: World regulatory domain updated:
[   17.164914] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.164925] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.164935] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.164945] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.164955] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.164965] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.263471] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[   17.313294] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   17.932712] init: failsafe main process (704) killed by TERM signal
[   18.244903] Bluetooth: Core ver 2.16
[   18.248071] NET: Registered protocol family 31
[   18.248081] Bluetooth: HCI device and connection manager initialized
[   18.248091] Bluetooth: HCI socket layer initialized
[   18.248098] Bluetooth: L2CAP socket layer initialized
[   18.248125] Bluetooth: SCO socket layer initialized
[   18.296187] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.296198] Bluetooth: BNEP filters: protocol multicast
[   18.298219] ppdev: user-space parallel port driver
[   18.346721] Bluetooth: RFCOMM TTY layer initialized
[   18.346740] Bluetooth: RFCOMM socket layer initialized
[   18.346748] Bluetooth: RFCOMM ver 1.11
[   18.479613] type=1400 audit(1371533848.621:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=815 comm="apparmor_parser"
[   18.498827] type=1400 audit(1371533848.641:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=814 comm="apparmor_parser"
[   18.505036] type=1400 audit(1371533848.649:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=815 comm="apparmor_parser"
[   18.505888] type=1400 audit(1371533848.649:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=815 comm="apparmor_parser"
[   18.535299] type=1400 audit(1371533848.677:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=818 comm="apparmor_parser"
[   18.546031] type=1400 audit(1371533848.689:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=818 comm="apparmor_parser"
[   18.597141] type=1400 audit(1371533848.741:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=817 comm="apparmor_parser"
[   20.063924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.114107] init: plymouth-stop pre-start process (1205) terminated with status 1
[   26.078655] r8169 0000:01:00.0: eth0: link down
[   26.079302] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  108.060736] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  108.646454] r8169 0000:01:00.0: eth0: link down
[  108.647178] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  109.652685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.431790] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[  115.433787] wlan0: authenticated
[  115.482567] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[  115.487236] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[  115.487248] wlan0: associated
[  115.496252] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  115.497411] cfg80211: Calling CRDA for country: CA
[  115.513953] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  115.513969] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.513979] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  115.513989] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.513998] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  115.514009] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514018] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  115.514029] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514039] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  115.514049] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514059] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  115.514070] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514080] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  115.514091] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514101] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  115.514112] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514122] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  115.514133] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514143] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  115.514154] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514163] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  115.514174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514183] cfg80211: Disabling freq 2467 MHz
[  115.514189] cfg80211: Disabling freq 2472 MHz
[  115.514195] cfg80211: Disabling freq 2484 MHz
[  115.514209] cfg80211: Regulatory domain changed to country: CA
[  115.514215] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  115.514225] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  115.514235] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  115.514244] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  115.514254] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  115.514264] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  126.248051] wlan0: no IPv6 routers present
[ 1007.215800] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 1007.262375] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1007.262397] cfg80211: Restoring regulatory settings
[ 1007.262415] cfg80211: Calling CRDA to update world regulatory domain
[ 1007.631475] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1007.631491] cfg80211: World regulatory domain updated:
[ 1007.631500] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1007.631513] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1007.631525] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1007.631536] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1007.631547] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1007.631559] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1008.064766] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1008.069375] wlan0: authenticated
[ 1008.069446] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1008.075820] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 1008.075835] wlan0: associated
[ 1008.084772] cfg80211: Calling CRDA for country: CA
[ 1008.095005] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095017] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095024] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095031] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095037] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095045] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095051] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095058] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095064] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095072] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095078] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095085] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095091] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095099] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095105] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095112] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095118] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095126] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095132] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095139] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095145] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1008.095153] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095158] cfg80211: Disabling freq 2467 MHz
[ 1008.095162] cfg80211: Disabling freq 2472 MHz
[ 1008.095167] cfg80211: Disabling freq 2484 MHz
[ 1008.095178] cfg80211: Regulatory domain changed to country: CA
[ 1008.095183] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1008.095190] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1008.095197] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1008.095204] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1008.095210] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1008.095217] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1325.241527] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 1325.260363] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1325.260376] cfg80211: Restoring regulatory settings
[ 1325.260389] cfg80211: Calling CRDA to update world regulatory domain
[ 1325.270238] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1325.270248] cfg80211: World regulatory domain updated:
[ 1325.270253] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1325.270261] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1325.270268] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1325.270275] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1325.270282] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1325.270289] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1326.045144] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1326.047423] wlan0: authenticated
[ 1326.067920] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1326.072208] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 1326.072222] wlan0: associated
[ 1326.080612] cfg80211: Calling CRDA for country: CA
[ 1326.096193] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096210] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096222] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096234] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096244] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096257] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096267] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096279] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096289] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096302] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096312] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096324] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096334] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096346] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096357] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096379] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096391] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096402] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096414] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096424] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1326.096436] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096445] cfg80211: Disabling freq 2467 MHz
[ 1326.096452] cfg80211: Disabling freq 2472 MHz
[ 1326.096459] cfg80211: Disabling freq 2484 MHz
[ 1326.096478] cfg80211: Regulatory domain changed to country: CA
[ 1326.096486] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1326.096497] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1326.096508] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1326.096520] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1326.096531] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1326.096542] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2006.269383] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 2006.291721] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2006.291736] cfg80211: Restoring regulatory settings
[ 2006.291747] cfg80211: Calling CRDA to update world regulatory domain
[ 2006.410354] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2006.410364] cfg80211: World regulatory domain updated:
[ 2006.410369] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2006.410377] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2006.410384] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2006.410391] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2006.410398] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2006.410404] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.080063] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 2007.082130] wlan0: authenticated
[ 2007.102658] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 2007.107037] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 2007.107049] wlan0: associated
[ 2007.114986] cfg80211: Calling CRDA for country: CA
[ 2007.124641] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124652] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124659] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124673] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124680] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124687] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124694] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124700] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124708] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124714] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124721] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124728] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124741] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124749] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124755] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124762] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124768] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124776] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124782] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2007.124790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124795] cfg80211: Disabling freq 2467 MHz
[ 2007.124799] cfg80211: Disabling freq 2472 MHz
[ 2007.124804] cfg80211: Disabling freq 2484 MHz
[ 2007.124815] cfg80211: Regulatory domain changed to country: CA
[ 2007.124820] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2007.124827] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2007.124834] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 2007.124841] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.124848] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.124854] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2007.688675] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 2007.707245] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2007.707261] cfg80211: Restoring regulatory settings
[ 2007.707275] cfg80211: Calling CRDA to update world regulatory domain
[ 2007.721004] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2007.721017] cfg80211: World regulatory domain updated:
[ 2007.721024] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2007.721034] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.721043] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2007.721053] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2007.721062] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.721071] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2007.827817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2008.494978] r8169 0000:01:00.0: eth0: link down
[ 2008.500638] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3507.179520] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3507.286010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3507.801104] r8169 0000:01:00.0: eth0: link down
[ 3507.802603] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3508.302904] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3511.307818] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 3511.309968] wlan0: authenticated
[ 3511.310059] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 3511.315987] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 3511.315997] wlan0: associated
[ 3511.323830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3511.324520] cfg80211: Calling CRDA for country: CA
[ 3511.547460] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547474] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547483] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547492] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547500] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547509] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547517] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547527] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547534] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547544] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547551] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547561] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547568] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547578] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547585] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547595] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547602] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547612] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547619] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547629] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547636] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3511.547646] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547652] cfg80211: Disabling freq 2467 MHz
[ 3511.547658] cfg80211: Disabling freq 2472 MHz
[ 3511.547663] cfg80211: Disabling freq 2484 MHz
[ 3511.547677] cfg80211: Regulatory domain changed to country: CA
[ 3511.547683] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3511.547692] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3511.547701] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 3511.547709] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3511.547718] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3511.547726] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 3522.240056] wlan0: no IPv6 routers present
[ 4999.322313] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 4999.366453] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4999.366475] cfg80211: Restoring regulatory settings
[ 4999.366494] cfg80211: Calling CRDA to update world regulatory domain
[ 4999.377279] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 4999.377289] cfg80211: World regulatory domain updated:
[ 4999.377294] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4999.377302] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4999.377309] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4999.377315] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4999.377322] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4999.377329] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5000.155402] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5000.157429] wlan0: authenticated
[ 5000.157495] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5000.162241] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 5000.162254] wlan0: associated
[ 5000.170910] cfg80211: Calling CRDA for country: CA
[ 5000.186332] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186350] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186362] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186374] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186385] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186407] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186420] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186430] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186442] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186465] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186475] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186488] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186498] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186521] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186533] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186544] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186556] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186566] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 5000.186579] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186588] cfg80211: Disabling freq 2467 MHz
[ 5000.186595] cfg80211: Disabling freq 2472 MHz
[ 5000.186602] cfg80211: Disabling freq 2484 MHz
[ 5000.186621] cfg80211: Regulatory domain changed to country: CA
[ 5000.186629] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5000.186640] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5000.186652] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 5000.186663] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5000.186674] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5000.186686] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 5108.480772] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 5108.515578] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5108.515595] cfg80211: Restoring regulatory settings
[ 5108.515609] cfg80211: Calling CRDA to update world regulatory domain
[ 5108.535597] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 5108.535616] cfg80211: World regulatory domain updated:
[ 5108.535626] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5108.535642] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5108.535657] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5108.535672] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5108.535686] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5108.535701] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5108.610010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5108.985088] r8169 0000:01:00.0: eth0: link down
[ 5108.985900] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5112.591964] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5112.702201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5113.093344] r8169 0000:01:00.0: eth0: link down
[ 5113.094140] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5113.512437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5115.974523] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5115.976547] wlan0: authenticated
[ 5115.997074] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5116.012536] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 5116.012545] wlan0: associated
[ 5116.020687] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5116.020881] cfg80211: Calling CRDA for country: CA
[ 5116.033376] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033394] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033405] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033418] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033428] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033440] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033451] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033463] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033473] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033485] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033496] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033508] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033518] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033530] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033541] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033553] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033563] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033575] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033586] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033608] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 5116.033620] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033629] cfg80211: Disabling freq 2467 MHz
[ 5116.033636] cfg80211: Disabling freq 2472 MHz
[ 5116.033643] cfg80211: Disabling freq 2484 MHz
[ 5116.033662] cfg80211: Regulatory domain changed to country: CA
[ 5116.033670] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5116.033681] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 5116.033693] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 5116.033704] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5116.033715] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5116.033726] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 5127.016078] wlan0: no IPv6 routers present
[ 6697.692100] usb 1-2: new high-speed USB device number 3 using ehci_hcd
[ 6697.992957] Initializing USB Mass Storage driver...
[ 6697.993389] scsi5 : usb-storage 1-2:1.5
[ 6697.993593] usbcore: registered new interface driver usb-storage
[ 6697.993599] USB Mass Storage support registered.
[ 6698.348223] cdc_acm 1-2:1.0: This device cannot do calls on its own. It is not a modem.
[ 6698.348655] cdc_acm 1-2:1.0: ttyACM0: USB ACM device
[ 6698.350707] usbcore: registered new interface driver cdc_acm
[ 6698.350721] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[ 6698.801879] cdc_ether 1-2:1.3: usb0: register 'cdc_ether' at usb-0000:00:1d.7-2, CDC Ethernet Device, 8e:82:d7:d7:a6:9f
[ 6698.801983] usbcore: registered new interface driver cdc_ether
[ 6698.993373] scsi 5:0:0:0: Direct-Access     LGE      E400             0100 PQ: 0 ANSI: 2
[ 6698.994106] scsi 5:0:0:1: Direct-Access     LGE      E400 SD Card     0100 PQ: 0 ANSI: 2
[ 6698.998218] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 6699.003741] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 6699.009605] sd 5:0:0:1: Attached scsi generic sg3 type 0
[ 6699.014835] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[ 6756.252996] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 6756.299261] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 6756.299288] cfg80211: Restoring regulatory settings
[ 6756.299308] cfg80211: Calling CRDA to update world regulatory domain
[ 6756.344807] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 6756.344820] cfg80211: World regulatory domain updated:
[ 6756.344827] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6756.344838] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6756.344847] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6756.344856] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6756.344866] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6756.344875] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6756.409462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6756.864742] r8169 0000:01:00.0: eth0: link down
[ 6756.865570] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6757.358024] r8169 0000:01:00.0: eth0: link down
[ 6757.358697] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6902.753629] usb 1-2: USB disconnect, device number 3
[ 6902.754750] cdc_ether 1-2:1.3: usb0: unregister 'cdc_ether' usb-0000:00:1d.7-2, CDC Ethernet Device
[ 6909.113073] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6909.226405] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6909.562410] r8169 0000:01:00.0: eth0: link down
[ 6909.563242] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6923.236120] usb 1-2: new high-speed USB device number 4 using ehci_hcd
[ 6923.370575] cdc_acm 1-2:1.0: This device cannot do calls on its own. It is not a modem.
[ 6923.370962] cdc_acm 1-2:1.0: ttyACM0: USB ACM device
[ 6923.379573] cdc_ether 1-2:1.3: usb0: register 'cdc_ether' at usb-0000:00:1d.7-2, CDC Ethernet Device, 8e:82:d7:d7:a6:9f
[ 6923.382496] scsi6 : usb-storage 1-2:1.5
[ 6924.381200] scsi 6:0:0:0: Direct-Access     LGE      E400             0100 PQ: 0 ANSI: 2
[ 6924.383377] scsi 6:0:0:1: Direct-Access     LGE      E400 SD Card     0100 PQ: 0 ANSI: 2
[ 6924.395681] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 6924.399439] sd 6:0:0:1: Attached scsi generic sg3 type 0
[ 6924.404413] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 6924.408773] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[ 6935.992924] usb 1-2: USB disconnect, device number 4
[ 6935.994051] cdc_ether 1-2:1.3: usb0: unregister 'cdc_ether' usb-0000:00:1d.7-2, CDC Ethernet Device
[ 6936.272179] usb 1-2: new high-speed USB device number 5 using ehci_hcd
[ 6936.410374] scsi7 : usb-storage 1-2:1.0
[ 6937.409083] scsi 7:0:0:0: Direct-Access     LGE      E400             0100 PQ: 0 ANSI: 2
[ 6937.409811] scsi 7:0:0:1: Direct-Access     LGE      E400 SD Card     0100 PQ: 0 ANSI: 2
[ 6937.417916] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 6937.421181] sd 7:0:0:1: Attached scsi generic sg3 type 0
[ 6937.424288] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 6937.428104] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[ 6940.138270] sd 7:0:0:1: [sdd] 3862528 512-byte logical blocks: (1.97 GB/1.84 GiB)
[ 6940.139411] sd 7:0:0:1: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6940.147611]  sdd:
[ 6950.379550] sd 7:0:0:0: [sdc] 2097152 512-byte logical blocks: (1.07 GB/1.00 GiB)
[ 6950.381183] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6950.386454]  sdc:
[ 7060.307667] netlink: 12 bytes leftover after parsing attributes.
[ 7060.307689] netlink: 12 bytes leftover after parsing attributes.
[ 7060.307884] netlink: 12 bytes leftover after parsing attributes.
[ 7584.796749] r8169 0000:01:00.0: eth0: link down
[ 7584.797547] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7596.405518] r8169 0000:01:00.0: eth0: link down
[ 7596.406346] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7613.832645] r8169 0000:01:00.0: eth0: link down
[ 7613.833474] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7625.436636] r8169 0000:01:00.0: eth0: link down
[ 7625.437458] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7635.553391] r8169 0000:01:00.0: eth0: link down
[ 7635.553887] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7644.618993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7655.910120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7656.260789] r8169 0000:01:00.0: eth0: link down
[ 7656.261591] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7656.844792] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7659.259910] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 7659.261929] wlan0: authenticated
[ 7659.261997] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 7659.266213] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[ 7659.266221] wlan0: associated
[ 7659.273874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7659.274961] cfg80211: Calling CRDA for country: CA
[ 7659.285306] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285318] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285325] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285339] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285346] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285352] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285366] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285373] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285380] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285387] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285393] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285401] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285407] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285414] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285421] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285428] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285434] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285442] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285448] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 7659.285455] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285461] cfg80211: Disabling freq 2467 MHz
[ 7659.285465] cfg80211: Disabling freq 2472 MHz
[ 7659.285469] cfg80211: Disabling freq 2484 MHz
[ 7659.285481] cfg80211: Regulatory domain changed to country: CA
[ 7659.285486] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7659.285493] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7659.285500] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 7659.285506] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7659.285513] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7659.285520] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 7669.824059] wlan0: no IPv6 routers present
bloed@bloed-HP-Mini-110-3000:~$ 


```

it says something about regulatory domain and country being CA... well i'm in the netherlands...
I do not know how to use grep or what it is, and when I type it as suggested the command returns nothing, so feel I have to post the entire bulk. Sorry.

```

$ sudo lshw -C network
                
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:48:7c:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:50004000-50004fff memory:50000000-50003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:3f:bc:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-41-generic-pae firmware=N/A ip=192.168.1.79 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:52000000-5200ffff


```

```

$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 7A:2B:C1:CC:4D:08
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Bagijnestraat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ea5ba2d170
                    Extra: Last beacon: 27224ms ago
                    IE: Unknown: 000D426167696A6E65737472616174
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A040600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286017A2BC1CC4D081021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05010033127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10

eth0      Interface doesn't support scanning.



```

```

$ lsb_release -d
Description:	Ubuntu 12.04 LTS


```

```

$ uname -mr
3.2.0-41-generic-pae i686


```

```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                             [ OK ] 
bloed@bloed-HP-Mini-110-3000:~$ 


```

Thank you so much

---

### Post by praseodym on 2013-06-18
Try to deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by rikki1913 on 2013-06-18
Also, it might be important that I have been running wicd for awhile after removing NetworkManager, but on my quest for a solution I found out that there were still networkmanager-gnome-related processes running. I "purged" the entire network-manager and network-manager-chrome package yesterday, which didn't help.

---

### Post by rikki1913 on 2013-06-18
Thank you for your quick response.

I entered those commands, which caused WICD to disconnect, and reconnected with WICD.

The result on the prompt:

```

$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for bloed: 
options ath9k nohwcrypt=1
bloed@bloed-HP-Mini-110-3000:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/net/wireless/cfg80211.ko
bloed@bloed-HP-Mini-110-3000:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.2.0-41-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1


```

I am connected to the wi-fi again, but Chrome still says "DNS lookup failed", and Firefox still says "Server not found".

---

### Post by praseodym on 2013-06-18
Add the DNSs 8.8.8.8 and 8.8.4.4 in Wicd, choose wlan0 as interface and wext as driver

---

### Post by rikki1913 on 2013-06-18
thank you. i did as you said, but no luck. This I have also tried before. The fields DNS Domain and Search Domain i left empty though, not sure what to do there. Turned wifi off and on and reconnected. Same errors in browser though. Ping [www.google.com](www.google.com) stil says unknown host, and pinging google's IP address takes forever and still 100% package loss...

---

### Post by praseodym on 2013-06-18
Which country do you live? Please show
```

iwlist chan
dmesg | egrep 'ath9k|wlan0'
ps aux | egrep '[N]etw|[W]icd|wpa'
```

---

### Post by rikki1913 on 2013-06-18
I live in the Netherlands.

```

$ iwlist chan
lo        no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.457 GHz (Channel 10)

eth0      no frequency information.

```

```

$ dmesg | egrep 'ath9k|wlan0'
[   16.148651] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.148679] ath9k 0000:02:00.0: setting latency timer to 64
[   16.325655] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.329063] Registered led device: ath9k-phy0
[   20.063924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  108.060736] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  109.652685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.431790] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[  115.433787] wlan0: authenticated
[  115.482567] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[  115.487236] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[  115.487248] wlan0: associated
[  115.496252] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.248051] wlan0: no IPv6 routers present
[ 1007.215800] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 1008.064766] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1008.069375] wlan0: authenticated
[ 1008.069446] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1008.075820] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 1008.075835] wlan0: associated
[ 1325.241527] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 1326.045144] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1326.047423] wlan0: authenticated
[ 1326.067920] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 1326.072208] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 1326.072222] wlan0: associated
[ 2006.269383] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 2007.080063] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 2007.082130] wlan0: authenticated
[ 2007.102658] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 2007.107037] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 2007.107049] wlan0: associated
[ 2007.688675] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 2007.827817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3507.179520] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3507.286010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3508.302904] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3511.307818] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 3511.309968] wlan0: authenticated
[ 3511.310059] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 3511.315987] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 3511.315997] wlan0: associated
[ 3511.323830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3522.240056] wlan0: no IPv6 routers present
[ 4999.322313] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 5000.155402] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5000.157429] wlan0: authenticated
[ 5000.157495] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5000.162241] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 5000.162254] wlan0: associated
[ 5108.480772] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 5108.610010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5112.591964] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5112.702201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5113.512437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5115.974523] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5115.976547] wlan0: authenticated
[ 5115.997074] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 5116.012536] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=1)
[ 5116.012545] wlan0: associated
[ 5116.020687] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5127.016078] wlan0: no IPv6 routers present
[ 6756.252996] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[ 6756.409462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6909.113073] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6909.226405] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7644.618993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7655.910120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7656.844792] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7659.259910] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 7659.261929] wlan0: authenticated
[ 7659.261997] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 7659.266213] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[ 7659.266221] wlan0: associated
[ 7659.273874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7669.824059] wlan0: no IPv6 routers present
[ 9111.472653] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[ 9112.300394] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9160.824226] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9160.944899] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9161.874845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9164.339920] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[ 9164.342078] wlan0: authenticated
[ 9164.342174] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[ 9164.350329] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[ 9164.350339] wlan0: associated
[ 9164.358486] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9174.832065] wlan0: no IPv6 routers present
[10631.504350] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[10632.383890] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[10632.386089] wlan0: authenticated
[10632.386155] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[10632.392561] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[10632.392569] wlan0: associated
[12417.562167] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[12418.419479] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[12418.421492] wlan0: authenticated
[12418.441856] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[12418.446146] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[12418.446161] wlan0: associated
[14270.574326] wlan0: deauthenticated from 7a:2b:c1:cc:4d:08 (Reason: 3)
[14271.399391] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[14271.401397] wlan0: authenticated
[14271.421692] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[14271.426332] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[14271.426342] wlan0: associated
[15628.831898] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[15628.952936] ath9k 0000:02:00.0: PCI INT A disabled
[15628.953014] ath9k: Driver unloaded
[15655.972766] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[15655.972801] ath9k 0000:02:00.0: setting latency timer to 64
[15656.027721] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[15656.033135] Registered led device: ath9k-phy0
[15820.892446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15821.010542] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15821.907100] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15825.306118] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[15825.308892] wlan0: authenticated
[15825.308957] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[15825.316184] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[15825.316204] wlan0: associated
[15825.324566] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15835.488057] wlan0: no IPv6 routers present
[23714.790968] wlan0: deauthenticating from 7a:2b:c1:cc:4d:08 by local choice (reason=3)
[23714.943517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23857.053011] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23876.557721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23877.605269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23880.212210] wlan0: authenticate with 7a:2b:c1:cc:4d:08 (try 1)
[23880.214277] wlan0: authenticated
[23880.214366] wlan0: associate with 7a:2b:c1:cc:4d:08 (try 1)
[23880.233115] wlan0: RX AssocResp from 7a:2b:c1:cc:4d:08 (capab=0x431 status=0 aid=2)
[23880.233130] wlan0: associated
[23880.241347] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23890.320056] wlan0: no IPv6 routers present

```

```

$ ps aux | egrep '[N]etw|[W]icd|wpa'
root      5880  0.0  0.1   5968  1064 ?        Ss   14:15   0:00 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/7a2bc1cc4d08 -Dwext
bloed     9697  0.0  0.0   4384   828 pts/1    S+   14:54   0:00 egrep --color=auto [N]etw|[W]icd|wpa


```

---

### Post by rikki1913 on 2013-06-18
Also tried it this way, which brought up some more processes:

```

$ ps aux | egrep 'netw|Netw|wicd|Wicd|wpa'
root       940  6.6  0.6  26164  6680 ?        R    07:37  30:00 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root       985  4.3  0.4  15536  4748 ?        S    07:37  19:50 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
bloed     1593  0.1  0.9  64196  9600 ?        Sl   07:37   0:54 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --tray
bloed     1894  0.6  1.8  97996 18644 ?        Sl   07:38   2:47 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --no-tray
root      5880  0.0  0.1   5968  1064 ?        Ss   14:15   0:00 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/7a2bc1cc4d08 -Dwext
bloed    11031  0.0  0.0   4388   816 pts/1    S+   15:08   0:00 egrep --color=auto netw|Netw|wicd|Wicd|wpa


```

---

### Post by praseodym on 2013-06-18
> [  115.497411] cfg80211: Calling CRDA for country: [COLOR="#FF0000"]CA[/COLOR]
Try:
```

sudo apt-get install iw
iw reg get
sudo iw reg set NL
iw reg get
iwlist chan
```
Also try a fixed channel instead of "auto"

---

### Post by rikki1913 on 2013-06-18
```

$ sudo apt-get install iw
[sudo] password for bloed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
iw is already the newest version.
iw set to manually installed.
The following package was automatically installed and is no longer required:
  libtrove-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.
bloed@bloed-HP-Mini-110-3000:~$ iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
bloed@bloed-HP-Mini-110-3000:~$ sudo iw reg set NL
bloed@bloed-HP-Mini-110-3000:~$ iw reg get
country NL:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
	(5250 - 5330 @ 40), (N/A, 20), NO-OUTDOOR, DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
bloed@bloed-HP-Mini-110-3000:~$ iwlist chan
lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.


```

You said to use a fixed channel. I didn't really know where or how to do that, but I did this, hoping it's what you meant:

```

$ sudo iwconfig wlan0 channel 10
[sudo] password for bloed: 
bloed@bloed-HP-Mini-110-3000:~$ 


```
Is it a fixed channel now??
I don't know if I did it right, but so far the problem is still there. I still cannot ping anything but 127.0.0.1.

---

### Post by praseodym on 2013-06-18
You need to enter the router interface, check the manual for it.

---

### Post by rikki1913 on 2013-06-18
I can't really change anything about the router, because I do not own it. Pretty sure the problem isn't the router though, because it worked fine before, and my cellphone can still use the same network. I checked that when I disabled mobile networking.

---

### Post by rikki1913 on 2013-06-19
maybe I should just give up and reinstall ubuntu

---

### Post by praseodym on 2013-06-19
Try Wicd instead, it can handle mixed mode better than the NM:
```

sudo apt-get install wicd
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose wlan0 as interface name and wext as driver in Wicd

---

### Post by rikki1913 on 2013-06-19
I already am using wicd...

---

### Post by rikki1913 on 2013-06-19
It works again. I don't know how long it will last. The problem has existed for about a week now, and today i am posting from my netbook. Only two things have happened that could have caused it: I turned it off wrong by holding the power switch till it shut down, and when I restarted just now, I switched to Unity 2D. And voilà, web pages. I dare anyone to explain this.

---

