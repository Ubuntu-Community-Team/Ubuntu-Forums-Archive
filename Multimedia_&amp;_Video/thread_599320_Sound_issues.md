---
title: "Sound issues"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by MeteorPhoenix on 2007-11-01
Using Gutsy, got no sound at all <_< Would appreciate any help, thanks.

---

### Post by Fire_Chief on 2007-11-01
Ok, let's start with some hardware info for your system please.

Do you know what kind of sound card you have installed?

Can you post the results of the following commands?
```
lspci -i
lsmod
dmesg
```

That should get us started. :)

---

### Post by MeteorPhoenix on 2007-11-01
> eduardo@eduardo-laptop:~$ lspci -i
lspci: option requires an argument -- i
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging


> eduardo@eduardo-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 29536  0 
hid                    28928  1 usbhid
ipv6                  273892  10 
xt_limit                3584  10 
xt_tcpudp               4224  12 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
af_packet              24840  4 
binfmt_misc            12936  1 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_pcm_oss            53632  0 
snd_mixer_oss          18304  1 snd_pcm_oss
snd_pcm                88836  1 snd_pcm_oss
snd_page_alloc         11528  1 snd_pcm
wlan_scan_sta          15104  1 
ath_rate_sample        14208  1 
pcmcia                 41388  0 
snd_seq_dummy           4740  0 
snd_seq_oss            35712  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
sdhci                  18828  0 
ath_pci                98336  0 
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
wlan                  206660  4 wlan_scan_sta,ath_rate_sample,ath_pci
mmc_core               28420  1 sdhci
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
ath_hal               192720  3 ath_rate_sample,ath_pci
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
snd_seq                58608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26116  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64012  10 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_oss,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
r8169                  32260  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


> [   19.130810] isapnp: No Plug & Play device found
[   19.157493] Real Time Clock Driver v1.12ac
[   19.157734] hpet_resources: 0xfed00000 is busy
[   19.157767] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.159028] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.159165] input: Macintosh mouse button emulation as /class/input/input0
[   19.159248] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.159555] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.159633] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.159638] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.159641] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.159644] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.159646] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.159844] mice: PS/2 mouse device common for all mice
[   19.160068] EISA: Probing bus 0 at eisa.0
[   19.160076] Cannot allocate resource for EISA slot 1
[   19.160080] Cannot allocate resource for EISA slot 2
[   19.160082] Cannot allocate resource for EISA slot 3
[   19.160084] Cannot allocate resource for EISA slot 4
[   19.160087] Cannot allocate resource for EISA slot 5
[   19.160102] EISA: Detected 0 cards.
[   19.160197] TCP cubic registered
[   19.160216] NET: Registered protocol family 1
[   19.160239] Using IPI No-Shortcut mode
[   19.160463]   Magic number: 15:749:429
[   19.160810] Freeing unused kernel memory: 364k freed
[   19.168395] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.373518] AppArmor: AppArmor initialized<5>audit(1193919925.784:2):  type=1505 info="AppArmor initialized" pid=1237
[   20.381936] fuse init (API version 7.8)
[   20.387713] Failure registering capabilities with primary security module.
[   20.425981] ACPI: SSDT 3F689648, 0238 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   20.426210] ACPI: SSDT 3F689101, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   20.426544] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.426785] ACPI: SSDT 3F689880, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   20.426993] ACPI: SSDT 3F6895C3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   20.427360] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.208000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.212000] Time: hpet clocksource has been installed.
[    3.696000] usbcore: registered new interface driver usbfs
[    3.696000] usbcore: registered new interface driver hub
[    3.696000] usbcore: registered new device driver usb
[    3.696000] USB Universal Host Controller Interface driver v3.0
[    3.696000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.696000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.696000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.696000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.696000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.696000] usb usb1: configuration #1 chosen from 1 choice
[    3.696000] hub 1-0:1.0: USB hub found
[    3.696000] hub 1-0:1.0: 2 ports detected
[    3.724000] SCSI subsystem initialized
[    3.728000] libata version 2.21 loaded.
[    3.800000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.800000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.800000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.800000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.800000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.800000] usb usb2: configuration #1 chosen from 1 choice
[    3.800000] hub 2-0:1.0: USB hub found
[    3.800000] hub 2-0:1.0: 2 ports detected
[    3.904000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.904000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.904000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.904000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.904000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.904000] usb usb3: configuration #1 chosen from 1 choice
[    3.904000] hub 3-0:1.0: USB hub found
[    3.904000] hub 3-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -151653194 ns)
[    4.008000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.008000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.008000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.008000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.008000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.008000] usb usb4: configuration #1 chosen from 1 choice
[    4.008000] hub 4-0:1.0: USB hub found
[    4.008000] hub 4-0:1.0: 2 ports detected
[    4.112000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.112000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    4.112000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    4.112000] eth0: RTL8101e at 0xf882c000, 00:1b:38:17:bb:a8, XID 34000000 IRQ 18
[    4.112000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.112000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.112000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.112000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.112000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.112000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.112000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[    4.116000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.116000] usb usb5: configuration #1 chosen from 1 choice
[    4.116000] hub 5-0:1.0: USB hub found
[    4.116000] hub 5-0:1.0: 8 ports detected
[    4.220000] ata_piix 0000:00:1f.2: version 2.11
[    4.220000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.376000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.376000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.376000] scsi0 : ata_piix
[    4.376000] scsi1 : ata_piix
[    4.376000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.376000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.540000] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7DP, max UDMA/100
[    4.540000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.556000] ata1.00: configured for UDMA/100
[    4.876000] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.90, max UDMA/33
[    5.048000] ata2.00: configured for UDMA/33
[    5.048000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    5.048000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.90 PQ: 0 ANSI: 5
[    5.048000] ACPI: PCI Interrupt 0000:06:04.1[B] -> GSI 17 (level, low) -> IRQ 16
[    5.100000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.100000] sd 0:0:0:0: [sda] Write Protect is off
[    5.100000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.100000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.100000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.100000] sd 0:0:0:0: [sda] Write Protect is off
[    5.100000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.100000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.100000]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dc005000-dc0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.120000]  sda1 sda2 < sda5 >
[    5.140000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.144000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.144000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.152000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.152000] Uniform CD-ROM driver Revision: 3.20
[    5.152000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.332000] Attempting manual resume
[    5.332000] swsusp: Resume From Partition 8:5
[    5.332000] PM: Checking swsusp image.
[    5.336000] PM: Resume from disk failed.
[    5.348000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.348000] EXT3-fs: write access will be enabled during recovery.
[    6.372000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f76a841c911]
[   11.240000] kjournald starting.  Commit interval 5 seconds
[   11.240000] EXT3-fs: sda1: orphan cleanup on readonly fs
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 6292377
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 7815174
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 7815173
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 7815172
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 7815171
[   11.240000] ext3_orphan_cleanup: deleting unreferenced inode 7815170
[   11.240000] EXT3-fs: sda1: 6 orphan inodes deleted
[   11.240000] EXT3-fs: recovery complete.
[   11.268000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.016000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.048000] Netfilter messages via NETLINK v0.30.
[   18.052000] nf_conntrack version 0.5.0 (8116 buckets, 64928 max)
[   19.220000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.224000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.360000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.492000] agpgart: Detected an Intel 945GM Chipset.
[   19.492000] agpgart: Detected 7932K stolen memory.
[   19.508000] agpgart: AGP aperture is 256M @ 0xc0000000
[   20.040000] iTCO_vendor_support: vendor-support=0
[   20.044000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.044000] ath_hal: module license 'Proprietary' taints kernel.
[   20.044000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.072000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.092000] Yenta: CardBus bridge found at 0000:06:04.0 [1179:ff00]
[   20.092000] Yenta: Enabling burst memory read transactions
[   20.092000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.092000] Yenta: Routing CardBus interrupts to PCI
[   20.092000] Yenta TI: socket 0000:06:04.0, mfunc 0x10aa1b22, devctl 0x64
[   20.180000] wlan: 0.8.4.2 (0.9.3.2)
[   20.240000] ath_pci: 0.9.4.5 (0.9.3.2)
[   20.244000] sdhci: Secure Digital Host Controller Interface driver
[   20.244000] sdhci: Copyright(c) Pierre Ossman
[   20.328000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   20.328000] Socket status: 30000006
[   20.328000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   20.328000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   20.328000] cs: IO port probe 0x5000-0x5fff: clean.
[   20.328000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   20.328000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   20.344000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   20.344000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   20.876000] ath_rate_sample: 1.2 (0.9.3.2)
[   20.876000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   20.876000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.876000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   20.876000] wifi0: mac 10.0 phy 6.1 radio 10.2
[   20.876000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   20.876000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   20.876000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   20.876000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   20.876000] wifi0: Use hw queue 8 for CAB traffic
[   20.876000] wifi0: Use hw queue 9 for beacons
[   20.892000] wifi0: Atheros 5424/2424: mem=0xd8000000, irq=16
[   20.892000] sdhci: SDHCI controller found at 0000:06:04.3 [104c:803c] (rev 0)
[   20.892000] ACPI: PCI Interrupt 0000:06:04.3[D] -> GSI 19 (level, low) -> IRQ 20
[   20.892000] mmc0: SDHCI at 0xdc005800 irq 20 DMA
[   20.968000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   20.968000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   21.000000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   21.000000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   21.000000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.072000] intel_rng: FWH not detected
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_new
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[   21.096000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   21.096000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   21.096000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   21.100000] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[   21.100000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   21.100000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   21.100000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   21.164000] cs: IO port probe 0x100-0x3af: clean.
[   21.168000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.168000] cs: IO port probe 0x820-0x8ff: clean.
[   21.168000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.168000] cs: IO port probe 0xa00-0xaff: clean.
[   21.400000] lp: driver loaded but no devices found
[   21.488000] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   21.700000] EXT3 FS on sda1, internal journal
[   23.040000] ACPI: AC Adapter [ACAD] (off-line)
[   23.172000] ACPI: Battery Slot [BAT1] (battery present)
[   23.188000] No dock devices found.
[   23.244000] input: Power Button (FF) as /class/input/input3
[   23.244000] ACPI: Power Button (FF) [PWRF]
[   23.244000] input: Lid Switch as /class/input/input4
[   23.244000] ACPI: Lid Switch [LID0]
[   23.244000] input: Power Button (CM) as /class/input/input5
[   23.244000] ACPI: Power Button (CM) [PWRB]
[   23.404000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.412000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.120000] ppdev: user-space parallel port driver
[   25.296000] audit(1193919948.981:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4963 profile="/usr/sbin/cupsd"
[   25.324000] r8169: eth0: link down
[   27.240000] apm: BIOS not found.
[   28.452000] Failure registering capabilities with primary security module.
[   28.648000] Bluetooth: Core ver 2.11
[   28.648000] NET: Registered protocol family 31
[   28.648000] Bluetooth: HCI device and connection manager initialized
[   28.648000] Bluetooth: HCI socket layer initialized
[   28.676000] Bluetooth: L2CAP ver 2.8
[   28.676000] Bluetooth: L2CAP socket layer initialized
[   28.748000] Bluetooth: RFCOMM socket layer initialized
[   28.748000] Bluetooth: RFCOMM TTY layer initialized
[   28.748000] Bluetooth: RFCOMM ver 1.8
[   31.044000] [drm] Initialized drm 1.1.0 20060810
[   31.048000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   31.048000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  144.032000] NET: Registered protocol family 17
[  154.372000] NET: Registered protocol family 10
[  154.372000] lo: Disabled Privacy Extensions
[  154.372000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  164.892000] ath0: no IPv6 routers present
[  174.528000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  174.716000] usb 2-1: configuration #1 chosen from 1 choice
[  174.836000] usbcore: registered new interface driver hiddev
[  174.868000] input: HID 04d9:1133 as /class/input/input6
[  174.868000] input: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.1-1
[  174.868000] usbcore: registered new interface driver usbhid
[  174.868000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  598.256000] usb 2-1: USB disconnect, address 2
[ 1078.720000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:63:69:00:00:7d:11:65:47:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:c1:92:7e:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=25449 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1080.244000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:63:cd:00:00:7d:11:64:e3:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:b1:92:7e:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=25549 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1081.752000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:64:2f:00:00:7d:11:64:81:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:b1:92:7e:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=25647 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1381.908000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:38:90:00:00:7d:11:90:20:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:b8:92:87:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=14480 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1383.424000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:38:ed:00:00:7d:11:8f:c3:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:a8:92:87:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=14573 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1384.932000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:39:90:00:00:7d:11:8f:20:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:a8:92:87:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=14736 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 2286.760000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[ 2286.948000] usb 2-1: configuration #1 chosen from 1 choice
[ 2286.984000] input: HID 04d9:1133 as /class/input/input7
[ 2286.984000] input: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.1-1
[ 2718.104000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:05:dc:ca:d5:40:00:33:06:8a:f7:c0:23:f4:32:88:91:af:67:00:50:9d:87:b6:8f:b8:d6:72:6e:86:52:50:10:c0:1c:48:28:00:00:ab:c5:83:ab:70:9f:dc:a7:f3:8a:31:1e:c1:31:12:77:b4:fb:37:6c:02:9f:6e:91:67:70:39:9c:08:db:a6:91:ea:95 SRC=192.35.244.50 DST=136.145.175.103 LEN=1500 TOS=0x00 PREC=0x00 TTL=51 ID=51925 DF PROTO=TCP SPT=80 DPT=40327 WINDOW=49180 RES=0x00 ACK URGP=0 
[ 2778.120000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:05:dc:b5:35:40:00:33:06:a0:97:c0:23:f4:32:88:91:af:67:00:50:9d:87:b6:8f:b8:d6:72:6e:86:52:50:10:c0:1c:48:28:00:00:ab:c5:83:ab:70:9f:dc:a7:f3:8a:31:1e:c1:31:12:77:b4:fb:37:6c:02:9f:6e:91:67:70:39:9c:08:db:a6:91:ea:95 SRC=192.35.244.50 DST=136.145.175.103 LEN=1500 TOS=0x00 PREC=0x00 TTL=51 ID=46389 DF PROTO=TCP SPT=80 DPT=40327 WINDOW=49180 RES=0x00 ACK URGP=0 
[ 2838.120000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:05:dc:9f:95:40:00:33:06:b6:37:c0:23:f4:32:88:91:af:67:00:50:9d:87:b6:8f:b8:d6:72:6e:86:52:50:10:c0:1c:48:28:00:00:ab:c5:83:ab:70:9f:dc:a7:f3:8a:31:1e:c1:31:12:77:b4:fb:37:6c:02:9f:6e:91:67:70:39:9c:08:db:a6:91:ea:95 SRC=192.35.244.50 DST=136.145.175.103 LEN=1500 TOS=0x00 PREC=0x00 TTL=51 ID=40853 DF PROTO=TCP SPT=80 DPT=40327 WINDOW=49180 RES=0x00 ACK URGP=0 
[ 2846.556000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:30:de:ed:40:00:6a:06:ca:36:50:5d:df:4d:88:91:af:67:0f:cc:00:6e:24:57:15:a7:00:00:00:00:70:02:40:00:91:43:00:00:02:04:05:b4:01:01:04:02:82:ab:4b:aa:2d:34:30:33:00:00:00:00:00:00:00:02:00:00:25:dd:18:00:50:f2:02:01 SRC=80.93.223.77 DST=136.145.175.103 LEN=48 TOS=0x00 PREC=0x00 TTL=106 ID=57069 DF PROTO=TCP SPT=4044 DPT=110 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2849.660000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:30:e1:65:40:00:6a:06:c7:be:50:5d:df:4d:88:91:af:67:0f:cc:00:6e:24:57:15:a7:00:00:00:00:70:02:40:00:91:43:00:00:02:04:05:b4:01:01:04:02:9b:a6:75:3d:2d:34:30:33:00:00:00:00:00:00:00:02:00:00:25:dd:18:00:50:f2:02:01 SRC=80.93.223.77 DST=136.145.175.103 LEN=48 TOS=0x00 PREC=0x00 TTL=106 ID=57701 DF PROTO=TCP SPT=4044 DPT=110 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2897.000000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:78:3f:00:00:7d:11:50:71:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:9b:92:a4:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=30783 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 2898.612000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:79:11:00:00:7d:11:4f:9f:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:8b:92:a4:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=30993 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 2899.968000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:79:bd:00:00:7d:11:4e:f3:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:8b:92:a4:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=31165 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3194.652000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:50:5f:00:00:7d:11:78:51:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:95:92:aa:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=20575 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3194.752000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:51:16:00:00:7d:11:77:9a:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:85:92:aa:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=20758 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3196.284000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:51:d4:00:00:7d:11:76:dc:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:85:92:aa:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=20948 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3499.376000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:2f:d9:00:00:7d:11:98:d7:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:8a:92:b5:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=12249 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3500.816000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:30:3d:00:00:7d:11:98:73:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:7a:92:b5:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=12349 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3502.316000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:31:3e:00:00:7d:11:97:72:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:7a:92:b5:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=12606 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3798.208000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:0d:ca:00:00:7d:11:ba:e6:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:84:92:bb:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=3530 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3799.716000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:0e:75:00:00:7d:11:ba:3b:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:74:92:bb:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=3701 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3801.172000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:0e:e6:00:00:7d:11:b9:ca:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:74:92:bb:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=3814 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 4092.188000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:01:84:80:3d:00:00:2e:11:7b:75:41:50:16:6e:88:91:af:67:77:c3:04:02:01:70:00:00:04:00:78:00:10:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:f8:91:7b:5a:00:ff:d0:11:a9:b2:00:c0:4f:b6:e6:fc:00:00:00:00:00:00 SRC=65.80.22.110 DST=136.145.175.103 LEN=388 TOS=0x00 PREC=0x00 TTL=46 ID=32829 PROTO=UDP SPT=30659 DPT=1026 LEN=368 
[ 4098.860000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:70:b5:00:00:7d:11:57:fb:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:7e:92:c1:00:00:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=28853 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 4100.364000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:71:78:00:00:7d:11:57:38:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:6e:92:c1:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=29048 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 4101.816000] Inbound IN=ath0 OUT= MAC=00:1b:9e:2b:96:cd:00:04:80:85:8d:00:08:00:45:00:00:4e:72:23:00:00:7d:11:56:8d:88:91:b4:64:88:91:af:67:00:89:00:89:00:3a:b8:6e:92:c1:00:10:00:01:00:00:00:00:00:00:20:43:4b:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:41:00 SRC=136.145.180.100 DST=136.145.175.103 LEN=78 TOS=0x00 PREC=0x00 TTL=125 ID=29219 PROTO=UDP SPT=137 DPT=137 LEN=58

The last command kind of cuts itself because of its length.

---

### Post by Fire_Chief on 2007-11-01
Slight oops on my part there with the lspci command...but no worries.

From your dmesg output, it looks like you have  an Intel HD Audio device in your system and it is having problems playing nicely with Ubuntu. This is not terribly surprising as support for this card is not very strong in Linux yet. I've had this same issue with my laptop when previously running Linux Mint (Ubuntu derivative). I've since installed Gutsy (clean install) and not had any problems so far.

Would you re-run the lspci command with no switches (it should give a list of hardware detected instead of the help file) and post it? Just want to make sure of the exact hardware version of your card.

On Mint, I fixed the issue by downloading the latest available version of Alsa from the Alsa website and compiled it. Since the problem is not occuring on Gutsy, I've not had to address it. Did you have sound when running on the live CD? If so, then that's a good sign.

---

### Post by MeteorPhoenix on 2007-11-01
I ran the LiveCD a few days back, but I still had no sound. I was ready to do a clean install, too.

> eduardo@eduardo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by thirunavukkarasu on 2007-11-01
Have a look over the below link it. This will help u to solve the issue

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is)

Rgds,
Thiru.S

---

### Post by MeteorPhoenix on 2007-11-01
I did <_<

> FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by Fire_Chief on 2007-11-01
The driver module that should be in use for your sound card is snd-hda-intel.

Try ```
sudo modprobe snd-hda-intel
aplay -l
```If aplay lists your soundcard properly then see if your volume control panel shows a new sound card to manage. Verify that the channels are not muted or turned down too low. Test playing some sound.

*Edit* I see I'm moving a bit too slow :( If you've already done the above then nevermind...

---

### Post by MeteorPhoenix on 2007-11-01
bump

---

### Post by Fire_Chief on 2007-11-01
I suppose you could use my snd-hda-intel.ko file as I have the same sound card and sound works fine for me. I have ALSA version 1.0.14 installed on my system (same kernel version too).

---

### Post by Vanten on 2007-11-01
I'm having the same problem. No sound, Alsamixer shows no muted lines and the same for volume monitor. I think it might be that the system is using the digital out but I have not found any place yet where to change this.

aplay gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Conexant CX20549 (Venice)                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: PCM [dB gain=0.00, 0.00]                                               &#9474;
&#9474;                                                                              &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;         &#9474;
&#9474;         &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;          &#9484;&#9472;&#9472;&#9488;          &#9500;&#9472;&#9472;&#9508;          &#9500;&#9472;&#9472;&#9508;         &#9474;
&#9474;         &#9474;OO&#9474;                        &#9474;MM&#9474;          &#9474;OO&#9474;          &#9474;OO&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;       100<>100      100<>100                    100<>100        0<>0         &#9474;
&#9474;        Master      <  PCM   >      IEC958       Ext Mic       Int Mic        &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

Notice that there isn't any box beneath the PCM, is it supposed to be like this?
Running on a Lenovo 3000 v200 - Ubuntu 7.10

Thanks for any help!
// Vanten

---

### Post by mike102282 on 2007-11-01
Yes it is supose to be like that.

---

### Post by Vanten on 2007-11-01
ok. Any clues where to disable digital out? I don't have any check box for this in my volume control. 

// Vanten

---

### Post by Fire_Chief on 2007-11-01
May not be an issue but just for reference, here's what my sound prefs settings look like.

---

### Post by Vanten on 2007-11-01
They look exactly as the mentioned picture.

EDIT: Still no sound, so what can i do? wait for better drivers?

// Vanten

---

### Post by Fire_Chief on 2007-11-01
Vanten, I noticed in your alsamixer screenshot that the chipset in your system is different than mine :(.

You have the 
Chip: Conexant CX20549 (Venice)

I have
Chip: Analog Devices AD1981

It seems things are more different than they seem :confused:

---

### Post by MeteorPhoenix on 2007-11-01
I'm kind of new at this, so, am I supposed to do something special with them o_o (the snd-hda-intel.ko file, I mean)?

---

### Post by Fire_Chief on 2007-11-01
I sent it to replace the file you had just in case it was corrupt. However, after Vanten's posts and the discovery that the Intel HD Audio can be different chipsets, the file may not resolve the problem. In any event, it should not hurt anything.

Replace your existing fie by typing```
sudo gzip -d snd-hda-intel.ko.gz
sudo mv snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/
```It may ask if you want to overwrite the file...say yes. Then do```
modprobe snd-hda-intel
```. If your chip is the same as mine (posted earlier), then you should be working (I think). If your chipset is like Vanten's (Conexant), then we're still stuck.

---

### Post by MeteorPhoenix on 2007-11-01
This is what I get:

> eduardo@eduardo-laptop:~$ sudo gzip -d snd-hda-intel.ko.gz
gzip: snd-hda-intel.ko.gz: No such file or directory
eduardo@eduardo-laptop:~$ sudo mv snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/
mv: cannot stat `snd-hda-intel.ko': No such file or directory

---

### Post by Fire_Chief on 2007-11-01
Did you download the attached file I posted earlier? If so, you need to be in the directory where you saved it and then run the commands.

---

### Post by Vanten on 2007-11-01
Tried the file you provided, didn't help me though. It changed the subdevice properties on my analog device to the same as my digital. Reverted the changes now and back to zero :(

Anyways; any other input on how to make the sound work? The soundcard is found and installed, alsa recognizes it and all lines are unmuted. What is wrong?

// Vanten

---

### Post by Fire_Chief on 2007-11-01
Check this Ubuntu Wiki page to see if your laptop is listed. If so, do the suggested fixes work for your system?
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

---

### Post by gene6482 on 2007-11-02
what model of laptops are you using?

Edit: by that i mean is it a dell laptop, toshiba, hp, lenovo.

---

### Post by Vanten on 2007-11-02
My laptop wasn't listed. But I have noticed that on some startups the sound does work. The downside is that each time the sound work, my network adapter and wifi doesn't respond :/ So I guess the drivers doesn't cooperate so good together.
// Vanten

---

### Post by MeteorPhoenix on 2007-11-03
> gzip: snd-hda-intel.ko.gz: No such file or directory


> eduardo@eduardo-laptop:~$ sudo mv snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/
mv: cannot stat `snd-hda-intel.ko': No such file or directory

I downloaded it, but it still says this. What am I doing wrong?

Also, my laptop isn't listed. It's a Toshiba Satellite A135, btw.

EDIT 2: Oh, am I supposed to download it to a certain directory XD?

---

### Post by Fire_Chief on 2007-11-04
No, You can download it wherever you like on the system. You just need to be in that directory on the command line when you run the commands to unzip it and move the file.

Let's try this...from the command line, type in **alsamixer **and at the top of the display, you should see something like this

```
Card: HDA Intel
Chip: Analog Devices AD1981
View: [Playback] Capture All
Item: Master [dB gain=-3.00, -3.00]
```The View and Item lines are not important. The critical line is the Chip: one.

Mine is the Analog Devices AD1981
Vanten has the Conexant CX20549 (Venice)

What does yours say?

---

### Post by MeteorPhoenix on 2007-11-05
> eduardo@eduardo-laptop:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device 
eduardo@eduardo-laptop:~$ 

This is what it says.

---

### Post by gene6482 on 2007-11-05
try sudo alsaconf and see if you can reconfigure it there.

Make sure you have alsa-utils installed.

---

### Post by MeteorPhoenix on 2007-11-06
> sudo: alsaconf: command not found

How do I check if I have alsa-utils installed?

---

### Post by discmaster on 2007-11-06
> How do I check if I have alsa-utils installed? look for it in synaptic; it will have a green box if installed.
OR

sudo apt-get install alsa-utils

:popcorn:

---

### Post by Hairy Hobbit on 2007-11-06
Hello all.

I have a Toshiba Satellite Pro P100.  I have the same issue as is being discussed here - having tried pretty much all the suggestions I see in the forums, including the sticky topic with the flowchart.  All to no avail.

When I run alsamixer, is get:

Card: HDA Intel                                                              &#9474;
Chip: Conexant CX20551 (Waikiki)                                             &#9474;
View: [Playback] Capture  All                                                &#9474;
Item: Master 

Anyone with the same managed to get it working?

Thanks,
HH

---

### Post by MeteorPhoenix on 2007-11-06
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  libcairo-jni libxcb-xv0 libpostproc0d libpostproc1d libgtk-jni libavformat0d
  libcairo-java libglib-jni libxcb1 libxine1-ffmpeg libxcb-shape0 libglib-java
  armagetronad-common libxvmc1 libavcodec0d libmodplug0c2 libpulse0
  libswt3.2-gtk-jni libxcb-shm0 libglademm-2.4-1c2a libsdl-image1.2 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Apparently, I already have them.

---

### Post by gene6482 on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For P100s there's an open bug report.  Apparently there's an issue with the current kernel that prevents our sound from working, if you use the feisty kernel you'll be good.(With some other tinkering)

> **Hairy Hobbit said:**
> Hello all.

I have a Toshiba Satellite Pro P100.  I have the same issue as is being discussed here - having tried pretty much all the suggestions I see in the forums, including the sticky topic with the flowchart.  All to no avail.

When I run alsamixer, is get:

Card: HDA Intel                                                              &#9474;
Chip: Conexant CX20551 (Waikiki)                                             &#9474;
View: [Playback] Capture  All                                                &#9474;
Item: Master 

Anyone with the same managed to get it working?

Thanks,
HH

---

### Post by MeteorPhoenix on 2007-11-06
Well, for some reason, I can't even run alsamixer.

---

### Post by Hairy Hobbit on 2007-11-06
Gene64 - Thanks for the information - at least I can stop looking for a while.  Please excuse the dumb question, but does that mean there will be no chance of a fix until I see my installation go to get some updates one day?

Thanks,
HH

---

### Post by gene6482 on 2007-11-07
pretty much yes, again unless you download the feisty kernel and install it.

---

### Post by MeteorPhoenix on 2007-11-07
bump

---

### Post by Fire_Chief on 2007-11-07
MeteorPhoenix,

Do you get any output information from ```
aplay -l
```or```
aplay -L
```

---

### Post by MeteorPhoenix on 2007-11-08
> aplay: device_list:204: no soundcards found...

The second one doesn't give back anything.

---

### Post by Fire_Chief on 2007-11-08
I'm quickly running out of ideas...

At this point, I'd suggest following the sound problem solution guide posted earlier
[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is]("http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is")

Except go to the ALSA Driver Compilation section and start there. Ignore the ALSA version recommended from the alsa-project as it is several versions old. Use the latest available version.

---

### Post by MeteorPhoenix on 2007-11-08
I tried it. Maybe I didn't do something right, always possible, but I followed the steps to the letter.

---

### Post by Fire_Chief on 2007-11-08
Also possible that your chipset is just not supported (or well supported) in Linux yet. Not that I want to drive you away from Ubuntu but I'd be curious if the issue happens with another distro such as PCLinuxOS or Knoppix. I only suggest those two because they can be run in a liveCD environment similar to Ubuntu.

---

### Post by pjvaanan on 2007-11-08
Make sure all files in /dev/snd/ have read-write permissions for "other" (crw-rw-rw-).
If not just # sudo chmod o+rw /dev/snd/*

This worked for my gutsy/asus a6ja

---

### Post by MeteorPhoenix on 2007-11-08
No idea how to do that -.-

> Also possible that your chipset is just not supported (or well supported) in Linux yet. Not that I want to drive you away from Ubuntu but I'd be curious if the issue happens with another distro such as PCLinuxOS or Knoppix. I only suggest those two because they can be run in a liveCD environment similar to Ubuntu.

If it helps any, it worked perfectly well with edgy, and it had problems (sort of fixable) on feisty.

---

### Post by Fire_Chief on 2007-11-09
I just ran across this article and wondered if it may help...
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

---

### Post by MeteorPhoenix on 2007-11-09
To my great regret, it didn't work either. 

PS: How do I know if I'm using a kernel that's not the generic one?

---

### Post by Yellow Pasque on 2007-11-09
If ALSA fails you, you can always uninstall it and go with OSS.
[http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

---

### Post by wabre on 2007-11-09
I have the same problem...no sound. Very interesting that in feisty it was working and now not anymore. also tried different things. going back to older kernel etc etc is a no-go. 

a great thanks to all those who try to help but a new version of a distro which does not support hardware that was supported before...back on vista...sorry...

---

### Post by MeteorPhoenix on 2007-11-09
> If ALSA fails you, you can always uninstall it and go with OSS.
[http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

Is there a thread that can walk me through it? I don't want to experiment.

---

### Post by Fire_Chief on 2007-11-09
MeteorPhoenix,

First of all, I'm impressed by your tenacity on this issue. I found a couple of other pages which *may* help with troubleshooting this.

Among other things suggested on [this page]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") is a codec check to help identify your specific needs driver-wise.```
grep Codec /proc/asound/card0/codec#*
```

I'm checking another thread also dealing with Intel HD audio to see if any positive results are there.

Regards,

*EDIT*: Have a look here also...the first page has a walkthrough but page 8 (post by CrazyPurple) may give you a good method to try.[http://ubuntuforums.org/showthread.php?t=530374&page=8]("http://ubuntuforums.org/showthread.php?t=530374&page=8")

---

### Post by MeteorPhoenix on 2007-11-09
And I'm likewise thankful for all the help you guys are giving me, especially after days.

> grep: /proc/asound/card0/codec#*: No such file or directory

I'm guessing this isn't what was supposed to appear.

---

### Post by Fire_Chief on 2007-11-09
> **Fire_Chief said:**
>  Have a look here also...the first page has a walkthrough but page 8 (post by CrazyPurple) may give you a good method to try.[http://ubuntuforums.org/showthread.php?t=530374&page=8]("http://ubuntuforums.org/showthread.php?t=530374&page=8")

Did you happen to see this edit on my last post? Give it a shot :)

---

### Post by MeteorPhoenix on 2007-11-09
I have the backports he suggested downloaded. I think that's what the other site suggested too, only through Synaptic this time.

---

### Post by Fire_Chief on 2007-11-09
I was hoping that post would get you up and working since he had the same laptop (Toshiba A135). He did mention two different linux-backports-modules available for install and he chose the 2nd one.

---

### Post by MeteorPhoenix on 2007-11-09
I dled the first one and restarted. Still no sound.

---

### Post by MeteorPhoenix on 2007-11-13
bump

---

### Post by Fire_Chief on 2007-11-13
Can't hurt to try the **2nd** one that he listed since it worked for him. :-k

---

### Post by MeteorPhoenix on 2007-11-13
The second one is the first one I tried, because it was the one he mentioned worked for him.

---

### Post by Low-key Lyesmith on 2007-11-13
Hi I have similar problems with 82801G (ICH7 Family) High Definition Audio Controller (this is my audio card): sometimes sound is fine, sometimes not. How do I have to use your patch?
I have very basic (almost none) knowledge of Linux-Ubuntu.
Thanks to anyone who can help
Lowkey

---

### Post by Yellow Pasque on 2007-11-14
Check to see if your device is supported by OSS:
The official and outdated list can be found at [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)
(Ignore the old references to retail drivers; it's all free now)
I've also attached the device list from the latest build (4.0-1014) so double-check that if you don't see your card on the site's list.

Go here:[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)
Get the Linux 2.6 DEB package for your architecture (use x86 unless you have the amd64 Ubuntu) and save it to your home folder (i.e. the ~/ directory)

0. Get necessary packages
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```
1. Copy these directions to a text file so you can view them from a terminal, or print them out/write them down
2. Remove ALSA:
```
sudo apt-get remove alsa-base
```
3. Reboot, but don't log in
4. Change your session (clicking the icon in the lower left of the login screen) to failsafe terminal.
5. Now Log In
6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_v4.0-1014_amd64.deb if you downloaded that version
```
sudo dpkg -i oss-linux_v4.0-1014_i386.deb
sudo soundon
```
7. Just issue the exit command and when it goes back to the login screen, log in as normal.
8. You'll need to right-click on and remove the mixer/volume control icon from the panel.
9. In a terminal, run the ossinfo command. The mixer devices are numbered, so note the number of the mixer device you want to control.
10. Add a new custom application launcher to the panel that runs the command: ossxmix -d<mixer number you got in step 9> That's oss**x**mix, not ossmix, and the command will default to -d0 if you don't add a switch. Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.

If you're still not getting sound, see what the ossdetect -v and ossinfo commands give you.

**ADDENDUM: Volume Control Patch** The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). I've also built and attached an AMD64 version to this post. Note that this patch was updated on 1/8/08, so if you tried it before then and it didn't work, try again.
Also, if you'd prefer to map commands to your shortcut keys, [here are some scripts to use](http://wiki.archlinux.org/index.php/OSSt) (at the bottom of the page).

**ADDENDUM2: Sound in Flash** (AMD64 users, see the end of this post for important note)

1. Run:
```
file /usr/lib/libflashsupport.so
```
If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. You need to compile /usr/lib/oss/lib/flashsupport.c 
To do so, open the file with a text editor (and root access) and comment out the #define OPENSSL line by putting two '/'s' in front of it. (Make sure #define OSS does not have anything in front of it.) Save and close.
3. ```
cd /usr/lib/oss/lib; sudo cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so; sudo cp /usr/lib/oss/lib/libflashsupport.so /usr/lib/
```
4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

**AMD64 Users:**If you're on 64-bit Ubuntu and running the 32-bit plugin with nspluginwrapper, follow the steps above, except add the -m32 flag to the compilation command in step 3. You'll also need the gcc-4.1-multilib package.
So, for step #3:
```
sudo apt-get install gcc-4.1-multilib
cd /usr/lib/oss/lib; sudo cc -shared -O2 -Wall -Werror -m32 flashsupport.c -o libflashsupport.so; sudo cp libflashsupport.so /usr/lib
```

---

### Post by aashay on 2007-11-15
I was scratching my brains trying to get the subwoofer working with ALSA on my lenovo laptop. OSS worked like a charm. Thanks!!
EDIT: oops.. looks like I spoke too soon. I lost sound in firefox,(flash videos). Any Ideas?

---

### Post by dkov on 2007-11-16
I successfully installed OSS according to the instructions above but it still didn't work for me.

Here's the output from the ossinfo command:

david@david-laptop:~$ ossinfo
Version info: OSS 4.0 (b1009/200711130545) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 (david-laptop)

Number of audio devices:        1
Number of audio engines:        10
Number of MIDI devices:         0
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH4 (24C5)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support

MIDI devices (/dev/midi*)

Mixer devices (/dev/mixer*)
 0: ICH AC97 Mixer (AD1981B) (Mixer 0 of device object 1)

Audio devices
/dev/oss/ich0/pcm0      Intel ICH4 (24C5)  (device index 0)
david@david-laptop:~$

---

### Post by Yellow Pasque on 2007-11-17
EDIT: Outdated.

---

### Post by Yellow Pasque on 2007-11-17
> **dkov said:**
> I successfully installed OSS according to the instructions above but it still didn't work for me.
It looks like it detected and installed correctly.
Are you sure it's not muted? What happens when you run ossxmix?

You can also try booting into recovery mode and running the sudo soundon and/or ossdetect -v command.

---

### Post by JunCTionS on 2007-11-17
worked good :) bye bye ALSA (which didn't work on gutsy anymore for my Satellite A135-S4677).
although now (minor issue) my volume wheel calls kmix which works with ALSA.
I'd like for it to work.
also, I feel the volume's a bit low (used to think that with alsa too) is there a way to fix this?.

---

### Post by Strangerdave on 2007-11-25
Tried to follow the instructions for oss, but this is what I got:

```
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

Sorry, I am a bit of a n00b, and am not sure what to do here.

-SD-

---

### Post by d00by on 2007-11-25
> **Temüjin said:**
> Sorry, I forgot to add that step in my howto.Thanks for reminding me! You need to compile /usr/lib/oss/lib/flashsupport.c
To do so, you need to open the file, comment out the #define SSL line, and copy the suggested line they give you to compile it (remove the -lssl flag).
You'll need gcc,  and possibly some other basic software compiling packages. When you get the file compiled, you'll get an output file named libflashsupport.so  Move that to your /usr/lib directory.

If you're on 64-bit Ubuntu and running the 32-bit plugin with nspluginwrapper, follow the steps above. The only difference is that you'll need the -m32 flag in the compilation command and the multilib package for the version of gcc you're using.

I have a #define openssl line. were you referring to this line to comment out?

I commented out the aopenssl line and then compiled using the -m32 option with multilib package installed as I am using AMD 64 bit gutsy.

I moved the .so file to /usr/lib folder.

It did not work. I am still NOT getting any sound.

I think it may be some other issue as I am not able to hear any sound when I login/logout.

I hear NO sound from gmail notifier extension in my firefox. 

Can you help me find out what the problem is in my case?

I can hear sound on music player.

---

### Post by Keith.Anyan on 2007-11-29
> **Strangerdave said:**
> Tried to follow the instructions for oss, but this is what I got:

```
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

Sorry, I am a bit of a n00b, and am not sure what to do here.

-SD-

I have the exact same problem.
Newbie here, I have no idea how to fix this, can somebody help me?

---

### Post by bmwman91 on 2007-12-06
> **Strangerdave said:**
> Tried to follow the instructions for oss, but this is what I got:

```
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

Sorry, I am a bit of a n00b, and am not sure what to do here.

-SD-

Same here.  This was my full log.

```
twinion@twinion-laptop:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1009_i386.deb
(Reading database ... 91072 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1009 (using oss-linux_v4.0-1009_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1009_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1009_i386.deb
twinion@twinion-laptop:~/Desktop$ ossxmix
/dev/mixer: No such file or directory

```

---

### Post by nautical34 on 2007-12-10
If you get the log above, go here and follow the instructions then try the install again. Should work fine.

[http://www.4front-tech.com/forum/viewtopic.php?t=2054]("http://www.4front-tech.com/forum/viewtopic.php?t=2054")


I do have a question though, I have a Compaq v3000 and it has the media touch buttons for sound, is there anyway to assign them to work with OSS? Also when I plug my headphones in it doesn't mute the internal speakers, is there a way to fix this?


Thanks,
-GM

---

### Post by Yellow Pasque on 2007-12-22
Look [here](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=) for a patch for the volume control issue. (Also, link added to the HowTo. Thanks)

---

### Post by CyberMagnus on 2007-12-27
> **Temüjin said:**
> Look [here](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=) for a patch for the volume control issue. (Also, link added to the HowTo. Thanks)

I was checking this post out as I would like to be able to (someday) run Ubuntu Linux on my home studio computer for audio recording. I have an M-Audio Audiophile 192 sound card and the list of supported cards says that it is only supported by the "retail" OSS. Based on what I've read online I don't think the card works with ALSA but I haven't tried it. What exactly is the retail version of OSS? 

Thanks!

---

### Post by Yellow Pasque on 2007-12-27
OSS started out free, then went proprietary($), but is now open source, so that reference is outdated. Some Linux distros have embraced OSSv4 anyway and returned it to mainstream, but most stick with ALSA That's unfortunate, as the the layout and documentation of the ALSA code is poor from my understanding; even to the point where the ALSA developers suggest using JACK with  ALSA.

---

### Post by Insomnia777 on 2008-01-06
I followed your instructions but I get this with ossinfo, still no sound :(

```
abner@R2D2:~$ ossinfo
Version info: OSS 4.0 (b1012/200801022350) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (R2D2)

Number of audio devices:        1
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH5 (24D5) interrupts=182477 (182477)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (AD1980) (Mixer 0 of device object 1)

Audio devices
Intel ICH5 (24D5)                 /dev/oss/ich0/pcm0  (device index 0)

```

---

### Post by Yellow Pasque on 2008-01-06
Insomnia77, I'm trying to get someone's sound working in another thread. They have the same chip (ICH5) as you. Keep an eye on this: [http://ubuntuforums.org/showthread.php?t=660062](http://ubuntuforums.org/showthread.php?t=660062)

I would start out with the same suggestion I gave there. Do the following command and delete the line that loads the ossusb driver. Then save it and reboot:
```
sudo gedit /usr/lib/oss/etc/installed_drivers 
```

---

### Post by MountainX on 2008-01-19
> **Temüjin said:**
> 
8. You'll need to right-click on and remove the mixer/volume control icon from the panel.
9. In a terminal, run the ossinfo command. The mixer devices are numbered, so note the number of the mixer device you want to control.
10. Add a new custom application launcher to the panel that runs the command: ossxmix -d<mixer number you got in step 9> That's oss**x**mix, not ossmix, and the command will default to -d0 if you don't add a switch. Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.


I was OK up to step 8...
What is the panel mentioned in step 8 and where do I find it?

In step 10, how do I add a ew custom application launcher?

Not sure this is important, but when I ran ossxmix -d0 in a terminal and then closed the app, I saw a bunch of errors similar to this:
(ossxmix:12138): Gtk-CRITICAL **: gtk_frame_set_label: assertion `GTK_IS_FRAME (frame)' failed


**_ossdetect -v_**
bash: /usr/sbin/ossdetect: Permission denied
computeruser@Condortu:/usr/lib/oss/lib$ sudo ossdetect -v
Detected Nvidia nForce4
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

**_ossinfo_**
Version info: OSS 4.0 (b1012/200801022339) (0x00040003) 
Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Condortu)

Number of audio devices:        2
Number of audio engines:        11
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Nvidia nForce4
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (ALC850) (Mixer 0 of device object 1)

Audio devices
Nvidia nForce4                    /dev/oss/ich0/pcm0  (device index 0)
Nvidia nForce4 S/PDIF out         /dev/oss/ich0/spdout  (device index 1)

Sound was working for me until I upgraded my nVidia video card driver using Envy.
I'm on Gutsy AMD64, so I will also have to deal with flash sound issue when I get the above stuff working. Thanks.

---

### Post by Yellow Pasque on 2008-01-20
The 'panel' I'm referring to is the bar across the top of your screen. There should be a speaker icon that you click on to bring up the mixer. Right click on that and select 'Remove from panel'. Now right click in the empty space where that was and select 'Add to panel..'. Select a custom application launcher and follow step 10.

---

### Post by randcoop on 2008-01-21
Been looking at this thread in the hopes of finding a solution.  I have a Toshiba Satellite with a sound card (Intel) that worked perfectly in Feisty.  Upgraded to Gutsy and suddenly sound was barely audible (though it was there).  After running through many of the suggestions here, I booted into 2.6.20 instead of the current Gutsy kernel of 2.6.22.  Sound was back with no other adjustments.

So I think the problem is the kernel.  I don't know if there's a way to fix that problem, but for now, I've set the default boot choice in grub to 2.6.20.  

Hope that helps others.

---

### Post by MountainX on 2008-01-21
I ended up reinstalling Ubuntu amd64 and my sound is working now. Just thought I'd let everyone know. Thanks for all the suggestions. After the clean installation I had no problems.

---

### Post by randcoop on 2008-01-23
I actually found the answer in another thread here, but it seems to work in almost all the Toshiba laptops.  Edit the /etc/modprobe.d/alsa-base file.  Add the line:

```
options snd-hda-intel model=3stack
```

to the options section.  Then reboot.  Sound was restored to its full power in the latest Gutsy kernel after I did this.

---

### Post by jonnywombat on 2008-02-24
> **Temüjin said:**
> Check to see if your device is supported by OSS:
The official and outdated list can be found at [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)
(Ignore the old references to retail drivers; it's all free now)
I've also attached the device list from the latest build (4.0-1013) so double-check that if you don't see your card on the site's list.

Go here:[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)
Get the Linux 2.6 DEB package for your architecture (use x86 unless you have the amd64 Ubuntu) and save it to your home folder (i.e. the ~/ directory)

0. Get necessary packages
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```
1. Copy these directions to a text file so you can view them from a terminal, or print them out/write them down
2. Remove ALSA:
```
sudo apt-get remove alsa-base
```
3. Reboot, but don't log in
4. Change your session (clicking the icon in the lower left of the login screen) to failsafe terminal.
5. Now Log In
6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_v4.0-1013_amd64.deb if you downloaded that version
```
sudo dpkg -i oss-linux_v4.0-1013_i386.deb
sudo soundon
```
7. Just issue the exit command and when it goes back to the login screen, log in as normal.
8. You'll need to right-click on and remove the mixer/volume control icon from the panel.
9. In a terminal, run the ossinfo command. The mixer devices are numbered, so note the number of the mixer device you want to control.
10. Add a new custom application launcher to the panel that runs the command: ossxmix -d<mixer number you got in step 9> That's oss**x**mix, not ossmix, and the command will default to -d0 if you don't add a switch. Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.

If you're still not getting sound, see what the ossdetect -v and ossinfo commands give you.

**ADDENDUM: Volume Control Patch** The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). I've also built and attached an AMD64 version to this post. Note that this patch was updated on 1/8/08, so if you tried it before then and it didn't work, try again.
Also, if you'd prefer to map commands to your shortcut keys, [here are some scripts to use](http://wiki.archlinux.org/index.php/OSSt) (at the bottom of the page).

**ADDENDUM2: Sound in Flash** (AMD64 users, see the end of this post for important note)

1. Run:
```
file /usr/lib/libflashsupport.so
```
If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. You need to compile /usr/lib/oss/lib/flashsupport.c 
To do so, open the file with a text editor (and root access) and comment out the #define OPENSSL line by putting two '/'s' in front of it. (Make sure #define OSS does not have anything in front of it.) Save and close.
3. ```
cd /usr/lib/oss/lib; sudo cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so; sudo cp /usr/lib/oss/lib/libflashsupport.so /usr/lib/
```
4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

**AMD64 Users:**If you're on 64-bit Ubuntu and running the 32-bit plugin with nspluginwrapper, follow the steps above, except add the -m32 flag to the compilation command in step 3. You'll also need the gcc-4.1-multilib package.
So, for step #3:
```
sudo apt-get install gcc-4.1-multilib
cd /usr/lib/oss/lib; sudo cc -shared -O2 -Wall -Werror -m32 flashsupport.c -o libflashsupport.so; sudo cp libflashsupport.so /usr/lib
```

Just a note

If you use AWN do not use this method to install OSS as it will break AWN

Instead read this post

[http://ubuntuforums.org/showthread.php?t=706115](http://ubuntuforums.org/showthread.php?t=706115)

Jonny

---

### Post by legendarysim on 2008-03-13
I have a Creative X-FI soundcard and this tutorial will get your card working!

Thanks a lot!

---

### Post by texasjim on 2008-03-15
Tumujin,
thanks for your quick reply. Everything went normally, oss installed, oss mixer on panel, no sound.
ossinfo shows 1 mixer device:

code:
Mixer devices
 0: ICH AC97 Mixer (ALC655) (Mixer 0 of device object 1),
 which is the same device in the mixer gui. The level meters show 
vmix0 outputs but vmix0 in level ????

I may be back to hardware/firmware, gonna keep lookin and tryin.

 Thanks,
   Jim

---

### Post by AJLobo on 2008-03-16
I followed the instructions and got my sound to work great in Gutsy -- there is some minor crackling, but I figured that's due to the beta version of the software. I also followed the steps to get flash working, but I still don't get sound in flash videos on Firefox. All the steps worked fine, but nothing changed.

I'm using:
Creative X-Fi XtremeGamer
Ubuntu 7.10 x64

I don't think I'm using the nspluginwrapper. Also not sure if my Firefox version is 64-bit.

Update: Nvm, sound in flash is now working :)

---

### Post by mevans336 on 2008-03-19
> **AJLobo said:**
> I followed the instructions and got my sound to work great in Gutsy -- there is some minor crackling, but I figured that's due to the beta version of the software. I also followed the steps to get flash working, but I still don't get sound in flash videos on Firefox. All the steps worked fine, but nothing changed.

I'm using:
Creative X-Fi XtremeGamer
Ubuntu 7.10 x64

I don't think I'm using the nspluginwrapper. Also not sure if my Firefox version is 64-bit.

Go into ossxmix and turn vmix0-src to medium. That fixed my crackling.

---

### Post by mevans336 on 2008-03-19
Thanks for the excellent write-up!

I can now get sound from Ubuntu and Virtualbox at the same time with my CMedia 6501! (What a crappy on-board soundcard. It even gave me trouble in Windows.)

I have a single, head scratching issue though. I can get sounds from everything, except the login/logout? I can play the login.wav, but when I go into System -> Preferences -> Sounds and hit play on the Login/Logout, heck, any of those sounds, nothing plays?

Any idea?

---

### Post by Subartu on 2008-03-23
Hello,

I have a Acer aspire 9920 and i read that OSS is working. But i follow all instructions but it isn't working Get the following thing : 
```
bart@Bart-laptop:~$ sudo dpkg -i /home/ oss-linux_v4.0-1014_i386.deb
dpkg-split: error reading /home/: Is a directory
dpkg: error processing /home/ (--install):
 subprocess dpkg-split returned error exit status 2
(Reading database ... 98603 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1014 (using oss-linux_v4.0-1014_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1014_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 /home/
 oss-linux_v4.0-1014_i386.deb

```

And no devices are detected but at  System >  Preferences > hardware information I can see the sound card.

```
bart@Bart-laptop:~$ ossinfo
Version info:   (0x00000000) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Bart-laptop)

Number of audio devices:        0
Number of audio engines:        0
Number of mixer devices:        0


Device objects


Mixer devices

Audio devices

```

And when i do sudo soundon I get the following thing

```
bart@Bart-laptop:~$ sudo soundon
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

I hope you can help me but with sound is better

---

### Post by Bogus83 on 2008-03-29
Hello,

I just attempted this method this morning, after a completely fresh install of Ubuntu 7.10.  I have a Soundblaster X-Fi Platinum.  The installation process worked without any issues.  The only odd thing I saw was when running the "sudo soundon" command from the failsafe terminal, I got back "OSS is already loaded."  However, when I run the OSSdetect -v command, I get the following:

```
Detected Creative SB X-Fi (EARLY BETA)
Detected Intel High Definition Audio (P35)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

```

So it sees my X-Fi, which seems good.  OSSinfo returns this:

```
Version info: OSS 4.0 (b1015/200803240317) (0x00040003) 
Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Bogus)

Number of audio devices:        12
Number of audio engines:        28
Number of mixer devices:        2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=615 (616)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1458a022
     Codec  2: ALC885 (0x10ec0885/0x1458a002)
 2: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=53844 (53844)
    PCI device 1102:0005, subdevice 1102:002c
 3: ossusb0 USB audio core services
 4: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio ALC885 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 2)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio rear                     /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio pcm4                     /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 5)
High Definition Audio rec         /dev/oss/hdaudio0/pcmin0  (device index 6)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin1  (device index 7)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin2  (device index 8)
High Definition Audio spdif-in    /dev/oss/hdaudio0/spdin0  (device index 9)
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 10)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 11)

```

Furthermore, launching "ossxmix -d1" opens a mixer window titled: "ossmix - device 1 / Sound Blaster X-Fi (SB046x/067x/076x)".

And yet there's still no sound.  I have rebooted, and when the system starts up I do get the speaker "pop" that implies initialization.. but there just isn't any sound.

Any ideas?  I'd really appreciate the help.  Thanks!

---

### Post by Bogus83 on 2008-03-29
Development:

On a whim I decided to execute "osstest" (lucky guess since I didn't know if tht was a valid command or not :) ).  It ran through the test for "Sound Adapter #-1", and nothing happened.  Then it got to "Sound Adapter #1" and I almost fell out of my chair when the music began playing because the volume was ALL the way up!

So.. my system is definitely capable of playing sound.  Is there some way to specify which sound adapter is used by default?  I think that may be my only remaining problem.

---

### Post by Conspi on 2008-03-30
Thanks, Temüjin!

Sound works perfectly now!.. well.. almost. I use laptop which has built in speakers. They work fine. But when I plug in my external speakers then it wont do anything.. just keeps playing from built in ones.

How would I change that?

---

### Post by Bogus83 on 2008-04-26
Hi Temüjin,

I recently installed the new release of Ubuntu 8.04, and followed the instructions on NullHead's post to get OSS working with my X-fi sound card.  I am using Hardy Heron 64-bit, and followed your instructions for the AMD64 flash sound fix.  I received no errors, but I still have no sound in flash.  Further, if I try to play any other sound while a flash video is running, I get "returned [null]".  That's not terribly important, as I've found installing Firefox through Wine allows me to play flash with sound quite nicely :) although if there is a fix, I'd be glad to hear it.  But my question is below:

I installed Clive's patch to fix the gnome-volume-control app, and while I CAN control the main volume (using my mouse) with that, I cannot use my media keys on my keyboard.  If you're interested, they output the following-
Mute- 0xa0
Vol up- 0xae
Vol down- 0xb0

Play/pause, next/back, and stop work fine.  However, when I press any of the other three listed above, I get the volume control window, with nothing at all in the bar representing volume.  So they're triggering something, but just not doing anything.  I've included a picture just in case I'm not being clear.  

If you have any advice on either issue I'd really appreciate it.  Thanks!
Bogus

---

### Post by temugen on 2008-04-29
> **Bogus83 said:**
> Hi Temüjin,

I recently installed the new release of Ubuntu 8.04, and followed the instructions on NullHead's post to get OSS working with my X-fi sound card.  I am using Hardy Heron 64-bit, and followed your instructions for the AMD64 flash sound fix.  I received no errors, but I still have no sound in flash.

I've found that in Ubuntu 8.04 I had to copy libflashsupport.so to /usr/lib32 to get sound to work in firefox with OSS. There may be a better way such as linking /usr/lib32/libflashsupport.so to /usr/lib/oss/lib/libflashsupport.so, but just copying it there will suffice.

P.S. I am not temujin, but I have used the name temugen for many years (derivative of Genghis Khan's birth name - temujin). Interesting...

---

### Post by feizex on 2008-05-01
> **Subartu said:**
> Hello,

I have a Acer aspire 9920 and i read that OSS is working. But i follow all instructions but it isn't working Get the following thing : 
```
bart@Bart-laptop:~$ sudo dpkg -i /home/ oss-linux_v4.0-1014_i386.deb
dpkg-split: error reading /home/: Is a directory
dpkg: error processing /home/ (--install):
 subprocess dpkg-split returned error exit status 2
(Reading database ... 98603 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1014 (using oss-linux_v4.0-1014_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1014_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 /home/
 oss-linux_v4.0-1014_i386.deb

```

Hi, if you are getting this error, it is because like me you tried installing the package without having disabled or removed existing sound drivers. Now your predicament is that you can neither reinstall or remove the package because whoever wrote it did not account for the case where it would remove the files and then fail (IE half install). The solution is this, unpack the DEB file. Inside it you will find a data folder. Inside that a usr folder. you need to copy those files and folders into your usr directory. Use commands like:
cd /usr
sudo cp -r /where_you_put_unpacked_files/data/usr/* .

There may be a neater way to do this, but this worked for me.

Then you need to remove package
sudo dpkg -r --force-all oss-linux

Then you should be able to install OK. Just remember to do all the preliminary sound driver removals before you do the install - that way it shouldn't fail and you won't be stuck again.

Regards,
Feizex. :)

---

### Post by kwatson512 on 2008-05-10
Temujin,

Thank you so much for the informative post.  This is in reply to your post #60 in this thread.  I'm almost there getting my Creative SB-XFi card to work.  I had to install the early beta OSS driver.  I have systems sounds, and can play DVDs and CDs.  I removed the non-functional volume control from the panel and used your procedure to install a custom application launcher on the panel.  Flash is the only thing not working now.  Movies play in Firefox, but without sound.

```
file /usr/lib/libflashsupport.so
```
returned "no such file or directory".
I commented out #define OPENSSL in the /usr/lib/oss/lib/flashsupport.c file, but when I tried 
```
cd /usr/lib/oss/lib; sudo cc -shared -02 -Wall -Werror flashsupport.c -o libflashsupport.so; sudo cp /usr/lib/oss/lib/libflashsupport.so /usr/lib/
```
I got:
```
cc: unrecognized option '-02'
```
Is there something I can substitute for "-02" or what steps should I take?

Linux Mint 4.0 (based on Gutsy Gibbon)
Dell XPS 400
Intel Pentium D 2.8 GHz
Dual-boot with WinXP Media Center Edition

---

### Post by kwatson512 on 2008-05-10
Quick update:  Just commenting out #define OPENSSL seems to have fixed my flash sound.  Now everything is working perfectly!  

Thank you!

---

### Post by kwatson512 on 2008-05-10
...except for one thing.  When I play .wav files in Amarok, there's an annoying tick in the right front speaker about once per second.  Any ideas?

---

### Post by bluestix on 2008-06-13
> **temugen said:**
> I've found that in Ubuntu 8.04 I had to copy libflashsupport.so to /usr/lib32 to get sound to work in firefox with OSS. There may be a better way such as linking /usr/lib32/libflashsupport.so to /usr/lib/oss/lib/libflashsupport.so, but just copying it there will suffice.

P.S. I am not temujin, but I have used the name temugen for many years (derivative of Genghis Khan's birth name - temujin). Interesting...


You are my hero. I have been trying tons of things to get sound to work in Flash. This worked perfectly.

Thank you much.

---

