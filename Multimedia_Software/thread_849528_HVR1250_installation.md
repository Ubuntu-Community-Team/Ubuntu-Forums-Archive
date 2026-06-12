---
title: "HVR1250 installation"
date: 2008-07-04
forum: Multimedia Software
---

### Post by tanso on 2008-07-04
hvr1250 install problems..
For some reason Ubuntu 8.04 LTS recognizes it but will not work.

dmesg:
CORE cx23885 [0] : subsystem: 0070:7911. board: Hauppauge WinTV-HVR1250 [card=3, autodetected]

Got it connected to my Satellite down-converter  so I only need channel 3.
BTW it might make a difference:
video: Nvidia 8500 with dual monitors using Envy Nvidia video driver.

dmseg:
module license 'NVIDIA' taints kernel

But works perfectly.

---

### Post by xc3RnbFO8P on 2008-07-04
Did you try in Terminal:
> sudo /sbin/modprobe cx23885

---

### Post by tanso on 2008-07-04
> **Ringi said:**
> Did you try in Terminal:
dsmeg:
[   22.131886] ACPI: Core revision 20070126
[   22.131944] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.176147] Using local APIC timer interrupts.
[   22.221365] APIC timer calibration result 12564410
[   22.221366] Detected 12.564 MHz APIC timer.
[   22.221454] SMP alternatives: switching to SMP code
[   22.221857] Booting processor 1/2 APIC 0x1
[   22.232213] Initializing CPU#1
[   22.309664] Calibrating delay using timer specific routine.. 4422.67 BogoMIPS (lpj=8845352)
[   22.309669] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.309671] CPU: L2 Cache: 512K (64 bytes/line)
[   22.309673] CPU 1/1 -> Node 0
[   22.309675] CPU: Physical Processor ID: 0
[   22.309676] CPU: Processor Core ID: 1
[   22.309745] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   22.309530] Brought up 2 CPUs
[   22.309607] CPU0 attaching sched-domain:
[   22.309609]  domain 0: span 03
[   22.309611]   groups: 01 02
[   22.309614]   domain 1: span 03
[   22.309615]    groups: 03
[   22.309616] CPU1 attaching sched-domain:
[   22.309618]  domain 0: span 03
[   22.309619]   groups: 02 01
[   22.309621]   domain 1: span 03
[   22.309622]    groups: 03
[   22.309819] net_namespace: 120 bytes
[   22.310176] Time:  1:44:47  Date: 07/03/08
[   22.310205] NET: Registered protocol family 16
[   22.310365] ACPI: bus type pci registered
[   22.310418] PCI: Using configuration type 1
[   22.311623] ACPI: EC: Look up EC in DSDT
[   22.317285] ACPI: Interpreter enabled
[   22.317288] ACPI: (supports S0 S3 S4 S5)
[   22.317299] ACPI: Using IOAPIC for interrupt routing
[   22.325341] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.325734] PCI: Transparent bridge - 0000:00:09.0
[   22.326015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.326294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.382620] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.382777] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.382932] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.383086] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.383240] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.383395] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.383549] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.383705] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.383858] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.384015] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.384172] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.384327] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.384482] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.384645] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.384808] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.384970] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.385143] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.385310] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   22.385482] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.385647] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   22.385757] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.385930] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.386100] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.386271] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.386440] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   22.386611] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   22.386782] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.386951] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.387121] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.387298] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.387474] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.387650] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.387768] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.387794] pnp: PnP ACPI init
[   22.387800] ACPI: bus type pnp registered
[   22.392457] pnpacpi: exceeded the max number of mem resources: 12
[   22.392510] pnp: PnP ACPI: found 14 devices
[   22.392512] ACPI: ACPI bus type pnp unregistered
[   22.392714] PCI: Using ACPI for IRQ routing
[   22.392717] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.401388] NET: Registered protocol family 8
[   22.401390] NET: Registered protocol family 20
[   22.401455] PCI-DMA: Disabling AGP.
[   22.401700] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   22.401704] PCI-DMA: using GART IOMMU.
[   22.401711] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   22.401912] AppArmor: AppArmor Filesystem Enabled
[   22.413432] system 00:01: ioport range 0x1000-0x107f has been reserved
[   22.413435] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   22.413438] system 00:01: ioport range 0x1400-0x147f has been reserved
[   22.413441] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   22.413444] system 00:01: ioport range 0x1800-0x187f has been reserved
[   22.413446] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   22.413450] system 00:01: iomem range 0x0-0x0 could not be reserved
[   22.413456] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   22.413459] system 00:02: ioport range 0x800-0x87f has been reserved
[   22.413461] system 00:02: ioport range 0x290-0x297 has been reserved
[   22.413473] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.413480] system 00:0d: iomem range 0xd1800-0xd3fff has been reserved
[   22.413482] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   22.413485] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   22.413488] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   22.413491] system 00:0d: iomem range 0xbfee0000-0xbfefffff could not be reserved
[   22.413494] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[   22.413497] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   22.413500] system 00:0d: iomem range 0x100000-0xbfedffff could not be reserved
[   22.413503] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.413505] system 00:0d: iomem range 0xfee00000-0xfeefffff could not be reserved
[   22.413508] system 00:0d: iomem range 0xfefff000-0xfeffffff has been reserved
[   22.413511] system 00:0d: iomem range 0xfff80000-0xfff80fff has been reserved
[   22.413851] PCI: Bridge: 0000:00:09.0
[   22.413853]   IO window: b000-bfff
[   22.413856]   MEM window: fde00000-fdefffff
[   22.413858]   PREFETCH window: fdf00000-fdffffff
[   22.413860] PCI: Bridge: 0000:00:0b.0
[   22.413862]   IO window: a000-afff
[   22.413864]   MEM window: fdd00000-fddfffff
[   22.413865]   PREFETCH window: fdc00000-fdcfffff
[   22.413868] PCI: Bridge: 0000:00:0c.0
[   22.413870]   IO window: 9000-9fff
[   22.413871]   MEM window: fd600000-fd7fffff
[   22.413873]   PREFETCH window: fdb00000-fdbfffff
[   22.413876] PCI: Bridge: 0000:00:0d.0
[   22.413877]   IO window: 8000-8fff
[   22.413879]   MEM window: fda00000-fdafffff
[   22.413881]   PREFETCH window: fd900000-fd9fffff
[   22.413885] PCI: Bridge: 0000:00:0e.0
[   22.413887]   IO window: 7000-7fff
[   22.413889]   MEM window: f8000000-fbffffff
[   22.413891]   PREFETCH window: d0000000-dfffffff
[   22.413897] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.413912] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.413918] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.413923] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.413928] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.413939] NET: Registered protocol family 2
[   22.417352] Time: acpi_pm clocksource has been installed.
[   22.417366] Switched to high resolution mode on CPU 0
[   22.417756] Switched to high resolution mode on CPU 1
[   22.449517] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   22.451416] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   22.456165] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.456748] TCP: Hash tables configured (established 524288 bind 65536)
[   22.456751] TCP reno registered
[   22.465441] checking if image is initramfs... it is
[   23.045173] Freeing initrd memory: 8203k freed
[   23.049823] audit: initializing netlink socket (disabled)
[   23.049834] audit(1215049487.360:1): initialized
[   23.051754] VFS: Disk quotas dquot_6.5.1
[   23.051818] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.051926] io scheduler noop registered
[   23.051928] io scheduler anticipatory registered
[   23.051930] io scheduler deadline registered
[   23.052015] io scheduler cfq registered (default)
[   23.052029] pci 0000:00:00.0: Enabling HT MSI Mapping
[   23.065563] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   23.065572] PCI: Found enabled HT MSI Mapping on 0000:00:0b.0
[   23.065579] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   23.065584] PCI: Found enabled HT MSI Mapping on 0000:00:0c.0
[   23.065591] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   23.065596] PCI: Found enabled HT MSI Mapping on 0000:00:0d.0
[   23.065602] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   23.065607] PCI: Found enabled HT MSI Mapping on 0000:00:0e.0
[   23.065621] Boot video device is 0000:05:00.0
[   23.065768] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.065784] assign_interrupt_mode Found MSI capability
[   23.065799] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.065852] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.065867] assign_interrupt_mode Found MSI capability
[   23.065878] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.065924] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.065939] assign_interrupt_mode Found MSI capability
[   23.065950] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.065998] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.066013] assign_interrupt_mode Found MSI capability
[   23.066023] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.090410] Real Time Clock Driver v1.12ac
[   23.090500] Linux agpgart interface v0.102
[   23.090502] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.090601] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.091073] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.091705] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.091764] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.091843] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.092467] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.092475] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.106575] mice: PS/2 mouse device common for all mice
[   23.106615] cpuidle: using governor ladder
[   23.106617] cpuidle: using governor menu
[   23.106735] NET: Registered protocol family 1
[   23.106824] registered taskstats version 1
[   23.106930]   Magic number: 0:18:710
[   23.107043] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.107046] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.107047] EDD information not available.
[   23.107057] Freeing unused kernel memory: 320k freed
[   23.145537] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.290409] fuse init (API version 7.9)
[   24.302173] ACPI: Fan [FAN] (on)
[   24.307506] ACPI: Thermal Zone [THRM] (40 C)
[   24.320722] device-mapper: uevent: version 1.0.3
[   24.320767] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   24.473825] usbcore: registered new interface driver usbfs
[   24.473844] usbcore: registered new interface driver hub
[   24.474356] usbcore: registered new device driver usb
[   24.475623] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.475965] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   24.475973] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   24.476193] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.476198] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.476399] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   24.476420] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   24.532352] usb usb1: configuration #1 chosen from 1 choice
[   24.532374] hub 1-0:1.0: USB hub found
[   24.532381] hub 1-0:1.0: 10 ports detected
[   24.710494] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   24.710503] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   24.710682] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   24.710687] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   24.710734] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   24.710759] ehci_hcd 0000:00:02.1: debug port 1
[   24.710762] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   24.710771] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   24.716444] SCSI subsystem initialized
[   24.722219] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.722323] usb usb2: configuration #1 chosen from 1 choice
[   24.722346] hub 2-0:1.0: USB hub found
[   24.722353] hub 2-0:1.0: 10 ports detected
[   24.733649] libata version 3.00 loaded.
[   24.826419] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   24.826731] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   24.826739] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   24.826744] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   24.844606] Floppy drive(s): fd0 is 1.44M
[   24.866027] FDC 0 is a post-1991 82077
[   25.345423] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:16:ec:a6:a5:61
[   25.345427] forcedeth 0000:00:0a.0: highdma csum timirq lnktim desc-v3
[   25.347214] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   25.347594] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   25.347602] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   25.347617] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.347623] ACPI: PCI interrupt for device 0000:00:07.0 disabled
[   25.347944] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   25.347946] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   25.347960] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.347966] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   25.349507] pata_amd 0000:00:06.0: version 0.3.10
[   25.349537] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   25.349623] scsi0 : pata_amd
[   25.349661] scsi1 : pata_amd
[   25.350246] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   25.350248] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   25.721999] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   25.853204] ata2.01: ATAPI: AOPEN   DUW1608/ARR, A05a, max UDMA/66
[   25.925130] usb 1-1: configuration #1 chosen from 1 choice
[   25.928063] hub 1-1:1.0: USB hub found
[   25.931055] hub 1-1:1.0: 4 ports detected
[   26.025109] ata2.01: configured for UDMA/66
[   26.027008] scsi 1:0:1:0: CD-ROM            AOPEN    DUW1608/ARR      A05a PQ: 0 ANSI: 5
[   26.027177] sata_nv 0000:00:07.0: version 3.5
[   26.027187] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   26.027191] sata_nv 0000:00:07.0: Using ADMA mode
[   26.027398] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   26.027719] scsi2 : sata_nv
[   26.027769] scsi3 : sata_nv
[   26.027916] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
[   26.027918] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 20
[   26.039770] Driver 'sr' needs updating - please use bus_type methods
[   26.047850] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   26.047854] Uniform CD-ROM driver Revision: 3.20
[   26.047890] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   26.051269] sr 1:0:1:0: Attached scsi generic sg0 type 5
[   26.353869] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   26.492852] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.516167] ata3.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[   26.516170] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.529133] ata3.00: configured for UDMA/133
[   26.568035] usb 1-3: configuration #1 chosen from 1 choice
[   26.789919] usb 1-1.4: new full speed USB device using ohci_hcd and address 4
[   26.897985] usb 1-1.4: configuration #1 chosen from 1 choice
[   26.901931] usbcore: registered new interface driver hiddev
[   26.901964] usbcore: registered new interface driver usbhid
[   26.901967] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.997746] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.023127] ata4.00: ATA-7: WDC WD3200AAJS-00RYA0, 12.01B01, max UDMA/133
[   27.023131] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (not used)
[   27.038660] ata4.00: configured for UDMA/133
[   27.038749] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[   27.038756] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.038821] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   27.038875] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[   27.038879] ata4: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.038929] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   27.038951] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   27.038956] sata_nv 0000:00:08.0: Using ADMA mode
[   27.039161] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   27.039264] scsi4 : sata_nv
[   27.039318] scsi5 : sata_nv
[   27.039463] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 23
[   27.039465] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 23
[   27.348681] ata5: SATA link down (SStatus 0 SControl 300)
[   27.817575] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.980625] ata6.00: ATAPI: HL-DT-ST DVDRAM GSA-H62N, CL00, max UDMA/100
[   28.153587] ata6.00: configured for UDMA/100
[   28.157117] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H62N  CL00 PQ: 0 ANSI: 5
[   28.157123] ata6: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   28.174157] sr1: scsi3-mmc drive: 0x/0x caddy
[   28.174193] sr 5:0:0:0: Attached scsi CD-ROM sr1
[   28.174221] sr 5:0:0:0: Attached scsi generic sg3 type 5
[   28.179710] Driver 'sd' needs updating - please use bus_type methods
[   28.179784] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.179795] sd 2:0:0:0: [sda] Write Protect is off
[   28.179797] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.179809] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.179864] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.179871] sd 2:0:0:0: [sda] Write Protect is off
[   28.179873] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.179883] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.179886]  sda: sda1
[   28.185676] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.185735] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   28.185745] sd 3:0:0:0: [sdb] Write Protect is off
[   28.185747] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.185759] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.185795] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   28.185802] sd 3:0:0:0: [sdb] Write Protect is off
[   28.185804] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.185815] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.185818]  sdb: sdb1 sdb2 < sdb5 >
[   28.197280] sd 3:0:0:0: [sdb] Attached SCSI disk
[   28.525861] Attempting manual resume
[   28.525864] swsusp: Resume From Partition 254:1
[   28.525866] PM: Checking swsusp image.
[   28.526030] PM: Resume from disk failed.
[   28.569070] kjournald starting.  Commit interval 5 seconds
[   28.569086] EXT3-fs: mounted filesystem with ordered data mode.
[   36.555908] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.573907] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.578818] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.758752] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   36.758768] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   36.779479] input: Power Button (FF) as /devices/virtual/input/input3
[   36.799804] ACPI: Power Button (FF) [PWRF]
[   36.799870] input: Power Button (CM) as /devices/virtual/input/input4
[   36.831803] ACPI: Power Button (CM) [PWRB]
[   36.917534] logips2pp: Detected unknown logitech mouse model 74
[   37.422063] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input5
[   37.434544] parport_pc 00:09: reported by Plug and Play ACPI
[   37.434609] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.844316] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   37.844325] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   37.844339] PCI: Setting latency timer of device 0000:01:07.0 to 64
[   38.025267] cx23885 driver version 0.0.1 loaded
[   38.025550] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   38.025558] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   38.025573] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   38.147980] cx23885[0]: i2c bus 0 registered
[   38.148016] cx23885[0]: i2c bus 1 registered
[   38.148028] cx23885[0]: i2c bus 2 registered
[   38.174160] tveeprom 2-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   38.174162] cx23885[0]: warning: unknown hauppauge model #0
[   38.174164] cx23885[0]: hauppauge eeprom: model=0
[   38.174166] cx23885[0]: cx23885 based dvb card
[   38.270963] nvidia: module license 'NVIDIA' taints kernel.
[   38.554890] MT2131: successfully identified at address 0x61
[   38.554896] DVB: registering new adapter (cx23885[0])
[   38.554899] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   38.555114] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 16, latency: 0, mmio: 0xfd600000
[   38.555120] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.556944] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   38.556954] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   38.556962] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   38.557100] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05  Mon May 19 00:03:22 PDT 2008
[   40.576941] /build/buildd/linux-2.6.24/drivers/input/tablet/aiptek.c: input: Aiptek using 400 ms programming speed
[   40.576944] 
[   40.577024] input: Aiptek as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input6
[   40.611028] usbcore: registered new interface driver aiptek
[   40.611032] /build/buildd/linux-2.6.24/drivers/input/tablet/aiptek.c: v2.3 (May 2, 2007): Bryan W. Headley/Chris Atenasio/Cedric Brun/Rene van Paassen
[   40.611036] /build/buildd/linux-2.6.24/drivers/input/tablet/aiptek.c: Aiptek HyperPen USB Tablet Driver (Linux 2.6.x)
[   41.735499] loop: module loaded
[   41.759971] lp0: using parport0 (interrupt-driven).
[   41.866051] Adding 12689400k swap on /dev/mapper/ubuntu-swap_1.  Priority:-1 extents:1 across:12689400k
[   42.417651] EXT3 FS on dm-0, internal journal
[   43.163854] kjournald starting.  Commit interval 5 seconds
[   43.170778] EXT3 FS on sdb1, internal journal
[   43.170784] EXT3-fs: mounted filesystem with ordered data mode.
[   43.796039] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.506423] No dock devices found.
[   44.800290] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   44.799984] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
[   44.799989] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc
[   44.799991] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe
[   44.799992] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   47.483075] ppdev: user-space parallel port driver
[   47.745937] audit(1215074713.113:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5533 profile="/usr/sbin/cupsd" namespace="default"
[   48.558675] NET: Registered protocol family 10
[   48.558870] lo: Disabled Privacy Extensions
[   49.460754] Bluetooth: Core ver 2.11
[   49.461125] NET: Registered protocol family 31
[   49.461128] Bluetooth: HCI device and connection manager initialized
[   49.461131] Bluetooth: HCI socket layer initialized
[   49.477770] Bluetooth: L2CAP ver 2.9
[   49.477773] Bluetooth: L2CAP socket layer initialized
[   49.509312] Bluetooth: RFCOMM socket layer initialized
[   49.509328] Bluetooth: RFCOMM TTY layer initialized
[   49.509330] Bluetooth: RFCOMM ver 1.8
[   49.783651] Clocksource tsc unstable (delta = -90144573 ns)
[   51.212576] lirc_dev: IR Remote Control driver registered, at major 61 
[   51.276956] Linux video capture interface: v2.00
[   51.313066] bttv: driver version 0.9.17 loaded
[   51.313072] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   51.397976] ivtv:  Start initialization, version 1.1.0
[   51.398022] ivtv:  End initialization
[   51.440719] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   51.457883] usbcore: registered new interface driver commandir
[   51.461862] lirc_dev: lirc_register_plugin: sample_rate: 20
[   51.476010] lirc_cmdir: freq set to 38000Hz
[   51.710539] lirc_cmdir: device is unplugged
[   51.827327] NET: Registered protocol family 17
[   58.541038] eth0: no IPv6 routers present
[13363.239839] audit(1215103266.534:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=9853 profile="/usr/sbin/cupsd" namespace="default"
[32311.336060] audit(1215144366.365:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=10786 profile="/usr/sbin/cupsd" namespace="default"
[32371.965066] audit(1215144475.438:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=10811 profile="/usr/sbin/cupsd" namespace="default"
[52684.863850] eth0: link down.
[52693.896682] eth0: link up.
[52693.903007] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[52701.989353] eth0: no IPv6 routers present

Ended up giving you all of the mesg instead of editing it, it seems much more convenient. I may have done something trying to get it to work.

Thanks for the reply.

---

### Post by xc3RnbFO8P on 2008-07-04
Did you install V4L-dvb like this:

sudo apt-get install build-essential 

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

cd v4l-dvb 

make all 

sudo make install

---

### Post by tanso on 2008-07-04
> **Ringi said:**
> Did you install V4L-dvb like this:

sudo apt-get install build-essential 

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

cd v4l-dvb 

make all 

sudo make install

What I did was used synaptic package manager, but will try that now.

---

### Post by tanso on 2008-07-04
> **Ringi said:**
> Did you install V4L-dvb like this:

sudo apt-get install build-essential 

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

cd v4l-dvb 

make all 

sudo make install

did cd to... uhh.. there is no such directory

---

### Post by thehandyman33 on 2008-07-18
I'm having the same problem, trying to install hvr-1250 on 8.04 with no success.  I tried v4l drivers as suggested above, with no luck.

lspci -v

```
03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 03)
	Subsystem: Hauppauge computer works Inc. Unknown device 7911
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>

```

So I know it's being recognized by the system, but I can't get any farther.

Does anyone know how to tell if this command

```
sudo modprobe cx23885

```

fails or not?  On my system executing the command doesn't produce any output, and dmesg doesn't seem to change.  dmesg output is:

```
[ 3848.495879] cx23885[0]: mpeg risc op code error
[ 3848.495965] cx23885[0]: TS2 C - dma channel status dump
[ 3848.495975] cx23885[0]:   cmds: init risc lo   : 0x1074f000
[ 3848.495979] cx23885[0]:   cmds: init risc hi   : 0x00000000
[ 3848.495983] cx23885[0]:   cmds: cdt base       : 0x000108d0
[ 3848.495987] cx23885[0]:   cmds: cdt size       : 0x0000000a
[ 3848.495991] cx23885[0]:   cmds: iq base        : 0x00010680
[ 3848.495995] cx23885[0]:   cmds: iq size        : 0x00000010
[ 3848.495999] cx23885[0]:   cmds: risc pc lo     : 0x106291b0
[ 3848.496002] cx23885[0]:   cmds: risc pc hi     : 0x00000000
[ 3848.496006] cx23885[0]:   cmds: iq wr ptr      : 0x000041ac
[ 3848.496010] cx23885[0]:   cmds: iq rd ptr      : 0x000041a0
[ 3848.496013] cx23885[0]:   cmds: cdt current    : 0x000108f8
[ 3848.496017] cx23885[0]:   cmds: pci target lo  : 0x0f9e7f50
[ 3848.496021] cx23885[0]:   cmds: pci target hi  : 0x00000000
[ 3848.496025] cx23885[0]:   cmds: line / byte    : 0x029b0000
[ 3848.496029] cx23885[0]:   risc0: 0x180000b0 [ write sol count=176 ]
[ 3848.496039] cx23885[0]:   risc1: 0x0f9e7f50 [ INVALID sol eol irq2 irq1 23 20 19 18 cnt1 14 13 12 count=3920 ]
[ 3848.496049] cx23885[0]:   risc2: 0x00000000 [ INVALID count=0 ]
[ 3848.496054] cx23885[0]:   risc3: 0x14000240 [ write eol count=576 ]
[ 3848.496060] cx23885[0]:   (0x00010680) iq 0: 0x14000240 [ write eol count=576 ]
[ 3848.496066] cx23885[0]:   iq 1: 0x10628000 [ arg #1 ]
[ 3848.496070] cx23885[0]:   iq 2: 0x00000000 [ arg #2 ]
[ 3848.496074] cx23885[0]:   (0x0001068c) iq 3: 0x1c0002f0 [ write sol eol count=752 ]
[ 3848.496081] cx23885[0]:   iq 4: 0x10628240 [ arg #1 ]
[ 3848.496084] cx23885[0]:   iq 5: 0x00000000 [ arg #2 ]
[ 3848.496088] cx23885[0]:   (0x00010698) iq 6: 0x1c0002f0 [ write sol eol count=752 ]
[ 3848.496093] cx23885[0]:   iq 7: 0x10628530 [ arg #1 ]
[ 3848.496097] cx23885[0]:   iq 8: 0x00000000 [ arg #2 ]
[ 3848.496100] cx23885[0]:   (0x000106a4) iq 9: 0x1c0002f0 [ write sol eol count=752 ]
[ 3848.496107] cx23885[0]:   iq a: 0x10628820 [ arg #1 ]
[ 3848.496111] cx23885[0]:   iq b: 0x00000000 [ arg #2 ]
[ 3848.496115] cx23885[0]:   (0x000106b0) iq c: 0x00000000 [ INVALID count=0 ]
[ 3848.496120] cx23885[0]:   (0x000106b4) iq d: 0x180000b0 [ write sol count=176 ]
[ 3848.496126] cx23885[0]:   iq e: 0x0f9e7f50 [ arg #1 ]
[ 3848.496130] cx23885[0]:   iq f: 0x00000000 [ arg #2 ]
[ 3848.496132] cx23885[0]: fifo: 0x00006000 -> 0x7000
[ 3848.496135] cx23885[0]: ctrl: 0x00010680 -> 0x106e0
[ 3848.496139] cx23885[0]:   ptr1_reg: 0x00006750
[ 3848.496142] cx23885[0]:   ptr2_reg: 0x000108f8
[ 3848.496146] cx23885[0]:   cnt1_reg: 0x00000017
[ 3848.496150] cx23885[0]:   cnt2_reg: 0x00000005

```

---

### Post by xc3RnbFO8P on 2008-07-18
From Hauppauge site:
> Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800
Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800 is in the current kernel 2.6.25 release.

---

### Post by thehandyman33 on 2008-07-18
> **Ringi said:**
> From Hauppauge site:

Um... how does this address the problem we're talking about above?  Have you worked on a 1250 in the current release and found it to be a problem?

UPDATE: video works for me now, after a reboot.  I'm still getting some of the errors and will keep investigating.

---

### Post by xc3RnbFO8P on 2008-07-18
And are you using 2.6.24 ? 
Or did get this tip.tar.gz file?

EDIT:
If you are so close you can try:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
and recompile again.

---

### Post by aaronlenentine on 2008-11-08
This is my very first post, so... gentle, oh yee Ubuntu Coding Wizrds ;-)

I'm having the exact same issue as thehandyman33 details in his July 18th, 2008, post - with the exact same outputs as well.

Hauppauge's official stance on this is what Ringi seems to have already said:

> Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800
Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800 is in the current kernel 2.6.25 release. 

I tried updating the kernel using the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158"), but X Server crashes when I log into that version.  It's been two exhilerating - and frustrating - weeks since I made my way back to linux and I've finally gotten compiz up and running - yeah me and all the many who so diligently help those of us who are so unbelievably ignorant!

At this point, I'm just looking to get this TV Tuner thing up and running so I can move into researching turning this thing into a server and start on migrating my financial files from Quicken to gnash.

But first... I'll *need* to watch TV while I work! ;-)

One thing further I've noticed from where thehandyman33 leaves off, after going through all the updates, modprobes, installs, etc..., when I try and **modprobe cx28835** I get the following:

> root@office:~# sudo modprobe cx23885
FATAL: Error inserting cx23885 (/lib/modules/2.6.24-21-generic/kernel/drivers/media/video/cx23885/cx23885.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I've extracted the two drivers using the instructs found [here]("http://www.steventoth.net/linux/hvr1200/") into /lib/firmware and rebooted *oh soooo many times*.

Here's the output from **sudo lshw -C multimedia**:

> *-multimedia UNCLAIMED
       description: Multimedia video controller
       product: Conexant
       vendor: Conexant
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: latency=0

Last, but I'm guessing not least, obviously I get the blue screen of death when I try and view tvtime, with a message that says no dev/video0.  From all that I've read so far, that basically means my driver hasn't installed correctly.

Thanks in advance for any assistance you guys can provide.  I tried all the distros before I settled on Ubuntu, and honestly one of the selling points was this forum and the support it offers!

---

### Post by clw3388 on 2008-12-16
I too am trying to configure the hvr-1250
attempting Ringi's advise.. 

sudo apt-get update
sudo apt-get install dvb-utils dvbstream

sudo apt-get install mercurial

cd /home
mkdir v4ldvb
cd v4ldvb/
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
make
make install
make reload.. 

rebooted for the heck of it... 
lspci shows 02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)

and lshw -C multimedia shows 
  *-multimedia
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=cx23885 latency=0 module=cx23885

mythtv setup and scanning channels and FREAKING MAGIC it finds a boat load and is working fine.... 

Hey ringi thanks for pointing in general direction of help.. it did set me on the right path.. watch tv still blanks out and wont let me watch.. but at least the backend seems to be working ..

---

### Post by clw3388 on 2008-12-17
After doing a bit more digging.. after above mentioned is complete you must go into the backend and delete your settings and walk through the setup again.. once all setup again and proper drivers are loaded (as followed above) all is well. can watch, record, and do have some free guide features too..

---

### Post by dallas8101 on 2008-12-22
I followed the above directions to install the new HVR1250 card into my existing hardy 8.04 system.  I had a PVR150, PVRUSB2, and a HD5500 in the system already, and was trying to replace the pvr-usb2 which was giving low quality recordings.  Once I finished the install and went into the backend to add the card, all the cards are now marked "failed to load".  If I go into a DVB mode I can see the HD5500.  The only card I see in the dmesg output is the HD5500.  None of the analog modes/cards are seen.

The only changes I made to the instructions was I had to use sudo for the make commands.

I took the card out and rebooted, but it looks like the software install has blocked the analog cards.  Is the v4l-dvb not compatible with the older v4l analog and the the other analog drivers?

---

### Post by dallas8101 on 2008-12-23
It appears there is a load order problem currently with v4l-dvb.  Some discussion is found here:
[http://ubuntuforums.org/showthread.php?t=959407&highlight=v4l-dvb](http://ubuntuforums.org/showthread.php?t=959407&highlight=v4l-dvb)

---

