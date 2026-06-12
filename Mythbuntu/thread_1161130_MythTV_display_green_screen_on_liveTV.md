---
title: "MythTV display green screen on liveTV"
date: 2009-05-16
forum: Mythbuntu
---

### Post by iankellogg on 2009-05-16
I previously had mythbuntu 9.04 installed on my computer. Everything worked perfectly on the mythbuntu install. However, I bought new harddrives and had to install regular Ubuntu 9.04 to get the raid to work.  After getting ubuntu all set up and testing the playback of the ATI TV Wonder VE in tvtime I installed mythbuntu-desktop.  I setup everything as I had in mythbuntu including nvidia display driver 180. But now in mythtv any channel above 16 is displayed as a green screen or some other pattern. Doesn't do this in TVtime and doesn't do this on channels 2-16. Any ideas?

---

### Post by vapblack on 2009-05-19
I'm pretty sure I have a similar problem... here's a screenshot if anyone knows why..

[IMG]http://farm4.static.flickr.com/3609/3547769344_6724930b11_b.jpg[/IMG]

as you can probably see, I have my wii connected and am trying to play megaman 9..:confused:

---

### Post by nickrout on 2009-05-19
> **iankellogg said:**
> I previously had mythbuntu 9.04 installed on my computer. Everything worked perfectly on the mythbuntu install. However, I bought new harddrives and had to install regular Ubuntu 9.04 to get the raid to work.  After getting ubuntu all set up and testing the playback of the ATI TV Wonder VE in tvtime I installed mythbuntu-desktop.  I setup everything as I had in mythbuntu including nvidia display driver 180. But now in mythtv any channel above 16 is displayed as a green screen or some other pattern. Doesn't do this in TVtime and doesn't do this on channels 2-16. Any ideas?

yes, look at the frontend logs and tell us what you see when you switch to a channel above 16 :)

---

### Post by cybermatthieu on 2009-05-21
Hi,
I'm also having troubles with my ATI TV WONDER (first version). Every thing was working fine in Mythbuntu 8.10 but now when I have a show with fast action (sports, camera panning) I get small grey lines on the display.

Don't really know where to look I never had any problem with my card before...

Any clue?

---

### Post by nickrout on 2009-05-21
your thumbnail is from tvtime not mythtv so is irrelevant.

Your post might be relevant if it referred to mythtv AND included the log files I referred to in my earlier post.

---

### Post by cybermatthieu on 2009-05-22
Hi,
Sorry I wasn't clear it does it in Mythtv AND tvtime... I think it's has to do with the bttv driver.

---

### Post by nickrout on 2009-05-22
Where is your log?

---

### Post by cybermatthieu on 2009-05-25
That's the thing... which log should I check?

Here are my dmesg and my myth logs...

I didn't find anything wrong in them...

dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009ec00/0009ec00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=aa47eb56-c142-4e7e-aecc-0956cb838a23 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077f90000 (usable)
[    0.000000]  BIOS-e820: 0000000077f90000 - 0000000077f9e000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077f9e000 - 0000000077fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077fe0000 - 0000000077fee000 (reserved)
[    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x77f90 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077f90000 (usable)
[    0.000000]  modified: 0000000077f90000 - 0000000077f9e000 (ACPI data)
[    0.000000]  modified: 0000000077f9e000 - 0000000077fe0000 (ACPI NVS)
[    0.000000]  modified: 0000000077fe0000 - 0000000077fee000 (reserved)
[    0.000000]  modified: 0000000077ff0000 - 0000000078000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-0000000077f90000
[    0.000000]  0000000000 - 0077e00000 page 2M
[    0.000000]  0077e00000 - 0077f90000 page 4k
[    0.000000] kernel direct mapping tables up to 77f90000 @ 10000-14000
[    0.000000] last_map_addr: 77f90000 end: 77f90000
[    0.000000] RAMDISK: 3784e000 - 37fef7ef
[    0.000000] ACPI: RSDP 000FB6B0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 77F90000, 0044 (r1 091608 RSDT1442 20080916 MSFT       97)
[    0.000000] ACPI: FACP 77F90200, 0084 (r1 091608 FACP1442 20080916 MSFT       97)
[    0.000000] ACPI: DSDT 77F90450, AA8D (r1  A1043 A1043000        0 INTL 20051117)
[    0.000000] ACPI: FACS 77F9E000, 0040
[    0.000000] ACPI: APIC 77F90390, 0080 (r1 091608 APIC1442 20080916 MSFT       97)
[    0.000000] ACPI: MCFG 77F90410, 003C (r1 091608 OEMMCFG  20080916 MSFT       97)
[    0.000000] ACPI: OEMB 77F9E040, 0072 (r1 091608 OEMB1442 20080916 MSFT       97)
[    0.000000] ACPI: HPET 77F9AEE0, 0038 (r1 091608 OEMHPET0 20080916 MSFT       97)
[    0.000000] ACPI: INFO 77F9E0C0, 0124 (r1 091608 AMDINFO  20080916 MSFT       97)
[    0.000000] ACPI: NVHD 77F9E1F0, 0284 (r1 091608  NVHDCP  20080916 MSFT       97)
[    0.000000] ACPI: SSDT 77F9AF20, 028A (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 0077f90000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003784e000 - 0037fef7ef]          RAMDISK ==> [003784e000 - 0037fef7ef]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x00077f90
[    0.000000] On node 0 totalpages: 491294
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2541 pages reserved
[    0.000000]   DMA zone: 1385 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6663 pages used for memmap
[    0.000000]   DMA32 zone: 480649 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86c00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 482034
[    0.000000] Kernel command line: root=UUID=aa47eb56-c142-4e7e-aecc-0956cb838a23 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2599.784 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 19660800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ b930000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1895684k/1965632k available (4760k kernel code, 456k absent, 68928k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5199.56 BogoMIPS (lpj=10399136)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] tseg: 0000000000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.004401] ACPI: Checking initramfs for custom DSDT
[    0.242590] Setting APIC routing to flat
[    0.243124] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.282814] CPU0: AMD Athlon(tm) Dual Core Processor 5050e stepping 02
[    0.284001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5199.98 BogoMIPS (lpj=10399962)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.368142] CPU1: AMD Athlon(tm) Dual Core Processor 5050e stepping 02
[    0.368157] Brought up 2 CPUs
[    0.368159] Total of 2 processors activated (10399.54 BogoMIPS).
[    0.368245] CPU0 attaching sched-domain:
[    0.368247]  domain 0: span 0-1 level CPU
[    0.368249]   groups: 0 1
[    0.368253] CPU1 attaching sched-domain:
[    0.368254]  domain 0: span 0-1 level CPU
[    0.368255]   groups: 1 0
[    0.368307] net_namespace: 1400 bytes
[    0.368307] Booting paravirtualized kernel on bare hardware
[    0.368307] Time: 22:04:27  Date: 05/24/09
[    0.368307] regulator: core version 0.5
[    0.368307] NET: Registered protocol family 16
[    0.368307] node 0 link 0: io port [1000, ffffff]
[    0.368307] node 0 link 0: io port [1000, 1fff]
[    0.368307] TOM: 0000000080000000 aka 2048M
[    0.368307] node 0 link 0: mmio [e0000000, efffffff]
[    0.368307] node 0 link 0: mmio [a0000, bffff]
[    0.368307] node 0 link 0: mmio [80000000, fe0bffff]
[    0.368307] bus: [00,07] on node 0 link 0
[    0.368307] bus: 00 index 0 io port: [0, ffff]
[    0.368307] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.368307] bus: 00 index 2 mmio: [a0000, bffff]
[    0.368307] ACPI: bus type pci registered
[    0.368307] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.368307] PCI: Not using MMCONFIG.
[    0.368307] PCI: Using configuration type 1 for base access
[    0.368307] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.368307] mtrr: probably your BIOS does not setup all CPUs.
[    0.368307] mtrr: corrected configuration.
[    0.368896] ACPI: EC: Look up EC in DSDT
[    0.388406] ACPI: Interpreter enabled
[    0.388410] ACPI: (supports S0 S1 S3 S4 S5)
[    0.388426] ACPI: Using IOAPIC for interrupt routing
[    0.388494] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.398379] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.410227] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.428507] ACPI: No dock devices found.
[    0.428596] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.428809] pci 0000:00:01.0: reg 10 io port: [0x900-0x9ff]
[    0.428844] pci 0000:00:01.1: reg 10 io port: [0xe00-0xe3f]
[    0.428854] pci 0000:00:01.1: reg 20 io port: [0x600-0x63f]
[    0.428857] pci 0000:00:01.1: reg 24 io port: [0x700-0x73f]
[    0.428867] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.428872] pci 0000:00:01.1: PME# disabled
[    0.428926] pci 0000:00:01.3: reg 10 32bit mmio: [0xfcf80000-0xfcffffff]
[    0.429040] pci 0000:00:02.0: reg 10 32bit mmio: [0xfcf7e000-0xfcf7efff]
[    0.429057] pci 0000:00:02.0: supports D1 D2
[    0.429058] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429061] pci 0000:00:02.0: PME# disabled
[    0.429081] pci 0000:00:02.1: reg 10 32bit mmio: [0xfcf7fc00-0xfcf7fcff]
[    0.429100] pci 0000:00:02.1: supports D1 D2
[    0.429101] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429104] pci 0000:00:02.1: PME# disabled
[    0.429127] pci 0000:00:04.0: reg 10 32bit mmio: [0xfcf7d000-0xfcf7dfff]
[    0.429145] pci 0000:00:04.0: supports D1 D2
[    0.429146] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429148] pci 0000:00:04.0: PME# disabled
[    0.429169] pci 0000:00:04.1: reg 10 32bit mmio: [0xfcf7f800-0xfcf7f8ff]
[    0.429187] pci 0000:00:04.1: supports D1 D2
[    0.429189] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429191] pci 0000:00:04.1: PME# disabled
[    0.429222] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.429253] pci 0000:00:07.0: reg 10 32bit mmio: [0xfcf78000-0xfcf7bfff]
[    0.429270] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.429272] pci 0000:00:07.0: PME# disabled
[    0.429316] pci 0000:00:09.0: reg 10 io port: [0xd480-0xd487]
[    0.429319] pci 0000:00:09.0: reg 14 io port: [0xd400-0xd403]
[    0.429322] pci 0000:00:09.0: reg 18 io port: [0xd080-0xd087]
[    0.429325] pci 0000:00:09.0: reg 1c io port: [0xd000-0xd003]
[    0.429328] pci 0000:00:09.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.429331] pci 0000:00:09.0: reg 24 32bit mmio: [0xfcf76000-0xfcf77fff]
[    0.429358] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfcf7c000-0xfcf7cfff]
[    0.429362] pci 0000:00:0a.0: reg 14 io port: [0xc880-0xc887]
[    0.429365] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfcf7f400-0xfcf7f4ff]
[    0.429368] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfcf7f000-0xfcf7f00f]
[    0.429378] pci 0000:00:0a.0: supports D1 D2
[    0.429379] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429383] pci 0000:00:0a.0: PME# disabled
[    0.429405] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429407] pci 0000:00:0b.0: PME# disabled
[    0.429546] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429553] pci 0000:00:10.0: PME# disabled
[    0.429720] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429727] pci 0000:00:12.0: PME# disabled
[    0.429894] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429900] pci 0000:00:13.0: PME# disabled
[    0.430005] pci 0000:01:06.0: reg 10 32bit mmio: [0xdfffe000-0xdfffefff]
[    0.430039] pci 0000:01:06.1: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.430089] pci 0000:00:08.0: transparent bridge
[    0.430093] pci 0000:00:08.0: bridge 32bit mmio pref: [0xdff00000-0xdfffffff]
[    0.430109] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.430114] pci 0000:02:00.0: reg 14 64bit mmio: [0xf0000000-0xf7ffffff]
[    0.430118] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.430121] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.430124] pci 0000:02:00.0: reg 30 32bit mmio: [0xfeae0000-0xfeafffff]
[    0.430143] pci 0000:00:0b.0: bridge io port: [0xe000-0xefff]
[    0.430145] pci 0000:00:0b.0: bridge 32bit mmio: [0xfd000000-0xfeafffff]
[    0.430148] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xf0000000-0xfbffffff]
[    0.430326] pci 0000:05:00.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.430334] pci 0000:05:00.0: reg 14 32bit mmio: [0xfebff400-0xfebff47f]
[    0.430355] pci 0000:05:00.0: reg 20 32bit mmio: [0xfebff000-0xfebff07f]
[    0.430363] pci 0000:05:00.0: reg 24 32bit mmio: [0xfebfec00-0xfebfec7f]
[    0.430436] pci 0000:00:13.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.430487] bus 00 -> node 0
[    0.430492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.430928] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.431089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.431207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.431341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.431477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.450181] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.450480] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.450777] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.451074] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.451373] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.451669] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.451969] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.452278] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.452574] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.452869] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.453165] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.453461] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.453764] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.454060] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.454357] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.454652] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.454952] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
[    0.455248] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.455544] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.455840] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.456148] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.456444] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.456740] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.457036] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.457332] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.457628] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.457924] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.458221] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.458518] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.458819] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.459117] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.459417] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.459714] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.460022] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.460319] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.460615] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.460915] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.461214] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.461513] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.461813] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.462112] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.462412] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *15
[    0.462712] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[    0.463011] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.463359] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.463659] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *15
[    0.463959] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
[    0.464091] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 60, should be 53 [20080926]
[    0.464201] ACPI: WMI: Mapper loaded
[    0.464270] SCSI subsystem initialized
[    0.464270] libata version 3.00 loaded.
[    0.464270] usbcore: registered new interface driver usbfs
[    0.464270] usbcore: registered new interface driver hub
[    0.464270] usbcore: registered new device driver usb
[    0.464270] PCI: Using ACPI for IRQ routing
[    0.480008] Bluetooth: Core ver 2.13
[    0.480020] NET: Registered protocol family 31
[    0.480020] Bluetooth: HCI device and connection manager initialized
[    0.480020] Bluetooth: HCI socket layer initialized
[    0.480020] NET: Registered protocol family 8
[    0.480021] NET: Registered protocol family 20
[    0.480028] NetLabel: Initializing
[    0.480029] NetLabel:  domain hash size = 128
[    0.480030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.480043] NetLabel:  unlabeled traffic allowed by default
[    0.480279] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.480282] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.484059] AppArmor: AppArmor Filesystem Enabled
[    0.488013] Switched to high resolution mode on CPU 0
[    0.488154] Switched to high resolution mode on CPU 1
[    0.496013] pnp: PnP ACPI init
[    0.496024] ACPI: bus type pnp registered
[    0.499857] pnp 00:06: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.499860] pnp 00:06: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.506742] pnp: PnP ACPI: found 14 devices
[    0.506743] ACPI: ACPI bus type pnp unregistered
[    0.506753] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.506755] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.506757] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.506758] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.506760] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.506762] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.506764] system 00:06: ioport range 0xd00-0xd7f has been reserved
[    0.506766] system 00:06: ioport range 0xd80-0xdff has been reserved
[    0.506769] system 00:06: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.506771] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.506776] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.506778] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.506782] system 00:0a: ioport range 0x230-0x23f has been reserved
[    0.506784] system 00:0a: ioport range 0x290-0x29f has been reserved
[    0.506786] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.506788] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.506791] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.506796] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.506798] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.506800] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.506802] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    0.506804] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.511470] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.511472] pci 0000:00:08.0:   IO window: disabled
[    0.511475] pci 0000:00:08.0:   MEM window: disabled
[    0.511477] pci 0000:00:08.0:   PREFETCH window: 0x000000dff00000-0x000000dfffffff
[    0.511481] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.511483] pci 0000:00:0b.0:   IO window: 0xe000-0xefff
[    0.511485] pci 0000:00:0b.0:   MEM window: 0xfd000000-0xfeafffff
[    0.511487] pci 0000:00:0b.0:   PREFETCH window: 0x000000f0000000-0x000000fbffffff
[    0.511490] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.511492] pci 0000:00:10.0:   IO window: disabled
[    0.511500] pci 0000:00:10.0:   MEM window: disabled
[    0.511507] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.511519] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.511520] pci 0000:00:12.0:   IO window: disabled
[    0.511528] pci 0000:00:12.0:   MEM window: disabled
[    0.511535] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.511547] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.511548] pci 0000:00:13.0:   IO window: disabled
[    0.511557] pci 0000:00:13.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.511563] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.511580] pci 0000:00:08.0: setting latency timer to 64
[    0.511584] pci 0000:00:0b.0: setting latency timer to 64
[    0.512012] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.512019] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.512027] pci 0000:00:10.0: setting latency timer to 64
[    0.512433] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.512439] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.512446] pci 0000:00:12.0: setting latency timer to 64
[    0.512851] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.512857] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.512864] pci 0000:00:13.0: setting latency timer to 64
[    0.512870] bus: 00 index 0 io port: [0x00-0xffff]
[    0.512871] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.512873] bus: 01 index 0 mmio: [0x0-0x0]
[    0.512874] bus: 01 index 1 mmio: [0x0-0x0]
[    0.512875] bus: 01 index 2 mmio: [0xdff00000-0xdfffffff]
[    0.512877] bus: 01 index 3 io port: [0x00-0xffff]
[    0.512878] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.512880] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.512881] bus: 02 index 1 mmio: [0xfd000000-0xfeafffff]
[    0.512883] bus: 02 index 2 mmio: [0xf0000000-0xfbffffff]
[    0.512884] bus: 02 index 3 mmio: [0x0-0x0]
[    0.512885] bus: 03 index 0 mmio: [0x0-0x0]
[    0.512886] bus: 03 index 1 mmio: [0x0-0x0]
[    0.512888] bus: 03 index 2 mmio: [0x0-0x0]
[    0.512889] bus: 03 index 3 mmio: [0x0-0x0]
[    0.512890] bus: 04 index 0 mmio: [0x0-0x0]
[    0.512891] bus: 04 index 1 mmio: [0x0-0x0]
[    0.512893] bus: 04 index 2 mmio: [0x0-0x0]
[    0.512894] bus: 04 index 3 mmio: [0x0-0x0]
[    0.512895] bus: 05 index 0 mmio: [0x0-0x0]
[    0.512897] bus: 05 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.512898] bus: 05 index 2 mmio: [0x0-0x0]
[    0.512899] bus: 05 index 3 mmio: [0x0-0x0]
[    0.512910] NET: Registered protocol family 2
[    0.548053] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.548450] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.550008] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.550418] TCP: Hash tables configured (established 262144 bind 65536)
[    0.550421] TCP reno registered
[    0.560104] NET: Registered protocol family 1
[    0.560207] checking if image is initramfs... it is
[    1.039135] Freeing initrd memory: 7813k freed
[    1.042999] audit: initializing netlink socket (disabled)
[    1.043015] type=2000 audit(1243202667.040:1): initialized
[    1.049285] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.050199] VFS: Disk quotas dquot_6.5.1
[    1.050237] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.050676] fuse init (API version 7.10)
[    1.050734] msgmni has been set to 3718
[    1.050891] alg: No test for stdrng (krng)
[    1.050904] io scheduler noop registered
[    1.050906] io scheduler anticipatory registered
[    1.050907] io scheduler deadline registered
[    1.050939] io scheduler cfq registered (default)
[    1.120597] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.120624] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.120652] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.120681] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.120708] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.120763] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.120828] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.120893] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.120937] pci 0000:02:00.0: Boot video device
[    1.134340] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.134509] pcieport-driver 0000:00:10.0: found MSI capability
[    1.134592] pcieport-driver 0000:00:10.0: irq 2303 for MSI/MSI-X
[    1.134624] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.134799] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.134965] pcieport-driver 0000:00:12.0: found MSI capability
[    1.135043] pcieport-driver 0000:00:12.0: irq 2302 for MSI/MSI-X
[    1.135075] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.135246] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.135412] pcieport-driver 0000:00:13.0: found MSI capability
[    1.135489] pcieport-driver 0000:00:13.0: irq 2301 for MSI/MSI-X
[    1.135521] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.135664] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.135670] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.135784] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.135786] ACPI: Power Button (FF) [PWRF]
[    1.135822] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.135823] ACPI: Power Button (CM) [PWRB]
[    1.136105] processor ACPI_CPU:00: registered as cooling_device0
[    1.136130] processor ACPI_CPU:01: registered as cooling_device1
[    1.172775] Linux agpgart interface v0.103
[    1.172783] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.172874] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.173109] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.173706] brd: module loaded
[    1.173946] loop: module loaded
[    1.174007] Fixed MDIO Bus: probed
[    1.174011] PPP generic driver version 2.4.2
[    1.174057] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.174083] Driver 'sd' needs updating - please use bus_type methods
[    1.174090] Driver 'sr' needs updating - please use bus_type methods
[    1.174127] ahci 0000:00:09.0: version 3.0
[    1.174593] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.174604] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.174646] ahci 0000:00:09.0: irq 2300 for MSI/MSI-X
[    1.174721] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.174724] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.174726] ahci 0000:00:09.0: setting latency timer to 64
[    1.175205] scsi0 : ahci
[    1.175330] scsi1 : ahci
[    1.175396] scsi2 : ahci
[    1.175456] scsi3 : ahci
[    1.175515] scsi4 : ahci
[    1.175575] scsi5 : ahci
[    1.175675] ata1: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76100 irq 2300
[    1.175677] ata2: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76180 irq 2300
[    1.175679] ata3: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76200 irq 2300
[    1.175681] ata4: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76280 irq 2300
[    1.175683] ata5: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76300 irq 2300
[    1.175685] ata6: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76380 irq 2300
[    1.656018] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.657326] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    1.657328] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.659092] ata1.00: configured for UDMA/133
[    1.976016] ata2: SATA link down (SStatus 0 SControl 300)
[    2.296015] ata3: SATA link down (SStatus 0 SControl 300)
[    2.616015] ata4: SATA link down (SStatus 0 SControl 300)
[    2.936014] ata5: SATA link down (SStatus 0 SControl 300)
[    3.256015] ata6: SATA link down (SStatus 0 SControl 300)
[    3.256109] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    3.256184] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.256197] sd 0:0:0:0: [sda] Write Protect is off
[    3.256199] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.256217] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.256284] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.256295] sd 0:0:0:0: [sda] Write Protect is off
[    3.256296] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.256313] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.256316]  sda: sda1 sda2 < sda5 sda6 >
[    3.294773] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.294816] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.294999] pata_amd 0000:00:06.0: version 0.3.10
[    3.295035] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.295124] scsi6 : pata_amd
[    3.295184] scsi7 : pata_amd
[    3.296274] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.296276] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.460353] ata7.00: ATAPI: PIONEER DVD-RW  DVR-110D, 1.11, max UDMA/66
[    3.460370] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    3.476293] ata7.00: configured for UDMA/66
[    3.476605] ata8: port disabled. ignoring.
[    3.476625] isa bounce pool size: 16 pages
[    3.482974] scsi 6:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.11 PQ: 0 ANSI: 5
[    3.506236] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    3.506239] Uniform CD-ROM driver Revision: 3.20
[    3.506323] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    3.506356] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    3.506691] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.507156] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    3.507166] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    3.507182] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.507185] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.507230] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.507257] ehci_hcd 0000:00:02.1: debug port 1
[    3.507260] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.507281] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfcf7fc00
[    3.516021] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.516078] usb usb1: configuration #1 chosen from 1 choice
[    3.516099] hub 1-0:1.0: USB hub found
[    3.516105] hub 1-0:1.0: 6 ports detected
[    3.516602] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    3.516609] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    3.516619] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.516621] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.516653] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    3.516676] ehci_hcd 0000:00:04.1: debug port 1
[    3.516679] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.516699] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfcf7f800
[    3.528015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.528061] usb usb2: configuration #1 chosen from 1 choice
[    3.528079] hub 2-0:1.0: USB hub found
[    3.528084] hub 2-0:1.0: 6 ports detected
[    3.528156] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.528587] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    3.528593] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    3.528602] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.528604] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.528639] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    3.528659] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfcf7e000
[    3.586038] usb usb3: configuration #1 chosen from 1 choice
[    3.586058] hub 3-0:1.0: USB hub found
[    3.586066] hub 3-0:1.0: 6 ports detected
[    3.586540] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    3.586543] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    3.586551] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.586553] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.586584] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    3.586603] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfcf7d000
[    3.642036] usb usb4: configuration #1 chosen from 1 choice
[    3.642055] hub 4-0:1.0: USB hub found
[    3.642061] hub 4-0:1.0: 6 ports detected
[    3.642129] uhci_hcd: USB Universal Host Controller Interface driver
[    3.642186] usbcore: registered new interface driver libusual
[    3.642212] usbcore: registered new interface driver usbserial
[    3.642220] USB Serial support registered for generic
[    3.642234] usbcore: registered new interface driver usbserial_generic
[    3.642235] usbserial: USB Serial Driver core
[    3.642273] PNP: No PS/2 controller found. Probing ports directly.
[    3.642622] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.642627] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.652534] mice: PS/2 mouse device common for all mice
[    3.688561] rtc_cmos 00:08: RTC can wake from S4
[    3.688590] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    3.688641] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    3.688694] device-mapper: uevent: version 1.0.3
[    3.688768] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.688893] device-mapper: multipath: version 1.0.5 loaded
[    3.688896] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.689033] cpuidle: using governor ladder
[    3.689035] cpuidle: using governor menu
[    3.689362] TCP cubic registered
[    3.689415] NET: Registered protocol family 10
[    3.689725] lo: Disabled Privacy Extensions
[    3.689930] NET: Registered protocol family 17
[    3.689947] Bluetooth: L2CAP ver 2.11
[    3.689948] Bluetooth: L2CAP socket layer initialized
[    3.689950] Bluetooth: SCO (Voice Link) ver 0.6
[    3.689951] Bluetooth: SCO socket layer initialized
[    3.689994] Bluetooth: RFCOMM socket layer initialized
[    3.690000] Bluetooth: RFCOMM TTY layer initialized
[    3.690002] Bluetooth: RFCOMM ver 1.10
[    3.690042] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 5050e processors (2 cpu cores) (version 2.20.00)
[    3.690096] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0xe
[    3.690098] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0x10
[    3.690100] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x12
[    3.690101] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x14
[    3.690102] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x16
[    3.690104] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x1a
[    3.690135] powernow-k8: ph2 null fid transition 0x12
[    3.690298] registered taskstats version 1
[    3.690443]   Magic number: 9:644:98
[    3.690446] input mouse0: hash matches
[    3.690565] rtc_cmos 00:08: setting system clock to 2009-05-24 22:04:30 UTC (1243202670)
[    3.690567] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.690569] EDD information not available.
[    3.690607] Freeing unused kernel memory: 536k freed
[    3.690847] Write protecting the kernel read-only data: 6708k
[    3.904382] FDC 0 is a post-1991 82077
[    3.948843] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.949320] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    3.949324] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    3.949329] forcedeth 0000:00:0a.0: setting latency timer to 64
[    3.978961] ohci1394 0000:05:00.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    3.978969] ohci1394 0000:05:00.0: setting latency timer to 64
[    4.030720] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.069807] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:23:54:63:00:ba
[    4.069811] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    4.092538] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    4.307156] usb 3-5: configuration #1 chosen from 1 choice
[    4.317937] usbcore: registered new interface driver hiddev
[    4.318044] usbcore: registered new interface driver usbhid
[    4.318046] usbhid: v2.6:USB HID core driver
[    4.333756] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.0/input/input3
[    4.360658] gyration 0003:0C16:0002.0001: input,hiddev96,hidraw0: USB HID v1.10 Keyboard [Gyration Gyration RF Technology Receiver] on usb-0000:00:02.0-5/input0
[    4.369734] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.1/input/input4
[    4.408671] gyration 0003:0C16:0002.0002: input,hiddev97,hidraw1: USB HID v1.20 Mouse [Gyration Gyration RF Technology Receiver] on usb-0000:00:02.0-5/input1
[    4.480762] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    4.507657] PM: Starting manual resume from disk
[    4.507660] PM: Resume from partition 8:5
[    4.507661] PM: Checking hibernation image.
[    4.507963] PM: Resume from disk failed.
[    4.525792] kjournald starting.  Commit interval 5 seconds
[    4.525813] EXT3-fs: mounted filesystem with ordered data mode.
[    4.614660] usb 2-4: configuration #1 chosen from 1 choice
[    4.944586] Initializing USB Mass Storage driver...
[    4.944696] scsi8 : SCSI emulation for USB Mass Storage devices
[    4.944767] usbcore: registered new interface driver usb-storage
[    4.944769] USB Mass Storage support registered.
[    4.944901] usb-storage: device found at 3
[    4.944902] usb-storage: waiting for device to settle before scanning
[    5.028528] usb 4-3: new low speed USB device using ohci_hcd and address 2
[    5.243485] usb 4-3: configuration #1 chosen from 1 choice
[    5.316666] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00019c576c]
[    5.548542] usb 4-6: new full speed USB device using ohci_hcd and address 3
[    5.723553] udev: starting version 141
[    5.776151] usb 4-6: configuration #1 chosen from 1 choice
[    5.823429] parport_pc 00:05: reported by Plug and Play ACPI
[    5.823478] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    5.867468] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input5
[    5.892196] logitech 0003:046D:C517.0003: input,hidraw2: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:04.0-3/input0
[    5.901051] logitech 0003:046D:C517.0004: fixing up Logitech keyboard report descriptor
[    5.901968] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.1/input/input6
[    5.935531] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.948196] logitech 0003:046D:C517.0004: input,hiddev98,hidraw3: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:04.0-3/input1
[    6.035225] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    6.400445] nvidia: module license 'NVIDIA' taints kernel.
[    6.654329] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
[    6.654334] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 21 (level, low) -> IRQ 21
[    6.654341] nvidia 0000:02:00.0: setting latency timer to 64
[    6.655556] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[    6.790040] ppdev: user-space parallel port driver
[    6.800894] USB Serial support registered for FTDI USB Serial Device
[    6.800973] ftdi_sio 4-6:1.0: FTDI USB Serial Device converter detected
[    6.801016] usb 4-6: Detected FT232RL
[    6.801077] usb 4-6: FTDI USB Serial Device converter now attached to ttyUSB0
[    6.801090] usbcore: registered new interface driver ftdi_sio
[    6.801093] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[    6.864086] Linux video capture interface: v2.00
[    6.899366] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[    6.899377] Bt87x 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 16 (level, low) -> IRQ 16
[    6.899629] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[    6.912712] bttv: driver version 0.9.17 loaded
[    6.912715] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    6.912766] bttv: Bt8xx card found (0).
[    6.912781] bttv 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, low) -> IRQ 16
[    6.912789] bttv0: Bt878 (rev 2) at 0000:01:06.0, irq: 16, latency: 64, mmio: 0xdfffe000
[    6.913301] bttv0: detected: ATI TV Wonder [card=63], PCI subsystem ID is 1002:0001
[    6.913304] bttv0: using: ATI TV-Wonder [card=63,autodetected]
[    6.913334] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[    6.913391] bttv0: tuner type=19
[    6.913393] bttv0: i2c: checking for MSP34xx @ 0x80... found
[    6.925336] msp3400' 0-0040: MSP3430G-A1 found @ 0x80 (bt878 #0 [sw])
[    6.925339] msp3400' 0-0040: msp3400 supports radio, mode is autodetect and autoselect
[    6.926094] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[    6.926644] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[    6.967547] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    6.968060] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[    6.968063] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[    6.968113] HDA Intel 0000:00:07.0: setting latency timer to 64
[    6.988740] All bytes are equal. It is not a TEA5767
[    6.988800] tuner' 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[    6.995844] tuner-simple 0-0060: creating new instance
[    6.995848] tuner-simple 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[    7.004585] bttv0: registered device video0
[    7.004623] bttv0: registered device vbi0
[    7.020378] bttv0: PLL: 28636363 => 35468950 .. ok
[    7.871232] lp0: using parport0 (interrupt-driven).
[    8.077835] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[    8.662437] EXT3 FS on sda1, internal journal
[    9.573319] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    9.574887] SGI XFS Quota Management subsystem
[    9.609522] XFS mounting filesystem sda6
[    9.786164] Ending clean XFS mount for filesystem: sda6
[    9.945022] usb-storage: device scan complete
[    9.946994] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    9.947484] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    9.947984] scsi 8:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    9.948485] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    9.950653] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[    9.950713] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    9.951742] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[    9.951805] sd 8:0:0:1: Attached scsi generic sg3 type 0
[    9.952975] sd 8:0:0:2: [sdd] Attached SCSI removable disk
[    9.953040] sd 8:0:0:2: Attached scsi generic sg4 type 0
[    9.954318] sd 8:0:0:3: [sde] Attached SCSI removable disk
[    9.954684] sd 8:0:0:3: Attached scsi generic sg5 type 0
[   10.884985] type=1505 audit(1243202677.693:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2319
[   10.885116] type=1505 audit(1243202677.693:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2319
[   10.885153] type=1505 audit(1243202677.693:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2319
[   10.885190] type=1505 audit(1243202677.693:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2319
[   10.994299] type=1505 audit(1243202677.801:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2324
[   10.994461] type=1505 audit(1243202677.801:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2324
[   11.020184] type=1505 audit(1243202677.825:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2328
[   11.044801] type=1505 audit(1243202677.853:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2332
[   18.830557] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.830559] Bluetooth: BNEP filters: protocol multicast
[   18.850147] Bridge firewalling registered
[   18.999830] bttv0: PLL can sleep, using XTAL (28636363).

```

mythbackend :
```
2009-05-20 19:22:35.017 Using runtime prefix = /usr
2009-05-20 19:22:35.064 Empty LocalHostName.
2009-05-20 19:22:35.079 Using localhost value of myth
2009-05-20 19:22:35.115 New DB connection, total: 1
2009-05-20 19:22:35.247 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:35.287 Closing DB connection named 'DBManager0'
2009-05-20 19:22:35.335 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:35.418 New DB connection, total: 2
2009-05-20 19:22:35.422 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:35.441 Current Schema Version: 1214
Starting up as the master server.
2009-05-20 19:22:35.537 New DB connection, total: 3
2009-05-20 19:22:35.539 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:35.629 New DB scheduler connection
2009-05-20 19:22:35.634 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:35.658 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-20 19:22:35.686 Main::Registering HttpStatus Extension
2009-05-20 19:22:35.701 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 19:22:35.715 Enabled verbose msgs:  important general
2009-05-20 19:22:35.740 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 19:22:38.639 Reschedule requested for id -1.
2009-05-20 19:22:38.663 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-05-20 19:22:38.740 Seem to be woken up by USER
2009-05-20 19:22:45.452 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 19:22:45.559 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2009-05-18T19:22:45') OR (status in (304) AND statustime < '2009-05-16T19:22:45')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 19:22:45.569 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-20T15:22:45' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 19:22:45.576 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 19:22:45.582 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 19:22:45.640 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-20 23:22:55.824 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:23:47.091 MainServer::HandleAnnounce Monitor
2009-05-20 23:23:47.169 adding: myth as a client (events: 0)
2009-05-20 23:23:47.172 MainServer::HandleAnnounce Monitor
2009-05-20 23:23:47.174 adding: myth as a client (events: 1)
2009-05-20 23:23:47.181 MainServer::HandleAnnounce Playback
2009-05-20 23:23:47.184 adding: myth as a client (events: 0)
2009-05-20 23:23:47.190 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:23:47.200 TVRec(1): HW Tuner: 1->1
2009-05-20 23:23:48.552 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:23:48.558 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:23:48.610 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:24:04.890 TVRec(1): HW Tuner: 1->1
2009-05-20 23:24:04.939 Finished recording Unknown: channel 1002
2009-05-20 23:24:05.990 Finished recording Unknown: channel 1002
2009-05-20 23:24:06.012 TVRec(1): RingBufferChanged()
2009-05-20 23:24:06.088 Finished recording Unknown: channel 1002
2009-05-20 23:24:06.116 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:24:06.214 Using runtime prefix = /usr
2009-05-20 23:24:06.239 Empty LocalHostName.
2009-05-20 23:24:06.241 Using localhost value of myth
2009-05-20 23:24:06.258 New DB connection, total: 1
2009-05-20 23:24:06.271 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:06.275 Closing DB connection named 'DBManager0'
2009-05-20 23:24:06.278 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:06.281 New DB connection, total: 2
2009-05-20 23:24:06.284 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:06.289 Current Schema Version: 1214
2009-05-20 23:24:06.446 Preview: Grabbed preview '/var/lib/mythtv/recordings/1002_20090520232347.nuv' 480x480@64s
2009-05-20 23:24:14.203 TVRec(1): HW Tuner: 1->1
2009-05-20 23:24:14.272 Finished recording Unknown: channel 1055
2009-05-20 23:24:15.315 Finished recording Unknown: channel 1055
2009-05-20 23:24:15.421 TVRec(1): RingBufferChanged()
2009-05-20 23:24:15.492 Finished recording Unknown: channel 1055
2009-05-20 23:24:15.501 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:24:15.514 Using runtime prefix = /usr
2009-05-20 23:24:15.519 Empty LocalHostName.
2009-05-20 23:24:15.611 Using localhost value of myth
2009-05-20 23:24:15.636 New DB connection, total: 1
2009-05-20 23:24:15.646 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:15.650 Closing DB connection named 'DBManager0'
2009-05-20 23:24:15.654 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:15.658 New DB connection, total: 2
2009-05-20 23:24:15.660 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:15.664 Current Schema Version: 1214
2009-05-20 23:24:15.797 Preview: Grabbed preview '/var/lib/mythtv/recordings/1055_20090520232404.nuv' 480x480@64s
2009-05-20 23:24:21.624 TVRec(1): HW Tuner: 1->1
2009-05-20 23:24:21.761 Finished recording Unknown: channel 1049
2009-05-20 23:24:22.803 Finished recording Unknown: channel 1049
2009-05-20 23:24:22.934 TVRec(1): RingBufferChanged()
2009-05-20 23:24:23.000 Using runtime prefix = /usr
2009-05-20 23:24:23.007 Finished recording Unknown: channel 1049
2009-05-20 23:24:23.050 Empty LocalHostName.
2009-05-20 23:24:23.107 Using localhost value of myth
2009-05-20 23:24:23.110 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:24:23.127 New DB connection, total: 1
2009-05-20 23:24:23.137 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:23.142 Closing DB connection named 'DBManager0'
2009-05-20 23:24:23.147 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:23.150 New DB connection, total: 2
2009-05-20 23:24:23.152 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:23.156 Current Schema Version: 1214
2009-05-20 23:24:23.279 Preview: Grabbed preview '/var/lib/mythtv/recordings/1049_20090520232414.nuv' 480x480@64s
2009-05-20 23:24:31.954 TVRec(1): HW Tuner: 1->1
2009-05-20 23:24:32.010 Finished recording Unknown: channel 1048
2009-05-20 23:24:33.057 Finished recording Unknown: channel 1048
2009-05-20 23:24:33.188 TVRec(1): RingBufferChanged()
2009-05-20 23:24:33.238 Using runtime prefix = /usr
2009-05-20 23:24:33.254 Empty LocalHostName.
2009-05-20 23:24:33.256 Using localhost value of myth
2009-05-20 23:24:33.259 Finished recording Unknown: channel 1048
2009-05-20 23:24:33.270 New DB connection, total: 1
2009-05-20 23:24:33.311 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:24:33.351 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:33.371 Closing DB connection named 'DBManager0'
2009-05-20 23:24:33.378 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:33.381 New DB connection, total: 2
2009-05-20 23:24:33.384 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:24:33.388 Current Schema Version: 1214
2009-05-20 23:24:33.514 Preview: Grabbed preview '/var/lib/mythtv/recordings/1048_20090520232421.nuv' 480x480@64s
2009-05-20 23:24:37.366 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 23:24:37.558 Finished recording Unknown: channel 1053
2009-05-20 23:32:00.943 Using runtime prefix = /usr
2009-05-20 23:32:00.988 Empty LocalHostName.
2009-05-20 23:32:00.997 Using localhost value of myth
2009-05-20 23:32:01.014 New DB connection, total: 1
2009-05-20 23:32:01.023 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:32:01.026 Closing DB connection named 'DBManager0'
2009-05-20 23:32:01.029 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:32:01.032 New DB connection, total: 2
2009-05-20 23:32:01.034 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:32:01.039 Current Schema Version: 1214
Starting up as the master server.
2009-05-20 23:32:01.065 New DB connection, total: 3
2009-05-20 23:32:01.067 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:32:01.228 New DB scheduler connection
2009-05-20 23:32:01.233 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:32:01.253 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-20 23:32:01.255 Main::Registering HttpStatus Extension
2009-05-20 23:32:01.257 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:32:01.259 Enabled verbose msgs:  important general
2009-05-20 23:32:01.265 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:32:04.260 Reschedule requested for id -1.
2009-05-20 23:32:04.300 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2009-05-20 23:32:04.308 Seem to be woken up by USER
2009-05-20 23:32:21.241 Expiring 19 MBytes for 1002 @ Wed May 20 23:23:47 2009 => Unknown
2009-05-20 23:32:21.248 Expiring 8 MBytes for 1055 @ Wed May 20 23:24:04 2009 => Unknown
2009-05-20 23:32:21.253 Expiring 6 MBytes for 1049 @ Wed May 20 23:24:14 2009 => Unknown
2009-05-20 23:32:21.255 Expiring 8 MBytes for 1048 @ Wed May 20 23:24:21 2009 => Unknown
2009-05-20 23:32:21.256 Expiring 4 MBytes for 1053 @ Wed May 20 23:24:32 2009 => Unknown
2009-05-20 23:32:28.267 New DB connection, total: 4
2009-05-20 23:32:30.413 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:33:21.260 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:33:25.075 MainServer::HandleAnnounce Monitor
2009-05-20 23:33:25.091 adding: myth as a client (events: 0)
2009-05-20 23:33:25.093 MainServer::HandleAnnounce Monitor
2009-05-20 23:33:25.095 adding: myth as a client (events: 1)
2009-05-20 23:33:25.097 Reschedule requested for id -1.
2009-05-20 23:33:25.097 MythSocket(98ceb0:-1): writeStringList: Error, called with unconnected socket.
2009-05-20 23:33:25.118 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-05-20 23:33:51.189 MainServer::HandleAnnounce Monitor
2009-05-20 23:33:51.198 adding: myth as a client (events: 0)
2009-05-20 23:33:51.201 MainServer::HandleAnnounce Monitor
2009-05-20 23:33:51.203 adding: myth as a client (events: 1)
2009-05-20 23:33:51.213 MainServer::HandleAnnounce Playback
2009-05-20 23:33:51.218 adding: myth as a client (events: 0)
2009-05-20 23:33:51.221 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:33:51.234 TVRec(1): HW Tuner: 1->1
2009-05-20 23:33:52.372 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:33:52.374 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:33:52.403 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:34:00.669 TVRec(1): HW Tuner: 1->1
2009-05-20 23:34:00.711 Finished recording Paris bouche &#8730;† bouche: channel 1053
2009-05-20 23:34:01.765 Finished recording Paris bouche &#8730;† bouche: channel 1053
2009-05-20 23:34:01.954 Using runtime prefix = /usr
2009-05-20 23:34:01.961 Empty LocalHostName.
2009-05-20 23:34:01.963 Using localhost value of myth
2009-05-20 23:34:01.977 New DB connection, total: 1
2009-05-20 23:34:01.986 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:01.991 Closing DB connection named 'DBManager0'
2009-05-20 23:34:01.994 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:01.996 TVRec(1): RingBufferChanged()
2009-05-20 23:34:01.999 New DB connection, total: 2
2009-05-20 23:34:02.050 Finished recording Paris bouche &#8730;† bouche: channel 1053
2009-05-20 23:34:02.050 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:02.061 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:34:02.069 Current Schema Version: 1214
2009-05-20 23:34:02.276 Preview: Grabbed preview '/var/lib/mythtv/recordings/1053_20090520233351.nuv' 480x480@64s
2009-05-20 23:34:06.389 TVRec(1): HW Tuner: 1->1
2009-05-20 23:34:06.436 Finished recording The Ultimate Fighter: channel 1048
2009-05-20 23:34:07.517 Finished recording The Ultimate Fighter: channel 1048
2009-05-20 23:34:07.593 TVRec(1): RingBufferChanged()
2009-05-20 23:34:07.655 Finished recording The Ultimate Fighter: channel 1048
2009-05-20 23:34:07.682 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:34:07.721 Using runtime prefix = /usr
2009-05-20 23:34:07.727 Empty LocalHostName.
2009-05-20 23:34:07.729 Using localhost value of myth
2009-05-20 23:34:07.743 New DB connection, total: 1
2009-05-20 23:34:07.757 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:07.760 Closing DB connection named 'DBManager0'
2009-05-20 23:34:07.763 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:07.772 New DB connection, total: 2
2009-05-20 23:34:07.779 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:07.788 Current Schema Version: 1214
2009-05-20 23:34:07.895 Preview: Grabbed preview '/var/lib/mythtv/recordings/1048_20090520233400.nuv' 480x480@64s
2009-05-20 23:34:10.700 TVRec(1): HW Tuner: 1->1
2009-05-20 23:34:10.760 Finished recording Marine Machines "Diggers": channel 1047
2009-05-20 23:34:11.809 Finished recording Marine Machines "Diggers": channel 1047
2009-05-20 23:34:11.932 TVRec(1): RingBufferChanged()
2009-05-20 23:34:12.003 Finished recording Marine Machines "Diggers": channel 1047
2009-05-20 23:34:12.005 Using runtime prefix = /usr
2009-05-20 23:34:12.012 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:34:12.126 Empty LocalHostName.
2009-05-20 23:34:12.147 Using localhost value of myth
2009-05-20 23:34:12.162 New DB connection, total: 1
2009-05-20 23:34:12.172 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:12.175 Closing DB connection named 'DBManager0'
2009-05-20 23:34:12.177 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:12.188 New DB connection, total: 2
2009-05-20 23:34:12.194 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:34:12.203 Current Schema Version: 1214
2009-05-20 23:34:12.303 Preview: Grabbed preview '/var/lib/mythtv/recordings/1047_20090520233406.nuv' 480x480@64s
2009-05-20 23:34:43.928 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 23:34:44.105 Finished recording Nouvelles: channel 1046
2009-05-20 23:36:21.287 Expiring 2 MBytes for 1053 @ Wed May 20 23:00:00 2009 => Paris bouche ‡ bouche
2009-05-20 23:36:21.291 Expiring 1 MBytes for 1048 @ Wed May 20 23:30:00 2009 => The Ultimate Fighter
2009-05-20 23:36:21.298 Expiring 1 MBytes for 1047 @ Wed May 20 23:00:00 2009 => Marine Machines "Diggers"
2009-05-20 23:36:21.300 Expiring 12 MBytes for 1046 @ Wed May 20 22:00:00 2009 => Nouvelles
2009-05-20 23:40:37.995 Using runtime prefix = /usr
2009-05-20 23:40:38.049 Empty LocalHostName.
2009-05-20 23:40:38.053 Using localhost value of myth
2009-05-20 23:40:38.069 New DB connection, total: 1
2009-05-20 23:40:38.078 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:40:38.080 Closing DB connection named 'DBManager0'
2009-05-20 23:40:38.083 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:40:38.086 New DB connection, total: 2
2009-05-20 23:40:38.089 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:40:38.093 Current Schema Version: 1214
Starting up as the master server.
2009-05-20 23:40:38.122 New DB connection, total: 3
2009-05-20 23:40:38.125 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:40:38.305 New DB scheduler connection
2009-05-20 23:40:38.313 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:40:38.336 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-20 23:40:38.339 Main::Registering HttpStatus Extension
2009-05-20 23:40:38.341 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:40:38.343 Enabled verbose msgs:  important general
2009-05-20 23:40:38.346 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:40:41.320 Reschedule requested for id -1.
2009-05-20 23:40:41.356 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-05-20 23:40:41.365 Seem to be woken up by USER
2009-05-20 23:40:58.795 MainServer::HandleAnnounce Monitor
2009-05-20 23:40:58.800 adding: myth as a client (events: 0)
2009-05-20 23:40:58.802 MainServer::HandleAnnounce Monitor
2009-05-20 23:40:58.803 adding: myth as a client (events: 1)
2009-05-20 23:40:58.805 Reschedule requested for id -1.
2009-05-20 23:40:58.832 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2009-05-20 23:41:17.960 MainServer::HandleAnnounce Monitor
2009-05-20 23:41:17.967 adding: myth as a client (events: 0)
2009-05-20 23:41:17.969 MainServer::HandleAnnounce Monitor
2009-05-20 23:41:17.971 adding: myth as a client (events: 1)
2009-05-20 23:41:17.979 MainServer::HandleAnnounce Playback
2009-05-20 23:41:17.983 adding: myth as a client (events: 0)
2009-05-20 23:41:17.986 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:41:17.993 TVRec(1): HW Tuner: 1->1
2009-05-20 23:41:19.135 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:41:19.137 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:41:19.163 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:41:58.331 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:42:01.224 TVRec(1): HW Tuner: 1->1
2009-05-20 23:42:01.273 Finished recording The Hour: channel 1002
2009-05-20 23:42:02.328 Finished recording The Hour: channel 1002
2009-05-20 23:42:02.372 TVRec(1): RingBufferChanged()
2009-05-20 23:42:02.438 Finished recording The Hour: channel 1002
2009-05-20 23:42:02.465 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:42:02.576 Using runtime prefix = /usr
2009-05-20 23:42:02.584 Empty LocalHostName.
2009-05-20 23:42:02.586 Using localhost value of myth
2009-05-20 23:42:02.602 New DB connection, total: 1
2009-05-20 23:42:02.612 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:02.615 Closing DB connection named 'DBManager0'
2009-05-20 23:42:02.619 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:02.629 New DB connection, total: 2
2009-05-20 23:42:02.631 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:02.637 Current Schema Version: 1214
2009-05-20 23:42:02.782 Preview: Grabbed preview '/var/lib/mythtv/recordings/1002_20090520234118.nuv' 480x480@64s
2009-05-20 23:42:13.147 TVRec(1): HW Tuner: 1->1
2009-05-20 23:42:13.223 Finished recording La Zone: channel 1003
2009-05-20 23:42:14.270 Finished recording La Zone: channel 1003
2009-05-20 23:42:14.353 TVRec(1): RingBufferChanged()
2009-05-20 23:42:14.466 Using runtime prefix = /usr
2009-05-20 23:42:14.467 Finished recording La Zone: channel 1003
2009-05-20 23:42:14.474 Empty LocalHostName.
2009-05-20 23:42:14.476 Using localhost value of myth
2009-05-20 23:42:14.485 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:42:14.509 New DB connection, total: 1
2009-05-20 23:42:14.524 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:14.527 Closing DB connection named 'DBManager0'
2009-05-20 23:42:14.530 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:14.539 New DB connection, total: 2
2009-05-20 23:42:14.546 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:14.556 Current Schema Version: 1214
2009-05-20 23:42:14.677 Preview: Grabbed preview '/var/lib/mythtv/recordings/1003_20090520234201.nuv' 480x480@64s
2009-05-20 23:42:29.288 TVRec(1): HW Tuner: 1->1
2009-05-20 23:42:29.344 Finished recording Late Show With David Letterman: channel 1014
2009-05-20 23:42:30.388 Finished recording Late Show With David Letterman: channel 1014
2009-05-20 23:42:30.494 TVRec(1): RingBufferChanged()
2009-05-20 23:42:30.564 Finished recording Late Show With David Letterman: channel 1014
2009-05-20 23:42:30.574 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:42:30.576 Using runtime prefix = /usr
2009-05-20 23:42:30.590 Empty LocalHostName.
2009-05-20 23:42:30.592 Using localhost value of myth
2009-05-20 23:42:30.607 New DB connection, total: 1
2009-05-20 23:42:30.650 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:30.653 Closing DB connection named 'DBManager0'
2009-05-20 23:42:30.656 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:30.666 New DB connection, total: 2
2009-05-20 23:42:30.681 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:30.703 Current Schema Version: 1214
2009-05-20 23:42:30.808 Preview: Grabbed preview '/var/lib/mythtv/recordings/1014_20090520234213.nuv' 480x480@64s
2009-05-20 23:43:05.263 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 23:43:05.475 Finished recording Vid&#8730;©o patrouille: channel 1020
2009-05-20 23:44:10.573 Using runtime prefix = /usr
2009-05-20 23:44:10.611 Empty LocalHostName.
2009-05-20 23:44:10.615 Using localhost value of myth
2009-05-20 23:44:10.631 New DB connection, total: 1
2009-05-20 23:44:10.639 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:10.642 Closing DB connection named 'DBManager0'
2009-05-20 23:44:10.645 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:10.649 New DB connection, total: 2
2009-05-20 23:44:10.652 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:10.656 Current Schema Version: 1214
Starting up as the master server.
2009-05-20 23:44:10.683 New DB connection, total: 3
2009-05-20 23:44:10.687 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:10.873 New DB scheduler connection
2009-05-20 23:44:10.882 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:10.905 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-20 23:44:10.908 Main::Registering HttpStatus Extension
2009-05-20 23:44:10.910 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:44:10.911 Enabled verbose msgs:  important general
2009-05-20 23:44:10.915 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:44:13.889 Reschedule requested for id -1.
2009-05-20 23:44:13.929 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2009-05-20 23:44:13.938 Seem to be woken up by USER
2009-05-20 23:44:30.524 MainServer::HandleAnnounce Monitor
2009-05-20 23:44:30.539 adding: myth as a client (events: 0)
2009-05-20 23:44:30.541 MainServer::HandleAnnounce Monitor
2009-05-20 23:44:30.543 adding: myth as a client (events: 1)
2009-05-20 23:44:30.544 Reschedule requested for id -1.
2009-05-20 23:44:30.565 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-05-20 23:44:30.892 Expiring 45 MBytes for 1002 @ Wed May 20 23:00:00 2009 => The Hour
2009-05-20 23:44:30.894 Expiring 11 MBytes for 1003 @ Wed May 20 23:00:00 2009 => La Zone
2009-05-20 23:44:30.902 Expiring 17 MBytes for 1014 @ Wed May 20 23:35:00 2009 => Late Show With David Letterman
2009-05-20 23:44:30.904 Expiring 51 MBytes for 1020 @ Wed May 20 23:00:00 2009 => VidÈo patrouille
2009-05-20 23:44:37.921 New DB connection, total: 4
2009-05-20 23:44:37.927 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:45:15.074 MainServer::HandleAnnounce Monitor
2009-05-20 23:45:15.078 adding: myth as a client (events: 0)
2009-05-20 23:45:15.080 MainServer::HandleAnnounce Monitor
2009-05-20 23:45:15.082 adding: myth as a client (events: 1)
2009-05-20 23:45:15.089 MainServer::HandleAnnounce Playback
2009-05-20 23:45:15.092 adding: myth as a client (events: 0)
2009-05-20 23:45:15.096 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:45:15.105 TVRec(1): HW Tuner: 1->1
2009-05-20 23:45:16.259 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:45:16.261 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:45:16.287 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:45:30.910 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:46:46.951 TVRec(1): HW Tuner: 1->1
2009-05-20 23:46:47.009 Finished recording Vid&#8730;©o patrouille: channel 1020
2009-05-20 23:46:48.058 Finished recording Vid&#8730;©o patrouille: channel 1020
2009-05-20 23:46:48.088 TVRec(1): RingBufferChanged()
2009-05-20 23:46:48.140 Finished recording Vid&#8730;©o patrouille: channel 1020
2009-05-20 23:46:48.150 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:46:48.264 Using runtime prefix = /usr
2009-05-20 23:46:48.268 Empty LocalHostName.
2009-05-20 23:46:48.269 Using localhost value of myth
2009-05-20 23:46:48.286 New DB connection, total: 1
2009-05-20 23:46:48.295 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:46:48.352 Closing DB connection named 'DBManager0'
2009-05-20 23:46:48.355 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:46:48.358 New DB connection, total: 2
2009-05-20 23:46:48.371 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:46:48.383 Current Schema Version: 1214
2009-05-20 23:46:48.527 Preview: Grabbed preview '/var/lib/mythtv/recordings/1020_20090520234515.nuv' 480x480@64s
2009-05-20 23:47:58.252 TVRec(1): HW Tuner: 1->1
2009-05-20 23:47:58.299 Finished recording Guide de l'auto: channel 1022
2009-05-20 23:47:59.350 Finished recording Guide de l'auto: channel 1022
2009-05-20 23:47:59.536 Using runtime prefix = /usr
2009-05-20 23:47:59.547 Empty LocalHostName.
2009-05-20 23:47:59.548 Using localhost value of myth
2009-05-20 23:47:59.563 New DB connection, total: 1
2009-05-20 23:47:59.572 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:47:59.574 Closing DB connection named 'DBManager0'
2009-05-20 23:47:59.577 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:47:59.581 New DB connection, total: 2
2009-05-20 23:47:59.586 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:47:59.596 Current Schema Version: 1214
2009-05-20 23:47:59.679 TVRec(1): RingBufferChanged()
2009-05-20 23:47:59.733 Preview: Grabbed preview '/var/lib/mythtv/recordings/1022_20090520234647.nuv' 480x480@64s
2009-05-20 23:47:59.741 Finished recording Guide de l'auto: channel 1022
2009-05-20 23:47:59.755 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:48:30.951 Expiring 105 MBytes for 1020 @ Wed May 20 23:00:00 2009 => VidÈo patrouille
2009-05-20 23:49:46.240 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 23:49:46.472 Finished recording Seinfeld "The Kiss Hello": channel 1031
2009-05-20 23:49:56.844 MainServer::HandleAnnounce Playback
2009-05-20 23:49:56.847 adding: myth as a client (events: 0)
2009-05-20 23:49:56.850 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:49:56.857 TVRec(1): HW Tuner: 1->1
2009-05-20 23:49:57.955 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:49:57.957 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:49:57.977 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:50:48.234 Using runtime prefix = /usr
2009-05-20 23:50:48.243 Empty LocalHostName.
2009-05-20 23:50:48.245 Using localhost value of myth
2009-05-20 23:50:48.261 New DB connection, total: 1
2009-05-20 23:50:48.271 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:50:48.274 Closing DB connection named 'DBManager0'
2009-05-20 23:50:48.276 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:50:48.279 New DB connection, total: 2
2009-05-20 23:50:48.281 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:50:48.286 Current Schema Version: 1214
Starting up as the master server.
2009-05-20 23:50:48.310 New DB connection, total: 3
2009-05-20 23:50:48.312 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:50:48.391 New DB scheduler connection
2009-05-20 23:50:48.393 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:50:48.420 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-20 23:50:48.422 Main::Registering HttpStatus Extension
2009-05-20 23:50:48.425 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:50:48.434 Enabled verbose msgs:  important general
2009-05-20 23:50:48.443 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-20 23:50:51.407 Reschedule requested for id -1.
2009-05-20 23:50:51.436 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-05-20 23:50:51.443 Seem to be woken up by USER
2009-05-20 23:50:55.190 MainServer::HandleAnnounce Monitor
2009-05-20 23:50:55.195 adding: myth as a client (events: 0)
2009-05-20 23:50:55.197 MainServer::HandleAnnounce Monitor
2009-05-20 23:50:55.199 adding: myth as a client (events: 1)
2009-05-20 23:50:55.206 MainServer::HandleAnnounce Playback
2009-05-20 23:50:55.208 adding: myth as a client (events: 0)
2009-05-20 23:50:55.212 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:50:55.216 TVRec(1): HW Tuner: 1->1
2009-05-20 23:50:56.348 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:50:56.350 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:50:56.369 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:52:08.416 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-20 23:52:08.422 Expiring 98 MBytes for 1022 @ Wed May 20 23:00:00 2009 => Guide de l'auto
2009-05-20 23:57:33.099 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 23:57:33.257 Finished recording Seinfeld "The Kiss Hello": channel 1031
2009-05-20 23:57:39.118 MainServer::HandleAnnounce Playback
2009-05-20 23:57:39.122 adding: myth as a client (events: 0)
2009-05-20 23:57:39.125 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 23:57:39.132 TVRec(1): HW Tuner: 1->1
2009-05-20 23:57:40.255 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-20 23:57:40.257 NVR(/dev/video0) Error: Unknown audio codec
2009-05-20 23:57:40.278 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 20:22:05.115 Using runtime prefix = /usr
2009-05-21 20:22:05.200 Empty LocalHostName.
2009-05-21 20:22:05.211 Using localhost value of myth
2009-05-21 20:22:05.293 New DB connection, total: 1
2009-05-21 20:22:05.410 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:05.444 Closing DB connection named 'DBManager0'
2009-05-21 20:22:05.557 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:05.574 New DB connection, total: 2
2009-05-21 20:22:05.661 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:05.814 Current Schema Version: 1214
Starting up as the master server.
2009-05-21 20:22:06.193 New DB connection, total: 3
2009-05-21 20:22:06.205 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:06.373 New DB scheduler connection
2009-05-21 20:22:06.384 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:06.464 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-21 20:22:06.479 Main::Registering HttpStatus Extension
2009-05-21 20:22:06.489 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-21 20:22:06.511 Enabled verbose msgs:  important general
2009-05-21 20:22:06.571 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 20:22:09.437 Reschedule requested for id -1.
2009-05-21 20:22:10.241 Scheduled 0 items in 0.8 = 0.76 match + 0.05 place
2009-05-21 20:22:10.333 Seem to be woken up by USER
2009-05-21 20:22:16.004 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:22:16.070 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2009-05-19T20:22:16') OR (status in (304) AND statustime < '2009-05-17T20:22:16')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:22:16.076 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-21T16:22:16' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:22:16.078 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:22:16.089 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:22:16.449 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-21 20:23:26.438 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 20:39:26.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 20:41:15.996 MainServer::HandleAnnounce Monitor
2009-05-21 20:41:16.001 adding: myth as a client (events: 0)
2009-05-21 20:41:16.004 MainServer::HandleAnnounce Monitor
2009-05-21 20:41:16.006 adding: myth as a client (events: 1)
2009-05-21 20:41:38.532 MainServer::HandleAnnounce Monitor
2009-05-21 20:41:38.546 adding: myth as a client (events: 0)
2009-05-21 20:41:38.549 MainServer::HandleAnnounce Monitor
2009-05-21 20:41:38.551 adding: myth as a client (events: 1)
2009-05-21 20:41:38.556 MainServer::HandleAnnounce Playback
2009-05-21 20:41:38.607 adding: myth as a client (events: 0)
2009-05-21 20:41:38.620 TVRec(1): Changing from None to WatchingLiveTV
2009-05-21 20:41:38.627 TVRec(1): HW Tuner: 1->1
2009-05-21 20:41:40.061 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-21 20:41:40.063 NVR(/dev/video0) Error: Unknown audio codec
2009-05-21 20:41:40.087 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 20:44:50.549 TVRec(1): Changing from WatchingLiveTV to None
2009-05-21 20:44:50.741 Finished recording So You Think You Can Dance: channel 1031
2009-05-21 20:54:26.379 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 21:08:15.779 MainServer::HandleAnnounce Monitor
2009-05-21 21:08:15.784 adding: myth as a client (events: 0)
2009-05-21 21:08:15.786 MainServer::HandleAnnounce Monitor
2009-05-21 21:08:15.788 adding: myth as a client (events: 1)
2009-05-21 21:08:15.793 MainServer::HandleAnnounce Playback
2009-05-21 21:08:15.797 adding: myth as a client (events: 0)
2009-05-21 21:08:15.800 TVRec(1): Changing from None to WatchingLiveTV
2009-05-21 21:08:15.806 TVRec(1): HW Tuner: 1->1
2009-05-21 21:08:16.936 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-21 21:08:16.938 NVR(/dev/video0) Error: Unknown audio codec
2009-05-21 21:08:16.960 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 21:08:26.951 TVRec(1): HW Tuner: 1->1
2009-05-21 21:08:27.047 Finished recording So You Think You Can Dance: channel 1031
2009-05-21 21:08:28.141 Finished recording So You Think You Can Dance: channel 1031
2009-05-21 21:08:28.272 TVRec(1): RingBufferChanged()
2009-05-21 21:08:28.328 Using runtime prefix = /usr
2009-05-21 21:08:28.338 Empty LocalHostName.
2009-05-21 21:08:28.340 Using localhost value of myth
2009-05-21 21:08:28.343 Finished recording So You Think You Can Dance: channel 1031
2009-05-21 21:08:28.356 New DB connection, total: 1
2009-05-21 21:08:28.421 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 21:08:28.431 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:28.437 Closing DB connection named 'DBManager0'
2009-05-21 21:08:28.441 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:28.445 New DB connection, total: 2
2009-05-21 21:08:28.448 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:28.457 Current Schema Version: 1214
2009-05-21 21:08:28.566 Preview: Grabbed preview '/var/lib/mythtv/recordings/1031_20090521210815.nuv' 480x480@64s
2009-05-21 21:08:33.170 TVRec(1): HW Tuner: 1->1
2009-05-21 21:08:33.225 Finished recording NHL Hockey "Carolina Hurricanes at Pittsburgh Penguins": channel 1032
2009-05-21 21:08:34.290 Finished recording NHL Hockey "Carolina Hurricanes at Pittsburgh Penguins": channel 1032
2009-05-21 21:08:34.474 Using runtime prefix = /usr
2009-05-21 21:08:34.486 Empty LocalHostName.
2009-05-21 21:08:34.488 Using localhost value of myth
2009-05-21 21:08:34.503 New DB connection, total: 1
2009-05-21 21:08:34.511 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:34.514 Closing DB connection named 'DBManager0'
2009-05-21 21:08:34.517 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:34.521 New DB connection, total: 2
2009-05-21 21:08:34.529 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:34.538 Current Schema Version: 1214
2009-05-21 21:08:34.595 TVRec(1): RingBufferChanged()
2009-05-21 21:08:34.656 Finished recording NHL Hockey "Carolina Hurricanes at Pittsburgh Penguins": channel 1032
2009-05-21 21:08:34.674 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 21:08:34.687 Preview: Grabbed preview '/var/lib/mythtv/recordings/1032_20090521210827.nuv' 480x480@64s
2009-05-21 21:08:44.807 TVRec(1): HW Tuner: 1->1
2009-05-21 21:08:44.863 Finished recording Hockey de la Ligue nationale "…liminatoires: Les Hurricanes de Caroline rencontrent les Penguins ‡ Pittsburgh, 2e match": channel 1033
2009-05-21 21:08:45.937 Finished recording Hockey de la Ligue nationale "…liminatoires: Les Hurricanes de Caroline rencontrent les Penguins ‡ Pittsburgh, 2e match": channel 1033
2009-05-21 21:08:46.039 TVRec(1): RingBufferChanged()
2009-05-21 21:08:46.101 Finished recording Hockey de la Ligue nationale "…liminatoires: Les Hurricanes de Caroline rencontrent les Penguins ‡ Pittsburgh, 2e match": channel 1033
2009-05-21 21:08:46.111 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 21:08:46.124 Using runtime prefix = /usr
2009-05-21 21:08:46.135 Empty LocalHostName.
2009-05-21 21:08:46.186 Using localhost value of myth
2009-05-21 21:08:46.204 New DB connection, total: 1
2009-05-21 21:08:46.219 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:46.222 Closing DB connection named 'DBManager0'
2009-05-21 21:08:46.225 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:46.229 New DB connection, total: 2
2009-05-21 21:08:46.237 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:46.246 Current Schema Version: 1214
2009-05-21 21:08:46.360 Preview: Grabbed preview '/var/lib/mythtv/recordings/1033_20090521210833.nuv' 480x480@64s
2009-05-21 21:09:02.494 TVRec(1): HW Tuner: 1->1
2009-05-21 21:09:02.570 Finished recording Les Simpson: channel 1044
2009-05-21 21:09:03.663 Finished recording Les Simpson: channel 1044
2009-05-21 21:09:03.814 TVRec(1): RingBufferChanged()
2009-05-21 21:09:03.849 Using runtime prefix = /usr
2009-05-21 21:09:03.875 Finished recording Les Simpson: channel 1044
2009-05-21 21:09:03.876 Empty LocalHostName.
2009-05-21 21:09:03.937 Using localhost value of myth
2009-05-21 21:09:03.953 New DB connection, total: 1
2009-05-21 21:09:03.955 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-21 21:09:03.963 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:09:03.969 Closing DB connection named 'DBManager0'
2009-05-21 21:09:03.972 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:09:03.981 New DB connection, total: 2
2009-05-21 21:09:03.983 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:09:03.988 Current Schema Version: 1214
2009-05-21 21:09:04.148 Preview: Grabbed preview '/var/lib/mythtv/recordings/1044_20090521210844.nuv' 480x480@64s
2009-05-21 21:09:16.084 TVRec(1): Changing from WatchingLiveTV to None
2009-05-21 21:09:16.330 Finished recording Futurama "Luck of the Fryish": channel 1049
2009-05-21 21:09:26.435 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 21:10:26.454 Expiring 10 MBytes for 1031 @ Thu May 21 20:00:00 2009 => So You Think You Can Dance
2009-05-21 21:10:26.463 Expiring 7 MBytes for 1032 @ Thu May 21 19:30:00 2009 => NHL Hockey "Carolina Hurricanes at Pittsburgh Penguins"
2009-05-21 21:10:26.466 Expiring 9 MBytes for 1033 @ Thu May 21 19:30:00 2009 => Hockey de la Ligue nationale "…liminatoires: Les Hurricanes de Caroline rencontrent les Penguins ‡ Pittsburgh, 2e match"
2009-05-21 21:10:26.469 Expiring 18 MBytes for 1044 @ Thu May 21 21:00:00 2009 => Les Simpson
2009-05-21 21:10:26.483 Expiring 10 MBytes for 1049 @ Thu May 21 21:00:00 2009 => Futurama "Luck of the Fryish"
2009-05-21 21:10:33.494 New DB connection, total: 4
2009-05-21 21:10:33.501 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:24:26.527 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 21:39:26.584 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-21 21:54:26.631 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-23 22:46:41.756 Using runtime prefix = /usr
2009-05-23 22:46:41.791 Empty LocalHostName.
2009-05-23 22:46:41.810 Using localhost value of myth
2009-05-23 22:46:41.883 New DB connection, total: 1
2009-05-23 22:46:42.019 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:42.051 Closing DB connection named 'DBManager0'
2009-05-23 22:46:42.094 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:42.171 New DB connection, total: 2
2009-05-23 22:46:42.185 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:42.239 Current Schema Version: 1214
Starting up as the master server.
2009-05-23 22:46:42.334 New DB connection, total: 3
2009-05-23 22:46:42.336 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:42.405 New DB scheduler connection
2009-05-23 22:46:42.418 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:42.447 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-23 22:46:42.464 Main::Registering HttpStatus Extension
2009-05-23 22:46:42.474 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-23 22:46:42.505 Enabled verbose msgs:  important general
2009-05-23 22:46:42.554 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-23 22:46:45.424 Reschedule requested for id -1.
2009-05-23 22:46:46.083 Scheduled 0 items in 0.7 = 0.60 match + 0.06 place
2009-05-23 22:46:46.235 Seem to be woken up by USER
2009-05-23 22:46:52.251 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:46:52.285 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2009-05-21T22:46:52') OR (status in (304) AND statustime < '2009-05-19T22:46:52')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:46:52.288 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-23T18:46:52' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:46:52.291 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:46:52.294 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:46:52.424 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-23 22:48:01.656 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-23 22:48:01.667 Expiring 109 MBytes for 1031 @ Wed May 20 23:30:00 2009 => Seinfeld "The Kiss Hello"
2009-05-23 22:48:01.668 Expiring 0 MBytes for 1031 @ Wed May 20 23:30:00 2009 => Seinfeld "The Kiss Hello"
2009-05-23 22:48:01.677 Expiring 393 MBytes for 1031 @ Wed May 20 23:30:00 2009 => Seinfeld "The Kiss Hello"
2009-05-23 22:48:01.681 Expiring 0 MBytes for 1031 @ Wed May 20 23:30:00 2009 => Seinfeld "The Kiss Hello"
2009-05-23 22:48:01.683 Expiring 212 MBytes for 1031 @ Thu May 21 20:00:00 2009 => So You Think You Can Dance
2009-05-23 22:48:08.795 New DB connection, total: 4
2009-05-23 22:48:08.800 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:03:01.787 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-23 23:03:54.598 MainServer::HandleAnnounce Monitor
2009-05-23 23:03:54.603 adding: myth as a client (events: 0)
2009-05-23 23:03:54.606 MainServer::HandleAnnounce Monitor
2009-05-23 23:03:54.608 adding: myth as a client (events: 1)
2009-05-23 23:03:54.617 MainServer::HandleAnnounce Playback
2009-05-23 23:03:54.640 adding: myth as a client (events: 0)
2009-05-23 23:03:54.644 TVRec(1): Changing from None to WatchingLiveTV
2009-05-23 23:03:54.653 TVRec(1): HW Tuner: 1->1
2009-05-23 23:03:55.983 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-23 23:03:55.985 NVR(/dev/video0) Error: Unknown audio codec
2009-05-23 23:03:56.006 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:05:38.727 TVRec(1): HW Tuner: 1->1
2009-05-23 23:05:38.763 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:05:39.848 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:05:40.030 Using runtime prefix = /usr
2009-05-23 23:05:40.037 Empty LocalHostName.
2009-05-23 23:05:40.039 Using localhost value of myth
2009-05-23 23:05:40.044 TVRec(1): RingBufferChanged()
2009-05-23 23:05:40.053 New DB connection, total: 1
2009-05-23 23:05:40.131 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:05:40.136 Closing DB connection named 'DBManager0'
2009-05-23 23:05:40.136 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:05:40.138 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:05:40.195 New DB connection, total: 2
2009-05-23 23:05:40.198 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:05:40.199 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:05:40.204 Current Schema Version: 1214
2009-05-23 23:05:40.321 Preview: Grabbed preview '/var/lib/mythtv/recordings/1049_20090523230354.nuv' 480x480@64s
2009-05-23 23:06:35.481 TVRec(1): HW Tuner: 1->1
2009-05-23 23:06:35.543 Finished recording Bill Engvall: Here's Your Sign Live: channel 1051
2009-05-23 23:06:36.636 Finished recording Bill Engvall: Here's Your Sign Live: channel 1051
2009-05-23 23:06:36.659 TVRec(1): RingBufferChanged()
2009-05-23 23:06:36.720 Finished recording Bill Engvall: Here's Your Sign Live: channel 1051
2009-05-23 23:06:36.755 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:06:36.848 Using runtime prefix = /usr
2009-05-23 23:06:36.851 Empty LocalHostName.
2009-05-23 23:06:36.864 Using localhost value of myth
2009-05-23 23:06:36.881 New DB connection, total: 1
2009-05-23 23:06:36.891 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:06:36.894 Closing DB connection named 'DBManager0'
2009-05-23 23:06:36.896 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:06:36.900 New DB connection, total: 2
2009-05-23 23:06:36.902 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:06:36.907 Current Schema Version: 1214
2009-05-23 23:06:37.034 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090523230538.nuv' 480x480@64s
2009-05-23 23:07:12.854 TVRec(1): HW Tuner: 1->1
2009-05-23 23:07:12.912 Finished recording Alien 3: channel 1056
2009-05-23 23:07:13.973 Finished recording Alien 3: channel 1056
2009-05-23 23:07:14.082 TVRec(1): RingBufferChanged()
2009-05-23 23:07:14.152 Finished recording Alien 3: channel 1056
2009-05-23 23:07:14.156 Using runtime prefix = /usr
2009-05-23 23:07:14.162 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:07:14.164 Empty LocalHostName.
2009-05-23 23:07:14.178 Using localhost value of myth
2009-05-23 23:07:14.251 New DB connection, total: 1
2009-05-23 23:07:14.259 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:07:14.263 Closing DB connection named 'DBManager0'
2009-05-23 23:07:14.270 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:07:14.273 New DB connection, total: 2
2009-05-23 23:07:14.309 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:07:14.318 Current Schema Version: 1214
2009-05-23 23:07:14.429 Preview: Grabbed preview '/var/lib/mythtv/recordings/1056_20090523230635.nuv' 480x480@64s
2009-05-23 23:08:01.823 Expiring 51 MBytes for 1051 @ Sat May 23 22:00:00 2009 => Bill Engvall: Here's Your Sign Live
2009-05-23 23:08:01.826 Expiring 32 MBytes for 1056 @ Sat May 23 22:00:00 2009 => Alien 3
2009-05-23 23:14:46.870 TVRec(1): HW Tuner: 1->1
2009-05-23 23:14:46.951 Finished recording Mo' Better Blues: channel 1057
2009-05-23 23:14:47.992 Finished recording Mo' Better Blues: channel 1057
2009-05-23 23:14:48.112 TVRec(1): RingBufferChanged()
2009-05-23 23:14:48.180 Using runtime prefix = /usr
2009-05-23 23:14:48.191 Finished recording Mo' Better Blues: channel 1057
2009-05-23 23:14:48.219 Empty LocalHostName.
2009-05-23 23:14:48.230 Using localhost value of myth
2009-05-23 23:14:48.238 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:14:48.244 New DB connection, total: 1
2009-05-23 23:14:48.273 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:48.276 Closing DB connection named 'DBManager0'
2009-05-23 23:14:48.278 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:48.282 New DB connection, total: 2
2009-05-23 23:14:48.287 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:48.293 Current Schema Version: 1214
2009-05-23 23:14:48.417 Preview: Grabbed preview '/var/lib/mythtv/recordings/1057_20090523230712.nuv' 480x480@64s
2009-05-23 23:14:56.510 TVRec(1): HW Tuner: 1->1
2009-05-23 23:14:56.564 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:14:57.648 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:14:57.724 TVRec(1): RingBufferChanged()
2009-05-23 23:14:57.786 Finished recording Moral Orel "Geniuses": channel 1049
2009-05-23 23:14:57.823 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:14:57.835 Using runtime prefix = /usr
2009-05-23 23:14:57.846 Empty LocalHostName.
2009-05-23 23:14:57.848 Using localhost value of myth
2009-05-23 23:14:57.864 New DB connection, total: 1
2009-05-23 23:14:57.874 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:57.877 Closing DB connection named 'DBManager0'
2009-05-23 23:14:57.880 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:57.883 New DB connection, total: 2
2009-05-23 23:14:57.891 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:14:57.900 Current Schema Version: 1214
2009-05-23 23:14:58.011 Preview: Grabbed preview '/var/lib/mythtv/recordings/1049_20090523231446.nuv' 480x480@64s
2009-05-23 23:16:01.856 Expiring 9 MBytes for 1049 @ Sat May 23 23:00:00 2009 => Moral Orel "Geniuses"
2009-05-23 23:18:01.878 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:30:01.685 Finished recording Les Simpson: channel 1044
2009-05-23 23:30:01.870 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:30:01.949 Using runtime prefix = /usr
2009-05-23 23:30:01.955 Empty LocalHostName.
2009-05-23 23:30:01.956 Using localhost value of myth
2009-05-23 23:30:01.975 New DB connection, total: 1
2009-05-23 23:30:02.012 TVRec(1): RingBufferChanged()
2009-05-23 23:30:02.044 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:30:02.222 Closing DB connection named 'DBManager0'
2009-05-23 23:30:02.230 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:30:02.244 New DB connection, total: 2
2009-05-23 23:30:02.260 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:30:02.213 Finished recording Les Simpson: channel 1044
2009-05-23 23:30:02.275 Current Schema Version: 1214
2009-05-23 23:30:02.619 Preview: Grabbed preview '/var/lib/mythtv/recordings/1044_20090523231456.nuv' 480x480@64s
2009-05-23 23:33:01.952 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-23 23:48:02.016 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:00:01.849 Finished recording Les DÈcalÈs du cosmos: channel 1044
2009-05-24 00:00:01.959 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:00:02.151 TVRec(1): RingBufferChanged()
2009-05-24 00:00:02.285 Finished recording Les DÈcalÈs du cosmos: channel 1044
2009-05-24 00:00:03.860 Using runtime prefix = /usr
2009-05-24 00:00:03.885 Empty LocalHostName.
2009-05-24 00:00:03.897 Using localhost value of myth
2009-05-24 00:00:03.948 New DB connection, total: 1
2009-05-24 00:00:04.020 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:04.027 Closing DB connection named 'DBManager0'
2009-05-24 00:00:04.032 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:04.081 New DB connection, total: 2
2009-05-24 00:00:04.089 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:04.096 Current Schema Version: 1214
2009-05-24 00:00:04.421 Preview: Grabbed preview '/var/lib/mythtv/recordings/1044_20090523233000.nuv' 480x480@64s
2009-05-24 00:00:06.846 TVRec(1): HW Tuner: 1->1
2009-05-24 00:00:06.896 Finished recording Henri pis sa gang: channel 1044
2009-05-24 00:00:07.988 Finished recording Henri pis sa gang: channel 1044
2009-05-24 00:00:08.063 TVRec(1): RingBufferChanged()
2009-05-24 00:00:08.133 Finished recording Henri pis sa gang: channel 1044
2009-05-24 00:00:08.156 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:00:08.231 Using runtime prefix = /usr
2009-05-24 00:00:08.235 Empty LocalHostName.
2009-05-24 00:00:08.237 Using localhost value of myth
2009-05-24 00:00:08.251 New DB connection, total: 1
2009-05-24 00:00:08.274 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:08.303 Closing DB connection named 'DBManager0'
2009-05-24 00:00:08.306 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:08.331 New DB connection, total: 2
2009-05-24 00:00:08.386 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:08.390 Current Schema Version: 1214
2009-05-24 00:00:08.544 Preview: Grabbed preview '/var/lib/mythtv/recordings/1044_20090524000000.nuv' 480x480@64s
2009-05-24 00:00:18.169 TVRec(1): HW Tuner: 1->1
2009-05-24 00:00:18.221 Finished recording Rick & Steve: The Happiest Gay Couple in All the World "Death of a Lesbian Bed": channel 1049
2009-05-24 00:00:19.285 Finished recording Rick & Steve: The Happiest Gay Couple in All the World "Death of a Lesbian Bed": channel 1049
2009-05-24 00:00:19.401 TVRec(1): RingBufferChanged()
2009-05-24 00:00:19.476 Using runtime prefix = /usr
2009-05-24 00:00:19.478 Finished recording Rick & Steve: The Happiest Gay Couple in All the World "Death of a Lesbian Bed": channel 1049
2009-05-24 00:00:19.482 Empty LocalHostName.
2009-05-24 00:00:19.494 Using localhost value of myth
2009-05-24 00:00:19.499 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:00:19.515 New DB connection, total: 1
2009-05-24 00:00:19.582 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:19.585 Closing DB connection named 'DBManager0'
2009-05-24 00:00:19.588 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:19.596 New DB connection, total: 2
2009-05-24 00:00:19.603 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:00:19.612 Current Schema Version: 1214
2009-05-24 00:00:19.735 Preview: Grabbed preview '/var/lib/mythtv/recordings/1049_20090524000006.nuv' 480x480@64s
2009-05-24 00:02:02.099 Expiring 7 MBytes for 1044 @ Sun May 24 00:00:00 2009 => Henri pis sa gang
2009-05-24 00:02:02.117 Expiring 15 MBytes for 1049 @ Sun May 24 00:00:00 2009 => Rick & Steve: The Happiest Gay Couple in All the World "Death of a Lesbian Bed"
2009-05-24 00:03:02.131 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:18:02.216 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:30:01.333 Finished recording South Park "Timmy 2000": channel 1051
2009-05-24 00:30:01.484 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:30:01.571 Using runtime prefix = /usr
2009-05-24 00:30:01.598 Empty LocalHostName.
2009-05-24 00:30:01.679 Using localhost value of myth
2009-05-24 00:30:01.707 New DB connection, total: 1
2009-05-24 00:30:01.717 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:30:01.723 Closing DB connection named 'DBManager0'
2009-05-24 00:30:01.725 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:30:01.729 New DB connection, total: 2
2009-05-24 00:30:01.731 Connected to database 'mythconverg' at host: localhost
2009-05-24 00:30:01.736 Current Schema Version: 1214
2009-05-24 00:30:01.794 TVRec(1): RingBufferChanged()
2009-05-24 00:30:01.929 Finished recording South Park "Timmy 2000": channel 1051
2009-05-24 00:30:02.020 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524000018.nuv' 480x480@64s
2009-05-24 00:33:02.296 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 00:48:02.374 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:00:01.377 Finished recording The Simpsons "Poppa's Got a Brand New Badge": channel 1051
2009-05-24 01:00:01.577 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:00:01.725 TVRec(1): RingBufferChanged()
2009-05-24 01:00:01.876 Finished recording The Simpsons "Poppa's Got a Brand New Badge": channel 1051
2009-05-24 01:00:02.584 Using runtime prefix = /usr
2009-05-24 01:00:02.608 Empty LocalHostName.
2009-05-24 01:00:02.611 Using localhost value of myth
2009-05-24 01:00:02.628 New DB connection, total: 1
2009-05-24 01:00:02.669 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:00:02.673 Closing DB connection named 'DBManager0'
2009-05-24 01:00:02.680 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:00:02.683 New DB connection, total: 2
2009-05-24 01:00:02.696 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:00:02.705 Current Schema Version: 1214
2009-05-24 01:00:02.893 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524003000.nuv' 480x480@64s
2009-05-24 01:03:02.448 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:18:02.533 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:30:01.500 Finished recording King of the Hill "Gone With the Windstorm": channel 1051
2009-05-24 01:30:01.759 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:30:01.864 TVRec(1): RingBufferChanged()
2009-05-24 01:30:02.104 Finished recording King of the Hill "Gone With the Windstorm": channel 1051
2009-05-24 01:30:02.794 Using runtime prefix = /usr
2009-05-24 01:30:02.815 Empty LocalHostName.
2009-05-24 01:30:02.822 Using localhost value of myth
2009-05-24 01:30:02.881 New DB connection, total: 1
2009-05-24 01:30:02.969 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:30:02.973 Closing DB connection named 'DBManager0'
2009-05-24 01:30:02.979 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:30:02.985 New DB connection, total: 2
2009-05-24 01:30:02.987 Connected to database 'mythconverg' at host: localhost
2009-05-24 01:30:02.991 Current Schema Version: 1214
2009-05-24 01:30:03.188 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524010000.nuv' 480x480@64s
2009-05-24 01:33:02.609 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 01:48:02.697 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 02:03:02.771 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 02:18:02.864 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 02:33:02.944 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 02:48:03.030 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:00:02.103 Finished recording Bill Engvall: Here's Your Sign Live: channel 1051
2009-05-24 03:00:02.367 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:00:02.574 TVRec(1): RingBufferChanged()
2009-05-24 03:00:02.757 Finished recording Bill Engvall: Here's Your Sign Live: channel 1051
2009-05-24 03:00:04.991 Using runtime prefix = /usr
2009-05-24 03:00:05.062 Empty LocalHostName.
2009-05-24 03:00:05.064 Using localhost value of myth
2009-05-24 03:00:05.318 New DB connection, total: 1
2009-05-24 03:00:05.389 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:00:05.394 Closing DB connection named 'DBManager0'
2009-05-24 03:00:05.399 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:00:05.423 New DB connection, total: 2
2009-05-24 03:00:05.426 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:00:05.432 Current Schema Version: 1214
2009-05-24 03:00:05.789 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524013000.nuv' 480x480@64s
2009-05-24 03:03:03.107 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:18:03.173 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:30:02.232 Finished recording Blue Collar TV "Bad Jobs": channel 1051
2009-05-24 03:30:02.394 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:30:02.564 TVRec(1): RingBufferChanged()
2009-05-24 03:30:02.719 Finished recording Blue Collar TV "Bad Jobs": channel 1051
2009-05-24 03:30:03.159 Using runtime prefix = /usr
2009-05-24 03:30:03.165 Empty LocalHostName.
2009-05-24 03:30:03.167 Using localhost value of myth
2009-05-24 03:30:03.249 New DB connection, total: 1
2009-05-24 03:30:03.283 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:30:03.293 Closing DB connection named 'DBManager0'
2009-05-24 03:30:03.300 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:30:03.304 New DB connection, total: 2
2009-05-24 03:30:03.317 Connected to database 'mythconverg' at host: localhost
2009-05-24 03:30:03.327 Current Schema Version: 1214
2009-05-24 03:30:03.595 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524030000.nuv' 480x480@64s
2009-05-24 03:33:03.246 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 03:48:03.315 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 04:00:02.436 Finished recording Corner Gas "All That and a Bag of Chips": channel 1051
2009-05-24 04:00:02.596 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 04:00:02.777 TVRec(1): RingBufferChanged()
2009-05-24 04:00:02.920 Finished recording Corner Gas "All That and a Bag of Chips": channel 1051
2009-05-24 04:00:03.690 Using runtime prefix = /usr
2009-05-24 04:00:03.719 Empty LocalHostName.
2009-05-24 04:00:03.730 Using localhost value of myth
2009-05-24 04:00:03.800 New DB connection, total: 1
2009-05-24 04:00:03.846 Connected to database 'mythconverg' at host: localhost
2009-05-24 04:00:03.855 Closing DB connection named 'DBManager0'
2009-05-24 04:00:03.873 Connected to database 'mythconverg' at host: localhost
2009-05-24 04:00:03.889 New DB connection, total: 2
2009-05-24 04:00:03.893 Connected to database 'mythconverg' at host: localhost
2009-05-24 04:00:03.897 Current Schema Version: 1214
2009-05-24 04:00:04.201 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524033001.nuv' 480x480@64s
2009-05-24 04:03:03.399 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 04:18:03.478 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 04:33:03.558 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 04:48:03.690 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 05:00:02.643 Finished recording Just for Laughs: channel 1051
2009-05-24 05:00:02.926 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 05:00:03.143 TVRec(1): RingBufferChanged()
2009-05-24 05:00:03.381 Finished recording Just for Laughs: channel 1051
2009-05-24 05:00:05.395 Using runtime prefix = /usr
2009-05-24 05:00:05.441 Empty LocalHostName.
2009-05-24 05:00:05.447 Using localhost value of myth
2009-05-24 05:00:05.706 New DB connection, total: 1
2009-05-24 05:00:05.784 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:00:05.787 Closing DB connection named 'DBManager0'
2009-05-24 05:00:05.801 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:00:05.848 New DB connection, total: 2
2009-05-24 05:00:05.850 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:00:05.855 Current Schema Version: 1214
2009-05-24 05:00:06.163 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524040001.nuv' 480x480@64s
2009-05-24 05:03:03.759 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 05:18:03.839 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 05:30:01.700 Finished recording Just for Laughs: channel 1051
2009-05-24 05:30:01.928 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 05:30:02.095 TVRec(1): RingBufferChanged()
2009-05-24 05:30:02.332 Finished recording Just for Laughs: channel 1051
2009-05-24 05:30:02.947 Using runtime prefix = /usr
2009-05-24 05:30:02.967 Empty LocalHostName.
2009-05-24 05:30:02.982 Using localhost value of myth
2009-05-24 05:30:03.045 New DB connection, total: 1
2009-05-24 05:30:03.081 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:30:03.090 Closing DB connection named 'DBManager0'
2009-05-24 05:30:03.100 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:30:03.121 New DB connection, total: 2
2009-05-24 05:30:03.125 Connected to database 'mythconverg' at host: localhost
2009-05-24 05:30:03.129 Current Schema Version: 1214
2009-05-24 05:30:03.393 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524050001.nuv' 480x480@64s
2009-05-24 05:30:35.219 TVRec(1): Changing from WatchingLiveTV to None
2009-05-24 05:30:35.571 Finished recording This Hour Has 22 Minutes: channel 1051
2009-05-24 05:32:03.902 Expiring 43 MBytes for 1051 @ Sun May 24 05:30:00 2009 => This Hour Has 22 Minutes
2009-05-24 05:33:03.909 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 05:48:03.959 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 06:03:04.003 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 06:18:04.046 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 06:33:04.104 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 06:48:04.150 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 07:03:04.197 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 07:18:04.243 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 07:33:04.288 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 07:48:04.327 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 08:03:04.369 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 08:18:04.420 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 08:33:04.467 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 08:48:04.510 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 09:03:04.565 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 09:18:04.610 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 18:04:45.231 Using runtime prefix = /usr
2009-05-24 18:04:45.266 Empty LocalHostName.
2009-05-24 18:04:45.293 Using localhost value of myth
2009-05-24 18:04:45.351 New DB connection, total: 1
2009-05-24 18:04:45.417 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:45.449 Closing DB connection named 'DBManager0'
2009-05-24 18:04:45.519 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:45.537 New DB connection, total: 2
2009-05-24 18:04:45.543 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:45.564 Current Schema Version: 1214
Starting up as the master server.
2009-05-24 18:04:45.784 New DB connection, total: 3
2009-05-24 18:04:45.793 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:45.871 New DB scheduler connection
2009-05-24 18:04:45.874 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:45.897 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 18:04:45.900 Main::Registering HttpStatus Extension
2009-05-24 18:04:45.903 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 18:04:45.919 Enabled verbose msgs:  important general
2009-05-24 18:04:45.962 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 18:04:48.877 Reschedule requested for id -1.
2009-05-24 18:04:49.505 Scheduled 0 items in 0.6 = 0.62 match + 0.01 place
2009-05-24 18:04:49.609 Seem to be woken up by USER
2009-05-24 18:04:55.694 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:04:55.720 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2009-05-22T18:04:55') OR (status in (304) AND statustime < '2009-05-20T18:04:55')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:04:55.724 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-24T14:04:55' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:04:55.727 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:04:55.729 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:04:55.880 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-24 18:06:05.880 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 18:06:36.383 MainServer::HandleAnnounce Monitor
2009-05-24 18:06:36.388 adding: myth as a client (events: 0)
2009-05-24 18:06:36.392 MainServer::HandleAnnounce Monitor
2009-05-24 18:06:36.394 adding: myth as a client (events: 1)
2009-05-24 18:06:36.402 MainServer::HandleAnnounce Playback
2009-05-24 18:06:36.455 adding: myth as a client (events: 0)
2009-05-24 18:06:36.459 TVRec(1): Changing from None to WatchingLiveTV
2009-05-24 18:06:36.470 TVRec(1): HW Tuner: 1->1
2009-05-24 18:06:38.009 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-05-24 18:06:38.011 NVR(/dev/video0) Error: Unknown audio codec
2009-05-24 18:06:38.035 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 18:21:05.959 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 18:30:01.625 Finished recording Just for Laughs: channel 1051
2009-05-24 18:30:01.865 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 18:30:01.993 TVRec(1): RingBufferChanged()
2009-05-24 18:30:02.084 Using runtime prefix = /usr
2009-05-24 18:30:02.088 Empty LocalHostName.
2009-05-24 18:30:02.101 Using localhost value of myth
2009-05-24 18:30:02.110 Finished recording Just for Laughs: channel 1051
2009-05-24 18:30:02.211 New DB connection, total: 1
2009-05-24 18:30:02.253 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:30:02.260 Closing DB connection named 'DBManager0'
2009-05-24 18:30:02.319 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:30:02.323 New DB connection, total: 2
2009-05-24 18:30:02.326 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:30:02.338 Current Schema Version: 1214
2009-05-24 18:30:02.666 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524180636.nuv' 480x480@64s
2009-05-24 18:36:06.041 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 18:51:06.108 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 19:00:02.237 Finished recording This Hour Has 22 Minutes: channel 1051
2009-05-24 19:00:02.425 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 19:00:02.581 TVRec(1): RingBufferChanged()
2009-05-24 19:00:02.764 Finished recording This Hour Has 22 Minutes: channel 1051
2009-05-24 19:00:03.975 Using runtime prefix = /usr
2009-05-24 19:00:04.063 Empty LocalHostName.
2009-05-24 19:00:04.079 Using localhost value of myth
2009-05-24 19:00:04.155 New DB connection, total: 1
2009-05-24 19:00:04.167 Connected to database 'mythconverg' at host: localhost
2009-05-24 19:00:04.171 Closing DB connection named 'DBManager0'
2009-05-24 19:00:04.177 Connected to database 'mythconverg' at host: localhost
2009-05-24 19:00:04.243 New DB connection, total: 2
2009-05-24 19:00:04.246 Connected to database 'mythconverg' at host: localhost
2009-05-24 19:00:04.267 Current Schema Version: 1214
2009-05-24 19:00:04.534 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524183000.nuv' 480x480@64s
2009-05-24 19:06:06.198 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 19:21:06.281 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 19:36:06.364 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 19:51:06.428 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:00:02.420 Finished recording Just for Laughs: channel 1051
2009-05-24 20:00:02.599 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:00:02.715 TVRec(1): RingBufferChanged()
2009-05-24 20:00:02.841 Finished recording Just for Laughs: channel 1051
2009-05-24 20:00:03.735 Using runtime prefix = /usr
2009-05-24 20:00:03.780 Empty LocalHostName.
2009-05-24 20:00:03.816 Using localhost value of myth
2009-05-24 20:00:03.968 New DB connection, total: 1
2009-05-24 20:00:04.030 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:00:04.038 Closing DB connection named 'DBManager0'
2009-05-24 20:00:04.047 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:00:04.074 New DB connection, total: 2
2009-05-24 20:00:04.076 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:00:04.084 Current Schema Version: 1214
2009-05-24 20:00:04.475 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524190000.nuv' 480x480@64s
2009-05-24 20:06:06.509 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:13:49.623 TVRec(1): HW Tuner: 1->1
2009-05-24 20:13:49.697 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:13:50.772 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:13:50.921 TVRec(1): RingBufferChanged()
2009-05-24 20:13:50.988 Using runtime prefix = /usr
2009-05-24 20:13:51.018 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:13:51.075 Empty LocalHostName.
2009-05-24 20:13:51.104 Using localhost value of myth
2009-05-24 20:13:51.142 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:13:51.175 New DB connection, total: 1
2009-05-24 20:13:51.189 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:13:51.192 Closing DB connection named 'DBManager0'
2009-05-24 20:13:51.194 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:13:51.199 New DB connection, total: 2
2009-05-24 20:13:51.202 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:13:51.205 Current Schema Version: 1214
2009-05-24 20:13:51.315 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524200000.nuv' 480x480@64s
2009-05-24 20:14:28.155 TVRec(1): HW Tuner: 1->1
2009-05-24 20:14:28.217 Finished recording Les StupÈfiants "Les Appareils antigravitÈ": channel 1056
2009-05-24 20:14:29.322 Finished recording Les StupÈfiants "Les Appareils antigravitÈ": channel 1056
2009-05-24 20:14:29.485 TVRec(1): RingBufferChanged()
2009-05-24 20:14:29.526 Using runtime prefix = /usr
2009-05-24 20:14:29.588 Finished recording Les StupÈfiants "Les Appareils antigravitÈ": channel 1056
2009-05-24 20:14:29.633 Empty LocalHostName.
2009-05-24 20:14:29.643 Using localhost value of myth
2009-05-24 20:14:29.651 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:14:29.676 New DB connection, total: 1
2009-05-24 20:14:29.694 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:14:29.697 Closing DB connection named 'DBManager0'
2009-05-24 20:14:29.700 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:14:29.703 New DB connection, total: 2
2009-05-24 20:14:29.705 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:14:29.709 Current Schema Version: 1214
2009-05-24 20:14:29.862 Preview: Grabbed preview '/var/lib/mythtv/recordings/1056_20090524201349.nuv' 480x480@64s
2009-05-24 20:16:06.573 Expiring 44 MBytes for 1056 @ Sun May 24 20:00:00 2009 => Les StupÈfiants "Les Appareils antigravitÈ"
2009-05-24 20:19:42.016 TVRec(1): HW Tuner: 1->1
2009-05-24 20:19:42.140 Finished recording Revenge of the Creature: channel 1057
2009-05-24 20:19:43.203 Finished recording Revenge of the Creature: channel 1057
2009-05-24 20:19:43.349 TVRec(1): RingBufferChanged()
2009-05-24 20:19:43.404 Using runtime prefix = /usr
2009-05-24 20:19:43.453 Finished recording Revenge of the Creature: channel 1057
2009-05-24 20:19:43.525 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:19:43.506 Empty LocalHostName.
2009-05-24 20:19:43.546 Using localhost value of myth
2009-05-24 20:19:43.562 New DB connection, total: 1
2009-05-24 20:19:43.571 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:19:43.575 Closing DB connection named 'DBManager0'
2009-05-24 20:19:43.577 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:19:43.585 New DB connection, total: 2
2009-05-24 20:19:43.592 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:19:43.602 Current Schema Version: 1214
2009-05-24 20:19:43.736 Preview: Grabbed preview '/var/lib/mythtv/recordings/1057_20090524201428.nuv' 480x480@64s
2009-05-24 20:21:06.596 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:26:07.765 TVRec(1): HW Tuner: 1->1
2009-05-24 20:26:07.826 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:26:08.922 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:26:09.135 Using runtime prefix = /usr
2009-05-24 20:26:09.142 Empty LocalHostName.
2009-05-24 20:26:09.144 Using localhost value of myth
2009-05-24 20:26:09.160 New DB connection, total: 1
2009-05-24 20:26:09.168 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:09.171 Closing DB connection named 'DBManager0'
2009-05-24 20:26:09.172 TVRec(1): RingBufferChanged()
2009-05-24 20:26:09.174 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:09.236 New DB connection, total: 2
2009-05-24 20:26:09.243 Finished recording Just for Laughs: Gags: channel 1051
2009-05-24 20:26:09.276 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:09.286 Current Schema Version: 1214
2009-05-24 20:26:09.288 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:26:09.445 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090524201942.nuv' 480x480@64s
2009-05-24 20:26:16.380 TVRec(1): HW Tuner: 1->1
2009-05-24 20:26:16.440 Finished recording Hockey "LCH: Coupe Memorial Mastercard, finale": channel 1033
2009-05-24 20:26:17.490 Finished recording Hockey "LCH: Coupe Memorial Mastercard, finale": channel 1033
2009-05-24 20:26:17.622 TVRec(1): RingBufferChanged()
2009-05-24 20:26:17.687 Using runtime prefix = /usr
2009-05-24 20:26:17.693 Finished recording Hockey "LCH: Coupe Memorial Mastercard, finale": channel 1033
2009-05-24 20:26:17.695 Empty LocalHostName.
2009-05-24 20:26:17.753 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:26:17.754 Using localhost value of myth
2009-05-24 20:26:17.787 New DB connection, total: 1
2009-05-24 20:26:17.797 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:17.800 Closing DB connection named 'DBManager0'
2009-05-24 20:26:17.802 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:17.805 New DB connection, total: 2
2009-05-24 20:26:17.816 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:17.825 Current Schema Version: 1214
2009-05-24 20:26:17.949 Preview: Grabbed preview '/var/lib/mythtv/recordings/1033_20090524202607.nuv' 480x480@64s
2009-05-24 20:26:56.730 TVRec(1): HW Tuner: 1->1
2009-05-24 20:26:56.798 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1032
2009-05-24 20:26:57.863 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1032
2009-05-24 20:26:57.953 TVRec(1): RingBufferChanged()
2009-05-24 20:26:58.024 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1032
2009-05-24 20:26:58.035 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:26:58.084 Using runtime prefix = /usr
2009-05-24 20:26:58.120 Empty LocalHostName.
2009-05-24 20:26:58.121 Using localhost value of myth
2009-05-24 20:26:58.144 New DB connection, total: 1
2009-05-24 20:26:58.156 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:58.160 Closing DB connection named 'DBManager0'
2009-05-24 20:26:58.162 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:58.175 New DB connection, total: 2
2009-05-24 20:26:58.181 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:26:58.189 Current Schema Version: 1214
2009-05-24 20:26:58.305 Preview: Grabbed preview '/var/lib/mythtv/recordings/1032_20090524202616.nuv' 480x480@64s
2009-05-24 20:28:06.660 Expiring 9 MBytes for 1033 @ Sun May 24 17:45:00 2009 => Hockey "LCH: Coupe Memorial Mastercard, finale"
2009-05-24 20:28:06.668 Expiring 55 MBytes for 1032 @ Sun May 24 17:00:00 2009 => NASCAR Racing "Sprint Cup: Coca-Cola 600"
2009-05-24 20:28:13.707 New DB connection, total: 4
2009-05-24 20:28:13.714 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:34:50.540 TVRec(1): HW Tuner: 1->1
2009-05-24 20:34:50.635 Finished recording Stargate Atlantis "Missing": channel 1027
2009-05-24 20:34:51.725 Finished recording Stargate Atlantis "Missing": channel 1027
2009-05-24 20:34:51.868 TVRec(1): RingBufferChanged()
2009-05-24 20:34:51.912 Using runtime prefix = /usr
2009-05-24 20:34:51.962 Finished recording Stargate Atlantis "Missing": channel 1027
2009-05-24 20:34:52.007 Empty LocalHostName.
2009-05-24 20:34:52.019 Using localhost value of myth
2009-05-24 20:34:52.029 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:34:52.049 New DB connection, total: 1
2009-05-24 20:34:52.062 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:34:52.065 Closing DB connection named 'DBManager0'
2009-05-24 20:34:52.068 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:34:52.071 New DB connection, total: 2
2009-05-24 20:34:52.080 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:34:52.090 Current Schema Version: 1214
2009-05-24 20:34:52.238 Preview: Grabbed preview '/var/lib/mythtv/recordings/1027_20090524202656.nuv' 480x480@64s
2009-05-24 20:36:06.704 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:38:26.639 TVRec(1): HW Tuner: 1->1
2009-05-24 20:38:26.701 Finished recording Grands reportages "L'Ëre du solaire": channel 1023
2009-05-24 20:38:27.801 Finished recording Grands reportages "L'Ëre du solaire": channel 1023
2009-05-24 20:38:27.994 Using runtime prefix = /usr
2009-05-24 20:38:28.005 Empty LocalHostName.
2009-05-24 20:38:28.007 Using localhost value of myth
2009-05-24 20:38:28.022 New DB connection, total: 1
2009-05-24 20:38:28.031 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:38:28.034 Closing DB connection named 'DBManager0'
2009-05-24 20:38:28.037 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:38:28.040 New DB connection, total: 2
2009-05-24 20:38:28.042 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:38:28.053 Current Schema Version: 1214
2009-05-24 20:38:28.102 TVRec(1): RingBufferChanged()
2009-05-24 20:38:28.163 Finished recording Grands reportages "L'Ëre du solaire": channel 1023
2009-05-24 20:38:28.176 Preview: Grabbed preview '/var/lib/mythtv/recordings/1023_20090524203450.nuv' 480x480@64s
2009-05-24 20:38:28.192 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:39:25.849 TVRec(1): HW Tuner: 1->1
2009-05-24 20:39:25.902 Finished recording CSI: Miami "Lost Son": channel 1028
2009-05-24 20:39:27.004 Finished recording CSI: Miami "Lost Son": channel 1028
2009-05-24 20:39:27.130 TVRec(1): RingBufferChanged()
2009-05-24 20:39:27.194 Finished recording CSI: Miami "Lost Son": channel 1028
2009-05-24 20:39:27.206 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 20:39:27.229 Using runtime prefix = /usr
2009-05-24 20:39:27.284 Empty LocalHostName.
2009-05-24 20:39:27.286 Using localhost value of myth
2009-05-24 20:39:27.301 New DB connection, total: 1
2009-05-24 20:39:27.318 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:39:27.327 Closing DB connection named 'DBManager0'
2009-05-24 20:39:27.330 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:39:27.334 New DB connection, total: 2
2009-05-24 20:39:27.345 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:39:27.353 Current Schema Version: 1214
2009-05-24 20:39:27.484 Preview: Grabbed preview '/var/lib/mythtv/recordings/1028_20090524203826.nuv' 480x480@64s
2009-05-24 20:40:06.750 Expiring 57 MBytes for 1028 @ Sun May 24 20:00:00 2009 => CSI: Miami "Lost Son"
2009-05-24 20:51:06.815 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 21:06:06.911 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 21:21:06.983 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 21:29:43.115 TVRec(1): HW Tuner: 1->1
2009-05-24 21:29:43.363 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1031
2009-05-24 21:29:44.584 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1031
2009-05-24 21:29:44.718 TVRec(1): RingBufferChanged()
2009-05-24 21:29:44.813 Finished recording NASCAR Racing "Sprint Cup: Coca-Cola 600": channel 1031
2009-05-24 21:29:44.887 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 21:29:46.993 Using runtime prefix = /usr
2009-05-24 21:29:47.023 Empty LocalHostName.
2009-05-24 21:29:47.027 Using localhost value of myth
2009-05-24 21:29:47.184 New DB connection, total: 1
2009-05-24 21:29:47.295 Connected to database 'mythconverg' at host: localhost
2009-05-24 21:29:47.299 Closing DB connection named 'DBManager0'
2009-05-24 21:29:47.302 Connected to database 'mythconverg' at host: localhost
2009-05-24 21:29:47.355 New DB connection, total: 2
2009-05-24 21:29:47.357 Connected to database 'mythconverg' at host: localhost
2009-05-24 21:29:47.364 Current Schema Version: 1214
2009-05-24 21:29:47.730 Preview: Grabbed preview '/var/lib/mythtv/recordings/1031_20090524203925.nuv' 480x480@64s
2009-05-24 21:36:07.077 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 21:51:07.156 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 22:06:07.252 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 22:21:07.320 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 22:36:07.409 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 22:51:07.494 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 23:00:02.372 Finished recording Cube: channel 1027
2009-05-24 23:00:02.537 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 23:00:02.830 TVRec(1): RingBufferChanged()
2009-05-24 23:00:03.013 Finished recording Cube: channel 1027
2009-05-24 23:00:04.804 Using runtime prefix = /usr
2009-05-24 23:00:04.837 Empty LocalHostName.
2009-05-24 23:00:04.839 Using localhost value of myth
2009-05-24 23:00:04.935 New DB connection, total: 1
2009-05-24 23:00:04.986 Connected to database 'mythconverg' at host: localhost
2009-05-24 23:00:04.992 Closing DB connection named 'DBManager0'
2009-05-24 23:00:05.003 Connected to database 'mythconverg' at host: localhost
2009-05-24 23:00:05.046 New DB connection, total: 2
2009-05-24 23:00:05.050 Connected to database 'mythconverg' at host: localhost
2009-05-24 23:00:05.054 Current Schema Version: 1214
2009-05-24 23:00:05.327 Preview: Grabbed preview '/var/lib/mythtv/recordings/1027_20090524212943.nuv' 480x480@64s
2009-05-24 23:06:07.573 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 23:06:07.592 Expiring 132 MBytes for 1049 @ Sat May 23 23:00:00 2009 => Moral Orel "Geniuses"
2009-05-24 23:21:07.689 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 23:21:07.717 Expiring 477 MBytes for 1057 @ Sat May 23 23:00:00 2009 => Mo' Better Blues
2009-05-24 23:36:07.790 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-05-24 23:36:07.803 Expiring 1169 MBytes for 1044 @ Sat May 23 23:00:00 2009 => Les Simpson
2009-05-24 23:51:07.911 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min

```

mythfrontend
```
Starting mythfrontend.real..
2009-05-20 19:22:42.404 New DB connection, total: 2
2009-05-20 19:22:42.404 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:42.406 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 19:22:42.406 Enabled verbose msgs:  important general
2009-05-20 19:22:42.502 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-05-20 19:22:44.876 Writing settings file /home/matthieu/.mythtv/mysql.txt
2009-05-20 19:22:44.877 Closing DB connection named 'DBManager1'
2009-05-20 19:22:44.877 Closing DB connection named 'DBManager0'
2009-05-20 19:22:44.878 Connected to database 'mythconverg' at host: localhost
2009-05-20 19:22:44.888 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 19:22:44.889 Primary screen 0.
2009-05-20 19:22:44.890 Using screen 0, 1600x1200 at 0,0
2009-05-20 19:22:44.890 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 19:22:44.890 Switching to square mode (Mythbuntu-8.04)
2009-05-20 19:22:45.006 Using the Qt painter
2009-05-20 19:22:45.006 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-20 19:22:45.034 lirc_init failed for mythtv, see preceding messages
2009-05-20 23:23:38.869 Specified base font 'medium' does not exist for font clock
2009-05-20 23:23:38.869 Specified base font 'medium' does not exist for font small
2009-05-20 23:23:38.869 Specified base font 'medium' does not exist for font medium
2009-05-20 23:23:38.869 Specified base font 'medium' does not exist for font large
2009-05-20 23:23:38.870 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-20 23:23:38.978 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-20 23:23:39.040 Registering Internal as a media playback plugin.
2009-05-20 23:23:39.078 Upgrading to MythArchive schema version 1001
2009-05-20 23:23:39.112 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:23:39.259 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-20 23:23:39.271 Setting Up MythMovies Database Tables
2009-05-20 23:23:39.403 MythMovies Database Setup Complete
2009-05-20 23:23:39.576 Upgrading to MythMusic schema version 1007
2009-05-20 23:23:39.631 Upgrading to MythMusic schema version 1008
2009-05-20 23:23:39.800 Upgrading to MythMusic schema version 1009
2009-05-20 23:23:39.841 Upgrading to MythMusic schema version 1010
2009-05-20 23:23:39.910 Updating music_albumart image types
2009-05-20 23:23:39.913 Upgrading to MythMusic schema version 1011
2009-05-20 23:23:39.914 Upgrading to MythMusic schema version 1012
2009-05-20 23:23:39.960 Upgrading to MythMusic schema version 1013
2009-05-20 23:23:40.097 Failed to run 'cdrecord --scanbus'
2009-05-20 23:23:40.103 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-20 23:23:40.115 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-20 23:23:40.167 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-20 23:23:40.288 Inserting MythWeather initial database information.
2009-05-20 23:23:40.288 Upgrading to MythWeather schema version 1000
2009-05-20 23:23:40.555 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:23:47.082 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:23:47.084 Using protocol version 40
2009-05-20 23:23:47.180 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:23:47.181 Using protocol version 40
2009-05-20 23:23:48.678 New DB connection, total: 3
2009-05-20 23:23:48.692 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:23:48.697 DPMS Deactivated 
2009-05-20 23:23:48.789 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:23:48.789 Opening ALSA audio device 'default'.
2009-05-20 23:23:49.015 mixer unable to find control Master 1
2009-05-20 23:23:49.016 mixer set channel 0 err -1: Operation not permitted
2009-05-20 23:23:49.016 mixer set channel 1 err -1: Operation not permitted
2009-05-20 23:23:49.155 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:23:49.179 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:23:49.651 TV: Changing from None to WatchingLiveTV
2009-05-20 23:23:49.654 New DB connection, total: 4
2009-05-20 23:23:49.654 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:23:49.655 Realtime priority would require SUID as root.
2009-05-20 23:23:49.760 Video timing method: USleep with busy wait
2009-05-20 23:24:04.878 mixer set channel 0 err -1: Operation not permitted
2009-05-20 23:24:04.879 mixer set channel 1 err -1: Operation not permitted
2009-05-20 23:24:05.788 NVP: prebuffering pause
2009-05-20 23:24:14.198 mixer set channel 0 err -1: Operation not permitted
2009-05-20 23:24:14.198 mixer set channel 1 err -1: Operation not permitted
2009-05-20 23:24:14.405 NVP: prebuffering pause
2009-05-20 23:24:16.063 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:24:21.616 mixer set channel 0 err -1: Operation not permitted
2009-05-20 23:24:21.616 mixer set channel 1 err -1: Operation not permitted
2009-05-20 23:24:21.787 NVP: prebuffering pause
2009-05-20 23:24:23.483 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:24:31.946 mixer set channel 0 err -1: Operation not permitted
2009-05-20 23:24:31.946 mixer set channel 1 err -1: Operation not permitted
2009-05-20 23:24:32.178 NVP: prebuffering pause
2009-05-20 23:24:33.795 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:24:37.344 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 23:24:37.395 Searching for frame header.
2009-05-20 23:24:37.612 NVP: prebuffering pause
2009-05-20 23:24:37.748 Broken packet: S 875233550
2009-05-20 23:24:37.922 TV: Changing from WatchingLiveTV to None
2009-05-20 23:24:37.959 DPMS Reactivated.
2009-05-20 23:24:45.053 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-20 23:33:45.962 New DB connection, total: 2
2009-05-20 23:33:45.963 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:33:45.966 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:33:45.966 Enabled verbose msgs:  important general
2009-05-20 23:33:46.499 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:33:46.502 Primary screen 0.
2009-05-20 23:33:46.502 Using screen 0, 1600x1200 at 0,0
2009-05-20 23:33:46.503 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:33:46.503 Switching to square mode (Mythbuntu-8.04)
2009-05-20 23:33:46.529 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-20 23:33:46.530 lirc_init failed for mythtv, see preceding messages
2009-05-20 23:33:46.531 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
2009-05-20 23:33:47.624 Specified base font 'medium' does not exist for font clock
2009-05-20 23:33:47.624 Specified base font 'medium' does not exist for font small
2009-05-20 23:33:47.624 Specified base font 'medium' does not exist for font medium
2009-05-20 23:33:47.624 Specified base font 'medium' does not exist for font large
2009-05-20 23:33:47.625 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-20 23:33:47.726 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-20 23:33:47.762 Registering Internal as a media playback plugin.
2009-05-20 23:33:47.869 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-20 23:33:47.885 Failed to run 'cdrecord --scanbus'
2009-05-20 23:33:47.891 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-20 23:33:47.899 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-20 23:33:47.917 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-20 23:33:47.947 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:33:51.187 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:33:51.188 Using protocol version 40
2009-05-20 23:33:51.212 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:33:51.213 Using protocol version 40
2009-05-20 23:33:52.416 DPMS Deactivated 
2009-05-20 23:33:52.471 New DB connection, total: 3
2009-05-20 23:33:52.472 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:33:52.623 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:33:52.623 Opening ALSA audio device 'default'.
2009-05-20 23:33:52.696 mixer unable to find control Master 1
2009-05-20 23:33:52.831 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:33:52.876 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:33:53.300 TV: Changing from None to WatchingLiveTV
2009-05-20 23:33:53.310 Realtime priority would require SUID as root.
2009-05-20 23:33:53.410 Video timing method: USleep with busy wait
2009-05-20 23:34:01.050 NVP: prebuffering pause
2009-05-20 23:34:02.713 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:34:06.643 NVP: prebuffering pause
2009-05-20 23:34:08.306 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:34:10.902 NVP: prebuffering pause
2009-05-20 23:34:12.557 NVP: Prebuffer wait timed out 10 times.
2009-05-20 23:34:21.256 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-05-20 23:34:21.798 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-05-20 23:34:21.798 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-05-20 23:34:21.866 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-05-20 23:34:21.867 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-05-20 23:34:43.897 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 23:34:44.213 TV: Changing from WatchingLiveTV to None
2009-05-20 23:34:44.297 DPMS Reactivated.
2009-05-20 23:34:46.859 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-20 23:41:09.140 New DB connection, total: 2
2009-05-20 23:41:09.141 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:41:09.144 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:41:09.144 Enabled verbose msgs:  important general
2009-05-20 23:41:09.684 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:41:09.686 Primary screen 0.
2009-05-20 23:41:09.687 Using screen 0, 1600x1200 at 0,0
2009-05-20 23:41:09.688 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:41:09.688 Switching to square mode (Mythbuntu-8.04)
2009-05-20 23:41:09.715 Using the Qt painter
2009-05-20 23:41:09.716 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-20 23:41:09.716 lirc_init failed for mythtv, see preceding messages
2009-05-20 23:41:11.579 Specified base font 'medium' does not exist for font clock
2009-05-20 23:41:11.579 Specified base font 'medium' does not exist for font small
2009-05-20 23:41:11.579 Specified base font 'medium' does not exist for font medium
2009-05-20 23:41:11.579 Specified base font 'medium' does not exist for font large
2009-05-20 23:41:11.581 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-20 23:41:11.808 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-20 23:41:11.852 Registering Internal as a media playback plugin.
2009-05-20 23:41:12.085 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-20 23:41:12.123 Failed to run 'cdrecord --scanbus'
2009-05-20 23:41:12.137 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-20 23:41:12.151 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-20 23:41:12.187 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-20 23:41:12.298 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:41:17.959 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:41:17.960 Using protocol version 40
2009-05-20 23:41:17.977 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:41:17.979 Using protocol version 40
2009-05-20 23:41:19.186 DPMS Deactivated 
2009-05-20 23:41:19.229 New DB connection, total: 3
2009-05-20 23:41:19.230 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:41:19.388 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:41:19.388 Opening ALSA audio device 'default'.
2009-05-20 23:41:19.470 mixer unable to find control Master 1
2009-05-20 23:41:19.564 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:41:19.617 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:41:20.136 TV: Changing from None to WatchingLiveTV
2009-05-20 23:41:20.137 Realtime priority would require SUID as root.
2009-05-20 23:41:20.244 Video timing method: USleep with busy wait
2009-05-20 23:42:01.974 NVP: prebuffering pause
2009-05-20 23:42:02.482 New DB connection, total: 4
2009-05-20 23:42:02.485 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:42:13.405 NVP: prebuffering pause
2009-05-20 23:42:13.442 WriteAudio: buffer underrun
2009-05-20 23:42:29.432 NVP: prebuffering pause
2009-05-20 23:42:29.468 WriteAudio: buffer underrun
2009-05-20 23:43:01.502 NVP: prebuffering pause
2009-05-20 23:43:05.228 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 23:43:05.278 Searching for frame header.
2009-05-20 23:43:05.358 Searching for frame header.
2009-05-20 23:43:05.457 Broken packet: D 83329246
2009-05-20 23:43:05.600 TV: Changing from WatchingLiveTV to None
2009-05-20 23:43:05.628 DPMS Reactivated.
2009-05-20 23:43:10.010 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-20 23:44:52.283 New DB connection, total: 2
2009-05-20 23:44:52.283 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:44:52.286 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 23:44:52.287 Enabled verbose msgs:  important general
2009-05-20 23:44:52.825 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:44:52.828 Primary screen 0.
2009-05-20 23:44:52.828 Using screen 0, 1600x1200 at 0,0
2009-05-20 23:44:52.829 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:44:52.829 Switching to square mode (Mythbuntu-8.04)
2009-05-20 23:44:52.855 Using the Qt painter
2009-05-20 23:44:52.856 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-20 23:44:52.857 lirc_init failed for mythtv, see preceding messages
2009-05-20 23:44:54.176 Specified base font 'medium' does not exist for font clock
2009-05-20 23:44:54.176 Specified base font 'medium' does not exist for font small
2009-05-20 23:44:54.176 Specified base font 'medium' does not exist for font medium
2009-05-20 23:44:54.176 Specified base font 'medium' does not exist for font large
2009-05-20 23:44:54.177 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-20 23:44:54.272 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-20 23:44:54.312 Registering Internal as a media playback plugin.
2009-05-20 23:44:54.421 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-20 23:44:54.437 Failed to run 'cdrecord --scanbus'
2009-05-20 23:44:54.443 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-20 23:44:54.451 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-20 23:44:54.469 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-20 23:44:54.510 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:45:15.072 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:45:15.074 Using protocol version 40
2009-05-20 23:45:15.088 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:45:15.089 Using protocol version 40
2009-05-20 23:45:16.295 DPMS Deactivated 
2009-05-20 23:45:16.343 New DB connection, total: 3
2009-05-20 23:45:16.343 Connected to database 'mythconverg' at host: localhost
2009-05-20 23:45:16.494 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:45:16.494 Opening ALSA audio device 'default'.
2009-05-20 23:45:16.572 mixer unable to find control Master 1
2009-05-20 23:45:16.655 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:45:16.708 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:45:17.241 TV: Changing from None to WatchingLiveTV
2009-05-20 23:45:17.250 Realtime priority would require SUID as root.
2009-05-20 23:45:17.351 Video timing method: USleep with busy wait
2009-05-20 23:46:47.870 NVP: prebuffering pause
2009-05-20 23:46:47.908 WriteAudio: buffer underrun
2009-05-20 23:46:59.532 NVP: prebuffering pause
2009-05-20 23:47:58.668 NVP: prebuffering pause
2009-05-20 23:47:58.705 WriteAudio: buffer underrun
2009-05-20 23:48:11.879 NVP: prebuffering pause
2009-05-20 23:48:31.261 NVP: prebuffering pause
2009-05-20 23:49:07.030 NVP: prebuffering pause
2009-05-20 23:49:46.199 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 23:49:46.565 TV: Changing from WatchingLiveTV to None
2009-05-20 23:49:46.599 DPMS Reactivated.
2009-05-20 23:49:52.136 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:49:56.842 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:49:56.843 Using protocol version 40
2009-05-20 23:49:58.049 DPMS Deactivated 
2009-05-20 23:49:58.161 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:49:58.161 Opening ALSA audio device 'default'.
2009-05-20 23:49:58.223 mixer unable to find control Master 1
2009-05-20 23:49:58.296 Event socket closed. No connection to the backend.
2009-05-20 23:50:18.036 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-05-20 23:50:18.046 MythSocket(267c760:-1): writeStringList: Error, socket went unconnected.
2009-05-20 23:50:18.046 MythSocket(267c760:-1): readStringList: Error, called with unconnected socket.
2009-05-20 23:50:18.047 RemoteEncoder::SendReceiveStringList(): No response.
2009-05-20 23:50:18.047 MythSocket(267c760:-1): writeStringList: Error, called with unconnected socket.
2009-05-20 23:50:18.047 MythSocket(267c760:-1): readStringList: Error, called with unconnected socket.
2009-05-20 23:50:18.047 RemoteEncoder::SendReceiveStringList(): No response.
2009-05-20 23:50:18.047 decodeLongLong() called with offset >= list size.
2009-05-20 23:50:18.073 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:50:18.114 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:50:18.523 Realtime priority would require SUID as root.
2009-05-20 23:50:18.626 Video timing method: USleep with busy wait
2009-05-20 23:50:18.637 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:50:18.638 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-05-20 23:50:54.210 TV Error: LiveTV not successfully started
2009-05-20 23:50:54.254 DPMS Reactivated.
2009-05-20 23:50:55.185 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:50:55.190 Using protocol version 40
2009-05-20 23:50:55.205 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:50:55.206 Using protocol version 40
2009-05-20 23:50:56.409 DPMS Deactivated 
2009-05-20 23:50:56.549 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:50:56.549 Opening ALSA audio device 'default'.
2009-05-20 23:50:56.620 mixer unable to find control Master 1
2009-05-20 23:50:56.697 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:50:56.745 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:50:57.212 TV: Changing from None to WatchingLiveTV
2009-05-20 23:50:57.217 Realtime priority would require SUID as root.
2009-05-20 23:50:57.317 Video timing method: USleep with busy wait
2009-05-20 23:57:33.034 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 23:57:33.334 TV: Changing from WatchingLiveTV to None
2009-05-20 23:57:33.336 DPMS Reactivated.
2009-05-20 23:57:34.681 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-20 23:57:39.117 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 23:57:39.118 Using protocol version 40
2009-05-20 23:57:40.320 DPMS Deactivated 
2009-05-20 23:57:40.463 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-20 23:57:40.463 Opening ALSA audio device 'default'.
2009-05-20 23:57:40.523 mixer unable to find control Master 1
2009-05-20 23:57:40.592 Event socket closed. No connection to the backend.
2009-05-20 23:58:00.340 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-05-20 23:58:00.346 MythSocket(25dfb50:-1): writeStringList: Error, socket went unconnected.
2009-05-20 23:58:00.346 MythSocket(25dfb50:-1): readStringList: Error, called with unconnected socket.
2009-05-20 23:58:00.346 RemoteEncoder::SendReceiveStringList(): No response.
2009-05-20 23:58:00.346 MythSocket(25dfb50:-1): writeStringList: Error, called with unconnected socket.
2009-05-20 23:58:00.346 MythSocket(25dfb50:-1): readStringList: Error, called with unconnected socket.
2009-05-20 23:58:00.346 RemoteEncoder::SendReceiveStringList(): No response.
2009-05-20 23:58:00.346 decodeLongLong() called with offset >= list size.
2009-05-20 23:58:00.371 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 23:58:00.410 OSD Theme Dimensions W: 640 H: 480
2009-05-20 23:58:00.841 Realtime priority would require SUID as root.
2009-05-20 23:58:00.944 Video timing method: USleep with busy wait
2009-05-20 23:58:00.957 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:58:00.957 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-05-20 23:58:00.992 TV Error: LiveTV not successfully started
2009-05-20 23:58:01.041 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-20 23:58:01.041 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-05-20 23:58:01.043 DPMS Reactivated.
2009-05-20 23:58:03.773 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-21 20:22:14.013 New DB connection, total: 2
2009-05-21 20:22:14.014 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:22:14.015 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-21 20:22:14.016 Enabled verbose msgs:  important general
2009-05-21 20:22:15.411 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:22:15.412 Primary screen 0.
2009-05-21 20:22:15.412 Using screen 0, 1600x1200 at 0,0
2009-05-21 20:22:15.412 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:22:15.412 Switching to square mode (Mythbuntu-8.04)
2009-05-21 20:22:15.528 Using the Qt painter
2009-05-21 20:22:15.528 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-21 20:22:15.528 lirc_init failed for mythtv, see preceding messages
2009-05-21 20:22:16.746 Specified base font 'medium' does not exist for font clock
2009-05-21 20:22:16.746 Specified base font 'medium' does not exist for font small
2009-05-21 20:22:16.746 Specified base font 'medium' does not exist for font medium
2009-05-21 20:22:16.746 Specified base font 'medium' does not exist for font large
2009-05-21 20:22:16.747 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-21 20:22:16.869 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-21 20:22:16.905 Registering Internal as a media playback plugin.
2009-05-21 20:22:17.036 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-21 20:22:17.257 Failed to run 'cdrecord --scanbus'
2009-05-21 20:22:17.260 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-21 20:22:17.265 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-21 20:22:17.284 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-21 20:22:17.403 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:41:15.983 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-21 20:41:15.985 Using protocol version 40
2009-05-21 20:41:18.076 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-21 20:41:33.448 New DB connection, total: 2
2009-05-21 20:41:33.449 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:41:33.452 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-21 20:41:33.452 Enabled verbose msgs:  important general
2009-05-21 20:41:33.977 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:41:33.980 Primary screen 0.
2009-05-21 20:41:33.980 Using screen 0, 1600x1200 at 0,0
2009-05-21 20:41:33.981 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:41:33.981 Switching to square mode (Mythbuntu-8.04)
2009-05-21 20:41:34.009 Using the Qt painter
2009-05-21 20:41:34.010 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-21 20:41:34.010 lirc_init failed for mythtv, see preceding messages
2009-05-21 20:41:35.367 Specified base font 'medium' does not exist for font clock
2009-05-21 20:41:35.367 Specified base font 'medium' does not exist for font small
2009-05-21 20:41:35.367 Specified base font 'medium' does not exist for font medium
2009-05-21 20:41:35.367 Specified base font 'medium' does not exist for font large
2009-05-21 20:41:35.368 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-21 20:41:35.463 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-21 20:41:35.481 Registering Internal as a media playback plugin.
2009-05-21 20:41:35.516 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-21 20:41:35.532 Failed to run 'cdrecord --scanbus'
2009-05-21 20:41:35.538 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-21 20:41:35.546 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-21 20:41:35.560 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-21 20:41:35.595 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 20:41:38.531 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-21 20:41:38.532 Using protocol version 40
2009-05-21 20:41:38.555 TV: Attempting to change from None to WatchingLiveTV
2009-05-21 20:41:38.556 Using protocol version 40
2009-05-21 20:41:40.111 DPMS Deactivated 
2009-05-21 20:41:40.202 New DB connection, total: 3
2009-05-21 20:41:40.202 Connected to database 'mythconverg' at host: localhost
2009-05-21 20:41:40.295 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-21 20:41:40.295 Opening ALSA audio device 'default'.
2009-05-21 20:41:40.444 mixer unable to find control Master 1
2009-05-21 20:41:40.583 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-21 20:41:40.636 OSD Theme Dimensions W: 640 H: 480
2009-05-21 20:41:41.226 TV: Changing from None to WatchingLiveTV
2009-05-21 20:41:41.236 Realtime priority would require SUID as root.
2009-05-21 20:41:41.336 Video timing method: USleep with busy wait
2009-05-21 20:44:50.525 TV: Attempting to change from WatchingLiveTV to None
2009-05-21 20:44:50.855 TV: Changing from WatchingLiveTV to None
2009-05-21 20:44:50.931 DPMS Reactivated.
2009-05-21 20:44:53.791 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-21 21:08:10.810 New DB connection, total: 2
2009-05-21 21:08:10.810 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:10.813 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-21 21:08:10.814 Enabled verbose msgs:  important general
2009-05-21 21:08:11.345 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 21:08:11.348 Primary screen 0.
2009-05-21 21:08:11.348 Using screen 0, 1600x1200 at 0,0
2009-05-21 21:08:11.349 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 21:08:11.349 Switching to square mode (Mythbuntu-8.04)
2009-05-21 21:08:11.376 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-21 21:08:11.377 lirc_init failed for mythtv, see preceding messages
2009-05-21 21:08:11.377 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
2009-05-21 21:08:12.780 Specified base font 'medium' does not exist for font clock
2009-05-21 21:08:12.780 Specified base font 'medium' does not exist for font small
2009-05-21 21:08:12.780 Specified base font 'medium' does not exist for font medium
2009-05-21 21:08:12.780 Specified base font 'medium' does not exist for font large
2009-05-21 21:08:12.781 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-21 21:08:12.883 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-21 21:08:12.901 Registering Internal as a media playback plugin.
2009-05-21 21:08:12.937 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-21 21:08:12.952 Failed to run 'cdrecord --scanbus'
2009-05-21 21:08:12.960 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-21 21:08:12.963 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-21 21:08:12.978 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-21 21:08:13.012 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 21:08:15.777 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-21 21:08:15.778 Using protocol version 40
2009-05-21 21:08:15.791 TV: Attempting to change from None to WatchingLiveTV
2009-05-21 21:08:15.792 Using protocol version 40
2009-05-21 21:08:16.998 DPMS Deactivated 
2009-05-21 21:08:17.045 New DB connection, total: 3
2009-05-21 21:08:17.046 Connected to database 'mythconverg' at host: localhost
2009-05-21 21:08:17.137 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-21 21:08:17.137 Opening ALSA audio device 'default'.
2009-05-21 21:08:17.214 mixer unable to find control Master 1
2009-05-21 21:08:17.476 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-21 21:08:17.520 OSD Theme Dimensions W: 640 H: 480
2009-05-21 21:08:17.958 TV: Changing from None to WatchingLiveTV
2009-05-21 21:08:17.964 Realtime priority would require SUID as root.
2009-05-21 21:08:18.063 Video timing method: USleep with busy wait
2009-05-21 21:08:27.859 NVP: prebuffering pause
2009-05-21 21:08:33.367 NVP: prebuffering pause
2009-05-21 21:08:33.403 WriteAudio: buffer underrun
2009-05-21 21:08:35.060 NVP: Prebuffer wait timed out 10 times.
2009-05-21 21:08:45.092 NVP: prebuffering pause
2009-05-21 21:08:45.129 WriteAudio: buffer underrun
2009-05-21 21:09:02.722 NVP: prebuffering pause
2009-05-21 21:09:02.759 WriteAudio: buffer underrun
2009-05-21 21:09:04.391 NVP: Prebuffer wait timed out 10 times.
2009-05-21 21:09:16.050 TV: Attempting to change from WatchingLiveTV to None
2009-05-21 21:09:16.428 TV: Changing from WatchingLiveTV to None
2009-05-21 21:09:16.448 DPMS Reactivated.
2009-05-21 21:09:18.091 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-21 21:09:24.070 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-23 22:46:49.521 New DB connection, total: 2
2009-05-23 22:46:49.521 Connected to database 'mythconverg' at host: localhost
2009-05-23 22:46:49.522 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-23 22:46:49.522 Enabled verbose msgs:  important general
2009-05-23 22:46:49.614 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-05-23 22:46:50.932 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-23 22:46:50.933 Primary screen 0.
2009-05-23 22:46:50.933 Using screen 0, 1600x1200 at 0,0
2009-05-23 22:46:50.933 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-23 22:46:50.933 Switching to square mode (Mythbuntu-8.04)
2009-05-23 22:46:51.029 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-23 22:46:51.030 lirc_init failed for mythtv, see preceding messages
2009-05-23 22:46:51.030 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
2009-05-23 22:46:52.228 Specified base font 'medium' does not exist for font clock
2009-05-23 22:46:52.229 Specified base font 'medium' does not exist for font small
2009-05-23 22:46:52.229 Specified base font 'medium' does not exist for font medium
2009-05-23 22:46:52.229 Specified base font 'medium' does not exist for font large
2009-05-23 22:46:52.229 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-23 22:46:52.353 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-23 22:46:52.405 Registering Internal as a media playback plugin.
2009-05-23 22:46:52.568 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-23 22:46:52.778 Failed to run 'cdrecord --scanbus'
2009-05-23 22:46:52.780 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-23 22:46:52.786 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-23 22:46:52.803 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-23 22:46:52.953 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-23 23:03:54.591 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-23 23:03:54.594 Using protocol version 40
2009-05-23 23:03:54.615 TV: Attempting to change from None to WatchingLiveTV
2009-05-23 23:03:54.617 Using protocol version 40
2009-05-23 23:03:56.043 DPMS Deactivated 
2009-05-23 23:03:56.126 New DB connection, total: 3
2009-05-23 23:03:56.126 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:03:56.220 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-23 23:03:56.220 Opening ALSA audio device 'default'.
2009-05-23 23:03:56.365 mixer unable to find control Master 1
2009-05-23 23:03:56.579 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-23 23:03:56.629 OSD Theme Dimensions W: 640 H: 480
2009-05-23 23:03:57.138 TV: Changing from None to WatchingLiveTV
2009-05-23 23:03:57.146 Realtime priority would require SUID as root.
2009-05-23 23:03:57.244 Video timing method: USleep with busy wait
2009-05-23 23:05:39.621 NVP: prebuffering pause
2009-05-23 23:05:52.717 NVP: prebuffering pause
2009-05-23 23:06:36.457 NVP: prebuffering pause
2009-05-23 23:06:36.775 New DB connection, total: 4
2009-05-23 23:06:36.777 Connected to database 'mythconverg' at host: localhost
2009-05-23 23:07:02.134 NVP: prebuffering pause
2009-05-23 23:07:13.083 NVP: prebuffering pause
2009-05-23 23:07:43.736 NVP: prebuffering pause
2009-05-23 23:10:48.680 NVP: prebuffering pause
2009-05-23 23:10:48.680 WriteAudio: buffer underrun
2009-05-23 23:12:22.249 NVP: prebuffering pause
2009-05-23 23:14:47.066 NVP: prebuffering pause
2009-05-23 23:14:47.104 WriteAudio: buffer underrun
2009-05-23 23:14:48.516 WriteAudio: buffer underrun
2009-05-23 23:14:48.729 NVP: Prebuffer wait timed out 10 times.
2009-05-23 23:14:56.783 NVP: prebuffering pause
2009-05-23 23:14:56.820 WriteAudio: buffer underrun
2009-05-23 23:15:31.282 NVP: prebuffering pause
2009-05-23 23:16:26.089 NVP: prebuffering pause
2009-05-23 23:16:36.448 NVP: prebuffering pause
2009-05-23 23:18:20.561 NVP: prebuffering pause
2009-05-23 23:18:20.562 WriteAudio: buffer underrun
2009-05-23 23:21:50.132 WriteAudio: buffer underrun
2009-05-23 23:21:55.282 WriteAudio: buffer underrun
2009-05-23 23:21:55.883 WriteAudio: buffer underrun
2009-05-23 23:22:11.388 NVP: prebuffering pause
2009-05-23 23:22:33.562 NVP: prebuffering pause
2009-05-23 23:22:33.562 WriteAudio: buffer underrun
2009-05-23 23:23:56.012 NVP: prebuffering pause
2009-05-23 23:29:10.614 NVP: prebuffering pause
2009-05-23 23:29:10.614 WriteAudio: buffer underrun
2009-05-23 23:32:32.539 NVP: prebuffering pause
2009-05-23 23:35:11.788 WriteAudio: buffer underrun
2009-05-23 23:35:31.173 WriteAudio: buffer underrun
2009-05-23 23:35:50.931 NVP: prebuffering pause
2009-05-23 23:39:51.224 NVP: prebuffering pause
2009-05-23 23:39:51.225 WriteAudio: buffer underrun
2009-05-23 23:41:50.245 NVP: prebuffering pause
2009-05-23 23:42:18.685 NVP: prebuffering pause
2009-05-23 23:42:29.761 NVP: prebuffering pause
2009-05-23 23:45:27.117 WriteAudio: buffer underrun
2009-05-23 23:45:48.053 NVP: prebuffering pause
2009-05-23 23:48:41.232 WriteAudio: buffer underrun
2009-05-23 23:48:45.995 NVP: prebuffering pause
2009-05-23 23:48:45.996 WriteAudio: buffer underrun
2009-05-23 23:50:29.236 NVP: prebuffering pause
2009-05-23 23:52:23.687 WriteAudio: buffer underrun
2009-05-23 23:52:30.160 WriteAudio: buffer underrun
2009-05-23 23:52:32.088 NVP: prebuffering pause
2009-05-23 23:53:46.839 WriteAudio: buffer underrun
2009-05-23 23:53:50.105 WriteAudio: buffer underrun
2009-05-23 23:53:51.379 NVP: prebuffering pause
2009-05-23 23:54:29.444 WriteAudio: buffer underrun
2009-05-23 23:54:30.045 NVP: prebuffering pause
2009-05-23 23:56:56.925 WriteAudio: buffer underrun
2009-05-23 23:56:58.125 NVP: prebuffering pause
2009-05-23 23:58:39.799 NVP: prebuffering pause
2009-05-24 00:00:07.425 NVP: prebuffering pause
2009-05-24 00:00:18.351 NVP: prebuffering pause
2009-05-24 00:00:18.389 WriteAudio: buffer underrun
2009-05-24 00:00:40.409 NVP: prebuffering pause
2009-05-24 00:00:42.522 NVP: prebuffering pause
2009-05-24 00:01:07.295 NVP: prebuffering pause
2009-05-24 00:02:38.509 WriteAudio: buffer underrun
2009-05-24 00:02:41.716 WriteAudio: buffer underrun
2009-05-24 00:02:45.035 NVP: prebuffering pause
2009-05-24 00:03:03.757 NVP: prebuffering pause
2009-05-24 00:03:07.330 NVP: prebuffering pause
2009-05-24 00:05:24.259 NVP: prebuffering pause
2009-05-24 00:05:24.260 WriteAudio: buffer underrun
2009-05-24 00:05:25.593 NVP: prebuffering pause
2009-05-24 00:09:05.873 WriteAudio: buffer underrun
2009-05-24 00:09:50.978 NVP: prebuffering pause
2009-05-24 00:09:50.979 WriteAudio: buffer underrun
2009-05-24 00:12:03.192 WriteAudio: buffer underrun
2009-05-24 00:12:11.277 NVP: prebuffering pause
2009-05-24 00:12:11.280 WriteAudio: buffer underrun
2009-05-24 00:15:28.957 NVP: prebuffering pause
2009-05-24 00:17:02.897 NVP: prebuffering pause
2009-05-24 00:17:02.908 WriteAudio: buffer underrun
2009-05-24 00:21:12.502 WriteAudio: buffer underrun
2009-05-24 00:21:51.595 NVP: prebuffering pause
2009-05-24 00:21:51.597 WriteAudio: buffer underrun
2009-05-24 00:24:32.002 NVP: prebuffering pause
2009-05-24 00:28:20.494 NVP: prebuffering pause
2009-05-24 00:30:02.181 NVP: prebuffering pause
2009-05-24 00:37:25.370 WriteAudio: buffer underrun
2009-05-24 00:38:25.084 NVP: prebuffering pause
2009-05-24 00:38:25.086 WriteAudio: buffer underrun
2009-05-24 00:40:13.670 NVP: prebuffering pause
2009-05-24 00:43:48.291 NVP: prebuffering pause
2009-05-24 00:47:21.440 NVP: prebuffering pause
2009-05-24 00:47:21.441 WriteAudio: buffer underrun
2009-05-24 00:48:50.799 NVP: prebuffering pause
2009-05-24 00:51:15.763 NVP: prebuffering pause
2009-05-24 00:51:15.766 WriteAudio: buffer underrun
2009-05-24 00:56:32.858 NVP: prebuffering pause
2009-05-24 00:57:56.546 NVP: prebuffering pause
2009-05-24 00:57:56.548 WriteAudio: buffer underrun
2009-05-24 01:05:45.017 WriteAudio: buffer underrun
2009-05-24 01:05:58.794 WriteAudio: buffer underrun
2009-05-24 01:06:21.516 WriteAudio: buffer underrun
2009-05-24 01:06:22.880 NVP: prebuffering pause
2009-05-24 01:07:15.695 NVP: prebuffering pause
2009-05-24 01:07:28.745 NVP: prebuffering pause
2009-05-24 01:09:50.986 WriteAudio: buffer underrun
2009-05-24 01:10:31.622 NVP: prebuffering pause
2009-05-24 01:13:35.923 NVP: prebuffering pause
2009-05-24 01:13:35.924 WriteAudio: buffer underrun
2009-05-24 01:17:41.386 NVP: prebuffering pause
2009-05-24 01:17:41.387 WriteAudio: buffer underrun
2009-05-24 01:19:51.785 WriteAudio: buffer underrun
2009-05-24 01:20:03.401 NVP: prebuffering pause
2009-05-24 01:20:03.403 WriteAudio: buffer underrun
2009-05-24 01:24:52.315 WriteAudio: buffer underrun
2009-05-24 01:25:08.629 WriteAudio: buffer underrun
2009-05-24 01:25:25.448 WriteAudio: buffer underrun
2009-05-24 01:25:35.137 WriteAudio: buffer underrun
2009-05-24 01:26:43.564 NVP: prebuffering pause
2009-05-24 01:26:43.566 WriteAudio: buffer underrun
2009-05-24 01:31:32.971 NVP: prebuffering pause
2009-05-24 01:33:01.570 WriteAudio: buffer underrun
2009-05-24 01:33:07.423 NVP: prebuffering pause
2009-05-24 01:34:37.763 WriteAudio: buffer underrun
2009-05-24 01:34:44.591 NVP: prebuffering pause
2009-05-24 01:36:26.606 NVP: prebuffering pause
2009-05-24 01:38:12.555 WriteAudio: buffer underrun
2009-05-24 01:38:15.093 NVP: prebuffering pause
2009-05-24 01:39:56.386 WriteAudio: buffer underrun
2009-05-24 01:40:06.590 WriteAudio: buffer underrun
2009-05-24 01:40:07.799 NVP: prebuffering pause
2009-05-24 01:42:58.169 WriteAudio: buffer underrun
2009-05-24 01:43:00.390 NVP: prebuffering pause
2009-05-24 01:45:28.547 WriteAudio: buffer underrun
2009-05-24 01:45:29.692 WriteAudio: buffer underrun
2009-05-24 01:45:31.987 WriteAudio: buffer underrun
2009-05-24 01:46:05.076 NVP: prebuffering pause
2009-05-24 01:48:45.381 WriteAudio: buffer underrun
2009-05-24 01:48:53.895 WriteAudio: buffer underrun
2009-05-24 01:49:58.008 WriteAudio: buffer underrun
2009-05-24 01:49:59.906 NVP: prebuffering pause
2009-05-24 01:52:31.181 WriteAudio: buffer underrun
2009-05-24 01:52:52.309 NVP: prebuffering pause
2009-05-24 01:54:52.983 WriteAudio: buffer underrun
2009-05-24 01:54:56.120 WriteAudio: buffer underrun
2009-05-24 01:55:17.073 WriteAudio: buffer underrun
2009-05-24 01:55:28.295 NVP: prebuffering pause
2009-05-24 01:58:41.209 WriteAudio: buffer underrun
2009-05-24 01:58:45.320 WriteAudio: buffer underrun
2009-05-24 01:59:14.537 NVP: prebuffering pause
2009-05-24 02:00:15.602 NVP: prebuffering pause
2009-05-24 02:03:42.791 WriteAudio: buffer underrun
2009-05-24 02:03:47.309 NVP: prebuffering pause
2009-05-24 02:04:22.717 NVP: prebuffering pause
2009-05-24 02:06:16.328 WriteAudio: buffer underrun
2009-05-24 02:06:17.235 NVP: prebuffering pause
2009-05-24 02:07:29.374 WriteAudio: buffer underrun
2009-05-24 02:07:29.399 WriteAudio: buffer underrun
2009-05-24 02:07:31.008 NVP: prebuffering pause
2009-05-24 02:07:55.536 WriteAudio: buffer underrun
2009-05-24 02:07:59.996 NVP: prebuffering pause
2009-05-24 02:07:59.996 WriteAudio: buffer underrun
2009-05-24 02:10:05.058 NVP: prebuffering pause
2009-05-24 02:10:05.059 WriteAudio: buffer underrun
2009-05-24 02:14:40.870 NVP: prebuffering pause
2009-05-24 02:14:41.488 WriteAudio: buffer underrun
2009-05-24 02:14:55.784 WriteAudio: buffer underrun
2009-05-24 02:15:33.250 WriteAudio: buffer underrun
2009-05-24 02:15:33.851 NVP: prebuffering pause
2009-05-24 02:15:33.852 WriteAudio: buffer underrun
2009-05-24 02:18:23.390 NVP: prebuffering pause
2009-05-24 02:19:48.470 WriteAudio: buffer underrun
2009-05-24 02:19:49.304 NVP: prebuffering pause
2009-05-24 02:19:49.305 WriteAudio: buffer underrun
2009-05-24 02:20:48.869 NVP: prebuffering pause
2009-05-24 02:23:37.100 NVP: prebuffering pause
2009-05-24 02:23:37.101 WriteAudio: buffer underrun
2009-05-24 02:27:20.379 NVP: prebuffering pause
2009-05-24 02:27:54.648 WriteAudio: buffer underrun
2009-05-24 02:28:09.981 WriteAudio: buffer underrun
2009-05-24 02:28:13.193 WriteAudio: buffer underrun
2009-05-24 02:28:39.411 WriteAudio: buffer underrun
2009-05-24 02:28:47.988 WriteAudio: buffer underrun
2009-05-24 02:28:52.085 WriteAudio: buffer underrun
2009-05-24 02:28:52.749 NVP: prebuffering pause
2009-05-24 02:30:37.010 NVP: prebuffering pause
2009-05-24 02:31:53.211 NVP: prebuffering pause
2009-05-24 02:34:39.594 NVP: prebuffering pause
2009-05-24 02:34:39.595 WriteAudio: buffer underrun
2009-05-24 02:36:28.308 NVP: prebuffering pause
2009-05-24 02:38:19.051 WriteAudio: buffer underrun
2009-05-24 02:38:27.016 NVP: prebuffering pause
2009-05-24 02:38:32.453 NVP: prebuffering pause
2009-05-24 02:39:40.297 WriteAudio: buffer underrun
2009-05-24 02:39:43.502 WriteAudio: buffer underrun
2009-05-24 02:39:44.770 WriteAudio: buffer underrun
2009-05-24 02:39:44.773 NVP: prebuffering pause
2009-05-24 02:40:05.132 NVP: prebuffering pause
2009-05-24 02:44:07.264 NVP: prebuffering pause
2009-05-24 02:46:26.489 WriteAudio: buffer underrun
2009-05-24 02:47:06.403 NVP: prebuffering pause
2009-05-24 02:49:13.873 WriteAudio: buffer underrun
2009-05-24 02:49:20.213 WriteAudio: buffer underrun
2009-05-24 02:49:20.820 NVP: prebuffering pause
2009-05-24 02:51:21.289 NVP: prebuffering pause
2009-05-24 02:53:58.454 WriteAudio: buffer underrun
2009-05-24 02:54:02.001 NVP: prebuffering pause
2009-05-24 02:55:14.727 NVP: prebuffering pause
2009-05-24 02:57:27.434 WriteAudio: buffer underrun
2009-05-24 02:57:28.079 NVP: prebuffering pause
2009-05-24 03:00:03.025 NVP: prebuffering pause
2009-05-24 03:06:40.551 WriteAudio: buffer underrun
2009-05-24 03:07:16.569 WriteAudio: buffer underrun
2009-05-24 03:07:17.348 NVP: prebuffering pause
2009-05-24 03:08:01.341 NVP: prebuffering pause
2009-05-24 03:09:57.853 WriteAudio: buffer underrun
2009-05-24 03:10:28.112 NVP: prebuffering pause
2009-05-24 03:10:28.114 WriteAudio: buffer underrun
2009-05-24 03:15:25.141 NVP: prebuffering pause
2009-05-24 03:15:26.408 NVP: prebuffering pause
2009-05-24 03:16:34.909 NVP: prebuffering pause
2009-05-24 03:18:41.538 WriteAudio: buffer underrun
2009-05-24 03:18:42.812 NVP: prebuffering pause
2009-05-24 03:18:42.816 WriteAudio: buffer underrun
2009-05-24 03:23:07.602 NVP: prebuffering pause
2009-05-24 03:23:07.657 WriteAudio: buffer underrun
2009-05-24 03:25:21.491 NVP: prebuffering pause
2009-05-24 03:25:21.491 WriteAudio: buffer underrun
2009-05-24 03:35:59.593 WriteAudio: buffer underrun
2009-05-24 03:37:21.941 WriteAudio: buffer underrun
2009-05-24 03:37:25.213 WriteAudio: buffer underrun
2009-05-24 03:37:27.754 NVP: prebuffering pause
2009-05-24 03:38:14.868 NVP: prebuffering pause
2009-05-24 03:38:15.505 NVP: prebuffering pause
2009-05-24 03:38:46.877 NVP: prebuffering pause
2009-05-24 03:40:09.460 WriteAudio: buffer underrun
2009-05-24 03:40:12.661 WriteAudio: buffer underrun
2009-05-24 03:40:43.097 NVP: prebuffering pause
2009-05-24 03:42:23.226 NVP: prebuffering pause
2009-05-24 03:48:00.132 NVP: prebuffering pause
2009-05-24 03:48:00.133 WriteAudio: buffer underrun
2009-05-24 03:49:09.058 NVP: prebuffering pause
2009-05-24 03:50:35.100 WriteAudio: buffer underrun
2009-05-24 03:50:35.688 WriteAudio: buffer underrun
2009-05-24 03:50:58.005 WriteAudio: buffer underrun
2009-05-24 03:51:12.018 WriteAudio: buffer underrun
2009-05-24 03:51:12.816 WriteAudio: buffer underrun
2009-05-24 03:51:13.753 NVP: prebuffering pause
2009-05-24 03:54:29.448 WriteAudio: buffer underrun
2009-05-24 03:54:30.052 WriteAudio: buffer underrun
2009-05-24 03:54:34.519 WriteAudio: buffer underrun
2009-05-24 03:54:40.194 WriteAudio: buffer underrun
2009-05-24 03:54:44.065 WriteAudio: buffer underrun
2009-05-24 03:54:58.808 NVP: prebuffering pause
2009-05-24 03:54:58.810 WriteAudio: buffer underrun
2009-05-24 03:57:10.442 NVP: prebuffering pause
2009-05-24 03:57:10.443 WriteAudio: buffer underrun
2009-05-24 04:04:08.558 NVP: prebuffering pause
2009-05-24 04:05:12.903 NVP: prebuffering pause
2009-05-24 04:08:01.024 WriteAudio: buffer underrun
2009-05-24 04:08:04.168 WriteAudio: buffer underrun
2009-05-24 04:08:07.971 NVP: prebuffering pause
2009-05-24 04:09:51.519 NVP: prebuffering pause
2009-05-24 04:12:50.320 WriteAudio: buffer underrun
2009-05-24 04:14:03.801 NVP: prebuffering pause
2009-05-24 04:17:28.081 NVP: prebuffering pause
2009-05-24 04:19:27.471 NVP: prebuffering pause
2009-05-24 04:19:27.473 WriteAudio: buffer underrun
2009-05-24 04:22:20.646 WriteAudio: buffer underrun
2009-05-24 04:22:34.672 WriteAudio: buffer underrun
2009-05-24 04:22:35.269 NVP: prebuffering pause
2009-05-24 04:25:12.164 WriteAudio: buffer underrun
2009-05-24 04:27:04.567 WriteAudio: buffer underrun
2009-05-24 04:27:18.312 NVP: prebuffering pause
2009-05-24 04:30:18.216 WriteAudio: buffer underrun
2009-05-24 04:30:54.398 WriteAudio: buffer underrun
2009-05-24 04:30:56.938 NVP: prebuffering pause
2009-05-24 04:32:56.788 WriteAudio: buffer underrun
2009-05-24 04:33:04.837 WriteAudio: buffer underrun
2009-05-24 04:33:05.563 WriteAudio: buffer underrun
2009-05-24 04:33:06.225 WriteAudio: buffer underrun
2009-05-24 04:33:06.827 NVP: prebuffering pause
2009-05-24 04:33:06.829 WriteAudio: buffer underrun
2009-05-24 04:36:45.020 WriteAudio: buffer underrun
2009-05-24 04:37:10.342 WriteAudio: buffer underrun
2009-05-24 04:37:12.349 WriteAudio: buffer underrun
2009-05-24 04:37:12.351 NVP: prebuffering pause
2009-05-24 04:39:29.612 WriteAudio: buffer underrun
2009-05-24 04:39:31.418 NVP: prebuffering pause
2009-05-24 04:39:31.420 WriteAudio: buffer underrun
2009-05-24 04:41:55.701 WriteAudio: buffer underrun
2009-05-24 04:44:01.525 WriteAudio: buffer underrun
2009-05-24 04:44:02.326 WriteAudio: buffer underrun
2009-05-24 04:44:02.996 WriteAudio: buffer underrun
2009-05-24 04:44:50.730 NVP: prebuffering pause
2009-05-24 04:45:39.657 NVP: prebuffering pause
2009-05-24 04:48:45.265 NVP: prebuffering pause
2009-05-24 04:51:17.221 NVP: prebuffering pause
2009-05-24 04:55:40.591 NVP: prebuffering pause
2009-05-24 04:55:40.591 WriteAudio: buffer underrun
2009-05-24 04:58:24.281 WriteAudio: buffer underrun
2009-05-24 04:58:30.076 NVP: prebuffering pause
2009-05-24 05:00:03.587 NVP: prebuffering pause
2009-05-24 05:05:31.893 WriteAudio: buffer underrun
2009-05-24 05:07:17.648 NVP: prebuffering pause
2009-05-24 05:07:31.674 NVP: prebuffering pause
2009-05-24 05:09:05.875 NVP: prebuffering pause
2009-05-24 05:09:05.875 WriteAudio: buffer underrun
2009-05-24 05:09:10.760 NVP: prebuffering pause
2009-05-24 05:11:30.900 WriteAudio: buffer underrun
2009-05-24 05:11:52.156 WriteAudio: buffer underrun
2009-05-24 05:11:52.769 WriteAudio: buffer underrun
2009-05-24 05:11:57.957 WriteAudio: buffer underrun
2009-05-24 05:12:09.376 WriteAudio: buffer underrun
2009-05-24 05:12:10.937 NVP: prebuffering pause
2009-05-24 05:12:10.938 WriteAudio: buffer underrun
2009-05-24 05:14:35.450 WriteAudio: buffer underrun
2009-05-24 05:14:47.966 NVP: prebuffering pause
2009-05-24 05:14:47.967 WriteAudio: buffer underrun
2009-05-24 05:18:59.805 NVP: prebuffering pause
2009-05-24 05:19:29.310 WriteAudio: buffer underrun
2009-05-24 05:19:49.294 WriteAudio: buffer underrun
2009-05-24 05:19:56.966 WriteAudio: buffer underrun
2009-05-24 05:20:06.538 NVP: prebuffering pause
2009-05-24 05:24:39.814 NVP: prebuffering pause
2009-05-24 05:26:13.053 WriteAudio: buffer underrun
2009-05-24 05:26:17.844 NVP: prebuffering pause
2009-05-24 05:26:17.845 WriteAudio: buffer underrun
2009-05-24 05:28:41.760 NVP: prebuffering pause
2009-05-24 05:30:35.118 TV: Attempting to change from WatchingLiveTV to None
2009-05-24 05:30:35.820 TV: Changing from WatchingLiveTV to None
2009-05-24 05:30:36.032 DPMS Reactivated.
2009-05-24 05:30:39.662 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-24 18:04:53.276 New DB connection, total: 2
2009-05-24 18:04:53.277 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:04:53.278 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 18:04:53.278 Enabled verbose msgs:  important general
2009-05-24 18:04:53.406 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-05-24 18:04:54.626 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-24 18:04:54.629 Primary screen 0.
2009-05-24 18:04:54.629 Using screen 0, 1600x1200 at 0,0
2009-05-24 18:04:54.630 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-24 18:04:54.630 Switching to square mode (Mythbuntu-8.04)
2009-05-24 18:04:54.700 Using the Qt painter
2009-05-24 18:04:54.701 JoystickMenuClient Error: Joystick disabled - Failed to read /home/matthieu/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-05-24 18:04:54.701 lirc_init failed for mythtv, see preceding messages
2009-05-24 18:04:55.789 Specified base font 'medium' does not exist for font clock
2009-05-24 18:04:55.789 Specified base font 'medium' does not exist for font small
2009-05-24 18:04:55.789 Specified base font 'medium' does not exist for font medium
2009-05-24 18:04:55.789 Specified base font 'medium' does not exist for font large
2009-05-24 18:04:55.789 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-24 18:04:55.915 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-24 18:04:55.951 Registering Internal as a media playback plugin.
2009-05-24 18:04:56.160 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-24 18:04:56.660 Failed to run 'cdrecord --scanbus'
2009-05-24 18:04:56.666 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-24 18:04:56.668 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-24 18:04:56.686 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-24 18:04:56.832 No theme dir: /home/matthieu/.mythtv/themes/Mythbuntu-8.04
2009-05-24 18:06:36.373 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-24 18:06:36.375 Using protocol version 40
2009-05-24 18:06:36.400 TV: Attempting to change from None to WatchingLiveTV
2009-05-24 18:06:36.401 Using protocol version 40
2009-05-24 18:06:38.132 New DB connection, total: 3
2009-05-24 18:06:38.133 Connected to database 'mythconverg' at host: localhost
2009-05-24 18:06:38.169 DPMS Deactivated 
2009-05-24 18:06:38.225 Opening audio device 'default'. ch 2(2) sr 44100
2009-05-24 18:06:38.225 Opening ALSA audio device 'default'.
2009-05-24 18:06:38.384 mixer unable to find control Master 1
2009-05-24 18:06:38.531 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-24 18:06:38.586 OSD Theme Dimensions W: 640 H: 480
2009-05-24 18:06:39.164 TV: Changing from None to WatchingLiveTV
2009-05-24 18:06:39.166 Realtime priority would require SUID as root.
2009-05-24 18:06:39.274 Video timing method: USleep with busy wait
2009-05-24 18:27:21.332 WriteAudio: buffer underrun
2009-05-24 18:29:38.972 WriteAudio: buffer underrun
2009-05-24 18:33:42.390 WriteAudio: buffer underrun
2009-05-24 18:34:14.183 NVP: prebuffering pause
2009-05-24 18:34:44.218 NVP: prebuffering pause
2009-05-24 18:35:03.935 NVP: prebuffering pause
2009-05-24 18:36:03.275 WriteAudio: buffer underrun
2009-05-24 18:36:07.800 WriteAudio: buffer underrun
2009-05-24 18:36:10.454 NVP: prebuffering pause
2009-05-24 18:36:10.455 WriteAudio: buffer underrun
2009-05-24 18:36:38.020 NVP: prebuffering pause
2009-05-24 18:37:07.381 NVP: prebuffering pause
2009-05-24 18:40:40.761 WriteAudio: buffer underrun
2009-05-24 18:41:31.724 WriteAudio: buffer underrun
2009-05-24 18:41:39.665 WriteAudio: buffer underrun
2009-05-24 18:41:40.935 WriteAudio: buffer underrun
2009-05-24 18:41:46.381 NVP: prebuffering pause
2009-05-24 18:42:40.150 NVP: prebuffering pause
2009-05-24 18:45:34.967 WriteAudio: buffer underrun
2009-05-24 18:45:35.523 NVP: prebuffering pause
2009-05-24 18:49:41.067 NVP: prebuffering pause
2009-05-24 18:51:10.723 NVP: prebuffering pause
2009-05-24 18:52:10.619 NVP: prebuffering pause
2009-05-24 18:57:26.396 NVP: prebuffering pause
2009-05-24 18:57:26.398 WriteAudio: buffer underrun
2009-05-24 19:05:11.089 NVP: prebuffering pause
2009-05-24 19:07:22.312 WriteAudio: buffer underrun
2009-05-24 19:07:22.975 WriteAudio: buffer underrun
2009-05-24 19:07:26.117 WriteAudio: buffer underrun
2009-05-24 19:08:29.951 NVP: prebuffering pause
2009-05-24 19:08:33.812 NVP: prebuffering pause
2009-05-24 19:14:03.309 WriteAudio: buffer underrun
2009-05-24 19:19:25.904 WriteAudio: buffer underrun
2009-05-24 19:19:25.906 NVP: prebuffering pause
2009-05-24 19:21:34.973 NVP: prebuffering pause
2009-05-24 19:21:34.974 WriteAudio: buffer underrun
2009-05-24 19:24:05.201 WriteAudio: buffer underrun
2009-05-24 19:24:28.285 NVP: prebuffering pause
2009-05-24 19:24:28.286 WriteAudio: buffer underrun
2009-05-24 19:27:55.095 NVP: prebuffering pause
2009-05-24 19:30:16.877 WriteAudio: buffer underrun
2009-05-24 19:30:49.073 WriteAudio: buffer underrun
2009-05-24 19:30:50.940 NVP: prebuffering pause
2009-05-24 19:33:22.774 WriteAudio: buffer underrun
2009-05-24 19:33:29.827 NVP: prebuffering pause
2009-05-24 19:36:28.830 WriteAudio: buffer underrun
2009-05-24 19:36:43.270 NVP: prebuffering pause
2009-05-24 19:40:11.074 NVP: prebuffering pause
2009-05-24 19:42:31.412 WriteAudio: buffer underrun
2009-05-24 19:43:46.415 NVP: prebuffering pause
2009-05-24 19:45:40.172 WriteAudio: buffer underrun
2009-05-24 19:45:52.748 NVP: prebuffering pause
2009-05-24 19:45:52.749 WriteAudio: buffer underrun
2009-05-24 19:49:03.772 WriteAudio: buffer underrun
2009-05-24 19:49:05.712 NVP: prebuffering pause
2009-05-24 19:51:43.931 NVP: prebuffering pause
2009-05-24 19:52:13.988 WriteAudio: buffer underrun
2009-05-24 19:52:20.879 NVP: prebuffering pause
2009-05-24 19:52:20.880 WriteAudio: buffer underrun
2009-05-24 19:56:48.139 NVP: prebuffering pause
2009-05-24 20:00:03.185 NVP: prebuffering pause
2009-05-24 20:03:48.718 WriteAudio: buffer underrun
2009-05-24 20:04:00.997 WriteAudio: buffer underrun
2009-05-24 20:06:29.522 WriteAudio: buffer underrun
2009-05-24 20:06:30.254 NVP: prebuffering pause
2009-05-24 20:06:30.255 WriteAudio: buffer underrun
2009-05-24 20:06:59.856 NVP: prebuffering pause
2009-05-24 20:11:46.577 NVP: prebuffering pause
2009-05-24 20:13:09.658 NVP: prebuffering pause
2009-05-24 20:13:49.955 NVP: prebuffering pause
2009-05-24 20:13:49.992 WriteAudio: buffer underrun
2009-05-24 20:13:51.167 New DB connection, total: 4
2009-05-24 20:13:51.168 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:13:51.620 NVP: Prebuffer wait timed out 10 times.
2009-05-24 20:14:09.588 NVP: prebuffering pause
2009-05-24 20:14:28.532 NVP: prebuffering pause
2009-05-24 20:14:28.570 WriteAudio: buffer underrun
2009-05-24 20:14:59.018 NVP: prebuffering pause
2009-05-24 20:19:42.238 NVP: prebuffering pause
2009-05-24 20:19:42.276 WriteAudio: buffer underrun
2009-05-24 20:19:43.853 NVP: Prebuffer wait timed out 10 times.
2009-05-24 20:20:34.125 NVP: prebuffering pause
2009-05-24 20:20:59.946 NVP: prebuffering pause
2009-05-24 20:22:30.289 NVP: prebuffering pause
2009-05-24 20:23:35.076 NVP: prebuffering pause
2009-05-24 20:26:08.022 NVP: prebuffering pause
2009-05-24 20:26:08.059 WriteAudio: buffer underrun
2009-05-24 20:26:09.639 NVP: Prebuffer wait timed out 10 times.
2009-05-24 20:26:16.650 NVP: prebuffering pause
2009-05-24 20:26:16.687 WriteAudio: buffer underrun
2009-05-24 20:26:52.293 NVP: prebuffering pause
2009-05-24 20:26:56.924 NVP: prebuffering pause
2009-05-24 20:27:35.716 NVP: prebuffering pause
2009-05-24 20:31:26.331 NVP: prebuffering pause
2009-05-24 20:34:24.001 WriteAudio: buffer underrun
2009-05-24 20:34:25.810 NVP: prebuffering pause
2009-05-24 20:34:25.812 WriteAudio: buffer underrun
2009-05-24 20:34:50.969 NVP: prebuffering pause
2009-05-24 20:34:51.007 WriteAudio: buffer underrun
2009-05-24 20:35:57.849 NVP: prebuffering pause
2009-05-24 20:36:09.694 NVP: prebuffering pause
2009-05-24 20:36:09.694 WriteAudio: buffer underrun
2009-05-24 20:36:13.939 NVP: prebuffering pause
2009-05-24 20:36:37.480 NVP: prebuffering pause
2009-05-24 20:38:27.053 NVP: prebuffering pause
2009-05-24 20:38:27.097 WriteAudio: buffer underrun
2009-05-24 20:38:45.637 NVP: prebuffering pause
2009-05-24 20:38:45.638 WriteAudio: buffer underrun
2009-05-24 20:39:26.211 NVP: prebuffering pause
2009-05-24 20:39:40.486 NVP: prebuffering pause
2009-05-24 20:39:40.489 WriteAudio: buffer underrun
2009-05-24 20:42:28.044 NVP: prebuffering pause
2009-05-24 20:42:28.045 WriteAudio: buffer underrun
2009-05-24 20:44:11.469 WriteAudio: buffer underrun
2009-05-24 20:44:46.917 WriteAudio: buffer underrun
2009-05-24 20:44:47.598 NVP: prebuffering pause
2009-05-24 20:46:45.546 NVP: prebuffering pause
2009-05-24 20:47:28.834 NVP: prebuffering pause
2009-05-24 20:50:18.499 WriteAudio: buffer underrun
2009-05-24 20:50:19.077 NVP: prebuffering pause
2009-05-24 20:50:19.079 WriteAudio: buffer underrun
2009-05-24 20:52:43.514 NVP: prebuffering pause
2009-05-24 20:52:43.514 WriteAudio: buffer underrun
2009-05-24 20:56:03.350 WriteAudio: buffer underrun
2009-05-24 20:56:04.679 WriteAudio: buffer underrun
2009-05-24 20:56:30.711 WriteAudio: buffer underrun
2009-05-24 20:56:33.937 WriteAudio: buffer underrun
2009-05-24 20:56:34.552 NVP: prebuffering pause
2009-05-24 20:57:35.911 NVP: prebuffering pause
2009-05-24 21:00:13.508 NVP: prebuffering pause
2009-05-24 21:03:13.482 NVP: prebuffering pause
2009-05-24 21:03:13.496 WriteAudio: buffer underrun
2009-05-24 21:07:10.981 NVP: prebuffering pause
2009-05-24 21:07:10.982 WriteAudio: buffer underrun
2009-05-24 21:07:30.495 NVP: prebuffering pause
2009-05-24 21:13:06.991 WriteAudio: buffer underrun
2009-05-24 21:13:09.001 WriteAudio: buffer underrun
2009-05-24 21:13:10.198 WriteAudio: buffer underrun
2009-05-24 21:13:10.203 NVP: prebuffering pause
2009-05-24 21:13:29.491 NVP: prebuffering pause
2009-05-24 21:13:29.492 WriteAudio: buffer underrun
2009-05-24 21:13:59.634 NVP: prebuffering pause
2009-05-24 21:15:48.765 NVP: prebuffering pause
2009-05-24 21:18:34.008 WriteAudio: buffer underrun
2009-05-24 21:18:34.010 NVP: prebuffering pause
2009-05-24 21:19:07.575 NVP: prebuffering pause
2009-05-24 21:25:28.089 WriteAudio: buffer underrun
2009-05-24 21:25:41.197 NVP: prebuffering pause
2009-05-24 21:27:47.857 WriteAudio: buffer underrun
2009-05-24 21:28:18.016 WriteAudio: buffer underrun
2009-05-24 21:29:43.439 NVP: prebuffering pause
2009-05-24 21:29:43.480 WriteAudio: buffer underrun
2009-05-24 21:29:45.139 NVP: Prebuffer wait timed out 10 times.
2009-05-24 21:29:55.465 NVP: prebuffering pause
2009-05-24 21:30:29.576 NVP: prebuffering pause
2009-05-24 21:30:46.928 NVP: prebuffering pause
2009-05-24 21:35:19.073 WriteAudio: buffer underrun
2009-05-24 21:35:19.656 WriteAudio: buffer underrun
2009-05-24 21:35:19.660 NVP: prebuffering pause
2009-05-24 21:36:58.853 NVP: prebuffering pause
2009-05-24 21:39:09.224 WriteAudio: buffer underrun
2009-05-24 21:39:09.227 NVP: prebuffering pause
2009-05-24 21:41:34.870 WriteAudio: buffer underrun
2009-05-24 21:42:36.654 NVP: prebuffering pause
2009-05-24 21:42:36.654 WriteAudio: buffer underrun
2009-05-24 21:46:32.861 NVP: prebuffering pause
2009-05-24 21:49:29.522 NVP: prebuffering pause
2009-05-24 21:51:41.640 WriteAudio: buffer underrun
2009-05-24 21:51:51.244 WriteAudio: buffer underrun
2009-05-24 21:51:58.245 NVP: prebuffering pause
2009-05-24 21:51:58.246 WriteAudio: buffer underrun
2009-05-24 21:53:22.271 NVP: prebuffering pause
2009-05-24 21:55:42.274 WriteAudio: buffer underrun
2009-05-24 21:55:48.616 NVP: prebuffering pause
2009-05-24 21:57:58.162 WriteAudio: buffer underrun
2009-05-24 21:58:06.805 WriteAudio: buffer underrun
2009-05-24 21:58:07.470 WriteAudio: buffer underrun
2009-05-24 21:58:13.560 WriteAudio: buffer underrun
2009-05-24 21:58:23.102 NVP: prebuffering pause
2009-05-24 21:58:23.103 WriteAudio: buffer underrun
2009-05-24 21:58:56.139 NVP: prebuffering pause
2009-05-24 22:01:15.459 NVP: prebuffering pause
2009-05-24 22:05:05.490 NVP: prebuffering pause
2009-05-24 22:05:05.492 WriteAudio: buffer underrun
2009-05-24 22:07:35.488 WriteAudio: buffer underrun
2009-05-24 22:08:00.446 NVP: prebuffering pause
2009-05-24 22:08:00.447 WriteAudio: buffer underrun
2009-05-24 22:11:37.299 WriteAudio: buffer underrun
2009-05-24 22:11:37.299 NVP: prebuffering pause
2009-05-24 22:11:59.787 NVP: prebuffering pause
2009-05-24 22:14:53.395 WriteAudio: buffer underrun
2009-05-24 22:14:56.595 WriteAudio: buffer underrun
2009-05-24 22:14:58.472 NVP: prebuffering pause
2009-05-24 22:16:44.024 NVP: prebuffering pause
2009-05-24 22:20:11.838 NVP: prebuffering pause
2009-05-24 22:21:40.124 NVP: prebuffering pause
2009-05-24 22:21:40.126 WriteAudio: buffer underrun
2009-05-24 22:26:04.968 NVP: prebuffering pause
2009-05-24 22:30:30.168 NVP: prebuffering pause
2009-05-24 22:34:05.398 NVP: prebuffering pause
2009-05-24 22:35:30.162 WriteAudio: buffer underrun
2009-05-24 22:35:33.300 WriteAudio: buffer underrun
2009-05-24 22:35:38.747 WriteAudio: buffer underrun
2009-05-24 22:35:38.754 NVP: prebuffering pause
2009-05-24 22:37:11.530 WriteAudio: buffer underrun
2009-05-24 22:37:12.129 NVP: prebuffering pause
2009-05-24 22:37:40.867 WriteAudio: buffer underrun
2009-05-24 22:38:40.641 NVP: prebuffering pause
2009-05-24 22:38:40.643 WriteAudio: buffer underrun
2009-05-24 22:41:49.277 NVP: prebuffering pause
2009-05-24 22:44:56.391 WriteAudio: buffer underrun
2009-05-24 22:45:10.683 NVP: prebuffering pause
2009-05-24 22:48:28.914 NVP: prebuffering pause
2009-05-24 22:48:28.917 WriteAudio: buffer underrun
2009-05-24 22:49:37.922 WriteAudio: buffer underrun
2009-05-24 22:50:52.445 WriteAudio: buffer underrun
2009-05-24 22:51:57.922 WriteAudio: buffer underrun
2009-05-24 22:52:02.071 NVP: prebuffering pause
2009-05-24 22:52:06.260 NVP: prebuffering pause
2009-05-24 22:52:39.256 NVP: prebuffering pause
2009-05-24 22:57:18.151 NVP: prebuffering pause
2009-05-24 22:58:18.020 NVP: prebuffering pause
2009-05-24 22:58:18.021 WriteAudio: buffer underrun
2009-05-24 23:00:03.266 NVP: prebuffering pause
2009-05-24 23:05:59.375 NVP: prebuffering pause
2009-05-24 23:10:34.081 NVP: prebuffering pause
2009-05-24 23:12:56.951 WriteAudio: buffer underrun
2009-05-24 23:12:57.676 NVP: prebuffering pause
2009-05-24 23:12:57.694 WriteAudio: buffer underrun
2009-05-24 23:14:41.708 WriteAudio: buffer underrun
2009-05-24 23:16:36.801 WriteAudio: buffer underrun
2009-05-24 23:16:41.405 WriteAudio: buffer underrun
2009-05-24 23:16:49.699 NVP: prebuffering pause
2009-05-24 23:16:49.700 WriteAudio: buffer underrun
2009-05-24 23:19:32.133 WriteAudio: buffer underrun
2009-05-24 23:19:38.906 WriteAudio: buffer underrun
2009-05-24 23:19:53.002 WriteAudio: buffer underrun
2009-05-24 23:20:16.854 NVP: prebuffering pause
2009-05-24 23:22:33.825 NVP: prebuffering pause
2009-05-24 23:24:58.814 WriteAudio: buffer underrun
2009-05-24 23:25:15.958 NVP: prebuffering pause
2009-05-24 23:27:24.213 WriteAudio: buffer underrun
2009-05-24 23:27:25.540 WriteAudio: buffer underrun
2009-05-24 23:27:27.493 WriteAudio: buffer underrun
2009-05-24 23:27:37.150 WriteAudio: buffer underrun
2009-05-24 23:27:38.356 NVP: prebuffering pause
2009-05-24 23:28:54.328 WriteAudio: buffer underrun
2009-05-24 23:28:54.332 NVP: prebuffering pause
2009-05-24 23:32:55.335 NVP: prebuffering pause
2009-05-24 23:32:55.335 WriteAudio: buffer underrun
2009-05-24 23:37:20.636 WriteAudio: buffer underrun
2009-05-24 23:37:22.485 NVP: prebuffering pause
2009-05-24 23:37:22.486 WriteAudio: buffer underrun
2009-05-24 23:40:06.250 NVP: prebuffering pause
2009-05-24 23:40:06.251 WriteAudio: buffer underrun
2009-05-24 23:43:11.518 WriteAudio: buffer underrun
2009-05-24 23:45:32.861 NVP: prebuffering pause
2009-05-24 23:45:32.865 WriteAudio: buffer underrun
2009-05-24 23:48:34.606 WriteAudio: buffer underrun
2009-05-24 23:48:39.621 WriteAudio: buffer underrun
2009-05-24 23:48:55.043 WriteAudio: buffer underrun
2009-05-24 23:48:55.767 NVP: prebuffering pause
2009-05-24 23:51:07.295 WriteAudio: buffer underrun
2009-05-24 23:51:10.498 WriteAudio: buffer underrun
2009-05-24 23:51:57.965 NVP: prebuffering pause
2009-05-24 23:51:57.967 WriteAudio: buffer underrun
2009-05-24 23:53:39.986 WriteAudio: buffer underrun
2009-05-24 23:53:57.335 WriteAudio: buffer underrun
2009-05-24 23:54:00.946 NVP: prebuffering pause
2009-05-24 23:54:26.454 NVP: prebuffering pause
2009-05-24 23:54:34.669 NVP: prebuffering pause

```

Sorry for the long post... I couldn't attach the files...

---

### Post by nickrout on 2009-05-25
Does this thread help?

[http://ubuntuforums.org/showthread.php?t=741408](http://ubuntuforums.org/showthread.php?t=741408)

(see the last post, he too is using an ATI card).

---

