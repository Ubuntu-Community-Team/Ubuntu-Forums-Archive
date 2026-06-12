---
title: "Audio Problems with dvd, iso and recordings"
date: 2008-07-07
forum: Mythbuntu
---

### Post by mark467 on 2008-07-07
My audio for dvd's, iso, and redordings seems almost fast (sounds high pitched but matches the video) Mp3's play fine. If someone could tell me where to look for problems it would be much appreciated. It was working great for weeks with no changes. It started in the middle of a movie.

Ok here is more info, i tried adjusting the timing and it just slows the video and audio down but the pitch is still high. Has nobody run into anything like this?

---

### Post by forger on 2008-07-07
need more info :)
1) what version/release of mythbuntu?
2) what architecture? i386 or amd64?
3) do you have all the related plugins installed? I'm not sure how mythbuntu handles the restricted codecs, but have you installed the [medibuntu]("http://www.medibuntu.org") repository? Did you install the following packages: **libdvdread3 libdvdcss2 w32codecs** (or w64codecs for amd64?)

---

### Post by mark467 on 2008-07-07
1)  Installed: 0.21.0+fixes16838-0ubuntu3.1
  Candidate: 0.21.0+fixes16838-0ubuntu3.1
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Ubuntu 8.04


2) i386  (p4 2.8 ht)

3) yes installed the prop. codecs  w32codecs  libdvdcss2  ffmpeg
medibuntu? when i searched that package name I came up with a big list of packages? Which one?

It worked fine for about a month and freaked out in the middle of a movie....

here is dmesg if it helps


 dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4d80
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6DC0 checksum 0
[    0.000000] ACPI: RSDP 000F6DC0, 0014 (r0 P4M800)
[    0.000000] ACPI: RSDT 3FFF3040, 002C (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF30C0, 0074 (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF3180, 53AC (r1 P4M800 AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF8580, 0068 (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=5f287288-9b68-416b-9bbb-be6bb0c24388 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2533.571 MHz processor.
[   22.445385] Console: colour VGA+ 80x25
[   22.445390] console [tty0] enabled
[   22.446075] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.446778] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.483605] Memory: 1027232k/1048512k available (2177k kernel code, 20592k reserved, 1006k data, 368k init, 131008k highmem)
[   22.483617] virtual kernel memory layout:
[   22.483618]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.483619]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.483620]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.483622]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.483623]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.483624]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   22.483625]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   22.483628] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.483687] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.563685] Calibrating delay using timer specific routine.. 5073.65 BogoMIPS (lpj=10147301)
[   22.563719] Security Framework initialized
[   22.563730] SELinux:  Disabled at boot.
[   22.563749] AppArmor: AppArmor initialized
[   22.563755] Failure registering capabilities with primary security module.
[   22.563766] Mount-cache hash table entries: 512
[   22.563939] Initializing cgroup subsys ns
[   22.563945] Initializing cgroup subsys cpuacct
[   22.563959] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   22.563975] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   22.563978] CPU: L2 cache: 512K
[   22.563981] CPU: Hyper-Threading is disabled
[   22.563984] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   22.563998] Compat vDSO mapped to ffffe000.
[   22.564016] Checking 'hlt' instruction... OK.
[   22.580142] SMP alternatives: switching to UP code
[   22.581918] Freeing SMP alternatives: 11k freed
[   22.582062] Early unpacking initramfs... done
[   22.923255] ACPI: Core revision 20070126
[   22.923322] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.927277] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
[   22.927324] Total of 1 processors activated (5073.65 BogoMIPS).
[   22.928092] ENABLING IO-APIC IRQs
[   22.928420] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.075533] Brought up 1 CPUs
[   23.075594] CPU0 attaching sched-domain:
[   23.075598]  domain 0: span 01
[   23.075600]   groups: 01
[   23.075825] net_namespace: 64 bytes
[   23.075838] Booting paravirtualized kernel on bare hardware
[   23.076454] Time: 21:33:17  Date: 07/07/08
[   23.076487] NET: Registered protocol family 16
[   23.076738] EISA bus registered
[   23.076775] ACPI: bus type pci registered
[   23.084303] PCI: PCI BIOS revision 2.10 entry at 0xfb3d0, last bus=1
[   23.084305] PCI: Using configuration type 1
[   23.084329] Setting up standard PCI resources
[   23.093286] ACPI: EC: Look up EC in DSDT
[   23.099504] ACPI: Interpreter enabled
[   23.099509] ACPI: (supports S0 S1 S4 S5)
[   23.099526] ACPI: Using IOAPIC for interrupt routing
[   23.106963] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.108207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.153514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   23.153702] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   23.153890] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   23.154060] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.154226] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.154384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.154542] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.154699] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.154900] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   23.155082] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   23.155262] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   23.155482] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   23.155622] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.155663] pnp: PnP ACPI init
[   23.155673] ACPI: bus type pnp registered
[   23.160193] pnp: PnP ACPI: found 13 devices
[   23.160197] ACPI: ACPI bus type pnp unregistered
[   23.160202] PnPBIOS: Disabled by ACPI PNP
[   23.160500] PCI: Using ACPI for IRQ routing
[   23.160504] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.183444] NET: Registered protocol family 8
[   23.183446] NET: Registered protocol family 20
[   23.183533] AppArmor: AppArmor Filesystem Enabled
[   23.187433] Time: tsc clocksource has been installed.
[   23.195478] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   23.195482] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   23.195485] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   23.195488] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   23.195491] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   23.195495] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   23.195497] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   23.195500] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[   23.195503] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   23.195507] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.195510] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
[   23.195518] system 00:02: ioport range 0x400-0x47f has been reserved
[   23.195521] system 00:02: ioport range 0x500-0x50f has been reserved
[   23.195528] system 00:03: ioport range 0xb78-0xb7b has been reserved
[   23.195531] system 00:03: ioport range 0xf78-0xf7b has been reserved
[   23.195534] system 00:03: ioport range 0xa78-0xa7b has been reserved
[   23.195537] system 00:03: ioport range 0xe78-0xe7b has been reserved
[   23.195539] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[   23.195542] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[   23.195545] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   23.195547] system 00:03: ioport range 0x290-0x297 has been reserved
[   23.226064] PCI: Bridge: 0000:00:01.0
[   23.226067]   IO window: disabled.
[   23.226073]   MEM window: f8000000-f9ffffff
[   23.226077]   PREFETCH window: f0000000-f7ffffff
[   23.226097] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.226111] NET: Registered protocol family 2
[   23.263505] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.263909] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.264982] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.265629] TCP: Hash tables configured (established 131072 bind 65536)
[   23.265634] TCP reno registered
[   23.275606] checking if image is initramfs... it is
[   23.727212] Switched to high resolution mode on CPU 0
[   23.940422] Freeing initrd memory: 7458k freed
[   23.941093] audit: initializing netlink socket (disabled)
[   23.941110] audit(1215466397.352:1): initialized
[   23.941335] highmem bounce pool size: 64 pages
[   23.943604] VFS: Disk quotas dquot_6.5.1
[   23.943701] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.943868] io scheduler noop registered
[   23.943871] io scheduler anticipatory registered
[   23.943873] io scheduler deadline registered
[   23.943886] io scheduler cfq registered (default)
[   23.943902] PCI: VIA PCI bridge detected. Disabling DAC.
[   23.943972] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   23.943995] Boot video device is 0000:01:00.0
[   23.944330] isapnp: Scanning for PnP cards...
[   24.298536] isapnp: No Plug & Play device found
[   24.333926] Real Time Clock Driver v1.12ac
[   24.334045] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.334176] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.334338] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.335134] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.335526] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.336514] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.336596] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.336726] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.337141] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.337147] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.339188] mice: PS/2 mouse device common for all mice
[   24.339357] EISA: Probing bus 0 at eisa.0
[   24.339397] EISA: Detected 0 cards.
[   24.339400] cpuidle: using governor ladder
[   24.339402] cpuidle: using governor menu
[   24.339513] NET: Registered protocol family 1
[   24.339549] Using IPI No-Shortcut mode
[   24.339589] registered taskstats version 1
[   24.339700]   Magic number: 0:788:600
[   24.339766]   hash matches device ptyd4
[   24.339855] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.339857] EDD information not available.
[   24.340270] Freeing unused kernel memory: 368k freed
[   24.366892] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.594299] fuse init (API version 7.9)
[   25.612112] ACPI: Fan [FAN] (on)
[   25.618955] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.620930] ACPI: Thermal Zone [THRM] (32 C)
[   26.346849] SCSI subsystem initialized
[   26.429903] libata version 3.00 loaded.
[   26.445977] usbcore: registered new interface driver usbfs
[   26.446010] usbcore: registered new interface driver hub
[   26.455863] sata_via 0000:00:0f.0: version 2.3
[   26.456155] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   26.456164] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.456216] sata_via 0000:00:0f.0: routed to hard irq line 11
[   26.464124] usbcore: registered new device driver usb
[   26.486407] scsi0 : sata_via
[   26.494479] USB Universal Host Controller Interface driver v3.0
[   26.505782] scsi1 : sata_via
[   26.507387] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe400 irq 16
[   26.507391] ata2: SATA max UDMA/133 cmd 0xe200 ctl 0xe300 bmdma 0xe408 irq 16
[   26.541237] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   26.541246] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   26.709781] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.921657] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.932535] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.932598] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   26.935283] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   26.935293] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   26.935306] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   26.935711] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   26.935750] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e700
[   26.935930] usb usb1: configuration #1 chosen from 1 choice
[   26.935959] hub 1-0:1.0: USB hub found
[   26.935966] hub 1-0:1.0: 2 ports detected
[   27.037772] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.037789] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.037819] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.037844] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000e800
[   27.037984] usb usb2: configuration #1 chosen from 1 choice
[   27.038013] hub 2-0:1.0: USB hub found
[   27.038020] hub 2-0:1.0: 2 ports detected
[   27.141676] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.141693] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.141727] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.141752] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000e900
[   27.141879] usb usb3: configuration #1 chosen from 1 choice
[   27.141907] hub 3-0:1.0: USB hub found
[   27.141916] hub 3-0:1.0: 2 ports detected
[   27.245635] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.245653] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   27.245684] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.245710] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000ea00
[   27.245840] usb usb4: configuration #1 chosen from 1 choice
[   27.245868] hub 4-0:1.0: USB hub found
[   27.245876] hub 4-0:1.0: 2 ports detected
[   27.349698] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.349718] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   27.349750] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   27.349797] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfb000000
[   27.361474] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.361642] usb usb5: configuration #1 chosen from 1 choice
[   27.361674] hub 5-0:1.0: USB hub found
[   27.361683] hub 5-0:1.0: 8 ports detected
[   27.465886] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   27.465897] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   27.466218] eth0: VIA Rhine II at 0xfb001000, 00:16:17:11:db:95, IRQ 18.
[   27.466929] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   27.467055] pata_via 0000:00:0f.1: version 0.3.3
[   27.467077] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   27.468559] scsi2 : pata_via
[   27.469456] scsi3 : pata_via
[   27.471108] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe600 irq 14
[   27.471111] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe608 irq 15
[   27.676934] ata3.00: ATA-7: MAXTOR STM3500630A, 3.AAE, max UDMA/100
[   27.676939] ata3.00: 976773168 sectors, multi 16: LBA48 
[   27.743530] ata3.00: configured for UDMA/100
[   28.077413] ata4.00: ATAPI: SONY    DVD RW DRU-190A, 1.64, max UDMA/66
[   28.265200] ata4.00: configured for UDMA/66
[   28.265350] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
[   28.266922] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-190A  1.64 PQ: 0 ANSI: 5
[   28.282738] Driver 'sd' needs updating - please use bus_type methods
[   28.282848] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.282865] sd 2:0:0:0: [sda] Write Protect is off
[   28.282869] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.282893] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.282952] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.282966] sd 2:0:0:0: [sda] Write Protect is off
[   28.282969] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.282991] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.282996]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.299236]  sda1 sda2 <<6>usb 5-7: new high speed USB device using ehci_hcd and address 2
[   28.319757]  sda5 >
[   28.319880] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.327975] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   28.327999] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   28.333978] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.333986] Uniform CD-ROM driver Revision: 3.20
[   28.334057] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   28.609977] Attempting manual resume
[   28.609982] swsusp: Resume From Partition 8:5
[   28.609984] PM: Checking swsusp image.
[   28.610207] PM: Resume from disk failed.
[   28.620666] usb 5-7: configuration #1 chosen from 1 choice
[   28.637360] EXT3-fs: INFO: recovery required on readonly filesystem.
[   28.637368] EXT3-fs: write access will be enabled during recovery.
[   29.173921] kjournald starting.  Commit interval 5 seconds
[   29.173941] EXT3-fs: sda1: orphan cleanup on readonly fs
[   29.173950] ext3_orphan_cleanup: deleting unreferenced inode 12599317
[   29.173978] ext3_orphan_cleanup: deleting unreferenced inode 12599304
[   29.173986] ext3_orphan_cleanup: deleting unreferenced inode 12599303
[   29.173992] ext3_orphan_cleanup: deleting unreferenced inode 12599302
[   29.173998] ext3_orphan_cleanup: deleting unreferenced inode 12599301
[   29.174004] ext3_orphan_cleanup: deleting unreferenced inode 12599300
[   29.174010] EXT3-fs: sda1: 6 orphan inodes deleted
[   29.174012] EXT3-fs: recovery complete.
[   29.177182] EXT3-fs: mounted filesystem with ordered data mode.
[   35.296939] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.456607] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.508194] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.743093] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   35.756560] parport_pc 00:0a: reported by Plug and Play ACPI
[   35.756665] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   35.978734] Linux agpgart interface v0.102
[   36.141334] input: Power Button (FF) as /devices/virtual/input/input4
[   36.169216] ACPI: Power Button (FF) [PWRF]
[   36.169290] input: Power Button (CM) as /devices/virtual/input/input5
[   36.186058] agpgart: Detected VIA P4M800 chipset
[   36.201194] ACPI: Power Button (CM) [PWRB]
[   36.201272] input: Sleep Button (CM) as /devices/virtual/input/input6
[   36.209196] agpgart: AGP aperture is 128M @ 0xe8000000
[   36.233191] ACPI: Sleep Button (CM) [SLPB]
[   36.257153] Linux video capture interface: v2.00
[   36.724924] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   36.725009] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 19
[   36.725080] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[   36.725084] cx88[0]: TV tuner type 44, Radio tuner type -1
[   36.882511] cx88[0]/0: found at 0000:00:06.0, rev: 5, irq: 19, latency: 32, mmio: 0xfa000000
[   37.184687] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   37.184716] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   37.184720] tuner 1-0043: type set to tda9887
[   37.187590] All bytes are equal. It is not a TEA5767
[   37.187593] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   37.187614] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   37.187617] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   37.187620] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   37.187622] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   37.232859] cx88[0]/0: registered device video0 [v4l2]
[   37.232887] cx88[0]/0: registered device vbi0
[   38.093511] nvidia: module license 'NVIDIA' taints kernel.
[   38.751442] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   38.751766] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   38.860775] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   38.860786] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
[   38.860933] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   39.052598] phy0: Selected rate control algorithm 'simple'
[   39.143069] usbcore: registered new interface driver rt73usb
[   41.247594] lp0: using parport0 (interrupt-driven).
[   41.441822] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   41.556936] wlan0: Initial auth_alg=0
[   41.556944] wlan0: authenticate with AP 00:30:bd:f8:92:07
[   41.558826] wlan0: RX authentication from 00:30:bd:f8:92:07 (alg=0 transaction=2 status=0)
[   41.558829] wlan0: authenticated
[   41.558833] wlan0: associate with AP 00:30:bd:f8:92:07
[   41.561465] wlan0: RX AssocResp from 00:30:bd:f8:92:07 (capab=0x1 status=0 aid=6)
[   41.561470] wlan0: associated
[   42.093900] EXT3 FS on sda1, internal journal
[   42.191333] NET: Registered protocol family 17
[   43.575624] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.771699] No dock devices found.
[   46.837679] NET: Registered protocol family 10
[   46.838025] lo: Disabled Privacy Extensions
[   49.480051] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   49.480058] apm: overridden by ACPI.
[   57.403462] wlan0: no IPv6 routers present
[   62.246480] eth0: link down
[   62.249193] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   66.298209] lirc_dev: IR Remote Control driver registered, major 61 
[   66.316516] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   66.318927] 
[   66.318933] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[   66.318936] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   66.334375] usbcore: registered new interface driver lirc_mceusb2
[   67.709106] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   67.709264] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   67.709345] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

---

### Post by jb5 on 2008-07-12
I've seen this on my setup.

For me, turning off, [use video as timebase (experimental)] solves the problem.

It's under - setup - tv settings - playback - (somewhere on page 1 of 9)

The utility seems to work for a while and then either an update OR (quite possibly) my messing about with the config/setup seems to prevent it working properly; this has happened twice now, once with Gutsy and now with Hardy!

---

