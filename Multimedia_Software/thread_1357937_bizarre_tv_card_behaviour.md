---
title: "bizarre tv card behaviour"
date: 2009-12-17
forum: Multimedia Software
---

### Post by cricka15 on 2009-12-17
hey everyone, recently started dualbooting XP and Xubuntu 9.10, been getting a long fine with adding packages etc etc not come across any serious problems that a little searching wouldn't fix until now.

I created channels.conf file to use with VLC to watch TV, this worked fine the first night, but now it will only work if I first reboot into XP, then reboot back to xubuntu :o

the card is a hauppauge hvr-1110, im guessing something isn't going right at startup but i've no idea what or how to find out, i've included output of lsmod and dmesg in case these are useful to someone.

i think it might have something to do with:
```
timeout waiting for DSP ready
```which flashes up just before desktop is loaded.

anyone got any ideas please?

thanks

/cricka15

i used this to scan for channels and populate channels.conf:
```
scan /usr/share/dvb/dvb-t/uk-Belmont -o zap | tee ~/channels.conf
```output of lsmod:

card details from sudo lspci -v

```

06:02.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: Hauppauge computer works Inc. Device 6701
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at f3b10000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```

output of lsmod

```

Module                  Size  Used by
xt_limit                3236  8 
xt_tcpudp               3616  7 
ipt_LOG                 6404  8 
ipt_MASQUERADE          2944  0 
xt_DSCP                 3744  0 
ipt_REJECT              3584  1 
nf_conntrack_irc        6552  0 
nf_conntrack_ftp        9016  0 
xt_state                2432  6 
arc4                    2144  2 
ecb                     3296  2 
tda1004x               17956  1 
saa7134_dvb            26860  0 
videobuf_dvb            8452  1 saa7134_dvb
dvb_core              104528  1 videobuf_dvb
saa7134_alsa           14560  2 
ir_kbd_i2c              8336  0 
snd_hda_codec_realtek   277860  1 
tda827x                11492  2 
snd_hda_intel          31880  4 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  3 snd_pcm_oss
snd_pcm                93160  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
iptable_nat             6656  0 
nf_nat                 22164  2 ipt_MASQUERADE,iptable_nat
tda8290                15748  1 
nf_conntrack_ipv4      16376  9 iptable_nat,nf_nat
nf_conntrack           80832  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
snd_seq_oss            33440  0 
ath5k                 136680  0 
mac80211              209912  1 ath5k
led_class               5256  1 ath5k
tuner                  24520  1 
ath                    10304  1 ath5k
snd_seq_midi            8192  0 
iptable_mangle          4192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  1 
ppdev                   8232  0 
ip_tables              21200  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               25832  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0 
serio_raw               6596  0 
parport_pc             37352  1 
cfg80211              109144  3 ath5k,mac80211,ath
saa7134               178356  2 saa7134_dvb,saa7134_alsa
ir_common              52740  2 ir_kbd_i2c,saa7134
v4l2_common            21024  2 tuner,saa7134
videodev               43360  3 tuner,saa7134,v4l2_common
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
videobuf_dma_sg        14436  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          21188  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               14884  1 saa7134
nvidia              10316904  26 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
snd                    77096  21 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  3 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
intel_agp              32816  0

```

output of dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=61308714-d3d4-4da1-8a94-c75660d7d164 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe2f800 (usable)
[    0.000000]  BIOS-e820: 000000007fe2f800 - 000000007fe3ea27 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff2f800 - 000000007ff30000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7fe2f max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 080000000 mask F80000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fe2f800 (usable)
[    0.000000]  modified: 000000007fe2f800 - 000000007fe3ea27 (ACPI NVS)
[    0.000000]  modified: 000000007ff2f800 - 000000007ff30000 (ACPI NVS)
[    0.000000]  modified: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  modified: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000feda0000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007fe2f000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fe2f000 page 4k
[    0.000000] kernel direct mapping tables up to 7fe2f000 @ 8000-c000
[    0.000000] RAMDISK: 3786e000 - 37fefedd
[    0.000000] ACPI: RSDP 00000000000f4ea0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ff30000 0003C (v01 INTEL  D915PCY  20060926 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ff30200 00081 (v02 INTEL  D915PCY  20060926 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ff30440 05B76 (v01 INTEL  D915PCY  00000001 INTL 02002026)
[    0.000000] ACPI: FACS 000000007ff40000 00040
[    0.000000] ACPI: APIC 000000007ff30390 00068 (v01 INTEL  D915PCY  20060926 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007ff30400 0003C (v01 INTEL  D915PCY  20060926 MSFT 00000097)
[    0.000000] ACPI: ASF! 000000007ff35fc0 00099 (v16 LEGEND I865PASF 00000001 INTL 02002026)
[    0.000000] ACPI: TCPA 000000007ff36060 00032 (v01 INTEL  TBLOEMID 00000001 MSFT 00000097)
[    0.000000] ACPI: WDDT 000000007ff36092 00040 (v01 INTEL  OEMWDDT  00000001 INTL 02002026)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe2f000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe2f000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001efc7] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fe2f000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [003786e000 - 0037fefedd]          RAMDISK ==> [003786e000 - 0037fefedd]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5124]              BRK ==> [00019e5000 - 00019e5124]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe2f
[    0.000000] On node 0 totalpages: 523721
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7106 pages used for memmap
[    0.000000]   DMA32 zone: 512621 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f6000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516458
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=61308714-d3d4-4da1-8a94-c75660d7d164 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2047980k/2095292k available (5315k kernel code, 408k absent, 46904k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3199.837 MHz processor.
[    0.001794] Console: colour VGA+ 80x25
[    0.001798] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010010] Calibrating delay loop (skipped), value calculated using timer frequency.. 6399.67 BogoMIPS (lpj=31998370)
[    0.010042] Security Framework initialized
[    0.010067] AppArmor: AppArmor initialized
[    0.010363] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011523] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012071] Mount-cache hash table entries: 256
[    0.012244] Initializing cgroup subsys ns
[    0.012250] Initializing cgroup subsys cpuacct
[    0.012254] Initializing cgroup subsys memory
[    0.012261] Initializing cgroup subsys freezer
[    0.012264] Initializing cgroup subsys net_cls
[    0.012284] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.012287] CPU: L2 cache: 2048K
[    0.012292] CPU 0/0x0 -> Node 0
[    0.012295] CPU: Physical Processor ID: 0
[    0.012297] CPU: Processor Core ID: 0
[    0.012301] mce: CPU supports 4 MCE banks
[    0.012313] CPU0: Thermal monitoring enabled (TM1)
[    0.012318] using mwait in idle threads.
[    0.012320] Performance Counters: no PMU driver, software counters only.
[    0.015049] ACPI: Core revision 20090521
[    0.026384] Setting APIC routing to flat
[    0.026702] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.126722] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6400.11 BogoMIPS (lpj=32000571)
[    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 4 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.280987] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[    0.281001] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290026] Brought up 2 CPUs
[    0.290031] Total of 2 processors activated (12799.78 BogoMIPS).
[    0.290084] CPU0 attaching sched-domain:
[    0.290088]  domain 0: span 0-1 level SIBLING
[    0.290091]   groups: 0 1
[    0.290098] CPU1 attaching sched-domain:
[    0.290100]  domain 0: span 0-1 level SIBLING
[    0.290103]   groups: 1 0
[    0.290193] Booting paravirtualized kernel on bare hardware
[    0.290219] regulator: core version 0.5
[    0.290219] Time: 23:25:19  Date: 12/17/09
[    0.290219] NET: Registered protocol family 16
[    0.290268] ACPI: bus type pci registered
[    0.290351] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.290355] PCI: MCFG area at e0000000 reserved in E820
[    0.294605] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.294607] PCI: Using configuration type 1 for base access
[    0.295691] bio: create slab <bio-0> at 0
[    0.295691] ACPI: EC: Look up EC in DSDT
[    2.302773] ACPI: Interpreter enabled
[    2.302778] ACPI: (supports S0 S1 S4 S5)
[    2.302804] ACPI: Using IOAPIC for interrupt routing
[    2.311212] ACPI: Power Resource [URP1] (off)
[    2.311260] ACPI: Power Resource [FDDP] (off)
[    2.311310] ACPI: Power Resource [LPTP] (off)
[    2.311355] ACPI: Power Resource [URP2] (off)
[    2.311825] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    2.313355] ACPI Warning: \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 20090521 nspredef-328
[    2.313366] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    2.313497] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    2.313502] pci 0000:00:01.0: PME# disabled
[    2.313574] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3afc000-0xf3afffff]
[    2.313619] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.313624] pci 0000:00:1b.0: PME# disabled
[    2.313687] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.313692] pci 0000:00:1c.0: PME# disabled
[    2.313756] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    2.313761] pci 0000:00:1c.1: PME# disabled
[    2.313826] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    2.313830] pci 0000:00:1c.2: PME# disabled
[    2.313895] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    2.313899] pci 0000:00:1c.3: PME# disabled
[    2.313952] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]
[    2.314005] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
[    2.314063] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
[    2.314117] pci 0000:00:1d.3: reg 20 io port: [0xd800-0xd81f]
[    2.314176] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3afbc00-0xf3afbfff]
[    2.314230] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    2.314235] pci 0000:00:1d.7: PME# disabled
[    2.314353] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    2.314361] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    2.314366] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    2.314370] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0680-06ff
[    2.314374] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 4700-470f
[    2.314401] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    2.314408] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    2.314415] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    2.314422] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    2.314429] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    2.314474] pci 0000:00:1f.2: reg 10 io port: [0xec00-0xec07]
[    2.314481] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]
[    2.314488] pci 0000:00:1f.2: reg 18 io port: [0xe400-0xe407]
[    2.314494] pci 0000:00:1f.2: reg 1c io port: [0xe000-0xe003]
[    2.314501] pci 0000:00:1f.2: reg 20 io port: [0xdc00-0xdc0f]
[    2.314527] pci 0000:00:1f.2: PME# supported from D3hot
[    2.314531] pci 0000:00:1f.2: PME# disabled
[    2.314579] pci 0000:00:1f.3: reg 20 io port: [0xc800-0xc81f]
[    2.314638] pci 0000:01:00.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    2.314649] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xd7ffffff]
[    2.314659] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf8ffffff]
[    2.314668] pci 0000:01:00.0: reg 30 32bit mmio: [0xf9000000-0xf901ffff]
[    2.314738] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xfbffffff]
[    2.314742] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    2.314792] pci 0000:00:1c.0: bridge 32bit mmio: [0xf3c00000-0xf3cfffff]
[    2.314800] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xcfc00000-0xcfcfffff]
[    2.314850] pci 0000:00:1c.1: bridge 32bit mmio: [0xf3d00000-0xf3dfffff]
[    2.314857] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xcfd00000-0xcfdfffff]
[    2.314906] pci 0000:00:1c.2: bridge 32bit mmio: [0xf3e00000-0xf3efffff]
[    2.314912] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xcfe00000-0xcfefffff]
[    2.314961] pci 0000:00:1c.3: bridge 32bit mmio: [0xf3f00000-0xf3ffffff]
[    2.314968] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xcff00000-0xcfffffff]
[    2.315009] pci 0000:06:02.0: reg 10 32bit mmio: [0xf3b10000-0xf3b107ff]
[    2.315061] pci 0000:06:02.0: supports D1 D2
[    2.315099] pci 0000:06:03.0: reg 10 32bit mmio: [0xf3b00000-0xf3b0ffff]
[    2.315198] pci 0000:00:1e.0: transparent bridge
[    2.315204] pci 0000:00:1e.0: bridge 32bit mmio: [0xf3b00000-0xf3bfffff]
[    2.315211] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xcfb00000-0xcfbfffff]
[    2.315241] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.315371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    2.315441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    2.315618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    2.315686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    2.315755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    2.320841] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    2.321038] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    2.321231] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    2.321422] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    2.321613] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    2.321806] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    2.322003] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    2.322194] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    2.322446] SCSI subsystem initialized
[    2.322479] libata version 3.00 loaded.
[    2.322479] usbcore: registered new interface driver usbfs
[    2.322479] usbcore: registered new interface driver hub
[    2.322479] usbcore: registered new device driver usb
[    2.322479] ACPI: WMI: Mapper loaded
[    2.322479] PCI: Using ACPI for IRQ routing
[    2.350013] Bluetooth: Core ver 2.15
[    2.350036] NET: Registered protocol family 31
[    2.350036] Bluetooth: HCI device and connection manager initialized
[    2.350036] Bluetooth: HCI socket layer initialized
[    2.350036] NetLabel: Initializing
[    2.350036] NetLabel:  domain hash size = 128
[    2.350036] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.350057] NetLabel:  unlabeled traffic allowed by default
[    2.350187] hpet clockevent registered
[    2.350195] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    2.350201] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    2.350207] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    2.390016] pnp: PnP ACPI init
[    2.390033] ACPI: bus type pnp registered
[    2.394512] pnp: PnP ACPI: found 14 devices
[    2.394515] ACPI: ACPI bus type pnp unregistered
[    2.394532] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    2.394536] system 00:09: ioport range 0x400-0x47f has been reserved
[    2.394540] system 00:09: ioport range 0x500-0x53f has been reserved
[    2.394548] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[    2.394558] system 00:0c: ioport range 0x400-0x47f has been reserved
[    2.394562] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    2.394565] system 00:0c: ioport range 0x500-0x53f has been reserved
[    2.394568] system 00:0c: iomem range 0xeec00000-0xeec03fff has been reserved
[    2.394572] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    2.394575] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    2.394579] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[    2.394582] system 00:0c: iomem range 0xfed13000-0xfed13fff has been reserved
[    2.394585] system 00:0c: iomem range 0xfed14000-0xfed17fff has been reserved
[    2.394588] system 00:0c: iomem range 0xfed18000-0xfed18fff has been reserved
[    2.394591] system 00:0c: iomem range 0xfed19000-0xfed19fff has been reserved
[    2.394595] system 00:0c: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    2.394598] system 00:0c: iomem range 0xfed20000-0xfed9ffff has been reserved
[    2.394605] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    2.394608] system 00:0d: iomem range 0xc0000-0xdffff has been reserved
[    2.394612] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    2.394615] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    2.399334] AppArmor: AppArmor Filesystem Enabled
[    2.399394] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    2.399398] pci 0000:00:01.0:   IO window: disabled
[    2.399403] pci 0000:00:01.0:   MEM window: 0xf4000000-0xfbffffff
[    2.399407] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    2.399411] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    2.399413] pci 0000:00:1c.0:   IO window: disabled
[    2.399419] pci 0000:00:1c.0:   MEM window: 0xf3c00000-0xf3cfffff
[    2.399423] pci 0000:00:1c.0:   PREFETCH window: 0x000000cfc00000-0x000000cfcfffff
[    2.399430] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    2.399432] pci 0000:00:1c.1:   IO window: disabled
[    2.399438] pci 0000:00:1c.1:   MEM window: 0xf3d00000-0xf3dfffff
[    2.399442] pci 0000:00:1c.1:   PREFETCH window: 0x000000cfd00000-0x000000cfdfffff
[    2.399449] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    2.399451] pci 0000:00:1c.2:   IO window: disabled
[    2.399456] pci 0000:00:1c.2:   MEM window: 0xf3e00000-0xf3efffff
[    2.399461] pci 0000:00:1c.2:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff
[    2.399468] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:02
[    2.399470] pci 0000:00:1c.3:   IO window: disabled
[    2.399475] pci 0000:00:1c.3:   MEM window: 0xf3f00000-0xf3ffffff
[    2.399480] pci 0000:00:1c.3:   PREFETCH window: 0x000000cff00000-0x000000cfffffff
[    2.399487] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    2.399489] pci 0000:00:1e.0:   IO window: disabled
[    2.399494] pci 0000:00:1e.0:   MEM window: 0xf3b00000-0xf3bfffff
[    2.399499] pci 0000:00:1e.0:   PREFETCH window: 0x000000cfb00000-0x000000cfbfffff
[    2.399513]   alloc irq_desc for 16 on node 0
[    2.399515]   alloc kstat_irqs on node 0
[    2.399521] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.399526] pci 0000:00:01.0: setting latency timer to 64
[    2.399534]   alloc irq_desc for 17 on node 0
[    2.399536]   alloc kstat_irqs on node 0
[    2.399540] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.399544] pci 0000:00:1c.0: setting latency timer to 64
[    2.399552] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    2.399557] pci 0000:00:1c.1: setting latency timer to 64
[    2.399564]   alloc irq_desc for 18 on node 0
[    2.399566]   alloc kstat_irqs on node 0
[    2.399570] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.399574] pci 0000:00:1c.2: setting latency timer to 64
[    2.399582]   alloc irq_desc for 19 on node 0
[    2.399584]   alloc kstat_irqs on node 0
[    2.399587] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.399592] pci 0000:00:1c.3: setting latency timer to 64
[    2.399599] pci 0000:00:1e.0: setting latency timer to 64
[    2.399604] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    2.399607] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    2.399610] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xfbffffff]
[    2.399613] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    2.399616] pci_bus 0000:05: resource 1 mem: [0xf3c00000-0xf3cfffff]
[    2.399618] pci_bus 0000:05: resource 2 pref mem [0xcfc00000-0xcfcfffff]
[    2.399621] pci_bus 0000:04: resource 1 mem: [0xf3d00000-0xf3dfffff]
[    2.399624] pci_bus 0000:04: resource 2 pref mem [0xcfd00000-0xcfdfffff]
[    2.399627] pci_bus 0000:03: resource 1 mem: [0xf3e00000-0xf3efffff]
[    2.399630] pci_bus 0000:03: resource 2 pref mem [0xcfe00000-0xcfefffff]
[    2.399633] pci_bus 0000:02: resource 1 mem: [0xf3f00000-0xf3ffffff]
[    2.399635] pci_bus 0000:02: resource 2 pref mem [0xcff00000-0xcfffffff]
[    2.399638] pci_bus 0000:06: resource 1 mem: [0xf3b00000-0xf3bfffff]
[    2.399641] pci_bus 0000:06: resource 2 pref mem [0xcfb00000-0xcfbfffff]
[    2.399644] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    2.399646] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffffffffffff]
[    2.399693] NET: Registered protocol family 2
[    2.399862] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    2.400920] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    2.403003] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.403542] TCP: Hash tables configured (established 262144 bind 65536)
[    2.403545] TCP reno registered
[    2.403661] NET: Registered protocol family 1
[    2.403743] Trying to unpack rootfs image as initramfs...
[    2.615150] Freeing initrd memory: 7687k freed
[    2.619027] Scanning for low memory corruption every 60 seconds
[    2.619179] audit: initializing netlink socket (disabled)
[    2.619196] type=2000 audit(1261092321.610:1): initialized
[    2.627586] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.629340] VFS: Disk quotas dquot_6.5.2
[    2.629412] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.630214] fuse init (API version 7.12)
[    2.630312] msgmni has been set to 4014
[    2.630578] alg: No test for stdrng (krng)
[    2.630599] io scheduler noop registered
[    2.630602] io scheduler anticipatory registered
[    2.630604] io scheduler deadline registered
[    2.630659] io scheduler cfq registered (default)
[    2.630774] pci 0000:01:00.0: Boot video device
[    2.630933]   alloc irq_desc for 24 on node 0
[    2.630936]   alloc kstat_irqs on node 0
[    2.630947] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    2.630955] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.631115]   alloc irq_desc for 25 on node 0
[    2.631118]   alloc kstat_irqs on node 0
[    2.631127] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    2.631136] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.631300]   alloc irq_desc for 26 on node 0
[    2.631303]   alloc kstat_irqs on node 0
[    2.631312] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    2.631321] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.631484]   alloc irq_desc for 27 on node 0
[    2.631486]   alloc kstat_irqs on node 0
[    2.631495] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    2.631505] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.631671]   alloc irq_desc for 28 on node 0
[    2.631674]   alloc kstat_irqs on node 0
[    2.631683] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    2.631692] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.631811] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.631834] Firmware did not grant requested _OSC control
[    2.631857] Firmware did not grant requested _OSC control
[    2.631874] Firmware did not grant requested _OSC control
[    2.631889] Firmware did not grant requested _OSC control
[    2.631925] Firmware did not grant requested _OSC control
[    2.631943] Firmware did not grant requested _OSC control
[    2.631959] Firmware did not grant requested _OSC control
[    2.631974] Firmware did not grant requested _OSC control
[    2.631992] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.632139] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.632144] ACPI: Power Button [PWRF]
[    2.632214] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.632221] ACPI: Power Button [PWRB]
[    2.632597] processor LNXCPU:00: registered as cooling_device0
[    2.632602] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.632681] processor LNXCPU:01: registered as cooling_device1
[    2.632686] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.636221] Linux agpgart interface v0.103
[    2.636233] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.636343] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.636674] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.637925] brd: module loaded
[    2.638462] loop: module loaded
[    2.638550] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.638722] ata_piix 0000:00:1f.1: version 2.13
[    2.638739] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.638780] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.638860] scsi0 : ata_piix
[    2.638987] scsi1 : ata_piix
[    2.640282] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.640286] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.640376] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.640398] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.640443] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.640510] scsi2 : ata_piix
[    2.640592] scsi3 : ata_piix
[    2.642036] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 19
[    2.642040] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 19
[    2.643080] Fixed MDIO Bus: probed
[    2.643122] PPP generic driver version 2.4.2
[    2.643241] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.643298]   alloc irq_desc for 23 on node 0
[    2.643303]   alloc kstat_irqs on node 0
[    2.643312] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.643333] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.643337] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.643397] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.647317] ehci_hcd 0000:00:1d.7: debug port 1
[    2.647323] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.647338] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3afbc00
[    2.670056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.670149] usb usb1: configuration #1 chosen from 1 choice
[    2.670185] hub 1-0:1.0: USB hub found
[    2.670194] hub 1-0:1.0: 8 ports detected
[    2.670295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.670316] uhci_hcd: USB Universal Host Controller Interface driver
[    2.670417] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.670424] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.670428] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.670469] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.670495] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[    2.670581] usb usb2: configuration #1 chosen from 1 choice
[    2.670617] hub 2-0:1.0: USB hub found
[    2.670626] hub 2-0:1.0: 2 ports detected
[    2.670718] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.670725] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.670729] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.670766] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.670791] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    2.670881] usb usb3: configuration #1 chosen from 1 choice
[    2.670916] hub 3-0:1.0: USB hub found
[    2.670924] hub 3-0:1.0: 2 ports detected
[    2.671019] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.671026] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.671029] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.671076] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.671114] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    2.671205] usb usb4: configuration #1 chosen from 1 choice
[    2.671237] hub 4-0:1.0: USB hub found
[    2.671245] hub 4-0:1.0: 2 ports detected
[    2.671339] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.671346] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.671349] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.671387] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.671418] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    2.671510] usb usb5: configuration #1 chosen from 1 choice
[    2.671541] hub 5-0:1.0: USB hub found
[    2.671550] hub 5-0:1.0: 2 ports detected
[    2.671681] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.674481] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.674489] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.674590] mice: PS/2 mouse device common for all mice
[    2.674709] rtc_cmos 00:02: RTC can wake from S4
[    2.674751] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.674776] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.674904] device-mapper: uevent: version 1.0.3
[    2.675005] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.675093] device-mapper: multipath: version 1.1.0 loaded
[    2.675098] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.675313] cpuidle: using governor ladder
[    2.675317] cpuidle: using governor menu
[    2.675813] TCP cubic registered
[    2.675969] NET: Registered protocol family 10
[    2.676444] lo: Disabled Privacy Extensions
[    2.676781] NET: Registered protocol family 17
[    2.676803] Bluetooth: L2CAP ver 2.13
[    2.676805] Bluetooth: L2CAP socket layer initialized
[    2.676809] Bluetooth: SCO (Voice Link) ver 0.6
[    2.676810] Bluetooth: SCO socket layer initialized
[    2.676848] Bluetooth: RFCOMM TTY layer initialized
[    2.676852] Bluetooth: RFCOMM socket layer initialized
[    2.676854] Bluetooth: RFCOMM ver 1.11
[    2.676966] PM: Resume from disk failed.
[    2.676986] registered taskstats version 1
[    2.677104]   Magic number: 5:131:454
[    2.677191] rtc_cmos 00:02: setting system clock to 2009-12-17 23:25:22 UTC (1261092322)
[    2.677195] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.677197] EDD information not available.
[    2.703344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.821684] ata1.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[    2.831615] ata3.00: ATA-6: WDC WD2000JD-55HBB0, 08.02D08, max UDMA/133
[    2.831620] ata3.00: 390721968 sectors, multi 16: LBA48 
[    2.833128] ata4.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[    2.833132] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.851172] Switched to high resolution mode on CPU 1
[    2.860144] Switched to high resolution mode on CPU 0
[    2.862740] ata1.00: configured for UDMA/33
[    2.870868] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[    2.871298] ata4.00: configured for UDMA/133
[    2.871805] ata3.00: configured for UDMA/133
[    2.873688] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.873692] Uniform CD-ROM driver Revision: 3.20
[    2.873802] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.873858] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.873975] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-55H 08.0 PQ: 0 ANSI: 5
[    2.874124] sd 2:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    2.874134] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.874223] sd 2:0:0:0: [sda] Write Protect is off
[    2.874229] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.874263] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[    2.874276] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.874451] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.874521] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.874526]  sda:
[    2.874659] sd 3:0:0:0: [sdb] Write Protect is off
[    2.874663] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.874695] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.874854]  sdb: sdb1
[    2.879309] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.885121]  sda1 sda2 sda3 < sda5 >
[    2.909001] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.909026] Freeing unused kernel memory: 660k freed
[    2.909306] Write protecting the kernel read-only data: 7584k
[    4.864648] PM: Starting manual resume from disk
[    4.864653] PM: Resume from partition 8:5
[    4.864655] PM: Checking hibernation image.
[    4.864803] PM: Resume from disk failed.
[    4.871616] EXT4-fs (sda2): barriers enabled
[    4.890368] kjournald2 starting: pid 379, dev sda2:8, commit interval 5 seconds
[    4.890384] EXT4-fs (sda2): delayed allocation enabled
[    4.890394] EXT4-fs: file extents enabled
[    4.896411] EXT4-fs: mballoc enabled
[    4.896432] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    5.525614] type=1505 audit(1261092325.342:2): operation="profile_load" pid=402 name=/sbin/dhclient3
[    5.526288] type=1505 audit(1261092325.342:3): operation="profile_load" pid=402 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.526657] type=1505 audit(1261092325.342:4): operation="profile_load" pid=402 name=/usr/lib/connman/scripts/dhclient-script
[    5.577993] type=1505 audit(1261092325.392:5): operation="profile_load" pid=403 name=/usr/bin/evince
[    5.589310] type=1505 audit(1261092325.402:6): operation="profile_load" pid=403 name=/usr/bin/evince-previewer
[    5.595611] type=1505 audit(1261092325.412:7): operation="profile_load" pid=403 name=/usr/bin/evince-thumbnailer
[    5.610494] type=1505 audit(1261092325.432:8): operation="profile_load" pid=405 name=/usr/lib/cups/backend/cups-pdf
[    5.611277] type=1505 audit(1261092325.432:9): operation="profile_load" pid=405 name=/usr/sbin/cupsd
[    5.620325] type=1505 audit(1261092325.442:10): operation="profile_load" pid=406 name=/usr/sbin/tcpdump
[   17.126549] udev: starting version 147
[   17.144074] Adding 3903752k swap on /dev/sda5.  Priority:-1 extents:1 across:3903752k 
[   17.250097] intel_rng: Firmware space is locked read-only. If you can't or
[   17.250100] intel_rng: don't want to disable this in firmware setup, and if
[   17.250102] intel_rng: you are certain that your system has a functional
[   17.250104] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.337743] lp: driver loaded but no devices found
[   17.377991] EXT4-fs (sda2): internal journal on sda2:8
[   17.387883] nvidia: module license 'NVIDIA' taints kernel.
[   17.387891] Disabling lock debugging due to kernel taint
[   17.409578] Linux video capture interface: v2.00
[   17.554868] saa7130/34: v4l2 driver version 0.2.15 loaded
[   17.554978] saa7134 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.554988] saa7133[0]: found at 0000:06:02.0, rev: 209, irq: 18, latency: 32, mmio: 0xf3b10000
[   17.554998] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
[   17.555019] saa7133[0]: board init: gpio is 6400000
[   17.555028] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.590375] parport_pc 00:08: reported by Plug and Play ACPI
[   17.590404] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   17.717595] lp0: using parport0 (interrupt-driven).
[   17.730663] saa7133[0]: i2c eeprom 00: 70 00 01 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   17.730684] saa7133[0]: i2c eeprom 10: ff ff ff 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   17.730705] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 aa ff ff ff ff
[   17.730722] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.730739] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
[   17.730761] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   17.730777] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   17.730793] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   17.730810] saa7133[0]: i2c eeprom 80: 84 09 00 04 20 77 00 40 71 1a 0c f0 73 05 29 00
[   17.730828] saa7133[0]: i2c eeprom 90: 84 08 00 06 cb 05 01 00 94 18 89 72 07 70 73 09
[   17.730846] saa7133[0]: i2c eeprom a0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[   17.730866] saa7133[0]: i2c eeprom b0: 10 01 72 11 1f 79 b7 00 00 00 00 00 00 00 00 00
[   17.730885] saa7133[0]: i2c eeprom c0: 84 09 00 04 20 77 00 40 71 1a 0c f0 73 05 29 00
[   17.730902] saa7133[0]: i2c eeprom d0: 84 08 00 06 cb 05 01 00 94 18 89 72 07 70 73 09
[   17.730919] saa7133[0]: i2c eeprom e0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[   17.730938] saa7133[0]: i2c eeprom f0: 10 01 72 11 1f 79 b7 00 00 00 00 00 00 00 00 00
[   17.730959] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[   17.739355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.743041] ppdev: user-space parallel port driver
[   17.759475] tveeprom 0-0050: Hauppauge model 67019, rev B1B4, serial# 793201
[   17.759483] tveeprom 0-0050: MAC address is 00-0D-FE-0C-1A-71
[   17.759488] tveeprom 0-0050: tuner model is Philips 8275A (idx 114, type 4)
[   17.759494] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   17.759499] tveeprom 0-0050: audio processor is SAA7131 (idx 41)
[   17.759503] tveeprom 0-0050: decoder processor is SAA7131 (idx 35)
[   17.759508] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[   17.759512] saa7133[0]: hauppauge eeprom: model=67019
[   17.785631] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.785646] nvidia 0000:01:00.0: setting latency timer to 64
[   17.785870] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   17.788379] cfg80211: Calling CRDA to update world regulatory domain
[   17.873901] cfg80211: World regulatory domain updated:
[   17.873908]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.873914]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.873919]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.873924]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.873929]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.873933]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.903451] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.903826] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   17.903831] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   17.903834] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   17.995906] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   18.111347] type=1505 audit(1261092337.932:11): operation="profile_replace" pid=920 name=/sbin/dhclient3
[   18.112118] type=1505 audit(1261092337.932:12): operation="profile_replace" pid=920 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.112753] type=1505 audit(1261092337.932:13): operation="profile_replace" pid=920 name=/usr/lib/connman/scripts/dhclient-script
[   18.120867] type=1505 audit(1261092337.942:14): operation="profile_replace" pid=922 name=/usr/bin/evince
[   18.134084] type=1505 audit(1261092337.952:15): operation="profile_replace" pid=922 name=/usr/bin/evince-previewer
[   18.141390] type=1505 audit(1261092337.962:16): operation="profile_replace" pid=922 name=/usr/bin/evince-thumbnailer
[   18.152292] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.152334] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.161270] type=1505 audit(1261092337.982:17): operation="profile_replace" pid=932 name=/usr/lib/cups/backend/cups-pdf
[   18.162182] type=1505 audit(1261092337.982:18): operation="profile_replace" pid=932 name=/usr/sbin/cupsd
[   18.169161] type=1505 audit(1261092337.982:19): operation="profile_replace" pid=933 name=/usr/sbin/tcpdump
[   18.179132] tda829x 0-004b: setting tuner address to 61
[   18.297398] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
[   18.322570] tda829x 0-004b: type set to tda8290+75a
[   18.392291] input: PS2++ Logitech MX Mouse as /devices/platform/i8042/serio1/input/input5
[   19.162290] CPU0 attaching NULL sched-domain.
[   19.162297] CPU1 attaching NULL sched-domain.
[   19.192641] CPU0 attaching sched-domain:
[   19.192646]  domain 0: span 0-1 level SIBLING
[   19.192650]   groups: 0 1
[   19.192655]   domain 1: span 0-1 level MC
[   19.192658]    groups: 0-1 (__cpu_power = 2048)
[   19.192664] CPU1 attaching sched-domain:
[   19.192666]  domain 0: span 0-1 level SIBLING
[   19.192669]   groups: 1 0
[   19.192673]   domain 1: span 0-1 level MC
[   19.192676]    groups: 0-1 (__cpu_power = 2048)
[   20.205530] usplash:342 freeing invalid memtype ffffffffd0000000-ffffffffd8000000
[   23.593210] input: i2c IR (HVR 1110) as /devices/virtual/input/input6
[   23.593284] ir-kbd-i2c: i2c IR (HVR 1110) detected at i2c-0/0-0071/ir0 [saa7133[0]]
[   23.730108] saa7133[0]: registered device video0 [v4l2]
[   23.730155] saa7133[0]: registered device vbi0
[   23.730197] saa7133[0]: registered device radio0
[   23.730878] ath5k 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.730941] ath5k 0000:06:03.0: registered as 'phy0'
[   23.738126] saa7134 ALSA driver for DMA sound loaded
[   23.738141] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   23.738174] saa7133[0]/alsa: saa7133[0] at 0xf3b10000 irq 18 registered as card -2
[   23.829524] dvb_init() allocating 1 frontend
[   23.855873] ath: EEPROM regdomain: 0x809c
[   23.855878] ath: EEPROM indicates we should expect a country code
[   23.855882] ath: doing EEPROM country->regdmn map search
[   23.855885] ath: country maps to regdmn code: 0x52
[   23.855889] ath: Country alpha2 being used: CN
[   23.855892] ath: Regpair used: 0x52
[   23.871221] phy0: Selected rate control algorithm 'minstrel'
[   23.872085] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   23.952903] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.002626] DVB: registering new adapter (saa7133[0])
[   24.002633] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   24.740023] tda1004x: setting up plls for 48MHz sampling clock
[   27.480018] tda1004x: timeout waiting for DSP ready
[   27.580015] tda1004x: found firmware revision 0 -- invalid
[   27.580019] tda1004x: trying to boot from eeprom
[   29.972538] tda1004x: timeout waiting for DSP ready
[   30.082536] tda1004x: found firmware revision 0 -- invalid
[   30.082542] tda1004x: waiting for firmware upload...
[   30.082549] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10046.fw
[   30.130552] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10045.fw
[   30.152635] tda1004x: no firmware upload (timeout or file not found?)
[   30.152643] tda1004x: firmware upload failed
[   30.670857] cfg80211: Calling CRDA for country: CN
[   30.679616] cfg80211: Regulatory domain changed to country: CN
[   30.679624]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.679629]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.679633]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   39.502894] nvclock:1709 freeing invalid memtype f4000000-f4010000
[   39.598877] nvclock:1709 freeing invalid memtype f4010000-f4030000
[   45.217599] wlan0: authenticate with AP 00:16:01:b0:23:eb
[   45.219012] wlan0: authenticated
[   45.219017] wlan0: associate with AP 00:16:01:b0:23:eb
[   45.222702] wlan0: RX AssocResp from 00:16:01:b0:23:eb (capab=0x411 status=0 aid=1)
[   45.222706] wlan0: associated
[   45.223366] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.112337] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   55.380025] wlan0: no IPv6 routers present
[  146.692523] tda1004x: setting up plls for 48MHz sampling clock
[  149.150016] tda1004x: timeout waiting for DSP ready
[  149.250023] tda1004x: found firmware revision 0 -- invalid
[  149.250029] tda1004x: trying to boot from eeprom
[  151.650020] tda1004x: timeout waiting for DSP ready
[  151.750020] tda1004x: found firmware revision 0 -- invalid
[  151.750026] tda1004x: waiting for firmware upload...
[  151.750034] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10046.fw
[  151.754201] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10045.fw
[  151.763776] tda1004x: no firmware upload (timeout or file not found?)
[  151.763784] tda1004x: firmware upload failed
[  791.232532] tda1004x: setting up plls for 48MHz sampling clock
[  793.690012] tda1004x: timeout waiting for DSP ready
[  793.790012] tda1004x: found firmware revision 0 -- invalid
[  793.790017] tda1004x: trying to boot from eeprom
[  796.180047] tda1004x: timeout waiting for DSP ready
[  796.280022] tda1004x: found firmware revision 0 -- invalid
[  796.280027] tda1004x: waiting for firmware upload...
[  796.280035] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10046.fw
[  796.284267] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10045.fw
[  796.292407] tda1004x: no firmware upload (timeout or file not found?)
[  796.292415] tda1004x: firmware upload failed
[  835.800020] tda1004x: setting up plls for 48MHz sampling clock
[  838.242511] tda1004x: timeout waiting for DSP ready
[  838.342470] tda1004x: found firmware revision 0 -- invalid
[  838.342475] tda1004x: trying to boot from eeprom
[  840.722510] tda1004x: timeout waiting for DSP ready
[  840.822523] tda1004x: found firmware revision 0 -- invalid
[  840.822527] tda1004x: waiting for firmware upload...
[  840.822534] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10046.fw
[  840.826502] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10045.fw
[  840.835286] tda1004x: no firmware upload (timeout or file not found?)
[  840.835295] tda1004x: firmware upload failed
[ 1744.560013] tda1004x: setting up plls for 48MHz sampling clock
[ 1747.010022] tda1004x: timeout waiting for DSP ready
[ 1747.110016] tda1004x: found firmware revision 0 -- invalid
[ 1747.110022] tda1004x: trying to boot from eeprom
[ 1749.500016] tda1004x: timeout waiting for DSP ready
[ 1749.600012] tda1004x: found firmware revision 0 -- invalid
[ 1749.600018] tda1004x: waiting for firmware upload...
[ 1749.600026] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10046.fw
[ 1749.604252] saa7134 0000:06:02.0: firmware: requesting dvb-fe-tda10045.fw
[ 1749.613091] tda1004x: no firmware upload (timeout or file not found?)
[ 1749.613099] tda1004x: firmware upload failed

```

---

### Post by cricka15 on 2010-01-04
think i've managed to solve this, needed to get the firmware for the tvcard.

followed a few of the steps from this page [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)

obtained the file get_dvb_firmware from here (file save page as): [http://www.kernel.org/doc/Documentation/dvb/get_dvb_firmware](http://www.kernel.org/doc/Documentation/dvb/get_dvb_firmware)

then executed the code to get and extract the firmware file needed:
```
perl get_dvb_firmware tda10046
```and finally copied the .fw file into /lib/firmware directory and rebooted.

seems to be working from cold boots now, without having to boot into windows first and then reboot into xubuntu.

:cool:

---

### Post by cricka15 on 2010-01-11
> **cricka15 said:**
> think i've managed to solve this, needed to get the firmware for the tvcard.

followed a few of the steps from this page [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)

obtained the file get_dvb_firmware from here (file save page as): [http://www.kernel.org/doc/Documentation/dvb/get_dvb_firmware](http://www.kernel.org/doc/Documentation/dvb/get_dvb_firmware)

then executed the code to get and extract the firmware file needed:
```
perl get_dvb_firmware tda10046
```and finally copied the .fw file into /lib/firmware directory and rebooted.

seems to be working from cold boots now, without having to boot into windows first and then reboot into xubuntu.

:cool:

whilst this has got the card working properly on every boot i get quite a long pause with the message " tda1004x: timeout waiting for DSP ready".

bit of thread searching here has come up with the solution to install the linux-firmware-nonfree package, which seems to have solved the problem.

```
sudo apt-get install linux-firmware-nonfree
```so i think the problem is solved once and for all, no more posts about it...:biggrin:

---

### Post by HappyFeet on 2010-01-11
> **cricka15 said:**
> 
bit of thread searching here has come up with the solution to install the linux-firmware-nonfree package, which seems to have solved the problem.

```
sudo apt-get install linux-firmware-nonfree
```so i think the problem is solved once and for all, no more posts about it...:biggrin:

Thanks for sharing. More information for others to use is always good.

---

