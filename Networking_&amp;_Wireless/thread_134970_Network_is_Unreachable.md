---
title: "Network is Unreachable"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by qqqqqqqqqqqqqqqqq on 2006-02-22
I've never had this problem with any other operating system. I've got a Dell dual-booted with Windows XP (which, so far, is working far nicer than Ubuntu is), and Ubuntu. I'm having a hard time figuring out why this I'm having this problem.

```

garbage:/data# uname -a

```

```

Linux garbage 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

```

```

garbage:/data# ifconfig

```

```

Module                  Size  Used by
ipv6                  229504  6 
proc_intf               4100  0 
freq_table              4100  0 
cpufreq_userspace       4572  0 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
video                  16260  0 
sony_acpi               6280  0 
pcc_acpi               11264  0 
button                  6800  0 
battery                10244  0 
container               4608  0 
ac                      4996  0 
e100                   32384  0 
mii                     4736  1 e100
i2c_i801                8076  0 
i2c_core               21264  1 i2c_i801
piix                    9988  1 
usblp                  12032  0 
snd_intel8x0           29984  2 
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
usbhid                 29376  0 
ehci_hcd               29444  0 
uhci_hcd               30224  0 
usbcore               107384  5 usblp,usbhid,ehci_hcd,uhci_hcd
pci_hotplug            30512  0 
intel_agp              20636  1 
agpgart                31784  1 intel_agp
rtc                    12216  0 
pcspkr                  3816  0 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
tsdev                   7488  0 
evdev                   9088  0 
psmouse                19336  0 
mousedev               11160  1 
parport_pc             34372  1 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_generic             1664  0 
ide_disk               18176  0 
ide_cd                 38532  0 
ide_core              118988  4 piix,ide_generic,ide_disk,ide_cd
cdrom                  36508  1 ide_cd
ext3                  120968  4 
jbd                    54168  1 ext3
sd_mod                 16784  5 
ata_piix                8836  10 
libata                 44548  1 ata_piix
scsi_mod              119936  2 sd_mod,libata
unix                   26164  742 
thermal                13576  0 
processor              22708  1 thermal
fan                     4612  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

```

garbage:/data# route -n

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

```

garbage:/data# lspci

```

```

0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:03:01.0 Modem: Intel Corp.: Unknown device 1080 (rev 04)
0000:03:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 03)

```

```

garbage:/data# dmesg

```

```

T (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd34
ACPI: ASF! (v016 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd5c
ACPI: MCFG (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcdc3
ACPI: HPET (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fce01
ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:4 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 15:4 APIC version 20
WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x8086a201 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/sda5 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 510748k/522784k available (1436k kernel code, 11416k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3223ns tick, 3 64-bit timers
Using HPET for base-timer
Using HPET for gettimeofday
Detected 2793.360 MHz processor.
Using hpet for high-res timesource
Calibrating delay loop... 5537.79 BogoMIPS (lpj=2768896)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000
CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000
monitor/mwait feature present.
using mwait in idle threads.
CPU: Trace cache: 12K uops, L1 D cache: 16K
CPU: L2 cache: 1024K
CPU: After all inits, caps: bfebfbff 00100000 00000000 00000080 0000441d 00000000
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb2ca, last bus=3
PCI: Using MMCONFIG
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x800-0x85f could not be reserved
pnp: 00:00: ioport range 0xc00-0xc7f has been reserved
pnp: 00:00: ioport range 0x860-0x8ff has been reserved
pnp: 00:09: ioport range 0x100-0x1fe has been reserved
pnp: 00:09: ioport range 0x200-0x277 has been reserved
pnp: 00:09: ioport range 0x280-0x2e7 has been reserved
pnp: 00:09: ioport range 0x2e8-0x2ef has been reserved
pnp: 00:09: ioport range 0x2f0-0x2f7 has been reserved
pnp: 00:09: ioport range 0x2f8-0x2ff has been reserved
pnp: 00:09: ioport range 0x300-0x377 has been reserved
pnp: 00:09: ioport range 0x380-0x3bb has been reserved
Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Simple Boot Flag at 0x7a set to 0x1
audit: initializing netlink socket (disabled)
audit(1140648341.839:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
hpet_acpi_add: no address or irqs in _CRS
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ACPI: PCI interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
ttyS15 at I/O 0xcc08 (irq = 17) is a 16450
ttyS50 at I/O 0xcc10 (irq = 17) is a 8250
ttyS51 at I/O 0xcc18 (irq = 17) is a 16450
ttyS52 at I/O 0xcc20 (irq = 17) is a 8250
ttyS53 at I/O 0xcc28 (irq = 17) is a 8250
ttyS1 at I/O 0xcc60 (irq = 17) is a 8250
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 5
Cannot allocate resource for EISA slot 6
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
VBTN PCI0 PCI1 PCI2 PCI3 PCI4  KBD USB0 USB1 USB2 USB3 
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 20
ata2: SATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 20
ata1: dev 0 cfg 49:2f00 82:7c6b 83:7b09 84:4003 85:7c69 86:3a01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 156250000 sectors:
ata1: dev 0 configured for UDMA/133
scsi0 : ata_piix
ATA: abnormal status 0xFF on port 0xFE27
ata2: disabling port
scsi1 : ata_piix
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: Maxtor 6Y080M0    Rev: YAR5
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 p7 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda5, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
hdb: HL-DT-ST GCE-8483B, ATAPI CD/DVD-ROM drive
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 48X DVD-ROM drive, 254kB Cache
Uniform CD-ROM driver Revision: 3.20
hdb: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda7, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
input: PC Speaker
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 915G Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: AGP aperture is 256M @ 0x0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 21, io base 0xff80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 22, io base 0xff60
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xff40
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 23, io base 0xff20
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 21, pci mem 0xffa80800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usbcore: registered new driver hiddev
usbhid: probe of 2-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 2-1: USB disconnect, address 2
hw_random: RNG not detected
usb 2-1: new low speed USB device using uhci_hcd and address 3
ACPI: PCI interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:1e.2 to 64
input: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1d.1-1
usb 2-2: new full speed USB device using uhci_hcd and address 4
intel8x0_measure_ac97_clock: measured 49732 usecs
intel8x0: clocking to 48000
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
ICH6: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
ICH6: chipset revision 3
ICH6: not 100% native mode: will probe irqs later
ICH6: port 0x01f0 already claimed by ide0
ICH6: neither IDE port enabled (BIOS)
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 20
e100: eth0: e100_probe: addr 0xdfbff000, irq 20, MAC addr 00:13:20:36:28:C2
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present

```

```

garbage:/data# ifconfig

```

```

eth0      Link encap:Ethernet  HWaddr 00:13:20:36:28:C2  
          inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe36:28c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1386 (1.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107458 (104.9 KiB)  TX bytes:107458 (104.9 KiB)

```

```

garbage:/data# dhclient eth0

```

```

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:20:36:28:c2
Sending on   LPF/eth0/00:13:20:36:28:c2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Initially, I decided to use a static IP, as opposed to DHCP, because I've got 4 other boxes running, and it's a pain to have to keep updating hosts files, and configurations. The problem here really is that i'm not getting a reply from my router. Tcpdump is showing arp problems (who is ..., tell ...).

---

### Post by darth_vector on 2006-02-23
are you getting any entries in the arp table at all? maybe you have a loose/dodgy cable...

can you see any packet errors on your ethernet interface when you cat /proc/net/dev ??

---

### Post by Zimmer on 2006-02-23
Have you tried just issuing the command  dhclient  and seeing if the router will allocate you a working  connection ?

---

### Post by qqqqqqqqqqqqqqqqq on 2006-02-23
> 
Have you tried just issuing the command dhclient and seeing if the router will allocate you a working connection ?


Obviously I have, if you read what i posted. Darth_vector's advice was a bit more helpful.

---

### Post by Zimmer on 2006-02-23
Ok, maybe you have typed the routing addresses incorrectly, if you intended to use the recommended TCP/IP settings for Windows which should be:
IP address between 192.168.0.2 and 192.168.0.254
Subnet mask 255.255.255.0
Default Gateway 192.168.01

your route -n output shows
Destination          Gateway            Genmask            Flags Metric Ref    Use Iface
192.168.1.0          0.0.0.0             255.255.255.0      U     0      0        0 eth0
0.0.0.0                192.168.1.1          0.0.0.0            UG     0      0        0 eth0

My standard setup gives

Destination      Gateway          Genmask          Flags Metric Ref    Use Iface
192.168.0.0      0.0.0.0          255.255.255.0    U     0      0        0 eth0
0.0.0.0          192.168.0.1      0.0.0.0          UG    0      0        0 eth0

That could explain why you cannot find the network, if your GAteway is actually at 192.168.0.1....

Regards
Zimmer

---

### Post by darth_vector on 2006-02-23
ah, why do you have an IP address at all if you are using DHCP? check your /etc/network/interfaces file for a line like

iface eth0 inet dhcp

do you have that, or do you have

iface eth0 inet static

??

---

### Post by jamesr on 2006-02-24
> eth0      Link encap:Ethernet  HWaddr 00:13:20:36:28:C2  
          inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe36:28c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1386 (1.3 KiB

When you posted this output were you using DHCP or not?
the address certainly seems to be from the range associated with a router. 
What brand of Router?
It is therefore interesting that the  DHclient command gives no  replies. I normally use 

sudo dhclient 
not just 
dhclient 

Also the output shows a double sit0 response

Have you tried disabling ipv6 because the majority of home routers are not ipv6 capable 

When you go into the admin of the router ie from another PC is the dhcp set to work over the full range or not?.

Can you Ping the router?

---

### Post by qqqqqqqqqqqqqqqqq on 2006-02-25
No, my routers IP address is 192.168.1.1. And I ran dhclient as root, if you didn't notice the hash in the prompt in the snippets i posted. And when I try to ping my router, I get a Destination Unreachable error. Also, when I posted those examples, I was using a static IP. And in my /etc/network/interfaces file, I have it set up as iface eth0 inet static. It's a Linksys WRT54G wireless router. The range set up is 192.168.1.100-192.168.1.255

---

### Post by jamesr on 2006-02-25
Please rememember that we are not getting paid to help so snarkiness in replies does not help.

NO I DID NOT NOTICE THE HASH

> 
Also, when I posted those examples, I was using a static IP. And in my /etc/network/interfaces file, I have it set up as iface eth0 inet static.

 inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0

So that explains the address but does not explain the Bcast address. I thought that it should be in the router range.

My router is 192.168.123.254 and my Bcast is 192.168.123.255.

---

### Post by qqqqqqqqqqqqqqqqq on 2006-02-25
My broadcast address is 255.255.255.255.. I know all of the adresses I need to set, what I can't seem to figure out, is why my entire network is unreachable.

---

### Post by darth_vector on 2006-02-25
your broadcast address isn't in the routers subnet. if your router is at 192.168.1.1 and your subnet is 255.255.255.0 then your broadcast address will be (and can only be) 192.168.1.255.

needless to say, you cant have a static IP and be using DHCP at the same time. either get rid of the static IP and set everything up yourself, or get the settings by DHCP as previously explained.

also; change the DHCP range so it doesn't include 192.168.1.255. you cant assign the broadcast address to a host, so don't try.

---

### Post by qqqqqqqqqqqqqqqqq on 2006-02-25
Is it just me, or do people around here not listen? I said, that I had my desktop set to static, not dhcp. That snippet was posted to show you the output of dhclient. It's as if you think i'm an idiot. I probably have more experience dealing with unix-based systems than most of the people on this forum. As I stated earlier, I'm only having this problem with ubuntu. I'm not even going to seek assistance on this forum, as the only replies I get back, are restating the obvious, or are made before reading one of my previous posts. In short, no shit you can't use a static IP, and dhcp at the same time, and yes, my broadcast address is 255.255.255.255. As it  is on every other machine on my network.

---

### Post by mips on 2006-02-27
Is this a newer model Dell, if yes what is the model number ?

---

### Post by claes on 2006-02-27
[QUOTE=qqqqqqqqqqqqqqqqq]Is it just me, or do people around here not listen? I said, that I had my desktop set to static, not dhcp. That snippet was posted to show you the output of dhclient. It's as if you think i'm an idiot. I probably have more experience dealing with unix-based systems than most of the people on this forum. As I stated earlier, I'm only having this problem with ubuntu. I'm not even going to seek assistance on this forum, as the only replies I get back, are restating the obvious, or are made before reading one of my previous posts. In short, no shit you can't use a static IP, and dhcp at the same time, and yes, my broadcast address is 255.255.255.255. As it  is on every other machine on my network.[/QUOTE]

Are your other machines windows that will explain the all 1's broadcast. But that is not the way to do it in linux or cisco. There you use subnet broadcasts. 

Ofcourse in linux you can have a static ip and use a dhcp client. You can even have the dhcp server on the same machine so you get an dynamic ip from yourself. Can't see the real life useage of this. But it works.

If you have problem and someone comes with a suggestion to solve the problem, then try it. Don't just say that you have more unix experience than others on this forum. It's no pissing contest. We try to help you but if you don't try the suggestions we won't help you. Simple as that.

Claes

---

