---
title: "Wireless: Device not ready.  Broadcom Dell Ins. 6000"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by jrb56 on 2009-10-31
Dell Inspiron

john@john-dell:~$ lspci -nn | grep 'Wireless Brand'
john@john-dell:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-dell:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
john@john-dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:6f:e1:64  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6f:e164/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9234332 (9.2 MB)  TX bytes:386570 (386.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

john@john-dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-dell:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
arc4                    1660  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
ecb                     2524  2 
pcmcia                 36808  0 
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   122136  0 
sdhci_pci               7100  0 
joydev                 10272  0 
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              181236  1 b43
yenta_socket           24200  1 
sdhci                  17472  1 sdhci_pci
soundcore               7264  1 snd
cfg80211               93052  2 b43,mac80211
rsrc_nonstatic         11644  1 yenta_socket
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
led_class               4096  2 b43,sdhci
psmouse                56180  0 
dell_wmi                2564  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
b44                    28684  0 
ssb                    35300  2 b43,b44
mii                     5212  1 b44
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
john@john-dell:~$ 

.209807] system 00:0b: ioport range 0xcfc0-0xcfdf has been reserved
[    0.209813] system 00:0b: ioport range 0xd3b0-0xd3bb has been reserved
[    0.209818] system 00:0b: ioport range 0xd3c0-0xd3df has been reserved
[    0.209824] system 00:0b: ioport range 0xd7b0-0xd7bb has been reserved
[    0.209829] system 00:0b: ioport range 0xd7c0-0xd7df has been reserved
[    0.209835] system 00:0b: ioport range 0xdbb0-0xdbbb has been reserved
[    0.209840] system 00:0b: ioport range 0xdbc0-0xdbdf has been reserved
[    0.209846] system 00:0b: ioport range 0xdfb0-0xdfbb has been reserved
[    0.209852] system 00:0b: ioport range 0xdfc0-0xdfdf has been reserved
[    0.209857] system 00:0b: ioport range 0xe3b0-0xe3bb has been reserved
[    0.209863] system 00:0b: ioport range 0xe3c0-0xe3df has been reserved
[    0.209868] system 00:0b: ioport range 0xe7b0-0xe7bb has been reserved
[    0.209874] system 00:0b: ioport range 0xe7c0-0xe7df has been reserved
[    0.209880] system 00:0b: ioport range 0xebb0-0xebbb has been reserved
[    0.209885] system 00:0b: ioport range 0xebc0-0xebdf has been reserved
[    0.209891] system 00:0b: ioport range 0xefb0-0xefbb has been reserved
[    0.209896] system 00:0b: ioport range 0xefc0-0xefdf has been reserved
[    0.209902] system 00:0b: ioport range 0xf3b0-0xf3bb has been reserved
[    0.209908] system 00:0b: ioport range 0xf3c0-0xf3df has been reserved
[    0.209913] system 00:0b: ioport range 0xf7b0-0xf7bb has been reserved
[    0.209919] system 00:0b: ioport range 0xf7c0-0xf7df has been reserved
[    0.209925] system 00:0b: ioport range 0xfbb0-0xfbbb has been reserved
[    0.209931] system 00:0b: ioport range 0xfbc0-0xfbdf has been reserved
[    0.209936] system 00:0b: ioport range 0xffb0-0xffbb has been reserved
[    0.209942] system 00:0b: ioport range 0xffc0-0xffdf has been reserved
[    0.244711] AppArmor: AppArmor Filesystem Enabled
[    0.244760] pci 0000:00:1e.0: BAR 13: can't allocate I/O resource [0x10000-0xffff]
[    0.244777] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.244781] pci 0000:03:01.0:   IO window: 0x001400-0x0014ff
[    0.244789] pci 0000:03:01.0:   IO window: 0x001800-0x0018ff
[    0.244796] pci 0000:03:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.244803] pci 0000:03:01.0:   MEM window: 0x84000000-0x87ffffff
[    0.244811] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.244814] pci 0000:00:1e.0:   IO window: disabled
[    0.244822] pci 0000:00:1e.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.244830] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.244847] pci 0000:00:1e.0: setting latency timer to 64
[    0.244859] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.244869]   alloc irq_desc for 19 on node -1
[    0.244874]   alloc kstat_irqs on node -1
[    0.244882] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.244893] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.244898] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.244902] pci_bus 0000:03: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.244907] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.244911] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.244915] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.244920] pci_bus 0000:04: resource 0 io:  [0x1400-0x14ff]
[    0.244924] pci_bus 0000:04: resource 1 io:  [0x1800-0x18ff]
[    0.244928] pci_bus 0000:04: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.244933] pci_bus 0000:04: resource 3 mem: [0x84000000-0x87ffffff]
[    0.244988] NET: Registered protocol family 2
[    0.245130] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.245585] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.246835] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.247618] TCP: Hash tables configured (established 131072 bind 65536)
[    0.247623] TCP reno registered
[    0.247807] NET: Registered protocol family 1
[    0.247955] Trying to unpack rootfs image as initramfs...
[    0.567159] Freeing initrd memory: 7457k freed
[    0.575310] cpufreq-nforce2: No nForce2 chipset.
[    0.575357] Scanning for low memory corruption every 60 seconds
[    0.575539] audit: initializing netlink socket (disabled)
[    0.575567] type=2000 audit(1257019871.571:1): initialized
[    0.589185] highmem bounce pool size: 64 pages
[    0.589194] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.591374] VFS: Disk quotas dquot_6.5.2
[    0.591456] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.592301] fuse init (API version 7.12)
[    0.592423] msgmni has been set to 1706
[    0.592713] alg: No test for stdrng (krng)
[    0.592731] io scheduler noop registered
[    0.592735] io scheduler anticipatory registered
[    0.592738] io scheduler deadline registered
[    0.592809] io scheduler cfq registered (default)
[    0.592829] pci 0000:00:02.0: Boot video device
[    0.593049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.593085] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.593769] ACPI: AC Adapter [AC] (on-line)
[    0.593902] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.594442] ACPI: Lid Switch [LID]
[    0.594511] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.594519] ACPI: Power Button [PBTN]
[    0.594584] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.594589] ACPI: Sleep Button [SBTN]
[    0.595132] Marking TSC unstable due to TSC halts in idle
[    0.595168] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.595204] processor LNXCPU:00: registered as cooling_device0
[    0.595210] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.599186] Switched to high resolution mode on CPU 0
[    0.602063] thermal LNXTHERM:01: registered as thermal_zone0
[    0.602075] ACPI: Thermal Zone [THM] (48 C)
[    0.602142] isapnp: Scanning for PnP cards...
[    0.899670] ACPI: Battery Slot [BAT0] (battery present)
[    0.986795] isapnp: No Plug & Play device found
[    0.988414] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.988955]   alloc irq_desc for 17 on node -1
[    0.988959]   alloc kstat_irqs on node -1
[    0.988970] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.988981] serial 0000:00:1e.3: PCI INT B disabled
[    0.990338] brd: module loaded
[    0.991014] loop: module loaded
[    0.991126] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.991240] ahci 0000:00:1f.2: version 3.0
[    0.991256] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.991274] ahci 0000:00:1f.2: PCI INT B disabled
[    0.991280] ahci: probe of 0000:00:1f.2 failed with error -22
[    0.991337] ata_piix 0000:00:1f.2: version 2.13
[    0.991346] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.991354] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.144038] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.144226] scsi0 : ata_piix
[    1.144350] scsi1 : ata_piix
[    1.144558] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.144563] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.145783] Fixed MDIO Bus: probed
[    1.145839] PPP generic driver version 2.4.2
[    1.145963] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.145991]   alloc irq_desc for 16 on node -1
[    1.145995]   alloc kstat_irqs on node -1
[    1.146004] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.146025] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.146031] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.146102] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.150017] ehci_hcd 0000:00:1d.7: debug port 1
[    1.150026] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.150624] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    1.164020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.164130] usb usb1: configuration #1 chosen from 1 choice
[    1.164180] hub 1-0:1.0: USB hub found
[    1.164192] hub 1-0:1.0: 8 ports detected
[    1.164299] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.164325] uhci_hcd: USB Universal Host Controller Interface driver
[    1.164364] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.164375] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.164380] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.164438] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.164469] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.164592] usb usb2: configuration #1 chosen from 1 choice
[    1.164631] hub 2-0:1.0: USB hub found
[    1.164641] hub 2-0:1.0: 2 ports detected
[    1.164709] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.164718] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.164723] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.164764] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.164804] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.164924] usb usb3: configuration #1 chosen from 1 choice
[    1.164962] hub 3-0:1.0: USB hub found
[    1.164972] hub 3-0:1.0: 2 ports detected
[    1.165038]   alloc irq_desc for 18 on node -1
[    1.165042]   alloc kstat_irqs on node -1
[    1.165050] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.165060] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.165065] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.165108] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.165146] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.165261] usb usb4: configuration #1 chosen from 1 choice
[    1.165299] hub 4-0:1.0: USB hub found
[    1.165308] hub 4-0:1.0: 2 ports detected
[    1.165367] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.165377] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.165382] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.165425] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.165466] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.165575] usb usb5: configuration #1 chosen from 1 choice
[    1.165616] hub 5-0:1.0: USB hub found
[    1.165627] hub 5-0:1.0: 2 ports detected
[    1.165766] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.170336] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.170345] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.170426] mice: PS/2 mouse device common for all mice
[    1.170630] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.170665] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.170821] device-mapper: uevent: version 1.0.3
[    1.170951] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.171059] device-mapper: multipath: version 1.1.0 loaded
[    1.171063] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.171233] EISA: Probing bus 0 at eisa.0
[    1.171242] Cannot allocate resource for EISA slot 1
[    1.171282] EISA: Detected 0 cards.
[    1.171412] cpuidle: using governor ladder
[    1.171501] cpuidle: using governor menu
[    1.172226] TCP cubic registered
[    1.172462] NET: Registered protocol family 10
[    1.173096] lo: Disabled Privacy Extensions
[    1.173535] NET: Registered protocol family 17
[    1.173563] Bluetooth: L2CAP ver 2.13
[    1.173566] Bluetooth: L2CAP socket layer initialized
[    1.173570] Bluetooth: SCO (Voice Link) ver 0.6
[    1.173573] Bluetooth: SCO socket layer initialized
[    1.173630] Bluetooth: RFCOMM TTY layer initialized
[    1.173635] Bluetooth: RFCOMM socket layer initialized
[    1.173638] Bluetooth: RFCOMM ver 1.11
[    1.173680] Using IPI No-Shortcut mode
[    1.173776] PM: Resume from disk failed.
[    1.173802] registered taskstats version 1
[    1.173970]   Magic number: 13:94:196
[    1.174081] rtc_cmos 00:06: setting system clock to 2009-10-31 20:11:12 UTC (1257019872)
[    1.174087] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.174089] EDD information not available.
[    1.175754] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.312777] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM CDD5263, UD91, max UDMA/33
[    1.313145] ata1.00: ATA-6: TOSHIBA MK4026GAX, PA102D, max UDMA/100
[    1.313150] ata1.00: 78140160 sectors, multi 8: LBA 
[    1.313170] ata1.00: applying bridge limits
[    1.328695] ata2.00: configured for UDMA/33
[    1.328993] ata1.00: configured for UDMA/100
[    1.329166] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4026GA PA10 PQ: 0 ANSI: 5
[    1.329351] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.329408] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.329478] sd 0:0:0:0: [sda] Write Protect is off
[    1.329483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.329519] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.329701]  sda:
[    1.330415] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD CDD5263 UD91 PQ: 0 ANSI: 5
[    1.333415] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.333420] Uniform CD-ROM driver Revision: 3.20
[    1.333538] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.333598] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.389979]  sda1 sda2 < sda5 >
[    1.420076] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.420096] Freeing unused kernel memory: 540k freed
[    1.420529] Write protecting the kernel text: 4568k
[    1.420584] Write protecting the kernel read-only data: 1836k
[    1.620756] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/input/input5
[    1.620822] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.620884] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.620972] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:23/input/input6
[    1.621006] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    1.660032] Clocksource tsc unstable (delta = -234832902 ns)
[    1.707947] Linux agpgart interface v0.103
[    1.776745] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    1.777220] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.780869] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.862493] [drm] Initialized drm 1.1.0 20060810
[    1.885066] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.885076] i915 0000:00:02.0: setting latency timer to 64
[    2.001711] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.005158] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[    2.010979] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.531924] [drm] DAC-6: set mode 640x480 0
[    2.758690] [drm] TV-14: set mode NTSC 480i 0
[    2.780261] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.780300] b44.c:v2.0
[    2.780341] ohci1394 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.889006] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfdfb800-dfdfbfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.906996] [drm] fb0: inteldrmfb frame buffer device
[    2.907011] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.918127] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:43:6f:e1:64
[    2.974243] render error detected, EIR: 0x00000010
[    2.974248] page table error
[    2.974250]   PGTBL_ER: 0x00000100
[    2.974255] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.974265] render error detected, EIR: 0x00000010
[    2.974268] page table error
[    2.974270]   PGTBL_ER: 0x00000100
[    2.985924] [drm] LVDS-8: set mode 1280x800 17
[    3.365632] Console: switching to colour frame buffer device 160x50
[    3.767413] PM: Starting manual resume from disk
[    3.767420] PM: Resume from partition 8:5
[    3.767424] PM: Checking hibernation image.
[    3.767635] PM: Resume from disk failed.
[    3.799049] EXT4-fs (sda1): barriers enabled
[    3.818330] kjournald2 starting: pid 360, dev sda1:8, commit interval 5 seconds
[    3.818347] EXT4-fs (sda1): delayed allocation enabled
[    3.818353] EXT4-fs: file extents enabled
[    3.824504] EXT4-fs: mballoc enabled
[    3.824526] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.168203] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc000313578c1]
[    4.699003] type=1505 audit(1257019876.021:2): operation="profile_load" pid=383 name=/usr/share/gdm/guest-session/Xsession
[    4.946915] type=1505 audit(1257019876.269:3): operation="profile_load" pid=384 name=/sbin/dhclient3
[    4.947023] type=1505 audit(1257019876.269:4): operation="profile_load" pid=384 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.947091] type=1505 audit(1257019876.269:5): operation="profile_load" pid=384 name=/usr/lib/connman/scripts/dhclient-script
[   20.912156] type=1505 audit(1257019892.237:6): operation="profile_load" pid=385 name=/usr/bin/evince
[   20.913255] type=1505 audit(1257019892.237:7): operation="profile_load" pid=385 name=/usr/bin/evince-previewer
[   20.914195] type=1505 audit(1257019892.237:8): operation="profile_load" pid=385 name=/usr/bin/evince-thumbnailer
[   21.625154] type=1505 audit(1257019892.949:9): operation="profile_load" pid=387 name=/usr/lib/cups/backend/cups-pdf
[   21.625401] type=1505 audit(1257019892.949:10): operation="profile_load" pid=387 name=/usr/sbin/cupsd
[   21.753123] type=1505 audit(1257019893.077:11): operation="profile_load" pid=388 name=/usr/sbin/tcpdump
[   22.555044] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   23.047521] EXT4-fs (sda1): internal journal on sda1:8
[   23.196968] udev: starting version 147
[   24.820262] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.015253] intel_rng: FWH not detected
[   25.256869] dell-wmi: No known WMI GUID found
[   26.018407] lp: driver loaded but no devices found
[   26.134436] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   26.161273] cfg80211: Calling CRDA to update world regulatory domain
[   26.175486] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   26.464089] sdhci: Secure Digital Host Controller Interface driver
[   26.464095] sdhci: Copyright(c) Pierre Ossman
[   26.874727] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0188]
[   27.000795] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   27.000802] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   27.000809] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   27.000822] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   27.000827] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   27.041354] cfg80211: World regulatory domain updated:
[   27.041361]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.041366]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.041371]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.041375]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.041379]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.041383]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.583077] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[   28.583103] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[   28.585180] Registered led device: mmc0::
[   28.586234] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[   29.038894] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   29.152266] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.309727] type=1505 audit(1257019900.633:12): operation="profile_replace" pid=769 name=/usr/share/gdm/guest-session/Xsession
[   29.562496] type=1505 audit(1257019900.885:13): operation="profile_replace" pid=772 name=/sbin/dhclient3
[   29.562732] type=1505 audit(1257019900.885:14): operation="profile_replace" pid=772 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   29.562857] type=1505 audit(1257019900.885:15): operation="profile_replace" pid=772 name=/usr/lib/connman/scripts/dhclient-script
[   30.084975] phy0: Selected rate control algorithm 'minstrel'
[   30.085948] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   30.288703] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   30.290450] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   30.291199] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   30.291822] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   30.292700] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.895730] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.895797] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   31.720028] intel8x0_measure_ac97_clock: measured 55374 usecs (2668 samples)
[   31.720034] intel8x0: clocking to 48000
[   33.567744] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.787418] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   33.844574] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   33.860610] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   33.860706] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   33.860792] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   34.792157] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   34.800666] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   34.810987] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.811083] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   34.811167] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   36.816205] b44: eth0: Link is up at 100 Mbps, full duplex.
[   36.816211] b44: eth0: Flow control is off for TX and off for RX.
[   36.816957] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   37.235169] [drm] DAC-6: set mode 640x480 0
[   37.456049] [drm] DAC-6: set mode 640x480 0
[   37.868988] [drm] TV-14: set mode NTSC 480i 0
[   38.148740] [drm] TV-14: set mode NTSC 480i 0
[   38.465423] [drm] DAC-6: set mode 640x480 0
[   38.677164] [drm] DAC-6: set mode 640x480 0
[   39.113599] [drm] TV-14: set mode NTSC 480i 0
[   39.392724] [drm] TV-14: set mode NTSC 480i 0
[   47.044024] eth0: no IPv6 routers present
[   50.632829] type=1505 audit(1257019921.957:16): operation="profile_replace" pid=773 name=/usr/bin/evince
[   50.634846] type=1505 audit(1257019921.957:17): operation="profile_replace" pid=773 name=/usr/bin/evince-previewer
[   50.638148] type=1505 audit(1257019921.961:18): operation="profile_replace" pid=773 name=/usr/bin/evince-thumbnailer
[   51.152133] type=1505 audit(1257019922.477:19): operation="profile_replace" pid=1297 name=/usr/lib/cups/backend/cups-pdf
[   51.186994] type=1505 audit(1257019922.509:20): operation="profile_replace" pid=1297 name=/usr/sbin/cupsd
[   51.352260] type=1505 audit(1257019922.677:21): operation="profile_replace" pid=1299 name=/usr/sbin/tcpdump
[   52.466686] [drm] DAC-6: set mode 640x480 0
[   52.574961] [drm] DAC-6: set mode 640x480 0
[   52.786178] [drm] TV-14: set mode NTSC 480i 0
[   52.935319] [drm] TV-14: set mode NTSC 480i 0
[   53.147513] [drm] DAC-6: set mode 640x480 0
[   53.256820] [drm] DAC-6: set mode 640x480 0
[   53.475390] [drm] TV-14: set mode NTSC 480i 0
[   53.621981] [drm] TV-14: set mode NTSC 480i 0
[   53.649153] ppdev: user-space parallel port driver
[   53.782853] [drm] DAC-6: set mode 640x480 0
[   53.891984] [drm] DAC-6: set mode 640x480 0
[   54.103500] [drm] TV-14: set mode NTSC 480i 0
[   54.247591] [drm] TV-14: set mode NTSC 480i 0
[   59.732988] [drm] DAC-6: set mode 640x480 0
[   59.847370] [drm] DAC-6: set mode 640x480 0
[   60.051525] [drm] TV-14: set mode NTSC 480i 0
[   60.193866] [drm] TV-14: set mode NTSC 480i 0
[  227.184511] b43-phy1: Broadcom 4306 WLAN found (core revision 5)
[  227.232851] phy1: Selected rate control algorithm 'minstrel'
[  227.292066] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  227.297262] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  227.308519] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  227.308527] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  227.308532] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  227.314581] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  227.329681] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  227.339064] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  227.339072] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  227.339077] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  398.677008] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  398.677014] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  398.677019] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
john@john-dell:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:6f:e1:64
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.101 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfdfc000-dfdfdfff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:1a:f1:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
john@john-dell:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

john@john-dell:~$ lsb_release -d
Description:    Ubuntu 9.10
john@john-dell:~$ uname -mr
2.6.31-14-generic i686
john@john-dell:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
john@john-dell:~$

---

### Post by Ayuthia on 2009-10-31
Have you tried going into System->Administration->Hardware Drivers and enabled the b43 driver?

---

### Post by jrb56 on 2009-10-31
> **Ayuthia said:**
> Have you tried going into System->Administration->Hardware Drivers and enabled the b43 driver?

Yes I did that, but it still says the device is not ready

---

### Post by Ayuthia on 2009-10-31
Can you try the following from the terminal:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo iwlist scan
```
If it produces any error messages, please post the following:
```
dmesg|grep b43
ls /lib/firmware/b43*
```

The first set of commands will remove and reload your network drivers and then scan for wireless sites.

The second set of commands will confirm that the firmware is installed and also check the firmware folder to see if it is actually installed.

---

### Post by jrb56 on 2009-10-31
Hi, I tried that first command and now my wired connection doesn't work either.  I clicked on the connections up on top and it says "no network devices available."
So I can't copy and paste the results of the second set of commands because I'm on a different computer.

---

### Post by Ayuthia on 2009-10-31
Interesting.  You should be able to reboot and all should be back to normal (without the wireless).  It sounds like the firmware for you wireless is not there.  At least these symptoms point that direction.

If you restart and your wired connection is working again, please post the results of:
```
ls /lib/firmware/b43*
```

---

### Post by Jagsjim on 2009-11-01
I'm having the same problems.  Here is a copy of my log:

a0g0bsinitvals4.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  pcm5.fw
a0g0bsinitvals5.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  ucode11.fw
a0g0bsinitvals9.fw   b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode13.fw
a0g0initvals4.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode14.fw
a0g0initvals5.fw     b0g0bsinitvals5.fw   lp0initvals14.fw    ucode15.fw
a0g0initvals9.fw     b0g0bsinitvals9.fw   lp0initvals15.fw    ucode4.fw
a0g1bsinitvals13.fw  b0g0initvals13.fw    n0absinitvals11.fw  ucode5.fw
a0g1bsinitvals5.fw   b0g0initvals4.fw     n0bsinitvals11.fw   ucode9.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0initvals11.fw
a0g1initvals13.fw    b0g0initvals9.fw     pcm4.fw

/lib/firmware/b43legacy:
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw  b0g0initvals2.fw  ucode11.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode2.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw  pcm4.fw           ucode4.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw  pcm5.fw           ucode5.fw

---

### Post by Ayuthia on 2009-11-01
> **Jagsjim said:**
> I'm having the same problems.  Here is a copy of my log:

a0g0bsinitvals4.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  pcm5.fw
a0g0bsinitvals5.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  ucode11.fw
a0g0bsinitvals9.fw   b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode13.fw
a0g0initvals4.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode14.fw
a0g0initvals5.fw     b0g0bsinitvals5.fw   lp0initvals14.fw    ucode15.fw
a0g0initvals9.fw     b0g0bsinitvals9.fw   lp0initvals15.fw    ucode4.fw
a0g1bsinitvals13.fw  b0g0initvals13.fw    n0absinitvals11.fw  ucode5.fw
a0g1bsinitvals5.fw   b0g0initvals4.fw     n0bsinitvals11.fw   ucode9.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0initvals11.fw
a0g1initvals13.fw    b0g0initvals9.fw     pcm4.fw

/lib/firmware/b43legacy:
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw  b0g0initvals2.fw  ucode11.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode2.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw  pcm4.fw           ucode4.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw  pcm5.fw           ucode5.fw

It looks like your firmware is there.

Can you post the results of:
```
dmesg|grep b43
lsmod|grep -e b4 -e ssb -e wl -e ndis
lshw -C network
```

---

### Post by serek on 2009-11-01
Hi Ayuthia,

I have the same problem as above. It's Dell Latitude D620 laptop - damn standard brick.

Here is the output you have asked about.
```

root@talky:~# dmesg|grep b43
[    1.512207] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.512228] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    6.952586] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   12.636114] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   13.184509] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   13.189396] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   13.189402] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   13.189406] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.876095] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   14.879556] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   14.885324] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   14.885385] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   14.885444] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
root@talky:~# lsmod|grep -e b4 -e ssb -e wl -e ndis
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35300  1 b43
root@talky:~# lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:06:9e:37
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5752-v3.19 ip=172.24.2.44 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:efcf0000-efcfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:a8:06:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Ayuthia on 2009-11-01
> **serek said:**
> Hi Ayuthia,

I have the same problem as above. It's Dell Latitude D620 laptop - damn standard brick.

Here is the output you have asked about.
```

root@talky:~# dmesg|grep b43
[    1.512207] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.512228] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    6.952586] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   12.636114] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   13.184509] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   13.189396] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   13.189402] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   13.189406] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.876095] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   14.879556] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   14.885324] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   14.885385] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   14.885444] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
root@talky:~# lsmod|grep -e b4 -e ssb -e wl -e ndis
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35300  1 b43
root@talky:~# lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:06:9e:37
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5752-v3.19 ip=172.24.2.44 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:efcf0000-efcfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:a8:06:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

Does /lib/firmware have the files:
```
ls /lib/firmware/b43*
```

---

### Post by serek on 2009-11-01
Guys,

I got it resolved. See my "procedure":

1. As suggested earlier in this thread:

```

sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo iwlist scan

```

Last command did not returned anything promising. I have decided to give it a go with reboot.

2. After reboot first thing - visit to System->Administration->Hardware Drivers.

And there were 2 options now (checked before doing anything and the list was empty):

- Broadcom B43 wireless driver
- Broadcom STA wireless driver

3. First one installed - no change

4. Second installed - got a message that my Ubuntu needs reboot.

5. After reboot I had wireless networks available to me via NetworkManager applet in tray.

That's all. Good luck to everyone.

I hope there won't many more of those "small" things, which makes me disappointed.

Enjoy 9.10!

---

### Post by serek on 2009-11-01
> **Ayuthia said:**
> Does /lib/firmware have the files:
```
ls /lib/firmware/b43*
```

Ayuthia,

There was no files starting b43 before.

---

### Post by Jagsjim on 2009-11-02
> **Ayuthia said:**
> It looks like your firmware is there.

Can you post the results of:
```
dmesg|grep b43
lsmod|grep -e b4 -e ssb -e wl -e ndis
lshw -C network
```

here's the results:

jimmy@jimmy-laptop:~$ dmesg|grep b43
[   18.463619] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   18.463635] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.463647] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   19.209192] b43-phy0: Broadcom 4306 WLAN found
jimmy@jimmy-laptop:~$ lsmod|grep -e b4 -e ssb -e wl -e ndis
b43                   131484  0 
mac80211              217592  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ndiswrapper           193436  0 
b44                    35984  0 
ssb                    41220  2 b43,b44
mii                    13312  1 b44
jimmy@jimmy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:31:19:27
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.101 latency=32 multicast=yes
       resources: irq:7 memory:faffe000-faffffff
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:38000000-38001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:34:fd:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by grupy on 2009-11-02
Had a similar problem (missing ucode5.fw firmware files) on a DELL Latitude D520, with Karmic. 
A bit annoying that a fresh install has stupid wireless problems (8.10 worked smoothly), but after searching the web a bit, I came across this post:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
Which redirected to files from here:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

Followed it with no problems and it worked great for me.

---

### Post by Ayuthia on 2009-11-02
> **Jagsjim said:**
> here's the results:

jimmy@jimmy-laptop:~$ dmesg|grep b43
[   18.463619] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   18.463635] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.463647] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   19.209192] b43-phy0: Broadcom 4306 WLAN found
jimmy@jimmy-laptop:~$ lsmod|grep -e b4 -e ssb -e wl -e ndis
b43                   131484  0 
mac80211              217592  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ndiswrapper           193436  0 
b44                    35984  0 
ssb                    41220  2 b43,b44
mii                    13312  1 b44
jimmy@jimmy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:31:19:27
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.101 latency=32 multicast=yes
       resources: irq:7 memory:faffe000-faffffff
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:38000000-38001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:34:fd:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

What does 
```
sudo ifconfig wlan0 up
```
do?  It is supposed to start up the wireless.  It looks like yours is all set up.  It could also be that the wireless has not been enabled in Network Manager.

---

### Post by Jagsjim on 2009-11-02
> **Ayuthia said:**
> What does 
```
sudo ifconfig wlan0 up
```do?  It is supposed to start up the wireless.  It looks like yours is all set up.  It could also be that the wireless has not been enabled in Network Manager.

wlan0: ERROR while getting interface flags: No such device

I have wicd installed.

---

### Post by trainman536 on 2009-11-06
i am having the same problem on my Dell inspiron E1705 with wubi 64-bit the Brad-com's driver and firmware are there but it says under the wireless menu that the device is not ready

intel core 2 duo 
1gb RAM 
Bradcom advanced wirless

---

### Post by PePas on 2009-11-17
Serek's solution in post #11 worked for me on Dell 1501 with b43+44, so manually unload + reload, and then the Hardware Drivers will show the 2 drivers, choose STA. (My laptop froze after establishing the connection, but on reboot worked fine.)

---

