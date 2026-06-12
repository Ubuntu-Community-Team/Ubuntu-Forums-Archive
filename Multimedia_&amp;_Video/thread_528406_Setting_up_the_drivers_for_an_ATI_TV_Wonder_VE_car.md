---
title: "Setting up the drivers for an ATI TV Wonder VE card"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by 1feistymedic on 2007-08-17
I have an ATI TV Wonder VE PCI card in my desktop running Ubuntu Feisty. I am a total noob. I would like to know what software to use to get the card working, how to configure it, and what software to use to use the PVR and TV Tuner features. I got info from my card on this site:

[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

I have copied the info they give regarding the card as follows:

tuner: FI1236 Mk2/PH hm 3139 147 13251L

bttv0: Bt878 (rev 2) at 0000:00:0c.0, irq: 16, latency: 64, mmio: 0xfdffd000
bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init

I have copied and pasted my "dmesg" info from the terminal as follows:

sean@desktop:~$ dmesg
[ 0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[ 0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000004000 end: 00000000000ec000 type: 4
[ 0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000000be00000 end: 000000000bf00000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e8000 - 00000000000ec000 (ACPI NVS)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000000bf00000 (usable)
[ 0.000000] BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 191MB LOWMEM available.
[ 0.000000] Entering add_active_range(0, 0, 48896) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 48896
[ 0.000000] HighMem 48896 -> 48896
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 48896
[ 0.000000] On node 0 totalpages: 48896
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 350 pages used for memmap
[ 0.000000] Normal zone: 44450 pages, LIFO batch:7
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] DMI 2.3 present.
[ 0.000000] ACPI: RSDP (v000 COMPAQ ) @ 0x000e8010
[ 0.000000] ACPI: RSDT (v001 COMPAQ CARS6C21 0x00000001 0x00000000) @ 0x000e8080
[ 0.000000] ACPI: FADT (v001 COMPAQ CARS6C21 0x00000001 0x00000000) @ 0x000e80cc
[ 0.000000] ACPI: SSDT (v001 COMPAQ CARS6C2 0x00000001 MSFT 0x01000007) @ 0x000e8187
[ 0.000000] ACPI: DSDT (v001 COMPAQ DSDTTBL 0x00000001 MSFT 0x01000007) @ 0x00000000
[ 0.000000] ACPI: PM-Timer IO Port: 0xee08
[ 0.000000] Allocating PCI resources starting at 10000000 (gap: 0bf00000:f40c0000)
[ 0.000000] Detected 498.838 MHz processor.
[ 18.453105] Built 1 zonelists. Total pages: 48514
[ 18.453119] Kernel command line: root=UUID=5effcbf0-c39b-4e2c-82ce-3e59fd7624c4 ro quiet splash
[ 18.453904] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 18.453938] mapped APIC to ffffd000 (0118a000)
[ 18.453952] Enabling fast FPU save and restore... done.
[ 18.453989] Initializing CPU#0
[ 18.454122] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 18.456389] Console: colour VGA+ 80x25
[ 18.457040] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 18.457762] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 18.485325] Memory: 182840k/195584k available (1992k kernel code, 12208k reserved, 900k data, 328k init, 0k highmem)
[ 18.485371] virtual kernel memory layout:
[ 18.485376] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 18.485382] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 18.485388] vmalloc : 0xcc800000 - 0xff7fe000 ( 815 MB)
[ 18.485394] lowmem : 0xc0000000 - 0xcbf00000 ( 191 MB)
[ 18.485400] .init : 0xc03d9000 - 0xc042b000 ( 328 kB)
[ 18.485406] .data : 0xc02f2374 - 0xc03d36d4 ( 900 kB)
[ 18.485412] .text : 0xc0100000 - 0xc02f2374 (1992 kB)
[ 18.485426] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 18.562092] Calibrating delay using timer specific routine.. 998.91 BogoMIPS (lpj=1997837)
[ 18.562261] Security Framework v1.0.0 initialized
[ 18.562290] SELinux: Disabled at boot.
[ 18.562361] Mount-cache hash table entries: 512
[ 18.562896] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[ 18.562945] CPU: L1 I cache: 16K, L1 D cache: 16K
[ 18.562957] CPU: L2 cache: 128K
[ 18.562969] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[ 18.563013] Compat vDSO mapped to ffffe000.
[ 18.563041] Remapping vsyscall page to ffffe000
[ 18.563080] Checking 'hlt' instruction... OK.
[ 18.578203] SMP alternatives: switching to UP code
[ 18.578812] Freeing SMP alternatives: 11k freed
[ 18.579563] Early unpacking initramfs... done
[ 19.882714] ACPI: Core revision 20060707
[ 19.885243] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 19.889152] ACPI: setting ELCR to 0200 (from 0828)
[ 19.891991] CPU0: Intel Celeron (Mendocino) stepping 05
[ 19.892019] SMP motherboard not detected.
[ 19.892028] Local APIC not detected. Using dummy APIC emulation.
[ 19.892179] Brought up 1 CPUs
[ 19.893143] Booting paravirtualized kernel on bare hardware
[ 19.893435] Time: 1:43:28 Date: 07/17/107
[ 19.893568] NET: Registered protocol family 16
[ 19.894093] EISA bus registered
[ 19.894119] ACPI: bus type pci registered
[ 19.896105] PCI: PCI BIOS revision 2.10 entry at 0xfa134, last bus=1
[ 19.896115] PCI: Using configuration type 1
[ 19.896123] Setting up standard PCI resources
[ 19.908095] ACPI: Interpreter enabled
[ 19.908113] ACPI: Using PIC for interrupt routing
[ 19.910798] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 15)
[ 19.911938] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 15)
[ 19.913048] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 15)
[ 19.914333] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 15)
[ 19.914998] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 19.915019] PCI: Probing PCI hardware (bus 00)
[ 19.915765] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[ 19.916878] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[ 19.916896] PCI quirk: region ee80-eebf claimed by ICH4 GPIO
[ 19.917561] Boot video device is 0000:01:08.0
[ 19.918093] PCI: Transparent bridge - 0000:00:1e.0
[ 19.918165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 19.931160] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 19.931225] pnp: PnP ACPI init
[ 19.943691] pnp: PnP ACPI: found 14 devices
[ 19.943710] PnPBIOS: Disabled by ACPI PNP
[ 19.943950] PCI: Using ACPI for IRQ routing
[ 19.943965] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 20.002283] NET: Registered protocol family 8
[ 20.002293] NET: Registered protocol family 20
[ 20.003269] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[ 20.003286] pnp: 00:02: ioport range 0x400-0x47f has been reserved
[ 20.003299] pnp: 00:02: ioport range 0xee00-0xee7f could not be reserved
[ 20.004906] PCI: Bridge: 0000:00:1e.0
[ 20.004923] IO window: 1000-1fff
[ 20.004940] MEM window: 40000000-402fffff
[ 20.004953] PREFETCH window: 40300000-4fffffff
[ 20.004985] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 20.005102] NET: Registered protocol family 2
[ 20.041923] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 20.042262] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 20.042544] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 20.042707] TCP: Hash tables configured (established 8192 bind 4096)
[ 20.042719] TCP reno registered
[ 20.054162] checking if image is initramfs... it is
[ 22.480478] Freeing initrd memory: 6764k freed
[ 22.482177] audit: initializing netlink socket (disabled)
[ 22.482227] audit(1187315010.212:1): initialized
[ 22.482792] VFS: Disk quotas dquot_6.5.1
[ 22.482882] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 22.483100] io scheduler noop registered
[ 22.483114] io scheduler anticipatory registered
[ 22.483124] io scheduler deadline registered
[ 22.483166] io scheduler cfq registered (default)
[ 22.484217] isapnp: Scanning for PnP cards...
[ 22.837871] isapnp: No Plug & Play device found
[ 23.073816] Real Time Clock Driver v1.12ac
[ 23.074076] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 23.074408] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 23.078656] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 23.080110] mice: PS/2 mouse device common for all mice
[ 23.083166] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 23.083961] input: Macintosh mouse button emulation as /class/input/input0
[ 23.084148] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 23.084167] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 23.084950] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[ 23.088277] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 23.088301] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 23.089106] EISA: Probing bus 0 at eisa.0
[ 23.089135] Cannot allocate resource for EISA slot 1
[ 23.089144] Cannot allocate resource for EISA slot 2
[ 23.089183] EISA: Detected 0 cards.
[ 23.119521] TCP cubic registered
[ 23.119552] NET: Registered protocol family 1
[ 23.119641] Using IPI No-Shortcut mode
[ 23.119970] ACPI: (supports S0 S1 S5)
[ 23.120122] Magic number: 3:77:711
[ 23.120595] Time: tsc clocksource has been installed.
[ 23.122120] Freeing unused kernel memory: 328k freed
[ 23.140495] input: AT Translated Set 2 keyboard as /class/input/input1
[ 25.194196] Capability LSM initialized
[ 25.411922] ACPI: Invalid PBLK length [5]
[ 27.955131] SCSI subsystem initialized
[ 28.087729] libata version 2.20 loaded.
[ 28.099083] ata_piix 0000:00:1f.1: version 2.10ac1
[ 28.099166] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 28.099411] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012020 irq 14
[ 28.099551] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012028 irq 15
[ 28.099611] scsi0 : ata_piix
[ 28.284017] ata1.00: ata_hpa_resize 1: sectors = 33242832, hpa_sectors = 33242832
[ 28.284038] ata1.00: ATA-4: WDC WD170AA, 05.05B05, max UDMA/66
[ 28.284050] ata1.00: 33242832 sectors, multi 8: LBA
[ 28.292060] ata1.00: ata_hpa_resize 1: sectors = 33242832, hpa_sectors = 33242832
[ 28.292084] ata1.00: configured for UDMA/33
[ 28.314937] scsi1 : ata_piix
[ 28.434960] usbcore: registered new interface driver usbfs
[ 28.435051] usbcore: registered new interface driver hub
[ 28.435179] usbcore: registered new device driver usb
[ 28.441724] USB Universal Host Controller Interface driver v3.0
[ 28.611074] 8139too Fast Ethernet driver 0.9.28
[ 29.027766] Floppy drive(s): fd0 is 1.44M
[ 29.048026] FDC 0 is a post-1991 82077
[ 29.138905] ata2.00: ATAPI, max UDMA/33
[ 29.302864] ata2.00: configured for UDMA/33
[ 29.303399] scsi 0:0:0:0: Direct-Access ATA WDC WD170AA 05.0 PQ: 0 ANSI: 5
[ 29.305692] scsi 1:0:0:0: CD-ROM Compaq DVD-ROM DVD-114 1.14 PQ: 0 ANSI: 5
[ 29.328218] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[ 29.328237] PCI: setting IRQ 11 as level-triggered
[ 29.328248] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 29.328288] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 29.328302] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[ 29.328752] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[ 29.328819] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000eec0
[ 29.329316] usb usb1: configuration #1 chosen from 1 choice
[ 29.329439] hub 1-0:1.0: USB hub found
[ 29.329486] hub 1-0:1.0: 2 ports detected
[ 29.386655] SCSI device sda: 33242832 512-byte hdwr sectors (17020 MB)
[ 29.388778] sda: Write Protect is off
[ 29.388799] sda: Mode Sense: 00 3a 00 00
[ 29.388933] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 29.389175] SCSI device sda: 33242832 512-byte hdwr sectors (17020 MB)
[ 29.389226] sda: Write Protect is off
[ 29.389237] sda: Mode Sense: 00 3a 00 00
[ 29.389310] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 29.389330] sda: sda1 sda2 <PCI: Enabling device 0000:01:09.0 (0004 -> 0007)
[ 29.432311] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[ 29.432327] PCI: setting IRQ 5 as level-triggered
[ 29.432338] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 29.432948] eth0: RealTek RTL8139 at 0xcc85a000, 00:05:5d:44:6b:5c, IRQ 5
[ 29.432960] eth0: Identified 8139 chip type 'RTL-8139C'
[ 29.456567] sda5 >
[ 29.459388] sd 0:0:0:0: Attached scsi disk sda
[ 29.532603] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[ 29.532625] Uniform CD-ROM driver Revision: 3.20
[ 29.533555] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 29.539350] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 29.540065] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 29.670532] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 29.825045] usb 1-1: configuration #1 chosen from 1 choice
[ 29.826918] hub 1-1:1.0: USB hub found
[ 29.829728] hub 1-1:1.0: 4 ports detected
[ 29.991708] Attempting manual resume
[ 29.991724] swsusp: Resume From Partition 8:5
[ 29.991732] PM: Checking swsusp image.
[ 29.992215] PM: Resume from disk failed.
[ 30.121623] kjournald starting. Commit interval 5 seconds
[ 30.121678] EXT3-fs: mounted filesystem with ordered data mode.
[ 30.143589] usb 1-1.3: new full speed USB device using uhci_hcd and address 3
[ 30.451679] usb 1-1.3: configuration #1 chosen from 1 choice
[ 30.659248] usb 1-1.4: new full speed USB device using uhci_hcd and address 4
[ 30.821430] usb 1-1.4: configuration #1 chosen from 1 choice
[ 56.040125] Intel 82802 RNG detected
[ 56.099518] iTCO_vendor_support: vendor-support=0
[ 56.105447] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 56.105968] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[ 56.105998] iTCO_wdt: No card detected
[ 57.458870] Linux agpgart interface v0.102 (c) Dave Jones
[ 57.469045] agpgart: Detected an Intel i810 DC100 Chipset.
[ 57.476134] agpgart: detected 4MB dedicated video ram.
[ 57.494516] agpgart: AGP aperture is 64M @ 0x54000000
[ 58.606368] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 58.670993] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[ 58.780178] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 58.798958] input: PC Speaker as /class/input/input2
[ 59.158611] pnp: Device 00:09 activated.
[ 59.158632] parport: PnPBIOS parport detected.
[ 59.158675] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[ 59.352972] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[ 60.413240] Linux video capture interface: v2.00
[ 60.531735] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 60.550178] gameport: ES1938 is pci0000:01:05.0/gameport0, io 0x186c, speed 946kHz
[ 60.658992] bttv: driver version 0.9.16 loaded
[ 60.659010] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 60.659266] bttv: Bt8xx card found (0).
[ 60.659318] PCI: Enabling device 0000:01:0b.0 (0004 -> 0006)
[ 60.659350] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 60.659384] bttv0: Bt878 (rev 17) at 0000:01:0b.0, irq: 11, latency: 66, mmio: 0x40300000
[ 60.659428] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[ 60.659442] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[ 60.659517] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[ 60.660540] bttv0: using tuner=19
[ 60.660560] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 60.661439] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 60.662294] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 60.730494] tuner 2-0060: All bytes are equal. It is not a TEA5767
[ 60.730512] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[ 60.730635] tuner 2-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[ 60.730650] tuner 2-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[ 60.744121] bttv0: registered device video0
[ 60.744341] bttv0: registered device vbi0
[ 60.744406] bttv0: PLL: 28636363 => 35468950 .. ok
[ 61.258054] bt878: AUDIO driver version 0.0.0 loaded
[ 61.258262] bt878: Bt878 AUDIO function found (0).
[ 61.258304] PCI: Enabling device 0000:01:0b.1 (0004 -> 0006)
[ 61.258335] ACPI: PCI Interrupt 0000:01:0b.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 61.258358] bt878_probe: card id=[0x31002], Unknown card.
[ 61.258364] Exiting..
[ 61.258378] ACPI: PCI interrupt for device 0000:01:0b.1 disabled
[ 61.258396] bt878: probe of 0000:01:0b.1 failed with error -22
[ 61.475213] rtusb init ====>
[ 62.057652] idVendor = 0x13b1, idProduct = 0x20
[ 62.077733] drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
[ 62.082993] drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0404
[ 62.083049] usbcore: registered new interface driver usblp
[ 62.083063] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 62.849206] usbcore: registered new interface driver rt73
[ 62.877240] rt73 driver version - 1.0.3.6 CVS
[ 63.215952] ***rt73***: Interface goes up for the first time, activating permanent MAC
[ 63.215980] ***rt73***: Active MAC is: 00:16:b6:97:1a:f7.
[ 63.279146] lp0: using parport0 (interrupt-driven).
[ 63.647704] Adding 554200k swap on /dev/disk/by-uuid/813e2f67-6540-437d-9c4a-1adacb0f8c50. Priority:-1 extents:1 across:554200k
[ 63.741579] NET: Registered protocol family 10
[ 63.741943] lo: Disabled Privacy Extensions
[ 64.022265] EXT3 FS on sda1, internal journal
[ 67.562764] ibm_acpi: ec object not found
[ 67.893979] input: Power Button (FF) as /class/input/input4
[ 67.894937] ACPI: Power Button (FF) [PWRF]
[ 67.921995] input: Power Button (CM) as /class/input/input5
[ 67.923004] ACPI: Power Button (CM) [PBTN]
[ 68.304050] Using specific hotkey driver
[ 68.863499] No dock devices found.
[ 69.030180] pcc_acpi: loading...
[ 73.511656] eth0: link down
[ 73.512592] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 74.011845] wlan0: no IPv6 routers present
[ 75.636323] [drm] Initialized drm 1.1.0 20060810
[ 75.782419] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[ 75.782450] PCI: setting IRQ 3 as level-triggered
[ 75.782461] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[ 75.793173] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[ 76.469982] ppdev: user-space parallel port driver
[ 77.381728] [drm] Setting GART location based on new memory map
[ 77.383223] [drm] writeback test succeeded in 1 usecs
[ 79.381567] apm: BIOS not found.
[ 80.850462] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[ 83.114461] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 83.213019] NFSD: starting 90-second grace period
[ 90.559810] Bluetooth: Core ver 2.11
[ 90.560058] NET: Registered protocol family 31
[ 90.560070] Bluetooth: HCI device and connection manager initialized
[ 90.560084] Bluetooth: HCI socket layer initialized
[ 90.714755] Bluetooth: L2CAP ver 2.8
[ 90.714774] Bluetooth: L2CAP socket layer initialized
[ 90.743013] Bluetooth: RFCOMM socket layer initialized
[ 90.743066] Bluetooth: RFCOMM TTY layer initialized
[ 90.743075] Bluetooth: RFCOMM ver 1.8
sean@desktop:~$

Any help you could give is very much appreciated!

---

### Post by 1feistymedic on 2007-08-24
Any takers?  I still can not get this thing to work.:confused:

---

### Post by smacfarl on 2007-10-15
I also have a 7000 card and am having trouble getting the 3d acceleration working.

Were you able to solve your problem?

---

