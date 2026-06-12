---
title: "Can't enable wireless"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by matt_mccarron on 2011-12-14
should I start my own thread?  I seems we have the EXACT same problem

or can I jump in on this one?

```
Module                  Size  Used by
ath9k                 112711  0 
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
acer_wmi               23302  0 
binfmt_misc            17292  1 
uvcvideo               67271  0 
rts5139               279514  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73673  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              393459  4 ath9k,rt2800lib,rt2x00pci,rt2x00lib
serio_raw              12990  0 
cfg80211              172392  4 ath9k,ath,rt2x00lib,mac80211
k10temp                12990  0 
eeprom_93cx6           12653  1 rt2800pci
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_seq_midi           13132  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2642629  86 
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
wmi                    18744  1 acer_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
```

---

### Post by nothingspecial on 2011-12-14
> **matt_mccarron said:**
> should I start my own thread?  I seems we have the EXACT same problem

or can I jump in on this one?



I've moved your post to it's own thread. Please start a new thread for your own problem, and please do not post in multiple threads about the same problem. Thanks......

.....oh and when posting terminal output please use code tags. The easiest way to do this is to highlight the text then click the # in the formatting options at the top of the posting box. :)

---

### Post by matt_mccarron on 2011-12-14
like this?
```
Module                  Size  Used by
ath9k                 112711  0 
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
acer_wmi               23302  0 
binfmt_misc            17292  1 
uvcvideo               67271  0 
rts5139               279514  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73673  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              393459  4 ath9k,rt2800lib,rt2x00pci,rt2x00lib
serio_raw              12990  0 
cfg80211              172392  4 ath9k,ath,rt2x00lib,mac80211
k10temp                12990  0 
eeprom_93cx6           12653  1 rt2800pci
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_seq_midi           13132  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2642629  86 
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
wmi                    18744  1 acer_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci


```

---

### Post by nothingspecial on 2011-12-14
> **matt_mccarron said:**
> like this?
```
Module                  Size  Used by
ath9k                 112711  0 
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
acer_wmi               23302  0 
binfmt_misc            17292  1 
uvcvideo               67271  0 
rts5139               279514  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73673  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              393459  4 ath9k,rt2800lib,rt2x00pci,rt2x00lib
serio_raw              12990  0 
cfg80211              172392  4 ath9k,ath,rt2x00lib,mac80211
k10temp                12990  0 
eeprom_93cx6           12653  1 rt2800pci
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_seq_midi           13132  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2642629  86 
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
wmi                    18744  1 acer_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci


```

Yep :)

---

### Post by pastalavista on 2011-12-14
> **nothingspecial said:**
> I've moved your post to it's own thread. Please start a new thread for your own problem(Snip)...

I've seen lots of posts where people with the same problem posted and joined if to solve it together. I posted a possible solution to this problem on the original thread and now I'll need to post it here too. That seems rather inefficient to me.

@matt_mccarron see if this post helps: [http://ubuntuforums.org/showthread.php?t=1745317]("http://ubuntuforums.org/showthread.php?t=1745317")

---

### Post by matt_mccarron on 2011-12-14
ran these in terminal:

sudo ifconfig wlan0 down 
sudo rmmod -f ath9k 
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

got this:

sudo rmmod -f ath9k
ERROR: Removing 'ath9k': No such file or directory

still no wireless

---

### Post by matt_mccarron on 2011-12-14
I guess the honus is on me to search for problems that you've already solved... or start my own thread and hope that you will solve this one too?

Anyways, i think i need to clarify...  here's the info criteria suggested by the posting guidelines:

```

Lenovo Laptop B575

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b272 Chicony Electronics Co., Ltd
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp.
Bus 005 Device 002: ID 1c7a:0603 LighTuning Technology Inc.

eth0 Link encap:Ethernet HWaddr f0:de:f1:6f:85:e8
inet addr:192.168.2.15 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::f2de:f1ff:fe6f:85e8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5653 errors:0 dropped:0 overruns:0 frame:0
TX packets:3801 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4046247 (4.0 MB) TX bytes:607412 (607.4 KB)
Interrupt:42 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:48 errors:0 dropped:0 overruns:0 frame:0
TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4456 (4.4 KB) TX bytes:4456 (4.4 KB)

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Module Size Used by
bnep 17923 2
rfcomm 38408 0
bluetooth 148839 10 bnep,rfcomm
parport_pc 32114 0
ppdev 12849 0
binfmt_misc 17292 1
vesafb 13489 1
snd_hda_codec_conexant 52418 1
snd_hda_codec_hdmi 31426 1
snd_hda_intel 24262 2
snd_hda_codec 91754 3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_ intel
snd_hwdep 13276 1 snd_hda_codec
arc4 12473 2
rt2800pci 18340 0
rt2800lib 48909 1 rt2800pci
crc_ccitt 12595 1 rt2800lib
rt2x00pci 14202 1 rt2800pci
snd_pcm 80435 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00lib 48114 3 rt2800pci,rt2800lib,rt2x00pci
fglrx 2642629 94
snd_seq_midi 13132 0
snd_rawmidi 25241 1 snd_seq_midi
joydev 17393 0
mac80211 393459 3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211 172392 2 rt2x00lib,mac80211
rts5139 279514 0
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop 13575 0
acer_wmi 23302 0
lp 17455 0
uvcvideo 67271 0
videodev 85626 1 uvcvideo
sp5100_tco 13495 0
i2c_piix4 13093 0
snd_timer 28932 2 snd_pcm,snd_seq
psmouse 73673 0
eeprom_93cx6 12653 1 rt2800pci
serio_raw 12990 0
sparse_keymap 13658 2 ideapad_laptop,acer_wmi
video 18908 0
k10temp 12990 0
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
wmi 18744 1 acer_wmi
parport 40930 3 parport_pc,ppdev,lp
snd 55902 14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_ intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi, snd_seq,snd_timer,snd_seq_device
soundcore 12600 1 snd
snd_page_alloc 14115 2 snd_hda_intel,snd_pcm
r8169 43104 0
ahci 21634 2
libahci 25727 1 ahci

[ 1.284163] udevd[82]: starting version 173
[ 1.312144] usb 2-3: new high speed USB device number 2 using ehci_hcd
[ 1.436119] Refined TSC clocksource calibration: 1596.599 MHz.
[ 1.436132] Switching to clocksource tsc
[ 1.458439] ahci 0000:00:11.0: version 3.0
[ 1.458483] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 1.459153] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[ 1.459162] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio ccc sxs
[ 1.463476] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.463585] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.463647] r8169 0000:02:00.0: setting latency timer to 64
[ 1.463730] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[ 1.464608] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xf803e000, f0:de:f1:6f:85:e8, XID 0c200000 IRQ 42
[ 1.466303] scsi0 : ahci
[ 1.467552] scsi1 : ahci
[ 1.471595] scsi2 : ahci
[ 1.472348] ata1: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b100 irq 19
[ 1.472355] ata2: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b180 irq 19
[ 1.472361] ata3: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b200 irq 19
[ 1.576358] usb 2-5: new high speed USB device number 3 using ehci_hcd
[ 1.792415] ata3: SATA link down (SStatus 0 SControl 300)
[ 1.844329] usb 5-1: new full speed USB device number 2 using ohci_hcd
[ 1.964363] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.964405] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.966497] ata1.00: ATA-8: WDC WD3200BPVT-24ZEST0, 02.01A02, max UDMA/133
[ 1.966511] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[ 1.966597] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633F, LE02, max UDMA/33
[ 1.968106] ata1.00: configured for UDMA/133
[ 1.968773] scsi 0:0:0:0: Direct-Access ATA WDC WD3200BPVT-2 02.0 PQ: 0 ANSI: 5
[ 1.969098] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.969342] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 1.969348] sd 0:0:0:0: [sda] 4096-byte physical blocks
[ 1.970125] sd 0:0:0:0: [sda] Write Protect is off
[ 1.970135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.970500] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.971639] ata2.00: configured for UDMA/33
[ 1.979701] scsi 1:0:0:0: CD-ROM TSSTcorp CDDVDW TS-L633F LE02 PQ: 0 ANSI: 5
[ 1.989357] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.989366] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 1.989603] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.989720] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 2.033659] sda: sda1 sda2 < sda5 >
[ 2.034424] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.434283] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[ 4.850493] udevd[317]: starting version 173
[ 5.283091] Adding 3773436k swap on /dev/sda5. Priority:-1 extents:1 across:3773436k
[ 7.080638] wmi: Mapper loaded
[ 7.370879] acpi device:3d: registered as cooling_device2
[ 7.371239] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[ 7.371346] ACPI: Video Device [VGA1] (multi-head: yes rom: no post: no)
[ 7.545016] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[ 7.569299] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[ 7.569418] SP5100 TCO timer: mmio address 0xb80830 already in use
[ 7.600973] Linux video capture interface: v2.00
[ 7.613137] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b272)
[ 7.615817] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input6
[ 7.616788] usbcore: registered new interface driver uvcvideo
[ 7.616792] USB Video Class driver (v1.1.0)
[ 7.689605] lp: driver loaded but no devices found
[ 7.773585] acer_wmi: Acer Laptop ACPI-WMI Extras
[ 7.779156] input: Ideapad extra buttons as /devices/platform/ideapad/input/input7
[ 8.325496] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[ 8.327738] Initializing rts5139 USB card reader driver...
[ 8.335577] scsi3 : SCSI emulation for RTS5139 USB card reader
[ 8.336681] scsi 3:0:0:0: Direct-Access Generic- xD/SD/M.S. 1.00 PQ: 0 ANSI: 0 CCS
[ 8.336741] scsi: killing requests for dead queue
[ 8.337365] usbcore: registered new interface driver rts5139
[ 8.337370] Realtek rts5139 USB card reader support registered.
[ 8.352280] scsi: killing requests for dead queue
[ 8.358963] cfg80211: Calling CRDA to update world regulatory domain
[ 8.368208] scsi: killing requests for dead queue
[ 8.376312] scsi: killing requests for dead queue
[ 8.388278] scsi: killing requests for dead queue
[ 8.404288] scsi: killing requests for dead queue
[ 8.407500] type=1400 audit(1323808227.667:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=617 comm="apparmor_parser"
[ 8.407538] type=1400 audit(1323808227.667:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=491 comm="apparmor_parser"
[ 8.408272] type=1400 audit(1323808227.671:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[ 8.408305] type=1400 audit(1323808227.671:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=617 comm="apparmor_parser"
[ 8.408762] type=1400 audit(1323808227.671:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[ 8.408804] type=1400 audit(1323808227.671:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=617 comm="apparmor_parser"
[ 8.416237] scsi: killing requests for dead queue
[ 8.434009] scsi: killing requests for dead queue
[ 8.446343] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[ 8.448620] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 8.453770] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 8.510150] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[ 8.602232] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[ 8.602242] Disabling lock debugging due to kernel taint
[ 8.800861] [fglrx] Maximum main memory to use for locked dma buffers: 2746 MBytes.
[ 8.800945] [fglrx] vendor: 1002 device: 9802 count: 1
[ 8.801754] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[ 8.801782] pci 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 8.801791] pci 0000:00:01.0: setting latency timer to 64
[ 8.802555] [fglrx] Kernel PAT support is enabled
[ 8.802598] [fglrx] module loaded - fglrx 8.90.5 [Oct 12 2011] with 1 minors
[ 9.178166] rt2800pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 9.178184] rt2800pci 0000:03:00.0: setting latency timer to 64
[ 9.181334] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181340] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181344] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181349] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181353] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181358] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181362] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181367] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181371] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181375] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181379] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181384] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181388] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181393] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181397] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181402] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181405] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181410] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181414] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181419] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181423] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181428] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181432] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181436] cfg80211: 2457000 KHz - 2482000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181440] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181445] cfg80211: 2457000 KHz - 2482000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.181449] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 9.181454] cfg80211: 2474000 KHz - 2494000 KHz @ KHz), (600 mBi, 2000 mBm)
[ 9.215114] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 9.216149] Registered led device: rt2800pci-phy0::radio
[ 9.216181] Registered led device: rt2800pci-phy0::assoc
[ 9.216217] Registered led device: rt2800pci-phy0::quality
[ 9.466360] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 9.466442] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[ 9.466481] HDA Intel 0000:00:01.1: setting latency timer to 64
[ 9.754357] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[ 9.754768] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[ 9.755334] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 10.515377] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515386] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515391] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515396] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515400] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515405] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515409] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515414] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515417] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515422] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515426] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515431] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515435] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515439] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515443] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515448] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515452] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515456] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515460] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515465] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515469] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515473] cfg80211: 2402000 KHz - 2472000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515477] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515482] cfg80211: 2457000 KHz - 2482000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515486] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515491] cfg80211: 2457000 KHz - 2482000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515495] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 10.515499] cfg80211: 2474000 KHz - 2494000 KHz @ KHz), (300 mBi, 2000 mBm)
[ 10.515505] cfg80211: World regulatory domain updated:
[ 10.515508] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 10.515513] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 10.515518] cfg80211: (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 10.515523] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 10.515527] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 10.515532] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 11.186307] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 11.617743] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[ 11.617750] vesafb: scrolling: redraw
[ 11.617756] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[ 11.618547] vesafb: framebuffer at 0xd0000000, mapped to 0xf9600000, using 3072k, total 3072k
[ 11.618854] Console: switching to colour frame buffer device 128x48
[ 11.618900] fb0: VESA VGA frame buffer device
[ 14.499560] ppdev: user-space parallel port driver
[ 14.839817] type=1400 audit(1323808234.099:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[ 14.840649] type=1400 audit(1323808234.103:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[ 14.841148] type=1400 audit(1323808234.103:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[ 15.172794] type=1400 audit(1323808234.435:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=957 comm="apparmor_parser"
[ 15.385963] type=1400 audit(1323808234.647:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[ 15.386772] type=1400 audit(1323808234.647:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
[ 16.143781] r8169 0000:02:00.0: eth0: link down
[ 16.143797] r8169 0000:02:00.0: eth0: link down
[ 16.144495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 16.594357] type=1400 audit(1323808235.855:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=956 comm="apparmor_parser"
[ 16.595562] type=1400 audit(1323808235.855:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=956 comm="apparmor_parser"
[ 16.868729] type=1400 audit(1323808236.131:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=963 comm="apparmor_parser"
[ 16.869463] type=1400 audit(1323808236.131:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=963 comm="apparmor_parser"
[ 17.780896] r8169 0000:02:00.0: eth0: link up
[ 17.781227] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 26.673072] audit_printk_skb: 3 callbacks suppressed
[ 26.673079] type=1400 audit(1323808245.935:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=959 comm="apparmor_parser"
[ 26.675833] type=1400 audit(1323808245.935:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=959 comm="apparmor_parser"
[ 26.677896] type=1400 audit(1323808245.939:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=959 comm="apparmor_parser"
[ 27.198532] init: failsafe main process (889) killed by TERM signal
[ 27.351908] init: apport pre-start process (1062) terminated with status 1
[ 27.357168] init: apport post-stop process (1089) terminated with status 1
[ 28.208187] eth0: no IPv6 routers present
[ 30.650723] Bluetooth: Core ver 2.16
[ 30.650785] NET: Registered protocol family 31
[ 30.650788] Bluetooth: HCI device and connection manager initialized
[ 30.650793] Bluetooth: HCI socket layer initialized
[ 30.650797] Bluetooth: L2CAP socket layer initialized
[ 30.652301] Bluetooth: SCO socket layer initialized
[ 30.704083] Bluetooth: RFCOMM TTY layer initialized
[ 30.704093] Bluetooth: RFCOMM socket layer initialized
[ 30.704096] Bluetooth: RFCOMM ver 1.11
[ 30.709060] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 30.709066] Bluetooth: BNEP filters: protocol multicast
[ 30.730921] [fglrx] ATIF platform detected with notification ID: 0x81
[ 32.145704] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 32.203711] fglrx_pci 0000:00:01.0: irq 44 for MSI/MSI-X
[ 32.205048] [fglrx] Firegl kernel thread PID: 1214
[ 32.205357] [fglrx] Firegl kernel thread PID: 1215
[ 32.205666] [fglrx] Firegl kernel thread PID: 1216
[ 32.205910] [fglrx] IRQ 44 Enabled
[ 32.485037] [fglrx] Gart USWC size:904 M.
[ 32.485044] [fglrx] Gart cacheable size:357 M.
[ 32.485055] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[ 32.485059] [fglrx] Reserved FB block: Unshared offset:fd2b000, size:2d5000
[ 32.485064] [fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000
[ 43.361892] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10322.638118] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10326.300486] PM: Syncing filesystems ... done.
[10326.303314] PM: Preparing system for mem sleep
[10326.303345] Freezing user space processes ... (elapsed 0.01 seconds) done.
[10326.316338] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[10326.332346] PM: Entering mem sleep
[10326.332461] Suspending console(s) (use no_console_suspend to debug)
[10326.333175] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10326.412460] rt2800pci 0000:03:00.0: PCI INT A disabled
[10326.412512] ohci_hcd 0000:00:14.5: PCI INT C disabled
[10326.412630] ohci_hcd 0000:00:13.0: PCI INT A disabled
[10326.412651] ehci_hcd 0000:00:12.2: PCI INT B disabled
[10326.412664] ohci_hcd 0000:00:12.0: PCI INT A disabled
[10326.412835] [fglrx] IRQ 44 Disabled
[10326.412876] [fglrx] Preparing suspend fglrx in kernel.
[10326.428157] ehci_hcd 0000:00:13.2: PCI INT B disabled
[10326.517361] HDA Intel 0000:00:14.2: PCI INT A disabled
[10326.517457] HDA Intel 0000:00:01.1: PCI INT B disabled
[10326.517493] ACPI handle has no context!
[10326.519261] sd 0:0:0:0: [sda] Stopping disk
[10326.532024] PM: suspend of drv:HDA Intel dev:0000:00:01.1 complete after 119.321 msecs
[10326.532106] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 119.580 msecs
[10326.694301] [fglrx] Suspending fglrx in kernel completed.
[10326.694304] [fglrx] Power down the ASIC .
[10326.694432] PM: suspend of drv:fglrx_pci dev:0000:00:01.0 complete after 281.659 msecs
[10327.111435] PM: suspend of drv:sd dev:0:0:0:0 complete after 778.267 msecs
[10327.111466] PM: suspend of drv:scsi dev:target0:0:0 complete after 778.014 msecs
[10327.111485] PM: suspend of drv:scsi dev:host0 complete after 776.854 msecs
[10327.111742] ahci 0000:00:11.0: PCI INT A disabled
[10327.111752] PM: suspend of drv:ahci dev:0000:00:11.0 complete after 699.082 msecs
[10327.111774] PM: suspend of drv: dev:pci0000:00 complete after 683.633 msecs
[10327.111788] PM: suspend of devices complete after 778.982 msecs
[10327.111792] PM: suspend devices took 0.776 seconds
[10327.112143] r8169 0000:02:00.0: PME# enabled
[10327.112160] pcieport 0000:00:15.0: wake-up capability enabled by ACPI
[10327.160199] PM: late suspend of devices complete after 48.400 msecs
[10327.160243] ACPI: Preparing to enter system sleep state S3
[10327.220887] PM: Saving platform NVS memory
[10327.223407] Disabling non-boot CPUs ...
[10327.223882] Broke affinity for irq 17
[10327.224954] CPU 1 is now offline
[10327.225336] ACPI: Low-level resume complete
[10327.225336] PM: Restoring platform NVS memory
[10327.225336] Enabling non-boot CPUs ...
[10327.225336] Booting Node 0 Processor 1 APIC 0x1
[10327.225336] smpboot cpu 1: start_ip = 99000
[10327.224913] Initializing CPU#1
[10327.336819] CPU1 is up
[10327.337752] ACPI: Waking up from system sleep state S3
[10327.340026] Switched to NOHz mode on CPU #1
[10327.469914] power_supply BAT0: parent PNP0C0A:00 should not be sleeping
[10327.469948] HDA Intel 0000:00:01.1: restoring config space at offset 0xf (was 0x2ff, writing 0x205)
[10327.469966] HDA Intel 0000:00:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xe0244000)
[10327.469973] HDA Intel 0000:00:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x80000( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.470027] HDA Intel 0000:00:01.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[10327.484070] ehci_hcd 0000:00:12.2: BAR 0: set to [mem 0xe024b500-0xe024b5ff] (PCI address [0xe024b500-0xe024b5ff])
[10327.484108] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[10327.500065] ehci_hcd 0000:00:13.2: BAR 0: set to [mem 0xe024b400-0xe024b4ff] (PCI address [0xe024b400-0xe024b4ff])
[10327.500104] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[10327.500148] piix4_smbus 0000:00:14.0: restoring config space at offset 0x1 (was 0x2200403, writing 0x2200400)
[10327.500168] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[10327.500192] HDA Intel 0000:00:14.2: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[10327.500334] pcieport 0000:00:15.0: restoring config space at offset 0x3 (was 0x810000, writing 0x81000( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.500416] pcieport 0000:00:15.2: restoring config space at offset 0x3 (was 0x810000, writing 0x81000( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.500678] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[10327.500698] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xe000000c)
[10327.500708] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000400c)
[10327.500719] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x1001)
[10327.500727] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.500737] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[10327.500825] rt2800pci 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[10327.500853] rt2800pci 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xe0100000)
[10327.500861] rt2800pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x ( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.500871] rt2800pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[10327.501047] PM: early resume of devices complete after 31.239 msecs
[10327.501207] fglrx_pci 0000:00:01.0: setting latency timer to 64
[10327.501272] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[10327.501281] HDA Intel 0000:00:01.1: setting latency timer to 64
[10327.501335] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[10327.501426] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[10327.501502] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.503715] [fglrx] Power up the ASIC
[10327.503723] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[10327.503879] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.503889] [fglrx] Preparing resume fglrx in kernel.
[10327.503916] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[10327.503956] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[10327.503998] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[10327.504104] pcieport 0000:00:15.0: wake-up capability disabled by ACPI
[10327.504113] r8169 0000:02:00.0: PME# disabled
[10327.504468] rt2800pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.563054] [fglrx] Resuming fglrx in kernel completed.
[10327.563170] [fglrx] IRQ 44 Enabled
[10327.564326] sd 0:0:0:0: [sda] Starting disk
[10327.641183] PM: resume of drv:r8169 dev:0000:02:00.0 complete after 137.081 msecs
[10327.692396] PM: resume of drv:hub dev:2-0:1.0 complete after 129.141 msecs
[10327.692409] PM: resume of drv: dev:ep_00 complete after 129.097 msecs
[10327.692441] PM: resume of drv: dev:ep_81 complete after 129.178 msecs
[10327.828299] usb 5-1: reset full speed USB device number 2 using ohci_hcd
[10327.872359] ata3: SATA link down (SStatus 0 SControl 300)
[10327.991572] PM: resume of drv: dev:ep_00 complete after 418.474 msecs
[10327.991590] PM: resume of drv:usb dev:5-1:1.0 complete after 418.607 msecs
[10327.991713] PM: resume of drv: dev:ep_02 complete after 418.650 msecs
[10327.991731] PM: resume of drv: dev:ep_81 complete after 418.712 msecs
[10328.048205] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[10328.067751] ata2.00: configured for UDMA/33
[10328.096322] usb 2-5: reset high speed USB device number 3 using ehci_hcd
[10328.238110] PM: resume of drv: dev:ep_00 complete after 673.815 msecs
[10328.238130] PM: resume of drv:rts5139 dev:2-5:1.0 complete after 673.986 msecs
[10328.238166] PM: resume of drv: dev:ep_83 complete after 673.908 msecs
[10328.238176] PM: resume of drv: dev:ep_82 complete after 673.963 msecs
[10328.238184] PM: resume of drv: dev:ep_01 complete after 674.006 msecs
[10328.238193] PM: resume of drv:scsi dev:host3 complete after 665.068 msecs
[10328.238207] PM: resume of drv:scsi_host dev:host3 complete after 665.047 msecs
[10328.238215] PM: resume of drv:scsi dev:target3:0:0 complete after 665.020 msecs
[10328.238232] PM: resume of drv:sd dev:3:0:0:0 complete after 665.000 msecs
[10328.238243] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 664.977 msecs
[10328.340328] usb 2-3: reset high speed USB device number 2 using ehci_hcd
[10328.484384] PM: resume of drv: dev:ep_00 complete after 920.313 msecs
[10328.484403] PM: resume of drv:uvcvideo dev:2-3:1.1 complete after 920.416 msecs
[10328.484412] PM: resume of drv:uvcvideo dev:2-3:1.0 complete after 920.533 msecs
[10328.484535] PM: resume of drv: dev:ep_81 complete after 920.609 msecs
[10330.004342] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[10330.037158] ata1.00: configured for UDMA/133
[10330.064169] PM: resume of drv:sd dev:0:0:0:0 complete after 2499.839 msecs
[10330.064288] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2422.970 msecs
[10330.069012] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2496.118 msecs
[10330.069258] PM: resume of devices complete after 2568.130 msecs
[10330.069413] PM: resume devices took 2.568 seconds
[10330.069459] PM: Finishing wakeup.
[10330.069462] Restarting tasks ... done.
[10330.070600] video LNXVIDEO:01: Restoring backlight state
[10332.779796] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10332.979952] r8169 0000:02:00.0: eth0: link down
[10332.979976] r8169 0000:02:00.0: eth0: link down
[10332.980744] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10334.625939] r8169 0000:02:00.0: eth0: link up
[10334.626668] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[10345.472264] eth0: no IPv6 routers present
[10395.581162] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[10398.821278] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10404.925346] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10406.729286] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10408.158645] r8169 0000:02:00.0: eth0: link down
[10418.889924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10435.263930] r8169 0000:02:00.0: eth0: link down
[10435.264366] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10444.357271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10458.895876] r8169 0000:02:00.0: eth0: link up
[10458.896554] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[10469.008262] eth0: no IPv6 routers present
[10599.509635] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 06
serial: f0:de:f1:6f:85:e8
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.2.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:42 ioport:1000(size=256) memory:e0004000-e0004fff memory:e0000000-e0003fff
*-network DISABLED
description: Wireless interface
product: RT3090 Wireless 802.11n 1T/1R PCIe
vendor: Ralink corp.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: cc:af:78:40:61:cc
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-14-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:18 memory:e0100000-e010ffff

iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wlan0 Failed to read scan data : Network is down

ubuntu version: ubuntu 11.10

uname -mr
3.0.0-14-generic i686

sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces...

```

If you tell me that thread is the way, well, i've tried and gotten no results... I can try again... i didn't do anything in terminal with commands that included the word "acer" only ath9k...
very green at terminal... ubuntu in general...

---

### Post by pastalavista on 2011-12-14
> **matt_mccarron said:**
> 
If you tell me that thread is the way, well, i've tried and gotten no results... I can try again... i didn't do anything in terminal with commands that included the word "acer" only ath9k...
very green at terminal... ubuntu in general...

The part you missed was removing the acer-wmi module and unblocking the rfkill. Try this in terminal```
sudo rmmod -f acer-wmi
sudo modprobe ath9k
sudo rfkill unblock all
``` You'll also need to blacklist the acer-wmi mod from loading on restart```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
```Then```
gksu gedit /etc/rc.local
```
Add one line above Exit 0 

```
rfkill unblock all
```
Proofread, save and close gedit.

exit

---

### Post by matt_mccarron on 2011-12-14
ok,

done, but that didn't work either...

perhaps you can be very specific with me.  like do I need to add a # before rfkill etc. in gedit?
sudo su (and hit enter)
then enter the next line separately?

anyways at the end of that I tried the wireless and now the "Enable Wireless" option is no longer highlight-able... just grey and unselectable

---

### Post by matt_mccarron on 2011-12-14
oh, and I did all this with the wired internet disconnected...
thought i read that somewhere...

---

### Post by nothingspecial on 2011-12-14
> **matt_mccarron said:**
> 

perhaps you can be very specific with me.  like do I need to add a # before rfkill etc. in gedit?

Nope.
> **matt_mccarron said:**
> sudo su (and hit enter)
then enter the next line separately?



Yep

---

### Post by nothingspecial on 2011-12-14
Read the last part of pastalavista's instructions again. There was a formatting problem that has been corrected.

---

### Post by matt_mccarron on 2011-12-14
scratch that!
reboot got 'er goin'!

Pastalavista!  you are a scholar and cyber philanthropist...

thank you very very much for your time!  if you ever find yourself in northern New Brunswick Canada, i'll buy you 3 beers.

Cheers:P

---

### Post by matt_mccarron on 2011-12-14
@Nothingspecial

Thanks to you too, I appreciate the warm welcome and all your assistance.

Incidentally, I DID indeed add a hash mark(#) before the entry in gedit.  Does that matter, or should I go back in there and remove it?

Thanks again, I LOVE THIS COMMUNITY!!!!  UBUNTU RULESZ!!!!:KS:KS:KS:KS:KS

---

