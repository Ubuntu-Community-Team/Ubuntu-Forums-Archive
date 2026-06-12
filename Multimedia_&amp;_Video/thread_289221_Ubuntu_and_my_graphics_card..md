---
title: "Ubuntu and my graphics card."
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by VibesTalen on 2006-10-30
vibes@Neji:~$ dmesg
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000] BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[4294667.296000] BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
[4294667.296000] BIOS-e820: 000000000fef0000 - 000000000feffc00 (ACPI data)
[4294667.296000] BIOS-e820: 000000000feffc00 - 000000000ff00000 (ACPI NVS)
[4294667.296000] BIOS-e820: 000000000ff00000 - 0000000010000000 (reserved)
[4294667.296000] BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 254MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65264
[4294667.296000] DMA zone: 4096 pages, LIFO batch:1
[4294667.296000] Normal zone: 61168 pages, LIFO batch:31
[4294667.296000] HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD ) @ 0x000f6590
[4294667.296000] ACPI: RSDT (v001 PTLTD RSDT 0x06040000 LTP 0x00000000) @ 0x0fefae57
[4294667.296000] ACPI: FADT (v001 INTEL Whitney 0x06040000 PTL 0x000f4240) @ 0x0feffb8c
[4294667.296000] ACPI: DSDT (v001 INTEL Whitney 0x06040000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:eff00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (011ff000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1100.492 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.730000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)[4294670.731000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.759000] Memory: 250756k/261056k available (1415k kernel code, 9744k reserved, 763k data, 224k init, 0k highmem)
[4294670.759000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.759000] Calibrating delay loop... 2179.07 BogoMIPS (lpj=1089536)
[4294670.783000] Security Framework v1.0.0 initialized
[4294670.783000] SELinux: Disabled at boot.
[4294670.783000] Mount-cache hash table entries: 512
[4294670.783000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.783000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.783000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294670.783000] CPU: L2 cache: 128K
[4294670.783000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294670.783000] CPU: Intel Celeron (Coppermine) stepping 0a
[4294670.783000] Enabling fast FPU save and restore... done.
[4294670.783000] Enabling unmasked SIMD FPU exception support... done.
[4294670.783000] Checking 'hlt' instruction... OK.
[4294670.787000] Checking for popad bug... OK.
[4294670.787000] checking if image is initramfs... it is
[4294671.552000] Freeing initrd memory: 4821k freed
[4294671.554000] ACPI: Looking for DSDT in initrd... not found!
[4294671.673000] not found!
[4294671.685000] ACPI: setting ELCR to 0200 (from 0a00)
[4294671.686000] NET: Registered protocol family 16
[4294671.686000] EISA bus registered
[4294671.686000] ACPI: bus type pci registered
[4294671.686000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[4294671.686000] PCI: Using configuration type 1
[4294671.686000] mtrr: v2.0 (20020519)
[4294671.687000] ACPI: Subsystem revision 20050729
[4294671.698000] ACPI: Interpreter enabled
[4294671.698000] ACPI: Using PIC for interrupt routing
[4294671.698000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.698000] PCI: Probing PCI hardware (bus 00)
[4294671.698000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.700000] Boot video device is 0000:00:01.0
[4294671.700000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.702000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.704000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[4294671.704000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[4294671.704000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294671.705000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[4294671.705000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[4294671.706000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.706000] pnp: PnP ACPI init
[4294671.708000] pnp: PnP ACPI: found 7 devices
[4294671.708000] PnPBIOS: Disabled by ACPI PNP
[4294671.708000] PCI: Using ACPI for IRQ routing
[4294671.708000] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[4294671.712000] audit: initializing netlink socket (disabled)
[4294671.712000] audit: initialized
[4294671.713000] VFS: Disk quotas dquot_6.5.1
[4294671.713000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.713000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.713000] devfs: boot_options: 0x0
[4294671.713000] Initializing Cryptographic API
[4294671.713000] isapnp: Scanning for PnP cards...
[4294672.067000] isapnp: No Plug & Play device found
[4294672.144000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294672.144000] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 112
[4294672.156000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.158000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.158000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.168000] io scheduler noop registered
[4294672.168000] io scheduler anticipatory registered
[4294672.168000] io scheduler deadline registered
[4294672.168000] io scheduler cfq registered
[4294672.169000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.171000] EISA: Probing bus 0 at eisa.0
[4294672.171000] Cannot allocate resource for EISA slot 1
[4294672.171000] Cannot allocate resource for EISA slot 3
[4294672.171000] EISA: Detected 0 cards.
[4294672.171000] NET: Registered protocol family 2
[4294672.181000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.181000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294672.181000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.181000] TCP: Hash tables configured (established 8192 bind 8192)
[4294672.182000] NET: Registered protocol family 8
[4294672.182000] NET: Registered protocol family 20
[4294672.182000] ACPI wakeup devices:
[4294672.182000] KBC0 HUB USB PWRB
[4294672.182000] ACPI: (supports S0 S1 S5)
[4294672.183000] Freeing unused kernel memory: 224k freed
[4294672.246000] vga16fb: initializing
[4294672.246000] vga16fb: mapped to 0xc00a0000
[4294672.360000] Console: switching to colour frame buffer device 80x30
[4294672.360000] fb0: VGA16 VGA frame buffer device
[4294672.511000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.513000] Capability LSM initialized
[4294673.544000] NET: Registered protocol family 1
[4294673.577000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.577000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.577000] ACPI: bus type ide registered
[4294673.593000] ICH: IDE controller at PCI slot 0000:00:1f.1
[4294673.593000] ICH: chipset revision 2
[4294673.593000] ICH: not 100% native mode: will probe irqs later
[4294673.593000] ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[4294673.593000] ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[4294673.593000] Probing IDE interface ide0...
[4294673.857000] hda: WDC WD400EB-00CPF0, ATA DISK drive
[4294674.469000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.470000] Probing IDE interface ide1...
[4294674.836000] hdc: SAMSUNG SC-148, ATAPI CD/DVD-ROM drive
[4294675.550000] hdd: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[4294675.550000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.550000] Probing IDE interface ide2...
[4294676.063000] Probing IDE interface ide3...
[4294676.575000] Probing IDE interface ide4...
[4294677.087000] Probing IDE interface ide5...
[4294677.609000] hda: max request size: 128KiB
[4294677.632000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[4294677.632000] hda: cache flushes not supported
[4294677.632000] /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.685000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache
[4294677.685000] Uniform CD-ROM driver Revision: 3.20
[4294677.690000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[4294679.106000] Attempting manual resume
[4294679.107000] swsusp: Suspend partition has wrong signature?
[4294679.206000] usbcore: registered new driver usbfs
[4294679.207000] usbcore: registered new driver hub
[4294679.209000] USB Universal Host Controller Interface driver v2.2
[4294679.210000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294679.210000] PCI: setting IRQ 9 as level-triggered
[4294679.210000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294679.210000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294679.210000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294679.272000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294679.272000] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001820
[4294679.272000] hub 1-0:1.0: USB hub found
[4294679.272000] hub 1-0:1.0: 2 ports detected
[4294679.324000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[4294679.324000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294679.324000] PCI: setting IRQ 11 as level-triggered
[4294679.324000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294679.347000] eth0: Davicom DM9102 at pci0000:01:0e.0, 00:80:ad:7b:d8:99, irq 11.
[4294679.351000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294682.866000] ACPI: CPU0 (power states: C1[C1])
[4294683.103000] Attempting manual resume
[4294683.103000] swsusp: Suspend partition has wrong signature?
[4294683.135000] kjournald starting. Commit interval 5 seconds
[4294683.135000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.756000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294696.930000] Adding 746980k swap on /dev/hda5. Priority:-1 extents:1
[4294697.224000] EXT3 FS on hda1, internal journal
[4294703.757000] lp: driver loaded but no devices found
[4294703.818000] mice: PS/2 mouse device common for all mice
[4294706.946000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294707.942000] cdrom: open failed.
[4294707.945000] cdrom: open failed.
[4294710.687000] Linux agpgart interface v0.101 (c) Dave Jones
[4294710.724000] agpgart: Detected an Intel i810 Chipset.
[4294710.770000] agpgart: AGP aperture is 64M @ 0xec000000
[4294711.091000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294711.131000] shpchp: shpc_init : shpc_cap_offset == 0
[4294711.131000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294711.294000] hw_random hardware driver 1.0.0 loaded
[4294712.247000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294712.248000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294712.248000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294712.556000] intel8x0_measure_ac97_clock: measured 49168 usecs
[4294712.556000] intel8x0: clocking to 48000
[4294716.226000] Real Time Clock Driver v1.12
[4294716.367000] input: PC Speaker
[4294720.741000] ACPI: Power Button (FF) [PWRF]
[4294720.741000] ACPI: Power Button (CM) [PWRB]
[4294721.073000] ibm_acpi: ec object not found
[4294738.825000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294738.825000] apm: overridden by ACPI.
[4294742.250000] Bluetooth: Core ver 2.7
[4294742.250000] NET: Registered protocol family 31
[4294742.250000] Bluetooth: HCI device and connection manager initialized
[4294742.250000] Bluetooth: HCI socket layer initialized
[4294742.302000] Bluetooth: L2CAP ver 2.7
[4294742.302000] Bluetooth: L2CAP socket layer initialized
[4294742.368000] Bluetooth: RFCOMM ver 1.5
[4294742.368000] Bluetooth: RFCOMM socket layer initialized
[4294742.368000] Bluetooth: RFCOMM TTY layer initialized
[4295046.260000] ibm_acpi: ec object not found
[4296782.710000] NET: Registered protocol family 10
[4296782.710000] Disabled Privacy Extensions on device c02eb280(lo)
[4296782.711000] IPv6 over IPv4 tunneling driver
[4298947.942000] usb 1-2: new full speed USB device using uhci_hcd and address 2[4298948.111000] usb 1-2: configuration #1 chosen from 2 choices
[4298949.146000] SCSI subsystem initialized
[4298949.174000] Initializing USB Mass Storage driver...
[4298949.180000] scsi0 : SCSI emulation for USB Mass Storage devices
[4298949.189000] usb-storage: device found at 2
[4298949.189000] usb-storage: waiting for device to settle before scanning
[4298949.189000] usbcore: registered new driver usb-storage
[4298949.189000] USB Mass Storage support registered.
[4298954.195000] Vendor: Apple Model: iPod Rev: 1.62
[4298954.195000] Type: Direct-Access ANSI SCSI revision: 00
[4298954.225000] usb-storage: device scan complete
[4298954.467000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4298954.474000] sda: Write Protect is off
[4298954.474000] sda: Mode Sense: 68 00 00 08
[4298954.474000] sda: assuming drive cache: write through
[4298954.496000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4298954.502000] sda: Write Protect is off
[4298954.502000] sda: Mode Sense: 68 00 00 08
[4298954.502000] sda: assuming drive cache: write through
[4298954.502000] /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4298954.540000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4298956.682000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4298958.146000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4298958.168000] FAT: count of clusters too big (7325576)
[4298958.168000] VFS: Can't find a valid FAT filesystem on dev sda.
[4299844.025000] usb 1-2: USB disconnect, address 2
[4299844.597000] scsi0 (0:0): rejecting I/O to dead device
[4299844.597000] FAT: bread failed in fat_clusters_flush
[4299844.597000] scsi0 (0:0): rejecting I/O to dead device
[4299849.941000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4299850.587000] usbcore: registered new driver hiddev
[4299850.669000] input: USB HID v1.10 Mouse [Kensington Pocket Mouse Pro Wireless] on usb-0000:00:1f.2-2
[4299850.669000] usbcore: registered new driver usbhid
[4299850.669000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4301330.089000] NET: Registered protocol family 17
[4301348.791000] eth0: no IPv6 routers present

Hey im new to linux and ubuntu i just installed it and i wanted to know if it is detecting my graphics card (not the integraded one) and how i could go about installing it. thanks for the help

---

### Post by chippy99 on 2006-10-30
Have a look in /var/log/XFree86.0.log to see what chipset it is using.
"cat /var/log/XFree86.0.log | grep Chipset" should list it.

---

