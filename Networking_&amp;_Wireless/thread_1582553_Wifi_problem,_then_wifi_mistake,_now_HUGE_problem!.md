---
title: "Wifi problem, then wifi mistake, now HUGE problem!"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by tancrackers on 2010-09-26
Hi, I've Ubuntu for a couple of months and am getting the hang of it. However, I have a large problem!
At college, my wifi switch is ON and it says that I am fully connected to the network. I can surf the web, but eventually the connection will hang and then I won't be able to use the internet at all, yet it says that there's a connection to the network. When I had Ubtuntu and Windows 7 dual booted, Windows had NO problem. I clean installed just Ubuntu over everything, still the problem persists. I tried to use "Windows Wireless Drivers" and no .inf files work so far -__-
I tried tinkering the wifi using the post [here by Cavalier,]("http://ubuntuforums.org/showthread.php?t=1525780") but now I actually don't have wifi now! There isn't a wireless option at all! I can only use an ethernet cord (never a problem connecting with a cord, so I thought that it was a problem with my wireless card).  When I check for proprietary drivers, I get nothing. I am running Ubuntu Lucid (10.04) (desktop edition) 64-bit on a Toshiba Satellite A505-5-S6960. My wireless card is Intel Wifi Link 5100.

So...

john@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
04:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)




john@john-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:d104 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:d8:1e:9f  
          inet addr:128.226.228.52  Bcast:128.226.228.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fed8:1e9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85288076 (85.2 MB)  TX bytes:6871220 (6.8 MB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10212 (10.2 KB)  TX bytes:10212 (10.2 KB)



john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

^WTF?



john@john-laptop:~$ iwconfig wlan0
wlan0     No such device

john@john-laptop:~$ 
^ !!!



john@john-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5171  0 
vboxnetflt             14998  0 
vboxdrv              1792440  2 vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279040  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_hda_intel          25677  4 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
softcursor              1565  1 bitblit
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
joydev                 11072  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
i915                  321654  3 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
drm_kms_helper         30742  1 i915
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   198948  4 i915,drm_kms_helper
uvcvideo               62467  0 
i2c_algo_bit            6024  1 i915
snd                    71187  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  20623  1 i915
soundcore               8052  1 snd
intel_agp              29095  2 i915
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
output                  2503  1 video
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
psmouse                64576  0 
v4l2_compat_ioctl32    11956  1 videodev
serio_raw               4918  0 
led_class               3764  1 sdhci
ndiswrapper           244800  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   37870  2 
r8169                  39650  0 
mii                     5237  1 r8169
john@john-laptop:~$ 

I couldn't get all of it, but I entered:
dmesg
And got:


abled.
[    0.514700] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.514861] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.515023] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.515173] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.515189] vgaarb: loaded
[    0.515314] SCSI subsystem initialized
[    0.515409] libata version 3.00 loaded.
[    0.515487] usbcore: registered new interface driver usbfs
[    0.515498] usbcore: registered new interface driver hub
[    0.515525] usbcore: registered new device driver usb
[    0.515660] ACPI: WMI: Mapper loaded
[    0.515662] PCI: Using ACPI for IRQ routing
[    0.515889] NetLabel: Initializing
[    0.515891] NetLabel:  domain hash size = 128
[    0.515892] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.515906] NetLabel:  unlabeled traffic allowed by default
[    0.515944] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.515949] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.520267] Switching to clocksource tsc
[    0.521801] AppArmor: AppArmor Filesystem Enabled
[    0.521820] pnp: PnP ACPI init
[    0.521838] ACPI: bus type pnp registered
[    0.525590] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.4 BAR 13 (0x1000-0x1fff), disabling
[    0.526502] pnp: PnP ACPI: found 8 devices
[    0.526504] ACPI: ACPI bus type pnp unregistered
[    0.526517] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.526520] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.526523] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.526526] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.526528] system 00:01: ioport range 0x500-0x57f has been reserved
[    0.526532] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.526535] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.526538] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.526541] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.526544] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.526547] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.526550] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.526553] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.526556] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[    0.531279] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.531339] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.531343] pci 0000:00:1c.0:   IO window: 0x4000-0x5fff
[    0.531349] pci 0000:00:1c.0:   MEM window: 0xd7800000-0xd87fffff
[    0.531353] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d14fffff
[    0.531361] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.531365] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.531371] pci 0000:00:1c.1:   MEM window: 0xd6700000-0xd77fffff
[    0.531376] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1500000-0x000000d24fffff
[    0.531384] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.531387] pci 0000:00:1c.3:   IO window: 0x2000-0x2fff
[    0.531393] pci 0000:00:1c.3:   MEM window: 0xd5600000-0xd66fffff
[    0.531397] pci 0000:00:1c.3:   PREFETCH window: 0x000000d2500000-0x000000d34fffff
[    0.531405] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.531409] pci 0000:00:1c.4:   IO window: 0x1000-0x1fff
[    0.531415] pci 0000:00:1c.4:   MEM window: 0xd4600000-0xd55fffff
[    0.531420] pci 0000:00:1c.4:   PREFETCH window: 0x000000d3500000-0x000000d44fffff
[    0.531427] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.531429] pci 0000:00:1e.0:   IO window: disabled
[    0.531434] pci 0000:00:1e.0:   MEM window: disabled
[    0.531438] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.531458]   alloc irq_desc for 17 on node -1
[    0.531460]   alloc kstat_irqs on node -1
[    0.531470] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.531476] pci 0000:00:1c.0: setting latency timer to 64
[    0.531486]   alloc irq_desc for 16 on node -1
[    0.531488]   alloc kstat_irqs on node -1
[    0.531491] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.531496] pci 0000:00:1c.1: setting latency timer to 64
[    0.531505]   alloc irq_desc for 19 on node -1
[    0.531507]   alloc kstat_irqs on node -1
[    0.531510] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.531514] pci 0000:00:1c.3: setting latency timer to 64
[    0.531525] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.531529] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.531535] pci 0000:00:1c.4: setting latency timer to 64
[    0.531543] pci 0000:00:1e.0: setting latency timer to 64
[    0.531547] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.531549] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.531552] pci_bus 0000:02: resource 0 io:  [0x4000-0x5fff]
[    0.531554] pci_bus 0000:02: resource 1 mem: [0xd7800000-0xd87fffff]
[    0.531557] pci_bus 0000:02: resource 2 pref mem [0xd0400000-0xd14fffff]
[    0.531559] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.531561] pci_bus 0000:03: resource 1 mem: [0xd6700000-0xd77fffff]
[    0.531564] pci_bus 0000:03: resource 2 pref mem [0xd1500000-0xd24fffff]
[    0.531566] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.531568] pci_bus 0000:04: resource 1 mem: [0xd5600000-0xd66fffff]
[    0.531571] pci_bus 0000:04: resource 2 pref mem [0xd2500000-0xd34fffff]
[    0.531573] pci_bus 0000:07: resource 0 io:  [0x1000-0x1fff]
[    0.531575] pci_bus 0000:07: resource 1 mem: [0xd4600000-0xd55fffff]
[    0.531578] pci_bus 0000:07: resource 2 pref mem [0xd3500000-0xd44fffff]
[    0.531580] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.531582] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.531619] NET: Registered protocol family 2
[    0.531792] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.533046] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.537953] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.538540] TCP: Hash tables configured (established 524288 bind 65536)
[    0.538542] TCP reno registered
[    0.538672] NET: Registered protocol family 1
[    0.538698] pci 0000:00:02.0: Boot video device
[    0.559678] Freeing initrd memory: 8244k freed
[    2.530009] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.530006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.530182] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    4.530184] Simple Boot Flag at 0x44 set to 0x1
[    4.530375] Scanning for low memory corruption every 60 seconds
[    4.530514] audit: initializing netlink socket (disabled)
[    4.530527] type=2000 audit(1285520811.530:1): initialized
[    4.540158] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.541520] VFS: Disk quotas dquot_6.5.2
[    4.541572] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.542133] fuse init (API version 7.13)
[    4.542210] msgmni has been set to 7665
[    4.542398] alg: No test for stdrng (krng)
[    4.542449] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.542452] io scheduler noop registered
[    4.542454] io scheduler anticipatory registered
[    4.542456] io scheduler deadline registered
[    4.542488] io scheduler cfq registered (default)
[    4.542655]   alloc irq_desc for 24 on node -1
[    4.542657]   alloc kstat_irqs on node -1
[    4.542669] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    4.542680] pcieport 0000:00:1c.0: setting latency timer to 64
[    4.542836]   alloc irq_desc for 25 on node -1
[    4.542838]   alloc kstat_irqs on node -1
[    4.542846] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    4.542857] pcieport 0000:00:1c.1: setting latency timer to 64
[    4.543008]   alloc irq_desc for 26 on node -1
[    4.543010]   alloc kstat_irqs on node -1
[    4.543018] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    4.543029] pcieport 0000:00:1c.3: setting latency timer to 64
[    4.543182]   alloc irq_desc for 27 on node -1
[    4.543184]   alloc kstat_irqs on node -1
[    4.543192] pcieport 0000:00:1c.4: irq 27 for MSI/MSI-X
[    4.543203] pcieport 0000:00:1c.4: setting latency timer to 64
[    4.543300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.543586] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.543741] ACPI: AC Adapter [ADP0] (on-line)
[    4.543842] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    4.543846] ACPI: Power Button [PWRB]
[    4.543887] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    4.545070] ACPI: Lid Switch [LID0]
[    4.545128] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.545131] ACPI: Power Button [PWRF]
[    4.545323] fan PNP0C0B:00: registered as cooling_device0
[    4.545329] ACPI: Fan [FAN] (on)
[    4.546509] ACPI: SSDT 00000000b7b77c98 00229 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    4.547136] ACPI: SSDT 00000000b7b75598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    4.547700] Monitor-Mwait will be used to enter C-1 state
[    4.547724] Monitor-Mwait will be used to enter C-2 state
[    4.547733] Marking TSC unstable due to TSC halts in idle
[    4.547757] Switching to clocksource hpet
[    4.547801] processor LNXCPU:00: registered as cooling_device1
[    4.548373] ACPI: SSDT 00000000b7b76e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    4.548912] ACPI: SSDT 00000000b7b77f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    4.549627] processor LNXCPU:01: registered as cooling_device2
[    4.555461] thermal LNXTHERM:01: registered as thermal_zone0
[    4.555468] ACPI: Thermal Zone [THRM] (45 C)
[    4.556775] ACPI: Battery Slot [BAT0] (battery present)
[    4.556929] Linux agpgart interface v0.103
[    4.556960] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.558174] brd: module loaded
[    4.558616] loop: module loaded
[    4.558700] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.559072] Fixed MDIO Bus: probed
[    4.559105] PPP generic driver version 2.4.2
[    4.559136] tun: Universal TUN/TAP device driver, 1.6
[    4.559138] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.559206] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.559230] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.559248] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.559252] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.559285] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.559320] ehci_hcd 0000:00:1a.7: debug port 1
[    4.563231] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.563248] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd8804c00
[    4.581267] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.581363] usb usb1: configuration #1 chosen from 1 choice
[    4.581389] hub 1-0:1.0: USB hub found
[    4.581397] hub 1-0:1.0: 4 ports detected
[    4.581454]   alloc irq_desc for 23 on node -1
[    4.581456]   alloc kstat_irqs on node -1
[    4.581462] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.581472] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.581476] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.581507] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.581536] ehci_hcd 0000:00:1d.7: debug port 1
[    4.585411] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.585423] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd8804800
[    4.600017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.600079] usb usb2: configuration #1 chosen from 1 choice
[    4.600103] hub 2-0:1.0: USB hub found
[    4.600109] hub 2-0:1.0: 8 ports detected
[    4.600173] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.600186] uhci_hcd: USB Universal Host Controller Interface driver
[    4.600206] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.600213] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.600216] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.600245] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.600281] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060e0
[    4.600367] usb usb3: configuration #1 chosen from 1 choice
[    4.600390] hub 3-0:1.0: USB hub found
[    4.600396] hub 3-0:1.0: 2 ports detected
[    4.600442]   alloc irq_desc for 21 on node -1
[    4.600444]   alloc kstat_irqs on node -1
[    4.600448] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.600454] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.600458] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.600486] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.600519] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000060c0
[    4.600601] usb usb4: configuration #1 chosen from 1 choice
[    4.600623] hub 4-0:1.0: USB hub found
[    4.600629] hub 4-0:1.0: 2 ports detected
[    4.600672] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.600678] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.600682] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.600719] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.600746] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000060a0
[    4.600829] usb usb5: configuration #1 chosen from 1 choice
[    4.600854] hub 5-0:1.0: USB hub found
[    4.600860] hub 5-0:1.0: 2 ports detected
[    4.600902] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.600908] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.600912] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.600939] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.600965] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006080
[    4.601045] usb usb6: configuration #1 chosen from 1 choice
[    4.601073] hub 6-0:1.0: USB hub found
[    4.601078] hub 6-0:1.0: 2 ports detected
[    4.601121] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.601127] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.601130] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.601157] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.601183] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00006060
[    4.601263] usb usb7: configuration #1 chosen from 1 choice
[    4.601285] hub 7-0:1.0: USB hub found
[    4.601291] hub 7-0:1.0: 2 ports detected
[    4.601336]   alloc irq_desc for 18 on node -1
[    4.601338]   alloc kstat_irqs on node -1
[    4.601343] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.601349] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.601352] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.601382] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.601414] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00006040
[    4.601502] usb usb8: configuration #1 chosen from 1 choice
[    4.601527] hub 8-0:1.0: USB hub found
[    4.601532] hub 8-0:1.0: 2 ports detected
[    4.601616] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.626711] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.626717] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.626825] mice: PS/2 mouse device common for all mice
[    4.627676] rtc_cmos 00:03: RTC can wake from S4
[    4.627711] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.627742] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.627853] device-mapper: uevent: version 1.0.3
[    4.627967] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    4.628040] device-mapper: multipath: version 1.1.0 loaded
[    4.628042] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.628256] cpuidle: using governor ladder
[    4.628336] cpuidle: using governor menu
[    4.628656] TCP cubic registered
[    4.628774] NET: Registered protocol family 10
[    4.629196] lo: Disabled Privacy Extensions
[    4.629458] NET: Registered protocol family 17
[    4.630111] PM: Resume from disk failed.
[    4.630124] registered taskstats version 1
[    4.630828]   Magic number: 10:839:138
[    4.630847] block ram3: hash matches
[    4.630945] rtc_cmos 00:03: setting system clock to 2010-09-26 17:06:52 UTC (1285520812)
[    4.630948] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.630949] EDD information not available.
[    4.631022] Freeing unused kernel memory: 880k freed
[    4.631321] Write protecting the kernel read-only data: 7696k
[    4.645858] udev: starting version 151
[    4.662976] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.712876] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.712925] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.713056] r8169 0000:02:00.0: setting latency timer to 64
[    4.713216]   alloc irq_desc for 28 on node -1
[    4.713219]   alloc kstat_irqs on node -1
[    4.713258] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    4.713861] eth0: RTL8102e at 0xffffc90000672000, 00:1e:33:d8:1e:9f, XID 04c00000 IRQ 28
[    4.737691] ahci 0000:00:1f.2: version 3.0
[    4.737718] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.737789]   alloc irq_desc for 29 on node -1
[    4.737791]   alloc kstat_irqs on node -1
[    4.737804] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    4.737916] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.737919] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    4.737925] ahci 0000:00:1f.2: setting latency timer to 64
[    4.759108] scsi0 : ahci
[    4.776623] scsi1 : ahci
[    4.782841] scsi2 : ahci
[    4.782982] scsi3 : ahci
[    4.783081] scsi4 : ahci
[    4.783172] scsi5 : ahci
[    4.783538] ata1: SATA max UDMA/133 abar m2048@0xd8804000 port 0xd8804100 irq 29
[    4.783543] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 29
[    4.783545] ata3: DUMMY
[    4.783546] ata4: DUMMY
[    4.783549] ata5: SATA max UDMA/133 abar m2048@0xd8804000 port 0xd8804300 irq 29
[    4.783553] ata6: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 29
[    4.900087] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    5.130063] ata1: SATA link down (SStatus 0 SControl 300)
[    5.130107] ata5: SATA link down (SStatus 0 SControl 300)
[    5.265082] usb 1-2: configuration #1 chosen from 1 choice
[    5.710065] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.710092] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.711582] ata6.00: ATAPI: MATSHITADVD-RAM UJ880ES, 1.80, max UDMA/33
[    5.713910] ata6.00: configured for UDMA/33
[    5.749827] ata2.00: ATA-8: TOSHIBA MK3255GSX, FG011M, max UDMA/100
[    5.749832] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.750767] ata2.00: configured for UDMA/100
[    5.750928] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK3255GS FG01 PQ: 0 ANSI: 5
[    5.751094] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    5.751114] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    5.751203] sd 1:0:0:0: [sda] Write Protect is off
[    5.751205] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.751229] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.751365]  sda:
[    5.753777] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ880ES  1.80 PQ: 0 ANSI: 5
[    5.759205] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.759207] Uniform CD-ROM driver Revision: 3.20
[    5.759295] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.759345] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    5.803882]  sda1 sda2 < sda5 >
[    5.831933] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.248522] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    8.740478] Adding 11498488k swap on /dev/sda5.  Priority:-1 extents:1 across:11498488k 
[    9.338940] udev: starting version 151
[   10.231288] type=1505 audit(1285520818.099:2):  operation="profile_load" pid=559 name="/sbin/dhclient3"
[   10.231924] type=1505 audit(1285520818.099:3):  operation="profile_load" pid=559 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.232264] type=1505 audit(1285520818.099:4):  operation="profile_load" pid=559 name="/usr/lib/connman/scripts/dhclient-script"
[   10.341082] Disabling lock debugging due to kernel taint
[   10.347516] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.901518] lp: driver loaded but no devices found
[   10.977300] usbcore: registered new interface driver ndiswrapper
[   11.409693] Linux video capture interface: v2.00
[   11.411052] sdhci: Secure Digital Host Controller Interface driver
[   11.411054] sdhci: Copyright(c) Pierre Ossman
[   11.432305] sdhci-pci 0000:04:00.0: SDHCI controller found [1180:e822] (rev 1)
[   11.432332] sdhci-pci 0000:04:00.0: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[   11.432391] sdhci-pci 0000:04:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   11.432399] sdhci-pci 0000:04:00.0: setting latency timer to 64
[   11.432466] Registered led device: mmc0::
[   11.432525] mmc0: SDHCI controller on PCI [0000:04:00.0] using DMA
[   11.447534] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   11.448206] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[   11.475059] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.516941] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:d104)
[   11.520849] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input5
[   11.520927] usbcore: registered new interface driver uvcvideo
[   11.520957] USB Video Class driver (v0.1.0)
[   11.702467] [drm] Initialized drm 1.1.0 20060810
[   12.110673] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.110679] i915 0000:00:02.0: setting latency timer to 64
[   12.127044]   alloc irq_desc for 30 on node -1
[   12.127047]   alloc kstat_irqs on node -1
[   12.127057] i915 0000:00:02.0: irq 30 for MSI/MSI-X
[   12.127065] [drm] set up 127M of stolen space
[   12.239945] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1e0b1, caps: 0xd04731/0xa40000
[   12.302386] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   12.724317] fb0: inteldrmfb frame buffer device
[   12.724320] registered panic notifier
[   12.735050] acpi device:03: registered as cooling_device3
[   12.735886] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   12.735970] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   12.736051] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.142228] vga16fb: initializing
[   13.142232] vga16fb: mapped to 0xffff8800000a0000
[   13.142236] vga16fb: not registering due to another framebuffer present
[   13.512384]   alloc irq_desc for 22 on node -1
[   13.512387]   alloc kstat_irqs on node -1
[   13.512394] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.512470] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.803040] Console: switching to colour frame buffer device 170x48
[   14.002459] hda_codec: ALC272: BIOS auto-probing.
[   14.003785] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   14.985588] type=1505 audit(1285520822.849:5):  operation="profile_load" pid=894 name="/usr/share/gdm/guest-session/Xsession"
[   14.987810] type=1505 audit(1285520822.849:6):  operation="profile_replace" pid=899 name="/sbin/dhclient3"
[   14.988454] type=1505 audit(1285520822.849:7):  operation="profile_replace" pid=899 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.988800] type=1505 audit(1285520822.849:8):  operation="profile_replace" pid=899 name="/usr/lib/connman/scripts/dhclient-script"
[   15.485697] type=1505 audit(1285520823.349:9):  operation="profile_load" pid=900 name="/usr/bin/evince"
[   15.493894] type=1505 audit(1285520823.359:10):  operation="profile_load" pid=900 name="/usr/bin/evince-previewer"
[   15.498904] type=1505 audit(1285520823.359:11):  operation="profile_load" pid=900 name="/usr/bin/evince-thumbnailer"
[   15.700902] type=1505 audit(1285520823.569:12):  operation="profile_load" pid=905 name="/usr/lib/cups/backend/cups-pdf"
[   15.701680] type=1505 audit(1285520823.569:13):  operation="profile_load" pid=905 name="/usr/sbin/cupsd"
[   15.796811] type=1505 audit(1285520823.659:14):  operation="profile_load" pid=906 name="/usr/sbin/tcpdump"
[   16.866905] r8169: eth0: link up
[   16.866932] r8169: eth0: link up
[   17.233469] type=1503 audit(1285520825.102:15):  operation="open" pid=933 parent=917 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[   17.651702] type=1503 audit(1285520825.519:16):  operation="open" pid=1000 parent=933 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[   20.166417] type=1503 audit(1285520828.029:17):  operation="open" pid=1071 parent=933 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[   24.838988] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.838992] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   24.838993] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   24.838994] vboxdrv: the usage of hardware performance counters by
[   24.838995] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   24.838999] vboxdrv: Found 2 processor cores.
[   24.839417] VBoxDrv: dbg - g_abExecMemory=ffffffffa02adca0
[   24.839438] vboxdrv: fAsync=0 offMin=0x1e3 offMax=0x111b
[   24.840376] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.840379] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   26.540891] ppdev: user-space parallel port driver
[   26.576874] type=1503 audit(1285520834.439:18):  operation="open" pid=1239 parent=1220 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[   26.617986] type=1503 audit(1285520834.479:19):  operation="open" pid=1240 parent=1239 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[   27.540023] eth0: no IPv6 routers present
[   30.011294] CPU0 attaching NULL sched-domain.
[   30.011300] CPU1 attaching NULL sched-domain.
[   30.070070] CPU0 attaching sched-domain:
[   30.070074]  domain 0: span 0-1 level MC
[   30.070076]   groups: 0 1
[   30.070081] CPU1 attaching sched-domain:
[   30.070083]  domain 0: span 0-1 level MC
[   30.070085]   groups: 1 0
[   61.722087] lo: Disabled Privacy Extensions
[ 8485.704956] r8169: eth0: link down
[ 8496.434323] r8169: eth0: link up
[ 8496.448908] type=1503 audit(1285529304.309:20):  operation="open" pid=2441 parent=917 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[ 8496.453063] type=1503 audit(1285529304.319:21):  operation="open" pid=2442 parent=2441 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[ 8498.161934] type=1503 audit(1285529306.029:22):  operation="open" pid=2443 parent=2441 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
[ 9732.886184] lo: Disabled Privacy Extensions
john@john-laptop:~$ 



john@john-laptop:~$ sudo lshw -C network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:d8:1e:9f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=128.226.228.52 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6700000-d6701fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
john@john-laptop:~$ 



john@john-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

john@john-laptop:~$ 


john@john-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
john@john-laptop:~$ iwlist --help
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
john@john-laptop:~$ 



john@john-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS
john@john-laptop:~$ 



john@john-laptop:~$ uname -mr
2.6.32-24-generic x86_64
john@john-laptop:~$ 



john@john-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for john: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
john@john-laptop:~$

---

### Post by walt.smith1960 on 2010-09-26
Something simple--if you right click on Network Manager, are both Enable Networking and Enable Wireless checked?  This got me a couple days ago.  A machine disabled networking seemingly on its own.

---

### Post by tancrackers on 2010-09-27
Yes they're both enabled.
I reinstalled my OS, so I have wireless again. However, I'm back to the start where my connection drops at college all the time (not with ethernet though). I tested openSUSE and Fedora 11.2 and 13 respectively; they had the same problem.

---

