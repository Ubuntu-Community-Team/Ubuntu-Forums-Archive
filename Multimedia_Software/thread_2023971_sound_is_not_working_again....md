---
title: "sound is not working again..."
date: 2012-07-13
forum: Multimedia Software
---

### Post by mastablasta on 2012-07-13
I've had a similar porblem with 10.04 which i could solve by using newer ALSA (an upgrade to 10.10 made it almost perfect). the sound never worked in HD mode but since i use analog stereo anyway that was ifne enough. when 12.04 came out i tested live everyhting worked so a fresh install was made. sound worked very well except when computer went to hibernation. so i turned of hibernaiton. sound worked well until...
 
kernel -26 and now again in -27. i do not know what went wrong or how. i tried to load kernel generic -26 and sound now works there. after upgrading to -27 it doen't work again. the volume button shows dummy output and sound settings wants to delete the sound card since they are not available anymore (funny that lshw and lspci shows them as available and recognises them propperly)
 
since i had trouble before i deided to try a few commands.
 
```
 
sudo alsa reload -c

``` 
the sound volume icon changes immediatelly to empty "paper" and is still showing dummy output. however sound works. and if i click mixer the card is there. affter a while a strange thing happens. system says "dummy output not available anymore switching to" (well the porpper sound card)
 
i then did 
 
```
 
sudo alsactl store

``` 
and checked that the file was saved and it was. .i reboot. sound works perfectly. i reboot agian it works. i turn the computer off and turn it back on and get dummy output again with no sound. :confused:
i even trid shutting it down and unplugging the electric wire. in case there was some static or something. 
 
so what is going on? is this a bug? shoud i report it? i mean there were no issues before so why are there now? can a setting for the sound chip somehow be saved? so it doesn't look for it every time on reboot and then selects dummy output. or how could this be solved?
 
i've never seen anything like that in other operating systems where a system update would mess with users hardware settings.
 
i am adding some outputs here and attaching a few screenshots so you can see how silly the whole thing looks like.
 
```
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:65 memory:febfc000-febfffff
```
 
```
~$ sudo alsa reload -c
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-wavefront snd-cs4236 snd-wss-lib snd-opl3-lib snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-mpu401 snd-mpu401-uart snd-seq-midi snd-page-alloc snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-wavefront snd-cs4236 snd-wss-lib snd-opl3-lib snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-mpu401 snd-mpu401-uart snd-seq-midi snd-page-alloc snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
~$ sudo alsactl store
Home directory /home/tatie not ours.

```
 
file asound.state
```
state.VT82xx {
 control.1 {
  iface MIXER
  name 'Front Playback Volume'
  value.0 64
  value.1 64
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 64'
   dbmin -6400
   dbmax 0
   dbvalue.0 0
   dbvalue.1 0
  }
 }
 control.2 {
  iface MIXER
  name 'Front Playback Switch'
  value.0 true
  value.1 true
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.3 {
  iface MIXER
  name 'Surround Playback Volume'
  value.0 64
  value.1 64
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 64'
   dbmin -6400
   dbmax 0
   dbvalue.0 0
   dbvalue.1 0
  }
 }
 control.4 {
  iface MIXER
  name 'Surround Playback Switch'
  value.0 true
  value.1 true
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.5 {
  iface MIXER
  name 'Center Playback Volume'
  value 64
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 64'
   dbmin -6400
   dbmax 0
   dbvalue.0 0
  }
 }
 control.6 {
  iface MIXER
  name 'LFE Playback Volume'
  value 64
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 64'
   dbmin -6400
   dbmax 0
   dbvalue.0 0
  }
 }
 control.7 {
  iface MIXER
  name 'Center Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.8 {
  iface MIXER
  name 'LFE Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.9 {
  iface MIXER
  name 'Mic Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.10 {
  iface MIXER
  name 'Mic Playback Switch'
  value.0 false
  value.1 false
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.11 {
  iface MIXER
  name 'Line Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.12 {
  iface MIXER
  name 'Line Playback Switch'
  value.0 false
  value.1 false
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.13 {
  iface MIXER
  name 'Mic Boost Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 3'
   dbmin 0
   dbmax 3000
   dbvalue.0 0
   dbvalue.1 0
  }
 }
 control.14 {
  iface MIXER
  name 'Capture Switch'
  value.0 true
  value.1 true
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.15 {
  iface MIXER
  name 'Capture Switch'
  index 1
  value.0 false
  value.1 true
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.16 {
  iface MIXER
  name 'Capture Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -1350
   dbmax 3300
   dbvalue.0 -1350
   dbvalue.1 -1350
  }
 }
 control.17 {
  iface MIXER
  name 'Capture Volume'
  index 1
  value.0 0
  value.1 31
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -1350
   dbmax 3300
   dbvalue.0 -1350
   dbvalue.1 3300
  }
 }
 control.18 {
  iface MIXER
  name 'Input Source'
  value Mic
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Mic
   item.1 Line
  }
 }
 control.19 {
  iface MIXER
  name 'Input Source'
  index 1
  value Mic
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Mic
   item.1 Line
  }
 }
 control.20 {
  iface MIXER
  name 'Beep Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.21 {
  iface MIXER
  name 'Beep Playback Switch'
  value.0 false
  value.1 false
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.22 {
  iface MIXER
  name 'Master Playback Volume'
  value 44
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 64'
   dbmin -6400
   dbmax 0
   dbvalue.0 -2000
  }
 }
 control.23 {
  iface MIXER
  name 'Master Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.24 {
  iface CARD
  name 'Line-Out Front Jack'
  value false
  comment {
   access read
   type BOOLEAN
   count 1
  }
 }
 control.25 {
  iface CARD
  name 'Line-Out Surround Jack'
  value false
  comment {
   access read
   type BOOLEAN
   count 1
  }
 }
 control.26 {
  iface CARD
  name 'Line-Out CLFE Jack'
  value true
  comment {
   access read
   type BOOLEAN
   count 1
  }
 }
 control.27 {
  iface CARD
  name 'Mic Jack'
  value true
  comment {
   access read
   type BOOLEAN
   count 1
  }
 }
 control.28 {
  iface CARD
  name 'Line Jack'
  value false
  comment {
   access read
   type BOOLEAN
   count 1
  }
 }
 control.29 {
  iface MIXER
  name 'Digital Capture Volume'
  value.0 78
  value.1 78
  comment {
   access 'read write user'
   type INTEGER
   count 2
   range '0 - 120'
   tlv '0000000100000008fffff44800000032'
   dbmin -3000
   dbmax 3000
   dbvalue.0 900
   dbvalue.1 900
  }
 }
 control.30 {
  iface MIXER
  name 'PCM Playback Volume'
  value.0 255
  value.1 255
  comment {
   access 'read write user'
   type INTEGER
   count 2
   range '0 - 255'
   tlv '0000000100000008ffffec1400000014'
   dbmin -5100
   dbmax 0
   dbvalue.0 0
   dbvalue.1 0
  }
 }
}
state.UART {
 control {
 }
}
```
 
```
 dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-26-generic-pae (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 (Ubuntu 3.2.0-26.41-generic-pae 3.2.19)
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
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000004ffb0000 - 000000004ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004ffc0000 - 000000004fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff0000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./4CoreDual-SATA2., BIOS P2.20 09/22/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x4ffb0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 358de000 - 36c67000
[    0.000000] ACPI: RSDP 000f8860 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 4ffb0000 00038 (v01 A M I  OEMRSDT  09000922 MSFT 00000097)
[    0.000000] ACPI: FACP 4ffb0200 00084 (v02 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 4ffb0450 04B66 (v01  4CDS2 4CDS2218 00000218 INTL 02002026)
[    0.000000] ACPI: FACS 4ffc0000 00040
[    0.000000] ACPI: APIC 4ffb0390 00078 (v01 A M I  OEMAPIC  09000922 MSFT 00000097)
[    0.000000] ACPI: MCFG 4ffb0410 0003C (v01 A M I  OEMMCFG  09000922 MSFT 00000097)
[    0.000000] ACPI: OEMB 4ffc0040 00051 (v01 A M I  AMI_OEM  09000922 MSFT 00000097)
[    0.000000] ACPI: AAFT 4ffb4fc0 00027 (v01 A M I  OEMAAFT  09000922 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 387MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0004ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004ffb0
[    0.000000] On node 0 totalpages: 327487
[    0.000000] free_area_init_node: node 0, pgdat c18669c0, node_mem_map f71fd200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 776 pages used for memmap
[    0.000000]   HighMem zone: 98474 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:aec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f71bd000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324927
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=3f43c7a8-003b-4564-9f0d-a7a4c0393e06 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 5241344 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0004ffb0)
[    0.000000] Memory: 1263164k/1310400k available (5814k kernel code, 46784k reserved, 2841k data, 740k init, 397000k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
[    0.000000]       .data : 0xc15ada24 - 0xc18741c0   (2841 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ada24   (5814 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:1024 16
[    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2493.744 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4987.48 BogoMIPS (lpj=9974976)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004037] Security Framework initialized
[    0.004069] AppArmor: AppArmor initialized
[    0.004071] Yama: becoming mindful.
[    0.004145] Mount-cache hash table entries: 512
[    0.004345] Initializing cgroup subsys cpuacct
[    0.004353] Initializing cgroup subsys memory
[    0.004363] Initializing cgroup subsys devices
[    0.004365] Initializing cgroup subsys freezer
[    0.004367] Initializing cgroup subsys blkio
[    0.004375] Initializing cgroup subsys perf_event
[    0.004409] CPU: Physical Processor ID: 0
[    0.004411] CPU: Processor Core ID: 0
[    0.004416] mce: CPU supports 6 MCE banks
[    0.004427] CPU0: Thermal monitoring enabled (TM2)
[    0.004434] using mwait in idle threads.
[    0.009467] ACPI: Core revision 20110623
[    0.012022] ftrace: allocating 26538 entries in 52 pages
[    0.016098] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.016733] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059421] CPU0: Intel(R) Celeron(R) CPU        E3300  @ 2.50GHz stepping 0a
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f4d12000 soft=f4d14000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148069] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148133] Brought up 2 CPUs
[    0.148136] Total of 2 processors activated (10069.80 BogoMIPS).
[    0.149421] devtmpfs: initialized
[    0.149421] EVM: security.selinux
[    0.149421] EVM: security.SMACK64
[    0.149421] EVM: security.capability
[    0.149421] PM: Registering ACPI NVS region at 4ffc0000 (196608 bytes)
[    0.149421] print_constraints: dummy: 
[    0.149421] RTC time:  5:04:13, date: 07/13/12
[    0.149421] NET: Registered protocol family 16
[    0.149421] Trying to unpack rootfs image as initramfs...
[    0.149421] EISA bus registered
[    0.149421] ACPI: bus type pci registered
[    0.149472] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149475] PCI: not using MMCONFIG
[    0.149702] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.149816] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
[    0.149818] PCI: Using configuration type 1 for base access
[    0.152978] bio: create slab <bio-0> at 0
[    0.153108] ACPI: Added _OSI(Module Device)
[    0.153110] ACPI: Added _OSI(Processor Device)
[    0.153112] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.153114] ACPI: Added _OSI(Processor Aggregator Device)
[    0.154063] ACPI: EC: Look up EC in DSDT
[    0.155320] ACPI: Executed 1 blocks of module-level executable AML code
[    0.157919] ACPI: Interpreter enabled
[    0.157938] ACPI: (supports S0 S1 S4 S5)
[    0.157965] ACPI: Using IOAPIC for interrupt routing
[    0.157998] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.158745] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.158748] PCI: Using MMCONFIG for extended config space
[    0.164987] ACPI: No dock devices found.
[    0.164993] HEST: Table not found.
[    0.165000] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.165173] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7f])
[    0.165361] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.165364] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.165366] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.165369] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.165371] pci_root PNP0A03:00: host bridge window [mem 0x50000000-0xdfffffff]
[    0.165373] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfeafffff]
[    0.165403] pci 0000:00:00.0: [1106:0308] type 0 class 0x000600
[    0.165421] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.165533] pci 0000:00:00.1: [1106:1308] type 0 class 0x000600
[    0.165595] pci 0000:00:00.2: [1106:2308] type 0 class 0x000600
[    0.165657] pci 0000:00:00.3: [1106:3208] type 0 class 0x000600
[    0.165729] pci 0000:00:00.4: [1106:4308] type 0 class 0x000600
[    0.165791] pci 0000:00:00.5: [1106:5308] type 0 class 0x000800
[    0.165883] pci 0000:00:00.7: [1106:7308] type 0 class 0x000600
[    0.165956] pci 0000:00:01.0: [1106:b198] type 1 class 0x000604
[    0.166016] pci 0000:00:01.0: supports D1
[    0.166036] pci 0000:00:02.0: [1106:a208] type 1 class 0x000604
[    0.166132] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.166138] pci 0000:00:02.0: PME# disabled
[    0.166192] pci 0000:00:0f.0: [1106:5372] type 0 class 0x000101
[    0.166212] pci 0000:00:0f.0: reg 10: [io  0xdc00-0xdc07]
[    0.166224] pci 0000:00:0f.0: reg 14: [io  0xd880-0xd883]
[    0.166235] pci 0000:00:0f.0: reg 18: [io  0xd800-0xd807]
[    0.166247] pci 0000:00:0f.0: reg 1c: [io  0xd480-0xd483]
[    0.166258] pci 0000:00:0f.0: reg 20: [io  0xd400-0xd40f]
[    0.166270] pci 0000:00:0f.0: reg 24: [io  0xd000-0xd0ff]
[    0.166330] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.166386] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.166465] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.166529] pci 0000:00:10.0: reg 20: [io  0xc480-0xc49f]
[    0.166578] pci 0000:00:10.0: supports D1 D2
[    0.166580] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166585] pci 0000:00:10.0: PME# disabled
[    0.166603] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.166658] pci 0000:00:10.1: reg 20: [io  0xc800-0xc81f]
[    0.166707] pci 0000:00:10.1: supports D1 D2
[    0.166709] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166713] pci 0000:00:10.1: PME# disabled
[    0.166732] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.166795] pci 0000:00:10.2: reg 20: [io  0xc880-0xc89f]
[    0.166845] pci 0000:00:10.2: supports D1 D2
[    0.166847] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166852] pci 0000:00:10.2: PME# disabled
[    0.166874] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.166929] pci 0000:00:10.3: reg 20: [io  0xcc00-0xcc1f]
[    0.166977] pci 0000:00:10.3: supports D1 D2
[    0.166980] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166984] pci 0000:00:10.3: PME# disabled
[    0.167005] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.167027] pci 0000:00:10.4: reg 10: [mem 0xfe9ffc00-0xfe9ffcff]
[    0.167132] pci 0000:00:10.4: supports D1 D2
[    0.167134] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.167139] pci 0000:00:10.4: PME# disabled
[    0.167165] pci 0000:00:11.0: [1106:3372] type 0 class 0x000601
[    0.167294] pci 0000:00:11.7: [1106:287e] type 0 class 0x000600
[    0.167373] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
[    0.167392] pci 0000:00:12.0: reg 10: [io  0xc000-0xc0ff]
[    0.167404] pci 0000:00:12.0: reg 14: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.167492] pci 0000:00:12.0: supports D1 D2
[    0.167494] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.167499] pci 0000:00:12.0: PME# disabled
[    0.167516] pci 0000:00:13.0: [1106:337b] type 0 class 0x000600
[    0.167596] pci 0000:00:13.1: [1106:337a] type 1 class 0x000604
[    0.167746] pci 0000:01:00.0: [1002:4e51] type 0 class 0x000300
[    0.167772] pci 0000:01:00.0: reg 10: [mem 0xb0000000-0xbfffffff pref]
[    0.167785] pci 0000:01:00.0: reg 14: [io  0xe000-0xe0ff]
[    0.167794] pci 0000:01:00.0: reg 18: [mem 0xfeae0000-0xfeaeffff]
[    0.167825] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.167861] pci 0000:01:00.0: supports D1 D2
[    0.167879] pci 0000:01:00.1: [1002:4e71] type 0 class 0x000380
[    0.167893] pci 0000:01:00.1: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.167903] pci 0000:01:00.1: reg 14: [mem 0xfeaf0000-0xfeafffff]
[    0.167964] pci 0000:01:00.1: supports D1 D2
[    0.168064] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.168069] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.168074] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.168079] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff pref]
[    0.168132] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.168142] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.168224] pci 0000:00:13.1: PCI bridge to [bus 03-03] (subtractive decode)
[    0.168236] pci 0000:00:13.1:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.168239] pci 0000:00:13.1:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.168241] pci 0000:00:13.1:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.168243] pci 0000:00:13.1:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.168246] pci 0000:00:13.1:   bridge window [mem 0x50000000-0xdfffffff] (subtractive decode)
[    0.168248] pci 0000:00:13.1:   bridge window [mem 0xf0000000-0xfeafffff] (subtractive decode)
[    0.168267] pci_bus 0000:00: on NUMA node 0
[    0.168274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.168502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.168632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.168764]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.168906]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.176971] ACPI: PCI Root Bridge [PCI1] (domain 0000 [bus 80-ff])
[    0.177196] pci_root PNP0A08:00: host bridge window [mem 0xfeb00000-0xfebfffff]
[    0.177227] pci 0000:80:01.0: [1106:3288] type 0 class 0x000403
[    0.177254] pci 0000:80:01.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.177354] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.177359] pci 0000:80:01.0: PME# disabled
[    0.177417] pci_bus 0000:80: on NUMA node 0
[    0.177421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.177571]  pci0000:80: Requesting ACPI _OSC control (0x1d)
[    0.177575]  pci0000:80: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.177577] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.177739] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.177786] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.177831] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.177875] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.177923] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.177974] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.178025] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.178075] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.178308] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.178313] vgaarb: loaded
[    0.178314] vgaarb: bridge control possible 0000:01:00.0
[    0.178450] i2c-core: driver [aat2870] using legacy suspend method
[    0.178451] i2c-core: driver [aat2870] using legacy resume method
[    0.178569] SCSI subsystem initialized
[    0.180132] libata version 3.00 loaded.
[    0.180141] usbcore: registered new interface driver usbfs
[    0.180154] usbcore: registered new interface driver hub
[    0.180206] usbcore: registered new device driver usb
[    0.180341] PCI: Using ACPI for IRQ routing
[    0.185764] PCI: pci_cache_line_size set to 64 bytes
[    0.185899] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.185903] reserve RAM buffer: 000000004ffb0000 - 000000004fffffff 
[    0.186101] NetLabel: Initializing
[    0.186104] NetLabel:  domain hash size = 128
[    0.186105] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.186121] NetLabel:  unlabeled traffic allowed by default
[    0.196777] AppArmor: AppArmor Filesystem Enabled
[    0.196842] pnp: PnP ACPI init
[    0.196870] ACPI: bus type pnp registered
[    0.197056] pnp 00:00: [bus 00-7f]
[    0.197059] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.197062] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.197064] pnp 00:00: [io  0x0d00-0xffff window]
[    0.197066] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.197068] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.197071] pnp 00:00: [mem 0x50000000-0xdfffffff window]
[    0.197073] pnp 00:00: [mem 0xf0000000-0xfeafffff window]
[    0.197158] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.197255] pnp 00:01: [dma 4]
[    0.197257] pnp 00:01: [io  0x0000-0x000f]
[    0.197259] pnp 00:01: [io  0x0081-0x0083]
[    0.197261] pnp 00:01: [io  0x0087]
[    0.197262] pnp 00:01: [io  0x0089-0x008b]
[    0.197264] pnp 00:01: [io  0x008f]
[    0.197266] pnp 00:01: [io  0x00c0-0x00df]
[    0.197300] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.197309] pnp 00:02: [io  0x0061]
[    0.197345] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.197354] pnp 00:03: [io  0x00f0-0x00ff]
[    0.197375] pnp 00:03: [irq 13]
[    0.197406] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.197644] pnp 00:04: [io  0x02f8-0x02ff]
[    0.197650] pnp 00:04: [irq 3]
[    0.197653] pnp 00:04: [dma 0 disabled]
[    0.197759] pnp 00:04: Plug and Play ACPI device, IDs PNP0510 (active)
[    0.198026] pnp 00:05: [io  0x03f0-0x03f5]
[    0.198028] pnp 00:05: [io  0x03f7]
[    0.198034] pnp 00:05: [irq 6]
[    0.198036] pnp 00:05: [dma 2]
[    0.198095] pnp 00:05: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.198357] pnp 00:06: [io  0x0378-0x037f]
[    0.198359] pnp 00:06: [io  0x0778-0x077b]
[    0.198365] pnp 00:06: [irq 7]
[    0.198367] pnp 00:06: [dma 3]
[    0.198507] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.198837] pnp 00:07: [io  0x0330-0x0331]
[    0.198845] pnp 00:07: [irq 5]
[    0.198901] pnp 00:07: Plug and Play ACPI device, IDs PNPb006 (active)
[    0.199020] pnp 00:08: [io  0x0010-0x001f]
[    0.199022] pnp 00:08: [io  0x0022-0x003f]
[    0.199029] pnp 00:08: [io  0x0044-0x005f]
[    0.199031] pnp 00:08: [io  0x0062-0x0063]
[    0.199033] pnp 00:08: [io  0x0065-0x006f]
[    0.199034] pnp 00:08: [io  0x0072-0x007f]
[    0.199036] pnp 00:08: [io  0x0080]
[    0.199038] pnp 00:08: [io  0x0084-0x0086]
[    0.199040] pnp 00:08: [io  0x0088]
[    0.199042] pnp 00:08: [io  0x008c-0x008e]
[    0.199044] pnp 00:08: [io  0x0090-0x009f]
[    0.199046] pnp 00:08: [io  0x00a2-0x00bf]
[    0.199047] pnp 00:08: [io  0x00e0-0x00ef]
[    0.199049] pnp 00:08: [io  0x0295-0x0296]
[    0.199051] pnp 00:08: [io  0x03e0-0x03e7]
[    0.199053] pnp 00:08: [io  0x04d0-0x04d1]
[    0.199055] pnp 00:08: [io  0x0800-0x087f]
[    0.199057] pnp 00:08: [io  0x0400-0x041f]
[    0.199059] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.199061] pnp 00:08: [mem 0xfecc0000-0xfecc0fff]
[    0.199063] pnp 00:08: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.199159] system 00:08: [io  0x0295-0x0296] has been reserved
[    0.199162] system 00:08: [io  0x03e0-0x03e7] has been reserved
[    0.199164] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.199167] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.199169] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.199173] system 00:08: [mem 0xfecc0000-0xfecc0fff] could not be reserved
[    0.199176] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199212] pnp 00:09: [io  0x0070-0x0071]
[    0.199218] pnp 00:09: [irq 8]
[    0.199260] pnp 00:09: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.199304] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.199306] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.199365] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.199367] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.199371] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199399] pnp 00:0b: [io  0x0060]
[    0.199401] pnp 00:0b: [io  0x0064]
[    0.199407] pnp 00:0b: [irq 1]
[    0.199452] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.199494] pnp 00:0c: [irq 12]
[    0.199538] pnp 00:0c: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.199768] pnp 00:0d: [io  0x03f8-0x03ff]
[    0.199774] pnp 00:0d: [irq 4]
[    0.199776] pnp 00:0d: [dma 0 disabled]
[    0.199852] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.199882] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.199946] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.199950] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200145] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.200147] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.200149] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.200152] pnp 00:0f: [mem 0x00100000-0x4fffffff]
[    0.200154] pnp 00:0f: [mem 0xfeb00000-0xffffffff]
[    0.200219] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.200222] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.200225] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.200227] system 00:0f: [mem 0x00100000-0x4fffffff] could not be reserved
[    0.200230] system 00:0f: [mem 0xfeb00000-0xffffffff] could not be reserved
[    0.200233] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200454] pnp 00:10: [bus 80-ff]
[    0.200457] pnp 00:10: [io  0x0000 window]
[    0.200459] pnp 00:10: [mem 0xfeb00000-0xfebfffff window]
[    0.200510] pnp 00:10: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.200556] pnp: PnP ACPI: found 17 devices
[    0.200558] ACPI: ACPI bus type pnp unregistered
[    0.200564] PnPBIOS: Disabled by ACPI PNP
[    0.237079] Switching to clocksource acpi_pm
[    0.237207] PCI: max bus depth: 1 pci_try_num: 2
[    0.237270] pci 0000:00:02.0: BAR 14: assigned [mem 0x50000000-0x503fffff]
[    0.237274] pci 0000:00:02.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.237280] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.237284] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.237289] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.237294] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff pref]
[    0.237301] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.237304] pci 0000:00:02.0:   bridge window [io  0x1000-0x1fff]
[    0.237310] pci 0000:00:02.0:   bridge window [mem 0x50000000-0x503fffff]
[    0.237315] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.237323] pci 0000:00:13.1: PCI bridge to [bus 03-03]
[    0.237354] pci 0000:00:01.0: setting latency timer to 64
[    0.237362] pci 0000:00:02.0: enabling device (0106 -> 0107)
[    0.237396] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.237401] pci 0000:00:02.0: setting latency timer to 64
[    0.237409] pci 0000:00:13.1: setting latency timer to 64
[    0.237413] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.237416] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.237418] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.237420] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.237422] pci_bus 0000:00: resource 8 [mem 0x50000000-0xdfffffff]
[    0.237425] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfeafffff]
[    0.237427] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.237429] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.237432] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xcfffffff pref]
[    0.237434] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.237436] pci_bus 0000:02: resource 1 [mem 0x50000000-0x503fffff]
[    0.237439] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff pref]
[    0.237441] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.237443] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.237446] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.237448] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.237450] pci_bus 0000:03: resource 8 [mem 0x50000000-0xdfffffff]
[    0.237452] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfeafffff]
[    0.237456] pci_bus 0000:80: resource 4 [mem 0xfeb00000-0xfebfffff]
[    0.237536] NET: Registered protocol family 2
[    0.237643] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.237951] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.239055] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.239921] TCP: Hash tables configured (established 131072 bind 65536)
[    0.239925] TCP reno registered
[    0.239931] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.239955] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.239955] NET: Registered protocol family 1
[    0.239955] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.239955] PCI: CLS mismatch (32 != 64), using 64 bytes
[    0.239955] pci 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.239955] pci 0000:00:10.0: PCI INT A disabled
[    0.239955] pci 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.239955] pci 0000:00:10.1: PCI INT B disabled
[    0.239955] pci 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.239955] pci 0000:00:10.2: PCI INT C disabled
[    0.239955] pci 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.239955] pci 0000:00:10.3: PCI INT D disabled
[    0.239955] pci 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.239955] pci 0000:00:10.4: PCI INT C disabled
[    0.239955] pci 0000:01:00.0: Boot video device
[    0.239978] audit: initializing netlink socket (disabled)
[    0.240031] type=2000 audit(1342155852.236:1): initialized
[    0.266818] highmem bounce pool size: 64 pages
[    0.266826] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.280762] VFS: Disk quotas dquot_6.5.2
[    0.280848] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.281485] fuse init (API version 7.17)
[    0.281602] msgmni has been set to 1691
[    0.282007] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.282038] io scheduler noop registered
[    0.282040] io scheduler deadline registered
[    0.282048] io scheduler cfq registered (default)
[    0.282253] pcieport 0000:00:02.0: setting latency timer to 64
[    0.282332] pcieport 0000:00:02.0: irq 64 for MSI/MSI-X
[    0.282508] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.282526] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.282531] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.282550] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.282611] pciehp 0000:00:02.0:pcie04: HPC vendor_id 1106 device_id a208 ss_vid 0 ss_did 0
[    0.282637] pciehp 0000:00:02.0:pcie04: service driver pciehp loaded
[    0.282643] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.282738] intel_idle: MWAIT substates: 0x22220
[    0.282740] intel_idle: does not run on family 6 model 23
[    0.282867] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.282877] ACPI: Sleep Button [SLPB]
[    0.282926] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.282929] ACPI: Power Button [PWRB]
[    0.282971] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.282974] ACPI: Power Button [PWRF]
[    0.285096] ERST: Table is not found!
[    0.285100] GHES: HEST is not enabled!
[    0.285346] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.292113] isapnp: Scanning for PnP cards...
[    0.305764] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.364504] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.601381] Freeing initrd memory: 20004k freed
[    0.652854] isapnp: No Plug & Play device found
[    0.728686] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.744312] Linux agpgart interface v0.103
[    0.744405] agpgart: Detected VIA PT880 Ultra chipset
[    0.758218] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.759845] brd: module loaded
[    0.760685] loop: module loaded
[    0.760962] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.761013] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.761393] Fixed MDIO Bus: probed
[    0.761412] tun: Universal TUN/TAP device driver, 1.6
[    0.761414] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.761483] PPP generic driver version 2.4.2
[    0.761607] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.761632] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.761659] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.761705] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.761736] ehci_hcd 0000:00:10.4: debug port 1
[    0.761773] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfe9ffc00
[    0.772019] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.772169] hub 1-0:1.0: USB hub found
[    0.772174] hub 1-0:1.0: 8 ports detected
[    0.772261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.772280] uhci_hcd: USB Universal Host Controller Interface driver
[    0.772312] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.772320] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.772367] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.772400] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000c480
[    0.772528] hub 2-0:1.0: USB hub found
[    0.772533] hub 2-0:1.0: 2 ports detected
[    0.772599] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.772606] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.772667] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.772699] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000c800
[    0.772827] hub 3-0:1.0: USB hub found
[    0.772832] hub 3-0:1.0: 2 ports detected
[    0.772900] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.772909] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.772958] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.772981] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c880
[    0.773106] hub 4-0:1.0: USB hub found
[    0.773110] hub 4-0:1.0: 2 ports detected
[    0.773180] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.773188] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.773235] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.773267] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000cc00
[    0.773395] hub 5-0:1.0: USB hub found
[    0.773399] hub 5-0:1.0: 2 ports detected
[    0.773513] usbcore: registered new interface driver libusual
[    0.773582] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.774032] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.774044] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.774221] mousedev: PS/2 mouse device common for all mice
[    0.774416] rtc_cmos 00:09: RTC can wake from S4
[    0.774593] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.774628] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.774700] device-mapper: uevent: version 1.0.3
[    0.774781] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.774823] EISA: Probing bus 0 at eisa.0
[    0.774825] EISA: Cannot allocate resource for mainboard
[    0.774827] Cannot allocate resource for EISA slot 1
[    0.774829] Cannot allocate resource for EISA slot 2
[    0.774831] Cannot allocate resource for EISA slot 3
[    0.774833] Cannot allocate resource for EISA slot 4
[    0.774834] Cannot allocate resource for EISA slot 5
[    0.774836] Cannot allocate resource for EISA slot 6
[    0.774838] Cannot allocate resource for EISA slot 7
[    0.774840] Cannot allocate resource for EISA slot 8
[    0.774841] EISA: Detected 0 cards.
[    0.774856] cpufreq-nforce2: No nForce2 chipset.
[    0.774859] cpuidle: using governor ladder
[    0.774860] cpuidle: using governor menu
[    0.774863] EFI Variables Facility v0.08 2004-May-17
[    0.775134] TCP cubic registered
[    0.775265] NET: Registered protocol family 10
[    0.775831] NET: Registered protocol family 17
[    0.775836] Registering the dns_resolver key type
[    0.775869] Using IPI No-Shortcut mode
[    0.775991] PM: Hibernation image not present or could not be loaded.
[    0.776031] registered taskstats version 1
[    0.788994]   Magic number: 4:24:62
[    0.789164] rtc_cmos 00:09: setting system clock to 2012-07-13 05:04:14 UTC (1342155854)
[    0.789194] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.789196] EDD information not available.
[    0.789425] Freeing unused kernel memory: 740k freed
[    0.789757] Write protecting the kernel text: 5816k
[    0.789775] Write protecting the kernel read-only data: 2376k
[    0.789776] NX-protecting the kernel data: 4424k
[    0.797114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.812651] udevd[86]: starting version 175
[    0.907458] Floppy drive(s): fd0 is 1.44M
[    0.926516] FDC 0 is a post-1991 82077
[    0.928508] sata_via 0000:00:0f.0: version 2.6
[    0.928533] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.928571] sata_via 0000:00:0f.0: routed to hard irq line 10
[    0.929761] scsi0 : sata_via
[    0.930625] [drm] Initialized drm 1.1.0 20060810
[    0.932446] scsi1 : sata_via
[    0.934373] ata1: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 21
[    0.934379] ata2: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 21
[    0.934485] pata_via 0000:00:0f.1: version 0.3.4
[    0.938754] scsi2 : pata_via
[    0.941618] scsi3 : pata_via
[    0.943500] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.943505] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.953456] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    0.953529] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.954163] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xfe9ff800, 00:25:22:47:70:ca, IRQ 23
[    0.954875] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1
[    1.136023] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.240023] Refined TSC clocksource calibration: 2493.751 MHz.
[    1.240030] Switching to clocksource tsc
[    1.284377] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S222A, SB02, max UDMA/66
[    1.284382] ata3.01: ATAPI: CD-RW   CDR-2440MB, 5SGC, max UDMA/33
[    1.284387] ata3.00: limited to UDMA/33 due to 40-wire cable
[    1.300233] ata3.00: configured for UDMA/33
[    1.316232] ata3.01: configured for UDMA/33
[    1.348009] ata2: SATA link up 1.5 Gbps (SStatus 123 SControl 300)
[    1.384010] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    1.512554] ata2.00: ATA-8: WDC WD7500AARX-00N0YB0, 51.0AB51, max UDMA/133
[    1.512557] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.520560] ata2.00: configured for UDMA/133
[    1.520738] scsi 1:0:0:0: Direct-Access     ATA      WDC WD7500AARX-0 51.0 PQ: 0 ANSI: 5
[    1.520979] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.520998] sd 1:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.521001] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.521051] sd 1:0:0:0: [sda] Write Protect is off
[    1.521058] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.521081] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.521790] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S222A  SB02 PQ: 0 ANSI: 5
[    1.524136] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.524140] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.524308] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.524488] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.525202] scsi 2:0:1:0: CD-ROM            CD-RW    CDR-2440MB       5SGC PQ: 0 ANSI: 5
[    1.526054] sr1: scsi3-mmc drive: 100x/40x writer cd/rw xa/form2 cdda tray
[    1.526206] sr 2:0:1:0: Attached scsi CD-ROM sr1
[    1.526383] sr 2:0:1:0: Attached scsi generic sg2 type 5
[    1.696750] ata4.00: ATA-6: ExcelStor Technology J360, V22OA63A, max UDMA/100
[    1.696754] ata4.00: 120103200 sectors, multi 16: LBA48 
[    1.720607] ata4.00: configured for UDMA/100
[    1.720764] scsi 3:0:0:0: Direct-Access     ATA      ExcelStor Techno V22O PQ: 0 ANSI: 5
[    1.720994] sd 3:0:0:0: [sdb] 120103200 512-byte logical blocks: (61.4 GB/57.2 GiB)
[    1.721034] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.721067] sd 3:0:0:0: [sdb] Write Protect is off
[    1.721071] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.721093] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.760043]  sdb: sdb1 sdb2 < sdb5 >
[    1.760444] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.910757]  sda: sda1
[    1.911055] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.928564] [drm] radeon defaulting to kernel modesetting.
[    1.928568] [drm] radeon kernel modesetting enabled.
[    1.928713] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.929753] [drm] initializing kernel modesetting (RV350 0x1002:0x4E51 0x174B:0x0200).
[    1.929793] [drm] register mmio base: 0xFEAE0000
[    1.929795] [drm] register mmio size: 65536
[    1.932443] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[    1.932479] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[    1.932627] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[    1.932650] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
[    1.932654] [drm] Generation 2 PCI interface, using max accessible memory
[    1.932659] radeon 0000:01:00.0: VRAM: 256M 0x00000000B0000000 - 0x00000000BFFFFFFF (256M used)
[    1.932680] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.932682] [drm] Driver supports precise vblank timestamp query.
[    1.932720] [drm] radeon: irq initialized.
[    1.934744] [drm] Detected VRAM RAM=256M, BAR=256M
[    1.934749] [drm] RAM width 128bits DDR
[    1.934853] [TTM] Zone  kernel: Available graphics memory: 443454 kiB.
[    1.934855] [TTM] Zone highmem: Available graphics memory: 641954 kiB.
[    1.934858] [TTM] Initializing pool allocator.
[    1.934894] [drm] radeon: 256M of VRAM memory ready
[    1.934896] [drm] radeon: 256M of GTT memory ready.
[    1.934949] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[    1.936385] radeon 0000:01:00.0: WB disabled
[    1.936533] [drm] Loading R300 Microcode
[    1.943287] [drm] radeon: ring at 0x00000000D0001000
[    1.943316] [drm] ring test succeeded in 0 usecs
[    1.943638] [drm] radeon: ib pool ready.
[    1.943738] [drm] ib test succeeded in 0 usecs
[    1.944654] [drm] Radeon Display Connectors
[    1.944657] [drm] Connector 0:
[    1.944658] [drm]   VGA
[    1.944661] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    1.944662] [drm]   Encoders:
[    1.944664] [drm]     CRT1: INTERNAL_DAC1
[    1.944665] [drm] Connector 1:
[    1.944667] [drm]   DVI-I
[    1.944668] [drm]   HPD1
[    1.944670] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    1.944671] [drm]   Encoders:
[    1.944672] [drm]     CRT2: INTERNAL_DAC2
[    1.944674] [drm]     DFP1: INTERNAL_TMDS1
[    1.944675] [drm] Connector 2:
[    1.944677] [drm]   S-video
[    1.944678] [drm]   Encoders:
[    1.944679] [drm]     TV1: INTERNAL_DAC2
[    2.066206] [drm] fb mappable at 0xB0040000
[    2.066210] [drm] vram apper at 0xB0000000
[    2.066212] [drm] size 7057408
[    2.066213] [drm] fb depth is 24
[    2.066215] [drm]    pitch is 6720
[    2.066333] fbcon: radeondrmfb (fb0) is primary device
[    2.066474] Console: switching to colour frame buffer device 210x65
[    2.066522] fb0: radeondrmfb frame buffer device
[    2.066523] drm: registered panic notifier
[    2.066541] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[    3.507692] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   20.306510] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.336341] udevd[355]: starting version 175
[   20.386406] lp: driver loaded but no devices found
[   20.432521] Adding 1309692k swap on /dev/sdb5.  Priority:-1 extents:1 across:1309692k 
[   20.456838] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.559952] parport_pc 00:06: reported by Plug and Play ACPI
[   20.560130] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   20.659362] lp0: using parport0 (interrupt-driven).
[   20.678126] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   20.825318] Linux video capture interface: v2.00
[   20.828984] gspca_main: v2.14.0 registered
[   20.829858] gspca_main: zc3xx-2.14.0 probing 0471:0325
[   20.856798] type=1400 audit(1342155874.566:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=601 comm="apparmor_parser"
[   20.857270] type=1400 audit(1342155874.566:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=601 comm="apparmor_parser"
[   20.857528] type=1400 audit(1342155874.566:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=601 comm="apparmor_parser"
[   20.858573] snd_hda_intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.858669] snd_hda_intel 0000:80:01.0: irq 65 for MSI/MSI-X
[   20.858843] snd_hda_intel 0000:80:01.0: setting latency timer to 64
[   20.858850] snd_hda_intel 0000:80:01.0: PCI: Disallowing DAC for device
[   20.892048] hda-intel: spurious response 0x101:0x0, last cmd=0xdf0009
[   20.892085] hda-intel: spurious response 0x20025:0x0, last cmd=0xdf0009
[   20.892087] hda-intel: spurious response 0x1d:0x0, last cmd=0xdf0009
[   20.892149] hda-intel: spurious response 0x1d:0x0, last cmd=0xef0009
[   20.892151] hda-intel: spurious response 0xf00000:0x0, last cmd=0xff0009
[   20.893141] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893161] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893179] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893199] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893221] hda-intel: spurious response 0x18490662:0x0, last cmd=0x1f0500
[   20.893242] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893262] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893283] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.893303] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0500
[   20.907377] hda_codec: ALC662 rev1: SKU not ready 0x00400300
[   20.907746] hda_codec: Too many connections 10 for NID 0x23
[   20.907782] hda_codec: Too many connections 10 for NID 0x23
[   20.907784] hda_codec: Too many connections 10 for NID 0x23
[   20.907785] hda_codec: Too many connections 10 for NID 0x23
[   20.907787] hda_codec: Too many connections 10 for NID 0x23
[   20.907790] hda_codec: Too many connections 10 for NID 0x23
[   20.907792] hda_codec: Too many connections 10 for NID 0x23
[   20.908663] hda_codec: Too many connections 10 for NID 0x23
[   20.908671] hda_codec: Too many connections 10 for NID 0x23
[   20.908673] hda_codec: Too many connections 10 for NID 0x23
[   20.908726] hda_codec: Too many connections 10 for NID 0x23
[   20.908728] hda_codec: Too many connections 10 for NID 0x23
[   21.019804] psmouse serio1: logips2pp: Detected unknown Logitech mouse model 115
[   21.063171] input: zc3xx as /devices/pci0000:00/0000:00:10.0/usb2/2-2/input/input4
[   21.065483] usbcore: registered new interface driver zc3xx
[   21.217397] ppdev: user-space parallel port driver
[   21.326851] init: failsafe main process (758) killed by TERM signal
[   21.513556] Bluetooth: Core ver 2.16
[   21.513678] NET: Registered protocol family 31
[   21.513681] Bluetooth: HCI device and connection manager initialized
[   21.513684] Bluetooth: HCI socket layer initialized
[   21.513687] Bluetooth: L2CAP socket layer initialized
[   21.513696] Bluetooth: SCO socket layer initialized
[   21.526440] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.526444] Bluetooth: BNEP filters: protocol multicast
[   21.534170] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   21.582848] Bluetooth: RFCOMM TTY layer initialized
[   21.582860] Bluetooth: RFCOMM socket layer initialized
[   21.582861] Bluetooth: RFCOMM ver 1.11
[   21.673453] type=1400 audit(1342155875.382:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=835 comm="apparmor_parser"
[   21.674125] type=1400 audit(1342155875.382:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=835 comm="apparmor_parser"
[   21.736390] type=1400 audit(1342155875.446:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=860 comm="apparmor_parser"
[   21.737523] type=1400 audit(1342155875.446:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=860 comm="apparmor_parser"
[   21.737774] type=1400 audit(1342155875.446:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=860 comm="apparmor_parser"
[   21.743678] type=1400 audit(1342155875.450:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=862 comm="apparmor_parser"
[   21.747389] type=1400 audit(1342155875.454:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=863 comm="apparmor_parser"
[   21.971708] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   22.253307] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)
[   22.254466] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)
[   22.731862] hda-intel: spurious response 0x0:0x0, last cmd=0x1fb8000
[   22.731878] hda-intel: spurious response 0x100101:0x0, last cmd=0x1fb8000
[   22.731899] hda-intel: spurious response 0x10001:0x0, last cmd=0x1fb8000
[   22.731920] hda-intel: spurious response 0x101:0x0, last cmd=0x1fb8000
[   22.731940] hda-intel: spurious response 0x20025:0x0, last cmd=0x1fb8000
[   22.731961] hda-intel: spurious response 0x1d:0x0, last cmd=0x1fb8000
[   22.731981] hda-intel: spurious response 0x1d:0x0, last cmd=0x1fb8000
[   22.732019] hda-intel: spurious response 0x1d:0x0, last cmd=0x1fb8000
[   22.732029] hda-intel: spurious response 0xf00000:0x0, last cmd=0x1fb8000
[   22.732050] hda-intel: spurious response 0x211:0x0, last cmd=0x1fb8000
[   22.732071] hda-intel: spurious response 0xf00000:0x0, last cmd=0x1fb8000
[   22.732092] hda-intel: spurious response 0x10011b:0x0, last cmd=0x1fb8000
[   22.732113] hda-intel: spurious response 0x10011b:0x0, last cmd=0x1fb8000
[   22.732133] hda-intel: spurious response 0xf00000:0x0, last cmd=0x1fb8000
[   22.732154] hda-intel: spurious response 0x20010b:0x0, last cmd=0x1fb8000
[   22.732175] hda-intel: spurious response 0x20010b:0x0, last cmd=0x1fb8000
[   22.732197] hda-intel: spurious response 0x20010b:0x0, last cmd=0x1fb8000
[   22.732218] hda-intel: spurious response 0x20010b:0x0, last cmd=0x1fb8000
[   22.732322] hda-intel: spurious response 0xf00000:0x0, last cmd=0x835011
[   22.732342] hda-intel: spurious response 0x40018d:0x0, last cmd=0x835011
[   22.732363] hda-intel: spurious response 0x40018d:0x0, last cmd=0x835011
[   22.732384] hda-intel: spurious response 0x40018d:0x0, last cmd=0x835011
[   22.732404] hda-intel: spurious response 0xf00000:0x0, last cmd=0x835011
[   22.732426] hda-intel: spurious response 0x40018f:0x0, last cmd=0x835011
[   22.732447] hda-intel: spurious response 0x40018f:0x0, last cmd=0x835011
[   22.732467] hda-intel: spurious response 0x40018d:0x0, last cmd=0x835011
[   22.732488] hda-intel: spurious response 0x40018f:0x0, last cmd=0x835011
[   22.732509] hda-intel: spurious response 0x400001:0x0, last cmd=0x835011
[   22.732604] hda-intel: spurious response 0xf00040:0x0, last cmd=0xcb0000
[   22.732654] hda-intel: spurious response 0x20010b:0x0, last cmd=0x11b0000
[   22.732674] hda-intel: spurious response 0x10ec0662:0x0, last cmd=0x11b0000
[   22.732845] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)
[   22.732862] hda-intel: spurious response 0x1d:0x0, last cmd=0x1f000d
[   22.732883] hda-intel: spurious response 0xf00000:0x0, last cmd=0x1f000d
[   22.732903] hda-intel: spurious response 0x211:0x0, last cmd=0x1f000d
[   22.733029] hda-intel: spurious response 0x20010b:0x0, last cmd=0xbb2000
[   22.733049] hda-intel: spurious response 0x20010b:0x0, last cmd=0xbb2000
[   22.733070] hda-intel: spurious response 0x20010b:0x0, last cmd=0xbb2000
[   22.733091] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733111] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733132] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733153] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733174] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733194] hda-intel: spurious response 0x40018d:0x0, last cmd=0xbb2000
[   22.733216] hda-intel: spurious response 0x40018d:0x0, last cmd=0xbb2000
[   22.733236] hda-intel: spurious response 0x40018d:0x0, last cmd=0xbb2000
[   22.733257] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733277] hda-intel: spurious response 0x40018f:0x0, last cmd=0xbb2000
[   22.733298] hda-intel: spurious response 0x40018f:0x0, last cmd=0xbb2000
[   22.733320] hda-intel: spurious response 0x40018d:0x0, last cmd=0xbb2000
[   22.733340] hda-intel: spurious response 0x40018f:0x0, last cmd=0xbb2000
[   22.733361] hda-intel: spurious response 0x400001:0x0, last cmd=0xbb2000
[   22.733382] hda-intel: spurious response 0x400000:0x0, last cmd=0xbb2000
[   22.733403] hda-intel: spurious response 0x400300:0x0, last cmd=0xbb2000
[   22.733424] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733445] hda-intel: spurious response 0xf00040:0x0, last cmd=0xbb2000
[   22.733465] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733486] hda-intel: spurious response 0x20010b:0x0, last cmd=0xbb2000
[   22.733510] hda-intel: spurious response 0x20010b:0x0, last cmd=0xbb2000
[   22.733528] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733549] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733569] hda-intel: spurious response 0xf00000:0x0, last cmd=0xbb2000
[   22.733590] hda-intel: spurious response 0x40041e01:0x0, last cmd=0xbb2000
[   22.733611] hda-intel: spurious response 0x20:0x0, last cmd=0xbb2000
[   22.733632] hda-intel: spurious response 0x144e120:0x0, last cmd=0xbb2000
[   22.733653] hda-intel: spurious response 0x40:0x0, last cmd=0xbb2000
[   22.733678] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733694] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733714] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733736] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733756] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733778] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733798] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733819] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733839] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733861] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733882] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733902] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733923] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733944] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.733965] hda-intel: spurious response 0x18490662:0x0, last cmd=0xbb2000
[   22.733985] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734006] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734027] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734049] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734068] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734090] hda-intel: spurious response 0xf:0x0, last cmd=0xbb2000
[   22.734110] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734130] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734152] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734173] hda-intel: spurious response 0x11:0x0, last cmd=0xbb2000
[   22.734193] hda-intel: spurious response 0xa:0x0, last cmd=0xbb2000
[   22.734219] hda-intel: spurious response 0x1b1a1918:0x0, last cmd=0xbb2000
[   22.734234] hda-intel: spurious response 0x15141d1c:0x0, last cmd=0xbb2000
[   22.734255] hda-intel: spurious response 0xb16:0x0, last cmd=0xbb2000
[   22.734276] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734296] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734317] hda-intel: spurious response 0x1:0x0, last cmd=0xbb2000
[   22.734338] hda-intel: spurious response 0x23:0x0, last cmd=0xbb2000
[   22.734359] hda-intel: spurious response 0x2:0x0, last cmd=0xbb2000
[   22.734380] hda-intel: spurious response 0xb02:0x0, last cmd=0xbb2000
[   22.734400] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734422] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734443] hda-intel: spurious response 0x0:0x0, last cmd=0xbb2000
[   22.734505] hda-intel: spurious response 0x1:0x0, last cmd=0x835011
[   22.734526] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734546] hda-intel: spurious response 0xf:0x0, last cmd=0x835011
[   22.734567] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734589] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734609] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734630] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734651] hda-intel: spurious response 0x0:0x0, last cmd=0x835011
[   22.734705] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)
[   22.734713] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734733] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734754] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734775] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734796] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734816] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734838] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734859] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734879] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734900] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734921] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734942] hda-intel: spurious response 0x80:0x0, last cmd=0x835000
[   22.734962] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.734983] hda-intel: spurious response 0x80:0x0, last cmd=0x835000
[   22.735004] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735025] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735046] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735066] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735087] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735109] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735129] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735150] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735171] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735192] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735214] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735236] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735255] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735276] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735297] hda-intel: spurious response 0x80:0x0, last cmd=0x835000
[   22.735317] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735337] hda-intel: spurious response 0x80:0x0, last cmd=0x835000
[   22.735359] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735380] hda-intel: spurious response 0x80:0x0, last cmd=0x835000
[   22.735401] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735422] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735441] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.735462] hda-intel: spurious response 0x0:0x0, last cmd=0x835000
[   22.736126] init: alsa-restore main process (903) terminated with status 99
[   23.633178] init: plymouth-stop pre-start process (1293) terminated with status 1
[   32.856057] eth0: no IPv6 routers present
[   33.264743] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)
[   33.273722] hda_codec: num_steps = 0 for NID=0xb (ctl = Beep Playback Volume)

```
 
I know about "hda-intel: spurious response" bug that is "not critical" and still not fixed. this message was spewed before as well. awlays. though it didn't cause any immediate issues.

---

### Post by mastablasta on 2012-07-16
BUMP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 
3 days, many views, no reply....
 
is this a kernel issue (upstream)?

---

### Post by jmthomas on 2012-07-18
Have you tried running alsamixer from the command line?

I had a similar problem tonight. Opend up the mixer from the volume control and everything was maxed out but still no sound.

Opened alsamixer from a terminal and the master channel was completely off. Used the arrow keys to dial it up, then move to next channel and do the same.

Now my sound works fine.

By the way, my profile is incorrect. I am running Kubuntu 12.04 Precise Pangolin since it was realeased.

---

### Post by jmfal on 2012-07-18
Hi Mastablasta
Can you run
```
 aplay -l
```
And post the output

Does kubuntu have a :
```
 /etc/modprobe.d/alsa-base.conf   
```

File.
I haven't messed with kubuntu ,, but if sound is similar to ubuntu maybe I can help

---

### Post by mastablasta on 2012-07-19
forgot to run those two commands. i will do it when i get to the maschine.
 
in the mean time it seem the issue dissapeart for a short while and then came back.
 
alsa mixer is showing the card, however the volume is only one and maxed out. strange... the porblme is dummy output. it's like sometimes it doesn't get recognised. i used to have similar issue with Ubuntu 10.04, but then i with fresh install upgraded to 10.10 and decided to go Kubuntu while doing fresh install. it was working more or less on that version but sometimes it would stop working if the computer went into hibernaiton. a reboot solved ther issue.
 
 
fast forward to 12.04... when i go to sound settings it tells me that the card is not available anymore (in all it's verisons - analog, digital etc.) and ask me if i want to remove it (despite it being in listed hardware and PCI devices. for fun i decided to remove them, shut down the PC and turn it back on. 
 
lo and behold sound worked and card were found again. so i went to sound settings to see what is the situation there.
 
this time it told me that dummy output no longer exists on the system and if i want to remove it. i said ok to that and shutdwon the maschine and boot it back up. and sound worked. i then repeated this it still worked. it seemd like it was working. after some internet surfing and work done on the maschine i turned it off again as it was time to go to bed. next day a new boot, sound didn't work again.
---
 
Bottom line is, i do not understand why sometimes sound card is recognised and working great while other times it is not. the funny thing is that reloading modules makes it work propperly.
 
 
 
power management features are off (except for monitor) because they are not working anymore on this motherboard (it would go to sleep but then i couldn't wake it up again). used to work in 10.10. apparently there is a bug in 12.04 that is being worked on.

---

### Post by jmfal on 2012-07-19
It could be a problem with the new kernal,
but there are problems with the "via" "vt" modules also

when you get a chance post make/model of pc/laptop along with the other info

---

### Post by mastablasta on 2012-07-19
here we go, aplay... sound is showing dummy output.

```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and alsaconf

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

i am also attaching how alsamixer looks like when i get that dummy output. if the sound is working it is showing other channels as well.

if this can't really be fixed, how would i make a script to run the alsa reload command?

> It could be a problem with the new kernal,
but there are problems with the "via" "vt" modules also

when you get a chance post make/model of pc/laptop along with the other info

well a first few kernel versions in 12.04 worked perfectly. i am not sure how would i go about reporting this bug. 

PC is home made stuff. it's the only new mothebroard i could find that had DDR ram (it also has DDR2 slots :-O )and AGP for the graphics card.



edit: i found the motherboard. it's this one:   [http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2](http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2)

hmm maybe it has something to do with onboard HDMI sound output that is not connected to GPU. I mean this ATI GPU someitmes changes it's designation. for example in 10.10 final updates i had it recognised the card as Mobility Radeon series suddenly eventhough it's ATI radeon 9600 XT

---

### Post by jmfal on 2012-07-19
Alright, I found this in the
```
 zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz    
```

It should be in your pc, scroll down to snd-via82xx and see if it is there.
It should be, try this for now,, it might get rid of the dummy mixer.
Open the alsabase file:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf    
```

And add this line to end of file:
```
 options snd-hda-intel model=via82xx    
```
Save/close and be sure to save to the etc folder (click on etc in window, click save)

If that makes it worse change "snd-hda-intel" to "snd-hda-via"..

---

### Post by mastablasta on 2012-07-20
adding
 options snd-hda-intel model=via82xx 
to the end of file changed dummy output onto porpper card, however there was still no sound.
via option din't do anything and changed it back to dummy output.
so after a fe wreboots i decided to go to sound settings where it again suggested to remove all sound cards (options) from the system since dummy output was the working choice. then i did a reboot so it found the cards again only this time i added the upper line to the file. 

like expected (and like before) sound works again (for now). but i will need a few more shutdown and reboots to see if that options line actually fixes it's choice of sound card on boot so it won't select dummy output again as the correct sound option.

will post back if problem is solved and also some additonal informaiton on how to do it in KDE if anyone else stumbles on this issue.

---

### Post by jmfal on 2012-07-20
No Problem

Good Luck

---

### Post by mastablasta on 2012-07-21
well it worked yesterday when i tried it but doens't work again today. i believe it has something to do with power management settings. since nothign special was done yesterday, but monitor did turn off like it is set to. as explained before i disabled other featuers such as suspend or hibernate because they didn't work propperly anymore.
before sound worked well as long as computer didn't go into suspend.so i turned of suspend. and then after certian update hibernate didn't work propperly anymore as well.


Otherwsie it now shows dummy output inthe KDE mixer (don't really know it's name). it's also dummy output under sound settings, but the propper card with more volume levels (and all at max) is in alsamixer.


since the 
```
sudo alsa reload -c 
```
command seems to work i was thinking of making a script to be used as workarround.

---

### Post by jmfal on 2012-07-21
Did you edit the alsabase.conf file?

If you did go back and change it to "model=auto enable=yes
remember to save/close to the "etc"folder.

---

### Post by mastablasta on 2012-07-21
will try that as well. a funny thing happened. I created script as i said and sicne sound wasn't wokring again wife ran it whiel Amarok (the music player) was running. It gave a mesage in sound mixer saying: dropping dummy output, falling back to VIA8 (whatever the right card :-) ). i will try mode auto enable...

just to be clear.

i change
options snd-hda-intel model=via82xx

to
options snd-hda-intel model=auto enable=yes

inside this file: 
/etc/modprobe.d/alsa-base.conf

edit: it's not working :-(

---

