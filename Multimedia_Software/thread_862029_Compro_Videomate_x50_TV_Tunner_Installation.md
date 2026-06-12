---
title: "Compro Videomate x50 TV Tunner Installation"
date: 2008-07-17
forum: Multimedia Software
---

### Post by MSToTheEnd on 2008-07-17
Hi... 

 I have a problem with my tv tunner, I can't get it to work on my Ubuntu Hardy 8.04.
 I've tried MythTV, TVTime with no luck.

 The problem is that it doesn't recognize my tv card. It only shows the composite input options but I need the coaxial input.

 Any advice will be appreciated.

 Srry for my english I'm from Argentina and we don't speak english here.

---

### Post by xc3RnbFO8P on 2008-07-17
In Terminal:
> lspci
Show the output.

---

### Post by MSToTheEnd on 2008-07-18
Here it is:

```
mstotheend@Desktop:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0c.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) 

```

---

### Post by xc3RnbFO8P on 2008-07-19
I need also 
> dmesg

---

### Post by MSToTheEnd on 2008-07-19
Here it is:

```
00000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257166
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f482382f-e373-4bf3-a8a2-c52e217246bc ro quiet splash vga=795
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   17.062935] time.c: Detected 2199.792 MHz processor.
[   17.062969] Console: colour dummy device 80x25
[   17.062972] console [tty0] enabled
[   17.062985] Checking aperture...
[   17.062987] CPU 0: aperture @ d0000000 size 256 MB
[   17.073410] Memory: 1020924k/1048256k available (2489k kernel code, 26944k reserved, 1318k data, 320k init)
[   17.073441] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.152833] Calibrating delay using timer specific routine.. 4404.88 BogoMIPS (lpj=8809773)
[   17.152864] Security Framework initialized
[   17.152869] SELinux:  Disabled at boot.
[   17.152881] AppArmor: AppArmor initialized
[   17.152884] Failure registering capabilities with primary security module.
[   17.152968] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.153657] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.153991] Mount-cache hash table entries: 256
[   17.154104] Initializing cgroup subsys ns
[   17.154108] Initializing cgroup subsys cpuacct
[   17.154118] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.154119] CPU: L2 Cache: 512K (64 bytes/line)
[   17.154121] CPU 0/0 -> Node 0
[   17.154140] SMP alternatives: switching to UP code
[   17.154625] Early unpacking initramfs... done
[   17.432959] ACPI: Core revision 20070126
[   17.433001] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.475374] Using local APIC timer interrupts.
[   17.520788] APIC timer calibration result 13748698
[   17.520789] Detected 13.748 MHz APIC timer.
[   17.520837] Brought up 1 CPUs
[   17.521040] CPU0 attaching sched-domain:
[   17.521042]  domain 0: span 01
[   17.521044]   groups: 01
[   17.521166] net_namespace: 120 bytes
[   17.521530] Time:  4:03:35  Date: 07/19/08
[   17.521554] NET: Registered protocol family 16
[   17.521695] ACPI: bus type pci registered
[   17.521751] PCI: Using configuration type 1
[   17.523288] ACPI: EC: Look up EC in DSDT
[   17.526059] ACPI: Interpreter enabled
[   17.526061] ACPI: (supports S0 S1 S3 S4 S5)
[   17.526073] ACPI: Using IOAPIC for interrupt routing
[   17.530931] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.531755] PCI: enabled onboard AC97/MC97 devices
[   17.532027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.538676] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   17.538752] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   17.538824] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   17.538897] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   17.538970] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   17.539044] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   17.539117] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   17.539190] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   17.539271] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  0A, should be FD [20070126]
[   17.539277] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.539299] pnp: PnP ACPI init
[   17.539305] ACPI: bus type pnp registered
[   17.541986] pnp: PnP ACPI: found 13 devices
[   17.541989] ACPI: ACPI bus type pnp unregistered
[   17.542168] PCI: Using ACPI for IRQ routing
[   17.542170] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.542178] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   17.552786] NET: Registered protocol family 8
[   17.552787] NET: Registered protocol family 20
[   17.552840] agpgart: Detected AGP bridge 0
[   17.559357] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.559415] AppArmor: AppArmor Filesystem Enabled
[   17.560763] Time: tsc clocksource has been installed.
[   17.572782] system 00:08: ioport range 0x680-0x6ff has been reserved
[   17.572785] system 00:08: ioport range 0x290-0x297 has been reserved
[   17.572790] system 00:09: ioport range 0x3e1-0x3e7 has been reserved
[   17.572792] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   17.572794] system 00:09: ioport range 0x800-0x87f has been reserved
[   17.572796] system 00:09: ioport range 0x400-0x41f has been reserved
[   17.572802] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   17.572805] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.572807] system 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
[   17.572813] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   17.572815] system 00:0c: iomem range 0xc0000-0xdffff has been reserved
[   17.572817] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   17.572820] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[   17.572822] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   17.573116] PCI: Bridge: 0000:00:01.0
[   17.573118]   IO window: disabled.
[   17.573121]   MEM window: f9f00000-fbffffff
[   17.573124]   PREFETCH window: e0000000-f6ffffff
[   17.573144] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.573176] NET: Registered protocol family 2
[   17.608779] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   17.609157] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   17.610544] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.611188] TCP: Hash tables configured (established 131072 bind 65536)
[   17.611191] TCP reno registered
[   17.620826] checking if image is initramfs... it is
[   18.076212] Switched to high resolution mode on CPU 0
[   18.161246] Freeing initrd memory: 7552k freed
[   18.166550] audit: initializing netlink socket (disabled)
[   18.166560] audit(1216440216.064:1): initialized
[   18.168070] VFS: Disk quotas dquot_6.5.1
[   18.168140] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.168243] io scheduler noop registered
[   18.168245] io scheduler anticipatory registered
[   18.168247] io scheduler deadline registered
[   18.168328] io scheduler cfq registered (default)
[   18.168338] PCI: VIA PCI bridge detected. Disabling DAC.
[   18.192159] Boot video device is 0000:01:00.0
[   18.214361] Real Time Clock Driver v1.12ac
[   18.214437] Linux agpgart interface v0.102
[   18.214439] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.214541] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.215019] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.215543] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.215593] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.215655] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   18.215657] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   18.215760] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.216430] mice: PS/2 mouse device common for all mice
[   18.216461] cpuidle: using governor ladder
[   18.216463] cpuidle: using governor menu
[   18.216583] NET: Registered protocol family 1
[   18.216659] registered taskstats version 1
[   18.216763]   Magic number: 0:368:60
[   18.216878] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.216880] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.216881] EDD information not available.
[   18.216887] Freeing unused kernel memory: 320k freed
[   18.244008] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.297803] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc20000600000, using 10240k, total 262144k
[   18.297807] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   18.297809] vesafb: scrolling: redraw
[   18.297811] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   18.297903] Console: switching to colour frame buffer device 160x64
[   18.405563] fb0: VESA VGA frame buffer device
[   19.599473] fuse init (API version 7.9)
[   19.612862] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.018079] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.018091] PCI: Disallowing DAC for device 0000:00:0a.0
[   20.018189] skge 1.13 addr 0xf9c00000 irq 17 chip Yukon-Lite rev 9
[   20.018422] skge eth0: addr 00:15:f2:ce:03:a9
[   20.070351] SCSI subsystem initialized
[   20.113913] libata version 3.00 loaded.
[   20.129538] usbcore: registered new interface driver usbfs
[   20.129556] usbcore: registered new interface driver hub
[   20.133937] sata_via 0000:00:0f.0: version 2.3
[   20.133957] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   20.133991] sata_via 0000:00:0f.0: routed to hard irq line 10
[   20.140216] usbcore: registered new device driver usb
[   20.145899] scsi0 : sata_via
[   20.164591] scsi1 : sata_via
[   20.164632] ata1: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 20
[   20.164634] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 20
[   20.173862] USB Universal Host Controller Interface driver v3.0
[   20.257707] Floppy drive(s): fd0 is 1.44M
[   20.280593] FDC 0 is a post-1991 82077
[   20.365614] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   20.577396] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.741497] ata2.00: ATA-7: WDC WD1600JS-19NCB1, 10.02E01, max UDMA/133
[   20.741500] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   20.757485] ata2.00: configured for UDMA/133
[   20.757583] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600JS-19N 10.0 PQ: 0 ANSI: 5
[   20.757997] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   20.758039] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   20.760144] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   20.760155] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   20.760373] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   20.760407] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[   20.760520] usb usb1: configuration #1 chosen from 1 choice
[   20.760540] hub 1-0:1.0: USB hub found
[   20.760544] hub 1-0:1.0: 2 ports detected
[   20.765354] Driver 'sd' needs updating - please use bus_type methods
[   20.765420] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   20.765430] sd 1:0:0:0: [sda] Write Protect is off
[   20.765432] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.765444] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.765477] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   20.765483] sd 1:0:0:0: [sda] Write Protect is off
[   20.765485] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.765496] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.765499]  sda: sda1 sda2 < sda5 sda6 >
[   20.800414] sd 1:0:0:0: [sda] Attached SCSI disk
[   20.804231] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   20.861147] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   20.861159] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   20.861178] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   20.861201] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[   20.861287] usb usb2: configuration #1 chosen from 1 choice
[   20.861306] hub 2-0:1.0: USB hub found
[   20.861311] hub 2-0:1.0: 2 ports detected
[   20.965014] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   20.965025] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   20.965044] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   20.965069] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[   20.965154] usb usb3: configuration #1 chosen from 1 choice
[   20.965173] hub 3-0:1.0: USB hub found
[   20.965176] hub 3-0:1.0: 2 ports detected
[   21.068898] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   21.068909] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   21.068926] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   21.068947] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[   21.069033] usb usb4: configuration #1 chosen from 1 choice
[   21.069050] hub 4-0:1.0: USB hub found
[   21.069054] hub 4-0:1.0: 2 ports detected
[   21.100778] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   21.149566] Attempting manual resume
[   21.149569] swsusp: Resume From Partition 8:6
[   21.149570] PM: Checking swsusp image.
[   21.149748] PM: Resume from disk failed.
[   21.159840] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.159844] EXT3-fs: write access will be enabled during recovery.
[   21.172861] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   21.172960] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   21.173008] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   21.173042] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9e00000
[   21.224654] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.224801] usb usb5: configuration #1 chosen from 1 choice
[   21.224819] hub 5-0:1.0: USB hub found
[   21.224824] hub 5-0:1.0: 8 ports detected
[   21.332207] pata_via 0000:00:0f.1: version 0.3.3
[   21.332229] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   21.333033] scsi2 : pata_via
[   21.333734] scsi3 : pata_via
[   21.334789] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   21.334792] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   21.620186] usb 1-1: device not accepting address 2, error -71
[   21.652563] ata3.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.06, max UDMA/66
[   21.824246] ata3.00: configured for UDMA/66
[   21.998383] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.06 PQ: 0 ANSI: 5
[   21.998445] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   22.005509] Driver 'sr' needs updating - please use bus_type methods
[   22.036593] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   22.036598] Uniform CD-ROM driver Revision: 3.20
[   22.036642] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   22.344582] kjournald starting.  Commit interval 5 seconds
[   22.344596] EXT3-fs: sda5: orphan cleanup on readonly fs
[   22.344600] ext3_orphan_cleanup: deleting unreferenced inode 148247
[   22.344632] ext3_orphan_cleanup: deleting unreferenced inode 81632
[   22.344638] ext3_orphan_cleanup: deleting unreferenced inode 81611
[   22.344641] ext3_orphan_cleanup: deleting unreferenced inode 81610
[   22.344645] ext3_orphan_cleanup: deleting unreferenced inode 81609
[   22.344649] ext3_orphan_cleanup: deleting unreferenced inode 81608
[   22.344653] ext3_orphan_cleanup: deleting unreferenced inode 81605
[   22.344656] EXT3-fs: sda5: 7 orphan inodes deleted
[   22.344657] EXT3-fs: recovery complete.
[   22.358018] EXT3-fs: mounted filesystem with ordered data mode.
[   23.234370] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   31.701310] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.944572] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.984566] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.165700] parport_pc 00:07: reported by Plug and Play ACPI
[   32.165743] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   32.376963] input: Power Button (FF) as /devices/virtual/input/input3
[   32.416040] ACPI: Power Button (FF) [PWRF]
[   32.416099] input: Power Button (CM) as /devices/virtual/input/input4
[   32.447238] ACPI: Power Button (CM) [PWRB]
[   32.447284] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.476008] ACPI: Sleep Button (CM) [SLPB]
[   32.655682] Linux video capture interface: v2.00
[   32.913900] skge eth0: enabling interface
[   33.030856] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   33.030903] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.030940] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   33.030941] cx88[0]: try to pick one of the existing card configs via
[   33.030942] cx88[0]: card=<n> insmod option.  Updating to the latest
[   33.030943] cx88[0]: version might help as well.
[   33.030946] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   33.030947] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   33.030949] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   33.030950] cx88[0]:    card=2 -> GDI Black Gold
[   33.030952] cx88[0]:    card=3 -> PixelView
[   33.030953] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   33.030954] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   33.030956] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   33.030957] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   33.030959] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   33.030960] cx88[0]:    card=9 -> Leadtek PVR 2000
[   33.030962] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   33.030963] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   33.030964] cx88[0]:    card=12 -> ASUS PVR-416
[   33.030966] cx88[0]:    card=13 -> MSI TV-@nywhere
[   33.030967] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   33.030969] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   33.030970] cx88[0]:    card=16 -> KWorld LTV883RF
[   33.030972] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   33.030973] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   33.030975] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   33.030976] cx88[0]:    card=20 -> Provideo PV259
[   33.030977] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   33.030979] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   33.030980] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   33.030982] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   33.030984] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   33.030985] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   33.030987] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   33.030988] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   33.030990] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   33.030992] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   33.030993] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   33.030995] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   33.030996] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   33.030998] cx88[0]:    card=34 -> ATI HDTV Wonder
[   33.030999] cx88[0]:    card=35 -> WinFast DTV1000-T
[   33.031000] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   33.031002] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   33.031003] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   33.031005] cx88[0]:    card=39 -> KWorld DVB-S 100
[   33.031006] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   33.031008] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   33.031010] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   33.031011] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   33.031013] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   33.031015] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   33.031016] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   33.031018] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   33.031019] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   33.031020] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   33.031022] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   33.031023] cx88[0]:    card=51 -> WinFast DTV2000 H
[   33.031025] cx88[0]:    card=52 -> Geniatech DVB-S
[   33.031026] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   33.031028] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   33.031030] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   33.031031] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   33.031033] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   33.031035] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   33.031036] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   33.031038] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   33.031039] cx88[0]:    card=61 -> Winfast TV2000 XP Global
[   33.031041] cx88[0]:    card=62 -> PowerColor RA330
[   33.031042] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   33.031043] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   33.031045] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   33.031046] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   33.031048] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   33.031050] cx88[0]: subsystem: 185b:e000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   33.031052] cx88[0]: TV tuner type -1, Radio tuner type -1
[   33.334200] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   33.366468] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 17, latency: 64, mmio: 0xf7000000
[   33.366523] cx88[0]/0: registered device video0 [v4l2]
[   33.366548] cx88[0]/0: registered device vbi0
[   33.366558] tuner' 1-0061: tuner type not set
[   33.388658] usb 1-1: configuration #1 chosen from 1 choice
[   33.432209] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[   33.432213] cx88_alsa: Unknown symbol videobuf_dma_free
[   33.432249] cx88_alsa: disagrees about version of symbol cx88_core_put
[   33.432251] cx88_alsa: Unknown symbol cx88_core_put
[   33.432315] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   33.432339] cx88_alsa: disagrees about version of symbol cx88_core_irq
[   33.432340] cx88_alsa: Unknown symbol cx88_core_irq
[   33.432373] cx88_alsa: disagrees about version of symbol cx88_core_get
[   33.432374] cx88_alsa: Unknown symbol cx88_core_get
[   33.432507] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[   33.432509] cx88_alsa: Unknown symbol btcx_riscmem_free
[   33.432587] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[   33.432589] cx88_alsa: Unknown symbol videobuf_dma_init
[   33.432644] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[   33.432645] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   33.432678] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[   33.432679] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   33.432707] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   33.432708] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[   33.432752] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   33.432808] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   33.432839] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[   33.432841] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   33.432866] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   33.432867] cx88_alsa: Unknown symbol videobuf_to_dma
[   33.524932] nvidia: module license 'NVIDIA' taints kernel.
[   33.878369] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   34.025761] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.025895] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   34.034218] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   34.034226] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   34.050757] usb 2-1: configuration #1 chosen from 1 choice
[   34.219837] NET: Registered protocol family 10
[   34.220004] lo: Disabled Privacy Extensions
[   34.220266] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.562263] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   34.562797] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.785336] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   35.288980] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   35.288993] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   35.289110] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   35.289248] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   35.305034] Bluetooth: Core ver 2.11
[   35.313788] NET: Registered protocol family 31
[   35.313791] Bluetooth: HCI device and connection manager initialized
[   35.313795] Bluetooth: HCI socket layer initialized
[   35.344716] Bluetooth: HCI USB driver ver 2.9
[   35.346305] usbcore: registered new interface driver hci_usb
[   35.402602] usbcore: registered new interface driver hiddev
[   35.415131] input: Navigator as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input6
[   35.432614] input,hidraw0: USB HID v1.10 Mouse [Navigator] on usb-0000:00:10.1-1
[   35.432628] usbcore: registered new interface driver usbhid
[   35.432631] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.087675] lp0: using parport0 (interrupt-driven).
[   36.170070] Adding 1220900k swap on /dev/sda6.  Priority:-1 extents:1 across:1220900k
[   36.725463] EXT3 FS on sda5, internal journal
[   38.302965] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.740986] No dock devices found.
[   39.029221] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   39.030139] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   41.876333] ppdev: user-space parallel port driver
[   42.084696] audit(1216440236.080:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5124 profile="/usr/sbin/cupsd" namespace="default"
[   44.852172] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   44.852177] vboxdrv: Successfully done.
[   44.852179] vboxdrv: Found 1 processor cores.
[   44.852181] vboxdrv: fAsync=0 u64DiffCores=1.
[   44.852226] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   44.852228] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   45.118278] tun: Universal TUN/TAP device driver, 1.6
[   45.118282] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   45.273479] eth0: no IPv6 routers present
[   49.080201] Bluetooth: L2CAP ver 2.9
[   49.080205] Bluetooth: L2CAP socket layer initialized
[   49.331141] Bluetooth: RFCOMM socket layer initialized
[   49.331161] Bluetooth: RFCOMM TTY layer initialized
[   49.331163] Bluetooth: RFCOMM ver 1.8
[   51.545061] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   51.545076] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   51.545154] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
```

---

### Post by xc3RnbFO8P on 2008-07-20
Try this:
> sudo gedit /etc/modprobe.d/cx88xx
add this line:
> options cx88xx card=12 radio=1
Save,restart the computer and try Tvtime.

---

### Post by MSToTheEnd on 2008-07-20
When I typed:
```
sudo gedit /etc/modprobe.d/cx88xx 
```

 It opened a blank document I added the line:

```
options cx88xx card=12 radio=1 
```

 Restart the computer and now it detects my card. But I get "no signal" I've have checked the conexion and it was ok.
 What could be the problem? 

 I'm from Argentina, using a tv cable signal. what are the configurations I have to make?

 Again, sorry for my english.

 Thank you for helping me!

---

### Post by xc3RnbFO8P on 2008-07-20
It is not supported,
> 33.031050] cx88[0]: subsystem: **185b:e000**, board: UNKNOWN/GENERIC [card=0,autodetected]

[http://pci-ids.ucw.cz/iii/?i=14f18800:s=1]("http://pci-ids.ucw.cz/iii/?i=14f18800:s=1")
Or you could try find if some of the card on the dmesg list work.
example card=36 or 32, not if they are dvb or HDTV.

---

### Post by thaltek on 2008-12-29
```
 18
[   24.983461] saa7130[0]: found at 0000:02:0a.0, rev: 1, irq: 18, latency: 15, mmio: 0xdfdff000
[   24.983530] PCI: Setting latency timer of device 0000:02:0a.0 to 64
[   24.983534] saa7134: <rant>
[   24.983535] saa7134:  Congratulations!  Your TV card vendor saved a few
[   24.983536] saa7134:  cents for a eeprom, thus your pci board has no
[   24.983537] saa7134:  subsystem ID and I can't identify it automatically
[   24.983538] saa7134: </rant>
[   24.983538] saa7134: I feel better now.  Ok, here are the good news:
[   24.983539] saa7134: You can use the card=<nr> insmod option to specify
[   24.983540] saa7134: which board do you have.  The list:
[   24.983983] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   24.984082] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   24.984273] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   24.984464] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   24.984655] saa7134:   card=4 -> EMPRESS                    

```
gah!!!!!! *beats head on keyboard*
[http://www.zogis.com/main_products_series_tv_tuner_PCI_RA220.htm](http://www.zogis.com/main_products_series_tv_tuner_PCI_RA220.htm)
it looked nice in the store and works well under vista i am now trying to get it to work..... *wanders back to the computers innards...*

---

### Post by wolfen69 on 2008-12-29
> **thaltek said:**
> ```
 18
[   24.983461] saa7130[0]: found at 0000:02:0a.0, rev: 1, irq: 18, latency: 15, mmio: 0xdfdff000
[   24.983530] PCI: Setting latency timer of device 0000:02:0a.0 to 64
[   24.983534] saa7134: <rant>
[   24.983535] saa7134:  Congratulations!  Your TV card vendor saved a few
[   24.983536] saa7134:  cents for a eeprom, thus your pci board has no
[   24.983537] saa7134:  subsystem ID and I can't identify it automatically
[   24.983538] saa7134: </rant>
[   24.983538] saa7134: I feel better now.  Ok, here are the good news:
[   24.983539] saa7134: You can use the card=<nr> insmod option to specify
[   24.983540] saa7134: which board do you have.  The list:
[   24.983983] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   24.984082] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   24.984273] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   24.984464] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   24.984655] saa7134:   card=4 -> EMPRESS                    

```
gah!!!!!! *beats head on keyboard*
[http://www.zogis.com/main_products_series_tv_tuner_PCI_RA220.htm](http://www.zogis.com/main_products_series_tv_tuner_PCI_RA220.htm)
it looked nice in the store and works well under vista i am now trying to get it to work..... *wanders back to the computers innards...*

[Here]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") is a how to help get it going.

---

### Post by thaltek on 2009-01-05
> **wolfen69 said:**
> [Here]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") is a how to help get it going.

thanks but i got it working only 3 or 4 hours after i posted that last message..... linux for me is one of those things where i have to beat my head on the keyboard for magic to happen... kind of like the pair of 9500 gt cards.. up and working....

---

### Post by echi24 on 2009-02-08
> **thaltek said:**
> thanks but i got it working only 3 or 4 hours after i posted that last message..... linux for me is one of those things where i have to beat my head on the keyboard for magic to happen... kind of like the pair of 9500 gt cards.. up and working....

Can you explain how you do it. I have a Compro Gold +, Im from Argentina and have the same problem.
i also try with mythbuntu but have the same problem of "no signal".
If you have the answer to this please post it.

Thanks
Exequiel

---

### Post by thaltek on 2009-04-15
> **echi24 said:**
> Can you explain how you do it. I have a Compro Gold +, Im from Argentina and have the same problem.
i also try with mythbuntu but have the same problem of "no signal".
If you have the answer to this please post it.

Thanks
Exequiel
:S !make sure you are using the right input source and are using the correct tv standard.... ! 

i do recall that the only way i could get it to work was though the command line and i basically had to assign the card a tuner number..... 

[https://answers.launchpad.net/ubuntu/+question/48158](https://answers.launchpad.net/ubuntu/+question/48158)

the code that worked for me is about 3/4 of the way down the page. however i would suggest reading the whole thing as there are several steps....

---

