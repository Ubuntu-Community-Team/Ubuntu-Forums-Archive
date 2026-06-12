---
title: "getting my usb wireless connector to work"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by jimi_hendrix on 2009-01-01
hi all so i have ndiswrapper installed and the gtk frontend but i cant get my wireless to work.  i have a Dynex wireless N adapter thingie...now i just need to install the driver...i found the one on the disk and installed it and it detected the hardware but then i mouse over to the internet thingie and theres no wireless thing no wlan0 just eth0 (wifi is my only internet option so...)

please help!

---

### Post by Noel96 on 2009-01-01
Hi,
I've just spent a day playing around trying to get a NetGrear wpn111 USB wireless connector to work. 

Probably the best place to start is to look in /etc/ndiswrapper and see if the .inf and .sys files you need to run the device are there. If you they are, you're probably on the way. One thing that I learned was that there are two things you need to keep in mind...

1. Don't have a wired connection going while you're trying to set up a wireless one.

2. When you've done all the ndiswrapper setting up, shutdown the computer (don't use restart). Now un-blug the device. By doing this, you ensure that it's properly off. UBUNTU doesn't seem to shutdown my USB wireless device properly and I assume it's the same for some others, too. Turn the computer back on and plug the device back in before Ubuntu starts loading.

The URL below is the procedure I followed and while it's not specific for your device, it might give you some ideas.

[http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111](http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111)

As I said, I know this is not specific for you, but it might give you some ideas.

---

### Post by jimi_hendrix on 2009-01-01
i see both an inf and sys in the folder...so i assume they are the correct ones...

any other file type (like .dll) i should need?

---

### Post by Noel96 on 2009-01-01
In my folder, I only have the inf, sys and another one (not dll) specific for the hardware. From what I've read about ndiswrapper, many programs only require the inf and sys.

Being pretty new to this myself, I'm not all that much help! Still, by replying, I'm keeping your thread up the top of the list :)

---

### Post by jimi_hendrix on 2009-01-01
lol...if this dies ill just post again...cause i cant use ubuntu without this

---

### Post by jimi_hendrix on 2009-01-01
desperate bump

---

### Post by balloooza on 2009-01-01
can you post the output of
```
lsusb
```
and
```
lspci
```

---

### Post by jimi_hendrix on 2009-01-01
here you go:

```

#lspci:

00:00.0 Host bridge: Intel Corporation QuickPath Architecture I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation QuickPath Interconnect Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation QuickPath Interconnect Routing and Protocol Layer Registers Port 0 (rev 12)
00:13.0 PIC: Intel Corporation QuickPath Architecture I/O Hub I/OxAPIC Interrupt Controller (rev 12)
00:14.0 PIC: Intel Corporation QuickPath Architecture I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation QuickPath Architecture I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation QuickPath Architecture I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation QuickPath Architecture I/O Hub Throttle Registers (rev 12)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
02:00.0 Communication controller: Agere Systems Device 0630 (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
05:00.1 Audio device: ATI Technologies Inc HD48x0 audio
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)

#lsusb:

Bus 008 Device 004: ID 050d:d321 Belkin Components 
Bus 008 Device 003: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bda:0152 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04eb:e030 Northstar Systems, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

---

### Post by balloooza on 2009-01-01
Is the usb pluged in, can you run
```
dmesg
```

---

### Post by Tim Sharitt on 2009-01-01
The only file you need to install with ndiswrapper is the inf file, but It probably need to be in the directory with the other driver files. 
```
ndiswrapper -i /directory_to_files/bcmwlhigh5.inf
```
If you have the driver installed on a windows partition, you can use the file in the installation directory.
If you still can't get anything, post the output of
```
ndiswrapper -l
```
to make sure the device is found by ndiswrapper.

---

### Post by jimi_hendrix on 2009-01-02
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=0a94061f-4b6f-4baf-ae3d-457db01b7775 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf790000 (usable)
[    0.000000]  BIOS-e820: 00000000bf790000 - 00000000bf79e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf79e000 - 00000000bf7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7d0000 - 00000000bf7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf7ec000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xbf790 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf790000 page 4k
[    0.000000] kernel direct mapping tables up to bf790000 @ 8000-d000
[    0.000000] last_map_addr: bf790000 end: bf790000
[    0.000000] RAMDISK: 377b2000 - 37fefc87
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FA3B0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BF790100, 0064 (r1 ACRSYS ACRPRDCT 20080927 MSFT       97)
[    0.000000] ACPI: FACP BF790290, 00F4 (r4 GATEWA FACP1520 20080927 MSFT       97)
[    0.000000] ACPI: DSDT BF7905F0, 6EBC (r2  842P0 842P091G        4 INTL 20051117)
[    0.000000] ACPI: FACS BF79E000, 0040
[    0.000000] ACPI: APIC BF790390, 0098 (r2 GATEWA APIC1520 20080927 MSFT       97)
[    0.000000] ACPI: MCFG BF790430, 003C (r1 GATEWA OEMMCFG  20080927 MSFT       97)
[    0.000000] ACPI: SLIC BF790470, 0176 (r1 ACRSYS ACRPRDCT 20080927 MSFT       97)
[    0.000000] ACPI: OEMB BF79E040, 0072 (r1 GATEWA OEMB1520 20080927 MSFT       97)
[    0.000000] ACPI: DMAR BF79E0C0, 0138 (r1    AMI  OEMDMAR        1 MSFT       97)
[    0.000000] ACPI: AWMI BF79E200, 004E (r1 GATEWA OEMB1520 20080927 MSFT       97)
[    0.000000] ACPI: SSDT BF7A0880, 1298 (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bf790000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bf790000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  0000000000022ef7] pages 18
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bf790000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b2000 - 0037fefc87]          RAMDISK ==> [00377b2000 - 0037fefc87]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20002ffffff] PMD -> [ffff880001200000-ffff8800041fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bf790
[    0.000000] On node 0 totalpages: 784173
[    0.000000]   DMA zone: 2107 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 767985 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec8a000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 0, address 0xfec8a000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 770092
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=0a94061f-4b6f-4baf-ae3d-457db01b7775 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2666.255 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 3071476k/3137088k available (3112k kernel code, 65216k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5332.51 BogoMIPS (lpj=10665020)
[    0.004019] Security Framework initialized
[    0.004023] SELinux:  Disabled at boot.
[    0.004032] AppArmor: AppArmor initialized
[    0.004312] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005078] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.005393] Mount-cache hash table entries: 256
[    0.005490] Initializing cgroup subsys ns
[    0.005493] Initializing cgroup subsys cpuacct
[    0.005495] Initializing cgroup subsys memory
[    0.005505] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.005507] CPU: L2 cache: 256K
[    0.005508] CPU: L3 cache: 8192K
[    0.005510] CPU 0/0 -> Node 0
[    0.005511] CPU: Physical Processor ID: 0
[    0.005512] CPU: Processor Core ID: 0
[    0.005521] CPU0: Thermal monitoring enabled (TM1)
[    0.005523] using mwait in idle threads.
[    0.007021] ACPI: Core revision 20080609
[    0.008854] ACPI: Checking initramfs for custom DSDT
[    0.308174] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.349737] CPU0: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.349741] Using local APIC timer interrupts.
[    0.352022] APIC timer calibration result 8332070
[    0.352024] Detected 8.332 MHz APIC timer.
[    0.352125] Booting processor 1/2 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5332.38 BogoMIPS (lpj=10664774)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 1/2 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.440464] CPU1: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.440483] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.444101] Booting processor 2/4 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 5332.38 BogoMIPS (lpj=10664772)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 2/4 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU2: Thermal monitoring enabled (TM1)
[    0.532531] CPU2: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.532550] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.536107] Booting processor 3/6 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 5332.37 BogoMIPS (lpj=10664759)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 3/6 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU3: Thermal monitoring enabled (TM1)
[    0.624474] CPU3: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.624493] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.628105] Booting processor 4/1 ip 6000
[    0.004000] Initializing CPU#4
[    0.004000] Calibrating delay using timer specific routine.. 5332.38 BogoMIPS (lpj=10664760)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 4/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU4: Thermal monitoring enabled (TM1)
[    0.716543] CPU4: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.716567] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[    0.720111] Booting processor 5/3 ip 6000
[    0.004000] Initializing CPU#5
[    0.004000] Calibrating delay using timer specific routine.. 5332.38 BogoMIPS (lpj=10664775)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 5/3 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU5: Thermal monitoring enabled (TM1)
[    0.808595] CPU5: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.808614] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[    0.812106] Booting processor 6/5 ip 6000
[    0.004000] Initializing CPU#6
[    0.004000] Calibrating delay using timer specific routine.. 5332.38 BogoMIPS (lpj=10664766)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 6/5 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU6: Thermal monitoring enabled (TM1)
[    0.900636] CPU6: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.900655] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[    0.904106] Booting processor 7/7 ip 6000
[    0.004000] Initializing CPU#7
[    0.004000] Calibrating delay using timer specific routine.. 5165.79 BogoMIPS (lpj=10331580)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU 7/7 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU7: Thermal monitoring enabled (TM1)
[    0.992555] CPU7: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.992574] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[    0.996054] Brought up 8 CPUs
[    0.996056] Total of 8 processors activated (42492.60 BogoMIPS).
[    0.996102] CPU0 attaching sched-domain:
[    0.996103]  domain 0: span 0-7 level MC
[    0.996105]   groups: 0 1 2 3 4 5 6 7
[    0.996109]   domain 1: span 0-7 level NODE
[    0.996111]    groups: 0-7
[    0.996114] CPU1 attaching sched-domain:
[    0.996115]  domain 0: span 0-7 level MC
[    0.996116]   groups: 1 2 3 4 5 6 7 0
[    0.996120]   domain 1: span 0-7 level NODE
[    0.996121]    groups: 0-7
[    0.996123] CPU2 attaching sched-domain:
[    0.996124]  domain 0: span 0-7 level MC
[    0.996125]   groups: 2 3 4 5 6 7 0 1
[    0.996129]   domain 1: span 0-7 level NODE
[    0.996130]    groups: 0-7
[    0.996132] CPU3 attaching sched-domain:
[    0.996133]  domain 0: span 0-7 level MC
[    0.996134]   groups: 3 4 5 6 7 0 1 2
[    0.996138]   domain 1: span 0-7 level NODE
[    0.996139]    groups: 0-7
[    0.996141] CPU4 attaching sched-domain:
[    0.996142]  domain 0: span 0-7 level MC
[    0.996143]   groups: 4 5 6 7 0 1 2 3
[    0.996147]   domain 1: span 0-7 level NODE
[    0.996148]    groups: 0-7
[    0.996150] CPU5 attaching sched-domain:
[    0.996151]  domain 0: span 0-7 level MC
[    0.996152]   groups: 5 6 7 0 1 2 3 4
[    0.996156]   domain 1: span 0-7 level NODE
[    0.996157]    groups: 0-7
[    0.996159] CPU6 attaching sched-domain:
[    0.996160]  domain 0: span 0-7 level MC
[    0.996162]   groups: 6 7 0 1 2 3 4 5
[    0.996165]   domain 1: span 0-7 level NODE
[    0.996166]    groups: 0-7
[    0.996168] CPU7 attaching sched-domain:
[    0.996169]  domain 0: span 0-7 level MC
[    0.996171]   groups: 7 0 1 2 3 4 5 6
[    0.996174]   domain 1: span 0-7 level NODE
[    0.996176]    groups: 0-7
[    0.996296] net_namespace: 1552 bytes
[    0.996296] Booting paravirtualized kernel on bare hardware
[    0.996296] Time: 16:32:17  Date: 01/01/09
[    0.996296] NET: Registered protocol family 16
[    0.996296] ACPI: bus type pci registered
[    0.996296] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.996296] PCI: Not using MMCONFIG.
[    0.996296] PCI: Using configuration type 1 for base access
[    0.996699] ACPI: EC: Look up EC in DSDT
[    1.009919] ACPI: Interpreter enabled
[    1.009920] ACPI: (supports S0 S1 S3 S4 S5)
[    1.009933] ACPI: Using IOAPIC for interrupt routing
[    1.009992] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.016506] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    1.023157] PCI: Using MMCONFIG at e0000000 - efffffff
[    1.032363] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.032363] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.032363] pci 0000:00:01.0: PME# disabled
[    1.032363] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.032363] pci 0000:00:03.0: PME# disabled
[    1.032363] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.032363] pci 0000:00:07.0: PME# disabled
[    1.032363] PCI: 0000:00:13.0 reg 10 32bit mmio: [fec8a000, fec8afff]
[    1.032363] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
[    1.032363] pci 0000:00:13.0: PME# disabled
[    1.032497] PCI: 0000:00:19.0 reg 10 32bit mmio: [fbac0000, fbadffff]
[    1.032502] PCI: 0000:00:19.0 reg 14 32bit mmio: [fbaf2000, fbaf2fff]
[    1.032507] PCI: 0000:00:19.0 reg 18 io port: [a080, a09f]
[    1.032535] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    1.032538] pci 0000:00:19.0: PME# disabled
[    1.032576] PCI: 0000:00:1a.0 reg 20 io port: [a400, a41f]
[    1.032630] PCI: 0000:00:1a.1 reg 20 io port: [a480, a49f]
[    1.032684] PCI: 0000:00:1a.2 reg 20 io port: [a800, a81f]
[    1.032741] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fbaf8000, fbaf83ff]
[    1.032783] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.032786] pci 0000:00:1a.7: PME# disabled
[    1.032813] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fbaf4000, fbaf7fff]
[    1.032844] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.032847] pci 0000:00:1b.0: PME# disabled
[    1.032887] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.032890] pci 0000:00:1c.0: PME# disabled
[    1.032932] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.032935] pci 0000:00:1c.4: PME# disabled
[    1.032974] PCI: 0000:00:1d.0 reg 20 io port: [a880, a89f]
[    1.033027] PCI: 0000:00:1d.1 reg 20 io port: [ac00, ac1f]
[    1.033081] PCI: 0000:00:1d.2 reg 20 io port: [b000, b01f]
[    1.033138] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fbafa000, fbafa3ff]
[    1.033180] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.033183] pci 0000:00:1d.7: PME# disabled
[    1.033316] PCI: 0000:00:1f.2 reg 10 io port: [b880, b887]
[    1.033321] PCI: 0000:00:1f.2 reg 14 io port: [b800, b803]
[    1.033325] PCI: 0000:00:1f.2 reg 18 io port: [b480, b487]
[    1.033329] PCI: 0000:00:1f.2 reg 1c io port: [b400, b403]
[    1.033334] PCI: 0000:00:1f.2 reg 20 io port: [b080, b09f]
[    1.033338] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fbafc000, fbafc7ff]
[    1.033358] pci 0000:00:1f.2: PME# supported from D3hot
[    1.033361] pci 0000:00:1f.2: PME# disabled
[    1.033376] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fbaffc00, fbaffcff]
[    1.033387] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    1.033468] PCI: 0000:06:00.0 reg 24 32bit mmio: [fbefe000, fbefffff]
[    1.033490] pci 0000:06:00.0: PME# supported from D3hot
[    1.033494] pci 0000:06:00.0: PME# disabled
[    1.033524] PCI: 0000:06:00.1 reg 10 io port: [ec00, ec07]
[    1.033530] PCI: 0000:06:00.1 reg 14 io port: [e880, e883]
[    1.033536] PCI: 0000:06:00.1 reg 18 io port: [e800, e807]
[    1.033542] PCI: 0000:06:00.1 reg 1c io port: [e480, e483]
[    1.033549] PCI: 0000:06:00.1 reg 20 io port: [e400, e40f]
[    1.033597] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    1.033600] PCI: bridge 0000:00:01.0 32bit mmio: [fbe00000, fbefffff]
[    1.033627] PCI: 0000:05:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    1.033637] PCI: 0000:05:00.0 reg 18 64bit mmio: [fbde0000, fbdeffff]
[    1.033641] PCI: 0000:05:00.0 reg 20 io port: [d000, d0ff]
[    1.033649] PCI: 0000:05:00.0 reg 30 32bit mmio: [fbdc0000, fbddffff]
[    1.033661] pci 0000:05:00.0: supports D1
[    1.033662] pci 0000:05:00.0: supports D2
[    1.033683] PCI: 0000:05:00.1 reg 10 64bit mmio: [fbdfc000, fbdfffff]
[    1.033711] pci 0000:05:00.1: supports D1
[    1.033712] pci 0000:05:00.1: supports D2
[    1.033732] PCI: bridge 0000:00:03.0 io port: [d000, dfff]
[    1.033735] PCI: bridge 0000:00:03.0 32bit mmio: [fbd00000, fbdfffff]
[    1.033739] PCI: bridge 0000:00:03.0 64bit mmio pref: [d0000000, dfffffff]
[    1.033844] PCI: 0000:02:00.0 reg 10 64bit mmio: [fbcff000, fbcfffff]
[    1.033892] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    1.033896] pci 0000:02:00.0: PME# disabled
[    1.033925] PCI: bridge 0000:00:1c.4 32bit mmio: [fbc00000, fbcfffff]
[    1.033965] PCI: 0000:01:06.0 reg 10 32bit mmio: [fbbff800, fbbfffff]
[    1.033971] PCI: 0000:01:06.0 reg 14 io port: [cc00, cc7f]
[    1.034006] pci 0000:01:06.0: supports D2
[    1.034007] pci 0000:01:06.0: PME# supported from D2 D3hot D3cold
[    1.034011] pci 0000:01:06.0: PME# disabled
[    1.034040] pci 0000:00:1e.0: transparent bridge
[    1.034042] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    1.034045] PCI: bridge 0000:00:1e.0 32bit mmio: [fbb00000, fbbfffff]
[    1.034074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.036169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    1.036280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    1.036390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    1.036499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.036637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.036748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.064722] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.064722] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    1.064722] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.064722] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.064722] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *6 7 10 11 12 14 15)
[    1.064824] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.064960] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.065095] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.065153] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - CA, should be C9 [20080609]
[    1.065153] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.065153] pnp: PnP ACPI init
[    1.065153] ACPI: bus type pnp registered
[    1.068956] pnp: PnP ACPI: found 13 devices
[    1.068956] ACPI: ACPI bus type pnp unregistered
[    1.068956] PCI: Using ACPI for IRQ routing
[    1.088041] NET: Registered protocol family 8
[    1.088043] NET: Registered protocol family 20
[    1.088056] NetLabel: Initializing
[    1.088056] NetLabel:  domain hash size = 128
[    1.088056] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.088056] NetLabel:  unlabeled traffic allowed by default
[    1.088073] PCI-GART: No AMD northbridge found.
[    1.091112] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    1.091113]    actual entries 65586
[    1.091156] AppArmor: AppArmor Filesystem Enabled
[    1.091172] ACPI: RTC can wake from S4
[    1.104055] system 00:01: iomem range 0xfbf00000-0xfbffffff has been reserved
[    1.104058] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    1.104061] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    1.104064] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    1.104072] system 00:07: ioport range 0xa00-0xa0f has been reserved
[    1.104075] system 00:07: ioport range 0xa10-0xa1f has been reserved
[    1.104077] system 00:07: ioport range 0xa20-0xa2f has been reserved
[    1.104080] system 00:07: ioport range 0xa30-0xa3f has been reserved
[    1.104085] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.104088] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.104091] system 00:08: ioport range 0x480-0x4bf has been reserved
[    1.104094] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.104096] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.104099] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    1.104104] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.104107] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.104115] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    1.104118] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.104119] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    1.104121] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.104123] system 00:0c: iomem range 0x100000-0xbfffffff could not be reserved
[    1.104124] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
[    1.108951] pci 0000:00:01.0: PCI bridge, secondary bus 0000:06
[    1.108953] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    1.108956] pci 0000:00:01.0:   MEM window: 0xfbe00000-0xfbefffff
[    1.108959] pci 0000:00:01.0:   PREFETCH window: disabled
[    1.108963] pci 0000:00:03.0: PCI bridge, secondary bus 0000:05
[    1.108965] pci 0000:00:03.0:   IO window: 0xd000-0xdfff
[    1.108968] pci 0000:00:03.0:   MEM window: 0xfbd00000-0xfbdfffff
[    1.108971] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.108975] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
[    1.108976] pci 0000:00:07.0:   IO window: disabled
[    1.108979] pci 0000:00:07.0:   MEM window: disabled
[    1.108982] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.108986] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    1.108987] pci 0000:00:1c.0:   IO window: disabled
[    1.108990] pci 0000:00:1c.0:   MEM window: disabled
[    1.108993] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.108997] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    1.108998] pci 0000:00:1c.4:   IO window: disabled
[    1.109002] pci 0000:00:1c.4:   MEM window: 0xfbc00000-0xfbcfffff
[    1.109005] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.109009] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.109011] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    1.109015] pci 0000:00:1e.0:   MEM window: 0xfbb00000-0xfbbfffff
[    1.109018] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.109027] pci 0000:00:01.0: setting latency timer to 64
[    1.109033] pci 0000:00:03.0: setting latency timer to 64
[    1.109039] pci 0000:00:07.0: setting latency timer to 64
[    1.109047] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.109050] pci 0000:00:1c.0: setting latency timer to 64
[    1.109055] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.109058] pci 0000:00:1c.4: setting latency timer to 64
[    1.109063] pci 0000:00:1e.0: setting latency timer to 64
[    1.109065] bus: 00 index 0 io port: [0, ffff]
[    1.109066] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    1.109068] bus: 06 index 0 io port: [e000, efff]
[    1.109069] bus: 06 index 1 mmio: [fbe00000, fbefffff]
[    1.109070] bus: 06 index 2 mmio: [0, 0]
[    1.109071] bus: 06 index 3 mmio: [0, 0]
[    1.109072] bus: 05 index 0 io port: [d000, dfff]
[    1.109073] bus: 05 index 1 mmio: [fbd00000, fbdfffff]
[    1.109074] bus: 05 index 2 mmio: [d0000000, dfffffff]
[    1.109075] bus: 05 index 3 mmio: [0, 0]
[    1.109076] bus: 04 index 0 mmio: [0, 0]
[    1.109077] bus: 04 index 1 mmio: [0, 0]
[    1.109078] bus: 04 index 2 mmio: [0, 0]
[    1.109079] bus: 04 index 3 mmio: [0, 0]
[    1.109080] bus: 03 index 0 mmio: [0, 0]
[    1.109081] bus: 03 index 1 mmio: [0, 0]
[    1.109082] bus: 03 index 2 mmio: [0, 0]
[    1.109083] bus: 03 index 3 mmio: [0, 0]
[    1.109084] bus: 02 index 0 mmio: [0, 0]
[    1.109085] bus: 02 index 1 mmio: [fbc00000, fbcfffff]
[    1.109086] bus: 02 index 2 mmio: [0, 0]
[    1.109087] bus: 02 index 3 mmio: [0, 0]
[    1.109088] bus: 01 index 0 io port: [c000, cfff]
[    1.109089] bus: 01 index 1 mmio: [fbb00000, fbbfffff]
[    1.109090] bus: 01 index 2 mmio: [0, 0]
[    1.109091] bus: 01 index 3 io port: [0, ffff]
[    1.109092] bus: 01 index 4 mmio: [0, ffffffffffffffff]
[    1.109099] NET: Registered protocol family 2
[    1.152176] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.152922] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.154076] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.154220] TCP: Hash tables configured (established 524288 bind 65536)
[    1.154222] TCP reno registered
[    1.164161] NET: Registered protocol family 1
[    1.164235] checking if image is initramfs... it is
[    1.608519] Switched to high resolution mode on CPU 1
[    1.608521] Switched to high resolution mode on CPU 3
[    1.608577] Switched to high resolution mode on CPU 2
[    1.608600] Switched to high resolution mode on CPU 4
[    1.608602] Switched to high resolution mode on CPU 7
[    1.608641] Switched to high resolution mode on CPU 5
[    1.608683] Switched to high resolution mode on CPU 6
[    1.612041] Switched to high resolution mode on CPU 0
[    1.755082] Freeing initrd memory: 8439k freed
[    1.757850] audit: initializing netlink socket (disabled)
[    1.757864] type=2000 audit(1230827536.756:1): initialized
[    1.762515] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.764081] VFS: Disk quotas dquot_6.5.1
[    1.764133] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.764192] msgmni has been set to 6015
[    1.764265] io scheduler noop registered
[    1.764267] io scheduler anticipatory registered
[    1.764268] io scheduler deadline registered
[    1.764337] io scheduler cfq registered (default)
[    1.764461] pci 0000:05:00.0: Boot video device
[    1.764538] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.764570] pcieport-driver 0000:00:01.0: found MSI capability
[    1.764596] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.764621] pci_express 0000:00:01.0:pcie01: allocate port service
[    1.764688] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.764719] pcieport-driver 0000:00:03.0: found MSI capability
[    1.764743] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.764766] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.764832] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.764863] pcieport-driver 0000:00:07.0: found MSI capability
[    1.764887] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.764911] pci_express 0000:00:07.0:pcie01: allocate port service
[    1.764977] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.765004] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.765031] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.765053] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.765075] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.765137] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.765164] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.765192] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.765218] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.765241] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.765343] aer 0000:00:01.0:pcie01: AER service couldn't init device: no _OSC support
[    1.765355] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.765366] aer 0000:00:07.0:pcie01: AER service couldn't init device: no _OSC support
[    1.784807] Linux agpgart interface v0.103
[    1.784810] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.784914] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.785308] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.786296] brd: module loaded
[    1.786337] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.786398] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.786399] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.786474] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.801861] mice: PS/2 mouse device common for all mice
[    1.801927] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.801947] rtc0: alarms up to one month, y3k
[    1.801972] cpuidle: using governor ladder
[    1.801973] cpuidle: using governor menu
[    1.802232] TCP cubic registered
[    1.802345] registered taskstats version 1
[    1.802451]   Magic number: 9:217:539
[    1.802507] rtc_cmos 00:03: setting system clock to 2009-01-01 16:32:17 UTC (1230827537)
[    1.802509] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.802511] EDD information not available.
[    1.802536] Freeing unused kernel memory: 536k freed
[    1.802621] Write protecting the kernel read-only data: 4348k
[    1.824450] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.867728] fuse init (API version 7.9)
[    1.881146] ACPI: SSDT BF79E250, 03C1 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.881489] ACPI: SSDT BF7A00D0, 03B2 (r1  PmRef  P001Cst     3001 INTL 20051117)
[    1.883941] Monitor-Mwait will be used to enter C-1 state
[    1.883943] Monitor-Mwait will be used to enter C-2 state
[    1.883945] Monitor-Mwait will be used to enter C-3 state
[    1.884120] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.884163] processor ACPI0007:00: registered as cooling_device0
[    1.884513] ACPI: SSDT BF79E620, 03C1 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.884793] ACPI: SSDT BF7A0490, 0085 (r1  PmRef  P002Cst     3000 INTL 20051117)
[    1.887409] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.887454] processor ACPI0007:01: registered as cooling_device1
[    1.887813] ACPI: SSDT BF79E9F0, 03C1 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[    1.888010] Marking TSC unstable due to TSC halts in idle
[    1.888098] ACPI: SSDT BF7A0520, 0085 (r1  PmRef  P003Cst     3000 INTL 20051117)
[    1.890809] ACPI: CPU2 (power states: C1[C1] C2[C2] C3[C3])
[    1.890877] processor ACPI0007:02: registered as cooling_device2
[    1.891302] ACPI: SSDT BF79EDC0, 03C1 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[    1.891668] ACPI: SSDT BF7A05B0, 0085 (r1  PmRef  P004Cst     3000 INTL 20051117)
[    1.894484] ACPI: CPU3 (power states: C1[C1] C2[C2] C3[C3])
[    1.894540] processor ACPI0007:03: registered as cooling_device3
[    1.894912] ACPI: SSDT BF79F190, 03C1 (r1 DpgPmm  P005Ist       12 INTL 20051117)
[    1.895218] ACPI: SSDT BF7A0640, 0085 (r1  PmRef  P005Cst     3000 INTL 20051117)
[    1.897990] ACPI: CPU4 (power states: C1[C1] C2[C2] C3[C3])
[    1.898048] processor ACPI0007:04: registered as cooling_device4
[    1.898416] ACPI: SSDT BF79F560, 03C1 (r1 DpgPmm  P006Ist       12 INTL 20051117)
[    1.898729] ACPI: SSDT BF7A06D0, 0085 (r1  PmRef  P006Cst     3000 INTL 20051117)
[    1.901493] ACPI: CPU5 (power states: C1[C1] C2[C2] C3[C3])
[    1.901562] processor ACPI0007:05: registered as cooling_device5
[    1.901938] ACPI: SSDT BF79F930, 03C1 (r1 DpgPmm  P007Ist       12 INTL 20051117)
[    1.902252] ACPI: SSDT BF7A0760, 0085 (r1  PmRef  P007Cst     3000 INTL 20051117)
[    1.907873] ACPI: CPU6 (power states: C1[C1] C2[C2] C3[C3])
[    1.907942] processor ACPI0007:06: registered as cooling_device6
[    1.908349] ACPI: SSDT BF79FD00, 03C1 (r1 DpgPmm  P008Ist       12 INTL 20051117)
[    1.908696] ACPI: SSDT BF7A07F0, 0085 (r1  PmRef  P008Cst     3000 INTL 20051117)
[    1.911447] ACPI: CPU7 (power states: C1[C1] C2[C2] C3[C3])
[    1.911505] processor ACPI0007:07: registered as cooling_device7
[    1.913763] thermal LNXTHERM:01: registered as thermal_zone0
[    1.914132] ACPI: Thermal Zone [THRM] (23 C)
[    2.014331] No dock devices found.
[    2.025928] SCSI subsystem initialized
[    2.037824] libata version 3.00 loaded.
[    2.046262] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.046264] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.046307] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.046314] e1000e 0000:00:19.0: setting latency timer to 64
[    2.056285] usbcore: registered new interface driver usbfs
[    2.056303] usbcore: registered new interface driver hub
[    2.056354] usbcore: registered new device driver usb
[    2.071430] USB Universal Host Controller Interface driver v3.0
[    2.134966] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:22:68:07:5e:f7
[    2.134969] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.134996] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: ffffff-0ff
[    2.137094] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.137102] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.137105] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.137138] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.137166] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a400
[    2.137252] usb usb1: configuration #1 chosen from 1 choice
[    2.137270] hub 1-0:1.0: USB hub found
[    2.137274] hub 1-0:1.0: 2 ports detected
[    2.242022] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.242029] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.242032] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.242051] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.242079] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a480
[    2.242141] usb usb2: configuration #1 chosen from 1 choice
[    2.242158] hub 2-0:1.0: USB hub found
[    2.242162] hub 2-0:1.0: 2 ports detected
[    2.448503] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.448510] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.448513] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.448532] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.448560] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000a800
[    2.448618] usb usb3: configuration #1 chosen from 1 choice
[    2.448636] hub 3-0:1.0: USB hub found
[    2.448639] hub 3-0:1.0: 2 ports detected
[    2.560829] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.656589] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.656598] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.656601] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.656618] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.660525] ehci_hcd 0000:00:1a.7: debug port 1
[    2.660529] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.660539] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbaf8000
[    2.744085] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.744147] usb usb4: configuration #1 chosen from 1 choice
[    2.744177] hub 4-0:1.0: USB hub found
[    2.744183] hub 4-0:1.0: 6 ports detected
[    2.953056] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.953062] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.953064] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.953083] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.953109] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a880
[    2.953166] usb usb5: configuration #1 chosen from 1 choice
[    2.953183] hub 5-0:1.0: USB hub found
[    2.953186] hub 5-0:1.0: 2 ports detected
[    3.056431] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.056436] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.056438] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.056454] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.056473] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ac00
[    3.056558] usb usb6: configuration #1 chosen from 1 choice
[    3.056577] hub 6-0:1.0: USB hub found
[    3.056581] hub 6-0:1.0: 2 ports detected
[    3.140090] usb 2-1: device not accepting address 2, error -71
[    3.196114] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.264969] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.264974] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.264976] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.264998] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.265017] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b000
[    3.265074] usb usb7: configuration #1 chosen from 1 choice
[    3.265091] hub 7-0:1.0: USB hub found
[    3.265094] hub 7-0:1.0: 2 ports detected
[    3.436090] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    3.473149] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.473156] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.473158] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.473195] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.477087] ehci_hcd 0000:00:1d.7: debug port 1
[    3.477092] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.477096] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbafa000
[    3.560095] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.560189] usb usb8: configuration #1 chosen from 1 choice
[    3.560205] hub 8-0:1.0: USB hub found
[    3.560208] hub 8-0:1.0: 6 ports detected
[    3.571153] usb 4-3: config 1 interface 1 altsetting 0 endpoint 0x83 has an invalid bInterval 30, changing to 8
[    3.576371] usb 4-3: configuration #1 chosen from 1 choice
[    3.769466] ahci 0000:00:1f.2: version 3.0
[    3.769478] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.769575] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.769578] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    3.769581] ahci 0000:00:1f.2: setting latency timer to 64
[    3.769943] scsi0 : ahci
[    3.771054] scsi1 : ahci
[    3.772131] scsi2 : ahci
[    3.773383] scsi3 : ahci
[    3.774557] scsi4 : ahci
[    3.775781] scsi5 : ahci
[    3.775928] ata1: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc100 irq 2298
[    3.775930] ata2: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc180 irq 2298
[    3.775932] ata3: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc200 irq 2298
[    3.775934] ata4: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc280 irq 2298
[    3.775936] ata5: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc300 irq 2298
[    3.775938] ata6: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc380 irq 2298
[    4.092096] ata1: SATA link down (SStatus 0 SControl 300)
[    4.256089] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.428071] ata2: SATA link down (SStatus 0 SControl 300)
[    4.435756] usb 3-1: configuration #1 chosen from 1 choice
[    4.604085] usb 8-5: new high speed USB device using ehci_hcd and address 3
[    4.745553] usb 8-5: configuration #1 chosen from 1 choice
[    4.764072] ata3: SATA link down (SStatus 0 SControl 300)
[    4.856094] usb 8-6: new high speed USB device using ehci_hcd and address 4
[    4.992136] usb 8-6: configuration #1 chosen from 1 choice
[    5.100822] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.103835] ata4.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[    5.107671] ata4.00: configured for UDMA/100
[    5.232093] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    5.401296] usb 6-1: configuration #1 chosen from 1 choice
[    5.440074] ata5: SATA link down (SStatus 0 SControl 300)
[    5.776072] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.777606] ata6.00: ATA-8: ST3750630AS, SD46, max UDMA/133
[    5.777609] ata6.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.779542] ata6.00: configured for UDMA/133
[    5.795603] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
[    5.797589] scsi 5:0:0:0: Direct-Access     ATA      ST3750630AS      SD46 PQ: 0 ANSI: 5
[    5.797871] ahci 0000:06:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    5.812607] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    5.812611] ahci 0000:06:00.0: flags: 64bit ncq led clo pmp pio 
[    5.812616] ahci 0000:06:00.0: setting latency timer to 64
[    5.812777] scsi6 : ahci
[    5.814185] scsi7 : ahci
[    5.814237] ata7: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 28
[    5.814240] ata8: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 28
[    6.132079] ata7: SATA link down (SStatus 0 SControl 300)
[    6.452077] ata8: SATA link down (SStatus 0 SControl 300)
[    6.452340] pata_jmicron 0000:06:00.1: enabling device (0000 -> 0001)
[    6.452352] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 40 (level, low) -> IRQ 40
[    6.452379] pata_jmicron 0000:06:00.1: setting latency timer to 64
[    6.455652] scsi8 : pata_jmicron
[    6.457850] scsi9 : pata_jmicron
[    6.457891] ata9: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 40
[    6.457894] ata10: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 40
[    6.459576] scsi 3:0:0:0: Attached scsi generic sg0 type 5
[    6.459605] scsi 5:0:0:0: Attached scsi generic sg1 type 0
[    6.473160] Driver 'sr' needs updating - please use bus_type methods
[    6.476406] Driver 'sd' needs updating - please use bus_type methods
[    6.481159] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.481163] Uniform CD-ROM driver Revision: 3.20
[    6.482524] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    6.482610] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    6.482628] sd 5:0:0:0: [sda] Write Protect is off
[    6.482630] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.482660] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.482716] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    6.482733] sd 5:0:0:0: [sda] Write Protect is off
[    6.482734] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.482764] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.482766]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    6.553562] sd 5:0:0:0: [sda] Attached SCSI disk
[    6.779498] ohci1394 0000:01:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.832165] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbbff800-fbbfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.844596] usbcore: registered new interface driver hiddev
[    8.109633] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20009104eb]
[   16.844215] usbhid: timeout initializing reports
[   16.844364] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:1a.7-3
[   16.875156] input: Device Media Center Interface as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input2
[   16.884426] input,hiddev97,hidraw1: USB HID v1.10 Keyboard [Device Media Center Interface] on usb-0000:00:1a.2-1
[   16.899174] hiddev98hidraw2: USB HID v1.10 Device [Device Media Center Interface] on usb-0000:00:1a.2-1
[   16.913164] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input3
[   16.936410] input,hidraw3: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1
[   16.937260] usbcore: registered new interface driver usbhid
[   16.937263] usbhid: v2.6:USB HID core driver
[   16.937332] usbcore: registered new interface driver libusual
[   16.941780] Initializing USB Mass Storage driver...
[   16.941879] scsi10 : SCSI emulation for USB Mass Storage devices
[   16.941961] usb-storage: device found at 2
[   16.941963] usb-storage: waiting for device to settle before scanning
[   16.942042] scsi11 : SCSI emulation for USB Mass Storage devices
[   16.942106] usb-storage: device found at 3
[   16.942107] usb-storage: waiting for device to settle before scanning
[   16.942117] usbcore: registered new interface driver usb-storage
[   16.942119] USB Mass Storage support registered.
[   16.988863] PM: Starting manual resume from disk
[   16.988865] PM: Resume from partition 8:6
[   16.988866] PM: Checking hibernation image.
[   16.989188] PM: Resume from disk failed.
[   17.033710] kjournald starting.  Commit interval 5 seconds
[   17.033726] EXT3-fs: mounted filesystem with ordered data mode.
[   21.941562] usb-storage: device scan complete
[   21.941580] usb-storage: device scan complete
[   21.941597] isa bounce pool size: 16 pages
[   21.942623] scsi 11:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   21.944079] scsi 10:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   21.946540] scsi 10:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   21.949079] scsi 10:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   21.951665] scsi 10:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   21.953464] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[   21.953534] sd 10:0:0:0: Attached scsi generic sg2 type 0
[   21.954413] sd 10:0:0:1: [sdc] Attached SCSI removable disk
[   21.954449] sd 10:0:0:1: Attached scsi generic sg3 type 0
[   21.955435] sd 10:0:0:2: [sdd] Attached SCSI removable disk
[   21.955471] sd 10:0:0:2: Attached scsi generic sg4 type 0
[   21.956450] sd 10:0:0:3: [sde] Attached SCSI removable disk
[   21.956486] sd 10:0:0:3: Attached scsi generic sg5 type 0
[   21.957625] sd 11:0:0:0: [sdf] 15646720 512-byte hardware sectors (8011 MB)
[   21.958321] sd 11:0:0:0: [sdf] Write Protect is off
[   21.958323] sd 11:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   21.958324] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[   21.960102] sd 11:0:0:0: [sdf] 15646720 512-byte hardware sectors (8011 MB)
[   21.960696] sd 11:0:0:0: [sdf] Write Protect is off
[   21.960698] sd 11:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   21.960699] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[   21.960702]  sdf: sdf1
[   21.962476] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[   21.962517] sd 11:0:0:0: Attached scsi generic sg6 type 0
[   22.071596] udevd version 124 started
[   22.285324] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.317731] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.348396] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   22.373785] ACPI: Power Button (FF) [PWRF]
[   22.373881] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   22.405783] ACPI: Power Button (CM) [PWRB]
[   22.405901] ACPI: WMI: Mapper loaded
[   22.608428] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   22.658797] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   22.872579] usb 8-6: reset high speed USB device using ehci_hcd and address 4
[   22.897875] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.897899] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   22.966427] HDA Intel 0000:05:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
[   22.966451] HDA Intel 0000:05:00.1: setting latency timer to 64
[   23.359298] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   23.359304] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   23.359308] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   23.359312] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   23.359316] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   23.359322] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   23.359326] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   23.359330] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   23.359337] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   23.359341] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   23.359345] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   23.359350] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   23.359355] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   23.359360] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   23.359364] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   23.359368] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   23.359373] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   23.359378] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   23.359382] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   23.359386] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   23.359393] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   23.359402] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   23.359410] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   23.359413] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   23.359415] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[   23.359798] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[   23.359829] usbcore: registered new interface driver ndiswrapper
[   24.102031] lp: driver loaded but no devices found
[   24.247449] Adding 1004020k swap on /dev/sda6.  Priority:-1 extents:1 across:1004020k
[   24.801428] EXT3 FS on sda5, internal journal
[   25.707929] type=1505 audit(1230845561.777:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5307
[   25.798680] type=1505 audit(1230845561.869:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5312
[   25.798876] type=1505 audit(1230845561.869:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5312
[   25.950098] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.238339] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   27.389731] ppdev: user-space parallel port driver
[   29.006615] Bluetooth: Core ver 2.13
[   29.006933] NET: Registered protocol family 31
[   29.006936] Bluetooth: HCI device and connection manager initialized
[   29.006940] Bluetooth: HCI socket layer initialized
[   29.020195] Bluetooth: L2CAP ver 2.11
[   29.020202] Bluetooth: L2CAP socket layer initialized
[   29.045620] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.045627] Bluetooth: BNEP filters: protocol multicast
[   29.070192] Bridge firewalling registered
[   29.070460] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   29.079755] Bluetooth: SCO (Voice Link) ver 0.6
[   29.079762] Bluetooth: SCO socket layer initialized
[   29.136476] Bluetooth: RFCOMM socket layer initialized
[   29.136488] Bluetooth: RFCOMM TTY layer initialized
[   29.136492] Bluetooth: RFCOMM ver 1.10
[   30.932196] pci 0000:05:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[  351.380815] UDF-fs: No VRS found
[  351.395560] ISO 9660 Extensions: Microsoft Joliet Level 3
[  351.396960] ISOFS: changing to secondary root


```

dmesg ^^^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by jimi_hendrix on 2009-01-02
should i be installing the vista driver or the xp one?

---

### Post by jimi_hendrix on 2009-01-02
and in response to ndiswrapper -l:

bcmwlhigh5 : driver installed
             device (050D:D321) present

iwconfig still lists no wlan0

sorry for the triple post i just noticed i did

---

### Post by Tim Sharitt on 2009-01-03
Try removing all the files in /etc/ndiswrapper to make sure you've got the bcmwlhigh6 driver completely removed. That should leave ndiswrapper in a fairly clean state. To make sure you get eveything out it may be better to completely remove ndiswrapper and reinstall it.
```
sudo apt-get purge ndiswrapper
```
Note: where ndiswrapper is you may have to substitute ndiswrapper-util or whatever the package was called.

Then reinstall just the bcmwlhigh5.inf driver.
```
sudo ndiswrapper -i bcmwlhigh5.inf
sudo ndiswrapper -ma
```
That last line is what writes the alias configuration so that the installed device is given the alias wlan0.

---

### Post by jimi_hendrix on 2009-01-14
tried it...didnt work...still no wlan0 interface

---

### Post by Tim Sharitt on 2009-01-17
b43 firmware installation

First, download these files and transfer them to you linux box
```
http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2

```
```
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2

```
Place both tarballs in the same directory and do the following:
```

tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make

cd ..

tar xjf broadcom-wl-4.150.10.5.tar.bz2

cd broadcom-wl-4.150.10.5/driver

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

sudo rmmod ndiswrapper

sudo rmmod b43

sudo modprobe b43

```

If that works remove or blacklist ndiswrapper and make sure b43 is not blacklisted.

---

