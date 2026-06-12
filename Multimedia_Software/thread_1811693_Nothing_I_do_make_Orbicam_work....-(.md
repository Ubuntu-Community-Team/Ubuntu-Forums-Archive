---
title: "Nothing I do make Orbicam work....:-("
date: 2011-07-25
forum: Multimedia Software
---

### Post by KaYnemO on 2011-07-25
Hi all,

before upgrade to 10.10 the webcam worked fine. After  - nothing I read works - no webcam in anything (cheese, skype, xawtv etc.)

Please help !!!

lsusb returns:


```
Bus 001 Device 003: ID 046d:0896 Logitech, Inc. OrbiCam
```

gstreamer-properties returns:

```
Video for Linux (v4l): Could not open device "/dev/video0" for reading and writing.
```

lsmod returns:

```
Module                  Size  Used by
videodev               34361  0 
v4l1_compat            13251  1 videodev
hidp                   11166  1 
hid                    67032  1 hidp
binfmt_misc             6587  1 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
rfcomm                 32679  8 
sco                     7562  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9199  2 
l2cap                  30618  21 hidp,rfcomm,bnep
parport_pc             25962  0 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_realtek   203168  1 
pcmcia                 33024  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674135  3 
iwl3945                70360  0 
ttm                    49943  1 radeon
iwlcore               110869  1 iwl3945
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
drm_kms_helper         29297  1 radeon
tifm_7xx1               3690  0 
mac80211              209734  2 iwl3945,iwlcore
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acer_wmi               13861  0 
drm                   162471  6 radeon,ttm,drm_kms_helper
tifm_core               6045  1 tifm_7xx1
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              130639  3 iwl3945,iwlcore,mac80211
btusb                  10925  4 
bluetooth              50422  10 hidp,rfcomm,sco,bnep,l2cap,btusb
led_class               2864  1 acer_wmi
i2c_algo_bit            5028  1 radeon
intel_agp              24177  0 
psmouse                63245  0 
serio_raw               3978  0 
compat_firmware_class     7043  1 iwl3945
agpgart                31724  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
irda                  186556  0 
crc_ccitt               1339  1 irda
lp                      7028  0 
parport                32635  3 parport_pc,ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
tg3                   109292  0 



```

Earlier, to avoid a loop at the boot time I had to blacklist gspca_vc032x to avoid so...

NOTHING I do works... no webcam, no skype (and I need it badly) !! Please help !

Regards...

---

### Post by no2498 on 2011-07-26
in a terminal type  dmesg click enter
after it stops 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so xawtv click enter

see if that helps

---

### Post by KaYnemO on 2011-07-28
nope....

dmesg: 

```
[    1.002582] pci 0000:00:1c.3: setting latency timer to 64
[    1.002591] pci 0000:00:1e.0: setting latency timer to 64
[    1.002604]   alloc irq_desc for 20 on node -1
[    1.002606]   alloc kstat_irqs on node -1
[    1.002610] pci 0000:0a:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.002619] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.002623] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.002627] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    1.002630] pci_bus 0000:01: resource 1 mem: [0xc8100000-0xc81fffff]
[    1.002634] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    1.002637] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    1.002641] pci_bus 0000:02: resource 1 mem: [0x44000000-0x441fffff]
[    1.002644] pci_bus 0000:02: resource 2 pref mem [0x44200000-0x443fffff]
[    1.002648] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]
[    1.002651] pci_bus 0000:03: resource 1 mem: [0x44400000-0x445fffff]
[    1.002655] pci_bus 0000:03: resource 2 pref mem [0x44600000-0x447fffff]
[    1.002659] pci_bus 0000:04: resource 0 io:  [0x5000-0x5fff]
[    1.002662] pci_bus 0000:04: resource 1 mem: [0x44800000-0x449fffff]
[    1.002666] pci_bus 0000:04: resource 2 pref mem [0x44a00000-0x44bfffff]
[    1.002669] pci_bus 0000:05: resource 0 io:  [0x6000-0x6fff]
[    1.002672] pci_bus 0000:05: resource 1 mem: [0x44c00000-0x44dfffff]
[    1.002676] pci_bus 0000:05: resource 2 pref mem [0x44e00000-0x44ffffff]
[    1.002680] pci_bus 0000:0a: resource 0 io:  [0x7000-0x7fff]
[    1.002683] pci_bus 0000:0a: resource 1 mem: [0xc8400000-0xc84fffff]
[    1.002687] pci_bus 0000:0a: resource 2 pref mem [0x40000000-0x43ffffff]
[    1.002690] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    1.002693] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffff]
[    1.002697] pci_bus 0000:0b: resource 0 io:  [0x7000-0x70ff]
[    1.002700] pci_bus 0000:0b: resource 1 io:  [0x7400-0x74ff]
[    1.002704] pci_bus 0000:0b: resource 2 pref mem [0x40000000-0x43ffffff]
[    1.002707] pci_bus 0000:0b: resource 3 mem: [0x48000000-0x4bffffff]
[    1.002748] NET: Registered protocol family 2
[    1.002861] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.003245] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.004014] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.004382] TCP: Hash tables configured (established 131072 bind 65536)
[    1.004386] TCP reno registered
[    1.004496] NET: Registered protocol family 1
[    1.004630] pci 0000:01:00.0: Boot video device
[    1.004671] Simple Boot Flag at 0x36 set to 0x1
[    1.004895] cpufreq-nforce2: No nForce2 chipset.
[    1.004930] Scanning for low memory corruption every 60 seconds
[    1.005076] audit: initializing netlink socket (disabled)
[    1.005089] type=2000 audit(1311876427.003:1): initialized
[    1.017623] highmem bounce pool size: 64 pages
[    1.017629] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.019698] VFS: Disk quotas dquot_6.5.2
[    1.019774] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.020566] fuse init (API version 7.13)
[    1.020679] msgmni has been set to 1731
[    1.020948] alg: No test for stdrng (krng)
[    1.021020] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.021024] io scheduler noop registered
[    1.021027] io scheduler anticipatory registered
[    1.021029] io scheduler deadline registered
[    1.021083] io scheduler cfq registered (default)
[    1.021254]   alloc irq_desc for 24 on node -1
[    1.021256]   alloc kstat_irqs on node -1
[    1.021266] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    1.021275] pcieport 0000:00:01.0: setting latency timer to 64
[    1.021407]   alloc irq_desc for 25 on node -1
[    1.021410]   alloc kstat_irqs on node -1
[    1.021420] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    1.021431] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.021601]   alloc irq_desc for 26 on node -1
[    1.021604]   alloc kstat_irqs on node -1
[    1.021613] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    1.021625] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.021794]   alloc irq_desc for 27 on node -1
[    1.021796]   alloc kstat_irqs on node -1
[    1.021806] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    1.021818] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.021984]   alloc irq_desc for 28 on node -1
[    1.021987]   alloc kstat_irqs on node -1
[    1.021997] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    1.022008] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.022128] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.022288] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.036117] ACPI: AC Adapter [ACAD] (on-line)
[    1.036228] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.036301] ACPI: Lid Switch [LID]
[    1.036358] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.036362] ACPI: Power Button [PWRB]
[    1.036421] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.036425] ACPI: Sleep Button [SLPB]
[    1.036481] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.036485] ACPI: Power Button [PWRF]
[    1.037281] ACPI: SSDT 3fe8f165 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.037829] ACPI: SSDT 3fe8ef10 001D0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.038304] Marking TSC unstable due to TSC halts in idle
[    1.038357] Switching to clocksource hpet
[    1.038424] processor LNXCPU:00: registered as cooling_device0
[    1.038889] ACPI: SSDT 3fe8f30d 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.039368] ACPI: SSDT 3fe8f0e0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.039944] processor LNXCPU:01: registered as cooling_device1
[    1.072075] thermal LNXTHERM:01: registered as thermal_zone0
[    1.072085] ACPI: Thermal Zone [THRM] (37 C)
[    1.072175] ACPI: Battery Slot [BAT1] (battery absent)
[    1.072202] isapnp: Scanning for PnP cards...
[    1.074010] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.074185] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.075837] brd: module loaded
[    1.076467] loop: module loaded
[    1.076563] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.076667] ata_piix 0000:00:1f.2: version 2.13
[    1.076687] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.076694] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.232025] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.232124] scsi0 : ata_piix
[    1.232222] scsi1 : ata_piix
[    1.232810] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.232814] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.233256] Fixed MDIO Bus: probed
[    1.233305] PPP generic driver version 2.4.2
[    1.233351] tun: Universal TUN/TAP device driver, 1.6
[    1.233354] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.233459] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.233482]   alloc irq_desc for 23 on node -1
[    1.233485]   alloc kstat_irqs on node -1
[    1.233491] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.233503] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.233508] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.233552] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.233578] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.233592] ehci_hcd 0000:00:1d.7: debug port 1
[    1.237472] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.237488] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc8004000
[    1.252018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.252139] usb usb1: configuration #1 chosen from 1 choice
[    1.252176] hub 1-0:1.0: USB hub found
[    1.252186] hub 1-0:1.0: 8 ports detected
[    1.252271] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.252289] uhci_hcd: USB Universal Host Controller Interface driver
[    1.252316] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.252324] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.252329] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.252369] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.252399] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    1.252507] usb usb2: configuration #1 chosen from 1 choice
[    1.252543] hub 2-0:1.0: USB hub found
[    1.252551] hub 2-0:1.0: 2 ports detected
[    1.252607] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.252614] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.252619] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.252658] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.252697] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    1.252808] usb usb3: configuration #1 chosen from 1 choice
[    1.252841] hub 3-0:1.0: USB hub found
[    1.252849] hub 3-0:1.0: 2 ports detected
[    1.252904] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.252911] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.252916] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.252953] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.252991] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    1.253106] usb usb4: configuration #1 chosen from 1 choice
[    1.253139] hub 4-0:1.0: USB hub found
[    1.253147] hub 4-0:1.0: 2 ports detected
[    1.253206] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.253214] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.253218] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.253255] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.253293] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    1.253414] usb usb5: configuration #1 chosen from 1 choice
[    1.253447] hub 5-0:1.0: USB hub found
[    1.253455] hub 5-0:1.0: 2 ports detected
[    1.253572] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.255699] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.258222] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.258231] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.258235] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.258239] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.258243] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.258330] mice: PS/2 mouse device common for all mice
[    1.258505] rtc_cmos 00:06: RTC can wake from S4
[    1.258554] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.258589] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.258717] device-mapper: uevent: version 1.0.3
[    1.258832] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.258909] device-mapper: multipath: version 1.1.0 loaded
[    1.258913] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.259051] EISA: Probing bus 0 at eisa.0
[    1.259058] Cannot allocate resource for EISA slot 1
[    1.259061] Cannot allocate resource for EISA slot 2
[    1.259064] Cannot allocate resource for EISA slot 3
[    1.259067] Cannot allocate resource for EISA slot 4
[    1.259070] Cannot allocate resource for EISA slot 5
[    1.259073] Cannot allocate resource for EISA slot 6
[    1.259076] Cannot allocate resource for EISA slot 7
[    1.259083] EISA: Detected 0 cards.
[    1.259266] cpuidle: using governor ladder
[    1.259419] cpuidle: using governor menu
[    1.259973] TCP cubic registered
[    1.260200] NET: Registered protocol family 10
[    1.260783] lo: Disabled Privacy Extensions
[    1.261204] NET: Registered protocol family 17
[    1.261553] Using IPI No-Shortcut mode
[    1.261644] PM: Resume from disk failed.
[    1.261664] registered taskstats version 1
[    1.262227]   Magic number: 3:86:141
[    1.262239] block ram6: hash matches
[    1.262276] acpi device:12: hash matches
[    1.262322] rtc_cmos 00:06: setting system clock to 2011-07-28 18:07:08 UTC (1311876428)
[    1.262326] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.262328] EDD information not available.
[    1.293828] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.405561] ata1.00: ATA-7: ST9120821AS, 3.06, max UDMA/133
[    1.405566] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.414111] ata2.00: ATAPI: PIONEER DVD-RW DVR-K06RS, 1.01, max UDMA/33
[    1.421606] ata1.00: configured for UDMA/133
[    1.426521] isapnp: No Plug & Play device found
[    1.426672] scsi 0:0:0:0: Direct-Access     ATA      ST9120821AS      3.06 PQ: 0 ANSI: 5
[    1.426832] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.426837] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.426906] sd 0:0:0:0: [sda] Write Protect is off
[    1.426910] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.426941] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.427101]  sda: sda1 sda2 sda3
[    1.445538] ata2.00: configured for UDMA/33
[    1.461238] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.467459] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW DVR-K06RS 1.01 PQ: 0 ANSI: 5
[    1.493580] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.493584] Uniform CD-ROM driver Revision: 3.20
[    1.493679] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.493733] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.493804] Freeing unused kernel memory: 656k freed
[    1.494248] Write protecting the kernel text: 4676k
[    1.494324] Write protecting the kernel read-only data: 1840k
[    1.513666] udev: starting version 151
[    1.650374] tg3.c:v3.102 (September 1, 2009)
[    1.650395] tg3 0000:04:00.0: enabling device (0000 -> 0002)
[    1.650406] tg3 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.650420] tg3 0000:04:00.0: setting latency timer to 64
[    1.671091] ohci1394 0000:0a:09.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.700293] eth0: Tigon3 [partno(BCM95789) rev 4201] (PCI Express) MAC address 00:16:36:70:3d:cb
[    1.700298] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.700302] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.700305] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.705086] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.725122] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c8405000-c84057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.877051] usb 1-8: configuration #1 chosen from 1 choice
[    1.894171] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.116052] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.287167] usb 4-1: configuration #1 chosen from 1 choice
[   27.002933] udev[360]: starting version 163
[   27.085803] lp: driver loaded but no devices found
[   27.145769] irda_init()
[   27.145786] NET: Registered protocol family 23
[   27.162271] Adding 4096564k swap on /dev/sda2.  Priority:-1 extents:1 across:4096564k 
[   27.391027] intel_rng: FWH not detected
[   27.417257] Linux agpgart interface v0.103
[   27.461470] cfg80211: Calling CRDA to update world regulatory domain
[   27.487212] cfg80211: World regulatory domain updated:
[   27.487218]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.487222]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.487226]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.487230]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.487234]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.487238]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.490706] Bluetooth: Core ver 2.15
[   27.491931] NET: Registered protocol family 31
[   27.491935] Bluetooth: HCI device and connection manager initialized
[   27.491939] Bluetooth: HCI socket layer initialized
[   27.500121] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0094]
[   27.500149] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   27.500153] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   27.500160] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   27.503080] acer-wmi: Acer Laptop ACPI-WMI Extras
[   27.532786] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   27.533223] usbcore: registered new interface driver btusb
[   27.573488] type=1505 audit(1311876454.809:2):  operation="profile_load" pid=680 name="/sbin/dhclient3"
[   27.574284] type=1505 audit(1311876454.809:3):  operation="profile_load" pid=680 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.574709] type=1505 audit(1311876454.809:4):  operation="profile_load" pid=680 name="/usr/lib/connman/scripts/dhclient-script"
[   27.577011] type=1505 audit(1311876454.813:5):  operation="profile_replace" pid=692 name="/sbin/dhclient3"
[   27.577802] type=1505 audit(1311876454.813:6):  operation="profile_replace" pid=692 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.578388] type=1505 audit(1311876454.813:7):  operation="profile_replace" pid=692 name="/usr/lib/connman/scripts/dhclient-script"
[   27.592234] [drm] Initialized drm 1.1.0 20060810
[   27.667035] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 2.6.32-22-generic-ks
[   27.667040] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   27.667121] iwl3945 0000:03:00.0: enabling device (0000 -> 0002)
[   27.667135] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.667156] iwl3945 0000:03:00.0: setting latency timer to 64
[   27.738621] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.738627] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   27.738745]   alloc irq_desc for 29 on node -1
[   27.738748]   alloc kstat_irqs on node -1
[   27.738783] iwl3945 0000:03:00.0: irq 29 for MSI/MSI-X
[   27.742134] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.742143] pci 0000:01:00.0: setting latency timer to 64
[   27.742345] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[   27.747680] vga16fb: initializing
[   27.747686] vga16fb: mapped to 0xc00a0000
[   27.747818] fb0: VGA16 VGA frame buffer device
[   27.750329] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   27.750335] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   27.750341] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   27.750351] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[   27.750356] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean.
[   27.750652] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0xc8400000 - 0xc84fffff
[   27.750657] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   27.754208] tifm_7xx1 0000:0a:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   27.864362] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   27.919208]   alloc irq_desc for 22 on node -1
[   27.919211]   alloc kstat_irqs on node -1
[   27.919220] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.919259] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   27.920895] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.948449] Console: switching to colour frame buffer device 80x30
[   28.034889] hda_codec: ALC883: BIOS auto-probing.
[   28.035922] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   28.158132] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   28.202012] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   29.052024] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x006f0d00
[   29.161115] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   29.163109] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.163958] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.164680] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   29.165603] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   32.443351] type=1505 audit(1311876459.677:8):  operation="profile_load" pid=936 name="/usr/lib/cups/backend/cups-pdf"
[   32.444361] type=1505 audit(1311876459.681:9):  operation="profile_load" pid=936 name="/usr/sbin/cupsd"
[   32.492198] type=1505 audit(1311876459.729:10):  operation="profile_replace" pid=970 name="/sbin/dhclient3"
[   32.493052] type=1505 audit(1311876459.729:11):  operation="profile_replace" pid=970 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   32.497416] ppdev: user-space parallel port driver
[   32.589715] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   32.631199] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   32.713095] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.714997]   alloc irq_desc for 30 on node -1
[   32.715001]   alloc kstat_irqs on node -1
[   32.715019] tg3 0000:04:00.0: irq 30 for MSI/MSI-X
[   32.866616] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.965977] apm: BIOS not found.
[   33.377191] [drm] Setting GART location based on new memory map
[   33.379115] [drm] Loading R500 Microcode
[   33.379121] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[   33.381280] [drm] Num pipes: 1
[   33.381291] [drm] writeback test succeeded in 2 usecs
[   33.846836] Bluetooth: L2CAP ver 2.14
[   33.846841] Bluetooth: L2CAP socket layer initialized
[   33.858974] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.858979] Bluetooth: BNEP filters: protocol multicast
[   33.871979] Bridge firewalling registered
[   33.887101] Bluetooth: SCO (Voice Link) ver 0.6
[   33.887105] Bluetooth: SCO socket layer initialized
[   33.961842] Bluetooth: RFCOMM TTY layer initialized
[   33.961849] Bluetooth: RFCOMM socket layer initialized
[   33.961852] Bluetooth: RFCOMM ver 1.11
[   91.810973] CE: hpet increasing min_delta_ns to 15000 nsec
[  149.221601] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  149.222629] input: Kensington SlimBlade Trackball Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input8
[  149.222765] generic-bluetooth 0005:047D:1153.0001: input,hidraw0: BLUETOOTH HID v1.29 Mouse [Kensington SlimBlade Trackball Mouse] on 00:16:CE:DF:7F:BC
[  160.716746] wlan0: direct probe to AP b0:e7:54:eb:c4:41 (try 1)
[  160.719719] wlan0: direct probe responded
[  160.719726] wlan0: authenticate with AP b0:e7:54:eb:c4:41 (try 1)
[  160.722083] wlan0: authenticated
[  160.722110] wlan0: associate with AP b0:e7:54:eb:c4:41 (try 1)
[  160.723877] wlan0: RX AssocResp from b0:e7:54:eb:c4:41 (capab=0x431 status=0 aid=3)
[  160.723881] wlan0: associated
[  160.725431] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  160.736104] cfg80211: Calling CRDA for country: US
[  160.770431] cfg80211: Received country IE:
[  160.770436] cfg80211: Regulatory domain: US
[  160.770439]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  160.770443]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  160.770446] cfg80211: CRDA thinks this should applied:
[  160.770448] cfg80211: Regulatory domain: US
[  160.770451]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  160.770454]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  160.770458]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  160.770462]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.770466]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.770470]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.770473]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  160.770476] cfg80211: We intersect both of these and get:
[  160.770478] cfg80211: Regulatory domain: 98
[  160.770481]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  160.770485]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  160.770491] cfg80211: Current regulatory domain updated by AP to: US
[  160.770493]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  160.770497]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  171.596028] wlan0: no IPv6 routers present
[  201.750317] input: Kensington SlimBlade Trackball Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input9
[  201.750462] generic-bluetooth 0005:047D:1153.0002: input,hidraw0: BLUETOOTH HID v1.29 Mouse [Kensington SlimBlade Trackball Mouse] on 00:16:CE:DF:7F:BC
[  231.820701] lo: Disabled Privacy Extensions
[ 2011.024139] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 2011.144187] usb 3-1: device descriptor read/64, error -71
[ 2011.372187] usb 3-1: device descriptor read/64, error -71
[ 2011.588152] usb 3-1: new low speed USB device using uhci_hcd and address 3
[ 2011.768190] usb 3-1: device descriptor read/64, error -71
[ 2011.993219] usb 3-1: device descriptor read/64, error -71
[ 2012.208191] usb 3-1: new low speed USB device using uhci_hcd and address 4
[ 2012.620083] usb 3-1: device not accepting address 4, error -71
[ 2012.732189] usb 3-1: new low speed USB device using uhci_hcd and address 5
[ 2013.144064] usb 3-1: device not accepting address 5, error -71
[ 2013.144096] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 2014.479463] input: Kensington SlimBlade Trackball Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input10
[ 2014.480064] generic-bluetooth 0005:047D:1153.0003: input,hidraw0: BLUETOOTH HID v1.29 Mouse [Kensington SlimBlade Trackball Mouse] on 00:16:CE:DF:7F:BC
[ 2034.980954] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2272.060119] usb 3-1: new low speed USB device using uhci_hcd and address 6
[ 2272.180084] usb 3-1: device descriptor read/64, error -71
[ 2272.404083] usb 3-1: device descriptor read/64, error -71
[ 2272.620083] usb 3-1: new low speed USB device using uhci_hcd and address 7
[ 2272.740182] usb 3-1: device descriptor read/64, error -71
[ 2272.964154] usb 3-1: device descriptor read/64, error -71
[ 2273.180192] usb 3-1: new low speed USB device using uhci_hcd and address 8
[ 2273.592048] usb 3-1: device not accepting address 8, error -71
[ 2273.704154] usb 3-1: new low speed USB device using uhci_hcd and address 9
[ 2274.112167] usb 3-1: device not accepting address 9, error -71
[ 2274.112202] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 6336.000572] __ratelimit: 30 callbacks suppressed
[ 6336.000581] Xorg[1101]: segfault at 0 ip 080a1e82 sp bfa007ec error 4 in Xorg[8048000+1a7000]
[ 6338.333223] [drm] Num pipes: 1
[ 6342.008194] wlan0: deauthenticating from b0:e7:54:eb:c4:41 by local choice (reason=3)
[ 6348.877142] [drm] Setting GART location based on new memory map
[ 6348.879183] [drm] Loading R500 Microcode
[ 6348.879189] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[ 6349.076500] [drm] Num pipes: 1
[ 6349.076514] [drm] writeback test succeeded in 1 usecs
[ 6432.425896] wlan0: direct probe to AP b0:e7:54:eb:c4:41 (try 1)
[ 6432.428476] wlan0: direct probe responded
[ 6432.428484] wlan0: authenticate with AP b0:e7:54:eb:c4:41 (try 1)
[ 6432.432033] wlan0: authenticated
[ 6432.432348] wlan0: associate with AP b0:e7:54:eb:c4:41 (try 1)
[ 6432.435207] wlan0: RX AssocResp from b0:e7:54:eb:c4:41 (capab=0x431 status=0 aid=2)
[ 6432.435212] wlan0: associated
[ 6485.855806] lo: Disabled Privacy Extensions

```

and xawtv after:

```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-22-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```

---

### Post by no2498 on 2011-07-29
looks like you may need to un black list the driver
or the cam is bad
you may have a piece of dust in the cam wire or usb port

---

### Post by KaYnemO on 2011-07-30
> **no2498 said:**
> looks like you may need to un black list the driver
or the cam is bad
you may have a piece of dust in the cam wire or usb port

hmm... I removed the blacklisted chain for the gspca, to no avail... the camera is built-in, so no dust in usb port...

---

### Post by no2498 on 2011-07-31
do you need to click keys like fn f4 at the same time to start the cam the first time ?

rerun the dmesg see if it finds the cam

also run lsusb

---

