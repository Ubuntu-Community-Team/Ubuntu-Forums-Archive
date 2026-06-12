---
title: "Mythbuntu 9.10 DVD Problems"
date: 2009-11-17
forum: Mythbuntu
---

### Post by SickNick on 2009-11-17
I have mythbuntu 9.10 set up on my friends computer which I built a few years back and now we have it set up to be a mediacenter. He has an enormous stack of DVD's which we want to rip so they don't take up so much space. I started with mythbuntu from version 9.04. Here where the problems with that.


The DVD would mount and you could browse through it with the file manager.

I had libdvdcss2, ffmpeg, and w64 codecs installed.
A very few select dvds where able to rip, maybe like 3/20 dvds. The rest just mounted but where not able to play, and when I went to rip them through mythtv, all I got was No Jobs.

Now that I installed Mythbuntu 9.10 I figured some of these things may be straightened out, but it got worse. As usual I updated, and installed all the proprietary codecs. This time in mythbuntu 9.10 the DVD's will not even mount. I checked through the directory /cdrom and found nothing. I am thinking this may be an issue with the drive? I have tried so many things I read online and I am completely stuck on this one.

Can someone point me into a direction where to start to solve this one?

---

### Post by SickNick on 2009-11-18
](*,)

---

### Post by klc5555 on 2009-11-19
The Mythtv dvd ripper is OK, but has never been great. It simply can't rip a lot of dvds.

For the very significant number of dvd's that it can't rip at all, or can only rip in iso format (or conversely can only rip in _other_ than iso format) you're going to need to have a full stable of linux dvd ripping tools at your disposal. These should include (but not necessarily be limited to) dvd::rip, thoggen, and vlc (the latter being about the only thing that can handle those pesky disney/sony dvds). You might want to start by reading the comparative review of some rippers at [http://www.linux.com/archive/feature/128105](http://www.linux.com/archive/feature/128105)

Cheers!

---

### Post by Dewey_Oxberger on 2009-11-19
> **klc5555 said:**
> The Mythtv dvd ripper is OK, but has never been great. It simply can't rip a lot of dvds.
......those pesky disney/sony dvds). You might want to start by reading the comparative review of some rippers at [http://www.linux.com/archive/feature/128105](http://www.linux.com/archive/feature/128105)

Cheers!


+1 to that.  Side note: The new myth 0.22 is a major improvement on the loads of dvd menu system bugs that 0.21 had.  All my Disney and Sony test cases play fine now.  Also the latest VLC is great.

---

### Post by SickNick on 2009-11-19
Thank you for the replies guys, I appreciate your help. I don't think getting a ripper will solve the problem, the biggest problem I'm facing is that the dvd is not even being recognized and mounted. I can click my cdrom drive and it opens the folder and displays nothing, no error, no content. I am really considering just getting a new drive. The drive does read cds no problem. But DVDs are not even appearing at all to begin with, so I'm pretty sure a new ripper would not fix the problem. Even if I don't have lildvdcss2 installed, the content would still appear as vobs if I explore the drive and it even gives it a name, this computer just dosent show it :-(

---

### Post by nickrout on 2009-11-19
hmmm sounds like a hardware problem, but to be sure do some troubleshooting.

take a look at dmesg after you insert a dvd.

try mounting a dvd yourself. command is ```
mount /dev/dvd /mnt/dvd
``` (after making sure /mnt/dvd exists).

Sometimes they just crap out.

---

### Post by SickNick on 2009-11-19
Ok I tried to manually mount and...

```
mount: mount point /mnt/dvd does not exist
```

and for dmesg this was my output, hope you can see something I don't

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=4c4f5287-58c2-4d6e-b1f2-d161032c5897 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
[    0.000000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ff30 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff30000 (usable)
[    0.000000]  modified: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  modified: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007ff30000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007ff30000 page 4k
[    0.000000] kernel direct mapping tables up to 7ff30000 @ 10000-14000
[    0.000000] RAMDISK: 3786e000 - 37feffcd
[    0.000000] ACPI: RSDP 00000000000fa850 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ff30000 00030 (v01 A M I  OEMRSDT  06000517 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ff30200 00081 (v01 A M I  OEMFACP  06000517 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ff303e0 03755 (v01  A0058 A0058002 00000002 MSFT 0100000D)
[    0.000000] ACPI: FACS 000000007ff40000 00040
[    0.000000] ACPI: APIC 000000007ff30390 0004A (v01 A M I  OEMAPIC  06000517 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ff40040 0003F (v01 A M I  OEMBIOS  06000517 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ff30000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ff30000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  0000000000026fe7] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007ff30000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786e000 - 0037feffcd]          RAMDISK ==> [003786e000 - 0037feffcd]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3294]              BRK ==> [00019e3000 - 00019e3294]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff30
[    0.000000] On node 0 totalpages: 523967
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3826 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 512874 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ff80000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f4000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516700
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=4c4f5287-58c2-4d6e-b1f2-d161032c5897 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ f8000000 old size 32 MB
[    0.000000] Aperture from AGP @ f8000000 size 64 MB (APSIZE f30)
[    0.000000] Node 0: aperture @ f8000000 size 64 MB
[    0.000000] Memory: 2049104k/2096320k available (5313k kernel code, 452k absent, 46764k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2402.836 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.001171] Console: colour VGA+ 80x25
[    0.001174] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4805.67 BogoMIPS (lpj=24028360)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] tseg: 0000000000
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] Performance Counters: AMD PMU driver.
[    0.010000] ... version:                 0
[    0.010000] ... bit width:               48
[    0.010000] ... generic counters:        4
[    0.010000] ... value mask:              0000ffffffffffff
[    0.010000] ... max period:              00007fffffffffff
[    0.010000] ... fixed-purpose counters:  0
[    0.010000] ... counter mask:            000000000000000f
[    0.010000] SMP alternatives: switching to UP code
[    0.011563] Freeing SMP alternatives: 39k freed
[    0.011577] ACPI: Core revision 20090521
[    0.015928] Setting APIC routing to flat
[    0.016748] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.116762] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 0a
[    0.120000] Brought up 1 CPUs
[    0.120000] Total of 1 processors activated (4805.67 BogoMIPS).
[    0.120000] CPU0 attaching NULL sched-domain.
[    0.120000] Booting paravirtualized kernel on bare hardware
[    0.120000] regulator: core version 0.5
[    0.120000] Time:  3:27:10  Date: 11/20/09
[    0.120000] NET: Registered protocol family 16
[    0.120000] node 0 link 0: io port [1000, ffffff]
[    0.120000] TOM: 0000000080000000 aka 2048M
[    0.120000] node 0 link 0: mmio [a0000, bffff]
[    0.120000] node 0 link 0: mmio [80000000, ffffffff]
[    0.120000] bus: [00,ff] on node 0 link 0
[    0.120000] bus: 00 index 0 io port: [0, ffff]
[    0.120000] bus: 00 index 1 mmio: [a0000, bffff]
[    0.120000] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.120000] ACPI: bus type pci registered
[    0.120000] PCI: Using configuration type 1 for base access
[    0.120000] bio: create slab <bio-0> at 0
[    0.120000] ACPI: EC: Look up EC in DSDT
[    0.120000] ACPI: Interpreter enabled
[    0.120000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.120000] ACPI: Using IOAPIC for interrupt routing
[    0.121563] ACPI: No dock devices found.
[    0.121657] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.121706] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.121786] pci 0000:00:01.0: supports D1
[    0.121817] pci 0000:00:07.0: reg 10 32bit mmio: [0xfdf00000-0xfdf007ff]
[    0.121823] pci 0000:00:07.0: reg 14 io port: [0xc800-0xc87f]
[    0.121854] pci 0000:00:07.0: supports D2
[    0.121856] pci 0000:00:07.0: PME# supported from D2 D3hot D3cold
[    0.121860] pci 0000:00:07.0: PME# disabled
[    0.121891] pci 0000:00:0c.0: reg 10 io port: [0xc400-0xc4ff]
[    0.121896] pci 0000:00:0c.0: reg 14 32bit mmio: [0xfde00000-0xfde003ff]
[    0.121927] pci 0000:00:0c.0: supports D1 D2
[    0.121928] pci 0000:00:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.121932] pci 0000:00:0c.0: PME# disabled
[    0.121959] pci 0000:00:0d.0: reg 10 io port: [0xc000-0xc01f]
[    0.121964] pci 0000:00:0d.0: reg 14 io port: [0xb800-0xb80f]
[    0.121969] pci 0000:00:0d.0: reg 18 io port: [0xb400-0xb40f]
[    0.121974] pci 0000:00:0d.0: reg 1c io port: [0xb000-0xb03f]
[    0.121998] pci 0000:00:0d.0: supports D2
[    0.122026] pci 0000:00:0f.0: reg 10 io port: [0xe800-0xe807]
[    0.122031] pci 0000:00:0f.0: reg 14 io port: [0xe400-0xe403]
[    0.122037] pci 0000:00:0f.0: reg 18 io port: [0xe000-0xe007]
[    0.122042] pci 0000:00:0f.0: reg 1c io port: [0xd800-0xd803]
[    0.122047] pci 0000:00:0f.0: reg 20 io port: [0xd400-0xd40f]
[    0.122053] pci 0000:00:0f.0: reg 24 io port: [0xd000-0xd0ff]
[    0.122109] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.122174] pci 0000:00:10.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.122194] pci 0000:00:10.0: supports D1 D2
[    0.122196] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122199] pci 0000:00:10.0: PME# disabled
[    0.122237] pci 0000:00:10.1: reg 20 io port: [0xcc00-0xcc1f]
[    0.122258] pci 0000:00:10.1: supports D1 D2
[    0.122259] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122263] pci 0000:00:10.1: PME# disabled
[    0.122300] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[    0.122321] pci 0000:00:10.2: supports D1 D2
[    0.122322] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122326] pci 0000:00:10.2: PME# disabled
[    0.122363] pci 0000:00:10.3: reg 20 io port: [0xec00-0xec1f]
[    0.122384] pci 0000:00:10.3: supports D1 D2
[    0.122385] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122389] pci 0000:00:10.3: PME# disabled
[    0.122414] pci 0000:00:10.4: reg 10 32bit mmio: [0xfdb00000-0xfdb000ff]
[    0.122447] pci 0000:00:10.4: supports D1 D2
[    0.122448] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122452] pci 0000:00:10.4: PME# disabled
[    0.122503] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.122508] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.122551] pci 0000:00:11.5: reg 10 io port: [0x1000-0x10ff]
[    0.122586] pci 0000:00:11.5: supports D1 D2
[    0.122613] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.122726] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.122730] pci 0000:01:00.0: reg 14 io port: [0xa000-0xa0ff]
[    0.122733] pci 0000:01:00.0: reg 18 32bit mmio: [0xfd800000-0xfd80ffff]
[    0.122742] pci 0000:01:00.0: reg 30 32bit mmio: [0xfd700000-0xfd71ffff]
[    0.122753] pci 0000:01:00.0: supports D1 D2
[    0.122769] pci 0000:01:00.1: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.122773] pci 0000:01:00.1: reg 14 32bit mmio: [0xfd600000-0xfd60ffff]
[    0.122789] pci 0000:01:00.1: supports D1 D2
[    0.122813] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.122816] pci 0000:00:01.0: bridge 32bit mmio: [0xfd300000-0xfd8fffff]
[    0.122820] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd5200000-0xf51fffff]
[    0.122828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.127118] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.127189] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.127259] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.127328] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127398] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127468] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127538] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127608] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127752] SCSI subsystem initialized
[    0.127812] libata version 3.00 loaded.
[    0.127870] usbcore: registered new interface driver usbfs
[    0.127883] usbcore: registered new interface driver hub
[    0.127911] usbcore: registered new device driver usb
[    0.128013] ACPI: WMI: Mapper loaded
[    0.128015] PCI: Using ACPI for IRQ routing
[    0.128023] pci 0000:00:00.0: BAR 0: address space collision on of device [0xf8000000-0xfbffffff]
[    0.128025] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.128148] Bluetooth: Core ver 2.15
[    0.128175] NET: Registered protocol family 31
[    0.128176] Bluetooth: HCI device and connection manager initialized
[    0.128179] Bluetooth: HCI socket layer initialized
[    0.128181] NetLabel: Initializing
[    0.128182] NetLabel:  domain hash size = 128
[    0.128183] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.128198] NetLabel:  unlabeled traffic allowed by default
[    0.128255] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[    0.131340] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.132770] pnp: PnP ACPI init
[    0.132792] ACPI: bus type pnp registered
[    0.134313] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134316] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134319] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134322] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134325] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134328] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134331] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134334] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134337] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134339] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134342] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134345] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134348] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.135459] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135463] pnp 00:0c: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135466] pnp 00:0c: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135469] pnp 00:0c: mem resource (0x100000-0x7ffeffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135704] pnp: PnP ACPI: found 13 devices
[    0.135705] ACPI: ACPI bus type pnp unregistered
[    0.135717] system 00:08: ioport range 0x295-0x296 has been reserved
[    0.135720] system 00:08: ioport range 0x3e1-0x3e7 has been reserved
[    0.135722] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.135725] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.135732] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.135737] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.135740] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.135743] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.140406] AppArmor: AppArmor Filesystem Enabled
[    0.140435] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.140438] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.140442] pci 0000:00:01.0:   MEM window: 0xfd300000-0xfd8fffff
[    0.140446] pci 0000:00:01.0:   PREFETCH window: 0xd5200000-0xf51fffff
[    0.140458] pci 0000:00:01.0: setting latency timer to 64
[    0.140463] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.140465] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.140468] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.140470] pci_bus 0000:01: resource 1 mem: [0xfd300000-0xfd8fffff]
[    0.140473] pci_bus 0000:01: resource 2 pref mem [0xd5200000-0xf51fffff]
[    0.140511] NET: Registered protocol family 2
[    0.140636] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.141718] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.145388] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.146321] TCP: Hash tables configured (established 262144 bind 65536)
[    0.146323] TCP reno registered
[    0.146426] NET: Registered protocol family 1
[    0.146494] Trying to unpack rootfs image as initramfs...
[    0.316189] Freeing initrd memory: 7687k freed
[    0.323051] Scanning for low memory corruption every 60 seconds
[    0.323197] audit: initializing netlink socket (disabled)
[    0.323215] type=2000 audit(1258687630.320:1): initialized
[    0.331212] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.332404] VFS: Disk quotas dquot_6.5.2
[    0.332453] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.332958] fuse init (API version 7.12)
[    0.333025] msgmni has been set to 4017
[    0.333184] alg: No test for stdrng (krng)
[    0.333195] io scheduler noop registered
[    0.333197] io scheduler anticipatory registered
[    0.333198] io scheduler deadline registered
[    0.333234] io scheduler cfq registered (default)
[    0.333243] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.360040] pci 0000:01:00.0: Boot video device
[    0.360132] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.360151] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.360243] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.360247] ACPI: Power Button [PWRF]
[    0.360295] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.360300] ACPI: Power Button [PWRB]
[    0.360337] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.360340] ACPI: Sleep Button [SLPB]
[    0.360478] processor LNXCPU:00: registered as cooling_device0
[    0.362975] Linux agpgart interface v0.103
[    0.362985] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.363078] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.363151] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.363360] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.363451] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.364216] brd: module loaded
[    0.364565] loop: module loaded
[    0.364631] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.365111] pata_via 0000:00:0f.1: version 0.3.4
[    0.365126]   alloc irq_desc for 20 on node 0
[    0.365128]   alloc kstat_irqs on node 0
[    0.365136] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.365324] scsi0 : pata_via
[    0.365409] scsi1 : pata_via
[    0.366830] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.366833] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.367122] Fixed MDIO Bus: probed
[    0.367152] PPP generic driver version 2.4.2
[    0.367214] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.367353]   alloc irq_desc for 21 on node 0
[    0.367354]   alloc kstat_irqs on node 0
[    0.367358] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.367374] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.367429] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.367495] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdb00000
[    0.380025] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.380096] usb usb1: configuration #1 chosen from 1 choice
[    0.380128] hub 1-0:1.0: USB hub found
[    0.380135] hub 1-0:1.0: 8 ports detected
[    0.380192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.380203] uhci_hcd: USB Universal Host Controller Interface driver
[    0.380271] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.380277] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.380301] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.380320] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000bc00
[    0.380382] usb usb2: configuration #1 chosen from 1 choice
[    0.380401] hub 2-0:1.0: USB hub found
[    0.380408] hub 2-0:1.0: 2 ports detected
[    0.380467] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.380472] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.380495] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.380513] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000cc00
[    0.380586] usb usb3: configuration #1 chosen from 1 choice
[    0.380605] hub 3-0:1.0: USB hub found
[    0.380612] hub 3-0:1.0: 2 ports detected
[    0.380662] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.380667] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.380699] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.380718] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.380782] usb usb4: configuration #1 chosen from 1 choice
[    0.380804] hub 4-0:1.0: USB hub found
[    0.380810] hub 4-0:1.0: 2 ports detected
[    0.380862] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.380867] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.380890] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.380908] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000ec00
[    0.380976] usb usb5: configuration #1 chosen from 1 choice
[    0.380995] hub 5-0:1.0: USB hub found
[    0.381002] hub 5-0:1.0: 2 ports detected
[    0.381074] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.381076] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.381479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.381484] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.381530] mice: PS/2 mouse device common for all mice
[    0.381615] rtc_cmos 00:02: RTC can wake from S4
[    0.381645] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.381694] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.381781] device-mapper: uevent: version 1.0.3
[    0.381881] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.381925] device-mapper: multipath: version 1.1.0 loaded
[    0.381928] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.382033] cpuidle: using governor ladder
[    0.382035] cpuidle: using governor menu
[    0.382410] TCP cubic registered
[    0.382517] NET: Registered protocol family 10
[    0.382887] lo: Disabled Privacy Extensions
[    0.383123] NET: Registered protocol family 17
[    0.383139] Bluetooth: L2CAP ver 2.13
[    0.383141] Bluetooth: L2CAP socket layer initialized
[    0.383144] Bluetooth: SCO (Voice Link) ver 0.6
[    0.383145] Bluetooth: SCO socket layer initialized
[    0.383169] Bluetooth: RFCOMM TTY layer initialized
[    0.383172] Bluetooth: RFCOMM socket layer initialized
[    0.383173] Bluetooth: RFCOMM ver 1.11
[    0.383184] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    0.383227] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x2
[    0.383229] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x6
[    0.383231] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xa
[    0.383233] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
[    0.383235] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[    0.383321] PM: Resume from disk failed.
[    0.383332] registered taskstats version 1
[    0.383462]   Magic number: 1:774:462
[    0.383548] rtc_cmos 00:02: setting system clock to 2009-11-20 03:27:11 UTC (1258687631)
[    0.383551] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.383553] EDD information not available.
[    0.541681] ata1.00: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
[    0.541683] ata1.00: 390721968 sectors, multi 16: LBA48 
[    0.581551] ata1.00: configured for UDMA/100
[    0.581665] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-00G 08.0 PQ: 0 ANSI: 5
[    0.581757] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.581790] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    0.581827] sd 0:0:0:0: [sda] Write Protect is off
[    0.581829] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.581847] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.581954]  sda: sda1 sda2 < sda5 >
[    0.619700] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.650060] Switched to high resolution mode on CPU 0
[    0.890360] ata2.01: ATAPI: LITE-ON DVDRW SOHW-1673S, JS01, max UDMA/66
[    0.890378] ata2.01: limited to UDMA/33 due to 40-wire cable
[    0.930008] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    0.930258] ata2.01: configured for UDMA/33
[    0.931387] scsi 1:0:1:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS01 PQ: 0 ANSI: 5
[    0.934922] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.934925] Uniform CD-ROM driver Revision: 3.20
[    0.934976] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    0.935004] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    0.935024] Freeing unused kernel memory: 660k freed
[    0.935513] Write protecting the kernel read-only data: 7580k
[    1.103353]   alloc irq_desc for 16 on node 0
[    1.103357]   alloc kstat_irqs on node 0
[    1.103366] ohci1394 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.107678] Floppy drive(s): fd0 is 1.44M
[    1.128904] FDC 0 is a post-1991 82077
[    1.177825] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fdf00000-fdf007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.185136] usb 3-2: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    1.190688] sata_via 0000:00:0f.0: version 2.4
[    1.190706] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.190762] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.190842] scsi2 : sata_via
[    1.190910] scsi3 : sata_via
[    1.190939] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 20
[    1.190942] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 20
[    1.205282] [drm] Initialized drm 1.1.0 20060810
[    1.286566] usb 3-2: configuration #1 chosen from 1 choice
[    1.295778] usbcore: registered new interface driver hiddev
[    1.309949] input: HID 0c16:0001 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
[    1.310043] generic-usb 0003:0C16:0001.0001: input,hidraw0: USB HID v1.00 Keyboard [HID 0c16:0001] on usb-0000:00:10.1-2/input0
[    1.341149] input: HID 0c16:0001 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input5
[    1.341245] generic-usb 0003:0C16:0001.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [HID 0c16:0001] on usb-0000:00:10.1-2/input1
[    1.341259] usbcore: registered new interface driver usbhid
[    1.341262] usbhid: v2.6:USB HID core driver
[    1.410012] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.630007] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.656813] [drm] radeon default to kernel modesetting DISABLED.
[    1.656926] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.657392] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    2.316814] PM: Starting manual resume from disk
[    2.316818] PM: Resume from partition 8:5
[    2.316820] PM: Checking hibernation image.
[    2.316954] PM: Resume from disk failed.
[    2.342725] EXT4-fs (sda1): barriers enabled
[    2.358400] kjournald2 starting: pid 362, dev sda1:8, commit interval 5 seconds
[    2.358411] EXT4-fs (sda1): delayed allocation enabled
[    2.358414] EXT4-fs: file extents enabled
[    2.382931] EXT4-fs: mballoc enabled
[    2.382951] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.530105] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000b062a8]
[    2.915690] type=1505 audit(1258687634.026:2): operation="profile_load" pid=385 name=/sbin/dhclient3
[    2.915941] type=1505 audit(1258687634.026:3): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.916082] type=1505 audit(1258687634.026:4): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
[    2.941068] type=1505 audit(1258687634.056:5): operation="profile_load" pid=386 name=/usr/bin/evince
[    2.945204] type=1505 audit(1258687634.056:6): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
[    2.947580] type=1505 audit(1258687634.056:7): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
[    2.969116] type=1505 audit(1258687634.076:8): operation="profile_load" pid=388 name=/usr/sbin/mysqld
[    2.970842] type=1505 audit(1258687634.086:9): operation="profile_load" pid=389 name=/usr/sbin/ntpd
[    2.973050] type=1505 audit(1258687634.086:10): operation="profile_load" pid=390 name=/usr/sbin/tcpdump
[    3.681111] Adding 6024332k swap on /dev/sda5.  Priority:-1 extents:1 across:6024332k 
[    3.998103] EXT4-fs (sda1): internal journal on sda1:8
[    4.546419] udev: starting version 147
[    5.007573] parport_pc 00:07: reported by Plug and Play ACPI
[    5.007614] parport0: PC-style at 0x378, irq 7 [PCSPP]
[    5.142310] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.177516] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    5.193057] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    5.193128] EDAC amd64: ECC is enabled by BIOS, Proceeding with EDAC module initialization
[    5.193169] EDAC MC: Rev E or earlier detected
[    5.193240] EDAC MC0: Giving out device to 'amd64_edac' 'RevF': DEV 0000:00:18.2
[    5.193261] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
[    5.326028] RPC: Registered udp transport module.
[    5.326032] RPC: Registered tcp transport module.
[    5.393813] lp0: using parport0 (interrupt-driven).
[    5.408731] ppdev: user-space parallel port driver
[    5.491162] cfg80211: Calling CRDA to update world regulatory domain
[    5.726388] cfg80211: World regulatory domain updated:
[    5.726392] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.726394] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.726397] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.726399] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.726401] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.726404] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.766336] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[    5.886831]   alloc irq_desc for 17 on node 0
[    5.886835]   alloc kstat_irqs on node 0
[    5.886844] rtl8180 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.549396] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    6.684756] phy0: Selected rate control algorithm 'minstrel'
[    6.685287] phy0: hwaddr 00:18:e7:76:4e:45, RTL8185vD + rtl8225z2
[    7.346543]   alloc irq_desc for 18 on node 0
[    7.346547]   alloc kstat_irqs on node 0
[    7.346556] ICE1712 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.492477] type=1505 audit(1258687638.606:11): operation="profile_replace" pid=791 name=/sbin/dhclient3
[    7.492732] type=1505 audit(1258687638.606:12): operation="profile_replace" pid=791 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.492876] type=1505 audit(1258687638.606:13): operation="profile_replace" pid=791 name=/usr/lib/connman/scripts/dhclient-script
[    7.497489] type=1505 audit(1258687638.606:14): operation="profile_replace" pid=792 name=/usr/bin/evince
[    7.502497] type=1505 audit(1258687638.616:15): operation="profile_replace" pid=792 name=/usr/bin/evince-previewer
[    7.504948] type=1505 audit(1258687638.616:16): operation="profile_replace" pid=792 name=/usr/bin/evince-thumbnailer
[    7.509804] type=1505 audit(1258687638.616:17): operation="profile_replace" pid=794 name=/usr/sbin/mysqld
[    7.511285] type=1505 audit(1258687638.626:18): operation="profile_replace" pid=795 name=/usr/sbin/ntpd
[    7.512705] type=1505 audit(1258687638.626:19): operation="profile_replace" pid=796 name=/usr/sbin/tcpdump
[    7.617082] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.626547] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[    7.626556]   alloc irq_desc for 22 on node 0
[    7.626558]   alloc kstat_irqs on node 0
[    7.626566] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    8.370058] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[    8.880227] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[    8.880267] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[    8.881055] VIA 82xx Audio 0000:00:11.5: enabling device (0000 -> 0001)
[    8.881061] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    8.881211] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[    9.401062] codec_read: codec 0 is not valid [0xfe0000]
[    9.407926] codec_read: codec 0 is not valid [0xfe0000]
[    9.414845] codec_read: codec 0 is not valid [0xfe0000]
[    9.422307] codec_read: codec 0 is not valid [0xfe0000]
[   12.638019] usplash:325 freeing invalid memtype ffffffffe8000000-ffffffffe9000000
[   14.195846] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   14.195864] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   14.195927] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   14.526720] [drm] Setting GART location based on new memory map
[   14.526729] [drm] Loading R200 Microcode
[   14.526794] [drm] writeback test succeeded in 1 usecs
[   17.369553] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.762390] type=1503 audit(1258687649.876:20): operation="open" pid=1211 parent=1210 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.254304] type=1503 audit(1258687650.366:21): operation="open" pid=1251 parent=1250 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.704635] type=1503 audit(1258687650.816:22): operation="open" pid=1377 parent=1260 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.482571] type=1503 audit(1258687651.596:23): operation="open" pid=1391 parent=1390 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.951582] type=1503 audit(1258687653.066:24): operation="open" pid=1439 parent=1438 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.981193] type=1503 audit(1258687653.096:25): operation="open" pid=1450 parent=1449 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.984267] svc: failed to register lockdv1 RPC service (errno 97).
[   22.985132] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.991391] NFSD: starting 90-second grace period
[   24.445098] xfce4-volumed[1518] trap divide error ip:402f2d sp:7fff060396a0 error:0 in xfce4-volumed[400000+6000]
[   29.090388] wlan0: authenticate with AP 00:21:29:d6:42:b5
[   29.109344] wlan0: authenticated
[   29.109349] wlan0: associate with AP 00:21:29:d6:42:b5
[   29.112445] wlan0: RX AssocResp from 00:21:29:d6:42:b5 (capab=0x411 status=0 aid=4)
[   29.112449] wlan0: associated
[   29.113831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.447713] cfg80211: Calling CRDA for country: US
[   29.449573] cfg80211: Received country IE:
[   29.449577] cfg80211: Regulatory domain: US
[   29.449579] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.449582] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   29.449584] cfg80211: CRDA thinks this should applied:
[   29.449585] cfg80211: Regulatory domain: US
[   29.449586] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.449589] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   29.449591] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   29.449593] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.449596] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.449598] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   29.449600] cfg80211: We intersect both of these and get:
[   29.449601] cfg80211: Regulatory domain: 98
[   29.449603] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.449605] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   29.449610] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   29.449612] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   29.449614] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   29.449618] cfg80211: Current regulatory domain updated by AP to: US
[   29.449619] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.449622] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   40.020008] wlan0: no IPv6 routers present
[   92.060543] Marking TSC unstable due to cpufreq changes
[   92.640036] Clocksource tsc unstable (delta = -224183574 ns)
[  482.426401] udev: starting version 147
[  487.189643] type=1505 audit(1258688118.296:26): operation="profile_replace" pid=4153 name=/sbin/dhclient3
[  487.189899] type=1505 audit(1258688118.296:27): operation="profile_replace" pid=4153 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  487.190103] type=1505 audit(1258688118.306:28): operation="profile_replace" pid=4153 name=/usr/lib/connman/scripts/dhclient-script
[  487.195691] type=1505 audit(1258688118.306:29): operation="profile_replace" pid=4154 name=/usr/bin/evince
[  487.199907] type=1505 audit(1258688118.306:30): operation="profile_replace" pid=4154 name=/usr/bin/evince-previewer
[  487.203227] type=1505 audit(1258688118.316:31): operation="profile_replace" pid=4154 name=/usr/bin/evince-thumbnailer
[  487.208624] type=1505 audit(1258688118.316:32): operation="profile_replace" pid=4156 name=/usr/sbin/mysqld
[  487.210309] type=1505 audit(1258688118.326:33): operation="profile_replace" pid=4157 name=/usr/sbin/ntpd
[  487.212846] type=1505 audit(1258688118.326:34): operation="profile_replace" pid=4158 name=/usr/sbin/tcpdump
[  495.620900] __ratelimit: 9 callbacks suppressed
[  495.620903] type=1505 audit(1258688126.736:38): operation="profile_replace" pid=4189 name=/usr/bin/evince
[  495.622634] type=1505 audit(1258688126.736:39): operation="profile_replace" pid=4189 name=/usr/bin/evince-previewer
[  495.623738] type=1505 audit(1258688126.736:40): operation="profile_replace" pid=4189 name=/usr/bin/evince-thumbnailer
[  495.718256] type=1505 audit(1258688126.826:41): operation="profile_replace" pid=4191 name=/usr/sbin/mysqld
[  495.780907] type=1505 audit(1258688126.896:42): operation="profile_replace" pid=4192 name=/usr/sbin/ntpd
[  495.847149] type=1505 audit(1258688126.956:43): operation="profile_replace" pid=4193 name=/usr/sbin/tcpdump
[  520.718719] type=1505 audit(1258688151.826:44): operation="profile_replace" pid=4362 name=/usr/bin/evince
[  520.720478] type=1505 audit(1258688151.836:45): operation="profile_replace" pid=4362 name=/usr/bin/evince-previewer
[  520.721571] type=1505 audit(1258688151.836:46): operation="profile_replace" pid=4362 name=/usr/bin/evince-thumbnailer
[  534.123643] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  534.132196] SGI XFS Quota Management subsystem
[  534.181160] JFS: nTxBlock = 8192, nTxLock = 65536
[  534.288103] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  534.371934] QNX4 filesystem 0.2.3 registered.
```


New Drive???

---

### Post by klc5555 on 2009-11-20
Note that Ubuntu (since 8.04) is all scsi all the time. So mostly  Mythtv's default "/dev/dvd" goes nowhere.

Can you mount the drive as /dev/sr0 (or similar)? If so, you're in business. Then change references in the frontend setup from "/dev/dvd" to "/dev/sr0"

---

### Post by AlecJ on 2009-11-20
I had this problem, on 9.10
Turned out Thunar was not set to auto mount removable media when inserted.

Start Thunar file manager from the applications menu.
then Edit - Preferences
then Advanced

Make sure Enable Volume management is ticked then Click "Configure"

Make sure the top 2 boxes are ticked, Mount removable drives / Media

Close and re-insert DVD,  You should see the icon appear on the Desktop

---

### Post by SickNick on 2009-11-23
Hey guys I tried enabling that check box, which was unchecked. I reinserted the dvd and got nothing.

I switched to sr0 and got "mount: mount point /mnt/sr0 does not exist"

What ls command can I use to see what the CD drive maps to???

---

### Post by klc5555 on 2009-11-24
> **SickNick said:**
> Hey guys I tried enabling that check box, which was unchecked. I reinserted the dvd and got nothing.

I switched to sr0 and got "mount: mount point /mnt/sr0 does not exist"

What ls command can I use to see what the CD drive maps to???

If the OS can't autoload an unencrypted DVD for reading, and a mount point doesn't exist as /dev/dvd or /dev/sr0 (or sr1) or maybe /dev/sdX (where X=the letter after your last fixed drive, e.g. sdb, sdc, sde), then nicrout is likely right : "sometimes they just crap out".

If the OS can find and autoload an inserted unencrypted disk for reading, then, while the disk is still in the drive, df -h should give you all the fixed and removable disks the OS is accessing (where the DVD drive will be listed as 100% utilized).

---

### Post by SickNick on 2009-11-25
I just confirmed that it read an unencrypted DVD with data on it, with music production software on it. I have disk utility installed and also checked what that was showing. The device was mounted to /dev/sr0 to media/cdrom. When I insert a DVD i can check for media and the disk utility says nothing is in the drive. Any ideas???

---

### Post by nickrout on 2009-11-25
> **SickNick said:**
> I just confirmed that it read an unencrypted DVD with data on it, with music production software on it. I have disk utility installed and also checked what that was showing. The device was mounted to /dev/sr0 to media/cdrom. When I insert a DVD i can check for media and the disk utility says nothing is in the drive. Any ideas???

yes, what is the output of 

mount /dev/sr0 /media/cdrom ?

---

### Post by SickNick on 2009-11-25
Disk Utility has a GUI, what command can I use to see a verbose output from the cdrom?

---

### Post by nickrout on 2009-11-25
> **SickNick said:**
> Disk Utility has a GUI, what command can I use to see a verbose output from the cdrom?

Say again:

```
sudo mount /dev/sr0 /media/cdrom
```



You might then also get some useful info from:

```
dmesg
```

---

### Post by SickNick on 2009-11-25
Same output, dmesg might have gave some more useful info:
```

me@-mediacenter:~$ sudo mount /dev/sr0 /media/cdrom
mount: /dev/sr0: unknown device
me@-mediacenter:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=4c4f5287-58c2-4d6e-b1f2-d161032c5897 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
[    0.000000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ff30 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff30000 (usable)
[    0.000000]  modified: 000000007ff30000 - 000000007ff40000 (ACPI data)
[    0.000000]  modified: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007ff30000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007ff30000 page 4k
[    0.000000] kernel direct mapping tables up to 7ff30000 @ 10000-14000
[    0.000000] RAMDISK: 3786d000 - 37fef1ff
[    0.000000] ACPI: RSDP 00000000000fa850 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ff30000 00030 (v01 A M I  OEMRSDT  06000517 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ff30200 00081 (v01 A M I  OEMFACP  06000517 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ff303e0 03755 (v01  A0058 A0058002 00000002 MSFT 0100000D)
[    0.000000] ACPI: FACS 000000007ff40000 00040
[    0.000000] ACPI: APIC 000000007ff30390 0004A (v01 A M I  OEMAPIC  06000517 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ff40040 0003F (v01 A M I  OEMBIOS  06000517 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ff30000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ff30000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  0000000000026fe7] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007ff30000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786d000 - 0037fef1ff]          RAMDISK ==> [003786d000 - 0037fef1ff]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3294]              BRK ==> [00019e3000 - 00019e3294]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff30
[    0.000000] On node 0 totalpages: 523967
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3826 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 512874 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ff80000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f4000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516700
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=4c4f5287-58c2-4d6e-b1f2-d161032c5897 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ f8000000 old size 32 MB
[    0.000000] Aperture from AGP @ f8000000 size 64 MB (APSIZE f30)
[    0.000000] Node 0: aperture @ f8000000 size 64 MB
[    0.000000] Memory: 2049100k/2096320k available (5313k kernel code, 452k absent, 46768k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2403.251 MHz processor.
[    0.000016] spurious 8259A interrupt: IRQ7.
[    0.001171] Console: colour VGA+ 80x25
[    0.001174] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4806.50 BogoMIPS (lpj=24032510)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] tseg: 0000000000
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] Performance Counters: AMD PMU driver.
[    0.010000] ... version:                 0
[    0.010000] ... bit width:               48
[    0.010000] ... generic counters:        4
[    0.010000] ... value mask:              0000ffffffffffff
[    0.010000] ... max period:              00007fffffffffff
[    0.010000] ... fixed-purpose counters:  0
[    0.010000] ... counter mask:            000000000000000f
[    0.010000] SMP alternatives: switching to UP code
[    0.011565] Freeing SMP alternatives: 39k freed
[    0.011579] ACPI: Core revision 20090521
[    0.015930] Setting APIC routing to flat
[    0.016740] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.116771] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 0a
[    0.120000] Brought up 1 CPUs
[    0.120000] Total of 1 processors activated (4806.50 BogoMIPS).
[    0.120000] CPU0 attaching NULL sched-domain.
[    0.120000] Booting paravirtualized kernel on bare hardware
[    0.120000] regulator: core version 0.5
[    0.120000] Time: 20:35:35  Date: 11/25/09
[    0.120000] NET: Registered protocol family 16
[    0.120000] node 0 link 0: io port [1000, ffffff]
[    0.120000] TOM: 0000000080000000 aka 2048M
[    0.120000] node 0 link 0: mmio [a0000, bffff]
[    0.120000] node 0 link 0: mmio [80000000, ffffffff]
[    0.120000] bus: [00,ff] on node 0 link 0
[    0.120000] bus: 00 index 0 io port: [0, ffff]
[    0.120000] bus: 00 index 1 mmio: [a0000, bffff]
[    0.120000] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.120000] ACPI: bus type pci registered
[    0.120000] PCI: Using configuration type 1 for base access
[    0.120000] bio: create slab <bio-0> at 0
[    0.120000] ACPI: EC: Look up EC in DSDT
[    0.120000] ACPI: Interpreter enabled
[    0.120000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.120000] ACPI: Using IOAPIC for interrupt routing
[    0.121564] ACPI: No dock devices found.
[    0.121658] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.121707] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.121787] pci 0000:00:01.0: supports D1
[    0.121818] pci 0000:00:07.0: reg 10 32bit mmio: [0xfdf00000-0xfdf007ff]
[    0.121824] pci 0000:00:07.0: reg 14 io port: [0xc800-0xc87f]
[    0.121855] pci 0000:00:07.0: supports D2
[    0.121857] pci 0000:00:07.0: PME# supported from D2 D3hot D3cold
[    0.121861] pci 0000:00:07.0: PME# disabled
[    0.121892] pci 0000:00:0c.0: reg 10 io port: [0xc400-0xc4ff]
[    0.121897] pci 0000:00:0c.0: reg 14 32bit mmio: [0xfde00000-0xfde003ff]
[    0.121928] pci 0000:00:0c.0: supports D1 D2
[    0.121929] pci 0000:00:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.121933] pci 0000:00:0c.0: PME# disabled
[    0.121960] pci 0000:00:0d.0: reg 10 io port: [0xc000-0xc01f]
[    0.121965] pci 0000:00:0d.0: reg 14 io port: [0xb800-0xb80f]
[    0.121970] pci 0000:00:0d.0: reg 18 io port: [0xb400-0xb40f]
[    0.121976] pci 0000:00:0d.0: reg 1c io port: [0xb000-0xb03f]
[    0.121999] pci 0000:00:0d.0: supports D2
[    0.122027] pci 0000:00:0f.0: reg 10 io port: [0xe800-0xe807]
[    0.122032] pci 0000:00:0f.0: reg 14 io port: [0xe400-0xe403]
[    0.122038] pci 0000:00:0f.0: reg 18 io port: [0xe000-0xe007]
[    0.122043] pci 0000:00:0f.0: reg 1c io port: [0xd800-0xd803]
[    0.122048] pci 0000:00:0f.0: reg 20 io port: [0xd400-0xd40f]
[    0.122054] pci 0000:00:0f.0: reg 24 io port: [0xd000-0xd0ff]
[    0.122111] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.122175] pci 0000:00:10.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.122195] pci 0000:00:10.0: supports D1 D2
[    0.122197] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122201] pci 0000:00:10.0: PME# disabled
[    0.122239] pci 0000:00:10.1: reg 20 io port: [0xcc00-0xcc1f]
[    0.122259] pci 0000:00:10.1: supports D1 D2
[    0.122261] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122264] pci 0000:00:10.1: PME# disabled
[    0.122302] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[    0.122322] pci 0000:00:10.2: supports D1 D2
[    0.122323] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122327] pci 0000:00:10.2: PME# disabled
[    0.122365] pci 0000:00:10.3: reg 20 io port: [0xec00-0xec1f]
[    0.122385] pci 0000:00:10.3: supports D1 D2
[    0.122387] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122390] pci 0000:00:10.3: PME# disabled
[    0.122415] pci 0000:00:10.4: reg 10 32bit mmio: [0xfdb00000-0xfdb000ff]
[    0.122448] pci 0000:00:10.4: supports D1 D2
[    0.122450] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122453] pci 0000:00:10.4: PME# disabled
[    0.122504] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.122509] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.122552] pci 0000:00:11.5: reg 10 io port: [0x1000-0x10ff]
[    0.122587] pci 0000:00:11.5: supports D1 D2
[    0.122614] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.122727] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.122730] pci 0000:01:00.0: reg 14 io port: [0xa000-0xa0ff]
[    0.122734] pci 0000:01:00.0: reg 18 32bit mmio: [0xfd800000-0xfd80ffff]
[    0.122743] pci 0000:01:00.0: reg 30 32bit mmio: [0xfd700000-0xfd71ffff]
[    0.122754] pci 0000:01:00.0: supports D1 D2
[    0.122770] pci 0000:01:00.1: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.122774] pci 0000:01:00.1: reg 14 32bit mmio: [0xfd600000-0xfd60ffff]
[    0.122790] pci 0000:01:00.1: supports D1 D2
[    0.122814] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.122817] pci 0000:00:01.0: bridge 32bit mmio: [0xfd300000-0xfd8fffff]
[    0.122821] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd5200000-0xf51fffff]
[    0.122829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.127118] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.127189] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.127259] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.127328] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127398] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127538] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127609] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.127753] SCSI subsystem initialized
[    0.127812] libata version 3.00 loaded.
[    0.127870] usbcore: registered new interface driver usbfs
[    0.127883] usbcore: registered new interface driver hub
[    0.127911] usbcore: registered new device driver usb
[    0.128013] ACPI: WMI: Mapper loaded
[    0.128015] PCI: Using ACPI for IRQ routing
[    0.128023] pci 0000:00:00.0: BAR 0: address space collision on of device [0xf8000000-0xfbffffff]
[    0.128025] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.128147] Bluetooth: Core ver 2.15
[    0.128174] NET: Registered protocol family 31
[    0.128176] Bluetooth: HCI device and connection manager initialized
[    0.128179] Bluetooth: HCI socket layer initialized
[    0.128180] NetLabel: Initializing
[    0.128182] NetLabel:  domain hash size = 128
[    0.128183] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.128198] NetLabel:  unlabeled traffic allowed by default
[    0.128255] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[    0.131341] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.132770] pnp: PnP ACPI init
[    0.132792] ACPI: bus type pnp registered
[    0.134313] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134317] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134320] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134323] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134326] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134328] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134331] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134334] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134337] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134340] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134343] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134346] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.134348] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.135460] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135463] pnp 00:0c: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135466] pnp 00:0c: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135470] pnp 00:0c: mem resource (0x100000-0x7ffeffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.135705] pnp: PnP ACPI: found 13 devices
[    0.135706] ACPI: ACPI bus type pnp unregistered
[    0.135718] system 00:08: ioport range 0x295-0x296 has been reserved
[    0.135721] system 00:08: ioport range 0x3e1-0x3e7 has been reserved
[    0.135723] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.135726] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.135733] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.135738] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.135741] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.135744] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.140408] AppArmor: AppArmor Filesystem Enabled
[    0.140437] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.140440] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.140444] pci 0000:00:01.0:   MEM window: 0xfd300000-0xfd8fffff
[    0.140448] pci 0000:00:01.0:   PREFETCH window: 0xd5200000-0xf51fffff
[    0.140460] pci 0000:00:01.0: setting latency timer to 64
[    0.140465] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.140467] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.140470] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.140472] pci_bus 0000:01: resource 1 mem: [0xfd300000-0xfd8fffff]
[    0.140475] pci_bus 0000:01: resource 2 pref mem [0xd5200000-0xf51fffff]
[    0.140513] NET: Registered protocol family 2
[    0.140637] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.141719] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.145390] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.146325] TCP: Hash tables configured (established 262144 bind 65536)
[    0.146328] TCP reno registered
[    0.146431] NET: Registered protocol family 1
[    0.146499] Trying to unpack rootfs image as initramfs...
[    0.316017] Freeing initrd memory: 7688k freed
[    0.323109] Scanning for low memory corruption every 60 seconds
[    0.323259] audit: initializing netlink socket (disabled)
[    0.323276] type=2000 audit(1259181334.319:1): initialized
[    0.331269] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.332460] VFS: Disk quotas dquot_6.5.2
[    0.332509] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.333025] fuse init (API version 7.12)
[    0.333092] msgmni has been set to 4017
[    0.333254] alg: No test for stdrng (krng)
[    0.333263] io scheduler noop registered
[    0.333265] io scheduler anticipatory registered
[    0.333266] io scheduler deadline registered
[    0.333304] io scheduler cfq registered (default)
[    0.333313] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.360004] pci 0000:01:00.0: Boot video device
[    0.360096] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.360114] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.360209] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.360212] ACPI: Power Button [PWRF]
[    0.360259] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.360264] ACPI: Power Button [PWRB]
[    0.360300] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.360304] ACPI: Sleep Button [SLPB]
[    0.360444] processor LNXCPU:00: registered as cooling_device0
[    0.362959] Linux agpgart interface v0.103
[    0.362969] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.363063] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.363136] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.363346] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.363437] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.364193] brd: module loaded
[    0.364543] loop: module loaded
[    0.364608] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.365093] pata_via 0000:00:0f.1: version 0.3.4
[    0.365108]   alloc irq_desc for 20 on node 0
[    0.365110]   alloc kstat_irqs on node 0
[    0.365118] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.365304] scsi0 : pata_via
[    0.365390] scsi1 : pata_via
[    0.366803] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.366805] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.367091] Fixed MDIO Bus: probed
[    0.367121] PPP generic driver version 2.4.2
[    0.367188] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.367329]   alloc irq_desc for 21 on node 0
[    0.367330]   alloc kstat_irqs on node 0
[    0.367334] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.367351] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.367397] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.367464] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdb00000
[    0.379986] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.380056] usb usb1: configuration #1 chosen from 1 choice
[    0.380088] hub 1-0:1.0: USB hub found
[    0.380095] hub 1-0:1.0: 8 ports detected
[    0.380153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.380164] uhci_hcd: USB Universal Host Controller Interface driver
[    0.380229] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.380235] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.380260] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.380278] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000bc00
[    0.380340] usb usb2: configuration #1 chosen from 1 choice
[    0.380359] hub 2-0:1.0: USB hub found
[    0.380367] hub 2-0:1.0: 2 ports detected
[    0.380426] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.380431] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.380460] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.380478] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000cc00
[    0.380551] usb usb3: configuration #1 chosen from 1 choice
[    0.380570] hub 3-0:1.0: USB hub found
[    0.380576] hub 3-0:1.0: 2 ports detected
[    0.380627] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.380632] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.380658] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.380676] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.380740] usb usb4: configuration #1 chosen from 1 choice
[    0.380762] hub 4-0:1.0: USB hub found
[    0.380768] hub 4-0:1.0: 2 ports detected
[    0.380820] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.380825] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.380853] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.380871] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000ec00
[    0.380937] usb usb5: configuration #1 chosen from 1 choice
[    0.380955] hub 5-0:1.0: USB hub found
[    0.380962] hub 5-0:1.0: 2 ports detected
[    0.381033] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.381035] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.381435] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.381440] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.381486] mice: PS/2 mouse device common for all mice
[    0.381572] rtc_cmos 00:02: RTC can wake from S4
[    0.381602] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.381651] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.381736] device-mapper: uevent: version 1.0.3
[    0.381837] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.381882] device-mapper: multipath: version 1.1.0 loaded
[    0.381885] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.381989] cpuidle: using governor ladder
[    0.381991] cpuidle: using governor menu
[    0.382364] TCP cubic registered
[    0.382471] NET: Registered protocol family 10
[    0.382839] lo: Disabled Privacy Extensions
[    0.383072] NET: Registered protocol family 17
[    0.383088] Bluetooth: L2CAP ver 2.13
[    0.383090] Bluetooth: L2CAP socket layer initialized
[    0.383092] Bluetooth: SCO (Voice Link) ver 0.6
[    0.383094] Bluetooth: SCO socket layer initialized
[    0.383117] Bluetooth: RFCOMM TTY layer initialized
[    0.383120] Bluetooth: RFCOMM socket layer initialized
[    0.383121] Bluetooth: RFCOMM ver 1.11
[    0.383130] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    0.383176] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x2
[    0.383178] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x6
[    0.383180] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xa
[    0.383182] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
[    0.383184] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[    0.383263] PM: Resume from disk failed.
[    0.383275] registered taskstats version 1
[    0.383405]   Magic number: 1:63:600
[    0.383491] rtc_cmos 00:02: setting system clock to 2009-11-25 20:35:35 UTC (1259181335)
[    0.383494] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.383496] EDD information not available.
[    0.541630] ata1.00: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
[    0.541633] ata1.00: 390721968 sectors, multi 16: LBA48 
[    0.581482] ata1.00: configured for UDMA/100
[    0.581594] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-00G 08.0 PQ: 0 ANSI: 5
[    0.581685] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.581718] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    0.581755] sd 0:0:0:0: [sda] Write Protect is off
[    0.581757] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.581775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.581882]  sda: sda1 sda2 < sda5 >
[    0.628292] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.649976] Switched to high resolution mode on CPU 0
[    0.890357] ata2.01: ATAPI: LITE-ON DVDRW SOHW-1673S, JS01, max UDMA/66
[    0.890375] ata2.01: limited to UDMA/33 due to 40-wire cable
[    0.930007] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    0.930256] ata2.01: configured for UDMA/33
[    0.931501] scsi 1:0:1:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS01 PQ: 0 ANSI: 5
[    0.935034] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.935037] Uniform CD-ROM driver Revision: 3.20
[    0.935087] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    0.935116] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    0.935135] Freeing unused kernel memory: 660k freed
[    0.935625] Write protecting the kernel read-only data: 7580k
[    1.106036]   alloc irq_desc for 16 on node 0
[    1.106040]   alloc kstat_irqs on node 0
[    1.106049] ohci1394 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.110380] Floppy drive(s): fd0 is 1.44M
[    1.162310] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fdf00000-fdf007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.183534] FDC 0 is a post-1991 82077
[    1.189958] sata_via 0000:00:0f.0: version 2.4
[    1.189977] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.190052] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.190132] scsi2 : sata_via
[    1.190196] scsi3 : sata_via
[    1.190224] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 20
[    1.190226] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 20
[    1.190447] [drm] Initialized drm 1.1.0 20060810
[    1.202723] usb 3-2: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    1.299370] usb 3-2: configuration #1 chosen from 1 choice
[    1.308843] usbcore: registered new interface driver hiddev
[    1.322635] input: HID 0c16:0001 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
[    1.322708] generic-usb 0003:0C16:0001.0001: input,hidraw0: USB HID v1.00 Keyboard [HID 0c16:0001] on usb-0000:00:10.1-2/input0
[    1.352907] input: HID 0c16:0001 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input5
[    1.352995] generic-usb 0003:0C16:0001.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [HID 0c16:0001] on usb-0000:00:10.1-2/input1
[    1.353009] usbcore: registered new interface driver usbhid
[    1.353012] usbhid: v2.6:USB HID core driver
[    1.410035] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.630009] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.656789] [drm] radeon default to kernel modesetting DISABLED.
[    1.656902] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.657375] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    2.287969] PM: Starting manual resume from disk
[    2.287973] PM: Resume from partition 8:5
[    2.287975] PM: Checking hibernation image.
[    2.288110] PM: Resume from disk failed.
[    2.318133] EXT4-fs (sda1): barriers enabled
[    2.333805] kjournald2 starting: pid 366, dev sda1:8, commit interval 5 seconds
[    2.333816] EXT4-fs (sda1): delayed allocation enabled
[    2.333818] EXT4-fs: file extents enabled
[    2.358314] EXT4-fs: mballoc enabled
[    2.358333] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.510107] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000b062a8]
[    2.935316] type=1505 audit(1259181338.046:2): operation="profile_load" pid=389 name=/usr/share/gdm/guest-session/Xsession
[    2.937470] type=1505 audit(1259181338.046:3): operation="profile_load" pid=390 name=/sbin/dhclient3
[    2.937720] type=1505 audit(1259181338.046:4): operation="profile_load" pid=390 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.937862] type=1505 audit(1259181338.046:5): operation="profile_load" pid=390 name=/usr/lib/connman/scripts/dhclient-script
[    2.976119] type=1505 audit(1259181338.086:6): operation="profile_load" pid=391 name=/usr/bin/evince
[    2.980448] type=1505 audit(1259181338.096:7): operation="profile_load" pid=391 name=/usr/bin/evince-previewer
[    2.983002] type=1505 audit(1259181338.096:8): operation="profile_load" pid=391 name=/usr/bin/evince-thumbnailer
[    3.012913] type=1505 audit(1259181338.126:9): operation="profile_load" pid=393 name=/usr/lib/cups/backend/cups-pdf
[    3.013225] type=1505 audit(1259181338.126:10): operation="profile_load" pid=393 name=/usr/sbin/cupsd
[    3.854467] Adding 6024332k swap on /dev/sda5.  Priority:-1 extents:1 across:6024332k 
[    4.340599] EXT4-fs (sda1): internal journal on sda1:8
[    5.600269] RPC: Registered udp transport module.
[    5.600273] RPC: Registered tcp transport module.
[    6.318628] udev: starting version 147
[    7.141614] __ratelimit: 9 callbacks suppressed
[    7.141617] type=1505 audit(1259181342.256:14): operation="profile_replace" pid=698 name=/usr/share/gdm/guest-session/Xsession
[    7.143024] type=1505 audit(1259181342.256:15): operation="profile_replace" pid=699 name=/sbin/dhclient3
[    7.143276] type=1505 audit(1259181342.256:16): operation="profile_replace" pid=699 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.143418] type=1505 audit(1259181342.256:17): operation="profile_replace" pid=699 name=/usr/lib/connman/scripts/dhclient-script
[    7.148063] type=1505 audit(1259181342.256:18): operation="profile_replace" pid=700 name=/usr/bin/evince
[    7.153644] type=1505 audit(1259181342.266:19): operation="profile_replace" pid=700 name=/usr/bin/evince-previewer
[    7.156189] type=1505 audit(1259181342.266:20): operation="profile_replace" pid=700 name=/usr/bin/evince-thumbnailer
[    7.169938] type=1505 audit(1259181342.276:21): operation="profile_replace" pid=704 name=/usr/lib/cups/backend/cups-pdf
[    7.170316] type=1505 audit(1259181342.286:22): operation="profile_replace" pid=704 name=/usr/sbin/cupsd
[    7.172720] type=1505 audit(1259181342.286:23): operation="profile_replace" pid=705 name=/usr/sbin/mysqld
[    7.904817] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.965606] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    8.179013] cfg80211: Calling CRDA to update world regulatory domain
[    8.198881] lp: driver loaded but no devices found
[    8.570263] cfg80211: World regulatory domain updated:
[    8.570267] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.570270] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.570272] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.570275] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.570277] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.570279] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.612760] parport_pc 00:07: reported by Plug and Play ACPI
[    8.612801] parport0: PC-style at 0x378, irq 7 [PCSPP]
[    8.690133] lp0: using parport0 (interrupt-driven).
[    8.813320] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    8.813410] EDAC amd64: ECC is enabled by BIOS, Proceeding with EDAC module initialization
[    8.813448] EDAC MC: Rev E or earlier detected
[    8.813518] EDAC MC0: Giving out device to 'amd64_edac' 'RevF': DEV 0000:00:18.2
[    8.813539] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
[    8.988133] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[    9.454079] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    9.456466] ppdev: user-space parallel port driver
[    9.678974] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.881512]   alloc irq_desc for 17 on node 0
[    9.881516]   alloc kstat_irqs on node 0
[    9.881524] rtl8180 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.232998] phy0: Selected rate control algorithm 'minstrel'
[   11.233571] phy0: hwaddr 00:18:e7:76:4e:45, RTL8185vD + rtl8225z2
[   11.887402] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   11.887410]   alloc irq_desc for 22 on node 0
[   11.887412]   alloc kstat_irqs on node 0
[   11.887420] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   12.630013] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   13.140241] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   13.140282] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   13.141005] VIA 82xx Audio 0000:00:11.5: enabling device (0000 -> 0001)
[   13.141011] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.141161] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   13.661044] codec_read: codec 0 is not valid [0xfe0000]
[   13.668070] codec_read: codec 0 is not valid [0xfe0000]
[   13.674958] codec_read: codec 0 is not valid [0xfe0000]
[   13.682145] codec_read: codec 0 is not valid [0xfe0000]
[   13.698689]   alloc irq_desc for 18 on node 0
[   13.698693]   alloc kstat_irqs on node 0
[   13.698702] ICE1712 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.166867] usplash:329 freeing invalid memtype ffffffffe8000000-ffffffffe9000000
[   18.276147] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   18.276166] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   18.276228] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   18.716667] [drm] Setting GART location based on new memory map
[   18.716676] [drm] Loading R200 Microcode
[   18.716742] [drm] writeback test succeeded in 1 usecs
[   22.640404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.528655] __ratelimit: 6 callbacks suppressed
[   24.528658] type=1503 audit(1259181359.636:26): operation="open" pid=1283 parent=1282 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.361070] type=1503 audit(1259181360.476:27): operation="open" pid=1334 parent=1333 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.520242] type=1503 audit(1259181361.636:28): operation="open" pid=1459 parent=1341 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.730676] type=1503 audit(1259181361.846:29): operation="open" pid=1465 parent=1464 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.754362] type=1503 audit(1259181362.866:30): operation="open" pid=1481 parent=1480 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.093158] type=1503 audit(1259181364.206:31): operation="open" pid=1509 parent=1508 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.224740] type=1503 audit(1259181364.336:32): operation="open" pid=1520 parent=1519 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   30.207717] svc: failed to register lockdv1 RPC service (errno 97).
[   30.208459] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   30.208653] NFSD: starting 90-second grace period
[   43.410155] xfce4-volumed[1675] trap divide error ip:402f2d sp:7fffff0878a0 error:0 in xfce4-volumed[400000+6000]
[   44.480010] wlan0: authenticate with AP 00:21:29:d6:42:b5
[   44.531008] wlan0: authenticated
[   44.531015] wlan0: associate with AP 00:21:29:d6:42:b5
[   44.731797] wlan0: associate with AP 00:21:29:d6:42:b5
[   44.850624] wlan0: RX AssocResp from 00:21:29:d6:42:b5 (capab=0x411 status=0 aid=1)
[   44.850630] wlan0: associated
[   44.851681] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.304556] cfg80211: Calling CRDA for country: US
[   47.306435] cfg80211: Received country IE:
[   47.306439] cfg80211: Regulatory domain: US
[   47.306441] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.306443] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   47.306445] cfg80211: CRDA thinks this should applied:
[   47.306446] cfg80211: Regulatory domain: US
[   47.306448] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.306450] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   47.306452] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   47.306454] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.306456] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.306459] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   47.306460] cfg80211: We intersect both of these and get:
[   47.306461] cfg80211: Regulatory domain: 98
[   47.306463] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.306465] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   47.306470] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   47.306472] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   47.306474] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   47.306477] cfg80211: Current regulatory domain updated by AP to: US
[   47.306479] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.306481] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   55.030006] wlan0: no IPv6 routers present
[  105.920521] Marking TSC unstable due to cpufreq changes
[  106.140029] Clocksource tsc unstable (delta = -136090211 ns)

```

---

### Post by nickrout on 2009-11-25
I assume you mean sme output as in "/media/cdrom does not exist"

I tild you in my first post to make sure the mount point exists. So:

```
sudo mkdir /media/cdrom
mount /dev/sr0 /media/cdrom
```

---

### Post by SickNick on 2009-11-25
Just tried that out. This is what the output was:

```

$ sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists
$ sudo mount /dev/sr0 /media/cdrom
mount: /dev/sr0: unknown device

```

---

### Post by nickrout on 2009-11-25
This is getting confusing. dmesg certainly shows the drive being detected. No doubt about that.

I am quite confused myself about what device is allocated to DVD/CD drives in current kernels. Try```
mount /dev/scd0 /media/cdrom
```

alternatively ```
ls /dev/s*
``` may give some clues as to what device is allocated.

---

### Post by SickNick on 2009-11-25
Thank you so much for your patience, I really appreciate your help. I tried the two lines above and got this in return.

```
$ sudo mount /dev/scd0 /media/cdrom

mount: /dev/sr0: unknown device

$ ls /dev/s*
/dev/scd0  /dev/sda2       /dev/sequencer2  /dev/snapshot  /dev/stderr
/dev/sda   /dev/sda5       /dev/sg0         /dev/sndstat   /dev/stdin
/dev/sda1  /dev/sequencer  /dev/sg1         /dev/sr0       /dev/stdout

/dev/shm:
pulse-shm-1204070811  pulse-shm-265765729   pulse-shm-4258502047
pulse-shm-1526833940  pulse-shm-3858260802  pulse-shm-995341608
pulse-shm-2439403108  pulse-shm-418181167

/dev/snd:
by-path    controlC1  pcmC0D0c  pcmC0D1c  pcmC1D0c  seq
controlC0  midiC1D0   pcmC0D0p  pcmC0D1p  pcmC1D0p  timer

```

---

### Post by nickrout on 2009-11-25
```
ls -ld /dev/sr0 /dev/scd0
```

---

### Post by AlecJ on 2009-11-27
Did this drive work before 9.10? it's not region locked or anything silly?

---

### Post by SickNick on 2009-11-28
```
$ ls -ld /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2009-11-28 18:33 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-11-28 18:33 /dev/sr0

```

On Mythbuntu 9.04 the drive was mounting and ripping very few DVDs. Now it just dosen't mount them

---

### Post by nickrout on 2009-11-29
> **SickNick said:**
> ```
$ ls -ld /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2009-11-28 18:33 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-11-28 18:33 /dev/sr0

```

On Mythbuntu 9.04 the drive was mounting and ripping very few DVDs. Now it just dosen't mount them

is the user that is trying to mount the dvd a member of the cdrom group?

---

### Post by SickNick on 2009-11-30
Just checked, and yup the user trying to mount the dvd is a cdrom user of the group

---

### Post by SickNick on 2009-12-02
No other ideas???

---

### Post by dewmanstl on 2009-12-04
> **SickNick said:**
> No other ideas???
 
Yank the drive and plop in a new one....Sounds like the drive could be borked...

---

### Post by SickNick on 2009-12-07
Good news... I yanked out the drive, plopped in my drive from my computer...started the computer...inserted a dvd................. and it mounted :D. Im gonna order a new drive for his computer from newegg this week.

But...I had 1 problem, which happened on my own computer at my house as well as my friends (even though this is using the same CD drive that I popped in my friends computer) not sure if I should start a new thread for this but heres the new problem (which occured on both computers, but using the same CD drive)

I am pretty sure this is purely a MythTV problem. When I goto rip the DVD it loads up the job, always with the DVD name "Unknown" normally I think it should detect the DVD name. Second after I wrote in the DVD name when I tried to Start Rip, I could just select it nothing happens. Another thing I noticed is right above that there are two blank transparrent buttons over some Check Box. Im sure if I use another ripper ill be able to do the job but just wanted to see if its fixable. Anyone ever heard of this problem???

---

### Post by tgm4883 on 2009-12-07
> **SickNick said:**
> Good news... I yanked out the drive, plopped in my drive from my computer...started the computer...inserted a dvd................. and it mounted :D. Im gonna order a new drive for his computer from newegg this week.

But...I had 1 problem, which happened on my own computer at my house as well as my friends (even though this is using the same CD drive that I popped in my friends computer) not sure if I should start a new thread for this but heres the new problem (which occured on both computers, but using the same CD drive)

I am pretty sure this is purely a MythTV problem. When I goto rip the DVD it loads up the job, always with the DVD name "Unknown" normally I think it should detect the DVD name. Second after I wrote in the DVD name when I tried to Start Rip, I could just select it nothing happens. Another thing I noticed is right above that there are two blank transparrent buttons over some Check Box. Im sure if I use another ripper ill be able to do the job but just wanted to see if its fixable. Anyone ever heard of this problem???

Probably due to this [http://www.mythbuntu.org/FAQ](http://www.mythbuntu.org/FAQ) see the last one.

---

### Post by SickNick on 2010-01-02
Can you link me to an updated link. I finally put in the new drive everything is perfect except for MythTV doing that. Thank you

---

### Post by tgm4883 on 2010-01-03
[http://www.mythbuntu.org/wiki/faq](http://www.mythbuntu.org/wiki/faq)

---

### Post by SickNick on 2010-01-25
Sorry for the very delayed responses. Turns out its not exactly what you think. I probably would have ran into that problem after this current one. This time I took a screenshot so you can see my interface, its easier like this than trying to describe what I am seeing.

[[IMG]http://img704.imageshack.us/img704/1015/screenshotcr.th.png[/IMG]](http://img704.imageshack.us/i/screenshotcr.png/)

Has anyone seen anything like this?

---

### Post by SickNick on 2010-02-04
Nobody has ever seen anything like this?? 

Im really stuck.

---

