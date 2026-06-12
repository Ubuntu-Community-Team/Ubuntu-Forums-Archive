---
title: "Wireless Great with W7, Drops Out with Ubuntu"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-03-13
Ubuntu Karmic Koala, Linux 2.6.21-30-generic, Acer Aspire 1 "netbook," dual-boot Windows 7.

When this laptop is booted into Windows 7, it gets good, solid wireless connections which can last all day. When booted to Ubuntu, the signal strength meter starts strong, fades to weak, and after about 5 minutes, the connection is lost. Near as I can tell, the only way to get wireless re-connected is to reboot the OS.

lspci shows Network controller: Atheros Communications AR928X Wireless Network Adapter (PCI-Express) (rev 01)

I'm hoping I can get this thing nice and solid under Ubuntu else I'm going to have to run the laptop under W7 and give up any hope of achieving coffeehouse geek cred.

Any ideas that can help a newbie? I've read quite a few very technical posts here and there about installing drivers and gracious it's complicated.

---

### Post by Rocket J Squirrel on 2010-03-13
Sorry, just found the sticky. I'll plug along at this until the connection drops. 
------------------
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b175 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==========================
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:6c:5a:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:ee:e6:a6:90:ab  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eee:e6ff:fea6:90ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33172035 (33.1 MB)  TX bytes:1600348 (1.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 0C-EE-E6-A6-90-AB-61-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
======================
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"The Shop"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:06:25:75:A5:E3   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=17/70  Signal level=-93 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
=========================
lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
snd_hda_codec_realtek   203328  1 
joydev                 10240  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
arc4                    1660  2 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 258744  0 
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181140  1 ath9k
uvcvideo               59080  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath                     8060  1 ath9k
videodev               36736  1 uvcvideo
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
led_class               4096  1 ath9k
v4l1_compat            14336  2 uvcvideo,videodev
serio_raw               5280  0 
atl1c                  30880  0 
soundcore               7264  1 snd
cfg80211               93052  3 ath9k,mac80211,ath
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
=============================
dmesg
[    0.509648]   alloc irq_desc for 16 on node -1
[    0.509653]   alloc kstat_irqs on node -1
[    0.509665] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.509675] pci 0000:00:1c.0: setting latency timer to 64
[    0.509689] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.509696]   alloc irq_desc for 17 on node -1
[    0.509700]   alloc kstat_irqs on node -1
[    0.509708] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.509719] pci 0000:00:1c.1: setting latency timer to 64
[    0.509732]   alloc irq_desc for 18 on node -1
[    0.509736]   alloc kstat_irqs on node -1
[    0.509744] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.509753] pci 0000:00:1c.2: setting latency timer to 64
[    0.509765] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.509773]   alloc irq_desc for 19 on node -1
[    0.509777]   alloc kstat_irqs on node -1
[    0.509785] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.509795] pci 0000:00:1c.3: setting latency timer to 64
[    0.509807] pci 0000:00:1e.0: setting latency timer to 64
[    0.509817] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.509823] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.509829] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.509835] pci_bus 0000:01: resource 1 mem: [0x57100000-0x581fffff]
[    0.509842] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.509848] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.509854] pci_bus 0000:02: resource 1 mem: [0x56100000-0x570fffff]
[    0.509860] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.509866] pci_bus 0000:03: resource 0 io:  [0x2000-0x3fff]
[    0.509872] pci_bus 0000:03: resource 1 mem: [0x55000000-0x560fffff]
[    0.509878] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.509884] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.509890] pci_bus 0000:04: resource 1 mem: [0x54000000-0x54ffffff]
[    0.509896] pci_bus 0000:04: resource 2 pref mem [0x53000000-0x53ffffff]
[    0.509903] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.509908] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.509980] NET: Registered protocol family 2
[    0.510179] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.510810] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.511739] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512224] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512231] TCP reno registered
[    0.512440] NET: Registered protocol family 1
[    0.512571] Trying to unpack rootfs image as initramfs...
[    0.877035] Freeing initrd memory: 7738k freed
[    0.884333] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.884342] Simple Boot Flag at 0x44 set to 0x1
[    0.884729] cpufreq-nforce2: No nForce2 chipset.
[    0.884787] Scanning for low memory corruption every 60 seconds
[    0.884995] audit: initializing netlink socket (disabled)
[    0.885033] type=2000 audit(1268465236.884:1): initialized
[    0.901667] highmem bounce pool size: 64 pages
[    0.901680] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.904766] VFS: Disk quotas dquot_6.5.2
[    0.904891] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.906114] fuse init (API version 7.12)
[    0.906287] msgmni has been set to 1732
[    0.906768] alg: No test for stdrng (krng)
[    0.906800] io scheduler noop registered
[    0.906806] io scheduler anticipatory registered
[    0.906810] io scheduler deadline registered
[    0.906913] io scheduler cfq registered (default)
[    0.906939] pci 0000:00:02.0: Boot video device
[    0.907366]   alloc irq_desc for 24 on node -1
[    0.907372]   alloc kstat_irqs on node -1
[    0.907392] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.907408] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.907620]   alloc irq_desc for 25 on node -1
[    0.907625]   alloc kstat_irqs on node -1
[    0.907638] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.907653] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.907862]   alloc irq_desc for 26 on node -1
[    0.907867]   alloc kstat_irqs on node -1
[    0.907880] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.907895] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.908143]   alloc irq_desc for 27 on node -1
[    0.908148]   alloc kstat_irqs on node -1
[    0.908162] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.908176] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.908347] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.908565] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.908580] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.908837] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.908851] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.909101] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.909116] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.909359] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.909372] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.909654] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.909668] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.909908] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.909922] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.910161] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.910175] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.910416] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.910430] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.910525] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.972155] ACPI: AC Adapter [AC] (on-line)
[    0.972301] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.972309] ACPI: Power Button [PWRF]
[    0.972407] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.972413] ACPI: Power Button [PWRB]
[    0.972509] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.972588] ACPI: Lid Switch [LID0]
[    0.972685] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.972692] ACPI: Sleep Button [SLPB]
[    0.972984] fan PNP0C0B:00: registered as cooling_device0
[    0.973000] ACPI: Fan [FAN] (on)
[    0.974320] ACPI: SSDT 3f5b7c90 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.975135] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.976845] Marking TSC unstable due to TSC halts in idle
[    0.976877] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.976924] processor LNXCPU:00: registered as cooling_device1
[    0.976933] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.977672] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.978402] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.980218] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.980268] processor LNXCPU:01: registered as cooling_device2
[    0.980278] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.043195] thermal LNXTHERM:01: registered as thermal_zone0
[    1.043212] ACPI: Thermal Zone [THRM] (27 C)
[    1.043345] isapnp: Scanning for PnP cards...
[    1.397608] isapnp: No Plug & Play device found
[    1.724200] ACPI: Battery Slot [BAT0] (battery present)
[    1.724497] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.727019] brd: module loaded
[    1.727989] loop: module loaded
[    1.728201] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.728365] ahci 0000:00:1f.2: version 3.0
[    1.728393] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.728452]   alloc irq_desc for 28 on node -1
[    1.728458]   alloc kstat_irqs on node -1
[    1.728476] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.728538] ahci: SSS flag set, parallel bus scan disabled
[    1.728588] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.728596] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    1.728605] ahci 0000:00:1f.2: setting latency timer to 64
[    1.728968] scsi0 : ahci
[    1.729230] scsi1 : ahci
[    1.729365] scsi2 : ahci
[    1.729497] scsi3 : ahci
[    1.729862] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 28
[    1.729869] ata2: DUMMY
[    1.729875] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
[    1.729880] ata4: DUMMY
[    1.731862] Fixed MDIO Bus: probed
[    1.731943] PPP generic driver version 2.4.2
[    1.732184] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.732239] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.732271] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.732278] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.732342] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.732352] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.736280] ehci_hcd 0000:00:1d.7: debug port 1
[    1.736290] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.736321] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    1.752031] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.752190] usb usb1: configuration #1 chosen from 1 choice
[    1.752259] hub 1-0:1.0: USB hub found
[    1.752275] hub 1-0:1.0: 8 ports detected
[    1.752395] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.752435] uhci_hcd: USB Universal Host Controller Interface driver
[    1.752501] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.752515] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.752522] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.752603] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.752642] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    1.752828] usb usb2: configuration #1 chosen from 1 choice
[    1.752886] hub 2-0:1.0: USB hub found
[    1.752900] hub 2-0:1.0: 2 ports detected
[    1.752985] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.752997] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.753004] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.753065] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.753116] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    1.753276] usb usb3: configuration #1 chosen from 1 choice
[    1.753333] hub 3-0:1.0: USB hub found
[    1.753346] hub 3-0:1.0: 2 ports detected
[    1.753430] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.753442] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.753448] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.753509] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.753555] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    1.753716] usb usb4: configuration #1 chosen from 1 choice
[    1.753775] hub 4-0:1.0: USB hub found
[    1.753789] hub 4-0:1.0: 2 ports detected
[    1.753871] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.753883] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.753890] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.753950] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.753997] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    1.754161] usb usb5: configuration #1 chosen from 1 choice
[    1.754218] hub 5-0:1.0: USB hub found
[    1.754232] hub 5-0:1.0: 2 ports detected
[    1.754416] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.781740] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.781755] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.781915] mice: PS/2 mouse device common for all mice
[    1.782193] rtc_cmos 00:03: RTC can wake from S4
[    1.782280] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.782329] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.782629] device-mapper: uevent: version 1.0.3
[    1.782875] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.783052] device-mapper: multipath: version 1.1.0 loaded
[    1.783060] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.783376] EISA: Probing bus 0 at eisa.0
[    1.783387] Cannot allocate resource for EISA slot 1
[    1.783392] Cannot allocate resource for EISA slot 2
[    1.783397] Cannot allocate resource for EISA slot 3
[    1.783402] Cannot allocate resource for EISA slot 4
[    1.783406] Cannot allocate resource for EISA slot 5
[    1.783411] Cannot allocate resource for EISA slot 6
[    1.783426] EISA: Detected 0 cards.
[    1.783778] cpuidle: using governor ladder
[    1.783966] cpuidle: using governor menu
[    1.785077] TCP cubic registered
[    1.785426] NET: Registered protocol family 10
[    1.786339] lo: Disabled Privacy Extensions
[    1.787076] NET: Registered protocol family 17
[    1.787120] Bluetooth: L2CAP ver 2.13
[    1.787124] Bluetooth: L2CAP socket layer initialized
[    1.787130] Bluetooth: SCO (Voice Link) ver 0.6
[    1.787133] Bluetooth: SCO socket layer initialized
[    1.787233] Bluetooth: RFCOMM TTY layer initialized
[    1.787244] Bluetooth: RFCOMM socket layer initialized
[    1.787250] Bluetooth: RFCOMM ver 1.11
[    1.789053] Using IPI No-Shortcut mode
[    1.789230] PM: Resume from disk failed.
[    1.789256] registered taskstats version 1
[    1.789472]   Magic number: 2:623:470
[    1.789600] rtc_cmos 00:03: setting system clock to 2010-03-13 07:27:18 UTC (1268465238)
[    1.789608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.789612] EDD information not available.
[    1.803781] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.048135] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.049390] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.049574] ata1.00: ATA-8: Hitachi HTS545025B9A300, PB2OC60F, max UDMA/133
[    2.049587] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.051027] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.051273] ata1.00: configured for UDMA/133
[    2.064082] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.064374] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[    2.064649] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.064741] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.064870] sd 0:0:0:0: [sda] Write Protect is off
[    2.064877] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.064944] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.065299]  sda: sda1 sda2 sda3
[    2.093811] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.230223] usb 1-2: configuration #1 chosen from 1 choice
[    2.384125] ata3: SATA link down (SStatus 0 SControl 300)
[    2.400210] Freeing unused kernel memory: 540k freed
[    2.400686] Write protecting the kernel text: 4580k
[    2.400768] Write protecting the kernel read-only data: 1840k
[    2.717990] Linux agpgart interface v0.103
[    2.753906] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    2.754236] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.757108] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    3.045737] acpi device:1d: registered as cooling_device3
[    3.046179] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[    3.046287] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    3.093376] [drm] Initialized drm 1.1.0 20060810
[    3.123714] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.123728] i915 0000:00:02.0: setting latency timer to 64
[    3.350516] [drm] fb0: inteldrmfb frame buffer device
[    3.350534] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.675804] [drm] LVDS-8: set mode 1024x600 e
[    4.136972] Console: switching to colour frame buffer device 128x37
[    4.874627] EXT4-fs (loop0): barriers enabled
[    4.902440] kjournald2 starting: pid 388, dev loop0:8, commit interval 5 seconds
[    4.902602] EXT4-fs (loop0): delayed allocation enabled
[    4.902611] EXT4-fs: file extents enabled
[    4.906537] EXT4-fs: mballoc enabled
[    4.906569] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    5.768306] type=1505 audit(1268465242.478:2): operation="profile_load" pid=414 name=/usr/share/gdm/guest-session/Xsession
[    5.773324] type=1505 audit(1268465242.483:3): operation="profile_load" pid=415 name=/sbin/dhclient3
[    5.774060] type=1505 audit(1268465242.483:4): operation="profile_load" pid=415 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.774393] type=1505 audit(1268465242.483:5): operation="profile_load" pid=415 name=/usr/lib/connman/scripts/dhclient-script
[    5.836601] type=1505 audit(1268465242.546:6): operation="profile_load" pid=416 name=/usr/bin/evince
[    5.845683] type=1505 audit(1268465242.554:7): operation="profile_load" pid=416 name=/usr/bin/evince-previewer
[    5.851152] type=1505 audit(1268465242.558:8): operation="profile_load" pid=416 name=/usr/bin/evince-thumbnailer
[    5.884722] type=1505 audit(1268465242.594:9): operation="profile_load" pid=418 name=/usr/lib/cups/backend/cups-pdf
[    5.885459] type=1505 audit(1268465242.594:10): operation="profile_load" pid=418 name=/usr/sbin/cupsd
[    5.906472] type=1505 audit(1268465242.614:11): operation="profile_load" pid=419 name=/usr/sbin/tcpdump
[   16.049543] udev: starting version 147
[   16.141355] lp: driver loaded but no devices found
[   16.576950] intel_rng: FWH not detected
[   16.804916] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.804942] atl1c 0000:03:00.0: setting latency timer to 64
[   16.805032] atl1c 0000:03:00.0: PME# disabled
[   16.805045] atl1c 0000:03:00.0: PME# disabled
[   16.864730] cfg80211: Calling CRDA to update world regulatory domain
[   16.894138] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   16.948790] Linux video capture interface: v2.00
[   16.979095] acer-wmi: Acer Laptop ACPI-WMI Extras
[   17.053053] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
[   17.068694] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   17.068868] usbcore: registered new interface driver uvcvideo
[   17.068879] USB Video Class driver (v0.1.0)
[   17.160970] acer-wmi: Unable to detect available WMID devices
[   17.212088] cfg80211: World regulatory domain updated:
[   17.212099]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.212110]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.212119]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.212128]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.212136]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.212145]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.257696] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.257723] ath9k 0000:01:00.0: setting latency timer to 64
[   17.422663] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.696207] ath: EEPROM regdomain: 0x65
[   17.696216] ath: EEPROM indicates we should expect a direct regpair map
[   17.696227] ath: Country alpha2 being used: 00
[   17.696234] ath: Regpair used: 0x65
[   17.865171] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.866696] Registered led device: ath9k-phy0::radio
[   17.866735] Registered led device: ath9k-phy0::assoc
[   17.866772] Registered led device: ath9k-phy0::tx
[   17.866821] Registered led device: ath9k-phy0::rx
[   17.866850] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8c60000, irq=16
[   18.025545] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   18.116264] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.189626] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.189687] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.336011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000
[   19.336035] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   19.336957] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   24.636743] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   24.741196] EXT4-fs (loop0): internal journal on loop0:8
[   25.309147] type=1505 audit(1268494062.019:12): operation="profile_replace" pid=927 name=/usr/share/gdm/guest-session/Xsession
[   25.325921] type=1505 audit(1268494062.035:13): operation="profile_replace" pid=928 name=/sbin/dhclient3
[   25.326742] type=1505 audit(1268494062.035:14): operation="profile_replace" pid=928 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   25.327217] type=1505 audit(1268494062.035:15): operation="profile_replace" pid=928 name=/usr/lib/connman/scripts/dhclient-script
[   25.329503] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.336570] type=1505 audit(1268494062.043:16): operation="profile_replace" pid=929 name=/usr/bin/evince
[   25.338397]   alloc irq_desc for 29 on node -1
[   25.338407]   alloc kstat_irqs on node -1
[   25.338442] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   25.339317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.392131] type=1505 audit(1268494062.099:17): operation="profile_replace" pid=929 name=/usr/bin/evince-previewer
[   25.408386] type=1505 audit(1268494062.115:18): operation="profile_replace" pid=929 name=/usr/bin/evince-thumbnailer
[   25.487801] type=1505 audit(1268494062.195:19): operation="profile_replace" pid=949 name=/usr/lib/cups/backend/cups-pdf
[   25.488826] type=1505 audit(1268494062.195:20): operation="profile_replace" pid=949 name=/usr/sbin/cupsd
[   25.496656] type=1505 audit(1268494062.203:21): operation="profile_replace" pid=951 name=/usr/sbin/tcpdump
[   27.916935] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   27.916945] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   27.916949] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   27.916952] vboxdrv: the usage of hardware performance counters by
[   27.916955] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   27.916963] vboxdrv: Found 2 processor cores.
[   27.917125] vboxdrv: fAsync=0 offMin=0x190 offMax=0x1f36
[   27.917238] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.917246] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   28.023857] ppdev: user-space parallel port driver
[   28.754486] CPU0 attaching NULL sched-domain.
[   28.754500] CPU1 attaching NULL sched-domain.
[   28.773155] CPU0 attaching sched-domain:
[   28.773166]  domain 0: span 0-1 level SIBLING
[   28.773174]   groups: 0 1
[   28.773188] CPU1 attaching sched-domain:
[   28.773194]  domain 0: span 0-1 level SIBLING
[   28.773201]   groups: 1 0
[   29.778745] CPU0 attaching NULL sched-domain.
[   29.778761] CPU1 attaching NULL sched-domain.
[   29.796176] CPU0 attaching sched-domain:
[   29.796188]  domain 0: span 0-1 level SIBLING
[   29.796197]   groups: 0 1
[   29.796214] CPU1 attaching sched-domain:
[   29.796221]  domain 0: span 0-1 level SIBLING
[   29.796229]   groups: 1 0
[   52.924106] wlan0: authenticate with AP 00:1e:e5:50:ea:48
[   52.927554] wlan0: authenticated
[   52.927566] wlan0: associate with AP 00:1e:e5:50:ea:48
[   52.936066] wlan0: RX AssocResp from 00:1e:e5:50:ea:48 (capab=0x411 status=0 aid=3)
[   52.936078] wlan0: associated
[   52.943496] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.504049] wlan0: no IPv6 routers present
[   64.052717] wlan0: disassociating by local choice (reason=3)
[   67.961215] wlan0: authenticate with AP 00:1e:e5:50:ea:48
[   67.963377] wlan0: authenticated
[   67.963388] wlan0: associate with AP 00:1e:e5:50:ea:48
[   67.966542] wlan0: RX AssocResp from 00:1e:e5:50:ea:48 (capab=0x411 status=0 aid=3)
[   67.966554] wlan0: associated
[   78.050784] wlan0: disassociating by local choice (reason=3)
[   90.930370] wlan0: authenticate with AP 00:06:25:75:a5:e3
[   90.932220] wlan0: authenticated
[   90.932237] wlan0: associate with AP 00:06:25:75:a5:e3
[   90.936918] wlan0: RX AssocResp from 00:06:25:75:a5:e3 (capab=0x1 status=0 aid=3)
[   90.936930] wlan0: associated
[  612.005134] wlan0: no probe response from AP 00:06:25:75:a5:e3 - disassociating
[  613.186818] wlan0: authenticate with AP 00:06:25:75:a5:e3
[  613.193732] wlan0: authenticated
[  613.193749] wlan0: associate with AP 00:06:25:75:a5:e3
[  613.196924] wlan0: RX ReassocResp from 00:06:25:75:a5:e3 (capab=0x1 status=0 aid=3)
[  613.196942] wlan0: associated
[ 2359.901038] wlan0: disassociating by local choice (reason=3)
[ 2371.094917] wlan0: authenticate with AP 00:1e:e5:50:ea:48
[ 2371.096975] wlan0: authenticated
[ 2371.096987] wlan0: associate with AP 00:1e:e5:50:ea:48
[ 2371.103738] wlan0: RX AssocResp from 00:1e:e5:50:ea:48 (capab=0x411 status=0 aid=3)
[ 2371.103749] wlan0: associated
[ 2382.051502] wlan0: disassociating by local choice (reason=3)
[ 2385.953247] wlan0: authenticate with AP 00:06:25:75:a5:e3
[ 2385.955838] wlan0: authenticated
[ 2385.955855] wlan0: associate with AP 00:06:25:75:a5:e3
[ 2385.958402] wlan0: RX AssocResp from 00:06:25:75:a5:e3 (capab=0x1 status=0 aid=3)
[ 2385.958419] wlan0: associated
[ 2457.004162] wlan0: no probe response from AP 00:06:25:75:a5:e3 - disassociating
[ 2458.186110] wlan0: authenticate with AP 00:06:25:75:a5:e3
[ 2458.197328] wlan0: authenticated
[ 2458.197338] wlan0: associate with AP 00:06:25:75:a5:e3
[ 2458.200703] wlan0: RX ReassocResp from 00:06:25:75:a5:e3 (capab=0x1 status=0 aid=3)
[ 2458.200713] wlan0: associated
[ 2476.952399] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 2477.172685] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 2477.183673] wlan0: no probe response from AP 00:06:25:75:a5:e3 - disassociating
[ 2478.368734] wlan0: authenticate with AP 00:06:25:75:a5:e3
[ 2478.370754] wlan0: authenticated
[ 2478.370766] wlan0: associate with AP 00:06:25:75:a5:e3
[ 2478.373287] wlan0: RX ReassocResp from 00:06:25:75:a5:e3 (capab=0x1 status=0 aid=3)
[ 2478.373301] wlan0: associated
==========================
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:ee:e6:a6:90:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:57100000-5710ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:6c:5a:20
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:55000000-5503ffff ioport:2000(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
===============================
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:75:A5:E3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"The Shop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000033682fe91ba
                    Extra: Last beacon: 27716ms ago
                    IE: Unknown: 00085468652053686F70
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101

vboxnet0  Interface doesn't support scanning.
========================
lsb_release -d
Description:    Ubuntu 9.10
==========================
uname -mr
2.6.31-20-generic i686
===========================
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

---

### Post by Rocket J Squirrel on 2010-03-13
Okay, I've just installed the newest driver per the instructions found here: [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285) and I'll see if the wireless stabilizes.

---

### Post by Rocket J Squirrel on 2010-03-13
Well, okay -- that seems to have fixed it. The connection has been rock-solid and fast all day. 

I feel like I've been having a conversation with myself. 

[SIZE=4]HELLO[/SIZE]...[SIZE=3]hello[/SIZE]...[SIZE=1]hello[/SIZE]...
[SIZE=4]ECHO[/SIZE]...[SIZE=3]echo.[/SIZE]..[SIZE=1]echo[/SIZE]...

---

### Post by Rocket J Squirrel on 2010-03-27
No, wait -- I had to remove the Ubuntu partition (wubi install) and re-wubi-ize this machine for another reason. I applied the above patch again and the wireless still reads weak and loses connection. Not so if I boot to W7. I notice that the computer randomly turns off the Bluetooth adapter, too, and recall that during the make process of installing the wireless path, that there were plenty of messages about the Bluetooth that showed up during the process. 

It seems they are related. 

If I restart Ubuntu then the wireless connection is happy for a while, then gets weak, then disconnects, then tries to connect, tries to connect, tries to connect, but nothing happens. 

If anyone has any light they can shed on this, it would be greatly appreciated. All the details earlier in this thread still apply.

---

### Post by bkratz on 2010-03-27
> **Rocket J Squirrel said:**
> No, wait -- I had to remove the Ubuntu partition (wubi install) and re-wubi-ize this machine for another reason. I applied the above patch again and the wireless still reads weak and loses connection. Not so if I boot to W7. I notice that the computer randomly turns off the Bluetooth adapter, too, and recall that during the make process of installing the wireless path, that there were plenty of messages about the Bluetooth that showed up during the process. 

It seems they are related. 

If I restart Ubuntu then the wireless connection is happy for a while, then gets weak, then disconnects, then tries to connect, tries to connect, tries to connect, but nothing happens. 

If anyone has any light they can shed on this, it would be greatly appreciated. All the details earlier in this thread still apply.

did you do this?

[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by optimusmedia on 2010-03-27
I have an Acer Aspire 7736Z-4088 
"sudo lshw -C network" reveals: 

description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.

... and these pages

[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

> changed to: 
cd Desktop
tar -xf compat-wireless-2.6.33.tar.bz2
cd compat-wireless-2.6.33
make
sudo make install
sudo make unload

...seemed to have helped.. so far. :)

Thanks to all who helped!

---

### Post by Rocket J Squirrel on 2010-03-27
Thanks, optimusmedia.

I think what you did works here, too. 

After I re-installed Ubuntu I ran the driver update you describe and the wireless got rock-steady, showing signal of more than 60% here in my house. 

Then, using Update Manager, I let Ubuntu do a series of updates that it found, and the wireless got flaky again, falling down to 8% and then dropping out entirely and unable to re-connect at all. The Bluetooth lamp on the laptop liked to turn itself off, too. I guess the wireless stuff is tangled up with the Bluetooth stuff?

So this morning I re-ran the driver update again and this seems to have fixed the problem. 

This suggests that what Update Manager considered to be new and necessary might have been less good than the manual driver update you show, and which worked for me. 

I wonder if there is some way to "protect" the current wireless configuration from further automatic updates.

---

### Post by optimusmedia on 2010-03-27
I may have spoken too soon.  Shortly after posting it dropped out. 

Anyone have any suggestions?

---

### Post by Rocket J Squirrel on 2010-03-27
Bummer -- mine is still holding rock-steady at 64%. Let's hope that someone who knows this stuff will drop by and make some suggestions. I really want my wireless to be dependable so I can ditch the dual-boot setup, forgo Windows 7, and make Ubuntu my main OS.

---

### Post by optimusmedia on 2010-03-27
Trying the backport suggestion from above now. I'll know within a few hours, for sure. :)

---

### Post by Rocket J Squirrel on 2010-03-27
Right on -- keep me posted. Looks like we are a mutual support team of two. In my case, total Ubuntu newbie.

---

### Post by NightwishFan on 2010-03-27
The pefrormance problems on the ath9k driver are fixed install Wireless Kernel Backports.
[Click Here to install..]("apt://linux-backports-modules-wireless-karmic-generic") and press ok to use apturl. Or use:
```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```

I skimmed through the thread and am not sure what driver etc is being used. Find out before you run this command.

---

### Post by teo_rossi on 2010-03-27
Hi,
I have Ubuntu Lucid beta installed on a Sony Vaio CW2 laptop, which has a Atheros AR9285 wifi device and I'm experiencing a very slow connection, with the bandwidth which is constantly 0 except for some peaks.

I tried with the compat-wireless stable and nightly releases but they didn't work. Are there other things I can try?

---

### Post by NightwishFan on 2010-03-27
What is the driver used? Right click network manager and choose connection information.

---

### Post by Rocket J Squirrel on 2010-03-27
> **NightwishFan said:**
> What is the driver used? Right click network manager and choose connection information.

ath9k

Thanks for taking a look at this.

---

### Post by NightwishFan on 2010-03-27
My card is a built in Atheros AR9285 (ath9k driver) and it works in Karmic using kernel backports. Without it, my wireless had a connection that barely worked and eventually dropped. It works out of the box for me on lucid, but I suppose you could try the lucid kernel backports on there as well.

---

### Post by Rocket J Squirrel on 2010-03-27
Thanks. So, near as you can tell, 

```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```might do what needs to be done?

---

### Post by NightwishFan on 2010-03-27
Yes, or click this link and hit ok to install automatically.
[apt://linux-backports-modules-wireless-karmic-generic]("apt://linux-backports-modules-wireless-karmic-generic")

The reboot, and try the connection.

---

### Post by Rocket J Squirrel on 2010-03-27
Okee dokee. I'm goin' in. Throwing myself on the grenade for others in the same boat. Will report back on the other side.

---

### Post by Rocket J Squirrel on 2010-03-27
I'm back. Miss me?

The card connected right up after restart. I'll see if it holds. Signal is starting at 55% which is lower than it was after I applied the driver update mentioned earlier in this thread, and has already dropped to 50%. If it keeps dropping it looks like I've gone backwards. I should know in an hour or so.

---

### Post by NightwishFan on 2010-03-27
The signal strength on mine never makes much sense. Though I will say it was higher after I applied the backports. Try throughput and latency rather than just signal strength.
```
ping google.com
```
Do all the pings succeed? Is the latency low (below 80ms)?



Also try installing a package using the command line and keep an eye out on the average download speed.
```
sudo aptitude install packagename
```
Is the download fast and stable? If not it does not tell us much, but if so then it is working right. ;)

---

### Post by optimusmedia on 2010-03-27
backports seems to have done it!  Been up for hours, that's more than ever before. Again, thanks to all!

---

### Post by Rocket J Squirrel on 2010-03-27
Seems to be holding here, too, at around 55%. Pinging Google.com is averaging 40ms. Gracious me -- could this thing be fixed?

---

### Post by xnostradamusx on 2010-03-27
@NightwishFan i have the exact same problem and your post saved me thanks alot :popcorn:

---

### Post by NightwishFan on 2010-03-27
Good, I am glad it works for you.

---

### Post by teo_rossi on 2010-04-05
Well, even with Lucid backports, compat driver or kernel 2.6.33 the performance is abysmal. The connection doesn't drop, but transfer rate is 0 except for some peaks up to 1 MBps.

Should I try ndiswrapper? Does it work with Windows 7 x64 drivers?

---

### Post by NightwishFan on 2010-04-05
I have never used Ndiswrapper, but here is a link about the subject.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have also heard of a frontend called ndisgtk or similar.

---

### Post by teo_rossi on 2010-04-05
Ndiswrapper doesn't seem to work. I tried with the driver that comes with Windows 7. Ndiswrapper reports that the driver is installed:

```

ndiswrapper -l
netathrx : driver installed
	device (168C:002B) present (alternate driver: ath9k)

```

but after using ```
modprobe ndiswrapper
``` no wireless interface is detected by iwconfig

---

### Post by NightwishFan on 2010-04-05
I am sorry it does not work. I am far from an expert in these issues. I can only think "compile the latest!" but it seems you have already tried that?

---

### Post by shabadoo52 on 2010-05-01
I have the same issue: the connection doesn't drop, but the transfer rate keeps dropping to zero.  Max speed of about 1Mbps.  I had this issue in both Karmic and Lucid.  I'm using a CW Vaio laptop with the AR9285.

I tried installing the latest compat-wireless drivers without seeing much difference.

Ideas anyone?

---

### Post by teo_rossi on 2010-05-02
Well, a possible workaround is to install madwifi driver and to use it instead of ath9k. With this driver the performance is much better, even if it's still not perfect.
Here are the detailed instructions offered by a friend who had the same problem:

[LIST=1]
[*]Install build-essential (if isn't installed)
[*]Install subversion (if isn't installed)
[*]Download [http://madwifi-project.org/attachment/ticket/2391/madwifi-4122-ar9285.patch](http://madwifi-project.org/attachment/ticket/2391/madwifi-4122-ar9285.patch)
[*]mkdir madwifi, copy madwifi-4122-ar9285.patch to it, enter it
[*]svn checkout [http://madwifi-project.org/svn/madwifi/trunk/](http://madwifi-project.org/svn/madwifi/trunk/) madwifi_last
[*]patch -p0 < madwifi-4122-ar9285.patch
[*]cd madwifi_last
[*]make
[*]sudo make install
[*]sudo gedit /etc/rc.local, add following lines:
[/LIST]

```
modprobe -r ath9k
modprobe ath_pci
```

Anyway this is just a workaround, it would be great if the development team could fix the problem so that we can keep the supported driver, but no one replied on launchpad or on kernel bug tracker.

---

### Post by Rocket J Squirrel on 2010-05-02
Or, a little less work, try installing some backports, i.e.,

```
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```and 

```
sudo apt-get install linux-backports-modules-karmic
```

---

### Post by teo_rossi on 2010-05-02
I've tried that, but I couldn't see any appreciable improvement in performance

---

### Post by Rocket J Squirrel on 2010-05-02
Yeah, sorry -- that was my best shot.

I don't know why Ubuntu has so many problems with wireless. If you look through the forums, it's clearly an ongoing and common issue.

---

### Post by teo_rossi on 2010-05-02
Well in this case I think the problem is with the kernel driver ath9k, because I read about problems with my chip even in Red Hat, Fedora and kernel forums.

---

### Post by shabadoo52 on 2010-05-02
Thanks, teo_rossi!  I'm trying to install the Madwifi drivers and I get an error at step 8 of your instructions: 

```
ted@ted-laptop:~/madwifi/madwifi_last$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/ted/madwifi/madwifi_last modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
make[3]: *** No rule to make target `/home/ted/madwifi/madwifi_last/ath_hal/ah_eeprom_v4k.o', needed by `/home/ted/madwifi/madwifi_last/ath_hal/ath_hal.o'.  Stop.
make[2]: *** [/home/ted/madwifi/madwifi_last/ath_hal] Error 2
make[1]: *** [_module_/home/ted/madwifi/madwifi_last] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2
```

I'm a bit of a n00b when it comes to some of this stuff.  Any idea what the problem is?

---

### Post by diazdiego86 on 2010-05-04
The error in compilation is that the patch creates another folder, my folders looks like this --->

madwifi/
       madwifi_4119_bsdhal/          (folder generated by patch)
       madwifi_last/
       madwifi-4122-ar9285.patch


both folders contents another one, the "ath_hal" folder. So, the problem is in the makefile file, it doesn't find the files provided by the patch. (My english sucks! I hope that you can understand what i mean:D)

the solution is to make a simple copy of these  --->
  cp  -R  madwifi_4119_bsdhal/ath_hal   madwifi_last/ath_hal

and then, continue with the steps... make, sudo make install!

Ah, remember that in the /etc/modules file, it must have only the "ath_pci" module. I had other modules (lp, ath9k)... so, remove or just comment these lines. If I didn't do that, the network-manager doesn't work at all.


BEST REGARDS FROM ARGENTINA :D

---

### Post by diazdiego86 on 2010-05-04
the identation doesn't work



the folders are like :

madwifi/ 

inside of this, are the other three... 
* madwifi_4119_bsdhal/       (folder generated by patch)
* madwifi_last/
* madwifi-4122-ar9285.patch


now, All this worked for me. Wifi performance improves exponentially

---

### Post by ben_malaga on 2010-05-05
Hello [diazdiego86]("http://ubuntuforums.org/member.php?u=1066996")

I had looking a solution with the this problem. I have a atheros ar9285 in a sony vaio. I tried to install madwifi and had the same problem explained by [shabadoo52]("http://ubuntuforums.org/member.php?u=1012584"). 

I had solved the problem. Thank you, thank you [diazdiego86]("http://ubuntuforums.org/member.php?u=1066996").

I had installed the newest ath9k driver. I downloaded it from [**http://wireless.kernel.org/en/users/Download/stable/**]("http://wireless.kernel.org/en/users/Download/stable/")

The problem was strange. If the signal power was lower than 70% the card after download 2Mb stopped to work. However if it had the 100% worked fine. With a continuos ping didn't lost packets but sometimes had a bigger delay. When the signal was lower the delay was bigger and then the connection was dropped.

---

### Post by rasturn on 2010-05-05
Same Problem, Intel wifi, work fine 9.10 but since the update, it works until screensaver kicks in. I disconnect wireless from taskbar then turn it off on the laptop turn it back on then it works until the next time. quick work around but they got to fix this!!
screen saver irrelevant, seems about 30 mins before internet just stops. have to disconnect, off/on, reconnect then it works another 30 or so?

---

### Post by jnick13 on 2010-05-21
Hey all,

I too have a Sony Vaio CW series laptop (VPCCW23FD, a Canada-only model) with Atheros 9285 wireless.  I can confirm the bug in Ubuntu 10.04: wifi connectivity is erratic, dropping to 1Mbps, then increasing into the 60Mbps area, then back down to 1.  Sometimes the connection drops altogether.  Often, the connection speed is reported as "unknown".  It appears large data transfers (such as images/media on a webpage) trigger the bug.  Wifi connectivity under Windows 7 is rock solid.

Something I've noticed that I don't think has been mentioned thus far... the wifi card itself gets very warm, in turn heating up the front of the laptop, from the right of the trackpad to the right edge.  Obviously this only occurs when the wireless is switched ON, so to avoid this, I've switched it off.

I can also confirm the latest compat-wireless and madwifi drivers are both a **bust**.  I also installed wireless backports with no success.

I'm a SysAdmin with a background in application development, and it's my educated guess that the issue is with a buffer somewhere in the driver software.  I have absolutely zero experience in linux driver development, so offering that guess is the extent to which I can help :(

I'll continue troubleshooting and searching various forums.  If I find a solution, I'll provide a link here.

---

### Post by gibzaki on 2010-05-22
I also have a VAIO CW21FX with Atheros 9285 wireless on Ubuntu 10.04 
I'm siting next to my router, the signal is strong but the connection speed is awful.. 5kbps if I'm lucky (300kbps with the wired connection). In windows7 the wifi works like a charm.

I tried the linux-backports-modules-wireless-lucid-generic,linux-backports-modules-wireless-2.6.32-22-generic with no improves.
Also installed the compat-wireless-2.6.34 drivers but it didn't work..still slow transfers.
I haven't tried ndiswrapper yet..

At this point I don't know which drivers are currently installed.
I'm lost, any solution? :(

---

### Post by Ichido on 2010-05-22
> **NightwishFan said:**
> The pefrormance problems on the ath9k driver are fixed install Wireless Kernel Backports.
[Click Here to install..]("apt://linux-backports-modules-wireless-karmic-generic") and press ok to use apturl. Or use:
```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```

I'm also losing my wireless.
It takes forever (5 Minutes) to connect and continally drops off.
So, I ran the code and I got this:

dave :~$ sudo aptitude install linux-backports-modules-wireless-karmic-generic
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
[B]Couldn't find any package whose name or description matched "linux-backports-modules-wireless-karmic-generic"
Couldn't find any package whose name or description matched "linux-backports-modules-wireless-karmic-generic"[/B]
The following packages will be REMOVED:
  libboost-regex1.40.0{u} libphysfs1{u} libsdl-sound1.2{u} 
  libsigc++-1.2-5c2{u} libwxbase2.8-0{u} libwxgtk2.8-0{u} 
  linux-headers-2.6.32-21{u} linux-headers-2.6.32-21-generic{u} 
0 packages upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 98.1MB will be freed.
Do you want to continue? [Y/n/?] 

Now what do I do?

---

### Post by NightwishFan on 2010-05-22
Not sure why. Are you running Karmic? In any case here is a direct link to the package. Try running this command first.
```
sudo aptitude update
```

32bit: [http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb)

64bit: [http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_amd64.deb)

---

### Post by Ichido on 2010-05-22
[QUOTE= Try running this command first.
```
sudo aptitude update
```

32bit: [http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb)[/QUOTE]

I am Running Karmic.

Results from your code:
"Error: Dependency is not satisfiable: linux-backports-modules-2.6.31-20-generic"

---

### Post by NightwishFan on 2010-05-22
That is interesting. Try:
```
sudo apt-get -f install
```

---

### Post by Ichido on 2010-05-22
> **NightwishFan said:**
> That is interesting. Try:
```
sudo apt-get -f install
```

I just got back online :-(
What does this code do?

Just in case I get Kicked Off, THANKS for your help.

---

### Post by Ichido on 2010-05-24
I seem to have fixed my problem by running the following:

1st: sudo apt-get update
2nd: sudo apt-get upgrade 
Then lastly: sudo apt-get install ubuntu-restricted-extras

So far so good.

---

### Post by gibzaki on 2010-06-08
Did not work for me :(

---

### Post by gibzaki on 2010-06-29
Is there anybody out there?

Guys, any news on this issue?

---

### Post by Gordon D on 2010-11-14
I was having a similar problem. Ubuntu 10.10 Maverick. 2 x laptops with wireless - Dell D420 and  Dell Inspiron Mini. Wireless connection rock solid on mains power but kept dropping out on battery. Both dual boot, one with Win XP, one with Win 7. Both worked fine on battery in Windows.

Installed the backports:-
linux-backports-modules-wireless-maverick-generic

So far, so good! Been streaming audio to both of them concurrently for 20 minutes on battery with no drop outs.

Happy Chappy. Was about to go and beat up my Radio Ham enthusiast neighbour, which may have been premature :)

Bit of a n00b, but have attached some config output. Happy to provide more if anyone is interested. Haven't worked out how to get those cool inline attachment window things in my posts!

Cheers, Gordon

---

