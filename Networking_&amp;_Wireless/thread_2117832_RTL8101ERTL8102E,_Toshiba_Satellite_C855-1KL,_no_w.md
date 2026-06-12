---
title: "RTL8101E/RTL8102E, Toshiba Satellite C855-1KL, no wi-fi showing"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Susuris on 2013-02-19
Greetings! I recently purchased a laptop and have installed Xubuntu 12.04 on it. Amongst other annoying things (for example, not being able to shut down my laptop while it's connected to power cable) is the fact that my Network manager (Wicd) doesn't show any available wireless networks, although I'm sure they are there. It simply says "No Wireless Networks found". I hope you can give an advice on what to do.
[B]
1 ) Machine Brand and Model (PC/Laptop)[/B]:
Toshiba Satellite C855-1KL

**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     $ lspci  
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```$ lsusb

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 04f2:b307 Chicony Electronics Co., Ltd
```**3 ) check interface:**
     Code:
     $ ifconfig  
```
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:cc:d8:f7  
          inet addr:78.84.165.227  Bcast:78.84.191.255  Mask:255.255.224.0
          inet6 addr: fe80::4e72:b9ff:fecc:d8f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1588278 (1.5 MB)  TX bytes:199171 (199.1 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21266 (21.2 KB)  TX bytes:21266 (21.2 KB)

```$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```**4 ) Check for modules:**
     Code:
     $ lsmod 

```
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
rfcomm                 47604  16 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
sparse_keymap          13890  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  0 
snd                    79041  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
toshiba_bluetooth      12807  0 
i915                  477602  2 
psmouse                97485  0 
serio_raw              13211  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
btusb                  18332  2 
soundcore              15091  1 snd
mei                    41616  0 
i2c_algo_bit           13423  1 i915
bluetooth             180153  23 rfcomm,bnep,btusb
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
uas                    18180  0 
r8169                  62154  0 
usb_storage            49198  1 ums_realtek

```[B]

5 ) Kernel boot messages[/B]
     Code:
     $ dmesg 
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=c1a4b9b4-eee2-4f68-90cf-775c351c950c ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000a59ee000 (usable)
[    0.000000]  BIOS-e820: 00000000a59ee000 - 00000000a6177000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000a6177000 - 00000000a619a000 (usable)
[    0.000000]  BIOS-e820: 00000000a619a000 - 00000000a619f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000a619f000 - 00000000aa7bf000 (usable)
[    0.000000]  BIOS-e820: 00000000aa7bf000 - 00000000aaebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000aaebf000 - 00000000aafbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aafbf000 - 00000000aafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000aafff000 - 00000000ab000000 (usable)
[    0.000000]  BIOS-e820: 00000000ab000000 - 00000000afa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000014f600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: TOSHIBA SATELLITE C855-1KL/Type2 - Board Product Name1, BIOS 1.60 06/27/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x14f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0AB000000 mask FFF000000 uncachable
[    0.000000]   3 base 0AC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask FC0000000 write-back
[    0.000000]   7 base 140000000 mask FF0000000 write-back
[    0.000000]   8 base 14F600000 mask FFFE00000 uncachable
[    0.000000]   9 base 14F800000 mask FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xab000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe200] fe200
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000ab000000
[    0.000000]  0000000000 - 00ab000000 page 2M
[    0.000000] kernel direct mapping tables up to ab000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000014f600000
[    0.000000]  0100000000 - 014f600000 page 2M
[    0.000000] kernel direct mapping tables up to 14f600000 @ aa7bc000-aa7bf000
[    0.000000] RAMDISK: 364d6000 - 37263000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSASU)
[    0.000000] ACPI: XSDT 00000000aaffe210 0009C (v01 TOSASU TOSASU00 00000100      01000013)
[    0.000000] ACPI: FACP 00000000aaffa000 0010C (v05 TOSASU TOSASU00 00000100 ACPI 00040000)
[    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
[    0.000000] ACPI: DSDT 00000000aafdf000 17D26 (v01 TOSASU TOSASU00 00000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000aafb2000 00040
[    0.000000] ACPI: ECDT 00000000aaffd000 000C1 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 00000000aaffc000 00236 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000aaffb000 000A5 (v32 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 00000000aaff9000 00038 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000aaff8000 0008C (v03 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000aaff7000 0003C (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000aafde000 00176 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000aafdd000 00224 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafdb000 01068 (v01 INSYDE CR CRB   00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000aafd9000 00028 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 00000000aafd4000 00034 (v07 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 00000000aafd2000 00044 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafd1000 00979 (v01 INSYDE CR CRB   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafd0000 00A92 (v01 INSYDE CR CRB   00003000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000014f600000
[    0.000000] Initmem setup node 0 0000000000000000-000000014f600000
[    0.000000]   NODE_DATA [000000014f5fb000 - 000000014f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00053fffff] PMD -> [ffff88014ac00000-ffff88014ebfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0014f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000a59ee
[    0.000000]     0: 0x000a6177 -> 0x000a619a
[    0.000000]     0: 0x000a619f -> 0x000aa7bf
[    0.000000]     0: 0x000aafff -> 0x000ab000
[    0.000000]     0: 0x00100000 -> 0x0014f600
[    0.000000] On node 0 totalpages: 1020351
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 674930 pages, LIFO batch:31
[    0.000000]   Normal zone: 5080 pages used for memmap
[    0.000000]   Normal zone: 320040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000a59ee000 - 00000000a6177000
[    0.000000] PM: Registered nosave memory: 00000000a619a000 - 00000000a619f000
[    0.000000] PM: Registered nosave memory: 00000000aa7bf000 - 00000000aaebf000
[    0.000000] PM: Registered nosave memory: 00000000aaebf000 - 00000000aafbf000
[    0.000000] PM: Registered nosave memory: 00000000aafbf000 - 00000000aafff000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000afa00000
[    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at afa00000 (gap: afa00000:30600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88014f200000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 998882
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=c1a4b9b4-eee2-4f68-90cf-775c351c950c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3919204k/5494784k available (6569k kernel code, 1413380k absent, 162200k reserved, 6634k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2195.182 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.36 BogoMIPS (lpj=8780728)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000041] AppArmor: AppArmor initialized
[    0.000043] Yama: becoming mindful.
[    0.000367] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001398] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001846] Mount-cache hash table entries: 256
[    0.001958] Initializing cgroup subsys cpuacct
[    0.001963] Initializing cgroup subsys memory
[    0.001970] Initializing cgroup subsys devices
[    0.001972] Initializing cgroup subsys freezer
[    0.001974] Initializing cgroup subsys blkio
[    0.001979] Initializing cgroup subsys perf_event
[    0.002005] CPU: Physical Processor ID: 0
[    0.002007] CPU: Processor Core ID: 0
[    0.002012] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002013] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002016] mce: CPU supports 7 MCE banks
[    0.002028] CPU0: Thermal monitoring enabled (TM1)
[    0.002036] using mwait in idle threads.
[    0.004673] ACPI: Core revision 20110623
[    0.025405] ftrace: allocating 27033 entries in 107 pages
[    0.036126] x2apic not enabled, IRQ remapping init failed
[    0.036524] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076169] CPU0: Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz stepping 07
[    0.180164] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.180169] PEBS disabled due to CPU errata.
[    0.180171] ... version:                3
[    0.180173] ... bit width:              48
[    0.180174] ... generic registers:      4
[    0.180175] ... value mask:             0000ffffffffffff
[    0.180177] ... max period:             000000007fffffff
[    0.180178] ... fixed-purpose events:   3
[    0.180179] ... event mask:             000000070000000f
[    0.180328] NMI watchdog enabled, takes one hw-pmu counter.
[    0.180398] Booting Node   0, Processors  #1
[    0.180401] smpboot cpu 1: start_ip = 98000
[    0.288211] NMI watchdog enabled, takes one hw-pmu counter.
[    0.288298]  #2
[    0.288300] smpboot cpu 2: start_ip = 98000
[    0.395995] NMI watchdog enabled, takes one hw-pmu counter.
[    0.396071]  #3
[    0.396072] smpboot cpu 3: start_ip = 98000
[    0.503868] NMI watchdog enabled, takes one hw-pmu counter.
[    0.503897] Brought up 4 CPUs
[    0.503899] Total of 4 processors activated (17560.38 BogoMIPS).
[    0.507656] devtmpfs: initialized
[    0.508372] EVM: security.selinux
[    0.508373] EVM: security.SMACK64
[    0.508374] EVM: security.capability
[    0.508398] PM: Registering ACPI NVS region at a59ee000 (7901184 bytes)
[    0.508512] PM: Registering ACPI NVS region at a619a000 (20480 bytes)
[    0.508514] PM: Registering ACPI NVS region at aaebf000 (1048576 bytes)
[    0.509280] print_constraints: dummy: 
[    0.509310] RTC time: 17:39:03, date: 02/19/13
[    0.509341] NET: Registered protocol family 16
[    0.509430] Trying to unpack rootfs image as initramfs...
[    0.509437] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.509439] ACPI: bus type pci registered
[    0.509507] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.509510] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.576508] PCI: Using configuration type 1 for base access
[    0.577388] bio: create slab <bio-0> at 0
[    0.577472] ACPI: Added _OSI(Module Device)
[    0.577474] ACPI: Added _OSI(Processor Device)
[    0.577475] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.577477] ACPI: Added _OSI(Processor Aggregator Device)
[    0.579886] ACPI: EC: EC description table is found, configuring boot EC
[    0.582411] ACPI: Executed 1 blocks of module-level executable AML code
[    0.585880] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.757446] Freeing initrd memory: 13876k freed
[    1.263579] ACPI: SSDT 00000000aae18018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20120111)
[    1.264185] ACPI: Dynamic OEM Table Load:
[    1.264188] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20120111)
[    1.275286] ACPI: SSDT 00000000aae19a98 00303 (v01  PmRef    ApIst 00003000 INTL 20120111)
[    1.275915] ACPI: Dynamic OEM Table Load:
[    1.275917] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20120111)
[    1.287132] ACPI: SSDT 00000000aae17d98 00119 (v01  PmRef    ApCst 00003000 INTL 20120111)
[    1.287726] ACPI: Dynamic OEM Table Load:
[    1.287729] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20120111)
[    1.299605] ACPI: Interpreter enabled
[    1.299609] ACPI: (supports S0 S3 S4 S5)
[    1.299638] ACPI: Using IOAPIC for interrupt routing
[    1.337904] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    1.338311] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    1.338313] HEST: Table not found.
[    1.338316] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.338635] \_SB_.PCI0:_OSC invalid UUID
[    1.338637] _OSC request data:1 8 1f 
[    1.338641] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.339171] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.339173] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.339176] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.339179] pci_root PNP0A08:00: host bridge window [mem 0xafa00000-0xfeafffff]
[    1.339190] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.339228] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    1.339239] pci 0000:00:02.0: reg 10: [mem 0xc2000000-0xc23fffff 64bit]
[    1.339246] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.339251] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    1.339305] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
[    1.339329] pci 0000:00:14.0: reg 10: [mem 0xc2500000-0xc250ffff 64bit]
[    1.339404] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.339409] pci 0000:00:14.0: PME# disabled
[    1.339431] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
[    1.339455] pci 0000:00:16.0: reg 10: [mem 0xc2514000-0xc251400f 64bit]
[    1.339535] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.339539] pci 0000:00:16.0: PME# disabled
[    1.339575] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
[    1.339898] pci 0000:00:1a.0: reg 10: [mem 0xc2519000-0xc25193ff]
[    1.341719] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.341723] pci 0000:00:1a.0: PME# disabled
[    1.341749] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
[    1.341766] pci 0000:00:1b.0: reg 10: [mem 0xc2510000-0xc2513fff 64bit]
[    1.341837] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.341841] pci 0000:00:1b.0: PME# disabled
[    1.341865] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
[    1.341946] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.341951] pci 0000:00:1c.0: PME# disabled
[    1.341976] pci 0000:00:1c.1: [8086:1e12] type 1 class 0x000604
[    1.342058] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.342062] pci 0000:00:1c.1: PME# disabled
[    1.342086] pci 0000:00:1c.2: [8086:1e14] type 1 class 0x000604
[    1.342168] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.342172] pci 0000:00:1c.2: PME# disabled
[    1.342207] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
[    1.342516] pci 0000:00:1d.0: reg 10: [mem 0xc2518000-0xc25183ff]
[    1.344344] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.344349] pci 0000:00:1d.0: PME# disabled
[    1.344374] pci 0000:00:1f.0: [8086:1e59] type 0 class 0x000601
[    1.344505] pci 0000:00:1f.2: [8086:1e03] type 0 class 0x000106
[    1.344524] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    1.344533] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    1.344542] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    1.344551] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    1.344559] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    1.344568] pci 0000:00:1f.2: reg 24: [mem 0xc2517000-0xc25177ff]
[    1.344615] pci 0000:00:1f.2: PME# supported from D3hot
[    1.344619] pci 0000:00:1f.2: PME# disabled
[    1.344639] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
[    1.344656] pci 0000:00:1f.3: reg 10: [mem 0xc2515000-0xc25150ff 64bit]
[    1.344678] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
[    1.344756] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.344846] pci 0000:02:00.0: [10ec:8723] type 0 class 0x000280
[    1.344875] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    1.344925] pci 0000:02:00.0: reg 18: [mem 0xc2400000-0xc2403fff 64bit]
[    1.345078] pci 0000:02:00.0: supports D1 D2
[    1.345080] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.345088] pci 0000:02:00.0: PME# disabled
[    1.350908] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.350918] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.350928] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc24fffff]
[    1.351043] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    1.351063] pci 0000:03:00.0: reg 10: [io  0x2000-0x20ff]
[    1.351099] pci 0000:03:00.0: reg 18: [mem 0xc0004000-0xc0004fff 64bit pref]
[    1.351122] pci 0000:03:00.0: reg 20: [mem 0xc0000000-0xc0003fff 64bit pref]
[    1.351216] pci 0000:03:00.0: supports D1 D2
[    1.351218] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.351224] pci 0000:03:00.0: PME# disabled
[    1.358885] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.358895] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.358905] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.358920] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.358961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.359102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.359131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.359159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.359254] \_SB_.PCI0:_OSC invalid UUID
[    1.359255] _OSC request data:1 1f 1f 
[    1.359259]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.359300] \_SB_.PCI0:_OSC invalid UUID
[    1.359301] _OSC request data:1 0 1d 
[    1.359304]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.359306] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.363288] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.363334] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.363377] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.363419] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.363460] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.363504] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.363546] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.363588] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.363687] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.363693] vgaarb: loaded
[    1.363694] vgaarb: bridge control possible 0000:00:02.0
[    1.363780] i2c-core: driver [aat2870] using legacy suspend method
[    1.363782] i2c-core: driver [aat2870] using legacy resume method
[    1.363835] SCSI subsystem initialized
[    1.363882] libata version 3.00 loaded.
[    1.363919] usbcore: registered new interface driver usbfs
[    1.363929] usbcore: registered new interface driver hub
[    1.363950] usbcore: registered new device driver usb
[    1.364021] PCI: Using ACPI for IRQ routing
[    1.370829] PCI: pci_cache_line_size set to 64 bytes
[    1.370904] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.370906] reserve RAM buffer: 00000000a59ee000 - 00000000a7ffffff 
[    1.370908] reserve RAM buffer: 00000000a619a000 - 00000000a7ffffff 
[    1.370910] reserve RAM buffer: 00000000aa7bf000 - 00000000abffffff 
[    1.370912] reserve RAM buffer: 00000000ab000000 - 00000000abffffff 
[    1.370914] reserve RAM buffer: 000000014f600000 - 000000014fffffff 
[    1.371001] NetLabel: Initializing
[    1.371003] NetLabel:  domain hash size = 128
[    1.371004] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.371014] NetLabel:  unlabeled traffic allowed by default
[    1.371060] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.371066] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.373078] Switching to clocksource hpet
[    1.378657] AppArmor: AppArmor Filesystem Enabled
[    1.378682] pnp: PnP ACPI init
[    1.378695] ACPI: bus type pnp registered
[    1.378999] pnp 00:00: [bus 00-fe]
[    1.379002] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.379004] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.379006] pnp 00:00: [io  0x0d00-0xffff window]
[    1.379008] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.379010] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.379011] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.379013] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.379015] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.379017] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.379019] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.379021] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.379023] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.379025] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.379027] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.379028] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.379030] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.379032] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.379034] pnp 00:00: [mem 0xafa00000-0xfeafffff window]
[    1.379036] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    1.379102] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.379126] pnp 00:01: [io  0x0000-0x001f]
[    1.379128] pnp 00:01: [io  0x0081-0x0091]
[    1.379129] pnp 00:01: [io  0x0093-0x009f]
[    1.379131] pnp 00:01: [io  0x00c0-0x00df]
[    1.379133] pnp 00:01: [dma 4]
[    1.379154] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.379161] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.379184] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.379272] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.379293] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.379302] pnp 00:04: [io  0x00f0]
[    1.379311] pnp 00:04: [irq 13]
[    1.379331] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.379341] pnp 00:05: [io  0x002e-0x002f]
[    1.379342] pnp 00:05: [io  0x004e-0x004f]
[    1.379344] pnp 00:05: [io  0x0061]
[    1.379345] pnp 00:05: [io  0x0063]
[    1.379347] pnp 00:05: [io  0x0065]
[    1.379348] pnp 00:05: [io  0x0067]
[    1.379350] pnp 00:05: [io  0x0070]
[    1.379351] pnp 00:05: [io  0x0080]
[    1.379352] pnp 00:05: [io  0x0092]
[    1.379354] pnp 00:05: [io  0x00b2-0x00b3]
[    1.379356] pnp 00:05: [io  0x025c-0x025d]
[    1.379357] pnp 00:05: [io  0x0680-0x069f]
[    1.379359] pnp 00:05: [io  0x1000-0x100f]
[    1.379360] pnp 00:05: [io  0xffff]
[    1.379362] pnp 00:05: [io  0xffff]
[    1.379363] pnp 00:05: [io  0x0400-0x0453]
[    1.379365] pnp 00:05: [io  0x0458-0x047f]
[    1.379366] pnp 00:05: [io  0x0500-0x057f]
[    1.379368] pnp 00:05: [io  0x164e-0x164f]
[    1.379407] system 00:05: [io  0x025c-0x025d] has been reserved
[    1.379409] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.379412] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.379414] system 00:05: [io  0xffff] has been reserved
[    1.379416] system 00:05: [io  0xffff] has been reserved
[    1.379418] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.379420] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.379422] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.379424] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.379427] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.379435] pnp 00:06: [io  0x0070-0x0077]
[    1.379440] pnp 00:06: [irq 8]
[    1.379460] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.379484] pnp 00:07: [io  0x0454-0x0457]
[    1.379515] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.379518] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.379530] pnp 00:08: [io  0x0060]
[    1.379532] pnp 00:08: [io  0x0064]
[    1.379537] pnp 00:08: [irq 1]
[    1.379556] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.379571] pnp 00:09: [irq 12]
[    1.379593] pnp 00:09: Plug and Play ACPI device, IDs TOS0310 TOS0220 TTP0100 PNP0f13 (active)
[    1.379742] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.379744] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.379746] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.379747] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.379749] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.379751] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.379753] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.379754] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.379756] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.379758] pnp 00:0a: [mem 0xafa00000-0xafa00fff]
[    1.379793] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.379795] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.379798] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.379800] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.379802] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.379805] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.379807] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.379810] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.379812] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.379814] system 00:0a: [mem 0xafa00000-0xafa00fff] has been reserved
[    1.379817] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.380034] pnp 00:0b: [mem 0x20000000-0x201fffff]
[    1.380035] pnp 00:0b: [mem 0x40000000-0x401fffff]
[    1.380083] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
[    1.380085] system 00:0b: [mem 0x40000000-0x401fffff] has been reserved
[    1.380088] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.380142] pnp: PnP ACPI: found 12 devices
[    1.380144] ACPI: ACPI bus type pnp unregistered
[    1.386759] PCI: max bus depth: 1 pci_try_num: 2
[    1.386790] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.386802] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.386806] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.386812] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc24fffff]
[    1.386821] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.386824] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.386830] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.386835] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.386854] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.386861] pci 0000:00:1c.0: setting latency timer to 64
[    1.386872] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.386877] pci 0000:00:1c.1: setting latency timer to 64
[    1.386887] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.386891] pci 0000:00:1c.2: setting latency timer to 64
[    1.386896] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.386898] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.386900] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.386902] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    1.386904] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    1.386906] pci_bus 0000:02: resource 1 [mem 0xc2400000-0xc24fffff]
[    1.386908] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    1.386910] pci_bus 0000:03: resource 1 [mem 0xc1000000-0xc1ffffff]
[    1.386912] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.386939] NET: Registered protocol family 2
[    1.387054] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.387754] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.389568] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.389788] TCP: Hash tables configured (established 524288 bind 65536)
[    1.389790] TCP reno registered
[    1.389800] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.389820] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.389904] NET: Registered protocol family 1
[    1.389917] pci 0000:00:02.0: Boot video device
[    1.389935] pci 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.391200] pci 0000:00:14.0: PCI INT A disabled
[    1.391213] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.405026] pci 0000:00:1a.0: PCI INT A disabled
[    1.405073] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.420996] pci 0000:00:1d.0: PCI INT A disabled
[    1.421030] PCI: CLS 64 bytes, default 64
[    1.421035] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.421041] Placing 64MB software IO TLB between ffff8800a67bc000 - ffff8800aa7bc000
[    1.421046] software IO TLB at phys 0xa67bc000 - 0xaa7bc000
[    1.421068] Simple Boot Flag at 0x44 set to 0x1
[    1.421534] audit: initializing netlink socket (disabled)
[    1.421541] type=2000 audit(1361295543.256:1): initialized
[    1.445132] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.446829] VFS: Disk quotas dquot_6.5.2
[    1.446875] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.447295] fuse init (API version 7.17)
[    1.447373] msgmni has been set to 7681
[    1.447710] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.447735] io scheduler noop registered
[    1.447737] io scheduler deadline registered
[    1.447763] io scheduler cfq registered (default)
[    1.447984] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.448003] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.448046] intel_idle: MWAIT substates: 0x21120
[    1.448048] intel_idle: v0.4 model 0x2A
[    1.448049] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.448148] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.448212] ACPI: AC Adapter [AC0] (on-line)
[    1.448358] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input0
[    1.448363] ACPI: Power Button [PWRB]
[    1.448401] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.449073] ACPI: Lid Switch [LID]
[    1.449110] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.449114] ACPI: Power Button [PWRF]
[    1.449151] ACPI: duty_cycle spans bit 4
[    1.449178] ACPI: duty_cycle spans bit 4
[    1.449198] ACPI: duty_cycle spans bit 4
[    1.449219] ACPI: duty_cycle spans bit 4
[    1.450983] thermal LNXTHERM:00: registered as thermal_zone0
[    1.450986] ACPI: Thermal Zone [THRM] (50 C)
[    1.451000] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.451007] ACPI: Battery Slot [BAT0] (battery present)
[    1.451033] ERST: Table is not found!
[    1.451035] GHES: HEST is not enabled!
[    1.451099] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.458289] ACPI: Battery Slot [BAT0] (battery present)
[    1.673054] Linux agpgart interface v0.103
[    1.673120] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.673271] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.674562] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.674671] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.675852] brd: module loaded
[    1.676466] loop: module loaded
[    1.676569] ahci 0000:00:1f.2: version 3.0
[    1.676590] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.676631] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.676656] ahci: SSS flag set, parallel bus scan disabled
[    1.688731] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1d impl SATA mode
[    1.688740] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    1.688751] ahci 0000:00:1f.2: setting latency timer to 64
[    1.713143] scsi0 : ahci
[    1.713224] scsi1 : ahci
[    1.713293] scsi2 : ahci
[    1.713354] scsi3 : ahci
[    1.713414] scsi4 : ahci
[    1.713476] scsi5 : ahci
[    1.713560] ata1: SATA max UDMA/133 abar m2048@0xc2517000 port 0xc2517100 irq 40
[    1.713562] ata2: DUMMY
[    1.713565] ata3: SATA max UDMA/133 abar m2048@0xc2517000 port 0xc2517200 irq 40
[    1.713569] ata4: SATA max UDMA/133 abar m2048@0xc2517000 port 0xc2517280 irq 40
[    1.713572] ata5: SATA max UDMA/133 abar m2048@0xc2517000 port 0xc2517300 irq 40
[    1.713574] ata6: DUMMY
[    1.713871] Fixed MDIO Bus: probed
[    1.713885] tun: Universal TUN/TAP device driver, 1.6
[    1.713886] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.713938] PPP generic driver version 2.4.2
[    1.714029] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.714043] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.714062] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.714066] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.714110] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.714137] ehci_hcd 0000:00:1a.0: debug port 2
[    1.718015] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.718031] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc2519000
[    1.732644] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.732826] hub 1-0:1.0: USB hub found
[    1.732830] hub 1-0:1.0: 2 ports detected
[    1.732882] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.732896] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.732900] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.732947] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.732967] ehci_hcd 0000:00:1d.0: debug port 2
[    1.736854] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.736867] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xc2518000
[    1.752623] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.752790] hub 2-0:1.0: USB hub found
[    1.752795] hub 2-0:1.0: 2 ports detected
[    1.752843] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.752852] uhci_hcd: USB Universal Host Controller Interface driver
[    1.752875] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.752904] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.752908] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.752950] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.753035] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.753047] xhci_hcd 0000:00:14.0: irq 21, io mem 0xc2500000
[    1.753095] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.753200] xHCI xhci_add_endpoint called for root hub
[    1.753201] xHCI xhci_check_bandwidth called for root hub
[    1.753223] hub 3-0:1.0: USB hub found
[    1.753230] hub 3-0:1.0: 4 ports detected
[    1.753277] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.753316] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.753392] xHCI xhci_add_endpoint called for root hub
[    1.753394] xHCI xhci_check_bandwidth called for root hub
[    1.753414] hub 4-0:1.0: USB hub found
[    1.753421] hub 4-0:1.0: 4 ports detected
[    1.788662] usbcore: registered new interface driver libusual
[    1.788712] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.790475] i8042: Detected active multiplexing controller, rev 1.1
[    1.792638] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.792643] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.792667] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.792685] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.792704] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.792810] mousedev: PS/2 mouse device common for all mice
[    1.792973] rtc_cmos 00:06: RTC can wake from S4
[    1.793076] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.793104] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.793167] device-mapper: uevent: version 1.0.3
[    1.793230] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.793341] cpuidle: using governor ladder
[    1.793501] cpuidle: using governor menu
[    1.793502] EFI Variables Facility v0.08 2004-May-17
[    1.793668] TCP cubic registered
[    1.793747] NET: Registered protocol family 10
[    1.794094] NET: Registered protocol family 17
[    1.794099] Registering the dns_resolver key type
[    1.794231] PM: Hibernation image not present or could not be loaded.
[    1.794241] registered taskstats version 1
[    1.800357]   Magic number: 1:339:694
[    1.800461] rtc_cmos 00:06: setting system clock to 2013-02-19 17:39:04 UTC (1361295544)
[    1.801263] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.801265] EDD information not available.
[    1.807448] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.032415] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.044406] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.089303] ata1.00: ATA-8: TOSHIBA MK5075GSX, GT001M, max UDMA/100
[    2.089306] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.090340] ata1.00: configured for UDMA/100
[    2.090493] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK5075GS GT00 PQ: 0 ANSI: 5
[    2.090692] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.090725] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.090794] sd 0:0:0:0: [sda] Write Protect is off
[    2.090797] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.090826] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.166031]  sda: sda1 sda2 < sda5 >
[    2.167057] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.177239] hub 1-1:1.0: USB hub found
[    2.177389] hub 1-1:1.0: 6 ports detected
[    2.288141] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.407999] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.412033] ata3.00: ATAPI: TSSTcorp CDDVDW SN-208AB, TO04, max UDMA/100
[    2.419973] Refined TSC clocksource calibration: 2195.013 MHz.
[    2.419986] Switching to clocksource tsc
[    2.421107] hub 2-1:1.0: USB hub found
[    2.421241] hub 2-1:1.0: 6 ports detected
[    2.421914] ata3.00: configured for UDMA/100
[    2.427147] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-208AB  TO04 PQ: 0 ANSI: 5
[    2.441575] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.441585] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.441836] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.441929] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.587796] usb 3-3: new full-speed USB device number 2 using xhci_hcd
[    2.675862] usb 1-1.1: new high-speed USB device number 3 using ehci_hcd
[    2.759614] ata4: SATA link down (SStatus 0 SControl 300)
[    2.788344] Initializing USB Mass Storage driver...
[    2.788393] usbcore: registered new interface driver usb-storage
[    2.788395] USB Mass Storage support registered.
[    2.855655] usb 1-1.3: new high-speed USB device number 4 using ehci_hcd
[    3.079252] ata5: SATA link down (SStatus 0 SControl 300)
[    3.080794] Freeing unused kernel memory: 924k freed
[    3.080894] Write protecting the kernel read-only data: 12288k
[    3.085365] Freeing unused kernel memory: 1604k freed
[    3.088835] Freeing unused kernel memory: 1196k freed
[    3.103715] udevd[110]: starting version 175
[    3.148161] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.148188] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.148226] r8169 0000:03:00.0: setting latency timer to 64
[    3.148306] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    3.148794] r8169 0000:03:00.0: eth0: RTL8105e at 0xffffc9000064c000, 4c:72:b9:cc:d8:f7, XID 00c00000 IRQ 42
[    3.152755] usbcore: registered new interface driver uas
[    3.176662] scsi6 : usb-storage 1-1.1:1.0
[    3.176743] usbcore: registered new interface driver ums-realtek
[    3.257640] usb 1-1.1: USB disconnect, device number 3
[    3.452293] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.248984] Adding 4079612k swap on /dev/sda5.  Priority:-1 extents:1 across:4079612k 
[   11.253295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.285314] udevd[344]: starting version 175
[   11.337063] Bluetooth: Core ver 2.16
[   11.337571] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   11.338280] lp: driver loaded but no devices found
[   11.339235] NET: Registered protocol family 31
[   11.339239] Bluetooth: HCI device and connection manager initialized
[   11.339243] Bluetooth: HCI socket layer initialized
[   11.339245] Bluetooth: L2CAP socket layer initialized
[   11.339254] Bluetooth: SCO socket layer initialized
[   11.339366] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.339375] mei 0000:00:16.0: setting latency timer to 64
[   11.339446] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   11.339671] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.344173] usbcore: registered new interface driver btusb
[   11.346899] [drm] Initialized drm 1.1.0 20060810
[   11.349458] Linux video capture interface: v2.00
[   11.353818] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.353824] i915 0000:00:02.0: setting latency timer to 64
[   11.356286] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera - HD (04f2:b307)
[   11.360545] type=1400 audit(1361295554.067:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=428 comm="apparmor_parser"
[   11.360966] type=1400 audit(1361295554.067:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=428 comm="apparmor_parser"
[   11.361210] type=1400 audit(1361295554.067:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=428 comm="apparmor_parser"
[   11.367431] input: TOSHIBA Web Camera - HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[   11.367521] usbcore: registered new interface driver uvcvideo
[   11.367524] USB Video Class driver (1.1.1)
[   11.371913] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   11.371971] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   11.409165] wmi: Mapper loaded
[   11.465968] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[   11.465973] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   11.472117] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   11.472124] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.472126] [drm] Driver supports precise vblank timestamp query.
[   11.472457] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[   11.472483] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.972425] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.061646] fbcon: inteldrmfb (fb0) is primary device
[   12.061835] Console: switching to colour frame buffer device 170x48
[   12.061866] fb0: inteldrmfb frame buffer device
[   12.061869] drm: registered panic notifier
[   12.064001] acpi device:3e: registered as cooling_device4
[   12.064228] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   12.064283] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.064334] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.064519] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.064600] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.064637] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   12.074950] init: failsafe main process (814) killed by TERM signal
[   12.078534] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   12.113064] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   12.262717] ppdev: user-space parallel port driver
[   12.288832] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.288836] Bluetooth: BNEP filters: protocol multicast
[   12.292931] Bluetooth: RFCOMM TTY layer initialized
[   12.292938] Bluetooth: RFCOMM socket layer initialized
[   12.292940] Bluetooth: RFCOMM ver 1.11
[   12.297877] type=1400 audit(1361295555.007:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=888 comm="apparmor_parser"
[   12.298444] type=1400 audit(1361295555.007:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=888 comm="apparmor_parser"
[   12.563720] r8169 0000:03:00.0: eth0: link down
[   12.564030] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.564332] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.616678] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[   12.616766] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.616911] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.617053] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.865600] type=1400 audit(1361295555.575:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=943 comm="apparmor_parser"
[   12.865890] type=1400 audit(1361295555.575:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=944 comm="apparmor_parser"
[   12.866373] type=1400 audit(1361295555.575:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=944 comm="apparmor_parser"
[   12.866654] type=1400 audit(1361295555.575:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=944 comm="apparmor_parser"
[   12.867925] type=1400 audit(1361295555.575:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=947 comm="apparmor_parser"
[   13.496945] init: plymouth-stop pre-start process (1214) terminated with status 1
[ 1739.505634] r8169 0000:03:00.0: eth0: link up
[ 1739.506440] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1749.943800] eth0: no IPv6 routers present

```**6 ) Network configuration**
     Code:
     $ sudo lshw -C network 
```
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c2400000-c2403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 4c:72:b9:cc:d8:f7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=78.84.165.227 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff

```[B]


7 ) Scan for networks:[/B]
     Code:
     $ iwlist scan 
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```[B]

8 ) Ubuntu Version: [/B]
     Code:
     $ lsb_release -d 
```
Description:    Ubuntu 12.04.2 LTS
```[B]

9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
     Code:
     $ uname -mr 
```
3.2.0-37-generic x86_64

```**10 ) Restarting the network:**
     Code:
    $ sudo /etc/init.d/networking restart


```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

---

### Post by chili555 on 2013-02-19
Your wireless device is this:> Realtek Semiconductor Co., Ltd. Device 8723And the instructions are here: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by Susuris on 2013-02-23
chili555, those instructions don't work for me. I installed two of the provided drivers, but nothing has changed. Furthermore, I now can't uninstall them. When I right click on a folder containing the driver and open Terminal using the given menu, I type "make uninstall", but nothing happens.

It looks like this:
```
root@Nelabais:/home/pauls/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# make uninstall
root@Nelabais:/home/pauls/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# 

```

---

### Post by chili555 on 2013-02-23
What I'd really like to see is the result of sequence here:```
cd /home/pauls/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
sudo su
make clean
make
make install
modprobe rtl8723e
exit
```Please post all the terminal output so we can diagnose.

---

