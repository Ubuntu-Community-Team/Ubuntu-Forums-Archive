---
title: "Upgrade to 13.04 has borked the wireless connection"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by patman0623 on 2013-05-03
The upgrade to Ubuntu 13.04 has caused my wireless connection to fail. It usually fails altogether, although occasionally it will connect briefly and I will get a little bit of data through. It was working before the upgrade, and it is currently working fine from Windows.

Here is my system information dump. Can anybody help?

System:
```

P Pavilion p6000

```

lspci -nn:
```

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200] [1002:9710]
01:05.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```

iwconfig
```

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth2      no wireless extensions.

lo        no wireless extensions.

```

lsmod
```

Module                  Size  Used by
wl                   3074449  0 
lib80211               14352  1 wl
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
dm_crypt               22820  0 
kvm                   443165  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_rawmidi            30180  1 snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
arc4                   12615  2 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
rt2800pci              18582  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13205  0 
psmouse                95870  0 
serio_raw              13215  0 
cfg80211              510937  3 wl,mac80211,rt2x00lib
sp5100_tco             13735  0 
i2c_piix4              13266  0 
soundcore              12680  1 snd
eeprom_93cx6           13344  1 rt2800pci
edac_core              62003  0 
crc_ccitt              12707  1 rt2800lib
shpchp                 37032  0 
edac_mce_amd           23114  0 
microcode              22881  0 
k10temp                13126  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_logitech_dj        18604  0 
hid_generic            12540  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  3 hid_generic,usbhid,hid_logitech_dj
usb_storage            57204  0 
radeon                937749  3 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
wmi                    19070  0 
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci

```

dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 (Ubuntu 3.8.0-19.30-generic 3.8.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=f2347f51-daec-4ef5-a86b-2d7866993f06 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009a3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009a400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfd9ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfda0000-0x00000000cfdadfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfdae000-0x00000000cfdcffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfdd0000-0x00000000cfddffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cfded000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard p6710f/2AB1 , BIOS 6.11 12/28/2011
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfda0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcfd9ffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfbfffff] page 2M
[    0.000000]  [mem 0xcfc00000-0xcfd9ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcfd9ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x11fffffff @ [mem 0xcfd9e000-0xcfd9ffff]
[    0.000000] RAMDISK: [mem 0x34418000-0x36203fff]
[    0.000000] ACPI: RSDP 00000000000fb480 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000cfda0100 0006C (v01 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfda0290 000F4 (v03 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI BIOS Bug: Warning: Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20121018/tbfadt-598)
[    0.000000] ACPI: DSDT 00000000cfda05d0 04AB6 (v01 HPQOEM SLIC-CPC 00000C28 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cfdae000 00040
[    0.000000] ACPI: APIC 00000000cfda0390 0007C (v01 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfda0410 0003C (v01 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cfda0450 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: OEMB 00000000cfdae040 00072 (v01 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfdaa6b0 00843 (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
[    0.000000] ACPI: SRAT 00000000cfdaaf00 000E8 (v03 HPQOEM SLIC-CPC 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cfdaaff0 00038 (v01 HPQOEM SLIC-CPC 20111228 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfdab030 0088C (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x00100000-0xcfffffff]
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x100000000-0x12fffffff]
[    0.000000] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0xcfffffff] -> [mem 0x00000000-0xcfffffff]
[    0.000000] NUMA: Node 0 [mem 0x00000000-0xcfffffff] + [mem 0x100000000-0x11fffffff] -> [mem 0x00000000-0x11fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fffffff]
[    0.000000]   NODE_DATA [mem 0x11fffb000-0x11fffffff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ba00000-ffff88011f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00099fff]
[    0.000000]   node   0: [mem 0x00100000-0xcfd9ffff]
[    0.000000]   node   0: [mem 0x100000000-0x11fffffff]
[    0.000000] On node 0 totalpages: 982314
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3908 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13239 pages used for memmap
[    0.000000]   DMA32 zone: 834025 pages, LIFO batch:31
[    0.000000]   Normal zone: 2048 pages used for memmap
[    0.000000]   Normal zone: 129024 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfda0000 - 00000000cfdae000
[    0.000000] PM: Registered nosave memory: 00000000cfdae000 - 00000000cfdd0000
[    0.000000] PM: Registered nosave memory: 00000000cfdd0000 - 00000000cfde0000
[    0.000000] PM: Registered nosave memory: 00000000cfde0000 - 00000000cfded000
[    0.000000] PM: Registered nosave memory: 00000000cfded000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011fc00000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966957
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=f2347f51-daec-4ef5-a86b-2d7866993f06 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3689088k/4718592k available (7006k kernel code, 789336k absent, 240168k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=6.
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15728640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2999.792 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.58 BogoMIPS (lpj=11999168)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000039] Yama: becoming mindful.
[    0.000294] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001326] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001777] Mount-cache hash table entries: 256
[    0.001934] Initializing cgroup subsys cpuacct
[    0.001936] Initializing cgroup subsys memory
[    0.001944] Initializing cgroup subsys devices
[    0.001945] Initializing cgroup subsys freezer
[    0.001947] Initializing cgroup subsys blkio
[    0.001948] Initializing cgroup subsys perf_event
[    0.001951] Initializing cgroup subsys hugetlb
[    0.001971] tseg: 00cfe00000
[    0.001973] CPU: Physical Processor ID: 0
[    0.001974] CPU: Processor Core ID: 0
[    0.001975] mce: CPU supports 6 MCE banks
[    0.001980] LVT offset 0 assigned for vector 0xf9
[    0.001986] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.001986] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.001986] tlb_flushall_shift: 4
[    0.002080] Freeing SMP alternatives: 24k freed
[    0.003383] ACPI: Core revision 20121018
[    0.005420] ftrace: allocating 26690 entries in 105 pages
[    0.015539] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.055184] smpboot: CPU0: AMD Athlon(tm) II X4 640 Processor (fam: 10, model: 0a, stepping: 00)
[    0.162787] Performance Events: AMD PMU driver.
[    0.162791] ... version:                0
[    0.162792] ... bit width:              48
[    0.162793] ... generic registers:      4
[    0.162794] ... value mask:             0000ffffffffffff
[    0.162795] ... max period:             00007fffffffffff
[    0.162796] ... fixed-purpose events:   0
[    0.162797] ... event mask:             000000000000000f
[    0.163702] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.163771] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.202967] Brought up 4 CPUs
[    0.202969] smpboot: Total of 4 processors activated (23998.33 BogoMIPS)
[    0.203715] devtmpfs: initialized
[    0.204717] EVM: security.selinux
[    0.204718] EVM: security.SMACK64
[    0.204719] EVM: security.capability
[    0.204816] PM: Registering ACPI NVS region [mem 0xcfdae000-0xcfdcffff] (139264 bytes)
[    0.205646] regulator-dummy: no parameters
[    0.205693] NET: Registered protocol family 16
[    0.205780] node 0 link 0: io port [1000, ffffff]
[    0.205782] TOM: 00000000d0000000 aka 3328M
[    0.205784] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.205786] node 0 link 0: mmio [a0000, bffff]
[    0.205788] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.205791] node 0 link 0: mmio [f0000000, fe7fffff]
[    0.205792] node 0 link 0: mmio [fe800000, fe9fffff]
[    0.205794] node 0 link 0: mmio [fea00000, ffefffff]
[    0.205795] TOM2: 0000000130000000 aka 4864M
[    0.205797] bus: [bus 00-07] on node 0 link 0
[    0.205798] bus: 00 [io  0x0000-0xffff]
[    0.205799] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.205800] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.205801] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.205802] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.205901] ACPI: bus type pci registered
[    0.205949] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.205951] PCI: not using MMCONFIG
[    0.205952] PCI: Using configuration type 1 for base access
[    0.205953] PCI: Using configuration type 1 for extended access
[    0.206090] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.206091] mtrr: probably your BIOS does not setup all CPUs.
[    0.206092] mtrr: corrected configuration.
[    0.206776] bio: create slab <bio-0> at 0
[    0.206859] ACPI: Added _OSI(Module Device)
[    0.206861] ACPI: Added _OSI(Processor Device)
[    0.206862] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.206863] ACPI: Added _OSI(Processor Aggregator Device)
[    0.207327] ACPI: EC: Look up EC in DSDT
[    0.207961] ACPI: Executed 3 blocks of module-level executable AML code
[    0.209419] ACPI: Interpreter enabled
[    0.209422] ACPI: (supports S0 S1 S3 S4 S5)
[    0.209436] ACPI: Using IOAPIC for interrupt routing
[    0.209458] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.209934] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.222179] ACPI: No dock devices found.
[    0.222185] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.222247] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.222249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.222445] PCI host bridge to bus 0000:00
[    0.222448] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.222450] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.222452] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.222454] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.222455] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.222457] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.222459] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.222470] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
[    0.222515] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
[    0.222552] pci 0000:00:05.0: [1022:9605] type 01 class 0x060400
[    0.222582] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.222599] pci 0000:00:0a.0: [1022:9609] type 01 class 0x060400
[    0.222628] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.222665] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.222683] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.222693] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.222702] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.222711] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.222720] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.222739] pci 0000:00:11.0: reg 24: [mem 0xfe7ffc00-0xfe7fffff]
[    0.222794] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.222806] pci 0000:00:12.0: reg 10: [mem 0xfe7fe000-0xfe7fefff]
[    0.222869] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.222881] pci 0000:00:12.1: reg 10: [mem 0xfe7fd000-0xfe7fdfff]
[    0.222949] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.222970] pci 0000:00:12.2: reg 10: [mem 0xfe7ff800-0xfe7ff8ff]
[    0.223050] pci 0000:00:12.2: supports D1 D2
[    0.223051] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.223074] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.223087] pci 0000:00:13.0: reg 10: [mem 0xfe7fc000-0xfe7fcfff]
[    0.223149] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.223162] pci 0000:00:13.1: reg 10: [mem 0xfe7f7000-0xfe7f7fff]
[    0.223229] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.223247] pci 0000:00:13.2: reg 10: [mem 0xfe7ff400-0xfe7ff4ff]
[    0.223326] pci 0000:00:13.2: supports D1 D2
[    0.223328] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.223353] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.223449] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.223470] pci 0000:00:14.2: reg 10: [mem 0xfe7f0000-0xfe7f3fff 64bit]
[    0.223533] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.223548] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.223621] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.223664] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.223680] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.223691] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.223703] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.223717] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.223759] pci 0000:01:05.0: [1002:9710] type 00 class 0x030000
[    0.223766] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.223770] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.223774] pci 0000:01:05.0: reg 18: [mem 0xfe8f0000-0xfe8fffff]
[    0.223783] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
[    0.223798] pci 0000:01:05.0: supports D1 D2
[    0.223806] pci 0000:01:05.1: [1002:970f] type 00 class 0x040300
[    0.223814] pci 0000:01:05.1: reg 10: [mem 0xfe8e8000-0xfe8ebfff]
[    0.223840] pci 0000:01:05.1: supports D1 D2
[    0.223879] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.223882] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.223884] pci 0000:00:01.0:   bridge window [mem 0xfe800000-0xfe9fffff]
[    0.223888] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.223920] pci 0000:02:00.0: [1814:5390] type 00 class 0x028000
[    0.223931] pci 0000:02:00.0: reg 10: [mem 0xfeaf0000-0xfeafffff]
[    0.230758] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.230766] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.230805] pci 0000:03:00.0: [10ec:8136] type 00 class 0x020000
[    0.230819] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.230838] pci 0000:03:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
[    0.230851] pci 0000:03:00.0: reg 20: [mem 0xfdffc000-0xfdffffff 64bit pref]
[    0.230905] pci 0000:03:00.0: supports D1 D2
[    0.230907] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.238750] pci 0000:00:0a.0: PCI bridge to [bus 03]
[    0.238756] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.238759] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.238762] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.238825] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.238834] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.238836] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.238837] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.238839] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.238841] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.238842] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.238870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.238911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.238944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.238989]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.238991]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.239698] ACPI: PCI Interrupt Link [LNKA] (IRQs *4 7 10 11 12 14 15)
[    0.239728] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.239754] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.239779] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.239804] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.239830] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.239856] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *7 10 11 12 14 15)
[    0.239881] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.239990] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.239991] vgaarb: loaded
[    0.239992] vgaarb: bridge control possible 0000:01:05.0
[    0.240140] SCSI subsystem initialized
[    0.240141] ACPI: bus type scsi registered
[    0.240201] libata version 3.00 loaded.
[    0.240218] ACPI: bus type usb registered
[    0.240234] usbcore: registered new interface driver usbfs
[    0.240242] usbcore: registered new interface driver hub
[    0.240260] usbcore: registered new device driver usb
[    0.240339] PCI: Using ACPI for IRQ routing
[    0.248698] PCI: pci_cache_line_size set to 64 bytes
[    0.248756] e820: reserve RAM buffer [mem 0x0009a400-0x0009ffff]
[    0.248757] e820: reserve RAM buffer [mem 0xcfda0000-0xcfffffff]
[    0.248832] NetLabel: Initializing
[    0.248833] NetLabel:  domain hash size = 128
[    0.248834] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.248842] NetLabel:  unlabeled traffic allowed by default
[    0.248920] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.248923] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.250945] Switching to clocksource hpet
[    0.255224] AppArmor: AppArmor Filesystem Enabled
[    0.255251] pnp: PnP ACPI init
[    0.255263] ACPI: bus type pnp registered
[    0.255393] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.255424] pnp 00:01: [dma 4]
[    0.255438] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.255464] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.255481] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.255499] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.255529] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.255604] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.255606] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.255608] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.255745] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.255748] system 00:07: [io  0x040b] has been reserved
[    0.255749] system 00:07: [io  0x04d6] has been reserved
[    0.255751] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    0.255753] system 00:07: [io  0x0c14] has been reserved
[    0.255754] system 00:07: [io  0x0c50-0x0c51] has been reserved
[    0.255756] system 00:07: [io  0x0c52] has been reserved
[    0.255758] system 00:07: [io  0x0c6c] has been reserved
[    0.255759] system 00:07: [io  0x0c6f] has been reserved
[    0.255761] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
[    0.255763] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
[    0.255765] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
[    0.255766] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
[    0.255768] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
[    0.255770] system 00:07: [io  0x0800-0x089f] has been reserved
[    0.255772] system 00:07: [io  0x0b00-0x0b0f] has been reserved
[    0.255773] system 00:07: [io  0x0b20-0x0b3f] has been reserved
[    0.255775] system 00:07: [io  0x0900-0x090f] has been reserved
[    0.255777] system 00:07: [io  0x0910-0x091f] has been reserved
[    0.255779] system 00:07: [io  0xfe00-0xfefe] has been reserved
[    0.255781] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.255783] system 00:07: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.255785] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.255896] system 00:08: [io  0x0e00-0x0e0f] has been reserved
[    0.255898] system 00:08: [io  0x0e80-0x0e8f] has been reserved
[    0.255900] system 00:08: [io  0x0f40-0x0f4f] has been reserved
[    0.255902] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.255941] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.255944] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.256040] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.256043] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.256045] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.256047] system 00:0a: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.256049] system 00:0a: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.256051] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.256126] pnp: PnP ACPI: found 11 devices
[    0.256128] ACPI: ACPI bus type pnp unregistered
[    0.262347] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.262350] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.262353] pci 0000:00:01.0:   bridge window [mem 0xfe800000-0xfe9fffff]
[    0.262356] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.262359] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.262361] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.262365] pci 0000:00:0a.0: PCI bridge to [bus 03]
[    0.262367] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.262370] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.262372] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.262375] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.262409] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.262410] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.262412] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.262414] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.262415] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.262417] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.262418] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.262420] pci_bus 0000:01: resource 1 [mem 0xfe800000-0xfe9fffff]
[    0.262422] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.262423] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.262425] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.262427] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.262428] pci_bus 0000:03: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.262430] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.262432] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.262434] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.262435] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.262437] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.262438] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.262473] NET: Registered protocol family 2
[    0.262607] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.262748] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.262865] TCP: Hash tables configured (established 32768 bind 32768)
[    0.262906] TCP: reno registered
[    0.262916] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.262939] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.263043] NET: Registered protocol family 1
[    0.263053] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.230157] pci 0000:01:05.0: Boot video device
[    1.230167] PCI: CLS 64 bytes, default 64
[    1.230207] Trying to unpack rootfs image as initramfs...
[    1.649327] Freeing initrd memory: 30640k freed
[    1.656758] PCI-DMA: Disabling AGP.
[    1.656857] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.656858] PCI-DMA: using GART IOMMU.
[    1.656861] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.659759] LVT offset 1 assigned for vector 0x400
[    1.659771] IBS: LVT offset 1 assigned
[    1.659798] perf: AMD IBS detected (0x0000001f)
[    1.660002] Initialise module verification
[    1.660047] audit: initializing netlink socket (disabled)
[    1.660062] type=2000 audit(1367609791.556:1): initialized
[    1.682975] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.684305] VFS: Disk quotas dquot_6.5.2
[    1.684344] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.684812] fuse init (API version 7.20)
[    1.684880] msgmni has been set to 7393
[    1.685325] Key type asymmetric registered
[    1.685327] Asymmetric key parser 'x509' registered
[    1.685351] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.685378] io scheduler noop registered
[    1.685380] io scheduler deadline registered (default)
[    1.685385] io scheduler cfq registered
[    1.685517] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    1.685634] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    1.685684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.685695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.685778] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.685783] ACPI: Power Button [PWRB]
[    1.685813] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.685815] ACPI: Power Button [PWRF]
[    1.686943] GHES: HEST is not enabled!
[    1.687056] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.688092] Linux agpgart interface v0.103
[    1.689119] brd: module loaded
[    1.689815] loop: module loaded
[    1.690097] libphy: Fixed MDIO Bus: probed
[    1.690142] tun: Universal TUN/TAP device driver, 1.6
[    1.690144] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.690183] PPP generic driver version 2.4.2
[    1.690221] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.690222] ehci-pci: EHCI PCI platform driver
[    1.690276] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.690282] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.690287] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.690299] ehci-pci 0000:00:12.2: debug port 1
[    1.690333] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe7ff800
[    1.701599] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.701629] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.701631] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.701633] usb usb1: Product: EHCI Host Controller
[    1.701635] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.701636] usb usb1: SerialNumber: 0000:00:12.2
[    1.701761] hub 1-0:1.0: USB hub found
[    1.701764] hub 1-0:1.0: 6 ports detected
[    1.701894] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.701901] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.701904] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.701916] ehci-pci 0000:00:13.2: debug port 1
[    1.701949] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe7ff400
[    1.713596] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.713620] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.713622] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.713623] usb usb2: Product: EHCI Host Controller
[    1.713625] usb usb2: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.713626] usb usb2: SerialNumber: 0000:00:13.2
[    1.713735] hub 2-0:1.0: USB hub found
[    1.713738] hub 2-0:1.0: 6 ports detected
[    1.713851] ehci-platform: EHCI generic platform driver
[    1.713864] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.713914] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.713920] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.713945] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
[    1.773533] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.773537] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.773539] usb usb3: Product: OHCI Host Controller
[    1.773541] usb usb3: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.773542] usb usb3: SerialNumber: 0000:00:12.0
[    1.773666] hub 3-0:1.0: USB hub found
[    1.773672] hub 3-0:1.0: 3 ports detected
[    1.773773] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.773778] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.773795] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
[    1.833469] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.833473] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.833474] usb usb4: Product: OHCI Host Controller
[    1.833476] usb usb4: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.833477] usb usb4: SerialNumber: 0000:00:12.1
[    1.833603] hub 4-0:1.0: USB hub found
[    1.833609] hub 4-0:1.0: 3 ports detected
[    1.833713] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.833718] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.833743] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    1.893411] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.893415] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.893416] usb usb5: Product: OHCI Host Controller
[    1.893418] usb usb5: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.893419] usb usb5: SerialNumber: 0000:00:13.0
[    1.893551] hub 5-0:1.0: USB hub found
[    1.893557] hub 5-0:1.0: 3 ports detected
[    1.893659] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.893664] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.893680] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7f7000
[    1.953358] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.953362] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.953363] usb usb6: Product: OHCI Host Controller
[    1.953365] usb usb6: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.953366] usb usb6: SerialNumber: 0000:00:13.1
[    1.953501] hub 6-0:1.0: USB hub found
[    1.953508] hub 6-0:1.0: 3 ports detected
[    1.953595] uhci_hcd: USB Universal Host Controller Interface driver
[    1.953656] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.954080] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.954092] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.954241] mousedev: PS/2 mouse device common for all mice
[    1.954349] rtc_cmos 00:02: RTC can wake from S4
[    1.954447] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.954470] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.954540] device-mapper: uevent: version 1.0.3
[    1.954595] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.954601] cpuidle: using governor ladder
[    1.954602] cpuidle: using governor menu
[    1.954605] ledtrig-cpu: registered to indicate activity on CPUs
[    1.954606] EFI Variables Facility v0.08 2004-May-17
[    1.954808] ashmem: initialized
[    1.954903] TCP: cubic registered
[    1.954975] NET: Registered protocol family 10
[    1.955105] NET: Registered protocol family 17
[    1.955112] Key type dns_resolver registered
[    1.955352] Loading module verification certificates
[    1.956266] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4fb521df0b0fa81f775431361b8076d5d0f1869a'
[    1.956276] registered taskstats version 1
[    1.958623] Key type trusted registered
[    1.960564] Key type encrypted registered
[    1.962924] rtc_cmos 00:02: setting system clock to 2013-05-03 19:36:32 UTC (1367609792)
[    1.962960] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    1.963905] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.964402] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.964405] EDD information not available.
[    1.965623] Freeing unused kernel memory: 992k freed
[    1.965832] Write protecting the kernel read-only data: 12288k
[    1.968715] Freeing unused kernel memory: 1176k freed
[    1.971557] Freeing unused kernel memory: 1080k freed
[    1.987099] udevd[111]: starting version 175
[    2.007697] Disabling lock debugging due to kernel taint
[    2.008257] ahci 0000:00:11.0: version 3.0
[    2.008403] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.008407] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    2.009593] scsi0 : ahci
[    2.009697] scsi1 : ahci
[    2.010389] scsi2 : ahci
[    2.011040] scsi3 : ahci
[    2.011088] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
[    2.011091] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
[    2.011094] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
[    2.011096] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
[    2.014626] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.014831] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    2.015008] r8169 0000:03:00.0 eth0: RTL8168e/8111e at 0xffffc9000064c000, 78:ac:c0:b3:b5:6c, XID 0c200000 IRQ 42
[    2.015011] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.026284] [drm] Initialized drm 1.1.0 20060810
[    2.034228] wmi: Mapper loaded
[    2.050041] [drm] radeon defaulting to kernel modesetting.
[    2.050044] [drm] radeon kernel modesetting enabled.
[    2.050322] [drm] initializing kernel modesetting (RS880 0x1002:0x9710 0x103C:0x2AB1).
[    2.050349] [drm] register mmio base: 0xFE8F0000
[    2.050350] [drm] register mmio size: 65536
[    2.051017] ATOM BIOS: BR34448.005
[    2.051037] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    2.051039] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    2.051393] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.051397] [drm] RAM width 32bits DDR
[    2.051817] [TTM] Zone  kernel: Available graphics memory: 1894476 kiB
[    2.051818] [TTM] Initializing pool allocator
[    2.051822] [TTM] Initializing DMA pool allocator
[    2.051852] [drm] radeon: 256M of VRAM memory ready
[    2.051853] [drm] radeon: 512M of GTT memory ready.
[    2.051865] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.051866] [drm] Driver supports precise vblank timestamp query.
[    2.051881] [drm] radeon: irq initialized.
[    2.051886] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.052880] [drm] Loading RS780 Microcode
[    2.076720] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[    2.076803] radeon 0000:01:05.0: WB enabled
[    2.076806] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880113bcac00
[    2.076808] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880113bcac0c
[    2.077043] radeon 0000:01:05.0: setting latency timer to 64
[    2.108691] [drm] ring test on 0 succeeded in 1 usecs
[    2.108749] [drm] ring test on 3 succeeded in 1 usecs
[    2.108827] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.108840] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.108991] [drm] Radeon Display Connectors
[    2.108992] [drm] Connector 0:
[    2.108993] [drm]   VGA-1
[    2.108995] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.108996] [drm]   Encoders:
[    2.108997] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.108998] [drm] Connector 1:
[    2.108999] [drm]   DVI-D-1
[    2.109000] [drm]   HPD1
[    2.109001] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.109002] [drm]   Encoders:
[    2.109003] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[    2.109023] [drm] radeon: power management initialized
[    2.167275] [drm] fb mappable at 0xD0142000
[    2.167278] [drm] vram apper at 0xD0000000
[    2.167279] [drm] size 5787648
[    2.167280] [drm] fb depth is 24
[    2.167281] [drm]    pitch is 6400
[    2.167379] fbcon: radeondrmfb (fb0) is primary device
[    2.321017] Console: switching to colour frame buffer device 200x56
[    2.329025] ata2: SATA link down (SStatus 0 SControl 300)
[    2.329091] ata4: SATA link down (SStatus 0 SControl 300)
[    2.333694] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    2.333696] radeon 0000:01:05.0: registered panic notifier
[    2.333763] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:05.0 on minor 0
[    2.500859] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.500898] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.501920] ata3.00: ATA-8: ST31000528AS, HP35, max UDMA/100
[    2.501924] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.503108] ata3.00: configured for UDMA/100
[    2.506955] ata1.00: ATA-8: ST640LM000 HM641JI, 2AJ10003, max UDMA/133
[    2.506959] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.513102] ata1.00: configured for UDMA/133
[    2.513248] scsi 0:0:0:0: Direct-Access     ATA      ST640LM000 HM641 2AJ1 PQ: 0 ANSI: 5
[    2.513377] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.513405] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.513409] sd 0:0:0:0: [sda] Write Protect is off
[    2.513411] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.513425] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.513552] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     HP35 PQ: 0 ANSI: 5
[    2.513642] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.513652] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.513668] sd 2:0:0:0: [sdb] Write Protect is off
[    2.513670] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.513687] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.560248]  sda: sda1 sda2 sda3
[    2.560782] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.578065]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 > sdb4
[    2.578594] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.584775] usb 2-6: new high-speed USB device number 2 using ehci-pci
[    2.656672] tsc: Refined TSC clocksource calibration: 2999.998 MHz
[    2.656676] Switching to clocksource tsc
[    2.732186] usb 2-6: New USB device found, idVendor=0bda, idProduct=0151
[    2.732190] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.732192] usb 2-6: Product: USB2.0-CRW
[    2.732194] usb 2-6: Manufacturer: Generic
[    2.732196] usb 2-6: SerialNumber: 20060413092100000
[    2.735712] Initializing USB Mass Storage driver...
[    2.735843] scsi4 : usb-storage 2-6:1.0
[    2.735925] usbcore: registered new interface driver usb-storage
[    2.735927] USB Mass Storage support registered.
[    2.868449] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    3.050300] usb 3-1: New USB device found, idVendor=04d9, idProduct=1605
[    3.050304] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.050306] usb 3-1: Product: USB Keyboard
[    3.050308] usb 3-1: Manufacturer:  
[    3.086326] usbcore: registered new interface driver usbhid
[    3.086329] usbhid: USB HID core driver
[    3.089266] input:   USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2
[    3.089710] hid-generic 0003:04D9:1605.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:12.0-1/input0
[    3.093319] input:   USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3
[    3.093423] hid-generic 0003:04D9:1605.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:12.0-1/input1
[    3.316018] usb 3-2: new full-speed USB device number 3 using ohci_hcd
[    3.488850] usb 3-2: New USB device found, idVendor=046d, idProduct=c52b
[    3.488854] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.488856] usb 3-2: Product: USB Receiver
[    3.488858] usb 3-2: Manufacturer: Logitech
[    3.512967] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-2/input2
[    3.517023] input: Logitech Unifying Device. Wireless PID:400a as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0005/input/input4
[    3.517152] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:400a] on usb-0000:00:12.0-2:1
[    3.736668] scsi 4:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    3.741661] scsi 4:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    3.746530] scsi 4:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    3.751399] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    3.752086] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.752208] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    3.752547] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    3.752738] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    3.776467] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    3.777236] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    3.778110] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    3.778988] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[    8.377541] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    8.377545] EXT4-fs (sda2): write access will be enabled during recovery
[    8.766209] EXT4-fs (sda2): recovery complete
[    8.773894] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   24.903842] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.953249] udevd[436]: starting version 175
[   25.364519] type=1400 audit(1367624215.922:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=576 comm="apparmor_parser"
[   25.364536] type=1400 audit(1367624215.922:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=577 comm="apparmor_parser"
[   25.364902] type=1400 audit(1367624215.922:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=576 comm="apparmor_parser"
[   25.364921] type=1400 audit(1367624215.922:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=577 comm="apparmor_parser"
[   25.365113] type=1400 audit(1367624215.922:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=576 comm="apparmor_parser"
[   25.365135] type=1400 audit(1367624215.922:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=577 comm="apparmor_parser"
[   25.803445] microcode: CPU0: patch_level=0x010000bf
[   25.803720] MCE: In-kernel MCE decoding enabled.
[   25.804552] lp: driver loaded but no devices found
[   25.805702] EDAC MC: Ver: 3.0.0
[   25.806292] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.807510] AMD64 EDAC driver v3.4.0
[   25.807540] EDAC amd64: DRAM ECC disabled.
[   25.807547] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   25.807547]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   25.807547]  (Note that use of the override may cause unknown side effects.)
[   25.812122] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   25.812187] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[   25.813837] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   25.813891] sp5100_tco: PCI Revision ID: 0x3c
[   25.813912] sp5100_tco: failed to find MMIO address, giving up.
[   25.820090] cfg80211: Calling CRDA to update world regulatory domain
[   25.865500] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   25.905812] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   25.905898] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   25.905939] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   25.905980] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   25.906023] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   25.906066] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   25.906108] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   25.906150] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   25.906421] snd_hda_intel 0000:01:05.1: setting latency timer to 64
[   25.913328] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1/input13
[   26.038704] microcode: CPU0: new patch_level=0x010000dc
[   26.038727] microcode: CPU1: patch_level=0x010000bf
[   26.038739] microcode: CPU1: new patch_level=0x010000dc
[   26.038754] microcode: CPU2: patch_level=0x010000bf
[   26.038765] microcode: CPU2: new patch_level=0x010000dc
[   26.038771] microcode: CPU3: patch_level=0x010000bf
[   26.038777] microcode: CPU3: new patch_level=0x010000dc
[   26.038843] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   26.049063] kvm: disabled by bios
[   26.050445] kvm: disabled by bios
[   26.078514] kvm: disabled by bios
[   26.082474] kvm: disabled by bios
[   26.169587] cfg80211: World regulatory domain updated:
[   26.169592] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.169594] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.169596] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.169597] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.169598] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.169600] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.978254] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   28.601907] init: failsafe main process (968) killed by TERM signal
[   28.972634] type=1400 audit(1367624219.534:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1065 comm="apparmor_parser"
[   28.973840] type=1400 audit(1367624219.534:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1065 comm="apparmor_parser"
[   28.974037] type=1400 audit(1367624219.534:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1065 comm="apparmor_parser"
[   28.980911] type=1400 audit(1367624219.542:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1066 comm="apparmor_parser"
[   29.194513] Bluetooth: Core ver 2.16
[   29.194538] NET: Registered protocol family 31
[   29.194539] Bluetooth: HCI device and connection manager initialized
[   29.194548] Bluetooth: HCI socket layer initialized
[   29.194550] Bluetooth: L2CAP socket layer initialized
[   29.194554] Bluetooth: SCO socket layer initialized
[   29.197626] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.197630] Bluetooth: BNEP filters: protocol multicast
[   29.197638] Bluetooth: BNEP socket layer initialized
[   29.198094] Bluetooth: RFCOMM TTY layer initialized
[   29.198107] Bluetooth: RFCOMM socket layer initialized
[   29.198109] Bluetooth: RFCOMM ver 1.11
[   29.636724] init: avahi-cups-reload main process (1107) terminated with status 1
[   29.683268] ppdev: user-space parallel port driver
[   29.757995] init: gdm main process (1190) killed by TERM signal
[   31.364865] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   31.365164] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   31.657433] r8169 0000:03:00.0 eth2: link down
[   31.657472] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   31.657792] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   34.358697] init: plymouth main process (269) killed by SEGV signal
[   34.741458] lib80211: common routines for IEEE802.11 drivers
[   34.741462] lib80211_crypt: registered algorithm 'NULL'
[   34.743529] wl: module license 'MIXED/Proprietary' taints kernel.
[   34.765128] init: plymouth-stop pre-start process (1486) terminated with status 1
[   57.255781] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   57.271304] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   57.475048] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   57.678820] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   57.882614] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   65.180027] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   65.187614] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   65.391301] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   65.595108] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   65.798888] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   66.998286] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   67.006042] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   67.209499] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   67.413311] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   67.617086] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   68.816324] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   68.824151] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   69.027732] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   69.231505] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   69.435309] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   76.732583] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   76.740323] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   76.943991] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   77.147805] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   77.351575] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   78.550813] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   78.558524] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   78.762184] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   78.965982] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   79.169792] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   86.463163] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   86.470778] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   86.674444] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   86.878286] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   87.082076] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   88.281278] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   88.289005] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   88.492712] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   88.696527] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   88.900403] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   90.099507] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   90.107279] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   90.310908] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   90.514706] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   90.718509] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   98.016321] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   98.023666] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[   98.227177] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[   98.430971] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[   98.634771] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[   99.834605] wlan1: authenticate with 00:1f:90:b4:ad:c0
[   99.841902] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  100.045426] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  100.249236] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  100.453021] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  113.849016] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  113.856823] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  114.059755] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  114.263535] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  114.467336] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  121.761781] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  121.768465] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  121.971965] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  122.175841] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  122.379617] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  122.417288] systemd-hostnamed[2602]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  123.579719] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  123.586629] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  123.790178] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  123.993976] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  124.197778] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  125.397779] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  125.405353] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  125.608408] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  125.812236] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  126.016040] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  133.309787] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  133.317119] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  133.520667] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  133.724433] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  133.928273] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  135.128119] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  135.135301] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  135.338899] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  135.542736] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  135.746554] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  149.138486] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  149.148582] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  149.349204] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  149.552953] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  149.756795] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out
[  163.148810] wlan1: authenticate with 00:1f:90:b4:ad:c0
[  163.155938] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 1/3)
[  163.359478] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 2/3)
[  163.563285] wlan1: direct probe to 00:1f:90:b4:ad:c0 (try 3/3)
[  163.767136] wlan1: authentication with 00:1f:90:b4:ad:c0 timed out

```

sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 00
       serial: ac:81:12:69:0c:9c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-19-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 05
       serial: 78:ac:c0:b3:b5:6c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff

```

iwlist scan
```

wlan1     No scan results

```

lsb_release -d
```

Description:	Ubuntu 13.04

```

uname -mr
```
3.8.0-19-generic x86_64
```

---

### Post by Hadaka on 2013-05-03
Hi, looking at your printout it looks like you have
a broadcom driver in there,so that should be removed.
please do.
```
sudo modprobe -rfv wl
cat /etc/modules
sudo modprobe rt2800pci
```
thanks.

Edit:

wl: module license 'MIXED/Proprietary' taints kernel
found this in your dmesg output..may have to end up
blacklist that module.

---

### Post by patman0623 on 2013-05-04
Yup, that did it. Old drivers are because I ported the hard drive from a laptop that had that wireless card about 3 months ago.

When/if I port the hard drive back to the laptop, is there a way to reinstall the broadcom driver?

---

### Post by Hadaka on 2013-05-04
Hi, glad that worked for you.
if you put the drive back,just reverse the process
```
sudo modprobe -rfv rt2800pci
```
and just to make sure the broadcom divers is there do.
```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```
and lastly, please mark this thread SOLVED.
how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by patman0623 on 2013-05-04
Well, the advice is much appreciated, but it appears I spoke too soon, and the problem is still occurring intermittently.

---

### Post by Hadaka on 2013-05-04
Hi, this is your wireless card..

Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
you'll notice its N speed only...no b/g/n. Sometimes this plays nice,other times it doesnt.
about the only suggestion i have,short of replaceing the card, it to see if you can possibly
adjust your routers stettings to omit N. Then also try..
```
modprobe -rfv rt2800pci
modprobe rt2800pci nohwcrypt=1 
```
this will hold till the first boot.
if that stops the dropouts then do..
```
sudo gedit /etc/modprobe.d/rt2800pci.conf
options rt2800pci nohwcrypt=1

```
enter that one line..save and close gedit.
good luck !

---

### Post by patman0623 on 2013-05-05
Thank you! :)

---

### Post by Hadaka on 2013-05-05
You're welome !

---

