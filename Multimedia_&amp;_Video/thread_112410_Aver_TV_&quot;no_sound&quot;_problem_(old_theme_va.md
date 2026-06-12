---
title: "Aver TV &quot;no sound&quot; problem (old theme variation)"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by Anilael on 2006-01-04
I am a newbie to linux. I have an "AverTV GO" card that works fine under "Windows XP" but displays a picture without any sound in Ubuntu. 
I can see a nice picture with xawtv and mplayer and a B&W picture in tvtime but all without any sound.
I've read some of the messages regarding this problem but didn't find their solutions  helpful. I plugged the TV card to the sound card line-in entry, and all the controls in the "volume control" are enabled and their slide bar is up.
The bttv galery shows this on my card:

> AverTV Go: bt878, ... No Radio, No S-Video

AverTV Go:
# chips: bt878a, xtal28
tuner: TAPC-G702P
pcb: M169-E
picture etc wanted.
bttv module with options "card=41 tuner=37"

bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 00:14.0, irq: 10, latency: 32, mmio: 0xe3001000
bttv0: subsystem: 1461:a903 (UNKNOWN)
bttv0: Avermedia eeprom[0x0491]: tuner=Unknown type radio:no remote control:yes

tuner: type set to 37 (LG PAL (newer TAPC series))

00:14.0 Class 0400: 109e:036e (rev 11)
        Subsystem: 1461:a903      
00:14.1 Class 0480: 109e:0878 (rev 11)
        Subsystem: 1461:a903      


The device is shown in the "Device Manager" as Saa7133. 
The "Advance" tab's "info.linux.driver" is saa7134.

I geditted the /etc/modules and added:
bttv card=41 tuner=37
bt878
tda9887
snd_bt87x

Here is my 'lsmod' output:
> Module                  Size  Used by
isofs                  32824  1
udf                    75524  0
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
tsdev                   7616  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
usblp                  11776  0
ohci1394               30644  0
saa7134                98772  0
v4l1_compat            12420  1 saa7134
ir_common               7428  1 saa7134
sk98lin               166872  1
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
snd_hda_intel          15872  2
snd_hda_codec          72064  1 snd_hda_intel
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
dm_mod                 50364  1
snd_bt87x              13768  0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
evdev                   9088  0
snd_pcm                78344  4 snd_hda_intel,snd_hda_codec,snd_bt87x,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  9 snd_hda_intel,snd_hda_codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  3 saa7134,snd
snd_page_alloc         10120  3 snd_hda_intel,snd_bt87x,snd_pcm
tda9887                13208  0
bt878                   9912  0
bttv                  141456  1 bt878
video_buf              19844  2 saa7134,bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  2 saa7134,bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
i2c_core               19728  6 i2c_acpi_ec,saa7134,tda9887,bttv,i2c_algo_bit,tveeprom
videodev                9344  2 saa7134,bttv
sr_mod                 15652  0
sbp2                   21128  0
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
processor              23100  1 thermal
fan                     4740  0
ide_disk               16128  1
usb_storage            64704  0
usbhid                 30688  0
siimage                11392  1
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  6 usblp,usb_storage,usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
ata_piix                9476  0
ahci                   11268  5
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sr_mod,sbp2,usb_storage,sd_mod,ahci,libata
piix                    9476  1
ide_core              125268  6 ide_disk,usb_storage,siimage,ide_cd,ide_generic,piix
unix                   24624  786
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



Following is my 'dmesg' output:
> 
0x30
[4294674.537000] fb0: VGA16 VGA frame buffer device
[4294674.650000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294675.673000] Capability LSM initialized
[4294675.682000] NET: Registered protocol family 1
[4294675.697000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294675.697000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294675.697000] ACPI: bus type ide registered
[4294675.705000] SCSI subsystem initialized
[4294675.706000] libata version 1.11 loaded.
[4294675.707000] ahci version 1.00
[4294675.707000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294680.885000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[4294681.052000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294681.052000] ahci(0000:00:1f.2) AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[4294681.052000] ahci(0000:00:1f.2) flags: 64bit ncq led slum part 
[4294681.052000] ata1: SATA max UDMA/133 cmd 0xF886AD00 ctl 0x0 bmdma 0x0 irq 19
[4294681.052000] ata2: SATA max UDMA/133 cmd 0xF886AD80 ctl 0x0 bmdma 0x0 irq 19

[4294681.052000] ata3: SATA max UDMA/133 cmd 0xF886AE00 ctl 0x0 bmdma 0x0 irq 19
[4294681.052000] ata4: SATA max UDMA/133 cmd 0xF886AE80 ctl 0x0 bmdma 0x0 irq 19
[4294681.253000] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7b09 84:4003 85:7c69 86:3a01 87:4003 88:007f
[4294681.253000] ata1: dev 0 ATA, max UDMA/133, 240121728 sectors:
[4294681.253000] ata1: dev 0 configured for UDMA/133
[4294681.253000] scsi0 : ahci
[4294681.455000] ata2: no device found (phy stat 00000000)
[4294681.455000] scsi1 : ahci
[4294681.656000] ata3: no device found (phy stat 00000000)
[4294681.656000] scsi2 : ahci
[4294681.936000] ata4: no device found (phy stat 00000000)
[4294681.936000] scsi3 : ahci
[4294681.936000]   Vendor: ATA       Model: Maxtor 6Y120M0    Rev: YAR5
[4294681.936000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294681.944000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294681.944000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294681.944000] ICH6: chipset revision 3
[4294681.944000] ICH6: not 100% native mode: will probe irqs later
[4294681.944000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294681.944000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[4294681.944000] Probing IDE interface ide0...
[4294682.745000] hda: Pioneer DVD-ROM ATAPIModel DVD-117 0107, ATAPI CD/DVD-ROM drive
[4294683.589000] hdb: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[4294683.640000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294683.640000] Probing IDE interface ide1...
[4294684.280000] Probing IDE interface ide1...
[4294684.798000] Probing IDE interface ide2...
[4294685.482000] Probing IDE interface ide3...
[4294686.088000] Probing IDE interface ide4...
[4294686.630000] Probing IDE interface ide5...
[4294686.742000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[4294687.146000] hda: ATAPI 126X DVD-ROM drive, 256kB Cache
[4294687.146000] Uniform CD-ROM driver Revision: 3.20
[4294687.151000] hdb: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[4294687.162000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[4294687.162000] SCSI device sda: drive cache: write back
[4294687.162000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[4294687.162000] SCSI device sda: drive cache: write back
[4294687.162000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
[4294687.206000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294687.558000] Attempting manual resume
[4294687.558000] swsusp: Suspend partition has wrong signature?
[4294687.602000] usbcore: registered new driver usbfs
[4294687.602000] usbcore: registered new driver hub
[4294687.603000] USB Universal Host Controller Interface driver v2.2
[4294687.603000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294687.603000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294687.603000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294687.665000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294687.665000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[4294687.665000] hub 1-0:1.0: USB hub found
[4294687.665000] hub 1-0:1.0: 2 ports detected
[4294687.668000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294687.668000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294687.668000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294687.730000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294687.730000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[4294687.730000] hub 2-0:1.0: USB hub found
[4294687.730000] hub 2-0:1.0: 2 ports detected
[4294687.733000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294687.733000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294687.733000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294687.795000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294687.795000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400

[4294687.795000] hub 3-0:1.0: USB hub found
[4294687.795000] hub 3-0:1.0: 2 ports detected
[4294687.798000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294687.798000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294687.798000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294687.834000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[4294687.860000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294687.860000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[4294687.860000] hub 4-0:1.0: USB hub found
[4294687.860000] hub 4-0:1.0: 2 ports detected
[4294687.885000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294687.885000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294687.885000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294687.885000] ehci_hcd 0000:00:1d.7: debug port 1
[4294687.885000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294687.885000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdffff800
[4294687.889000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294687.889000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294687.889000] hub 5-0:1.0: USB hub found
[4294687.889000] hub 5-0:1.0: 8 ports detected
[4294687.964000] SiI680: IDE controller at PCI slot 0000:06:01.0
[4294687.964000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294687.964000] SiI680: chipset revision 2
[4294687.964000] SiI680: BASE CLOCK == 133
[4294687.964000] SiI680: 100% native mode on irq 22
[4294687.964000]     ide2: MMIO-DMA , BIOS settings: hde:pio, hdf:pio
[4294687.964000]     ide3: MMIO-DMA , BIOS settings: hdg:pio, hdh:pio
[4294687.964000] Probing IDE interface ide2...
[4294688.228000] hde: IC35L040AVER07-0, ATA DISK drive
[4294688.269000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[4294688.840000] ide2 at 0xf8888480-0xf8888487,0xf888848a on irq 22
[4294688.840000] Probing IDE interface ide3...
[4294688.849000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[4294689.162000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4294689.308000] hdh: WDC WD2500PB-00FBA0, ATA DISK drive
[4294689.360000] ide3 at 0xf88884c0-0xf88884c7,0xf88884ca on irq 22
[4294691.389000] usbcore: registered new driver hiddev
[4294691.406000] input: USB HID v1.00 Mouse [Acrox USB Email Mouse Acrox USB Email Mouse] on usb-0000:00:1d.2-1
[4294691.406000] usbcore: registered new driver usbhid
[4294691.406000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294691.429000] Initializing USB Mass Storage driver...
[4294691.429000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294691.429000] usb-storage: device found at 2
[4294691.429000] usb-storage: waiting for device to settle before scanning
[4294691.429000] usbcore: registered new driver usb-storage
[4294691.429000] USB Mass Storage support registered.
[4294691.436000] hde: max request size: 64KiB
[4294691.442000] hde: 80418240 sectors (41174 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(100)
[4294691.442000] hde: cache flushes not supported
[4294691.442000]  /dev/ide/host2/bus0/target0/lun0: p1 p2 < >
[4294691.467000] hdh: max request size: 64KiB
[4294691.495000] hdh: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[4294691.497000] hdh: cache flushes supported
[4294691.497000]  /dev/ide/host2/bus1/target1/lun0:
[4294691.960000] ACPI: CPU0 (power states: C1[C1])
[4294691.960000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294692.064000] Attempting manual resume
[4294692.064000] swsusp: Suspend partition has wrong signature?
[4294692.073000] kjournald starting.  Commit interval 5 seconds
[4294692.073000] EXT3-fs: mounted filesystem with ordered data mode.
[4294693.300000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294695.893000] Adding 2409708k swap on /dev/sda5.  Priority:-1 extents:1
[4294696.042000] EXT3 FS on sda2, internal journal
[4294696.433000]   Vendor: GENERIC   Model: USB Storage-SMC   Rev: I19B
[4294696.433000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.438000] Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
[4294696.443000]   Vendor: GENERIC   Model: USB Storage-CFC   Rev: I19B
[4294696.443000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.448000] Attached scsi removable disk sdc at scsi4, channel 0, id 0, lun 1
[4294696.453000]   Vendor: GENERIC   Model: USB Storage-SDC   Rev: I19B
[4294696.453000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.455000] Attached scsi removable disk sdd at scsi4, channel 0, id 0, lun 2
[4294696.461000]   Vendor: GENERIC   Model: USB Storage-MSC   Rev: I19B
[4294696.461000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.464000] Attached scsi removable disk sde at scsi4, channel 0, id 0, lun 3
[4294696.465000] usb-storage: device scan complete
[4294701.101000] parport: PnPBIOS parport detected.
[4294701.101000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294701.195000] lp0: using parport0 (interrupt-driven).
[4294701.263000] mice: PS/2 mouse device common for all mice
[4294701.316000] ieee1394: Initialized config rom entry `ip1394'
[4294701.322000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294701.348000] Linux video capture interface: v1.00
[4294701.391000] bttv: driver version 0.9.15 loaded
[4294701.391000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294701.401000] bt878: AUDIO driver version 0.0.0 loaded
[4294704.482000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294705.043000] cdrom: open failed.
[4294706.449000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294706.458000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294706.525000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294706.525000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294707.113000] hw_random hardware driver 1.0.0 loaded
[4294707.392000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294707.392000] sk98lin: Network Device Driver v8.23.1.3
[4294707.392000] (C)Copyright 1999-2005 Marvell(R).
[4294707.392000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294707.392000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[4294707.449000] eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
[4294707.449000]       PrefPort:A  RlmtMode:Check Link State
[4294707.532000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294707.534000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294707.534000] saa7133[0]: found at 0000:06:00.0, rev: 208, irq: 21, latency: 32, mmio: 0xdfeff800
[4294707.534000] saa7133[0]: subsystem: 1461:f31f, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294707.534000] saa7133[0]: board init: gpio is 80688
[4294707.535000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294707.536000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294707.641000] tda9885/6/7: chip found @ 0x96
[4294707.665000] saa7133[0]: i2c eeprom 00: 61 14 1f f3 ff ff ff ff ff ff ff ff ff ff ff ff
[4294707.665000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294707.665000] saa7133[0]: i2c eeprom 20: ff d2 fe ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294707.665000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294707.668000] saa7133[0]: registered device video0 [v4l2]
[4294707.668000] saa7133[0]: registered device vbi0
[4294707.817000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294707.817000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294707.821000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294707.872000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[dfefe000-dfefe7ff]  Max Packet=[2048]
[4294709.143000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001111000024d418]
[4294709.545000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3304
[4294709.549000] usbcore: registered new driver usblp
[4294709.549000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294709.746000] Real Time Clock Driver v1.12
[4294709.812000] input: PC Speaker
[4294709.925000] Floppy drive(s): fd0 is 1.44M
[4294709.939000] FDC 0 is a post-1991 82077
[4294710.216000] ts: Compaq touchscreen protocol output
[4294710.897000] NET: Registered protocol family 17
[4294713.151000] eth0: network connection up using port A
[4294713.151000]     speed:           10
[4294713.151000]     autonegotiation: yes
[4294713.151000]     duplex mode:     half
[4294713.151000]     flowctrl:        none
[4294713.151000]     irq moderation:  disabled
[4294713.151000]     tcp offload:     enabled
[4294713.151000]     scatter-gather:  enabled
[4294713.151000]     tx-checksum:     enabled
[4294713.151000]     rx-checksum:     enabled
[4294713.151000]     rx-polling:      enabled
[4294720.510000] NET: Registered protocol family 10
[4294720.510000] Disabled Privacy Extensions on device c02eb280(lo)
[4294720.511000] IPv6 over IPv4 tunneling driver
[4294721.548000] ACPI: Power Button (FF) [PWRF]
[4294721.548000] ACPI: Power Button (CM) [PWRB]
[4294721.627000] ibm_acpi: ec object not found
[4294728.536000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294728.536000] apm: overridden by ACPI.
[4294729.855000] Bluetooth: Core ver 2.7
[4294729.855000] NET: Registered protocol family 31
[4294729.855000] Bluetooth: HCI device and connection manager initialized
[4294729.855000] Bluetooth: HCI socket layer initialized
[4294729.876000] Bluetooth: L2CAP ver 2.7
[4294729.876000] Bluetooth: L2CAP socket layer initialized
[4294729.898000] Bluetooth: RFCOMM ver 1.5
[4294729.898000] Bluetooth: RFCOMM socket layer initialized
[4294729.898000] Bluetooth: RFCOMM TTY layer initialized
[4294730.971000] eth0: no IPv6 routers present


And still there is no sound.
Can anybody help me??

---

### Post by Anilael on 2006-01-04
> 
I am a newbie to linux. I have an "AverTV GO" card that works fine under "Windows XP" but displays a picture without any sound in Ubuntu.
I can see a nice picture with xawtv and mplayer and a B&W picture in tvtime but all without any sound.

Forgot to mention that the TV card is connected to my VCR via an S-Video cable and an audio cable (RCA to Phono).

anybody can help?

---

