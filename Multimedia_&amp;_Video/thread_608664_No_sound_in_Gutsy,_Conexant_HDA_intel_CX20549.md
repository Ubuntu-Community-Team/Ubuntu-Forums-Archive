---
title: "No sound in Gutsy, Conexant HDA intel CX20549"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by FlyingPenguin on 2007-11-10
So I have problems with my Intel HDA Conexant sound card.

Issue: Sound card is detected in Ubuntu 7.10 and 7.04., however, no sound produced at all in Ubuntu 7.10, 7.04 (as an aside, openSUSE 10.3 would not detect my card at all).

Laptop: Toshiba P100 ST9752

Card: Intel High Definition Audio, I believe Conexant CX20549 Venice (according to the Ubuntu sound volume GUI, then "File", then "Change Device").

I have tried several fixes, but none have worked. I am ready to start anew. Please help me out!

---

### Post by warmwaddle on 2007-11-10
I have the same problem. We even have the same computers! Bump fo you.

---

### Post by FlyingPenguin on 2007-11-10
Here are some things I ran based on other posts if they will help:

```
~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  18060  11 
sbs                    19592  0 
button                  8976  0 
container               5504  0 
dock                   10656  0 
battery                11012  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
nvidia               6221648  36 
snd_hda_intel         291488  1 
ipw3945               119840  1 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
i2c_core               26112  1 nvidia
pcmcia                 41388  0 
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
serio_raw               8068  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
sdhci                  18828  0 
shpchp                 34580  0 
psmouse                39952  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
mmc_core               28420  1 sdhci
soundcore               8800  1 snd
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
pci_hotplug            32704  1 shpchp
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  4 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
e1000                 126272  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Results of dmesg (what would show up)

```
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1839.403 MHz processor.
[   14.983516] Console: colour VGA+ 80x25
[   14.983770] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.984043] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.009181] Memory: 1026480k/1047104k available (2015k kernel code, 19960k reserved, 916k data, 364k init, 129600k highmem)
[   15.009189] virtual kernel memory layout:
[   15.009190]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.009191]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.009192]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.009193]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.009194]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.009195]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   15.009196]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   15.009199] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.009227] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.009359] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.009364] hpet0: 3 64-bit timers, 14318180 Hz
[   15.090278] Calibrating delay using timer specific routine.. 3682.85 BogoMIPS (lpj=7365714)
[   15.090295] Security Framework v1.0.0 initialized
[   15.090299] SELinux:  Disabled at boot.
[   15.090310] Mount-cache hash table entries: 512
[   15.090408] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   15.090415] monitor/mwait feature present.
[   15.090416] using mwait in idle threads.
[   15.090420] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.090422] CPU: L2 cache: 2048K
[   15.090424] CPU: Physical Processor ID: 0
[   15.090426] CPU: Processor Core ID: 0
[   15.090427] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   15.090435] Compat vDSO mapped to ffffe000.
[   15.090446] Checking 'hlt' instruction... OK.
[   15.106345] SMP alternatives: switching to UP code
[   15.106704] Early unpacking initramfs... done
[   15.405225] ACPI: Core revision 20070126
[   15.405230] Toshiba Satellite P100 detected: requires not _OSI(Linux)
[   15.405232] ACPI: Disabled _OSI(Linux)
[   15.405279] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.421618] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[   15.421633] SMP alternatives: switching to SMP code
[   15.421705] Booting processor 1/1 eip 3000
[   15.431893] Initializing CPU#1
[   15.509734] Calibrating delay using timer specific routine.. 3678.80 BogoMIPS (lpj=7357617)
[   15.509740] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   15.509744] monitor/mwait feature present.
[   15.509747] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.509749] CPU: L2 cache: 2048K
[   15.509751] CPU: Physical Processor ID: 0
[   15.509752] CPU: Processor Core ID: 1
[   15.509754] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   15.510237] CPU1: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[   15.510260] Total of 2 processors activated (7361.66 BogoMIPS).
[   15.510449] ENABLING IO-APIC IRQs
[   15.510647] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.657629] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.677618] Brought up 2 CPUs
[   15.829694] migration_cost=71
[   15.829812] Booting paravirtualized kernel on bare hardware
[   15.829896] Time:  9:38:12  Date: 10/11/107
[   15.829913] NET: Registered protocol family 16
[   15.829987] EISA bus registered
[   15.829991] ACPI: bus type pci registered
[   15.855108] PCI: PCI BIOS revision 2.10 entry at 0xfd704, last bus=11
[   15.855110] PCI: Using configuration type 1
[   15.855111] Setting up standard PCI resources
[   15.857737] ACPI: EC: Look up EC in DSDT
[   15.858392] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   15.938893] ACPI: System BIOS is requesting _OSI(Linux)
[   15.938895] ACPI: Please test with "acpi_osi=!Linux"
[   15.938896] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   15.939132] ACPI: Interpreter enabled
[   15.939134] ACPI: (supports S0 S3 S4 S5)
[   15.939148] ACPI: Using IOAPIC for interrupt routing
[   15.958166] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   15.958217] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.958225] PCI: Probing PCI hardware (bus 00)
[   15.958920] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.958924] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.960254] PCI: Transparent bridge - 0000:00:1e.0
[   15.960398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.960654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   15.960777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.960894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.961010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   15.961140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.969087] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.969206] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.969303] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.969399] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.969494] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   15.969589] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   15.969685] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.969780] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[   15.969912] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.969921] pnp: PnP ACPI init
[   15.969928] ACPI: bus type pnp registered
[   15.972055] pnp: PnP ACPI: found 9 devices
[   15.972057] ACPI: ACPI bus type pnp unregistered
[   15.972060] PnPBIOS: Disabled by ACPI PNP
[   15.972101] PCI: Using ACPI for IRQ routing
[   15.972103] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.972108] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   15.972201] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   15.972291] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   15.972380] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   15.972470] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   15.972559] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   15.972648] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   15.972738] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   15.972828] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   16.004923] NET: Registered protocol family 8
[   16.004925] NET: Registered protocol family 20
[   16.004971] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.004975] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.004977] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.004980] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.004986] pnp: 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.005099] Time: tsc clocksource has been installed.
[   16.005112] Switched to high resolution mode on CPU 0
[   16.005188] Switched to high resolution mode on CPU 1
[   16.035301] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[   16.035393] PCI: Bridge: 0000:00:01.0
[   16.035395]   IO window: 2000-2fff
[   16.035399]   MEM window: d0000000-d1ffffff
[   16.035402]   PREFETCH window: c0000000-cfffffff
[   16.035418] PCI: Bridge: 0000:00:1c.0
[   16.035421]   IO window: 3000-3fff
[   16.035427]   MEM window: 54000000-540fffff
[   16.035431]   PREFETCH window: disabled.
[   16.035447] PCI: Bridge: 0000:00:1c.1
[   16.035449]   IO window: disabled.
[   16.035454]   MEM window: 54100000-541fffff
[   16.035458]   PREFETCH window: disabled.
[   16.035464] PCI: Bridge: 0000:00:1c.2
[   16.035465]   IO window: disabled.
[   16.035471]   MEM window: disabled.
[   16.035475]   PREFETCH window: disabled.
[   16.035482] PCI: Bus 11, cardbus bridge: 0000:0a:04.0
[   16.035484]   IO window: 00004000-000040ff
[   16.035489]   IO window: 00004400-000044ff
[   16.035494]   PREFETCH window: 50000000-53ffffff
[   16.035500]   MEM window: 58000000-5bffffff
[   16.035505] PCI: Bridge: 0000:00:1e.0
[   16.035508]   IO window: 4000-4fff
[   16.035514]   MEM window: d2100000-d21fffff
[   16.035518]   PREFETCH window: 50000000-53ffffff
[   16.035534] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.035539] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.035560] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   16.035565] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.035572] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.035595] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[   16.035598] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   16.035605] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.035629] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.035636] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.035647] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   16.035653] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.035670] PCI: Enabling device 0000:0a:04.0 (0000 -> 0003)
[   16.035673] ACPI: PCI Interrupt 0000:0a:04.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.035682] PCI: Setting latency timer of device 0000:0a:04.0 to 64
[   16.035691] NET: Registered protocol family 2
[   16.080977] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.081026] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.081698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.081943] TCP: Hash tables configured (established 131072 bind 65536)
[   16.081945] TCP reno registered
[   16.097083] checking if image is initramfs... it is
[   16.685161] Freeing initrd memory: 7054k freed
[   16.685271] Simple Boot Flag at 0x36 set to 0x1
[   16.685718] audit: initializing netlink socket (disabled)
[   16.685734] audit(1194773892.364:1): initialized
[   16.685835] highmem bounce pool size: 64 pages
[   16.687521] VFS: Disk quotas dquot_6.5.1
[   16.687565] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.687647] io scheduler noop registered
[   16.687649] io scheduler anticipatory registered
[   16.687651] io scheduler deadline registered
[   16.687663] io scheduler cfq registered (default)
[   24.673635] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   24.673757] Boot video device is 0000:01:00.0
[   24.673833] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.673870] assign_interrupt_mode Found MSI capability
[   24.673872] Allocate Port Service[0000:00:01.0:pcie00]
[   24.673948] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.674006] assign_interrupt_mode Found MSI capability
[   24.674008] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.674035] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.674129] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.674187] assign_interrupt_mode Found MSI capability
[   24.674189] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.674218] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.674313] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.674370] assign_interrupt_mode Found MSI capability
[   24.674372] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.674399] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.674551] isapnp: Scanning for PnP cards...
[   25.028582] isapnp: No Plug & Play device found
[   25.048149] Real Time Clock Driver v1.12ac
[   25.048356] hpet_resources: 0xfed00000 is busy
[   25.048389] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.049398] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.049517] input: Macintosh mouse button emulation as /class/input/input0
[   25.049591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.051176] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.051181] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.051303] mice: PS/2 mouse device common for all mice
[   25.051392] EISA: Probing bus 0 at eisa.0
[   25.051399] Cannot allocate resource for EISA slot 1
[   25.051402] Cannot allocate resource for EISA slot 2
[   25.051404] Cannot allocate resource for EISA slot 3
[   25.051406] Cannot allocate resource for EISA slot 4
[   25.051424] EISA: Detected 0 cards.
[   25.051504] TCP cubic registered
[   25.051516] NET: Registered protocol family 1
[   25.051535] Using IPI No-Shortcut mode
[   25.051680]   Magic number: 15:390:626
[   25.051772]   hash matches device 0000:00:1b.0
[   25.051961] Freeing unused kernel memory: 364k freed
[   25.085132] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.230883] AppArmor: AppArmor initialized<5>audit(1194773901.864:2):  type=1505 info="AppArmor initialized" pid=1241
[   26.237814] fuse init (API version 7.8)
[   26.242591] Failure registering capabilities with primary security module.
[   26.274993] ACPI: SSDT 3FE92D9E, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[   26.275203] ACPI: SSDT 3FE92855, 04C4 (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[   26.275705] Monitor-Mwait will be used to enter C-1 state
[   26.275709] Monitor-Mwait will be used to enter C-2 state
[   26.275711] Monitor-Mwait will be used to enter C-3 state
[   26.275716] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   26.275932] ACPI: SSDT 3FE92F94, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20060912)
[   26.276128] ACPI: SSDT 3FE92D19, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20060912)
[   26.276657] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   11.156000] Marking TSC unstable due to: possible TSC halt in C2.
[   11.156000] ACPI: Thermal Zone [THRM] (54 C)
[   11.160000] Time: hpet clocksource has been installed.
[   11.612000] usbcore: registered new interface driver usbfs
[   11.612000] usbcore: registered new interface driver hub
[   11.612000] usbcore: registered new device driver usb
[   11.612000] USB Universal Host Controller Interface driver v3.0
[   11.612000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   11.612000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.612000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.612000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.612000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[   11.612000] usb usb1: configuration #1 chosen from 1 choice
[   11.612000] hub 1-0:1.0: USB hub found
[   11.612000] hub 1-0:1.0: 2 ports detected
[   11.636000] SCSI subsystem initialized
[   11.640000] libata version 2.21 loaded.
[   11.644000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   11.644000] Copyright (c) 1999-2006 Intel Corporation.
[   11.716000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   11.716000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.716000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.716000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.716000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[   11.716000] usb usb2: configuration #1 chosen from 1 choice
[   11.716000] hub 2-0:1.0: USB hub found
[   11.716000] hub 2-0:1.0: 2 ports detected
[   11.820000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.820000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.820000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.820000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.820000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   11.820000] usb usb3: configuration #1 chosen from 1 choice
[   11.820000] hub 3-0:1.0: USB hub found
[   11.820000] hub 3-0:1.0: 2 ports detected
[   11.924000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   11.924000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.924000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.924000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.924000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   11.924000] usb usb4: configuration #1 chosen from 1 choice
[   11.924000] hub 4-0:1.0: USB hub found
[   11.924000] hub 4-0:1.0: 2 ports detected
[   12.000000] Clocksource tsc unstable (delta = -276915687 ns)
[   12.028000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   12.028000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.028000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.028000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.028000] ehci_hcd 0000:00:1d.7: debug port 1
[   12.028000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.028000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd2504000
[   12.032000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.032000] usb usb5: configuration #1 chosen from 1 choice
[   12.032000] hub 5-0:1.0: USB hub found
[   12.032000] hub 5-0:1.0: 8 ports detected
[   12.136000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   12.136000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.136000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   12.196000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:16:36:e4:78:00
[   12.256000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   12.256000] ata_piix 0000:00:1f.2: version 2.11
[   12.256000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   12.412000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   12.412000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.412000] scsi0 : ata_piix
[   12.412000] scsi1 : ata_piix
[   12.412000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[   12.412000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[   12.576000] ata1.00: ATA-7: TOSHIBA MK1234GSX, AH001M, max UDMA/100
[   12.576000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   12.584000] ata1.00: configured for UDMA/100
[   12.668000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   12.848000] usb 3-1: configuration #1 chosen from 1 choice
[   12.904000] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.10, max UDMA/33
[   13.076000] ata2.00: configured for UDMA/33
[   13.076000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GS AH00 PQ: 0 ANSI: 5
[   13.076000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.10 PQ: 0 ANSI: 5
[   13.076000] PCI: Enabling device 0000:0a:04.1 (0000 -> 0002)
[   13.076000] ACPI: PCI Interrupt 0000:0a:04.1[A] -> GSI 17 (level, low) -> IRQ 17
[   13.076000] PCI: Setting latency timer of device 0000:0a:04.1 to 64
[   13.128000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d2102000-d21027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.132000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   13.132000] sd 0:0:0:0: [sda] Write Protect is off
[   13.132000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.132000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.132000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   13.132000] sd 0:0:0:0: [sda] Write Protect is off
[   13.132000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.132000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.132000]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.136000] Uniform CD-ROM driver Revision: 3.20
[   13.136000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.140000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.140000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.160000]  sda1 sda2 sda3 sda4
[   13.188000] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.536000] Attempting manual resume
[   13.536000] swsusp: Resume From Partition 8:3
[   13.536000] PM: Checking swsusp image.
[   13.548000] PM: Resume from disk failed.
[   13.588000] kjournald starting.  Commit interval 5 seconds
[   13.588000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.428000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.440000] intel_rng: FWH not detected
[   21.476000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.484000] PCI: Enabling device 0000:0a:04.2 (0000 -> 0002)
[   21.484000] ACPI: PCI Interrupt 0000:0a:04.2[A] -> GSI 17 (level, low) -> IRQ 17
[   21.484000] PCI: Setting latency timer of device 0000:0a:04.2 to 64
[   21.532000] Yenta: CardBus bridge found at 0000:0a:04.0 [1179:ff31]
[   21.532000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.532000] Yenta: Routing CardBus interrupts to PCI
[   21.532000] Yenta TI: socket 0000:0a:04.0, mfunc 0x01a21b22, devctl 0x66
[   21.580000] sdhci: Secure Digital Host Controller Interface driver
[   21.580000] sdhci: Copyright(c) Pierre Ossman
[   21.588000] iTCO_vendor_support: vendor-support=0
[   21.588000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   21.772000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   21.772000] Socket status: 30000006
[   21.772000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   21.772000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   21.772000] cs: IO port probe 0x4000-0x4fff: clean.
[   21.772000] pcmcia: parent PCI bridge Memory window: 0xd2100000 - 0xd21fffff
[   21.772000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   21.776000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.784000] sdhci: SDHCI controller found at 0000:0a:04.3 [104c:803c] (rev 0)
[   21.784000] PCI: Enabling device 0000:0a:04.3 (0000 -> 0002)
[   21.784000] ACPI: PCI Interrupt 0000:0a:04.3[A] -> GSI 17 (level, low) -> IRQ 17
[   21.784000] PCI: Setting latency timer of device 0000:0a:04.3 to 64
[   21.784000] mmc0: SDHCI at 0xd2102800 irq 17 DMA
[   21.928000] ieee80211_crypt: registered algorithm 'NULL'
[   21.936000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.936000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.016000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   22.016000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   22.016000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   22.016000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.016000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   22.016000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.108000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   22.108000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   22.128000] nvidia: module license 'NVIDIA' taints kernel.
[   22.140000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x82a0b1, caps: 0xb04713/0x60040d
[   22.140000] synaptics: Toshiba Satellite P100 detected, limiting rate to 40pps.
[   22.172000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.184000] cs: IO port probe 0x100-0x3af: clean.
[   22.184000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.188000] cs: IO port probe 0x820-0x8ff: clean.
[   22.188000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.188000] cs: IO port probe 0xa00-0xaff: clean.
[   22.196000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   22.196000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.384000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.384000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   22.384000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   22.832000] lp: driver loaded but no devices found
[   22.904000] Adding 2080408k swap on /dev/sda3.  Priority:-1 extents:1 across:2080408k
[   23.284000] EXT3 FS on sda4, internal journal
[   23.920000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   25.092000] ACPI: AC Adapter [ACAD] (on-line)
[   25.180000] ACPI: Battery Slot [BAT1] (battery present)
[   25.192000] No dock devices found.
[   25.344000] input: Power Button (FF) as /class/input/input3
[   25.344000] ACPI: Power Button (FF) [PWRF]
[   25.344000] input: Lid Switch as /class/input/input4
[   25.344000] ACPI: Lid Switch [LID]
[   25.372000] input: Power Button (CM) as /class/input/input5
[   25.372000] ACPI: Power Button (CM) [PWRB]
[   25.424000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.480000] ppdev: user-space parallel port driver
[   26.560000] audit(1194741517.471:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4990 profile="/usr/sbin/cupsd"
[   26.620000] apm: BIOS not found.
[   26.728000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   26.728000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   26.972000] Failure registering capabilities with primary security module.
[   27.184000] Bluetooth: Core ver 2.11
[   27.184000] NET: Registered protocol family 31
[   27.184000] Bluetooth: HCI device and connection manager initialized
[   27.184000] Bluetooth: HCI socket layer initialized
[   27.196000] Bluetooth: L2CAP ver 2.8
[   27.196000] Bluetooth: L2CAP socket layer initialized
[   27.284000] Bluetooth: RFCOMM socket layer initialized
[   27.284000] Bluetooth: RFCOMM TTY layer initialized
[   27.284000] Bluetooth: RFCOMM ver 1.8
[   31.884000] NET: Registered protocol family 17
[   34.504000] NET: Registered protocol family 10
[   34.504000] lo: Disabled Privacy Extensions
[   34.504000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   45.044000] eth0: no IPv6 routers present

```

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by natehatewindows on 2007-11-11
its a bug, no fix yet and looks like its going to be a long time.. do you have sound if you boot acpi=off?

here is the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

if you figure anything out post it please. :)

---

### Post by FlyingPenguin on 2007-11-11
How do I boot with it off?

---

### Post by natehatewindows on 2007-11-11
well you really dont want to do that. If you boot with it off you wil not be able to see your battery state and there is a really good chance your fans wont work and you will over heat. to try to see if it work for you do this

reboot and when grub comes up highlight the kernel and press "e", then you will get a litle grub looking menu and go to the one that starts with "kernel...." and press "e" add "acpi=off" and press "enter" and then you will be back to the grub like menu where you saw the "kernel....." now just press "b". 

its pretty easy and there is kind of instructions on how to do it.

---

### Post by natehatewindows on 2007-11-14
ok there is a temporary fix to this bug until a real one is released.
there are now complete files and instructions here at the bottom. you might want to hurry though becasue where the file is being hosted is only temporary until the guys bandwidth gets close to his limit and i would say that a 250 mg file could use that limit up fast.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by Yellow Pasque on 2007-11-14
Have you tried OSSv4? Conexant Audio support is included in there.

See my guide:
[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

### Post by zerofx on 2007-11-14
> **natehatewindows said:**
> its a bug, no fix yet and looks like its going to be a long time.. do you have sound if you boot acpi=off?

here is the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

if you figure anything out post it please. :)

No, even with acpi off there is no sound. I'm havin' the same issue.

---

### Post by natehatewindows on 2007-11-15
well if there is no sounds when acpi=off i think your not involved in this bug and i would try some other fixes. everyone in this bug has sound when acpi=off.

---

### Post by natehatewindows on 2007-11-15
> **Temüjin said:**
> Have you tried OSSv4? Conexant Audio support is included in there.

See my guide:
[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

so what problems were you having when you found this fix? im thinking about trying it but im a little nervous because everything i do to fix my sound messed up my winmodem driver.

---

### Post by Yellow Pasque on 2007-11-15
Well, I have an M-Audio Revolution 5.1. My headphone jack did not work and I always had to adjust sound after a reboot or the left speaker would be muted. Also, the volume control was pretty generic and separate channels relied on the same volume control. THe biggest thing that drove me to OSS was the problems I had with ALSA and WINE.  I use foobar2000 under WINE as my primary music player and ALSA didn't want to work that. I tried building the latest version of jthe ALSA

I can't guarantee that OSS will fix your problems, but it usually has cleaner code and working features, even if they're not the latest. IMO, it's worth a shot. I don't see how this would bork your modem unless perhaps you have a sound/modem combo.

---

### Post by natehatewindows on 2007-11-15
yes, my modem is on my sounds card :( i just dont know what to do at this point....im lost and getting frustrated about not having sound. everyhting but sound works so well right now...i just want that sound. as said before i have sound with acpi=off but then my fans dont work and i dont have battery state....so i guess im just going to wait for a fix and find a different distro to dual boot for now until gusty is fixed.

---

### Post by Yellow Pasque on 2007-11-15
> **natehatewindows said:**
> yes, my modem is on my sounds card :( i just dont know what to do at this point....im lost and getting frustrated about not having sound. everyhting but sound works so well right now...i just want that sound. as said before i have sound with acpi=off but then my fans dont work and i dont have battery state....so i guess im just going to wait for a fix and find a different distro to dual boot for now until gusty is fixed.

Good luck with that. I'm not sure, but I think you'll have the same problem with other distros since the problem is with ALSA. I kept waiting and waiting for ALSA to get the headphone jack working on my card and fix the annoying volume bug. (Those bugs are still in ALSA 1.0.15)

---

### Post by natehatewindows on 2007-11-15
well in past ditros the dsdt.aml fix fixed the problems but it wont work in gusty....and i think actually mandriva works fine from what i have read....

here is my bug they talk about it there.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by FlyingPenguin on 2007-11-15
I am really confused with this whole mess. Is there a working fix for the ST9752? I saw something about custom DSDT files (which I still don't know what they are) but there was not one for the 9752. There was one for the 9762 but will it work and do I need it anyway?

Does the OSS thing work on the 9752?

---

### Post by natehatewindows on 2007-11-15
honestly man this whole thing is a mess. 

what i would do, it do the custom dsdt thing with one of the link on the bug site and download the "fix" file.....just do the instructions as said on the bug site and im sure it will work for you. yes you do need the dsdt. the only reason it wont work for me is i have a minmodem for my dialup internet :(

---

### Post by Chii on 2007-11-30
Currently I also have a p100 st9752, and before I had to send it in for repairs (the GPU went caput) I had Ubuntu installed and had to use the dsdt for the bios.  But since I've had it returned they ever so kindly upgraded my bios for me ](*,) .

So now, I am currently using Vista until I can find a DSDT file, or that it is confirmed that the bios has finally been fixed so that acpi no longer blacklists my bios and prevents my computer from working as it should :/

---

### Post by twizler on 2008-01-04
No sound intel card WHEN NOTHING else worked ! ! 

script from : antonywilliams.com
gusty no sound  intel hda sound card - DELL gusty no sound 
Did a gusty update and then no sound. THIS IS THE ONLY THING THAT WORKED!!! 
 
THIS IS A DO IT FOR YOU NOW WORK SCRIPT -- COPY PASTE and you get sound!!! 
> just copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh 
> sudo gedit -- then copy - paste into it. 
>  then cd to it in a terminal and type "sudo sh alsa_1.sh"
then reboot, and>  then type "sudo sh alsa_2.sh"
> (make sure the scripts have execute privileges. (by typing "chmod a+x alsa_1.sh")
>  
#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1

  
> 
to run -- in terminal window ---[QUOTE] sh alsa_1.sh  (or what you named the file you copied and pasted)[/QUOTE]
  > 
#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2
  

---

### Post by bb44wsu on 2008-01-04
Try installing Hardy Heron. Works out of the box.  Gnome seems to be broken, if so use kde until it is fixed. "sudo apt-get install kde"  [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

---

### Post by Yellow Pasque on 2008-01-04
> **bb44wsu said:**
> Try installing Hardy Heron. Works out of the box.  Gnome seems to be broken, if so use kde until it is fixed. "sudo apt-get install kde"  [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)
At least try OSSv4 before doing that. No Gnome? Damn, I was about to try Hardy out too.

---

### Post by jtstriker3 on 2008-01-05
Gnome might work fine, it seemed to get hung for awhile and then it would load. extremely annoying.  To get it to even boot into gnome we had to disable composite from the X config file.  However we were using a very new laptop HP dv2660se with the new intel x3100 graphics.  So others would probably have better luck.  KDE worked like a champ though.

---

### Post by XanStarcloud on 2008-01-19
Does anyone know if there has been a bug fix release for this??? I've tried everything I can think of.

---

### Post by Chii on 2008-02-24
If you need a fix for this and have a p100-st9752 try this:  [http://ubuntuforums.org/showthread.php?t=349491&page=13](http://ubuntuforums.org/showthread.php?t=349491&page=13)

---

