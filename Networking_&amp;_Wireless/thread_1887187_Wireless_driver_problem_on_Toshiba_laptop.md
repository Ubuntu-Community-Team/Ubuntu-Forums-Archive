---
title: "Wireless driver problem on Toshiba laptop"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by Inodoro Pereyra on 2011-11-26
I have a brand new Toshiba Satellite C655D-S5300 laptop. A few days ago, I installed Windows 7 and Lucid, in a dual boot configuration.
Of course, when I finished installing Lucid, the wireless driver was not there. After opening this thread:

[http://ubuntuforums.org/showthread.php?t=1885825](http://ubuntuforums.org/showthread.php?t=1885825)

I followed the advise received, and got the wireless working perfectly. Then, next morning, I ran the Update Manager, mostly because the video driver wasn't the right one. Then, my wireless driver seemed to disappear. I tried to reinstall it, using the same method I had used before, but nothing happened.

The wireless card is a Realtek RTL 8188CE. 

Can anybody tell me what am I doing wrong?

Thanks in advance. :)

---

### Post by Inodoro Pereyra on 2011-11-27
Nobody? :(

---

### Post by bluexrider on 2011-11-27
When you ran the update manager did you install a different kernel? If so you may need to revert back to the previous or recompile the new one.

What updates were installed at the time that would break your wifi?

AND did you try the Live CD again to verify the WIFI issue?

---

### Post by praseodym on 2011-11-27
Please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
dmesg | egrep 'rtl8|r8'
```

---

### Post by Inodoro Pereyra on 2011-11-29
> **praseodym said:**
> Please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
dmesg | egrep 'rtl8|r8'
```

Sorry for the delay. Had a rough few days...

Here it is:

uname -a

```
Linux bernardo-laptop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux 

```

lspci

```
grep: net: No such file or directory 
```

iwconfig

```
lo        no wireless extensions.
```

lsmod

```
Module                  Size  Used by 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  1 snd_hda_intel 
snd_hwdep               6924  1 snd_hda_codec 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              23681  2 snd_pcm,snd_seq 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
fbcon                  39270  71 
tileblit                2487  1 fbcon 
font                    8053  1 fbcon 
bitblit                 5811  1 fbcon 
uvcvideo               62883  0 
videodev               40550  1 uvcvideo 
v4l1_compat            15495  2 uvcvideo,videodev 
softcursor              1565  1 bitblit 
psmouse                65040  0 
v4l2_compat_ioctl32    11892  1 videodev 
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw               4918  0 
shpchp                 33711  0 
lp                      9336  0 
soundcore               8052  1 snd 
i2c_piix4               9639  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
vga16fb                12757  1 
vgastate                9857  1 vga16fb 
video                  20623  0 
output                  2503  1 video 
parport                37160  2 ppdev,lp 
usb_storage            50441  0 
ahci                   38030  2 

```

rfkill list
Nothing?:confused:

dmesg

```
rtl8|r8: command not found 
```

---

### Post by praseodym on 2011-11-30
```
lspci -nnk | grep -iA2 net
```
and
```
dmesg | egrep 'rtl8|r8'
```
are single lines each.

---

### Post by Inodoro Pereyra on 2011-11-30
I know. I typed them exactly as you did. :confused:

---

### Post by praseodym on 2011-12-01
Try
```
lspci -nnk >> lspci.txt
dmesg >> dmesg.txt
```
and upload these 2 files

---

### Post by Inodoro Pereyra on 2011-12-02
> **praseodym said:**
> Try
```
lspci -nnk >> lspci.txt
dmesg >> dmesg.txt
```and upload these 2 files

Nothing. :(
it just goes straight back to the prompt.

---

### Post by praseodym on 2011-12-02
The files **lspci.txt** and **dmesg.txt** are in your /home directory. Upload these

---

### Post by mr_raider on 2011-12-02
2.6.32 does not contain the drivers for the rtl 8188ce. The steps you followed earlier actually built the kernel module from source. Every time you update the kernel you need to rebuild the kernel module. Repeat the steps you followed initially again.

---

### Post by Inodoro Pereyra on 2011-12-02
> **praseodym said:**
> The files **lspci.txt** and **dmesg.txt** are in your /home directory. Upload these

Now I got it. Here's dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-35-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 (Ubuntu 2.6.32-35.78-generic 2.6.32.46+drm33.20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-35-generic root=UUID=6bfd0051-fe03-4f9d-b1d7-41ee073d6233 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df507000 (usable)
[    0.000000]  BIOS-e820: 00000000df507000 - 00000000df910000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df910000 - 00000000dfb3f000 (usable)
[    0.000000]  BIOS-e820: 00000000dfb3f000 - 00000000dfbbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000dfbbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfef6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef6000 - 00000000dff00000 (usable)
[    0.000000]  BIOS-e820: 00000000dff00000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000107000000 (usable)
[    0.000000]  BIOS-e820: 0000000107000000 - 000000011f000000 (reserved)
[    0.000000] DMI 2.7 present.
[    0.000000] last_pfn = 0x107000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFEBE000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000011f000000 aka 4592M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xdff00 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000df507000 (usable)
[    0.000000]  modified: 00000000df507000 - 00000000df910000 (ACPI NVS)
[    0.000000]  modified: 00000000df910000 - 00000000dfb3f000 (usable)
[    0.000000]  modified: 00000000dfb3f000 - 00000000dfbbf000 (reserved)
[    0.000000]  modified: 00000000dfbbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  modified: 00000000dfebf000 - 00000000dfef6000 (ACPI data)
[    0.000000]  modified: 00000000dfef6000 - 00000000dff00000 (usable)
[    0.000000]  modified: 00000000dff00000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000107000000 (usable)
[    0.000000]  modified: 0000000107000000 - 000000011f000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000dff00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dff00000 page 4k
[    0.000000] kernel direct mapping tables up to dff00000 @ 8000-b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000107000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0107000000 page 2M
[    0.000000] kernel direct mapping tables up to 107000000 @ a000-c000
[    0.000000] RAMDISK: 377f3000 - 37fef471
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 00000000dfef5120 0006C (v01 TOSINV TOSINV00 00000003      01000013)
[    0.000000] ACPI: FACP 00000000dfef4000 000F4 (v04 TOSINV TOSINV00 00000003 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000dfeea000 061BA (v01 TOSINV TOSINV00 F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000dfc98000 00040
[    0.000000] ACPI: HPET 00000000dfef3000 00038 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000dfef2000 00084 (v02 TOSINV TOSINV00 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000dfef1000 0003C (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000dfee9000 00028 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000dfee8000 00176 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000dfee5000 026C6 (v01 TOSINV   TsbOdm 00001000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000dfee4000 003F4 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000dfee2000 0168E (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000107000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000107000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000030dff] pages 21
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0107000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a30ac4]    TEXT DATA BSS ==> [0001000000 - 0001a30ac4]
[    0.000000]   #3 [00377f3000 - 0037fef471]          RAMDISK ==> [00377f3000 - 0037fef471]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a31000 - 0001a311f4]              BRK ==> [0001a31000 - 0001a311f4]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000]  [ffffea0000000000-ffffea00039fffff] PMD -> [ffff880028600000-ffff88002b9fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00107000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000df507
[    0.000000]     0: 0x000df910 -> 0x000dfb3f
[    0.000000]     0: 0x000dfef6 -> 0x000dff00
[    0.000000]     0: 0x00100000 -> 0x00107000
[    0.000000] On node 0 totalpages: 943834
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 896888 pages, LIFO batch:31
[    0.000000]   Normal zone: 392 pages used for memmap
[    0.000000]   Normal zone: 28280 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df507000 - 00000000df910000
[    0.000000] PM: Registered nosave memory: 00000000dfb3f000 - 00000000dfbbf000
[    0.000000] PM: Registered nosave memory: 00000000dfbbf000 - 00000000dfebf000
[    0.000000] PM: Registered nosave memory: 00000000dfebf000 - 00000000dfef6000
[    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u524288
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 929004
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-35-generic root=UUID=6bfd0051-fe03-4f9d-b1d7-41ee073d6233 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 3636804k/4308992k available (5415k kernel code, 533656k absent, 138532k reserved, 2978k data, 888k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 38010880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1296.671 MHz processor.
[    0.020011] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.33 BogoMIPS (lpj=12966690)
[    0.020064] Security Framework initialized
[    0.020106] AppArmor: AppArmor initialized
[    0.020939] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.032198] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.033575] Mount-cache hash table entries: 256
[    0.033867] Initializing cgroup subsys ns
[    0.033878] Initializing cgroup subsys cpuacct
[    0.033887] Initializing cgroup subsys memory
[    0.033903] Initializing cgroup subsys devices
[    0.033909] Initializing cgroup subsys freezer
[    0.033914] Initializing cgroup subsys net_cls
[    0.033960] CPU: L1 I Cache: 32K (64 bytes/line), D cache 32K (64 bytes/line)
[    0.033965] CPU: L2 Cache: 512K (64 bytes/line)
[    0.033970] CPU 0/0x0 -> Node 0
[    0.033974] CPU: Physical Processor ID: 0
[    0.033977] CPU: Processor Core ID: 0
[    0.033983] mce: CPU supports 6 MCE banks
[    0.034002] Performance Events: AMD PMU driver.
[    0.034011] ... version:                0
[    0.034014] ... bit width:              48
[    0.034016] ... generic registers:      4
[    0.034020] ... value mask:             0000ffffffffffff
[    0.034023] ... max period:             00007fffffffffff
[    0.034027] ... fixed-purpose events:   0
[    0.034030] ... event mask:             000000000000000f
[    0.038250] ACPI: Core revision 20090903
[    0.060046] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060059] ftrace: allocating 22484 entries in 89 pages
[    0.070172] Setting APIC routing to flat
[    0.070528] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.178923] CPU0: AMD E-300 APU with Radeon(tm) HD Graphics stepping 00
[    0.180000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 32K (64 bytes/line), D cache 32K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.330074] CPU1: AMD E-300 APU with Radeon(tm) HD Graphics stepping 00
[    0.330087] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.340026] Brought up 2 CPUs
[    0.340031] Total of 2 processors activated (5186.87 BogoMIPS).
[    0.340452] CPU0 attaching sched-domain:
[    0.340463]  domain 0: span 0-1 level MC
[    0.340468]   groups: 0 1
[    0.340478] CPU1 attaching sched-domain:
[    0.340482]  domain 0: span 0-1 level MC
[    0.340486]   groups: 1 0
[    0.340625] devtmpfs: initialized
[    0.340893] regulator: core version 0.5
[    0.340893] Time: 13:37:39  Date: 12/02/11
[    0.340893] NET: Registered protocol family 16
[    0.340893] Trying to unpack rootfs image as initramfs...
[    0.340893] ACPI: bus type pci registered
[    0.340893] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.340893] PCI: MCFG area at f8000000 reserved in E820
[    0.345559] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.345564] PCI: Using configuration type 1 for base access
[    0.350190] bio: create slab <bio-0> at 0
[    0.352110] ACPI: EC: Look up EC in DSDT
[    0.356234] ACPI: Executed 1 blocks of module-level executable AML code
[    0.364515] ACPI: BIOS _OSI(Linux) query ignored
[    0.401432] ACPI: Interpreter enabled
[    0.401439] ACPI: (supports S0 S3 S4 S5)
[    0.401482] ACPI: Using IOAPIC for interrupt routing
[    0.436993] ACPI: Power Resource [PFA1] (off)
[    0.437660] ACPI: No dock devices found.
[    0.438057] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.438208] pci 0000:00:01.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.438219] pci 0000:00:01.0: reg 14 io port: [0x4000-0x40ff]
[    0.438227] pci 0000:00:01.0: reg 18 32bit mmio: [0xf0300000-0xf033ffff]
[    0.438268] pci 0000:00:01.0: supports D1 D2
[    0.438392] pci 0000:00:11.0: reg 10 io port: [0x4138-0x413f]
[    0.438403] pci 0000:00:11.0: reg 14 io port: [0x414c-0x414f]
[    0.438414] pci 0000:00:11.0: reg 18 io port: [0x4130-0x4137]
[    0.438424] pci 0000:00:11.0: reg 1c io port: [0x4148-0x414b]
[    0.438435] pci 0000:00:11.0: reg 20 io port: [0x4110-0x411f]
[    0.438445] pci 0000:00:11.0: reg 24 32bit mmio: [0xf034a000-0xf034a3ff]
[    0.438522] pci 0000:00:12.0: reg 10 32bit mmio: [0xf0349000-0xf0349fff]
[    0.438624] pci 0000:00:12.2: reg 10 32bit mmio: [0xf0348000-0xf03480ff]
[    0.438695] pci 0000:00:12.2: supports D1 D2
[    0.438699] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.438707] pci 0000:00:12.2: PME# disabled
[    0.438758] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0347000-0xf0347fff]
[    0.438861] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0346000-0xf03460ff]
[    0.438932] pci 0000:00:13.2: supports D1 D2
[    0.438935] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.438942] pci 0000:00:13.2: PME# disabled
[    0.439081] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0340000-0xf0343fff]
[    0.439140] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.439147] pci 0000:00:14.2: PME# disabled
[    0.439363] pci 0000:00:15.0: supports D1 D2
[    0.439469] pci 0000:00:15.1: supports D1 D2
[    0.439531] pci 0000:00:16.0: reg 10 32bit mmio: [0xf0345000-0xf0345fff]
[    0.439634] pci 0000:00:16.2: reg 10 32bit mmio: [0xf0344000-0xf03440ff]
[    0.439704] pci 0000:00:16.2: supports D1 D2
[    0.439708] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.439714] pci 0000:00:16.2: PME# disabled
[    0.440369] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.440401] pci 0000:02:00.0: reg 18 64bit mmio: [0xf0200000-0xf0203fff]
[    0.440481] pci 0000:02:00.0: supports D1 D2
[    0.440485] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440493] pci 0000:02:00.0: PME# disabled
[    0.440583] pci 0000:00:15.0: bridge io port: [0x3000-0x3fff]
[    0.440590] pci 0000:00:15.0: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    0.440600] pci 0000:00:15.0: bridge 64bit mmio pref: [0xf0000000-0xf00fffff]
[    0.440678] pci 0000:06:00.0: reg 10 64bit mmio: [0xf0100000-0xf013ffff]
[    0.440691] pci 0000:06:00.0: reg 18 io port: [0x2000-0x207f]
[    0.440778] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440786] pci 0000:06:00.0: PME# disabled
[    0.440872] pci 0000:00:15.1: bridge io port: [0x2000-0x2fff]
[    0.440879] pci 0000:00:15.1: bridge 32bit mmio: [0xf0100000-0xf01fffff]
[    0.440920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.441273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    0.441422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    0.441683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.473583] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.474072] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.474603] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475101] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475551] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475905] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.476325] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.476746] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.476993] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.477021] vgaarb: loaded
[    0.477228] SCSI subsystem initialized
[    0.477433] libata version 3.00 loaded.
[    0.477576] usbcore: registered new interface driver usbfs
[    0.477598] usbcore: registered new interface driver hub
[    0.477650] usbcore: registered new device driver usb
[    0.477925] ACPI: WMI: Mapper loaded
[    0.477929] PCI: Using ACPI for IRQ routing
[    0.478248] NetLabel: Initializing
[    0.478253] NetLabel:  domain hash size = 128
[    0.478255] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.478287] NetLabel:  unlabeled traffic allowed by default
[    0.478362] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.478371] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.480049] Switching to clocksource tsc
[    0.482951] AppArmor: AppArmor Filesystem Enabled
[    0.482991] pnp: PnP ACPI init
[    0.483025] ACPI: bus type pnp registered
[    0.487572] pnp: PnP ACPI: found 11 devices
[    0.487577] ACPI: ACPI bus type pnp unregistered
[    0.487603] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.487609] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.487625] system 00:09: ioport range 0x400-0x4cf has been reserved
[    0.487630] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.487634] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[    0.487639] system 00:09: ioport range 0x680-0x6ff has been reserved
[    0.487644] system 00:09: ioport range 0x77a-0x77a has been reserved
[    0.487648] system 00:09: ioport range 0xc00-0xc01 has been reserved
[    0.487653] system 00:09: ioport range 0xc14-0xc14 has been reserved
[    0.487657] system 00:09: ioport range 0xc50-0xc52 has been reserved
[    0.487661] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[    0.487666] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[    0.487670] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[    0.487680] system 00:0a: iomem range 0xff800000-0xff80ffff has been reserved
[    0.487685] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.487690] system 00:0a: iomem range 0xffe00000-0xffffffff has been reserved
[    0.492843] pci 0000:00:14.4: PCI bridge, secondary bus 0000:01
[    0.492847] pci 0000:00:14.4:   IO window: disabled
[    0.492855] pci 0000:00:14.4:   MEM window: disabled
[    0.492862] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.492873] pci 0000:00:15.0: PCI bridge, secondary bus 0000:02
[    0.492879] pci 0000:00:15.0:   IO window: 0x3000-0x3fff
[    0.492887] pci 0000:00:15.0:   MEM window: 0xf0200000-0xf02fffff
[    0.492894] pci 0000:00:15.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    0.492905] pci 0000:00:15.1: PCI bridge, secondary bus 0000:06
[    0.492911] pci 0000:00:15.1:   IO window: 0x2000-0x2fff
[    0.492919] pci 0000:00:15.1:   MEM window: 0xf0100000-0xf01fffff
[    0.492925] pci 0000:00:15.1:   PREFETCH window: disabled
[    0.492960]   alloc irq_desc for 16 on node -1
[    0.492964]   alloc kstat_irqs on node -1
[    0.492976] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.492983] pci 0000:00:15.0: setting latency timer to 64
[    0.492998] pci 0000:00:15.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.493005] pci 0000:00:15.1: setting latency timer to 64
[    0.493014] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.493019] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.493025] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.493029] pci_bus 0000:02: resource 1 mem: [0xf0200000-0xf02fffff]
[    0.493033] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf00fffff]
[    0.493038] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    0.493042] pci_bus 0000:06: resource 1 mem: [0xf0100000-0xf01fffff]
[    0.493116] NET: Registered protocol family 2
[    0.493444] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.495810] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.501509] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.502186] TCP: Hash tables configured (established 524288 bind 65536)
[    0.502191] TCP reno registered
[    0.502401] NET: Registered protocol family 1
[    0.502440] pci 0000:00:01.0: Boot video device
[    0.619616] Simple Boot Flag at 0x44 set to 0x1
[    0.619943] Scanning for low memory corruption every 60 seconds
[    0.620197] audit: initializing netlink socket (disabled)
[    0.620218] type=2000 audit(1322833059.619:1): initialized
[    0.636247] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.638884] VFS: Disk quotas dquot_6.5.2
[    0.639008] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.640391] fuse init (API version 7.13)
[    0.640561] msgmni has been set to 7103
[    0.641026] alg: No test for stdrng (krng)
[    0.641147] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.641153] io scheduler noop registered
[    0.641157] io scheduler anticipatory registered
[    0.641161] io scheduler deadline registered
[    0.641247] io scheduler cfq registered (default)
[    0.641610]   alloc irq_desc for 24 on node -1
[    0.641615]   alloc kstat_irqs on node -1
[    0.641635] pcieport 0000:00:15.0: irq 24 for MSI/MSI-X
[    0.641650] pcieport 0000:00:15.0: setting latency timer to 64
[    0.641889]   alloc irq_desc for 25 on node -1
[    0.641893]   alloc kstat_irqs on node -1
[    0.641907] pcieport 0000:00:15.1: irq 25 for MSI/MSI-X
[    0.641919] pcieport 0000:00:15.1: setting latency timer to 64
[    0.642037] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.642166] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.642539] ACPI: AC Adapter [ADP0] (off-line)
[    0.642653] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.642660] ACPI: Power Button [PWRB]
[    0.642763] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.645041] ACPI: Lid Switch [LID0]
[    0.645124] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.645128] ACPI: Power Button [PWRF]
[    0.645433] fan PNP0C0B:00: registered as cooling_device0
[    0.645443] ACPI: Fan [FAN1] (off)
[    0.646254] processor LNXCPU:00: registered as cooling_device1
[    0.646415] processor LNXCPU:01: registered as cooling_device2
[    0.652090] thermal LNXTHERM:01: registered as thermal_zone0
[    0.652105] ACPI: Thermal Zone [THZN] (49 C)
[    0.654978] ACPI: Battery Slot [BAT0] (battery present)
[    0.657532] Linux agpgart interface v0.103
[    0.657601] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.660044] brd: module loaded
[    0.660959] loop: module loaded
[    0.661148] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.661921] Fixed MDIO Bus: probed
[    0.661988] PPP generic driver version 2.4.2
[    0.662055] tun: Universal TUN/TAP device driver, 1.6
[    0.662058] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.662205] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.662313]   alloc irq_desc for 17 on node -1
[    0.662317]   alloc kstat_irqs on node -1
[    0.662332] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.662426] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.662433] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.662511] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.662569] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    0.662615] ehci_hcd 0000:00:12.2: debug port 1
[    0.662652] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0348000
[    0.679348] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.679588] usb usb1: configuration #1 chosen from 1 choice
[    0.679646] hub 1-0:1.0: USB hub found
[    0.679664] hub 1-0:1.0: 5 ports detected
[    0.679876] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.679956] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.679963] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.680034] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.680090] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    0.680126] ehci_hcd 0000:00:13.2: debug port 1
[    0.680150] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf0346000
[    0.699348] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.699586] usb usb2: configuration #1 chosen from 1 choice
[    0.699639] hub 2-0:1.0: USB hub found
[    0.699657] hub 2-0:1.0: 5 ports detected
[    0.699880] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.699960] ehci_hcd 0000:00:16.2: setting latency timer to 64
[    0.699966] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    0.700051] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    0.700107] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    0.700143] ehci_hcd 0000:00:16.2: debug port 1
[    0.700169] ehci_hcd 0000:00:16.2: irq 17, io mem 0xf0344000
[    0.719347] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    0.719596] usb usb3: configuration #1 chosen from 1 choice
[    0.719652] hub 3-0:1.0: USB hub found
[    0.719670] hub 3-0:1.0: 4 ports detected
[    0.719847] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.719920]   alloc irq_desc for 18 on node -1
[    0.719924]   alloc kstat_irqs on node -1
[    0.719937] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.720022] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.720029] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.720097] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    0.720186] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf0349000
[    0.772925] Freeing initrd memory: 8177k freed
[    0.783797] usb usb4: configuration #1 chosen from 1 choice
[    0.783854] hub 4-0:1.0: USB hub found
[    0.783943] hub 4-0:1.0: 5 ports detected
[    0.784086] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.784166] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    0.784173] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.784241] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.784316] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0347000
[    0.843752] usb usb5: configuration #1 chosen from 1 choice
[    0.843808] hub 5-0:1.0: USB hub found
[    0.843896] hub 5-0:1.0: 5 ports detected
[    0.844041] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.844121] ohci_hcd 0000:00:16.0: setting latency timer to 64
[    0.844127] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    0.844201] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    0.844279] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0345000
[    0.903768] usb usb6: configuration #1 chosen from 1 choice
[    0.903830] hub 6-0:1.0: USB hub found
[    0.903918] hub 6-0:1.0: 4 ports detected
[    0.904053] uhci_hcd: USB Universal Host Controller Interface driver
[    0.904193] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.929891] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.929903] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.930062] mice: PS/2 mouse device common for all mice
[    0.930352] rtc_cmos 00:05: RTC can wake from S4
[    0.930427] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.930466] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    0.930709] device-mapper: uevent: version 1.0.3
[    0.930943] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.931719] device-mapper: multipath: version 1.1.0 loaded
[    0.931729] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.933007] cpuidle: using governor ladder
[    0.933188] cpuidle: using governor menu
[    0.933877] TCP cubic registered
[    0.934189] NET: Registered protocol family 10
[    0.935613] NET: Registered protocol family 17
[    0.935721] powernow-k8: Found 1 AMD E-300 APU with Radeon(tm) HD Graphics processors (2 cpu cores) (version 2.20.00)
[    0.936036] powernow-k8:    0 : pstate 0 (1300 MHz)
[    0.936041] powernow-k8:    1 : pstate 1 (1114 MHz)
[    0.936044] powernow-k8:    2 : pstate 2 (780 MHz)
[    0.936049] [Firmware Warn]: powernow-k8: Invalid zero transition latency
[    0.936522] [Firmware Warn]: powernow-k8: Invalid zero transition latency
[    0.936970] PM: Resume from disk failed.
[    0.936996] registered taskstats version 1
[    0.937634]   Magic number: 7:146:634
[    0.937834] rtc_cmos 00:05: setting system clock to 2011-12-02 13:37:40 UTC (1322833060)
[    0.937840] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.937843] EDD information not available.
[    0.938015] Freeing unused kernel memory: 888k freed
[    0.938525] Write protecting the kernel read-only data: 7692k
[    0.964182] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.980514] udev: starting version 151
[    1.019573] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.184925] usb 2-2: configuration #1 chosen from 1 choice
[    1.232839] ahci 0000:00:11.0: version 3.0
[    1.232930]   alloc irq_desc for 19 on node -1
[    1.232935]   alloc kstat_irqs on node -1
[    1.232951] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.233182] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 6 Gbps 0x7 impl SATA mode
[    1.233190] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.233748] scsi0 : ahci
[    1.234013] scsi1 : ahci
[    1.234129] scsi2 : ahci
[    1.234279] ata1: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a100 irq 19
[    1.234285] ata2: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a180 irq 19
[    1.234291] ata3: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a200 irq 19
[    1.267641] Initializing USB Mass Storage driver...
[    1.267875] scsi3 : SCSI emulation for USB Mass Storage devices
[    1.268068] usbcore: registered new interface driver usb-storage
[    1.268074] USB Mass Storage support registered.
[    1.268222] usb-storage: device found at 2
[    1.268229] usb-storage: waiting for device to settle before scanning
[    1.311596] usb 3-4: new high speed USB device using ehci_hcd and address 2
[    1.523343] usb 3-4: configuration #1 chosen from 1 choice
[    1.580367] ata3: SATA link down (SStatus 0 SControl 300)
[    1.760370] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.760386] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.772163] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633J, TF03, max UDMA/100
[    1.785312] ata2.00: configured for UDMA/100
[    1.807729] ata1.00: ATA-8: TOSHIBA MK3265GSXN, GH101M, max UDMA/100
[    1.807742] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.809699] ata1.00: configured for UDMA/100
[    1.820944] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GH10 PQ: 0 ANSI: 5
[    1.821315] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.821543] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.821692] sd 0:0:0:0: [sda] Write Protect is off
[    1.821702] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.822128] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.823699]  sda:
[    1.824330] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633J  TF03 PQ: 0 ANSI: 5
[    1.847730] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.847740] Uniform CD-ROM driver Revision: 3.20
[    1.847984] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.848103] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.870279]  sda1 sda2 sda3 < sda5 sda6 >
[    1.911516] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.478464] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.261055] usb-storage: device scan complete
[    6.264670] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.267246] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    6.274890] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   10.957345] udev: starting version 151
[   11.027637] vga16fb: initializing
[   11.027646] vga16fb: mapped to 0xffff8800000a0000
[   11.027852] fb0: VGA16 VGA frame buffer device
[   11.030932] Adding 4630520k swap on /dev/sda6.  Priority:-1 extents:1 across:4630520k 
[   11.091213] lp: driver loaded but no devices found
[   11.152818] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.159902] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.570287] acpi device:00: registered as cooling_device3
[   11.570566] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   11.570677] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.590582] Linux video capture interface: v2.00
[   11.603257] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera (10f1:1a34)
[   11.617952] input: TOSHIBA Web Camera as /devices/pci0000:00/0000:00:16.2/usb3/3-4/3-4:1.0/input/input6
[   11.618057] usbcore: registered new interface driver uvcvideo
[   11.618062] USB Video Class driver (v0.1.0)
[   11.778190] Console: switching to colour frame buffer device 80x30
[   11.870795] type=1505 audit(1322851071.423:2):  operation="profile_load" pid=708 name="/sbin/dhclient3"
[   11.871314] type=1505 audit(1322851071.433:3):  operation="profile_load" pid=708 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.871610] type=1505 audit(1322851071.433:4):  operation="profile_load" pid=708 name="/usr/lib/connman/scripts/dhclient-script"
[   12.015335] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.015490] HDA Intel 0000:00:14.2: setting latency timer to 64
[   12.593920] type=1505 audit(1322851072.152:5):  operation="profile_load" pid=941 name="/usr/share/gdm/guest-session/Xsession"
[   12.603781] type=1505 audit(1322851072.162:6):  operation="profile_replace" pid=942 name="/sbin/dhclient3"
[   12.604327] type=1505 audit(1322851072.162:7):  operation="profile_replace" pid=942 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.612718] type=1505 audit(1322851072.172:8):  operation="profile_replace" pid=942 name="/usr/lib/connman/scripts/dhclient-script"
[   12.637487] type=1505 audit(1322851072.192:9):  operation="profile_load" pid=946 name="/usr/lib/cups/backend/cups-pdf"
[   12.638148] type=1505 audit(1322851072.192:10):  operation="profile_load" pid=946 name="/usr/sbin/cupsd"
[   12.646322] type=1505 audit(1322851072.202:11):  operation="profile_load" pid=943 name="/usr/bin/evince"
[   12.724055] input: PS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   12.959798] ppdev: user-space parallel port driver
[   13.394617] CPU0 attaching NULL sched-domain.
[   13.394631] CPU1 attaching NULL sched-domain.
[   13.450338] CPU0 attaching sched-domain:
[   13.450348]  domain 0: span 0-1 level MC
[   13.450353]   groups: 0 1
[   13.450360]   domain 1: span 0-1 level CPU
[   13.450364]    groups: 0-1 (cpu_power = 2048)
[   13.450375] CPU1 attaching sched-domain:
[   13.450378]  domain 0: span 0-1 level MC
[   13.450382]   groups: 1 0
[   13.450388]   domain 1: span 0-1 level CPU
[   13.450391]    groups: 0-1 (cpu_power = 2048)
[   15.814246] CPU0 attaching NULL sched-domain.
[   15.814261] CPU1 attaching NULL sched-domain.
[   15.860182] CPU0 attaching sched-domain:
[   15.860191]  domain 0: span 0-1 level MC
[   15.860197]   groups: 0 1
[   15.860205]   domain 1: span 0-1 level CPU
[   15.860209]    groups: 0-1 (cpu_power = 2048)
[   15.860221] CPU1 attaching sched-domain:
[   15.860224]  domain 0: span 0-1 level MC
[   15.860228]   groups: 1 0
[   15.860234]   domain 1: span 0-1 level CPU
[   15.860238]    groups: 0-1 (cpu_power = 2048)

```

...and here's lspci:

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
    Kernel modules: shpchp
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
    Kernel modules: shpchp
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)

```

I sure hope you can make sense of it...

Mr_raider: I already tried that. It didn't work. :(

---

### Post by praseodym on 2011-12-03
Install the driver again because of a kernel upgrade. You can also install this driver which will be build automatically via dkms:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/ 
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192ce_dkms_2.6.0006.0321.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192ce_dkms_2.6.0006.0321.tar.gz)
sudo tar xvf rtl8192ce_dkms_2.6.0006.0321.tar.gz -C /usr/src
sudo dkms add -m rtl8192ce -v 2.6.0006.0321
sudo dkms build -m rtl8192ce -v 2.6.0006.0321
sudo dkms install -m rtl8192ce -v 2.6.0006.0321
```
Reboot and show:
```
lsmod
modinfo 8712u
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by Inodoro Pereyra on 2011-12-04
Dammit.
When I get here:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms

```

it asks me for the install CD, and, when I put it in and press enter, it doesn't recognize it.
Is there a way around it?

By the way, thanks Praseodym for all your help, so far. Sorry it's taking so long... :(

---

### Post by praseodym on 2011-12-04
Try it with cable connection after deactivating the CD in "Software-sorces"

---

### Post by Inodoro Pereyra on 2011-12-05
I don't have access to an ethernet connection. :(
I'll see if there's a Kinko's nearby...

---

