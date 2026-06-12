---
title: "Where's the sound : ("
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by BitTorrentBuddha on 2006-01-15
I've only had ubuntu installed for a few days, and it's come to my attention that the sound isn't quite working...
the sound is onboard and I have no idea why it's not working :???:

---

### Post by BitTorrentBuddha on 2006-01-15
If it's of any use, my motherboard is a pc chips m960gv

---

### Post by ghansel on 2006-01-15
Do you get startup sounds?

---

### Post by BitTorrentBuddha on 2006-01-15
nothing i'm afraid:(

---

### Post by BitTorrentBuddha on 2006-01-15
Can anyone help me?
Is this a mobo issue?
:confused:

---

### Post by ghansel on 2006-01-15
It could be, or it could be an install issue. You could borrow or buy a (cheap) soundcard from a friend to see which... that's what worked for me on an old PII.

---

### Post by BitTorrentBuddha on 2006-01-15
I'm pretty sure it's not the card, because it worked back when it was a windows machine :(

---

### Post by ghansel on 2006-01-15
Sorry for the ambiguity. I didn't mean that the hardware itself had a problem, merely that it simply may not be supported, difficult as that may be.

---

### Post by crovax666 on 2006-01-15
Check if you have some kind of sound device under /dev

On my box /dev/audio is autodetected.

If no such thing is detected, or nothing audio erlated I would suggest trying the "lspci" command from commandline check if any sound card like device is listed there.

It is also possible that you don't have the right things installed, personally I'm using debian (but this should be almost completely the same with ubuntu) but when I just installed my system I had to install alsa and configure it a bit to get the sound to work right.

Also make sure to tell the applications you use which mixer device they're to send their audio output to. This may depend a bit on your desktop environment in the case of KDE you're most likely using the "arts" sound daemon which works... and in most other cases I'd suggest to try alsa.

But I'm sure this is all already mentioned in some FAQ with more detail, so go look for that.

Note: the mixer is essential you can play one audiostream with kinda low quality typically without installing a sound daemon. However this will block the sound device then and play your stuff. The proper way is to let the sound daemon access the device and mix what you send to it.

---

### Post by BitTorrentBuddha on 2006-01-15
there's a file called audio in /dev

---

### Post by az on 2006-01-15
Please post what the device manager is seeing as your sound card (name of chipset)

You can also just post the output from

lspci

(open a terminal and type that....)

---

### Post by newuser111 on 2006-01-15
first of all check to see sound isnt muted under the sound control

try sudo killall esd in a terminal and change sound ouput to alsa in XMMS and see if it plays, sometimes esd hogs the sound card output

its too bad ubuntu devs removed alsaconf from alsa utils, because that is a great sound setup utility, if you download and compile the alsa drivers from the [http://www.alsa-project.org/](http://www.alsa-project.org/) you can get alsaconf

---

### Post by BitTorrentBuddha on 2006-01-16
> 0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
That's what it has for sound

---

### Post by az on 2006-01-16
[QUOTE=BitTorrentBuddha]That's what it has for sound[/QUOTE]
That should be an ac97 codec device.  Post the whole lspci to see if there are any conflicts.

Also, post the result from
dmesg
To see how it is being set up at boot.

---

### Post by BitTorrentBuddha on 2006-01-16
> 0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP
lspci

---

### Post by BitTorrentBuddha on 2006-01-16
> [4294668.228000] VFS: Disk quotas dquot_6.5.1
[4294668.228000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.228000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.228000] devfs: boot_options: 0x0
[4294668.228000] Initializing Cryptographic API
[4294668.228000] isapnp: Scanning for PnP cards...
[4294668.582000] isapnp: No Plug & Play device found
[4294668.662000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294668.662000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294668.662000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.662000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.662000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.663000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.670000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.670000] io scheduler noop registered
[4294668.671000] io scheduler anticipatory registered
[4294668.671000] io scheduler deadline registered
[4294668.671000] io scheduler cfq registered
[4294668.672000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.672000] EISA: Probing bus 0 at eisa.0
[4294668.672000] EISA: Detected 0 cards.
[4294668.672000] NET: Registered protocol family 2
[4294668.682000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294668.682000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294668.684000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.684000] TCP: Hash tables configured (established 131072 bind 65536)
[4294668.685000] NET: Registered protocol family 8
[4294668.685000] NET: Registered protocol family 20
[4294668.685000] ACPI wakeup devices:
[4294668.685000] PCI0 PS2K UAR1 EUSB  USB USB2 USB3 S139 AC97 MC97  MAC PWRB SLPB
[4294668.685000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.685000] Freeing unused kernel memory: 224k freed
[4294668.705000] input: AT Raw Set 2 keyboard on isa0060/serio1
[4294668.729000] vga16fb: initializing
[4294668.729000] vga16fb: mapped to 0xc00a0000
[4294668.839000] Console: switching to colour frame buffer device 80x30
[4294668.839000] fb0: VGA16 VGA frame buffer device
[4294669.944000] Capability LSM initialized
[4294669.966000] NET: Registered protocol family 1
[4294669.987000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.987000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.987000] ACPI: bus type ide registered
[4294670.006000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294670.006000] SIS5513: chipset revision 1
[4294670.006000] SIS5513: not 100% native mode: will probe irqs later
[4294670.006000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294670.006000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294670.006000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[4294670.006000] Probing IDE interface ide0...
[4294670.678000] hda: CD-W54E, ATAPI CD/DVD-ROM drive
[4294671.392000] hdb: LTN485S, ATAPI CD/DVD-ROM drive
[4294671.443000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.443000] Probing IDE interface ide1...
[4294671.707000] hdc: QUANTUM FIREBALLlct10 30, ATA DISK drive
[4294672.319000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.319000] Probing IDE interface ide2...
[4294672.832000] Probing IDE interface ide3...
[4294673.344000] Probing IDE interface ide4...
[4294673.856000] Probing IDE interface ide5...
[4294674.377000] hda: ATAPI 32X CD-ROM CD-R/RW drive, 1280kB Cache
[4294674.377000] Uniform CD-ROM driver Revision: 3.20
[4294674.922000] hdb: ATAPI 48X CD-ROM drive, 120kB Cache
[4294674.931000] hdc: max request size: 128KiB
[4294674.939000] hdc: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63, UDMA(33)
[4294674.939000] hdc: cache flushes not supported
[4294674.939000]  /dev/ide/host0/bus1/target0/lun0: p1 p2 < p5 >
[4294676.060000] Attempting manual resume
[4294676.060000] swsusp: Suspend partition has wrong signature?
[4294676.128000] usbcore: registered new driver usbfs
[4294676.128000] usbcore: registered new driver hub
[4294676.129000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.129000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294676.129000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294676.130000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[4294676.130000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdffdc000
[4294676.183000] hub 1-0:1.0: USB hub found
[4294676.183000] hub 1-0:1.0: 3 ports detected
[4294676.186000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294676.186000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294676.186000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[4294676.186000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdffdd000
[4294676.239000] hub 2-0:1.0: USB hub found
[4294676.239000] hub 2-0:1.0: 3 ports detected
[4294676.242000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294676.242000] ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
[4294676.242000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[4294676.242000] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdffde000
[4294676.295000] hub 3-0:1.0: USB hub found
[4294676.295000] hub 3-0:1.0: 2 ports detected
[4294676.332000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[4294676.332000] ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
[4294676.332000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[4294676.332000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffdf000
[4294676.332000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[4294676.332000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.332000] hub 4-0:1.0: USB hub found
[4294676.332000] hub 4-0:1.0: 8 ports detected
[4294676.366000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.366000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294676.367000] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[4294676.380000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294676.381000] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:11:5b:f1:61:a7.
[4294679.616000] ACPI: CPU0 (power states: C1[C1])
[4294679.616000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294679.802000] Attempting manual resume
[4294679.823000] swsusp: Suspend partition has wrong signature?
[4294679.857000] kjournald starting.  Commit interval 5 seconds
[4294679.857000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.333000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.436000] Adding 1220900k swap on /dev/hdc5.  Priority:-1 extents:1
[4294686.674000] EXT3 FS on hdc1, internal journal
[4294695.873000] lp: driver loaded but no devices found
[4294695.913000] mice: PS/2 mouse device common for all mice
[4294698.557000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.748000] cdrom: open failed.
[4294704.116000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.133000] agpgart: Detected SiS 661 chipset
[4294704.160000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294704.315000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.339000] shpchp: shpc_init : shpc_cap_offset == 0
[4294704.339000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294704.829000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[4294705.137000] intel8x0_measure_ac97_clock: measured 49532 usecs
[4294705.137000] intel8x0: clocking to 48000
[4294706.381000] ath_hal: module license 'Proprietary' taints kernel.
[4294706.390000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294706.401000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294706.410000] ath_rate_sample: 1.2
[4294706.423000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294706.432000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294707.020000] Build date: Oct 11 2005
[4294707.020000] Debugging version (IEEE80211)
[4294707.020000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294707.020000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294707.020000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294707.020000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294707.020000] ath0: mac 7.9 phy 4.5 radio 5.6
[4294707.020000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294707.020000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294707.020000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294707.020000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294707.020000] ath0: Use hw queue 8 for CAB traffic
[4294707.020000] ath0: Use hw queue 9 for beacons
[4294707.020000] Debugging version (ATH)
[4294707.020000] ath0: Atheros 5212: mem=0xdfff0000, irq=16
[4294708.754000] Real Time Clock Driver v1.12
[4294708.928000] input: PC Speaker
[4294709.212000] FDC 0 is a post-1991 82077
[4294710.364000] NET: Registered protocol family 17
[4294718.551000] NET: Registered protocol family 10
[4294718.551000] Disabled Privacy Extensions on device c02eb280(lo)
[4294718.551000] IPv6 over IPv4 tunneling driver
[4294721.638000] ACPI: Power Button (FF) [PWRF]
[4294721.638000] ACPI: Power Button (CM) [PWRB]
[4294721.638000] ACPI: Sleep Button (CM) [SLPB]
[4294721.834000] ibm_acpi: ec object not found
[4294728.582000] ath0: no IPv6 routers present
[4294733.707000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294733.707000] apm: overridden by ACPI.
[4294736.008000] Bluetooth: Core ver 2.7
[4294736.008000] NET: Registered protocol family 31
[4294736.008000] Bluetooth: HCI device and connection manager initialized
[4294736.008000] Bluetooth: HCI socket layer initialized
[4294736.052000] Bluetooth: L2CAP ver 2.7
[4294736.052000] Bluetooth: L2CAP socket layer initialized
[4294736.097000] Bluetooth: RFCOMM ver 1.5
[4294736.097000] Bluetooth: RFCOMM socket layer initialized
[4294736.097000] Bluetooth: RFCOMM TTY layer initialized
[4294763.781000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294769.767000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294770.133000] ts: Compaq touchscreen protocol output
samm@Ubuntu:~$ clear

samm@Ubuntu:~$ dmesg
296000] ACPI: DSDT (v001   M960 960GVV30 0x00000000 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 3e000000 (gap: 3e000000:c0e00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hdc1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2000.042 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.382000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.383000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.415000] Memory: 998556k/1015616k available (1415k kernel code, 16268k reserved, 763k data, 224k init, 98112k highmem)
[4294667.415000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.415000] Calibrating delay loop... 3964.92 BogoMIPS (lpj=1982464)
[4294667.437000] Security Framework v1.0.0 initialized
[4294667.437000] SELinux:  Disabled at boot.
[4294667.437000] Mount-cache hash table entries: 512
[4294667.437000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.437000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.437000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.437000] CPU: L2 cache: 128K
[4294667.437000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294667.437000] CPU: Intel(R) Celeron(R) CPU 2.00GHz stepping 09
[4294667.437000] Enabling fast FPU save and restore... done.
[4294667.437000] Enabling unmasked SIMD FPU exception support... done.
[4294667.437000] Checking 'hlt' instruction... OK.
[4294667.441000] Checking for popad bug... OK.
[4294667.441000] checking if image is initramfs... it is
[4294667.984000] Freeing initrd memory: 4821k freed
[4294667.986000] ACPI: Looking for DSDT in initrd... not found!
[4294668.042000]  not found!
[4294668.043000]     ACPI-0457: *** Error: Looking up [GPIX] in namespace, AE_ALREADY_EXISTS
[4294668.050000] ENABLING IO-APIC IRQs
[4294668.050000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.161000] NET: Registered protocol family 16
[4294668.161000] EISA bus registered
[4294668.161000] ACPI: bus type pci registered
[4294668.162000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294668.162000] PCI: Using configuration type 1
[4294668.162000] mtrr: v2.0 (20020519)
[4294668.163000] ACPI: Subsystem revision 20050729
[4294668.177000] ACPI: Interpreter enabled
[4294668.177000] ACPI: Using IOAPIC for interrupt routing
[4294668.178000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.178000] PCI: Probing PCI hardware (bus 00)
[4294668.178000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.184000] Boot video device is 0000:01:00.0
[4294668.196000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.209000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.210000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294668.210000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[4294668.210000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.211000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[4294668.211000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *7 10 11 12 14 15)
[4294668.212000] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10 11 12 14 15)
[4294668.212000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294668.213000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.213000] pnp: PnP ACPI init
[4294668.221000] pnp: PnP ACPI: found 10 devices
[4294668.221000] PnPBIOS: Disabled by ACPI PNP
[4294668.221000] PCI: Using ACPI for IRQ routing
[4294668.221000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.227000] audit: initializing netlink socket (disabled)
[4294668.227000] audit: initialized
[4294668.227000] highmem bounce pool size: 64 pages
[4294668.228000] VFS: Disk quotas dquot_6.5.1
[4294668.228000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.228000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.228000] devfs: boot_options: 0x0
[4294668.228000] Initializing Cryptographic API
[4294668.228000] isapnp: Scanning for PnP cards...
[4294668.582000] isapnp: No Plug & Play device found
[4294668.662000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294668.662000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294668.662000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.662000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.662000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.663000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.670000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.670000] io scheduler noop registered
[4294668.671000] io scheduler anticipatory registered
[4294668.671000] io scheduler deadline registered
[4294668.671000] io scheduler cfq registered
[4294668.672000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.672000] EISA: Probing bus 0 at eisa.0
[4294668.672000] EISA: Detected 0 cards.
[4294668.672000] NET: Registered protocol family 2
[4294668.682000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294668.682000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294668.684000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.684000] TCP: Hash tables configured (established 131072 bind 65536)
[4294668.685000] NET: Registered protocol family 8
[4294668.685000] NET: Registered protocol family 20
[4294668.685000] ACPI wakeup devices:
[4294668.685000] PCI0 PS2K UAR1 EUSB  USB USB2 USB3 S139 AC97 MC97  MAC PWRB SLPB
[4294668.685000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.685000] Freeing unused kernel memory: 224k freed
[4294668.705000] input: AT Raw Set 2 keyboard on isa0060/serio1
[4294668.729000] vga16fb: initializing
[4294668.729000] vga16fb: mapped to 0xc00a0000
[4294668.839000] Console: switching to colour frame buffer device 80x30
[4294668.839000] fb0: VGA16 VGA frame buffer device
[4294669.944000] Capability LSM initialized
[4294669.966000] NET: Registered protocol family 1
[4294669.987000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.987000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.987000] ACPI: bus type ide registered
[4294670.006000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294670.006000] SIS5513: chipset revision 1
[4294670.006000] SIS5513: not 100% native mode: will probe irqs later
[4294670.006000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294670.006000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294670.006000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[4294670.006000] Probing IDE interface ide0...
[4294670.678000] hda: CD-W54E, ATAPI CD/DVD-ROM drive
[4294671.392000] hdb: LTN485S, ATAPI CD/DVD-ROM drive
[4294671.443000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.443000] Probing IDE interface ide1...
[4294671.707000] hdc: QUANTUM FIREBALLlct10 30, ATA DISK drive
[4294672.319000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.319000] Probing IDE interface ide2...
[4294672.832000] Probing IDE interface ide3...
[4294673.344000] Probing IDE interface ide4...
[4294673.856000] Probing IDE interface ide5...
[4294674.377000] hda: ATAPI 32X CD-ROM CD-R/RW drive, 1280kB Cache
[4294674.377000] Uniform CD-ROM driver Revision: 3.20
[4294674.922000] hdb: ATAPI 48X CD-ROM drive, 120kB Cache
[4294674.931000] hdc: max request size: 128KiB
[4294674.939000] hdc: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63, UDMA(33)
[4294674.939000] hdc: cache flushes not supported
[4294674.939000]  /dev/ide/host0/bus1/target0/lun0: p1 p2 < p5 >
[4294676.060000] Attempting manual resume
[4294676.060000] swsusp: Suspend partition has wrong signature?
[4294676.128000] usbcore: registered new driver usbfs
[4294676.128000] usbcore: registered new driver hub
[4294676.129000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.129000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294676.129000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294676.130000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[4294676.130000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdffdc000
[4294676.183000] hub 1-0:1.0: USB hub found
[4294676.183000] hub 1-0:1.0: 3 ports detected
[4294676.186000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294676.186000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294676.186000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[4294676.186000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdffdd000
[4294676.239000] hub 2-0:1.0: USB hub found
[4294676.239000] hub 2-0:1.0: 3 ports detected
[4294676.242000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294676.242000] ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
[4294676.242000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[4294676.242000] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdffde000
[4294676.295000] hub 3-0:1.0: USB hub found
[4294676.295000] hub 3-0:1.0: 2 ports detected
[4294676.332000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[4294676.332000] ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
[4294676.332000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[4294676.332000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffdf000
[4294676.332000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[4294676.332000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.332000] hub 4-0:1.0: USB hub found
[4294676.332000] hub 4-0:1.0: 8 ports detected
[4294676.366000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.366000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294676.367000] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[4294676.380000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294676.381000] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:11:5b:f1:61:a7.
[4294679.616000] ACPI: CPU0 (power states: C1[C1])
[4294679.616000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294679.802000] Attempting manual resume
[4294679.823000] swsusp: Suspend partition has wrong signature?
[4294679.857000] kjournald starting.  Commit interval 5 seconds
[4294679.857000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.333000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.436000] Adding 1220900k swap on /dev/hdc5.  Priority:-1 extents:1
[4294686.674000] EXT3 FS on hdc1, internal journal
[4294695.873000] lp: driver loaded but no devices found
[4294695.913000] mice: PS/2 mouse device common for all mice
[4294698.557000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.748000] cdrom: open failed.
[4294704.116000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.133000] agpgart: Detected SiS 661 chipset
[4294704.160000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294704.315000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.339000] shpchp: shpc_init : shpc_cap_offset == 0
[4294704.339000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294704.829000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[4294705.137000] intel8x0_measure_ac97_clock: measured 49532 usecs
[4294705.137000] intel8x0: clocking to 48000
[4294706.381000] ath_hal: module license 'Proprietary' taints kernel.
[4294706.390000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294706.401000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294706.410000] ath_rate_sample: 1.2
[4294706.423000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294706.432000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294707.020000] Build date: Oct 11 2005
[4294707.020000] Debugging version (IEEE80211)
[4294707.020000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294707.020000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294707.020000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294707.020000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294707.020000] ath0: mac 7.9 phy 4.5 radio 5.6
[4294707.020000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294707.020000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294707.020000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294707.020000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294707.020000] ath0: Use hw queue 8 for CAB traffic
[4294707.020000] ath0: Use hw queue 9 for beacons
[4294707.020000] Debugging version (ATH)
[4294707.020000] ath0: Atheros 5212: mem=0xdfff0000, irq=16
[4294708.754000] Real Time Clock Driver v1.12
[4294708.928000] input: PC Speaker
[4294709.212000] FDC 0 is a post-1991 82077
[4294710.364000] NET: Registered protocol family 17
[4294718.551000] NET: Registered protocol family 10
[4294718.551000] Disabled Privacy Extensions on device c02eb280(lo)
[4294718.551000] IPv6 over IPv4 tunneling driver
[4294721.638000] ACPI: Power Button (FF) [PWRF]
[4294721.638000] ACPI: Power Button (CM) [PWRB]
[4294721.638000] ACPI: Sleep Button (CM) [SLPB]
[4294721.834000] ibm_acpi: ec object not found
[4294728.582000] ath0: no IPv6 routers present
[4294733.707000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294733.707000] apm: overridden by ACPI.
[4294736.008000] Bluetooth: Core ver 2.7
[4294736.008000] NET: Registered protocol family 31
[4294736.008000] Bluetooth: HCI device and connection manager initialized
[4294736.008000] Bluetooth: HCI socket layer initialized
[4294736.052000] Bluetooth: L2CAP ver 2.7
[4294736.052000] Bluetooth: L2CAP socket layer initialized
[4294736.097000] Bluetooth: RFCOMM ver 1.5
[4294736.097000] Bluetooth: RFCOMM socket layer initialized
[4294736.097000] Bluetooth: RFCOMM TTY layer initialized
[4294763.781000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294769.767000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294770.133000] ts: Compaq touchscreen protocol output
dmesg

EDIT: damn smileys

---

### Post by BitTorrentBuddha on 2006-01-16
I'm going to bed, I really wanna get sound on my computer, downloaded the new episode of lost and I'm just waiting on the sound :smile:

---

### Post by BitTorrentBuddha on 2006-01-17
bump :(

---

### Post by az on 2006-01-17
Try loading the intel8x0 module

sudo modprobe intel8x0

If that works, (Restart X) you need to know why the module is not loading.

Check to see if the intel8x0 module is blacklisted in /etc/hotplug/blacklist.


Also, check to see that sound is not disabled in BIOS.

---

### Post by BitTorrentBuddha on 2006-01-17
> # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
snd_intel8x0m
I found this under the blacklist, I'm not sure if it's the same as intel8x0 though

---

### Post by BitTorrentBuddha on 2006-01-17
The output of sudo modprobe intel8x0 is:

FATAL: Module intel8x0 not found.

---

### Post by BitTorrentBuddha on 2006-01-17
I opened my case back up and connected the front panel audio, there is sound when connected to the front but no volume control

---

### Post by az on 2006-01-17
[QUOTE=BitTorrentBuddha]The output of sudo modprobe intel8x0 is:

FATAL: Module intel8x0 not found.[/QUOTE]
I guess that should be snd_interl8x0...

But the module is probably already loaded if sound is working...

Before you do that, post

lsmod

---

### Post by BitTorrentBuddha on 2006-01-17
> Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
wlan_wep                5888  1
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
sis_agp                 8452  1
agpgart                32328  1 sis_agp
dm_mod                 50364  1
tsdev                   7616  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
evdev                   9088  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sis900                 19456  0
mii                     5248  1 sis900
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd
ide_disk               16128  3
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
sis5513                14472  1
ide_core              125268  4 ide_disk,ide_cd,ide_generic,sis5513
unix                   24624  810
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

when I have headphones plugged into the front, volume control doesn't work nor does mute, it's stuck at [to the best of my guess] max volume.

[PS The output for sudo modprobe snd_intel8x0 is nothing, it just gives me another command line]

---

### Post by az on 2006-01-17
The module is properly loaded.  The output from lspci is before you tried to load the module, right?  (reboot, lspci, then modprobe...)

If that is the case, then this is a bug in the intel8x0 driver.

Try this, blacklist the snd_intle8x0 module (along with the intel8x0m module - which is for a modem based on the ac97 codec.  To do thatm add the name of the module on a line in /etc/hotplug/blacklist.

Add 
i810_audio
to /etc/modules.  This will load an alternate sound driver for your card.  See if that works.

If not, I will advise you on how to report this bug.

---

### Post by az on 2006-01-17
Did you look at all the sound sliders in the volume control?  Double click the volume applet to show all the volume controls.

[https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/23180](https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/23180)

Quote:
"Re: Sound no longer works in kubuntu, though snd_intel8x0 is loaded Posted by Christian <https://launchpad.net/people/info-cvjb> at 2005-10-26 16:36:31 EDT 
Hi,
Have a similar problem with my Intel ICH4 sound chip on my Dell laptop. After the upgrade from Hoary to Breezy, I hear no sound through the speaker, but only through the headphone. The speakers are ok, because shortly I can hear a sound (e.g. an mp3 file), when a system beep is generated, and I don't mean the beep itself ;-)
The relevant mixer levels (PCH, master) are all up and not muted.
Calling alsaconf does not fix the problem.
What information do you need to investigate this any further?
Greetings,
Christian"

And then

"Re: Sound no longer works in kubuntu, though snd_intel8x0 is loaded Posted by Christian <https://launchpad.net/people/info-cvjb> at 2005-10-26 17:17:15 EDT 
Found the solution.
It was really the last mixer slider in alsamixer, named "Extern". Its not a real
slider, but only a toggle, and it was muted :-P
Maybe this info helps others with the same "problem".
Shame on me, and greetings,
Christian"

And finaly:
"Re: Sound no longer works in kubuntu, though snd_intel8x0 is loaded Posted by Flemming Bjerke <https://launchpad.net/people/flem> at 2005-11-06 16:28:54 EST 
(In reply to comment #23)
> I had the same problem and I fixed it by unmuting "Master Surround" in
> alsamixer. It has to be unmuted even if you only have two speakers.
>
> I'm using Ubuntu Breezy. This happened when I dist-upgraded from Hoary.
>
Well, I booted in gnome and after some time, the worked. But, in kde only cd-playing worked. Then, I unmuted PCM in alsamixer, and now it seems to work. (It not because I haven't tried that before!)
flemming"


Does this help?

---

### Post by BitTorrentBuddha on 2006-01-17
Well, in the alsamixer I found that my headphones are hooked up to PCM and that PC speaker was muted. Unmuting PC speaker however did not do as I thought it would.

---

### Post by az on 2006-01-17
PC speaker is the speaker inside your computer case - if it has one - not the speakers you connect to your card.  Turn all the sliders up.  Make sure none are muted (little tiny X on the bottom)

---

### Post by BitTorrentBuddha on 2006-01-17
Ok, I did all that, rebooted and now when I try and use the System>Preferences>Multimedia systems selector> and try to test ESD or ALSA they cannot find the proper pipeline
also in /etc/modules the snd_intel8x0 isn't listed, should it be?

---

### Post by az on 2006-01-17
[QUOTE=BitTorrentBuddha]Ok, I did all that, rebooted and now when I try and use the System>Preferences>Multimedia systems selector> and try to test ESD or ALSA they cannot find the proper pipeline
also in /etc/modules the snd_intel8x0 isn't listed, should it be?[/QUOTE]

The i810_audio module uses the OSS infrastructure.  snd_intel8x0 uses the alsa infrastructure.  If the alsa driver is buggy (not a problem with settings, muted things and sliders) then it is reasonable to try to see if the OSS one works.  If it does not, then forget about it.

Do you get an OSS option in the Multimedia selector?

and if you want to use the OSS driver, then you shold not try to load the ALS one  - That is why you only put the oss one in /etc/modules.

If you want to go back to the alsa one, remove the OSS driver from /etc/modules, and remove the blacklisted one from the blacklist file and reboot.

---

### Post by BitTorrentBuddha on 2006-01-17
The OSS didn't work :( 
but what I was asking before was is the snd_intel8x0 supposed to be listed in modules?

---

### Post by BitTorrentBuddha on 2006-01-17
These are the contents of /etc/modules, is there anything in there that shouldn't be or anything that should be that isn't?
> lp
mousedev
psmouse
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq

---

### Post by az on 2006-01-17
[QUOTE=BitTorrentBuddha]The OSS didn't work :( 
but what I was asking before was is the snd_intel8x0 supposed to be listed in modules?[/QUOTE]
No.  That is properlky loaded by hotplug.  Your last lsmod showed that.

---

### Post by BitTorrentBuddha on 2006-01-19
OK, I think I've just about given up hope on the sound card, what I would like advice on is what to do, buy a new one, wait till dapper and see if that fixes it, or keep trying on this one?

---

### Post by az on 2006-01-19
You can try a Knoppix live cd.  If not, I have a box full of sound cards...

wiki.ubuntu.com/forum/GiveAway

---

### Post by BitTorrentBuddha on 2006-01-19
Ok, I pulled an old sound card from my HP, but I can't find the driver for it, the brand isn't on there anywhere, all the info I have is that it came in the case from the factory built HP Pavillion 8655C, I checked google to see if I could come up with the card-type to little aveil.

---

### Post by az on 2006-01-19
[QUOTE=BitTorrentBuddha]Ok, I pulled an old sound card from my HP, but I can't find the driver for it, the brand isn't on there anywhere, all the info I have is that it came in the case from the factory built HP Pavillion 8655C, I checked google to see if I could come up with the card-type to little aveil.[/QUOTE]
What do you mean, you can't find the driver for it?

The driver for it should already be in the kernel and it will be hotplug loaded when you boot.

---

### Post by BitTorrentBuddha on 2006-01-19
maybe the driver's there, but the card isn't detected to my knowledge, [not in the device manager]

---

### Post by az on 2006-01-20
Here we go again....


Post lsmod lspci and so forth....

---

### Post by BitTorrentBuddha on 2006-01-20
I'm sorry :( 
lsmod
> Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  27
af_packet              20232  2
wlan_wep                5888  1
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
sis_agp                 8452  1
agpgart                32328  1 sis_agp
dm_mod                 50364  1
tsdev                   7616  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
evdev                   9088  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sis900                 19456  0
mii                     5248  1 sis900
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd
ide_disk               16128  3
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_generic             1664  0
sis5513                14472  1
ide_core              125268  4 ide_disk,ide_cd,ide_generic,sis5513
unix                   24624  808
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
lspci
> 0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP

Just tell me if you need dmesg too

---

### Post by BitTorrentBuddha on 2006-01-21
bump

---

### Post by az on 2006-01-21
Can you disable your onboard sound in your bios?

---

