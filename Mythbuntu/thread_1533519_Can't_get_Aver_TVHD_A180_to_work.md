---
title: "Can't get Aver TVHD A180 to work"
date: 2010-07-18
forum: Mythbuntu
---

### Post by geofffox on 2010-07-18
I am trying to get my Aver A180 to work with Mythbuntu 10.04.  The card is recognized as Air2PC.  When I scan there are signals, but no lock!

I've tried downloading get_tvb_firmware to extract the nxt2004 firmware, but get an error message:  

geoff@mythbox:~/Desktop$ ./get_dvb_firmware nxt2004
--2010-07-18 03:52:22--  [http://www.aver.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip](http://www.aver.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip)
Resolving [www.aver.com](www.aver.com)... 59.124.45.51
Connecting to [www.aver.com|59.124.45.51|:80](www.aver.com|59.124.45.51|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-18 03:52:28 ERROR 404: Not Found.


I'm not even sure this is what I should be doing!

Any help greatly appreciated.

---

### Post by kja999 on 2010-07-18
Hi,

Bit of reading for you :
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/508317](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/508317)
Shows the driver seems to be added to the firmware-nonfree package (some instructions to test there too)

Plus this link [http://www.gossamer-threads.com/lists/mythtv/users/385020](http://www.gossamer-threads.com/lists/mythtv/users/385020)
which has the link to a copy of the zip file..

Hope this helps

---

### Post by geofffox on 2010-07-19
Thanks.  I appreciate your effort.

I had seen both before.  Yes, I have downloaded and, seemingly, installed the firmware.  There's got to be something else?  Alas, most of these postings are almost complete.  There's usually a 'ya' know' step in there somewhere.

I will keep looking.  Someone has solved this problem.

---

### Post by klc5555 on 2010-07-19
> **geofffox said:**
> Thanks.  I appreciate your effort.

I had seen both before.  Yes, I have downloaded and, seemingly, installed the firmware.  There's got to be something else?  Alas, most of these postings are almost complete.  There's usually a 'ya' know' step in there somewhere.

I will keep looking.  Someone has solved this problem.

I assume this is a "new-style" A180, that has just the single output port for digital.

First you need to know if the firmware is loading. "dmesg | grep nxt" should provide you the answer to this question. If the firmware refuses to load, the problem is frequently some kind of I2c bus support problem. In my case, i2c support was built into my kernel --I had to recompile with i2c support in module form. But this was on a Slackware 2.6.27.7 kernel; Ubuntu I believe already gives you i2c support as a module. 

Assuming the firmware has loaded, the A180 has an additional problem that the onboard chipset is too cheap to properly identify the card and tuner to the driver at bootup. In my one machine that has this card, I have to blacklist the saa7134 module (which seems to cheerfully ignore .conf files and loads to its defaults) and then load the driver with the following modprobe command:

modprobe saa7134 card=75 tuner=68

I found that if the "card" param was omitted, the card could not find signals; if the "tuner" param was omitted, it found signals but couldn't lock.

You may be able to test this by unloading your saa7134 module and then modprobing it with the desired parameters.  

lsmod should show you that saa7134 and saa7134-dvb are both loaded. You may be able to, after stopping the mythtv backend, unload these as follows:

sudo rmmod saa7134-dvb
sudo rmmod saa7134

If this is successful, then reload the saa7134 mod with the above parameters.

sudo modprobe saa7134 card=75 tuner=68

The secondary module saa7134-dvb loads itself. Then give a channel scan a try.

Now by way of caveats, while I use my A180 card daily, my compiled drivers and firmware date to Feb. 09. There may have been enough developments in the driver over the subsequent year to render these techniques obsolete. Also, as is mentioned in the wiki article for the card, after enough driver and startup problems, the card gets stubborn and refuses to function properly until the machine has been shut down and "cold-started" after a 30-ish second delay --a warm reboot won't cut it. 

Good luck.

---

### Post by geofffox on 2010-07-20
I tried everything you said and it was exactly what you said it would be.  The card still doesn't work.  Oh well.

I am downloading MythDora which I believe works with this card out of the box.  I like Ubuntu, so I was hoping, but sometimes this stuff gets a little esoteric.

Thanks for all your help.

---

### Post by newlinux on 2010-07-20
I have the older A180 (I've had it since Ubuntu 6.10) and after placing the proper firmware in the /lib/firmware directory all I have to do is make sure the saa7134 and saa7134-dvb modules are loaded (no module options) and everything works (scanning, tuning, locking, recording). Never had any problems with it stopping working or not working after reboots. I have 3 other cards (Kworld ATSC 110s) that have the same chipset and use the same firmware and modules. 

Which A180 do you have, the older or newer one? Did you confirm the firmware was loading with the dmesg command posted earlier? I have most often seen this problem when firmware wasn't loaded.

---

### Post by Caysho on 2010-07-20
Air2PC is a TechniSat card.
A few searches show the AVerMedia card used to get incorrectly detected as Air2PC.

Post lspci and dmesg - worth checking to see if things are getting confused.

---

### Post by geofffox on 2010-07-21
No luck!  Reloaded Mythbuntu to make sure I hadn't introduced anything.

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffc0 max_arch_pfn = 0x100000
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
[    0.000000]  modified: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffc0000 (usable)
[    0.000000]  modified: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  modified: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37857000 - 37fef037
[    0.000000] Allocated new RAMDISK: 008de000 - 01076037
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef036 to 008de000 - 01076036
[    0.000000] ACPI: RSDP 000fb870 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7ffc0100 00044 (v01 A M I  OEMXSDT  01000617 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffc0290 000F4 (v03 A M I  OEMFACP  01000617 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffc0440 05691 (v01  A0368 A0368001 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 7ffce000 00040
[    0.000000] ACPI: APIC 7ffc0390 00070 (v01 A M I  OEMAPIC  01000617 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffc0400 0003C (v01 A M I  OEMMCFG  01000617 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffce040 0005B (v01 A M I  AMI_OEM  01000617 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd284]              BRK ==> [00008da000 - 00008dd284]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 0001076037]      NEW RAMDISK ==> [00008de000 - 0001076037]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffc0
[    0.000000] On node 0 totalpages: 524111
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1078200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294578 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
[    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520015
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=4238cabc-6e33-4424-a51d-0cc7afcb9668 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffc0)
[    0.000000] Memory: 2051992k/2096896k available (4673k kernel code, 43432k reserved, 2122k data, 656k init, 1187592k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2009.113 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4018.22 BogoMIPS (lpj=8036452)
[    0.008030] Security Framework initialized
[    0.008061] AppArmor: AppArmor initialized
[    0.008069] Mount-cache hash table entries: 512
[    0.008236] Initializing cgroup subsys ns
[    0.008241] Initializing cgroup subsys cpuacct
[    0.008245] Initializing cgroup subsys memory
[    0.008253] Initializing cgroup subsys devices
[    0.008257] Initializing cgroup subsys freezer
[    0.008259] Initializing cgroup subsys net_cls
[    0.008282] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008285] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008287] CPU: Physical Processor ID: 0
[    0.008289] CPU: Processor Core ID: 0
[    0.008294] mce: CPU supports 5 MCE banks
[    0.008317] Performance Events: AMD PMU driver.
[    0.008325] ... version:                0
[    0.008327] ... bit width:              48
[    0.008329] ... generic registers:      4
[    0.008331] ... value mask:             0000ffffffffffff
[    0.008333] ... max period:             00007fffffffffff
[    0.008335] ... fixed-purpose events:   0
[    0.008337] ... event mask:             000000000000000f
[    0.008342] Checking 'hlt' instruction... OK.
[    0.026545] ACPI: Core revision 20090903
[    0.035686] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.035694] ftrace: allocating 21771 entries in 43 pages
[    0.040129] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040664] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.082938] CPU0: AMD Athlon(tm)64 X2 Dual Core Processor  3800+ stepping 01
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.012000] Initializing CPU#1
[    0.012000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012000] CPU: Physical Processor ID: 0
[    0.012000] CPU: Processor Core ID: 1
[    0.168111] CPU1: AMD Athlon(tm)64 X2 Dual Core Processor  3800+ stepping 01
[    0.168143] Brought up 2 CPUs
[    0.168146] Total of 2 processors activated (8036.77 BogoMIPS).
[    0.168386] CPU0 attaching sched-domain:
[    0.168390]  domain 0: span 0-1 level MC
[    0.168393]   groups: 0 1
[    0.168400] CPU1 attaching sched-domain:
[    0.168402]  domain 0: span 0-1 level MC
[    0.168405]   groups: 1 0
[    0.168505] devtmpfs: initialized
[    0.168505] regulator: core version 0.5
[    0.168505] Time:  8:52:28  Date: 07/21/10
[    0.168505] NET: Registered protocol family 16
[    0.168505] EISA bus registered
[    0.168505] ACPI: bus type pci registered
[    0.168505] Trying to unpack rootfs image as initramfs...
[    0.168505] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168505] PCI: Not using MMCONFIG.
[    0.169246] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.169249] PCI: Using configuration type 1 for base access
[    0.172126] bio: create slab <bio-0> at 0
[    0.172900] ACPI: EC: Look up EC in DSDT
[    0.176620] ACPI: Executed 1 blocks of module-level executable AML code
[    0.181011] ACPI: Interpreter enabled
[    0.181019] ACPI: (supports S0 S1 S3 S4 S5)
[    0.181043] ACPI: Using IOAPIC for interrupt routing
[    0.181094] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.186354] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.186356] PCI: Using MMCONFIG for extended config space
[    0.194791] ACPI Warning: Incorrect checksum in table [OEMB] - FC, should be EF (20090903/tbutils-314)
[    0.194908] ACPI: No dock devices found.
[    0.195033] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.195314] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195318] pci 0000:00:02.0: PME# disabled
[    0.195358] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195361] pci 0000:00:03.0: PME# disabled
[    0.195400] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195403] pci 0000:00:04.0: PME# disabled
[    0.195601] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.195654] pci 0000:00:0a.1: reg 20 io port: [0x600-0x63f]
[    0.195661] pci 0000:00:0a.1: reg 24 io port: [0x700-0x73f]
[    0.195686] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.195692] pci 0000:00:0a.1: PME# disabled
[    0.195726] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfebde000-0xfebdefff]
[    0.195756] pci 0000:00:0b.0: supports D1 D2
[    0.195759] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195763] pci 0000:00:0b.0: PME# disabled
[    0.195791] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfebdfc00-0xfebdfcff]
[    0.195823] pci 0000:00:0b.1: supports D1 D2
[    0.195826] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195830] pci 0000:00:0b.1: PME# disabled
[    0.195870] pci 0000:00:0d.0: reg 20 io port: [0xffa0-0xffaf]
[    0.195914] pci 0000:00:0e.0: reg 10 io port: [0xe800-0xe807]
[    0.195920] pci 0000:00:0e.0: reg 14 io port: [0xe480-0xe483]
[    0.195925] pci 0000:00:0e.0: reg 18 io port: [0xe400-0xe407]
[    0.195931] pci 0000:00:0e.0: reg 1c io port: [0xe080-0xe083]
[    0.195937] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
[    0.195943] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfebff000-0xfebfffff]
[    0.195993] pci 0000:00:0f.0: reg 10 io port: [0xdc00-0xdc07]
[    0.196007] pci 0000:00:0f.0: reg 14 io port: [0xd880-0xd883]
[    0.196012] pci 0000:00:0f.0: reg 18 io port: [0xd800-0xd807]
[    0.196018] pci 0000:00:0f.0: reg 1c io port: [0xd480-0xd483]
[    0.196024] pci 0000:00:0f.0: reg 20 io port: [0xd400-0xd40f]
[    0.196029] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.196124] pci 0000:00:10.1: reg 10 32bit mmio: [0xfebd8000-0xfebdbfff]
[    0.196160] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.196165] pci 0000:00:10.1: PME# disabled
[    0.196201] pci 0000:00:14.0: reg 10 32bit mmio: [0xfebd7000-0xfebd7fff]
[    0.196207] pci 0000:00:14.0: reg 14 io port: [0xd080-0xd087]
[    0.196231] pci 0000:00:14.0: supports D1 D2
[    0.196234] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196238] pci 0000:00:14.0: PME# disabled
[    0.196429] pci 0000:03:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.196438] pci 0000:03:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.196447] pci 0000:03:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.196453] pci 0000:03:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.196459] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xfe9e0000-0xfe9fffff]
[    0.196520] pci 0000:00:04.0: bridge io port: [0xb000-0xbfff]
[    0.196524] pci 0000:00:04.0: bridge 32bit mmio: [0xf8900000-0xfe9fffff]
[    0.196529] pci 0000:00:04.0: bridge 64bit mmio pref: [0xb7f00000-0xd7efffff]
[    0.196566] pci 0000:04:05.0: reg 10 32bit mmio: [0xfeaff800-0xfeafffff]
[    0.196573] pci 0000:04:05.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.196609] pci 0000:04:05.0: supports D2
[    0.196612] pci 0000:04:05.0: PME# supported from D2 D3hot D3cold
[    0.196616] pci 0000:04:05.0: PME# disabled
[    0.196648] pci 0000:04:08.0: reg 10 32bit mmio: [0xfeaff000-0xfeaff7ff]
[    0.196687] pci 0000:04:08.0: supports D1 D2
[    0.196720] pci 0000:04:09.0: reg 10 32bit mmio pref: [0xd8000000-0xdbffffff]
[    0.196787] pci 0000:00:10.0: transparent bridge
[    0.196791] pci 0000:00:10.0: bridge io port: [0xc000-0xcfff]
[    0.196795] pci 0000:00:10.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.196799] pci 0000:00:10.0: bridge 32bit mmio pref: [0xd7f00000-0xdfefffff]
[    0.196811] pci_bus 0000:00: on NUMA node 0
[    0.196816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.197023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
[    0.197085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
[    0.197146] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.197237] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.208790] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *5
[    0.209028] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *5
[    0.209275] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.209508] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *5
[    0.210088] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *11
[    0.210323] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.210555] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.210795] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.211037] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.211273] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[    0.211507] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.211743] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.211979] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.212246] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.212479] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    0.212719] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.212951] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    0.213184] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.213464] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.213611] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.213616] vgaarb: loaded
[    0.213771] SCSI subsystem initialized
[    0.213902] libata version 3.00 loaded.
[    0.213979] usbcore: registered new interface driver usbfs
[    0.213993] usbcore: registered new interface driver hub
[    0.214020] usbcore: registered new device driver usb
[    0.214172] ACPI: WMI: Mapper loaded
[    0.214174] PCI: Using ACPI for IRQ routing
[    0.214375] NetLabel: Initializing
[    0.214377] NetLabel:  domain hash size = 128
[    0.214379] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.214395] NetLabel:  unlabeled traffic allowed by default
[    0.216646] AppArmor: AppArmor Filesystem Enabled
[    0.216671] pnp: PnP ACPI init
[    0.216690] ACPI: bus type pnp registered
[    0.222517] pnp: PnP ACPI: found 13 devices
[    0.222520] ACPI: ACPI bus type pnp unregistered
[    0.222525] PnPBIOS: Disabled by ACPI PNP
[    0.222542] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.222546] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.222550] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.222553] system 00:07: ioport range 0x580-0x5ff has been reserved
[    0.222557] system 00:07: ioport range 0x800-0x87f could not be reserved
[    0.222561] system 00:07: ioport range 0x880-0x8ff has been reserved
[    0.222565] system 00:07: ioport range 0x900-0x97f has been reserved
[    0.222569] system 00:07: ioport range 0x980-0x9ff has been reserved
[    0.222572] system 00:07: ioport range 0x2000-0x207f has been reserved
[    0.222576] system 00:07: ioport range 0x2080-0x20ff has been reserved
[    0.222581] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.222585] system 00:07: iomem range 0xfeb80000-0xfebbffff has been reserved
[    0.222590] system 00:07: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.222597] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.222601] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.222608] system 00:0a: ioport range 0x290-0x297 has been reserved
[    0.222614] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.222621] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.222625] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.222629] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.222633] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.222637] system 00:0c: iomem range 0xff780000-0xffffffff has been reserved
[    0.257342] Switching to clocksource acpi_pm
[    0.257721] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.257721] pci 0000:00:02.0:   IO window: disabled
[    0.257721] pci 0000:00:02.0:   MEM window: disabled
[    0.257721] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.257721] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.257721] pci 0000:00:03.0:   IO window: disabled
[    0.257721] pci 0000:00:03.0:   MEM window: disabled
[    0.257721] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.257721] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.257721] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.257721] pci 0000:00:04.0:   MEM window: 0xf8900000-0xfe9fffff
[    0.257721] pci 0000:00:04.0:   PREFETCH window: 0x000000b7f00000-0x000000d7efffff
[    0.257721] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.257721] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.257721] pci 0000:00:10.0:   MEM window: 0xfea00000-0xfeafffff
[    0.257721] pci 0000:00:10.0:   PREFETCH window: 0xd7f00000-0xdfefffff
[    0.257721] pci 0000:00:02.0: setting latency timer to 64
[    0.257721] pci 0000:00:03.0: setting latency timer to 64
[    0.257721] pci 0000:00:04.0: setting latency timer to 64
[    0.257721] pci 0000:00:10.0: setting latency timer to 64
[    0.257721] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.257721] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.257721] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.257721] pci_bus 0000:03: resource 1 mem: [0xf8900000-0xfe9fffff]
[    0.257721] pci_bus 0000:03: resource 2 pref mem [0xb7f00000-0xd7efffff]
[    0.257721] pci_bus 0000:04: resource 0 io:  [0xc000-0xcfff]
[    0.257721] pci_bus 0000:04: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.257721] pci_bus 0000:04: resource 2 pref mem [0xd7f00000-0xdfefffff]
[    0.257721] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.257721] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.257721] NET: Registered protocol family 2
[    0.257721] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257721] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.258472] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.259288] TCP: Hash tables configured (established 131072 bind 65536)
[    0.259291] TCP reno registered
[    0.259425] NET: Registered protocol family 1
[    0.259492] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.259518] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.259548] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.696103] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.696163] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.696225] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.696289] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.696310] pci 0000:03:00.0: Boot video device
[    0.696561] cpufreq-nforce2: No nForce2 chipset.
[    0.696591] Scanning for low memory corruption every 60 seconds
[    0.696721] audit: initializing netlink socket (disabled)
[    0.696734] type=2000 audit(1279702347.696:1): initialized
[    0.707015] highmem bounce pool size: 64 pages
[    0.707021] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.708617] VFS: Disk quotas dquot_6.5.2
[    0.708682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.709280] fuse init (API version 7.13)
[    0.709367] msgmni has been set to 1690
[    0.709629] alg: No test for stdrng (krng)
[    0.709691] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.709695] io scheduler noop registered
[    0.709697] io scheduler anticipatory registered
[    0.709700] io scheduler deadline registered
[    0.709741] io scheduler cfq registered (default)
[    0.709925]   alloc irq_desc for 24 on node -1
[    0.709928]   alloc kstat_irqs on node -1
[    0.709939] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.709945] pcieport 0000:00:02.0: setting latency timer to 64
[    0.710020]   alloc irq_desc for 25 on node -1
[    0.710022]   alloc kstat_irqs on node -1
[    0.710027] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.710032] pcieport 0000:00:03.0: setting latency timer to 64
[    0.710107]   alloc irq_desc for 26 on node -1
[    0.710109]   alloc kstat_irqs on node -1
[    0.710114] pcieport 0000:00:04.0: irq 26 for MSI/MSI-X
[    0.710119] pcieport 0000:00:04.0: setting latency timer to 64
[    0.710185] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.710213] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.710346] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.710351] ACPI: Power Button [PWRB]
[    0.710408] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.710411] ACPI: Power Button [PWRF]
[    0.710971] processor LNXCPU:00: registered as cooling_device0
[    0.711247] processor LNXCPU:01: registered as cooling_device1
[    0.716683] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.716797] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.717161] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.718326] brd: module loaded
[    0.718833] loop: module loaded
[    0.718931] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.719188] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.719569] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.719576]   alloc irq_desc for 23 on node -1
[    0.719578]   alloc kstat_irqs on node -1
[    0.719592] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.719609] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.719618] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.719913] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.719916]   alloc irq_desc for 22 on node -1
[    0.719918]   alloc kstat_irqs on node -1
[    0.719926] pata_acpi 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.719943] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.719951] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.720329] Fixed MDIO Bus: probed
[    0.720372] PPP generic driver version 2.4.2
[    0.720414] tun: Universal TUN/TAP device driver, 1.6
[    0.720416] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.720508] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.720808] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.720811]   alloc irq_desc for 21 on node -1
[    0.720813]   alloc kstat_irqs on node -1
[    0.720821] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.720842] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.720846] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.720911] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.720944] ehci_hcd 0000:00:0b.1: debug port 1
[    0.720951] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.720976] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfebdfc00
[    0.721050] isapnp: Scanning for PnP cards...
[    0.770056] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.770159] usb usb1: configuration #1 chosen from 1 choice
[    0.770191] hub 1-0:1.0: USB hub found
[    0.770205] hub 1-0:1.0: 8 ports detected
[    0.770277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.770613] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.770616]   alloc irq_desc for 20 on node -1
[    0.770618]   alloc kstat_irqs on node -1
[    0.770627] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.770637] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.770640] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.770675] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.770704] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfebde000
[    0.820803] Freeing initrd memory: 7776k freed
[    0.835303] usb usb2: configuration #1 chosen from 1 choice
[    0.835338] hub 2-0:1.0: USB hub found
[    0.835356] hub 2-0:1.0: 8 ports detected
[    0.835441] uhci_hcd: USB Universal Host Controller Interface driver
[    0.835570] PNP: No PS/2 controller found. Probing ports directly.
[    0.838264] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.838273] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.838358] mice: PS/2 mouse device common for all mice
[    0.838470] rtc_cmos 00:02: RTC can wake from S4
[    0.838520] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.838554] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.838660] device-mapper: uevent: version 1.0.3
[    0.838804] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.838879] device-mapper: multipath: version 1.1.0 loaded
[    0.838883] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.839005] EISA: Probing bus 0 at eisa.0
[    0.839016] Cannot allocate resource for EISA slot 2
[    0.839024] Cannot allocate resource for EISA slot 5
[    0.839034] EISA: Detected 0 cards.
[    0.839122] cpuidle: using governor ladder
[    0.839125] cpuidle: using governor menu
[    0.839602] TCP cubic registered
[    0.839758] NET: Registered protocol family 10
[    0.840234] lo: Disabled Privacy Extensions
[    0.840560] NET: Registered protocol family 17
[    0.840597] powernow-k8: Found 1 AMD Athlon(tm)64 X2 Dual Core Processor  3800+ processors (2 cpu cores) (version 2.20.00)
[    0.840645] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[    0.840647] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[    0.840650] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    0.857908] Using IPI No-Shortcut mode
[    0.857992] PM: Resume from disk failed.
[    0.858006] registered taskstats version 1
[    0.858400]   Magic number: 2:769:877
[    0.858527] rtc_cmos 00:02: setting system clock to 2010-07-21 08:52:28 UTC (1279702348)
[    0.858531] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.858533] EDD information not available.
[    1.075551] isapnp: No Plug & Play device found
[    1.075579] Freeing unused kernel memory: 656k freed
[    1.076257] Write protecting the kernel text: 4676k
[    1.076297] Write protecting the kernel read-only data: 1840k
[    1.096871] udev: starting version 151
[    1.207561] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.207910] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    1.207917] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.207923] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.207978] nv_probe: set workaround bit for reversed mac addr
[    1.216145] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.255378] Floppy drive(s): fd0 is 1.44M
[    1.259816] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    1.259824]   alloc irq_desc for 19 on node -1
[    1.259827]   alloc kstat_irqs on node -1
[    1.259840] ohci1394 0000:04:05.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    1.275917] FDC 0 is a post-1991 82077
[    1.313083] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.347612] usb 1-7: configuration #1 chosen from 1 choice
[    1.356326] Initializing USB Mass Storage driver...
[    1.356512] scsi0 : SCSI emulation for USB Mass Storage devices
[    1.356686] usbcore: registered new interface driver usb-storage
[    1.356689] USB Mass Storage support registered.
[    1.356819] usb-storage: device found at 4
[    1.356821] usb-storage: waiting for device to settle before scanning
[    1.704030] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    1.724905] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:15:f2:05:25:2a
[    1.724909] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    1.724948] pata_amd 0000:00:0d.0: version 0.4.1
[    1.725028] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.725130] scsi1 : pata_amd
[    1.725227] scsi2 : pata_amd
[    1.728816] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.728820] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.728959] sata_nv 0000:00:0e.0: version 3.5
[    1.728972] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.728975] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.729059] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.729264] scsi3 : sata_nv
[    1.729337] scsi4 : sata_nv
[    1.729499] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe000 irq 23
[    1.729503] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 23
[    1.729527] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.729530] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.729586] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.729796] scsi5 : sata_nv
[    1.729989] scsi6 : sata_nv
[    1.730146] ata5: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 22
[    1.730149] ata6: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 22
[    1.893657] ata1.00: ATA-6: WDC WD1600JB-75GVC0, 08.02D08, max UDMA/100
[    1.893661] ata1.00: 312500000 sectors, multi 16: LBA48 
[    1.893688] ata1: nv_mode_filter: 0x3f39f&0x739f->0x739f, BIOS=0x7000 (0xc000c000) ACPI=0x701f (60:900:0x11)
[    1.909598] ata1.00: configured for UDMA/33
[    1.909761] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600JB-75G 08.0 PQ: 0 ANSI: 5
[    1.910006] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.910019] sd 1:0:0:0: [sda] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    1.910181] sd 1:0:0:0: [sda] Write Protect is off
[    1.910185] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.910209] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.910374]  sda:
[    1.918215] usb 2-3: configuration #1 chosen from 1 choice
[    1.934168]  sda1 sda2 < sda5 >
[    1.972794] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.050509] ata3: SATA link down (SStatus 0 SControl 300)
[    2.060999] ata5: SATA link down (SStatus 0 SControl 300)
[    2.072352] ata2.00: ATAPI: PIONEER DVD-RW  DVR-104, 1.41, max UDMA/33
[    2.072379] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c000) ACPI=0x701f (60:900:0x11)
[    2.088296] ata2.00: configured for UDMA/33
[    2.095507] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-104  1.41 PQ: 0 ANSI: 5
[    2.118603] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.118606] Uniform CD-ROM driver Revision: 3.20
[    2.118712] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.118790] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.228029] usb 2-4: new low speed USB device using ohci_hcd and address 3
[    2.438501] ata4: SATA link down (SStatus 0 SControl 300)
[    2.440200] usb 2-4: configuration #1 chosen from 1 choice
[    2.456518] usbcore: registered new interface driver hiddev
[    2.462444] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input3
[    2.462553] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:0b.0-3/input0
[    2.467335] input: Cypress Sem USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input4
[    2.467416] generic-usb 0003:05FE:0005.0002: input,hidraw1: USB HID v1.00 Mouse [Cypress Sem USB Mouse] on usb-0000:00:0b.0-4/input0
[    2.467435] usbcore: registered new interface driver usbhid
[    2.467438] usbhid: v2.6:USB HID core driver
[    2.584439] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800007c654f]
[    2.758512] ata6: SATA link down (SStatus 0 SControl 300)
[    2.758538] usb 2-8: new low speed USB device using ohci_hcd and address 4
[    2.940040] usb 2-8: device descriptor read/64, error -62
[    3.102612] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.102618] EXT4-fs (sda1): write access will be enabled during recovery
[    3.228024] usb 2-8: device descriptor read/64, error -62
[    3.508036] usb 2-8: new low speed USB device using ohci_hcd and address 5
[    3.688023] usb 2-8: device descriptor read/64, error -62
[    3.972024] usb 2-8: device descriptor read/64, error -62
[    4.252025] usb 2-8: new low speed USB device using ohci_hcd and address 6
[    4.660023] usb 2-8: device not accepting address 6, error -62
[    4.836030] usb 2-8: new low speed USB device using ohci_hcd and address 7
[    5.244042] usb 2-8: device not accepting address 7, error -62
[    5.244065] hub 2-0:1.0: unable to enumerate USB device on port 8
[    6.356233] usb-storage: device scan complete
[    6.358300] scsi 0:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.358787] scsi 0:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.359283] scsi 0:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    6.359782] scsi 0:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.360728] sd 0:0:0:0: Attached scsi generic sg2 type 0
[    6.362221] sd 0:0:0:1: Attached scsi generic sg3 type 0
[    6.362547] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[    6.362800] sd 0:0:0:2: Attached scsi generic sg4 type 0
[    6.362960] sd 0:0:0:3: Attached scsi generic sg5 type 0
[    6.364768] sd 0:0:0:1: [sdc] Attached SCSI removable disk
[    6.366713] sd 0:0:0:3: [sde] Attached SCSI removable disk
[    6.368824] sd 0:0:0:2: [sdd] Attached SCSI removable disk
[    7.073420] EXT4-fs (sda1): recovery complete
[    7.073866] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   22.943650] udev: starting version 151
[   23.030463] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   23.030520] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   23.093404] vga16fb: initializing
[   23.093410] vga16fb: mapped to 0xc00a0000
[   23.093505] fb0: VGA16 VGA frame buffer device
[   23.130251] lp: driver loaded but no devices found
[   23.149917] Adding 6037496k swap on /dev/sda5.  Priority:-1 extents:1 across:6037496k 
[   23.232631] Linux agpgart interface v0.103
[   23.307210] type=1505 audit(1279702370.945:2):  operation="profile_load" pid=642 name="/sbin/dhclient3"
[   23.307499] type=1505 audit(1279702370.945:3):  operation="profile_load" pid=642 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.307659] type=1505 audit(1279702370.945:4):  operation="profile_load" pid=642 name="/usr/lib/connman/scripts/dhclient-script"
[   23.319561] type=1505 audit(1279702370.957:5):  operation="profile_load" pid=669 name="/usr/sbin/ntpd"
[   23.423973] nvidia: module license 'NVIDIA' taints kernel.
[   23.423978] Disabling lock debugging due to kernel taint
[   24.564274] Linux video capture interface: v2.00
[   24.579152] ivtv: Start initialization, version 1.4.1
[   24.579276] ivtv0: Initializing card 0
[   24.579280] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   24.579697] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   24.579704]   alloc irq_desc for 18 on node -1
[   24.579706]   alloc kstat_irqs on node -1
[   24.579719] ivtv 0000:04:09.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   24.638355] tveeprom 2-0050: Hauppauge model 26582, rev F0B2, serial# 9798247
[   24.638359] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   24.638363] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   24.638366] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   24.638369] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   24.638371] tveeprom 2-0050: has no radio
[   24.638374] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   24.645067] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   24.655089] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   24.663247] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   24.690907] tuner-simple 2-0061: creating new instance
[   24.690912] tuner-simple 2-0061: type set to 50 (TCL 2002N)
[   24.691934] IRQ 18/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.692479] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   24.692574] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   24.692659] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   24.692741] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   24.692745] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   24.693275] ivtv: End initialization
[   24.783290] parport_pc 00:06: reported by Plug and Play ACPI
[   24.783423] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   24.934684] saa7130/34: v4l2 driver version 0.2.15 loaded
[   24.935139] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[   24.935147]   alloc irq_desc for 17 on node -1
[   24.935149]   alloc kstat_irqs on node -1
[   24.935163] saa7134 0000:04:08.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[   24.935170] saa7133[0]: found at 0000:04:08.0, rev: 209, irq: 17, latency: 64, mmio: 0xfeaff000
[   24.935178] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   24.935218] saa7133[0]: board init: gpio is 10400
[   24.935249] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.939111] ppdev: user-space parallel port driver
[   24.940364] lp0: using parport0 (interrupt-driven).
[   24.971984] type=1505 audit(1279702372.609:6):  operation="profile_replace" pid=842 name="/sbin/dhclient3"
[   24.972299] type=1505 audit(1279702372.613:7):  operation="profile_replace" pid=842 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   24.972475] type=1505 audit(1279702372.613:8):  operation="profile_replace" pid=842 name="/usr/lib/connman/scripts/dhclient-script"
[   24.989122] type=1505 audit(1279702372.629:9):  operation="profile_load" pid=845 name="/usr/bin/evince"
[   25.016975] type=1505 audit(1279702372.657:10):  operation="profile_load" pid=845 name="/usr/bin/evince-previewer"
[   25.032880] type=1505 audit(1279702372.673:11):  operation="profile_load" pid=845 name="/usr/bin/evince-thumbnailer"
[   25.093457] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 16
[   25.093465]   alloc irq_desc for 16 on node -1
[   25.093467]   alloc kstat_irqs on node -1
[   25.093480] nvidia 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 16 (level, low) -> IRQ 16
[   25.093488] nvidia 0000:03:00.0: setting latency timer to 64
[   25.093493] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   25.093916] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   25.096062] Console: switching to colour frame buffer device 80x30
[   25.119634] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   25.119647] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   25.119658] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   25.119669] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   25.119679] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   25.119688] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119699] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119709] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119719] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119729] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119739] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119749] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119759] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119769] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119779] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119789] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.119803] i2c i2c-3: Invalid 7-bit address 0x7a
[   25.128025] saa7133[0]: registered device video1 [v4l2]
[   25.128061] saa7133[0]: registered device vbi1
[   25.168966] dvb_init() allocating 1 frontend
[   25.213107] nxt200x: NXT2004 Detected
[   25.233874] saa7134 ALSA driver for DMA sound loaded
[   25.233892] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.233918] saa7133[0]/alsa: saa7133[0] at 0xfeaff000 irq 17 registered as card -2
[   25.257953] DVB: registering new adapter (saa7133[0])
[   25.257961] DVB: registering adapter 0 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   25.264078] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   25.264089] saa7134 0000:04:08.0: firmware: requesting dvb-fe-nxt2004.fw
[   25.321038] ivtv 0000:04:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   25.337888] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   25.337897] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   25.337901] hda_intel: Disable MSI for Nvidia chipset
[   25.337938] HDA Intel 0000:00:10.1: setting latency timer to 64
[   25.453118] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   25.652162] ivtv0: Encoder revision: 0x02060039
[   25.669996] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
[   25.697458] nxt2004: Waiting for firmware upload(2)...
[   26.182880] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
[   27.081086] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   27.081096] saa7134 0000:04:08.0: firmware: requesting dvb-fe-nxt2004.fw
[   27.117789] nxt2004: Waiting for firmware upload(2)...
[   28.068034] nxt2004: Firmware upload complete
[   28.161037] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   28.488880] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   28.489027] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -5)
[   28.648875] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   28.649052] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -5)
[   28.740863] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   28.741013] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -5)
[   28.952943] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   29.248858] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   29.355036] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   29.468313] nxt200x: Error writing multireg register 0x08
[   29.516090] nxt200x: Error writing multireg register 0x08
[   29.608111] nxt200x: Error writing multireg register 0x80
[   29.696061] nxt200x: Error writing multireg register 0x80
[   29.768054] nxt200x: Error writing multireg register 0x08
[   29.840059] nxt200x: Error writing multireg register 0x08
[   29.912025] nxt200x: Error writing multireg register 0x80
[   29.952032] nxt200x: Error writing multireg register 0x81
[   29.992032] nxt200x: Error writing multireg register 0x82
[   30.064023] nxt200x: Error writing multireg register 0x88
[   30.136032] nxt200x: Error writing multireg register 0x80
[   30.248568] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   30.248710] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -5)
[   30.248843] nxt200x: nxt200x_writebytes: i2c write error (addr 0x0a, err == -5)
[   30.272028] nxt2004: Firmware upload complete
[   32.361023] nxt200x: Timeout waiting for nxt2004 to init.
[   35.245022] eth0: no IPv6 routers present
[   47.322128] end_request: I/O error, dev fd0, sector 0
[   59.513395] end_request: I/O error, dev fd0, sector 0
[   86.668076] Clocksource tsc unstable (delta = -217221381 ns)

lspci:


geoff@mythbox:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
04:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

---

### Post by Caysho on 2010-07-21
I think klc5555 is correct - you need to use the correct module parameters (card and tuner).
The card is being detected correctly
The frontend is a Nextwave NXT200X VSB/QAM and the firmware is being loaded correctly.
I am guessing ubuntu is asking the saa7134 driver what the tuner is and it is defaulting to the air2pc. I would expect it to show Nextwave.

The Air2PC card uses a variant of the frontend.  If you do searches on A180, the frontend's name etc you will see the problems.

The card is #76 in CARDLIST.saa7134 according to [mjmwired's card list]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134"), other searches for the PCI ID give #75.

The [AVerTVHD MCE A180]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_MCE_A180") page contains essentially what you have done, from what I can see.

---

### Post by klc5555 on 2010-07-21
The simplest issue is that, though the card is being correctly autodetected as card=75 (a small miracle in itself), the tuner parameter must also be specified for this card to get channel locks. So the param tuner=68 needs to get passed to the saa7134 driver with modprobe. 

However, if the tuner=68 param doesn't get the card working, I suspect that newlinux's guess may be correct. Because unless I'm misreading it, the dmesg output seems to indicate that the firmware may not be initializing properly. It also seems to indicate that the root of the matter is some kind of i2c problem.

Now I'm aware that the 2.6.31 kernels were subject to some odd i2c behavior, and I don't know if such things have been fixed in the 2.6.32 and subsequent kernels. And geofffox's firmware init timeout may be dependent on something else entirely.

As a last ditch attempt to get this card going, it might be worth seeing if the A180 card and driver can be got working if a myth distro relying on a 2.6.30 or earlier kernel is used. In the Ubuntu world this would imply 9.04 (or 8.04). As I said, I initially had i2c issues with the firmware, but was able to get it going on a 2.6.27.7 kernel as long as i2c support was a module and not built-in.

---

### Post by newlinux on 2010-07-21
I think it is definitely an i2c/firmware loading problem (if tuner=68 doesn't work). You still haven't answered which version of the card you have (I'm gonna guess the newer one, not the old one like I have as mine has always gotten autodetected properly since support was in the kernel with no tuner options).

What does ```
 lspci -v
``` return for the Avermedia Card? Mine returns:
```

05:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Device 1044
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d4000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

```

and also to klc555's point, I do remember there are specific kernels where this card did not work easily, but I don't remember what they are. That said, I'm running 2.6.32-22 with no problems. what kernel are you running?

and just to double check, what does:

```
ls -lh /lib/firmware/ | grep nxt
```

return?

---

### Post by geofffox on 2010-07-21
First, thanks to all of you for your help.  You are more than kind and even though this is very frustrating I suspect the end result will be fine.  It is this kind of help that attracts me to Linux and keeps me hacking along even as my 60th birthday approaches on Monday.

I have already passed the edge of my knowledge, so if you want to just tell me what to do instead of making believe I still have a say, feel free!

Geoff

(I have included the full lspci output though I suspect only the a180 is necessary.  As you see I also have a PVR150 for analog recording)


geoff@mythbox:~$  lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81cd
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8900000-fe9fffff
	Prefetchable memory behind bridge: 00000000b7f00000-00000000d7efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at febde000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at febdfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e000 [size=16]
	Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: d7f00000-dfefffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at febd8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8141
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at febd7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

03:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
	Subsystem: nVidia Corporation Device 0438
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808a
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

04:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Device 1044
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at feaff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. Device 8801
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv


---------------------

geoff@mythbox:~$ ls -lh /lib/firmware/ | grep nxt
-rw-r--r--  1 root root 9.4K 2010-04-16 00:10 dvb-fe-nxt2004.fw

---

### Post by klc5555 on 2010-07-22
From your lspci output, it looks like you have one of the old-style A180s, similar to newlinux's. Output from a new-style card, such as I have, would look as follows:
 
05:03.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)

I don't have any experience in getting an old-style card working. But before trying anything more complicated, I'd recommend trying loading the saa7134 module by hand with the correct parameters, to see whether you can get channel locks. So, stop the mythtv backend if it's running, and then:

sudo rmmod saa7134-dvb
sudo rmmod saa7134

followed by:

sudo modprobe saa7134 card=75 tuner=68

And assuming the module loads without error messages, go into mythtv-setup, do a channel scan with the card and see whether you get channel locks.

If you still can't get locks, then it would appear that the firmware really is not initializing correctly, and that the problem is with i2c, as the output from your dmesg | grep nxt indicated earlier. I'm not sure what the best solution in that case would be.

---

