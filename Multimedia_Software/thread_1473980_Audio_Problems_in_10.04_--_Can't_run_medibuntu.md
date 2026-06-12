---
title: "Audio Problems in 10.04 -- Can't run medibuntu"
date: 2010-05-05
forum: Multimedia Software
---

### Post by Eyore15 on 2010-05-05
I upgraded a machine from 9.10 in the hopes that 10.04 will have fixed the audio problems that were present in the 9.10 installation -- the problem being that I have no audio.

When I check the pulseaudio volume meter, it shows audio present in both channels.  I've not been able to find anything where a mute button is checked.

Thinking it might be a codec, I tried to reinstall Medibuntu.  I get the error message: unable to lock /var/lib/dpkg. Is another process using it.  I've done a "ps -ef" looking for a process that might be causing problems, but no luck.

I'm using an Intel ICH5 audio board -- if I'm reading everything correctly.

Sorry for the multiple headings, but I thought they might be inter-related.

What I'd like:  audio playback from an on-line source (Hulu.com).

Ideas on how to make that happen will be greatly appreciated.  If medibuntu isn't part of the problem, just let that slide by, and I'll post a separate help "request" later.

tnx

mcm

---

### Post by Mercury_Alpha on 2010-05-05
Open up your system logs (System>Administration>Log File Viewer)and try to play an MP3 or other sound file. When you do that, your logs will record this attempt and log any errors. Then you can paste those errors in here using the [code] tags.

As for dpkg being locked, that error will come up if you have Synaptic open while trying to install something via the terminal.

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Eyore15 on 2010-05-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

I'm not quite sure what you mean when you talk about posting with code tags; could you clarify that for me?

tnx

---

### Post by lidex on 2010-05-06
Look at post #3. See the info in the box, just after Code: ?
You get that by clicking the '#' in the toolbar. Just copy the text, click the #, and paste. The cursor is automatically in between the tags. Alternately, paste the text, highlight it and click the #.

---

### Post by Eyore15 on 2010-05-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Here's the results of those commands on my machine.  I think I've done something wrong with the "head -n" command as you can see the output isn't anything there except an error code,I hope this can help me overcome a real impediment to adopting Ubuntu.

thx

mcm

```
c Eeyore15@eyore2:~$ uname -a
Linux eyore2 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
eyore15@eyore2:~$ 


eyore15@eyore2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
eyore15@eyore2:~$ 


eyore15@eyore2:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
eyore15@eyore2:~$ 


eyore15@eyore2:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/prob/asound/card*/codec#*' for reading: No such file or directory
eyore15@eyore2:~$ 


```

---

### Post by Eyore15 on 2010-05-06
> **Mercury_Alpha said:**
> Open up your system logs (System>Administration>Log File Viewer)and try to play an MP3 or other sound file. When you do that, your logs will record this attempt and log any errors. Then you can paste those errors in here using the ```
 tags.

As for dpkg being locked, that error will come up if you have Synaptic open while trying to install something via the terminal.

Here's the results of the log files while the computer was play a TV show over hulu.  I apologize for the length of the posting.  I didn't know what to trim off.

Here it comes

Here I go.

Thanks for helping to figure this out. 

[CODE]ay  6 16:59:59 eyore2 kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  6 16:59:59 eyore2 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="507" x-info="http://www.rsyslog.com"] (re)start
May  6 16:59:59 eyore2 rsyslogd: rsyslogd's groupid changed to 102
May  6 16:59:59 eyore2 rsyslogd: rsyslogd's userid changed to 101
May  6 16:59:59 eyore2 kernel: [    0.000000] Initializing cgroup subsys cpuset
May  6 16:59:59 eyore2 kernel: [    0.000000] Initializing cgroup subsys cpu
May  6 16:59:59 eyore2 kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
May  6 16:59:59 eyore2 kernel: [    0.000000] KERNEL supported cpus:
May  6 16:59:59 eyore2 kernel: [    0.000000]   Intel GenuineIntel
May  6 16:59:59 eyore2 kernel: [    0.000000]   AMD AuthenticAMD
May  6 16:59:59 eyore2 kernel: [    0.000000]   NSC Geode by NSC
May  6 16:59:59 eyore2 kernel: [    0.000000]   Cyrix CyrixInstead
May  6 16:59:59 eyore2 kernel: [    0.000000]   Centaur CentaurHauls
May  6 16:59:59 eyore2 kernel: [    0.000000]   Transmeta GenuineTMx86
May  6 16:59:59 eyore2 kernel: [    0.000000]   Transmeta TransmetaCPU
May  6 16:59:59 eyore2 kernel: [    0.000000]   UMC UMC UMC UMC
May  6 16:59:59 eyore2 kernel: [    0.000000] BIOS-provided physical RAM map:
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f770000 (usable)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 000000003f770000 - 000000003f77a000 (ACPI data)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 000000003f77a000 - 000000003f780000 (ACPI NVS)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 000000003f780000 - 0000000040000000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000] DMI present.
May  6 16:59:59 eyore2 kernel: [    0.000000] last_pfn = 0x3f770 max_arch_pfn = 0x100000
May  6 16:59:59 eyore2 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  6 16:59:59 eyore2 kernel: [    0.000000] Scanning 1 areas for low memory corruption
May  6 16:59:59 eyore2 kernel: [    0.000000] modified physical RAM map:
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 0000000000100000 - 000000003f770000 (usable)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 000000003f770000 - 000000003f77a000 (ACPI data)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 000000003f77a000 - 000000003f780000 (ACPI NVS)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 000000003f780000 - 0000000040000000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
May  6 16:59:59 eyore2 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
May  6 16:59:59 eyore2 kernel: [    0.000000] Using x86 segment limits to approximate NX protection
May  6 16:59:59 eyore2 kernel: [    0.000000] RAMDISK: 37859000 - 37fefd4b
May  6 16:59:59 eyore2 kernel: [    0.000000] Allocated new RAMDISK: 008de000 - 01074d4b
May  6 16:59:59 eyore2 kernel: [    0.000000] Move RAMDISK from 0000000037859000 - 0000000037fefd4a to 008de000 - 01074d4a
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: RSDP 000f64a0 00014 (v00 PTLTD )
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: RSDT 3f775106 00034 (v01 PTLTD    RSDT   060400D0  LTP 00000000)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: FACP 3f779ed8 00074 (v01 IBM    THINKCEN 060400D0 PTL  00000001)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: DSDT 3f77513a 04D9E (v01    IBM THINKCEN 060400D0 MSFT 0100000E)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: FACS 3f77afc0 00040
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: TCPA 3f779f4c 00032 (v01 IBM    THINKCEN 060400D0 PTL  00000001)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: APIC 3f779f7e 0005A (v01 PTLTD  ? APIC   060400D0  LTP 00000000)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: BOOT 3f779fd8 00028 (v01 PTLTD  $SBFTBL$ 060400D0  LTP 00000001)
May  6 16:59:59 eyore2 kernel: [    0.000000] 127MB HIGHMEM available.
May  6 16:59:59 eyore2 kernel: [    0.000000] 887MB LOWMEM available.
May  6 16:59:59 eyore2 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
May  6 16:59:59 eyore2 kernel: [    0.000000]   low ram: 0 - 377fe000
May  6 16:59:59 eyore2 kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
May  6 16:59:59 eyore2 kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
May  6 16:59:59 eyore2 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #5 [00008da000 - 00008dd0d8]              BRK ==> [00008da000 - 00008dd0d8]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #7 [00008de000 - 0001074d4b]      NEW RAMDISK ==> [00008de000 - 0001074d4b]
May  6 16:59:59 eyore2 kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
May  6 16:59:59 eyore2 kernel: [    0.000000] found SMP MP-table at [c00f63f0] f63f0
May  6 16:59:59 eyore2 kernel: [    0.000000] Zone PFN ranges:
May  6 16:59:59 eyore2 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  6 16:59:59 eyore2 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
May  6 16:59:59 eyore2 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f770
May  6 16:59:59 eyore2 kernel: [    0.000000] Movable zone start PFN for each node
May  6 16:59:59 eyore2 kernel: [    0.000000] early_node_map[3] active PFN ranges
May  6 16:59:59 eyore2 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May  6 16:59:59 eyore2 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
May  6 16:59:59 eyore2 kernel: [    0.000000]     0: 0x00000100 -> 0x0003f770
May  6 16:59:59 eyore2 kernel: [    0.000000] Using APIC driver default
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
May  6 16:59:59 eyore2 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
May  6 16:59:59 eyore2 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  6 16:59:59 eyore2 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  6 16:59:59 eyore2 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  6 16:59:59 eyore2 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May  6 16:59:59 eyore2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 16:59:59 eyore2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  6 16:59:59 eyore2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  6 16:59:59 eyore2 kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
May  6 16:59:59 eyore2 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  6 16:59:59 eyore2 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
May  6 16:59:59 eyore2 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u4194304
May  6 16:59:59 eyore2 kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
May  6 16:59:59 eyore2 kernel: [    0.000000] pcpu-alloc: [0] 0 
May  6 16:59:59 eyore2 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257820
May  6 16:59:59 eyore2 kernel: [    0.000000] Kernel command line: root=UUID=f85224c9-1157-4149-b383-4c49b2c6ed0d ro quiet splash 
May  6 16:59:59 eyore2 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
May  6 16:59:59 eyore2 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  6 16:59:59 eyore2 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  6 16:59:59 eyore2 kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  6 16:59:59 eyore2 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  6 16:59:59 eyore2 kernel: [    0.000000] Initializing CPU#0
May  6 16:59:59 eyore2 kernel: [    0.000000] allocated 5199040 bytes of page_cgroup
May  6 16:59:59 eyore2 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  6 16:59:59 eyore2 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f770)
May  6 16:59:59 eyore2 kernel: [    0.000000] Memory: 1009008k/1039808k available (4673k kernel code, 29936k reserved, 2122k data, 656k init, 130504k highmem)
May  6 16:59:59 eyore2 kernel: [    0.000000] virtual kernel memory layout:
May  6 16:59:59 eyore2 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
May  6 16:59:59 eyore2 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May  6 16:59:59 eyore2 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
May  6 16:59:59 eyore2 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
May  6 16:59:59 eyore2 kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
May  6 16:59:59 eyore2 kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
May  6 16:59:59 eyore2 kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
May  6 16:59:59 eyore2 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  6 16:59:59 eyore2 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  6 16:59:59 eyore2 kernel: [    0.000000] Hierarchical RCU implementation.
May  6 16:59:59 eyore2 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
May  6 16:59:59 eyore2 kernel: [    0.000000] Console: colour VGA+ 80x25
May  6 16:59:59 eyore2 kernel: [    0.000000] console [tty0] enabled
May  6 16:59:59 eyore2 kernel: [    0.000000] Fast TSC calibration using PIT
May  6 16:59:59 eyore2 kernel: [    0.000000] Detected 2792.913 MHz processor.
May  6 16:59:59 eyore2 kernel: [    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.82 BogoMIPS (lpj=11171652)
May  6 16:59:59 eyore2 kernel: [    0.008028] Security Framework initialized
May  6 16:59:59 eyore2 kernel: [    0.008060] AppArmor: AppArmor initialized
May  6 16:59:59 eyore2 kernel: [    0.008071] Mount-cache hash table entries: 512
May  6 16:59:59 eyore2 kernel: [    0.008239] Initializing cgroup subsys ns
May  6 16:59:59 eyore2 kernel: [    0.008246] Initializing cgroup subsys cpuacct
May  6 16:59:59 eyore2 kernel: [    0.008252] Initializing cgroup subsys memory
May  6 16:59:59 eyore2 kernel: [    0.008265] Initializing cgroup subsys devices
May  6 16:59:59 eyore2 kernel: [    0.008269] Initializing cgroup subsys freezer
May  6 16:59:59 eyore2 kernel: [    0.008272] Initializing cgroup subsys net_cls
May  6 16:59:59 eyore2 kernel: [    0.008306] CPU: Trace cache: 12K uops, L1 D cache: 16K
May  6 16:59:59 eyore2 kernel: [    0.008311] CPU: L2 cache: 1024K
May  6 16:59:59 eyore2 kernel: [    0.008314] CPU: Hyper-Threading is disabled
May  6 16:59:59 eyore2 kernel: [    0.008319] mce: CPU supports 4 MCE banks
May  6 16:59:59 eyore2 kernel: [    0.008334] CPU0: Thermal monitoring enabled (TM1)
May  6 16:59:59 eyore2 kernel: [    0.008342] using mwait in idle threads.
May  6 16:59:59 eyore2 kernel: [    0.008352] Performance Events: no PMU driver, software events only.
May  6 16:59:59 eyore2 kernel: [    0.008360] Checking 'hlt' instruction... OK.
May  6 16:59:59 eyore2 kernel: [    0.025273] SMP alternatives: switching to UP code
May  6 16:59:59 eyore2 kernel: [    0.038592] Freeing SMP alternatives: 19k freed
May  6 16:59:59 eyore2 kernel: [    0.038610] ACPI: Core revision 20090903
May  6 16:59:59 eyore2 kernel: [    0.050826] ftrace: converting mcount calls to 0f 1f 44 00 00
May  6 16:59:59 eyore2 kernel: [    0.050833] ftrace: allocating 21771 entries in 43 pages
May  6 16:59:59 eyore2 kernel: [    0.052076] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  6 16:59:59 eyore2 kernel: [    0.052378] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  6 16:59:59 eyore2 kernel: [    0.093297] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
May  6 16:59:59 eyore2 kernel: [    0.096001] Brought up 1 CPUs
May  6 16:59:59 eyore2 kernel: [    0.096001] Total of 1 processors activated (5585.82 BogoMIPS).
May  6 16:59:59 eyore2 kernel: [    0.096001] devtmpfs: initialized
May  6 16:59:59 eyore2 kernel: [    0.096001] regulator: core version 0.5
May  6 16:59:59 eyore2 kernel: [    0.096001] Time: 20:59:29  Date: 05/06/10
May  6 16:59:59 eyore2 kernel: [    0.096001] NET: Registered protocol family 16
May  6 16:59:59 eyore2 kernel: [    0.096001] EISA bus registered
May  6 16:59:59 eyore2 kernel: [    0.096001] ACPI: bus type pci registered
May  6 16:59:59 eyore2 kernel: [    0.096001] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=3
May  6 16:59:59 eyore2 kernel: [    0.096001] PCI: Using configuration type 1 for base access
May  6 16:59:59 eyore2 kernel: [    0.096001] bio: create slab <bio-0> at 0
May  6 16:59:59 eyore2 kernel: [    0.118195] ACPI: Interpreter enabled
May  6 16:59:59 eyore2 kernel: [    0.118203] ACPI: (supports S0 S1 S3 S4 S5)
May  6 16:59:59 eyore2 kernel: [    0.118234] ACPI: Using IOAPIC for interrupt routing
May  6 16:59:59 eyore2 kernel: [    0.157240] ACPI: No dock devices found.
May  6 16:59:59 eyore2 kernel: [    0.158821] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  6 16:59:59 eyore2 kernel: [    0.158870] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
May  6 16:59:59 eyore2 kernel: [    0.160528] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May  6 16:59:59 eyore2 kernel: [    0.160534] pci 0000:00:1d.7: PME# disabled
May  6 16:59:59 eyore2 kernel: [    0.160642] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
May  6 16:59:59 eyore2 kernel: [    0.160647] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
May  6 16:59:59 eyore2 kernel: [    0.160885] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
May  6 16:59:59 eyore2 kernel: [    0.160890] pci 0000:00:1f.5: PME# disabled
May  6 16:59:59 eyore2 kernel: [    0.161029] pci 0000:03:0b.0: PME# supported from D0 D3hot D3cold
May  6 16:59:59 eyore2 kernel: [    0.161034] pci 0000:03:0b.0: PME# disabled
May  6 16:59:59 eyore2 kernel: [    0.161072] pci 0000:00:1e.0: transparent bridge
May  6 16:59:59 eyore2 kernel: [    0.252092] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  6 16:59:59 eyore2 kernel: [    0.252242] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  6 16:59:59 eyore2 kernel: [    0.252389] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  6 16:59:59 eyore2 kernel: [    0.252537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  6 16:59:59 eyore2 kernel: [    0.252693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  6 16:59:59 eyore2 kernel: [    0.252850] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  6 16:59:59 eyore2 kernel: [    0.253006] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  6 16:59:59 eyore2 kernel: [    0.253163] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  6 16:59:59 eyore2 kernel: [    0.253314] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
May  6 16:59:59 eyore2 kernel: [    0.253324] vgaarb: loaded
May  6 16:59:59 eyore2 kernel: [    0.253500] SCSI subsystem initialized
May  6 16:59:59 eyore2 kernel: [    0.253675] usbcore: registered new interface driver usbfs
May  6 16:59:59 eyore2 kernel: [    0.253695] usbcore: registered new interface driver hub
May  6 16:59:59 eyore2 kernel: [    0.253729] usbcore: registered new device driver usb
May  6 16:59:59 eyore2 kernel: [    0.253920] ACPI: WMI: Mapper loaded
May  6 16:59:59 eyore2 kernel: [    0.253924] PCI: Using ACPI for IRQ routing
May  6 16:59:59 eyore2 kernel: [    0.254171] NetLabel: Initializing
May  6 16:59:59 eyore2 kernel: [    0.254174] NetLabel:  domain hash size = 128
May  6 16:59:59 eyore2 kernel: [    0.254176] NetLabel:  protocols = UNLABELED CIPSOv4
May  6 16:59:59 eyore2 kernel: [    0.254197] NetLabel:  unlabeled traffic allowed by default
May  6 16:59:59 eyore2 kernel: [    0.254326] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  6 16:59:59 eyore2 kernel: [    0.254332] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May  6 16:59:59 eyore2 kernel: [    0.254339] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
May  6 16:59:59 eyore2 kernel: [    0.260014] Switching to clocksource tsc
May  6 16:59:59 eyore2 kernel: [    0.262465] AppArmor: AppArmor Filesystem Enabled
May  6 16:59:59 eyore2 kernel: [    0.262482] pnp: PnP ACPI init
May  6 16:59:59 eyore2 kernel: [    0.262500] ACPI: bus type pnp registered
May  6 16:59:59 eyore2 kernel: [    0.312437] pnp: PnP ACPI: found 15 devices
May  6 16:59:59 eyore2 kernel: [    0.312441] ACPI: ACPI bus type pnp unregistered
May  6 16:59:59 eyore2 kernel: [    0.312446] PnPBIOS: Disabled by ACPI PNP
May  6 16:59:59 eyore2 kernel: [    0.312463] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312467] system 00:01: ioport range 0x800-0x87f has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312471] system 00:01: ioport range 0x1000-0x107f has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312475] system 00:01: ioport range 0x1100-0x111f has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312478] system 00:01: ioport range 0x1180-0x11bf has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312482] system 00:01: ioport range 0xe000-0xe00f has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312486] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312489] system 00:01: ioport range 0xfe10-0xfe11 has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312494] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
May  6 16:59:59 eyore2 kernel: [    0.312498] system 00:01: iomem range 0xfed90000-0xfed903ff has been reserved
May  6 16:59:59 eyore2 kernel: [    0.347276] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
May  6 16:59:59 eyore2 kernel: [    0.347281] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
May  6 16:59:59 eyore2 kernel: [    0.347288] pci 0000:00:1e.0:   MEM window: 0xe8100000-0xe81fffff
May  6 16:59:59 eyore2 kernel: [    0.347293] pci 0000:00:1e.0:   PREFETCH window: disabled
May  6 16:59:59 eyore2 kernel: [    0.347382] NET: Registered protocol family 2
May  6 16:59:59 eyore2 kernel: [    0.347506] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  6 16:59:59 eyore2 kernel: [    0.348018] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  6 16:59:59 eyore2 kernel: [    0.348588] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  6 16:59:59 eyore2 kernel: [    0.349048] TCP: Hash tables configured (established 131072 bind 65536)
May  6 16:59:59 eyore2 kernel: [    0.349052] TCP reno registered
May  6 16:59:59 eyore2 kernel: [    0.349207] NET: Registered protocol family 1
May  6 16:59:59 eyore2 kernel: [    0.349550] Simple Boot Flag at 0x35 set to 0x1
May  6 16:59:59 eyore2 kernel: [    0.349714] cpufreq-nforce2: No nForce2 chipset.
May  6 16:59:59 eyore2 kernel: [    0.349761] Scanning for low memory corruption every 60 seconds
May  6 16:59:59 eyore2 kernel: [    0.349916] audit: initializing netlink socket (disabled)
May  6 16:59:59 eyore2 kernel: [    0.349931] type=2000 audit(1273179569.347:1): initialized
May  6 16:59:59 eyore2 kernel: [    0.359643] Trying to unpack rootfs image as initramfs...
May  6 16:59:59 eyore2 kernel: [    0.372347] highmem bounce pool size: 64 pages
May  6 16:59:59 eyore2 kernel: [    0.372356] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May  6 16:59:59 eyore2 kernel: [    0.374209] VFS: Disk quotas dquot_6.5.2
May  6 16:59:59 eyore2 kernel: [    0.374289] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  6 16:59:59 eyore2 kernel: [    0.380283] fuse init (API version 7.13)
May  6 16:59:59 eyore2 kernel: [    0.380425] msgmni has been set to 1716
May  6 16:59:59 eyore2 kernel: [    0.380720] alg: No test for stdrng (krng)
May  6 16:59:59 eyore2 kernel: [    0.380797] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  6 16:59:59 eyore2 kernel: [    0.380802] io scheduler noop registered
May  6 16:59:59 eyore2 kernel: [    0.380804] io scheduler anticipatory registered
May  6 16:59:59 eyore2 kernel: [    0.380807] io scheduler deadline registered
May  6 16:59:59 eyore2 kernel: [    0.380862] io scheduler cfq registered (default)
May  6 16:59:59 eyore2 kernel: [    0.381007] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  6 16:59:59 eyore2 kernel: [    0.381045] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  6 16:59:59 eyore2 kernel: [    0.381190] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
May  6 16:59:59 eyore2 kernel: [    0.381196] ACPI: Power Button [PWRB]
May  6 16:59:59 eyore2 kernel: [    0.381260] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  6 16:59:59 eyore2 kernel: [    0.381264] ACPI: Power Button [PWRF]
May  6 16:59:59 eyore2 kernel: [    0.381507] processor LNXCPU:00: registered as cooling_device0
May  6 16:59:59 eyore2 kernel: [    0.426767] thermal LNXTHERM:01: registered as thermal_zone0
May  6 16:59:59 eyore2 kernel: [    0.426779] ACPI: Thermal Zone [THM0] (65 C)
May  6 16:59:59 eyore2 kernel: [    0.431999] isapnp: Scanning for PnP cards...
May  6 16:59:59 eyore2 kernel: [    0.437759] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
May  6 16:59:59 eyore2 kernel: [    0.437867] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 16:59:59 eyore2 kernel: [    0.437979] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 16:59:59 eyore2 kernel: [    0.438480] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 16:59:59 eyore2 kernel: [    0.438640] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 16:59:59 eyore2 kernel: [    0.444332] brd: module loaded
May  6 16:59:59 eyore2 kernel: [    0.444988] loop: module loaded
May  6 16:59:59 eyore2 kernel: [    0.445125] input: Macintosh mouse button emulation as /devices/virtual/input/input2
May  6 16:59:59 eyore2 kernel: [    0.445288] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
May  6 16:59:59 eyore2 kernel: [    0.445311] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  6 16:59:59 eyore2 kernel: [    0.445476] scsi0 : ata_piix
May  6 16:59:59 eyore2 kernel: [    0.489179] scsi1 : ata_piix
May  6 16:59:59 eyore2 kernel: [    0.490521] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
May  6 16:59:59 eyore2 kernel: [    0.490525] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
May  6 16:59:59 eyore2 kernel: [    0.491108] Fixed MDIO Bus: probed
May  6 16:59:59 eyore2 kernel: [    0.491163] PPP generic driver version 2.4.2
May  6 16:59:59 eyore2 kernel: [    0.491227] tun: Universal TUN/TAP device driver, 1.6
May  6 16:59:59 eyore2 kernel: [    0.491231] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  6 16:59:59 eyore2 kernel: [    0.491344] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  6 16:59:59 eyore2 kernel: [    0.491380] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
May  6 16:59:59 eyore2 kernel: [    0.491406] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  6 16:59:59 eyore2 kernel: [    0.491452] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
May  6 16:59:59 eyore2 kernel: [    0.491490] ehci_hcd 0000:00:1d.7: debug port 1
May  6 16:59:59 eyore2 kernel: [    0.500548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8080000
May  6 16:59:59 eyore2 kernel: [    0.520104] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May  6 16:59:59 eyore2 kernel: [    0.520261] usb usb1: configuration #1 chosen from 1 choice
May  6 16:59:59 eyore2 kernel: [    0.520309] hub 1-0:1.0: USB hub found
May  6 16:59:59 eyore2 kernel: [    0.520322] hub 1-0:1.0: 8 ports detected
May  6 16:59:59 eyore2 kernel: [    0.520410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  6 16:59:59 eyore2 kernel: [    0.520433] uhci_hcd: USB Universal Host Controller Interface driver
May  6 16:59:59 eyore2 kernel: [    0.520503] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  6 16:59:59 eyore2 kernel: [    0.520518] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  6 16:59:59 eyore2 kernel: [    0.520565] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May  6 16:59:59 eyore2 kernel: [    0.520602] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
May  6 16:59:59 eyore2 kernel: [    0.520721] usb usb2: configuration #1 chosen from 1 choice
May  6 16:59:59 eyore2 kernel: [    0.520758] hub 2-0:1.0: USB hub found
May  6 16:59:59 eyore2 kernel: [    0.520769] hub 2-0:1.0: 2 ports detected
May  6 16:59:59 eyore2 kernel: [    0.520832] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  6 16:59:59 eyore2 kernel: [    0.520843] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  6 16:59:59 eyore2 kernel: [    0.520883] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
May  6 16:59:59 eyore2 kernel: [    0.520914] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
May  6 16:59:59 eyore2 kernel: [    0.521027] usb usb3: configuration #1 chosen from 1 choice
May  6 16:59:59 eyore2 kernel: [    0.521063] hub 3-0:1.0: USB hub found
May  6 16:59:59 eyore2 kernel: [    0.521073] hub 3-0:1.0: 2 ports detected
May  6 16:59:59 eyore2 kernel: [    0.521124] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May  6 16:59:59 eyore2 kernel: [    0.521137] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  6 16:59:59 eyore2 kernel: [    0.521177] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
May  6 16:59:59 eyore2 kernel: [    0.521208] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
May  6 16:59:59 eyore2 kernel: [    0.521329] usb usb4: configuration #1 chosen from 1 choice
May  6 16:59:59 eyore2 kernel: [    0.521365] hub 4-0:1.0: USB hub found
May  6 16:59:59 eyore2 kernel: [    0.521379] hub 4-0:1.0: 2 ports detected
May  6 16:59:59 eyore2 kernel: [    0.521429] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  6 16:59:59 eyore2 kernel: [    0.521442] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  6 16:59:59 eyore2 kernel: [    0.521486] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
May  6 16:59:59 eyore2 kernel: [    0.521510] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
May  6 16:59:59 eyore2 kernel: [    0.521619] usb usb5: configuration #1 chosen from 1 choice
May  6 16:59:59 eyore2 kernel: [    0.521655] hub 5-0:1.0: USB hub found
May  6 16:59:59 eyore2 kernel: [    0.521666] hub 5-0:1.0: 2 ports detected
May  6 16:59:59 eyore2 kernel: [    0.521797] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
May  6 16:59:59 eyore2 kernel: [    0.528612] serio: i8042 KBD port at 0x60,0x64 irq 1
May  6 16:59:59 eyore2 kernel: [    0.528625] serio: i8042 AUX port at 0x60,0x64 irq 12
May  6 16:59:59 eyore2 kernel: [    0.528828] mice: PS/2 mouse device common for all mice
May  6 16:59:59 eyore2 kernel: [    0.528986] rtc_cmos 00:04: RTC can wake from S4
May  6 16:59:59 eyore2 kernel: [    0.529042] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  6 16:59:59 eyore2 kernel: [    0.529068] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May  6 16:59:59 eyore2 kernel: [    0.529237] device-mapper: uevent: version 1.0.3
May  6 16:59:59 eyore2 kernel: [    0.529378] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
May  6 16:59:59 eyore2 kernel: [    0.529442] device-mapper: multipath: version 1.1.0 loaded
May  6 16:59:59 eyore2 kernel: [    0.529446] device-mapper: multipath round-robin: version 1.0.0 loaded
May  6 16:59:59 eyore2 kernel: [    0.532462] EISA: Probing bus 0 at eisa.0
May  6 16:59:59 eyore2 kernel: [    0.532472] Cannot allocate resource for EISA slot 1
May  6 16:59:59 eyore2 kernel: [    0.532476] Cannot allocate resource for EISA slot 2
May  6 16:59:59 eyore2 kernel: [    0.532502] EISA: Detected 0 cards.
May  6 16:59:59 eyore2 kernel: [    0.532568] cpuidle: using governor ladder
May  6 16:59:59 eyore2 kernel: [    0.532571] cpuidle: using governor menu
May  6 16:59:59 eyore2 kernel: [    0.533180] TCP cubic registered
May  6 16:59:59 eyore2 kernel: [    0.533352] NET: Registered protocol family 10
May  6 16:59:59 eyore2 kernel: [    0.533953] lo: Disabled Privacy Extensions
May  6 16:59:59 eyore2 kernel: [    0.534393] NET: Registered protocol family 17
May  6 16:59:59 eyore2 kernel: [    0.534458] Using IPI No-Shortcut mode
May  6 16:59:59 eyore2 kernel: [    0.534602] registered taskstats version 1
May  6 16:59:59 eyore2 kernel: [    0.534806]   Magic number: 10:9:1003
May  6 16:59:59 eyore2 kernel: [    0.534855] vc vcs: hash matches
May  6 16:59:59 eyore2 kernel: [    0.534859] input input0: hash matches
May  6 16:59:59 eyore2 kernel: [    0.534866] pnp 00:05: hash matches
May  6 16:59:59 eyore2 kernel: [    0.534918] rtc_cmos 00:04: setting system clock to 2010-05-06 20:59:30 UTC (1273179570)
May  6 16:59:59 eyore2 kernel: [    0.534923] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  6 16:59:59 eyore2 kernel: [    0.534925] EDD information not available.
May  6 16:59:59 eyore2 kernel: [    0.607530] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May  6 16:59:59 eyore2 kernel: [    0.888806] ata1.00: ATA-6: WDC WD400BB-23JHA1, 06.01C06, max UDMA/100
May  6 16:59:59 eyore2 kernel: [    0.888812] ata1.00: 78156288 sectors, multi 16: LBA 
May  6 16:59:59 eyore2 kernel: [    0.888864] ata1.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
May  6 16:59:59 eyore2 kernel: [    0.894956] Freeing initrd memory: 7771k freed
May  6 16:59:59 eyore2 kernel: [    0.945120] ata1.00: configured for UDMA/100
May  6 16:59:59 eyore2 kernel: [    1.032442] isapnp: No Plug & Play device found
May  6 16:59:59 eyore2 kernel: [    1.032646] ata1.01: configured for UDMA/66
May  6 16:59:59 eyore2 kernel: [    1.033487] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-23JH 06.0 PQ: 0 ANSI: 5
May  6 16:59:59 eyore2 kernel: [    1.033719] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  6 16:59:59 eyore2 kernel: [    1.034803] sd 0:0:0:0: [sda] 78156288 512-byte logical blocks: (40.0 GB/37.2 GiB)
May  6 16:59:59 eyore2 kernel: [    1.034873] sd 0:0:0:0: [sda] Write Protect is off
May  6 16:59:59 eyore2 kernel: [    1.034914] scsi 0:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
May  6 16:59:59 eyore2 kernel: [    1.036213] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 16:59:59 eyore2 kernel: [    1.037527]  sda: sda1 sda2 < sda5 >
May  6 16:59:59 eyore2 kernel: [    1.079764] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  6 16:59:59 eyore2 kernel: [    1.079770] Uniform CD-ROM driver Revision: 3.20
May  6 16:59:59 eyore2 kernel: [    1.079928] sr 0:0:1:0: Attached scsi generic sg1 type 5
May  6 16:59:59 eyore2 kernel: [    1.080106] sd 0:0:0:0: [sda] Attached SCSI disk
May  6 16:59:59 eyore2 kernel: [    1.080123] Freeing unused kernel memory: 656k freed
May  6 16:59:59 eyore2 kernel: [    1.080694] Write protecting the kernel text: 4676k
May  6 16:59:59 eyore2 kernel: [    1.080727] Write protecting the kernel read-only data: 1840k
May  6 16:59:59 eyore2 kernel: [    1.107783] udev: starting version 151
May  6 16:59:59 eyore2 kernel: [    1.378516] Floppy drive(s): fd0 is 1.44M
May  6 16:59:59 eyore2 kernel: [    1.395805] FDC 0 is a post-1991 82077
May  6 16:59:59 eyore2 kernel: [    1.398385] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
May  6 16:59:59 eyore2 kernel: [    1.398390] Copyright (c) 1999-2006 Intel Corporation.
May  6 16:59:59 eyore2 kernel: [    1.398434] e1000 0000:03:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  6 16:59:59 eyore2 kernel: [    1.758068] e1000: 0000:03:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:79:28:54
May  6 16:59:59 eyore2 kernel: [    1.801743] EXT3-fs: INFO: recovery required on readonly filesystem.
May  6 16:59:59 eyore2 kernel: [    1.801748] EXT3-fs: write access will be enabled during recovery.
May  6 16:59:59 eyore2 kernel: [    2.026895] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
May  6 16:59:59 eyore2 kernel: [    7.024378] kjournald starting.  Commit interval 5 seconds
May  6 16:59:59 eyore2 kernel: [    7.024403] EXT3-fs: sda1: orphan cleanup on readonly fs
May  6 16:59:59 eyore2 kernel: [    7.024474] EXT3-fs: sda1: 2 orphan inodes deleted
May  6 16:59:59 eyore2 kernel: [    7.024478] EXT3-fs: recovery complete.
May  6 16:59:59 eyore2 kernel: [    7.059502] EXT3-fs: mounted filesystem with ordered data mode.
May  6 16:59:59 eyore2 kernel: [   28.601389] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
May  6 16:59:59 eyore2 kernel: [   28.736191] EXT3 FS on sda1, internal journal
May  6 16:59:59 eyore2 kernel: [   28.760785] udev: starting version 151
May  6 16:59:59 eyore2 kernel: [   29.251968] lp: driver loaded but no devices found
May  6 16:59:59 eyore2 kernel: [   29.350381] intel_rng: Firmware space is locked read-only. If you can't or
May  6 16:59:59 eyore2 kernel: [   29.350384] intel_rng: don't want to disable this in firmware setup, and if
May  6 16:59:59 eyore2 kernel: [   29.350386] intel_rng: you are certain that your system has a functional
May  6 16:59:59 eyore2 kernel: [   29.350388] intel_rng: RNG, try using the 'no_fwh_detect' option.
May  6 16:59:59 eyore2 kernel: [   29.350777] Linux agpgart interface v0.103
May  6 16:59:59 eyore2 kernel: [   29.369693] parport_pc 00:0e: reported by Plug and Play ACPI
May  6 16:59:59 eyore2 kernel: [   29.369753] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May  6 16:59:59 eyore2 kernel: [   29.379018] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  6 16:59:59 eyore2 kernel: [   29.465120] lp0: using parport0 (interrupt-driven).
May  6 16:59:59 eyore2 kernel: [   29.475107] ppdev: user-space parallel port driver
May  6 16:59:59 eyore2 kernel: [   29.476065] agpgart-intel 0000:00:00.0: Intel 865 Chipset
May  6 16:59:59 eyore2 kernel: [   29.476370] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
May  6 16:59:59 eyore2 kernel: [   29.498010] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
May  6 16:59:59 eyore2 kernel: [   29.757756] type=1505 audit(1273179599.721:2):  operation="profile_load" pid=513 name="/sbin/dhclient3"
May  6 16:59:59 eyore2 kernel: [   29.758496] type=1505 audit(1273179599.721:3):  operation="profile_load" pid=513 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  6 16:59:59 eyore2 kernel: [   29.758891] type=1505 audit(1273179599.721:4):  operation="profile_load" pid=513 name="/usr/lib/connman/scripts/dhclient-script"
May  6 16:59:59 eyore2 kernel: [   29.855403] type=1505 audit(1273179599.817:5):  operation="profile_load" pid=588 name="/usr/share/gdm/guest-session/Xsession"
May  6 16:59:59 eyore2 kernel: [   29.858100] type=1505 audit(1273179599.821:6):  operation="profile_replace" pid=589 name="/sbin/dhclient3"
May  6 16:59:59 eyore2 kernel: [   29.858857] type=1505 audit(1273179599.821:7):  operation="profile_replace" pid=589 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  6 16:59:59 eyore2 kernel: [   29.859265] type=1505 audit(1273179599.821:8):  operation="profile_replace" pid=589 name="/usr/lib/connman/scripts/dhclient-script"
May  6 16:59:59 eyore2 kernel: [   29.864568] type=1505 audit(1273179599.829:9):  operation="profile_load" pid=590 name="/usr/bin/evince"
May  6 16:59:59 eyore2 kernel: [   29.885202] type=1505 audit(1273179599.849:10):  operation="profile_load" pid=590 name="/usr/bin/evince-previewer"
May  6 16:59:59 eyore2 kernel: [   29.900074] type=1505 audit(1273179599.865:11):  operation="profile_load" pid=590 name="/usr/bin/evince-thumbnailer"
May  6 16:59:59 eyore2 kernel: [   29.981548] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
May  6 17:00:00 eyore2 kernel: [   30.204549] [drm] Initialized drm 1.1.0 20060810
May  6 17:00:00 eyore2 kernel: [   30.453059] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  6 17:00:00 eyore2 kernel: [   30.459521] [drm] set up 7M of stolen space
May  6 17:00:00 eyore2 kernel: [   30.504984] [drm] initialized overlay support
May  6 17:00:00 eyore2 kernel: [   30.732339] fb0: inteldrmfb frame buffer device
May  6 17:00:00 eyore2 kernel: [   30.732344] registered panic notifier
May  6 17:00:00 eyore2 kernel: [   30.732356] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
May  6 17:00:00 eyore2 kernel: [   30.769917] IBM machine detected. Enabling interrupts during APM calls.
May  6 17:00:00 eyore2 kernel: [   30.769924] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May  6 17:00:00 eyore2 kernel: [   30.769927] apm: overridden by ACPI.
May  6 17:00:00 eyore2 kernel: [   30.996800] vga16fb: mapped to 0xc00a0000
May  6 17:00:00 eyore2 kernel: [   30.996806] vga16fb: not registering due to another framebuffer present
May  6 17:00:01 eyore2 kernel: [   31.116416] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
May  6 17:00:01 eyore2 kernel: [   31.116592] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 17:00:01 eyore2 kernel: [   31.116821] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  6 17:00:01 eyore2 kernel: [   31.254984] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  6 17:00:01 eyore2 kernel: [   31.494690] Console: switching to colour frame buffer device 180x56
May  6 17:00:01 eyore2 kernel: [   31.688020] intel8x0_measure_ac97_clock: measured 54061 usecs (2605 samples)
May  6 17:00:01 eyore2 kernel: [   31.688025] intel8x0: clocking to 48000
May  6 17:00:21 eyore2 pulseaudio[1057]: ratelimit.c: 4 events suppressed
May  6 17:35:23 eyore2 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="507" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May  6 17:35:23 eyore2 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="507" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```

---

### Post by lidex on 2010-05-06
> **Eyore15 said:**
> Here's the results of those commands on my machine.  I think I've done something wrong with the "head -n" command as you can see the output isn't anything there except an error code,I hope this can help me overcome a real impediment to adopting Ubuntu.

thx

mcm

```
c Eeyore15@eyore2:~$ uname -a
Linux eyore2 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
eyore15@eyore2:~$ 


eyore15@eyore2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
eyore15@eyore2:~$ 


eyore15@eyore2:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
eyore15@eyore2:~$ 


eyore15@eyore2:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/prob/asound/card*/codec#*' for reading: No such file or directory
eyore15@eyore2:~$ 


```

Probably just AC97, which uses a different directory. Try this:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0
```

---

### Post by Eyore15 on 2010-05-06
> **lidex said:**
> Probably just AC97, which uses a different directory. Try this:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0
```

here's the result of that command:

```
eyore15@eyore2:~$ head -1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Analog Devices AD1981B
eyore15@eyore2:~$ 

```

---

### Post by lidex on 2010-05-06
I've modified the above command, see if it finds anything else. Some other threads have suggested the codec should actually be snd-intel8x0, not AD1981B.
```
head -1 /proc/asound/card0/codec97#*/ac97#*
```
Also show this output please:
```
lsmod | grep snd
```
Have a look here:
[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html]("https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html")
Try opening gnome-alsamixer and enabling everything in 'Edit>Sound Card Properties'

---

### Post by Eyore15 on 2010-05-07
> **lidex said:**
> I've modified the above command, see if it finds anything else. Some other threads have suggested the codec should actually be snd-intel8x0, not AD1981B.
```
head -1 /proc/asound/card0/codec97#*/ac97#*
```
Also show this output please:
```
lsmod | grep snd
```
Have a look here:
[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html]("https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html")
Try opening gnome-alsamixer and enabling everything in 'Edit>Sound Card Properties'

```
eyore15@eyore2:~$ head -1 /proc/asound/card0/codec97#*/ac97#*
==> /proc/asound/card0/codec97#0/ac97#0-0 <==
0-0/0: Analog Devices AD1981B

==> /proc/asound/card0/codec97#0/ac97#0-0+regs <==
0:00 = 0090
eyore15@eyore2:~$ 

```

```
eyore15@eyore2:~$ lsmod | grep snd
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
eyore15@eyore2:~$ 

```

---

### Post by Eyore15 on 2010-05-07
[QUOTE=
Try opening gnome-alsamixer and enabling everything in 'Edit>Sound Card Properties'[/QUOTE]

This did the trick.  I had been working with alsamixergui to try and resolve the issue myself.  Once I looked in gnome-alsamixer, I discovered that "master m" was muted. Fixed that, and the audio began working the way it should.

Thanks to all those that helped. Were that I was as smart.  I wish I understood the output of the commands I ran.

tnx again

mcm

---

