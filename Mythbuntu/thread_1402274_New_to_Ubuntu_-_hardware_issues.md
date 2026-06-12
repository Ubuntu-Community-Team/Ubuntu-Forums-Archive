---
title: "New to Ubuntu - hardware issues"
date: 2010-02-08
forum: Mythbuntu
---

### Post by Stunpals on 2010-02-08
I setup a MythTV box and I have been having complete system freezing. The only option i have is a hard reboot.
 
Often when this hapens the system first becomes unresponsive locally and often even a remote ssh connection is not possible.
 
The video, not always but often, goes nuts, very pixelated or bright pink and distorted. This is all new hardware and I am starting to think something is failing.
 
How do I test the hardware, starting with the video card. I did run the memtest from the boot menu and it completed succesfully.

---

### Post by warfacegod on 2010-02-08
I would test the hard drive next.

```
sudo apt-get install gsmartcontrol
```

---

### Post by Sef on 2010-02-08
1) Moved to Mythbuntu subforms.

2) What are your system specs?

---

### Post by Stunpals on 2010-02-10
AMD Athlon IIX2 240 2.8GHz 2MBAM3 
eVGA De-GeForce 8500GT 256MB Passi 
Gigabyte GA-MA785GMT-UD2H Motherboard 
Kingston 4GB 1333MHz CL91.5V (2x2GB) 
Seagate 500GB 7200.12 16MB SATAII 
UieOn 4x Blu Ray ROM SATA black 
Antec Fusion Black no PSU 
SPI400W ATX Power Supply 120mm 


All the hardware is new, only the video card was an open box.

When the system is acting up if I do a glxinfo I only get an error, didn't copy it down sorry. If I remove the card it will boot fine but the onboard video is probably not good enough. It seems if I let the card sit for a while then put it back in, reload the drivers it is good for a while then the system messes up again. Have only tested that once so not sure it is a coincidence.


I had a friend take a quick look and he thinks its the video card causing the kernal to crash, here is the dmesg after a reboot.

```
Feb  8 22:14:31 MythTv-01 kernel: [    8.606119] type=1505 audit(1265692471.873:13): operation="profile_replace" pid=874 name=/usr/lib/connman/scripts/dhclient-script
Feb  8 22:14:31 MythTv-01 kernel: [    8.608225] type=1505 audit(1265692471.877:14): operation="profile_replace" pid=875 name=/usr/bin/evince
Feb  8 22:14:31 MythTv-01 kernel: [    8.611549] type=1505 audit(1265692471.877:15): operation="profile_replace" pid=875 name=/usr/bin/evince-previewer
Feb  8 22:14:31 MythTv-01 kernel: [    8.613523] type=1505 audit(1265692471.881:16): operation="profile_replace" pid=875 name=/usr/bin/evince-thumbnailer
Feb  8 22:14:31 MythTv-01 kernel: [    8.617499] type=1505 audit(1265692471.885:17): operation="profile_replace" pid=877 name=/usr/sbin/mysqld
Feb  8 22:14:31 MythTv-01 kernel: [    8.618404] type=1505 audit(1265692471.885:18): operation="profile_replace" pid=878 name=/usr/sbin/ntpd
Feb  8 22:14:31 MythTv-01 kernel: [    8.619291] type=1505 audit(1265692471.885:19): operation="profile_replace" pid=879 name=/usr/sbin/tcpdump
Feb  8 22:14:33 MythTv-01 kernel: [    9.877559] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb  8 22:14:33 MythTv-01 kernel: [    9.901383] r8169: eth0: link up
Feb  8 22:14:33 MythTv-01 kernel: [    9.901388] r8169: eth0: link up
Feb  8 22:14:33 MythTv-01 kernel: [   10.605331] type=1503 audit(1265692473.874:20): operation="open" pid=1159 parent=1158 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 06:55:29 MythTv-01 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="862" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Feb  9 21:03:44 MythTv-01 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Feb  9 21:03:44 MythTv-01 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="723" x-info="http://www.rsyslog.com"] (re)start
Feb  9 21:03:44 MythTv-01 rsyslogd: rsyslogd's groupid changed to 102
Feb  9 21:03:44 MythTv-01 rsyslogd: rsyslogd's userid changed to 101
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic-pae)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] KERNEL supported cpus:
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Intel GenuineIntel
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   AMD AuthenticAMD
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   NSC Geode by NSC
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Cyrix CyrixInstead
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Centaur CentaurHauls
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Transmeta GenuineTMx86
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Transmeta TransmetaCPU
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   UMC UMC UMC UMC
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfde0000 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] DMI 2.4 present.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x1000000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] modified physical RAM map:
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfde0000 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] NX (Execute Disable) protection: active
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] RAMDISK: 3789d000 - 37fef16a
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Allocated new RAMDISK: 008b5000 - 0100716a
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Move RAMDISK from 000000003789d000 - 0000000037fef169 to 008b5000 - 01007169
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: RSDP 000f7260 00014 (v00 GBT   )
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: RSDT cfde3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: FACP cfde3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: DSDT cfde30c0 07420 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: FACS cfde0000 00040
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: SSDT cfdea5c0 0095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: HPET cfdeaf40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: MCFG cfdeaf80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: TAMG cfdeafc0 0029A (v01 GBT    GBT   B0 5455312E BG 53450101)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: APIC cfdea500 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] 3974MB HIGHMEM available.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] 889MB LOWMEM available.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   low ram: 0 - 379fe000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #5 [00008ae000 - 00008b4106]              BRK ==> [00008ae000 - 00008b4106]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #7 [00008b5000 - 000100716a]      NEW RAMDISK ==> [00008b5000 - 000100716a]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] found SMP MP-table at [c00f58c0] f58c0
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Zone PFN ranges:
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]   HighMem  0x000379fe -> 0x00130000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Movable zone start PFN for each node
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] early_node_map[4] active PFN ranges
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     0: 0x00000100 -> 0x000cfde0
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Using APIC driver default
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Allocating PCI resources starting at cfe00000 (gap: cfe00000:10200000)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PERCPU: Embedded 14 pages at c3618000, static data 35612 bytes
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038202
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=95382a00-f50c-4536-b1b6-9db37fa37b96 ro quiet splash
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Initializing CPU#0
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] allocated 24903680 bytes of page_cgroup
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00130000)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Memory: 4111092k/4980736k available (4590k kernel code, 79736k reserved, 2147k data, 544k init, 3280776k highmem)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] virtual kernel memory layout:
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]       .data : 0xc057b894 - 0xc07947e8   (2147 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000]       .text : 0xc0100000 - 0xc057b894   (4590 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Fast TSC calibration using PIT
Feb  9 21:03:44 MythTv-01 kernel: [    0.000000] Detected 2813.230 MHz processor.
Feb  9 21:03:44 MythTv-01 kernel: [    0.001694] Console: colour VGA+ 80x25
Feb  9 21:03:44 MythTv-01 kernel: [    0.001696] console [tty0] enabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.001837] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Feb  9 21:03:44 MythTv-01 kernel: [    0.001841] Calibrating delay loop (skipped), value calculated using timer frequency.. 5626.46 BogoMIPS (lpj=11252920)
Feb  9 21:03:44 MythTv-01 kernel: [    0.001853] Security Framework initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.001864] AppArmor: AppArmor initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.001869] Mount-cache hash table entries: 512
Feb  9 21:03:44 MythTv-01 kernel: [    0.001936] Initializing cgroup subsys ns
Feb  9 21:03:44 MythTv-01 kernel: [    0.001939] Initializing cgroup subsys cpuacct
Feb  9 21:03:44 MythTv-01 kernel: [    0.001942] Initializing cgroup subsys memory
Feb  9 21:03:44 MythTv-01 kernel: [    0.001946] Initializing cgroup subsys freezer
Feb  9 21:03:44 MythTv-01 kernel: [    0.001947] Initializing cgroup subsys net_cls
Feb  9 21:03:44 MythTv-01 kernel: [    0.001955] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 21:03:44 MythTv-01 kernel: [    0.001957] CPU: L2 Cache: 1024K (64 bytes/line)
Feb  9 21:03:44 MythTv-01 kernel: [    0.001958] CPU: Physical Processor ID: 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.001959] CPU: Processor Core ID: 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.001962] mce: CPU supports 6 MCE banks
Feb  9 21:03:44 MythTv-01 kernel: [    0.001968] using C1E aware idle routine
Feb  9 21:03:44 MythTv-01 kernel: [    0.001972] Performance Counters: AMD PMU driver.
Feb  9 21:03:44 MythTv-01 kernel: [    0.001974] ... version:                 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.001975] ... bit width:               48
Feb  9 21:03:44 MythTv-01 kernel: [    0.001977] ... generic counters:        4
Feb  9 21:03:44 MythTv-01 kernel: [    0.001978] ... value mask:              0000ffffffffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.001979] ... max period:              00007fffffffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.001981] ... fixed-purpose counters:  0
Feb  9 21:03:44 MythTv-01 kernel: [    0.001982] ... counter mask:            000000000000000f
Feb  9 21:03:44 MythTv-01 kernel: [    0.001984] Checking 'hlt' instruction... OK.
Feb  9 21:03:44 MythTv-01 kernel: [    0.017469] ACPI: Core revision 20090521
Feb  9 21:03:44 MythTv-01 kernel: [    0.028518] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  9 21:03:44 MythTv-01 kernel: [    0.070591] CPU0: AMD Athlon(tm) II X2 240 Processor stepping 02
Feb  9 21:03:44 MythTv-01 kernel: [    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] Initializing CPU#1
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] Calibrating delay using timer specific routine.. 5625.45 BogoMIPS (lpj=11250900)
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] CPU: Processor Core ID: 1
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] mce: CPU supports 6 MCE banks
Feb  9 21:03:44 MythTv-01 kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Feb  9 21:03:44 MythTv-01 kernel: [    0.156469] CPU1: AMD Athlon(tm) II X2 240 Processor stepping 02
Feb  9 21:03:44 MythTv-01 kernel: [    0.156476] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Feb  9 21:03:44 MythTv-01 kernel: [    0.160010] Brought up 2 CPUs
Feb  9 21:03:44 MythTv-01 kernel: [    0.160012] Total of 2 processors activated (11251.91 BogoMIPS).
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] Booting paravirtualized kernel on bare hardware
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] regulator: core version 0.5
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] Time:  4:03:39  Date: 02/10/10
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] NET: Registered protocol family 16
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] EISA bus registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.160161] ACPI: bus type pci registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.160186] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Feb  9 21:03:44 MythTv-01 kernel: [    0.160188] PCI: MCFG area at e0000000 reserved in E820
Feb  9 21:03:44 MythTv-01 kernel: [    0.160189] PCI: Using MMCONFIG for extended config space
Feb  9 21:03:44 MythTv-01 kernel: [    0.160191] PCI: Using configuration type 1 for base access
Feb  9 21:03:44 MythTv-01 kernel: [    0.160735] bio: create slab <bio-0> at 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.167949] ACPI: Interpreter enabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.167955] ACPI: (supports S0 S3 S4 S5)
Feb  9 21:03:44 MythTv-01 kernel: [    0.167972] ACPI: Using IOAPIC for interrupt routing
Feb  9 21:03:44 MythTv-01 kernel: [    0.171105] ACPI: No dock devices found.
Feb  9 21:03:44 MythTv-01 kernel: [    0.171186] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  9 21:03:44 MythTv-01 kernel: [    0.171268] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Feb  9 21:03:44 MythTv-01 kernel: [    0.171270] pci 0000:00:02.0: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.171304] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Feb  9 21:03:44 MythTv-01 kernel: [    0.171307] pci 0000:00:0a.0: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.171593] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Feb  9 21:03:44 MythTv-01 kernel: [    0.171597] pci 0000:00:12.2: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.171789] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Feb  9 21:03:44 MythTv-01 kernel: [    0.171793] pci 0000:00:13.2: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.172038] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Feb  9 21:03:44 MythTv-01 kernel: [    0.172042] pci 0000:00:14.2: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.172445] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  9 21:03:44 MythTv-01 kernel: [    0.172448] pci 0000:02:00.0: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.172711] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
Feb  9 21:03:44 MythTv-01 kernel: [    0.172715] pci 0000:03:07.0: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.172829] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
Feb  9 21:03:44 MythTv-01 kernel: [    0.172833] pci 0000:03:0e.0: PME# disabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.172866] pci 0000:00:14.4: transparent bridge
Feb  9 21:03:44 MythTv-01 kernel: [    0.188730] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.188799] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.188865] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.188932] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.188997] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.189063] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.189129] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.189195] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:03:44 MythTv-01 kernel: [    0.189305] SCSI subsystem initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] usbcore: registered new interface driver usbfs
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] usbcore: registered new interface driver hub
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] usbcore: registered new device driver usb
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] ACPI: WMI: Mapper loaded
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] PCI: Using ACPI for IRQ routing
Feb  9 21:03:44 MythTv-01 kernel: [    0.189334] pci 0000:00:00.0: BAR 3: can't allocate resource
Feb  9 21:03:44 MythTv-01 kernel: [    0.200018] Bluetooth: Core ver 2.15
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] NET: Registered protocol family 31
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] Bluetooth: HCI device and connection manager initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] Bluetooth: HCI socket layer initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] NetLabel: Initializing
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] NetLabel:  domain hash size = 128
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  9 21:03:44 MythTv-01 kernel: [    0.200049] NetLabel:  unlabeled traffic allowed by default
Feb  9 21:03:44 MythTv-01 kernel: [    0.200068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Feb  9 21:03:44 MythTv-01 kernel: [    0.200072] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Feb  9 21:03:44 MythTv-01 kernel: [    0.216021] pnp: PnP ACPI init
Feb  9 21:03:44 MythTv-01 kernel: [    0.216034] ACPI: bus type pnp registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.217975] pnp 00:0c: mem resource (0xd1a00-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.217978] pnp 00:0c: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.217981] pnp 00:0c: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.217983] pnp 00:0c: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.217986] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.217989] pnp 00:0c: mem resource (0x100000-0xcfddffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:03:44 MythTv-01 kernel: [    0.218048] pnp: PnP ACPI: found 13 devices
Feb  9 21:03:44 MythTv-01 kernel: [    0.218049] ACPI: ACPI bus type pnp unregistered
Feb  9 21:03:44 MythTv-01 kernel: [    0.218052] PnPBIOS: Disabled by ACPI PNP
Feb  9 21:03:44 MythTv-01 kernel: [    0.218059] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218061] system 00:01: ioport range 0x220-0x225 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218063] system 00:01: ioport range 0x290-0x294 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218067] system 00:02: ioport range 0x4100-0x411f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218069] system 00:02: ioport range 0x228-0x22f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218071] system 00:02: ioport range 0x40b-0x40b has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218073] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218075] system 00:02: ioport range 0xc00-0xc01 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218078] system 00:02: ioport range 0xc14-0xc14 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218080] system 00:02: ioport range 0xc50-0xc52 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218082] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218084] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218086] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218088] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218090] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218092] system 00:02: ioport range 0x4000-0x40fe has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218094] system 00:02: ioport range 0x4210-0x4217 has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218097] system 00:02: ioport range 0xb00-0xb0f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218099] system 00:02: ioport range 0xb10-0xb1f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218101] system 00:02: ioport range 0xb20-0xb3f has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218106] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218111] system 00:0c: iomem range 0xcfde0000-0xcfdfffff could not be reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218113] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218115] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218118] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.218120] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Feb  9 21:03:44 MythTv-01 kernel: [    0.252723] AppArmor: AppArmor Filesystem Enabled
Feb  9 21:03:44 MythTv-01 kernel: [    0.252745] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Feb  9 21:03:44 MythTv-01 kernel: [    0.252748] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252751] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252753] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252758] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
Feb  9 21:03:44 MythTv-01 kernel: [    0.252760] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252762] pci 0000:00:0a.0:   MEM window: 0xfdd00000-0xfddfffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252765] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252769] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Feb  9 21:03:44 MythTv-01 kernel: [    0.252771] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252776] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252780] pci 0000:00:14.4:   PREFETCH window: 0xf4000000-0xf7ffffff
Feb  9 21:03:44 MythTv-01 kernel: [    0.252796] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    0.252804] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    0.252862] NET: Registered protocol family 2
Feb  9 21:03:44 MythTv-01 kernel: [    0.252924] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.253123] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.253491] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.253678] TCP: Hash tables configured (established 131072 bind 65536)
Feb  9 21:03:44 MythTv-01 kernel: [    0.253680] TCP reno registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.253737] NET: Registered protocol family 1
Feb  9 21:03:44 MythTv-01 kernel: [    0.253776] Trying to unpack rootfs image as initramfs...
Feb  9 21:03:44 MythTv-01 kernel: [    0.395760] Freeing initrd memory: 7496k freed
Feb  9 21:03:44 MythTv-01 kernel: [    0.397698] cpufreq-nforce2: No nForce2 chipset.
Feb  9 21:03:44 MythTv-01 kernel: [    0.397715] Scanning for low memory corruption every 60 seconds
Feb  9 21:03:44 MythTv-01 kernel: [    0.397777] audit: initializing netlink socket (disabled)
Feb  9 21:03:44 MythTv-01 kernel: [    0.397787] type=2000 audit(1265774618.395:1): initialized
Feb  9 21:03:44 MythTv-01 kernel: [    0.403895] highmem bounce pool size: 64 pages
Feb  9 21:03:44 MythTv-01 kernel: [    0.403898] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb  9 21:03:44 MythTv-01 kernel: [    0.404757] VFS: Disk quotas dquot_6.5.2
Feb  9 21:03:44 MythTv-01 kernel: [    0.404796] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  9 21:03:44 MythTv-01 kernel: [    0.405154] fuse init (API version 7.12)
Feb  9 21:03:44 MythTv-01 kernel: [    0.405202] msgmni has been set to 1638
Feb  9 21:03:44 MythTv-01 kernel: [    0.405353] alg: No test for stdrng (krng)
Feb  9 21:03:44 MythTv-01 kernel: [    0.405367] io scheduler noop registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.405369] io scheduler anticipatory registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.405370] io scheduler deadline registered
Feb  9 21:03:44 MythTv-01 kernel: [    0.405397] io scheduler cfq registered (default)
Feb  9 21:03:44 MythTv-01 kernel: [    1.252034] pci 0000:00:13.0: OHCI: BIOS handoff failed (BIOS bug?) 00000184
Feb  9 21:03:44 MythTv-01 kernel: [    1.308258] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  9 21:03:44 MythTv-01 kernel: [    1.308274] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  9 21:03:44 MythTv-01 kernel: [    1.308353] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Feb  9 21:03:44 MythTv-01 kernel: [    1.308356] ACPI: Power Button [PWRF]
Feb  9 21:03:44 MythTv-01 kernel: [    1.308387] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Feb  9 21:03:44 MythTv-01 kernel: [    1.308389] ACPI: Power Button [PWRB]
Feb  9 21:03:44 MythTv-01 kernel: [    1.308609] processor LNXCPU:00: registered as cooling_device0
Feb  9 21:03:44 MythTv-01 kernel: [    1.308641] processor LNXCPU:01: registered as cooling_device1
Feb  9 21:03:44 MythTv-01 kernel: [    1.310026] isapnp: Scanning for PnP cards...
Feb  9 21:03:44 MythTv-01 kernel: [    1.663696] isapnp: No Plug & Play device found
Feb  9 21:03:44 MythTv-01 kernel: [    1.664400] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb  9 21:03:44 MythTv-01 kernel: [    1.664503] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 21:03:44 MythTv-01 kernel: [    1.664740] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 21:03:44 MythTv-01 kernel: [    1.665324] brd: module loaded
Feb  9 21:03:44 MythTv-01 kernel: [    1.665577] loop: module loaded
Feb  9 21:03:44 MythTv-01 kernel: [    1.665622] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Feb  9 21:03:44 MythTv-01 kernel: [    1.665677] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.665775] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Feb  9 21:03:44 MythTv-01 kernel: [    1.665777] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part
Feb  9 21:03:44 MythTv-01 kernel: [    1.666094] scsi0 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666190] scsi1 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666227] scsi2 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666264] scsi3 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666301] scsi4 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666337] scsi5 : ahci
Feb  9 21:03:44 MythTv-01 kernel: [    1.666419] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666422] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666425] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666429] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666432] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666435] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 22
Feb  9 21:03:44 MythTv-01 kernel: [    1.666618] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:03:44 MythTv-01 kernel: [    1.666725] scsi6 : pata_atiixp
Feb  9 21:03:44 MythTv-01 kernel: [    1.666761] scsi7 : pata_atiixp
Feb  9 21:03:44 MythTv-01 kernel: [    1.667447] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Feb  9 21:03:44 MythTv-01 kernel: [    1.667449] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Feb  9 21:03:44 MythTv-01 kernel: [    1.667893] Fixed MDIO Bus: probed
Feb  9 21:03:44 MythTv-01 kernel: [    1.667914] PPP generic driver version 2.4.2
Feb  9 21:03:44 MythTv-01 kernel: [    1.667981] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  9 21:03:44 MythTv-01 kernel: [    1.668017] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  9 21:03:44 MythTv-01 kernel: [    1.668029] ehci_hcd 0000:00:12.2: EHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.668059] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.668086] ehci_hcd 0000:00:12.2: debug port 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.668105] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Feb  9 21:03:44 MythTv-01 kernel: [    1.680035] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Feb  9 21:03:44 MythTv-01 kernel: [    1.680104] usb usb1: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.680126] hub 1-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.680131] hub 1-0:1.0: 6 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.680193] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb  9 21:03:44 MythTv-01 kernel: [    1.680208] ehci_hcd 0000:00:13.2: EHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.680229] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Feb  9 21:03:44 MythTv-01 kernel: [    1.680256] ehci_hcd 0000:00:13.2: debug port 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.680278] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Feb  9 21:03:44 MythTv-01 kernel: [    1.692036] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Feb  9 21:03:44 MythTv-01 kernel: [    1.692103] usb usb2: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.692124] hub 2-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.692130] hub 2-0:1.0: 6 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.692182] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  9 21:03:44 MythTv-01 kernel: [    1.692199] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:03:44 MythTv-01 kernel: [    1.692214] ohci_hcd 0000:00:12.0: OHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.692238] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Feb  9 21:03:44 MythTv-01 kernel: [    1.692266] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Feb  9 21:03:44 MythTv-01 kernel: [    1.752080] usb usb3: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.752098] hub 3-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.752109] hub 3-0:1.0: 3 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.752154] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:03:44 MythTv-01 kernel: [    1.752167] ohci_hcd 0000:00:12.1: OHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.752192] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Feb  9 21:03:44 MythTv-01 kernel: [    1.752208] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Feb  9 21:03:44 MythTv-01 kernel: [    1.812082] usb usb4: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.812101] hub 4-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.812108] hub 4-0:1.0: 3 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.812155] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    1.812169] ohci_hcd 0000:00:13.0: OHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.812191] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Feb  9 21:03:44 MythTv-01 kernel: [    1.812219] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Feb  9 21:03:44 MythTv-01 kernel: [    1.872082] usb usb5: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.872101] hub 5-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.872109] hub 5-0:1.0: 3 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.872154] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    1.872167] ohci_hcd 0000:00:13.1: OHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.872189] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Feb  9 21:03:44 MythTv-01 kernel: [    1.872205] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Feb  9 21:03:44 MythTv-01 kernel: [    1.932082] usb usb6: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.932100] hub 6-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.932108] hub 6-0:1.0: 3 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.932156] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    1.932171] ohci_hcd 0000:00:14.5: OHCI Host Controller
Feb  9 21:03:44 MythTv-01 kernel: [    1.932195] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Feb  9 21:03:44 MythTv-01 kernel: [    1.932211] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Feb  9 21:03:44 MythTv-01 kernel: [    1.984064] ata2: SATA link down (SStatus 0 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    1.984091] ata3: SATA link down (SStatus 0 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    1.984116] ata1: SATA link down (SStatus 0 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    1.984140] ata6: SATA link down (SStatus 0 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    1.992084] usb usb7: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    1.992103] hub 7-0:1.0: USB hub found
Feb  9 21:03:44 MythTv-01 kernel: [    1.992111] hub 7-0:1.0: 2 ports detected
Feb  9 21:03:44 MythTv-01 kernel: [    1.992157] uhci_hcd: USB Universal Host Controller Interface driver
Feb  9 21:03:44 MythTv-01 kernel: [    1.992212] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.992214] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Feb  9 21:03:44 MythTv-01 kernel: [    1.992288] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.992338] mice: PS/2 mouse device common for all mice
Feb  9 21:03:44 MythTv-01 kernel: [    1.992406] rtc_cmos 00:05: RTC can wake from S4
Feb  9 21:03:44 MythTv-01 kernel: [    1.992428] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb  9 21:03:44 MythTv-01 kernel: [    1.992457] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Feb  9 21:03:44 MythTv-01 kernel: [    1.992528] device-mapper: uevent: version 1.0.3
Feb  9 21:03:44 MythTv-01 kernel: [    1.992605] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Feb  9 21:03:44 MythTv-01 kernel: [    1.992684] device-mapper: multipath: version 1.1.0 loaded
Feb  9 21:03:44 MythTv-01 kernel: [    1.992686] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb  9 21:03:44 MythTv-01 kernel: [    1.992763] EISA: Probing bus 0 at eisa.0
Feb  9 21:03:44 MythTv-01 kernel: [    1.992779] Cannot allocate resource for EISA slot 4
Feb  9 21:03:44 MythTv-01 kernel: [    1.992795] EISA: Detected 0 cards.
Feb  9 21:03:44 MythTv-01 kernel: [    1.992895] cpuidle: using governor ladder
Feb  9 21:03:44 MythTv-01 kernel: [    1.992897] cpuidle: using governor menu
Feb  9 21:03:44 MythTv-01 kernel: [    1.993212] TCP cubic registered
Feb  9 21:03:44 MythTv-01 kernel: [    1.993302] NET: Registered protocol family 10
Feb  9 21:03:44 MythTv-01 kernel: [    1.993592] lo: Disabled Privacy Extensions
Feb  9 21:03:44 MythTv-01 kernel: [    1.993803] NET: Registered protocol family 17
Feb  9 21:03:44 MythTv-01 kernel: [    1.993812] Bluetooth: L2CAP ver 2.13
Feb  9 21:03:44 MythTv-01 kernel: [    1.993813] Bluetooth: L2CAP socket layer initialized
Feb  9 21:03:44 MythTv-01 kernel: [    1.993815] Bluetooth: SCO (Voice Link) ver 0.6
Feb  9 21:03:44 MythTv-01 kernel: [    1.993816] Bluetooth: SCO socket layer initialized
Feb  9 21:03:44 MythTv-01 kernel: [    1.993865] Bluetooth: RFCOMM TTY layer initialized
Feb  9 21:03:44 MythTv-01 kernel: [    1.993867] Bluetooth: RFCOMM socket layer initialized
Feb  9 21:03:44 MythTv-01 kernel: [    1.993868] Bluetooth: RFCOMM ver 1.11
Feb  9 21:03:44 MythTv-01 kernel: [    1.993878] powernow-k8: Found 1 AMD Athlon(tm) II X2 240 Processor processors (2 cpu cores) (version 2.20.00)
Feb  9 21:03:44 MythTv-01 kernel: [    1.993904] powernow-k8:    0 : pstate 0 (2800 MHz)
Feb  9 21:03:44 MythTv-01 kernel: [    1.993906] powernow-k8:    1 : pstate 1 (2100 MHz)
Feb  9 21:03:44 MythTv-01 kernel: [    1.993907] powernow-k8:    2 : pstate 2 (1600 MHz)
Feb  9 21:03:44 MythTv-01 kernel: [    1.993909] powernow-k8:    3 : pstate 3 (800 MHz)
Feb  9 21:03:44 MythTv-01 kernel: [    1.993992] Using IPI No-Shortcut mode
Feb  9 21:03:44 MythTv-01 kernel: [    1.994071] registered taskstats version 1
Feb  9 21:03:44 MythTv-01 kernel: [    1.994161]   Magic number: 14:658:59
Feb  9 21:03:44 MythTv-01 kernel: [    1.994237] rtc_cmos 00:05: setting system clock to 2010-02-10 04:03:40 UTC (1265774620)
Feb  9 21:03:44 MythTv-01 kernel: [    1.994240] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  9 21:03:44 MythTv-01 kernel: [    1.994241] EDD information not available.
Feb  9 21:03:44 MythTv-01 kernel: [    2.017371] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Feb  9 21:03:44 MythTv-01 kernel: [    2.148039] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    2.148062] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  9 21:03:44 MythTv-01 kernel: [    2.148075] usb 4-2: new low speed USB device using ohci_hcd and address 2
Feb  9 21:03:44 MythTv-01 kernel: [    2.148827] ata4.00: ATAPI: ATAPI   iHOS104, WL0B, max UDMA/100, ATAPI AN
Feb  9 21:03:44 MythTv-01 kernel: [    2.149072] ata5.00: ATA-8: ST3500418AS, CC37, max UDMA/133
Feb  9 21:03:44 MythTv-01 kernel: [    2.149075] ata5.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Feb  9 21:03:44 MythTv-01 kernel: [    2.149599] ata4.00: configured for UDMA/100
Feb  9 21:03:44 MythTv-01 kernel: [    2.150319] ata5.00: configured for UDMA/133
Feb  9 21:03:44 MythTv-01 kernel: [    2.174890] scsi 3:0:0:0: CD-ROM            ATAPI    iHOS104          WL0B PQ: 0 ANSI: 5
Feb  9 21:03:44 MythTv-01 kernel: [    2.182654] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
Feb  9 21:03:44 MythTv-01 kernel: [    2.182657] Uniform CD-ROM driver Revision: 3.20
Feb  9 21:03:44 MythTv-01 kernel: [    2.182764] sr 3:0:0:0: Attached scsi generic sg0 type 5
Feb  9 21:03:44 MythTv-01 kernel: [    2.182868] scsi 4:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
Feb  9 21:03:44 MythTv-01 kernel: [    2.182979] sd 4:0:0:0: Attached scsi generic sg1 type 0
Feb  9 21:03:44 MythTv-01 kernel: [    2.183117] sd 4:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb  9 21:03:44 MythTv-01 kernel: [    2.183143] sd 4:0:0:0: [sda] Write Protect is off
Feb  9 21:03:44 MythTv-01 kernel: [    2.183157] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  9 21:03:44 MythTv-01 kernel: [    2.183238]  sda: sda1 sda2 sda3 < sda5 >
Feb  9 21:03:44 MythTv-01 kernel: [    2.203234] sd 4:0:0:0: [sda] Attached SCSI disk
Feb  9 21:03:44 MythTv-01 kernel: [    2.319077] usb 4-2: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    2.336104] Freeing unused kernel memory: 544k freed
Feb  9 21:03:44 MythTv-01 kernel: [    2.336281] Write protecting the kernel text: 4592k
Feb  9 21:03:44 MythTv-01 kernel: [    2.336327] Write protecting the kernel read-only data: 1836k
Feb  9 21:03:44 MythTv-01 kernel: [    2.414835] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb  9 21:03:44 MythTv-01 kernel: [    2.414850] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    2.415340] eth0: RTL8168c/8111c at 0xf8248000, 6c:f0:49:06:48:26, XID 3c4000c0 IRQ 27
Feb  9 21:03:44 MythTv-01 kernel: [    2.456530] ohci1394 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb  9 21:03:44 MythTv-01 kernel: [    2.456559] usb 5-1: new low speed USB device using ohci_hcd and address 2
Feb  9 21:03:44 MythTv-01 kernel: [    2.461786] usbcore: registered new interface driver hiddev
Feb  9 21:03:44 MythTv-01 kernel: [    2.468157] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input4
Feb  9 21:03:44 MythTv-01 kernel: [    2.468209] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:12.1-2/input0
Feb  9 21:03:44 MythTv-01 kernel: [    2.468221] usbcore: registered new interface driver usbhid
Feb  9 21:03:44 MythTv-01 kernel: [    2.468223] usbhid: v2.6:USB HID core driver
Feb  9 21:03:44 MythTv-01 kernel: [    2.514062] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Feb  9 21:03:44 MythTv-01 kernel: [    2.524140] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  9 21:03:44 MythTv-01 kernel: [    2.580065] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb  9 21:03:44 MythTv-01 kernel: [    2.620059] usb 5-1: configuration #1 chosen from 1 choice
Feb  9 21:03:44 MythTv-01 kernel: [    3.370166] PM: Starting manual resume from disk
Feb  9 21:03:44 MythTv-01 kernel: [    3.378411] EXT4-fs (sda1): barriers enabled
Feb  9 21:03:44 MythTv-01 kernel: [    3.383849] kjournald2 starting: pid 415, dev sda1:8, commit interval 5 seconds
Feb  9 21:03:44 MythTv-01 kernel: [    3.383859] EXT4-fs (sda1): delayed allocation enabled
Feb  9 21:03:44 MythTv-01 kernel: [    3.383863] EXT4-fs: file extents enabled
Feb  9 21:03:44 MythTv-01 kernel: [    3.384358] EXT4-fs: mballoc enabled
Feb  9 21:03:44 MythTv-01 kernel: [    3.384367] EXT4-fs (sda1): mounted filesystem with ordered data mode
Feb  9 21:03:44 MythTv-01 kernel: [    3.732534] type=1505 audit(1265774622.238:2): operation="profile_load" pid=438 name=/sbin/dhclient3
Feb  9 21:03:44 MythTv-01 kernel: [    3.732740] type=1505 audit(1265774622.238:3): operation="profile_load" pid=438 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb  9 21:03:44 MythTv-01 kernel: [    3.732855] type=1505 audit(1265774622.238:4): operation="profile_load" pid=438 name=/usr/lib/connman/scripts/dhclient-script
Feb  9 21:03:44 MythTv-01 kernel: [    3.766145] type=1505 audit(1265774622.270:5): operation="profile_load" pid=439 name=/usr/bin/evince
Feb  9 21:03:44 MythTv-01 kernel: [    3.769445] type=1505 audit(1265774622.274:6): operation="profile_load" pid=439 name=/usr/bin/evince-previewer
Feb  9 21:03:44 MythTv-01 kernel: [    3.771402] type=1505 audit(1265774622.274:7): operation="profile_load" pid=439 name=/usr/bin/evince-thumbnailer
Feb  9 21:03:44 MythTv-01 kernel: [    3.782606] type=1505 audit(1265774622.286:8): operation="profile_load" pid=441 name=/usr/sbin/mysqld
Feb  9 21:03:44 MythTv-01 kernel: [    3.784165] type=1505 audit(1265774622.286:9): operation="profile_load" pid=442 name=/usr/sbin/ntpd
Feb  9 21:03:44 MythTv-01 kernel: [    3.785473] type=1505 audit(1265774622.290:10): operation="profile_load" pid=443 name=/usr/sbin/tcpdump
Feb  9 21:03:44 MythTv-01 kernel: [    4.160225] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k
Feb  9 21:03:44 MythTv-01 kernel: [    4.402600] EXT4-fs (sda1): internal journal on sda1:8
Feb  9 21:03:44 MythTv-01 kernel: [    4.449486] udev: starting version 147
Feb  9 21:03:44 MythTv-01 kernel: [    4.965776] ieee1394: raw1394: /dev/raw1394 device initialized
Feb  9 21:03:44 MythTv-01 kernel: [    4.967986] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb  9 21:03:44 MythTv-01 kernel: [    4.969259] lp: driver loaded but no devices found
Feb  9 21:03:44 MythTv-01 kernel: [    4.973306] parport_pc 00:09: reported by Plug and Play ACPI
Feb  9 21:03:44 MythTv-01 kernel: [    4.973359] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  9 21:03:44 MythTv-01 kernel: [    4.983978] Linux agpgart interface v0.103
Feb  9 21:03:44 MythTv-01 kernel: [    5.032599] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Feb  9 21:03:44 MythTv-01 kernel: [    5.035075] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb  9 21:03:44 MythTv-01 kernel: [    5.035441] SGI XFS Quota Management subsystem
Feb  9 21:03:44 MythTv-01 kernel: [    5.037560] Linux video capture interface: v2.00
Feb  9 21:03:44 MythTv-01 kernel: [    5.039862] ppdev: user-space parallel port driver
Feb  9 21:03:44 MythTv-01 kernel: [    5.068655] lp0: using parport0 (interrupt-driven).
Feb  9 21:03:44 MythTv-01 kernel: [    5.697430] nvidia: module license 'NVIDIA' taints kernel.
Feb  9 21:03:44 MythTv-01 kernel: [    5.697434] Disabling lock debugging due to kernel taint
Feb  9 21:03:44 MythTv-01 kernel: [    5.853195] type=1505 audit(1265774624.358:11): operation="profile_replace" pid=778 name=/sbin/dhclient3
Feb  9 21:03:44 MythTv-01 kernel: [    5.853403] type=1505 audit(1265774624.358:12): operation="profile_replace" pid=778 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb  9 21:03:44 MythTv-01 kernel: [    5.853519] type=1505 audit(1265774624.358:13): operation="profile_replace" pid=778 name=/usr/lib/connman/scripts/dhclient-script
Feb  9 21:03:44 MythTv-01 kernel: [    5.857922] type=1505 audit(1265774624.362:14): operation="profile_replace" pid=782 name=/usr/bin/evince
Feb  9 21:03:44 MythTv-01 kernel: [    5.861235] type=1505 audit(1265774624.366:15): operation="profile_replace" pid=782 name=/usr/bin/evince-previewer
Feb  9 21:03:44 MythTv-01 kernel: [    5.863209] type=1505 audit(1265774624.366:16): operation="profile_replace" pid=782 name=/usr/bin/evince-thumbnailer
Feb  9 21:03:44 MythTv-01 kernel: [    5.867381] type=1505 audit(1265774624.370:17): operation="profile_replace" pid=784 name=/usr/sbin/mysqld
Feb  9 21:03:44 MythTv-01 kernel: [    5.868307] type=1505 audit(1265774624.370:18): operation="profile_replace" pid=785 name=/usr/sbin/ntpd
Feb  9 21:03:44 MythTv-01 kernel: [    5.869493] type=1505 audit(1265774624.374:19): operation="profile_replace" pid=786 name=/usr/sbin/tcpdump
Feb  9 21:03:44 MythTv-01 kernel: [    5.951858] XFS mounting filesystem sda5
Feb  9 21:03:44 MythTv-01 kernel: [    5.953365] lirc_dev: IR Remote Control driver registered, major 61
Feb  9 21:03:44 MythTv-01 kernel: [    5.953594] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:03:44 MythTv-01 kernel: [    5.953698] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
Feb  9 21:03:44 MythTv-01 kernel: [    5.987834] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Feb  9 21:03:44 MythTv-01 kernel: [    5.987855] lirc_dev: lirc_register_driver: sample_rate: 0
Feb  9 21:03:44 MythTv-01 kernel: [    5.987885] lirc_imon: Registered iMON driver (lirc minor: 0)
Feb  9 21:03:44 MythTv-01 kernel: [    5.987919] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input5
Feb  9 21:03:44 MythTv-01 kernel: [    5.990608] lirc_imon: iMON device (15c2:0038, intf0) on usb<5:2> initialized
Feb  9 21:03:44 MythTv-01 kernel: [    5.992613] lirc_imon: iMON device (15c2:0038, intf1) on usb<5:2> initialized
Feb  9 21:03:44 MythTv-01 kernel: [    5.992644] usbcore: registered new interface driver lirc_imon
Feb  9 21:03:44 MythTv-01 kernel: [    6.234456] ivtv: Start initialization, version 1.4.1
Feb  9 21:03:44 MythTv-01 kernel: [    6.234503] ivtv0: Initializing card 0
Feb  9 21:03:44 MythTv-01 kernel: [    6.234506] ivtv0: Autodetected Hauppauge card (cx23416 based)
Feb  9 21:03:44 MythTv-01 kernel: [    6.234955] ivtv 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  9 21:03:44 MythTv-01 kernel: [    6.234964] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Feb  9 21:03:44 MythTv-01 kernel: [    6.299859] tveeprom 0-0050: Hauppauge model 26582, rev C299, serial# 8454218
Feb  9 21:03:44 MythTv-01 kernel: [    6.299862] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
Feb  9 21:03:44 MythTv-01 kernel: [    6.299865] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
Feb  9 21:03:44 MythTv-01 kernel: [    6.299866] tveeprom 0-0050: audio processor is CX25843 (idx 37)
Feb  9 21:03:44 MythTv-01 kernel: [    6.299868] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
Feb  9 21:03:44 MythTv-01 kernel: [    6.299870] tveeprom 0-0050: has no radio
Feb  9 21:03:44 MythTv-01 kernel: [    6.299872] ivtv0: Autodetected Hauppauge WinTV PVR-150
Feb  9 21:03:44 MythTv-01 kernel: [    6.400790] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Feb  9 21:03:44 MythTv-01 kernel: [    6.415895] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  9 21:03:44 MythTv-01 kernel: [    6.432240] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb  9 21:03:44 MythTv-01 kernel: [    6.481750] tuner-simple 0-0061: creating new instance
Feb  9 21:03:44 MythTv-01 kernel: [    6.481754] tuner-simple 0-0061: type set to 50 (TCL 2002N)
Feb  9 21:03:44 MythTv-01 kernel: [    6.482849] IRQ 20/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
Feb  9 21:03:44 MythTv-01 kernel: [    6.483046] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    6.483061] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    6.483075] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    6.483089] ivtv0: Registered device video24 for encoder PCM (320 kB)
Feb  9 21:03:44 MythTv-01 kernel: [    6.483091] ivtv0: Initialized card: Hauppauge WinTV PVR-150
Feb  9 21:03:44 MythTv-01 kernel: [    6.483105] ivtv: End initialization
Feb  9 21:03:45 MythTv-01 kernel: [    6.493640] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:03:45 MythTv-01 kernel: [    6.612633] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
Feb  9 21:03:45 MythTv-01 kernel: [    6.612803] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
Feb  9 21:03:45 MythTv-01 kernel: [    7.124531] ivtv 0000:03:06.0: firmware: requesting v4l-cx2341x-enc.fw
Feb  9 21:03:45 MythTv-01 kernel: [    7.339164] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Feb  9 21:03:46 MythTv-01 kernel: [    7.536712] ivtv0: Encoder revision: 0x02060039
Feb  9 21:03:46 MythTv-01 kernel: [    7.555742] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
Feb  9 21:03:46 MythTv-01 kernel: [    7.579654] r8169: eth0: link up
Feb  9 21:03:46 MythTv-01 kernel: [    7.579659] r8169: eth0: link up
Feb  9 21:03:46 MythTv-01 kernel: [    8.330192] type=1503 audit(1265774626.834:20): operation="open" pid=1109 parent=1108 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:03:49 MythTv-01 kernel: [   11.291817] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb  9 21:03:51 MythTv-01 kernel: [   11.676570] __ratelimit: 12 callbacks suppressed
Feb  9 21:03:51 MythTv-01 kernel: [   11.676573] type=1503 audit(1265774631.017:25): operation="open" pid=1456 parent=1455 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:03:51 MythTv-01 kernel: [   11.719883] type=1503 audit(1265774631.057:26): operation="open" pid=1467 parent=1466 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:45:43 MythTv-01 kernel: [ 2517.448762] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Feb  9 21:52:36 MythTv-01 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Feb  9 21:52:36 MythTv-01 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="775" x-info="http://www.rsyslog.com"] (re)start
Feb  9 21:52:36 MythTv-01 rsyslogd: rsyslogd's groupid changed to 102
Feb  9 21:52:36 MythTv-01 rsyslogd: rsyslogd's userid changed to 101
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic-pae)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] KERNEL supported cpus:
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Intel GenuineIntel
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   AMD AuthenticAMD
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   NSC Geode by NSC
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Cyrix CyrixInstead
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Centaur CentaurHauls
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Transmeta GenuineTMx86
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Transmeta TransmetaCPU
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   UMC UMC UMC UMC
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfde0000 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] DMI 2.4 present.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x1000000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] modified physical RAM map:
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfde0000 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] NX (Execute Disable) protection: active
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] RAMDISK: 3789d000 - 37fef16a
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Allocated new RAMDISK: 008b5000 - 0100716a
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Move RAMDISK from 000000003789d000 - 0000000037fef169 to 008b5000 - 01007169
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: RSDP 000f7260 00014 (v00 GBT   )
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: RSDT cfde3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: FACP cfde3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: DSDT cfde30c0 07420 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: FACS cfde0000 00040
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: SSDT cfdea5c0 0095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: HPET cfdeaf40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: MCFG cfdeaf80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: TAMG cfdeafc0 0029A (v01 GBT    GBT   B0 5455312E BG 53450101)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: APIC cfdea500 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] 3974MB HIGHMEM available.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] 889MB LOWMEM available.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   low ram: 0 - 379fe000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #5 [00008ae000 - 00008b4106]              BRK ==> [00008ae000 - 00008b4106]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #7 [00008b5000 - 000100716a]      NEW RAMDISK ==> [00008b5000 - 000100716a]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] found SMP MP-table at [c00f58c0] f58c0
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Zone PFN ranges:
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]   HighMem  0x000379fe -> 0x00130000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Movable zone start PFN for each node
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] early_node_map[4] active PFN ranges
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     0: 0x00000100 -> 0x000cfde0
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Using APIC driver default
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Allocating PCI resources starting at cfe00000 (gap: cfe00000:10200000)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PERCPU: Embedded 14 pages at c3618000, static data 35612 bytes
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038202
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=95382a00-f50c-4536-b1b6-9db37fa37b96 ro quiet splash
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Initializing CPU#0
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] allocated 24903680 bytes of page_cgroup
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00130000)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Memory: 4111092k/4980736k available (4590k kernel code, 79736k reserved, 2147k data, 544k init, 3280776k highmem)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] virtual kernel memory layout:
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]       .data : 0xc057b894 - 0xc07947e8   (2147 kB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000]       .text : 0xc0100000 - 0xc057b894   (4590 kB)
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Fast TSC calibration using PIT
Feb  9 21:52:36 MythTv-01 kernel: [    0.000000] Detected 2813.024 MHz processor.
Feb  9 21:52:36 MythTv-01 kernel: [    0.001743] Console: colour VGA+ 80x25
Feb  9 21:52:36 MythTv-01 kernel: [    0.001744] console [tty0] enabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.001885] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Feb  9 21:52:36 MythTv-01 kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5626.04 BogoMIPS (lpj=11252096)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004017] Security Framework initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.004028] AppArmor: AppArmor initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.004032] Mount-cache hash table entries: 512
Feb  9 21:52:36 MythTv-01 kernel: [    0.004099] Initializing cgroup subsys ns
Feb  9 21:52:36 MythTv-01 kernel: [    0.004102] Initializing cgroup subsys cpuacct
Feb  9 21:52:36 MythTv-01 kernel: [    0.004104] Initializing cgroup subsys memory
Feb  9 21:52:36 MythTv-01 kernel: [    0.004108] Initializing cgroup subsys freezer
Feb  9 21:52:36 MythTv-01 kernel: [    0.004110] Initializing cgroup subsys net_cls
Feb  9 21:52:36 MythTv-01 kernel: [    0.004117] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004119] CPU: L2 Cache: 1024K (64 bytes/line)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004120] CPU: Physical Processor ID: 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.004122] CPU: Processor Core ID: 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.004124] mce: CPU supports 6 MCE banks
Feb  9 21:52:36 MythTv-01 kernel: [    0.004130] using C1E aware idle routine
Feb  9 21:52:36 MythTv-01 kernel: [    0.004134] Performance Counters: AMD PMU driver.
Feb  9 21:52:36 MythTv-01 kernel: [    0.004136] ... version:                 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.004138] ... bit width:               48
Feb  9 21:52:36 MythTv-01 kernel: [    0.004139] ... generic counters:        4
Feb  9 21:52:36 MythTv-01 kernel: [    0.004140] ... value mask:              0000ffffffffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.004142] ... max period:              00007fffffffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.004143] ... fixed-purpose counters:  0
Feb  9 21:52:36 MythTv-01 kernel: [    0.004144] ... counter mask:            000000000000000f
Feb  9 21:52:36 MythTv-01 kernel: [    0.004147] Checking 'hlt' instruction... OK.
Feb  9 21:52:36 MythTv-01 kernel: [    0.021473] ACPI: Core revision 20090521
Feb  9 21:52:36 MythTv-01 kernel: [    0.032519] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  9 21:52:36 MythTv-01 kernel: [    0.074562] CPU0: AMD Athlon(tm) II X2 240 Processor stepping 02
Feb  9 21:52:36 MythTv-01 kernel: [    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] Initializing CPU#1
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] Calibrating delay using timer specific routine.. 5625.45 BogoMIPS (lpj=11250909)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] CPU: Processor Core ID: 1
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] mce: CPU supports 6 MCE banks
Feb  9 21:52:36 MythTv-01 kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Feb  9 21:52:36 MythTv-01 kernel: [    0.160469] CPU1: AMD Athlon(tm) II X2 240 Processor stepping 02
Feb  9 21:52:36 MythTv-01 kernel: [    0.160477] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Feb  9 21:52:36 MythTv-01 kernel: [    0.164010] Brought up 2 CPUs
Feb  9 21:52:36 MythTv-01 kernel: [    0.164012] Total of 2 processors activated (11251.50 BogoMIPS).
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] Booting paravirtualized kernel on bare hardware
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] regulator: core version 0.5
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] Time:  4:52:30  Date: 02/10/10
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] NET: Registered protocol family 16
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] EISA bus registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.164161] ACPI: bus type pci registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.164186] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Feb  9 21:52:36 MythTv-01 kernel: [    0.164188] PCI: MCFG area at e0000000 reserved in E820
Feb  9 21:52:36 MythTv-01 kernel: [    0.164190] PCI: Using MMCONFIG for extended config space
Feb  9 21:52:36 MythTv-01 kernel: [    0.164191] PCI: Using configuration type 1 for base access
Feb  9 21:52:36 MythTv-01 kernel: [    0.164737] bio: create slab <bio-0> at 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.171954] ACPI: Interpreter enabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.171961] ACPI: (supports S0 S3 S4 S5)
Feb  9 21:52:36 MythTv-01 kernel: [    0.171978] ACPI: Using IOAPIC for interrupt routing
Feb  9 21:52:36 MythTv-01 kernel: [    0.175105] ACPI: No dock devices found.
Feb  9 21:52:36 MythTv-01 kernel: [    0.175186] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  9 21:52:36 MythTv-01 kernel: [    0.175269] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Feb  9 21:52:36 MythTv-01 kernel: [    0.175271] pci 0000:00:02.0: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.175305] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Feb  9 21:52:36 MythTv-01 kernel: [    0.175307] pci 0000:00:0a.0: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.175596] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Feb  9 21:52:36 MythTv-01 kernel: [    0.175599] pci 0000:00:12.2: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.175792] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Feb  9 21:52:36 MythTv-01 kernel: [    0.175796] pci 0000:00:13.2: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.176032] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Feb  9 21:52:36 MythTv-01 kernel: [    0.176036] pci 0000:00:14.2: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.176440] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  9 21:52:36 MythTv-01 kernel: [    0.176444] pci 0000:02:00.0: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.176707] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
Feb  9 21:52:36 MythTv-01 kernel: [    0.176711] pci 0000:03:07.0: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.176825] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
Feb  9 21:52:36 MythTv-01 kernel: [    0.176829] pci 0000:03:0e.0: PME# disabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.176862] pci 0000:00:14.4: transparent bridge
Feb  9 21:52:36 MythTv-01 kernel: [    0.192758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.192827] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.192894] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.192960] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.193026] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.193092] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.193157] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.193223] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Feb  9 21:52:36 MythTv-01 kernel: [    0.193334] SCSI subsystem initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] usbcore: registered new interface driver usbfs
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] usbcore: registered new interface driver hub
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] usbcore: registered new device driver usb
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] ACPI: WMI: Mapper loaded
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] PCI: Using ACPI for IRQ routing
Feb  9 21:52:36 MythTv-01 kernel: [    0.193362] pci 0000:00:00.0: BAR 3: can't allocate resource
Feb  9 21:52:36 MythTv-01 kernel: [    0.204019] Bluetooth: Core ver 2.15
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] NET: Registered protocol family 31
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] Bluetooth: HCI device and connection manager initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] Bluetooth: HCI socket layer initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] NetLabel: Initializing
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] NetLabel:  domain hash size = 128
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  9 21:52:36 MythTv-01 kernel: [    0.204050] NetLabel:  unlabeled traffic allowed by default
Feb  9 21:52:36 MythTv-01 kernel: [    0.204066] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Feb  9 21:52:36 MythTv-01 kernel: [    0.204070] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Feb  9 21:52:36 MythTv-01 kernel: [    0.220022] pnp: PnP ACPI init
Feb  9 21:52:36 MythTv-01 kernel: [    0.220034] ACPI: bus type pnp registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.221980] pnp 00:0c: mem resource (0xd1a00-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.221983] pnp 00:0c: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.221986] pnp 00:0c: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.221988] pnp 00:0c: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.221991] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.221994] pnp 00:0c: mem resource (0x100000-0xcfddffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Feb  9 21:52:36 MythTv-01 kernel: [    0.222053] pnp: PnP ACPI: found 13 devices
Feb  9 21:52:36 MythTv-01 kernel: [    0.222054] ACPI: ACPI bus type pnp unregistered
Feb  9 21:52:36 MythTv-01 kernel: [    0.222057] PnPBIOS: Disabled by ACPI PNP
Feb  9 21:52:36 MythTv-01 kernel: [    0.222064] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222066] system 00:01: ioport range 0x220-0x225 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222069] system 00:01: ioport range 0x290-0x294 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222072] system 00:02: ioport range 0x4100-0x411f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222075] system 00:02: ioport range 0x228-0x22f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222077] system 00:02: ioport range 0x40b-0x40b has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222079] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222081] system 00:02: ioport range 0xc00-0xc01 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222083] system 00:02: ioport range 0xc14-0xc14 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222085] system 00:02: ioport range 0xc50-0xc52 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222087] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222089] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222091] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222093] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222095] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222098] system 00:02: ioport range 0x4000-0x40fe has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222100] system 00:02: ioport range 0x4210-0x4217 has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222102] system 00:02: ioport range 0xb00-0xb0f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222104] system 00:02: ioport range 0xb10-0xb1f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222106] system 00:02: ioport range 0xb20-0xb3f has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222112] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222116] system 00:0c: iomem range 0xcfde0000-0xcfdfffff could not be reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222118] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222121] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222123] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.222126] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Feb  9 21:52:36 MythTv-01 kernel: [    0.256726] AppArmor: AppArmor Filesystem Enabled
Feb  9 21:52:36 MythTv-01 kernel: [    0.256749] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Feb  9 21:52:36 MythTv-01 kernel: [    0.256751] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256754] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256757] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256761] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
Feb  9 21:52:36 MythTv-01 kernel: [    0.256763] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256766] pci 0000:00:0a.0:   MEM window: 0xfdd00000-0xfddfffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256769] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256772] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Feb  9 21:52:36 MythTv-01 kernel: [    0.256775] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256780] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256784] pci 0000:00:14.4:   PREFETCH window: 0xf4000000-0xf7ffffff
Feb  9 21:52:36 MythTv-01 kernel: [    0.256800] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    0.256808] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    0.256865] NET: Registered protocol family 2
Feb  9 21:52:36 MythTv-01 kernel: [    0.256928] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.257127] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.257496] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.257685] TCP: Hash tables configured (established 131072 bind 65536)
Feb  9 21:52:36 MythTv-01 kernel: [    0.257687] TCP reno registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.257743] NET: Registered protocol family 1
Feb  9 21:52:36 MythTv-01 kernel: [    0.257784] Trying to unpack rootfs image as initramfs...
Feb  9 21:52:36 MythTv-01 kernel: [    0.399789] Freeing initrd memory: 7496k freed
Feb  9 21:52:36 MythTv-01 kernel: [    0.401719] cpufreq-nforce2: No nForce2 chipset.
Feb  9 21:52:36 MythTv-01 kernel: [    0.401736] Scanning for low memory corruption every 60 seconds
Feb  9 21:52:36 MythTv-01 kernel: [    0.401798] audit: initializing netlink socket (disabled)
Feb  9 21:52:36 MythTv-01 kernel: [    0.401808] type=2000 audit(1265777550.399:1): initialized
Feb  9 21:52:36 MythTv-01 kernel: [    0.407909] highmem bounce pool size: 64 pages
Feb  9 21:52:36 MythTv-01 kernel: [    0.407913] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb  9 21:52:36 MythTv-01 kernel: [    0.408772] VFS: Disk quotas dquot_6.5.2
Feb  9 21:52:36 MythTv-01 kernel: [    0.408810] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  9 21:52:36 MythTv-01 kernel: [    0.409168] fuse init (API version 7.12)
Feb  9 21:52:36 MythTv-01 kernel: [    0.409217] msgmni has been set to 1638
Feb  9 21:52:36 MythTv-01 kernel: [    0.409368] alg: No test for stdrng (krng)
Feb  9 21:52:36 MythTv-01 kernel: [    0.409383] io scheduler noop registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.409384] io scheduler anticipatory registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.409386] io scheduler deadline registered
Feb  9 21:52:36 MythTv-01 kernel: [    0.409412] io scheduler cfq registered (default)
Feb  9 21:52:36 MythTv-01 kernel: [    1.252035] pci 0000:00:13.0: OHCI: BIOS handoff failed (BIOS bug?) 00000184
Feb  9 21:52:36 MythTv-01 kernel: [    1.308259] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  9 21:52:36 MythTv-01 kernel: [    1.308275] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  9 21:52:36 MythTv-01 kernel: [    1.308355] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Feb  9 21:52:36 MythTv-01 kernel: [    1.308357] ACPI: Power Button [PWRF]
Feb  9 21:52:36 MythTv-01 kernel: [    1.308389] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Feb  9 21:52:36 MythTv-01 kernel: [    1.308391] ACPI: Power Button [PWRB]
Feb  9 21:52:36 MythTv-01 kernel: [    1.308612] processor LNXCPU:00: registered as cooling_device0
Feb  9 21:52:36 MythTv-01 kernel: [    1.308644] processor LNXCPU:01: registered as cooling_device1
Feb  9 21:52:36 MythTv-01 kernel: [    1.310031] isapnp: Scanning for PnP cards...
Feb  9 21:52:36 MythTv-01 kernel: [    1.663675] isapnp: No Plug & Play device found
Feb  9 21:52:36 MythTv-01 kernel: [    1.664372] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb  9 21:52:36 MythTv-01 kernel: [    1.664473] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 21:52:36 MythTv-01 kernel: [    1.664716] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 21:52:36 MythTv-01 kernel: [    1.665300] brd: module loaded
Feb  9 21:52:36 MythTv-01 kernel: [    1.665554] loop: module loaded
Feb  9 21:52:36 MythTv-01 kernel: [    1.665600] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Feb  9 21:52:36 MythTv-01 kernel: [    1.665655] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.665753] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Feb  9 21:52:36 MythTv-01 kernel: [    1.665756] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part
Feb  9 21:52:36 MythTv-01 kernel: [    1.666068] scsi0 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666162] scsi1 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666199] scsi2 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666236] scsi3 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666273] scsi4 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666309] scsi5 : ahci
Feb  9 21:52:36 MythTv-01 kernel: [    1.666393] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666396] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666399] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666402] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666405] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666408] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 22
Feb  9 21:52:36 MythTv-01 kernel: [    1.666588] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:52:36 MythTv-01 kernel: [    1.666692] scsi6 : pata_atiixp
Feb  9 21:52:36 MythTv-01 kernel: [    1.666728] scsi7 : pata_atiixp
Feb  9 21:52:36 MythTv-01 kernel: [    1.667417] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Feb  9 21:52:36 MythTv-01 kernel: [    1.667419] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Feb  9 21:52:36 MythTv-01 kernel: [    1.667877] Fixed MDIO Bus: probed
Feb  9 21:52:36 MythTv-01 kernel: [    1.667899] PPP generic driver version 2.4.2
Feb  9 21:52:36 MythTv-01 kernel: [    1.667965] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  9 21:52:36 MythTv-01 kernel: [    1.667986] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  9 21:52:36 MythTv-01 kernel: [    1.667998] ehci_hcd 0000:00:12.2: EHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.668039] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.668066] ehci_hcd 0000:00:12.2: debug port 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.668086] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Feb  9 21:52:36 MythTv-01 kernel: [    1.680036] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Feb  9 21:52:36 MythTv-01 kernel: [    1.680104] usb usb1: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.680126] hub 1-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.680131] hub 1-0:1.0: 6 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.680194] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb  9 21:52:36 MythTv-01 kernel: [    1.680209] ehci_hcd 0000:00:13.2: EHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.680230] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Feb  9 21:52:36 MythTv-01 kernel: [    1.680257] ehci_hcd 0000:00:13.2: debug port 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.680280] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Feb  9 21:52:36 MythTv-01 kernel: [    1.692037] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Feb  9 21:52:36 MythTv-01 kernel: [    1.692105] usb usb2: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.692127] hub 2-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.692132] hub 2-0:1.0: 6 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.692184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  9 21:52:36 MythTv-01 kernel: [    1.692202] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:52:36 MythTv-01 kernel: [    1.692216] ohci_hcd 0000:00:12.0: OHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.692241] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Feb  9 21:52:36 MythTv-01 kernel: [    1.692269] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Feb  9 21:52:36 MythTv-01 kernel: [    1.752081] usb usb3: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.752099] hub 3-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.752110] hub 3-0:1.0: 3 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.752154] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:52:36 MythTv-01 kernel: [    1.752168] ohci_hcd 0000:00:12.1: OHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.752192] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Feb  9 21:52:36 MythTv-01 kernel: [    1.752208] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Feb  9 21:52:36 MythTv-01 kernel: [    1.812082] usb usb4: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.812101] hub 4-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.812109] hub 4-0:1.0: 3 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.812154] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    1.812169] ohci_hcd 0000:00:13.0: OHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.812190] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Feb  9 21:52:36 MythTv-01 kernel: [    1.812219] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Feb  9 21:52:36 MythTv-01 kernel: [    1.872082] usb usb5: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.872101] hub 5-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.872109] hub 5-0:1.0: 3 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.872154] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    1.872167] ohci_hcd 0000:00:13.1: OHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.872189] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Feb  9 21:52:36 MythTv-01 kernel: [    1.872205] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Feb  9 21:52:36 MythTv-01 kernel: [    1.932082] usb usb6: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.932101] hub 6-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.932109] hub 6-0:1.0: 3 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.932156] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    1.932171] ohci_hcd 0000:00:14.5: OHCI Host Controller
Feb  9 21:52:36 MythTv-01 kernel: [    1.932194] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Feb  9 21:52:36 MythTv-01 kernel: [    1.932210] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Feb  9 21:52:36 MythTv-01 kernel: [    1.984045] ata1: SATA link down (SStatus 0 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    1.984073] ata3: SATA link down (SStatus 0 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    1.984117] ata6: SATA link down (SStatus 0 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    1.984159] ata2: SATA link down (SStatus 0 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    1.992087] usb usb7: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    1.992107] hub 7-0:1.0: USB hub found
Feb  9 21:52:36 MythTv-01 kernel: [    1.992115] hub 7-0:1.0: 2 ports detected
Feb  9 21:52:36 MythTv-01 kernel: [    1.992160] uhci_hcd: USB Universal Host Controller Interface driver
Feb  9 21:52:36 MythTv-01 kernel: [    1.992216] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.992218] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Feb  9 21:52:36 MythTv-01 kernel: [    1.992292] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.992341] mice: PS/2 mouse device common for all mice
Feb  9 21:52:36 MythTv-01 kernel: [    1.992410] rtc_cmos 00:05: RTC can wake from S4
Feb  9 21:52:36 MythTv-01 kernel: [    1.992431] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb  9 21:52:36 MythTv-01 kernel: [    1.992461] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Feb  9 21:52:36 MythTv-01 kernel: [    1.992526] device-mapper: uevent: version 1.0.3
Feb  9 21:52:36 MythTv-01 kernel: [    1.992601] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Feb  9 21:52:36 MythTv-01 kernel: [    1.992681] device-mapper: multipath: version 1.1.0 loaded
Feb  9 21:52:36 MythTv-01 kernel: [    1.992683] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb  9 21:52:36 MythTv-01 kernel: [    1.992760] EISA: Probing bus 0 at eisa.0
Feb  9 21:52:36 MythTv-01 kernel: [    1.992777] Cannot allocate resource for EISA slot 4
Feb  9 21:52:36 MythTv-01 kernel: [    1.992792] EISA: Detected 0 cards.
Feb  9 21:52:36 MythTv-01 kernel: [    1.992895] cpuidle: using governor ladder
Feb  9 21:52:36 MythTv-01 kernel: [    1.992896] cpuidle: using governor menu
Feb  9 21:52:36 MythTv-01 kernel: [    1.993212] TCP cubic registered
Feb  9 21:52:36 MythTv-01 kernel: [    1.993302] NET: Registered protocol family 10
Feb  9 21:52:36 MythTv-01 kernel: [    1.993591] lo: Disabled Privacy Extensions
Feb  9 21:52:36 MythTv-01 kernel: [    1.993802] NET: Registered protocol family 17
Feb  9 21:52:36 MythTv-01 kernel: [    1.993812] Bluetooth: L2CAP ver 2.13
Feb  9 21:52:36 MythTv-01 kernel: [    1.993813] Bluetooth: L2CAP socket layer initialized
Feb  9 21:52:36 MythTv-01 kernel: [    1.993815] Bluetooth: SCO (Voice Link) ver 0.6
Feb  9 21:52:36 MythTv-01 kernel: [    1.993816] Bluetooth: SCO socket layer initialized
Feb  9 21:52:36 MythTv-01 kernel: [    1.993862] Bluetooth: RFCOMM TTY layer initialized
Feb  9 21:52:36 MythTv-01 kernel: [    1.993864] Bluetooth: RFCOMM socket layer initialized
Feb  9 21:52:36 MythTv-01 kernel: [    1.993865] Bluetooth: RFCOMM ver 1.11
Feb  9 21:52:36 MythTv-01 kernel: [    1.993875] powernow-k8: Found 1 AMD Athlon(tm) II X2 240 Processor processors (2 cpu cores) (version 2.20.00)
Feb  9 21:52:36 MythTv-01 kernel: [    1.993901] powernow-k8:    0 : pstate 0 (2800 MHz)
Feb  9 21:52:36 MythTv-01 kernel: [    1.993903] powernow-k8:    1 : pstate 1 (2100 MHz)
Feb  9 21:52:36 MythTv-01 kernel: [    1.993904] powernow-k8:    2 : pstate 2 (1600 MHz)
Feb  9 21:52:36 MythTv-01 kernel: [    1.993906] powernow-k8:    3 : pstate 3 (800 MHz)
Feb  9 21:52:36 MythTv-01 kernel: [    1.993989] Using IPI No-Shortcut mode
Feb  9 21:52:36 MythTv-01 kernel: [    1.994070] registered taskstats version 1
Feb  9 21:52:36 MythTv-01 kernel: [    1.994160]   Magic number: 14:485:868
Feb  9 21:52:36 MythTv-01 kernel: [    1.994236] rtc_cmos 00:05: setting system clock to 2010-02-10 04:52:32 UTC (1265777552)
Feb  9 21:52:36 MythTv-01 kernel: [    1.994239] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  9 21:52:36 MythTv-01 kernel: [    1.994240] EDD information not available.
Feb  9 21:52:36 MythTv-01 kernel: [    2.018780] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Feb  9 21:52:36 MythTv-01 kernel: [    2.148039] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    2.148064] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  9 21:52:36 MythTv-01 kernel: [    2.148076] usb 4-2: new low speed USB device using ohci_hcd and address 2
Feb  9 21:52:36 MythTv-01 kernel: [    2.148922] ata4.00: ATAPI: ATAPI   iHOS104, WL0B, max UDMA/100, ATAPI AN
Feb  9 21:52:36 MythTv-01 kernel: [    2.149128] ata5.00: ATA-8: ST3500418AS, CC37, max UDMA/133
Feb  9 21:52:36 MythTv-01 kernel: [    2.149131] ata5.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Feb  9 21:52:36 MythTv-01 kernel: [    2.149721] ata4.00: configured for UDMA/100
Feb  9 21:52:36 MythTv-01 kernel: [    2.150342] ata5.00: configured for UDMA/133
Feb  9 21:52:36 MythTv-01 kernel: [    2.174930] scsi 3:0:0:0: CD-ROM            ATAPI    iHOS104          WL0B PQ: 0 ANSI: 5
Feb  9 21:52:36 MythTv-01 kernel: [    2.182102] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
Feb  9 21:52:36 MythTv-01 kernel: [    2.182105] Uniform CD-ROM driver Revision: 3.20
Feb  9 21:52:36 MythTv-01 kernel: [    2.182213] sr 3:0:0:0: Attached scsi generic sg0 type 5
Feb  9 21:52:36 MythTv-01 kernel: [    2.182318] scsi 4:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
Feb  9 21:52:36 MythTv-01 kernel: [    2.182430] sd 4:0:0:0: Attached scsi generic sg1 type 0
Feb  9 21:52:36 MythTv-01 kernel: [    2.182443] sd 4:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb  9 21:52:36 MythTv-01 kernel: [    2.182468] sd 4:0:0:0: [sda] Write Protect is off
Feb  9 21:52:36 MythTv-01 kernel: [    2.182483] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  9 21:52:36 MythTv-01 kernel: [    2.182570]  sda: sda1 sda2 sda3 < sda5 >
Feb  9 21:52:36 MythTv-01 kernel: [    2.205267] sd 4:0:0:0: [sda] Attached SCSI disk
Feb  9 21:52:36 MythTv-01 kernel: [    2.319116] usb 4-2: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    2.336106] Freeing unused kernel memory: 544k freed
Feb  9 21:52:36 MythTv-01 kernel: [    2.336285] Write protecting the kernel text: 4592k
Feb  9 21:52:36 MythTv-01 kernel: [    2.336330] Write protecting the kernel read-only data: 1836k
Feb  9 21:52:36 MythTv-01 kernel: [    2.444175] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb  9 21:52:36 MythTv-01 kernel: [    2.444190] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:36 MythTv-01 kernel: [    2.444788] eth0: RTL8168c/8111c at 0xf8250000, 6c:f0:49:06:48:26, XID 3c4000c0 IRQ 27
Feb  9 21:52:36 MythTv-01 kernel: [    2.457201] ohci1394 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb  9 21:52:36 MythTv-01 kernel: [    2.457301] usb 5-1: new low speed USB device using ohci_hcd and address 2
Feb  9 21:52:36 MythTv-01 kernel: [    2.466610] usbcore: registered new interface driver hiddev
Feb  9 21:52:36 MythTv-01 kernel: [    2.473198] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input4
Feb  9 21:52:36 MythTv-01 kernel: [    2.473250] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:12.1-2/input0
Feb  9 21:52:36 MythTv-01 kernel: [    2.473262] usbcore: registered new interface driver usbhid
Feb  9 21:52:36 MythTv-01 kernel: [    2.473265] usbhid: v2.6:USB HID core driver
Feb  9 21:52:36 MythTv-01 kernel: [    2.514572] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Feb  9 21:52:36 MythTv-01 kernel: [    2.524629] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  9 21:52:36 MythTv-01 kernel: [    2.580560] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb  9 21:52:36 MythTv-01 kernel: [    2.620114] usb 5-1: configuration #1 chosen from 1 choice
Feb  9 21:52:36 MythTv-01 kernel: [    3.355184] PM: Starting manual resume from disk
Feb  9 21:52:36 MythTv-01 kernel: [    3.357667] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Feb  9 21:52:36 MythTv-01 kernel: [    3.357671] EXT4-fs (sda1): write access will be enabled during recovery
Feb  9 21:52:36 MythTv-01 kernel: [    3.363880] EXT4-fs (sda1): barriers enabled
Feb  9 21:52:36 MythTv-01 kernel: [    3.869701] kjournald2 starting: pid 434, dev sda1:8, commit interval 5 seconds
Feb  9 21:52:36 MythTv-01 kernel: [    3.869715] EXT4-fs (sda1): delayed allocation enabled
Feb  9 21:52:36 MythTv-01 kernel: [    3.869719] EXT4-fs: file extents enabled
Feb  9 21:52:36 MythTv-01 kernel: [    3.870213] EXT4-fs: mballoc enabled
Feb  9 21:52:36 MythTv-01 kernel: [    3.870223] EXT4-fs (sda1): orphan cleanup on readonly fs
Feb  9 21:52:36 MythTv-01 kernel: [    3.870271] EXT4-fs (sda1): 5 orphan inodes deleted
Feb  9 21:52:36 MythTv-01 kernel: [    3.870273] EXT4-fs (sda1): recovery complete
Feb  9 21:52:36 MythTv-01 kernel: [    4.079026] EXT4-fs (sda1): mounted filesystem with ordered data mode
Feb  9 21:52:36 MythTv-01 kernel: [    4.342375] type=1505 audit(1265777554.846:2): operation="profile_load" pid=457 name=/sbin/dhclient3
Feb  9 21:52:36 MythTv-01 kernel: [    4.342584] type=1505 audit(1265777554.846:3): operation="profile_load" pid=457 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb  9 21:52:36 MythTv-01 kernel: [    4.342698] type=1505 audit(1265777554.846:4): operation="profile_load" pid=457 name=/usr/lib/connman/scripts/dhclient-script
Feb  9 21:52:36 MythTv-01 kernel: [    4.359160] type=1505 audit(1265777554.862:5): operation="profile_load" pid=458 name=/usr/bin/evince
Feb  9 21:52:36 MythTv-01 kernel: [    4.362467] type=1505 audit(1265777554.866:6): operation="profile_load" pid=458 name=/usr/bin/evince-previewer
Feb  9 21:52:36 MythTv-01 kernel: [    4.364423] type=1505 audit(1265777554.866:7): operation="profile_load" pid=458 name=/usr/bin/evince-thumbnailer
Feb  9 21:52:36 MythTv-01 kernel: [    4.375799] type=1505 audit(1265777554.878:8): operation="profile_load" pid=460 name=/usr/sbin/mysqld
Feb  9 21:52:36 MythTv-01 kernel: [    4.400938] type=1505 audit(1265777554.906:9): operation="profile_load" pid=461 name=/usr/sbin/ntpd
Feb  9 21:52:36 MythTv-01 kernel: [    4.402482] type=1505 audit(1265777554.906:10): operation="profile_load" pid=462 name=/usr/sbin/tcpdump
Feb  9 21:52:36 MythTv-01 kernel: [    4.770107] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k
Feb  9 21:52:36 MythTv-01 kernel: [    5.021074] EXT4-fs (sda1): internal journal on sda1:8
Feb  9 21:52:36 MythTv-01 kernel: [    5.161845] udev: starting version 147
Feb  9 21:52:36 MythTv-01 kernel: [    5.542665] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Feb  9 21:52:36 MythTv-01 kernel: [    5.546009] ieee1394: raw1394: /dev/raw1394 device initialized
Feb  9 21:52:36 MythTv-01 kernel: [    5.547912] lp: driver loaded but no devices found
Feb  9 21:52:36 MythTv-01 kernel: [    5.552631] SGI XFS Quota Management subsystem
Feb  9 21:52:36 MythTv-01 kernel: [    5.633191] parport_pc 00:09: reported by Plug and Play ACPI
Feb  9 21:52:36 MythTv-01 kernel: [    5.633244] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  9 21:52:36 MythTv-01 kernel: [    5.639344] lirc_dev: IR Remote Control driver registered, major 61
Feb  9 21:52:36 MythTv-01 kernel: [    5.643797] Linux agpgart interface v0.103
Feb  9 21:52:36 MythTv-01 kernel: [    5.645736] ppdev: user-space parallel port driver
Feb  9 21:52:36 MythTv-01 kernel: [    5.648718] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb  9 21:52:36 MythTv-01 kernel: [    5.723760] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Feb  9 21:52:36 MythTv-01 kernel: [    5.723778] lirc_dev: lirc_register_driver: sample_rate: 0
Feb  9 21:52:36 MythTv-01 kernel: [    5.723806] lirc_imon: Registered iMON driver (lirc minor: 0)
Feb  9 21:52:36 MythTv-01 kernel: [    5.723838] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input5
Feb  9 21:52:36 MythTv-01 kernel: [    5.726920] lirc_imon: iMON device (15c2:0038, intf0) on usb<5:2> initialized
Feb  9 21:52:36 MythTv-01 kernel: [    5.728649] lp0: using parport0 (interrupt-driven).
Feb  9 21:52:36 MythTv-01 kernel: [    5.729992] lirc_imon: iMON device (15c2:0038, intf1) on usb<5:2> initialized
Feb  9 21:52:36 MythTv-01 kernel: [    5.730010] usbcore: registered new interface driver lirc_imon
Feb  9 21:52:36 MythTv-01 kernel: [    5.809433] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb  9 21:52:36 MythTv-01 kernel: [    5.819590] Linux video capture interface: v2.00
Feb  9 21:52:36 MythTv-01 kernel: [    6.122939] XFS mounting filesystem sda5
Feb  9 21:52:36 MythTv-01 kernel: [    6.330986] type=1505 audit(1265777556.834:11): operation="profile_replace" pid=853 name=/sbin/dhclient3
Feb  9 21:52:36 MythTv-01 kernel: [    6.331197] type=1505 audit(1265777556.834:12): operation="profile_replace" pid=853 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb  9 21:52:36 MythTv-01 kernel: [    6.331314] type=1505 audit(1265777556.834:13): operation="profile_replace" pid=853 name=/usr/lib/connman/scripts/dhclient-script
Feb  9 21:52:36 MythTv-01 kernel: [    6.333470] type=1505 audit(1265777556.838:14): operation="profile_replace" pid=854 name=/usr/bin/evince
Feb  9 21:52:36 MythTv-01 kernel: [    6.336797] type=1505 audit(1265777556.842:15): operation="profile_replace" pid=854 name=/usr/bin/evince-previewer
Feb  9 21:52:36 MythTv-01 kernel: [    6.338765] type=1505 audit(1265777556.842:16): operation="profile_replace" pid=854 name=/usr/bin/evince-thumbnailer
Feb  9 21:52:36 MythTv-01 kernel: [    6.342617] type=1505 audit(1265777556.846:17): operation="profile_replace" pid=856 name=/usr/sbin/mysqld
Feb  9 21:52:36 MythTv-01 kernel: [    6.343826] type=1505 audit(1265777556.846:18): operation="profile_replace" pid=857 name=/usr/sbin/ntpd
Feb  9 21:52:36 MythTv-01 kernel: [    6.345054] type=1505 audit(1265777556.850:19): operation="profile_replace" pid=858 name=/usr/sbin/tcpdump
Feb  9 21:52:37 MythTv-01 kernel: [    6.780742] nvidia: module license 'NVIDIA' taints kernel.
Feb  9 21:52:37 MythTv-01 kernel: [    6.780745] Disabling lock debugging due to kernel taint
Feb  9 21:52:37 MythTv-01 kernel: [    7.032304] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  9 21:52:37 MythTv-01 kernel: [    7.032462] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
Feb  9 21:52:37 MythTv-01 kernel: [    7.285283] ivtv: Start initialization, version 1.4.1
Feb  9 21:52:37 MythTv-01 kernel: [    7.285327] ivtv0: Initializing card 0
Feb  9 21:52:37 MythTv-01 kernel: [    7.285330] ivtv0: Autodetected Hauppauge card (cx23416 based)
Feb  9 21:52:37 MythTv-01 kernel: [    7.285785] ivtv 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  9 21:52:37 MythTv-01 kernel: [    7.285794] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Feb  9 21:52:37 MythTv-01 kernel: [    7.350795] tveeprom 0-0050: Hauppauge model 26582, rev C299, serial# 8454218
Feb  9 21:52:37 MythTv-01 kernel: [    7.350797] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
Feb  9 21:52:37 MythTv-01 kernel: [    7.350800] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
Feb  9 21:52:37 MythTv-01 kernel: [    7.350801] tveeprom 0-0050: audio processor is CX25843 (idx 37)
Feb  9 21:52:37 MythTv-01 kernel: [    7.350803] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
Feb  9 21:52:37 MythTv-01 kernel: [    7.350805] tveeprom 0-0050: has no radio
Feb  9 21:52:37 MythTv-01 kernel: [    7.350807] ivtv0: Autodetected Hauppauge WinTV PVR-150
Feb  9 21:52:37 MythTv-01 kernel: [    7.486616] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:52:37 MythTv-01 kernel: [    7.490759] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Feb  9 21:52:38 MythTv-01 kernel: [    7.533739] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  9 21:52:38 MythTv-01 kernel: [    7.572852] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
Feb  9 21:52:38 MythTv-01 kernel: [    7.573022] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
Feb  9 21:52:38 MythTv-01 kernel: [    7.577428] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb  9 21:52:38 MythTv-01 kernel: [    7.823370] tuner-simple 0-0061: creating new instance
Feb  9 21:52:38 MythTv-01 kernel: [    7.823373] tuner-simple 0-0061: type set to 50 (TCL 2002N)
Feb  9 21:52:38 MythTv-01 kernel: [    7.824490] IRQ 20/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
Feb  9 21:52:38 MythTv-01 kernel: [    7.824684] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Feb  9 21:52:38 MythTv-01 kernel: [    7.824700] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Feb  9 21:52:38 MythTv-01 kernel: [    7.824714] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Feb  9 21:52:38 MythTv-01 kernel: [    7.824728] ivtv0: Registered device video24 for encoder PCM (320 kB)
Feb  9 21:52:38 MythTv-01 kernel: [    7.824729] ivtv0: Initialized card: Hauppauge WinTV PVR-150
Feb  9 21:52:38 MythTv-01 kernel: [    7.824745] ivtv: End initialization
Feb  9 21:52:38 MythTv-01 kernel: [    7.931856] r8169: eth0: link up
Feb  9 21:52:38 MythTv-01 kernel: [    7.931865] r8169: eth0: link up
Feb  9 21:52:38 MythTv-01 kernel: [    8.456025] ivtv 0000:03:06.0: firmware: requesting v4l-cx2341x-enc.fw
Feb  9 21:52:39 MythTv-01 kernel: [    8.598920] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Feb  9 21:52:39 MythTv-01 kernel: [    8.796225] ivtv0: Encoder revision: 0x02060039
Feb  9 21:52:39 MythTv-01 kernel: [    8.814410] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
Feb  9 21:52:39 MythTv-01 kernel: [    9.089190] type=1503 audit(1265777559.594:20): operation="open" pid=1179 parent=1178 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:52:39 MythTv-01 kernel: [    9.312099] Starting XFS recovery on filesystem: sda5 (logdev: internal)
Feb  9 21:52:40 MythTv-01 kernel: [    9.782633] Ending XFS recovery on filesystem: sda5 (logdev: internal)
Feb  9 21:52:42 MythTv-01 kernel: [   11.695747] __ratelimit: 9 callbacks suppressed
Feb  9 21:52:42 MythTv-01 kernel: [   11.695750] type=1503 audit(1265777562.198:24): operation="open" pid=1455 parent=1454 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:52:42 MythTv-01 kernel: [   11.723846] type=1503 audit(1265777562.226:25): operation="open" pid=1466 parent=1465 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb  9 21:52:43 MythTv-01 kernel: [   12.517884] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb  9 21:53:07 MythTv-01 kernel: [   33.905812] hrtimer: interrupt too slow, forcing clock min delta to 174313347 ns
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] EIP: 0060:[<f973fa3c>] EFLAGS: 00003246 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] EIP is at os_io_write_word+0xc/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] EAX: 000080a8 EBX: 0000c000 ECX: 00000000 EDX: 000003d4
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] ESI: 0000184e EDI: f54adfa4 EBP: f380bcd8 ESP: f380bcd8
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f971b432>] _nv000005rm+0x17/0x1b [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f966d221>] ? _nv000110rm+0x38/0x46 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [   97.732532]  [<c0103448>] ? work_notifysig+0x13/0x1b
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] EIP: 0060:[<f973fa3c>] EFLAGS: 00003246 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] EIP is at os_io_write_word+0xc/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] EAX: 000080a8 EBX: 0000c000 ECX: 00000000 EDX: 000003d4
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] ESI: 0000184e EDI: f54adfa4 EBP: f380bcd8 ESP: f380bcd8
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f971b432>] _nv000005rm+0x17/0x1b [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f966d221>] ? _nv000110rm+0x38/0x46 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  163.328561]  [<c0103448>] ? work_notifysig+0x13/0x1b
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] EIP: 0060:[<f973fa2b>] EFLAGS: 00003286 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] EIP is at os_io_write_byte+0xb/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] EAX: 000000e8 EBX: 0000c000 ECX: 00000000 EDX: 000003d4
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] ESI: 0000184e EDI: f54adfa4 EBP: f380bcd8 ESP: f380bcd8
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f971b3ff>] _nv000007rm+0x17/0x1b [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f966d1db>] ? _nv000114rm+0x16/0x24 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  228.752561]  [<c0103448>] ? work_notifysig+0x13/0x1b
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] EIP: 0060:[<f973fa57>] EFLAGS: 00003286 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] EIP is at os_io_read_byte+0x7/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] EAX: 00000300 EBX: 0000c000 ECX: 00000000 EDX: 000003da
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] ESI: 0000184e EDI: f54adfa4 EBP: f380bce0 ESP: f380bce0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f971b3e1>] _nv000013rm+0x11/0x18 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f966d16f>] ? _nv000214rm+0xe/0x21 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  294.364534]  [<c0103448>] ? work_notifysig+0x13/0x1b
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] EIP: 0060:[<f973fa2b>] EFLAGS: 00003282 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] EIP is at os_io_write_byte+0xb/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] EAX: 00000000 EBX: 0000c000 ECX: 00000000 EDX: 000003d4
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] ESI: 0000184e EDI: f54adfa4 EBP: f380bcd8 ESP: f380bcd8
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f971b3ff>] _nv000007rm+0x17/0x1b [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f966d1db>] ? _nv000114rm+0x16/0x24 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  359.804533]  [<c0103448>] ? work_notifysig+0x13/0x1b
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] Modules linked in: tuner_simple tuner_types wm8775 snd_hda_codec_realtek tuner cx25840 snd_hda_intel snd_hda_codec snd_hwdep ivtv i2c_algo_bit snd_pcm_oss snd_mixer_oss cx2341x snd_pcm snd_seq_dummy v4l2_common snd_seq_oss nvidia(P) videodev i2c_piix4 snd_seq_midi v4l1_compat snd_rawmidi tveeprom dv1394 lirc_imon snd_seq_midi_event iptable_filter snd_seq snd_timer ip_tables ppdev agpgart lirc_dev x_tables parport_pc snd_seq_device snd lp raw1394 xfs parport soundcore exportfs snd_page_alloc usbhid ohci1394 r8169 mii ieee1394
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] Pid: 1755, comm: Xorg Tainted: P           (2.6.31-17-generic-pae #54-Ubuntu) GA-MA785GMT-UD2H
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] EIP: 0060:[<f973fa57>] EFLAGS: 00003286 CPU: 0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] EIP is at os_io_read_byte+0x7/0x10 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] EAX: 00000300 EBX: 0000c000 ECX: 00000000 EDX: 000003da
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] ESI: 0000184e EDI: f54adfa4 EBP: f380bce0 ESP: f380bce0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] CR0: 8005003b CR2: b7753644 CR3: 0074b000 CR4: 000006f0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] DR6: ffff0ff0 DR7: 00000400
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533] Call Trace:
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f971b3e1>] _nv000013rm+0x11/0x18 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f966d16f>] ? _nv000214rm+0xe/0x21 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f93cc19a>] ? _nv000307rm+0x7e/0x9c [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f971b9ce>] ? _nv006228rm+0x1a8/0x1de [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f9672cde>] ? _nv005232rm+0x99/0x2e0 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f967707e>] ? _nv003683rm+0x377/0x5ec [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f96779ad>] ? _nv003861rm+0x56e/0x90f [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f967e3b2>] ? _nv003791rm+0xcd/0x14e [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f9679006>] ? rm_disable_adapter+0x62/0xab [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<f973cc87>] ? nv_kern_close+0x1c7/0x390 [nvidia]
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0315dad>] ? kobject_put+0x1d/0x50
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01ec93a>] ? __fput+0xda/0x1f0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01eca65>] ? fput+0x15/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01e8e87>] ? filp_close+0x47/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0148473>] ? put_files_struct+0x63/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0148503>] ? exit_files+0x43/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01495cf>] ? do_exit+0x11f/0x2e0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c015462d>] ? dequeue_signal+0x2d/0x170
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01497ca>] ? do_group_exit+0x3a/0xb0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0155e8f>] ? get_signal_to_deliver+0x18f/0x300
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c010304b>] ? do_signal+0x6b/0x160
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c02cb90f>] ? security_file_permission+0xf/0x20
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01eafdf>] ? rw_verify_area+0x5f/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01eb187>] ? vfs_write+0x127/0x190
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01ead80>] ? do_sync_write+0x0/0x100
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c01ebbbd>] ? sys_write+0x3d/0x70
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0102771>] ? restore_sigcontext+0xc1/0xe0
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c010318d>] ? do_notify_resume+0x4d/0x60
Feb  9 21:59:36 MythTv-01 kernel: [  425.252533]  [<c0103448>] ? work_notifysig+0x13/0x1b
```

---

### Post by warfacegod on 2010-02-10
Um... wow. That was long... try code tags... next time... winded from scrolling... past that...

Have you tried another video card?

---

### Post by Stunpals on 2010-02-15
When the system is acting up, if I remove the video card and boot off the on-board card is boots fine, unfortunately the onboard card is a bit weak but I think this proves its the video card causing the issue, or at least I hope so.

I contacted the vendor and they have issued me a RMA so I hope the next card doesn't have the same issues.

---

