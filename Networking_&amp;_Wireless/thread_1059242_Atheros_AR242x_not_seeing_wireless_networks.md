---
title: "Atheros AR242x not seeing wireless networks"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by Mriswithe on 2009-02-03
On a fresh install of ubuntu 8.10 it appears to recognise my wireless because if I go to hardware drivers it shows "Support for Atheros 802.11 wireless lan cards." which is an ubuntu distributed driver. left clicking on networking only recognizes that a wired connection exists. I am fairly inexperienced with ubuntu and linux. Following the directions for opening a wireless post. The wireless built into my laptop doesn't have a hard switch, it has a button that in windows changes color when enabled/disabled. pressing the button does not seem to change anything color or ubuntu seeing or not seeing my wireless.

Any help would be much appreciated.

brand/model Compaq cq-220us

--LSPCI:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

--ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1f:16:5e:77:f4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe5e:77f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8371 errors:0 dropped:144886389 overruns:0 frame:0
          TX packets:7748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10217982 (10.2 MB)  TX bytes:1020724 (1.0 MB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

--iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

--lsmod

```
Module                  Size  Used by
usbhid                 35840  0 
hid                    50560  1 usbhid
ipv6                  263972  14 
i915                   38528  2 
drm                    86056  3 i915
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
serio_raw              13444  0 
pcspkr                 10624  0 
psmouse                45200  0 
evdev                  17696  10 
snd_hda_intel         384176  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
battery                18436  0 
ac                     12292  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
button                 14224  0 
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
soundcore              15328  1 snd
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
usb_storage            82752  0 
libusual               30356  1 usb_storage
sg                     39732  0 
ahci                   37132  2 
libata                178208  1 ahci
scsi_mod              155212  5 sr_mod,sd_mod,usb_storage,sg,libata
dock                   16656  1 libata
r8169                  36100  0 
mii                    13440  1 r8169
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```
--dmesg
```

[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017715] ACPI: Core revision 20080609
[    0.021238] ACPI: Checking initramfs for custom DSDT
[    0.340254] ENABLING IO-APIC IRQs
[    0.340444] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.381475] CPU0: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz stepping 0d
[    0.384024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4322.50 BogoMIPS (lpj=8645018)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.468380] CPU1: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz stepping 0d
[    0.468396] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.472048] Brought up 2 CPUs
[    0.472050] Total of 2 processors activated (8644.94 BogoMIPS).
[    0.472070] CPU0 attaching sched-domain:
[    0.472073]  domain 0: span 0-1 level MC
[    0.472076]   groups: 0 1
[    0.472082] CPU1 attaching sched-domain:
[    0.472084]  domain 0: span 0-1 level MC
[    0.472086]   groups: 1 0
[    0.472161] net_namespace: 840 bytes
[    0.472161] Booting paravirtualized kernel on bare hardware
[    0.472277] Time: 19:58:22  Date: 02/03/09
[    0.472304] NET: Registered protocol family 16
[    0.472322] EISA bus registered
[    0.472322] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.472322] ACPI: bus type pci registered
[    0.472322] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.472322] PCI: MCFG area at f8000000 reserved in E820
[    0.472322] PCI: Using MMCONFIG for extended config space
[    0.472322] PCI: Using configuration type 1 for base access
[    0.473550] ACPI: EC: Look up EC in DSDT
[    0.480255] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.480660] ACPI: Interpreter enabled
[    0.480665] ACPI: (supports S0 S3 S4 S5)
[    0.480686] ACPI: Using IOAPIC for interrupt routing
[    0.480766] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.528634] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.528634] ACPI: EC: driver started in interrupt mode
[    0.528634] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.528634] PCI: 0000:00:02.0 reg 10 64bit mmio: [90000000, 903fffff]
[    0.528634] PCI: 0000:00:02.0 reg 18 64bit mmio: [80000000, 8fffffff]
[    0.528634] PCI: 0000:00:02.0 reg 20 io port: [5110, 5117]
[    0.528634] PCI: 0000:00:02.1 reg 10 64bit mmio: [92500000, 925fffff]
[    0.528634] PCI: 0000:00:1a.0 reg 20 io port: [50e0, 50ff]
[    0.528634] PCI: 0000:00:1a.1 reg 20 io port: [50c0, 50df]
[    0.528634] PCI: 0000:00:1a.2 reg 20 io port: [50a0, 50bf]
[    0.528634] PCI: 0000:00:1a.7 reg 10 32bit mmio: [94705c00, 94705fff]
[    0.528634] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.528634] pci 0000:00:1a.7: PME# disabled
[    0.528664] PCI: 0000:00:1b.0 reg 10 64bit mmio: [94700000, 94703fff]
[    0.528719] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.528724] pci 0000:00:1b.0: PME# disabled
[    0.528797] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.528802] pci 0000:00:1c.0: PME# disabled
[    0.528874] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.528879] pci 0000:00:1c.1: PME# disabled
[    0.528949] PCI: 0000:00:1d.0 reg 20 io port: [5080, 509f]
[    0.529037] PCI: 0000:00:1d.1 reg 20 io port: [5060, 507f]
[    0.529125] PCI: 0000:00:1d.2 reg 20 io port: [5040, 505f]
[    0.529215] PCI: 0000:00:1d.7 reg 10 32bit mmio: [94705800, 94705bff]
[    0.529277] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.529283] pci 0000:00:1d.7: PME# disabled
[    0.529515] PCI: 0000:00:1f.2 reg 10 io port: [5108, 510f]
[    0.529523] PCI: 0000:00:1f.2 reg 14 io port: [511c, 511f]
[    0.529531] PCI: 0000:00:1f.2 reg 18 io port: [5100, 5107]
[    0.529539] PCI: 0000:00:1f.2 reg 1c io port: [5118, 511b]
[    0.529547] PCI: 0000:00:1f.2 reg 20 io port: [5020, 503f]
[    0.529555] PCI: 0000:00:1f.2 reg 24 32bit mmio: [94705000, 947057ff]
[    0.529592] pci 0000:00:1f.2: PME# supported from D3hot
[    0.529597] pci 0000:00:1f.2: PME# disabled
[    0.529624] PCI: 0000:00:1f.3 reg 10 64bit mmio: [94706000, 947060ff]
[    0.529645] PCI: 0000:00:1f.3 reg 20 io port: [5000, 501f]
[    0.529719] PCI: 0000:00:1f.6 reg 10 64bit mmio: [94704000, 94704fff]
[    0.529842] PCI: 0000:01:00.0 reg 10 io port: [3000, 30ff]
[    0.529870] PCI: 0000:01:00.0 reg 18 64bit mmio: [90410000, 90410fff]
[    0.529890] PCI: 0000:01:00.0 reg 20 64bit mmio: [90400000, 9040ffff]
[    0.529901] PCI: 0000:01:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.529940] pci 0000:01:00.0: supports D1
[    0.529942] pci 0000:01:00.0: supports D2
[    0.529944] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529950] pci 0000:01:00.0: PME# disabled
[    0.530005] PCI: bridge 0000:00:1c.0 io port: [3000, 4fff]
[    0.530010] PCI: bridge 0000:00:1c.0 32bit mmio: [93700000, 946fffff]
[    0.530018] PCI: bridge 0000:00:1c.0 64bit mmio pref: [90400000, 914fffff]
[    0.530092] PCI: 0000:02:00.0 reg 10 64bit mmio: [92600000, 9260ffff]
[    0.530226] PCI: bridge 0000:00:1c.1 io port: [2000, 2fff]
[    0.530231] PCI: bridge 0000:00:1c.1 32bit mmio: [92600000, 936fffff]
[    0.530240] PCI: bridge 0000:00:1c.1 64bit mmio pref: [91500000, 924fffff]
[    0.530311] pci 0000:00:1e.0: transparent bridge
[    0.530346] bus 00 -> node 0
[    0.530356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.532533] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.532710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.532911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.536241] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.536321] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.536487] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.536652] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.536816] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.536981] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.537145] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.537309] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.537409] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.537409] pnp: PnP ACPI init
[    0.537409] ACPI: bus type pnp registered
[    0.540685] pnp: PnP ACPI: found 9 devices
[    0.540685] ACPI: ACPI bus type pnp unregistered
[    0.540685] PnPBIOS: Disabled by ACPI PNP
[    0.540685] PCI: Using ACPI for IRQ routing
[    0.548040] NET: Registered protocol family 8
[    0.548043] NET: Registered protocol family 20
[    0.548057] NetLabel: Initializing
[    0.548057] NetLabel:  domain hash size = 128
[    0.548057] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.548064] NetLabel:  unlabeled traffic allowed by default
[    0.548072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.548078] hpet0: 4 64-bit timers, 14318180 Hz
[    0.549947] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.549950]    actual entries 65620
[    0.550056] AppArmor: AppArmor Filesystem Enabled
[    0.550084] ACPI: RTC can wake from S4
[    0.552042] Switched to high resolution mode on CPU 0
[    0.552413] Switched to high resolution mode on CPU 1
[    0.556025] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.556029] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.556031] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.556034] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.556037] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.556040] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.556042] system 00:01: ioport range 0x830-0x83b has been reserved
[    0.556045] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.556047] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.556052] system 00:01: iomem range 0xf8000000-0xfbffffff could not be reserved
[    0.556055] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.556058] system 00:01: iomem range 0xfed10000-0xfed13fff could not be reserved
[    0.556061] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.556064] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.556067] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.556070] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.556073] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.556076] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.556078] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.556081] system 00:01: iomem range 0xff800000-0xff800fff has been reserved
[    0.591165] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.591170] pci 0000:00:1c.0:   IO window: 0x3000-0x4fff
[    0.591177] pci 0000:00:1c.0:   MEM window: 0x93700000-0x946fffff
[    0.591182] pci 0000:00:1c.0:   PREFETCH window: 0x00000090400000-0x000000914fffff
[    0.591190] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.591194] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.591201] pci 0000:00:1c.1:   MEM window: 0x92600000-0x936fffff
[    0.591206] pci 0000:00:1c.1:   PREFETCH window: 0x00000091500000-0x000000924fffff
[    0.591214] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.591216] pci 0000:00:1e.0:   IO window: disabled
[    0.591222] pci 0000:00:1e.0:   MEM window: disabled
[    0.591227] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.591248] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.591254] pci 0000:00:1c.0: setting latency timer to 64
[    0.591264] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.591269] pci 0000:00:1c.1: setting latency timer to 64
[    0.591278] pci 0000:00:1e.0: setting latency timer to 64
[    0.591282] bus: 00 index 0 io port: [0, ffff]
[    0.591284] bus: 00 index 1 mmio: [0, ffffffff]
[    0.591286] bus: 01 index 0 io port: [3000, 4fff]
[    0.591288] bus: 01 index 1 mmio: [93700000, 946fffff]
[    0.591290] bus: 01 index 2 mmio: [90400000, 914fffff]
[    0.591292] bus: 01 index 3 mmio: [0, 0]
[    0.591294] bus: 02 index 0 io port: [2000, 2fff]
[    0.591296] bus: 02 index 1 mmio: [92600000, 936fffff]
[    0.591298] bus: 02 index 2 mmio: [91500000, 924fffff]
[    0.591300] bus: 02 index 3 mmio: [0, 0]
[    0.591302] bus: 03 index 0 mmio: [0, 0]
[    0.591303] bus: 03 index 1 mmio: [0, 0]
[    0.591305] bus: 03 index 2 mmio: [0, 0]
[    0.591307] bus: 03 index 3 io port: [0, ffff]
[    0.591309] bus: 03 index 4 mmio: [0, ffffffff]
[    0.591317] NET: Registered protocol family 2
[    0.604051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.604287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.604712] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.605005] TCP: Hash tables configured (established 131072 bind 65536)
[    0.605009] TCP reno registered
[    0.612113] NET: Registered protocol family 1
[    0.612231] checking if image is initramfs... it is
[    1.247181] Freeing initrd memory: 8013k freed
[    1.247360] Simple Boot Flag value 0x9 read from CMOS RAM was invalid
[    1.247362] Simple Boot Flag at 0x44 set to 0x1
[    1.248197] audit: initializing netlink socket (disabled)
[    1.248218] type=2000 audit(1233691102.244:1): initialized
[    1.253687] highmem bounce pool size: 64 pages
[    1.253693] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.255769] VFS: Disk quotas dquot_6.5.1
[    1.255845] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.255941] msgmni has been set to 1744
[    1.256063] io scheduler noop registered
[    1.256066] io scheduler anticipatory registered
[    1.256068] io scheduler deadline registered
[    1.256080] io scheduler cfq registered (default)
[    1.256093] pci 0000:00:02.0: Boot video device
[    1.256555] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.256607] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.256657] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.256697] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.256730] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.256839] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.256889] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.256938] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.256973] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.257005] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.257307] isapnp: Scanning for PnP cards...
[    1.611196] isapnp: No Plug & Play device found
[    1.641239] hpet_resources: 0xfed00000 is busy
[    1.641315] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.643323] brd: module loaded
[    1.643385] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.643494] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.666819] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.681902] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.681907] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.681909] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.681912] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.681914] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.682214] mice: PS/2 mouse device common for all mice
[    1.683107] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.683139] rtc0: alarms up to one month, hpet irqs
[    1.683250] EISA: Probing bus 0 at eisa.0
[    1.683262] Cannot allocate resource for EISA slot 2
[    1.683264] Cannot allocate resource for EISA slot 3
[    1.683266] Cannot allocate resource for EISA slot 4
[    1.683268] Cannot allocate resource for EISA slot 5
[    1.683283] EISA: Detected 0 cards.
[    1.683286] cpuidle: using governor ladder
[    1.683288] cpuidle: using governor menu
[    1.683763] TCP cubic registered
[    1.683791] Using IPI No-Shortcut mode
[    1.683961] registered taskstats version 1
[    1.684086]   Magic number: 13:656:1000
[    1.684166]  pnp1: hash matches
[    1.684171] pnp 00:02: hash matches
[    1.684217] rtc_cmos 00:03: setting system clock to 2009-02-03 19:58:23 UTC (1233691103)
[    1.684220] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.684222] EDD information not available.
[    1.684459] Freeing unused kernel memory: 424k freed
[    1.684494] Write protecting the kernel text: 2580k
[    1.684529] Write protecting the kernel read-only data: 940k
[    1.709003] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.836064] fuse init (API version 7.9)
[    1.884688] ACPI: SSDT 7BBB3C18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.885219] ACPI: SSDT 7BBB1598, 0537 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.885805] Monitor-Mwait will be used to enter C-1 state
[    1.885809] Monitor-Mwait will be used to enter C-2 state
[    1.885947] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.885998] processor ACPI0007:00: registered as cooling_device0
[    1.886002] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.886506] ACPI: SSDT 7BBB2E18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117)
[    1.887062] ACPI: SSDT 7BBB3F18, 008D (r1  PmRef    ApCst     3000 INTL 20051117)
[    1.888013] Marking TSC unstable due to TSC halts in idle
[    1.892141] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.892186] processor ACPI0007:01: registered as cooling_device1
[    1.892190] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.129481] thermal LNXTHERM:01: registered as thermal_zone0
[    2.146566] ACPI: Thermal Zone [TZS0] (53 C)
[    2.154599] thermal LNXTHERM:02: registered as thermal_zone1
[    2.161403] ACPI: Thermal Zone [TZS1] (53 C)
[    2.453771] usbcore: registered new interface driver usbfs
[    2.453796] usbcore: registered new interface driver hub
[    2.453830] usbcore: registered new device driver usb
[    2.456228] USB Universal Host Controller Interface driver v3.0
[    2.456281] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.456292] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.456296] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.456341] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.456378] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000050e0
[    2.456527] usb usb1: configuration #1 chosen from 1 choice
[    2.456554] hub 1-0:1.0: USB hub found
[    2.456562] hub 1-0:1.0: 2 ports detected
[    2.459160] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.534244] No dock devices found.
[    2.554936] SCSI subsystem initialized
[    2.570511] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.570522] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.570526] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.570550] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.570587] uhci_hcd 0000:00:1a.1: irq 19, io base 0x000050c0
[    2.570679] usb usb2: configuration #1 chosen from 1 choice
[    2.570704] hub 2-0:1.0: USB hub found
[    2.570711] hub 2-0:1.0: 2 ports detected
[    2.571281] libata version 3.00 loaded.
[    2.672294] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    2.672306] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.672310] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.672352] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.672397] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000050a0
[    2.672515] usb usb3: configuration #1 chosen from 1 choice
[    2.672542] hub 3-0:1.0: USB hub found
[    2.672550] hub 3-0:1.0: 2 ports detected
[    2.776323] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[    2.776343] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.776347] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.776372] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.780291] ehci_hcd 0000:00:1a.7: debug port 1
[    2.780299] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.780307] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x94705c00
[    2.796050] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.796213] usb usb4: configuration #1 chosen from 1 choice
[    2.796249] hub 4-0:1.0: USB hub found
[    2.796258] hub 4-0:1.0: 6 ports detected
[    3.000064] Clocksource tsc unstable (delta = -125412214 ns)
[    3.004250] uhci_hcd 0000:00:1d.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.004260] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.004264] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.004288] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.004319] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00005080
[    3.004411] usb usb5: configuration #1 chosen from 1 choice
[    3.004435] hub 5-0:1.0: USB hub found
[    3.004442] hub 5-0:1.0: 2 ports detected
[    3.108250] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.108259] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.108263] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.108287] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.108317] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[    3.108408] usb usb6: configuration #1 chosen from 1 choice
[    3.108432] hub 6-0:1.0: USB hub found
[    3.108439] hub 6-0:1.0: 2 ports detected
[    3.120063] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    3.212258] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 17 (level, low) -> IRQ 17
[    3.212266] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.212270] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.212294] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.212324] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00005040
[    3.212411] usb usb7: configuration #1 chosen from 1 choice
[    3.212437] hub 7-0:1.0: USB hub found
[    3.212443] hub 7-0:1.0: 2 ports detected
[    3.263593] usb 4-3: configuration #1 chosen from 1 choice
[    3.316254] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.316271] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.316274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.316300] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.320198] ehci_hcd 0000:00:1d.7: debug port 1
[    3.320206] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.320213] ehci_hcd 0000:00:1d.7: irq 18, io mem 0x94705800
[    3.336057] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.336161] usb usb8: configuration #1 chosen from 1 choice
[    3.336191] hub 8-0:1.0: USB hub found
[    3.336197] hub 8-0:1.0: 6 ports detected
[    3.441454] ahci 0000:00:1f.2: version 3.0
[    3.441477] ahci 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.441625] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    3.441629] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[    3.441635] ahci 0000:00:1f.2: setting latency timer to 64
[    3.442525] scsi0 : ahci
[    3.442635] scsi1 : ahci
[    3.442688] scsi2 : ahci
[    3.442911] scsi3 : ahci
[    3.443209] scsi4 : ahci
[    3.443415] scsi5 : ahci
[    3.443604] ata1: SATA max UDMA/133 abar m2048@0x94705000 port 0x94705100 irq 221
[    3.443607] ata2: SATA max UDMA/133 abar m2048@0x94705000 port 0x94705180 irq 221
[    3.443610] ata3: DUMMY
[    3.443611] ata4: DUMMY
[    3.443614] ata5: SATA max UDMA/133 abar m2048@0x94705000 port 0x94705300 irq 221
[    3.443617] ata6: SATA max UDMA/133 abar m2048@0x94705000 port 0x94705380 irq 221
[    3.924065] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.926230] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    3.926236] ata1.00: ATA-8: ST9250320AS, HP07, max UDMA/100
[    3.926238] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.928745] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    3.928760] ata1.00: configured for UDMA/100
[    4.428079] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.428062] ata2.00: qc timeout (cmd 0x0)
[    9.428073] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
[    9.912066] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   14.912062] ata2.00: qc timeout (cmd 0x0)
[   14.912073] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
[   14.912076] ata2.00: ACPI: failed the second time, disabled
[   14.912079] ata2.00: revalidation failed (errno=-5)
[   15.396563] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.400993] ata2.00: configured for UDMA/100
[   15.736067] ata5: SATA link down (SStatus 0 SControl 300)
[   16.072065] ata6: SATA link down (SStatus 0 SControl 300)
[   16.088162] scsi 0:0:0:0: Direct-Access     ATA      ST9250320AS      HP07 PQ: 0 ANSI: 5
[   16.093772] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7591S  1.84 PQ: 0 ANSI: 5
[   16.093882] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.093908] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.093928] r8169 0000:01:00.0: setting latency timer to 64
[   16.093943] r8169 0000:01:00.0: unknown MAC (37a00000)
[   16.094276] eth0: RTL8169 at 0xf88b0000, 00:1f:16:5e:77:f4, XID 34a00000 IRQ 220
[   16.124531] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   16.124577] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   16.135870] usbcore: registered new interface driver libusual
[   16.142257] Initializing USB Mass Storage driver...
[   16.145413] scsi6 : SCSI emulation for USB Mass Storage devices
[   16.145534] usbcore: registered new interface driver usb-storage
[   16.145538] USB Mass Storage support registered.
[   16.147974] usb-storage: device found at 2
[   16.147978] usb-storage: waiting for device to settle before scanning
[   16.152266] Driver 'sd' needs updating - please use bus_type methods
[   16.152378] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   16.152395] sd 0:0:0:0: [sda] Write Protect is off
[   16.152397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.152420] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.152531] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   16.152545] sd 0:0:0:0: [sda] Write Protect is off
[   16.152547] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.152570] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.152573]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.173964]  sda1 sda2 < sda5 >
[   16.222916] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.246955] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.246959] Uniform CD-ROM driver Revision: 3.20
[   16.247062] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.343935] PM: Starting manual resume from disk
[   16.343939] PM: Resume from partition 8:5
[   16.343940] PM: Checking hibernation image.
[   16.344197] PM: Resume from disk failed.
[   16.439293] kjournald starting.  Commit interval 5 seconds
[   16.439310] EXT3-fs: mounted filesystem with ordered data mode.
[   21.144437] usb-storage: device scan complete
[   21.146532] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   21.148852] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   21.148950] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   23.405956] udevd version 124 started
[   23.752203] Linux agpgart interface v0.103
[   23.796154] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
[   23.796476] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[   23.807349] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   23.891089] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.940190] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.000236] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   24.020042] ACPI: Power Button (FF) [PWRF]
[   24.020184] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   24.023180] ACPI: Lid Switch [LID0]
[   24.023261] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   24.052036] ACPI: Sleep Button (CM) [SLPB]
[   24.107309] acpi device:04: registered as cooling_device2
[   24.107752] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[   24.124531] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   24.124731] ACPI: WMI: Mapper loaded
[   24.303861] ACPI: AC Adapter [ADP1] (on-line)
[   24.357624] ath_hal: module license 'Proprietary' taints kernel.
[   24.374893] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   24.385581] wlan: 0.9.4
[   24.392191] ath_pci: 0.9.4
[   24.392942] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.392955] ath_pci 0000:02:00.0: setting latency timer to 64
[   24.441442] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   24.441459] ath_pci 0000:02:00.0: PCI INT A disabled
[   24.614259] ACPI: Battery Slot [BAT0] (battery present)
[   24.743092] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.743123] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.157136] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   25.933563] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000
[   26.000080] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   27.412679] lp: driver loaded but no devices found
[   27.634909] Adding 5863684k swap on /dev/sda5.  Priority:-1 extents:1 across:5863684k
[   28.174190] EXT3 FS on sda1, internal journal
[   29.211327] type=1505 audit(1233691130.960:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4231
[   29.367910] type=1505 audit(1233691131.116:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4236
[   29.368151] type=1505 audit(1233691131.120:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4236
[   29.546324] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.222146] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.314973] apm: BIOS not found.
[   31.487480] ppdev: user-space parallel port driver
[   33.958797] Bluetooth: Core ver 2.13
[   33.958905] NET: Registered protocol family 31
[   33.958911] Bluetooth: HCI device and connection manager initialized
[   33.958919] Bluetooth: HCI socket layer initialized
[   33.976158] Bluetooth: L2CAP ver 2.11
[   33.976167] Bluetooth: L2CAP socket layer initialized
[   33.990273] Bluetooth: SCO (Voice Link) ver 0.6
[   33.990284] Bluetooth: SCO socket layer initialized
[   34.012920] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.012930] Bluetooth: BNEP filters: protocol multicast
[   34.040743] Bridge firewalling registered
[   34.213385] Bluetooth: RFCOMM socket layer initialized
[   34.213406] Bluetooth: RFCOMM TTY layer initialized
[   34.213410] Bluetooth: RFCOMM ver 1.10
[   38.337334] r8169: eth0: link up
[   38.337350] r8169: eth0: link up
[   38.472275] NET: Registered protocol family 17
[   38.583029] [drm] Initialized drm 1.1.0 20060810
[   38.591381] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   38.591395] pci 0000:00:02.0: setting latency timer to 64
[   38.593943] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.840657] set status page addr 0x03fff000
[   43.936440] NET: Registered protocol family 10
[   43.937423] lo: Disabled Privacy Extensions
[   54.932086] eth0: no IPv6 routers present
[   86.995482] CPU0 attaching NULL sched-domain.
[   86.995498] CPU1 attaching NULL sched-domain.
[   86.997294] CPU0 attaching sched-domain:
[   86.997302]  domain 0: span 0-1 level MC
[   86.997308]   groups: 0 1
[   86.997319] CPU1 attaching sched-domain:
[   86.997323]  domain 0: span 0-1 level MC
[   86.997328]   groups: 1 0
[ 2669.396051] usb 6-1: new low speed USB device using uhci_hcd and address 2
[ 2669.628787] usb 6-1: configuration #1 chosen from 1 choice
[ 2669.734045] usbcore: registered new interface driver hiddev
[ 2669.748328] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input8
[ 2669.749573] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[ 2669.749597] usbcore: registered new interface driver usbhid
[ 2669.749601] usbhid: v2.6:USB HID core driver

```
--sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:5e:77:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:26:75:3c:9e:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

-- iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

-- lsb_release -d

Description:	Ubuntu 8.10

-- uname -mr

2.6.27-11-generic i686

--sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                               Ignoring unknown interface eth0=eth0.

---

### Post by Mriswithe on 2009-02-03
Kept googling and searching around and found this link, solved all of my problems

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

