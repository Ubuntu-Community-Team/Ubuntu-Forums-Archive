---
title: "Weird Desktop Video Problem GeForce 6200"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by n0fx on 2006-01-17
I have a strange problem and I tried searching the forums for a resolution before posting a new thread.  The problem that I have is that when I use my desktop for a random amount of time andthe screen starts to mess up.  The graphics on the desktop doesn't seem to refresh anymore. The only remedy is to reboot the computer. 

Here is my setup:

Motherboard: Asus A8R-MVP w/ Opteron 144 CPU
Video Card: Asus N6200TC PCI-X (Nvidia Geforce 6200 chipset)
Memory: 2 x 1 GB Corsair PC3200 Value RAM
OS: Ubuntu 5.10 w/ recompiled kernel 2.6.14cK1 (Patched)
Monitor: Dell E173 LCD (17" LCD)

and here is the output of dmesg, lspci and lsmod:

dmesg:

io: i8042 AUX port at 0x60,0x64 irq 12
[4294670.029000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.029000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharin g enabled
[4294670.029000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.029000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.029000] io scheduler noop registered
[4294670.030000] io scheduler cfq registered
[4294670.030000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294670.030000] EISA: Probing bus 0 at eisa.0
[4294670.030000] Cannot allocate resource for EISA slot 4
[4294670.030000] EISA: Detected 0 cards.
[4294670.030000] NET: Registered protocol family 2
[4294670.039000] IP route cache hash table entries: 131072 (order: 7, 524288 byt es)
[4294670.039000] TCP established hash table entries: 524288 (order: 9, 2097152 b ytes)
[4294670.040000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.041000] TCP: Hash tables configured (established 524288 bind 65536)
[4294670.041000] TCP reno registered
[4294670.041000] TCP bic registered
[4294670.041000] NET: Registered protocol family 8
[4294670.041000] NET: Registered protocol family 20
[4294670.041000] Using IPI Shortcut mode
[4294670.041000] ACPI wakeup devices:
[4294670.041000] P0P2 P0P3 P0P4 P0P5 P0P6 P0P7 PE2P UAR1 USB0 USB1 USB2 UB20 AC9 7 MC97 AZAL
[4294670.041000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.041000] Freeing unused kernel memory: 220k freed
[4294670.055000] vga16fb: initializing
[4294670.055000] vga16fb: mapped to 0xc00a0000
[4294670.285000] Console: switching to colour frame buffer device 80x30
[4294670.285000] fb0: VGA16 VGA frame buffer device
[4294671.354000] NET: Registered protocol family 1
[4294671.366000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.366000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294671.367000] ALI15X3: IDE controller at PCI slot 0000:00:1f.0
[4294671.367000] ACPI: PCI Interrupt 0000:00:1f.0[A] -> GSI 19 (level, low) -> I RQ 16
[4294671.367000] ALI15X3: chipset revision 200
[4294671.367000] ALI15X3: not 100% native mode: will probe irqs later
[4294671.367000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb: DMA
[4294671.367000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd: pio
[4294671.367000] Probing IDE interface ide0...
[4294671.631000] hda: Maxtor 6Y080P0, ATA DISK drive
[4294672.039000] hdb: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
[4294672.090000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.090000] Probing IDE interface ide1...
[4294672.614000] Probing IDE interface ide1...
[4294673.136000] hda: max request size: 128KiB
[4294673.143000] hda: 160086528 sectors (81964 MB) w/7936KiB Cache, CHS=65535/16 /63, UDMA(133)
[4294673.143000] hda: cache flushes supported
[4294673.143000]  hda: hda1 hda2 < hda5 >
[4294673.171000] hdb: ATAPI 48X DVD-ROM drive, 512kB Cache
[4294673.171000] Uniform CD-ROM driver Revision: 3.20
[4294673.357000] Attempting manual resume
[4294673.384000] usbcore: registered new driver usbfs
[4294673.384000] usbcore: registered new driver hub
[4294673.384000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) D river (PCI)
[4294673.385000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> I RQ 17
[4294673.385000] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[4294673.808000] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus num ber 1
[4294673.808000] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xcbffc000
[4294673.861000] hub 1-0:1.0: USB hub found
[4294673.861000] hub 1-0:1.0: 3 ports detected
[4294673.962000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 18 (level, low) -> I RQ 18
[4294673.962000] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[4294673.973000] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus num ber 2
[4294673.973000] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xcbffd000
[4294674.026000] hub 2-0:1.0: USB hub found
[4294674.026000] hub 2-0:1.0: 3 ports detected
[4294674.127000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 19 (level, low) -> I RQ 16
[4294674.127000] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[4294674.138000] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus num ber 3
[4294674.138000] ohci_hcd 0000:00:1c.2: irq 16, io mem 0xcbffe000
[4294674.191000] hub 3-0:1.0: USB hub found
[4294674.191000] hub 3-0:1.0: 3 ports detected
[4294674.310000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> I RQ 19
[4294674.310000] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[4294674.310000] ehci_hcd 0000:00:1c.3: debug port 1
[4294674.331000] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus num ber 4
[4294674.331000] ehci_hcd 0000:00:1c.3: irq 19, io mem 0xcbfffc00
[4294674.331000] ehci_hcd 0000:00:1c.3: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294674.331000] hub 4-0:1.0: USB hub found
[4294674.331000] hub 4-0:1.0: 8 ports detected
[4294674.344000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294674.456000] SCSI subsystem initialized
[4294674.457000] libata version 1.12 loaded.
[4294674.457000] ahci version 1.01
[4294674.457000] PCI: Enabling device 0000:00:1f.1 (0105 -> 0107)
[4294674.458000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> I RQ 16
[4294675.137000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[4294675.503000] usb 2-2: new low speed USB device using ohci_hcd and address 4
[4294676.592000] ahci(0000:00:1f.1) AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf i mpl RAID mode
[4294676.592000] ahci(0000:00:1f.1) flags: ncq ilck pm led clo pmp pio slum part 
[4294676.592000] ata1: SATA max UDMA/133 cmd 0xF8888900 ctl 0x0 bmdma 0x0 irq 16
[4294676.592000] ata2: SATA max UDMA/133 cmd 0xF8888980 ctl 0x0 bmdma 0x0 irq 16
[4294676.592000] ata3: SATA max UDMA/133 cmd 0xF8888A00 ctl 0x0 bmdma 0x0 irq 16
[4294676.592000] ata4: SATA max UDMA/133 cmd 0xF8888A80 ctl 0x0 bmdma 0x0 irq 16
[4294676.794000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01  87:4023 88:407f
[4294676.794000] ata1: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
[4294676.794000] ata1: dev 0 configured for UDMA/133
[4294676.794000] scsi0 : ahci
[4294676.996000] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01  87:4023 88:407f
[4294676.996000] ata2: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
[4294676.996000] ata2: dev 0 configured for UDMA/133
[4294676.996000] scsi1 : ahci
[4294677.198000] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01  87:4023 88:407f
[4294677.198000] ata3: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
[4294677.198000] ata3: dev 0 configured for UDMA/133
[4294677.198000] scsi2 : ahci
[4294677.400000] ata4: no device found (phy stat 00000000)
[4294677.400000] scsi3 : ahci
[4294677.400000]   Vendor: ATA       Model: ST3250823AS       Rev: 3.03
[4294677.400000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294677.400000]   Vendor: ATA       Model: ST3250823AS       Rev: 3.03
[4294677.400000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294677.401000]   Vendor: ATA       Model: ST3250823AS       Rev: 3.03
[4294677.401000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294677.437000] ACPI: PCI Interrupt 0000:02:14.0[A] -> GSI 21 (level, low) -> I RQ 20
[4294677.437000] skge addr 0xceff0000 irq 20 chip Yukon-Lite rev 9
[4294677.437000] skge eth0: addr 00:15:f2:66:5d:02
[4294679.456000] usbcore: registered new driver hiddev
[4294679.465000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0 000:00:1c.1-1
[4294679.473000] input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo M ouse] on usb-0000:00:1c.1-2
[4294679.473000] usbcore: registered new driver usbhid
[4294679.473000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294679.496000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.496000] SCSI device sda: drive cache: write back
[4294679.496000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.496000] SCSI device sda: drive cache: write back
[4294679.496000]  sda: unknown partition table
[4294679.514000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294679.514000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.514000] SCSI device sdb: drive cache: write back
[4294679.514000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.514000] SCSI device sdb: drive cache: write back
[4294679.514000]  sdb: unknown partition table
[4294679.532000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4294679.532000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.532000] SCSI device sdc: drive cache: write back
[4294679.532000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[4294679.532000] SCSI device sdc: drive cache: write back
[4294679.532000]  sdc: unknown partition table
[4294679.554000] Attached scsi disk sdc at scsi2, channel 0, id 0, lun 0
[4294679.927000] ACPI: CPU0 (power states: C1[C1])
[4294679.927000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294679.998000] Attempting manual resume
[4294680.033000] kjournald starting.  Commit interval 5 seconds
[4294680.033000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.098000] md: md driver 0.90.2 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.098000] md: bitmap version 3.39
[4294681.889000] md: md0 stopped.
[4294681.890000] md: bind<sdb>
[4294681.890000] md: bind<sdc>
[4294681.890000] md: bind<sda>
[4294681.967000] raid5: automatically using best checksumming function: pIII_sse
[4294681.972000]    pIII_sse  :  6072.000 MB/sec
[4294681.972000] raid5: using function: pIII_sse (6072.000 MB/sec)
[4294681.981000] md: raid5 personality registered as nr 4
[4294681.987000] raid5: device sda operational as raid disk 0
[4294681.987000] raid5: device sdc operational as raid disk 2
[4294681.987000] raid5: device sdb operational as raid disk 1
[4294681.987000] raid5: allocated 3161kB for md0
[4294681.987000] raid5: raid level 5 set md0 active with 3 out of 3 devices, alg orithm 2
[4294681.987000] RAID5 conf printout:
[4294681.987000]  --- rd:3 wd:3 fd:0
[4294681.987000]  disk 0, o:1, dev:sda
[4294681.987000]  disk 1, o:1, dev:sdb
[4294681.987000]  disk 2, o:1, dev:sdc
[4294684.472000] Adding 3269188k swap on /dev/hda5.  Priority:-1 extents:1 acros s:3269188k
[4294684.748000] EXT3 FS on hda1, internal journal
[4294686.791000] parport: PnPBIOS parport detected.
[4294686.791000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,ECP,DMA]
[4294686.880000] lp0: using parport0 (interrupt-driven).
[4294686.932000] mice: PS/2 mouse device common for all mice
[4294687.026000] ieee1394: Initialized config rom entry `ip1394'
[4294687.030000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294687.030000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294687.030000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294690.082000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294690.840000] cdrom: open failed.
[4294690.929000] device-mapper: dm-linear: Device lookup failed
[4294690.929000] device-mapper: error adding target to table
[4294690.935000] device-mapper: dm-linear: Device lookup failed
[4294690.935000] device-mapper: error adding target to table
[4294690.941000] device-mapper: dm-linear: Device lookup failed
[4294690.941000] device-mapper: error adding target to table
[4294690.947000] device-mapper: dm-linear: Device lookup failed
[4294690.947000] device-mapper: error adding target to table
[4294690.953000] device-mapper: dm-linear: Device lookup failed
[4294690.953000] device-mapper: error adding target to table
[4294690.959000] device-mapper: dm-linear: Device lookup failed
[4294690.959000] device-mapper: error adding target to table
[4294690.965000] device-mapper: dm-linear: Device lookup failed
[4294690.965000] device-mapper: error adding target to table
[4294690.971000] device-mapper: dm-linear: Device lookup failed
[4294690.971000] device-mapper: error adding target to table
[4294691.428000] kjournald starting.  Commit interval 5 seconds
[4294691.428000] EXT3-fs warning: maximal mount count reached, running e2fsck is  recommended
[4294691.438000] EXT3 FS on md0, internal journal
[4294691.438000] EXT3-fs: mounted filesystem with ordered data mode.
[4294694.114000] Linux agpgart interface v0.101 (c) Dave Jones
[4294694.607000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.619000] shpchp: shpc_init : shpc_cap_offset == 0
[4294694.619000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.924000] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294694.924000] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not in serted.
[4294695.013000] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[4294695.013000] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not in serted.
[4294695.335000] ACPI: PCI Interrupt 0000:02:11.0[A] -> GSI 18 (level, low) -> I RQ 18
[4294695.341000] ALSA /home/n0fx/alsa/alsa-driver-1.0.10/pci/emu10k1/../../alsa- kernel/pci/emu10k1/emufx.c:1395: Installing spdif_bug patch: Audigy 2 Platinum [ SB0240P]
[4294696.174000] gameport: EMU10K1 is pci0000:02:11.1/gameport0, io 0xe800, spee d 693kHz
[4294696.261000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294696.261000] ACPI: PCI Interrupt 0000:02:11.2[B] -> GSI 19 (level, low) -> I RQ 16
[4294696.315000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[cefff8 00-ceffffff]  Max Packet=[2048]
[4294696.315000] ACPI: PCI Interrupt 0000:02:13.0[A] -> GSI 20 (level, low) -> I RQ 21
[4294696.369000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[cefff0 00-cefff7ff]  Max Packet=[2048]
[4294697.574000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0091045ddc]
[4294697.879000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011d800007eeb03]
[4294698.052000] Real Time Clock Driver v1.12
[4294698.095000] input: PC Speaker
[4294698.167000] FDC 0 is a post-1991 82077
[4294698.430000] ts: Compaq touchscreen protocol output
[4294699.087000] skge eth1: enabling interface
[4294699.113000] NET: Registered protocol family 17
[4294701.031000] skge eth1: Link is up at 100 Mbps, full duplex, flow control no ne
[4294708.288000] NET: Registered protocol family 10
[4294708.288000] Disabled Privacy Extensions on device c02b0e80(lo)
[4294708.288000] IPv6 over IPv4 tunneling driver
[4294710.239000] ACPI: Power Button (FF) [PWRF]
[4294710.239000] ACPI: Power Button (CM) [PWRB]
[4294710.255000] Using specific hotkey driver
[4294710.282000] ibm_acpi: ec object not found
[4294710.300000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[4294717.089000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294717.089000] apm: overridden by ACPI.
[4294717.814000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (versio n 1.50.4)
[4294717.817000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[4294718.712000] eth1: no IPv6 routers present
[4294718.871000] Bluetooth: Core ver 2.7
[4294718.871000] NET: Registered protocol family 31
[4294718.871000] Bluetooth: HCI device and connection manager initialized
[4294718.871000] Bluetooth: HCI socket layer initialized
[4294718.939000] Bluetooth: L2CAP ver 2.7
[4294718.939000] Bluetooth: L2CAP socket layer initialized
[4294718.956000] Bluetooth: RFCOMM ver 1.5
[4294718.956000] Bluetooth: RFCOMM socket layer initialized
[4294718.956000] Bluetooth: RFCOMM TTY layer initialized

lspci:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
0000:00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:1e.0 ISA bridge: ALi Corporation: Unknown device 1575
0000:00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
0000:00:1f.1 RAID bus controller: ALi Corporation: Unknown device 5288 (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0161 (rev a1)
0000:02:11.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:11.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:02:11.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:02:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:14.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 14)

lsmod:

Module                  Size  Used by
rfcomm                 35740  0
l2cap                  22404  5 rfcomm
bluetooth              42116  4 rfcomm,l2cap
cpufreq_userspace       4572  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6300  0
cpufreq_conservative     7076  0
video                  16388  0
button                  6672  0
battery                 9732  0
container               4608  0
ac                      4996  0
ipv6                  219648  6
af_packet              20360  2
tsdev                   7232  0
floppy                 54980  0
pcspkr                  3680  0
rtc                    11576  0
sk98lin               143456  0
ohci1394               30516  0
emu10k1_gp              3712  0
gameport               14216  2 emu10k1_gp
snd_emu10k1_synth       6656  0
snd_emux_synth         32384  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6272  1 snd_emux_synth
snd_seq_dummy           3972  0
snd_seq_oss            30720  0
snd_seq_midi            8736  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                45584  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            98084  2 snd_emu10k1_synth
snd_rawmidi            22944  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8588  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         83104  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          17024  1 snd_pcm_oss
snd_pcm                78088  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21892  3 snd_seq,snd_emu10k1,snd_pcm
snd_ac97_bus            2304  1 snd_ac97_codec
snd_page_alloc         10376  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  2 snd_emux_synth,snd_emu10k1
snd                    50532  16 snd_emux_synth,snd_seq_virmidi,snd_seq_dummy,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
i2c_ali1535             7044  0
i2c_ali15x3             7300  0
i2c_core               20112  2 i2c_ali1535,i2c_ali15x3
shpchp                 80996  0
pci_hotplug            25268  1 shpchp
ati_agp                 8204  0
agpgart                31816  1 ati_agp
dm_mod                 51772  0
amd74xx                12956  0 [permanent]
sr_mod                 15524  0
sbp2                   21252  0
ieee1394               88376  2 ohci1394,sbp2
psmouse                33412  0
mousedev               10528  1
parport_pc             32452  1
lp                     10820  0
parport                32072  2 parport_pc,lp
raid5                  20736  1
xor                    14216  1 raid5
md_mod                 56784  2 raid5
ext3                  118024  2
jbd                    48148  1 ext3
thermal                13704  0
processor              22972  1 thermal
fan                     4868  0
sd_mod                 17168  3
usbhid                 32096  0
skge                   32656  0
ahci                   11012  3
libata                 43912  1 ahci
scsi_mod              126568  5 sr_mod,sbp2,sd_mod,ahci,libata
ehci_hcd               29960  0
ohci_hcd               18436  0
usbcore               106624  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 37252  0
cdrom                  33696  2 sr_mod,ide_cd
ide_disk               16256  3
ide_generic             1408  0 [permanent]
generic                 4612  0 [permanent]
alim15x3               10892  0 [permanent]
ide_core              112736  6 amd74xx,ide_cd,ide_disk,ide_generic,generic,alim15x3
unix                   24624  771
vga16fb                12104  1
vgastate                8448  1 vga16fb
softcursor              2304  1 vga16fb
cfbimgblt               3072  1 vga16fb
cfbfillrect             3712  1 vga16fb
cfbcopyarea             3584  1 vga16fb
fbcon                  35584  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 4992  1 fbcon

Also, I used Automatix's Nvidia driver installation but I'm not sure if it's fully installed. There is a shortcut on the menu (it works) but when I try to run glxgears or glfxinfo in the shell, I get these errors:

glxgears:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

glxinfo:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Here is the xorg.conf, just incase:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

I was wondering if anyone know what is wrong and how to fix the video problem that I'm having?  I have also attached a screenshot of what happens when the graphics get all messed up.  Thanks!

---

### Post by ]Nbx*cmD[ on 2006-01-26
Wow!
That doesn't seem to be a software problem :-k
Did it happen to you with other OSes?

---

### Post by n0fx on 2006-01-26
I believe it is a software problem.  I installed a newer version of the Nvidia drivers and the graphic problem went away but now I get intermitten lockups once in a while, even if I disable the screensaver, screen blackout timeout periods and acpi, apm, etc.  It's doing better but I can't go to power saving mode now.

---

### Post by n0fx on 2006-04-17
I managed to get this problem fixed for anyone who gets this same problem. I just installed the latest NVIDIA drivers (1.0-8756) and the graphical glitches aren't there.

---

