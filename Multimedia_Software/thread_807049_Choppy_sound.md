---
title: "Choppy sound"
date: 2008-05-25
forum: Multimedia Software
---

### Post by jwhal on 2008-05-25
Hi there. Running Hardy Heron. Have and older pc, AMD Duron 650 (or 600), 440mb's RAM. Runs half decent. Was having a problem with sound chopping every three seconds or so - changed System > Pref's > Sound settings from Autodect to use the alsa drivers. That fixed the intial choppiness. However, whenever I move a window, minimize/maximize, open/close, browse through the menu, the sound cuts out. Never had that problem on Windows (apples and oranges I know), but I'm wondering if there's anything I can do to fix that? Obviously a better computer would fix the problem, but cash is an issue at the moment.

I guess I should clarify a bit more. The sound doesn't cut out completely when performing basic windowing-tasks (moving windows, resizing windows, opening or closing windows/menus, etc...), it get's choppy - as though the operation is interfering with audio play-back. What I was saying about Windows, is that I could perform heavier operations and the sound always worked fine. Throw in Ubuntu (or Kubuntu for that matter) and the sound get's chopped up. So perhaps this system just isn't powerful enough for Ubuntu? OpenBSD works fine btw. No issues there.

Here's my dmesg:
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bff8000 - 000000001c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114672
[    0.000000]   HighMem    114672 ->   114672
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114672
[    0.000000] On node 0 totalpages: 114672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109713 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA9E0 checksum 0
[    0.000000] ACPI: RSDP 000FA9E0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1BFF0000, 0028 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: FACP 1BFF0030, 0074 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: DSDT 1BFF00B0, 293A (r1    VIA   VT8371     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1BFF8000, 0040
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3ff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ec000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ec000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113777
[    0.000000] Kernel command line: root=UUID=d63850f1-59be-4f5c-b9df-2c5bc843c6fd ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0138d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 650.041 MHz processor.
[   38.457597] Console: colour VGA+ 80x25
[   38.457607] console [tty0] enabled
[   38.458643] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   38.460261] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   38.499762] Memory: 442404k/458688k available (2157k kernel code, 15748k reserved, 998k data, 364k init, 0k highmem)
[   38.499788] virtual kernel memory layout:
[   38.499792]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   38.499796]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   38.499800]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   38.499804]     lowmem  : 0xc0000000 - 0xdbff0000   ( 447 MB)
[   38.499808]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   38.499811]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   38.499815]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   38.499827] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   38.499937] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   38.579968] Calibrating delay using timer specific routine.. 1301.95 BogoMIPS (lpj=2603902)
[   38.580050] Security Framework initialized
[   38.580068] SELinux:  Disabled at boot.
[   38.580122] AppArmor: AppArmor initialized
[   38.580135] Failure registering capabilities with primary security module.
[   38.580162] Mount-cache hash table entries: 512
[   38.580521] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   38.580553] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.580563] CPU: L2 Cache: 64K (64 bytes/line)
[   38.580571] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   38.580604] Compat vDSO mapped to ffffe000.
[   38.580640] Checking 'hlt' instruction... OK.
[   38.596066] SMP alternatives: switching to UP code
[   38.599159] Freeing SMP alternatives: 11k freed
[   38.599541] Early unpacking initramfs... done
[   39.670768] CPU0: AMD Duron(tm) Processor  stepping 00
[   39.670787] SMP motherboard not detected.
[   39.670795] Local APIC not detected. Using dummy APIC emulation.
[   39.670935] Brought up 1 CPUs
[   39.671005] CPU0 attaching sched-domain:
[   39.671014]  domain 0: span 01
[   39.671019]   groups: 01
[   39.671635] net_namespace: 64 bytes
[   39.671664] Booting paravirtualized kernel on bare hardware
[   39.673227] Time: 22:42:54  Date: 05/24/08
[   39.673330] NET: Registered protocol family 16
[   39.674032] EISA bus registered
[   39.699163] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[   39.699175] PCI: Using configuration type 1
[   39.699181] Setting up standard PCI resources
[   39.712335] ACPI: Interpreter disabled.
[   39.712351] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.712454] pnp: PnP ACPI: disabled
[   39.712466] PnPBIOS: Scanning system for PnP BIOS support...
[   39.712551] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7640
[   39.712560] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x64d4, dseg 0xf0000
[   39.714522] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   39.715288] PCI: Probing PCI hardware
[   39.715334] PCI: Probing PCI hardware (bus 00)
[   39.715963] PCI quirk: region 0800-08ff claimed by vt82c586 ACPI
[   39.715976] PCI quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[   39.715985] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[   39.717929] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   39.724090] NET: Registered protocol family 8
[   39.724101] NET: Registered protocol family 20
[   39.724417] AppArmor: AppArmor Filesystem Enabled
[   39.724567] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   39.724578] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   39.724588] system 00:00: iomem range 0xec000-0xeffff has been reserved
[   39.724597] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   39.724606] system 00:00: iomem range 0x100000-0x1bfeffff could not be reserved
[   39.724615] system 00:00: iomem range 0x1bff0000-0x1bff7fff could not be reserved
[   39.724624] system 00:00: iomem range 0x1bff8000-0x1bffffff could not be reserved
[   39.724634] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   39.725965] PCI: Bridge: 0000:00:01.0
[   39.725977]   IO window: 9000-9fff
[   39.725988]   MEM window: dde00000-dfefffff
[   39.725996]   PREFETCH window: cdc00000-ddcfffff
[   39.726022] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   39.726069] NET: Registered protocol family 2
[   39.727803] Time: tsc clocksource has been installed.
[   39.760072] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   39.760807] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   39.761505] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   39.762240] TCP: Hash tables configured (established 16384 bind 16384)
[   39.762251] TCP reno registered
[   39.772238] checking if image is initramfs... it is
[   41.792990] Freeing initrd memory: 7649k freed
[   41.794807] audit: initializing netlink socket (disabled)
[   41.794851] audit(1211668976.296:1): initialized
[   41.800997] VFS: Disk quotas dquot_6.5.1
[   41.801283] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   41.801987] io scheduler noop registered
[   41.801999] io scheduler anticipatory registered
[   41.802005] io scheduler deadline registered
[   41.802047] io scheduler cfq registered (default)
[   41.802089] PCI: VIA PCI bridge detected. Disabling DAC.
[   41.802099] PCI: Disabling Via external APIC routing
[   41.802151] Boot video device is 0000:01:00.0
[   41.802912] isapnp: Scanning for PnP cards...
[   42.157773] isapnp: No Plug & Play device found
[   42.312905] Real Time Clock Driver v1.12ac
[   42.313140] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.313447] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.314001] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.316079] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.317182] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.317847] PCI: setting IRQ 10 as level-triggered
[   42.317860] PCI: Found IRQ 10 for device 0000:00:0a.0
[   42.317880] PCI: Sharing IRQ 10 with 0000:00:07.5
[   42.318585] 0000:00:0a.0: ttyS2 at I/O 0xc400 (irq = 10) is a 16550A
[   42.321143] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.321384] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   42.321728] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   42.322312] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.322327] serio: i8042 AUX port at 0x60,0x64 irq 12
[   42.335791] mice: PS/2 mouse device common for all mice
[   42.336194] EISA: Probing bus 0 at eisa.0
[   42.336271] EISA: Detected 0 cards.
[   42.336281] cpuidle: using governor ladder
[   42.336288] cpuidle: using governor menu
[   42.336773] NET: Registered protocol family 1
[   42.336869] Using IPI No-Shortcut mode
[   42.336984] registered taskstats version 1
[   42.337179]   Magic number: 8:815:755
[   42.337523] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   42.337529] EDD information not available.
[   42.338929] Freeing unused kernel memory: 364k freed
[   42.365385] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   44.190856] fuse init (API version 7.9)
[   44.305482] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   45.388966] SCSI subsystem initialized
[   45.444428] usbcore: registered new interface driver usbfs
[   45.444501] usbcore: registered new interface driver hub
[   45.503067] usbcore: registered new device driver usb
[   45.521538] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   45.521665] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   45.521678] 8139cp 0000:00:09.0: Try the "8139too" driver instead.
[   45.637241] USB Universal Host Controller Interface driver v3.0
[   45.637473] PCI: setting IRQ 9 as level-triggered
[   45.637483] PCI: Found IRQ 9 for device 0000:00:07.2
[   45.637499] PCI: Sharing IRQ 9 with 0000:00:07.3
[   45.637536] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   45.638316] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   45.638375] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000cc00
[   45.638801] usb usb1: configuration #1 chosen from 1 choice
[   45.638873] hub 1-0:1.0: USB hub found
[   45.638946] hub 1-0:1.0: 2 ports detected
[   45.695033] 8139too Fast Ethernet driver 0.9.28
[   45.714928] libata version 3.00 loaded.
[   45.743281] PCI: Found IRQ 9 for device 0000:00:07.3
[   45.743305] PCI: Sharing IRQ 9 with 0000:00:07.2
[   45.743342] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   45.743416] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   45.743461] uhci_hcd 0000:00:07.3: irq 9, io base 0x0000d000
[   45.743818] usb usb2: configuration #1 chosen from 1 choice
[   45.743891] hub 2-0:1.0: USB hub found
[   45.743910] hub 2-0:1.0: 2 ports detected
[   45.847573] PCI: setting IRQ 5 as level-triggered
[   45.847588] PCI: Found IRQ 5 for device 0000:00:09.0
[   45.848567] eth0: RealTek RTL8139 at 0xc800, 00:50:ba:84:f0:58, IRQ 5
[   45.848576] eth0:  Identified 8139 chip type 'RTL-8139B'
[   45.939089] pata_via 0000:00:07.1: version 0.3.3
[   45.978893] scsi0 : pata_via
[   46.010937] scsi1 : pata_via
[   46.011132] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   46.011141] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   46.054623] Floppy drive(s): fd0 is 1.44M
[   46.074825] FDC 0 is a post-1991 82077
[   46.239497] ata1.00: ATA-7: Maxtor 2B020H1, WAK21R90, max UDMA/100
[   46.239513] ata1.00: 39876480 sectors, multi 16: LBA48 
[   46.239805] ata1.01: ATA-6: ST3120026A, 3.16, max UDMA/100
[   46.239814] ata1.01: 234375000 sectors, multi 16: LBA48 
[   46.255429] ata1.00: configured for UDMA/66
[   46.271405] ata1.01: configured for UDMA/66
[   46.615231] ata2.00: ATAPI: PIONEER DVD-RW  DVR-112D, 1.24, max UDMA/33
[   46.615721] ata2.01: ATA-5: ST340016A, 3.75, max UDMA/100
[   46.615733] ata2.01: 78165360 sectors, multi 16: LBA 
[   46.615773] ata2.01: limited to UDMA/33 due to 40-wire cable
[   46.787134] ata2.00: configured for UDMA/33
[   46.804407] ata2.01: configured for UDMA/33
[   46.804782] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2B020H1   WAK2 PQ: 0 ANSI: 5
[   46.805106] scsi 0:0:1:0: Direct-Access     ATA      ST3120026A       3.16 PQ: 0 ANSI: 5
[   46.811680] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.24 PQ: 0 ANSI: 5
[   46.812133] scsi 1:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[   48.159771] Driver 'sd' needs updating - please use bus_type methods
[   48.160464] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   48.160510] sd 0:0:0:0: [sda] Write Protect is off
[   48.160519] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.160575] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.160737] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   48.160768] sd 0:0:0:0: [sda] Write Protect is off
[   48.160776] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.160826] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.160843]  sda: sda1 sda2
[   48.185812] Driver 'sr' needs updating - please use bus_type methods
[   48.204138] sd 0:0:0:0: [sda] Attached SCSI disk
[   48.204355] sd 0:0:1:0: [sdb] 234375000 512-byte hardware sectors (120000 MB)
[   48.204397] sd 0:0:1:0: [sdb] Write Protect is off
[   48.204406] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   48.204463] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.204600] sd 0:0:1:0: [sdb] 234375000 512-byte hardware sectors (120000 MB)
[   48.204634] sd 0:0:1:0: [sdb] Write Protect is off
[   48.204642] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   48.204694] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.204707]  sdb: sdb1
[   48.216853] sd 0:0:1:0: [sdb] Attached SCSI disk
[   48.217086] sd 1:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
[   48.217128] sd 1:0:1:0: [sdc] Write Protect is off
[   48.217136] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   48.217192] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.217326] sd 1:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
[   48.217358] sd 1:0:1:0: [sdc] Write Protect is off
[   48.217366] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   48.217417] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.217430]  sdc: sdc4
[   48.240956] sd 1:0:1:0: [sdc] Attached SCSI disk
[   48.281986] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   48.282048] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   48.282128] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   48.282182] sd 1:0:1:0: Attached scsi generic sg3 type 0
[   48.284926] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   48.284945] Uniform CD-ROM driver Revision: 3.20
[   48.285124] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   49.053430] Attempting manual resume
[   49.053445] swsusp: Resume From Partition 8:2
[   49.053450] PM: Checking swsusp image.
[   49.053951] PM: Resume from disk failed.
[   62.645295] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.745694] parport_pc: VIA 686A/8231 detected
[   62.745707] parport_pc: probing current configuration
[   62.745734] parport_pc: Current parallel port base: 0x378
[   62.745842] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   62.832506] parport_pc: VIA parallel port: io=0x378, irq=7
[   62.860117] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.932409] Linux agpgart interface v0.102
[   62.980876] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   62.996558] agpgart: AGP aperture is 64M @ 0xe0000000
[   63.652733] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   64.815018] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   66.628575] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   66.813710] NET: Registered protocol family 10
[   66.814404] lo: Disabled Privacy Extensions
[   68.747367] PCI: Found IRQ 10 for device 0000:00:07.5
[   68.747443] PCI: Sharing IRQ 10 with 0000:00:0a.0
[   68.747606] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   73.484944] lp0: using parport0 (interrupt-driven).
[   73.662783] Adding 2016148k swap on /dev/sda2.  Priority:-1 extents:1 across:2016148k
[   76.588971] ip_tables: (C) 2000-2006 Netfilter Core Team
[   77.330142] eth0: no IPv6 routers present
[   78.242411] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   78.242599] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   78.242889] powernow_k7: Unknown symbol acpi_processor_register_performance
[   78.330214] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   78.330400] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   78.330864] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   78.331098] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   80.174830] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   80.784765] ppdev: user-space parallel port driver
[   80.809594] Clocksource tsc unstable (delta = 144027387 ns)
[   80.813595] Time: pit clocksource has been installed.
[   81.388167] audit(1211669016.175:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4554 profile="/usr/sbin/cupsd" namespace="default"
[   84.019046] Bluetooth: Core ver 2.11
[   84.021709] NET: Registered protocol family 31
[   84.021724] Bluetooth: HCI device and connection manager initialized
[   84.021738] Bluetooth: HCI socket layer initialized
[   84.121559] Bluetooth: L2CAP ver 2.9
[   84.121576] Bluetooth: L2CAP socket layer initialized
[   84.273108] Bluetooth: RFCOMM socket layer initialized
[   84.274801] Bluetooth: RFCOMM TTY layer initialized
[   84.274818] Bluetooth: RFCOMM ver 1.8
[21522.868817] sp-sc[5718]: segfault at 000b181a eip 0805be6e esp b7cbd2c0 error 4
[30336.477123] sp-sc[6692]: segfault at 000b181a eip 0805be6e esp b7d262c0 error 4
[31884.417526] UDP: bad checksum. From 125.95.59.86:34462 to 192.168.2.100:26760 ulen 468
[32234.149658] sp-sc[7278]: segfault at 000b181a eip 0805be6e esp b7ca62c0 error 4
[34598.163272] sp-sc[8019]: segfault at 000b181a eip 0805be6e esp b7ca72c0 error 4
[41515.107429] sp-sc[10127]: segfault at 000b181a eip 0805be6e esp b7d362c0 error 4
[41911.564077] sp-sc[10255]: segfault at 000b181a eip 0805be6e esp b7c882c0 error 4

Here's my lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

Not sure what other info would be helpful...

Thanks,

Jon

---

