---
title: "Audio stops working at log-on"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by Master Jedi on 2006-05-29
The drumroll sound plays at the log-in screen, but as soon as I log in the sound stops working.

lspci output:
```
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller
0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```



dmesg output:
```
 Framework v1.0.0 initialized
[4294667.940000] SELinux:  Disabled at boot.
[4294667.940000] Mount-cache hash table entries: 512
[4294667.940000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.940000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.940000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.940000] CPU: L2 Cache: 512K (64 bytes/line)
[4294667.940000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294667.940000] CPU: AMD mobile AMD Athlon(tm) XP2600+ stepping 00
[4294667.940000] Enabling fast FPU save and restore... done.
[4294667.940000] Enabling unmasked SIMD FPU exception support... done.
[4294667.940000] Checking 'hlt' instruction... OK.
[4294667.944000] Checking for popad bug... OK.
[4294667.944000] checking if image is initramfs... it is
[4294668.321000] Freeing initrd memory: 4821k freed
[4294668.323000] ACPI: Looking for DSDT in initrd... not found!
[4294668.370000]  not found!
[4294668.384000] ACPI: setting ELCR to 0200 (from 0e28)
[4294668.386000] NET: Registered protocol family 16
[4294668.386000] EISA bus registered
[4294668.386000] ACPI: bus type pci registered
[4294668.393000] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[4294668.393000] PCI: Using configuration type 1
[4294668.393000] mtrr: v2.0 (20020519)
[4294668.393000] ACPI: Subsystem revision 20050729
[4294670.589000] ACPI: Interpreter enabled
[4294670.589000] ACPI: Using PIC for interrupt routing
[4294670.590000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.590000] PCI: Probing PCI hardware (bus 00)
[4294670.590000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.593000] Boot video device is 0000:01:05.0
[4294670.594000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.595000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[4294670.596000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[4294670.596000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[4294670.596000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *9
[4294670.596000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *0, disabled.
[4294670.597000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[4294670.597000] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *10
[4294670.597000] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[4294670.598000] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[4294670.598000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[4294670.601000] burst-mode-ec-10-Aug
[4294670.601000] ACPI: Embedded Controller [EC0] (gpe 24)
[4294670.605000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.605000] pnp: PnP ACPI init
[4294670.609000] pnp: PnP ACPI: found 13 devices
[4294670.609000] PnPBIOS: Disabled by ACPI PNP
[4294670.609000] PCI: Using ACPI for IRQ routing
[4294670.609000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.611000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[4294670.611000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[4294670.611000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[4294670.611000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[4294670.611000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[4294670.611000] Simple Boot Flag at 0x36 set to 0x1
[4294670.612000] audit: initializing netlink socket (disabled)
[4294670.612000] audit: initialized
[4294670.612000] VFS: Disk quotas dquot_6.5.1
[4294670.612000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.612000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.612000] devfs: boot_options: 0x0
[4294670.612000] Initializing Cryptographic API
[4294670.612000] ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
[4294670.612000] Activating ISA DMA hang workarounds.
[4294670.612000] isapnp: Scanning for PnP cards...
[4294670.880000] isapnp: No Plug & Play device found
[4294670.896000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294670.901000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.901000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.901000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.901000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.903000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.903000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[4294670.903000] PCI: setting IRQ 3 as level-triggered
[4294670.903000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[4294670.904000] ttyS53 at I/O 0x8828 (irq = 3) is a 8250
[4294670.904000] ttyS1 at I/O 0x8840 (irq = 3) is a 8250
[4294670.904000] ttyS2 at I/O 0x8850 (irq = 3) is a 8250
[4294670.904000] ttyS3 at I/O 0x8860 (irq = 3) is a 8250
[4294670.904000] ttyS4 at I/O 0x8870 (irq = 3) is a 8250
[4294670.905000] io scheduler noop registered
[4294670.905000] io scheduler anticipatory registered
[4294670.905000] io scheduler deadline registered
[4294670.905000] io scheduler cfq registered
[4294670.906000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.907000] EISA: Probing bus 0 at eisa.0
[4294670.907000] Cannot allocate resource for EISA slot 8
[4294670.907000] EISA: Detected 0 cards.
[4294670.907000] NET: Registered protocol family 2
[4294670.917000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.917000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.917000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.917000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.917000] NET: Registered protocol family 8
[4294670.917000] NET: Registered protocol family 20
[4294670.917000] ACPI wakeup devices:
[4294670.917000] PCI0 MDEM  LAN  LID
[4294670.917000] ACPI: (supports S0 S3 S4 S5)
[4294670.918000] Freeing unused kernel memory: 224k freed
[4294670.930000] vga16fb: initializing
[4294670.930000] vga16fb: mapped to 0xc00a0000
[4294671.050000] Console: switching to colour frame buffer device 80x30
[4294671.050000] fb0: VGA16 VGA frame buffer device
[4294671.071000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.158000] Capability LSM initialized
[4294672.169000] NET: Registered protocol family 1
[4294672.181000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.181000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.181000] ACPI: bus type ide registered
[4294672.185000] Warning: ATI Radeon IGP Northbridge is not yet fully tested.
[4294672.185000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[4294672.186000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[4294672.186000] ALI15X3: chipset revision 196
[4294672.186000] ALI15X3: not 100% native mode: will probe irqs later
[4294672.186000]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[4294672.186000]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
[4294672.186000] Probing IDE interface ide0...
[4294672.450000] hda: IC25N020ATCS04-0, ATA DISK drive
[4294673.062000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.062000] Probing IDE interface ide1...
[4294673.734000] hdc: TOSHIBA CD/DVD-ROM SD-C2612, ATAPI CD/DVD-ROM drive
[4294674.349000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.349000] Probing IDE interface ide2...
[4294674.862000] Probing IDE interface ide3...
[4294675.374000] Probing IDE interface ide4...
[4294675.886000] Probing IDE interface ide5...
[4294676.401000] hda: max request size: 128KiB
[4294676.417000] hda: 39070080 sectors (20003 MB) w/1768KiB Cache, CHS=38760/16/63, UDMA(100)
[4294676.417000] hda: cache flushes not supported
[4294676.417000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294676.507000] hdc: ATAPI 24X DVD-ROM drive, 192kB Cache
[4294676.507000] Uniform CD-ROM driver Revision: 3.20
[4294676.714000] Attempting manual resume
[4294676.715000] swsusp: Suspend partition has wrong signature?
[4294676.737000] usbcore: registered new driver usbfs
[4294676.737000] usbcore: registered new driver hub
[4294676.738000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.738000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[4294676.738000] PCI: setting IRQ 10 as level-triggered
[4294676.738000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 10 (level, low) -> IRQ 10
[4294676.739000] ohci_hcd 0000:00:02.0: ALi Corporation USB 1.1 Controller
[4294676.952000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294676.952000] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0004000
[4294677.005000] hub 1-0:1.0: USB hub found
[4294677.005000] hub 1-0:1.0: 4 ports detected
[4294677.066000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[4294677.066000]   originally by Donald Becker <becker@scyld.com>
[4294677.066000]   http://www.scyld.com/network/natsemi.html
[4294677.066000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[4294677.067000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294677.067000] PCI: setting IRQ 11 as level-triggered
[4294677.067000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294677.069000] natsemi eth0: NatSemi DP8381[56] at 0xd0008000 (0000:00:12.0), 00:0d:9d:80:bd:c3, IRQ 11, port TP.
[4294679.374000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294679.377000] ACPI: Thermal Zone [THRM] (81 C)
[4294679.562000] Attempting manual resume
[4294679.562000] swsusp: Suspend partition has wrong signature?
[4294679.577000] kjournald starting.  Commit interval 5 seconds
[4294679.577000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.292000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.366000] Adding 779144k swap on /dev/hda3.  Priority:-1 extents:1
[4294685.651000] EXT3 FS on hda2, internal journal
[4294694.639000] parport: PnPBIOS parport detected.
[4294694.639000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294694.728000] lp0: using parport0 (interrupt-driven).
[4294694.756000] mice: PS/2 mouse device common for all mice
[4294694.802000] ieee1394: Initialized config rom entry `ip1394'
[4294694.815000] SCSI subsystem initialized
[4294694.830000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294695.465000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[4294695.470000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294695.860000] ts: Compaq touchscreen protocol output
[4294699.009000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294700.307000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294700.307000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[4294700.307000] ide: failed opcode was: unknown
[4294700.308000] cdrom: open failed.
[4294701.180000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294701.316000] NTFS volume version 3.0.
[4294702.791000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.802000] agpgart: Detected Ati IGP320/M chipset
[4294702.823000] agpgart: AGP aperture is 64M @ 0xd4000000
[4294702.928000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.943000] shpchp: shpc_init : shpc_cap_offset == 0
[4294702.943000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294703.131000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[4294703.131000] PCI: setting IRQ 5 as level-triggered
[4294703.131000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[4294704.169000] AC'97 1 does not respond - RESET
[4294704.169000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294704.169000] ali mixer 1 creating error.
[4294705.116000] Linux Kernel Card Services
[4294705.116000]   options:  [pci] [cardbus] [pm]
[4294705.136000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[4294705.136000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[4294705.136000] Yenta: CardBus bridge found at 0000:00:0a.0 [0000:0000]
[4294705.136000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294705.136000] Yenta O2: enabling read prefetch/write burst
[4294705.256000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
[4294705.256000] Socket status: 30000007
[4294705.399000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294705.400000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294705.400000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294705.457000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0007000-d00077ff]  Max Packet=[2048]
[4294705.660000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294705.660000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[4294706.900000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d9d719e801df1][4294707.441000] Real Time Clock Driver v1.12
[4294707.531000] input: PC Speaker
[4294707.871000] FDC 0 is a post-1991 82077
[4294709.581000] eth0: DSPCFG accepted after 0 usec.
[4294709.581000] eth0: link up.
[4294709.581000] eth0: Setting full-duplex based on negotiated link capability.
[4294709.595000] NET: Registered protocol family 17
[4294711.293000] NET: Registered protocol family 10
[4294711.294000] Disabled Privacy Extensions on device c02eb280(lo)
[4294711.294000] IPv6 over IPv4 tunneling driver
[4294712.775000] ACPI: AC Adapter [ACAD] (on-line)
[4294712.822000] ACPI: Battery Slot [BAT1] (battery present)
[4294712.844000] ACPI: Power Button (FF) [PWRF]
[4294712.844000] ACPI: Power Button (CM) [PWRB]
[4294712.844000] ACPI: Lid Switch [LID]
[4294712.958000] ibm_acpi: ec object not found
[4294713.088000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294721.922000] eth0: no IPv6 routers present
[4294722.034000] [drm] Initialized drm 1.0.0 20040925
[4294722.038000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294722.044000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon Mobility U1
[4294722.045000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294722.045000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294722.045000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[4294724.305000] apm: BIOS not found.
[4294725.141000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[4294725.144000] cs: IO port probe 0xc00-0xcf7: clean.
[4294725.145000] cs: IO port probe 0xa00-0xaff: clean.
[4294725.566000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294725.571000] Detected 1988.067 MHz processor.
[4294725.577000] powernow: No PST tables match this cpuid (0x7a0)
[4294725.577000] powernow: This is indicative of a broken BIOS.
[4294725.577000] powernow: Trying ACPI perflib
[4294725.577000] powernow: Minimum speed 530 MHz. Maximum speed 1988 MHz.
[4294726.616000] Bluetooth: Core ver 2.7
[4294726.616000] NET: Registered protocol family 31
[4294726.616000] Bluetooth: HCI device and connection manager initialized
[4294726.616000] Bluetooth: HCI socket layer initialized
[4294726.787000] Bluetooth: L2CAP ver 2.7
[4294726.787000] Bluetooth: L2CAP socket layer initialized
[4294726.867000] Bluetooth: RFCOMM ver 1.5
[4294726.867000] Bluetooth: RFCOMM socket layer initialized
[4294726.867000] Bluetooth: RFCOMM TTY layer initialized
```










What could be the problem?

---

### Post by Master Jedi on 2006-05-29
lsmod:
```
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k7             8616  0
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 powernow_k7,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
i2c_ali1535             6788  0
i2c_ali15x3             7172  0
i2c_core               19728  3 i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_ali5451            22596  0
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  1 snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
ati_agp                 8716  1
agpgart                32328  2 drm,ati_agp
nls_cp437               5888  1
ntfs                   92016  1
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
amd74xx                12828  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 powernow_k7,thermal
fan                     4740  0
natsemi                23904  0
ohci_hcd               18564  0
usbcore               104188  2 ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  5
ide_generic             1664  0
alim15x3               11020  1
ide_core              125268  5 amd74xx,ide_cd,ide_disk,ide_generic,alim15x3
unix                   24624  605
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
```

---

### Post by KiLLeR_WoMBaT on 2006-05-30
I have the same problem...and have had it for MONTHS with no solution from the forums.  I have a different sound card (Intel8x0) and have tried EVERY which way to make it work.

daniel@WoMBaT-Laptop:~$ lsmod
Module                  Size  Used by
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
pcmcia                 24584  4
fglrx                 445772  7
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
ndiswrapper           114376  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
bt878                   9912  0
tuner                  24488  0
tvaudio                21668  0
bttv                  141456  1 bt878
video_buf              19844  1 bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
i2c_core               19728  6 i2c_acpi_ec,tuner,tvaudio,bttv,i2c_algo_bit,tveeprom
videodev                9344  1 bttv
ohci1394               30644  0
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  3
snd_ac97_codec         71420  1 snd_intel8x0
snd_pcm_oss            46240  0
snd_mixer_oss          16256  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 fglrx,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
snd_seq_oss            30848  0
snd_seq_midi_event      6656  1 snd_seq_oss
snd_seq                45072  4 snd_seq_oss,snd_seq_midi_event
snd_timer              21764  3 snd_pcm,snd_seq
snd_seq_device          8332  2 snd_seq_oss,snd_seq
snd                    47716  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
evdev                   9088  1
soundcore               9184  1 snd
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
sd_mod                 17424  0
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ide_disk               16128  3
usb_storage            64704  0
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,usb_storage
usbhid                 30688  0
r8169                  23180  0
pdc202xx_old           10240  1
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  6 ndiswrapper,usb_storage,usbhid,ehci_hcd,uhci_hcdide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  6 ide_disk,usb_storage,pdc202xx_old,ide_cd,ide_generic,piix
unix                   24624  654
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
daniel@WoMBaT-Laptop:~$

---

### Post by Ubuntist on 2006-05-31
I had problems with the audio not working.  In my case, the solution was to double click on the volume control to open it.  Then select the "Switches" tab and make sure that the analog/digital output jack is on (box is checked).  This sometimes seems to get turned off, particularly when I restart a hibernated session.

---

### Post by KiLLeR_WoMBaT on 2006-05-31
Now when I open System>Administration>Sound there is no default sound card and no way to select one.  See the screenshot:

---

### Post by perstromgren on 2007-03-29
> **Ubuntist said:**
> I had problems with the audio not working.  In my case, the solution was to double click on the volume control to open it.  Then select the "Switches" tab and make sure that the analog/digital output jack is on (box is checked).  This sometimes seems to get turned off, particularly when I restart a hibernated session.

Thanks! 

This helped me too! My PCM and Headphones sliders was set to zero, I have no idea why.

Per.

---

