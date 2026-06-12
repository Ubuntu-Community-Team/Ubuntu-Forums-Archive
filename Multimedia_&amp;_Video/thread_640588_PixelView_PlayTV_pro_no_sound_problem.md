---
title: "PixelView PlayTV pro no sound problem"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by mimo74 on 2007-12-14
Hello,

I have a problem with my TV tuner. It is a PixelView PlayTVpro (prolink) with FM radio it has the BT878 (PV-BT878P+(w/FM & w/o FM). OS Ubuntu 7.10.

After searching on the internet I got my TV tuner to work and the image quality is super! 

with :

modprobe bttv card=139 tuner=69 radio=1

BUT the sound is not working. It has something with the card or the tuner value selection? I tried the modprobe snd_bt87x  it replies FATAL: Module snd_bt87x not found.

computer@PC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ipv6                  273892  8 
af_packet              24840  2 
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
sbs                    19592  0 
button                  8976  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
bt878                  11832  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
tuner                  63144  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
analog                 13344  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
gameport               16776  1 analog
nvidia               4716468  32 
bttv                  177012  1 bt878
video_buf              26244  1 bttv
ir_common              35460  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7428  1 bttv
btcx_risc               5896  1 bttv
tveeprom               16784  1 bttv
videodev               29312  1 bttv
v4l2_common            18432  3 tuner,bttv,videodev
v4l1_compat            15364  2 bttv,videodev
i2c_core               26112  5 tuner,nvidia,bttv,i2c_algo_bit,tveeprom
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  7 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
floppy                 60004  0 
ehci_hcd               36492  0 
e100                   37644  0 
mii                     6528  1 e100
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor


computer@PC:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C50 checksum 0
[    0.000000] ACPI: RSDP 000F6C50, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 1FFF3000, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 3D87 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=a01c7c18-80dc-4331-bd47-84d0278ff7bd ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1297.537 MHz processor.
[   32.350882] Console: colour VGA+ 80x25
[   32.352218] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.353762] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.402174] Memory: 507920k/524224k available (2015k kernel code, 15708k reserved, 916k data, 364k init, 0k highmem)
[   32.402193] virtual kernel memory layout:
[   32.402195]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   32.402198]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.402200]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   32.402202]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   32.402205]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   32.402207]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   32.402209]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   32.402215] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.402290] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   32.482301] Calibrating delay using timer specific routine.. 2596.93 BogoMIPS (lpj=5193877)
[   32.482356] Security Framework v1.0.0 initialized
[   32.482374] SELinux:  Disabled at boot.
[   32.482403] Mount-cache hash table entries: 512
[   32.482654] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   32.482673] CPU: L1 I cache: 16K, L1 D cache: 16K
[   32.482678] CPU: L2 cache: 256K
[   32.482684] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   32.482702] Compat vDSO mapped to ffffe000.
[   32.482726] Checking 'hlt' instruction... OK.
[   32.498499] SMP alternatives: switching to UP code
[   32.498845] Freeing SMP alternatives: 11k freed
[   32.499411] Early unpacking initramfs... done
[   33.111552] ACPI: Core revision 20070126
[   33.111799] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.114720] ACPI: setting ELCR to 0200 (from 1e20)
[   33.117106] CPU0: Intel(R) Celeron(TM) CPU                1300MHz stepping 01
[   33.117119] SMP motherboard not detected.
[   33.117124] Local APIC not detected. Using dummy APIC emulation.
[   33.117225] Brought up 1 CPUs
[   33.117536] Booting paravirtualized kernel on bare hardware
[   33.117655] Time: 17:20:55  Date: 11/14/107
[   33.117734] NET: Registered protocol family 16
[   33.118029] EISA bus registered
[   33.118057] ACPI: bus type pci registered
[   33.145756] PCI: PCI BIOS revision 2.10 entry at 0xfb190, last bus=2
[   33.145762] PCI: Using configuration type 1
[   33.145765] Setting up standard PCI resources
[   33.149653] ACPI: EC: Look up EC in DSDT
[   33.155520] ACPI: Interpreter enabled
[   33.155530] ACPI: (supports S0 S1 S4 S5)
[   33.155560] ACPI: Using PIC for interrupt routing
[   33.164500] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.164517] PCI: Probing PCI hardware (bus 00)
[   33.164798] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[   33.164805] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[   33.165483] PCI: Firmware left 0000:02:0c.0 e100 interrupts enabled, disabling
[   33.165719] PCI: Transparent bridge - 0000:00:1e.0
[   33.165768] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.165986] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   33.188402] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   33.188587] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   33.188762] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   33.188938] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   33.189113] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   33.189290] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   33.189483] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   33.189660] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   33.189852] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.189891] pnp: PnP ACPI init
[   33.189915] ACPI: bus type pnp registered
[   33.195764] pnp: PnP ACPI: found 13 devices
[   33.195771] ACPI: ACPI bus type pnp unregistered
[   33.195781] PnPBIOS: Disabled by ACPI PNP
[   33.195921] PCI: Using ACPI for IRQ routing
[   33.195928] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.215975] NET: Registered protocol family 8
[   33.215979] NET: Registered protocol family 20
[   33.216166] pnp: 00:00: iomem range 0xd0800-0xd3fff has been reserved
[   33.216173] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   33.216178] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   33.216183] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   33.218143] Time: tsc clocksource has been installed.
[   33.246781] PCI: Bridge: 0000:00:01.0
[   33.246785]   IO window: disabled.
[   33.246793]   MEM window: dc000000-ddffffff
[   33.246799]   PREFETCH window: d0000000-d7ffffff
[   33.246811] PCI: Bridge: 0000:00:1e.0
[   33.246815]   IO window: c000-cfff
[   33.246823]   MEM window: de000000-dfffffff
[   33.246829]   PREFETCH window: e0000000-e00fffff
[   33.246852] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   33.246906] NET: Registered protocol family 2
[   33.286220] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   33.286343] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   33.287135] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   33.287863] TCP: Hash tables configured (established 16384 bind 16384)
[   33.287871] TCP reno registered
[   33.298517] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   33.756737]  it is
[   34.412057] Freeing initrd memory: 7334k freed
[   34.413046] audit: initializing netlink socket (disabled)
[   34.413083] audit(1197652855.820:1): initialized
[   34.417666] VFS: Disk quotas dquot_6.5.1
[   34.417920] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.418217] io scheduler noop registered
[   34.418223] io scheduler anticipatory registered
[   34.418227] io scheduler deadline registered
[   34.418283] io scheduler cfq registered (default)
[   34.418359] Boot video device is 0000:01:00.0
[   34.418813] isapnp: Scanning for PnP cards...
[   34.772603] isapnp: No Plug & Play device found
[   34.844879] Real Time Clock Driver v1.12ac
[   34.845065] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.845195] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.845641] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.847085] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.847638] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.849231] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.849876] input: Macintosh mouse button emulation as /class/input/input0
[   34.850036] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   34.850043] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   35.101887] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.102214] mice: PS/2 mouse device common for all mice
[   35.102455] EISA: Probing bus 0 at eisa.0
[   35.102484] Cannot allocate resource for EISA slot 4
[   35.102489] Cannot allocate resource for EISA slot 5
[   35.102504] EISA: Detected 0 cards.
[   35.102715] TCP cubic registered
[   35.102756] NET: Registered protocol family 1
[   35.102818] Using IPI No-Shortcut mode
[   35.103225]   Magic number: 3:164:340
[   35.103265]   hash matches device ttyzf
[   35.104828] Freeing unused kernel memory: 364k freed
[   35.133727] input: AT Translated Set 2 keyboard as /class/input/input1
[   36.538573] AppArmor: AppArmor initialized<5>audit(1197652857.820:2):  type=1505 info="AppArmor initialized" pid=1178
[   36.553070] fuse init (API version 7.8)
[   36.564505] Failure registering capabilities with primary security module.
[   36.582903] ACPI: Fan [FAN] (on)
[   36.595446] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   36.595458] ACPI: Processor [CPU0] (supports 2 throttling states)
[   36.599163] ACPI: Thermal Zone [THRM] (45 C)
[   38.121488] usbcore: registered new interface driver usbfs
[   38.121542] usbcore: registered new interface driver hub
[   38.121591] usbcore: registered new device driver usb
[   38.124361] USB Universal Host Controller Interface driver v3.0
[   38.124990] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   38.124997] PCI: setting IRQ 10 as level-triggered
[   38.125003] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   38.125026] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   38.125033] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   38.125350] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   38.125392] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000d000
[   38.125679] usb usb1: configuration #1 chosen from 1 choice
[   38.125731] hub 1-0:1.0: USB hub found
[   38.125746] hub 1-0:1.0: 2 ports detected
[   38.186353] SCSI subsystem initialized
[   38.203027] libata version 2.21 loaded.
[   38.229453] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   38.229464] PCI: setting IRQ 5 as level-triggered
[   38.229469] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   38.229491] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   38.229497] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   38.229550] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   38.229590] uhci_hcd 0000:00:1f.4: irq 5, io base 0x0000d800
[   38.229827] usb usb2: configuration #1 chosen from 1 choice
[   38.229882] hub 2-0:1.0: USB hub found
[   38.229898] hub 2-0:1.0: 2 ports detected
[   38.275504] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   38.275513] e100: Copyright(c) 1999-2006 Intel Corporation
[   38.333425] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   38.333436] PCI: setting IRQ 12 as level-triggered
[   38.333442] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   38.333464] uhci_hcd 0000:02:0d.0: UHCI Host Controller
[   38.333596] uhci_hcd 0000:02:0d.0: new USB bus registered, assigned bus number 3
[   38.333635] uhci_hcd 0000:02:0d.0: irq 12, io base 0x0000c400
[   38.333861] usb usb3: configuration #1 chosen from 1 choice
[   38.333915] hub 3-0:1.0: USB hub found
[   38.333933] hub 3-0:1.0: 2 ports detected
[   38.437385] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   38.437396] PCI: setting IRQ 9 as level-triggered
[   38.437401] ACPI: PCI Interrupt 0000:02:0d.1[B] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   38.437423] uhci_hcd 0000:02:0d.1: UHCI Host Controller
[   38.437481] uhci_hcd 0000:02:0d.1: new USB bus registered, assigned bus number 4
[   38.437520] uhci_hcd 0000:02:0d.1: irq 9, io base 0x0000c800
[   38.437745] usb usb4: configuration #1 chosen from 1 choice
[   38.437798] hub 4-0:1.0: USB hub found
[   38.437816] hub 4-0:1.0: 2 ports detected
[   38.467223] Floppy drive(s): fd0 is 1.44M
[   38.468676] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   38.525367] FDC 0 is a post-1991 82077
[   38.542138] ata_piix 0000:00:1f.1: version 2.11
[   38.542276] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   38.542680] scsi0 : ata_piix
[   38.542788] scsi1 : ata_piix
[   38.543010] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   38.543017] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   38.643498] usb 1-1: configuration #1 chosen from 1 choice
[   38.712929] ata1.00: ATA-7: ExcelStor Technology J880, PF2OA21B, max UDMA/133
[   38.712940] ata1.00: 160836480 sectors, multi 16: LBA48 
[   38.736924] ata1.00: configured for UDMA/100
[    6.440000] Marking TSC unstable due to: possible TSC halt in C2.
[    6.444000] Time: acpi_pm clocksource has been installed.
[    6.684000] ata2.00: ATAPI: _NEC CD-RW NR-9100A, 2.12, max UDMA/33
[    6.772000] usbcore: registered new interface driver hiddev
[    6.784000] input: A4Tech USB Optical Mouse as /class/input/input2
[    6.784000] input: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1f.2-1
[    6.784000] usbcore: registered new interface driver usbhid
[    6.784000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.880000] ata2.00: configured for UDMA/33
[    6.880000] scsi 0:0:0:0: Direct-Access     ATA      ExcelStor Techno PF2O PQ: 0 ANSI: 5
[    6.880000] scsi 1:0:0:0: CD-ROM            _NEC     CD-RW NR-9100A   2.12 PQ: 0 ANSI: 5
[    6.884000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    6.884000] PCI: setting IRQ 11 as level-triggered
[    6.884000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.908000] e100: eth0: e100_probe: addr 0xe0002000, irq 11, MAC addr 00:08:C7:99:C4:A6
[    6.908000] ACPI: PCI Interrupt 0000:02:0d.2[C] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    6.908000] ehci_hcd 0000:02:0d.2: EHCI Host Controller
[    6.908000] ehci_hcd 0000:02:0d.2: new USB bus registered, assigned bus number 5
[    6.908000] ehci_hcd 0000:02:0d.2: irq 10, io mem 0xdf120000
[    6.908000] ehci_hcd 0000:02:0d.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.908000] usb usb5: configuration #1 chosen from 1 choice
[    6.908000] hub 5-0:1.0: USB hub found
[    6.908000] hub 5-0:1.0: 4 ports detected
[    7.052000] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[    7.056000] sd 0:0:0:0: [sda] Write Protect is off
[    7.056000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.056000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.056000] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[    7.056000] sd 0:0:0:0: [sda] Write Protect is off
[    7.056000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.056000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.056000]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    7.116000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.128000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.128000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.180000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    7.180000] Uniform CD-ROM driver Revision: 3.20
[    7.180000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.548000] Attempting manual resume
[    7.548000] swsusp: Resume From Partition 8:6
[    7.548000] PM: Checking swsusp image.
[    7.564000] PM: Resume from disk failed.
[    7.632000] kjournald starting.  Commit interval 5 seconds
[    7.632000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.152000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.156000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.240000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.284000] agpgart: Detected an Intel i815 Chipset.
[   18.288000] agpgart: AGP aperture is 64M @ 0xd8000000
[   18.296000] iTCO_vendor_support: vendor-support=0
[   18.300000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   18.300000] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   18.300000] iTCO_wdt: No card detected
[   18.312000] intel_rng: FWH not detected
[   19.316000] Linux video capture interface: v2.00
[   19.564000] bttv: driver version 0.9.17 loaded
[   19.564000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.564000] bttv: Bt8xx card found (0).
[   19.564000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   19.564000] bttv0: Bt878 (rev 17) at 0000:02:09.0, irq: 12, latency: 32, mmio: 0xe0000000
[   19.564000] bttv0: using: Prolink PixelView PlayTV MPEG2 PV-M4900 [card=139,insmod option]
[   19.564000] bttv0: gpio: en=00000000, out=00000000 in=00afc0ff [init]
[   20.940000] nvidia: module license 'NVIDIA' taints kernel.
[   21.220000] input: PC Speaker as /class/input/input3
[   21.396000] bttv0: using tuner=69
[   21.396000] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>parport_pc 00:0a: reported by Plug and Play ACPI
[   21.444000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   21.644000] not found
[   21.644000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   21.960000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   22.024000] tuner 0-0060: TEA5767 detected.
[   22.024000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   22.028000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   22.028000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   22.028000] tuner 0-0061: type set to 69 (Tena TNF 5335 and similar models)
[   22.028000] tuner 0-0061: type set to 69 (Tena TNF 5335 and similar models)
[   22.056000] bttv0: registered device video0
[   22.056000] bttv0: registered device vbi0
[   22.056000] bttv0: registered device radio0
[   22.056000] bttv0: PLL: 28636363 => 35468950 .. ok
[   22.088000] input: bttv IR (card=139) as /class/input/input4
[   22.088000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   22.088000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.112000] bt878: AUDIO driver version 0.0.0 loaded
[   22.412000] intel8x0_measure_ac97_clock: measured 54887 usecs
[   22.412000] intel8x0: clocking to 48000
[   22.412000] bt878: Bt878 AUDIO function found (0).
[   22.412000] ACPI: PCI Interrupt 0000:02:09.1[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   22.412000] bt878_probe: card id=[0x0], Unknown card.
[   22.412000] Exiting..
[   22.412000] ACPI: PCI interrupt for device 0000:02:09.1 disabled
[   22.412000] bt878: probe of 0000:02:09.1 failed with error -22
[   22.412000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.412000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   23.800000] lp0: using parport0 (interrupt-driven).
[   23.880000] Adding 682720k swap on /dev/sda6.  Priority:-1 extents:1 across:682720k
[   24.372000] EXT3 FS on sda7, internal journal
[   26.540000] No dock devices found.
[   26.772000] input: Power Button (FF) as /class/input/input5
[   26.784000] ACPI: Power Button (FF) [PWRF]
[   26.844000] input: Power Button (CM) as /class/input/input6
[   26.844000] ACPI: Power Button (CM) [PWRB]
[   26.876000] input: Sleep Button (CM) as /class/input/input7
[   26.876000] ACPI: Sleep Button (CM) [SLPB]
[   29.112000] ppdev: user-space parallel port driver
[   29.272000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   29.700000] audit(1197649283.831:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4631 profile="/usr/sbin/cupsd"
[   29.792000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   29.792000] apm: overridden by ACPI.
[   30.332000] Failure registering capabilities with primary security module.
[   31.856000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   31.856000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   31.856000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   34.908000] NET: Registered protocol family 17
[   40.800000] NET: Registered protocol family 10
[   40.800000] lo: Disabled Privacy Extensions
[   41.720000] eth0: duplicate address detected!
[ 1676.504000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[ 1676.668000] usb 5-1: configuration #1 chosen from 1 choice
[ 1678.504000] usbcore: registered new interface driver libusual
[ 1679.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1679.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1679.704000] Initializing USB Mass Storage driver...
[ 1679.704000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1679.708000] usb-storage: device found at 2
[ 1679.708000] usb-storage: waiting for device to settle before scanning
[ 1679.708000] usbcore: registered new interface driver usb-storage
[ 1679.708000] USB Mass Storage support registered.
[ 1684.708000] usb-storage: device scan complete
[ 1684.712000] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[ 1684.736000] sd 2:0:0:0: [sdb] 1971200 512-byte hardware sectors (1009 MB)
[ 1684.740000] sd 2:0:0:0: [sdb] Write Protect is off
[ 1684.740000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1684.740000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1684.752000] sd 2:0:0:0: [sdb] 1971200 512-byte hardware sectors (1009 MB)
[ 1684.752000] sd 2:0:0:0: [sdb] Write Protect is off
[ 1684.752000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1684.752000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1684.752000]  sdb: sdb1
[ 1684.756000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1684.756000] sd 2:0:0:0: Attached scsi generic sg2 type 0



Any help will be apreciated.

Thank you.

---

### Post by mimo74 on 2007-12-15
Any idea??? I tried a lot of things and always the same :(

---

