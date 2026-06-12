---
title: "wireless not working on Lenovo Q150"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by crisedwards on 2011-01-09
Tried the normal fixes and installed the wrapper, etc. Wired network works fine, and I am able to access some unlocked wifi networks from neighbors, but I cannot access my own password protected network. It just keeps asking for the password and never connects. Fairly new Ubuntu guy here. 

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a001]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a002]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82552 10/100 Network Connection [8086:10fe] (rev 02)

---

### Post by PatchesTheCaveman on 2011-01-10
Please provide all the diagnostic information as explained in this post:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by vb@vsbe.com on 2011-01-15
Sorry I can't help you with the wifi issue, but I hope you can help me: how did you install Ubuntu on Q150? I have a USB stick with the Ubuntu image, but the Q150 still boots Windows7 and the startup setup does not seem to allow to change the boot order..

---

### Post by crisedwards on 2011-01-16
Sorry for duplicate post

---

### Post by crisedwards on 2011-01-16
Deleted duplicate post

---

### Post by crisedwards on 2011-01-16
Deleted duplicate post

---

### Post by crisedwards on 2011-01-16
Thanks. I tried to fix this by moving my wired connection to my office, didn't work. Here are the details:

from lspci:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82552 10/100 Network Connection (rev 02)

from lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d80 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0402 Chicony Electronics Co., Ltd Genius LuxeMate i200 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:3323 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

from ifconfig:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:bf:fc:8e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:febf:fc8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154332963 (154.3 MB)  TX bytes:5137130 (5.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3999 (3.9 KB)  TX bytes:3999 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:3d:3f:95  
          inet6 addr: fe80::76f0:6dff:fe3d:3f95/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5163 (5.1 KB)

from iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

from lsmod: 

Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   218227  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  294989  4 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168092  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184207  0 
intel_agp              26694  2 i915
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
e100                   30356  0 
mii                     4425  1 e100

from dmesg: 

[    0.281603] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.281613] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.281636] system 00:06: [io  0x0a00-0x0a0f] has been reserved
[    0.281646] system 00:06: [io  0x0a10-0x0a1f] has been reserved
[    0.281655] system 00:06: [io  0x0a20-0x0a2f] has been reserved
[    0.281664] system 00:06: [io  0x0a30-0x0a3f] has been reserved
[    0.281683] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.281692] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.281702] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.281712] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.281722] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.281741] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.281751] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.281768] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.281786] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.281796] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.281806] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.281816] system 00:0b: [mem 0x00100000-0x3f6fffff] could not be reserved
[    0.281826] system 00:0b: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.322091] pci 0000:00:1f.2: BAR 5: assigned [mem 0x3f700000-0x3f7003ff]
[    0.322108] pci 0000:00:1f.2: BAR 5: set to [mem 0x3f700000-0x3f7003ff] (PCI address [0x3f700000-0x3f7003ff]
[    0.322118] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.322128] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.322139] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.322148] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.322173] pci 0000:00:1e.0: setting latency timer to 64
[    0.322184] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.322192] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.322200] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.322209] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.322218] pci_bus 0000:00: resource 8 [mem 0x3f700000-0xdfffffff]
[    0.322227] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.322236] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.322244] pci_bus 0000:01: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.322252] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.322259] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.322267] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.322276] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.322285] pci_bus 0000:01: resource 8 [mem 0x3f700000-0xdfffffff]
[    0.322294] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.322405] NET: Registered protocol family 2
[    0.322600] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.323457] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.324609] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.325183] TCP: Hash tables configured (established 131072 bind 65536)
[    0.325192] TCP reno registered
[    0.325203] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.325227] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.325551] NET: Registered protocol family 1
[    0.325596] pci 0000:00:02.0: Boot video device
[    0.325745] PCI: CLS 32 bytes, default 64
[    0.326367] cpufreq-nforce2: No nForce2 chipset.
[    0.326474] Scanning for low memory corruption every 60 seconds
[    0.326915] audit: initializing netlink socket (disabled)
[    0.326942] type=2000 audit(1295185137.320:1): initialized
[    0.350057] highmem bounce pool size: 64 pages
[    0.350075] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.355236] VFS: Disk quotas dquot_6.5.2
[    0.355461] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.357561] fuse init (API version 7.14)
[    0.357887] msgmni has been set to 1709
[    0.359027] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.359037] io scheduler noop registered
[    0.359043] io scheduler deadline registered
[    0.359101] io scheduler cfq registered (default)
[    0.359480] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.359570] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.359862] intel_idle: MWAIT substates: 0x10
[    0.359868] intel_idle: v0.4 model 0x1C
[    0.359874] intel_idle: lapic_timer_reliable_states 0x6
[    0.360248] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.360264] ACPI: Power Button [PWRB]
[    0.360423] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.360435] ACPI: Power Button [PWRF]
[    0.361040] ACPI: acpi_idle yielding to intel_idle
[    0.366095] ERST: Table is not found!
[    0.366815] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.371614] brd: module loaded
[    0.373591] loop: module loaded
[    0.374218] ata_piix 0000:00:1f.2: version 2.13
[    0.374250] ata_piix 0000:00:1f.2: enabling device (0005 -> 0007)
[    0.374267]   alloc irq_desc for 19 on node -1
[    0.374274]   alloc kstat_irqs on node -1
[    0.374292] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.374306] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.374390] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.374559] scsi0 : ata_piix
[    0.374859] scsi1 : ata_piix
[    0.375209] isapnp: Scanning for PnP cards...
[    0.378855] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.378865] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.380104] Fixed MDIO Bus: probed
[    0.380229] PPP generic driver version 2.4.2
[    0.380380] tun: Universal TUN/TAP device driver, 1.6
[    0.380387] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.380636] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.380684]   alloc irq_desc for 23 on node -1
[    0.380691]   alloc kstat_irqs on node -1
[    0.380708] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.380792] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.380801] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.380912] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.380962] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.380979] ehci_hcd 0000:00:1d.7: debug port 1
[    0.384871] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.384909] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaffc00
[    0.399578] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.399970] hub 1-0:1.0: USB hub found
[    0.399986] hub 1-0:1.0: 8 ports detected
[    0.400178] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.400227] uhci_hcd: USB Universal Host Controller Interface driver
[    0.400306] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.400322] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.400331] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.400456] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.400500] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
[    0.400855] hub 2-0:1.0: USB hub found
[    0.400868] hub 2-0:1.0: 2 ports detected
[    0.401010] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.401025] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.401033] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.401134] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.401192] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.401554] hub 3-0:1.0: USB hub found
[    0.401567] hub 3-0:1.0: 2 ports detected
[    0.401698]   alloc irq_desc for 18 on node -1
[    0.401705]   alloc kstat_irqs on node -1
[    0.401721] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.401734] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.401742] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.401842] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.401901] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
[    0.402234] hub 4-0:1.0: USB hub found
[    0.402247] hub 4-0:1.0: 2 ports detected
[    0.402382]   alloc irq_desc for 16 on node -1
[    0.402389]   alloc kstat_irqs on node -1
[    0.402403] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.402417] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.402425] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.402536] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.402592] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000dc00
[    0.402961] hub 5-0:1.0: USB hub found
[    0.402975] hub 5-0:1.0: 2 ports detected
[    0.403308] PNP: No PS/2 controller found. Probing ports directly.
[    0.403771] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.403787] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.404132] mice: PS/2 mouse device common for all mice
[    0.404474] rtc_cmos 00:03: RTC can wake from S4
[    0.404602] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.404642] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.404989] device-mapper: uevent: version 1.0.3
[    0.416057] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.467765] device-mapper: multipath: version 1.1.1 loaded
[    0.467776] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.476145] EISA: Probing bus 0 at eisa.0
[    0.476156] EISA: Cannot allocate resource for mainboard
[    0.476164] Cannot allocate resource for EISA slot 1
[    0.476172] Cannot allocate resource for EISA slot 2
[    0.476180] Cannot allocate resource for EISA slot 3
[    0.476187] Cannot allocate resource for EISA slot 4
[    0.476195] Cannot allocate resource for EISA slot 5
[    0.476202] Cannot allocate resource for EISA slot 6
[    0.476210] Cannot allocate resource for EISA slot 7
[    0.476217] Cannot allocate resource for EISA slot 8
[    0.476223] EISA: Detected 0 cards.
[    0.495946] cpuidle: using governor ladder
[    0.496149] cpuidle: using governor menu
[    0.496987] TCP cubic registered
[    0.497419] NET: Registered protocol family 10
[    0.498446] lo: Disabled Privacy Extensions
[    0.499070] NET: Registered protocol family 17
[    0.499206] Using IPI No-Shortcut mode
[    0.499668] PM: Resume from disk failed.
[    0.499697] registered taskstats version 1
[    0.500051]   Magic number: 11:130:635
[    0.500161] rtc_cmos 00:03: setting system clock to 2011-01-16 13:38:57 UTC (1295185137)
[    0.500170] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.500176] EDD information not available.
[    0.554716] ata1.00: ATA-8: WDC WD1600BEVT-24A23T0, 01.01A02, max UDMA/133
[    0.554727] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.568752] ata1.00: configured for UDMA/133
[    0.711864] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.728946] isapnp: No Plug & Play device found
[    0.729292] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 01.0 PQ: 0 ANSI: 5
[    0.729718] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.729966] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.730181] sd 0:0:0:0: [sda] Write Protect is off
[    0.730192] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.730286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.730776]  sda: sda1 sda2 < sda5 >
[    0.811456] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.836885] Freeing initrd memory: 10508k freed
[    0.845379] Freeing unused kernel memory: 688k freed
[    0.846200] Write protecting the kernel text: 4932k
[    0.846292] Write protecting the kernel read-only data: 1980k
[    0.889233] udev[79]: starting version 163
[    1.092889] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.092899] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.092984]   alloc irq_desc for 20 on node -1
[    1.092991]   alloc kstat_irqs on node -1
[    1.093010] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.118444] e100 0000:01:08.0: PME# disabled
[    1.200143] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.254333] e100 0000:01:08.0: eth0: addr 0xfebff000, irq 20, MAC addr 70:71:bc:bf:fc:8e
[    1.282164] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.282175] EXT4-fs (sda1): write access will be enabled during recovery
[    1.524081] usbcore: registered new interface driver hiddev
[    1.573713] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2
[    1.573992] generic-usb 0003:04F2:0402.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony USB Keyboard] on usb-0000:00:1d.1-2/input0
[    1.716632] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input3
[    1.717044] generic-usb 0003:04F2:0402.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony USB Keyboard] on usb-0000:00:1d.1-2/input1
[    1.717104] usbcore: registered new interface driver usbhid
[    1.717112] usbhid: USB HID core driver
[    1.720592] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.907315] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    1.907655] generic-usb 0003:0461:4D80.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1/input0
[    5.754406] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.777727] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179812
[    5.777885] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179811
[    5.777931] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179810
[    5.777969] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179809
[    5.778010] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179808
[    5.778048] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179807
[    5.778088] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179806
[    5.778125] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179805
[    5.778165] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179804
[    5.778202] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179803
[    5.778242] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179800
[    5.778279] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179799
[    5.778319] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179798
[    5.778355] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179797
[    5.778395] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179796
[    5.778432] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179795
[    5.778473] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179794
[    5.778509] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179793
[    5.778550] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179792
[    5.778588] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179791
[    5.778628] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179790
[    5.778665] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179789
[    5.778705] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179788
[    5.778742] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179787
[    5.778784] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179786
[    5.778820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179785
[    5.778861] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179784
[    5.778898] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179783
[    5.778938] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179780
[    5.778975] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179779
[    5.779015] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179778
[    5.779118] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179777
[    5.779161] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179776
[    5.779200] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179775
[    5.779241] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179774
[    5.779278] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179773
[    5.779318] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179770
[    5.779356] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179769
[    5.779397] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179768
[    5.779434] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179767
[    5.779474] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179766
[    5.779511] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179765
[    5.779552] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179764
[    5.779588] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179763
[    5.779629] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179762
[    5.779665] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179761
[    5.779707] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179758
[    5.779746] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179757
[    5.779787] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179756
[    5.779823] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179755
[    5.779865] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179754
[    5.779902] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179753
[    5.779942] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179752
[    5.779979] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179751
[    5.780044] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179750
[    5.780082] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179749
[    5.780124] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179748
[    5.780161] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179747
[    5.780203] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179744
[    5.780242] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179743
[    5.780283] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179742
[    5.780319] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179741
[    5.780360] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179740
[    5.780397] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179739
[    5.780437] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179738
[    5.780474] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179737
[    5.780521] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179736
[    5.780560] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179735
[    5.780601] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179734
[    5.780638] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179733
[    5.780678] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179730
[    5.780715] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179729
[    5.780757] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179725
[    5.796296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9175627
[    5.796354] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179723
[    5.796394] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9176011
[    5.796436] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672317
[    5.796478] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672315
[    5.796515] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672314
[    5.796552] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672313
[    5.796588] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672319
[    5.796611] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9308708
[    5.809055] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179708
[    5.809108] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9175971
[    5.809149] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672312
[    5.809171] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672251
[    5.829790] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672196
[    5.829845] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3672167
[    5.829886] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3671819
[    5.829926] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3671736
[    5.829965] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3671705
[    5.830013] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3671688
[    5.851813] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864344
[    5.871069] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9179696
[    5.886050] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9175423
[    5.886094] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864328
[    5.886117] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864327
[    5.886137] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864326
[    5.886157] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864325
[    5.886176] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864324
[    5.886194] EXT4-fs (sda1): 100 orphan inodes deleted
[    5.886201] EXT4-fs (sda1): recovery complete
[    7.349223] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   23.222169] udev[310]: starting version 163
[   23.253239] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
[   23.415291] lp: driver loaded but no devices found
[   23.759229] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.771184] Disabling lock debugging due to kernel taint
[   23.894421] Linux agpgart interface v0.103
[   24.061567] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[   24.062425] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   24.073882] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   24.160741] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   24.264867] type=1400 audit(1295203161.261:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=575 comm="apparmor_parser"
[   24.265678] type=1400 audit(1295203161.261:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=575 comm="apparmor_parser"
[   24.266146] type=1400 audit(1295203161.261:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=575 comm="apparmor_parser"
[   24.405541] [drm] Initialized drm 1.1.0 20060810
[   24.408095] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   24.674629] ndiswrapper: driver net8192su (Realtek Semiconductor Corp.,11/04/2010,1084.44.1104.2010) loaded
[   24.753988] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.754002] i915 0000:00:02.0: setting latency timer to 64
[   24.988193] type=1400 audit(1295203161.985:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=741 comm="apparmor_parser"
[   24.991583] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.995504] type=1400 audit(1295203161.989:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=742 comm="apparmor_parser"
[   24.996318] type=1400 audit(1295203161.993:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
[   25.004193]   alloc irq_desc for 40 on node -1
[   25.004203]   alloc kstat_irqs on node -1
[   25.004226] i915 0000:00:02.0: irq 40 for MSI/MSI-X
[   25.004253] [drm] set up 7M of stolen space
[   25.005534] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   25.005898] [drm] initialized overlay support
[   25.007644] type=1400 audit(1295203162.001:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
[   25.065516] type=1400 audit(1295203162.061:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=756 comm="apparmor_parser"
[   25.066551] type=1400 audit(1295203162.061:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=756 comm="apparmor_parser"
[   25.074240] type=1400 audit(1295203162.069:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=759 comm="apparmor_parser"
[   25.336867] Console: switching to colour frame buffer device 200x56
[   25.358187] fb0: inteldrmfb frame buffer device
[   25.358195] drm: registered panic notifier
[   25.358952] Slow work thread pool: Starting up
[   25.359186] Slow work thread pool: Ready
[   25.359258] No ACPI video bus found
[   25.359387] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   25.359962] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.360060]   alloc irq_desc for 41 on node -1
[   25.360068]   alloc kstat_irqs on node -1
[   25.360092] HDA Intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   25.360145] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.470425] hda_codec: ALC662 rev1: BIOS auto-probing.
[   26.630245] wlan0: ethernet device 74:f0:6d:3d:3f:95 using NDIS driver: net8192su, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192S Wireless LAN USB NIC                                     ', 13D3:3323.F.conf
[   26.630345] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   26.630489] usbcore: registered new interface driver ndiswrapper
[   26.675171] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.760916] ppdev: user-space parallel port driver
[   26.808671] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   26.809289] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.776896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   37.552018] eth0: no IPv6 routers present
[   51.636907] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.728024] wlan0: no IPv6 routers present
[   71.370370] lo: Disabled Privacy Extensions

from sudo lshw -C network:
 *-network               
       description: Ethernet interface
       product: 82552 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 70:71:bc:bf:fc:8e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:febff000-febfffff ioport:ec00(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 74:f0:6d:3d:3f:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.56+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g

from iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:C4:B3:26
                    ESSID:"poop!"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:B2:02:05:26
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:2F:6A:84:36
                    ESSID:"White"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:BF:20:1C:C0
                    ESSID:"\x00"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:B2:0B:68:88
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:1E:52:79:84:25
                    ESSID:"Historicity"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1C:10:0B:B0:A9
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:24:B2:D5:D2:48
                    ESSID:"Netgear1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


from lsb_release -d:
Ubuntu 10.10

from uname -mr:
2.6.35-24-generic i686

from sudo /etc/init.d/networking restart:
Ignoring unknown interface eth0=eth0.

---

### Post by crisedwards on 2011-01-16
Sorry about the dupe posts. Browser kept hanging up and I didn't know the things were posting.

---

