---
title: "Video to monitor"
date: 2008-07-02
forum: Multimedia Software
---

### Post by Fragger123 on 2008-07-02
Hello all,

I figured this would be the best place to post my question.

I have an old Pinnacle PCTV Pro card laying around,

I wonder if I would be able to connect my xbox composite cable to the video in and show the screen on my monitor, using Ubuntu, preferably a small ubuntu.

Greetings

---

### Post by xc3RnbFO8P on 2008-07-02
First put the Card into the Computer.
In Add/Remove (all available application) install Tvtime.
In Tvtime right click with mouse choose:
Input configuration> Change video source.
If Tvtime doesnt work>   
in terminal, run: 
> dmesg
Show the output.

---

### Post by Fragger123 on 2008-07-02
I will try this, thanks

---

### Post by Fragger123 on 2008-07-02
Ok when I run, tvtime

> Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/fragger/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.


and dmesg output

> [    0.000000] Linux version 2.6.22-15-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Jun 10 09:21:34 UTC 2008 (Ubuntu 2.6.22-15.54-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fbc70
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAB70 checksum 0
[    0.000000] ACPI: RSDP 000FAB70, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 1FFF0120, 32B4 (r1    SiS      746      100 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 005A (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=78e8d3d2-8c28-441b-b74a-948134ad8c40 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1733.296 MHz processor.
[   12.275334] Console: colour VGA+ 80x25
[   12.275781] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.276109] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.295199] Memory: 508172k/524224k available (2016k kernel code, 15436k reserved, 919k data, 364k init, 0k highmem)
[   12.295212] virtual kernel memory layout:
[   12.295213]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.295215]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.295216]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   12.295218]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   12.295219]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.295220]       .data : 0xc02f8036 - 0xc03dde84   ( 919 kB)
[   12.295222]       .text : 0xc0100000 - 0xc02f8036   (2016 kB)
[   12.295226] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.295282] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.375201] Calibrating delay using timer specific routine.. 3468.55 BogoMIPS (lpj=6937106)
[   12.375243] Security Framework v1.0.0 initialized
[   12.375253] SELinux:  Disabled at boot.
[   12.375273] Mount-cache hash table entries: 512
[   12.375456] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   12.375468] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.375472] CPU: L2 Cache: 512K (64 bytes/line)
[   12.375475] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   12.375489] Compat vDSO mapped to ffffe000.
[   12.375506] Checking 'hlt' instruction... OK.
[   12.391359] SMP alternatives: switching to UP code
[   12.391674] Freeing SMP alternatives: 11k freed
[   12.392083] Early unpacking initramfs... done
[   12.759751] ACPI: Core revision 20070126
[   12.759871] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.761428] CPU0: AMD Athlon(tm) XP 2200+ stepping 00
[   12.761454] Total of 1 processors activated (3468.55 BogoMIPS).
[   12.761563] ENABLING IO-APIC IRQs
[   12.761750] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.906607] Brought up 1 CPUs
[   12.906777] Booting paravirtualized kernel on bare hardware
[   12.906857] Time: 20:09:17  Date: 06/02/108
[   12.906892] NET: Registered protocol family 16
[   12.907033] EISA bus registered
[   12.907048] ACPI: bus type pci registered
[   12.908454] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[   12.908457] PCI: Using configuration type 1
[   12.908459] Setting up standard PCI resources
[   12.910505] ACPI: EC: Look up EC in DSDT
[   12.913758] ACPI: Interpreter enabled
[   12.913762] ACPI: (supports S0 S1 S4 S5)
[   12.913788] ACPI: Using IOAPIC for interrupt routing
[   12.918388] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.918400] PCI: Probing PCI hardware (bus 00)
[   12.918590] Enabling SiS 96x SMBus.
[   12.919306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.930728] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   12.930853] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   12.930952] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   12.931048] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   12.931143] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   12.931244] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   12.931342] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   12.931438] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   12.931543] ACPI: Power Resource [URP1] (off)
[   12.931571] ACPI: Power Resource [URP2] (off)
[   12.931598] ACPI: Power Resource [FDDP] (off)
[   12.931624] ACPI: Power Resource [LPTP] (off)
[   12.931635] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.931647] pnp: PnP ACPI init
[   12.931656] ACPI: bus type pnp registered
[   12.934335] pnp: PnP ACPI: found 12 devices
[   12.934338] ACPI: ACPI bus type pnp unregistered
[   12.934343] PnPBIOS: Disabled by ACPI PNP
[   12.934413] PCI: Using ACPI for IRQ routing
[   12.934417] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.938768] NET: Registered protocol family 8
[   12.938771] NET: Registered protocol family 20
[   12.938863] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   12.942500] Time: tsc clocksource has been installed.
[   12.969214] PCI: Bridge: 0000:00:01.0
[   12.969218]   IO window: b000-bfff
[   12.969224]   MEM window: cfd00000-cfefffff
[   12.969229]   PREFETCH window: 8fa00000-cfbfffff
[   12.969268] NET: Registered protocol family 2
[   13.006505] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   13.006588] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   13.006988] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   13.007283] TCP: Hash tables configured (established 16384 bind 16384)
[   13.007286] TCP reno registered
[   13.018556] checking if image is initramfs... it is
[   13.469849] Switched to high resolution mode on CPU 0
[   13.710399] Freeing initrd memory: 7064k freed
[   13.710992] audit: initializing netlink socket (disabled)
[   13.711012] audit(1215029357.044:1): initialized
[   13.713256] VFS: Disk quotas dquot_6.5.1
[   13.713315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.713443] io scheduler noop registered
[   13.713446] io scheduler anticipatory registered
[   13.713449] io scheduler deadline registered
[   13.713465] io scheduler cfq registered (default)
[   13.713518] Boot video device is 0000:01:00.0
[   13.713721] isapnp: Scanning for PnP cards...
[   14.066748] isapnp: No Plug & Play device found
[   14.097180] Real Time Clock Driver v1.12ac
[   14.097319] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.097425] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.098203] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.099160] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.099448] input: Macintosh mouse button emulation as /class/input/input0
[   14.099547] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   14.099875] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.099881] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.100085] mice: PS/2 mouse device common for all mice
[   14.100217] EISA: Probing bus 0 at eisa.0
[   14.100259] EISA: Detected 0 cards.
[   14.100496] TCP cubic registered
[   14.100508] NET: Registered protocol family 1
[   14.100533] Using IPI No-Shortcut mode
[   14.100756]   Magic number: 0:892:193
[   14.100840]   hash matches device ttys5
[   14.101673] Freeing unused kernel memory: 364k freed
[   14.140966] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.336307] AppArmor: AppArmor initialized<5>audit(1215029358.544:2):  type=1505 info="AppArmor initialized" pid=1181
[   15.346309] fuse init (API version 7.8)
[   15.352115] Failure registering capabilities with primary security module.
[   16.027035] SCSI subsystem initialized
[   16.032955] libata version 2.21 loaded.
[   16.034472] pata_sis 0000:00:02.5: version 0.5.1
[   16.034725] scsi0 : pata_sis
[   16.034809] scsi1 : pata_sis
[   16.034964] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   16.034968] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   16.101958] usbcore: registered new interface driver usbfs
[   16.101995] usbcore: registered new interface driver hub
[   16.102027] usbcore: registered new device driver usb
[   16.102905] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.125777] sis900.c: v1.08.10 Apr. 2 2006
[   16.297188] FDC 0 is a post-1991 82077
[   16.529843] ata1.00: ATA-6: WDC WD400BB-00JHC0, 05.01C05, max UDMA/100
[   16.529850] ata1.00: 78165360 sectors, multi 16: LBA 
[   16.529859] ata1.01: ATAPI: LITE-ON DVD SOHD-16P9SV, F$01, max UDMA/33
[   16.529866] ata1.00: limited to UDMA/33 due to 40-wire cable
[   16.537817] ata1.00: configured for UDMA/33
[   16.709508] ata1.01: configured for UDMA/33
[   16.865283] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00JH 05.0 PQ: 0 ANSI: 5
[   16.866212] scsi 0:0:1:0: CD-ROM            LITE-ON  DVD SOHD-16P9SV  F$01 PQ: 0 ANSI: 5
[   16.869431] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   16.869455] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   16.869886] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   16.869914] ohci_hcd 0000:00:03.0: irq 16, io mem 0xcfffd000
[   16.886772] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.886810] sd 0:0:0:0: [sda] Write Protect is off
[   16.886813] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.886836] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.886930] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.886942] sd 0:0:0:0: [sda] Write Protect is off
[   16.886945] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.886964] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.886969]  sda: sda1 sda2 < sda5 >
[   16.918814] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.927157] usb usb1: configuration #1 chosen from 1 choice
[   16.927196] hub 1-0:1.0: USB hub found
[   16.927211] hub 1-0:1.0: 3 ports detected
[   16.927797] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.927974] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   16.946785] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[   16.946795] Uniform CD-ROM driver Revision: 3.20
[   16.947065] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   17.029084] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   17.029109] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   17.029144] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   17.029172] ohci_hcd 0000:00:03.1: irq 17, io mem 0xcfffe000
[   17.086949] usb usb2: configuration #1 chosen from 1 choice
[   17.086990] hub 2-0:1.0: USB hub found
[   17.087004] hub 2-0:1.0: 3 ports detected
[   17.159680] Attempting manual resume
[   17.159686] swsusp: Resume From Partition 8:5
[   17.159688] PM: Checking swsusp image.
[   17.160026] PM: Resume from disk failed.
[   17.178893] EXT3-fs: INFO: recovery required on readonly filesystem.
[   17.178899] EXT3-fs: write access will be enabled during recovery.
[   17.188966] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 18
[   17.188985] ehci_hcd 0000:00:03.2: EHCI Host Controller
[   17.189022] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   17.189079] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[   17.189094] ehci_hcd 0000:00:03.2: irq 18, io mem 0xcffff000
[   17.189103] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.189209] usb usb3: configuration #1 chosen from 1 choice
[   17.189245] hub 3-0:1.0: USB hub found
[   17.189259] hub 3-0:1.0: 6 ports detected
[   17.292810] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   17.293764] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   17.303337] 0000:00:04.0: Using transceiver found at address 1 as default
[   17.304040] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:0b:6a:4f:b9:29.
[   19.508148] kjournald starting.  Commit interval 5 seconds
[   19.508174] EXT3-fs: recovery complete.
[   19.511448] EXT3-fs: mounted filesystem with ordered data mode.
[   29.640322] Linux agpgart interface v0.102 (c) Dave Jones
[   29.671643] agpgart: Detected SiS chipset - id:1862
[   29.676708] agpgart: AGP aperture is 64M @ 0xd0000000
[   29.839346] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   30.183779] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.186836] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.770649] Linux video capture interface: v2.00
[   30.919967] bttv: driver version 0.9.17 loaded
[   30.919975] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   30.920104] bttv: Bt8xx card found (0).
[   30.920143] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 20
[   30.920158] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 20, latency: 32, mmio: 0xcfcfe000
[   30.920171] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   30.920175] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   30.920213] bttv0: gpio: en=00000000, out=00000000 in=00fffbdf [init]
[   30.920564] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   30.920792] bttv0: pinnacle/mt: id=2 info="PAL+SECAM / stereo" radio=yes
[   30.920796] bttv0: using tuner=33
[   30.920801] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   30.944879] msp3400 1-0040: MSP3410G-B11 found @ 0x80 (bt878 #0 [sw])
[   30.944885] msp3400 1-0040: MSP3410G-B11 supports nicam and radio, mode is autodetect and autoselect
[   31.052174] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   31.102741] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   31.140202] tuner 1-0043: chip found @ 0x86 (bt878 #0 [sw])
[   31.140258] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.161150] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[   31.161157] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   31.163686] tuner 1-0060: microtune: companycode=4d54 part=04 rev=04
[   31.207629] tuner 1-0060: microtune MT2032 found, OK
[   31.210093] tuner 1-0060: microtune: companycode=4d54 part=04 rev=04
[   31.253974] tuner 1-0060: microtune MT2032 found, OK
[   31.381528] bttv0: registered device video0
[   31.381573] bttv0: registered device vbi0
[   31.381658] bttv0: registered device radio0
[   31.396273] bttv0: PLL: 28636363 => 35468950 .. ok
[   31.482423] bt878: AUDIO driver version 0.0.0 loaded
[   31.482469] bt878: Bt878 AUDIO function found (0).
[   31.482495] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 18 (level, low) -> IRQ 20
[   31.482504] bt878_probe: card id=[0x1211bd], Unknown card.
[   31.482506] Exiting..
[   31.482512] ACPI: PCI interrupt for device 0000:00:0a.1 disabled
[   31.482519] bt878: probe of 0000:00:0a.1 failed with error -22
[   31.493295] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 20
[   31.506869] input: PS/2 Logitech Mouse as /class/input/input2
[   31.511764] parport_pc 00:0a: reported by Plug and Play ACPI
[   31.511865] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   31.514012] input: PC Speaker as /class/input/input3
[   31.816412] intel8x0_measure_ac97_clock: measured 55383 usecs
[   31.816418] intel8x0: clocking to 48000
[   32.562643] lp0: using parport0 (interrupt-driven).
[   32.616641] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   32.888450] EXT3 FS on sda1, internal journal
[   33.933299] input: Power Button (FF) as /class/input/input4
[   33.939240] ACPI: Power Button (FF) [PWRF]
[   33.985794] input: Power Button (CM) as /class/input/input5
[   33.991687] ACPI: Power Button (CM) [PWRB]
[   34.092989] No dock devices found.
[   35.529451] Failure registering capabilities with primary security module.
[   35.845597] ppdev: user-space parallel port driver
[   36.015531] audit(1215029380.450:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4603 profile="/usr/sbin/cupsd"
[   36.092584] apm: BIOS not found.
[   36.399148] Bluetooth: Core ver 2.11
[   36.399338] NET: Registered protocol family 31
[   36.399342] Bluetooth: HCI device and connection manager initialized
[   36.399347] Bluetooth: HCI socket layer initialized
[   36.423622] Bluetooth: L2CAP ver 2.8
[   36.423630] Bluetooth: L2CAP socket layer initialized
[   36.483376] Bluetooth: RFCOMM socket layer initialized
[   36.483527] Bluetooth: RFCOMM TTY layer initialized
[   36.483530] Bluetooth: RFCOMM ver 1.8
[   37.689207] eth0: Media Link On 100mbps full-duplex 
[   38.126721] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   38.133138] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   38.133665] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   40.708749] NET: Registered protocol family 17
[   46.443060] NET: Registered protocol family 10
[   46.443304] lo: Disabled Privacy Extensions
[   56.535072] eth0: no IPv6 routers present


I already installed the latest ATI drivers off the site, it tells me YUY2 should work with those drivers...

---

### Post by xc3RnbFO8P on 2008-07-02
In Synaptic Package Manager install (search gatos):
Gatos
libgatos0
libgatos-dev

try again

---

### Post by Fragger123 on 2008-07-03
Still gives me the error about YUY2...

---

### Post by xc3RnbFO8P on 2008-07-03
Try this:
> I had the same problem and fixed it by adding the following
lines to the Driver section of /etc/X11/XF86Config-4:
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"

---

### Post by Fragger123 on 2008-07-03
Yeey, it works now, thanks alot dude :)

Cheers

---

