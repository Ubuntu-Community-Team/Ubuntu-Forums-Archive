---
title: "PCI Wireless and ACPI issues?"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by earle79 on 2008-12-09
Computer Spec:
[I][COLOR="Red"]HP xg910
384MB RAM
Celeron 800Mhz
NO ETHERNET CARD!!!
Xubuntu 8.10 up and running, used alternate CD
[/COLOR][/I]
[I][COLOR="RoyalBlue"]Wireless Card trying to use:
Belkin F5d7000 version 7 with Realtek 8185 Chip (visually verified)
[/COLOR][/I]
For some reason or another everytime I put this card in and try to boot up, it locks and hangs up just before the login screen leaving me with a blank screen can't switch to terminal, its a solid lock up.

What i've done so far is try what I found on here about boot grub options.  I used acpi=off, lapic, nolapic I tried them seperately and all together and combos of all of them.  With the card installed i get black screen.  

I get a ACPI error message after the grub loader finishes:

00:0b: can't evaluate _CRS: 12300<6>pnp: PnP ACPI: found 14 devices

Here is dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017effc00 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000018000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x17ef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 17ef0000 @ 7000-d000
[    0.000000] RAMDISK: 17717000 - 17edfb68
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7280, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 17EFCAB8, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 17EFFB64, 0074 (r1 HP     Hawk      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 17EFCAE4, 3080 (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 17EFFFC0, 0040
[    0.000000] ACPI: BOOT 17EFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 17ef0000
[    0.000000]   low ram: 00000000 - 17ef0000
[    0.000000]   bootmap 00002000 - 00004fe0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0017ef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0017717000 - 0017edfb68]          RAMDISK ==> [0017717000 - 0017edfb68]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000005000]          BOOTMAP ==> [0000002000 - 0000005000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00017ef0
[    0.000000]   HighMem  0x00017ef0 -> 0x00017ef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00017ef0
[    0.000000] On node 0 totalpages: 97935
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 93110 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01362000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7f00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97073
[    0.000000] Kernel command line: root=UUID=4fa5ac46-a73d-4707-b11c-747267098b07 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 801.816 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 374724k/392128k available (2572k kernel code, 16800k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd8800000 - 0xff3fe000   ( 619 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004027] Calibrating delay loop (skipped), value calculated using timer frequency.. 1603.63 BogoMIPS (lpj=3207264)
[    0.004088] Security Framework initialized
[    0.004119] SELinux:  Disabled at boot.
[    0.004195] AppArmor: AppArmor initialized
[    0.004224] Mount-cache hash table entries: 512
[    0.004802] Initializing cgroup subsys ns
[    0.004825] Initializing cgroup subsys cpuacct
[    0.004833] Initializing cgroup subsys memory
[    0.004884] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004894] CPU: L2 cache: 128K
[    0.004948] Checking 'hlt' instruction... OK.
[    0.020943] SMP alternatives: switching to UP code
[    0.032097] Freeing SMP alternatives: 11k freed
[    0.032113] ACPI: Core revision 20080609
[    0.034222] ACPI: Checking initramfs for custom DSDT
[    0.915346] ACPI: setting ELCR to 0200 (from 0a00)
[    0.916239] weird, boot CPU (#0) not listedby the BIOS.
[    0.916249] SMP motherboard not detected.
[    0.916258] Local APIC not detected. Using dummy APIC emulation.
[    0.916265] SMP disabled
[    0.916566] Brought up 1 CPUs
[    0.916579] Total of 1 processors activated (1603.63 BogoMIPS).
[    0.916621] CPU0 attaching sched-domain:
[    0.916631]  domain 0: span 0 level CPU
[    0.916639]   groups: 0
[    0.917797] net_namespace: 840 bytes
[    0.917833] Booting paravirtualized kernel on bare hardware
[    0.918531] Time: 23:03:31  Date: 12/10/08
[    0.918652] NET: Registered protocol family 16
[    0.920855] EISA bus registered
[    0.920954] ACPI: bus type pci registered
[    0.922626] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[    0.922640] PCI: Using configuration type 1 for base access
[    0.930174] ACPI: EC: Look up EC in DSDT
[    0.940819] ACPI: Interpreter enabled
[    0.940840] ACPI: (supports S0 S1 S5)
[    0.940876] ACPI: Using PIC for interrupt routing
[    0.960149] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.960620] PCI: 0000:00:01.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.960636] PCI: 0000:00:01.0 reg 14 32bit mmio: [f4000000, f407ffff]
[    0.960853] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.960864] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.960922] PCI: 0000:00:1f.1 reg 20 io port: [10a0, 10af]
[    0.961002] PCI: 0000:00:1f.2 reg 20 io port: [1080, 109f]
[    0.961079] PCI: 0000:00:1f.3 reg 20 io port: [10b0, 10bf]
[    0.961134] PCI: 0000:00:1f.5 reg 10 io port: [1200, 12ff]
[    0.961148] PCI: 0000:00:1f.5 reg 14 io port: [1300, 133f]
[    0.961263] pci 0000:00:1e.0: transparent bridge
[    0.961289] bus 00 -> node 0
[    0.961327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.961500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[    0.967947] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[    0.968364] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[    0.968712] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[    0.969073] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.969906] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.970157] pnp: PnP ACPI init
[    0.970201] ACPI: bus type pnp registered
[    0.972170] pnp 00:01: io resource (0x1000-0x105f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.972186] pnp 00:01: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.981935] ACPI Error (dsopcode-0595): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20080609]
[    0.981959] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node d7014360), AE_AML_BUFFER_LIMIT
[    0.982042] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node d7014360), AE_AML_BUFFER_LIMIT
[    0.982067] pnp 00:0b: can't evaluate _CRS: 12300<6>pnp: PnP ACPI: found 14 devices
[    0.985040] ACPI: ACPI bus type pnp unregistered
[    0.985054] PnPBIOS: Disabled by ACPI PNP
[    0.987568] PCI: Using ACPI for IRQ routing
[    0.988169] NET: Registered protocol family 8
[    0.988169] NET: Registered protocol family 20
[    0.988400] NetLabel: Initializing
[    0.988409] NetLabel:  domain hash size = 128
[    0.988414] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.988488] NetLabel:  unlabeled traffic allowed by default
[    0.989357] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.989365]    actual entries 65620
[    0.990154] AppArmor: AppArmor Filesystem Enabled
[    0.990350] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.990350] system 00:01: ioport range 0x1c00-0x1c7f has been reserved
[    0.990350] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.990350] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.990350] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[    1.029267] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.029279] pci 0000:00:1e.0:   IO window: disabled
[    1.029292] pci 0000:00:1e.0:   MEM window: disabled
[    1.029301] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.029336] pci 0000:00:1e.0: setting latency timer to 64
[    1.029347] bus: 00 index 0 io port: [0, ffff]
[    1.029354] bus: 00 index 1 mmio: [0, ffffffff]
[    1.029360] bus: 01 index 0 mmio: [0, 0]
[    1.029366] bus: 01 index 1 mmio: [0, 0]
[    1.029372] bus: 01 index 2 mmio: [0, 0]
[    1.029378] bus: 01 index 3 io port: [0, ffff]
[    1.029384] bus: 01 index 4 mmio: [0, ffffffff]
[    1.029427] NET: Registered protocol family 2
[    1.029988] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.030841] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.031355] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.032178] TCP: Hash tables configured (established 16384 bind 16384)
[    1.032197] TCP reno registered
[    1.032731] NET: Registered protocol family 1
[    1.033227] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.907382]  it is
[    3.098016] Freeing initrd memory: 7970k freed
[    3.098910] Simple Boot Flag at 0x36 set to 0x1
[    3.101521] audit: initializing netlink socket (disabled)
[    3.101576] type=2000 audit(1228950212.100:1): initialized
[    3.118539] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.133566] VFS: Disk quotas dquot_6.5.1
[    3.134123] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.134716] msgmni has been set to 747
[    3.135449] io scheduler noop registered
[    3.135463] io scheduler anticipatory registered
[    3.135470] io scheduler deadline registered
[    3.135560] io scheduler cfq registered (default)
[    3.135606] pci 0000:00:01.0: Boot video device
[    3.137706] isapnp: Scanning for PnP cards...
[    3.491663] isapnp: No Plug & Play device found
[    3.896006] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.896579] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.897601] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.902223] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.904522] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.917099] brd: module loaded
[    3.917503] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.918243] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.922681] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.922714] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.925463] mice: PS/2 mouse device common for all mice
[    3.926591] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.926676] rtc0: alarms up to one month, y3k
[    3.927503] EISA: Probing bus 0 at eisa.0
[    3.927530] Cannot allocate resource for EISA slot 1
[    3.927575] EISA: Detected 0 cards.
[    3.927586] cpuidle: using governor ladder
[    3.927594] cpuidle: using governor menu
[    3.929804] TCP cubic registered
[    3.929943] Using IPI No-Shortcut mode
[    3.932114] registered taskstats version 1
[    3.932403]   Magic number: 4:741:99
[    3.932818] rtc_cmos 00:04: setting system clock to 2008-12-10 23:03:34 UTC (1228950214)
[    3.932831] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.932838] EDD information not available.
[    3.934795] Freeing unused kernel memory: 424k freed
[    3.935071] Write protecting the kernel text: 2576k
[    3.935185] Write protecting the kernel read-only data: 936k
[    3.951269] input: AT Raw Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    4.521908] fuse init (API version 7.9)
[    4.863734] ACPI: Invalid PBLK length [5]
[    4.868198] processor ACPI0007:00: registered as cooling_device0
[    6.165502] No dock devices found.
[    6.820337] SCSI subsystem initialized
[    7.089387] usbcore: registered new interface driver usbfs
[    7.089471] usbcore: registered new interface driver hub
[    7.089750] usbcore: registered new device driver usb
[    7.217696] USB Universal Host Controller Interface driver v3.0
[    7.218431] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    7.218445] PCI: setting IRQ 11 as level-triggered
[    7.218457] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    7.218483] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    7.218493] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    7.218687] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    7.218746] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001080
[    7.219380] usb usb1: configuration #1 chosen from 1 choice
[    7.219496] hub 1-0:1.0: USB hub found
[    7.219539] hub 1-0:1.0: 2 ports detected
[    7.224777] libata version 3.00 loaded.
[    7.425304] pata_acpi 0000:00:1f.1: power state changed by ACPI to D0
[    7.425461] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    7.443652] ata_piix 0000:00:1f.1: version 2.12
[    7.443716] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    7.443878] ata_piix 0000:00:1f.1: setting latency timer to 64
[    7.445483] scsi0 : ata_piix
[    7.446095] scsi1 : ata_piix
[    7.446307] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
[    7.446318] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
[    7.552266] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    7.609002] ata1.00: ATA-5: QUANTUM FIREBALLlct20 20, APL.0900, max UDMA/100
[    7.609016] ata1.00: 39876480 sectors, multi 8: LBA 
[    7.624945] ata1.00: configured for UDMA/66
[    7.727425] usb 1-1: configuration #1 chosen from 1 choice
[    7.788520] ata2.00: ATAPI: LG      CD-ROM CRD-8485B, 1.00, max MWDMA2
[    7.796452] ata2.00: configured for MWDMA2
[    7.796929] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
[    7.797758] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8485B 1.00 PQ: 0 ANSI: 5
[    9.777719] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    9.777993] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    9.835008] usbcore: registered new interface driver libusual
[    9.889470] Initializing USB Mass Storage driver...
[    9.902006] scsi2 : SCSI emulation for USB Mass Storage devices
[    9.911699] usbcore: registered new interface driver usb-storage
[    9.911718] USB Mass Storage support registered.
[    9.911742] usb-storage: device found at 2
[    9.911749] usb-storage: waiting for device to settle before scanning
[    9.952750] Driver 'sd' needs updating - please use bus_type methods
[    9.953239] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[    9.953342] sd 0:0:0:0: [sda] Write Protect is off
[    9.953354] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.953499] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.953832] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[    9.953911] sd 0:0:0:0: [sda] Write Protect is off
[    9.953923] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.954053] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.954075]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   10.000587]  sda5 >
[   10.001151] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.022129] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   10.022146] Uniform CD-ROM driver Revision: 3.20
[   10.022497] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   10.852423] PM: Starting manual resume from disk
[   10.852443] PM: Resume from partition 8:5
[   10.852449] PM: Checking hibernation image.
[   10.853028] PM: Resume from disk failed.
[   10.996863] kjournald starting.  Commit interval 5 seconds
[   10.996921] EXT3-fs: mounted filesystem with ordered data mode.
[   14.909833] usb-storage: device scan complete
[   14.912923] scsi 2:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[   14.924688] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   14.927667] sd 2:0:0:0: [sdb] Write Protect is off
[   14.927687] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   14.927695] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   14.939701] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   14.942663] sd 2:0:0:0: [sdb] Write Protect is off
[   14.942684] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   14.942692] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   14.942781]  sdb: sdb1
[   14.995176] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   14.995778] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   22.057517] udevd version 124 started
[   24.588711] Linux agpgart interface v0.103
[   24.670493] intel_rng: FWH not detected
[   24.745432] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.854128] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.990794] agpgart-intel 0000:00:00.0: Intel i810 Chipset
[   25.038994] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   25.055583] iTCO_vendor_support: vendor-support=0
[   25.177784] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   25.183999] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   25.184143] iTCO_wdt: No card detected
[   25.518622] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.961507] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   25.972221] ACPI: Power Button (FF) [PWRF]
[   25.972793] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   25.988158] ACPI: Power Button (CM) [PWRB]
[   28.527556] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   30.795103] parport_pc 00:0b: disabled
[   30.795129] parport_pc: probe of 00:0b failed with error -22
[   32.608857] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   32.608872] PCI: setting IRQ 9 as level-triggered
[   32.608884] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[   32.608941] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   33.200158] intel8x0_measure_ac97_clock: measured 54929 usecs
[   33.200172] intel8x0: clocking to 48000
[   38.030231] loop: module loaded
[   38.136216] lp: driver loaded but no devices found
[   38.687401] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   39.461409] EXT3 FS on sda1, internal journal
[   41.347231] type=1505 audit(1228950251.616:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3621
[   41.348799] type=1505 audit(1228950251.620:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3621
[   41.679031] ip_tables: (C) 2000-2006 Netfilter Core Team


```

I really don't know where to start, on this kindof error.  If anyone could point me in the right direction, I will try it.

*[COLOR="Red"]Something to keep in mind with solutions if I have to download something, please remember I have to transfer via USB drive, this old thing don't have a Network card on it.[/COLOR]*

Thank you in advance for you time and help.

---

### Post by earle79 on 2008-12-10
can anybody help???

---

### Post by earle79 on 2008-12-10
open to suggestions, any advice is welcome?

---

### Post by earle79 on 2008-12-10
i used this and code:
```
pnpacpi=off
```
in grub bootloader and I don't recieve the ACPI PNP errors anymore.

Now i will try it with the PCI card installed.

Also in dmesg it says:
```
Local APIC disabled by BIOS -- you can enable it with "lapic"
```

should I use APIC?? will it improve any system performance?

---

### Post by earle79 on 2008-12-10
Well that didn't work either.  How can I get my pci slots to work?  What am I doing wrong.

---

### Post by spcwingo on 2008-12-11
Have you tried pci=noacpi?

---

### Post by earle79 on 2008-12-11
> **spcwingo said:**
> Have you tried pci=noacpi?

[/QUOTE]

yes i did, and i don't get the errors, but still can't boot with the pci card installed.  i also tried a modem card, as well but no go.

---

### Post by spcwingo on 2008-12-11
Well, that's above my head, but hopefully someone with more experience with this issue will chime in.

---

### Post by earle79 on 2008-12-11
ok, well thank you for replying.  I am just really getting frustrated, cause I can't get it to work, and don't know why.

---

### Post by harpoonz on 2008-12-11
Hey Earle, I'm the guy with the same problem as you.  I just posted in my thread but I'll give you an update.  

I did boot up the Ultimate Boot CD and ran some diagnostics on my motherboard.  The PCI diagnostic gave me a "BUS ACCESS DISABLED!!" error.  So it does seem like a hardware issue, however I am having no trouble booting into XP with wireless access when I swap out drives. This is definitely getting a bit frustrating.

---

### Post by earle79 on 2008-12-13
well i just switched to a dlink card and it works with ndiswrapper so i will just use that one for now until i can figure out whats up with the belkin.

---

