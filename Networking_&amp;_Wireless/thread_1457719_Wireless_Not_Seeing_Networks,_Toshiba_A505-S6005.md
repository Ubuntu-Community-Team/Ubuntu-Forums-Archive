---
title: "Wireless Not Seeing Networks, Toshiba A505-S6005"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by gloria0227 on 2010-04-19
Hello,

My wireless is not working in Ubuntu 9.10.  In the connection area wireless is not an option, I cant even see wireless networks.  I read some posts at [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126) but the solutions do not work for me.

Below is some more information

lspci:
```
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
03:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
3f:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
3f:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

```ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:45:58:f1  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe45:58f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2703461 (2.7 MB)  TX bytes:872256 (872.2 KB)
          Interrupt:34 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.


```lsmod:

```
Module                  Size  Used by
snd_hda_codec_intelhdmi    14880  1 
binfmt_misc            10220  1 
snd_hda_codec_realtek   277860  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              21200  1 iptable_filter
snd_timer              26992  2 snd_pcm,snd_seq
x_tables               25832  1 ip_tables
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0 
snd                    77096  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     11908  0 
serio_raw               6596  0 
parport                40528  2 ppdev,lp
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
ndiswrapper           245248  0 
led_class               5256  1 sdhci
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
i915                  252424  1 
drm                   194400  1 i915
i2c_algo_bit            7076  1 i915
video                  23612  1 i915
output                  3680  1 video
r8169                  38884  0 
mii                     6368  1 r8169
intel_agp              33040  2 i915

```dmesg:

```

[   18.727389] ACPI: SSDT 00000000bb691c18 003A6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[   18.728053] ACPI: SSDT 00000000bb68fa18 0045C (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[   18.728721] Monitor-Mwait will be used to enter C-1 state
[   18.728744] Monitor-Mwait will be used to enter C-2 state
[   18.728766] Monitor-Mwait will be used to enter C-3 state
[   18.728787] ACPI: CPU0 (power states: C1[C1] C3[C3])
[   18.728803] processor LNXCPU:00: registered as cooling_device1
[   18.728806] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.729504] ACPI: SSDT 00000000bb690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[   18.730140] ACPI: SSDT 00000000bb68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[   18.730959] ACPI: CPU1 (power states: C1[C1] C3[C3])
[   18.730974] processor LNXCPU:01: registered as cooling_device2
[   18.730977] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.732098] ACPI: CPU2 (power states: C1[C1] C3[C3])
[   18.732115] processor LNXCPU:02: registered as cooling_device3
[   18.732118] ACPI: Processor [CPU2] (supports 8 throttling states)
[   18.733226] ACPI: CPU3 (power states: C1[C1] C3[C3])
[   18.733242] processor LNXCPU:03: registered as cooling_device4
[   18.733245] ACPI: Processor [CPU3] (supports 8 throttling states)
[   18.733429] ACPI Error: Found unknown opcode 4 at AML address ffffc90000610d0f offset 0, ignoring 20090521 psloop-137
[   18.733523] ACPI Error (psargs-0359): [WB0p] Namespace lookup failure, AE_NOT_FOUND
[   18.733528] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HSB2._STA] (Node ffff880133838f00), AE_NOT_FOUND
[   18.733853] ACPI Error (psargs-0359): [G03S] Namespace lookup failure, AE_NOT_FOUND
[   18.733858] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.VALZ._STA] (Node ffff880133839460), AE_NOT_FOUND
[   18.733937] ACPI Error: Found unknown opcode 4 at AML address ffffc90000613459 offset 0, ignoring 20090521 psloop-137
[   18.733942] ACPI Error: Found unknown opcode D6 at AML address ffffc9000061345a offset 1, ignoring 20090521 psloop-137
[   18.733946] ACPI Error: Found unknown opcode 4 at AML address ffffc9000061345b offset 2, ignoring 20090521 psloop-137
[   18.733961] ACPI Error (psargs-0359): [G&#65533;] Namespace lookup failure, AE_NOT_FOUND
[   18.733965] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.FWEX._STA] (Node ffff8801338394e0), AE_NOT_FOUND
[   18.737269] ACPI Exception: AE_OK, No or invalid critical threshold 20090521 thermal-384
[   18.738082] Linux agpgart interface v0.103
[   18.738090] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[   18.739009] brd: module loaded
[   18.739345] loop: module loaded
[   18.739399] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[   18.739474] ahci 0000:00:1f.2: version 3.0
[   18.739488] ahci 0000:00:1f.2: can't derive routing for PCI INT B
[   18.739491] ahci 0000:00:1f.2: PCI INT B: no GSI - using IRQ 11
[   18.739538]   alloc irq_desc for 33 on node 0
[   18.739540]   alloc kstat_irqs on node 0
[   18.739549] ahci 0000:00:1f.2: irq 33 for MSI/MSI-X
[   18.739586] ahci: SSS flag set, parallel bus scan disabled
[   18.739636] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   18.739639] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems 
[   18.739644] ahci 0000:00:1f.2: setting latency timer to 64
[   18.802275] scsi0 : ahci
[   18.802360] scsi1 : ahci
[   18.802403] scsi2 : ahci
[   18.802442] scsi3 : ahci
[   18.802483] scsi4 : ahci
[   18.802526] scsi5 : ahci
[   18.803066] ata1: SATA max UDMA/133 abar m2048@0xd8405000 port 0xd8405100 irq 33
[   18.803070] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 33
[   18.803072] ata3: DUMMY
[   18.803073] ata4: DUMMY
[   18.803076] ata5: SATA max UDMA/133 abar m2048@0xd8405000 port 0xd8405300 irq 33
[   18.803079] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 33
[   18.803739] Fixed MDIO Bus: probed
[   18.803768] PPP generic driver version 2.4.2
[   18.803837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   18.803870] ehci_hcd 0000:00:1a.0: can't derive routing for PCI INT A
[   18.803873] ehci_hcd 0000:00:1a.0: PCI INT A: no GSI - using IRQ 5
[   18.803894] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[   18.803899] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[   18.803933] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   18.807844] ehci_hcd 0000:00:1a.0: debug port 2
[   18.807850] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[   18.807864] ehci_hcd 0000:00:1a.0: irq 5, io mem 0xd8405c00
[   18.832138] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[   18.832241] usb usb1: configuration #1 chosen from 1 choice
[   18.832265] hub 1-0:1.0: USB hub found
[   18.832271] hub 1-0:1.0: 3 ports detected
[   18.832338] ehci_hcd 0000:00:1d.0: can't derive routing for PCI INT A
[   18.832340] ehci_hcd 0000:00:1d.0: PCI INT A: no GSI - using IRQ 10
[   18.832355] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[   18.832358] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[   18.832384] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   18.836288] ehci_hcd 0000:00:1d.0: debug port 2
[   18.836295] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[   18.836308] ehci_hcd 0000:00:1d.0: irq 10, io mem 0xd8405800
[   18.862073] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[   18.862172] usb usb2: configuration #1 chosen from 1 choice
[   18.862191] hub 2-0:1.0: USB hub found
[   18.862196] hub 2-0:1.0: 3 ports detected
[   18.862242] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.862254] uhci_hcd: USB Universal Host Controller Interface driver
[   18.862335] PNP: No PS/2 controller found. Probing ports directly.
[   18.892438] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.892444] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.892493] mice: PS/2 mouse device common for all mice
[   18.892577] rtc_cmos 00:05: RTC can wake from S4
[   18.892603] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   18.892639] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[   18.892741] device-mapper: uevent: version 1.0.3
[   18.892809] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[   18.892882] device-mapper: multipath: version 1.1.0 loaded
[   18.892886] device-mapper: multipath round-robin: version 1.0.0 loaded
[   18.893131] cpuidle: using governor ladder
[   18.893627] cpuidle: using governor menu
[   18.894002] TCP cubic registered
[   18.894111] NET: Registered protocol family 10
[   18.894515] lo: Disabled Privacy Extensions
[   18.894771] NET: Registered protocol family 17
[   18.894788] Bluetooth: L2CAP ver 2.13
[   18.894789] Bluetooth: L2CAP socket layer initialized
[   18.894791] Bluetooth: SCO (Voice Link) ver 0.6
[   18.894793] Bluetooth: SCO socket layer initialized
[   18.894817] Bluetooth: RFCOMM TTY layer initialized
[   18.894820] Bluetooth: RFCOMM socket layer initialized
[   18.894821] Bluetooth: RFCOMM ver 1.11
[   18.896668] PM: Resume from disk failed.
[   18.896678] registered taskstats version 1
[   18.896810]   Magic number: 6:844:150
[   18.896824] bdi 1:2: hash matches
[   18.896864] acpi INT0800:00: hash matches
[   18.896903] rtc_cmos 00:05: setting system clock to 2010-04-18 23:06:29 UTC (1271631989)
[   18.896907] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.896908] EDD information not available.
[   18.924591] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   19.143438] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   19.153377] ata1: SATA link down (SStatus 0 SControl 300)
[   19.919917] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.920723] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 succeeded
[   19.920761] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   19.920769] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   19.920800] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 succeeded
[   20.286629] ata2.00: ATA-8: TOSHIBA MK5055GSX, FG001M, max UDMA/100
[   20.286634] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   20.287681] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 succeeded
[   20.287722] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   20.287726] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.287775] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 succeeded
[   20.288439] ata2.00: configured for UDMA/100
[   20.299249] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK5055GS FG00 PQ: 0 ANSI: 5
[   20.299352] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   20.299410] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   20.299473] sd 1:0:0:0: [sda] Write Protect is off
[   20.299476] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.299501] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.299607]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[   20.364685] sd 1:0:0:0: [sda] Attached SCSI disk
[   20.648425] ata5: SATA link down (SStatus 0 SControl 300)
[   21.418774] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.423926] ata6.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.424429] ata6.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.424437] ata6.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   21.424932] ata6.00: ACPI cmd ef/10:05:00:00:00:b0 succeeded
[   21.429774] ata6.00: ATAPI: HL-DT-ST DVDRAM GT20F, ET11, max UDMA/133, ATAPI AN
[   21.435099] ata6.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.435602] ata6.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.435609] ata6.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   21.436126] ata6.00: configured for UDMA/133
[   21.459944] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20F     ET11 PQ: 0 ANSI: 5
[   21.471100] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.471106] Uniform CD-ROM driver Revision: 3.20
[   21.471204] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   21.471235] sr 5:0:0:0: Attached scsi generic sg1 type 5
[   21.471256] Freeing unused kernel memory: 664k freed
[   21.471385] Write protecting the kernel read-only data: 7596k
[   21.559762] agpgart-intel 0000:00:00.0: Intel IGDNG/M Chipset
[   21.560482] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   21.569007] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   21.580717] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   21.580755] pcieport-driver 0000:00:1c.0: can't derive routing for PCI INT A
[   21.580758] r8169 0000:01:00.0: PCI INT A: no GSI - using IRQ 5
[   21.580882] r8169 0000:01:00.0: setting latency timer to 64
[   21.581054]   alloc irq_desc for 34 on node 0
[   21.581057]   alloc kstat_irqs on node 0
[   21.581110] r8169 0000:01:00.0: irq 34 for MSI/MSI-X
[   21.581877] eth0: RTL8102e at 0xffffc9000067c000, 00:26:6c:45:58:f1, XID 24c00000 IRQ 34
[   21.601967] [drm] Initialized drm 1.1.0 20060810
[   21.611383] i915 0000:00:02.0: can't derive routing for PCI INT A
[   21.611386] i915 0000:00:02.0: PCI INT A: no GSI - using IRQ 5
[   21.611391] i915 0000:00:02.0: setting latency timer to 64
[   21.624075] mtrr: no more MTRRs available
[   21.624079] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   21.624372]   alloc irq_desc for 35 on node 0
[   21.624378]   alloc kstat_irqs on node 0
[   21.624392] i915 0000:00:02.0: irq 35 for MSI/MSI-X
[   21.731834] [drm] i2c_init DPDDC-C
[   21.856842] i2c-adapter i2c-2: unable to read EDID block.
[   21.856845] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.868337] [drm] fb0: inteldrmfb frame buffer device
[   21.868432] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.149426] [drm] LVDS-8: set mode 1366x768 12
[   22.585999] Console: switching to colour frame buffer device 170x48
[   22.943940] PM: Starting manual resume from disk
[   22.943944] PM: Resume from partition 8:5
[   22.943946] PM: Checking hibernation image.
[   22.944068] PM: Resume from disk failed.
[   22.974397] EXT4-fs (sda6): barriers enabled
[   22.998521] kjournald2 starting: pid 403, dev sda6:8, commit interval 5 seconds
[   22.998641] EXT4-fs (sda6): delayed allocation enabled
[   22.998645] EXT4-fs: file extents enabled
[   23.024382] EXT4-fs: mballoc enabled
[   23.024398] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   23.617040] type=1505 audit(1271631994.226:2): operation="profile_load" pid=430 name=/usr/share/gdm/guest-session/Xsession
[   23.626498] type=1505 audit(1271631994.236:3): operation="profile_load" pid=431 name=/sbin/dhclient3
[   23.627002] type=1505 audit(1271631994.236:4): operation="profile_load" pid=431 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   23.627278] type=1505 audit(1271631994.236:5): operation="profile_load" pid=431 name=/usr/lib/connman/scripts/dhclient-script
[   23.674978] type=1505 audit(1271631994.286:6): operation="profile_load" pid=432 name=/usr/bin/evince
[   23.683217] type=1505 audit(1271631994.286:7): operation="profile_load" pid=432 name=/usr/bin/evince-previewer
[   23.688093] type=1505 audit(1271631994.296:8): operation="profile_load" pid=432 name=/usr/bin/evince-thumbnailer
[   23.708867] type=1505 audit(1271631994.316:9): operation="profile_load" pid=434 name=/usr/lib/cups/backend/cups-pdf
[   23.709472] type=1505 audit(1271631994.316:10): operation="profile_load" pid=434 name=/usr/sbin/cupsd
[   23.730264] type=1505 audit(1271631994.336:11): operation="profile_load" pid=435 name=/usr/sbin/mysqld-akonadi
[   23.754748] type=1505 audit(1271631994.366:12): operation="profile_load" pid=436 name=/usr/sbin/tcpdump
[   24.133218] ehci_hcd 0000:00:1a.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   30.877508] udev: starting version 147
[   30.900226] Adding 4881400k swap on /dev/sda5.  Priority:-1 extents:1 across:4881400k 
[   30.909740] Disabling lock debugging due to kernel taint
[   30.949456] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   30.952920] sdhci: Secure Digital Host Controller Interface driver
[   30.952924] sdhci: Copyright(c) Pierre Ossman
[   30.962678] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 1)
[   30.962704] pcieport-driver 0000:00:1c.3: can't derive routing for PCI INT D
[   30.962707] sdhci-pci 0000:03:00.0: PCI INT D: no GSI - using IRQ 11
[   30.962776] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   30.962790] sdhci-pci 0000:03:00.0: setting latency timer to 64
[   30.963854] Registered led device: mmc0::
[   30.963900] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[   30.987522] lp: driver loaded but no devices found
[   30.991483] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.050539] HDA Intel 0000:00:1b.0: can't derive routing for PCI INT A
[   31.050543] HDA Intel 0000:00:1b.0: PCI INT A: no GSI - using IRQ 11
[   31.050666] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   31.398975] EXT4-fs (sda6): internal journal on sda6:8
[   31.569138] r8169: eth0: link up
[   31.569156] r8169: eth0: link up
[   31.646788] type=1505 audit(1271650002.266:13): operation="profile_replace" pid=931 name=/usr/share/gdm/guest-session/Xsession
[   31.648166] type=1505 audit(1271650002.276:14): operation="profile_replace" pid=932 name=/sbin/dhclient3
[   31.648681] type=1505 audit(1271650002.276:15): operation="profile_replace" pid=932 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   31.648963] type=1505 audit(1271650002.276:16): operation="profile_replace" pid=932 name=/usr/lib/connman/scripts/dhclient-script
[   31.651379] type=1505 audit(1271650002.276:17): operation="profile_replace" pid=933 name=/usr/bin/evince
[   31.659987] type=1505 audit(1271650002.286:18): operation="profile_replace" pid=933 name=/usr/bin/evince-previewer
[   31.664917] type=1505 audit(1271650002.286:19): operation="profile_replace" pid=933 name=/usr/bin/evince-thumbnailer
[   31.672028] type=1505 audit(1271650002.296:20): operation="profile_replace" pid=935 name=/usr/lib/cups/backend/cups-pdf
[   31.672622] type=1505 audit(1271650002.296:21): operation="profile_replace" pid=935 name=/usr/sbin/cupsd
[   31.674353] type=1505 audit(1271650002.296:22): operation="profile_replace" pid=936 name=/usr/sbin/mysqld-akonadi
[   31.902758] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1e0b1, caps: 0xd04731/0xa40000
[   31.972092] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   32.074053] ppdev: user-space parallel port driver
[   32.136645] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   32.222129] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   32.222927] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   32.528380] CPU0 attaching NULL sched-domain.
[   32.528385] CPU1 attaching NULL sched-domain.
[   32.528388] CPU2 attaching NULL sched-domain.
[   32.528390] CPU3 attaching NULL sched-domain.
[   32.538181] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[   32.538188] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[   32.538198] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIOpenBlock'
[   32.538203] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIQueryAllData'
[   32.538211] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   32.538217] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   32.538222] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   32.538227] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   32.538232] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   32.538240] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   32.538245] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   32.538250] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   32.538257] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   32.538280] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   32.538285] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   32.538298] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   32.538303] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   32.538316] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   32.538321] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   32.538326] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   32.538331] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   32.538340] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   32.538345] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   32.538350] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   32.538358] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   32.538363] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   32.538369] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   32.538374] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   32.538385] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   32.538391] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   32.538396] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   32.538401] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   32.538406] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   32.538412] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   32.538414] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192se'
[   32.538784] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192se; check system log for messages from 'loadndisdriver'
[   32.563959] CPU0 attaching sched-domain:
[   32.563963]  domain 0: span 0-1 level SIBLING
[   32.563965]   groups: 0 1
[   32.563968]   domain 1: span 0-3 level MC
[   32.563970]    groups: 0-1 2-3
[   32.563974]    domain 2: span 0-3 level CPU
[   32.563975]     groups: 0-3 (__cpu_power = 2048)
[   32.563980] CPU1 attaching sched-domain:
[   32.563982]  domain 0: span 0-1 level SIBLING
[   32.563984]   groups: 1 0
[   32.563986]   domain 1: span 0-3 level MC
[   32.563988]    groups: 0-1 2-3
[   32.563991]    domain 2: span 0-3 level CPU
[   32.563993]     groups: 0-3 (__cpu_power = 2048)
[   32.563996] CPU2 attaching sched-domain:
[   32.563998]  domain 0: span 2-3 level SIBLING
[   32.563999]   groups: 2 3
[   32.564002]   domain 1: span 0-3 level MC
[   32.564004]    groups: 2-3 0-1
[   32.564007]    domain 2: span 0-3 level CPU
[   32.564009]     groups: 0-3 (__cpu_power = 2048)
[   32.564012] CPU3 attaching sched-domain:
[   32.564014]  domain 0: span 2-3 level SIBLING
[   32.564016]   groups: 3 2
[   32.564018]   domain 1: span 0-3 level MC
[   32.564020]    groups: 2-3 0-1
[   32.564023]    domain 2: span 0-3 level CPU
[   32.564025]     groups: 0-3 (__cpu_power = 2048)
[   32.564541] CPU0 attaching NULL sched-domain.
[   32.564544] CPU1 attaching NULL sched-domain.
[   32.564547] CPU2 attaching NULL sched-domain.
[   32.564548] CPU3 attaching NULL sched-domain.
[   32.603914] CPU0 attaching sched-domain:
[   32.603917]  domain 0: span 0-1 level SIBLING
[   32.603919]   groups: 0 1
[   32.603922]   domain 1: span 0-3 level MC
[   32.603924]    groups: 0-1 (__cpu_power = 2048) 2-3 (__cpu_power = 2048)
[   32.603929] CPU1 attaching sched-domain:
[   32.603931]  domain 0: span 0-1 level SIBLING
[   32.603933]   groups: 1 0
[   32.603936]   domain 1: span 0-3 level MC
[   32.603937]    groups: 0-1 (__cpu_power = 2048) 2-3 (__cpu_power = 2048)
[   32.603942] CPU2 attaching sched-domain:
[   32.603944]  domain 0: span 2-3 level SIBLING
[   32.603945]   groups: 2 3
[   32.603948]   domain 1: span 0-3 level MC
[   32.603950]    groups: 2-3 (__cpu_power = 2048) 0-1 (__cpu_power = 2048)
[   32.603955] CPU3 attaching sched-domain:
[   32.603956]  domain 0: span 2-3 level SIBLING
[   32.603958]   groups: 3 2
[   32.603961]   domain 1: span 0-3 level MC
[   32.603962]    groups: 2-3 (__cpu_power = 2048) 0-1 (__cpu_power = 2048)
[   34.679625] usb 1-1: device not accepting address 2, error -110
[   34.799326] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   42.313937] eth0: no IPv6 routers present
[   50.333453] usb 1-1: device not accepting address 3, error -110
[   50.453141] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   60.864596] usb 1-1: device not accepting address 4, error -110
[   60.986150] usb 1-1: new high speed USB device using ehci_hcd and address 5
[   71.397712] usb 1-1: device not accepting address 5, error -110
[   71.397738] hub 1-0:1.0: unable to enumerate USB device on port 1
[   71.539259] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   76.524601] ehci_hcd 0000:00:1d.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   87.067641] usb 2-1: device not accepting address 2, error -110
[   87.187359] usb 2-1: new high speed USB device using ehci_hcd and address 3
[  102.717637] usb 2-1: device not accepting address 3, error -110
[  102.839184] usb 2-1: new high speed USB device using ehci_hcd and address 4
[  113.252537] usb 2-1: device not accepting address 4, error -110
[  113.370427] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  123.785618] usb 2-1: device not accepting address 5, error -110
[  123.785638] hub 2-0:1.0: unable to enumerate USB device on port 1
[  123.805659] usbcore: registered new interface driver ndiswrapper
[  124.235828] CPU0 attaching NULL sched-domain.
[  124.235838] CPU1 attaching NULL sched-domain.
[  124.235843] CPU2 attaching NULL sched-domain.
[  124.235847] CPU3 attaching NULL sched-domain.
[  124.274478] CPU0 attaching sched-domain:
[  124.274483]  domain 0: span 0-1 level SIBLING
[  124.274486]   groups: 0 1
[  124.274491]   domain 1: span 0-3 level MC
[  124.274494]    groups: 0-1 (__cpu_power = 2048) 2-3 (__cpu_power = 2048)
[  124.274502] CPU1 attaching sched-domain:
[  124.274504]  domain 0: span 0-1 level SIBLING
[  124.274507]   groups: 1 0
[  124.274511]   domain 1: span 0-3 level MC
[  124.274514]    groups: 0-1 (__cpu_power = 2048) 2-3 (__cpu_power = 2048)
[  124.274520] CPU2 attaching sched-domain:
[  124.274523]  domain 0: span 2-3 level SIBLING
[  124.274525]   groups: 2 3
[  124.274529]   domain 1: span 0-3 level MC
[  124.274532]    groups: 2-3 (__cpu_power = 2048) 0-1 (__cpu_power = 2048)
[  124.274538] CPU3 attaching sched-domain:
[  124.274541]  domain 0: span 2-3 level SIBLING
[  124.274543]   groups: 3 2
[  124.274547]   domain 1: span 0-3 level MC
[  124.274550]    groups: 2-3 (__cpu_power = 2048) 0-1 (__cpu_power = 2048)
[  124.275058] CPU0 attaching NULL sched-domain.
[  124.275062] CPU1 attaching NULL sched-domain.
[  124.275064] CPU2 attaching NULL sched-domain.
[  124.275067] CPU3 attaching NULL sched-domain.
[  124.314340] CPU0 attaching sched-domain:
[  124.314345]  domain 0: span 0-1 level SIBLING
[  124.314349]   groups: 0 1
[  124.314353]   domain 1: span 0-3 level MC
[  124.314356]    groups: 0-1 2-3
[  124.314363] CPU1 attaching sched-domain:
[  124.314365]  domain 0: span 0-1 level SIBLING
[  124.314368]   groups: 1 0
[  124.314372]   domain 1: span 0-3 level MC
[  124.314374]    groups: 0-1 2-3
[  124.314379] CPU2 attaching sched-domain:
[  124.314381]  domain 0: span 2-3 level SIBLING
[  124.314384]   groups: 2 3
[  124.314388]   domain 1: span 0-3 level MC
[  124.314390]    groups: 2-3 0-1
[  124.314395] CPU3 attaching sched-domain:
[  124.314397]  domain 0: span 2-3 level SIBLING
[  124.314400]   groups: 3 2
[  124.314404]   domain 1: span 0-3 level MC
[  124.314407]    groups: 2-3 0-1




```sudo lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:45:58:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d6400000-d6403fff

```iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```lsb_release -d:

```
Description:    Ubuntu 9.10

```uname -mr:

```
2.6.31-20-generic x86_64
```sudo /etc/init.d/networking restart:

```
 * Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.
 [ OK ]

```


Thank you very much for your help!!!

---

### Post by hostilejosh on 2010-04-19
i am having same problem but on a dell inspiron 1545, internet works fine in windows vista, and worked in 9.04, but now nothing, kaput, rendering ubuntu useless.

---

### Post by ndstate on 2010-04-21
Maybe take a look at [http://ubuntuforums.org/showpost.php?p=9009017&postcount=26](http://ubuntuforums.org/showpost.php?p=9009017&postcount=26) and related posts.  That has been said to work. :)  Good luck.

---

### Post by gloria0227 on 2010-05-21
I followed the steps at [http://ubuntuforums.org/showpost.php?p=9009017&postcount=26](http://ubuntuforums.org/showpost.php?p=9009017&postcount=26) and it works!

---

