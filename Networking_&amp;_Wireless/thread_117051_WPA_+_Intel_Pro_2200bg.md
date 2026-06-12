---
title: "WPA + Intel Pro 2200bg"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by lokirulez on 2006-01-14
I just switched from Debian Sarge 3.1 to Kubuntu 5.10. I am trying to connect to a wireless network that requires WPA. After installing wpa_supplicant, I ran kwifimanager. I seem to connect and then disconnect, this goes on and on. I know the network works because I was able to connect to it via Windows XP, but I got rid of that. After some research I found many users complaining that the ipw drivers that come standard with Breezy have issues. I tried upgrading my ipw2200 driver, ieee80211 network stack, and the firmware. I installed those from source and did not get any errors. However when I tried running **sudo modprobe ipw2200**, I received the following:

```

FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-9-686/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
After seeing that, I tried **dmesg** and got the following:

```

n reserved
[4294669.578000] audit: initializing netlink socket (disabled)
[4294669.578000] audit: initialized
[4294669.578000] highmem bounce pool size: 64 pages
[4294669.578000] VFS: Disk quotas dquot_6.5.1
[4294669.578000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.578000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.578000] devfs: boot_options: 0x0
[4294669.578000] Initializing Cryptographic API
[4294669.578000] isapnp: Scanning for PnP cards...
[4294669.932000] isapnp: No Plug & Play device found
[4294669.945000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.949000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.949000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.949000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.950000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[4294669.950000] PCI: setting IRQ 7 as level-triggered
[4294669.950000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294669.950000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294669.950000] io scheduler noop registered
[4294669.950000] io scheduler anticipatory registered
[4294669.950000] io scheduler deadline registered
[4294669.950000] io scheduler cfq registered
[4294669.951000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.951000] NET: Registered protocol family 2
[4294669.961000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.961000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294669.963000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.964000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.964000] NET: Registered protocol family 8
[4294669.964000] NET: Registered protocol family 20
[4294669.964000] ACPI wakeup devices:
[4294669.964000]  LID PBTN PCI0 USB0 USB1 USB2 USB3 MODM PCIE
[4294669.964000] ACPI: (supports S0 S1 S3 S4 S4bios S5)
[4294669.964000] Freeing unused kernel memory: 168k freed
[4294669.964000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.973000] vga16fb: initializing
[4294669.973000] vga16fb: mapped to 0xc00a0000
[4294670.089000] Console: switching to colour frame buffer device 80x30
[4294670.089000] fb0: VGA16 VGA frame buffer device
[4294671.212000] Capability LSM initialized
[4294671.219000] NET: Registered protocol family 1
[4294671.228000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.228000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.228000] ACPI: bus type ide registered
[4294671.232000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294671.232000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.232000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294671.232000] PCI: setting IRQ 11 as level-triggered
[4294671.232000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294671.232000] ICH4: chipset revision 1
[4294671.232000] ICH4: not 100% native mode: will probe irqs later
[4294671.232000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[4294671.232000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294671.232000] Probing IDE interface ide0...
[4294671.496000] hda: FUJITSU MHU2100AT, ATA DISK drive
[4294672.110000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.110000] Probing IDE interface ide1...
[4294672.782000] hdc: _NEC DVD+/-RW ND-6500A, ATAPI CD/DVD-ROM drive
[4294673.394000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.394000] Probing IDE interface ide2...
[4294673.907000] Probing IDE interface ide3...
[4294674.419000] Probing IDE interface ide4...
[4294674.931000] Probing IDE interface ide5...
[4294675.445000] hda: max request size: 128KiB
[4294675.494000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.498000] hda: cache flushes supported
[4294675.498000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294675.530000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.530000] Uniform CD-ROM driver Revision: 3.20
[4294678.602000] Attempting manual resume
[4294678.610000] swsusp: Suspend partition has wrong signature?
[4294678.628000] usbcore: registered new driver usbfs
[4294678.628000] usbcore: registered new driver hub
[4294678.629000] USB Universal Host Controller Interface driver v2.2
[4294678.629000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294678.629000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.629000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294678.691000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294678.691000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[4294678.691000] hub 1-0:1.0: USB hub found
[4294678.691000] hub 1-0:1.0: 2 ports detected
[4294678.694000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294678.694000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294678.694000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294678.694000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294678.756000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294678.756000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[4294678.756000] hub 2-0:1.0: USB hub found
[4294678.756000] hub 2-0:1.0: 2 ports detected
[4294678.759000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294678.759000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294678.759000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294678.759000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294678.821000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294678.821000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[4294678.821000] hub 3-0:1.0: USB hub found
[4294678.821000] hub 3-0:1.0: 2 ports detected
[4294678.841000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294678.841000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294678.841000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294678.841000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294678.841000] ehci_hcd 0000:00:1d.7: debug port 1
[4294678.841000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294678.841000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[4294678.845000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294678.845000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.845000] hub 4-0:1.0: USB hub found
[4294678.845000] hub 4-0:1.0: 6 ports detected
[4294678.903000] b44.c:v0.95 (Aug 3, 2004)
[4294678.903000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294678.907000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:11:43:69:fe:4a
[4294679.425000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294680.941000] usbcore: registered new driver hiddev
[4294680.958000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[4294680.958000] usbcore: registered new driver usbhid
[4294680.958000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294681.222000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294681.222000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294681.225000] ACPI: Thermal Zone [THM] (36 C)
[4294681.396000] Attempting manual resume
[4294681.396000] swsusp: Suspend partition has wrong signature?
[4294681.417000] kjournald starting.  Commit interval 5 seconds
[4294681.417000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.739000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.463000] Adding 3036244k swap on /dev/hda5.  Priority:-1 extents:1
[4294685.784000] EXT3 FS on hda1, internal journal
[4294693.425000] lp: driver loaded but no devices found
[4294693.450000] mice: PS/2 mouse device common for all mice
[4294693.476000] ieee1394: Initialized config rom entry `ip1394'
[4294693.483000] SCSI subsystem initialized
[4294693.486000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294693.866000] alps.c: Enabling hardware tapping
[4294694.028000] input: PS/2 Mouse on isa0060/serio1
[4294694.089000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294694.398000] ts: Compaq touchscreen protocol output
[4294697.076000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294700.453000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.458000] agpgart: Detected an Intel 855PM Chipset.
[4294700.475000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294700.526000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.529000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.529000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.697000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.697000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.740000] hw_random: cannot enable RNG, aborting
[4294700.992000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294700.992000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294701.801000] intel8x0_measure_ac97_clock: measured 49466 usecs
[4294701.801000] intel8x0: clocking to 48000
[4294703.010000] Linux Kernel Card Services
[4294703.010000]   options:  [pci] [cardbus] [pm]
[4294703.016000] PCI: Enabling device 0000:02:01.0 (0000 -> 0002)
[4294703.016000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294703.016000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:0191]
[4294703.016000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294703.016000] Yenta: Routing CardBus interrupts to PCI
[4294703.016000] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64
[4294703.237000] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[4294703.237000] Socket status: 30000086
[4294703.311000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294703.311000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294703.364000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]
[4294703.418000] ieee80211_crypt: registered algorithm 'NULL'
[4294703.502000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4294703.502000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4294703.502000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4294703.502000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4294703.502000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294703.502000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4294703.502000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4294703.502000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4294703.503000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294703.503000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294703.514000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4294703.514000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4294703.514000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4294703.514000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4294703.514000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4294703.514000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4294703.514000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4294703.514000] ipw2200: Unknown symbol ieee80211_txb_free
[4294703.515000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294703.515000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4294703.515000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4294703.515000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4294703.515000] ipw2200: Unknown symbol escape_essid
[4294703.515000] ipw2200: disagrees about version of symbol ieee80211_rx
[4294703.515000] ipw2200: Unknown symbol ieee80211_rx
[4294703.515000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4294703.515000] ipw2200: Unknown symbol ieee80211_rx_mgt
[4294704.621000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc00030e660c1]
[4294704.910000] Real Time Clock Driver v1.12
[4294704.966000] input: PC Speaker
[4294705.926000] NET: Registered protocol family 17
[4294708.264000] ACPI: AC Adapter [AC] (on-line)
[4294708.565000] ACPI: Battery Slot [BAT0] (battery present)
[4294708.565000] ACPI: Battery Slot [BAT1] (battery absent)
[4294708.578000] ACPI: Lid Switch [LID]
[4294708.578000] ACPI: Power Button (CM) [PBTN]
[4294708.578000] ACPI: Sleep Button (CM) [SBTN]
[4294708.652000] ibm_acpi: ec object not found
[4294708.734000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294716.339000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294716.339000] hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
[4294716.339000] ide: failed opcode was: unknown
[4294716.339000] end_request: I/O error, dev hdc, sector 0
[4294716.339000] Buffer I/O error on device hdc, logical block 0
[4294722.162000] apm: BIOS not found.
[4294722.871000] cs: IO port probe 0x100-0x4ff: clean.
[4294722.873000] cs: IO port probe 0xc00-0xcf7: clean.
[4294722.873000] cs: IO port probe 0xa00-0xaff: clean.
[4294723.584000] Bluetooth: Core ver 2.7
[4294723.584000] NET: Registered protocol family 31
[4294723.584000] Bluetooth: HCI device and connection manager initialized
[4294723.584000] Bluetooth: HCI socket layer initialized
[4294723.641000] Bluetooth: L2CAP ver 2.7
[4294723.641000] Bluetooth: L2CAP socket layer initialized
[4294723.703000] Bluetooth: RFCOMM ver 1.5
[4294723.703000] Bluetooth: RFCOMM socket layer initialized
[4294723.703000] Bluetooth: RFCOMM TTY layer initialized
[4294769.829000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4294769.829000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4294769.829000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4294769.830000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4294769.830000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4294769.830000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4294769.830000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4294769.830000] ipw2200: Unknown symbol ieee80211_txb_free
[4294769.830000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294769.830000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4294769.830000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4294769.830000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4294769.830000] ipw2200: Unknown symbol escape_essid
[4294769.831000] ipw2200: disagrees about version of symbol ieee80211_rx
[4294769.831000] ipw2200: Unknown symbol ieee80211_rx
[4294769.832000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4294769.832000] ipw2200: Unknown symbol ieee80211_rx_mgt

```

Am I doing something wrong? Or am I missing a certain step. When I was using Debian, all I had to do was make, make install, then modprobe and everything worked. Any suggestions would help. I used the information in the following threads to install wpa_supplicant and to upgrade the drivers:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+WPA](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+WPA)
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by lokirulez on 2006-01-16
I figured it out. I needed to remove the old ipw2200 drivers prior to installation, I thought I did....I was wrong. Anyway, everything went well until I restarted. Once I restarted, my interface was missing. I had to manually load the driver from the source directory via **sudo sh load**. Is there a way to have this load durring boot?

---

### Post by Lambert on 2006-01-16
Add the driver to the /etc/modules file and it should load on boot.

---

