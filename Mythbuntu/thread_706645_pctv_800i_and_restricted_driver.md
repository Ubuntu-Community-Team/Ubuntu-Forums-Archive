---
title: "pctv 800i and restricted driver"
date: 2008-02-24
forum: Mythbuntu
---

### Post by bobbintb on 2008-02-24
after finally getting the pinnacle 800i card installed and mythtv to recognize it, it still wont work. the channel scan says "failed to open card" i looked at the restricted drivers manager and it is enabled but not in use. i searched and found a similar issue with different hardware and they used the "sudo depmod -a" and restarted. i tried it and no luck. tried disabling and re-enabling. nothing. i have mythbuntu 7.10 and very little linux experience. anyone got any ideas?  ive exhausted all my abilities and research has turned up nothing.

---

### Post by bobbintb on 2008-02-25
any help would be appreciated.

---

### Post by curryrice71 on 2008-02-25
Believe it or not I have 2 of these cards running. Did you get the firmware for it?

---

### Post by bobbintb on 2008-02-25
yea i downloaded the firmware from [http://linuxtv.org/hg/v4l-dvb]("http://linuxtv.org/hg/v4l-dvb") and the drivers from [http://www.steventoth.net/linux/xc5000/]("http://www.steventoth.net/linux/xc5000/").

followed the instructions on [http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)]("http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)")

after sorting through some dependencies issues, this is where im at. i just cant get the driver to be used.

---

### Post by curryrice71 on 2008-02-25
can you post your kernel output or e-mail it to me?

---

### Post by bobbintb on 2008-02-26
> **curryrice71 said:**
> can you post your kernel output or e-mail it to me?

where would i find that? /var/log/messages ?

---

### Post by curryrice71 on 2008-02-26
just open a terminal and type "dmesg" and it will output all of the messages from the kernel from bootup until the present.

---

### Post by bobbintb on 2008-02-26
here you go:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000080000 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dfec000 (usable)
[    0.000000]  BIOS-e820: 000000001dfec000 - 000000001dfef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfef000 - 000000001dfff000 (reserved)
[    0.000000]  BIOS-e820: 000000001dfff000 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 122860) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122860
[    0.000000]   HighMem    122860 ->   122860
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122860
[    0.000000] On node 0 totalpages: 122860
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117837 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7FF0 checksum 0
[    0.000000] ACPI: RSDP 000F7FF0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1DFEC000, 0030 (r1 ASUS   A7N266VM 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 1DFEC100, 0074 (r1 ASUS   A7N266VM 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 1DFEC180, 2A64 (r1   ASUS A7N266VM     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1DFFF000, 0040
[    0.000000] ACPI: BOOT 1DFEC040, 0028 (r1 ASUS   A7N266VM 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 1DFEC080, 005A (r1 ASUS   A7N266VM 42302E31 MSFT 31313031)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] Built 1 zonelists.  Total pages: 121901
[    0.000000] Kernel command line: root=UUID=5f08be7c-00fa-4230-ac74-cd2789610af6 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1529.395 MHz processor.
[   17.960319] Console: colour VGA+ 80x25
[   17.960793] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.961172] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.977501] Memory: 475408k/491440k available (2015k kernel code, 15336k reserved, 915k data, 364k init, 0k highmem)
[   17.977516] virtual kernel memory layout:
[   17.977517]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   17.977519]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.977521]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   17.977522]     lowmem  : 0xc0000000 - 0xddfec000   ( 479 MB)
[   17.977524]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   17.977526]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   17.977528]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   17.977532] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.977587] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.057551] Calibrating delay using timer specific routine.. 3061.39 BogoMIPS (lpj=6122788)
[   18.057590] Security Framework v1.0.0 initialized
[   18.057599] SELinux:  Disabled at boot.
[   18.057621] Mount-cache hash table entries: 512
[   18.057797] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   18.057810] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.057813] CPU: L2 Cache: 256K (64 bytes/line)
[   18.057817] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   18.057831] Compat vDSO mapped to ffffe000.
[   18.057847] Checking 'hlt' instruction... OK.
[   18.073712] SMP alternatives: switching to UP code
[   18.074066] Freeing SMP alternatives: 11k freed
[   18.074557] Early unpacking initramfs... done
[   18.488221] ACPI: Core revision 20070126
[   18.488336] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.489939] CPU0: AMD Athlon(TM) XP 1800+ stepping 00
[   18.489969] Total of 1 processors activated (3061.39 BogoMIPS).
[   18.490157] ENABLING IO-APIC IRQs
[   18.490363] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   18.637196] Brought up 1 CPUs
[   18.637376] Booting paravirtualized kernel on bare hardware
[   18.637465] Time:  4:08:15  Date: 01/27/108
[   18.637508] NET: Registered protocol family 16
[   18.637653] EISA bus registered
[   18.637668] ACPI: bus type pci registered
[   18.638887] PCI: PCI BIOS revision 2.10 entry at 0xf1ab0, last bus=2
[   18.638890] PCI: Using configuration type 1
[   18.638893] Setting up standard PCI resources
[   18.649329] ACPI: EC: Look up EC in DSDT
[   18.653075] ACPI: Interpreter enabled
[   18.653081] ACPI: (supports S0 S1 S3 S4 S5)
[   18.653102] ACPI: Using IOAPIC for interrupt routing
[   18.665111] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.665134] PCI: Probing PCI hardware (bus 00)
[   18.666169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.666284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   18.666505] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   18.707206] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 18) *5
[   18.707407] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 18) *0, disabled.
[   18.707602] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 18) *0, disabled.
[   18.707796] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 18) *5
[   18.707993] ACPI: PCI Interrupt Link [LNKE] (IRQs 19) *11
[   18.708186] ACPI: PCI Interrupt Link [LNKF] (IRQs 20 21 22) *5
[   18.708379] ACPI: PCI Interrupt Link [LNKU] (IRQs 20 21 22) *10
[   18.708580] ACPI: PCI Interrupt Link [LNKI] (IRQs 20 21 22) *10
[   18.708779] ACPI: PCI Interrupt Link [LNKJ] (IRQs 20 21 22) *5
[   18.708977] ACPI: PCI Interrupt Link [LNKK] (IRQs 20 21 22) *11
[   18.709188] ACPI: PCI Interrupt Link [LNKM] (IRQs 20 21 22) *0, disabled.
[   18.709302] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.709320] pnp: PnP ACPI init
[   18.709333] ACPI: bus type pnp registered
[   18.715886] pnp: PnP ACPI: found 17 devices
[   18.715890] ACPI: ACPI bus type pnp unregistered
[   18.715896] PnPBIOS: Disabled by ACPI PNP
[   18.715991] PCI: Using ACPI for IRQ routing
[   18.715996] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.724210] NET: Registered protocol family 8
[   18.724213] NET: Registered protocol family 20
[   18.724309] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   18.724314] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   18.724318] pnp: 00:00: iomem range 0x100000-0x1dffffff could not be reserved
[   18.724322] pnp: 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   18.724331] pnp: 00:02: ioport range 0xe400-0xe4fe has been reserved
[   18.724335] pnp: 00:02: ioport range 0xe4ff-0xe4ff has been reserved
[   18.724339] pnp: 00:02: ioport range 0xcf0-0xcf3 has been reserved
[   18.724343] pnp: 00:02: iomem range 0xffc00000-0xffffffff could not be reserved
[   18.724361] pnp: 00:0f: ioport range 0x370-0x371 has been reserved
[   18.725071] Time: tsc clocksource has been installed.
[   18.754751] PCI: Bridge: 0000:00:08.0
[   18.754754]   IO window: b000-bfff
[   18.754761]   MEM window: ea000000-ecffffff
[   18.754765]   PREFETCH window: disabled.
[   18.754771] PCI: Bridge: 0000:00:1e.0
[   18.754773]   IO window: disabled.
[   18.754778]   MEM window: e9000000-e9ffffff
[   18.754782]   PREFETCH window: eff00000-f7ffffff
[   18.754796] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.754803] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.754819] NET: Registered protocol family 2
[   18.793101] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.793184] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   18.793536] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.793801] TCP: Hash tables configured (established 16384 bind 16384)
[   18.793805] TCP reno registered
[   18.805242] checking if image is initramfs... it is
[   19.256709] Switched to high resolution mode on CPU 0
[   19.591195] Freeing initrd memory: 7217k freed
[   19.591370] Simple Boot Flag at 0x3f set to 0x1
[   19.591834] audit: initializing netlink socket (disabled)
[   19.591857] audit(1204085295.144:1): initialized
[   19.594350] VFS: Disk quotas dquot_6.5.1
[   19.594421] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.594570] io scheduler noop registered
[   19.594573] io scheduler anticipatory registered
[   19.594576] io scheduler deadline registered
[   19.594594] io scheduler cfq registered (default)
[   19.608317] Boot video device is 0000:02:00.0
[   19.608573] isapnp: Scanning for PnP cards...
[   19.962525] isapnp: No Plug & Play device found
[   19.995602] Real Time Clock Driver v1.12ac
[   19.995748] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.995865] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.996241] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.996994] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.997385] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.998367] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.998689] input: Macintosh mouse button emulation as /class/input/input0
[   19.998806] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.002233] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.002244] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.002522] mice: PS/2 mouse device common for all mice
[   20.002687] EISA: Probing bus 0 at eisa.0
[   20.002718] Cannot allocate resource for EISA slot 5
[   20.002734] EISA: Detected 0 cards.
[   20.002891] TCP cubic registered
[   20.002903] NET: Registered protocol family 1
[   20.002933] Using IPI No-Shortcut mode
[   20.003200]   Magic number: 12:489:111
[   20.004055] Freeing unused kernel memory: 364k freed
[   20.040007] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.255999] AppArmor: AppArmor initialized<5>audit(1204085297.144:2):  type=1505 info="AppArmor initialized" pid=1137
[   21.264129] fuse init (API version 7.8)
[   21.270413] Failure registering capabilities with primary security module.
[   22.048230] usbcore: registered new interface driver usbfs
[   22.048269] usbcore: registered new interface driver hub
[   22.048299] usbcore: registered new device driver usb
[   22.049358] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.049759] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 22
[   22.049772] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 16
[   22.049790] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.049796] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   22.050046] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   22.050070] ohci_hcd 0000:00:02.0: irq 16, io mem 0xef000000
[   22.106901] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   22.132932] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.132941] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.172630] usb usb1: configuration #1 chosen from 1 choice
[   22.172679] hub 1-0:1.0: USB hub found
[   22.172696] hub 1-0:1.0: 3 ports detected
[   22.274217] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 16
[   22.274240] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.274245] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   22.274278] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[   22.274298] ohci_hcd 0000:00:03.0: irq 16, io mem 0xee800000
[   22.302994] Floppy drive(s): fd0 is 1.44M
[   22.332104] usb usb2: configuration #1 chosen from 1 choice
[   22.332143] hub 2-0:1.0: USB hub found
[   22.332156] hub 2-0:1.0: 3 ports detected
[   22.370705] FDC 0 is a post-1991 82077
[   22.434550] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 21
[   22.434566] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKI] -> GSI 21 (level, high) -> IRQ 17
[   22.434575] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   22.953669] eth0: forcedeth.c: subsystem: 01043:0c11 bound to 0000:00:04.0
[   22.954170] NFORCE: IDE controller at PCI slot 0000:00:09.0
[   22.954204] NFORCE: chipset revision 195
[   22.954207] NFORCE: not 100% native mode: will probe irqs later
[   22.954213] NFORCE: BIOS didn't set cable bits correctly. Enabling workaround.
[   22.954221] NFORCE: 0000:00:09.0 (rev c3) UDMA100 controller
[   22.954235]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:pio
[   22.954247]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:DMA
[   22.954259] Probing IDE interface ide0...
[   23.241251] hda: Maxtor 6Y080L0, ATA DISK drive
[   23.912803] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.925648] Probing IDE interface ide1...
[   24.660028] hdc: LITE-ON LTR-48246S, ATAPI CD/DVD-ROM drive
[   25.443328] hdd: CD-540E, ATAPI CD/DVD-ROM drive
[   25.502893] ide1 at 0x170-0x177,0x376 on irq 15
[   25.522222] SCSI subsystem initialized
[   25.529778] libata version 2.21 loaded.
[   25.543599] hda: max request size: 128KiB
[   25.561002] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   25.562752] hda: cache flushes supported
[   25.562827]  hda: hda1 hda2 < hda5 >
[   25.613091] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.613104] Uniform CD-ROM driver Revision: 3.20
[   25.653357] hdd: ATAPI 40X CD-ROM drive, 128kB Cache, UDMA(33)
[   25.817288] Attempting manual resume
[   25.817294] swsusp: Resume From Partition 3:5
[   25.817296] PM: Checking swsusp image.
[   25.817502] PM: Resume from disk failed.
[   25.869037] kjournald starting.  Commit interval 5 seconds
[   25.869056] EXT3-fs: mounted filesystem with ordered data mode.
[   32.429735] Linux agpgart interface v0.102 (c) Dave Jones
[   32.435068] agpgart: Detected NVIDIA nForce chipset
[   32.439763] agpgart: AGP aperture is 64M @ 0xf8000000
[   33.241923] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.244231] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.037008] input: PC Speaker as /class/input/input2
[   34.451666] Linux video capture interface: v2.00
[   34.532190] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   34.532634] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   34.532647] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 18 (level, high) -> IRQ 18
[   34.532727] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected]
[   34.532732] cx88[0]: TV tuner type 76, Radio tuner type -1
[   34.603808] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   34.684030] input: cx88 IR (Pinnacle PCTV HD 800i) as /class/input/input3
[   34.684089] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 18, latency: 64, mmio: 0xec000000
[   34.685608] cx2388x alsa driver version 0.0.6 loaded
[   34.837606] input: PS/2 Generic Mouse as /class/input/input4
[   34.842215] parport_pc 00:0a: reported by Plug and Play ACPI
[   34.842301] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.990157] tuner' 1-0064: chip found @ 0xc8 (cx88[0])
[   34.990994] xc5000: Successfully identified at address 0x64
[   34.990997] xc5000: Firmware has not been loaded previously
[   34.991002] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   35.037374] xc5000: firmware read 12332 bytes.
[   35.037380] xc5000: firmware upload
[   39.760646] cx88[0]/0: registered device video0 [v4l2]
[   39.760699] cx88[0]/0: registered device vbi0
[   41.849233] cx88[0]/2: cx2388x 8802 Driver Manager
[   41.849269] ACPI: PCI Interrupt 0000:01:06.2[A] -> Link [LNKA] -> GSI 18 (level, high) -> IRQ 18
[   41.849284] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 18, latency: 64, mmio: 0xea000000
[   41.851339] ACPI: PCI Interrupt 0000:01:06.1[A] -> Link [LNKA] -> GSI 18 (level, high) -> IRQ 18
[   41.851387] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   41.852103] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[   41.852471] ACPI: PCI Interrupt Link [LNKK] enabled at IRQ 20
[   41.852482] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKK] -> GSI 20 (level, high) -> IRQ 19
[   41.852520] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.919062] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   41.919069] cx88/2: registering cx8802 driver, type: dvb access: shared
[   41.919075] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   41.919080] cx88[0]/2: cx2388x based DVB/ATSC card
[   41.980816] xc5000: Successfully identified at address 0x64
[   41.980821] xc5000: Firmware has been loaded previously
[   41.981779] DVB: registering new adapter (cx88[0])
[   41.981788] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   42.180603] intel8x0_measure_ac97_clock: measured 52616 usecs
[   42.180611] intel8x0: clocking to 47503
[   43.295677] lp0: using parport0 (interrupt-driven).
[   43.525631] Adding 1405648k swap on /dev/hda5.  Priority:-1 extents:1 across:1405648k
[   43.969657] EXT3 FS on hda1, internal journal
[   45.878532] input: Power Button (FF) as /class/input/input5
[   45.884005] ACPI: Power Button (FF) [PWRF]
[   45.935526] input: Power Button (CM) as /class/input/input6
[   45.940959] ACPI: Power Button (CM) [PWRB]
[   46.138214] No dock devices found.
[   50.250327] NET: Registered protocol family 10
[   50.250816] lo: Disabled Privacy Extensions
[   63.984863] NET: Registered protocol family 17
[   78.816610] eth0: no IPv6 routers present

```

---

### Post by jmore9 on 2008-02-29
Hello !

I have gotten the board to be 'seen' by ubuntu by using the setup on this page [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

I have gotten all the way to the scanning  to make a channels.conf file but i have the following problem.  The scan just stops at this point .  anyone have any ideas.  

jeff@jeff-desktop:~$ scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB | tee mychannels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB
service is running. Channel number: 35:1. Name: 'WGVU-HD&#65533;'
service is running. Channel number: 35:2. Name: 'WGVU-SD&#65533;'
service is running. Channel number: 35:3. Name: 'WGVUSD2&#65533;'
service is running. Channel number: 35:4. Name: 'WGVUSD3&#65533;

The page above gives step by step instructions on how to install Mercurial, dvb tree (i thinks its called that) , and the driver for this card.  I also could not get the extractor to work without logging in as root ?? If anyone has any ideas on how to create a channels.conf i looking for ideas.

jmor9651

---

### Post by curryrice71 on 2008-02-29
bobbintb,

Your kernel output looks good. Have you downloaded the very latest version of the dvb drivers from linuxtv.org/hg/vl4-dvb?

---

### Post by curryrice71 on 2008-02-29
what kind of capture card did you add it as in MythTV?

---

### Post by jmore9 on 2008-03-01
I did not have to add anything

my dmesg for the 800i part is as follows:

[   36.852375] Linux video capture interface: v2.00
[   37.320332] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   37.320453] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected]
[   37.320457] cx88[0]: TV tuner type 76, Radio tuner type -1
[   37.390686] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   37.624154] cx2388x alsa driver version 0.0.6 loaded
[   38.021553] input: PC Speaker as /class/input/input2
[   38.273972] tuner' 0-0064: chip found @ 0xc8 (cx88[0])
[   38.274637] xc5000: Successfully identified at address 0x64
[   38.274640] xc5000: Firmware has not been loaded previously
[   38.274643] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   38.461256] xc5000: firmware read 12332 bytes.
[   38.461260] xc5000: firmware upload
[   38.461264] cx88[0]: Calling XC5000 callback
[   38.780442] input: PS/2 Logitech Mouse as /class/input/input3
[   38.786753] parport_pc 00:0a: reported by Plug and Play ACPI
[   38.786796] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.009791] input: cx88 IR (Pinnacle PCTV HD 800i) as /class/input/input4
[   43.009950] cx88[0]/2: cx2388x 8802 Driver Manager
[   43.009968] ACPI: PCI Interrupt 0000:00:09.2[A] -> GSI 19 (level, low) -> IRQ 20
[   43.009977] cx88[0]/2: found at 0000:00:09.2, rev: 5, irq: 20, latency: 32, mmio: 0xec000000
[   43.010068] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 19 (level, low) -> IRQ 20
[   43.010095] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   43.011223] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 19 (level, low) -> IRQ 20
[   43.011235] cx88[0]/0: found at 0000:00:09.0, rev: 5, irq: 20, latency: 32, mmio: 0xea000000
[   43.011451] cx88[0]/0: registered device video0 [v4l2]
[   43.011597] cx88[0]/0: registered device vbi0
[   43.078717] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   43.078722] cx88/2: registering cx8802 driver, type: dvb access: shared
[   43.078727] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   43.078731] cx88[0]/2: cx2388x based DVB/ATSC card
[   43.176129] xc5000: Successfully identified at address 0x64
[   43.176134] xc5000: Firmware has been loaded previously
[   43.176920] DVB: registering new adapter (cx88[0])
[   43.176924] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...

as i said in previous post the insrructions on link provided worked for me.

---

### Post by bobbintb on 2008-03-02
> **curryrice71 said:**
> bobbintb,

Your kernel output looks good. Have you downloaded the very latest version of the dvb drivers from linuxtv.org/hg/vl4-dvb?

yea i did. its installed fine as far as i can tell, its just not using the driver.

---

### Post by bobbintb on 2008-03-07
still having the issue if anyone can help.

---

### Post by Lutiana on 2008-03-08
Did you specify the type of TV signal in the Mythbuntu Setup?

When I got my 800i installed and did a scan it only found about 10 channels. This was because I had the TV signal set to broadcast. I changed this to us cable and I now have all my channels.

Hope this helps.

---

### Post by bobbintb on 2008-03-10
> **Lutiana said:**
> Did you specify the type of TV signal in the Mythbuntu Setup?

When I got my 800i installed and did a scan it only found about 10 channels. This was because I had the TV signal set to broadcast. I changed this to us cable and I now have all my channels.

Hope this helps.
yes i did. like i said, mythtv recognized the card buti cant get anything because the driver isnt in use. i went to the restricted drivers manager and the driver in enabled but not in use (whatever that means). i tried sudo depmod -a and that didnt work either.

---

