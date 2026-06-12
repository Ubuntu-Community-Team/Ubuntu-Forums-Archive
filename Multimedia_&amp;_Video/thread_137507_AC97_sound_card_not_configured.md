---
title: "AC97 sound card not configured"
date: 2006-02-28
forum: Multimedia &amp; Video
---

### Post by jonger on 2006-02-28
i've been trying this for a week now, from alsa to automatix to several post instuctions. heres the stats can anyone help. thank you, i'm noob.

lspci says:
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

dmesg says:(alot)
a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001f740000 (usable)
[4294667.296000]  BIOS-e820: 000000001f740000 - 000000001f750000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001f750000 - 000000001f800000 (ACPI NVS)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 503MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 128832
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 124736 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] Allocating PCI resources starting at 1f800000 (gap: 1f800000:e0800000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro acpi=off quiet splash
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 1500.102 MHz processor.
[   25.447434] Using tsc for high-res timesource
[   25.448804] Console: colour VGA+ 80x25
[   25.449134] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.449524] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.466086] Memory: 502532k/515328k available (1416k kernel code, 12284k reserved, 762k data, 224k init, 0k highmem)
[   25.466090] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.466160] Calibrating delay loop... 2965.50 BogoMIPS (lpj=1482752)
[   25.487876] Security Framework v1.0.0 initialized
[   25.487882] SELinux:  Disabled at boot.
[   25.487894] Mount-cache hash table entries: 512
[   25.487991] CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[   25.488000] CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[   25.488012] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.488015] CPU: L2 cache: 1024K
[   25.488017] CPU: After all inits, caps: a7e9fbbf 00000000 00000000 00000040 00000180 00000000 00000000
[   25.488023] CPU: Intel(R) Pentium(R) M processor 1500MHz stepping 05
[   25.488028] Enabling fast FPU save and restore... done.
[   25.488031] Enabling unmasked SIMD FPU exception support... done.
[   25.488035] Checking 'hlt' instruction... OK.
[   25.491846] Checking for popad bug... OK.
[   25.492016] checking if image is initramfs... it is
[   26.084064] Freeing initrd memory: 5171k freed
[   26.186419] NET: Registered protocol family 16
[   26.186457] EISA bus registered
[   26.187126] PCI: Using configuration type 1
[   26.187130] mtrr: v2.0 (20020519)
[   26.187511] ACPI: Subsystem revision 20050729
[   26.187515] ACPI: Interpreter disabled.
[   26.187519] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.187526] pnp: PnP ACPI: disabled
[   26.187532] PnPBIOS: Scanning system for PnP BIOS support...
[   26.187538] PnPBIOS: Found PnP BIOS installation structure at 0xc00f2e00
[   26.187543] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x39da, dseg 0xf0000
[   26.187944] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   26.187948] PnPBIOS: Unknown tag '0x0', length '1'.
[   26.187966] PnPBIOS: Unknown tag '0x8', length '7'.
[   26.187980] PnPBIOS: Unknown tag '0x8', length '7'.
[   26.187993] PnPBIOS: Resource structure does not contain an end tag.
[   26.188100] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   26.188127] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   26.188170] PCI: Probing PCI hardware
[   26.188173] PCI: Probing PCI hardware (bus 00)
[   26.188349] Boot video device is 0000:00:02.0
[   26.188705] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   26.189002] PCI: Transparent bridge - 0000:00:1e.0
[   26.189554] PCI: Using IRQ router default [8086/24cc] at 0000:00:1f.0
[   26.189572] PCI: IRQ 0 for device 0000:00:1f.1 doesn't match PIRQ mask - try pci=usepirqmask
[   26.189577] PCI: IRQ 0 for device 0000:00:1f.5 doesn't match PIRQ mask - try pci=usepirqmask
[   26.189583] PCI: IRQ 0 for device 0000:00:1f.6 doesn't match PIRQ mask - try pci=usepirqmask
[   26.189589] PCI: IRQ 0 for device 0000:01:05.0 doesn't match PIRQ mask - try pci=usepirqmask
[   26.189690] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   26.189694] pnp: 00:0a: ioport range 0xcf8-0xcff could not be reserved
[   26.190211] audit: initializing netlink socket (disabled)
[   26.190217] audit: initialized
[   26.190310] VFS: Disk quotas dquot_6.5.1
[   26.190331] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.190364] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   26.190370] devfs: boot_options: 0x0
[   26.190400] Initializing Cryptographic API
[   26.190507] isapnp: Scanning for PnP cards...
[   26.544458] isapnp: No Plug & Play device found
[   26.559753] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   26.562026] i8042.c: Detected active multiplexing controller, rev 1.1.
[   26.563125] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   26.563287] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   26.563447] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   26.563658] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   26.563827] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.563832] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[   26.564016] ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   26.565794] PCI: IRQ 0 for device 0000:00:1f.6 doesn't match PIRQ mask - try pci=usepirqmask
[   26.565799] PCI: No IRQ known for interrupt pin B of device 0000:00:1f.6. Please try using pci=biosirq.
[   26.565812] io scheduler noop registered
[   26.565828] io scheduler anticipatory registered
[   26.565833] io scheduler deadline registered
[   26.565843] io scheduler cfq registered
[   26.566177] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.566678] EISA: Probing bus 0 at eisa.0
[   26.566713] EISA: Detected 0 cards.
[   26.566740] NET: Registered protocol family 2
[   26.575721] IP: routing cache hash table of 4096 buckets, 32Kbytes
[   26.575897] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   26.576058] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   26.576143] TCP: Hash tables configured (established 16384 bind 16384)
[   26.576233] NET: Registered protocol family 8
[   26.576236] NET: Registered protocol family 20
[   26.576460] Freeing unused kernel memory: 224k freed
[   26.589481] vga16fb: initializing
[   26.589485] vga16fb: mapped to 0xc00a0000
[   26.705172] Console: switching to colour frame buffer device 80x30
[   26.705177] fb0: VGA16 VGA frame buffer device
[   26.823069] input: AT Translated Set 2 keyboard on isa0060/serio0
[   27.804574] Capability LSM initialized
[   27.815332] NET: Registered protocol family 1
[   27.829940] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.829954] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.834757] ICH4: IDE controller at PCI slot 0000:00:1f.1
[   27.834767] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.834775] PCI: IRQ 0 for device 0000:00:1f.1 doesn't match PIRQ mask - try pci=usepirqmask
[   27.834788] ICH4: chipset revision 3
[   27.834790] ICH4: not 100% native mode: will probe irqs later
[   27.834800]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   27.834812]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   27.834821] Probing IDE interface ide0...
[   28.098127] hda: IC25N060ATMR04-0, ATA DISK drive
[   28.709583] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.709626] Probing IDE interface ide1...
[   29.380723] hdc: UJDA750 DVD/CDRW, ATAPI CD/DVD-ROM drive
[   29.991938] ide1 at 0x170-0x177,0x376 on irq 15
[   29.992014] Probing IDE interface ide2...
[   30.504361] Probing IDE interface ide3...
[   31.015801] Probing IDE interface ide4...
[   31.527241] Probing IDE interface ide5...
[   32.042381] hda: max request size: 1024KiB
[   32.063185] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[   32.063507] hda: cache flushes supported
[   32.063563]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[   32.124388] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[   32.124395] Uniform CD-ROM driver Revision: 3.20
[   32.325259] Attempting manual resume
[   32.390912] swsusp: Suspend partition has wrong signature?
[   32.451113] usbcore: registered new driver usbfs
[   32.451141] usbcore: registered new driver hub
[   32.452416] USB Universal Host Controller Interface driver v2.2
[   32.452476] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.452481] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[   32.514330] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   32.514338] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000d480
[   32.514443] hub 1-0:1.0: USB hub found
[   32.514449] hub 1-0:1.0: 2 ports detected
[   32.517174] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   32.517178] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[   32.579116] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   32.579123] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000d800
[   32.579210] hub 2-0:1.0: USB hub found
[   32.579216] hub 2-0:1.0: 2 ports detected
[   32.582106] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   32.582111] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[   32.644043] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   32.644049] uhci_hcd 0000:00:1d.2: irq 4, io base 0x0000d880
[   32.644136] hub 3-0:1.0: USB hub found
[   32.644141] hub 3-0:1.0: 2 ports detected
[   32.670729] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   32.670735] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[   32.670748] ehci_hcd 0000:00:1d.7: debug port 1
[   38.163978] ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
[   38.163983] ehci_hcd 0000:00:1d.7: continuing after BIOS bug...
[   38.164023] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   38.164031] ehci_hcd 0000:00:1d.7: irq 4, io mem 0xffa7fc00
[   38.167939] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   38.167947] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   38.168041] hub 4-0:1.0: USB hub found
[   38.168047] hub 4-0:1.0: 6 ports detected
[   38.255606] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[   38.255610] e100: Copyright(c) 1999-2005 Intel Corporation
[   38.278689] e100: eth0: e100_probe: addr 0xff7ff000, irq 11, MAC addr 00:0C:6E:C9:29:4C
[   40.830234] Attempting manual resume
[   40.841609] swsusp: Suspend partition has wrong signature?
[   40.901397] kjournald starting.  Commit interval 5 seconds
[   40.901406] EXT3-fs: mounted filesystem with ordered data mode.
[   42.238198] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   45.139645] Adding 915664k swap on /dev/hda5.  Priority:-1 extents:1
[   45.396951] EXT3 FS on hda2, internal journal
[   52.990574] parport: PnPBIOS parport detected.
[   52.990666] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   53.075958] lp0: using parport0 (interrupt-driven).
[   53.102539] mice: PS/2 mouse device common for all mice
[   53.144341] ieee1394: Initialized config rom entry `ip1394'
[   53.166654] SCSI subsystem initialized
[   53.174504] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   53.360963] PCI: Enabling device 0000:00:1f.5 (0005 -> 0007)
[   53.360973] PCI: IRQ 0 for device 0000:00:1f.5 doesn't match PIRQ mask - try pci=usepirqmask
[   53.360979] PCI: No IRQ known for interrupt pin B of device 0000:00:1f.5. Please try using pci=biosirq.
[   53.361004] unable to grab IRQ 0
[   53.361018] Intel ICH: probe of 0000:00:1f.5 failed with error -16
[   53.778524] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[   53.780914] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[   53.936097] ts: Compaq touchscreen protocol output
[   56.517980] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   57.537511] cdrom: open failed.
[   58.112369] NTFS driver 2.1.22 [Flags: R/O MODULE].
[   58.158667] NTFS volume version 3.1.
[   59.581089] Linux agpgart interface v0.101 (c) Dave Jones
[   59.589689] agpgart: Detected an Intel 855 Chipset.
[   59.590344] agpgart: Detected 8060K stolen memory.
[   59.613353] agpgart: AGP aperture is 128M @ 0xf0000000
[   59.957056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.962039] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[   60.021259] hw_random: RNG not detected
[   60.395291] ieee80211_crypt: registered algorithm 'NULL'
[   60.399890] ieee80211: 802.11 data/management/control stack, 1.0.3
[   60.399896] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   60.409926] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.2
[   60.409932] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[   60.413789] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   61.270267] Linux Kernel Card Services
[   61.270271]   options:  [pci] [cardbus] [pm]
[   61.274594] PCI: IRQ 0 for device 0000:01:05.0 doesn't match PIRQ mask - try pci=usepirqmask
[   61.274600] PCI: No IRQ known for interrupt pin A of device 0000:01:05.0. Please try using pci=biosirq.
[   61.274611] Yenta: CardBus bridge found at 0000:01:05.0 [1043:1744]
[   61.394962] Yenta: ISA IRQ mask 0x0208, PCI irq 0
[   61.394965] Socket status: 30000006
[   61.980753] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   62.034407] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[ff7fe800-ff7fefff]  Max Packet=[2048]
[   63.298945] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003114e39]
[   63.556614] Real Time Clock Driver v1.12
[   63.671077] input: PC Speaker
[   73.264880] [drm] Initialized drm 1.0.0 20040925
[   73.273790] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation 82852/855GM Integrated Graphics Device
[   73.277601] [drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corporation 82852/855GM Integrated Graphics Device (#2)
[   73.281093] mtrr: base(0xf0020000) is not aligned on a size(0x300000) boundary
[   78.555402] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   80.055559] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f
[   80.057977] cs: IO port probe 0xc00-0xcf7: clean.
[   80.058689] cs: IO port probe 0xa00-0xaff: clean.
[   80.570467] Bluetooth: Core ver 2.7
[   80.570477] NET: Registered protocol family 31
[   80.570479] Bluetooth: HCI device and connection manager initialized
[   80.570491] Bluetooth: HCI socket layer initialized
[   80.619968] Bluetooth: L2CAP ver 2.7
[   80.619972] Bluetooth: L2CAP socket layer initialized
[   80.653946] Bluetooth: RFCOMM ver 1.5
[   80.653956] Bluetooth: RFCOMM socket layer initialized
[   80.653965] Bluetooth: RFCOMM TTY layer initialized
[  127.073939] NET: Registered protocol family 17
[  127.417658] NET: Registered protocol family 10
[  127.417821] Disabled Privacy Extensions on device c02eb280(lo)
[  127.418003] IPv6 over IPv4 tunneling driver
[  223.304579] eth0: no IPv6 routers present

cat /proc/version says:
Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:13:15 UTC 2006

---

