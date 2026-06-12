---
title: "[SOLVED] Puzzled by trying to setup wireless"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Geoffzx6r on 2009-01-05
Hi I'm trying to setup the wireless on my notebook. It's a toshiba with atheros wireless. I went to system/ admin/ hardware drivers. It says I have support for atheros wireless LAN cards and it says it's activated. I typed iwconfig in terminal. It just says "no wireless extensions." for lo, eth0, and pan0. Not sure what I need to do to get wireless to work.

---

### Post by HuaiDan on 2009-01-05
there's the backports fix, sudo apt-get install linux-modules-backports or something like that, search for it, it works for most people. Didn't quite work for me.

---

### Post by superprash2003 on 2009-01-05
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by Ubayd on 2009-01-05
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

Wow! Thank you so much! I found this post while searching on the forum. I had to use the blacklist by the way, even though this is my first Ubuntu install (and first Linux install for that matter). Really loving this system, and I just have 2-3 bits of inbuilt hardware left to enable on my laptop... great! :)

---

### Post by Geoffzx6r on 2009-01-05
Sorry guys I didn't read the sticky for posting in this section

I found out specifically what wireless I'm using. It's an atheros  AR242x. I'm running the latest version of ubuntu from a 1 gig kingston flash drive.

here's what iwconfig gave me
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

Here's a check for modules
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
powernow_k8            22148  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
joydev                 18368  0 
pcmcia                 43052  0 
video                  25104  0 
snd_hda_intel         381488  3 
output                 11008  1 video
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
battery                18436  0 
sdhci_pci              15360  0 
ac                     12292  0 
sdhci                  23940  1 sdhci_pci
psmouse                45200  0 
tifm_7xx1              13824  0 
tifm_core              16028  1 tifm_7xx1
mmc_core               58268  1 sdhci
serio_raw              13444  0 
evdev                  17696  12 
pcspkr                 10624  0 
button                 14224  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy          10884  0 
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
i2c_piix4              16144  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
k8temp                 12416  0 
i2c_core               31892  1 i2c_piix4
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
squashfs               46600  1 
loop                   23180  2 
aufs                  169892  1 
exportfs               12544  1 aufs
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
libusual               27156  1 usb_storage
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_atiixp            12800  0 
pata_acpi              12160  0 
ohci1394               37936  0 
ieee1394               96324  1 ohci1394
ata_generic            12932  0 
ahci                   37132  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
libata                177312  4 pata_atiixp,pata_acpi,ata_generic,ahci
r8169                  35972  0 
usbcore               148848  6 usb_storage,libusual,ehci_hcd,ohci_hcd
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

Kernel boot message
```
[    0.729666] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.729666] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.729666] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.729666] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.729666] pnp 00:08: io resource (0x87f-0x87f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.729666] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling
[    0.756283] pnp: PnP ACPI: found 11 devices
[    0.756286] ACPI: ACPI bus type pnp unregistered
[    0.756290] PnPBIOS: Disabled by ACPI PNP
[    0.760064] PCI: Using ACPI for IRQ routing
[    0.760064] pci 0000:00:05.0: BAR 7: can't allocate resource
[    0.760064] pci 0000:00:05.0: BAR 8: can't allocate resource
[    0.764043] NET: Registered protocol family 8
[    0.764046] NET: Registered protocol family 20
[    0.768041] NetLabel: Initializing
[    0.768041] NetLabel:  domain hash size = 128
[    0.768042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.768059] NetLabel:  unlabeled traffic allowed by default
[    0.768071] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.768077] hpet0: 4 32-bit timers, 14318180 Hz
[    0.769784] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.769788]    actual entries 65620
[    0.769927] AppArmor: AppArmor Filesystem Enabled
[    0.769957] ACPI: RTC can wake from S4
[    0.772054] Switched to high resolution mode on CPU 0
[    0.772066] Switched to high resolution mode on CPU 1
[    0.772100] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.772105] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.772118] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.772124] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.772128] system 00:08: ioport range 0xfd60-0xfddf has been reserved
[    0.772137] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.807667] pci 0000:00:14.4: BAR 9: can't allocate mem resource [0x0-0x3ffffff]
[    0.807673] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.807677] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.807682] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    0.807686] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.807692] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.807695] pci 0000:00:05.0:   IO window: disabled
[    0.807699] pci 0000:00:05.0:   MEM window: disabled
[    0.807703] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.807708] pci 0000:00:06.0: PCI bridge, secondary bus 0000:0e
[    0.807712] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    0.807717] pci 0000:00:06.0:   MEM window: 0xf8300000-0xf83fffff
[    0.807721] pci 0000:00:06.0:   PREFETCH window: 0x000000f8500000-0x000000f85fffff
[    0.807726] pci 0000:00:07.0: PCI bridge, secondary bus 0000:14
[    0.807729] pci 0000:00:07.0:   IO window: disabled
[    0.807733] pci 0000:00:07.0:   MEM window: 0xf8200000-0xf82fffff
[    0.807737] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.807744] pci 0000:1a:04.0: BAR 9: can't allocate mem resource [0x0-0x3ffffff]
[    0.807749] pci 0000:1a:04.0: BAR 10: can't allocate mem resource [0x0-0x3ffffff]
[    0.807753] pci 0000:1a:04.0: CardBus bridge, secondary bus 0000:1b
[    0.807757] pci 0000:1a:04.0:   IO window: 0x002000-0x0020ff
[    0.807766] pci 0000:1a:04.0:   IO window: 0x002400-0x0024ff
[    0.807773] pci 0000:00:14.4: PCI bridge, secondary bus 0000:1a
[    0.807777] pci 0000:00:14.4:   IO window: 0x2000-0x2fff
[    0.807784] pci 0000:00:14.4:   MEM window: 0xf8400000-0xf84fffff
[    0.807789] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.807807] pci 0000:00:05.0: setting latency timer to 64
[    0.807813] pci 0000:00:06.0: setting latency timer to 64
[    0.807820] pci 0000:00:07.0: setting latency timer to 64
[    0.807841] pci 0000:1a:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.807849] bus: 00 index 0 io port: [0, ffff]
[    0.807852] bus: 00 index 1 mmio: [0, ffffffff]
[    0.807855] bus: 01 index 0 io port: [9000, 9fff]
[    0.807858] bus: 01 index 1 mmio: [f8000000, f81fffff]
[    0.807861] bus: 01 index 2 mmio: [f0000000, f7ffffff]
[    0.807863] bus: 01 index 3 mmio: [0, 0]
[    0.807866] bus: 08 index 0 mmio: [0, fff]
[    0.807869] bus: 08 index 1 mmio: [0, fffff]
[    0.807871] bus: 08 index 2 mmio: [0, 0]
[    0.807874] bus: 08 index 3 mmio: [0, 0]
[    0.807876] bus: 0e index 0 io port: [a000, afff]
[    0.807879] bus: 0e index 1 mmio: [f8300000, f83fffff]
[    0.807883] bus: 0e index 2 mmio: [f8500000, f85fffff]
[    0.807885] bus: 0e index 3 mmio: [0, 0]
[    0.807888] bus: 14 index 0 mmio: [0, 0]
[    0.807891] bus: 14 index 1 mmio: [f8200000, f82fffff]
[    0.807894] bus: 14 index 2 mmio: [0, 0]
[    0.807896] bus: 14 index 3 mmio: [0, 0]
[    0.807899] bus: 1a index 0 io port: [2000, 2fff]
[    0.807902] bus: 1a index 1 mmio: [f8400000, f84fffff]
[    0.807905] bus: 1a index 2 mmio: [0, 0]
[    0.807908] bus: 1a index 3 io port: [0, ffff]
[    0.807910] bus: 1a index 4 mmio: [0, ffffffff]
[    0.807913] bus: 1b index 0 io port: [2000, 20ff]
[    0.807916] bus: 1b index 1 io port: [2400, 24ff]
[    0.807919] bus: 1b index 2 mmio: [0, 0]
[    0.807921] bus: 1b index 3 mmio: [0, 0]
[    0.807935] NET: Registered protocol family 2
[    0.817089] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.817427] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.818079] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.818422] TCP: Hash tables configured (established 131072 bind 65536)
[    0.818426] TCP reno registered
[    0.821123] NET: Registered protocol family 1
[    0.821271] checking if image is initramfs... it is
[    1.360024] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.724885] Freeing initrd memory: 8250k freed
[    1.726630] audit: initializing netlink socket (disabled)
[    1.726647] type=2000 audit(1231163113.724:1): initialized
[    1.734244] highmem bounce pool size: 64 pages
[    1.734251] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.737916] VFS: Disk quotas dquot_6.5.1
[    1.738044] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.738187] msgmni has been set to 1719
[    1.738350] io scheduler noop registered
[    1.738353] io scheduler anticipatory registered
[    1.738356] io scheduler deadline registered
[    1.738371] io scheduler cfq registered (default)
[    1.738482] pci 0000:01:05.0: Boot video device
[    1.738656] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.738683] pcieport-driver 0000:00:05.0: found MSI capability
[    1.738713] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.738788] pci_express 0000:00:05.0:pcie02: allocate port service
[    1.738854] pci_express 0000:00:05.0:pcie03: allocate port service
[    1.738955] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.738981] pcieport-driver 0000:00:06.0: found MSI capability
[    1.739008] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.739075] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.739177] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.739203] pcieport-driver 0000:00:07.0: found MSI capability
[    1.739228] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.739299] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.739796] isapnp: Scanning for PnP cards...
[    2.096296] isapnp: No Plug & Play device found
[    2.149387] hpet_resources: 0xfed00000 is busy
[    2.149488] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.152754] brd: module loaded
[    2.152851] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.153024] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.184833] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.184841] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.185270] mice: PS/2 mouse device common for all mice
[    2.185458] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.185487] rtc0: alarms up to one month, hpet irqs
[    2.185650] EISA: Probing bus 0 at eisa.0
[    2.185658] Cannot allocate resource for EISA slot 1
[    2.185661] Cannot allocate resource for EISA slot 2
[    2.185684] Cannot allocate resource for EISA slot 8
[    2.185686] EISA: Detected 0 cards.
[    2.185690] cpuidle: using governor ladder
[    2.185694] cpuidle: using governor menu
[    2.186293] TCP cubic registered
[    2.186321] Using IPI No-Shortcut mode
[    2.186562] registered taskstats version 1
[    2.186729]   Magic number: 9:955:785
[    2.186823] tty ptyq7: hash matches
[    2.186906] rtc_cmos 00:04: setting system clock to 2009-01-05 13:45:16 UTC (1231163116)
[    2.186910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.186912] EDD information not available.
[    2.187221] Freeing unused kernel memory: 424k freed
[    2.187304] Write protecting the kernel text: 2576k
[    2.187359] Write protecting the kernel read-only data: 936k
[    2.206688] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.387813] fuse init (API version 7.9)
[    2.557693] ACPI: processor limited to max C-state 1
[    2.557819] processor ACPI0007:00: registered as cooling_device0
[    2.557826] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.557940] processor ACPI0007:01: registered as cooling_device1
[    2.955486] No dock devices found.
[    2.987316] SCSI subsystem initialized
[    3.003115] usbcore: registered new interface driver usbfs
[    3.003186] usbcore: registered new interface driver hub
[    3.003219] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.003241] r8169 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.003260] r8169 0000:0e:00.0: setting latency timer to 64
[    3.003673] eth0: RTL8101e at 0xf8874000, 00:1b:38:1c:c0:71, XID 34000000 IRQ 220
[    3.039088] usbcore: registered new device driver usb
[    3.092447] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.092485] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.092500] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.092551] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.092581] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8704000
[    3.098340] libata version 3.00 loaded.
[    3.148223] usb usb1: configuration #1 chosen from 1 choice
[    3.148259] hub 1-0:1.0: USB hub found
[    3.148276] hub 1-0:1.0: 2 ports detected
[    3.356481] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.356499] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.356531] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.356561] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8705000
[    3.412266] usb usb2: configuration #1 chosen from 1 choice
[    3.412303] hub 2-0:1.0: USB hub found
[    3.412320] hub 2-0:1.0: 2 ports detected
[    3.493106] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.516301] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.516319] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.516348] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.516374] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8706000
[    3.572236] usb usb3: configuration #1 chosen from 1 choice
[    3.572272] hub 3-0:1.0: USB hub found
[    3.572289] hub 3-0:1.0: 2 ports detected
[    3.669223] usb 1-1: configuration #1 chosen from 3 choices
[    3.676243] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.676259] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    3.676288] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    3.676306] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8707000
[    3.732169] usb usb4: configuration #1 chosen from 1 choice
[    3.732202] hub 4-0:1.0: USB hub found
[    3.732214] hub 4-0:1.0: 2 ports detected
[    3.812034] usb 1-2: new full speed USB device using ohci_hcd and address 3
[    3.840210] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.840223] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    3.840250] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    3.840265] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8708000
[    3.896221] usb usb5: configuration #1 chosen from 1 choice
[    3.896271] hub 5-0:1.0: USB hub found
[    3.896288] hub 5-0:1.0: 2 ports detected
[    3.987514] usb 1-2: configuration #1 chosen from 1 choice
[    4.000283] ahci 0000:00:12.0: version 3.0
[    4.000302] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.000326] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    4.000421] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.000425] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    4.000824] scsi0 : ahci
[    4.000970] scsi1 : ahci
[    4.001064] scsi2 : ahci
[    4.001166] scsi3 : ahci
[    4.001303] ata1: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709100 irq 22
[    4.001307] ata2: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709180 irq 22
[    4.001312] ata3: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709200 irq 22
[    4.001317] ata4: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709280 irq 22
[    4.484035] ata1: softreset failed (device not ready)
[    4.484041] ata1: failed due to HW bug, retry pmp=0
[    4.648046] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.648597] ata1.00: ATA-8: FUJITSU MHW2160BH PL, 0040001D, max UDMA/100
[    4.648602] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.648614] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.649288] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.649292] ata1.00: configured for UDMA/100
[    4.984052] ata2: SATA link down (SStatus 0 SControl 300)
[    5.320048] ata3: SATA link down (SStatus 0 SControl 300)
[    5.656048] ata4: SATA link down (SStatus 0 SControl 300)
[    5.672169] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 0040 PQ: 0 ANSI: 5
[    5.672500] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.672517] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    5.672553] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    5.672596] ehci_hcd 0000:00:13.5: debug port 1
[    5.672619] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8709400
[    5.684040] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.684203] usb usb6: configuration #1 chosen from 1 choice
[    5.684238] hub 6-0:1.0: USB hub found
[    5.684248] hub 6-0:1.0: 10 ports detected
[    5.856057] usb 1-1: USB disconnect, address 2
[    5.899141] ohci1394 0000:1a:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.899328] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.899378] pata_acpi 0000:00:14.1: setting latency timer to 64
[    5.949457] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8406000-f84067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.954224] scsi4 : pata_atiixp
[    5.954324] scsi5 : pata_atiixp
[    5.955441] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    5.955445] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    5.963282] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.984133] usb 1-2: USB disconnect, address 3
[    6.013803] Driver 'sd' needs updating - please use bus_type methods
[    6.013951] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.013981] sd 0:0:0:0: [sda] Write Protect is off
[    6.013985] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.014032] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.014126] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.014152] sd 0:0:0:0: [sda] Write Protect is off
[    6.014155] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.014203] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.014209]  sda:<6>ata5.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
[    6.132480] ata5.00: configured for UDMA/33
[    6.224041] usb 6-1: new high speed USB device using ehci_hcd and address 2
[    6.290926] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
[    6.291116] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    6.310779] Driver 'sr' needs updating - please use bus_type methods
[    6.351595]  sda1 sda2 sda3 <<6>usb 6-1: configuration #1 chosen from 3 choices
[    6.407654]  sda5 >
[    6.407869] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.412970] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.412976] Uniform CD-ROM driver Revision: 3.20
[    6.413082] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.480045] usb 6-2: new high speed USB device using ehci_hcd and address 3
[    6.621184] usb 6-2: configuration #1 chosen from 1 choice
[    6.621608] usbcore: registered new interface driver libusual
[    6.639985] Initializing USB Mass Storage driver...
[    6.640118] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.640235] usbcore: registered new interface driver usb-storage
[    6.640240] USB Mass Storage support registered.
[    6.640396] usb-storage: device found at 3
[    6.640399] usb-storage: waiting for device to settle before scanning
[    7.220718] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f77c04122e2]
[   11.640384] usb-storage: device scan complete
[   11.641357] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   11.646289] sd 6:0:0:0: [sdb] 1970176 512-byte hardware sectors (1009 MB)
[   11.646844] sd 6:0:0:0: [sdb] Write Protect is off
[   11.646848] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   11.646852] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.648712] sd 6:0:0:0: [sdb] 1970176 512-byte hardware sectors (1009 MB)
[   11.649211] sd 6:0:0:0: [sdb] Write Protect is off
[   11.649215] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   11.649217] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.649222]  sdb: sdb1
[   11.651200] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.651345] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   13.961280] aufs 20080922
[   13.969941] loop: module loaded
[   14.033739] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   14.085012] APIC error on CPU1: 00(40)
[   14.085018] APIC error on CPU0: 00(40)
[   55.675136] udevd version 124 started
[   56.588553] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.668103] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.916751] Linux agpgart interface v0.103
[   57.452658] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   58.141710] ath_hal: module license 'Proprietary' taints kernel.
[   58.172149] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   58.195981] wlan: 0.9.4
[   58.211654] ath_pci: 0.9.4
[   58.211707] ath_pci 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   58.211718] ath_pci 0000:14:00.0: setting latency timer to 64
[   58.236128] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   58.236154] ath_pci 0000:14:00.0: PCI INT A disabled
[   58.827836] Yenta: CardBus bridge found at 0000:1a:04.0 [1179:ff00]
[   58.827871] yenta_cardbus 0000:1a:04.0: CardBus bridge, secondary bus 0000:1b
[   58.827875] yenta_cardbus 0000:1a:04.0:   IO window: 0x002000-0x0020ff
[   58.827882] yenta_cardbus 0000:1a:04.0:   IO window: 0x002400-0x0024ff
[   58.827889] yenta_cardbus 0000:1a:04.0:   PREFETCH window: 0xf8800000-0xf8bfffff
[   58.827896] yenta_cardbus 0000:1a:04.0:   MEM window: 0xf8c00000-0xf8ffffff
[   58.827905] Yenta: Enabling burst memory read transactions
[   58.827911] Yenta: Using CSCINT to route CSC interrupts to PCI
[   58.827914] Yenta: Routing CardBus interrupts to PCI
[   58.827921] Yenta TI: socket 0000:1a:04.0, mfunc 0x10a01b22, devctl 0x64
[   58.837081] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   58.853170] ACPI: Power Button (FF) [PWRF]
[   58.853261] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   58.853363] ACPI: Lid Switch [LID]
[   58.853422] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   58.869999] ACPI: Power Button (CM) [PWRB]
[   58.915827] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   59.060789] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[   59.060794] Socket status: 30000006
[   59.060798] Yenta: Raising subordinate bus# of parent bus (#1a) from #1b to #1e
[   59.060806] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   59.060810] cs: IO port probe 0x2000-0x2fff: clean.
[   59.061034] pcmcia: parent PCI bridge Memory window: 0xf8400000 - 0xf84fffff
[   59.493055] tifm_7xx1 0000:1a:04.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   59.506681] sdhci: Secure Digital Host Controller Interface driver
[   59.506686] sdhci: Copyright(c) Pierre Ossman
[   59.519768] sdhci-pci 0000:1a:04.3: SDHCI controller found [104c:803c] (rev 0)
[   59.519788] sdhci-pci 0000:1a:04.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   59.519875] mmc0: SDHCI controller on PCI [0000:1a:04.3] using DMA
[   59.567357] ACPI: AC Adapter [ACAD] (on-line)
[   60.101161] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[   60.180056] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   60.258260] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   60.301373] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   60.397227] acpi device:04: registered as cooling_device2
[   60.397567] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input8
[   60.429290] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   60.465151] ACPI: Battery Slot [BAT1] (battery present)
[   60.466013] proc_dir_entry 'video/VGA' already registered
[   60.466020] Pid: 6323, comm: modprobe Tainted: P          2.6.27-7-generic #1
[   60.466024]  [<c037c3f6>] ? printk+0x1d/0x1f
[   60.466034]  [<c01f3eb2>] proc_register+0x1a2/0x1d0
[   60.466042]  [<c01f40c8>] proc_mkdir_mode+0x38/0x50
[   60.466047]  [<c01f40f4>] proc_mkdir+0x14/0x20
[   60.466051]  [<f8cb1d04>] acpi_video_bus_add_fs+0x29/0x163 [video]
[   60.466074]  [<f8cb2da6>] acpi_video_bus_add+0xd2/0x298 [video]
[   60.466083]  [<c0290a06>] acpi_device_probe+0x47/0x89
[   60.466091]  [<c02c3cb9>] really_probe+0x59/0x190
[   60.466096]  [<c028fd65>] ? acpi_match_device_ids+0x51/0x75
[   60.466105]  [<c02c3e33>] driver_probe_device+0x43/0x60
[   60.466110]  [<c02c3ec9>] __driver_attach+0x79/0x80
[   60.466115]  [<c02c3593>] bus_for_each_dev+0x53/0x80
[   60.466119]  [<c0290958>] ? acpi_device_remove+0x0/0x67
[   60.466126]  [<c02c3b6e>] driver_attach+0x1e/0x20
[   60.466130]  [<c02c3e50>] ? __driver_attach+0x0/0x80
[   60.466134]  [<c02c2f37>] bus_add_driver+0x1b7/0x230
[   60.466140]  [<c0290958>] ? acpi_device_remove+0x0/0x67
[   60.466144]  [<c02c409e>] driver_register+0x6e/0x150
[   60.466149]  [<f89db000>] ? acpi_video_init+0x0/0x56 [video]
[   60.466156]  [<c01f40c8>] ? proc_mkdir_mode+0x38/0x50
[   60.466162]  [<f89db000>] ? acpi_video_init+0x0/0x56 [video]
[   60.466168]  [<c0290cfe>] acpi_bus_register_driver+0x3f/0x41
[   60.466172]  [<f89db037>] acpi_video_init+0x37/0x56 [video]
[   60.466178]  [<c0101120>] _stext+0x30/0x160
[   60.466182]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[   60.466192]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[   60.466203]  [<c015c208>] sys_init_module+0x88/0x1b0
[   60.466209]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[   60.466214]  =======================
[   60.522661] acpi device:29: registered as cooling_device3
[   60.522924] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:26/device:27/input/input9
[   60.561200] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   60.867393] cs: IO port probe 0x100-0x3af: clean.
[   60.875159] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   60.881980] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   60.883274] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   60.885592] cs: IO port probe 0xa00-0xaff: clean.
[   62.802801] ip_tables: (C) 2000-2006 Netfilter Core Team
[   63.913750] ACPI: WMI: Mapper loaded
[   64.447291] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (2 cpu cores) (version 2.20.00)
[   64.447352] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[   64.447357] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   65.079829] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   65.137345] apm: BIOS not found.
[   65.261907] lp: driver loaded but no devices found
[   65.303886] ppdev: user-space parallel port driver
[   67.460756] Bluetooth: Core ver 2.13
[   67.463027] NET: Registered protocol family 31
[   67.463040] Bluetooth: HCI device and connection manager initialized
[   67.463052] Bluetooth: HCI socket layer initialized
[   67.501032] Clocksource tsc unstable (delta = -101042757 ns)
[   67.506861] Bluetooth: L2CAP ver 2.11
[   67.506877] Bluetooth: L2CAP socket layer initialized
[   67.554398] Bluetooth: SCO (Voice Link) ver 0.6
[   67.554413] Bluetooth: SCO socket layer initialized
[   67.621225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   67.621241] Bluetooth: BNEP filters: protocol multicast
[   67.669104] Bridge firewalling registered
[   67.669474] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   67.801506] Bluetooth: RFCOMM socket layer initialized
[   67.801547] Bluetooth: RFCOMM TTY layer initialized
[   67.801553] Bluetooth: RFCOMM ver 1.10
[   70.534219] pci 0000:01:05.0: power state changed by ACPI to D0
[   70.534259] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   70.952974] [drm] Initialized drm 1.1.0 20060810
[   70.978003] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   71.585706] [drm] Setting GART location based on new memory map
[   71.587476] [drm] Loading RS690 Microcode
[   71.587510] [drm] Num pipes: 1
[   71.587521] [drm] writeback test succeeded in 1 usecs
[   72.109341] r8169: eth0: link down
[   74.542936] hda-intel: Invalid position buffer, using LPIB read method instead.
[   97.600303] CPU0 attaching NULL sched-domain.
[   97.600326] CPU1 attaching NULL sched-domain.
[   97.620104] CPU0 attaching sched-domain:
[   97.620114]  domain 0: span 0-1 level CPU
[   97.620118]   groups: 0 1
[   97.620125] CPU1 attaching sched-domain:
[   97.620129]  domain 0: span 0-1 level CPU
[   97.620132]   groups: 1 0
[  124.281130] r8169: eth0: link down
[  207.400086] r8169: eth0: link up
[  207.526971] NET: Registered protocol family 17
[  235.510876] NET: Registered protocol family 10
[  235.512678] lo: Disabled Privacy Extensions
[  245.953042] eth0: no IPv6 routers present
[  806.788022] APIC error on CPU0: 40(40)
[  806.788039] APIC error on CPU1: 40(40)
[  933.081019] APIC error on CPU0: 40(40)
[  933.081035] APIC error on CPU1: 40(40)
ubuntu@ubuntu:~$ 


```

Network configuration

```
ubuntu@ubuntu:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1c:c0:71
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:d2:70:b2:c4:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

scan for networks
```
ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

ubuntu version 8.10

kernel
```
ubuntu@ubuntu:~$ uname -mr
2.6.27-7-generic i686

```

There I think I've listed everything.

---

### Post by Geoffzx6r on 2009-01-06
Alright I tried out this guide to fixing my wireless
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Here's what iwconfig gives me now

```
geoffrey@geoffrey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by superprash2003 on 2009-01-06
post outpt of iwlist scanning

---

### Post by Geoffzx6r on 2009-01-06
```
geoffrey@geoffrey-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
geoffrey@geoffrey-laptop:~$ 
```

I'm officially getting internet now. It was acting real funny when I first followed the guide. For about an hour or so after rebooting it was still acting like I didn't have wifi and then all of a sudden it found networks but I couldn't connect to my home network. I was having trouble with the security. I disabled the security settings and today when I turned on the computer it was able to connect.

I don't want to leave my network unsecured so I'm going to have to figure this out. I'll post some spec about my router soon.

---

### Post by theinnercityhippy on 2009-01-06
> **Geoffzx6r said:**
> ```
geoffrey@geoffrey-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
geoffrey@geoffrey-laptop:~$ 
```

I'm officially getting internet now. It was acting real funny when I first followed the guide. For about an hour or so after rebooting it was still acting like I didn't have wifi and then all of a sudden it found networks but I couldn't connect to my home network. I was having trouble with the security. I disabled the security settings and today when I turned on the computer it was able to connect.

I don't want to leave my network unsecured so I'm going to have to figure this out. I'll post some spec about my router soon.


You need to do the following I think

$> sudo apt-get install wpa-supplicant


Let me know how you get on, will help you further if this doesn't work

-JimDog*-

---

### Post by Geoffzx6r on 2009-01-06
my router is using wep encryption though.

the router says it's using 64/40bit encryption when it's on. I'm confused though, because when I go into edit it doesn't show an option for 64 bit encryption

---

### Post by Geoffzx6r on 2009-01-06
my router is using wep encryption though.

the router says it's using 64/40bit encryption when it's on. I'm confused though, because when I go into ubuntu to edit connection it doesn't show an option for 64 bit encryption.

---

### Post by bronxbomberz41 on 2009-01-06
thanks for the info!! works great now!

---

### Post by superprash2003 on 2009-01-07
please mark thread as SOLVED under thread tools

---

### Post by Geoffzx6r on 2009-01-07
Sorry but my problem isn't completely solved. I'm still having problems with wireless security

---

### Post by Favux on 2009-01-07
Hi Geoffzx6r,

Is it WEP-TKIP by any chance?  You're sure it's WEP and not WPA?  Anyway this workaround may not apply to you.  A bunch of us have found it gets us connected with wireless security through NM 0.7 to our router.  See:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Hope this is useful.

Edit:  Sorry, corrected link.

---

### Post by Geoffzx6r on 2009-01-08
Hi, I clicked your link and it attemted to let me reply to a thread. I think you gave me the wrong link by mistake. I'm fairly sure it's wep. The router has an option for wpa but it's definitely set at 64/40 bit wep encryption. I have a feeling I just don't understand how to setup a connection with the router under ubuntu. Thee maybe nothing wrong. Idk though I'm not at home right now. I'll take some screenshots of my router settings when iget home

---

### Post by Geoffzx6r on 2009-01-09
hey I got some screenshots

[IMG]http://i64.photobucket.com/albums/h177/doodycocky/settings.jpg[/IMG]

[IMG]http://i64.photobucket.com/albums/h177/doodycocky/settings2.jpg[/IMG]

---

### Post by HuaiDan on 2009-01-10
Let me ask you this:
Can you see the access point in Ub network manager? Do you see the ssid with the signal level (blue bar with my desktop settings) when you left click on the network manager icon? It should be automatic. If not, then your card still has problems. If you can, then this thread is solved, you have a router question. Have you checked the router manufacturer forums?

---

### Post by Geoffzx6r on 2009-01-12
well looks like it's solved. I went back into edit connections made a profile for my home connection to the best of my knowledge and it's working now with wep encryption.

---

