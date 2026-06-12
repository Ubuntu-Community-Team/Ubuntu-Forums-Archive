---
title: "Wiress doesn't show any networks - Ticket info followed, extensive info in post"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by SweetBearCub on 2012-03-12
Fresh install of Ubuntu 11.10 x64 on a partitioned hard drive shared with Windows 7 Ultimate x64. Wireless will not display any networks while in Ubuntu. I found "http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware", but cannot follow its directions since I cannot give the Ubuntu installation any Internet access other than wireless. However, Windows on the same machine does have access, and there is a separate hard drive that stores data that Ubuntu can access.

Please forgive this wall of text post!

1) Machine Brand/Model - MSI P7N SLI
2) Wireless Brand/Chipset - Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
3) Check Interfaces - ifconfig and iwconfig results below.

----- START IFCONFIG RESULTS ------

eth0      Link encap:Ethernet  HWaddr 00:21:85:5a:60:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)

------ END IFCONFIG RESULTS ------
------ START IWCONFIG RESULTS ------

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

------ END IWCONFIG RESULTS ------

4) Check for modules. lsmod results below.

------ START LSMOD RESULTS ------

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  1 
gspca_sn9c20x          36054  0 
gspca_main             28314  1 gspca_sn9c20x
videodev               93004  1 gspca_main
usbhid                 47198  0 
v4l2_compat_ioctl32    17083  1 videodev
hid                    95463  1 usbhid
nls_utf8               12557  1 
isofs                  40253  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
b43                   341198  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
nv_tco                 13687  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usb_storage            57901  0 
uas                    18027  0 
ssb                    52752  1 b43
crc_itu_t              12707  1 firewire_core
forcedeth              67563  0 
pata_amd               14121  0 
sata_nv                32305  5 
nouveau               728662  3 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236330  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau

------ END LSMOD RESULTS ------

5) Kernel boot messages. dmesg results below. Note that due to the volume of information returned, an unknown amount of data was lost from this command, and only the last several lines were able to be copied.

------ START DMESG RESULTS ------

[    0.947217] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.947295] device-mapper: uevent: version 1.0.3
[    0.947356] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.947364] cpuidle: using governor ladder
[    0.947366] cpuidle: using governor menu
[    0.947368] EFI Variables Facility v0.08 2004-May-17
[    0.947593] TCP cubic registered
[    0.947698] NET: Registered protocol family 10
[    0.948137] NET: Registered protocol family 17
[    0.948152] Registering the dns_resolver key type
[    0.948231] PM: Hibernation image not present or could not be loaded.
[    0.948242] registered taskstats version 1
[    0.963554]   Magic number: 4:963:400
[    0.963666] rtc_cmos 00:07: setting system clock to 2012-03-11 22:21:45 UTC (1331504505)
[    0.964993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.964995] EDD information not available.
[    0.966688] Freeing unused kernel memory: 984k freed
[    0.966951] Write protecting the kernel read-only data: 10240k
[    0.967167] Freeing unused kernel memory: 20k freed
[    0.971632] Freeing unused kernel memory: 1400k freed
[    0.980372] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.990282] udevd[90]: starting version 173
[    1.024710] wmi: Mapper loaded
[    1.043469] [drm] Initialized drm 1.1.0 20060810
[    1.063456] sata_nv 0000:00:0e.0: version 3.5
[    1.063490] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.063493] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.063620] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.065394] scsi0 : sata_nv
[    1.066967] scsi1 : sata_nv
[    1.067105] ata1: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb000 irq 23
[    1.067108] ata2: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xb008 irq 23
[    1.067170] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.067173] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.067322] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.068753] scsi2 : sata_nv
[    1.069927] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[    1.069948] nouveau 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[    1.069954] nouveau 0000:03:00.0: setting latency timer to 64
[    1.070125] scsi3 : sata_nv
[    1.070289] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 22
[    1.070292] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 22
[    1.070361] pata_amd 0000:00:0d.0: version 0.4.1
[    1.070410] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.071047] scsi4 : pata_amd
[    1.072673] scsi5 : pata_amd
[    1.072778] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    1.072801] b43-pci-bridge 0000:08:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    1.072840] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.072846] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.072852] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.072857] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.072864] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.073393] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x096080c1)
[    1.074131] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.074134] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.074252] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.075067] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    1.075071] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.075331] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.076256] ssb: Sonics Silicon Backplane found on PCI device 0000:08:07.0
[    1.079629] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[    1.154628] [drm] nouveau 0000:03:00.0: ... appears to be valid
[    1.154631] [drm] nouveau 0000:03:00.0: BIT BIOS found
[    1.154634] [drm] nouveau 0000:03:00.0: Bios version 62.94.29.00
[    1.154637] [drm] nouveau 0000:03:00.0: TMDS table version 2.0
[    1.154640] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[    1.154643] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 00000028
[    1.154646] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01000302 00020030
[    1.154648] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 04011310 00000028
[    1.154650] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02011312 00020030
[    1.154652] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 010223f1 00c0c080
[    1.154655] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 16 4
[    1.154658] [drm] nouveau 0000:03:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    1.154660] [drm] nouveau 0000:03:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    1.154663] [drm] nouveau 0000:03:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    1.154665] [drm] nouveau 0000:03:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    1.154667] [drm] nouveau 0000:03:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    1.154672] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xD0BE
[    1.179812] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xD4D3
[    1.182842] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xE4C4
[    1.182850] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xE60D
[    1.183921] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xE849
[    1.183923] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xE8AE
[    1.203769] [drm] nouveau 0000:03:00.0: 0xE8AE: Condition still not met after 20ms, skipping following opcodes
[    1.203793] [drm] nouveau 0000:03:00.0: timingset 255 does not exist
[    1.204119] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.222660] [drm] nouveau 0000:03:00.0: 1 available performance level(s)
[    1.222664] [drm] nouveau 0000:03:00.0: 3: memory 400MHz core 550MHz shader 1375MHz fanspeed 100%
[    1.222680] [drm] nouveau 0000:03:00.0: c: memory 399MHz core 400MHz shader 800MHz
[    1.222784] [TTM] Zone  kernel: Available graphics memory: 1545104 kiB.
[    1.222786] [TTM] Initializing pool allocator.
[    1.222800] [drm] nouveau 0000:03:00.0: Detected 512MiB VRAM
[    1.226724] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[    1.241083] [drm] nouveau 0000:03:00.0: DCB encoder 1 unknown
[    1.241085] [drm] nouveau 0000:03:00.0: TV-1 has no encoders, removing
[    1.241849] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.241851] [drm] No driver support for vblank timestamp query.
[    1.404199] [drm] nouveau 0000:03:00.0: allocated 1280x1024 fb: 0x40000000, bo ffff880036bfb400
[    1.404257] fbcon: nouveaufb (fb0) is primary device
[    1.404306] Console: switching to colour frame buffer device 160x64
[    1.404332] fb0: nouveaufb frame buffer device
[    1.404333] drm: registered panic notifier
[    1.404340] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
[    1.404360] nouveau 0000:04:00.0: enabling device (0000 -> 0003)
[    1.404520] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 17
[    1.404535] nouveau 0000:04:00.0: PCI INT A -> Link[LNEC] -> GSI 17 (level, low) -> IRQ 17
[    1.404541] nouveau 0000:04:00.0: setting latency timer to 64
[    1.406257] [drm] nouveau 0000:04:00.0: Detected an NV50 generation card (0x096080c1)
[    1.412103] [drm] nouveau 0000:04:00.0: Attempting to load BIOS image from PRAMIN
[    1.412110] [drm] nouveau 0000:04:00.0: ... BIOS signature not found
[    1.412112] [drm] nouveau 0000:04:00.0: Attempting to load BIOS image from PROM
[    1.532123] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.536098] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.541815] ata1.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    1.541818] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.544166] Refined TSC clocksource calibration: 2399.977 MHz.
[    1.544171] Switching to clocksource tsc
[    1.599277] [drm] nouveau 0000:04:00.0: ... appears to be valid
[    1.599280] [drm] nouveau 0000:04:00.0: BIT BIOS found
[    1.599283] [drm] nouveau 0000:04:00.0: Bios version 62.94.29.00
[    1.599286] [drm] nouveau 0000:04:00.0: TMDS table version 2.0
[    1.599288] [drm] nouveau 0000:04:00.0: Found Display Configuration Block version 4.0
[    1.599291] [drm] nouveau 0000:04:00.0: Raw DCB entry 0: 02000300 00000028
[    1.599294] [drm] nouveau 0000:04:00.0: Raw DCB entry 1: 01000302 00020030
[    1.599296] [drm] nouveau 0000:04:00.0: Raw DCB entry 2: 04011310 00000028
[    1.599298] [drm] nouveau 0000:04:00.0: Raw DCB entry 3: 02011312 00020030
[    1.599300] [drm] nouveau 0000:04:00.0: Raw DCB entry 4: 010223f1 00c0c080
[    1.599303] [drm] nouveau 0000:04:00.0: DCB connector table: VHER 0x40 5 16 4
[    1.599306] [drm] nouveau 0000:04:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    1.599308] [drm] nouveau 0000:04:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    1.599310] [drm] nouveau 0000:04:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    1.599313] [drm] nouveau 0000:04:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    1.599315] [drm] nouveau 0000:04:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    1.599323] [drm] nouveau 0000:04:00.0: Adaptor not initialised, running VBIOS init tables.
[    1.599325] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table 0 at offset 0xD0BE
[    1.624708] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table 1 at offset 0xD4D3
[    1.681268] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table 2 at offset 0xE4C4
[    1.681303] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table 3 at offset 0xE60D
[    1.683052] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table 4 at offset 0xE849
[    1.683054] [drm] nouveau 0000:04:00.0: Parsing VBIOS init table at offset 0xE8AE
[    1.702993] [drm] nouveau 0000:04:00.0: timingset 255 does not exist
[    1.703703] ata3.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.703706] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.703957] ata1.00: configured for UDMA/133
[    1.704080] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    1.704264] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.704333] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.704397] sd 0:0:0:0: [sda] Write Protect is off
[    1.704400] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.704424] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.716330] ata3.00: configured for UDMA/133
[    1.720987] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:85:5a:60:30
[    1.720990] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    1.721753] [drm] nouveau 0000:04:00.0: 1 available performance level(s)
[    1.721758] [drm] nouveau 0000:04:00.0: 3: memory 400MHz core 550MHz shader 1375MHz fanspeed 100%
[    1.721774] [drm] nouveau 0000:04:00.0: c: memory 399MHz core 400MHz shader 800MHz
[    1.721819] [drm] nouveau 0000:04:00.0: Detected 512MiB VRAM
[    1.725059] [drm] nouveau 0000:04:00.0: 512 MiB GART (aperture)
[    1.739339] [drm] nouveau 0000:04:00.0: DCB encoder 1 unknown
[    1.739341] [drm] nouveau 0000:04:00.0: TV-2 has no encoders, removing
[    1.740098] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.740100] [drm] No driver support for vblank timestamp query.
[    1.756020] usb 1-7: new high speed USB device number 5 using ehci_hcd
[    1.847780] No connectors reported connected with modes
[    1.847785] [drm] Cannot find any crtc or sizes - going 1024x768
[    1.848887] [drm] nouveau 0000:04:00.0: allocated 1024x768 fb: 0x40000000, bo ffff8800361f8400
[    1.848951] fb1: nouveaufb frame buffer device
[    1.848956] [drm] Initialized nouveau 0.0.16 20090420 for 0000:04:00.0 on minor 1
[    1.894643] usbcore: registered new interface driver uas
[    2.107517]  sda: sda1
[    2.107740] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.172025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.180696] ata2.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[    2.180700] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.196011] usb 2-3: new full speed USB device number 2 using ohci_hcd
[    2.196687] ata2.00: configured for UDMA/133
[    2.196814] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    2.196970] sd 1:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.197005] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.197021] sd 1:0:0:0: [sdb] Write Protect is off
[    2.197024] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.197047] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.197161] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.197266] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.197279] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.197324] sd 2:0:0:0: [sdc] Write Protect is off
[    2.197327] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.197369] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.219346]  sdc: sdc1
[    2.219535] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.236930]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.237205] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.664020] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.672163] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223L, SB02, max UDMA/100
[    2.688159] ata4.00: configured for UDMA/100
[    2.689007] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223L  SB02 PQ: 0 ANSI: 5
[    2.693327] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.693330] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.693432] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.693501] sr 3:0:0:0: Attached scsi generic sg3 type 5
[    2.860367] Initializing USB Mass Storage driver...
[    2.864471] scsi6 : usb-storage 1-7:1.0
[    2.864493] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 16
[    2.864522] firewire_ohci 0000:08:09.0: PCI INT A -> Link[LNKD] -> GSI 16 (level, low) -> IRQ 16
[    2.864788] usbcore: registered new interface driver usb-storage
[    2.864790] USB Mass Storage support registered.
[    2.928068] firewire_ohci: Added fw-ohci device 0000:08:09.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.416918] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    3.428151] firewire_core: created device fw0: GUID 0010dc000167a970, S400
[    3.866587] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    3.867323] scsi 6:0:0:1: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    3.867947] scsi 6:0:0:2: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    3.868697] scsi 6:0:0:3: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0 CCS
[    3.869321] scsi 6:0:0:4: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    4.308173] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    4.308287] sd 6:0:0:1: Attached scsi generic sg5 type 0
[    4.308398] sd 6:0:0:2: Attached scsi generic sg6 type 0
[    4.308515] sd 6:0:0:3: Attached scsi generic sg7 type 0
[    4.308625] sd 6:0:0:4: Attached scsi generic sg8 type 0
[    4.313192] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[    4.315696] sd 6:0:0:1: [sde] Attached SCSI removable disk
[    4.316317] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[    4.316940] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[    4.317569] sd 6:0:0:4: [sdh] Attached SCSI removable disk
[   10.373448] udevd[396]: starting version 173
[   10.417117] lp: driver loaded but no devices found
[   10.476893] i2c i2c-6: nForce2 SMBus adapter at 0x5000
[   10.476919] i2c i2c-7: nForce2 SMBus adapter at 0x6000
[   10.477223] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   10.477322] NV_TCO: Watchdog reboot not detected.
[   10.477474] NV_TCO: initialized (0x4440). heartbeat=30 sec (nowayout=0)
[   10.509709] cfg80211: Calling CRDA to update world regulatory domain
[   10.510998] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro
[   10.514294] type=1400 audit(1331529715.047:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=558 comm="apparmor_parser"
[   10.514570] type=1400 audit(1331529715.047:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=558 comm="apparmor_parser"
[   10.514768] type=1400 audit(1331529715.047:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=558 comm="apparmor_parser"
[   10.523907] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.550379] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   10.550387] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   10.550390] hda_intel: Disabling MSI
[   10.550432] HDA Intel 0000:00:10.1: setting latency timer to 64
[   10.568677] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.568685] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568687] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.568689] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568691] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.568694] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568696] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.568698] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568700] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.568703] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568705] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.568707] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568709] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.568712] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568714] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.568716] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568718] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.568721] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568723] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.568726] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568728] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.568730] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568732] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.568735] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568739] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.568741] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.568743] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.568746] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.586716] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.587942] Registered led device: b43-phy0::tx
[   10.587980] Registered led device: b43-phy0::rx
[   10.588291] Registered led device: b43-phy0::radio
[   10.588352] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   10.657940] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.657948] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657951] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.657953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657955] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.657958] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657960] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.657962] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657964] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.657967] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657969] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.657971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657973] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.657976] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657977] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.657980] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657982] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.657984] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657987] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.657989] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657991] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.657993] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.657995] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.657998] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.658000] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.658002] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.658005] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.658007] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.658014] cfg80211: World regulatory domain updated:
[   10.658015] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.658018] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.658021] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.658023] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.658026] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.658028] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.795661] type=1400 audit(1331529715.327:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=814 comm="apparmor_parser"
[   10.797636] type=1400 audit(1331529715.331:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=815 comm="apparmor_parser"
[   10.797892] type=1400 audit(1331529715.331:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=815 comm="apparmor_parser"
[   10.798049] type=1400 audit(1331529715.331:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=815 comm="apparmor_parser"
[   10.803018] type=1400 audit(1331529715.335:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=818 comm="apparmor_parser"
[   10.803310] type=1400 audit(1331529715.335:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=818 comm="apparmor_parser"
[   10.807973] type=1400 audit(1331529715.339:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=816 comm="apparmor_parser"
[   10.931489] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.931494] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.931497] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   10.933864] forcedeth 0000:00:14.0: eth0: no link during initialization
[   10.934680] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.054990] init: failsafe main process (757) killed by TERM signal
[   11.055780] init: apport pre-start process (871) terminated with status 1
[   11.058431] init: alsa-restore main process (879) terminated with status 19
[   11.066016] init: apport post-stop process (897) terminated with status 1
[   11.164021] hda_codec: ALC888: BIOS auto-probing.
[   11.194092] Bluetooth: Core ver 2.16
[   11.194147] NET: Registered protocol family 31
[   11.194149] Bluetooth: HCI device and connection manager initialized
[   11.194151] Bluetooth: HCI socket layer initialized
[   11.194153] Bluetooth: L2CAP socket layer initialized
[   11.194912] Bluetooth: SCO socket layer initialized
[   11.197864] Bluetooth: RFCOMM TTY layer initialized
[   11.197878] Bluetooth: RFCOMM socket layer initialized
[   11.197880] Bluetooth: RFCOMM ver 1.11
[   11.205714] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=none
[   11.205718] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.210189] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.210192] Bluetooth: BNEP filters: protocol multicast
[   11.512534] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:10.1/sound/card0/input3
[   11.738403] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro,commit=0
[   12.018470] init: plymouth-stop pre-start process (1082) terminated with status 1
[   13.059579] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro,commit=0
[   17.372011] usb 2-3: device descriptor read/64, error -110
[   25.304190] ISO 9660 Extensions: Microsoft Joliet Level 3
[   25.323063] ISO 9660 Extensions: RRIP_1991A
[   25.327830] init: ureadahead-other main process (1528) terminated with status 2
[   32.652011] usb 2-3: device descriptor read/64, error -110
[   32.932010] usb 2-3: new full speed USB device number 3 using ohci_hcd
[   48.108013] usb 2-3: device descriptor read/64, error -110
[   63.388010] usb 2-3: device descriptor read/64, error -110
[   63.668009] usb 2-3: new full speed USB device number 4 using ohci_hcd
[   68.688060] usb 2-3: device descriptor read/8, error -110
[   73.808075] usb 2-3: device descriptor read/8, error -110
[   74.088014] usb 2-3: new full speed USB device number 5 using ohci_hcd
[   79.108075] usb 2-3: device descriptor read/8, error -110
[   84.228083] usb 2-3: device descriptor read/8, error -110
[   84.332024] hub 2-0:1.0: unable to enumerate USB device on port 3
[   84.636054] usb 2-4: new low speed USB device number 6 using ohci_hcd
[   85.074339] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input4
[   85.074479] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-4/input0
[   85.074504] usbcore: registered new interface driver usbhid
[   85.074505] usbhid: USB HID core driver
[   85.074908] Linux video capture interface: v2.00
[   85.115969] gspca: v2.13.0 registered
[   85.172970] sn9c20x: MT9M111 sensor detected
[   85.173029] input: sn9c20x as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/input/input5
[   85.173273] usbcore: registered new interface driver sn9c20x
[   86.001700] ppdev: user-space parallel port driver
[   86.119284] audit_printk_skb: 15 callbacks suppressed
[   86.119288] type=1400 audit(1331529790.651:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1763 comm="apparmor_parser"
[   86.119617] type=1400 audit(1331529790.651:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1763 comm="apparmor_parser"
[   89.296204] Adding 15998972k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:15998972k 

------ END DMESG RESULTS ------

6) Network configuration. lshw results below.

------ START LSHW RESULTS ------

  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:08:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:febfe000-febfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:1c:d7:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

------ END LSHW RESULTS ------

7) Scan for networks. iwlist results below.

------ START IWLIST RESULTS ------

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

------ END IWLIST RESULTS ------

8) Ubuntu version - 11.10

9) Kernel/architecture - 3.0.0-12-generic x86_64

10) Restarting the network (sudo /etc/init.d/networking restart). Results below,

------ START NETWORK RESTART RESULTS ------

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

------ END NETWORK RESTART RESULTS ------

---

### Post by sanderj on 2012-03-12
Can you connect a ethernet wire to your ethernet port? Because first thing to check is whether Ubuntu will install a proprietary driver itself.

---

### Post by SweetBearCub on 2012-03-12
> **sanderj said:**
> Can you connect a ethernet wire to your ethernet port? Because first thing to check is whether Ubuntu will install a proprietary driver itself.

No, I cannot.

---

### Post by sanderj on 2012-03-12
> **SweetBearCub said:**
> No, I cannot.

Too bad.

---

### Post by varunendra on 2012-03-14
> **SweetBearCub said:**
> Wireless Brand/Chipset - Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
..
*<snip>*
..
[   10.931489] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.931494] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.931497] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
This is a common problem and the solution is relatively easier. Below are three methods to get it working, try whichever suits you best.

The simplest way is to get the firmware from a "legal distribution point" as the page linked above in dmesg says, then extract it to the **/lib/firmware/b43** directory. Not sure about legality, but a link with instructions is given here by *praseodym*: [http://ubuntuforums.org/showthread.php?p=11760101](http://ubuntuforums.org/showthread.php?p=11760101)

Alternatively, if you can do a fresh install, the best method would be as *TBABill *has suggested here: [http://ubuntuforums.org/showthread.php?p=11728201](http://ubuntuforums.org/showthread.php?p=11728201)

If you don't want to reinstall, that's not a problem either. Simply follow this guide for "B43- No Internet access" method: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by SweetBearCub on 2012-03-15
> **varunendra said:**
> This is a common problem and the solution is relatively easier. Below are three methods to get it working, try whichever suits you best.

The simplest way is to get the firmware from a "legal distribution point" as the page linked above in dmesg says, then extract it to the **/lib/firmware/b43** directory. Not sure about legality, but a link with instructions is given here by *praseodym*: [http://ubuntuforums.org/showthread.php?p=11760101](http://ubuntuforums.org/showthread.php?p=11760101)

Alternatively, if you can do a fresh install, the best method would be as *TBABill *has suggested here: [http://ubuntuforums.org/showthread.php?p=11728201](http://ubuntuforums.org/showthread.php?p=11728201)

If you don't want to reinstall, that's not a problem either. Simply follow this guide for "B43- No Internet access" method: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Thanks, solution number 1 worked like a charm, though apparently, installing the proprietary Nvidia graphics driver hosed it, and I had to redo it. Wireless then came back.

Also, solution number 2 (use the LiveCD) is missing instructions. When I booted from the LiveCD and opened up the app where the restricted drivers would have been listed, the list was blank. It made references to using the terminal, but was not clear on what exactly to type into the terminal window.

---

### Post by varunendra on 2012-03-15
> **SweetBearCub said:**
> Also, solution number 2 (use the LiveCD) is missing instructions. When I booted from the LiveCD and opened up the app where the restricted drivers would have been listed, the list was blank. It made references to using the terminal, but was not clear on what exactly to type into the terminal window.
Sorry, it was my mistake. That solution was meant for STA (wl) driver while your card uses b43 driver. However, the first solution implemented just the manual extraction of firmware package which is common for both b43 and STA supported cards (the package contains all the relevant firmware versions), so it worked.

Anyway, glad you got it working. Hope you'll enjoy Ubuntu.

**_PS_:**
As a new user, you may wish to take a look at some backup tools like [clonezilla]("http://clonezilla.org/"), [remastersys]("http://www.geekconnection.org/remastersys/") and [AptOnCD]("http://aptoncd.sourceforge.net/") (aptoncd is included in default repositories). Once installed, remastersys may amaze you with what it does and how easily.

---

