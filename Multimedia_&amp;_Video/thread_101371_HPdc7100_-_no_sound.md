---
title: "HPdc7100 - no sound"
date: 2005-12-09
forum: Multimedia &amp; Video
---

### Post by Jimbob0i0 on 2005-12-09
Hi guys,

I have installed Breezy on this machine. Previously has WinXP on it.

I have no audio and the speaker in gnome has a little cross by it.

I have tried reading the forum and followed the intel-hda instructions in the hope that it might help (apt-get alsa-source... making it etc)

Here are relevant logs... I hope you can help me. I don't want to go back to MS.

```
dmesg output:
[4294669.166000] Freeing initrd memory: 5499k freed
[4294669.166000] ACPI: Looking for DSDT in initrd... not found!
[4294669.212000]  not found!
[4294669.218000] ENABLING IO-APIC IRQs
[4294669.219000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.329000] NET: Registered protocol family 16
[4294669.329000] ACPI: bus type pci registered
[4294669.330000] PCI: PCI BIOS revision 2.20 entry at 0xec4ff, last bus=64
[4294669.330000] PCI: Using MMCONFIG
[4294669.330000] mtrr: v2.0 (20020519)
[4294669.330000] ACPI: Subsystem revision 20050729
[4294669.332000] ACPI: Interpreter enabled
[4294669.332000] ACPI: Using IOAPIC for interrupt routing
[4294669.333000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.333000] PCI: Probing PCI hardware (bus 00)
[4294669.333000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.333000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.335000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.335000] Boot video device is 0000:01:00.0
[4294669.335000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.347000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.348000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[4294669.348000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX2._PRT]
[4294669.349000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[4294669.352000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[4294669.352000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[4294669.352000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[4294669.353000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[4294669.353000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 14 15)
[4294669.353000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 14 15)
[4294669.353000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[4294669.354000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[4294669.354000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.354000] pnp: PnP ACPI init
[4294669.357000] pnp: PnP ACPI: found 15 devices
[4294669.357000] PnPBIOS: Disabled by ACPI PNP
[4294669.357000] PCI: Using ACPI for IRQ routing
[4294669.357000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.829000] pnp: 00:0b: ioport range 0x400-0x41f has been reserved
[4294669.829000] pnp: 00:0b: ioport range 0x420-0x43f has been reserved
[4294669.829000] pnp: 00:0b: ioport range 0x440-0x45f has been reserved
[4294669.829000] pnp: 00:0b: ioport range 0x460-0x47f could not be reserved
[4294669.829000] pnp: 00:0b: ioport range 0x480-0x48f has been reserved
[4294669.829000] pnp: 00:0b: ioport range 0xf800-0xf81f could not be reserved
[4294669.829000] pnp: 00:0b: ioport range 0xf820-0xf83f could not be reserved
[4294669.829000] pnp: 00:0b: ioport range 0xf840-0xf85f has been reserved
[4294669.829000] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[4294669.830000] audit: initializing netlink socket (disabled)
[4294669.830000] audit: initialized
[4294669.830000] highmem bounce pool size: 64 pages
[4294669.830000] VFS: Disk quotas dquot_6.5.1
[4294669.830000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.830000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.830000] devfs: boot_options: 0x0
[4294669.830000] Initializing Cryptographic API
[4294669.830000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.830000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.830000] assign_interrupt_mode Found MSI capability
[4294669.830000] Allocate Port Service[pcie00]
[4294669.830000] Allocate Port Service[pcie03]
[4294669.830000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.830000] pcie_portdrv_probe->Dev[2660:8086] has invalid IRQ. Check vendor BIOS
[4294669.830000] assign_interrupt_mode Found MSI capability
[4294669.830000] Allocate Port Service[pcie00]
[4294669.830000] Allocate Port Service[pcie02]
[4294669.830000] Allocate Port Service[pcie03]
[4294669.830000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294669.830000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294669.830000] assign_interrupt_mode Found MSI capability
[4294669.830000] Allocate Port Service[pcie00]
[4294669.830000] Allocate Port Service[pcie02]
[4294669.830000] Allocate Port Service[pcie03]
[4294669.831000] isapnp: Scanning for PnP cards...
[4294670.182000] isapnp: No Plug & Play device found
[4294670.202000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[4294670.203000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.204000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.204000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.204000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.206000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.206000] io scheduler noop registered
[4294670.206000] io scheduler anticipatory registered
[4294670.206000] io scheduler deadline registered
[4294670.206000] io scheduler cfq registered
[4294670.206000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.206000] NET: Registered protocol family 2
[4294670.216000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294670.216000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294670.217000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.217000] TCP: Hash tables configured (established 262144 bind 65536)
[4294670.217000] NET: Registered protocol family 8
[4294670.217000] NET: Registered protocol family 20
[4294670.217000] ACPI wakeup devices: 
[4294670.217000] PCI0 PEG1 PCX1 PCX2 PCX4  HUB COM1 USB1 USB2 USB3 USB4 EUSB PBTN 
[4294670.217000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.217000] Freeing unused kernel memory: 168k freed
[4294670.230000] vga16fb: initializing
[4294670.230000] vga16fb: mapped to 0xc00a0000
[4294670.434000] Console: switching to colour frame buffer device 80x30
[4294670.434000] fb0: VGA16 VGA frame buffer device
[4294670.455000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.636000] Capability LSM initialized
[4294671.645000] NET: Registered protocol family 1
[4294671.658000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.658000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.658000] ACPI: bus type ide registered
[4294671.668000] SCSI subsystem initialized
[4294671.668000] libata version 1.11 loaded.
[4294671.669000] ata_piix version 1.03
[4294671.669000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294671.669000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.669000] ata1: SATA max UDMA/133 cmd 0x1810 ctl 0x182A bmdma 0x14F0 irq 19
[4294671.669000] ata2: SATA max UDMA/133 cmd 0x1818 ctl 0x182E bmdma 0x14F8 irq 19
[4294671.823000] ata1: dev 0 cfg 49:2f00 82:3069 83:7d01 84:4023 85:3069 86:3401 87:4023 88:203f
[4294671.823000] ata1: dev 0 ATA, max UDMA/100, 156301488 sectors: lba48
[4294671.823000] ata1: dev 0 configured for UDMA/100
[4294671.823000] scsi0 : ata_piix
[4294671.984000] ATA: abnormal status 0x7F on port 0x181F
[4294671.984000] ata2: disabling port
[4294671.984000] scsi1 : ata_piix
[4294671.984000]   Vendor: ATA       Model: ST380013AS        Rev: 3.43
[4294671.984000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294671.987000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294671.987000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 17 (level, low) -> IRQ 17
[4294671.987000] ICH6: chipset revision 3
[4294671.987000] ICH6: not 100% native mode: will probe irqs later
[4294671.987000]     ide0: BM-DMA at 0x14e0-0x14e7, BIOS settings: hda:DMA, hdb:pio
[4294671.987000]     ide1: BM-DMA at 0x14e8-0x14ef, BIOS settings: hdc:pio, hdd:pio
[4294671.987000] Probing IDE interface ide0...
[4294672.659000] hda: LITE-ON COMBO SOHC-4832K, ATAPI CD/DVD-ROM drive
[4294673.271000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.271000] Probing IDE interface ide1...
[4294673.790000] Probing IDE interface ide1...
[4294674.308000] Probing IDE interface ide2...
[4294674.820000] Probing IDE interface ide3...
[4294675.332000] Probing IDE interface ide4...
[4294675.844000] Probing IDE interface ide5...
[4294676.360000] hda: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294676.360000] Uniform CD-ROM driver Revision: 3.20
[4294676.367000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294676.367000] SCSI device sda: drive cache: write back
[4294676.367000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294676.367000] SCSI device sda: drive cache: write back
[4294676.367000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.402000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294676.613000] Attempting manual resume
[4294676.613000] swsusp: Suspend partition has wrong signature?
[4294676.644000] usbcore: registered new driver usbfs
[4294676.644000] usbcore: registered new driver hub
[4294676.645000] USB Universal Host Controller Interface driver v2.2
[4294676.645000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294676.645000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.645000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294676.707000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.707000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001440
[4294676.707000] hub 1-0:1.0: USB hub found
[4294676.707000] hub 1-0:1.0: 2 ports detected
[4294676.710000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 18 (level, low) -> IRQ 18
[4294676.710000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.710000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294676.772000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.772000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001460
[4294676.772000] hub 2-0:1.0: USB hub found
[4294676.772000] hub 2-0:1.0: 2 ports detected
[4294676.775000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294676.775000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.775000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294676.837000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.837000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001480
[4294676.837000] hub 3-0:1.0: USB hub found
[4294676.837000] hub 3-0:1.0: 2 ports detected
[4294676.840000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 22
[4294676.840000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294676.840000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294676.902000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294676.902000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x000014a0
[4294676.902000] hub 4-0:1.0: USB hub found
[4294676.902000] hub 4-0:1.0: 2 ports detected
[4294676.929000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[4294676.929000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.929000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294676.929000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.929000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294676.929000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xcfd00000
[4294676.933000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294676.933000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.933000] hub 5-0:1.0: USB hub found
[4294676.933000] hub 5-0:1.0: 8 ports detected
[4294676.996000] tg3.c:v3.31 (June 8, 2005)
[4294676.996000] ACPI: PCI Interrupt 0000:40:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294676.996000] PCI: Setting latency timer of device 0000:40:00.0 to 64
[4294677.019000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCIX:100MHz:32-bit) 10/100/1000BaseT Ethernet 00:13:21:67:00:34
[4294677.019000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[4294677.019000] eth0: dma_rwctrl[76180000]
[4294677.441000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4294679.039000] usbcore: registered new driver hiddev
[4294679.056000] input: USB HID v1.10 Mouse [KYE USB MOUSE] on usb-0000:00:1d.1-1
[4294679.056000] usbcore: registered new driver usbhid
[4294679.056000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.522000] ACPI: CPU0 (power states: C1[C1])
[4294679.522000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294679.766000] Attempting manual resume
[4294679.786000] swsusp: Suspend partition has wrong signature?
[4294679.814000] kjournald starting.  Commit interval 5 seconds
[4294679.814000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.977000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.062000] Adding 3036244k swap on /dev/sda5.  Priority:-1 extents:1
[4294684.409000] EXT3 FS on sda1, internal journal
[4294690.542000] parport: PnPBIOS parport detected.
[4294690.542000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294690.628000] lp0: using parport0 (interrupt-driven).
[4294690.651000] mice: PS/2 mouse device common for all mice
[4294690.918000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.928000] nvidia: module license 'NVIDIA' taints kernel.
[4294690.938000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294690.938000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294690.938000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294693.747000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294694.626000] cdrom: open failed.
[4294697.163000] agpgart: Detected an Intel 915G Chipset.
[4294697.191000] agpgart: AGP aperture is 256M @ 0x0
[4294697.254000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.258000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.258000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.329000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.329000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.398000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.398000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.661000] hw_random: RNG not detected
[4294697.759000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 21
[4294697.759000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294698.068000] intel8x0_measure_ac97_clock: measured 49043 usecs
[4294698.068000] intel8x0: clocking to 48000
[4294700.134000] Real Time Clock Driver v1.12
[4294700.172000] input: PC Speaker
[4294700.389000] FDC 0 is a post-1991 82077
[4294700.634000] ts: Compaq touchscreen protocol output
[4294702.164000] NET: Registered protocol family 17
[4294703.779000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4294703.779000] tg3: eth0: Flow control is off for TX and off for RX.
[4294738.791000] NET: Registered protocol family 10
[4294738.791000] Disabled Privacy Extensions on device c031eb40(lo)
[4294738.792000] IPv6 over IPv4 tunneling driver
```

```
lsmod output:
Module                  Size  Used by
vmnet                  37700  13 
vmmon                 111948  0 
rfcomm                 38460  0 
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_userspace       4316  0 
cpufreq_stats           5252  0 
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0 
cpufreq_ondemand        6044  0 
cpufreq_conservative     6948  0 
ipt_limit               2208  8 
iptable_mangle          2720  0 
ipt_LOG                 6976  8 
ipt_MASQUERADE          3296  0 
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0 
ipt_REJECT              5376  1 
ip_conntrack_irc       71696  0 
ip_conntrack_ftp       72688  0 
ipt_state               1792  6 
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1 
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  15748  0 
tc1100_wmi              6692  0 
sony_acpi               5324  0 
pcc_acpi               11104  0 
hotkey                  9284  0 
dev_acpi               11108  0 
i2c_acpi_ec             5472  0 
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0 
battery                 9348  0 
container               4384  0 
ac                      4708  0 
ipv6                  251232  15 
af_packet              21768  2 
tsdev                   7776  0 
floppy                 59124  0 
pcspkr                  3396  0 
rtc                    12344  0 
tpm_nsc                 6656  0 
tpm                     9888  1 tpm_nsc
snd_intel8x0           34144  0 
snd_ac97_codec         86268  1 snd_intel8x0
snd_pcm_oss            53984  0 
snd_mixer_oss          19552  1 snd_pcm_oss
snd_pcm                92232  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9988  2 snd_intel8x0,snd_pcm
pci_hotplug            27508  0 
intel_agp              23164  1 
dm_mod                 57692  1 
evdev                   9664  0 
ide_disk               18464  0 
nvidia               3710980  12 
agpgart                34792  2 intel_agp,nvidia
snd_seq_dummy           3748  0 
snd_seq_oss            36544  0 
snd_seq_midi            9280  0 
snd_rawmidi            25248  1 snd_seq_midi
snd_seq_midi_event      6944  2 snd_seq_oss,snd_seq_midi
snd_seq                53104  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25028  2 snd_pcm,snd_seq
snd_seq_device          8844  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57636  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
psmouse                30116  0 
mousedev               11616  1 
parport_pc             35236  1 
lp                     12292  0 
parport                35912  2 parport_pc,lp
md                     45584  0 
ext3                  136264  1 
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0 
processor              22812  1 thermal
fan                     4484  0 
usbhid                 35264  0 
tg3                    96772  0 
ehci_hcd               34248  0 
uhci_hcd               31184  0 
usbcore               118044  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19120  3 
ide_cd                 41572  0 
cdrom                  39616  1 ide_cd
ide_generic             1376  0 
ata_piix               10052  4 
libata                 53764  1 ata_piix
scsi_mod              135688  2 sd_mod,libata
piix                   10372  1 
ide_core              138772  4 ide_disk,ide_cd,ide_generic,piix
unix                   26896  732 
vesafb                  7992  0 
capability              4712  0 
commoncap               6816  1 capability
vga16fb                12584  1 
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72 
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
```

```
uname output:

uname -a
Linux it08-linux 2.6.12-10-686 #1 Fri Nov 18 12:09:04 UTC 2005 i686 GNU/Linux
```

---

### Post by quonsar on 2005-12-09
<i>speaker in gnome has a little cross by it.</i>

right click the speaker icon and unmute.

---

### Post by Jimbob0i0 on 2005-12-10
there is no unmute - only mute

if i try and open volume control I get...
"No volume control elements and/or devices found.

---

