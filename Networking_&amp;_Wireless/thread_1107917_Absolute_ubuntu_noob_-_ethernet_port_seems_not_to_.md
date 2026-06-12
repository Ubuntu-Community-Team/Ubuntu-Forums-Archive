---
title: "Absolute ubuntu noob - ethernet port seems not to be working..?"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by ronaldfinch on 2009-03-27
Hi all,
Am a long time mac user/noob to ubuntu. A colleague gave me a functioning pc upon which I recently installed ubuntu 8.10. I want to connect to the internet via the ethernet port - the internet connection to my modem is fine when my mac is connected to it, but does not work when connected to the ubuntu pc. Am struggling to know where to start to sort it out. I imagine most of you have read this loads of times - any help would be greatly appreciated.

Cheers

Ron

---

### Post by ronaldfinch on 2009-03-27
My modem's ip address is 192.168.1.1. When I try to connect to it I get "The connection was refused when attempting to contact 192.168.1.1..." The modem is not set up to restrict access by MAC address. I can connect to my modem fine with my mac...

Thanks all!

---

### Post by coutts99 on 2009-03-27
Can you post the output of -:

```
sudo ifconfig
```

and 

```
sudo dmesg
```

---

### Post by ronaldfinch on 2009-03-27
Hi thanks, yes will do that - bear with me a few minutes have to figure out how to transfer results between this computer + ubuntu pc.

Cheers

---

### Post by ronaldfinch on 2009-03-27
Am having a few difficulties getting those results from my ubuntu pc to this mac. Are there any bits of the results in particular I can give you?


(I cannot get the mac to see the ubuntu pc, and my 2 external hard drives are appearing as read only on the ubuntu pc.)


Thanks

---

### Post by ronaldfinch on 2009-03-27
Different issue I know but can someone confirm that this is how I would make the external drive I have attached to the ubuntu pc writable by my account?

    sudo chmod go+w /media/disk


Cheers - if I can make disk writable I can post above results...

---

### Post by coutts99 on 2009-03-27
What filesystem is that external harddrive? If it's ntfs, then you need to install ntfs-3g first before you can write to it; but if it's vfat, then you just need to mount it with the right arguments so you can write to it.

```
sudo fdisk -l
```

---

### Post by ronaldfinch on 2009-03-27
Well it is HFS+. Suppose it was naive to assume I could plug it in and use it. All the files appear it is just read only...

---

### Post by ronaldfinch on 2009-03-27
Thanks for your efforts by the way

---

### Post by coutts99 on 2009-03-27
> **ronaldfinch said:**
> Well it is HFS+. Suppose it was naive to assume I could plug it in and use it. All the files appear it is just read only...

[http://ubuntuforums.org/showthread.php?t=98286]("http://ubuntuforums.org/showthread.php?t=98286")

Try that thread?

---

### Post by ronaldfinch on 2009-03-27
Excellent thank you. I had to turn journalling off then change the permissions - managed that so here is the info...


eth0      Link encap:Ethernet  HWaddr 00:07:95:2c:50:a0  
          inet6 addr: fe80::207:95ff:fe2c:50a0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4572 (4.5 KB)
          Interrupt:3 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17972 (17.9 KB)  TX bytes:17972 (17.9 KB)




[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to fff0000 @ 7000-d000
[    0.000000] RAMDISK: 0f822000 - 0ffef311
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FC390, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 0028 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 0FFF0030, 0074 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 0FFF00B0, 2D2C (r1    SiS     730S      100 MSFT  100000B)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00002000 - 00004000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f822000 - 000ffef311]          RAMDISK ==> [000f822000 - 000ffef311]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65423
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 60884 pages, LIFO batch:15
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64847
[    0.000000] Kernel command line: root=UUID=beb02269-6745-43d3-b0cc-ec8522158fd0 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 892.503 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 246212k/262080k available (2572k kernel code, 15468k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004030] Calibrating delay loop (skipped), value calculated using timer frequency.. 1785.00 BogoMIPS (lpj=3570012)
[    0.004091] Security Framework initialized
[    0.004114] SELinux:  Disabled at boot.
[    0.004211] AppArmor: AppArmor initialized
[    0.004236] Mount-cache hash table entries: 512
[    0.004725] Initializing cgroup subsys ns
[    0.004742] Initializing cgroup subsys cpuacct
[    0.004748] Initializing cgroup subsys memory
[    0.004795] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004803] CPU: L2 Cache: 64K (64 bytes/line)
[    0.004854] Checking 'hlt' instruction... OK.
[    0.020141] SMP alternatives: switching to UP code
[    0.032092] Freeing SMP alternatives: 11k freed
[    0.032316] weird, boot CPU (#0) not listedby the BIOS.
[    0.032323] SMP motherboard not detected.
[    0.032333] Local APIC not detected. Using dummy APIC emulation.
[    0.032339] SMP disabled
[    0.032580] Brought up 1 CPUs
[    0.032588] Total of 1 processors activated (1785.00 BogoMIPS).
[    0.032638] CPU0 attaching sched-domain:
[    0.032648]  domain 0: span 0 level CPU
[    0.032655]   groups: 0
[    0.033539] net_namespace: 840 bytes
[    0.033567] Booting paravirtualized kernel on bare hardware
[    0.034056] Time: 12:50:33  Date: 03/27/09
[    0.034177] NET: Registered protocol family 16
[    0.035454] EISA bus registered
[    0.038939] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[    0.038951] PCI: Using configuration type 1 for base access
[    0.042405] ACPI: Interpreter disabled.
[    0.042420] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.042570] pnp: PnP ACPI: disabled
[    0.042582] PnPBIOS: Scanning system for PnP BIOS support...
[    0.042682] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7d60
[    0.042691] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6b24, dseg 0xf0000
[    0.045630] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.047048] PCI: Probing PCI hardware
[    0.047062] PCI: Probing PCI hardware (bus 00)
[    0.047290] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d3ffffff]
[    0.047390] PCI: 0000:00:00.1 reg 20 io port: [ff00, ff0f]
[    0.047518] PCI: 0000:00:01.1 reg 10 io port: [d400, d4ff]
[    0.047530] PCI: 0000:00:01.1 reg 14 32bit mmio: [cfffb000, cfffbfff]
[    0.047562] PCI: 0000:00:01.1 reg 30 32bit mmio: [cffc0000, cffdffff]
[    0.047584] pci 0000:00:01.1: supports D1
[    0.047589] pci 0000:00:01.1: supports D2
[    0.047595] pci 0000:00:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.047604] pci 0000:00:01.1: PME# disabled
[    0.047630] PCI: 0000:00:01.2 reg 10 32bit mmio: [cfffc000, cfffcfff]
[    0.047699] PCI: 0000:00:01.3 reg 10 32bit mmio: [cfffd000, cfffdfff]
[    0.047772] PCI: 0000:00:01.4 reg 10 io port: [d800, d8ff]
[    0.047783] PCI: 0000:00:01.4 reg 14 32bit mmio: [cfffe000, cfffefff]
[    0.047828] pci 0000:00:01.4: supports D1
[    0.047832] pci 0000:00:01.4: supports D2
[    0.047838] pci 0000:00:01.4: PME# supported from D2 D3hot D3cold
[    0.047846] pci 0000:00:01.4: PME# disabled
[    0.047974] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.048030] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, c7ffffff]
[    0.048060] PCI: 0000:01:00.0 reg 30 32bit mmio: [cfee0000, cfefffff]
[    0.048123] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
[    0.048132] PCI: bridge 0000:00:02.0 32bit mmio: [cde00000, cfefffff]
[    0.048143] PCI: bridge 0000:00:02.0 32bit mmio pref: [bdc00000, cdcfffff]
[    0.049752] pci 0000:00:01.0: SIS IRQ router [1039/0018]
[    0.050202] NET: Registered protocol family 8
[    0.050202] NET: Registered protocol family 20
[    0.050202] NetLabel: Initializing
[    0.050202] NetLabel:  domain hash size = 128
[    0.050202] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.050202] NetLabel:  unlabeled traffic allowed by default
[    0.050202] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.050202]    actual entries 65620
[    0.052495] AppArmor: AppArmor Filesystem Enabled
[    0.052578] system 00:01: iomem range 0x0-0x9fbff could not be reserved
[    0.052586] system 00:01: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.052595] system 00:01: iomem range 0xf0000-0xfffff could not be reserved
[    0.052603] system 00:01: iomem range 0x100000-0xfffffff could not be reserved
[    0.052612] system 00:01: iomem range 0xfff0000-0xfff7fff could not be reserved
[    0.052620] system 00:01: iomem range 0xfff8000-0xfffffff could not be reserved
[    0.052630] system 00:01: iomem range 0xfffc0000-0xffffffff could not be reserved
[    0.054681] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.054694] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.054706] pci 0000:00:02.0:   MEM window: 0xcde00000-0xcfefffff
[    0.054717] pci 0000:00:02.0:   PREFETCH window: 0x000000bdc00000-0x000000cdcfffff
[    0.054745] pci 0000:00:02.0: setting latency timer to 64
[    0.054754] bus: 00 index 0 io port: [0, ffff]
[    0.054760] bus: 00 index 1 mmio: [0, ffffffff]
[    0.054766] bus: 01 index 0 io port: [b000, bfff]
[    0.054771] bus: 01 index 1 mmio: [cde00000, cfefffff]
[    0.054777] bus: 01 index 2 mmio: [bdc00000, cdcfffff]
[    0.054783] bus: 01 index 3 mmio: [0, 0]
[    0.054828] NET: Registered protocol family 2
[    0.055299] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.055939] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056226] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056451] TCP: Hash tables configured (established 8192 bind 8192)
[    0.056460] TCP reno registered
[    0.056824] NET: Registered protocol family 1
[    0.057209] checking if image is initramfs... it is
[    1.774335] Freeing initrd memory: 7988k freed
[    1.776615] audit: initializing netlink socket (disabled)
[    1.776683] type=2000 audit(1238158233.776:1): initialized
[    1.791112] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.799342] VFS: Disk quotas dquot_6.5.1
[    1.799737] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.800233] msgmni has been set to 496
[    1.800846] io scheduler noop registered
[    1.800858] io scheduler anticipatory registered
[    1.800864] io scheduler deadline registered
[    1.800932] io scheduler cfq registered (default)
[    1.801055] pci 0000:01:00.0: Boot video device
[    1.802072] isapnp: Scanning for PnP cards...
[    2.155512] isapnp: No Plug & Play device found
[    2.476431] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.476782] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.481580] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.488536] brd: module loaded
[    2.488805] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.489226] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    2.489237] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.489590] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.491790] mice: PS/2 mouse device common for all mice
[    2.492711] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.492758] rtc0: alarms up to one day
[    2.493239] EISA: Probing bus 0 at eisa.0
[    2.493278] Cannot allocate resource for EISA slot 5
[    2.493297] EISA: Detected 0 cards.
[    2.493308] cpuidle: using governor ladder
[    2.493314] cpuidle: using governor menu
[    2.494852] TCP cubic registered
[    2.494957] Using IPI No-Shortcut mode
[    2.496719] registered taskstats version 1
[    2.496939]   Magic number: 1:71:836
[    2.497244] tty ptyu2: hash matches
[    2.497434] rtc_cmos 00:05: setting system clock to 2009-03-27 12:50:35 UTC (1238158235)
[    2.497445] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.497451] EDD information not available.
[    2.499090] Freeing unused kernel memory: 424k freed
[    2.499248] Write protecting the kernel text: 2576k
[    2.499353] Write protecting the kernel read-only data: 936k
[    2.521730] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.992299] fuse init (API version 7.9)
[    3.263013] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    4.361387] SCSI subsystem initialized
[    4.397510] usbcore: registered new interface driver usbfs
[    4.397591] usbcore: registered new interface driver hub
[    4.451783] usbcore: registered new device driver usb
[    4.500129] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.500219] PCI: setting IRQ 12 as level-triggered
[    4.500282] ohci_hcd 0000:00:01.2: found PCI INT D -> IRQ 12
[    4.500309] ohci_hcd 0000:00:01.2: sharing IRQ 12 with 0000:00:01.3
[    4.500359] ohci_hcd 0000:00:01.2: OHCI Host Controller
[    4.500546] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    4.500594] ohci_hcd 0000:00:01.2: irq 12, io mem 0xcfffc000
[    4.514565] sis900.c: v1.08.10 Apr. 2 2006
[    4.517623] libata version 3.00 loaded.
[    4.558910] usb usb1: configuration #1 chosen from 1 choice
[    4.559033] hub 1-0:1.0: USB hub found
[    4.559072] hub 1-0:1.0: 3 ports detected
[    4.661251] ohci_hcd 0000:00:01.3: found PCI INT D -> IRQ 12
[    4.661282] ohci_hcd 0000:00:01.3: sharing IRQ 12 with 0000:00:01.2
[    4.661338] ohci_hcd 0000:00:01.3: OHCI Host Controller
[    4.661441] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[    4.661488] ohci_hcd 0000:00:01.3: irq 12, io mem 0xcfffd000
[    4.718948] usb usb2: configuration #1 chosen from 1 choice
[    4.719041] hub 2-0:1.0: USB hub found
[    4.719081] hub 2-0:1.0: 3 ports detected
[    4.925522] PCI: setting IRQ 3 as level-triggered
[    4.925538] sis900 0000:00:01.1: found PCI INT C -> IRQ 3
[    4.926414] 0000:00:01.1: VIA 6103 PHY transceiver found at address 1.
[    4.934815] 0000:00:01.1: Using transceiver found at address 1 as default
[    4.936071] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 3, 00:07:95:2c:50:a0
[    4.962443] pata_sis 0000:00:00.1: version 0.5.2
[    4.966558] scsi0 : pata_sis
[    4.967143] scsi1 : pata_sis
[    4.967261] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.967271] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.120422] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.136972] ata1.00: ATA-7: Maxtor 2F040J0, VAM51JJ0, max UDMA/133
[    5.136986] ata1.00: 80293248 sectors, multi 16: LBA 
[    5.137028] ata1.01: ATAPI: CD-532E-B, 1.0A, max MWDMA2
[    5.152824] ata1.00: configured for UDMA/100
[    5.168779] ata1.01: configured for PIO4
[    5.336034] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040J0   VAM5 PQ: 0 ANSI: 5
[    5.338605] scsi 0:0:1:0: CD-ROM            TEAC     CD-532E-B        1.0A PQ: 0 ANSI: 5
[    5.351828] usb 2-1: configuration #1 chosen from 1 choice
[    7.039501] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.039665] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    7.134971] usbcore: registered new interface driver hiddev
[    7.145365] input: Microsoft Microsoft IntelliMouseÔø&#937; Optical as /devices/pci0000:00/0000:00:01.3/usb2/2-1/2-1:1.0/input/input2
[    7.161223] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouseÔø&#937; Optical] on usb-0000:00:01.3-1
[    7.161296] usbcore: registered new interface driver usbhid
[    7.161308] usbhid: v2.6:USB HID core driver
[    7.186288] Driver 'sd' needs updating - please use bus_type methods
[    7.186689] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    7.186746] sd 0:0:0:0: [sda] Write Protect is off
[    7.186754] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.186831] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.187066] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    7.187112] sd 0:0:0:0: [sda] Write Protect is off
[    7.187119] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.187190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.187207]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.213327]  sda1 sda2 < sda5 >
[    7.247502] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.278994] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[    7.279013] Uniform CD-ROM driver Revision: 3.20
[    7.279345] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    7.833074] PM: Starting manual resume from disk
[    7.833096] PM: Resume from partition 8:5
[    7.833101] PM: Checking hibernation image.
[    7.840841] PM: Resume from disk failed.
[    7.965914] kjournald starting.  Commit interval 5 seconds
[    7.965984] EXT3-fs: mounted filesystem with ordered data mode.
[   16.080371] udevd version 124 started
[   18.001560] Linux agpgart interface v0.103
[   18.045573] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.173627] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.209558] agpgart-sis 0000:00:00.0: SiS chipset [1039/0730]
[   18.239584] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   18.240345] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   21.245031] PCI: setting IRQ 11 as level-triggered
[   21.245046] Trident4DWaveAudio 0000:00:01.4: found PCI INT B -> IRQ 11
[   22.186165] Clocksource tsc unstable (delta = 144006013 ns)
[   22.830129] MC'97 1 converters and GPIO not ready (0x800f)
[   22.854364] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2294kHz
[   26.105446] ac97 codec read TIMEOUT [0x54/0x800fc0d4]!!!
[   27.664625] parport_pc 00:0c: reported by Plug and Play BIOS
[   27.664698] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   27.759383] lp0: using parport0 (interrupt-driven).
[   28.891561] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   29.538355] EXT3 FS on sda1, internal journal
[   31.348101] type=1505 audit(1238158266.867:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3619
[   31.966796] type=1505 audit(1238158267.487:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3624
[   31.968094] type=1505 audit(1238158267.487:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3624
[   32.300237] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.245070] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   34.245548] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   34.246420] powernow_k7: Unknown symbol acpi_processor_register_performance
[   34.313181] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   34.313623] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   34.315028] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   34.315605] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   35.868025] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   36.032486] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.552329] ppdev: user-space parallel port driver
[   38.892217] Bluetooth: Core ver 2.13
[   38.899880] NET: Registered protocol family 31
[   38.899897] Bluetooth: HCI device and connection manager initialized
[   38.899910] Bluetooth: HCI socket layer initialized
[   38.977246] Bluetooth: L2CAP ver 2.11
[   38.977283] Bluetooth: L2CAP socket layer initialized
[   39.035431] Bluetooth: RFCOMM socket layer initialized
[   39.037366] Bluetooth: RFCOMM TTY layer initialized
[   39.037404] Bluetooth: RFCOMM ver 1.10
[   39.058801] Bluetooth: SCO (Voice Link) ver 0.6
[   39.058837] Bluetooth: SCO socket layer initialized
[   39.129552] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.129574] Bluetooth: BNEP filters: protocol multicast
[   39.250967] Bridge firewalling registered
[   39.252574] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   43.914913] NET: Registered protocol family 17
[   46.455139] eth0: Media Link On 100mbps full-duplex 
[   93.846268] NET: Registered protocol family 10
[   93.853078] lo: Disabled Privacy Extensions
[  103.973878] eth0: no IPv6 routers present
[  146.468990] ppdev0: registered pardevice
[  146.516486] ppdev0: unregistered pardevice
[  146.769077] ppdev0: registered pardevice
[  146.935498] ppdev0: unregistered pardevice
[  149.333280] ppdev0: registered pardevice
[  149.381221] ppdev0: unregistered pardevice
[  149.987078] type=1503 audit(1238158385.506:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/4944/net/" pid=4944 profile="/usr/sbin/cupsd"
[  149.994753] type=1503 audit(1238158385.514:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.001003] type=1503 audit(1238158385.522:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.007239] type=1503 audit(1238158385.526:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.010744] type=1503 audit(1238158385.530:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.014002] type=1503 audit(1238158385.534:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.014029] type=1503 audit(1238158385.534:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.014048] type=1503 audit(1238158385.534:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.014065] type=1503 audit(1238158385.534:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=4944 profile="/usr/sbin/cupsd"
[  150.014365] type=1503 audit(1238158385.534:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/4944/net/dev" pid=4944 profile="/usr/sbin/cupsd"
[  487.480009] eth0: Media Link Off

---

### Post by coutts99 on 2009-03-27
Can you try running -:

```
sudo dhclient eth0
```

---

### Post by coutts99 on 2009-03-27
Hmm you have this at the bottom of your dmesg out put -:

```
eth0: Media Link Off
```

Which suggest it hasn't got a link.

Does the port light up on the switch/router you are plugged into? Double check your cabling.

---

### Post by ronaldfinch on 2009-03-27
Hi when I connect the ubuntu pc to the modem using the ethernet cable the ethernet light on the modem lights up. Am using the same cable to connect to the same modem now to send this message...

Here is the result of the sudo dhclient eth0

Listening on LPF/eth0/00:07:95:2c:50:a0
Sending on   LPF/eth0/00:07:95:2c:50:a0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14


cheers

---

### Post by coutts99 on 2009-03-27
Can you plug the cable into the ubuntu pc do a dmesg whilst it is plugged in?

You should see a 'link up' message at the bottom

---

### Post by ronaldfinch on 2009-03-27
ok had a problem because I disconnected original drive from mac without unmounting by accident (knocked power cable out) and it wont mount on mac...! :(


Anyway got another drive sorted out will deal with that later. Here is the result with the ethernet cable connected to modem.

[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to fff0000 @ 7000-d000
[    0.000000] RAMDISK: 0f822000 - 0ffef311
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FC390, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 0028 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 0FFF0030, 0074 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 0FFF00B0, 2D2C (r1    SiS     730S      100 MSFT  100000B)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00002000 - 00004000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f822000 - 000ffef311]          RAMDISK ==> [000f822000 - 000ffef311]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65423
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 60884 pages, LIFO batch:15
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64847
[    0.000000] Kernel command line: root=UUID=beb02269-6745-43d3-b0cc-ec8522158fd0 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 892.503 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 246212k/262080k available (2572k kernel code, 15468k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004030] Calibrating delay loop (skipped), value calculated using timer frequency.. 1785.00 BogoMIPS (lpj=3570012)
[    0.004092] Security Framework initialized
[    0.004114] SELinux:  Disabled at boot.
[    0.004212] AppArmor: AppArmor initialized
[    0.004237] Mount-cache hash table entries: 512
[    0.004726] Initializing cgroup subsys ns
[    0.004743] Initializing cgroup subsys cpuacct
[    0.004750] Initializing cgroup subsys memory
[    0.004797] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004805] CPU: L2 Cache: 64K (64 bytes/line)
[    0.004855] Checking 'hlt' instruction... OK.
[    0.020141] SMP alternatives: switching to UP code
[    0.032091] Freeing SMP alternatives: 11k freed
[    0.032315] weird, boot CPU (#0) not listedby the BIOS.
[    0.032322] SMP motherboard not detected.
[    0.032331] Local APIC not detected. Using dummy APIC emulation.
[    0.032338] SMP disabled
[    0.032578] Brought up 1 CPUs
[    0.032586] Total of 1 processors activated (1785.00 BogoMIPS).
[    0.032637] CPU0 attaching sched-domain:
[    0.032646]  domain 0: span 0 level CPU
[    0.032654]   groups: 0
[    0.033534] net_namespace: 840 bytes
[    0.033562] Booting paravirtualized kernel on bare hardware
[    0.034051] Time: 14:56:26  Date: 03/27/09
[    0.034171] NET: Registered protocol family 16
[    0.035451] EISA bus registered
[    0.038937] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[    0.038949] PCI: Using configuration type 1 for base access
[    0.042403] ACPI: Interpreter disabled.
[    0.042419] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.042567] pnp: PnP ACPI: disabled
[    0.042580] PnPBIOS: Scanning system for PnP BIOS support...
[    0.042678] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7d60
[    0.042687] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6b24, dseg 0xf0000
[    0.045630] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.047041] PCI: Probing PCI hardware
[    0.047056] PCI: Probing PCI hardware (bus 00)
[    0.047284] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d3ffffff]
[    0.047384] PCI: 0000:00:00.1 reg 20 io port: [ff00, ff0f]
[    0.047511] PCI: 0000:00:01.1 reg 10 io port: [d400, d4ff]
[    0.047523] PCI: 0000:00:01.1 reg 14 32bit mmio: [cfffb000, cfffbfff]
[    0.047556] PCI: 0000:00:01.1 reg 30 32bit mmio: [cffc0000, cffdffff]
[    0.047578] pci 0000:00:01.1: supports D1
[    0.047583] pci 0000:00:01.1: supports D2
[    0.047589] pci 0000:00:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.047598] pci 0000:00:01.1: PME# disabled
[    0.047624] PCI: 0000:00:01.2 reg 10 32bit mmio: [cfffc000, cfffcfff]
[    0.047694] PCI: 0000:00:01.3 reg 10 32bit mmio: [cfffd000, cfffdfff]
[    0.047766] PCI: 0000:00:01.4 reg 10 io port: [d800, d8ff]
[    0.047778] PCI: 0000:00:01.4 reg 14 32bit mmio: [cfffe000, cfffefff]
[    0.047822] pci 0000:00:01.4: supports D1
[    0.047827] pci 0000:00:01.4: supports D2
[    0.047832] pci 0000:00:01.4: PME# supported from D2 D3hot D3cold
[    0.047840] pci 0000:00:01.4: PME# disabled
[    0.047969] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.048026] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, c7ffffff]
[    0.048056] PCI: 0000:01:00.0 reg 30 32bit mmio: [cfee0000, cfefffff]
[    0.048120] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
[    0.048129] PCI: bridge 0000:00:02.0 32bit mmio: [cde00000, cfefffff]
[    0.048139] PCI: bridge 0000:00:02.0 32bit mmio pref: [bdc00000, cdcfffff]
[    0.049750] pci 0000:00:01.0: SIS IRQ router [1039/0018]
[    0.050202] NET: Registered protocol family 8
[    0.050202] NET: Registered protocol family 20
[    0.050202] NetLabel: Initializing
[    0.050202] NetLabel:  domain hash size = 128
[    0.050202] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.050202] NetLabel:  unlabeled traffic allowed by default
[    0.050202] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.050202]    actual entries 65620
[    0.052487] AppArmor: AppArmor Filesystem Enabled
[    0.052568] system 00:01: iomem range 0x0-0x9fbff could not be reserved
[    0.052576] system 00:01: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.052586] system 00:01: iomem range 0xf0000-0xfffff could not be reserved
[    0.052594] system 00:01: iomem range 0x100000-0xfffffff could not be reserved
[    0.052602] system 00:01: iomem range 0xfff0000-0xfff7fff could not be reserved
[    0.052610] system 00:01: iomem range 0xfff8000-0xfffffff could not be reserved
[    0.052620] system 00:01: iomem range 0xfffc0000-0xffffffff could not be reserved
[    0.054675] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.054688] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.054701] pci 0000:00:02.0:   MEM window: 0xcde00000-0xcfefffff
[    0.054711] pci 0000:00:02.0:   PREFETCH window: 0x000000bdc00000-0x000000cdcfffff
[    0.054739] pci 0000:00:02.0: setting latency timer to 64
[    0.054748] bus: 00 index 0 io port: [0, ffff]
[    0.054754] bus: 00 index 1 mmio: [0, ffffffff]
[    0.054760] bus: 01 index 0 io port: [b000, bfff]
[    0.054766] bus: 01 index 1 mmio: [cde00000, cfefffff]
[    0.054771] bus: 01 index 2 mmio: [bdc00000, cdcfffff]
[    0.054777] bus: 01 index 3 mmio: [0, 0]
[    0.054822] NET: Registered protocol family 2
[    0.055291] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.055928] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056214] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056438] TCP: Hash tables configured (established 8192 bind 8192)
[    0.056447] TCP reno registered
[    0.056810] NET: Registered protocol family 1
[    0.057197] checking if image is initramfs... it is
[    1.773397] Freeing initrd memory: 7988k freed
[    1.775603] audit: initializing netlink socket (disabled)
[    1.775671] type=2000 audit(1238165787.772:1): initialized
[    1.790211] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.798560] VFS: Disk quotas dquot_6.5.1
[    1.798958] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.799401] msgmni has been set to 496
[    1.799974] io scheduler noop registered
[    1.799985] io scheduler anticipatory registered
[    1.799991] io scheduler deadline registered
[    1.800060] io scheduler cfq registered (default)
[    1.800232] pci 0000:01:00.0: Boot video device
[    1.801275] isapnp: Scanning for PnP cards...
[    2.154727] isapnp: No Plug & Play device found
[    2.481700] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.482042] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.486813] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.493756] brd: module loaded
[    2.494028] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.494441] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    2.494451] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.494855] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.497120] mice: PS/2 mouse device common for all mice
[    2.497966] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.498012] rtc0: alarms up to one day
[    2.498485] EISA: Probing bus 0 at eisa.0
[    2.498523] Cannot allocate resource for EISA slot 5
[    2.498543] EISA: Detected 0 cards.
[    2.498553] cpuidle: using governor ladder
[    2.498559] cpuidle: using governor menu
[    2.500090] TCP cubic registered
[    2.500257] Using IPI No-Shortcut mode
[    2.501921] registered taskstats version 1
[    2.502140]   Magic number: 1:386:941
[    2.502428] tty ptyyc: hash matches
[    2.502638] rtc_cmos 00:05: setting system clock to 2009-03-27 14:56:28 UTC (1238165788)
[    2.502649] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.502655] EDD information not available.
[    2.504369] Freeing unused kernel memory: 424k freed
[    2.504522] Write protecting the kernel text: 2576k
[    2.504627] Write protecting the kernel read-only data: 936k
[    2.524060] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.000323] fuse init (API version 7.9)
[    3.266772] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    4.363427] SCSI subsystem initialized
[    4.401409] usbcore: registered new interface driver usbfs
[    4.401492] usbcore: registered new interface driver hub
[    4.470225] usbcore: registered new device driver usb
[    4.505287] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.505378] PCI: setting IRQ 12 as level-triggered
[    4.505388] ohci_hcd 0000:00:01.2: found PCI INT D -> IRQ 12
[    4.505414] ohci_hcd 0000:00:01.2: sharing IRQ 12 with 0000:00:01.3
[    4.505465] ohci_hcd 0000:00:01.2: OHCI Host Controller
[    4.505647] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    4.505698] ohci_hcd 0000:00:01.2: irq 12, io mem 0xcfffc000
[    4.519540] sis900.c: v1.08.10 Apr. 2 2006
[    4.522607] libata version 3.00 loaded.
[    4.562977] usb usb1: configuration #1 chosen from 1 choice
[    4.563105] hub 1-0:1.0: USB hub found
[    4.563144] hub 1-0:1.0: 3 ports detected
[    4.769296] ohci_hcd 0000:00:01.3: found PCI INT D -> IRQ 12
[    4.769327] ohci_hcd 0000:00:01.3: sharing IRQ 12 with 0000:00:01.2
[    4.769383] ohci_hcd 0000:00:01.3: OHCI Host Controller
[    4.769472] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[    4.769528] ohci_hcd 0000:00:01.3: irq 12, io mem 0xcfffd000
[    4.827053] usb usb2: configuration #1 chosen from 1 choice
[    4.827148] hub 2-0:1.0: USB hub found
[    4.827187] hub 2-0:1.0: 3 ports detected
[    4.944452] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    5.033550] PCI: setting IRQ 3 as level-triggered
[    5.033565] sis900 0000:00:01.1: found PCI INT C -> IRQ 3
[    5.034445] 0000:00:01.1: VIA 6103 PHY transceiver found at address 1.
[    5.043120] 0000:00:01.1: Using transceiver found at address 1 as default
[    5.047026] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 3, 00:07:95:2c:50:a0
[    5.076599] pata_sis 0000:00:00.1: version 0.5.2
[    5.080492] scsi0 : pata_sis
[    5.081058] scsi1 : pata_sis
[    5.081164] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    5.081174] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.161120] usb 1-1: configuration #1 chosen from 1 choice
[    5.252974] ata1.00: ATA-7: Maxtor 2F040J0, VAM51JJ0, max UDMA/133
[    5.252988] ata1.00: 80293248 sectors, multi 16: LBA 
[    5.253031] ata1.01: ATAPI: CD-532E-B, 1.0A, max MWDMA2
[    5.270039] ata1.00: configured for UDMA/100
[    5.284697] ata1.01: configured for PIO4
[    5.340431] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.452023] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040J0   VAM5 PQ: 0 ANSI: 5
[    5.454526] scsi 0:0:1:0: CD-ROM            TEAC     CD-532E-B        1.0A PQ: 0 ANSI: 5
[    5.567948] usb 2-1: configuration #1 chosen from 1 choice
[    7.025369] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.025514] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    7.092698] usbcore: registered new interface driver libusual
[    7.128854] Initializing USB Mass Storage driver...
[    7.131338] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.131726] usbcore: registered new interface driver usb-storage
[    7.131739] USB Mass Storage support registered.
[    7.132254] usb-storage: device found at 2
[    7.132264] usb-storage: waiting for device to settle before scanning
[    7.174319] Driver 'sd' needs updating - please use bus_type methods
[    7.180601] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    7.180663] sd 0:0:0:0: [sda] Write Protect is off
[    7.180671] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.180747] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.181027] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    7.181073] sd 0:0:0:0: [sda] Write Protect is off
[    7.181081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.181150] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.181166]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    7.243597]  sda5 >
[    7.244163] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.275689] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[    7.275708] Uniform CD-ROM driver Revision: 3.20
[    7.276063] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    7.312917] usbcore: registered new interface driver hiddev
[    7.323230] input: Microsoft Microsoft IntelliMouseÔø&#937; Optical as /devices/pci0000:00/0000:00:01.3/usb2/2-1/2-1:1.0/input/input2
[    7.333056] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouseÔø&#937; Optical] on usb-0000:00:01.3-1
[    7.333131] usbcore: registered new interface driver usbhid
[    7.333142] usbhid: v2.6:USB HID core driver
[    7.936654] PM: Starting manual resume from disk
[    7.936673] PM: Resume from partition 8:5
[    7.936678] PM: Checking hibernation image.
[    7.937135] PM: Resume from disk failed.
[    8.061370] kjournald starting.  Commit interval 5 seconds
[    8.061436] EXT3-fs: mounted filesystem with ordered data mode.
[   12.130271] usb-storage: device scan complete
[   12.137235] scsi 2:0:0:0: Direct-Access     Maxtor   6L250R0          BAH4 PQ: 0 ANSI: 2
[   12.148163] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   12.161164] sd 2:0:0:0: [sdb] Write Protect is off
[   12.161183] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[   12.161191] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   12.172156] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   12.185251] sd 2:0:0:0: [sdb] Write Protect is off
[   12.185267] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[   12.185275] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   12.185299]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
[   12.222909] sd 2:0:0:0: [sdb] Attached SCSI disk
[   12.223642] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   16.077068] udevd version 124 started
[   18.043066] Linux agpgart interface v0.103
[   18.131296] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.243143] agpgart-sis 0000:00:00.0: SiS chipset [1039/0730]
[   18.252232] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   18.273560] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.380157] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   21.681316] PCI: setting IRQ 11 as level-triggered
[   21.681332] Trident4DWaveAudio 0000:00:01.4: found PCI INT B -> IRQ 11
[   22.853353] Clocksource tsc unstable (delta = 312015130 ns)
[   23.473558] MC'97 1 converters and GPIO not ready (0x800f)
[   23.490648] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2386kHz
[   26.953498] ac97 codec read TIMEOUT [0x54/0x800fc0d4]!!!
[   28.879441] parport_pc 00:0c: reported by Plug and Play BIOS
[   28.879510] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   28.975293] lp0: using parport0 (interrupt-driven).
[   29.825740] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   30.474941] EXT3 FS on sda1, internal journal
[   32.280712] type=1505 audit(1238165820.330:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3691
[   32.898733] type=1505 audit(1238165820.950:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3696
[   32.900041] type=1505 audit(1238165820.950:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3696
[   33.223200] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.200766] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   35.201215] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   35.201903] powernow_k7: Unknown symbol acpi_processor_register_performance
[   35.271668] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   35.272149] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   35.273491] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   35.274292] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   36.924078] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   37.086514] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   37.584895] ppdev: user-space parallel port driver
[   41.847859] Bluetooth: Core ver 2.13
[   41.853973] NET: Registered protocol family 31
[   41.853993] Bluetooth: HCI device and connection manager initialized
[   41.854006] Bluetooth: HCI socket layer initialized
[   41.923889] Bluetooth: L2CAP ver 2.11
[   41.923908] Bluetooth: L2CAP socket layer initialized
[   41.981306] Bluetooth: SCO (Voice Link) ver 0.6
[   41.981342] Bluetooth: SCO socket layer initialized
[   42.013474] Bluetooth: RFCOMM socket layer initialized
[   42.014618] Bluetooth: RFCOMM TTY layer initialized
[   42.014654] Bluetooth: RFCOMM ver 1.10
[   42.058669] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.058690] Bluetooth: BNEP filters: protocol multicast
[   42.124494] Bridge firewalling registered
[   42.127561] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   46.401198] eth0: Media Link Off
[   75.467278] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[  146.255921] ppdev0: registered pardevice
[  146.304359] ppdev0: unregistered pardevice
[  146.410601] ppdev0: registered pardevice
[  146.461576] ppdev0: unregistered pardevice
[  147.806879] ppdev0: registered pardevice
[  147.857015] ppdev0: unregistered pardevice
[  148.232602] type=1503 audit(1238165936.285:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5001/net/" pid=5001 profile="/usr/sbin/cupsd"
[  148.381445] NET: Registered protocol family 10
[  148.387988] lo: Disabled Privacy Extensions
[  148.391389] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  148.395185] type=1503 audit(1238165936.445:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395224] type=1503 audit(1238165936.445:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395243] type=1503 audit(1238165936.445:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395261] type=1503 audit(1238165936.445:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395279] type=1503 audit(1238165936.445:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395298] type=1503 audit(1238165936.445:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395317] type=1503 audit(1238165936.445:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.395335] type=1503 audit(1238165936.445:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5001 profile="/usr/sbin/cupsd"
[  148.414091] type=1503 audit(1238165936.465:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5001/net/dev" pid=5001 profile="/usr/sbin/cupsd"
[ 1829.918672] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 1841.215889] usb 1-1: USB disconnect, address 2
[ 2444.811304] usb 1-1: new full speed USB device using ohci_hcd and address 3
[ 2445.086723] usb 1-1: configuration #1 chosen from 1 choice
[ 2445.126272] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2445.140289] usb-storage: device found at 3
[ 2445.140308] usb-storage: waiting for device to settle before scanning
[ 2450.141537] usb-storage: device scan complete
[ 2450.148632] scsi 3:0:0:0: Direct-Access     Maxtor   6L250R0          BAH4 PQ: 0 ANSI: 2
[ 2450.177426] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 2450.203922] sd 3:0:0:0: [sdb] Write Protect is off
[ 2450.203948] sd 3:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 2450.203957] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2450.233437] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 2450.246540] sd 3:0:0:0: [sdb] Write Protect is off
[ 2450.246564] sd 3:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 2450.246573] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2450.248116]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
[ 2450.296979] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 2450.298360] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 2673.063072] usb 1-1: USB disconnect, address 3
[ 3262.959296] NET: Registered protocol family 17
[ 3350.418892] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 3350.647014] usb 1-1: configuration #1 chosen from 1 choice
[ 3350.663215] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3350.667146] usb-storage: device found at 4
[ 3350.667166] usb-storage: waiting for device to settle before scanning
[ 3355.669142] usb-storage: device scan complete
[ 3355.676102] scsi 4:0:0:0: Direct-Access     Maxtor   6L250R0          BAH4 PQ: 0 ANSI: 2
[ 3355.699045] sd 4:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 3355.713035] sd 4:0:0:0: [sdb] Write Protect is off
[ 3355.713060] sd 4:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 3355.713068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3355.736377] sd 4:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 3355.753123] sd 4:0:0:0: [sdb] Write Protect is off
[ 3355.753149] sd 4:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 3355.753157] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3355.757992]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
[ 3355.804200] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3355.806493] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3417.902620] usb 1-1: USB disconnect, address 4
[ 3967.624040] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3972.622875] eth0: Media Link On 100mbps full-duplex 
[ 3978.150655] eth0: no IPv6 routers present
[ 3981.434911] usb 1-1: new full speed USB device using ohci_hcd and address 5
[ 3981.662973] usb 1-1: configuration #1 chosen from 1 choice
[ 3981.700344] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3981.704290] usb-storage: device found at 5
[ 3981.704309] usb-storage: waiting for device to settle before scanning
[ 3986.705130] usb-storage: device scan complete
[ 3986.712083] scsi 5:0:0:0: Direct-Access     Maxtor   6L250R0          BAH4 PQ: 0 ANSI: 2
[ 3986.741037] sd 5:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 3986.773945] sd 5:0:0:0: [sdb] Write Protect is off
[ 3986.773973] sd 5:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 3986.773982] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3986.795439] sd 5:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[ 3986.808081] sd 5:0:0:0: [sdb] Write Protect is off
[ 3986.808106] sd 5:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 3986.808115] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3986.809590]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
[ 3986.853789] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 3986.855258] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3991.462047] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 4063.627799] eth0: Media Link Off
[ 4133.632052] eth0: Media Link On 100mbps full-duplex 




Thanks...!!!

---

### Post by coutts99 on 2009-03-30
Can you do 'sudo dhclient eth0' when the cable is connected please

---

