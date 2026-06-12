---
title: "Desperate to get Video Import working in 1104"
date: 2011-06-01
forum: Multimedia Software
---

### Post by wacky.banana on 2011-06-01
Hello,

I have been trying to get video import to work on Xubuntu 1104 for nearly 2 weeks without success. All I am trying to do is to drag video from my Sony Digital 8 Handycam via firewire onto my PC for safekeeping and editing.

Things I have done so far to help solve the problem:

- Installed Kino, then found it did not work because of a permissions error.
- Used gksudo to get around that then found it was giving me a firewire error..raw 1394 kernel not loaded or failure to...
- Did a load of research and de-blacklisted the  ohci drivers. Also installed dvgrab to make sure this aspect worked ok
- Used the list command to determine that the PC could see the firewire card, all OK
- Went back, using gksudo, etc to drag the video files in, same error as before
- Went onto the Kino website here...[http://www.kinodv.org/](http://www.kinodv.org/) (seems not to be updated that much) and , again, de blacklisted the firewire drivers
- Went to the Ubuntu website and found this...[https://help.ubuntu.com/community/Firewire...but](https://help.ubuntu.com/community/Firewire...but) none of that worked for me.
- Searched through the Ubuntu help forums, not yet found a solution that works for me.
- Installed Ubuntu studio to see if that worked, no joy.

I am now at a complete dead end. I am simply trying to find a piece of software that plugs in, works first time without issues, and allows me to initiate video imports as outlined above. Is anyone able to help me resolve this problem please?

My only other option, if I can't solve this, would be to install a copy of Windows 7 on my machine and use e.g a Pinnacle product to solve the problem. That would be a major failure as I much prefer to do this using my current set-up.

Appreciate any help that anyone can give here.

Kind regards,

WB

---

### Post by Toz on 2011-06-01
> **wacky.banana said:**
> - Installed Kino, then found it did not work because of a permissions error.Open a terminal window and type in```
ls -l /dev | grep raw
```and post back the results. You should have a raw1394 device file. Who is the group owner? You will need to be a member of that group.
> - Used gksudo to get around that then found it was giving me a firewire error..raw 1394 kernel not loaded or failure to...Can you post back the exact error message you are getting. Also run the following command in the terminal window and post back the results:```
lsmod | grep 1394
```
> - Went to the Ubuntu website and found this...[https://help.ubuntu.com/community/Firewire...but](https://help.ubuntu.com/community/Firewire...but) none of that worked for me.That link points to a non-existant page. Have a look at: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) (steps 4 & 5 only for Natty) and [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and [https://help.ubuntu.com/community/FirewireNatty](https://help.ubuntu.com/community/FirewireNatty). Can you let us know, as you go through those steps, what exactly doesn't work?
> - Searched through the Ubuntu help forums, not yet found a solution that works for me.Have you had a read of this post? [http://ubuntuforums.org/showthread.php?t=1093119](http://ubuntuforums.org/showthread.php?t=1093119) (specifically posts #8 & #9)

I don't own a device like this so I can't offer specific solutions based on experience, but I might be able to help troubleshoot.

---

### Post by wacky.banana on 2011-06-01
Toz,

Really really grateful for the help; appreciate it. I forgot to mention that I had created a group called firewire and added myself to it. Just double checked and I have permissions in the audio and video groups.I also made sure that in properties, I had access to audio and video devices. 

I am running through your suggestions now and will update this post again in a minute.

WB

Results as follows:
1)  ls - l /dev |grep raw gives this:

*crw-------  1 root root    250,   0 2011-06-01 15:33 hidraw0*

No 1394 raw device listed (strange)

2)  lsmod | grep 1394
gives this: no results at all, nothing listed

3) Running Kino from the terminal using gksudo gives this error message in the terminal window:

*"Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory"*
 
From within Kino itself, when I go to capture a video it says "waiting for DV (press play on camera)". This is a different error message to the one I was getting yesterday

4)  ls -al /dev/raw1394 gives:
[I]cannot access /dev/raw1394: No such file or directory

5) [/I]groups gives:[I]

dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare firewire

6) [/I]Viewed this file  - /lib/udev/rules.d/60-ffado.rules  

*No firewire devices listed*. I am unsure whether its because firewire is not loaded or my card is not supported

7) Installed everything off this list except gtk 2.6 (could not find it) .....[http://ubuntuforums.org/showpost.php?p=6879741&postcount=8](http://ubuntuforums.org/showpost.php?p=6879741&postcount=8)

8 ) Rebooted, ran Kino under sudo, gives error message (truncated) "Warning: raw1394 kernel module not loaded or failure to read/write/..." . If I look at the output from the terminal window I see this...Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


So where do I go from here please?

Many thanks

WB

---

### Post by Toz on 2011-06-01
Post back results of ```
dmesg
```Is your card getting recognized? And what kind of card is it? 

Second thing, with the terminal window open and the camera not connected, type in:```
tail -f /var/log/syslog
```Plug in the camera and post back whether anything displays in the terminal window. And then also post back results of:```
dmesg | tail -30 
```

---

### Post by wacky.banana on 2011-06-01
Toz,

I will respond in stages. Results of the query dmesg are as follows:

```
 [    0.000000] Initializing cgroup subsys cpuset

[LIST]
[*] [    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: To Be Filled By O.E.M. 775Dual-VSTA/775Dual-VSTA, BIOS P3.10 02/26/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677e000 - 373b7000
[    0.000000] ACPI: RSDP 000f7e20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00034 (v01 A M I  OEMRSDT  02000826 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v02 A M I  OEMFACP  02000826 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb0450 04AED (v01  75D8U 75D8U302 00000302 INTL 02002026)
[    0.000000] ACPI: FACS 7ffc0000 00040
[    0.000000] ACPI: APIC 7ffb0390 00078 (v01 A M I  OEMAPIC  02000826 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 A M I  OEMMCFG  02000826 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffc0040 00051 (v01 A M I  AMI_OEM  02000826 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f577e200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
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
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=9bd7725a-ccf4-44dd-982e-52db7a7e333a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2046820k/2096832k available (5188k kernel code, 49560k reserved, 2540k data, 700k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:1024 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2209.902 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4419.80 BogoMIPS (lpj=8839608)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004033] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004055] Yama: becoming mindful.
[    0.004115] Mount-cache hash table entries: 512
[    0.004263] Initializing cgroup subsys ns
[    0.004267] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004271] Initializing cgroup subsys cpuacct
[    0.004276] Initializing cgroup subsys memory
[    0.004284] Initializing cgroup subsys devices
[    0.004287] Initializing cgroup subsys freezer
[    0.004289] Initializing cgroup subsys net_cls
[    0.004291] Initializing cgroup subsys blkio
[    0.004328] CPU: Physical Processor ID: 0
[    0.004330] CPU: Processor Core ID: 0
[    0.004333] mce: CPU supports 6 MCE banks
[    0.004342] CPU0: Thermal monitoring enabled (TM1)
[    0.004347] using mwait in idle threads.
[    0.006704] ACPI: Core revision 20110112
[    0.010827] ftrace: allocating 23640 entries in 47 pages
[    0.012064] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.012538] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.053242] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
[    0.056003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.056003] PEBS disabled due to CPU errata.
[    0.056003] ... version:                2
[    0.056003] ... bit width:              40
[    0.056003] ... generic registers:      2
[    0.056003] ... value mask:             000000ffffffffff
[    0.056003] ... max period:             000000007fffffff
[    0.056003] ... fixed-purpose events:   3
[    0.056003] ... event mask:             0000000700000003
[    0.056003] CPU 1 irqstacks, hard=f40b2000 soft=f40b4000
[    0.056003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.144026] Brought up 2 CPUs
[    0.144029] Total of 2 processors activated (8839.83 BogoMIPS).
[    0.144435] devtmpfs: initialized
[    0.145171] print_constraints: dummy: 
[    0.145212] Time: 18:48:37  Date: 06/01/11
[    0.145252] NET: Registered protocol family 16
[    0.145291] Trying to unpack rootfs image as initramfs...
[    0.145388] EISA bus registered
[    0.145398] ACPI: bus type pci registered
[    0.145480] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.145483] PCI: not using MMCONFIG
[    0.145575] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
[    0.145577] PCI: Using configuration type 1 for base access
[    0.160225] bio: create slab <bio-0> at 0
[    0.161408] ACPI: EC: Look up EC in DSDT
[    0.162881] ACPI: Executed 1 blocks of module-level executable AML code
[    0.165929] ACPI: Interpreter enabled
[    0.165938] ACPI: (supports S0 S1 S3 S4 S5)
[    0.165964] ACPI: Using IOAPIC for interrupt routing
[    0.165995] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.167286] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.167289] PCI: Using MMCONFIG for extended config space
[    0.173970] ACPI: No dock devices found.
[    0.173975] HEST: Table not found.
[    0.173979] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.174180] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7f])
[    0.174391] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.174395] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.174397] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.174400] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.174403] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfff7ffff]
[    0.174427] pci 0000:00:00.0: [1106:0308] type 0 class 0x000600
[    0.174442] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.174526] pci 0000:00:00.1: [1106:1308] type 0 class 0x000600
[    0.174589] pci 0000:00:00.2: [1106:2308] type 0 class 0x000600
[    0.174655] pci 0000:00:00.3: [1106:3208] type 0 class 0x000600
[    0.174720] pci 0000:00:00.4: [1106:4308] type 0 class 0x000600
[    0.174782] pci 0000:00:00.5: [1106:5308] type 0 class 0x000800
[    0.174875] pci 0000:00:00.7: [1106:7308] type 0 class 0x000600
[    0.174940] pci 0000:00:01.0: [1106:b198] type 1 class 0x000604
[    0.174995] pci 0000:00:01.0: supports D1
[    0.175014] pci 0000:00:02.0: [1106:a208] type 1 class 0x000604
[    0.175093] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.175099] pci 0000:00:02.0: PME# disabled
[    0.175136] pci 0000:00:09.0: [10ec:8169] type 0 class 0x000200
[    0.175157] pci 0000:00:09.0: reg 10: [io  0xc800-0xc8ff]
[    0.175169] pci 0000:00:09.0: reg 14: [mem 0xf7ffe800-0xf7ffe8ff]
[    0.175219] pci 0000:00:09.0: reg 30: [mem 0xf7fc0000-0xf7fdffff pref]
[    0.175242] pci 0000:00:09.0: supports D1 D2
[    0.175244] pci 0000:00:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.175249] pci 0000:00:09.0: PME# disabled
[    0.175268] pci 0000:00:0a.0: [14db:2120] type 0 class 0x000701
[    0.175288] pci 0000:00:0a.0: reg 10: [io  0xd400-0xd407]
[    0.175300] pci 0000:00:0a.0: reg 14: [io  0xcc00-0xcc03]
[    0.175389] pci 0000:00:0b.0: [1033:0035] type 0 class 0x000c03
[    0.175410] pci 0000:00:0b.0: reg 10: [mem 0xf7ffc000-0xf7ffcfff]
[    0.175487] pci 0000:00:0b.0: supports D1 D2
[    0.175489] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.175494] pci 0000:00:0b.0: PME# disabled
[    0.175514] pci 0000:00:0b.1: [1033:0035] type 0 class 0x000c03
[    0.175534] pci 0000:00:0b.1: reg 10: [mem 0xf7ffd000-0xf7ffdfff]
[    0.175611] pci 0000:00:0b.1: supports D1 D2
[    0.175613] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.175618] pci 0000:00:0b.1: PME# disabled
[    0.175637] pci 0000:00:0b.2: [1033:00e0] type 0 class 0x000c03
[    0.175658] pci 0000:00:0b.2: reg 10: [mem 0xf7ffec00-0xf7ffecff]
[    0.175739] pci 0000:00:0b.2: supports D1 D2
[    0.175741] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.175746] pci 0000:00:0b.2: PME# disabled
[    0.175776] pci 0000:00:0c.0: [104c:8019] type 0 class 0x000c00
[    0.175798] pci 0000:00:0c.0: reg 10: [mem 0xf7fff000-0xf7fff7ff]
[    0.175810] pci 0000:00:0c.0: reg 14: [mem 0xf7ff8000-0xf7ffbfff]
[    0.175884] pci 0000:00:0c.0: supports D2
[    0.175886] pci 0000:00:0c.0: PME# supported from D2 D3hot
[    0.175891] pci 0000:00:0c.0: PME# disabled
[    0.175914] pci 0000:00:0f.0: [1106:0591] type 0 class 0x000101
[    0.175938] pci 0000:00:0f.0: reg 10: [io  0xe000-0xe007]
[    0.175951] pci 0000:00:0f.0: reg 14: [io  0xdc00-0xdc03]
[    0.175963] pci 0000:00:0f.0: reg 18: [io  0xd880-0xd887]
[    0.175975] pci 0000:00:0f.0: reg 1c: [io  0xd800-0xd803]
[    0.175987] pci 0000:00:0f.0: reg 20: [io  0xd480-0xd48f]
[    0.175999] pci 0000:00:0f.0: reg 24: [io  0xd000-0xd0ff]
[    0.176065] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.176125] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.176196] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.176254] pci 0000:00:10.0: reg 20: [io  0xe080-0xe09f]
[    0.176295] pci 0000:00:10.0: supports D1 D2
[    0.176297] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176302] pci 0000:00:10.0: PME# disabled
[    0.176322] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.176380] pci 0000:00:10.1: reg 20: [io  0xe400-0xe41f]
[    0.176424] pci 0000:00:10.1: supports D1 D2
[    0.176426] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176431] pci 0000:00:10.1: PME# disabled
[    0.176451] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.176509] pci 0000:00:10.2: reg 20: [io  0xe480-0xe49f]
[    0.176549] pci 0000:00:10.2: supports D1 D2
[    0.176551] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176556] pci 0000:00:10.2: PME# disabled
[    0.176576] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.176633] pci 0000:00:10.3: reg 20: [io  0xec00-0xec1f]
[    0.176674] pci 0000:00:10.3: supports D1 D2
[    0.176676] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176681] pci 0000:00:10.3: PME# disabled
[    0.176701] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.176723] pci 0000:00:10.4: reg 10: [mem 0xf7fff800-0xf7fff8ff]
[    0.176802] pci 0000:00:10.4: supports D1 D2
[    0.176804] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176809] pci 0000:00:10.4: PME# disabled
[    0.176834] pci 0000:00:11.0: [1106:3337] type 0 class 0x000601
[    0.176963] pci 0000:00:11.7: [1106:287e] type 0 class 0x000600
[    0.177037] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
[    0.177057] pci 0000:00:12.0: reg 10: [io  0xe800-0xe8ff]
[    0.177069] pci 0000:00:12.0: reg 14: [mem 0xf7fffc00-0xf7fffcff]
[    0.177144] pci 0000:00:12.0: supports D1 D2
[    0.177146] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177151] pci 0000:00:12.0: PME# disabled
[    0.177170] pci 0000:00:13.0: [1106:337b] type 0 class 0x000600
[    0.177309] pci 0000:01:00.0: [10de:02e2] type 0 class 0x000300
[    0.177331] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.177344] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff pref]
[    0.177356] pci 0000:01:00.0: reg 18: [mem 0xf5000000-0xf5ffffff]
[    0.177397] pci 0000:01:00.0: reg 30: [mem 0xf7ce0000-0xf7cfffff pref]
[    0.177473] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.177478] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.177483] pci 0000:00:01.0:   bridge window [mem 0xf3c00000-0xf7cfffff]
[    0.177488] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff pref]
[    0.177541] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.177546] pci 0000:00:02.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.177551] pci 0000:00:02.0:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.177557] pci 0000:00:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.177574] pci_bus 0000:00: on NUMA node 0
[    0.177580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.177876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.177977] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.178121]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.178300]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.188862] ACPI: PCI Root Bridge [PCI1] (domain 0000 [bus 80-ff])
[    0.188992] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.188995] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.188998] pci_root PNP0A08:00: host bridge window [mem 0xf7efc000-0xf7efffff]
[    0.189026] pci 0000:80:01.0: [1106:3288] type 0 class 0x000403
[    0.189053] pci 0000:80:01.0: reg 10: [mem 0xf7efc000-0xf7efffff 64bit]
[    0.189128] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.189133] pci 0000:80:01.0: PME# disabled
[    0.189192] pci_bus 0000:80: on NUMA node 0
[    0.189196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.189229]  pci0000:80: Requesting ACPI _OSC control (0x1d)
[    0.189342] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.189397] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.189453] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.189505] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.189556] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.189609] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.189661] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.189715] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.189847] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.189850] vgaarb: loaded
[    0.190083] SCSI subsystem initialized
[    0.190163] libata version 3.00 loaded.
[    0.190218] usbcore: registered new interface driver usbfs
[    0.190231] usbcore: registered new interface driver hub
[    0.190261] usbcore: registered new device driver usb
[    0.190396] wmi: Mapper loaded
[    0.190399] PCI: Using ACPI for IRQ routing
[    0.195696] PCI: pci_cache_line_size set to 64 bytes
[    0.195840] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.195843] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.195846] reserve RAM buffer: 000000007ffb0000 - 000000007fffffff 
[    0.195991] NetLabel: Initializing
[    0.195994] NetLabel:  domain hash size = 128
[    0.195996] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.196018] NetLabel:  unlabeled traffic allowed by default
[    0.204769] AppArmor: AppArmor Filesystem Enabled
[    0.204829] pnp: PnP ACPI init
[    0.204859] ACPI: bus type pnp registered
[    0.204999] pnp 00:00: [bus 00-7f]
[    0.205002] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.205005] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.205007] pnp 00:00: [io  0x0d00-0xffff window]
[    0.205010] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.205012] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.205015] pnp 00:00: [mem 0x80000000-0xfff7ffff window]
[    0.205094] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.205137] pnp 00:01: [dma 4]
[    0.205139] pnp 00:01: [io  0x0000-0x000f]
[    0.205141] pnp 00:01: [io  0x0081-0x0083]
[    0.205143] pnp 00:01: [io  0x0087]
[    0.205145] pnp 00:01: [io  0x0089-0x008b]
[    0.205147] pnp 00:01: [io  0x008f]
[    0.205149] pnp 00:01: [io  0x00c0-0x00df]
[    0.205189] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.205220] pnp 00:02: [io  0x0070-0x0071]
[    0.205234] pnp 00:02: [irq 8]
[    0.205269] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.205279] pnp 00:03: [io  0x0061]
[    0.205313] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.205327] pnp 00:04: [io  0x00f0-0x00ff]
[    0.205332] pnp 00:04: [irq 13]
[    0.205367] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.205810] pnp 00:05: [io  0x03f0-0x03f5]
[    0.205812] pnp 00:05: [io  0x03f7]
[    0.205818] pnp 00:05: [irq 6]
[    0.205820] pnp 00:05: [dma 2]
[    0.205889] pnp 00:05: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.206203] pnp 00:06: [io  0x0378-0x037f]
[    0.206206] pnp 00:06: [io  0x0778-0x077b]
[    0.206211] pnp 00:06: [irq 7]
[    0.206213] pnp 00:06: [dma 3]
[    0.206385] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.206759] pnp 00:07: [io  0x0010-0x001f]
[    0.206761] pnp 00:07: [io  0x0022-0x003f]
[    0.206764] pnp 00:07: [io  0x0044-0x005f]
[    0.206766] pnp 00:07: [io  0x0062-0x0063]
[    0.206768] pnp 00:07: [io  0x0065-0x006f]
[    0.206770] pnp 00:07: [io  0x0072-0x007f]
[    0.206772] pnp 00:07: [io  0x0080]
[    0.206774] pnp 00:07: [io  0x0084-0x0086]
[    0.206776] pnp 00:07: [io  0x0088]
[    0.206778] pnp 00:07: [io  0x008c-0x008e]
[    0.206780] pnp 00:07: [io  0x0090-0x009f]
[    0.206782] pnp 00:07: [io  0x00a2-0x00bf]
[    0.206784] pnp 00:07: [io  0x00e0-0x00ef]
[    0.206786] pnp 00:07: [io  0x0295-0x0296]
[    0.206788] pnp 00:07: [io  0x03e0-0x03e7]
[    0.206791] pnp 00:07: [mem 0xf7efc000-0xf7efffff]
[    0.206793] pnp 00:07: [mem 0xffb80000-0xffbfffff]
[    0.206796] pnp 00:07: [io  0x04d0-0x04d1]
[    0.206798] pnp 00:07: [io  0x0800-0x087f]
[    0.206800] pnp 00:07: [io  0x0400-0x041f]
[    0.206802] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    0.206905] system 00:07: [io  0x0295-0x0296] has been reserved
[    0.206908] system 00:07: [io  0x03e0-0x03e7] has been reserved
[    0.206911] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.206914] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.206917] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.206920] system 00:07: [mem 0xf7efc000-0xf7efffff] has been reserved
[    0.206924] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.206927] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.206997] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.207000] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.207064] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.207068] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.207071] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207104] pnp 00:09: [io  0x0060]
[    0.207106] pnp 00:09: [io  0x0064]
[    0.207113] pnp 00:09: [irq 1]
[    0.207152] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.207445] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.207451] pnp 00:0a: [irq 4]
[    0.207453] pnp 00:0a: [dma 0 disabled]
[    0.207531] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.207568] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.207635] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.207639] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207822] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.207825] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.207827] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.207829] pnp 00:0c: [mem 0x00100000-0x7fffffff]
[    0.207832] pnp 00:0c: [mem 0xfff80000-0xffffffff]
[    0.207907] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.207911] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.207914] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.207917] system 00:0c: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.207920] system 00:0c: [mem 0xfff80000-0xffffffff] has been reserved
[    0.207923] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.207993] pnp 00:0d: [bus 80-ff]
[    0.207996] pnp 00:0d: [io  0x0cf8-0x0cff]
[    0.207998] pnp 00:0d: [io  0x0000-0x0cf7 window]
[    0.208001] pnp 00:0d: [io  0x0d00-0xffff window]
[    0.208003] pnp 00:0d: [mem 0xf7efc000-0xf7efffff window]
[    0.208073] pnp 00:0d: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.208228] pnp: PnP ACPI: found 14 devices
[    0.208230] ACPI: ACPI bus type pnp unregistered
[    0.208234] PnPBIOS: Disabled by ACPI PNP
[    0.244765] Switching to clocksource acpi_pm
[    0.245136] pci 0000:00:02.0: BAR 15: assigned [mem 0x80000000-0x801fffff pref]
[    0.245140] pci 0000:00:02.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.245143] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.245145] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.245152] pci 0000:00:01.0:   bridge window [mem 0xf3c00000-0xf7cfffff]
[    0.245157] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff pref]
[    0.245164] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.245167] pci 0000:00:02.0:   bridge window [io  0x1000-0x1fff]
[    0.245174] pci 0000:00:02.0:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.245179] pci 0000:00:02.0:   bridge window [mem 0x80000000-0x801fffff pref]
[    0.245199] pci 0000:00:01.0: setting latency timer to 64
[    0.245207] pci 0000:00:02.0: enabling device (0106 -> 0107)
[    0.245227] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.245232] pci 0000:00:02.0: setting latency timer to 64
[    0.245237] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.245239] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.245242] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.245244] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.245247] pci_bus 0000:00: resource 8 [mem 0x80000000-0xfff7ffff]
[    0.245249] pci_bus 0000:01: resource 1 [mem 0xf3c00000-0xf7cfffff]
[    0.245252] pci_bus 0000:01: resource 2 [mem 0xbff00000-0xdfefffff pref]
[    0.245255] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.245257] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.245260] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff pref]
[    0.245262] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    0.245265] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    0.245267] pci_bus 0000:80: resource 6 [mem 0xf7efc000-0xf7efffff]
[    0.245318] NET: Registered protocol family 2
[    0.245404] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.245687] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.246222] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.246582] TCP: Hash tables configured (established 131072 bind 65536)
[    0.246587] TCP reno registered
[    0.246590] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.246604] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.246745] NET: Registered protocol family 1
[    0.246786] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.246955] pci 0000:01:00.0: Boot video device
[    0.246962] PCI: CLS 32 bytes, default 64
[    0.247282] cpufreq-nforce2: No nForce2 chipset.
[    0.247438] audit: initializing netlink socket (disabled)
[    0.247451] type=2000 audit(1306954116.244:1): initialized
[    0.247085] Switched to NOHz mode on CPU #0
[    0.247451] Switched to NOHz mode on CPU #1
[    0.255799] highmem bounce pool size: 64 pages
[    0.255805] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.257796] VFS: Disk quotas dquot_6.5.2
[    0.257870] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.258607] fuse init (API version 7.16)
[    0.258708] msgmni has been set to 1678
[    0.258995] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.259030] io scheduler noop registered
[    0.259032] io scheduler deadline registered
[    0.259052] io scheduler cfq registered (default)
[    0.259230] pcieport 0000:00:02.0: setting latency timer to 64
[    0.259307] pcieport 0000:00:02.0: irq 64 for MSI/MSI-X
[    0.259491] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.259511] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.259516] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.259538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.259586] pciehp 0000:00:02.0:pcie04: HPC vendor_id 1106 device_id a208 ss_vid 0 ss_did 0
[    0.259609] pciehp 0000:00:02.0:pcie04: service driver pciehp loaded
[    0.259617] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.259696] intel_idle: MWAIT substates: 0x220
[    0.259698] intel_idle: does not run on family 6 model 15
[    0.259813] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.259820] ACPI: Power Button [PWRB]
[    0.259876] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.259879] ACPI: Power Button [PWRF]
[    0.260137] ACPI: acpi_idle registered with cpuidle
[    0.262430] ERST: Table is not found!
[    0.262579] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.272213] isapnp: Scanning for PnP cards...
[    0.282966] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.436110] Freeing initrd memory: 12516k freed
[    0.626219] isapnp: No Plug & Play device found
[    0.656875] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.657188] Linux agpgart interface v0.103
[    0.657280] agpgart: Detected VIA PT880 Ultra chipset
[    0.660049] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.661414] brd: module loaded
[    0.662057] loop: module loaded
[    0.662161] i2c-core: driver [adp5520] using legacy suspend method
[    0.662163] i2c-core: driver [adp5520] using legacy resume method
[    0.662333] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.662372] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.662768] Fixed MDIO Bus: probed
[    0.662809] PPP generic driver version 2.4.2
[    0.662856] tun: Universal TUN/TAP device driver, 1.6
[    0.662858] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.662951] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.662974] ehci_hcd 0000:00:0b.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.662993] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[    0.663040] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 1
[    0.684035] ehci_hcd 0000:00:0b.2: irq 17, io mem 0xf7ffec00
[    0.696014] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00
[    0.696147] hub 1-0:1.0: USB hub found
[    0.696152] hub 1-0:1.0: 5 ports detected
[    0.696239] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.696251] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.696292] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 2
[    0.700069] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf7fff800
[    0.712016] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.712136] hub 2-0:1.0: USB hub found
[    0.712140] hub 2-0:1.0: 8 ports detected
[    0.712231] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.712254] ohci_hcd 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.712268] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.712309] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 3
[    0.716042] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xf7ffc000
[    0.801908] hub 3-0:1.0: USB hub found
[    0.801914] hub 3-0:1.0: 3 ports detected
[    0.802000] ohci_hcd 0000:00:0b.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.802012] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[    0.802060] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[    0.802101] ohci_hcd 0000:00:0b.1: irq 16, io mem 0xf7ffd000
[    0.885892] hub 4-0:1.0: USB hub found
[    0.885897] hub 4-0:1.0: 2 ports detected
[    0.885976] uhci_hcd: USB Universal Host Controller Interface driver
[    0.886021] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.886029] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.886071] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[    0.886125] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e080
[    0.886256] hub 5-0:1.0: USB hub found
[    0.886261] hub 5-0:1.0: 2 ports detected
[    0.886346] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.886353] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.886395] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[    0.886445] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000e400
[    0.886573] hub 6-0:1.0: USB hub found
[    0.886581] hub 6-0:1.0: 2 ports detected
[    0.886658] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.886665] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.886713] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 7
[    0.886752] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e480
[    0.886886] hub 7-0:1.0: USB hub found
[    0.886890] hub 7-0:1.0: 2 ports detected
[    0.886974] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.886981] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.887021] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 8
[    0.887069] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000ec00
[    0.887193] hub 8-0:1.0: USB hub found
[    0.887197] hub 8-0:1.0: 2 ports detected
[    0.887362] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.887364] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.887549] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.887638] mousedev: PS/2 mouse device common for all mice
[    0.887763] rtc_cmos 00:02: RTC can wake from S4
[    0.887870] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.887904] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.887999] device-mapper: uevent: version 1.0.3
[    0.888102] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.888187] device-mapper: multipath: version 1.2.0 loaded
[    0.888190] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.888271] EISA: Probing bus 0 at eisa.0
[    0.888274] EISA: Cannot allocate resource for mainboard
[    0.888275] Cannot allocate resource for EISA slot 1
[    0.888277] Cannot allocate resource for EISA slot 2
[    0.888279] Cannot allocate resource for EISA slot 3
[    0.888281] Cannot allocate resource for EISA slot 4
[    0.888283] Cannot allocate resource for EISA slot 5
[    0.888285] Cannot allocate resource for EISA slot 6
[    0.888287] Cannot allocate resource for EISA slot 7
[    0.888288] Cannot allocate resource for EISA slot 8
[    0.888290] EISA: Detected 0 cards.
[    0.888355] cpuidle: using governor ladder
[    0.888358] cpuidle: using governor menu
[    0.888669] TCP cubic registered
[    0.888805] NET: Registered protocol family 10
[    0.889445] NET: Registered protocol family 17
[    0.889466] Registering the dns_resolver key type
[    0.889517] Using IPI No-Shortcut mode
[    0.889627] PM: Hibernation image not present or could not be loaded.
[    0.889641] registered taskstats version 1
[    0.889984]   Magic number: 15:769:846
[    0.890085] rtc_cmos 00:02: setting system clock to 2011-06-01 18:48:37 UTC (1306954117)
[    0.890089] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.890090] EDD information not available.
[    0.890183] Freeing unused kernel memory: 700k freed
[    0.890443] Write protecting the kernel text: 5192k
[    0.890491] Write protecting the kernel read-only data: 2148k
[    0.907175] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.916178] <30>udev[64]: starting version 167
[    1.023716] Floppy drive(s): fd0 is 1.44M
[    1.044733] sata_via 0000:00:0f.0: version 2.6
[    1.044752] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.044789] sata_via 0000:00:0f.0: routed to hard irq line 5
[    1.050396] via-rhine.c:v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.055660] scsi0 : sata_via
[    1.056322] FDC 0 is a post-1991 82077
[    1.057370] scsi1 : sata_via
[    1.059100] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd480 irq 21
[    1.059104] ata2: SATA max UDMA/133 cmd 0xd880 ctl 0xd800 bmdma 0xd488 irq 21
[    1.061962] firewire_ohci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.116083] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0x2
[    1.116125] pata_via 0000:00:0f.1: version 0.3.4
[    1.116621] scsi2 : pata_via
[    1.116713] scsi3 : pata_via
[    1.118580] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.118584] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.118623] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.119255] eth0: VIA Rhine II at 0xf7fffc00, 00:13:8f:db:33:1d, IRQ 23.
[    1.119962] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    1.119993] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.120025] r8169 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.120049] r8169 0000:00:09.0: (unregistered net_device): no PCI Express capability
[    1.120651] r8169 0000:00:09.0: eth1: RTL8169sb/8110sb at 0xf8026800, 00:27:19:f1:db:f6, XID 10000000 IRQ 17
[    1.196018] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    1.252018] Refined TSC clocksource calibration: 2209.897 MHz.
[    1.252022] Switching to clocksource tsc
[    1.260010] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.280570] ata3.00: ATA-7: Hitachi HDT725032VLAT80, V54OA42A, max UDMA/133
[    1.280573] ata3.00: 625142448 sectors, multi 16: LBA48 
[    1.296420] ata3.00: configured for UDMA/133
[    1.424326] ata1.00: ATA-7: SAMSUNG HD642JJ, 1AA01112, max UDMA7
[    1.424331] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.432315] ata1.00: configured for UDMA/133
[    1.432441] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD642JJ  1AA0 PQ: 0 ANSI: 5
[    1.432653] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.432659] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.432704] sd 0:0:0:0: [sda] Write Protect is off
[    1.432707] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.432731] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.444579]  sda: sda1 sda2 < sda5 sda6 > sda4
[    1.444954] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.616100] firewire_core: created device fw0: GUID 005042e101908402, S400
[    1.636012] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.800212] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100
[    1.816211] ata2.00: configured for UDMA/100
[    1.817371] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    1.820281] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.820284] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.820436] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.820527] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.820682] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[    1.820813] sd 2:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.820848] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.820867] sd 2:0:0:0: [sdb] Write Protect is off
[    1.820870] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.820893] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.830675]  sdb: sdb1
[    1.830920] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.003826] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:10.0/usb5/5-2/5-2:1.0/input/input3
[    2.003969] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.0-2/input0
[    2.003991] usbcore: registered new interface driver usbhid
[    2.003993] usbhid: USB HID core driver
[    2.306555] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    6.858727] Adding 1951740k swap on /dev/sda5.  Priority:-1 extents:1 across:1951740k 
[    6.879119] <30>udev[296]: starting version 167
[    6.922016] lp: driver loaded but no devices found
[    6.953434] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.007909] parport_pc 00:06: reported by Plug and Play ACPI
[    7.008051] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    7.030089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.112251] type=1400 audit(1306950523.718:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
[    7.113121] type=1400 audit(1306950523.718:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 comm="apparmor_parser"
[    7.113667] type=1400 audit(1306950523.718:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="apparmor_parser"
[    7.148199] lp0: using parport0 (interrupt-driven).
[    7.148470] parport_pc 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.148475] PCI parallel port detected: 14db:2120, I/O at 0xd400(0xcc00), IRQ 18
[    7.148511] parport1: PC-style at 0xd400 (0xcc00), irq 18, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[    7.246531] lp1: using parport1 (interrupt-driven).
[    7.290629] r8169 0000:00:09.0: eth1: link down
[    7.293524] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.298437] eth0: link down
[    7.299378] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.352847] nvidia: module license 'NVIDIA' taints kernel.
[    7.352852] Disabling lock debugging due to kernel taint
[    7.676407] ppdev: user-space parallel port driver
[    7.764094] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.764099] hda_intel: msi for device 1849:0888 set to 0
[    7.764101] hda_intel: position_fix set to 1 for device 1849:0888
[    7.764131] HDA Intel 0000:80:01.0: setting latency timer to 64
[    7.764135] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[    8.002673] type=1400 audit(1306950524.606:5): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=707 comm="apparmor_parser"
[    8.005615] type=1400 audit(1306950524.610:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
[    8.006501] type=1400 audit(1306950524.610:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[    8.007052] type=1400 audit(1306950524.610:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[    8.023877] type=1400 audit(1306950524.626:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=707 comm="apparmor_parser"
[    8.024895] type=1400 audit(1306950524.630:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=709 comm="apparmor_parser"
[    8.025918] type=1400 audit(1306950524.630:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=709 comm="apparmor_parser"
[    8.099919] hda_codec: ALC888: BIOS auto-probing.
[    8.449335] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.449347] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.449488] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[    9.283334] vesafb: framebuffer at 0xc0000000, mapped to 0xf8380000, using 3072k, total 3072k
[    9.283339] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    9.283341] vesafb: scrolling: redraw
[    9.283344] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    9.283542] Console: switching to colour frame buffer device 128x48
[    9.283566] fb0: VESA VGA frame buffer device
[    9.776204] r8169 0000:00:09.0: eth1: link up
[    9.776363] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   10.469586] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   10.469612] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   10.469758] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   10.798343] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   13.099805] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.080005] eth1: no IPv6 routers present
[   28.331692] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[/LIST]

```

---

### Post by wacky.banana on 2011-06-01
With the camera off and disconnetcted, I get this:

```
tail -f /var/log/syslog
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Successfully limited resources.
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Running.
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Watchdog thread running.
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Canary thread running.
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Successfully made thread 1438 of process 1438 (n/a) owned by '1000' high priority at nice level -11.
Jun  1 21:37:25 ko1-desktop rtkit-daemon[1440]: Supervising 1 threads of 1 processes of 1 users.
Jun  1 21:37:27 ko1-desktop rtkit-daemon[1440]: Successfully made thread 1466 of process 1466 (n/a) owned by '1000' high priority at nice level -11.
Jun  1 21:37:27 ko1-desktop rtkit-daemon[1440]: Supervising 2 threads of 2 processes of 1 users.
Jun  1 21:37:27 ko1-desktop pulseaudio[1466]: pid.c: Daemon already running.
Jun  1 21:37:28 ko1-desktop kernel: [   27.429652] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```With the camera connected and switched on, I get this:

```
pulseaudio[1466]: pid.c: Daemon already running.
Jun  1 21:37:28 ko1-desktop kernel: [   27.429652] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jun  1 21:40:21 ko1-desktop kernel: [  201.140682] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:22 ko1-desktop kernel: [  201.505344] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:22 ko1-desktop kernel: [  201.729235] firewire_core: skipped bus generations, destroying all nodes
Jun  1 21:40:22 ko1-desktop kernel: [  202.228042] firewire_core: rediscovered device fw0
Jun  1 21:40:22 ko1-desktop kernel: [  202.228060] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jun  1 21:40:22 ko1-desktop kernel: [  202.228181] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:52 ko1-desktop kernel: [  232.304021] firewire_core: giving up on config rom for node id ffc0
```Finally, with the command dmesg |tail - 30 I get this:

```
 dmesg | tail -30
[    8.376710] hda_intel: msi for device 1849:0888 set to 0
[    8.376713] hda_intel: position_fix set to 1 for device 1849:0888
[    8.376743] HDA Intel 0000:80:01.0: setting latency timer to 64
[    8.376748] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[    8.459430] hda_codec: ALC888: BIOS auto-probing.
[    8.803733] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.803748] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.804977] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[    8.923592] vesafb: framebuffer at 0xc0000000, mapped to 0xf8380000, using 3072k, total 3072k
[    8.923598] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    8.923600] vesafb: scrolling: redraw
[    8.923602] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    8.924635] Console: switching to colour frame buffer device 128x48
[    8.924670] fb0: VESA VGA frame buffer device
[    9.497428] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[    9.497457] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[    9.497619] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[    9.744720] r8169 0000:00:09.0: eth0-eth1: link up
[    9.744883] ADDRCONF(NETDEV_CHANGE): eth0-eth1: link becomes ready
[    9.859436] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   12.518581] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.512016] eth0-eth1: no IPv6 routers present
[   27.429652] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  201.140682] firewire_ohci: node ID not valid, new bus reset in progress
[  201.505344] firewire_ohci: node ID not valid, new bus reset in progress
[  201.729235] firewire_core: skipped bus generations, destroying all nodes
[  202.228042] firewire_core: rediscovered device fw0
[  202.228060] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  202.228181] firewire_ohci: node ID not valid, new bus reset in progress
[  232.304021] firewire_core: giving up on config rom for node id ffc0
```

I am just about to break open the PC to give you details of the firewire card I am using........which is.......

---

### Post by wacky.banana on 2011-06-01
...a SCI Firewave firwire card. There's not a lot more I can tell you about the card except to say it was working without issues in another PC I have running WinXP. I then transferred it to my other machine running Xubuntu.

One thing I have spotted is that withthis card installed into my Xubuntu box, the box won't go into suspend or hibernate. I tried these options with it removed and suspend and hibernate work fine.

I think I have been through all of your last suggestions. Any further ideas please/things I could try.

Once again many thanks for putting yourself out like this; I am very grateful for the help.

Kind regards,

WB

---

### Post by Toz on 2011-06-01
Okay. Looks like you're problem is here:```
Jun  1 21:37:28 ko1-desktop kernel: [   27.429652] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jun  1 21:40:21 ko1-desktop kernel: [  201.140682] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:22 ko1-desktop kernel: [  201.505344] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:22 ko1-desktop kernel: [  201.729235] firewire_core: skipped bus generations, destroying all nodes
Jun  1 21:40:22 ko1-desktop kernel: [  202.228042] firewire_core: rediscovered device fw0
Jun  1 21:40:22 ko1-desktop kernel: [  202.228060] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jun  1 21:40:22 ko1-desktop kernel: [  202.228181] firewire_ohci: node ID not valid, new bus reset in progress
Jun  1 21:40:52 ko1-desktop kernel: [  232.304021] firewire_core: giving up on config rom for node id ffc0
```

Lets see if we can find out whats going on. Can you run the following commands and post back the results:```
lsmod
lspci
ls -l /dev | grep 1394
cat /var/log/kern.log | grep 1394
uname -a
sudo dvdgrab -i
```

---

### Post by Toz on 2011-06-01
And one more. With the camera plugged in, please post back results of:```
ls -l /dev | grep fw
```

---

### Post by wacky.banana on 2011-06-01
lsmod gives:
```
   lsmod
Module                  Size  Used by
saa7115                18319  1 
nvidia               9766978  28 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
em28xx                 89343  0 
v4l2_common            16757  2 saa7115,em28xx
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
videodev               75143  3 saa7115,em28xx,v4l2_common
videobuf_vmalloc       13336  1 em28xx
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ppdev                  12849  0 
ir_nec_decoder         12490  0 
videobuf_core          25193  2 em28xx,videobuf_vmalloc
snd_timer              28659  2 snd_pcm,snd_seq
rc_core                25760  7 em28xx,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tveeprom               17009  1 em28xx
snd                    55295  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
i2c_viapro             12969  0 
parport_pc             32111  2 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
r8169                  42534  0 
firewire_core          56138  1 firewire_ohci
floppy                 60032  0 
via_rhine              27131  0 
pata_via               13368  0 
sata_via               13464  2 
crc_itu_t              12627  1 firewire_core  
```lspci gives:
```
 lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Parallel controller: AFAVLAB Technology Inc TK9902
00:0b.0 USB Controller: NEC Corporation USB (rev 43)
00:0b.1 USB Controller: NEC Corporation USB (rev 43)
00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a2)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
   
```]ls -l /dev | grep 1394 gives:
```
Nothing returned on screen
```

cat /var/log/kern.log | grep 1394 gives:

```
Nothing returned on screen
```

---

### Post by wacky.banana on 2011-06-01
...continued from previous post:

uname -a gives:

```
 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
   
```sudo dvdgrab -i gives:

```
Command not found
```

Finally, 

ls -l /dev | grep fw gives:

```
Nothing returned on screen 
```

---

### Post by Toz on 2011-06-01
> sudo dvdgrab -i
Command not found
My bad, I meant:```
sudo dvgrab -i
```

> ls -l /dev | grep fw gives:
Nothing returned on screen
This one surprises me. Can you try this:```
ls -l /dev/fw*
```

If still nothing, then:```
sudo modprobe -r firewire_ohci
sudo modprobe firewire_ohci
ls -l /dev/fw*
```

---

### Post by wacky.banana on 2011-06-02
Toz,

Responses are as follows:

sudo dvgrab -i gives:
```
 rom1394_1 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 1
Error: no camera exists

```Strange one this; the camera was switched on and ready to go before I booted up just to make sure the PC saw it.

ls -l /dev/fw* gives:
```
crw-------  1 root root  251, 0 2011-06-02 18:36 /dev/fw0
crw-rw----+ 1 root video 251, 1 2011-06-02 18:36 /dev/fw1
  
```sudo modprobe -r firewire_ohci gives:
```
No result on screen 
```sudo modprobe firewire_ohci gives:
```
No result on screen  
```

End of tests.

WB

---

### Post by Toz on 2011-06-02
I've done a bit of research. In a nutshell, the old firewire stack (ieee1984) was slowly being deprecated over the past few versions of ubuntu (actually the kernels they were using) in favour of Juju. Natty's kernel is the first kernel that has fully eliminated the old stack. Apparently, dvgrab still uses the old stack and has not yet been re-written to take advantage of the new stack. I did come across a couple of posts suggesting that a simple link of the new firewire device file (/dev/fw0) to the old firewire device file (/dev/raw1394) might fix the issue with dvgrab. So, lets give it a try. In a terminal window, type in the following:```
sudo ln /dev/fw0 /dev/raw1394
```and try unplugging and plugging in the camera again and trying. If it still doesn't work:```
sudo modprobe -r firewire_ohci
sudo modprobe firewire_ohci
```and if it still doesn't work, I shudder to say reboot.

Let me know how it works out.

---

### Post by wacky.banana on 2011-06-02
Ah I see; really thought I was going mad not getting this to work. :)

Running suggestions now:....

sudo ln /dev/fw0 /dev/raw1394 gives:
```
 ln: creating hard link `/dev/raw1394': File exists  
```Nothing on screen first time around so I repeated the command sequence and got the message above.
 Unplugged and r-eplugged the device, ran sudo kino in a terminal and, in Kino, got the message"no av compliant device connected". Ran it again, message says "capture failed". Kept getting this message in terminal repeating itself as follows:
```
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read 
```Running other commands now....
sudo modprobe -r firewire_ohci sudo modprobe firewire_ohci gives:

```
No results on screen  
```I will reboot now and report...


Meanwhile, your comments have got me thinking; if the firewire stack has been getting phased out over a series of ubuntu releases, do you know what earlier release had the stack working in full? I would be quite happy running that version i a virtual machine or even on another machine if doing so gets the camera to work. What's your view on this alternative approach?


......Rebooted with the camera in and switched on, ran Kino again, get the message "No AV/C compliant cam connected or switched on". I press capture, I get the message "waiting for DV (press play on camera)". Play is pressed in anyway, 10 seconds later, I get the message "capture failed".

Tests completed.

WB

---

### Post by Toz on 2011-06-02
Can you also try with the dvgrab program? Also try:```
sudo dvgrab -i
```and post back results.

Another suggestion is:```
sudo rm /dev/raw1394 && sudo ln /dev/fw1 /dev/raw1394
```then try the camera.

According to what I've read, the old stack was still available with previous versions of ubuntu but needs to be manually enabled via:```
sudo modprobe -r firewire-ohci
sudo modprobe ohci1394
sudo modprobe raw1394
sudo chgrp video /dev/raw1394
(Plug in camcorder)
```

Another option is to roll your own kernel with ieee1394 enabled.

Here is a listing of my reference links:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
[https://ieee1394.wiki.kernel.org/index.php/Juju_Migration](https://ieee1394.wiki.kernel.org/index.php/Juju_Migration)
[https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680](https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680)
[http://forums.gentoo.org/viewtopic-t-850989.html](http://forums.gentoo.org/viewtopic-t-850989.html)
[http://ubuntuforums.org/showthread.php?t=1644001](http://ubuntuforums.org/showthread.php?t=1644001)
[http://ubuntuforums.org/showthread.php?t=1742787](http://ubuntuforums.org/showthread.php?t=1742787)
[http://sourceforge.net/mailarchive/forum.php?thread_name=4DD241A7.9070304%40netmaster.dk&forum_name=linux1394-user](http://sourceforge.net/mailarchive/forum.php?thread_name=4DD241A7.9070304%40netmaster.dk&forum_name=linux1394-user)
[http://sourceforge.net/mailarchive/forum.php?forum_name=linux1394-user](http://sourceforge.net/mailarchive/forum.php?forum_name=linux1394-user)

---

### Post by wacky.banana on 2011-06-03
sudo dvgrab -i gives:
```
rom1394_1 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 1
Error: no camera exists
  
```sudo rm /dev/raw1394 && sudo ln /dev/fw1 /dev/raw1394 gives:
```
 rm: cannot remove `/dev/raw1394': No such file or directory
 
```Ran the camera under sudo, capture failed again.

I will install ubuntu 904 onto another machine later today, transfer the card over, enable firewire in the way that you suggest, and I will report back.

Many t hanks

WB

---

### Post by wacky.banana on 2011-06-03
So I installed 9.04 onto my machine, alongside 11.04. Tried to install Kino from the repositories and got this message:
"Kino cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type."

I then ran the commands you suggested above anyway, tried the install one more time, same error.

At this point I decided to throw in the towel, install Win7, use Click & Convert and get the job done that way. The video grab is working now in Win7 as I write this.

I appreciate you taking time out to help; shame it did not work out. Once again my thanks for all your help.

Kind regards,

WB

---

### Post by jroughy on 2011-06-18
I am getting exactly the same results.

I have a sneaking suspicion that it is Natty?

IEEE1394  works great on two much older machines, one a laptop and the other a desktop.

Pretty upsetting.





:confused::confused::confused::confused::confused::confused::confused:

---

### Post by jroughy on 2011-06-18
I am able to capture after checking out:  [https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680](https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680)

Specifically I ran sudo apt-get install vloopback-source


Posted by Toz.

---

### Post by jroughy on 2011-06-18
Rebooted and now not working?

---

### Post by consman on 2011-07-14
I am having the same problems as wacky.banana.  This is a bummer because Kino was working great back on Jun 11, 2011, and maybe even later than that, with my exact same hardware.  I am not sure what happened.  Thank you for fixing this soon.

---

### Post by scubasean on 2011-09-26
I am not anywhere near as conversant with Linux as you all but from what I can see I am having similar problems. I too had the:

WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!

Error in Kino. When I set Kino as root, I got:

"No AV/C compliant cam or not switched on"

As stated, I understand a raw1394 is obsolete and Natty uses a new stack.

When I used the command: dmesg | tail I got no info about firewire either with:

87.961972] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.183735] Intel AES-NI instructions are not detected.
[   88.218249] padlock_aes: VIA PadLock not detected.
[   98.512023] wlan0: no IPv6 routers present
[  299.988019] [Hardware Error]: Machine check events logged
[ 2374.854081] handle_rx_packet: invalid, small RX packet : 1
[ 3936.905715] handle_rx_packet: invalid, small RX packet : 1
[ 4313.231173] handle_rx_packet: invalid, small RX packet : 1
[ 4934.856222] handle_rx_packet: invalid, small RX packet : 1
[ 4994.201071] handle_rx_packet: invalid, small RX packet : 1

Or without the camera on:

[   87.939664] wlan0: authenticate with 00:26:44:44:12:cb (try 1)
[   87.941617] wlan0: authenticated
[   87.958671] wlan0: associate with 00:26:44:44:12:cb (try 1)
[   87.961189] wlan0: RX AssocResp from 00:26:44:44:12:cb (capab=0x411 status=0 aid=1)
[   87.961197] wlan0: associated
[   87.961972] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.183735] Intel AES-NI instructions are not detected.
[   88.218249] padlock_aes: VIA PadLock not detected.
[   98.512023] wlan0: no IPv6 routers present
[  299.988019] [Hardware Error]: Machine check events logged

But, as I said, I am pretty much a novice so am totally flumoxed!!

Thanks

Sean

---

