---
title: "dell latitude cpi d300xt + fluxbuntu = no sound :("
date: 2009-01-05
forum: Multimedia Software
---

### Post by gfxcoder on 2009-01-05
i've installed fluxbuntu on my old latitude cpi, but i cannot get the audio to work at all.  i've searched through the forums and found some that got it working, but it doesn't seem to be working for me.

here are just two of the forums that i tried:
[http://ubuntuforums.org/showthread.php?t=90869](http://ubuntuforums.org/showthread.php?t=90869)
[http://ubuntuforums.org/showthread.php?t=188736](http://ubuntuforums.org/showthread.php?t=188736)

the only thing that happened after making the changes was my standby quit working (it would go to black screen with blinking cursor... had to reboot)

so, after undoing/commenting all (i think) the changes and getting back to square one, here are some dumps.  hopefully someone can help me find what i'm not seeing!

dmesg
```

[    0.000000] Linux version 2.6.22-16-386 (buildd@rothera) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Mon Nov 24 17:51:40 GMT 2008 (Ubuntu 2.6.22-16.60-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000008000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 127MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32752) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32752
[    0.000000]   HighMem     32752 ->    32752
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32752
[    0.000000] On node 0 totalpages: 32752
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 223 pages used for memmap
[    0.000000]   Normal zone: 28433 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F3CF0 checksum 0
[    0.000000] ACPI: RSDP 000F3CF0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 07FF0000, 0028 (r1 DELL    CPi     27D10B07 ASL        61)
[    0.000000] ACPI: FACP 07FF0400, 0074 (r1 DELL    CPi     27D10B07 ASL        61)
[    0.000000] ACPI: DSDT 07FF0800, 2DE4 (r1 INT430 SYSFexxx     1001 MSFT  100000C)
[    0.000000] ACPI: FACS 07FFF800, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efd00000)
[    0.000000] Built 1 zonelists.  Total pages: 32497
[    0.000000] Kernel command line: root=UUID=9b9a4332-1cae-4f03-9847-dad97a29a7d2 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (01101000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 300.707 MHz processor.
[   74.236419] Console: colour VGA+ 80x25
[   74.237195] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   74.237779] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   74.267282] Memory: 118804k/131008k available (1930k kernel code, 11712k reserved, 876k data, 348k init, 0k highmem)
[   74.267351] virtual kernel memory layout:
[   74.267359]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   74.267369]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   74.267379]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   74.267389]     lowmem  : 0xc0000000 - 0xc7ff0000   ( 127 MB)
[   74.267399]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   74.267408]       .data : 0xc02e2825 - 0xc03bda04   ( 876 kB)
[   74.267418]       .text : 0xc0100000 - 0xc02e2825   (1930 kB)
[   74.267439] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   74.267752] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   74.347806] Calibrating delay using timer specific routine.. 602.13 BogoMIPS (lpj=1204268)
[   74.347980] Security Framework v1.0.0 initialized
[   74.348038] SELinux:  Disabled at boot.
[   74.348083] Mount-cache hash table entries: 512
[   74.348725] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   74.348793] CPU: L1 I cache: 16K, L1 D cache: 16K
[   74.348809] CPU: L2 cache: 512K
[   74.348828] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   74.348890] Compat vDSO mapped to ffffe000.
[   74.348965] CPU: Intel Pentium II (Deschutes) stepping 02
[   74.348997] Checking 'hlt' instruction... OK.
[   74.366419] Early unpacking initramfs... done
[   76.567280] ACPI: Core revision 20070126
[   76.567861] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   76.576003] ACPI: setting ELCR to 0200 (from 0800)
[   76.580262] Booting paravirtualized kernel on bare hardware
[   76.580611] Time:  2:22:57  Date: 00/06/109
[   76.580802] NET: Registered protocol family 16
[   76.581426] EISA bus registered
[   76.581475] ACPI: bus type pci registered
[   76.586730] PCI: PCI BIOS revision 2.10 entry at 0xfbc7e, last bus=0
[   76.586747] PCI: Using configuration type 1
[   76.586760] Setting up standard PCI resources
[   76.595466] ACPI: EC: Look up EC in DSDT
[   76.677753] ACPI: Interpreter enabled
[   76.677779] ACPI: (supports S0 S1 S3 S4 S5)
[   76.677900] ACPI: Using PIC for interrupt routing
[   76.794231] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   76.794337] PCI: Probing PCI hardware (bus 00)
[   76.795179] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   76.795192] * this clock source is slow. Consider trying other clock sources
[   76.795281] PCI quirk: region 0800-083f claimed by PIIX4 ACPI
[   76.795300] PCI quirk: region 0840-084f claimed by PIIX4 SMB
[   76.795321] PIIX4 devres B PIO at 00e0-00e7
[   76.795336] PIIX4 devres C PIO at 0850-085f
[   76.795352] PIIX4 devres I PIO at 0210-0217
[   76.795367] PIIX4 devres J PIO at 0388-038b
[   76.795972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   76.953827] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   76.954506] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   76.955184] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   76.956004] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   76.956827] ACPI: Power Resource [PADA] (on)
[   76.956883] Linux Plug and Play Support v0.97 (c) Adam Belay
[   76.956950] pnp: PnP ACPI init
[   76.957004] ACPI: bus type pnp registered
[   77.260330] pnp: PnP ACPI: found 17 devices
[   77.260348] ACPI: ACPI bus type pnp unregistered
[   77.260375] PnPBIOS: Disabled by ACPI PNP
[   77.260722] PCI: Using ACPI for IRQ routing
[   77.260745] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   77.263104] NET: Registered protocol family 8
[   77.263122] NET: Registered protocol family 20
[   77.263475] Time: tsc clocksource has been installed.
[   77.263604] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[   77.263628] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   77.263649] pnp: 00:00: iomem range 0xc0000-0xcbfff could not be reserved
[   77.263670] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   77.263711] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   77.263732] pnp: 00:02: ioport range 0x800-0x805 has been reserved
[   77.263751] pnp: 00:02: ioport range 0x808-0x80f has been reserved
[   77.263786] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[   77.263806] pnp: 00:03: ioport range 0x850-0x853 has been reserved
[   77.263825] pnp: 00:03: ioport range 0x856-0x85f has been reserved
[   77.263844] pnp: 00:03: ioport range 0x810-0x83f has been reserved
[   77.263863] pnp: 00:03: ioport range 0x840-0x84f has been reserved
[   77.263900] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[   77.263923] pnp: 00:04: iomem range 0xed000000-0xedffffff has been reserved
[   77.263971] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[   77.296419] PCI: Bus 1, cardbus bridge: 0000:00:03.0
[   77.296439]   IO window: 00001000-000010ff
[   77.296457]   IO window: 00001400-000014ff
[   77.296476]   PREFETCH window: 20000000-23ffffff
[   77.296494]   MEM window: 24000000-27ffffff
[   77.296510] PCI: Bus 5, cardbus bridge: 0000:00:03.1
[   77.296525]   IO window: 00001800-000018ff
[   77.296541]   IO window: 00001c00-00001cff
[   77.296559]   PREFETCH window: 28000000-2bffffff
[   77.296577]   MEM window: 2c000000-2fffffff
[   77.296607] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[   77.297787] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   77.297811] PCI: setting IRQ 11 as level-triggered
[   77.297828] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   77.297872] PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
[   77.297892] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   77.297979] NET: Registered protocol family 2
[   77.335635] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   77.335883] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   77.336214] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[   77.336386] TCP: Hash tables configured (established 4096 bind 4096)
[   77.336404] TCP reno registered
[   77.348217] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   79.244732]  it is
[   81.539359] Freeing initrd memory: 7014k freed
[   81.541595] audit: initializing netlink socket (disabled)
[   81.541696] audit(1231208581.272:1): initialized
[   81.559831] VFS: Disk quotas dquot_6.5.1
[   81.559964] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   81.560750] io scheduler noop registered
[   81.560770] io scheduler anticipatory registered
[   81.560785] io scheduler deadline registered
[   81.560965] io scheduler cfq registered (default)
[   81.561027] Limiting direct PCI/PCI transfers.
[   81.561061] Boot video device is 0000:00:02.0
[   81.562073] isapnp: Scanning for PnP cards...
[   81.916221] isapnp: No Plug & Play device found
[   82.145824] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   82.146191] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   82.150734] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   82.156438] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   82.157435] input: Macintosh mouse button emulation as /class/input/input0
[   82.158031] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   82.172472] serio: i8042 KBD port at 0x60,0x64 irq 1
[   82.172505] serio: i8042 AUX port at 0x60,0x64 irq 12
[   82.173762] mice: PS/2 mouse device common for all mice
[   82.174565] EISA: Probing bus 0 at eisa.0
[   82.174651] Cannot allocate resource for EISA slot 1
[   82.174721] EISA: Detected 0 cards.
[   82.175422] TCP cubic registered
[   82.175530] NET: Registered protocol family 1
[   82.175686] Using IPI Shortcut mode
[   82.176601]   Magic number: 9:449:358
[   82.179943] Freeing unused kernel memory: 348k freed
[   82.180128] Write protecting the kernel read-only data: 712k
[   82.190775] input: AT Translated Set 2 keyboard as /class/input/input1
[   84.456096] AppArmor: AppArmor initialized<5>audit(1231208584.188:2):  type=1505 info="AppArmor initialized" pid=1118
[   84.522574] fuse init (API version 7.8)
[   84.560869] Failure registering capabilities with primary security module.
[   84.651085] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   84.685120] ACPI: Thermal Zone [THM] (25 C)
[   98.113051] SCSI subsystem initialized
[   98.194471] libata version 2.21 loaded.
[   98.217605] ata_piix 0000:00:07.1: version 2.11
[   98.218689] scsi0 : ata_piix
[   98.219003] scsi1 : ata_piix
[   98.220197] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00010860 irq 14
[   98.220274] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00010868 irq 15
[   98.346111] usbcore: registered new interface driver usbfs
[   98.346273] usbcore: registered new interface driver hub
[   98.346446] usbcore: registered new device driver usb
[   98.356921] USB Universal Host Controller Interface driver v3.0
[   98.722102] ata1.00: ATA-4: IBM-DKLA-24320, KL4OA42A, max UDMA/33
[   98.722136] ata1.00: 8452080 sectors, multi 8: LBA 
[   98.764781] ata1.00: configured for UDMA/33
[   99.124501] ata2.00: ATAPI: TOSHIBA CD-ROM XM-1802B, 1915, max MWDMA2, CDB intr
[   99.360493] ata2.00: configured for MWDMA2
[   99.368320] scsi 0:0:0:0: Direct-Access     ATA      IBM-DKLA-24320   KL4O PQ: 0 ANSI: 5
[   99.414746] scsi 1:0:0:0: CD-ROM            TOSHIBA  CD-ROM XM-1802B  1915 PQ: 0 ANSI: 5
[   99.436316] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   99.436388] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   99.437240] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   99.437339] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000ece0
[   99.438214] usb usb1: configuration #1 chosen from 1 choice
[   99.438420] hub 1-0:1.0: USB hub found
[   99.438491] hub 1-0:1.0: 2 ports detected
[   99.780120] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   99.869750] Floppy drive(s): fd0 is 1.44M
[   99.956067] usb 1-1: configuration #1 chosen from 1 choice
[  100.008712] FDC 0 is a post-1991 82077
[  100.677861] sd 0:0:0:0: [sda] 8452080 512-byte hardware sectors (4327 MB)
[  100.679943] sd 0:0:0:0: [sda] Write Protect is off
[  100.679965] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  100.687951] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  100.695912] sd 0:0:0:0: [sda] 8452080 512-byte hardware sectors (4327 MB)
[  100.699906] sd 0:0:0:0: [sda] Write Protect is off
[  100.699927] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  100.707908] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  100.707946]  sda: sda1 sda2 < sda5 >
[  100.754717] sd 0:0:0:0: [sda] Attached SCSI disk
[  101.017440] usbcore: registered new interface driver hiddev
[  101.050066] input: Logitech USB Optical Mouse as /class/input/input2
[  101.051076] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:07.2-1
[  101.051180] usbcore: registered new interface driver usbhid
[  101.051205] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  101.230985] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[  101.231024] Uniform CD-ROM driver Revision: 3.20
[  101.231384] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  101.412500] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  101.412648] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  103.534600] Attempting manual resume
[  103.534626] swsusp: Resume From Partition 8:5
[  103.534639] PM: Checking swsusp image.
[  103.631453] PM: Resume from disk failed.
[  104.367753] kjournald starting.  Commit interval 5 seconds
[  104.367833] EXT3-fs: mounted filesystem with ordered data mode.
[  215.570759] Yenta: CardBus bridge found at 0000:00:03.0 [1028:0074]
[  215.699666] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[  215.699697] Socket status: 30000006
[  215.700761] Yenta: CardBus bridge found at 0000:00:03.1 [1028:0074]
[  215.827556] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[  215.827581] Socket status: 30000010
[  216.462828] pccard: PCMCIA card inserted into slot 1
[  219.234301] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  222.034007] input: PC Speaker as /class/input/input3
[  222.070688] Real Time Clock Driver v1.12ac
[  222.175436] Synaptics Touchpad, model: 1, fw: 4.2, id: 0x844a1, caps: 0x0/0x0
[  222.234328] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  224.715656] parport_pc 00:0e: reported by Plug and Play ACPI
[  224.715762] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[  226.005642] cs: IO port probe 0x100-0x3af: excluding 0x210-0x217 0x220-0x22f 0x388-0x38f
[  226.007014] cs: IO port probe 0x3e0-0x4ff: clean.
[  226.007707] cs: IO port probe 0x820-0x8ff: clean.
[  226.008225] cs: IO port probe 0xc00-0xcf7: clean.
[  226.009575] cs: IO port probe 0xa00-0xaff: clean.
[  226.010264] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  226.020742] pcmcia: registering new device pcmcia1.0
[  226.024465] cs: IO port probe 0x100-0x3af: excluding 0x210-0x217 0x220-0x22f 0x388-0x38f
[  226.621731] cs: IO port probe 0x3e0-0x4ff: clean.
[  226.622445] cs: IO port probe 0x820-0x8ff: clean.
[  226.622965] cs: IO port probe 0xc00-0xcf7: clean.
[  226.624282] cs: IO port probe 0xa00-0xaff: clean.
[  229.047270] CS4232 WSS PnP manual resources are invalid, using auto config
[  229.047309] CS4232 WSS PnP configure failed for WSS (out of resources?)
[  229.047326] PnP BIOS detection failed for CS4232
[  229.053425] pnp: Device 00:10 disabled.
[  229.053466] cs4232-pnpbios: probe of 00:10 failed with error -16
[  231.569334] eth%d: MII link partner: 41e1
[  231.569362] eth%d: MII selected
[  231.592583] eth%d: media 100BaseT, silicon revision 5
[  231.594844] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:79:79:7E
[  231.594956] pcmcia: registering new device pcmcia1.1
[  231.740219] 1.1: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[  234.532872] eth0: MII link partner: 41e1
[  234.532899] eth0: MII selected
[  234.556162] eth0: media 100BaseT, silicon revision 5
[  234.807806] loop: module loaded
[  234.997943] lp0: using parport0 (interrupt-driven).
[  236.975048] NET: Registered protocol family 10
[  236.975742] lo: Disabled Privacy Extensions
[  237.193307] Adding 240932k swap on /dev/sda5.  Priority:-1 extents:1 across:240932k
[  239.972694] EXT3 FS on sda1, internal journal
[  247.622257] eth0: no IPv6 routers present
[  252.652640] NET: Registered protocol family 17
[  263.037214] ACPI: Battery Slot [BAT0] (battery present)
[  263.137693] ACPI: Battery Slot [BAT1] (battery absent)
[  264.411871] input: Lid Switch as /class/input/input5
[  264.413411] ACPI: Lid Switch [LID]
[  264.635738] input: Power Button (CM) as /class/input/input6
[  264.637345] ACPI: Power Button (CM) [PBTN]
[  264.913882] input: Sleep Button (CM) as /class/input/input7
[  264.937568] ACPI: Sleep Button (CM) [SBTN]
[  266.085618] ACPI: AC Adapter [AC] (on-line)
[  266.487672] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[  267.242477] ACPI: ACPI Dock Station Driver 
[  210.264000] Marking TSC unstable due to: possible TSC halt in C2.
[  210.268000] Time: acpi_pm clocksource has been installed.
[  211.304000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  211.304000] apm: overridden by ACPI.
[  217.156000] Bluetooth: Core ver 2.11
[  217.156000] NET: Registered protocol family 31
[  217.156000] Bluetooth: HCI device and connection manager initialized
[  217.156000] Bluetooth: HCI socket layer initialized
[  217.236000] Bluetooth: L2CAP ver 2.8
[  217.236000] Bluetooth: L2CAP socket layer initialized
[  217.320000] Bluetooth: RFCOMM socket layer initialized
[  217.320000] Bluetooth: RFCOMM TTY layer initialized
[  217.320000] Bluetooth: RFCOMM ver 1.8
[  233.032000] Clocksource tsc unstable (delta = -86501208 ns)

```

lspci -v
```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
	Flags: bus master, medium devsel, latency 32
	Memory at d0000000 (32-bit, prefetchable) [size=256M]

00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
	Subsystem: Dell MagicGraph 128XD
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=16M]
	Memory at fde00000 (32-bit, non-prefetchable) [size=2M]
	Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]

00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at ece0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Flags: medium devsel, IRQ 9

```

lspnp
```

00:00 PNP0c01 System board
00:01 PNP0a03 PCI bus
00:02 PNP0c01 System board
00:03 PNP0c01 System board
00:04 PNP0c01 System board
00:05 PNP0f13 PS/2 port for PS/2-style mice
00:06 PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse support)
00:07 PNP0b00 AT real-time clock
00:08 PNP0800 AT speaker
00:09 PNP0c01 System board
00:0a PNP0200 AT DMA controller
00:0b PNP0c04 Math coprocessor
00:0c PNP0700 PC standard floppy disk controller
00:0d PNP0501 16550A-compatible serial port
00:0e PNP0401 ECP printer port
00:0f CSC0010 Crystal PnP audio system control registers
00:10 CSC0000 Crystal PnP audio system CODEC

```

original alsa-base (tried adding line from [http://ubuntuforums.org/showthread.php?t=90869](http://ubuntuforums.org/showthread.php?t=90869))
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

# from http://ubuntuforums.org/showthread.php?t=90869
#options snd-cs4236 port=0x530 cport=0x210 isapnp=0 dma1=1 dma2=0 irq=5

```

my attempted alsa-base (from [http://ubuntuforums.org/showthread.php?t=188736](http://ubuntuforums.org/showthread.php?t=188736))
```

alias char-major-116 snd
alias char-major-14 soundcore

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-css
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3

alias sound snd-card-0
alias snd-card-0 snd-card-cs4236

alias snd-minor-oss-0 snd-card-cs4236
alias snd-minor-oss-1 snd-opl3
alias snd-minor-oss-3 snd-pcm-oss

options snd-cs4236 port=0x530 cport=0x538 mpu_port=-1 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0 sb_port=0x220

install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

```

/etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
#snd-cs4236 port=0x530 cport=0x210 isapnp=0 dma1=1 dma2=0 irq=5

```

/sys/devices/pnp0/00:0f/resources
```

state = active
io 0x210-0x217

```

/sys/devices/pnp0/00:10/resources  (i did try the echo activate > ...)
```

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

```

if you'd like to see anything dumped after i make the changes again, let me know.  i'm just stumped on this!

thanks for any help!!

---

### Post by wolfen69 on 2009-01-05
here's something you can try. it worked for me when i had no sound on my eeepc.

make sure to have all repos enabled.completely remove alsa. then ```
sudo apt-get update
```  then ```
sudo apt-get install module-assistant
``` then ```
sudo m-a a-i alsa
``` this will recompile alsa for you automatically. restart. it can't hurt to try.

---

### Post by gfxcoder on 2009-01-07
that didn't work for me.  it seemed to do alright, except that it didn't find alsa-base, so it downloaded it.  shouldn't it have "compiled" or created that too?

any other suggestions?  thanks!

---

### Post by gfxcoder on 2009-01-10
after doing a sudo apt-get purge alsa, this is what happened...

```

$ sudo m-a a-i alsa

Updated infos about 1 packages
Getting source for kernel version: 2.6.22-16-386
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

Done!
unpack
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
Target package file
/usr/src/alsa-modules-2.6.22-16-386_1.0.14-1ubuntu2+2.6.22-16.60_i386.deb
already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/alsa-modules-2.6.22-16-386_1.0.14-1ubuntu2+2.6.22-16.60_i386.deb
Selecting previously deselected package alsa-modules-2.6.22-16-386.
(Reading database ... 78459 files and directories currently installed.)
Unpacking alsa-modules-2.6.22-16-386 (from .../alsa-modules-2.6.22-16-386_1.0.14-1ubuntu2+2.6.22-16.60_i386.deb) ...
dpkg: dependency problems prevent configuration of alsa-modules-2.6.22-16-386:
 alsa-modules-2.6.22-16-386 depends on alsa-base (>= 1.0.12-1); however:
  Package alsa-base is not installed.
dpkg: error processing alsa-modules-2.6.22-16-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alsa-modules-2.6.22-16-386

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  alsa-base
Suggested packages:
  alsa-oss
The following NEW packages will be installed:
  alsa-base
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B/182kB of archives.
After unpacking 369kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package alsa-base.
(Reading database ... 78681 files and directories currently installed.)
Unpacking alsa-base (from .../alsa-base_1.0.14-1ubuntu2_all.deb) ...
Setting up alsa-base (1.0.14-1ubuntu2) ...

Setting up alsa-modules-2.6.22-16-386 (1.0.14-1ubuntu2+2.6.22-16.60) ...
You should now stop all applications using sound devices
and reload all ALSA sound modules.

$ sudo /etc/init.d/alsa-utils reset
 * Resetting ALSA... [ OK ]
$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA... * warning: 'alsactl store' failed with error message 'alsactl: save_state:1253: No soundcards found...'... [fail]
 * Setting up ALSA... [ OK ]
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

anybody else have an idea?  thanks!

---

### Post by erikthedrink on 2009-09-08
In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

if you have USB speakers.  For your Default speakers, replace the "1" with a "0"  Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

