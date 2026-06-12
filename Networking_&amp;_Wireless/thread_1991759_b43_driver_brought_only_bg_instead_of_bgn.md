---
title: "b43 driver brought only bg instead of bgn"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by derdigge on 2012-05-30
[INDENT]Dear cummunity!

Yes i have read several posts, used the search function and so on but the most solutions where made using bcmsta driver which isnt an option cause of no master mode aviable!

I have a mac mini mod 2010 and i am going to use it as a  mediaserver/wlanrouter cause of the low Powerconsumption when idle (12W measured)  and the great cpupower if its needed. It does a great job using ubuntu  12.10 but i have broblems bring up my wifi hotspot.

The wfi device is an Broadcom BCM43224 (pci:id 14e4:4353)  [linuxwireless.org]("http://linuxwireless.org") said its supported a/b/g/n since Kernel 3.1+. After i  found out there is a [bug]("http://www.digipedia.pl/usenet/thread/18960/22039/#post22033") inside compat-wireless in ubuntu 12.10 i  compiled it by my self using the latest stable source. (SPROM readout fails on some devices)

Whith this i am able to modprobe b43 successfully but i can use 150mbit with this driver. So i tried using an g hotspot and it works arround 12mbits wpa2 etc. But ieee80211n=1 isnt working cause of the kernelmodule somehow.

my lsmod:

```
root@Wurzelpeter:~# lsmod
Module                  Size  Used by
b43                   370008  0
bcma                   35220  1 b43
ssb                    61696  1 b43
pcmcia                 49310  2 b43,ssb
pcmcia_core            22614  1 pcmcia
vesafb                 13844  1
arc4                   12529  4
snd_hda_codec_hdmi     32474  3
snd_hda_codec_cirrus    23965  1
carl9170               81876  0
joydev                 17693  0
hid_apple              13375  0
usbhid                 47199  0
btusb                  18291  0
bluetooth             204548  2 btusb
mac80211              543880  2 b43,carl9170
hid                    99559  2 hid_apple,usbhid
ath                    23827  1 carl9170
applesmc               19554  0
input_polldev          13896  1 applesmc
cfg80211              210370  4 b43,carl9170,mac80211,ath
compat                 13447  8 b43,bcma,ssb,carl9170,btusb,bluetooth,mac80211,cfg80211
nouveau               774571  0
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
snd_hda_intel          33773  0
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29990  1 snd_pcm
snd                    78855  7 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37277  0
mac_hid                13253  0
lp                     17799  0
parport                46562  1 lp
mmc_block              27300  0
firewire_ohci          41000  0
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   152032  0
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci

```

my lspci:
```
root@Wurzelpeter:~# lspci -vnn -d 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
        Subsystem: Apple Inc. Device [106b:0093]
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d3300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 3b-81-35-ff-ff-81-58-b0
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: bcma-pci-bridge
        Kernel modules: bcma

```

my dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 0000000000090000 (reserved)
[    0.000000]  BIOS-e820: 0000000000090000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000af000000 (usable)
[    0.000000]  BIOS-e820: 00000000af000000 - 00000000bf000000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf000000 - 00000000bf70f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf930000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf930000 - 00000000bf931000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf931000 - 00000000bf939000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf939000 - 00000000bfef9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d3500000 - 00000000d3501000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Apple Inc. Macmini4,1/Mac-F2208EC8, BIOS     MM41.88Z.0042.B00.1004221740 04/22/10
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf70f max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf70f000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf70f000 page 4k
[    0.000000] kernel direct mapping tables up to bf70f000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf709000-bf70f000
[    0.000000] RAMDISK: 3656e000 - 372af000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
[    0.000000] ACPI: XSDT 00000000bf96a1c0 00084 (v01 APPLE   Apple00 00000042      01000013)
[    0.000000] ACPI: FACP 00000000bf968000 000F4 (v04 APPLE   Apple00 00000042 Loki 0000005F)
[    0.000000] ACPI: DSDT 00000000bf95b000 054A1 (v01 APPLE   Macmini 00040001 INTL 20061109)
[    0.000000] ACPI: FACS 00000000bf71e000 00040
[    0.000000] ACPI: HPET 00000000bf967000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf966000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf965000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 00000000bf963000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 00000000bf962000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 00000000bf961000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf957000 00024 (v01 APPLE     Apple 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf956000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: MCFG 00000000bf964000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf95a000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf959000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b800000-ffff88013f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000008f
[    0.000000]     0: 0x00000090 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000af000
[    0.000000]     0: 0x000bf000 -> 0x000bf70f
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 980637
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 698191 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 0000000000090000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000af000000 - 00000000bf000000
[    0.000000] PM: Registered nosave memory: 00000000bf70f000 - 00000000bf930000
[    0.000000] PM: Registered nosave memory: 00000000bf930000 - 00000000bf931000
[    0.000000] PM: Registered nosave memory: 00000000bf931000 - 00000000bf939000
[    0.000000] PM: Registered nosave memory: 00000000bf939000 - 00000000bfef9000
[    0.000000] PM: Registered nosave memory: 00000000bfef9000 - 00000000bfeff000
[    0.000000] PM: Registered nosave memory: 00000000bfeff000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000d3500000
[    0.000000] PM: Registered nosave memory: 00000000d3500000 - 00000000d3501000
[    0.000000] PM: Registered nosave memory: 00000000d3501000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d3501000 (gap: d3501000:1caff000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s83072 r8192 d23424 u1048576
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 960152
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3763376k/5242880k available (6566k kernel code, 1320332k absent, 159172k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2389.101 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4778.20 BogoMIPS (lpj=9556404)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004055] AppArmor: AppArmor initialized
[    0.004056] Yama: becoming mindful.
[    0.004446] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009712] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010612] Mount-cache hash table entries: 256
[    0.010758] Initializing cgroup subsys cpuacct
[    0.010764] Initializing cgroup subsys memory
[    0.010775] Initializing cgroup subsys devices
[    0.010777] Initializing cgroup subsys freezer
[    0.010780] Initializing cgroup subsys blkio
[    0.010786] Initializing cgroup subsys perf_event
[    0.010818] CPU: Physical Processor ID: 0
[    0.010820] CPU: Processor Core ID: 0
[    0.010822] mce: CPU supports 6 MCE banks
[    0.010831] CPU0: Thermal monitoring enabled (TM2)
[    0.010836] using mwait in idle threads.
[    0.013496] ACPI: Core revision 20110623
[    0.017711] ftrace: allocating 27049 entries in 107 pages
[    0.020512] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061626] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.152038] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152080] Brought up 2 CPUs
[    0.152082] Total of 2 processors activated (9556.73 BogoMIPS).
[    0.153977] devtmpfs: initialized
[    0.153977] EVM: security.selinux
[    0.153977] EVM: security.SMACK64
[    0.153977] EVM: security.capability
[    0.153977] PM: Registering ACPI NVS region at bf70f000 (2232320 bytes)
[    0.153977] PM: Registering ACPI NVS region at bf931000 (32768 bytes)
[    0.153977] print_constraints: dummy: 
[    0.153977] RTC time:  2:28:04, date: 05/31/12
[    0.153977] NET: Registered protocol family 16
[    0.156051] Trying to unpack rootfs image as initramfs...
[    0.156132] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.156135] ACPI: bus type pci registered
[    0.156403] PCI: MMCONFIG for domain 0000 [bus 00-05] at [mem 0xf0000000-0xf05fffff] (base 0xf0000000)
[    0.156407] PCI: MMCONFIG at [mem 0xf0000000-0xf05fffff] reserved in E820
[    0.157769] PCI: Using configuration type 1 for base access
[    0.172161] bio: create slab <bio-0> at 0
[    0.172205] ACPI: Added _OSI(Module Device)
[    0.172207] ACPI: Added _OSI(Processor Device)
[    0.172209] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172211] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173545] ACPI: EC: EC description table is found, configuring boot EC
[    0.176024] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.176322] ACPI: SSDT 00000000bf71dc98 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176618] ACPI: Dynamic OEM Table Load:
[    0.176621] ACPI: SSDT           (null) 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176726] ACPI: SSDT 00000000bf71c618 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.177008] ACPI: Dynamic OEM Table Load:
[    0.177011] ACPI: SSDT           (null) 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.244255] ACPI: SSDT 00000000bf71df18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244551] ACPI: Dynamic OEM Table Load:
[    0.244554] ACPI: SSDT           (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244636] ACPI: SSDT 00000000bf71bf18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.244920] ACPI: Dynamic OEM Table Load:
[    0.244922] ACPI: SSDT           (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.272210] ACPI: Interpreter enabled
[    0.272217] ACPI: (supports S0 S3 S4 S5)
[    0.272237] ACPI: Using IOAPIC for interrupt routing
[    0.277364] ACPI: EC: GPE = 0x57, I/O: command/status = 0x66, data = 0x62
[    0.277530] ACPI: No dock devices found.
[    0.277532] HEST: Table not found.
[    0.277536] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277665] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.277775] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.277777] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.277780] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.277782] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.277784] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.277787] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.277789] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.277791] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.277793] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.277796] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.277798] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.277800] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.277802] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.277805] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.277807] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.277809] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[    0.277811] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.277837] pci 0000:00:00.0: [10de:0d60] type 0 class 0x000600
[    0.277954] pci 0000:00:00.1: [10de:0d68] type 0 class 0x000500
[    0.278126] pci 0000:00:01.0: [10de:0d6d] type 0 class 0x000500
[    0.278293] pci 0000:00:01.1: [10de:0d6e] type 0 class 0x000500
[    0.278458] pci 0000:00:01.2: [10de:0d6f] type 0 class 0x000500
[    0.278623] pci 0000:00:01.3: [10de:0d70] type 0 class 0x000500
[    0.278793] pci 0000:00:02.0: [10de:0d71] type 0 class 0x000500
[    0.278959] pci 0000:00:02.1: [10de:0d72] type 0 class 0x000500
[    0.279123] pci 0000:00:03.0: [10de:0d80] type 0 class 0x000601
[    0.279132] pci 0000:00:03.0: reg 10: [io  0x2100-0x21ff]
[    0.279178] pci 0000:00:03.1: [10de:0d7b] type 0 class 0x000500
[    0.279263] pci 0000:00:03.2: [10de:0d79] type 0 class 0x000c05
[    0.279277] pci 0000:00:03.2: reg 10: [io  0x0000-0x00ff]
[    0.279300] pci 0000:00:03.2: reg 20: [io  0x2240-0x227f]
[    0.279307] pci 0000:00:03.2: reg 24: [io  0x2200-0x223f]
[    0.279343] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.279349] pci 0000:00:03.2: PME# disabled
[    0.279374] pci 0000:00:03.3: [10de:0d69] type 0 class 0x000500
[    0.279579] pci 0000:00:03.4: [10de:0d7a] type 0 class 0x000b40
[    0.279600] pci 0000:00:03.4: reg 10: [mem 0xd3500000-0xd357ffff]
[    0.279744] pci 0000:00:04.0: [10de:0d9c] type 0 class 0x000c03
[    0.279756] pci 0000:00:04.0: reg 10: [mem 0xd358a000-0xd358afff]
[    0.279804] pci 0000:00:04.0: supports D1 D2
[    0.279806] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.279810] pci 0000:00:04.0: PME# disabled
[    0.279824] pci 0000:00:04.1: [10de:0d9d] type 0 class 0x000c03
[    0.279838] pci 0000:00:04.1: reg 10: [mem 0xd358b100-0xd358b1ff]
[    0.279898] pci 0000:00:04.1: supports D1 D2
[    0.279900] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.279904] pci 0000:00:04.1: PME# disabled
[    0.279927] pci 0000:00:06.0: [10de:0d9c] type 0 class 0x000c03
[    0.279939] pci 0000:00:06.0: reg 10: [mem 0xd3589000-0xd3589fff]
[    0.279989] pci 0000:00:06.0: supports D1 D2
[    0.279990] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.279994] pci 0000:00:06.0: PME# disabled
[    0.280008] pci 0000:00:06.1: [10de:0d9d] type 0 class 0x000c03
[    0.280032] pci 0000:00:06.1: reg 10: [mem 0xd358b000-0xd358b0ff]
[    0.280094] pci 0000:00:06.1: supports D1 D2
[    0.280096] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280100] pci 0000:00:06.1: PME# disabled
[    0.280125] pci 0000:00:08.0: [10de:0d94] type 0 class 0x000403
[    0.280140] pci 0000:00:08.0: reg 10: [mem 0xd3580000-0xd3583fff]
[    0.280201] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.280205] pci 0000:00:08.0: PME# disabled
[    0.280224] pci 0000:00:0a.0: [10de:0d85] type 0 class 0x000101
[    0.280236] pci 0000:00:0a.0: reg 10: [io  0x2298-0x229f]
[    0.280243] pci 0000:00:0a.0: reg 14: [io  0x22a4-0x22a7]
[    0.280249] pci 0000:00:0a.0: reg 18: [io  0x2290-0x2297]
[    0.280255] pci 0000:00:0a.0: reg 1c: [io  0x22a0-0x22a3]
[    0.280262] pci 0000:00:0a.0: reg 20: [io  0x2280-0x228f]
[    0.280268] pci 0000:00:0a.0: reg 24: [mem 0xd3584000-0xd3585fff]
[    0.280315] pci 0000:00:0b.0: [10de:0d75] type 0 class 0x000500
[    0.280327] pci 0000:00:0b.0: reg 10: [mem 0xd3588000-0xd3588fff]
[    0.280447] pci 0000:00:0e.0: [10de:0d9a] type 1 class 0x000604
[    0.280715] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280724] pci 0000:00:0e.0: PME# disabled
[    0.280832] pci 0000:00:15.0: [10de:0d9b] type 1 class 0x000604
[    0.281100] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.281109] pci 0000:00:15.0: PME# disabled
[    0.281209] pci 0000:00:16.0: [10de:0d9b] type 1 class 0x000604
[    0.281478] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.281486] pci 0000:00:16.0: PME# disabled
[    0.281539] pci 0000:00:17.0: [10de:0d76] type 1 class 0x000604
[    0.281580] pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
[    0.281584] pci 0000:00:17.0: PME# disabled
[    0.281798] pci 0000:01:00.0: [104c:823e] type 1 class 0x000604
[    0.281904] pci 0000:01:00.0: supports D1 D2
[    0.288046] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.288069] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.288164] pci 0000:02:00.0: [104c:823f] type 0 class 0x000c00
[    0.288187] pci 0000:02:00.0: reg 10: [mem 0xd3404000-0xd34047ff]
[    0.288200] pci 0000:02:00.0: reg 14: [mem 0xd3400000-0xd3403fff]
[    0.288296] pci 0000:02:00.0: supports D1 D2
[    0.288298] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.288303] pci 0000:02:00.0: PME# disabled
[    0.288363] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.288374] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.288616] pci 0000:03:00.0: [14e4:4353] type 0 class 0x000280
[    0.288636] pci 0000:03:00.0: reg 10: [mem 0xd3300000-0xd3303fff 64bit]
[    0.288738] pci 0000:03:00.0: supports D1 D2
[    0.288740] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.288745] pci 0000:03:00.0: PME# disabled
[    0.288803] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.288825] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.289039] pci 0000:04:00.0: [14e4:16b4] type 0 class 0x000200
[    0.289060] pci 0000:04:00.0: reg 10: [mem 0xd3100000-0xd310ffff 64bit pref]
[    0.289076] pci 0000:04:00.0: reg 18: [mem 0xd3110000-0xd311ffff 64bit pref]
[    0.289159] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.289164] pci 0000:04:00.0: PME# disabled
[    0.289205] pci 0000:04:00.1: [14e4:16bc] type 0 class 0x000805
[    0.289227] pci 0000:04:00.1: reg 10: [mem 0xd3120000-0xd312ffff 64bit pref]
[    0.289321] pci 0000:04:00.1: PME# supported from D0 D3hot D3cold
[    0.289326] pci 0000:04:00.1: PME# disabled
[    0.296049] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.296072] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.296088] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.296124] pci 0000:05:00.0: [10de:08a4] type 0 class 0x000300
[    0.296137] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.296145] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.296154] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.296160] pci 0000:05:00.0: reg 24: [io  0x1000-0x107f]
[    0.296166] pci 0000:05:00.0: reg 30: [mem 0xd3000000-0xd301ffff pref]
[    0.296215] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.296219] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.296223] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.296227] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.296279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.296508] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.296623]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.296750]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.314943] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315022] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315098] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315176] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315250] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315324] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315399] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315473] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315547] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315622] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315696] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315771] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315846] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.315920] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.315995] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.316083] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.316158] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.316237] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.316310] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.316385] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.316463] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.316537] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.316611] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.316685] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.316759] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.316833] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.316907] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
[    0.317055] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.317057] vgaarb: loaded
[    0.317059] vgaarb: bridge control possible 0000:05:00.0
[    0.317163] i2c-core: driver [aat2870] using legacy suspend method
[    0.317165] i2c-core: driver [aat2870] using legacy resume method
[    0.317233] SCSI subsystem initialized
[    0.317298] libata version 3.00 loaded.
[    0.317349] usbcore: registered new interface driver usbfs
[    0.317359] usbcore: registered new interface driver hub
[    0.317386] usbcore: registered new device driver usb
[    0.317478] PCI: Using ACPI for IRQ routing
[    0.317483] PCI: pci_cache_line_size set to 64 bytes
[    0.317645] reserve RAM buffer: 000000000008f000 - 000000000008ffff 
[    0.317650] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.317652] reserve RAM buffer: 00000000af000000 - 00000000afffffff 
[    0.317654] reserve RAM buffer: 00000000bf70f000 - 00000000bfffffff 
[    0.317753] NetLabel: Initializing
[    0.317755] NetLabel:  domain hash size = 128
[    0.317756] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.317768] NetLabel:  unlabeled traffic allowed by default
[    0.317811] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.317818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.317823] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.320068] Switching to clocksource hpet
[    0.327869] AppArmor: AppArmor Filesystem Enabled
[    0.327909] pnp: PnP ACPI init
[    0.327931] ACPI: bus type pnp registered
[    0.328069] pnp 00:00: [bus 00-ff]
[    0.328072] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.328074] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.328076] pnp 00:00: [io  0x0d00-0xffff window]
[    0.328078] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.328080] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.328082] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.328084] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.328086] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.328088] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.328090] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.328092] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.328094] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.328096] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.328098] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.328100] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.328102] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.328104] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.328107] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.328188] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.328207] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.328209] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.328280] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.328284] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.328295] pnp 00:02: [io  0x0300-0x031f]
[    0.328306] pnp 00:02: [irq 6]
[    0.328332] pnp 00:02: Plug and Play ACPI device, IDs APP0001 (active)
[    0.328343] pnp 00:03: [io  0x0000-0x0008]
[    0.328345] pnp 00:03: [io  0x000a-0x000f]
[    0.328347] pnp 00:03: [io  0x0081-0x0083]
[    0.328349] pnp 00:03: [io  0x0087]
[    0.328351] pnp 00:03: [io  0x0089-0x008b]
[    0.328352] pnp 00:03: [io  0x008f]
[    0.328354] pnp 00:03: [io  0x00c0-0x00d1]
[    0.328356] pnp 00:03: [io  0x00d4-0x00df]
[    0.328358] pnp 00:03: [dma 4]
[    0.328380] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.328451] pnp 00:04: [irq 0 disabled]
[    0.328460] pnp 00:04: [irq 8]
[    0.328462] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.328510] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.328514] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.328524] pnp 00:05: [io  0x00f0-0x00f1]
[    0.328529] pnp 00:05: [irq 13]
[    0.328559] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.328660] pnp 00:06: [io  0x0400-0x047f]
[    0.328662] pnp 00:06: [io  0x0480-0x04ff]
[    0.328663] pnp 00:06: [io  0x0500-0x057f]
[    0.328665] pnp 00:06: [io  0x0580-0x05ff]
[    0.328667] pnp 00:06: [io  0x0800-0x087f]
[    0.328669] pnp 00:06: [io  0x0880-0x08ff]
[    0.328670] pnp 00:06: [io  0x0010-0x001f]
[    0.328672] pnp 00:06: [io  0x0022-0x003f]
[    0.328674] pnp 00:06: [io  0x0044-0x005f]
[    0.328675] pnp 00:06: [io  0x0063]
[    0.328677] pnp 00:06: [io  0x0065]
[    0.328679] pnp 00:06: [io  0x0067-0x006f]
[    0.328681] pnp 00:06: [io  0x0072-0x0073]
[    0.328682] pnp 00:06: [io  0x0074-0x007f]
[    0.328684] pnp 00:06: [io  0x0091-0x0093]
[    0.328686] pnp 00:06: [io  0x0097-0x009f]
[    0.328688] pnp 00:06: [io  0x00a2-0x00bf]
[    0.328690] pnp 00:06: [io  0x00e0-0x00ef]
[    0.328691] pnp 00:06: [io  0x04d0-0x04d1]
[    0.328693] pnp 00:06: [io  0x0080]
[    0.328695] pnp 00:06: [io  0x0295-0x0296]
[    0.328705] pnp 00:06: disabling [io  0x0010-0x001f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328708] pnp 00:06: disabling [io  0x0022-0x003f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328711] pnp 00:06: disabling [io  0x0044-0x005f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328714] pnp 00:06: disabling [io  0x0063] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328717] pnp 00:06: disabling [io  0x0065] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328720] pnp 00:06: disabling [io  0x0067-0x006f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328723] pnp 00:06: disabling [io  0x0072-0x0073] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328726] pnp 00:06: disabling [io  0x0074-0x007f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328729] pnp 00:06: disabling [io  0x0091-0x0093] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328732] pnp 00:06: disabling [io  0x0097-0x009f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328735] pnp 00:06: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328738] pnp 00:06: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328741] pnp 00:06: disabling [io  0x0080] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.328788] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.328791] system 00:06: [io  0x0480-0x04ff] has been reserved
[    0.328794] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.328796] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.328798] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.328800] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.328803] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.328806] system 00:06: [io  0x0295-0x0296] has been reserved
[    0.328809] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.328817] pnp 00:07: [io  0x0070-0x0077]
[    0.328842] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.329325] pnp: PnP ACPI: found 8 devices
[    0.329326] ACPI: ACPI bus type pnp unregistered
[    0.335624] PCI: max bus depth: 2 pci_try_num: 3
[    0.335716] pci 0000:00:03.2: BAR 0: assigned [io  0x2000-0x20ff]
[    0.335721] pci 0000:00:03.2: BAR 0: set to [io  0x2000-0x20ff] (PCI address [0x2000-0x20ff])
[    0.335725] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.335732] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.335742] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.335754] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.335774] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.335786] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.335806] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.335818] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.335826] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.335841] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.335844] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.335847] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.335851] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.336035] ACPI: PCI Interrupt Link [Z00B] enabled at IRQ 23
[    0.336047] pci 0000:00:0e.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    0.336058] pci 0000:00:0e.0: setting latency timer to 64
[    0.336070] pci 0000:01:00.0: setting latency timer to 64
[    0.336096] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.336103] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.336219] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
[    0.336226] pci 0000:00:15.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.336235] pci 0000:00:15.0: setting latency timer to 64
[    0.336353] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 21
[    0.336360] pci 0000:00:16.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    0.336370] pci 0000:00:16.0: setting latency timer to 64
[    0.336378] pci 0000:00:17.0: setting latency timer to 64
[    0.336382] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.336384] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.336386] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.336389] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.336391] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.336393] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.336395] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.336397] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.336399] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.336401] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.336403] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.336405] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.336408] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.336410] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.336412] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.336414] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.336416] pci_bus 0000:00: resource 20 [mem 0xc0000000-0xfebfffff]
[    0.336419] pci_bus 0000:01: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.336422] pci_bus 0000:02: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.336425] pci_bus 0000:03: resource 1 [mem 0xd3300000-0xd33fffff]
[    0.336428] pci_bus 0000:04: resource 1 [mem 0xd3200000-0xd32fffff]
[    0.336431] pci_bus 0000:04: resource 2 [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.336434] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.336437] pci_bus 0000:05: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.336440] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.336482] NET: Registered protocol family 2
[    0.336624] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.337753] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.341614] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.342109] TCP: Hash tables configured (established 524288 bind 65536)
[    0.342112] TCP reno registered
[    0.342122] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.342162] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.342289] NET: Registered protocol family 1
[    0.342465] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.342470] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.342598] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    0.342615] pci 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.407792] Freeing initrd memory: 13572k freed
[    0.412093] pci 0000:00:04.0: PCI INT A disabled
[    0.412224] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.412229] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.412398] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    0.412433] pci 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.412493] pci 0000:00:04.1: PCI INT B disabled
[    0.412525] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.412529] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.412647] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 18
[    0.412656] pci 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.468028] pci 0000:00:06.0: PCI INT A disabled
[    0.468076] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.468081] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.468202] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 17
[    0.468214] pci 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.468240] pci 0000:00:06.1: PCI INT B disabled
[    0.468439] PCI: CLS mismatch (256 != 64), using 64 bytes
[    0.468451] pci 0000:05:00.0: Boot video device
[    0.468455] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.468457] Placing 64MB software IO TLB between ffff8800ab000000 - ffff8800af000000
[    0.468459] software IO TLB at phys 0xab000000 - 0xaf000000
[    0.468850] audit: initializing netlink socket (disabled)
[    0.468864] type=2000 audit(1338431284.464:1): initialized
[    0.499732] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.520926] VFS: Disk quotas dquot_6.5.2
[    0.520984] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.521487] fuse init (API version 7.17)
[    0.521583] msgmni has been set to 7376
[    0.521963] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.521992] io scheduler noop registered
[    0.521995] io scheduler deadline registered
[    0.522031] io scheduler cfq registered (default)
[    0.522181] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.522334] pcieport 0000:00:0e.0: irq 40 for MSI/MSI-X
[    0.522510] pcieport 0000:00:15.0: setting latency timer to 64
[    0.522656] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.522830] pcieport 0000:00:16.0: setting latency timer to 64
[    0.522976] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.523180] pcieport 0000:00:0e.0: Signaling PME through PCIe PME interrupt
[    0.523183] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.523185] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.523193] pcie_pme 0000:00:0e.0:pcie01: service driver pcie_pme loaded
[    0.523231] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.523233] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.523242] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.523281] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
[    0.523284] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.523286] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.523295] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
[    0.523312] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.523334] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.523389] efifb: dmi detected Macmini4,1 - framebuffer at 0xd1000000 (640x480, stride 2560)
[    0.523392] intel_idle: MWAIT substates: 0x3122220
[    0.523393] intel_idle: does not run on family 6 model 23
[    0.523479] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.523484] ACPI: Power Button [PWRB]
[    0.523529] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.523532] ACPI: Sleep Button [SLPB]
[    0.523592] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.523595] ACPI: Power Button [PWRF]
[    0.523753] Monitor-Mwait will be used to enter C-1 state
[    0.523780] Monitor-Mwait will be used to enter C-2 state
[    0.523807] Monitor-Mwait will be used to enter C-3 state
[    0.523813] Marking TSC unstable due to TSC halts in idle
[    0.523828] ACPI: acpi_idle registered with cpuidle
[    0.525298] ERST: Table is not found!
[    0.525300] GHES: HEST is not enabled!
[    0.525374] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.644350] Linux agpgart interface v0.103
[    0.645815] brd: module loaded
[    0.646573] loop: module loaded
[    0.646696] ahci 0000:00:0a.0: version 3.0
[    0.646793] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.646797] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.646919] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 16
[    0.646930] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.646954] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    0.646965] pata_acpi 0000:00:0a.0: PCI INT A disabled
[    0.646993] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.646996] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.647001] ata_generic 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.647015] ata_generic 0000:00:0a.0: setting latency timer to 64
[    0.647304] scsi0 : ata_generic
[    0.647385] scsi1 : ata_generic
[    0.647496] ata1: PATA max UDMA/100 cmd 0x2298 ctl 0x22a4 bmdma 0x2280 irq 16
[    0.647499] ata2: PATA max UDMA/100 cmd 0x2290 ctl 0x22a0 bmdma 0x2288 irq 16
[    0.647779] Fixed MDIO Bus: probed
[    0.647798] tun: Universal TUN/TAP device driver, 1.6
[    0.647799] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.647895] PPP generic driver version 2.4.2
[    0.647994] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.648023] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.648027] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.648033] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.648053] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.648056] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.648097] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.648112] ehci_hcd 0000:00:04.1: disable lpm/ppcd for nvidia mcp89
[    0.648118] ehci_hcd 0000:00:04.1: debug port 1
[    0.672017] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.672031] ehci_hcd 0000:00:04.1: irq 19, io mem 0xd358b100
[    0.684017] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.10
[    0.684144] hub 1-0:1.0: USB hub found
[    0.684149] hub 1-0:1.0: 6 ports detected
[    0.684221] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.684224] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.684230] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.684241] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.684244] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.684290] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.684303] ehci_hcd 0000:00:06.1: disable lpm/ppcd for nvidia mcp89
[    0.684308] ehci_hcd 0000:00:06.1: debug port 1
[    0.708018] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.708032] ehci_hcd 0000:00:06.1: irq 17, io mem 0xd358b000
[    0.720017] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.10
[    0.720124] hub 2-0:1.0: USB hub found
[    0.720128] hub 2-0:1.0: 6 ports detected
[    0.720200] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.720212] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.720216] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.720221] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.720232] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.720235] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.720279] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.720300] ohci_hcd 0000:00:04.0: irq 20, io mem 0xd358a000
[    0.778103] hub 3-0:1.0: USB hub found
[    0.778108] hub 3-0:1.0: 6 ports detected
[    0.778176] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.778180] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.778185] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.778196] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.778199] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.778249] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.778268] ohci_hcd 0000:00:06.0: irq 18, io mem 0xd3589000
[    0.808210] ata1.00: ATA-8: SAMSUNG HN-M101MBB, 2AR10001, max UDMA/133
[    0.808213] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.808217] ata1.00: configured for UDMA/133
[    0.808324] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M101M 2AR1 PQ: 0 ANSI: 5
[    0.808453] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.808456] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.808500] sd 0:0:0:0: [sda] Write Protect is off
[    0.808503] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.808522] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.834167] hub 4-0:1.0: USB hub found
[    0.834173] hub 4-0:1.0: 6 ports detected
[    0.834243] uhci_hcd: USB Universal Host Controller Interface driver
[    0.834299] usbcore: registered new interface driver libusual
[    0.834332] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.835187] i8042: No controller found
[    0.835271] mousedev: PS/2 mouse device common for all mice
[    0.835455] rtc_cmos 00:07: RTC can wake from S4
[    0.835657] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.835707] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.835778] device-mapper: uevent: version 1.0.3
[    0.835855] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.835917] cpuidle: using governor ladder
[    0.835997] cpuidle: using governor menu
[    0.836000] EFI Variables Facility v0.08 2004-May-17
[    0.836235] TCP cubic registered
[    0.836338] NET: Registered protocol family 10
[    0.836763] NET: Registered protocol family 17
[    0.836780] Registering the dns_resolver key type
[    0.836971] PM: Hibernation image not present or could not be loaded.
[    0.836986] registered taskstats version 1
[    0.852553]   Magic number: 12:458:461
[    0.852705] rtc_cmos 00:07: setting system clock to 2012-05-31 02:28:05 UTC (1338431285)
[    0.853125] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.853127] EDD information not available.
[    0.864641]  sda: sda1 sda2 sda3 sda4 sda5 sda6
[    0.865397] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.964252] ata2.01: NODEV after polling detection
[    0.972227] ata2.00: ATAPI: HL-DT-STDVDRW  GA32N, KC08, max UDMA/100
[    0.972231] ata2.00: configured for UDMA/100
[    0.975047] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRW  GA32N     KC08 PQ: 0 ANSI: 5
[    0.979121] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.979124] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.979283] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.979382] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.981005] Freeing unused kernel memory: 920k freed
[    0.981262] Write protecting the kernel read-only data: 12288k
[    0.986505] Freeing unused kernel memory: 1608k freed
[    0.990803] Freeing unused kernel memory: 1196k freed
[    1.005910] udevd[94]: starting version 175
[    1.083150] sdhci: Secure Digital Host Controller Interface driver
[    1.083153] sdhci: Copyright(c) Pierre Ossman
[    1.083425] sdhci-pci 0000:04:00.1: SDHCI controller found [14e4:16bc] (rev 0)
[    1.083603] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 23
[    1.083608] sdhci-pci 0000:04:00.1: PCI INT B -> Link[Z00O] -> GSI 23 (level, low) -> IRQ 23
[    1.083612] sdhci-pci 0000:04:00.1: Invalid iomem size. You may experience problems.
[    1.083665] sdhci-pci 0000:04:00.1: setting latency timer to 64
[    1.083690] mmc0: no vmmc regulator found
[    1.083719] Registered led device: mmc0::
[    1.089244] mmc0: SDHCI controller on PCI [0000:04:00.1] using ADMA
[    1.089446] tg3.c:v3.121 (November 2, 2011)
[    1.089463] tg3 0000:04:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    1.089473] tg3 0000:04:00.0: setting latency timer to 64
[    1.095248] firewire_ohci 0000:02:00.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    1.100521] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM957765) rev 57785000] (PCI Express) MAC address c4:2c:03:03:07:cb
[    1.100526] tg3 0000:04:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.100529] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.100531] tg3 0000:04:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    1.148113] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x2
[    1.248107] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.264544] mmc0: new high speed SDHC card at address e624
[    1.266235] mmcblk0: mmc0:e624 SD32G 29.7 GiB 
[    1.278538]  mmcblk0: p1 p2 < p5 >
[    1.394207] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.648238] firewire_core: created device fw0: GUID e80688fffeafd696, S800
[    1.692140] usb 2-4: new high-speed USB device number 3 using ehci_hcd
[    2.384065] usb 4-2: new full-speed USB device number 2 using ohci_hcd
[    2.916044] usb 4-5: new low-speed USB device number 3 using ohci_hcd
[    3.440100] usb 4-6: new full-speed USB device number 4 using ohci_hcd
[    3.665153] hub 4-6:1.0: USB hub found
[    3.668053] hub 4-6:1.0: 3 ports detected
[    3.974116] usb 4-6.1: new full-speed USB device number 5 using ohci_hcd
[    4.086302] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.106872] udevd[328]: starting version 175
[    4.145247] lp: driver loaded but no devices found
[    4.166051] usb 4-6.2: new full-speed USB device number 6 using ohci_hcd
[    4.172861] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.207788] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.207794] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.207930] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[    4.207935] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[    4.207938] hda_intel: Disabling MSI
[    4.207941] hda_intel: position_fix set to 1 for device 10de:cb89
[    4.207988] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[    4.232840] Adding 3922760k swap on /dev/sda5.  Priority:-1 extents:1 across:3922760k 
[    4.258456] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    4.258623] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:31/LNXVIDEO:00/input/input3
[    4.258805] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    4.259162] wmi: Mapper loaded
[    4.263813] [drm] Initialized drm 1.1.0 20060810
[    4.314755] Compat-wireless backport release: compat-wireless-2012-05-04
[    4.314757] Backport based on linux-next.git next-20120510
[    4.325951] cfg80211: Calling CRDA to update world regulatory domain
[    4.346453] tg3 0000:04:00.0: irq 43 for MSI/MSI-X
[    4.346458] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[    4.346463] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[    4.475754] cfg80211: World regulatory domain updated:
[    4.475757] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.475760] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.475762] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.475765] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.475767] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.475770] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.592878] applesmc: key=215 fan=1 temp=29 acc=0 lux=0 kbd=0
[    4.634776] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.638237] usb 4-6.3: new full-speed USB device number 7 using ohci_hcd
[    4.780849] Bluetooth: Core ver 2.16
[    4.780871] NET: Registered protocol family 31
[    4.780873] Bluetooth: HCI device and connection manager initialized
[    4.780875] Bluetooth: HCI socket layer initialized
[    4.780877] Bluetooth: L2CAP socket layer initialized
[    4.781431] Bluetooth: SCO socket layer initialized
[    4.782139] usbcore: registered new interface driver btusb
[    4.804062] usb 4-6.1: USB disconnect, device number 5
[    4.805150] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input4
[    4.805305] generic-usb 0003:04D9:1203.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:04.0-1/input0
[    4.827135] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.1/input/input5
[    4.827350] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:04.0-1/input1
[    4.831349] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2:1.0/input/input6
[    4.831599] generic-usb 0003:046D:C531.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:06.0-2/input0
[    4.846204] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2:1.1/input/input7
[    4.847370] generic-usb 0003:046D:C531.0004: input,hiddev0,hidraw3: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:06.0-2/input1
[    4.860051] generic-usb: probe of 0003:05AC:820B.0006 failed with error -62
[    4.860084] usbcore: registered new interface driver usbhid
[    4.860086] usbhid: USB HID core driver
[    4.862293] apple 0003:05AC:8242.0005: hiddev0,hidraw4: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:06.0-5/input0
[    4.940051] usb 4-6.2: USB disconnect, device number 6
[    5.004048] usb 2-4: reset high-speed USB device number 3 using ehci_hcd
[    5.209422] usbcore: registered new interface driver carl9170
[    5.267506] usb 2-4: driver   API: 1.9.4 2011-08-15 [1-1]
[    5.267509] usb 2-4: firmware API: 1.9.4 2011-06-30
[    5.267512] usb 2-4: Unprotected firmware image.
[    5.523543] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    5.655338] ath: EEPROM regdomain: 0x80d0
[    5.655342] ath: EEPROM indicates we should expect a country code
[    5.655345] ath: doing EEPROM country->regdmn map search
[    5.655348] ath: country maps to regdmn code: 0x37
[    5.655350] ath: Country alpha2 being used: DK
[    5.655353] ath: Regpair used: 0x37
[    5.655357] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.655362] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655365] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.655369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655372] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.655376] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655379] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.655383] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655386] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.655390] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655394] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.655398] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655401] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.655405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655408] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.655412] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655420] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.655422] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655424] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.655427] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655429] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.655432] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.655434] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655436] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655438] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655441] cfg80211: Disabling freq 4920 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655443] cfg80211: Disabling freq 4940 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655445] cfg80211: Disabling freq 4960 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655447] cfg80211: Disabling freq 4980 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655449] cfg80211: Disabling freq 5040 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655451] cfg80211: Disabling freq 5060 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655454] cfg80211: Disabling freq 5080 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655456] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[    5.655458] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655460] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[    5.655463] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655465] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[    5.655468] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655470] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[    5.655473] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655475] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[    5.655477] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655479] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[    5.655482] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655484] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[    5.655487] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655489] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[    5.655492] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655494] cfg80211: Disabling freq 5500 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655496] cfg80211: Disabling freq 5520 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655498] cfg80211: Disabling freq 5540 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655500] cfg80211: Disabling freq 5560 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655502] cfg80211: Disabling freq 5580 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655504] cfg80211: Disabling freq 5600 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655507] cfg80211: Disabling freq 5620 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655509] cfg80211: Disabling freq 5640 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655511] cfg80211: Disabling freq 5660 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655513] cfg80211: Disabling freq 5680 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655515] cfg80211: Disabling freq 5700 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.655517] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[    5.655520] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655522] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[    5.655525] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655527] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[    5.655529] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655532] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[    5.655534] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655536] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[    5.655539] cfg80211: 5715000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655541] cfg80211: Updating information on frequency 5170 MHz for a 20 MHz width channel with regulatory rule:
[    5.655544] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655546] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[    5.655548] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655550] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[    5.655553] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655555] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[    5.655558] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[    5.655610] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.655613] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655615] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.655618] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655620] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.655623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655625] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.655628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655630] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.655632] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655634] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.655637] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655639] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.655642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655644] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.655647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655649] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.655651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655654] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.655656] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655658] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.655661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655663] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.655666] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.655668] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.655671] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.655673] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    5.655676] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.655678] cfg80211: Disabling freq 4920 MHz
[    5.655679] cfg80211: Disabling freq 4940 MHz
[    5.655681] cfg80211: Disabling freq 4960 MHz
[    5.655682] cfg80211: Disabling freq 4980 MHz
[    5.655684] cfg80211: Disabling freq 5040 MHz
[    5.655685] cfg80211: Disabling freq 5060 MHz
[    5.655687] cfg80211: Disabling freq 5080 MHz
[    5.655689] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[    5.655691] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655693] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[    5.655696] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655698] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[    5.655701] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655703] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[    5.655706] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655708] cfg80211: Disabling freq 5260 MHz
[    5.655709] cfg80211: Disabling freq 5280 MHz
[    5.655711] cfg80211: Disabling freq 5300 MHz
[    5.655712] cfg80211: Disabling freq 5320 MHz
[    5.655714] cfg80211: Disabling freq 5500 MHz
[    5.655715] cfg80211: Disabling freq 5520 MHz
[    5.655717] cfg80211: Disabling freq 5540 MHz
[    5.655718] cfg80211: Disabling freq 5560 MHz
[    5.655720] cfg80211: Disabling freq 5580 MHz
[    5.655721] cfg80211: Disabling freq 5600 MHz
[    5.655722] cfg80211: Disabling freq 5620 MHz
[    5.655724] cfg80211: Disabling freq 5640 MHz
[    5.655725] cfg80211: Disabling freq 5660 MHz
[    5.655727] cfg80211: Disabling freq 5680 MHz
[    5.655728] cfg80211: Disabling freq 5700 MHz
[    5.655730] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[    5.655733] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655735] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[    5.655738] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655740] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[    5.655742] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655745] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[    5.655747] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655749] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[    5.655752] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655754] cfg80211: Disabling freq 5170 MHz
[    5.655756] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[    5.655758] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655761] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[    5.655763] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.655765] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[    5.655768] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.685343] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    5.686598] cfg80211: Calling CRDA for country: DK
[    5.687038] Registered led device: carl9170-phy0::tx
[    5.687061] Registered led device: carl9170-phy0::assoc
[    5.689139] usb 2-4: Atheros AR9170 is registered as 'phy0'
[    5.690541] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.690545] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690547] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.690550] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690552] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.690555] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690557] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.690559] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690561] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.690564] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690566] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.690568] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690570] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.690573] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690575] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.690578] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690580] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.690582] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690584] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.690587] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690589] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.690592] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690594] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.690596] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690598] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.690601] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690603] cfg80211: Disabling freq 2484 MHz
[    5.690604] cfg80211: Disabling freq 4920 MHz
[    5.690606] cfg80211: Disabling freq 4940 MHz
[    5.690607] cfg80211: Disabling freq 4960 MHz
[    5.690609] cfg80211: Disabling freq 4980 MHz
[    5.690610] cfg80211: Disabling freq 5040 MHz
[    5.690611] cfg80211: Disabling freq 5060 MHz
[    5.690613] cfg80211: Disabling freq 5080 MHz
[    5.690615] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[    5.690617] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690619] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[    5.690622] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690624] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[    5.690626] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690628] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[    5.690631] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690633] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[    5.690636] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690638] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[    5.690640] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690642] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[    5.690645] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690647] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[    5.690650] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690652] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[    5.690654] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690656] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[    5.690659] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690661] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[    5.690664] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690666] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[    5.690668] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690670] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[    5.690673] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690675] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[    5.690678] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690680] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[    5.690683] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690684] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[    5.690687] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690689] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[    5.690692] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690694] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[    5.690696] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690698] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[    5.690701] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[    5.690703] cfg80211: Disabling freq 5745 MHz
[    5.690704] cfg80211: Disabling freq 5765 MHz
[    5.690706] cfg80211: Disabling freq 5785 MHz
[    5.690707] cfg80211: Disabling freq 5805 MHz
[    5.690708] cfg80211: Disabling freq 5825 MHz
[    5.690710] cfg80211: Disabling freq 5170 MHz
[    5.690712] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[    5.690714] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690716] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[    5.690719] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690721] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[    5.690723] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.690729] cfg80211: Regulatory domain changed to country: DK
[    5.690730] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.690733] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    5.690735] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    5.690737] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    5.690739] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[    5.768118] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.792054] HDMI status: Codec=4 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.816037] HDMI status: Codec=5 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.816145] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:08.0/sound/card0/input8
[    5.816276] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:08.0/sound/card0/input9
[    5.816380] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[    5.816484] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[    5.836520] udevd[337]: renamed network interface wlan0 to wlan1
[    5.883324] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    5.883327] vesafb: scrolling: redraw
[    5.883329] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    5.885233] vesafb: framebuffer at 0xd1000000, mapped to 0xffffc90001c80000, using 1216k, total 1216k
[    5.885366] Console: switching to colour frame buffer device 80x30
[    5.885377] fb0: VESA VGA frame buffer device
[    5.922739] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    7.037834] tg3 0000:04:00.0: eth0: Link is up at 1000 Mbps, full duplex
[    7.037838] tg3 0000:04:00.0: eth0: Flow control is on for TX and on for RX
[    7.038232] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    7.685165] init: failsafe main process (695) killed by TERM signal
[   17.792040] eth0: no IPv6 routers present
[  119.635478] bcma-pci-bridge 0000:03:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[  119.635491] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[  119.635527] bcma: Found chip with id 0xA8D8, rev 0x01 and package 0x08
[  119.635548] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[  119.635567] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[  119.635606] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[  119.704242] bcma: Bus registered
[  119.708575] b43-phy1: Broadcom 43224 WLAN found (core revision 23)
[  119.709453] Broadcom 43xx driver loaded [ Features: PMNLS ]
[  119.713878] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  119.713882] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713884] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  119.713887] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713889] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  119.713892] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713894] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  119.713897] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713899] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  119.713901] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713903] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  119.713906] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713908] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  119.713911] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713913] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  119.713915] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713918] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  119.713920] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713922] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  119.713925] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713927] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  119.713930] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713932] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  119.713935] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713937] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  119.713939] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  119.713942] cfg80211: Disabling freq 2484 MHz
[  119.714036] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'

```

My iw list:

```
Wiphy phy1
    Band 1:
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (disabled)
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 4
    max scan IEs length: 2285 bytes
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * WDS
         * monitor
         * mesh point
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    interface combinations are not supported
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * set_tx_bitrate_mask
         * action
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * Unknown command (84)
         * Unknown command (87)
         * Unknown command (85)
         * testmode
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * managed: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP/VLAN: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * mesh point: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-client: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-GO: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
    Supported RX frame types:
         * IBSS: 0x00d0
         * managed: 0x0040 0x00d0
         * AP: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * AP/VLAN: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * mesh point: 0x00b0 0x00c0 0x00d0
         * P2P-client: 0x0040 0x00d0
         * P2P-GO: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
    Device supports RSN-IBSS.

```

my iwconfig:

```
root@Wurzelpeter:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

eth0      no wireless extensions.

```

Thanks for your time, reading this!
derdigge
[/INDENT]

---

### Post by chili555 on 2012-05-31
> compat                 13447  8 [COLOR="Red"]b43[/COLOR],[COLOR="Red"]bcma[/COLOR],ssbYou have two possibly conflicting drivers at work here. That may be why it doesn't perform as expected. I don't know for sure which is best for your device. I think I'd try blacklisting b43 and reboot. See if bcma drives your device correctly. If not, unblacklist b43 and blacklist bcma. Once you have the probable conflict resolved, only then can you work on N speeds.

Some of the boys in the back room and I were chatting last evening and we know, so far, of no case where bcma works at all; however:> root@Wurzelpeter:~# lspci -vnn -d 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
        <snip>
        Kernel driver in use: bcma-pci-bridge
        [COLOR="Red"]Kernel modules: bcma[/COLOR]You seem pretty capable so I have not explained every step in detail. However, if you'd like the details, post back and I'll be happy to help.

---

### Post by derdigge on 2012-05-31
Thanks for taking the time!

I tried to blacklist bcma, so then b43 also did not come up:
```
root@Wurzelpeter:~# lsmod
Module                  Size  Used by
vesafb                 13844  1
nouveau               774571  0
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
snd_hda_codec_hdmi     32474  3
snd_hda_codec_cirrus    23965  1
applesmc               19554  0
input_polldev          13896  1 applesmc
btusb                  18291  0
hid_apple              13375  0
bluetooth             204548  2 btusb
compat                 13447  2 btusb,bluetooth
video                  19596  1 nouveau
shpchp                 37277  0
snd_hda_intel          33773  0
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29990  1 snd_pcm
snd                    78855  7 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
mac_hid                13253  0
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  1 lp
usbhid                 47199  0
hid                    99559  2 hid_apple,usbhid
mmc_block              27300  0
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0
tg3                   152032  0
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
```also it did not show in dmesg (grp´d it but nothing, so the full story):
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 0000000000090000 (reserved)
[    0.000000]  BIOS-e820: 0000000000090000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000af000000 (usable)
[    0.000000]  BIOS-e820: 00000000af000000 - 00000000bf000000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf000000 - 00000000bf70f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf930000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf930000 - 00000000bf931000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf931000 - 00000000bf939000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf939000 - 00000000bfef9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d3500000 - 00000000d3501000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Apple Inc. Macmini4,1/Mac-F2208EC8, BIOS     MM41.88Z.0042.B00.1004221740 04/22/10
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf70f max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf70f000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf70f000 page 4k
[    0.000000] kernel direct mapping tables up to bf70f000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf709000-bf70f000
[    0.000000] RAMDISK: 3656e000 - 372af000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
[    0.000000] ACPI: XSDT 00000000bf96a1c0 00084 (v01 APPLE   Apple00 00000042      01000013)
[    0.000000] ACPI: FACP 00000000bf968000 000F4 (v04 APPLE   Apple00 00000042 Loki 0000005F)
[    0.000000] ACPI: DSDT 00000000bf95b000 054A1 (v01 APPLE   Macmini 00040001 INTL 20061109)
[    0.000000] ACPI: FACS 00000000bf71e000 00040
[    0.000000] ACPI: HPET 00000000bf967000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf966000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf965000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 00000000bf963000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 00000000bf962000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 00000000bf961000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf957000 00024 (v01 APPLE     Apple 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf956000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: MCFG 00000000bf964000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf95a000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf959000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b800000-ffff88013f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000008f
[    0.000000]     0: 0x00000090 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000af000
[    0.000000]     0: 0x000bf000 -> 0x000bf70f
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 980637
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 698191 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 0000000000090000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000af000000 - 00000000bf000000
[    0.000000] PM: Registered nosave memory: 00000000bf70f000 - 00000000bf930000
[    0.000000] PM: Registered nosave memory: 00000000bf930000 - 00000000bf931000
[    0.000000] PM: Registered nosave memory: 00000000bf931000 - 00000000bf939000
[    0.000000] PM: Registered nosave memory: 00000000bf939000 - 00000000bfef9000
[    0.000000] PM: Registered nosave memory: 00000000bfef9000 - 00000000bfeff000
[    0.000000] PM: Registered nosave memory: 00000000bfeff000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000d3500000
[    0.000000] PM: Registered nosave memory: 00000000d3500000 - 00000000d3501000
[    0.000000] PM: Registered nosave memory: 00000000d3501000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d3501000 (gap: d3501000:1caff000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s83072 r8192 d23424 u1048576
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 960152
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3763376k/5242880k available (6566k kernel code, 1320332k absent, 159172k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2389.227 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4778.45 BogoMIPS (lpj=9556908)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004055] Yama: becoming mindful.
[    0.004444] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009710] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010610] Mount-cache hash table entries: 256
[    0.010757] Initializing cgroup subsys cpuacct
[    0.010762] Initializing cgroup subsys memory
[    0.010773] Initializing cgroup subsys devices
[    0.010775] Initializing cgroup subsys freezer
[    0.010778] Initializing cgroup subsys blkio
[    0.010784] Initializing cgroup subsys perf_event
[    0.010816] CPU: Physical Processor ID: 0
[    0.010817] CPU: Processor Core ID: 0
[    0.010820] mce: CPU supports 6 MCE banks
[    0.010829] CPU0: Thermal monitoring enabled (TM2)
[    0.010834] using mwait in idle threads.
[    0.013495] ACPI: Core revision 20110623
[    0.017713] ftrace: allocating 27049 entries in 107 pages
[    0.020511] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061638] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.152037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152077] Brought up 2 CPUs
[    0.152079] Total of 2 processors activated (9556.84 BogoMIPS).
[    0.153974] devtmpfs: initialized
[    0.153974] EVM: security.selinux
[    0.153974] EVM: security.SMACK64
[    0.153974] EVM: security.capability
[    0.153974] PM: Registering ACPI NVS region at bf70f000 (2232320 bytes)
[    0.153974] PM: Registering ACPI NVS region at bf931000 (32768 bytes)
[    0.153974] print_constraints: dummy: 
[    0.153974] RTC time: 12:48:38, date: 05/31/12
[    0.153974] NET: Registered protocol family 16
[    0.156065] Trying to unpack rootfs image as initramfs...
[    0.156119] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.156122] ACPI: bus type pci registered
[    0.156389] PCI: MMCONFIG for domain 0000 [bus 00-05] at [mem 0xf0000000-0xf05fffff] (base 0xf0000000)
[    0.156392] PCI: MMCONFIG at [mem 0xf0000000-0xf05fffff] reserved in E820
[    0.157754] PCI: Using configuration type 1 for base access
[    0.172147] bio: create slab <bio-0> at 0
[    0.172204] ACPI: Added _OSI(Module Device)
[    0.172207] ACPI: Added _OSI(Processor Device)
[    0.172209] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172211] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173547] ACPI: EC: EC description table is found, configuring boot EC
[    0.176033] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.176330] ACPI: SSDT 00000000bf71dc98 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176627] ACPI: Dynamic OEM Table Load:
[    0.176630] ACPI: SSDT           (null) 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176738] ACPI: SSDT 00000000bf71c618 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.177022] ACPI: Dynamic OEM Table Load:
[    0.177025] ACPI: SSDT           (null) 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.244258] ACPI: SSDT 00000000bf71df18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244556] ACPI: Dynamic OEM Table Load:
[    0.244559] ACPI: SSDT           (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244638] ACPI: SSDT 00000000bf71bf18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.244922] ACPI: Dynamic OEM Table Load:
[    0.244924] ACPI: SSDT           (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.284214] ACPI: Interpreter enabled
[    0.284221] ACPI: (supports S0 S3 S4 S5)
[    0.284241] ACPI: Using IOAPIC for interrupt routing
[    0.289374] ACPI: EC: GPE = 0x57, I/O: command/status = 0x66, data = 0x62
[    0.289540] ACPI: No dock devices found.
[    0.289542] HEST: Table not found.
[    0.289546] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.289676] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.289785] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.289788] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.289791] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.289793] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.289795] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.289797] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.289800] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.289802] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.289804] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.289807] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.289809] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.289811] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.289813] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.289816] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.289818] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.289820] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[    0.289822] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.289850] pci 0000:00:00.0: [10de:0d60] type 0 class 0x000600
[    0.289968] pci 0000:00:00.1: [10de:0d68] type 0 class 0x000500
[    0.290140] pci 0000:00:01.0: [10de:0d6d] type 0 class 0x000500
[    0.290307] pci 0000:00:01.1: [10de:0d6e] type 0 class 0x000500
[    0.290472] pci 0000:00:01.2: [10de:0d6f] type 0 class 0x000500
[    0.290637] pci 0000:00:01.3: [10de:0d70] type 0 class 0x000500
[    0.290807] pci 0000:00:02.0: [10de:0d71] type 0 class 0x000500
[    0.290972] pci 0000:00:02.1: [10de:0d72] type 0 class 0x000500
[    0.291137] pci 0000:00:03.0: [10de:0d80] type 0 class 0x000601
[    0.291146] pci 0000:00:03.0: reg 10: [io  0x2100-0x21ff]
[    0.291192] pci 0000:00:03.1: [10de:0d7b] type 0 class 0x000500
[    0.291276] pci 0000:00:03.2: [10de:0d79] type 0 class 0x000c05
[    0.291292] pci 0000:00:03.2: reg 10: [io  0x0000-0x00ff]
[    0.291315] pci 0000:00:03.2: reg 20: [io  0x2240-0x227f]
[    0.291323] pci 0000:00:03.2: reg 24: [io  0x2200-0x223f]
[    0.291358] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.291364] pci 0000:00:03.2: PME# disabled
[    0.291389] pci 0000:00:03.3: [10de:0d69] type 0 class 0x000500
[    0.291595] pci 0000:00:03.4: [10de:0d7a] type 0 class 0x000b40
[    0.291616] pci 0000:00:03.4: reg 10: [mem 0xd3500000-0xd357ffff]
[    0.291759] pci 0000:00:04.0: [10de:0d9c] type 0 class 0x000c03
[    0.291771] pci 0000:00:04.0: reg 10: [mem 0xd358a000-0xd358afff]
[    0.291822] pci 0000:00:04.0: supports D1 D2
[    0.291824] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.291828] pci 0000:00:04.0: PME# disabled
[    0.291842] pci 0000:00:04.1: [10de:0d9d] type 0 class 0x000c03
[    0.291856] pci 0000:00:04.1: reg 10: [mem 0xd358b100-0xd358b1ff]
[    0.291913] pci 0000:00:04.1: supports D1 D2
[    0.291915] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.291919] pci 0000:00:04.1: PME# disabled
[    0.291942] pci 0000:00:06.0: [10de:0d9c] type 0 class 0x000c03
[    0.291954] pci 0000:00:06.0: reg 10: [mem 0xd3589000-0xd3589fff]
[    0.292004] pci 0000:00:06.0: supports D1 D2
[    0.292005] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.292009] pci 0000:00:06.0: PME# disabled
[    0.292034] pci 0000:00:06.1: [10de:0d9d] type 0 class 0x000c03
[    0.292047] pci 0000:00:06.1: reg 10: [mem 0xd358b000-0xd358b0ff]
[    0.292109] pci 0000:00:06.1: supports D1 D2
[    0.292111] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.292115] pci 0000:00:06.1: PME# disabled
[    0.292141] pci 0000:00:08.0: [10de:0d94] type 0 class 0x000403
[    0.292155] pci 0000:00:08.0: reg 10: [mem 0xd3580000-0xd3583fff]
[    0.292215] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.292219] pci 0000:00:08.0: PME# disabled
[    0.292237] pci 0000:00:0a.0: [10de:0d85] type 0 class 0x000101
[    0.292249] pci 0000:00:0a.0: reg 10: [io  0x2298-0x229f]
[    0.292255] pci 0000:00:0a.0: reg 14: [io  0x22a4-0x22a7]
[    0.292261] pci 0000:00:0a.0: reg 18: [io  0x2290-0x2297]
[    0.292268] pci 0000:00:0a.0: reg 1c: [io  0x22a0-0x22a3]
[    0.292274] pci 0000:00:0a.0: reg 20: [io  0x2280-0x228f]
[    0.292280] pci 0000:00:0a.0: reg 24: [mem 0xd3584000-0xd3585fff]
[    0.292326] pci 0000:00:0b.0: [10de:0d75] type 0 class 0x000500
[    0.292339] pci 0000:00:0b.0: reg 10: [mem 0xd3588000-0xd3588fff]
[    0.292460] pci 0000:00:0e.0: [10de:0d9a] type 1 class 0x000604
[    0.292729] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.292737] pci 0000:00:0e.0: PME# disabled
[    0.292845] pci 0000:00:15.0: [10de:0d9b] type 1 class 0x000604
[    0.293113] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.293121] pci 0000:00:15.0: PME# disabled
[    0.293222] pci 0000:00:16.0: [10de:0d9b] type 1 class 0x000604
[    0.293490] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.293498] pci 0000:00:16.0: PME# disabled
[    0.293551] pci 0000:00:17.0: [10de:0d76] type 1 class 0x000604
[    0.293592] pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
[    0.293595] pci 0000:00:17.0: PME# disabled
[    0.293811] pci 0000:01:00.0: [104c:823e] type 1 class 0x000604
[    0.293917] pci 0000:01:00.0: supports D1 D2
[    0.300046] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.300069] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.300164] pci 0000:02:00.0: [104c:823f] type 0 class 0x000c00
[    0.300188] pci 0000:02:00.0: reg 10: [mem 0xd3404000-0xd34047ff]
[    0.300202] pci 0000:02:00.0: reg 14: [mem 0xd3400000-0xd3403fff]
[    0.300298] pci 0000:02:00.0: supports D1 D2
[    0.300300] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.300305] pci 0000:02:00.0: PME# disabled
[    0.300364] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.300375] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.300617] pci 0000:03:00.0: [14e4:4353] type 0 class 0x000280
[    0.300637] pci 0000:03:00.0: reg 10: [mem 0xd3300000-0xd3303fff 64bit]
[    0.300741] pci 0000:03:00.0: supports D1 D2
[    0.300743] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.300748] pci 0000:03:00.0: PME# disabled
[    0.300805] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.300827] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.301042] pci 0000:04:00.0: [14e4:16b4] type 0 class 0x000200
[    0.301064] pci 0000:04:00.0: reg 10: [mem 0xd3100000-0xd310ffff 64bit pref]
[    0.301080] pci 0000:04:00.0: reg 18: [mem 0xd3110000-0xd311ffff 64bit pref]
[    0.301164] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.301168] pci 0000:04:00.0: PME# disabled
[    0.301209] pci 0000:04:00.1: [14e4:16bc] type 0 class 0x000805
[    0.301230] pci 0000:04:00.1: reg 10: [mem 0xd3120000-0xd312ffff 64bit pref]
[    0.301325] pci 0000:04:00.1: PME# supported from D0 D3hot D3cold
[    0.301330] pci 0000:04:00.1: PME# disabled
[    0.308049] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.308072] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.308087] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.308123] pci 0000:05:00.0: [10de:08a4] type 0 class 0x000300
[    0.308135] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.308144] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.308152] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.308158] pci 0000:05:00.0: reg 24: [io  0x1000-0x107f]
[    0.308164] pci 0000:05:00.0: reg 30: [mem 0xd3000000-0xd301ffff pref]
[    0.308217] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.308221] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.308224] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.308228] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.308280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.308508] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.308625]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.308751]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.326943] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327021] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327096] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327174] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327249] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327323] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327398] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327472] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327547] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327621] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327696] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327771] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327846] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.327920] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.327995] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.328085] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.328159] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.328238] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.328312] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.328386] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.328461] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.328539] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.328614] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.328690] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.328764] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.328839] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.328913] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
[    0.329058] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.329060] vgaarb: loaded
[    0.329062] vgaarb: bridge control possible 0000:05:00.0
[    0.329169] i2c-core: driver [aat2870] using legacy suspend method
[    0.329171] i2c-core: driver [aat2870] using legacy resume method
[    0.329239] SCSI subsystem initialized
[    0.329301] libata version 3.00 loaded.
[    0.329352] usbcore: registered new interface driver usbfs
[    0.329363] usbcore: registered new interface driver hub
[    0.329391] usbcore: registered new device driver usb
[    0.329482] PCI: Using ACPI for IRQ routing
[    0.329486] PCI: pci_cache_line_size set to 64 bytes
[    0.329648] reserve RAM buffer: 000000000008f000 - 000000000008ffff 
[    0.329651] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.329653] reserve RAM buffer: 00000000af000000 - 00000000afffffff 
[    0.329655] reserve RAM buffer: 00000000bf70f000 - 00000000bfffffff 
[    0.329757] NetLabel: Initializing
[    0.329759] NetLabel:  domain hash size = 128
[    0.329760] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.329772] NetLabel:  unlabeled traffic allowed by default
[    0.329816] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.329822] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.329827] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.332072] Switching to clocksource hpet
[    0.339871] AppArmor: AppArmor Filesystem Enabled
[    0.339905] pnp: PnP ACPI init
[    0.339926] ACPI: bus type pnp registered
[    0.340066] pnp 00:00: [bus 00-ff]
[    0.340069] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.340071] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.340073] pnp 00:00: [io  0x0d00-0xffff window]
[    0.340076] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.340078] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.340080] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.340082] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.340084] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.340086] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.340088] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.340090] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.340092] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.340094] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.340096] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.340098] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.340100] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.340102] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.340104] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.340180] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.340199] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.340201] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.340278] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.340282] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.340293] pnp 00:02: [io  0x0300-0x031f]
[    0.340306] pnp 00:02: [irq 6]
[    0.340331] pnp 00:02: Plug and Play ACPI device, IDs APP0001 (active)
[    0.340342] pnp 00:03: [io  0x0000-0x0008]
[    0.340344] pnp 00:03: [io  0x000a-0x000f]
[    0.340346] pnp 00:03: [io  0x0081-0x0083]
[    0.340347] pnp 00:03: [io  0x0087]
[    0.340349] pnp 00:03: [io  0x0089-0x008b]
[    0.340351] pnp 00:03: [io  0x008f]
[    0.340353] pnp 00:03: [io  0x00c0-0x00d1]
[    0.340355] pnp 00:03: [io  0x00d4-0x00df]
[    0.340357] pnp 00:03: [dma 4]
[    0.340379] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.340449] pnp 00:04: [irq 0 disabled]
[    0.340457] pnp 00:04: [irq 8]
[    0.340460] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.340507] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.340510] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.340520] pnp 00:05: [io  0x00f0-0x00f1]
[    0.340526] pnp 00:05: [irq 13]
[    0.340554] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.340655] pnp 00:06: [io  0x0400-0x047f]
[    0.340657] pnp 00:06: [io  0x0480-0x04ff]
[    0.340659] pnp 00:06: [io  0x0500-0x057f]
[    0.340661] pnp 00:06: [io  0x0580-0x05ff]
[    0.340663] pnp 00:06: [io  0x0800-0x087f]
[    0.340664] pnp 00:06: [io  0x0880-0x08ff]
[    0.340666] pnp 00:06: [io  0x0010-0x001f]
[    0.340668] pnp 00:06: [io  0x0022-0x003f]
[    0.340670] pnp 00:06: [io  0x0044-0x005f]
[    0.340671] pnp 00:06: [io  0x0063]
[    0.340673] pnp 00:06: [io  0x0065]
[    0.340675] pnp 00:06: [io  0x0067-0x006f]
[    0.340676] pnp 00:06: [io  0x0072-0x0073]
[    0.340678] pnp 00:06: [io  0x0074-0x007f]
[    0.340680] pnp 00:06: [io  0x0091-0x0093]
[    0.340682] pnp 00:06: [io  0x0097-0x009f]
[    0.340683] pnp 00:06: [io  0x00a2-0x00bf]
[    0.340685] pnp 00:06: [io  0x00e0-0x00ef]
[    0.340687] pnp 00:06: [io  0x04d0-0x04d1]
[    0.340688] pnp 00:06: [io  0x0080]
[    0.340690] pnp 00:06: [io  0x0295-0x0296]
[    0.340700] pnp 00:06: disabling [io  0x0010-0x001f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340703] pnp 00:06: disabling [io  0x0022-0x003f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340706] pnp 00:06: disabling [io  0x0044-0x005f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340709] pnp 00:06: disabling [io  0x0063] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340712] pnp 00:06: disabling [io  0x0065] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340715] pnp 00:06: disabling [io  0x0067-0x006f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340718] pnp 00:06: disabling [io  0x0072-0x0073] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340721] pnp 00:06: disabling [io  0x0074-0x007f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340724] pnp 00:06: disabling [io  0x0091-0x0093] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340727] pnp 00:06: disabling [io  0x0097-0x009f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340730] pnp 00:06: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340733] pnp 00:06: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340736] pnp 00:06: disabling [io  0x0080] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.340783] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.340785] system 00:06: [io  0x0480-0x04ff] has been reserved
[    0.340788] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.340790] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.340793] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.340795] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.340798] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.340801] system 00:06: [io  0x0295-0x0296] has been reserved
[    0.340804] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.340813] pnp 00:07: [io  0x0070-0x0077]
[    0.340837] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.341320] pnp: PnP ACPI: found 8 devices
[    0.341322] ACPI: ACPI bus type pnp unregistered
[    0.347608] PCI: max bus depth: 2 pci_try_num: 3
[    0.347698] pci 0000:00:03.2: BAR 0: assigned [io  0x2000-0x20ff]
[    0.347703] pci 0000:00:03.2: BAR 0: set to [io  0x2000-0x20ff] (PCI address [0x2000-0x20ff])
[    0.347707] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.347714] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.347724] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.347736] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.347757] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.347768] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.347789] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.347800] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.347808] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.347823] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.347826] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.347830] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.347833] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.347994] ACPI: PCI Interrupt Link [Z00B] enabled at IRQ 23
[    0.348025] pci 0000:00:0e.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    0.348036] pci 0000:00:0e.0: setting latency timer to 64
[    0.348048] pci 0000:01:00.0: setting latency timer to 64
[    0.348075] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.348081] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.348197] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
[    0.348204] pci 0000:00:15.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.348213] pci 0000:00:15.0: setting latency timer to 64
[    0.348333] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 21
[    0.348339] pci 0000:00:16.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    0.348349] pci 0000:00:16.0: setting latency timer to 64
[    0.348357] pci 0000:00:17.0: setting latency timer to 64
[    0.348360] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.348363] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.348365] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.348367] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.348370] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.348372] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.348374] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.348376] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.348378] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.348380] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.348382] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.348385] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.348387] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.348389] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.348391] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.348393] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.348395] pci_bus 0000:00: resource 20 [mem 0xc0000000-0xfebfffff]
[    0.348398] pci_bus 0000:01: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.348401] pci_bus 0000:02: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.348403] pci_bus 0000:03: resource 1 [mem 0xd3300000-0xd33fffff]
[    0.348406] pci_bus 0000:04: resource 1 [mem 0xd3200000-0xd32fffff]
[    0.348409] pci_bus 0000:04: resource 2 [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.348413] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.348416] pci_bus 0000:05: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.348419] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.348461] NET: Registered protocol family 2
[    0.348606] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.349705] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.353594] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.354080] TCP: Hash tables configured (established 524288 bind 65536)
[    0.354082] TCP reno registered
[    0.354092] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.354130] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.354275] NET: Registered protocol family 1
[    0.354456] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.354461] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.354590] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    0.354606] pci 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.407455] Freeing initrd memory: 13572k freed
[    0.424045] pci 0000:00:04.0: PCI INT A disabled
[    0.424117] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.424122] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.424257] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    0.424276] pci 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.424313] pci 0000:00:04.1: PCI INT B disabled
[    0.424340] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.424344] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.424454] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 18
[    0.424461] pci 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.480021] pci 0000:00:06.0: PCI INT A disabled
[    0.480052] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.480056] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.480166] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 17
[    0.480173] pci 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.480192] pci 0000:00:06.1: PCI INT B disabled
[    0.480391] PCI: CLS mismatch (256 != 64), using 64 bytes
[    0.480403] pci 0000:05:00.0: Boot video device
[    0.480407] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.480409] Placing 64MB software IO TLB between ffff8800ab000000 - ffff8800af000000
[    0.480412] software IO TLB at phys 0xab000000 - 0xaf000000
[    0.480802] audit: initializing netlink socket (disabled)
[    0.480817] type=2000 audit(1338468518.476:1): initialized
[    0.511687] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.532884] VFS: Disk quotas dquot_6.5.2
[    0.532942] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.533447] fuse init (API version 7.17)
[    0.533543] msgmni has been set to 7376
[    0.533920] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.533950] io scheduler noop registered
[    0.533952] io scheduler deadline registered
[    0.533989] io scheduler cfq registered (default)
[    0.534140] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.534294] pcieport 0000:00:0e.0: irq 40 for MSI/MSI-X
[    0.534470] pcieport 0000:00:15.0: setting latency timer to 64
[    0.534616] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.534790] pcieport 0000:00:16.0: setting latency timer to 64
[    0.534935] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.535139] pcieport 0000:00:0e.0: Signaling PME through PCIe PME interrupt
[    0.535142] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.535144] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.535153] pcie_pme 0000:00:0e.0:pcie01: service driver pcie_pme loaded
[    0.535190] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.535193] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.535201] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.535241] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
[    0.535244] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.535246] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.535254] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
[    0.535272] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.535294] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.535349] efifb: dmi detected Macmini4,1 - framebuffer at 0xd1000000 (640x480, stride 2560)
[    0.535352] intel_idle: MWAIT substates: 0x3122220
[    0.535354] intel_idle: does not run on family 6 model 23
[    0.535440] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.535445] ACPI: Power Button [PWRB]
[    0.535489] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.535493] ACPI: Sleep Button [SLPB]
[    0.535554] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.535557] ACPI: Power Button [PWRF]
[    0.535720] Monitor-Mwait will be used to enter C-1 state
[    0.535748] Monitor-Mwait will be used to enter C-2 state
[    0.535775] Monitor-Mwait will be used to enter C-3 state
[    0.535781] Marking TSC unstable due to TSC halts in idle
[    0.535796] ACPI: acpi_idle registered with cpuidle
[    0.537261] ERST: Table is not found!
[    0.537263] GHES: HEST is not enabled!
[    0.537340] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.652351] Linux agpgart interface v0.103
[    0.653818] brd: module loaded
[    0.654571] loop: module loaded
[    0.654694] ahci 0000:00:0a.0: version 3.0
[    0.654790] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.654795] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.654914] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 16
[    0.654926] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.654950] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    0.654961] pata_acpi 0000:00:0a.0: PCI INT A disabled
[    0.654989] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.654993] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.654997] ata_generic 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.655011] ata_generic 0000:00:0a.0: setting latency timer to 64
[    0.655301] scsi0 : ata_generic
[    0.655381] scsi1 : ata_generic
[    0.655491] ata1: PATA max UDMA/100 cmd 0x2298 ctl 0x22a4 bmdma 0x2280 irq 16
[    0.655494] ata2: PATA max UDMA/100 cmd 0x2290 ctl 0x22a0 bmdma 0x2288 irq 16
[    0.655776] Fixed MDIO Bus: probed
[    0.655795] tun: Universal TUN/TAP device driver, 1.6
[    0.655797] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.655893] PPP generic driver version 2.4.2
[    0.655993] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.656024] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.656028] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.656034] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.656053] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.656056] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.656099] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.656114] ehci_hcd 0000:00:04.1: disable lpm/ppcd for nvidia mcp89
[    0.656121] ehci_hcd 0000:00:04.1: debug port 1
[    0.680016] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.680031] ehci_hcd 0000:00:04.1: irq 19, io mem 0xd358b100
[    0.692017] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.10
[    0.692144] hub 1-0:1.0: USB hub found
[    0.692148] hub 1-0:1.0: 6 ports detected
[    0.692220] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.692224] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.692230] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.692241] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.692244] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.692289] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.692302] ehci_hcd 0000:00:06.1: disable lpm/ppcd for nvidia mcp89
[    0.692308] ehci_hcd 0000:00:06.1: debug port 1
[    0.716018] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.716032] ehci_hcd 0000:00:06.1: irq 17, io mem 0xd358b000
[    0.728016] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.10
[    0.728123] hub 2-0:1.0: USB hub found
[    0.728126] hub 2-0:1.0: 6 ports detected
[    0.728198] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.728210] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.728214] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.728220] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.728230] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.728233] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.728277] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.728298] ohci_hcd 0000:00:04.0: irq 20, io mem 0xd358a000
[    0.786102] hub 3-0:1.0: USB hub found
[    0.786107] hub 3-0:1.0: 6 ports detected
[    0.786175] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.786179] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.786184] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.786196] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.786198] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.786249] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.786269] ohci_hcd 0000:00:06.0: irq 18, io mem 0xd3589000
[    0.816208] ata1.00: ATA-8: SAMSUNG HN-M101MBB, 2AR10001, max UDMA/133
[    0.816211] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.816215] ata1.00: configured for UDMA/133
[    0.816321] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M101M 2AR1 PQ: 0 ANSI: 5
[    0.816452] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.816454] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.816499] sd 0:0:0:0: [sda] Write Protect is off
[    0.816501] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.816521] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.842115] hub 4-0:1.0: USB hub found
[    0.842120] hub 4-0:1.0: 6 ports detected
[    0.842188] uhci_hcd: USB Universal Host Controller Interface driver
[    0.842244] usbcore: registered new interface driver libusual
[    0.842276] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.843131] i8042: No controller found
[    0.843212] mousedev: PS/2 mouse device common for all mice
[    0.843392] rtc_cmos 00:07: RTC can wake from S4
[    0.843593] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.843643] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.843714] device-mapper: uevent: version 1.0.3
[    0.843790] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.843851] cpuidle: using governor ladder
[    0.843931] cpuidle: using governor menu
[    0.843933] EFI Variables Facility v0.08 2004-May-17
[    0.844167] TCP cubic registered
[    0.844270] NET: Registered protocol family 10
[    0.844697] NET: Registered protocol family 17
[    0.844713] Registering the dns_resolver key type
[    0.844908] PM: Hibernation image not present or could not be loaded.
[    0.844923] registered taskstats version 1
[    0.860542]   Magic number: 12:383:836
[    0.860696] rtc_cmos 00:07: setting system clock to 2012-05-31 12:48:39 UTC (1338468519)
[    0.861121] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.861123] EDD information not available.
[    0.890300]  sda: sda1 sda2 sda3 sda4 sda5 sda6
[    0.890892] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.972252] ata2.01: NODEV after polling detection
[    0.980228] ata2.00: ATAPI: HL-DT-STDVDRW  GA32N, KC08, max UDMA/100
[    0.980233] ata2.00: configured for UDMA/100
[    0.983044] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRW  GA32N     KC08 PQ: 0 ANSI: 5
[    0.987120] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.987124] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.987281] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.987384] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.989008] Freeing unused kernel memory: 920k freed
[    0.989271] Write protecting the kernel read-only data: 12288k
[    0.994530] Freeing unused kernel memory: 1608k freed
[    0.998854] Freeing unused kernel memory: 1196k freed
[    1.013908] udevd[94]: starting version 175
[    1.084539] tg3.c:v3.121 (November 2, 2011)
[    1.084558] tg3 0000:04:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    1.084567] tg3 0000:04:00.0: setting latency timer to 64
[    1.086346] firewire_ohci 0000:02:00.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    1.086983] sdhci: Secure Digital Host Controller Interface driver
[    1.086985] sdhci: Copyright(c) Pierre Ossman
[    1.096558] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM957765) rev 57785000] (PCI Express) MAC address c4:2c:03:03:07:cb
[    1.096562] tg3 0000:04:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.096566] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.096568] tg3 0000:04:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    1.096640] sdhci-pci 0000:04:00.1: SDHCI controller found [14e4:16bc] (rev 0)
[    1.096819] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 23
[    1.096824] sdhci-pci 0000:04:00.1: PCI INT B -> Link[Z00O] -> GSI 23 (level, low) -> IRQ 23
[    1.096828] sdhci-pci 0000:04:00.1: Invalid iomem size. You may experience problems.
[    1.096888] sdhci-pci 0000:04:00.1: setting latency timer to 64
[    1.096917] mmc0: no vmmc regulator found
[    1.096946] Registered led device: mmc0::
[    1.097983] mmc0: SDHCI controller on PCI [0000:04:00.1] using ADMA
[    1.140081] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x2
[    1.256065] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.276568] mmc0: new high speed SDHC card at address e624
[    1.278142] mmcblk0: mmc0:e624 SD32G 29.7 GiB 
[    1.290326]  mmcblk0: p1 p2 < p5 >
[    1.489304] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input3
[    1.489402] generic-usb 0003:04D9:1203.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:04.0-1/input0
[    1.511110] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.1/input/input4
[    1.511247] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:04.0-1/input1
[    1.511261] usbcore: registered new interface driver usbhid
[    1.511262] usbhid: USB HID core driver
[    1.630907] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.640162] firewire_core: created device fw0: GUID e80688fffeafd696, S800
[    1.960136] usb 4-5: new low-speed USB device number 2 using ohci_hcd
[    2.484052] usb 4-6: new full-speed USB device number 3 using ohci_hcd
[    2.709089] hub 4-6:1.0: USB hub found
[    2.712042] hub 4-6:1.0: 3 ports detected
[    3.018120] usb 4-6.1: new full-speed USB device number 4 using ohci_hcd
[    3.139327] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-6/4-6.1/4-6.1:1.0/input/input5
[    3.139470] generic-usb 0003:05AC:820A.0004: input,hidraw2: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-6.1/input0
[    3.214044] usb 4-6.2: new full-speed USB device number 5 using ohci_hcd
[    3.335293] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-6/4-6.2/4-6.2:1.0/input/input6
[    3.335470] generic-usb 0003:05AC:820B.0005: input,hidraw3: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-6.2/input0
[    3.410041] usb 4-6.3: new full-speed USB device number 6 using ohci_hcd
[    4.250059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.266282] udevd[342]: starting version 175
[    4.307154] lp: driver loaded but no devices found
[    4.367130] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.367136] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.367272] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[    4.367277] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[    4.367280] hda_intel: Disabling MSI
[    4.367282] hda_intel: position_fix set to 1 for device 10de:cb89
[    4.367326] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[    4.391560] Adding 3922760k swap on /dev/sda5.  Priority:-1 extents:1 across:3922760k 
[    4.413160] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    4.413321] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:31/LNXVIDEO:00/input/input7
[    4.423601] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    4.449026] Compat-wireless backport release: compat-wireless-2012-05-04
[    4.449029] Backport based on linux-next.git next-20120510
[    4.462873] Bluetooth: Core ver 2.16
[    4.462898] NET: Registered protocol family 31
[    4.462900] Bluetooth: HCI device and connection manager initialized
[    4.462902] Bluetooth: HCI socket layer initialized
[    4.462904] Bluetooth: L2CAP socket layer initialized
[    4.462910] Bluetooth: SCO socket layer initialized
[    4.463089] tg3 0000:04:00.0: irq 43 for MSI/MSI-X
[    4.463094] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[    4.463099] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[    4.463935] usbcore: registered new interface driver btusb
[    4.474965] apple 0003:05AC:8242.0003: hiddev0,hidraw4: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:06.0-5/input0
[    4.493041] usb 4-6.1: USB disconnect, device number 4
[    4.752421] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.782196] applesmc: key=215 fan=1 temp=29 acc=0 lux=0 kbd=0
[    4.802950] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    4.972044] usb 4-6.2: USB disconnect, device number 5
[    5.193979] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    5.664129] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.688125] HDMI status: Codec=4 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.712125] HDMI status: Codec=5 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.712226] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:08.0/sound/card0/input8
[    5.712364] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:08.0/sound/card0/input9
[    5.712470] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[    5.712573] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[    5.713270] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.733502] wmi: Mapper loaded
[    5.738636] [drm] Initialized drm 1.1.0 20060810
[    5.784477] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    5.784480] vesafb: scrolling: redraw
[    5.784482] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    5.786355] vesafb: framebuffer at 0xd1000000, mapped to 0xffffc90001c80000, using 1216k, total 1216k
[    5.788285] Console: switching to colour frame buffer device 80x30
[    5.788297] fb0: VESA VGA frame buffer device
[    7.171568] tg3 0000:04:00.0: eth0: Link is up at 1000 Mbps, full duplex
[    7.171571] tg3 0000:04:00.0: eth0: Flow control is on for TX and on for RX
[    7.171969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.406343] init: failsafe main process (627) killed by TERM signal
[   17.608056] eth0: no IPv6 routers present

```Here ist is with b43 blacklisted: (no wifi defice is up)
```
root@Wurzelpeter:~# lsmod
Module                  Size  Used by
vesafb                 13844  1
nouveau               774571  0
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
snd_hda_codec_hdmi     32474  3
snd_hda_codec_cirrus    23965  1
applesmc               19554  0
input_polldev          13896  1 applesmc
btusb                  18291  0
video                  19596  1 nouveau
bluetooth             204548  2 btusb
shpchp                 37277  0
bcma                   35220  0
hid_apple              13375  0
compat                 13447  3 btusb,bluetooth,bcma
snd_hda_intel          33773  0
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29990  1 snd_pcm
snd                    78855  7 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15091  1 snd
mac_hid                13253  0
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  1 lp
usbhid                 47199  0
hid                    99559  2 hid_apple,usbhid
mmc_block              27300  0
firewire_ohci          41000  0
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci
tg3                   152032  0

```dmesg:
```
root@Wurzelpeter:~# dmesg | grep bcma
[    4.437263] bcma-pci-bridge 0000:03:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    4.437273] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[    4.437300] bcma: Found chip with id 0xA8D8, rev 0x01 and package 0x08
[    4.437320] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[    4.437338] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[    4.437374] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[    4.708168] bcma: Bus registered

```so now i blacklisted both, b43 and bcma:
```
root@Wurzelpeter:~# lsmod
Module                  Size  Used by
vesafb                 13844  1
nouveau               774571  0
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
snd_hda_codec_hdmi     32474  3
snd_hda_codec_cirrus    23965  1
applesmc               19554  0
input_polldev          13896  1 applesmc
video                  19596  1 nouveau
btusb                  18291  0
bluetooth             204548  2 btusb
shpchp                 37277  0
hid_apple              13375  0
compat                 13447  2 btusb,bluetooth
snd_hda_intel          33773  0
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac_hid                13253  0
snd_timer              29990  1 snd_pcm
snd                    78855  7 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  1 lp
usbhid                 47199  0
hid                    99559  2 hid_apple,usbhid
mmc_block              27300  0
tg3                   152032  0
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

``````
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 0000000000090000 (reserved)
[    0.000000]  BIOS-e820: 0000000000090000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000af000000 (usable)
[    0.000000]  BIOS-e820: 00000000af000000 - 00000000bf000000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf000000 - 00000000bf70f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf930000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf930000 - 00000000bf931000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf931000 - 00000000bf939000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf939000 - 00000000bfef9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d3500000 - 00000000d3501000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Apple Inc. Macmini4,1/Mac-F2208EC8, BIOS     MM41.88Z.0042.B00.1004221740 04/22/10
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf70f max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf70f000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf70f000 page 4k
[    0.000000] kernel direct mapping tables up to bf70f000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf709000-bf70f000
[    0.000000] RAMDISK: 3656e000 - 372af000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
[    0.000000] ACPI: XSDT 00000000bf96a1c0 00084 (v01 APPLE   Apple00 00000042      01000013)
[    0.000000] ACPI: FACP 00000000bf968000 000F4 (v04 APPLE   Apple00 00000042 Loki 0000005F)
[    0.000000] ACPI: DSDT 00000000bf95b000 054A1 (v01 APPLE   Macmini 00040001 INTL 20061109)
[    0.000000] ACPI: FACS 00000000bf71e000 00040
[    0.000000] ACPI: HPET 00000000bf967000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf966000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 00000000bf965000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 00000000bf963000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 00000000bf962000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 00000000bf961000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf957000 00024 (v01 APPLE     Apple 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf956000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: MCFG 00000000bf964000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 00000000bf95a000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf959000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b800000-ffff88013f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000008f
[    0.000000]     0: 0x00000090 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000af000
[    0.000000]     0: 0x000bf000 -> 0x000bf70f
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 980637
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 698191 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 0000000000090000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000af000000 - 00000000bf000000
[    0.000000] PM: Registered nosave memory: 00000000bf70f000 - 00000000bf930000
[    0.000000] PM: Registered nosave memory: 00000000bf930000 - 00000000bf931000
[    0.000000] PM: Registered nosave memory: 00000000bf931000 - 00000000bf939000
[    0.000000] PM: Registered nosave memory: 00000000bf939000 - 00000000bfef9000
[    0.000000] PM: Registered nosave memory: 00000000bfef9000 - 00000000bfeff000
[    0.000000] PM: Registered nosave memory: 00000000bfeff000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000d3500000
[    0.000000] PM: Registered nosave memory: 00000000d3500000 - 00000000d3501000
[    0.000000] PM: Registered nosave memory: 00000000d3501000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d3501000 (gap: d3501000:1caff000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s83072 r8192 d23424 u1048576
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 960152
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=87e6eef0-db09-4c66-935c-4c7b2129d078 ro nomodeset quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3763376k/5242880k available (6566k kernel code, 1320332k absent, 159172k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2389.082 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4778.16 BogoMIPS (lpj=9556328)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004055] Yama: becoming mindful.
[    0.004444] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009707] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010606] Mount-cache hash table entries: 256
[    0.010753] Initializing cgroup subsys cpuacct
[    0.010758] Initializing cgroup subsys memory
[    0.010769] Initializing cgroup subsys devices
[    0.010772] Initializing cgroup subsys freezer
[    0.010774] Initializing cgroup subsys blkio
[    0.010780] Initializing cgroup subsys perf_event
[    0.010813] CPU: Physical Processor ID: 0
[    0.010814] CPU: Processor Core ID: 0
[    0.010817] mce: CPU supports 6 MCE banks
[    0.010826] CPU0: Thermal monitoring enabled (TM2)
[    0.010830] using mwait in idle threads.
[    0.013492] ACPI: Core revision 20110623
[    0.017709] ftrace: allocating 27049 entries in 107 pages
[    0.020511] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061626] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.152036] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152078] Brought up 2 CPUs
[    0.152080] Total of 2 processors activated (9556.54 BogoMIPS).
[    0.153975] devtmpfs: initialized
[    0.153975] EVM: security.selinux
[    0.153975] EVM: security.SMACK64
[    0.153975] EVM: security.capability
[    0.153975] PM: Registering ACPI NVS region at bf70f000 (2232320 bytes)
[    0.153975] PM: Registering ACPI NVS region at bf931000 (32768 bytes)
[    0.153975] print_constraints: dummy: 
[    0.153975] RTC time: 13:13:07, date: 05/31/12
[    0.153975] NET: Registered protocol family 16
[    0.156065] Trying to unpack rootfs image as initramfs...
[    0.156121] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.156124] ACPI: bus type pci registered
[    0.156397] PCI: MMCONFIG for domain 0000 [bus 00-05] at [mem 0xf0000000-0xf05fffff] (base 0xf0000000)
[    0.156400] PCI: MMCONFIG at [mem 0xf0000000-0xf05fffff] reserved in E820
[    0.157762] PCI: Using configuration type 1 for base access
[    0.172158] bio: create slab <bio-0> at 0
[    0.172206] ACPI: Added _OSI(Module Device)
[    0.172208] ACPI: Added _OSI(Processor Device)
[    0.172210] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172212] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173545] ACPI: EC: EC description table is found, configuring boot EC
[    0.176027] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.176327] ACPI: SSDT 00000000bf71dc98 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176623] ACPI: Dynamic OEM Table Load:
[    0.176627] ACPI: SSDT           (null) 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.176736] ACPI: SSDT 00000000bf71c618 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.177019] ACPI: Dynamic OEM Table Load:
[    0.177022] ACPI: SSDT           (null) 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.244257] ACPI: SSDT 00000000bf71df18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244553] ACPI: Dynamic OEM Table Load:
[    0.244556] ACPI: SSDT           (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.244635] ACPI: SSDT 00000000bf71bf18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.244919] ACPI: Dynamic OEM Table Load:
[    0.244922] ACPI: SSDT           (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.276211] ACPI: Interpreter enabled
[    0.276218] ACPI: (supports S0 S3 S4 S5)
[    0.276237] ACPI: Using IOAPIC for interrupt routing
[    0.281350] ACPI: EC: GPE = 0x57, I/O: command/status = 0x66, data = 0x62
[    0.281516] ACPI: No dock devices found.
[    0.281519] HEST: Table not found.
[    0.281522] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.281653] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.281763] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.281766] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.281768] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.281771] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.281773] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.281775] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.281778] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.281780] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.281782] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.281784] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.281787] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.281789] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.281791] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.281793] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.281795] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.281798] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[    0.281800] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.281826] pci 0000:00:00.0: [10de:0d60] type 0 class 0x000600
[    0.281943] pci 0000:00:00.1: [10de:0d68] type 0 class 0x000500
[    0.282116] pci 0000:00:01.0: [10de:0d6d] type 0 class 0x000500
[    0.282282] pci 0000:00:01.1: [10de:0d6e] type 0 class 0x000500
[    0.282449] pci 0000:00:01.2: [10de:0d6f] type 0 class 0x000500
[    0.282613] pci 0000:00:01.3: [10de:0d70] type 0 class 0x000500
[    0.282783] pci 0000:00:02.0: [10de:0d71] type 0 class 0x000500
[    0.282948] pci 0000:00:02.1: [10de:0d72] type 0 class 0x000500
[    0.283112] pci 0000:00:03.0: [10de:0d80] type 0 class 0x000601
[    0.283121] pci 0000:00:03.0: reg 10: [io  0x2100-0x21ff]
[    0.283169] pci 0000:00:03.1: [10de:0d7b] type 0 class 0x000500
[    0.283253] pci 0000:00:03.2: [10de:0d79] type 0 class 0x000c05
[    0.283267] pci 0000:00:03.2: reg 10: [io  0x0000-0x00ff]
[    0.283289] pci 0000:00:03.2: reg 20: [io  0x2240-0x227f]
[    0.283297] pci 0000:00:03.2: reg 24: [io  0x2200-0x223f]
[    0.283334] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.283340] pci 0000:00:03.2: PME# disabled
[    0.283364] pci 0000:00:03.3: [10de:0d69] type 0 class 0x000500
[    0.283570] pci 0000:00:03.4: [10de:0d7a] type 0 class 0x000b40
[    0.283591] pci 0000:00:03.4: reg 10: [mem 0xd3500000-0xd357ffff]
[    0.283735] pci 0000:00:04.0: [10de:0d9c] type 0 class 0x000c03
[    0.283747] pci 0000:00:04.0: reg 10: [mem 0xd358a000-0xd358afff]
[    0.283796] pci 0000:00:04.0: supports D1 D2
[    0.283798] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.283801] pci 0000:00:04.0: PME# disabled
[    0.283816] pci 0000:00:04.1: [10de:0d9d] type 0 class 0x000c03
[    0.283829] pci 0000:00:04.1: reg 10: [mem 0xd358b100-0xd358b1ff]
[    0.283888] pci 0000:00:04.1: supports D1 D2
[    0.283890] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.283894] pci 0000:00:04.1: PME# disabled
[    0.283917] pci 0000:00:06.0: [10de:0d9c] type 0 class 0x000c03
[    0.283928] pci 0000:00:06.0: reg 10: [mem 0xd3589000-0xd3589fff]
[    0.283979] pci 0000:00:06.0: supports D1 D2
[    0.283980] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.283984] pci 0000:00:06.0: PME# disabled
[    0.283999] pci 0000:00:06.1: [10de:0d9d] type 0 class 0x000c03
[    0.284024] pci 0000:00:06.1: reg 10: [mem 0xd358b000-0xd358b0ff]
[    0.284082] pci 0000:00:06.1: supports D1 D2
[    0.284084] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.284087] pci 0000:00:06.1: PME# disabled
[    0.284113] pci 0000:00:08.0: [10de:0d94] type 0 class 0x000403
[    0.284128] pci 0000:00:08.0: reg 10: [mem 0xd3580000-0xd3583fff]
[    0.284191] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.284194] pci 0000:00:08.0: PME# disabled
[    0.284212] pci 0000:00:0a.0: [10de:0d85] type 0 class 0x000101
[    0.284224] pci 0000:00:0a.0: reg 10: [io  0x2298-0x229f]
[    0.284231] pci 0000:00:0a.0: reg 14: [io  0x22a4-0x22a7]
[    0.284237] pci 0000:00:0a.0: reg 18: [io  0x2290-0x2297]
[    0.284243] pci 0000:00:0a.0: reg 1c: [io  0x22a0-0x22a3]
[    0.284250] pci 0000:00:0a.0: reg 20: [io  0x2280-0x228f]
[    0.284256] pci 0000:00:0a.0: reg 24: [mem 0xd3584000-0xd3585fff]
[    0.284304] pci 0000:00:0b.0: [10de:0d75] type 0 class 0x000500
[    0.284318] pci 0000:00:0b.0: reg 10: [mem 0xd3588000-0xd3588fff]
[    0.284436] pci 0000:00:0e.0: [10de:0d9a] type 1 class 0x000604
[    0.284704] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.284712] pci 0000:00:0e.0: PME# disabled
[    0.284821] pci 0000:00:15.0: [10de:0d9b] type 1 class 0x000604
[    0.285090] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.285098] pci 0000:00:15.0: PME# disabled
[    0.285199] pci 0000:00:16.0: [10de:0d9b] type 1 class 0x000604
[    0.285466] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.285475] pci 0000:00:16.0: PME# disabled
[    0.285527] pci 0000:00:17.0: [10de:0d76] type 1 class 0x000604
[    0.285570] pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
[    0.285573] pci 0000:00:17.0: PME# disabled
[    0.285787] pci 0000:01:00.0: [104c:823e] type 1 class 0x000604
[    0.285895] pci 0000:01:00.0: supports D1 D2
[    0.292045] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.292069] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.292166] pci 0000:02:00.0: [104c:823f] type 0 class 0x000c00
[    0.292190] pci 0000:02:00.0: reg 10: [mem 0xd3404000-0xd34047ff]
[    0.292203] pci 0000:02:00.0: reg 14: [mem 0xd3400000-0xd3403fff]
[    0.292299] pci 0000:02:00.0: supports D1 D2
[    0.292302] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.292307] pci 0000:02:00.0: PME# disabled
[    0.292367] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.292378] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.292620] pci 0000:03:00.0: [14e4:4353] type 0 class 0x000280
[    0.292641] pci 0000:03:00.0: reg 10: [mem 0xd3300000-0xd3303fff 64bit]
[    0.292743] pci 0000:03:00.0: supports D1 D2
[    0.292745] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.292750] pci 0000:03:00.0: PME# disabled
[    0.292806] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.292828] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.293044] pci 0000:04:00.0: [14e4:16b4] type 0 class 0x000200
[    0.293065] pci 0000:04:00.0: reg 10: [mem 0xd3100000-0xd310ffff 64bit pref]
[    0.293082] pci 0000:04:00.0: reg 18: [mem 0xd3110000-0xd311ffff 64bit pref]
[    0.293168] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.293173] pci 0000:04:00.0: PME# disabled
[    0.293214] pci 0000:04:00.1: [14e4:16bc] type 0 class 0x000805
[    0.293234] pci 0000:04:00.1: reg 10: [mem 0xd3120000-0xd312ffff 64bit pref]
[    0.293330] pci 0000:04:00.1: PME# supported from D0 D3hot D3cold
[    0.293335] pci 0000:04:00.1: PME# disabled
[    0.300048] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.300071] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.300087] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.300123] pci 0000:05:00.0: [10de:08a4] type 0 class 0x000300
[    0.300136] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.300144] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.300153] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.300159] pci 0000:05:00.0: reg 24: [io  0x1000-0x107f]
[    0.300165] pci 0000:05:00.0: reg 30: [mem 0xd3000000-0xd301ffff pref]
[    0.300217] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.300221] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.300224] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.300229] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.300280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.300510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.300625]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.300751]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.318963] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319041] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319116] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319194] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319268] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319344] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319419] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319494] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319569] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319643] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319718] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319793] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.319868] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.319942] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.320030] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.320106] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.320180] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.320258] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.320333] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.320406] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.320482] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.320559] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.320635] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.320710] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.320784] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.320859] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.320932] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
[    0.321086] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.321088] vgaarb: loaded
[    0.321089] vgaarb: bridge control possible 0000:05:00.0
[    0.321197] i2c-core: driver [aat2870] using legacy suspend method
[    0.321198] i2c-core: driver [aat2870] using legacy resume method
[    0.321269] SCSI subsystem initialized
[    0.321334] libata version 3.00 loaded.
[    0.321385] usbcore: registered new interface driver usbfs
[    0.321395] usbcore: registered new interface driver hub
[    0.321422] usbcore: registered new device driver usb
[    0.321516] PCI: Using ACPI for IRQ routing
[    0.321520] PCI: pci_cache_line_size set to 64 bytes
[    0.321684] reserve RAM buffer: 000000000008f000 - 000000000008ffff 
[    0.321686] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.321688] reserve RAM buffer: 00000000af000000 - 00000000afffffff 
[    0.321690] reserve RAM buffer: 00000000bf70f000 - 00000000bfffffff 
[    0.321796] NetLabel: Initializing
[    0.321797] NetLabel:  domain hash size = 128
[    0.321799] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.321810] NetLabel:  unlabeled traffic allowed by default
[    0.321856] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.321862] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.321867] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.328078] Switching to clocksource hpet
[    0.335883] AppArmor: AppArmor Filesystem Enabled
[    0.335917] pnp: PnP ACPI init
[    0.335938] ACPI: bus type pnp registered
[    0.336077] pnp 00:00: [bus 00-ff]
[    0.336080] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.336082] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.336084] pnp 00:00: [io  0x0d00-0xffff window]
[    0.336086] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.336088] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.336090] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.336092] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.336094] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.336096] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.336098] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.336101] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.336103] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.336105] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.336107] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.336109] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.336111] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.336113] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.336115] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.336194] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.336213] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.336215] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.336283] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.336287] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.336298] pnp 00:02: [io  0x0300-0x031f]
[    0.336311] pnp 00:02: [irq 6]
[    0.336338] pnp 00:02: Plug and Play ACPI device, IDs APP0001 (active)
[    0.336349] pnp 00:03: [io  0x0000-0x0008]
[    0.336351] pnp 00:03: [io  0x000a-0x000f]
[    0.336353] pnp 00:03: [io  0x0081-0x0083]
[    0.336355] pnp 00:03: [io  0x0087]
[    0.336357] pnp 00:03: [io  0x0089-0x008b]
[    0.336358] pnp 00:03: [io  0x008f]
[    0.336360] pnp 00:03: [io  0x00c0-0x00d1]
[    0.336362] pnp 00:03: [io  0x00d4-0x00df]
[    0.336364] pnp 00:03: [dma 4]
[    0.336386] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.336456] pnp 00:04: [irq 0 disabled]
[    0.336465] pnp 00:04: [irq 8]
[    0.336467] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.336515] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.336519] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.336528] pnp 00:05: [io  0x00f0-0x00f1]
[    0.336534] pnp 00:05: [irq 13]
[    0.336561] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.336663] pnp 00:06: [io  0x0400-0x047f]
[    0.336665] pnp 00:06: [io  0x0480-0x04ff]
[    0.336666] pnp 00:06: [io  0x0500-0x057f]
[    0.336668] pnp 00:06: [io  0x0580-0x05ff]
[    0.336670] pnp 00:06: [io  0x0800-0x087f]
[    0.336671] pnp 00:06: [io  0x0880-0x08ff]
[    0.336673] pnp 00:06: [io  0x0010-0x001f]
[    0.336675] pnp 00:06: [io  0x0022-0x003f]
[    0.336677] pnp 00:06: [io  0x0044-0x005f]
[    0.336678] pnp 00:06: [io  0x0063]
[    0.336680] pnp 00:06: [io  0x0065]
[    0.336682] pnp 00:06: [io  0x0067-0x006f]
[    0.336683] pnp 00:06: [io  0x0072-0x0073]
[    0.336685] pnp 00:06: [io  0x0074-0x007f]
[    0.336687] pnp 00:06: [io  0x0091-0x0093]
[    0.336689] pnp 00:06: [io  0x0097-0x009f]
[    0.336690] pnp 00:06: [io  0x00a2-0x00bf]
[    0.336692] pnp 00:06: [io  0x00e0-0x00ef]
[    0.336694] pnp 00:06: [io  0x04d0-0x04d1]
[    0.336695] pnp 00:06: [io  0x0080]
[    0.336697] pnp 00:06: [io  0x0295-0x0296]
[    0.336707] pnp 00:06: disabling [io  0x0010-0x001f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336710] pnp 00:06: disabling [io  0x0022-0x003f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336713] pnp 00:06: disabling [io  0x0044-0x005f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336716] pnp 00:06: disabling [io  0x0063] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336719] pnp 00:06: disabling [io  0x0065] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336722] pnp 00:06: disabling [io  0x0067-0x006f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336725] pnp 00:06: disabling [io  0x0072-0x0073] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336728] pnp 00:06: disabling [io  0x0074-0x007f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336731] pnp 00:06: disabling [io  0x0091-0x0093] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336734] pnp 00:06: disabling [io  0x0097-0x009f] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336737] pnp 00:06: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336740] pnp 00:06: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336743] pnp 00:06: disabling [io  0x0080] because it overlaps 0000:00:03.2 BAR 0 [io  0x0000-0x00ff]
[    0.336790] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.336793] system 00:06: [io  0x0480-0x04ff] has been reserved
[    0.336795] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.336798] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.336800] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.336802] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.336805] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.336808] system 00:06: [io  0x0295-0x0296] has been reserved
[    0.336811] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.336819] pnp 00:07: [io  0x0070-0x0077]
[    0.336844] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.337325] pnp: PnP ACPI: found 8 devices
[    0.337326] ACPI: ACPI bus type pnp unregistered
[    0.343609] PCI: max bus depth: 2 pci_try_num: 3
[    0.343698] pci 0000:00:03.2: BAR 0: assigned [io  0x2000-0x20ff]
[    0.343703] pci 0000:00:03.2: BAR 0: set to [io  0x2000-0x20ff] (PCI address [0x2000-0x20ff])
[    0.343706] pci 0000:01:00.0: PCI bridge to [bus 02-02]
[    0.343713] pci 0000:01:00.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.343724] pci 0000:00:0e.0: PCI bridge to [bus 01-02]
[    0.343735] pci 0000:00:0e.0:   bridge window [mem 0xd3400000-0xd34fffff]
[    0.343756] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.343767] pci 0000:00:15.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.343788] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.343799] pci 0000:00:16.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.343808] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.343823] pci 0000:00:17.0: PCI bridge to [bus 05-05]
[    0.343826] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.343829] pci 0000:00:17.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.343833] pci 0000:00:17.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.344013] ACPI: PCI Interrupt Link [Z00B] enabled at IRQ 23
[    0.344027] pci 0000:00:0e.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    0.344037] pci 0000:00:0e.0: setting latency timer to 64
[    0.344050] pci 0000:01:00.0: setting latency timer to 64
[    0.344076] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.344083] pci 0000:00:15.0: power state changed by ACPI to D0
[    0.344199] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
[    0.344206] pci 0000:00:15.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.344215] pci 0000:00:15.0: setting latency timer to 64
[    0.344334] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 21
[    0.344340] pci 0000:00:16.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    0.344350] pci 0000:00:16.0: setting latency timer to 64
[    0.344358] pci 0000:00:17.0: setting latency timer to 64
[    0.344362] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.344364] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.344366] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.344369] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.344371] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.344373] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.344375] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.344377] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.344379] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.344381] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.344384] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.344386] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.344388] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.344390] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.344392] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.344394] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.344396] pci_bus 0000:00: resource 20 [mem 0xc0000000-0xfebfffff]
[    0.344399] pci_bus 0000:01: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.344402] pci_bus 0000:02: resource 1 [mem 0xd3400000-0xd34fffff]
[    0.344404] pci_bus 0000:03: resource 1 [mem 0xd3300000-0xd33fffff]
[    0.344407] pci_bus 0000:04: resource 1 [mem 0xd3200000-0xd32fffff]
[    0.344411] pci_bus 0000:04: resource 2 [mem 0xd3100000-0xd31fffff 64bit pref]
[    0.344414] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.344417] pci_bus 0000:05: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.344420] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.344465] NET: Registered protocol family 2
[    0.344606] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.345706] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.349608] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.350086] TCP: Hash tables configured (established 524288 bind 65536)
[    0.350089] TCP reno registered
[    0.350100] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.350137] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.350267] NET: Registered protocol family 1
[    0.350444] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.350448] pci 0000:00:04.0: power state changed by ACPI to D0
[    0.350576] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    0.350591] pci 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.407589] Freeing initrd memory: 13572k freed
[    0.420044] pci 0000:00:04.0: PCI INT A disabled
[    0.420117] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.420122] pci 0000:00:04.1: power state changed by ACPI to D0
[    0.420256] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    0.420274] pci 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.420312] pci 0000:00:04.1: PCI INT B disabled
[    0.420339] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.420343] pci 0000:00:06.0: power state changed by ACPI to D0
[    0.420453] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 18
[    0.420460] pci 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.476021] pci 0000:00:06.0: PCI INT A disabled
[    0.476052] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.476056] pci 0000:00:06.1: power state changed by ACPI to D0
[    0.476166] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 17
[    0.476174] pci 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.476193] pci 0000:00:06.1: PCI INT B disabled
[    0.476391] PCI: CLS mismatch (256 != 64), using 64 bytes
[    0.476403] pci 0000:05:00.0: Boot video device
[    0.476407] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.476409] Placing 64MB software IO TLB between ffff8800ab000000 - ffff8800af000000
[    0.476411] software IO TLB at phys 0xab000000 - 0xaf000000
[    0.476801] audit: initializing netlink socket (disabled)
[    0.476816] type=2000 audit(1338469987.472:1): initialized
[    0.507687] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.528884] VFS: Disk quotas dquot_6.5.2
[    0.528943] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.529449] fuse init (API version 7.17)
[    0.529545] msgmni has been set to 7376
[    0.529923] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.529953] io scheduler noop registered
[    0.529955] io scheduler deadline registered
[    0.529991] io scheduler cfq registered (default)
[    0.530141] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.530295] pcieport 0000:00:0e.0: irq 40 for MSI/MSI-X
[    0.530472] pcieport 0000:00:15.0: setting latency timer to 64
[    0.530618] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.530792] pcieport 0000:00:16.0: setting latency timer to 64
[    0.530937] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.531142] pcieport 0000:00:0e.0: Signaling PME through PCIe PME interrupt
[    0.531144] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.531146] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.531155] pcie_pme 0000:00:0e.0:pcie01: service driver pcie_pme loaded
[    0.531192] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.531195] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.531203] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.531243] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
[    0.531245] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.531248] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.531256] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
[    0.531274] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.531296] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.531351] efifb: dmi detected Macmini4,1 - framebuffer at 0xd1000000 (640x480, stride 2560)
[    0.531354] intel_idle: MWAIT substates: 0x3122220
[    0.531355] intel_idle: does not run on family 6 model 23
[    0.531442] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.531447] ACPI: Power Button [PWRB]
[    0.531491] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.531494] ACPI: Sleep Button [SLPB]
[    0.531555] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.531558] ACPI: Power Button [PWRF]
[    0.531723] Monitor-Mwait will be used to enter C-1 state
[    0.531750] Monitor-Mwait will be used to enter C-2 state
[    0.531777] Monitor-Mwait will be used to enter C-3 state
[    0.531784] Marking TSC unstable due to TSC halts in idle
[    0.531798] ACPI: acpi_idle registered with cpuidle
[    0.533260] ERST: Table is not found!
[    0.533262] GHES: HEST is not enabled!
[    0.533336] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.648350] Linux agpgart interface v0.103
[    0.649812] brd: module loaded
[    0.650565] loop: module loaded
[    0.650687] ahci 0000:00:0a.0: version 3.0
[    0.650783] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.650787] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    0.650908] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 16
[    0.650920] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.650943] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    0.650953] pata_acpi 0000:00:0a.0: PCI INT A disabled
[    0.650981] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.650985] ata_generic 0000:00:0a.0: power state changed by ACPI to D0
[    0.650990] ata_generic 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 16 (level, low) -> IRQ 16
[    0.651004] ata_generic 0000:00:0a.0: setting latency timer to 64
[    0.651295] scsi0 : ata_generic
[    0.651375] scsi1 : ata_generic
[    0.651486] ata1: PATA max UDMA/100 cmd 0x2298 ctl 0x22a4 bmdma 0x2280 irq 16
[    0.651489] ata2: PATA max UDMA/100 cmd 0x2290 ctl 0x22a0 bmdma 0x2288 irq 16
[    0.651771] Fixed MDIO Bus: probed
[    0.651790] tun: Universal TUN/TAP device driver, 1.6
[    0.651791] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.651888] PPP generic driver version 2.4.2
[    0.651988] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.652016] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.652021] ehci_hcd 0000:00:04.1: power state changed by ACPI to D0
[    0.652026] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.652046] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.652049] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.652093] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.652108] ehci_hcd 0000:00:04.1: disable lpm/ppcd for nvidia mcp89
[    0.652114] ehci_hcd 0000:00:04.1: debug port 1
[    0.676017] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.676032] ehci_hcd 0000:00:04.1: irq 19, io mem 0xd358b100
[    0.688017] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.10
[    0.688145] hub 1-0:1.0: USB hub found
[    0.688149] hub 1-0:1.0: 6 ports detected
[    0.688220] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.688224] ehci_hcd 0000:00:06.1: power state changed by ACPI to D0
[    0.688230] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 17 (level, low) -> IRQ 17
[    0.688241] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.688243] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.688290] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.688302] ehci_hcd 0000:00:06.1: disable lpm/ppcd for nvidia mcp89
[    0.688308] ehci_hcd 0000:00:06.1: debug port 1
[    0.712018] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.712033] ehci_hcd 0000:00:06.1: irq 17, io mem 0xd358b000
[    0.724016] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.10
[    0.724123] hub 2-0:1.0: USB hub found
[    0.724127] hub 2-0:1.0: 6 ports detected
[    0.724199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.724211] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.724215] ohci_hcd 0000:00:04.0: power state changed by ACPI to D0
[    0.724220] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.724231] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.724234] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.724279] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.724300] ohci_hcd 0000:00:04.0: irq 20, io mem 0xd358a000
[    0.782102] hub 3-0:1.0: USB hub found
[    0.782107] hub 3-0:1.0: 6 ports detected
[    0.782175] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.782179] ohci_hcd 0000:00:06.0: power state changed by ACPI to D0
[    0.782184] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
[    0.782195] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.782198] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.782247] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.782266] ohci_hcd 0000:00:06.0: irq 18, io mem 0xd3589000
[    0.812207] ata1.00: ATA-8: SAMSUNG HN-M101MBB, 2AR10001, max UDMA/133
[    0.812210] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.812214] ata1.00: configured for UDMA/133
[    0.812321] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M101M 2AR1 PQ: 0 ANSI: 5
[    0.812450] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.812452] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.812497] sd 0:0:0:0: [sda] Write Protect is off
[    0.812499] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.812520] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.838114] hub 4-0:1.0: USB hub found
[    0.838119] hub 4-0:1.0: 6 ports detected
[    0.838187] uhci_hcd: USB Universal Host Controller Interface driver
[    0.838243] usbcore: registered new interface driver libusual
[    0.838275] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.839130] i8042: No controller found
[    0.839210] mousedev: PS/2 mouse device common for all mice
[    0.839389] rtc_cmos 00:07: RTC can wake from S4
[    0.839590] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.839640] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.839710] device-mapper: uevent: version 1.0.3
[    0.839787] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.839848] cpuidle: using governor ladder
[    0.839928] cpuidle: using governor menu
[    0.839930] EFI Variables Facility v0.08 2004-May-17
[    0.840163] TCP cubic registered
[    0.840267] NET: Registered protocol family 10
[    0.840692] NET: Registered protocol family 17
[    0.840708] Registering the dns_resolver key type
[    0.840902] PM: Hibernation image not present or could not be loaded.
[    0.840917] registered taskstats version 1
[    0.856557]   Magic number: 12:868:231
[    0.856710] rtc_cmos 00:07: setting system clock to 2012-05-31 13:13:08 UTC (1338469988)
[    0.857133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.857134] EDD information not available.
[    0.872414]  sda: sda1 sda2 sda3 sda4 sda5 sda6
[    0.873148] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.968252] ata2.01: NODEV after polling detection
[    0.976228] ata2.00: ATAPI: HL-DT-STDVDRW  GA32N, KC08, max UDMA/100
[    0.976232] ata2.00: configured for UDMA/100
[    0.979046] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRW  GA32N     KC08 PQ: 0 ANSI: 5
[    0.983122] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.983126] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.983284] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.983383] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.984994] Freeing unused kernel memory: 920k freed
[    0.985250] Write protecting the kernel read-only data: 12288k
[    0.990493] Freeing unused kernel memory: 1608k freed
[    0.994793] Freeing unused kernel memory: 1196k freed
[    1.009755] udevd[94]: starting version 175
[    1.084727] tg3.c:v3.121 (November 2, 2011)
[    1.084746] tg3 0000:04:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
[    1.084756] tg3 0000:04:00.0: setting latency timer to 64
[    1.097463] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM957765) rev 57785000] (PCI Express) MAC address c4:2c:03:03:07:cb
[    1.097468] tg3 0000:04:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.097471] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.097474] tg3 0000:04:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    1.100440] sdhci: Secure Digital Host Controller Interface driver
[    1.100443] sdhci: Copyright(c) Pierre Ossman
[    1.100703] sdhci-pci 0000:04:00.1: SDHCI controller found [14e4:16bc] (rev 0)
[    1.100872] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 23
[    1.100877] sdhci-pci 0000:04:00.1: PCI INT B -> Link[Z00O] -> GSI 23 (level, low) -> IRQ 23
[    1.100880] sdhci-pci 0000:04:00.1: Invalid iomem size. You may experience problems.
[    1.100931] sdhci-pci 0000:04:00.1: setting latency timer to 64
[    1.100955] mmc0: no vmmc regulator found
[    1.100984] Registered led device: mmc0::
[    1.102082] mmc0: SDHCI controller on PCI [0000:04:00.1] using ADMA
[    1.107244] firewire_ohci 0000:02:00.0: PCI INT A -> Link[Z00B] -> GSI 23 (level, low) -> IRQ 23
[    1.160109] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x2
[    1.248050] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.280845] mmc0: new high speed SDHC card at address e624
[    1.282490] mmcblk0: mmc0:e624 SD32G 29.7 GiB 
[    1.294826]  mmcblk0: p1 p2 < p5 >
[    1.469372] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input3
[    1.469533] generic-usb 0003:04D9:1203.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:04.0-1/input0
[    1.491113] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.1/input/input4
[    1.491206] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:04.0-1/input1
[    1.491223] usbcore: registered new interface driver usbhid
[    1.491224] usbhid: USB HID core driver
[    1.664173] firewire_core: created device fw0: GUID e80688fffeafd696, S800
[    1.668317] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.932054] usb 4-5: new low-speed USB device number 2 using ohci_hcd
[    2.456129] usb 4-6: new full-speed USB device number 3 using ohci_hcd
[    2.681091] hub 4-6:1.0: USB hub found
[    2.684046] hub 4-6:1.0: 3 ports detected
[    2.990118] usb 4-6.1: new full-speed USB device number 4 using ohci_hcd
[    3.111326] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-6/4-6.1/4-6.1:1.0/input/input5
[    3.111465] generic-usb 0003:05AC:820A.0004: input,hidraw2: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-6.1/input0
[    3.186047] usb 4-6.2: new full-speed USB device number 5 using ohci_hcd
[    3.307699] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-6/4-6.2/4-6.2:1.0/input/input6
[    3.307915] generic-usb 0003:05AC:820B.0005: input,hidraw3: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-6.2/input0
[    3.382046] usb 4-6.3: new full-speed USB device number 6 using ohci_hcd
[    4.273581] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.292079] udevd[342]: starting version 175
[    4.329707] lp: driver loaded but no devices found
[    4.400185] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.400191] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[    4.400335] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[    4.400340] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[    4.400344] hda_intel: Disabling MSI
[    4.400346] hda_intel: position_fix set to 1 for device 10de:cb89
[    4.400398] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[    4.417858] Adding 3922760k swap on /dev/sda5.  Priority:-1 extents:1 across:3922760k 
[    4.432474] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    4.432628] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:31/LNXVIDEO:00/input/input7
[    4.432675] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    4.485904] tg3 0000:04:00.0: irq 43 for MSI/MSI-X
[    4.485910] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[    4.485914] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[    4.489151] apple 0003:05AC:8242.0003: hiddev0,hidraw4: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:06.0-5/input0
[    4.729831] applesmc: key=215 fan=1 temp=29 acc=0 lux=0 kbd=0
[    4.774261] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.243407] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    5.674943] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    5.980104] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.004100] HDMI status: Codec=4 Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.028100] HDMI status: Codec=5 Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.028211] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:08.0/sound/card0/input8
[    6.028305] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:08.0/sound/card0/input9
[    6.028373] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[    6.028440] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[    6.029071] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.039133] wmi: Mapper loaded
[    6.045117] [drm] Initialized drm 1.1.0 20060810
[    6.104261] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    6.104264] vesafb: scrolling: redraw
[    6.104266] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    6.106143] vesafb: framebuffer at 0xd1000000, mapped to 0xffffc90001c80000, using 1216k, total 1216k
[    6.106286] Console: switching to colour frame buffer device 80x30
[    6.106298] fb0: VESA VGA frame buffer device
[    7.177524] tg3 0000:04:00.0: eth0: Link is up at 1000 Mbps, full duplex
[    7.177527] tg3 0000:04:00.0: eth0: Flow control is on for TX and on for RX
[    7.177934] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    7.890722] init: failsafe main process (624) killed by TERM signal
[   17.480089] eth0: no IPv6 routers present
[   50.038090] Compat-wireless backport release: compat-wireless-2012-05-04
[   50.038093] Backport based on linux-next.git next-20120510
[   50.043402] bcma-pci-bridge 0000:03:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[   50.043413] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   50.043513] bcma: Found chip with id 0xA8D8, rev 0x01 and package 0x08
[   50.043534] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   50.043551] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   50.043587] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   50.112038] bcma: Bus registered
[   50.115728] cfg80211: Calling CRDA to update world regulatory domain
[   50.120948] cfg80211: World regulatory domain updated:
[   50.120951] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.120953] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.120956] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.120958] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.120961] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.120963] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.128420] b43-phy0: Broadcom 43224 WLAN found (core revision 23)
[   50.129003] Broadcom 43xx driver loaded [ Features: PMNLS ]
[   50.134333] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   50.134337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134339] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   50.134342] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134344] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   50.134347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134349] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   50.134352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134354] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   50.134357] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134359] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   50.134361] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134363] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   50.134366] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134368] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   50.134371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134373] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   50.134376] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134378] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   50.134381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134383] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   50.134385] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.134387] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   50.134390] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.134392] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   50.134395] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.134397] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   50.134400] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.137894] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'


```
So then when i modprobeb43, b43 comes up with bcma and  bg wifi defice.

It seams that the bcma module loads somekind of "bridge". Here you can see what we are talking about, it is an BT/WIFI Combo :
[http://guide-images.ifixit.net/igi/cKIO3uOhZ2UnfSK5.huge](http://guide-images.ifixit.net/igi/cKIO3uOhZ2UnfSK5.huge)

Any Ideas?
derdigge

---

### Post by chili555 on 2012-05-31
> So then when i modprobeb43, b43 comes up with bcma and bg wifi defice.

It seams that the bcma module loads somekind of "bridge".Yes, indeed. We are all learning more about this every day. Let's be sure neither is blacklisted and try some other things.> But ieee80211n=1 isnt working cause of the kernelmodule somehow.Where and how did you implement that parameter? What does this tell us?```
cat /sys/module/cfg80211/parameters/ieee80211_regdom
```

---

### Post by derdigge on 2012-05-31
[QUOTE=Where and how did you implement that parameter? What does this tell us?```
cat /sys/module/cfg80211/parameters/ieee80211_regdom
```[/QUOTE]

That Parameter tells us that i tried to add this in "/etc/hostapd/hostap.conf" :]

but how do i have to understand this :

```
root@Wurzelpeter:~# cat /sys/module/cfg80211/parameters/ieee80211_regdom
00
```

---

### Post by chili555 on 2012-05-31
I believe we understand that cfg80211, upon which b43 depends, has not properly set your region. I'm not sure that's really a pertinent symptom yet. Let's look at:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```In a few cases, the rate algorithm gets erroneously set to 'minstrel;' we hope it's 'minstrel_ht.' 

I wonder if N works in Managed mode but not Master.

---

### Post by derdigge on 2012-05-31
```
root@Wurzelpeter:~# cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
minstrel_ht

```

it is ...

---

### Post by derdigge on 2012-06-03
So i dont think that there will be an solution for that.
Is it possible to disable pci devices? I mean full powerdown.
If so i decide to Powerdown the graphics Card, Wifi/Bluetooth Card, Firewire Controller! I will use then a Usb stick for my hotspot.
):P

---

