---
title: "Trying Ubuntu from DVD - but can't get wireless working"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by CameronWyse on 2012-10-26
Hi all,
 
Linux Newbie here and yesterday i downloaded latest ubuntu to try (before installing) and while it looks great, i can't get wireless to work.
 
i can connect to a local BT Open (pay as you go) service so i'm guessing the wireless card etc works and the problem is the introduction of my wireless security. it never really connects and after trying to connect just doesn't. one of the distros gave a message about authentication failure.
 
i'm using WEP with the full hex string and for info, i've also tried latest versions of PCLINUXOS, KNOPPIX and OpenSuse and all experience the exact same issue. Also, i tried this on both an apple mac (my computer) and my son's windows laptop (forget the make).
 
that would normally make me suspect the router, but the wireless works ok (using it now) and have several different devices that can all happily connect from gaming machines, mobiles, kindles as well as laptops (they're not all mine BTW!) so that leads me to linux somewhere as it's the only thing that is having the problem.
 
I liked the look and feel of Ubuntu, hence posting on this forum.
 
Some details (from mac osx system profiler) are below and any help would be greatly appreciated
 
Thanks,
 
Cameron
 
P.S. my router is a NetGear Dual Band Wireless-N Modem Router DGND3300v2 and i have the same issue on either of the two wireless networks it offers.
 
**Hardware Overview:**
 
Model Name: MacBook
Model Identifier: MacBook2,1
Processor Name: Intel Core 2 Duo
Processor Speed: 2 GHz
Number Of Processors: 1
Total Number Of Cores: 2
L2 Cache: 4 MB
Memory: 1 GB
Bus Speed: 667 MHz
Boot ROM Version: MB21.00A5.B07
SMC Version (system): 1.13f3
 
 
 
**Network AirPort:**
 
Type: AirPort
Hardware: AirPort
BSD Device Name: en1
IPv4 Addresses: 192.168.0.7
IPv4:
Addresses: 192.168.0.7
Configuration Method: DHCP
Interface Name: en1
Network Signature: IPv4.Router=192.168.0.1;IPv4.RouterHardwareAddress=00:26:f2:4a:df:67
Router: 192.168.0.1
Subnet Masks: 255.255.255.0
IPv6:
Configuration Method: Automatic
DNS:
Server Addresses: 192.168.0.1
DHCP Server Responses:
Domain Name Servers: 192.168.0.1
Lease Duration (seconds): 0
DHCP Message Type: 0x05
Routers: 192.168.0.1
Server Identifier: 192.168.0.1
Subnet Mask: 255.255.255.0
Ethernet:
MAC Address: 00:19:e3:05:3e:c2
Media Options: 
Media Subtype: Auto Select
Proxies:
Proxy Configuration Method: Manual
Exclude Simple Hostnames: 0
FTP Passive Mode: Yes
Auto Discovery Enabled: No
Service Order: 3
 
 
Software Versions:
Menu Extra: 6.2.2 (622.2)
configd plug-in: 6.2.5 (625.6)
System Profiler: 6.0.1 (601.1)
Network Preference: 6.2.2 (622.2)
AirPort Utility: 5.6.1 (561.3)
IO80211 Family: 3.2 (320.1)
Interfaces:
en1:
Card Type: AirPort Extreme
Firmware Version: Atheros 5416: 2.1.14.6
Locale: ETSI
Country Code: 
Supported PHY Modes: 802.11 a/b/g/n
Supported Channels: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140
Status: Connected

---

### Post by CameronWyse on 2012-10-26
Hi all, just found the how to log a wireless issue post so here goes:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61)

ubuntu@ubuntu:~$ lsusb
Bus 001 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 002 Device 002: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:e3:35:18:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11744 (11.7 KB)  TX bytes:11744 (11.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:e3:05:3e:c2  
          inet6 addr: fe80::219:e3ff:fe05:3ec2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18504 (18.5 KB)


ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"DBNetworkPlus"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:26:F2:4A:DF:66   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               22402  0 
arc4                   12473  2 
ath9k                 116549  0 
mac80211              461161  1 ath9k
snd_hda_codec_idt      59761  1 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
ath9k_common           13783  1 ath9k
ath9k_hw              376155  2 ath9k,ath9k_common
coretemp               13168  0 
kvm_intel             126745  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
kvm                   357806  1 kvm_intel
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
lpc_ich                16925  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  17950  0 
isight_firmware        12593  0 
bnep                   17707  2 
appletouch             17366  0 
cfg80211              175375  3 ath9k,mac80211,ath
joydev                 17161  0 
soundcore              14599  1 snd
parport_pc             31968  0 
rfcomm                 37276  12 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
applesmc               18778  0 
bluetooth             183228  22 btusb,bnep,rfcomm
apple_bl               13425  0 
mac_hid                13037  0 
ppdev                  12817  0 
input_polldev          13648  1 applesmc
microcode              18209  0 
lp                     13299  0 
dm_multipath           22365  0 
parport                40753  3 parport_pc,ppdev,lp
scsi_dh                14178  1 dm_multipath
squashfs               35834  1 
overlayfs              27233  1 
nls_utf8               12493  1 
isofs                  39210  1 
nls_iso8859_1          12617  0 
dm_raid45              75357  0 
xor                    26090  1 dm_raid45
dm_mirror              21665  0 
dm_region_hash         15977  1 dm_mirror
dm_log                 18137  3 dm_raid45,dm_mirror,dm_region_hash
hid_generic            12445  0 
hid_apple              13045  0 
usbhid                 41702  0 
hid                    82142  3 hid_generic,hid_apple,usbhid
i915                  457161  3 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   52926  0 
video                  18847  1 i915

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:19:e3:35:18:b2
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:50200000-50203fff ioport:1000(size=256) memory:50500000-5051ffff
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:e3:05:3e:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:50100000-5010ffff

iwlist scan


ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 12.10

ubuntu@ubuntu:~$ uname -mr
3.5.0-17-generic i686

---

### Post by CameronWyse on 2012-10-26
dmesg results:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-17-generic (buildd@roseapple) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 (Ubuntu 3.5.0-17.28-generic 3.5.5)
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
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003e0f7fff] usable
[    0.000000] BIOS-e820: [mem 0x000000003e0f8000-0x000000003e2f8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003e2f9000-0x000000003eebdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000003eebe000-0x000000003eeeefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003eeef000-0x000000003eefffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000003ef00000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Apple Inc. MacBook2,1/Mac-F4208CA9, BIOS     MB21.88Z.00A5.B07.0706270922 06/27/07
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3e0f8 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask FC0000000 write-back
[    0.000000]   2 base 03F000000 mask FFF000000 uncachable
[    0.000000]   3 base 03EF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x3d0df000-0x3e0f7fff]
[    0.000000] Allocated new RAMDISK: [mem 0x36be5000-0x37bfdeff]
[    0.000000] Move RAMDISK from [mem 0x3d0df000-0x3e0f7eff] to [mem 0x36be5000-0x37bfdeff]
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 APPLE )
[    0.000000] ACPI: XSDT 3eefd1c0 00074 (v01 APPLE   Apple00 000000A5      01000013)
[    0.000000] ACPI: FACP 3eefb000 000F4 (v03 APPLE   Apple00 000000A5 Loki 0000005F)
[    0.000000] ACPI: DSDT 3eef0000 041E4 (v01 APPLE   MacBook 00020001 INTL 20050309)
[    0.000000] ACPI: FACS 3eec0000 00040
[    0.000000] ACPI: HPET 3eefa000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 3eef9000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: MCFG 3eef8000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 3eef7000 000A0 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 3eef6000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 3eef5000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 3eeef000 004DC (v01 APPLE     CpuPm 00003000 INTL 20050309)
[    0.000000] ACPI: SSDT 3eebd000 0064F (v01 SataRe  SataPri 00001000 INTL 20050309)
[    0.000000] ACPI: SSDT 3eebc000 0069C (v01 SataRe  SataSec 00001000 INTL 20050309)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 100MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3e0f7fff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3e0f7fff]
[    0.000000] On node 0 totalpages: 254087
[    0.000000] free_area_init_node: node 0, pgdat c18a0840, node_mem_map f641c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 202 pages used for memmap
[    0.000000]   HighMem zone: 25648 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0x40000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f63fa000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 252101
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2033472 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003e0f8)
[    0.000000] Memory: 978360k/1016800k available (5956k kernel code, 37988k reserved, 2928k data, 756k init, 103400k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18ae000 - 0xc196b000   ( 756 kB)
[    0.000000]       .data : 0xc15d1358 - 0xc18ad6c0   (2928 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15d1358   (5956 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using HPET reference calibration
[    0.000000] Detected 1994.986 MHz processor.
[    0.016003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.97 BogoMIPS (lpj=7979944)
[    0.016009] pid_max: default: 32768 minimum: 301
[    0.016041] Security Framework initialized
[    0.016060] AppArmor: AppArmor initialized
[    0.016062] Yama: becoming mindful.
[    0.020056] Mount-cache hash table entries: 512
[    0.020367] Initializing cgroup subsys cpuacct
[    0.020370] Initializing cgroup subsys memory
[    0.020381] Initializing cgroup subsys devices
[    0.020384] Initializing cgroup subsys freezer
[    0.020386] Initializing cgroup subsys blkio
[    0.020389] Initializing cgroup subsys perf_event
[    0.020424] Disabled fast string operations
[    0.020429] CPU: Physical Processor ID: 0
[    0.020431] CPU: Processor Core ID: 0
[    0.020435] mce: CPU supports 6 MCE banks
[    0.020444] CPU0: Thermal monitoring enabled (TM2)
[    0.020448] using mwait in idle threads.
[    0.023497] ACPI: Core revision 20120320
[    0.027618] ftrace: allocating 24585 entries in 49 pages
[    0.036068] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036535] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077062] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    0.080004] Performance Events: PEBS fmt0-, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.080004] PEBS disabled due to CPU errata.
[    0.080004] ... version:                2
[    0.080004] ... bit width:              40
[    0.080004] ... generic registers:      2
[    0.080004] ... value mask:             000000ffffffffff
[    0.080004] ... max period:             000000007fffffff
[    0.080004] ... fixed-purpose events:   3
[    0.080004] ... event mask:             0000000700000003
[    0.080004] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080004] CPU 1 irqstacks, hard=f5ce2000 soft=f5ce4000
[    0.080004] Booting Node   0, Processors  #1 Ok.
[    0.020001] Initializing CPU#1
[    0.020001] Disabled fast string operations
[    0.088095] Brought up 2 CPUs
[    0.088102] Total of 2 processors activated (7979.94 BogoMIPS).
[    0.092116] devtmpfs: initialized
[    0.092349] EVM: security.selinux
[    0.092352] EVM: security.SMACK64
[    0.092354] EVM: security.capability
[    0.092374] PM: Registering ACPI NVS region [mem 0x3e0f8000-0x3e2f8fff] (2101248 bytes)
[    0.092374] PM: Registering ACPI NVS region [mem 0x3eebe000-0x3eeeefff] (200704 bytes)
[    0.093551] dummy: 
[    0.093597] RTC time: 13:14:38, date: 10/26/12
[    0.093652] NET: Registered protocol family 16
[    0.093668] Trying to unpack rootfs image as initramfs...
[    0.093942] EISA bus registered
[    0.094095] ACPI: bus type pci registered
[    0.094191] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.094195] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in E820
[    0.094199] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
[    0.094201] PCI: Using MMCONFIG for extended config space
[    0.094203] PCI: Using configuration type 1 for base access
[    0.292133] bio: create slab <bio-0> at 0
[    0.292293] ACPI: Added _OSI(Module Device)
[    0.292297] ACPI: Added _OSI(Processor Device)
[    0.292300] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.292303] ACPI: Added _OSI(Processor Aggregator Device)
[    0.293802] ACPI: EC: EC description table is found, configuring boot EC
[    0.297023] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.268924] ACPI: SSDT 3eeb8c10 0026C (v01 APPLE   Cpu0Ist 00003000 INTL 20050309)
[    1.269304] ACPI: Dynamic OEM Table Load:
[    1.269309] ACPI: SSDT   (null) 0026C (v01 APPLE   Cpu0Ist 00003000 INTL 20050309)
[    1.269460] ACPI: SSDT 3eeb8910 002A0 (v01 APPLE   Cpu0Cst 00003001 INTL 20050309)
[    1.269814] ACPI: Dynamic OEM Table Load:
[    1.269818] ACPI: SSDT   (null) 002A0 (v01 APPLE   Cpu0Cst 00003001 INTL 20050309)
[    1.612521] ACPI: SSDT 3eeb8f10 00087 (v01 APPLE   Cpu1Ist 00003000 INTL 20050309)
[    1.612898] ACPI: Dynamic OEM Table Load:
[    1.612902] ACPI: SSDT   (null) 00087 (v01 APPLE   Cpu1Ist 00003000 INTL 20050309)
[    1.613043] ACPI: SSDT 3eeb7f10 00085 (v01 APPLE   Cpu1Cst 00003000 INTL 20050309)
[    1.613400] ACPI: Dynamic OEM Table Load:
[    1.613404] ACPI: SSDT   (null) 00085 (v01 APPLE   Cpu1Cst 00003000 INTL 20050309)
[    3.000497] ACPI: Interpreter enabled
[    3.000518] ACPI: (supports S0 S3 S4 S5)
[    3.000551] ACPI: Using IOAPIC for interrupt routing
[    3.012584] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    3.012820] ACPI: No dock devices found.
[    3.012830] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    3.013375] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    3.014136] pci_root PNP0A08:00: >host bridge window [io  0x0000-0x0cf7] (ignored)
[    3.014140] pci_root PNP0A08:00: >host bridge window [io  0x0d00-0xffff] (ignored)
[    3.014144] pci_root PNP0A08:00: >host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    3.014150] pci_root PNP0A08:00: >host bridge window [mem 0x40000000-0xfebfffff] (ignored)
[    3.014153] PCI: root bus 00: using default resources
[    3.014200] PCI host bridge to bus 0000:00
[    3.014204] pci_bus 0000:00: >root bus resource [io  0x0000-0xffff]
[    3.014208] pci_bus 0000:00: >root bus resource [mem 0x00000000-0xfffffffff]
[    3.014225] pci 0000:00:00.0: >[8086:27a0] type 00 class 0x060000
[    3.014294] pci 0000:00:02.0: >[8086:27a2] type 00 class 0x030000
[    3.014311] pci 0000:00:02.0: >reg 10: [mem 0x50380000-0x503fffff]
[    3.014320] pci 0000:00:02.0: >reg 14: [io  0x20e0-0x20e7]
[    3.014329] pci 0000:00:02.0: >reg 18: [mem 0x40000000-0x4fffffff pref]
[    3.014338] pci 0000:00:02.0: >reg 1c: [mem 0x50400000-0x5043ffff]
[    3.014396] pci 0000:00:02.1: >[8086:27a6] type 00 class 0x038000
[    3.014409] pci 0000:00:02.1: >reg 10: [mem 0x50300000-0x5037ffff]
[    3.014493] pci 0000:00:07.0: >[8086:27a3] type 00 class 0x110100
[    3.014508] pci 0000:00:07.0: >reg 10: [mem 0x50444000-0x50444fff]
[    3.014620] pci 0000:00:1b.0: >[8086:27d8] type 00 class 0x040300
[    3.014646] pci 0000:00:1b.0: >reg 10: [mem 0x50440000-0x50443fff 64bit]
[    3.014765] pci 0000:00:1b.0: >PME# supported from D0 D3hot D3cold
[    3.014804] pci 0000:00:1c.0: >[8086:27d0] type 01 class 0x060400
[    3.016288] pci 0000:00:1c.0: >PME# supported from D0 D3hot D3cold
[    3.016330] pci 0000:00:1c.1: >[8086:27d2] type 01 class 0x060400
[    3.016456] pci 0000:00:1c.1: >PME# supported from D0 D3hot D3cold
[    3.016501] pci 0000:00:1d.0: >[8086:27c8] type 00 class 0x0c0300
[    3.016564] pci 0000:00:1d.0: >reg 20: [io  0x2080-0x209f]
[    3.016614] pci 0000:00:1d.1: >[8086:27c9] type 00 class 0x0c0300
[    3.016677] pci 0000:00:1d.1: >reg 20: [io  0x2060-0x207f]
[    3.016726] pci 0000:00:1d.2: >[8086:27ca] type 00 class 0x0c0300
[    3.016790] pci 0000:00:1d.2: >reg 20: [io  0x2040-0x205f]
[    3.016840] pci 0000:00:1d.3: >[8086:27cb] type 00 class 0x0c0300
[    3.016903] pci 0000:00:1d.3: >reg 20: [io  0x2020-0x203f]
[    3.016966] pci 0000:00:1d.7: >[8086:27cc] type 00 class 0x0c0320
[    3.016994] pci 0000:00:1d.7: >reg 10: [mem 0x50445400-0x504457ff]
[    3.017114] pci 0000:00:1d.7: >PME# supported from D0 D3hot D3cold
[    3.017147] pci 0000:00:1e.0: >[8086:2448] type 01 class 0x060401
[    3.017261] pci 0000:00:1f.0: >[8086:27b9] type 00 class 0x060100
[    3.017391] pci 0000:00:1f.0: >ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 000f)
[    3.017396] pci 0000:00:1f.0: >ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    3.017404] pci 0000:00:1f.0: >ICH7 LPC Generic IO decode 4 PIO at 0300 (mask 001f)
[    3.017467] pci 0000:00:1f.1: >[8086:27df] type 00 class 0x01018a
[    3.017487] pci 0000:00:1f.1: >reg 10: [io  0x20d8-0x20df]
[    3.017501] pci 0000:00:1f.1: >reg 14: [io  0x20f4-0x20f7]
[    3.017515] pci 0000:00:1f.1: >reg 18: [io  0x20d0-0x20d7]
[    3.017530] pci 0000:00:1f.1: >reg 1c: [io  0x20f0-0x20f3]
[    3.017544] pci 0000:00:1f.1: >reg 20: [io  0x20b0-0x20bf]
[    3.017600] pci 0000:00:1f.2: >[8086:27c4] type 00 class 0x01018f
[    3.017625] pci 0000:00:1f.2: >reg 10: [io  0x20c8-0x20cf]
[    3.017639] pci 0000:00:1f.2: >reg 14: [io  0x20ec-0x20ef]
[    3.017653] pci 0000:00:1f.2: >reg 18: [io  0x20c0-0x20c7]
[    3.017668] pci 0000:00:1f.2: >reg 1c: [io  0x20e8-0x20eb]
[    3.017682] pci 0000:00:1f.2: >reg 20: [io  0x20a0-0x20af]
[    3.017697] pci 0000:00:1f.2: >reg 24: [mem 0x50445000-0x504453ff]
[    3.017749] pci 0000:00:1f.2: >PME# supported from D3hot
[    3.017774] pci 0000:00:1f.3: >[8086:27da] type 00 class 0x0c0500
[    3.017855] pci 0000:00:1f.3: >reg 20: [io  0xefa0-0xefbf]
[    3.018012] pci 0000:01:00.0: >[11ab:4362] type 00 class 0x020000
[    3.018047] pci 0000:01:00.0: >reg 10: [mem 0x50200000-0x50203fff 64bit]
[    3.018066] pci 0000:01:00.0: >reg 18: [io  0x1000-0x10ff]
[    3.018134] pci 0000:01:00.0: >reg 30: [mem 0xfffe0000-0xffffffff pref]
[    3.018238] pci 0000:01:00.0: >supports D1 D2
[    3.018242] pci 0000:01:00.0: >PME# supported from D0 D1 D2 D3hot D3cold
[    3.018268] pci 0000:01:00.0: >disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    3.018283] pci 0000:00:1c.0: >PCI bridge to [bus 01-01]
[    3.018290] pci 0000:00:1c.0: >  bridge window [io  0x1000-0x1fff]
[    3.018296] pci 0000:00:1c.0: >  bridge window [mem 0x50200000-0x502fffff]
[    3.018401] pci 0000:02:00.0: >[168c:0024] type 00 class 0x028000
[    3.018436] pci 0000:02:00.0: >reg 10: [mem 0x50100000-0x5010ffff 64bit]
[    3.018612] pci 0000:02:00.0: >supports D1
[    3.018615] pci 0000:02:00.0: >PME# supported from D0 D1 D3hot
[    3.018655] pci 0000:02:00.0: >disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    3.018669] pci 0000:00:1c.1: >PCI bridge to [bus 02-02]
[    3.018679] pci 0000:00:1c.1: >  bridge window [mem 0x50100000-0x501fffff]
[    3.018744] pci 0000:03:03.0: >[11c1:5811] type 00 class 0x0c0010
[    3.018769] pci 0000:03:03.0: >reg 10: [mem 0x50000000-0x50000fff]
[    3.018883] pci 0000:03:03.0: >supports D1 D2
[    3.018886] pci 0000:03:03.0: >PME# supported from D0 D1 D2 D3hot
[    3.018956] pci 0000:00:1e.0: >PCI bridge to [bus 03-03] (subtractive decode)
[    3.018966] pci 0000:00:1e.0: >  bridge window [mem 0x50000000-0x500fffff]
[    3.018976] pci 0000:00:1e.0: >  bridge window [io  0x0000-0xffff] (subtractive decode)
[    3.018980] pci 0000:00:1e.0: >  bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    3.019004] pci_bus 0000:00: >on NUMA node 0
[    3.019009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.019227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    3.019304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    3.019401] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    3.019786]  pci0000:00: >Requesting ACPI _OSC control (0x1d)
[    3.020168]  pci0000:00: >ACPI _OSC control (0x1d) granted
[    3.025647] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    3.025721] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.025790] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    3.025859] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.025928] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    3.025998] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    3.026068] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    3.026136] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[    3.026302] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    3.026319] vgaarb: loaded
[    3.026322] vgaarb: bridge control possible 0000:00:02.0
[    3.026687] SCSI subsystem initialized
[    3.200255] libata version 3.00 loaded.
[    3.200305] ACPI: bus type usb registered
[    3.200344] usbcore: registered new interface driver usbfs
[    3.200366] usbcore: registered new interface driver hub
[    3.200423] usbcore: registered new device driver usb
[    3.200586] PCI: Using ACPI for IRQ routing
[    3.203364] PCI: pci_cache_line_size set to 64 bytes
[    3.203485] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    3.203489] e820: reserve RAM buffer [mem 0x3e0f8000-0x3fffffff]
[    3.203649] NetLabel: Initializing
[    3.203651] NetLabel:  domain hash size = 128
[    3.203653] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.203668] NetLabel:  unlabeled traffic allowed by default
[    3.203849] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    3.203857] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    3.203865] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    3.356380] Switching to clocksource hpet
[    3.369222] AppArmor: AppArmor Filesystem Enabled
[    3.369265] pnp: PnP ACPI init
[    3.369289] ACPI: bus type pnp registered
[    3.369760] pnp 00:00: >[bus 00-ff]
[    3.369765] pnp 00:00: >[io  0x0000-0x0cf7 window]
[    3.369768] pnp 00:00: >[io  0x0cf8-0x0cff]
[    3.369772] pnp 00:00: >[io  0x0d00-0xffff window]
[    3.369776] pnp 00:00: >[mem 0x000a0000-0x000bffff window]
[    3.369779] pnp 00:00: >[mem 0x000c0000-0x000c3fff window]
[    3.369783] pnp 00:00: >[mem 0x000c4000-0x000c7fff window]
[    3.369786] pnp 00:00: >[mem 0x000c8000-0x000cbfff window]
[    3.369789] pnp 00:00: >[mem 0x000cc000-0x000cffff window]
[    3.369793] pnp 00:00: >[mem 0x000d0000-0x000d3fff window]
[    3.369796] pnp 00:00: >[mem 0x000d4000-0x000d7fff window]
[    3.369800] pnp 00:00: >[mem 0x000d8000-0x000dbfff window]
[    3.369803] pnp 00:00: >[mem 0x000dc000-0x000dffff window]
[    3.369806] pnp 00:00: >[mem 0x000e0000-0x000e3fff window]
[    3.369810] pnp 00:00: >[mem 0x000e4000-0x000e7fff window]
[    3.369813] pnp 00:00: >[mem 0x000e8000-0x000ebfff window]
[    3.369816] pnp 00:00: >[mem 0x000ec000-0x000effff window]
[    3.369820] pnp 00:00: >[mem 0x000f0000-0x000fffff window]
[    3.369826] pnp 00:00: >[mem 0x40000000-0xfebfffff window]
[    3.369920] pnp 00:00: >Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    3.369937] pnp 00:01: >[mem 0xf0000000-0xf3ffffff]
[    3.369940] pnp 00:01: >[mem 0xfed14000-0xfed17fff]
[    3.369943] pnp 00:01: >[mem 0xfed18000-0xfed18fff]
[    3.369947] pnp 00:01: >[mem 0xfed19000-0xfed19fff]
[    3.369950] pnp 00:01: >[mem 0xfed1c000-0xfed1ffff]
[    3.369953] pnp 00:01: >[mem 0xfed20000-0xfed8ffff]
[    3.370029] system 00:01: >[mem 0xf0000000-0xf3ffffff] has been reserved
[    3.370034] system 00:01: >[mem 0xfed14000-0xfed17fff] has been reserved
[    3.370038] system 00:01: >[mem 0xfed18000-0xfed18fff] has been reserved
[    3.370042] system 00:01: >[mem 0xfed19000-0xfed19fff] has been reserved
[    3.370046] system 00:01: >[mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.370050] system 00:01: >[mem 0xfed20000-0xfed8ffff] has been reserved
[    3.370055] system 00:01: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.370317] pnp 00:02: >[io  0x0300-0x031f]
[    3.370333] pnp 00:02: >[irq 6]
[    3.370396] pnp 00:02: >Plug and Play ACPI device, IDs APP0001 (active)
[    3.370450] pnp 00:03: >[io  0x0000-0x001f]
[    3.370454] pnp 00:03: >[io  0x0081-0x0091]
[    3.370457] pnp 00:03: >[io  0x0093-0x009f]
[    3.370460] pnp 00:03: >[io  0x00c0-0x00df]
[    3.370463] pnp 00:03: >[dma 4]
[    3.370524] pnp 00:03: >Plug and Play ACPI device, IDs PNP0200 (active)
[    3.370538] pnp 00:04: >[mem 0xff000000-0xffffffff]
[    3.370598] pnp 00:04: >Plug and Play ACPI device, IDs INT0800 (active)
[    3.370688] pnp 00:05: >[irq 0 disabled]
[    3.370696] pnp 00:05: >[irq 8]
[    3.370699] pnp 00:05: >[mem 0xfed00000-0xfed003ff]
[    3.370790] system 00:05: >[mem 0xfed00000-0xfed003ff] has been reserved
[    3.370795] system 00:05: >Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    3.370812] pnp 00:06: >[io  0x00f0]
[    3.370820] pnp 00:06: >[irq 13]
[    3.370883] pnp 00:06: >Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.370916] pnp 00:07: >[io  0x002e-0x002f]
[    3.370920] pnp 00:07: >[io  0x004e-0x004f]
[    3.370923] pnp 00:07: >[io  0x0061]
[    3.370926] pnp 00:07: >[io  0x0063]
[    3.370929] pnp 00:07: >[io  0x0065]
[    3.370932] pnp 00:07: >[io  0x0067]
[    3.370935] pnp 00:07: >[io  0x0070]
[    3.370938] pnp 00:07: >[io  0x0080]
[    3.370940] pnp 00:07: >[io  0x0092]
[    3.370944] pnp 00:07: >[io  0x00b2-0x00b3]
[    3.370947] pnp 00:07: >[io  0x0680-0x06ef]
[    3.370950] pnp 00:07: >[io  0x0800-0x080f]
[    3.370953] pnp 00:07: >[io  0x0810-0x0817]
[    3.370956] pnp 00:07: >[io  0x0400-0x047f]
[    3.370960] pnp 00:07: >[io  0x0500-0x053f]
[    3.370963] pnp 00:07: >[io  0x1640-0x164f]
[    3.370978] pnp 00:07: >disabling [io  0x1640-0x164f] because it overlaps 0000:00:1c.0 BAR 13 [io  0x1000-0x1fff]
[    3.371072] system 00:07: >[io  0x0680-0x06ef] has been reserved
[    3.371077] system 00:07: >[io  0x0800-0x080f] has been reserved
[    3.371080] system 00:07: >[io  0x0810-0x0817] has been reserved
[    3.371084] system 00:07: >[io  0x0400-0x047f] has been reserved
[    3.371088] system 00:07: >[io  0x0500-0x053f] has been reserved
[    3.371093] system 00:07: >Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.371107] pnp 00:08: >[io  0x0070-0x0077]
[    3.371170] pnp 00:08: >Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.374843] pnp: PnP ACPI: found 9 devices
[    3.374846] ACPI: ACPI bus type pnp unregistered
[    3.374851] PnPBIOS: Disabled by ACPI PNP
[    3.411964] pci 0000:01:00.0: >no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    3.412019] pci 0000:00:1c.0: >bridge window [mem 0x00100000-0x001fffff pref] to [bus 01-01] add_size 200000
[    3.412034] pci 0000:00:1c.1: >bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    3.412039] pci 0000:00:1c.1: >bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    3.412058] pci 0000:00:1c.0: >res[15]=[mem 0x00100000-0x001fffff pref] get_res_add_size add_size 200000
[    3.412062] pci 0000:00:1c.1: >res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    3.412066] pci 0000:00:1c.1: >res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    3.412074] pci 0000:00:1c.0: >BAR 15: assigned [mem 0x50500000-0x507fffff pref]
[    3.412079] pci 0000:00:1c.1: >BAR 15: assigned [mem 0x50800000-0x509fffff 64bit pref]
[    3.412085] pci 0000:00:1c.1: >BAR 13: assigned [io  0x3000-0x3fff]
[    3.412090] pci 0000:01:00.0: >BAR 6: assigned [mem 0x50500000-0x5051ffff pref]
[    3.412095] pci 0000:00:1c.0: >PCI bridge to [bus 01-01]
[    3.412100] pci 0000:00:1c.0: >  bridge window [io  0x1000-0x1fff]
[    3.412108] pci 0000:00:1c.0: >  bridge window [mem 0x50200000-0x502fffff]
[    3.412115] pci 0000:00:1c.0: >  bridge window [mem 0x50500000-0x507fffff pref]
[    3.412124] pci 0000:00:1c.1: >PCI bridge to [bus 02-02]
[    3.412129] pci 0000:00:1c.1: >  bridge window [io  0x3000-0x3fff]
[    3.412137] pci 0000:00:1c.1: >  bridge window [mem 0x50100000-0x501fffff]
[    3.412144] pci 0000:00:1c.1: >  bridge window [mem 0x50800000-0x509fffff 64bit pref]
[    3.412154] pci 0000:00:1e.0: >PCI bridge to [bus 03-03]
[    3.412163] pci 0000:00:1e.0: >  bridge window [mem 0x50000000-0x500fffff]
[    3.412238] pci 0000:00:1e.0: >power state changed by ACPI to D0
[    3.412244] pci 0000:00:1e.0: >power state changed by ACPI to D0
[    3.412253] pci 0000:00:1e.0: >setting latency timer to 64
[    3.412259] pci_bus 0000:00: >resource 4 [io  0x0000-0xffff]
[    3.412262] pci_bus 0000:00: >resource 5 [mem 0x00000000-0xfffffffff]
[    3.412266] pci_bus 0000:01: >resource 0 [io  0x1000-0x1fff]
[    3.412269] pci_bus 0000:01: >resource 1 [mem 0x50200000-0x502fffff]
[    3.412273] pci_bus 0000:01: >resource 2 [mem 0x50500000-0x507fffff pref]
[    3.412277] pci_bus 0000:02: >resource 0 [io  0x3000-0x3fff]
[    3.412280] pci_bus 0000:02: >resource 1 [mem 0x50100000-0x501fffff]
[    3.412284] pci_bus 0000:02: >resource 2 [mem 0x50800000-0x509fffff 64bit pref]
[    3.412287] pci_bus 0000:03: >resource 1 [mem 0x50000000-0x500fffff]
[    3.412291] pci_bus 0000:03: >resource 4 [io  0x0000-0xffff]
[    3.412294] pci_bus 0000:03: >resource 5 [mem 0x00000000-0xfffffffff]
[    3.412344] NET: Registered protocol family 2
[    3.412426] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.412670] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.413181] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    3.413438] TCP: Hash tables configured (established 131072 bind 65536)
[    3.413441] TCP: reno registered
[    3.413444] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    3.413455] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    3.413526] NET: Registered protocol family 1
[    3.413547] pci 0000:00:02.0: >Boot video device
[    3.413760] PCI: CLS mismatch (256 != 64), using 64 bytes
[    3.414387] audit: initializing netlink socket (disabled)
[    3.414400] type=2000 audit(1351257281.408:1): initialized
[    3.444366] highmem bounce pool size: 64 pages
[    3.444382] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.446795] VFS: Disk quotas dquot_6.5.2
[    3.446868] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.447652] fuse init (API version 7.19)
[    3.447780] msgmni has been set to 1708
[    3.448225] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.448262] io scheduler noop registered
[    3.448265] io scheduler deadline registered (default)
[    3.448274] io scheduler cfq registered
[    3.448508] pcieport 0000:00:1c.0: >irq 40 for MSI/MSI-X
[    3.448717] pcieport 0000:00:1c.1: >irq 41 for MSI/MSI-X
[    3.448898] pcieport 0000:00:1c.0: >Signaling PME through PCIe PME interrupt
[    3.448902] pci 0000:01:00.0: >Signaling PME through PCIe PME interrupt
[    3.448909] pcie_pme 0000:00:1c.0:pcie01: >service driver pcie_pme loaded
[    3.448937] pcieport 0000:00:1c.1: >Signaling PME through PCIe PME interrupt
[    3.448941] pci 0000:02:00.0: >Signaling PME through PCIe PME interrupt
[    3.448947] pcie_pme 0000:00:1c.1:pcie01: >service driver pcie_pme loaded
[    3.448974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.449043] pciehp 0000:00:1c.0:pcie04: >HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[    3.449072] pciehp 0000:00:1c.0:pcie04: >service driver pciehp loaded
[    3.449090] pciehp 0000:00:1c.1:pcie04: >HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[    3.449118] pciehp 0000:00:1c.1:pcie04: >service driver pciehp loaded
[    3.449129] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.449244] intel_idle: does not run on family 6 model 15
[    3.449349] ACPI: AC Adapter [ADP1] (off-line)
[    3.449448] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    3.449472] ACPI: Lid Switch [LID0]
[    3.449531] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.449536] ACPI: Power Button [PWRB]
[    3.449593] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.449597] ACPI: Sleep Button [SLPB]
[    3.449668] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    3.449672] ACPI: Power Button [PWRF]
[    3.449780] ACPI: Requesting acpi_cpufreq
[    4.745483] Refined TSC clocksource calibration: 1994.999 MHz.
[    4.745496] Switching to clocksource tsc
[    4.902444] Freeing initrd memory: 16484k freed
[    4.916851] Monitor-Mwait will be used to enter C-1 state
[    4.916870] Monitor-Mwait will be used to enter C-2 state
[    4.916886] Monitor-Mwait will be used to enter C-3 state
[    4.916898] Marking TSC unstable due to TSC halts in idle
[    4.916925] ACPI: acpi_idle registered with cpuidle
[    4.918538] Switching to clocksource hpet
[    4.928946] ACPI: Battery Slot [BAT0] (battery present)
[    4.928986] GHES: HEST is not enabled!
[    4.929140] isapnp: Scanning for PnP cards...
[    4.929241] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.933886] Linux agpgart interface v0.103
[    4.933999] agpgart-intel 0000:00:00.0: >Intel 945GM Chipset
[    4.934069] agpgart-intel 0000:00:00.0: >detected gtt size: 262144K total, 262144K mappable
[    4.935449] agpgart-intel 0000:00:00.0: >detected 16384K stolen memory
[    4.935852] agpgart-intel 0000:00:00.0: >AGP aperture is 256M @ 0x40000000
[    4.939184] brd: module loaded
[    4.941179] loop: module loaded
[    4.941634] ata_piix 0000:00:1f.1: >version 2.13
[    4.941646] ata_piix 0000:00:1f.1: >power state changed by ACPI to D0
[    4.941651] ata_piix 0000:00:1f.1: >power state changed by ACPI to D0
[    4.941707] ata_piix 0000:00:1f.1: >setting latency timer to 64
[    4.942465] scsi0 : ata_piix
[    4.943719] scsi1 : ata_piix
[    4.944267] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[    4.944271] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[    4.944296] ata_piix 0000:00:1f.2: >MAP [
[    4.944298]  P0 P2 -- -- ]
[    5.001299] ACPI: Battery Slot [BAT0] (battery present)
[    5.100038] ata_piix 0000:00:1f.2: >setting latency timer to 64
[    5.111695] scsi2 : ata_piix
[    5.112341] ata1.00: ATAPI: MATSHITADVD-R   UJ-857D, KBVB, max UDMA/66
[    5.112507] scsi3 : ata_piix
[    5.113286] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[    5.113289] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[    5.113825] Fixed MDIO Bus: probed
[    5.113914] tun: Universal TUN/TAP device driver, 1.6
[    5.113916] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.113973] PPP generic driver version 2.4.2
[    5.114034] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.114082] ehci_hcd 0000:00:1d.7: >setting latency timer to 64
[    5.114087] ehci_hcd 0000:00:1d.7: >EHCI Host Controller
[    5.114095] ehci_hcd 0000:00:1d.7: >new USB bus registered, assigned bus number 1
[    5.114121] ehci_hcd 0000:00:1d.7: >using broken periodic workaround
[    5.114135] ehci_hcd 0000:00:1d.7: >debug port 1
[    5.118022] ehci_hcd 0000:00:1d.7: >cache line size of 64 is not supported
[    5.118042] ehci_hcd 0000:00:1d.7: >irq 21, io mem 0x50445400
[    5.128460] ata1.00: configured for UDMA/66
[    5.128546] ehci_hcd 0000:00:1d.7: >USB 2.0 started, EHCI 1.00
[    5.128603] usb usb1: >New USB device found, idVendor=1d6b, idProduct=0002
[    5.128607] usb usb1: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.128611] usb usb1: >Product: EHCI Host Controller
[    5.128614] usb usb1: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
[    5.128617] usb usb1: >SerialNumber: 0000:00:1d.7
[    5.128779] hub 1-0:1.0: >USB hub found
[    5.128786] hub 1-0:1.0: >8 ports detected
[    5.128937] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.128967] uhci_hcd: USB Universal Host Controller Interface driver
[    5.128996] uhci_hcd 0000:00:1d.0: >setting latency timer to 64
[    5.129001] uhci_hcd 0000:00:1d.0: >UHCI Host Controller
[    5.129008] uhci_hcd 0000:00:1d.0: >new USB bus registered, assigned bus number 2
[    5.129039] uhci_hcd 0000:00:1d.0: >irq 21, io base 0x00002080
[    5.129082] usb usb2: >New USB device found, idVendor=1d6b, idProduct=0001
[    5.129086] usb usb2: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.129089] usb usb2: >Product: UHCI Host Controller
[    5.129093] usb usb2: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    5.129096] usb usb2: >SerialNumber: 0000:00:1d.0
[    5.129246] hub 2-0:1.0: >USB hub found
[    5.129253] hub 2-0:1.0: >2 ports detected
[    5.129350] uhci_hcd 0000:00:1d.1: >setting latency timer to 64
[    5.129355] uhci_hcd 0000:00:1d.1: >UHCI Host Controller
[    5.129362] uhci_hcd 0000:00:1d.1: >new USB bus registered, assigned bus number 3
[    5.129393] uhci_hcd 0000:00:1d.1: >irq 19, io base 0x00002060
[    5.129436] usb usb3: >New USB device found, idVendor=1d6b, idProduct=0001
[    5.129439] usb usb3: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.129443] usb usb3: >Product: UHCI Host Controller
[    5.129446] usb usb3: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    5.129449] usb usb3: >SerialNumber: 0000:00:1d.1
[    5.129592] hub 3-0:1.0: >USB hub found
[    5.129598] hub 3-0:1.0: >2 ports detected
[    5.129694] uhci_hcd 0000:00:1d.2: >setting latency timer to 64
[    5.129699] uhci_hcd 0000:00:1d.2: >UHCI Host Controller
[    5.129706] uhci_hcd 0000:00:1d.2: >new USB bus registered, assigned bus number 4
[    5.129752] uhci_hcd 0000:00:1d.2: >irq 18, io base 0x00002040
[    5.129797] usb usb4: >New USB device found, idVendor=1d6b, idProduct=0001
[    5.129801] usb usb4: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.129804] usb usb4: >Product: UHCI Host Controller
[    5.129807] usb usb4: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    5.129810] usb usb4: >SerialNumber: 0000:00:1d.2
[    5.129962] hub 4-0:1.0: >USB hub found
[    5.129968] hub 4-0:1.0: >2 ports detected
[    5.130065] uhci_hcd 0000:00:1d.3: >setting latency timer to 64
[    5.130070] uhci_hcd 0000:00:1d.3: >UHCI Host Controller
[    5.130078] uhci_hcd 0000:00:1d.3: >new USB bus registered, assigned bus number 5
[    5.130123] uhci_hcd 0000:00:1d.3: >irq 16, io base 0x00002020
[    5.130166] usb usb5: >New USB device found, idVendor=1d6b, idProduct=0001
[    5.130170] usb usb5: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.130173] usb usb5: >Product: UHCI Host Controller
[    5.130176] usb usb5: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    5.130179] usb usb5: >SerialNumber: 0000:00:1d.3
[    5.130319] hub 5-0:1.0: >USB hub found
[    5.130325] hub 5-0:1.0: >2 ports detected
[    5.130484] usbcore: registered new interface driver libusual
[    5.130553] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    5.131435] i8042: No controller found
[    5.131511] mousedev: PS/2 mouse device common for all mice
[    5.131734] rtc_cmos 00:08: >RTC can wake from S4
[    5.131900] rtc_cmos 00:08: >rtc core: registered rtc_cmos as rtc0
[    5.131935] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    5.132023] device-mapper: uevent: version 1.0.3
[    5.132107] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    5.132154] EISA: Probing bus 0 at eisa.0
[    5.132163] Cannot allocate resource for EISA slot 1
[    5.132166] Cannot allocate resource for EISA slot 2
[    5.132169] Cannot allocate resource for EISA slot 3
[    5.132199] EISA: Detected 0 cards.
[    5.132263] cpuidle: using governor ladder
[    5.132342] cpuidle: using governor menu
[    5.132345] EFI Variables Facility v0.08 2004-May-17
[    5.132576] ashmem: initialized
[    5.132770] TCP: cubic registered
[    5.132923] NET: Registered protocol family 10
[    5.133187] NET: Registered protocol family 17
[    5.133211] Key type dns_resolver registered
[    5.133342] Using IPI No-Shortcut mode
[    5.133454] PM: Hibernation image not present or could not be loaded.
[    5.133470] registered taskstats version 1
[    5.136401] Key type trusted registered
[    5.138984] Key type encrypted registered
[    5.142002]   Magic number: 0:525:231
[    5.142104] rtc_cmos 00:08: >setting system clock to 2012-10-26 13:14:43 UTC (1351257283)
[    5.142730] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.142732] EDD information not available.
[    5.284170] isapnp: No Plug & Play device found
[    5.295477] scsi 0:0:0:0: >CD-ROM            MATSHITA DVD-R   UJ-857D  KBVB PQ: 0 ANSI: 5
[    5.297069] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    5.297074] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.297332] sr 0:0:0:0: >Attached scsi CD-ROM sr0
[    5.297465] sr 0:0:0:0: >Attached scsi generic sg0 type 5
[    5.300464] ata3.01: ATA-7: TOSHIBA MK8034GSX, AH303B, max UDMA/100
[    5.300471] ata3.01: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/8)
[    5.308518] ata3.01: configured for UDMA/100
[    5.308752] scsi 2:0:1:0: >Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[    5.309013] sd 2:0:1:0: >[sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    5.309035] sd 2:0:1:0: >Attached scsi generic sg1 type 0
[    5.309069] sd 2:0:1:0: >[sda] Write Protect is off
[    5.309073] sd 2:0:1:0: >[sda] Mode Sense: 00 3a 00 00
[    5.309120] sd 2:0:1:0: >[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.552086] usb 1-4: >new high-speed USB device number 3 using ehci_hcd
[    5.684381] usb 1-4: >New USB device found, idVendor=05ac, idProduct=8300
[    5.684389] usb 1-4: >New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.749433]  sda: sda1 sda2
[    5.749872] sd 2:0:1:0: >[sda] Attached SCSI disk
[    5.749987] Freeing unused kernel memory: 756k freed
[    5.750393] Write protecting the kernel text: 5960k
[    5.750424] Write protecting the kernel read-only data: 2424k
[    5.750426] NX-protecting the kernel data: 4280k
[    5.771348] udevd[103]: starting version 175
[    5.842990] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.843055] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    5.866205] sky2: driver version 1.30
[    5.866299] sky2 0000:01:00.0: >Yukon-2 EC chip revision 2
[    5.866422] sky2 0000:01:00.0: >irq 42 for MSI/MSI-X
[    5.867124] sky2 0000:01:00.0: >eth0: addr 00:19:e3:35:18:b2
[    5.944176] firewire_ohci 0000:03:03.0: >added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    5.953157] [drm] Initialized drm 1.1.0 20060810
[    5.958081] i915 0000:00:02.0: >setting latency timer to 64
[    5.958373] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.958376] [drm] Driver supports precise vblank timestamp query.
[    5.958438] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    6.148186] usb 2-2: >new full-speed USB device number 2 using uhci_hcd
[    6.395115] usb 2-2: >New USB device found, idVendor=05ac, idProduct=021b
[    6.395124] usb 2-2: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.395130] usb 2-2: >Product: Apple Internal Keyboard / Trackpad
[    6.395135] usb 2-2: >Manufacturer: Apple Computer
[    6.410218] usbcore: registered new interface driver usbhid
[    6.410223] usbhid: USB HID core driver
[    6.413100] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
[    6.413240] apple 0003:05AC:021B.0001: >input,hidraw0: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2/input0
[    6.414155] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2/input/input6
[    6.414278] apple 0003:05AC:021B.0002: >input,hidraw1: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2/input2
[    6.444268] firewire_core 0000:03:03.0: created device fw0: GUID 0019e3fffe79be9a, S400
[    6.569435] [drm] initialized overlay support
[    6.569465] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[    6.571948] i915: render error detected, EIR: 0x00000010
[    6.571950] i915: page table error
[    6.571952] i915:   PGTBL_ER: 0x00000102
[    6.571956] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[    6.571963] i915: render error detected, EIR: 0x00000010
[    6.571965] i915: page table error
[    6.571966] i915:   PGTBL_ER: 0x00000102
[    6.644101] usb 4-2: >new full-speed USB device number 2 using uhci_hcd
[    6.766615] fbcon: inteldrmfb (fb0) is primary device
[    6.821828] usb 4-2: >New USB device found, idVendor=05ac, idProduct=8240
[    6.821832] usb 4-2: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.821836] usb 4-2: >Product: IR Receiver
[    6.821839] usb 4-2: >Manufacturer: Apple Computer, Inc.
[    6.833199] hid-generic 0003:05AC:8240.0003: >hiddev0,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-2/input0
[    7.064080] usb 5-1: >new full-speed USB device number 2 using uhci_hcd
[    7.132340] Console: switching to colour frame buffer device 160x50
[    7.136825] fb0: inteldrmfb frame buffer device
[    7.136827] drm: registered panic notifier
[    7.136835] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.245207] usb 5-1: >New USB device found, idVendor=05ac, idProduct=1000
[    7.245217] usb 5-1: >New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    7.265781] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input7
[    7.265879] hid-generic 0003:05AC:1000.0004: >input,hidraw3: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1d.3-1/input0
[    7.306813] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input8
[    7.306945] hid-generic 0003:05AC:1000.0005: >input,hidraw4: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1d.3-1/input1
[    7.689641] xor: automatically using best checksumming function:
[    7.728008]    pIII_sse  :  6903.000 MB/sec
[    7.728868] device-mapper: dm-raid45: initialized v0.2594b
[    8.526181] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.532391] ISO 9660 Extensions: RRIP_1991A
[    9.036219] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   60.911497] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.678514] udevd[1172]: starting version 175
[   67.951432] device-mapper: multipath: version 1.4.0 loaded
[   68.251978] microcode: CPU0 sig=0x6f6, pf=0x20, revision=0xc7
[   68.364462] lp: driver loaded but no devices found
[   69.203068] init: failsafe main process (1359) killed by TERM signal
[   69.221225] usb 5-1: >usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -75
[   69.496096] usb 5-1: >USB disconnect, device number 2
[   69.627524] Bluetooth: Core ver 2.16
[   69.627549] NET: Registered protocol family 31
[   69.627551] Bluetooth: HCI device and connection manager initialized
[   69.627553] Bluetooth: HCI socket layer initialized
[   69.627555] Bluetooth: L2CAP socket layer initialized
[   69.627563] Bluetooth: SCO socket layer initialized
[   69.744090] usb 5-1: >new full-speed USB device number 3 using uhci_hcd
[   69.786908] microcode: CPU1 sig=0x6f6, pf=0x20, revision=0xc7
[   69.794193] ppdev: user-space parallel port driver
[   69.799551] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   69.940223] usb 5-1: >New USB device found, idVendor=05ac, idProduct=8205
[   69.940230] usb 5-1: >New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   70.066863] applesmc: key=225 fan=1 temp=10 acc=1 lux=0 kbd=0
[   70.130469] input: applesmc as /devices/platform/applesmc.768/input/input9
[   70.675408] Bluetooth: RFCOMM TTY layer initialized
[   70.675415] Bluetooth: RFCOMM socket layer initialized
[   70.675417] Bluetooth: RFCOMM ver 1.11
[   71.385838] intel_rng: FWH not detected
[   71.396057] cfg80211: Calling CRDA to update world regulatory domain
[   71.397105] appletouch 2-2:1.1: >Geyser mode initialized.
[   71.397181] input: appletouch as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input10
[   71.397375] usbcore: registered new interface driver appletouch
[   71.666231] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   71.666237] Bluetooth: BNEP filters: protocol multicast
[   72.073632] usbcore: registered new interface driver btusb
[   73.076852] Unable to load isight firmware
[   73.077829] usbcore: registered new interface driver isight_firmware
[   73.710916] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   73.710925] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   73.710928] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   73.710932] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   73.710937] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   73.710942] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   73.710946] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   73.710948] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   75.103645] cfg80211: World regulatory domain updated:
[   75.103650] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   75.103653] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.103655] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.103658] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.103660] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.103663] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.271778] leds_ss4200: no LED devices found
[   84.650265] snd_hda_intel 0000:00:1b.0: >irq 43 for MSI/MSI-X
[   85.137755] hda_codec: STAC922x, Apple subsys_id=106b2200
[   85.149766] input: HDA Intel SPDIF In as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   85.149965] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   85.150145] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   85.150319] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   92.599832] sky2 0000:01:00.0: >eth0: enabling interface
[   92.600124] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   92.600722] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   92.865154] ath: EEPROM regdomain: 0x37
[   92.865158] ath: EEPROM indicates we should expect a direct regpair map
[   92.865161] ath: Country alpha2 being used: AW
[   92.865163] ath: Regpair used: 0x37
[   92.865167] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   92.865170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865172] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   92.865175] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865177] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   92.865179] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865181] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   92.865184] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865186] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   92.865188] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865190] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   92.865193] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865195] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   92.865197] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865199] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   92.865202] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865204] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   92.865206] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865208] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   92.865210] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865212] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   92.865215] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   92.865217] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865219] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865221] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865224] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   92.865226] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865228] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   92.865231] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865233] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   92.865235] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865237] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   92.865240] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865242] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   92.865244] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865246] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   92.865249] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865251] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   92.865253] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865255] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   92.865258] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865260] cfg80211: Disabling freq 5500 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865262] cfg80211: Disabling freq 5520 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865264] cfg80211: Disabling freq 5540 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865266] cfg80211: Disabling freq 5560 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865268] cfg80211: Disabling freq 5580 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865270] cfg80211: Disabling freq 5600 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865272] cfg80211: Disabling freq 5620 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865274] cfg80211: Disabling freq 5640 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865276] cfg80211: Disabling freq 5660 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865278] cfg80211: Disabling freq 5680 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865280] cfg80211: Disabling freq 5700 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   92.865282] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   92.865284] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865286] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   92.865289] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865291] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   92.865293] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865295] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   92.865298] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.865300] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   92.865302] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   92.871518] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   92.871521] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871524] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   92.871526] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871528] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   92.871531] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871533] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   92.871535] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871537] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   92.871540] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871542] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   92.871544] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871546] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   92.871549] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871551] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   92.871553] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871555] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   92.871558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871560] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   92.871562] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871564] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   92.871566] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871569] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   92.871571] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   92.871573] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   92.871576] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   92.871578] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   92.871580] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   92.871582] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   92.871585] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871587] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   92.871589] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871591] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   92.871594] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871596] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   92.871598] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871600] cfg80211: Disabling freq 5260 MHz
[   92.871602] cfg80211: Disabling freq 5280 MHz
[   92.871604] cfg80211: Disabling freq 5300 MHz
[   92.871605] cfg80211: Disabling freq 5320 MHz
[   92.871607] cfg80211: Disabling freq 5500 MHz
[   92.871608] cfg80211: Disabling freq 5520 MHz
[   92.871610] cfg80211: Disabling freq 5540 MHz
[   92.871612] cfg80211: Disabling freq 5560 MHz
[   92.871613] cfg80211: Disabling freq 5580 MHz
[   92.871615] cfg80211: Disabling freq 5600 MHz
[   92.871616] cfg80211: Disabling freq 5620 MHz
[   92.871618] cfg80211: Disabling freq 5640 MHz
[   92.871619] cfg80211: Disabling freq 5660 MHz
[   92.871621] cfg80211: Disabling freq 5680 MHz
[   92.871623] cfg80211: Disabling freq 5700 MHz
[   92.871625] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   92.871627] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871629] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   92.871632] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871634] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   92.871636] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871639] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   92.871641] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   92.871643] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   92.871645] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.227121] ieee80211 phy0: >Selected rate control algorithm 'ath9k_rate_control'
[   93.227783] Registered led device: ath9k-phy0
[   93.227790] ieee80211 phy0: >Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81 mem=0xf8e40000, irq=17
[   93.228371] cfg80211: Calling CRDA for country: AW
[   93.235521] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   93.235526] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235529] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   93.235532] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235534] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   93.235536] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235538] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   93.235541] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235543] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   93.235545] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235547] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   93.235550] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235552] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   93.235554] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235556] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   93.235559] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235561] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   93.235563] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235565] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   93.235568] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235570] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   93.235572] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235574] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   93.235576] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235579] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   93.235581] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235583] cfg80211: Disabling freq 2484 MHz
[   93.235585] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   93.235588] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235590] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   93.235593] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235595] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   93.235597] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235599] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   93.235602] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235604] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   93.235606] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235608] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   93.235611] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235613] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   93.235615] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235617] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   93.235620] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   93.235622] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   93.235624] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235626] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   93.235629] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235631] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   93.235633] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235635] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   93.235638] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235640] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   93.235642] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235644] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   93.235647] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235649] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   93.235651] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235653] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   93.235656] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235658] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   93.235660] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235662] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   93.235665] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235667] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   93.235669] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   93.235671] cfg80211: Disabling freq 5745 MHz
[   93.235673] cfg80211: Disabling freq 5765 MHz
[   93.235674] cfg80211: Disabling freq 5785 MHz
[   93.235676] cfg80211: Disabling freq 5805 MHz
[   93.235678] cfg80211: Disabling freq 5825 MHz
[   93.235683] cfg80211: Regulatory domain changed to country: AW
[   93.235685] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   93.235687] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   93.235690] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   93.235692] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   93.235694] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   93.261784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   93.262900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   97.125268] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[  317.954994] wlan0: authenticate with 00:26:f2:4a:df:66
[  317.959239] wlan0: send auth to 00:26:f2:4a:df:66 (try 1/3)
[  317.960268] wlan0: authenticated
[  317.964105] wlan0: associate with 00:26:f2:4a:df:66 (try 1/3)
[  317.965225] wlan0: RX AssocResp from 00:26:f2:4a:df:66 (capab=0x11 status=0 aid=1)
[  317.965297] wlan0: associated
[  317.965497] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  363.216801] wlan0: deauthenticating from 00:26:f2:4a:df:66 by local choice (reason=3)
[  363.247666] cfg80211: All devices are disconnected, going to restore regulatory settings
[  363.247672] cfg80211: Restoring regulatory settings
[  363.247677] cfg80211: Calling CRDA to update world regulatory domain
[  363.510115] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  363.510122] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510125] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  363.510128] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510131] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  363.510134] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510136] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  363.510139] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510142] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  363.510145] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510147] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  363.510150] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510152] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  363.510155] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510157] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  363.510160] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510163] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  363.510166] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510168] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  363.510171] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510173] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  363.510176] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510179] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  363.510181] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510184] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  363.510187] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510189] cfg80211: Disabling freq 2484 MHz
[  363.510192] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  363.510195] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510198] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  363.510201] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510203] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  363.510206] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510208] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  363.510211] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510214] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  363.510216] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510219] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  363.510222] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510224] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  363.510227] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510230] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  363.510232] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  363.510235] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[  363.510238] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510240] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[  363.510243] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510246] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[  363.510249] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510251] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[  363.510254] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510256] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[  363.510259] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510262] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[  363.510265] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510267] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[  363.510270] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510273] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[  363.510275] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510278] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[  363.510281] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510283] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[  363.510286] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510289] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[  363.510292] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  363.510294] cfg80211: Disabling freq 5745 MHz
[  363.510296] cfg80211: Disabling freq 5765 MHz
[  363.510298] cfg80211: Disabling freq 5785 MHz
[  363.510300] cfg80211: Disabling freq 5805 MHz
[  363.510302] cfg80211: Disabling freq 5825 MHz
[  363.510455] cfg80211: World regulatory domain updated:
[  363.510457] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  363.510460] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  363.510463] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  363.510466] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  363.510469] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  363.510472] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  366.776956] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[  368.833042] wlan0: authenticate with 00:26:f2:4a:df:66
[  368.838134] wlan0: send auth to 00:26:f2:4a:df:66 (try 1/3)
[  368.839185] wlan0: authenticated
[  368.844050] wlan0: associate with 00:26:f2:4a:df:66 (try 1/3)
[  368.845192] wlan0: RX AssocResp from 00:26:f2:4a:df:66 (capab=0x11 status=0 aid=1)
[  368.845261] wlan0: associated
[  414.208445] wlan0: deauthenticating from 00:26:f2:4a:df:66 by local choice (reason=3)
[  414.241994] cfg80211: All devices are disconnected, going to restore regulatory settings
[  414.242000] cfg80211: Restoring regulatory settings
[  414.242005] cfg80211: Calling CRDA to update world regulatory domain
[  414.255286] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  414.255292] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255294] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  414.255297] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255299] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  414.255301] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255304] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  414.255306] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255308] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  414.255310] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255312] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  414.255315] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255317] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  414.255319] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255321] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  414.255324] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255326] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  414.255328] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255330] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  414.255333] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255335] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  414.255337] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255339] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  414.255342] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255344] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  414.255346] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255349] cfg80211: Disabling freq 2484 MHz
[  414.255351] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  414.255353] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255355] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  414.255358] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255360] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  414.255363] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255365] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  414.255367] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255369] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  414.255372] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255374] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  414.255376] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255378] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  414.255381] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255383] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  414.255385] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  414.255387] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[  414.255390] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255392] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[  414.255394] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255396] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[  414.255399] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255401] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[  414.255403] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255405] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[  414.255408] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255410] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[  414.255412] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255414] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[  414.255417] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255419] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[  414.255421] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255423] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[  414.255426] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255428] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[  414.255430] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255432] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[  414.255435] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[  414.255437] cfg80211: Disabling freq 5745 MHz
[  414.255438] cfg80211: Disabling freq 5765 MHz
[  414.255440] cfg80211: Disabling freq 5785 MHz
[  414.255442] cfg80211: Disabling freq 5805 MHz
[  414.255443] cfg80211: Disabling freq 5825 MHz
[  414.255595] cfg80211: World regulatory domain updated:
[  414.255596] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  414.255599] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  414.255602] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  414.255604] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  414.255606] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  414.255609] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  417.781110] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[  419.837413] wlan0: authenticate with 00:26:f2:4a:df:66
[  419.843352] wlan0: send auth to 00:26:f2:4a:df:66 (try 1/3)
[  419.844409] wlan0: authenticated
[  419.852152] wlan0: associate with 00:26:f2:4a:df:66 (try 1/3)
[  419.853299] wlan0: RX AssocResp from 00:26:f2:4a:df:66 (capab=0x11 status=0 aid=1)
[  419.853371] wlan0: associated

---

### Post by CameronWyse on 2012-10-26
iwlist scan results:

wlan0     Scan completed :
          Cell 01 - Address: 00:AC:54:DD:D7:8A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-9FS2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000305d8d5c656
                    Extra: Last beacon: 11816ms ago
                    IE: Unknown: 000B4254487562332D39465332
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDAB0050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000242541023001B427573696E6573732048756220332E30204D756C7469204D6F646510240014425420427573696E6573732048756220332E30411042000A313231333039353130301054000800060050F204000110110014425420427573696E6573732048756220332E3041100800020080103C000101
          Cell 02 - Address: 00:18:4D:10:C8:26
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"MarziandMuffin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005933207b25a
                    Extra: Last beacon: 11796ms ago
                    IE: Unknown: 000E4D61727A69616E644D756666696E
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 02:AC:54:DD:D7:8A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000305d8d6b07a
                    Extra: Last beacon: 11808ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 12:AC:54:DD:D7:8A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000305d8d71180
                    Extra: Last beacon: 11784ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D42
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: 00:FE:F4:04:89:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-KG8N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000123365640f2
                    Extra: Last beacon: 11536ms ago
                    IE: Unknown: 000B4254487562332D4B47384E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: 02:FE:F4:04:89:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001233657401e
                    Extra: Last beacon: 11524ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 12:FE:F4:04:89:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012336576668
                    Extra: Last beacon: 11512ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 08 - Address: 02:FE:F4:2B:3A:90
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012337287d80
                    Extra: Last beacon: 11560ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
          Cell 09 - Address: 00:FE:F4:2B:3A:90
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-KK3T"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001233728e180
                    Extra: Last beacon: 11484ms ago
                    IE: Unknown: 000B4254487562332D4B4B3354
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 10 - Address: 00:26:F2:4A:DF:67
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DBNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000286602b18e
                    Extra: Last beacon: 11212ms ago
                    IE: Unknown: 000944424E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B000103104700107577C6BA8EE85A1AF05D63818E84B7E2102100074E6574676561721023000844474E44333330301024000631323334353610420004313233341054000800060050F20400011011000844474E4433333030100800020088
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 02:AC:54:D4:F2:22
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012335f31d80
                    Extra: Last beacon: 11288ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
          Cell 12 - Address: 00:40:36:39:E0:8B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"nagshead"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001288d31e8
                    Extra: Last beacon: 11276ms ago
                    IE: Unknown: 00086E61677368656164
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 070A474220010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400
                    IE: Unknown: 050400010000
          Cell 13 - Address: 12:AC:54:D4:F2:22
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012335f38180
                    Extra: Last beacon: 11260ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
          Cell 14 - Address: 00:26:F2:4A:DF:66
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"DBNetworkPlus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002865ed1f5e
                    Extra: Last beacon: 9036ms ago
                    IE: Unknown: 000D44424E6574776F726B506C7573
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 2D1A6E081BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1624051300000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B000103104700107577C6BA8EE85A1AF05D63818E84B7E2102100074E6574676561721023000844474E44333330301024000631323334353610420004313233341054000800060050F20400011011000844474E4433333030100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E081BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424051300000000000000000000000000000000000000

---

### Post by ahallubuntu on 2012-10-26
Can you try the earlier 12.04 LTS release instead?  12.10 is pretty new, and a number of people seem to have network issues with it.  If you wind up installing Ubuntu and using it long term, 12.04 may be better for you in the end since it will be supported longer than 12.10, until 2017.

---

### Post by CameronWyse on 2012-10-26
thanks, i'll download that and give that a go and let you know how i got on

---

### Post by CameronWyse on 2012-10-26
Hi there,

downloaded and running (from cd) the previous 12.04 version and unfortunately still have the same issue.

I can wirelessly connect to the BT Open Zone and surf the BT web page (login page, find hotspots, etc) but can't connect to my WEP protected router.

i could try changing the security to WAP but i'm sure there is one device in the house that can't use WAP which is why we are on WEP - however, do you think it's something else?

---

### Post by robtygart on 2012-10-26
Look in settings, go to software sources, go to the Additional drivers tab, look for drivers.




When your posting stuf from the terminal "Code" please use the **[ code ] [ /code ]** tags, in Advanced it is shown by "#".

---

### Post by robtygart on 2012-10-26
Sorry I forgot to add, I think it will want a restart, and since you can't when useing a cd. 

If your Using a USB you can make the usb store information between restart. You can make this using your live CD. Look for "Start up disk creator" There will be a check box asking to store info and how much.

---

