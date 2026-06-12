---
title: "ubuntu driver install toshiba RTL8188CE adapter"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by jgilk1 on 2011-03-02
ok im a new user to linux distro but not to computers im @ a loss for process and codes i have picked up a few linux distro manuals but still cant get this to work

my problem as everything else on my netbook has installed but network drivers i cant access the internet vis linux 10.10 netbook either through a direct connection to the modem or router

router is lynksys 500???
and modem is qwest????

am getting no access what so ever

on the other side of the partition i am running windows 7 starter and have no issue connection to the internet via wireless (full signal strength) or direct connect from the modem


toshiba nb505

command line: $lspci

> 
jim@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)




command line: lsusb
> 
jim@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

command line: lspci -nn | grep 'Wireless Brand'

gives no info prompts for new command but does not rehect the code

jim@ubuntu:~$ lspci -nn | grep 'Wireless Brand'
jim@ubuntu:~$


command code:$ ifconfig
> 
jim@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 1c:75:08:75:d1:b0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:43 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:72 errors:0 dropped:0 overruns:0 frame:0
TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5600 (5.6 KB) TX bytes:5600 (5.6 KB)

command line:iwconfig
> 
jim@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 1c:75:08:75:d1:b0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:43 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:72 errors:0 dropped:0 overruns:0 frame:0
TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5600 (5.6 KB) TX bytes:5600 (5.6 KB)


command line: $lsmod
> 
jim@ubuntu:~$ lsmod
Module Size Used by
nls_iso8859_1 3261 1
nls_cp437 4931 1
vfat 9201 1
fat 48240 1 vfat
binfmt_misc 6599 1
parport_pc 26058 0
ppdev 5556 0
snd_hda_codec_realtek 217980 1
joydev 8735 0
snd_hda_intel 22107 2
snd_hda_codec 87552 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5040 1 snd_hda_codec
snd_pcm 71475 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 4588 0
i915 290938 4
snd_rawmidi 17783 1 snd_seq_midi
drm_kms_helper 30200 1 i915
snd_seq_midi_event 6047 1 snd_seq_midi
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event
drm 168054 5 i915,drm_kms_helper
snd_timer 19067 2 snd_pcm,snd_seq
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo 55847 0
intel_agp 26360 2 i915
snd 49006 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev 43098 1 uvcvideo
psmouse 59033 0
v4l1_compat 13359 2 uvcvideo,videodev
soundcore 880 1 snd
i2c_algo_bit 5168 1 i915
serio_raw 4022 0
agpgart 32011 2 drm,intel_agp
snd_page_alloc 7120 2 snd_hda_intel,snd_pcm
video 18712 1 i915
output 1883 1 video
lp 7342 0
parport 31492 3 parport_pc,ppdev,lp
usb_storage 40172 1
ahci 19013 0
libahci 21667 2 ahci
r8169 36489 0
mii 4425 1 r8169


command line: $dmesg (i think i got this whole code if not just let me know)
> 
[ 0.272878] pci 0000:00:1c.2: bridge window [io 0x3000-0x3fff]
[ 0.272889] pci 0000:00:1c.2: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.272904] pci 0000:00:1c.2: bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[ 0.273003] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[ 0.273014] pci 0000:00:1e.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.273025] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.273040] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.273050] pci 0000:00:1e.0: bridge window [io 0x0000-0x0cf7] (subtractive decode)
[ 0.273059] pci 0000:00:1e.0: bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[ 0.273068] pci 0000:00:1e.0: bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[ 0.273077] pci 0000:00:1e.0: bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[ 0.273087] pci 0000:00:1e.0: bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[ 0.273096] pci 0000:00:1e.0: bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[ 0.273105] pci 0000:00:1e.0: bridge window [mem 0x40000000-0xf7ffffff] (subtractive decode)
[ 0.273115] pci 0000:00:1e.0: bridge window [io 0x0d00-0xfdff] (subtractive decode)
[ 0.273151] pci_bus 0000:00: on NUMA node 0
[ 0.273172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.273497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[ 0.273697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[ 0.273893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[ 0.274097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 0.274636] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.274656] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.295048] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[ 0.295331] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[ 0.295617] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.295909] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.296231] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.296524] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.296829] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.297118] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[ 0.297275] HEST: Table is not found!
[ 0.297504] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.297534] vgaarb: loaded
[ 0.297975] SCSI subsystem initialized
[ 0.298200] libata version 3.00 loaded.
[ 0.298353] usbcore: registered new interface driver usbfs
[ 0.298398] usbcore: registered new interface driver hub
[ 0.298469] usbcore: registered new device driver usb
[ 0.298860] ACPI: WMI: Mapper loaded
[ 0.298867] PCI: Using ACPI for IRQ routing
[ 0.298876] PCI: pci_cache_line_size set to 64 bytes
[ 0.298942] pci 0000:00:1d.7: address space collision: [mem 0xf0504000-0xf05043ff] conflicts with PCI Bus 0000:09 [mem 0xf0500000-0xf05fffff 64bit pref]
[ 0.298969] pci 0000:00:1f.2: address space collision: [mem 0xf0504400-0xf05047ff] conflicts with PCI Bus 0000:09 [mem 0xf0500000-0xf05fffff 64bit pref]
[ 0.299053] reserve RAM buffer: 0000000000002000 - 000000000000ffff
[ 0.299061] reserve RAM buffer: 000000000009dc00 - 000000000009ffff
[ 0.299069] reserve RAM buffer: 000000003f5d0000 - 000000003fffffff
[ 0.299338] NetLabel: Initializing
[ 0.299345] NetLabel: domain hash size = 128
[ 0.299350] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.299381] NetLabel: unlabeled traffic allowed by default
[ 0.299485] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.299499] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.299515] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.304348] Switching to clocksource tsc
[ 0.538081] AppArmor: AppArmor Filesystem Enabled
[ 0.538117] pnp: PnP ACPI init
[ 0.538160] ACPI: bus type pnp registered
[ 0.564248] pnp: PnP ACPI: found 8 devices
[ 0.564256] ACPI: ACPI bus type pnp unregistered
[ 0.564265] PnPBIOS: Disabled by ACPI PNP
[ 0.564304] system 00:01: [io 0x0800-0x080f] has been reserved
[ 0.564314] system 00:01: [io 0x1000-0x107f] has been reserved
[ 0.564323] system 00:01: [io 0x1180-0x11bf] has been reserved
[ 0.564333] system 00:01: [io 0x04d0-0x04d1] has been reserved
[ 0.564342] system 00:01: [io 0xfe00] has been reserved
[ 0.564351] system 00:01: [io 0x164e-0x174c] has been reserved
[ 0.564362] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.564372] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[ 0.564382] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[ 0.564392] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[ 0.604042] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[ 0.604057] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[ 0.604070] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[ 0.604081] pci 0000:00:1c.2: BAR 14: assigned [mem 0x40600000-0x409fffff]
[ 0.604093] pci 0000:00:1c.0: BAR 13: assigned [io 0x4000-0x4fff]
[ 0.604103] pci 0000:00:1d.7: BAR 0: assigned [mem 0x40a00000-0x40a003ff]
[ 0.604118] pci 0000:00:1d.7: BAR 0: set to [mem 0x40a00000-0x40a003ff] (PCI address [0x40a00000-0x40a003ff]
[ 0.604130] pci 0000:00:1f.2: BAR 5: assigned [mem 0x40a00400-0x40a007ff]
[ 0.604144] pci 0000:00:1f.2: BAR 5: set to [mem 0x40a00400-0x40a007ff] (PCI address [0x40a00400-0x40a007ff]
[ 0.604154] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[ 0.604163] pci 0000:00:1c.0: bridge window [io 0x4000-0x4fff]
[ 0.604175] pci 0000:00:1c.0: bridge window [mem 0x40000000-0x401fffff]
[ 0.604187] pci 0000:00:1c.0: bridge window [mem 0x40200000-0x403fffff 64bit pref]
[ 0.604201] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[ 0.604210] pci 0000:00:1c.1: bridge window [io 0x2000-0x2fff]
[ 0.604222] pci 0000:00:1c.1: bridge window [mem 0xf0100000-0xf01fffff]
[ 0.604234] pci 0000:00:1c.1: bridge window [mem 0x40400000-0x405fffff 64bit pref]
[ 0.604248] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[ 0.604256] pci 0000:00:1c.2: bridge window [io 0x3000-0x3fff]
[ 0.604269] pci 0000:00:1c.2: bridge window [mem 0x40600000-0x409fffff]
[ 0.604280] pci 0000:00:1c.2: bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[ 0.604294] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[ 0.604300] pci 0000:00:1e.0: bridge window [io disabled]
[ 0.604310] pci 0000:00:1e.0: bridge window [mem disabled]
[ 0.604319] pci 0000:00:1e.0: bridge window [mem pref disabled]
[ 0.604346] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[ 0.604361] alloc irq_desc for 16 on node -1
[ 0.604368] alloc kstat_irqs on node -1
[ 0.604385] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.604398] pci 0000:00:1c.0: setting latency timer to 64
[ 0.604417] alloc irq_desc for 17 on node -1
[ 0.604423] alloc kstat_irqs on node -1
[ 0.604435] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 0.604446] pci 0000:00:1c.1: setting latency timer to 64
[ 0.604464] alloc irq_desc for 18 on node -1
[ 0.604470] alloc kstat_irqs on node -1
[ 0.604482] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 0.604492] pci 0000:00:1c.2: setting latency timer to 64
[ 0.604507] pci 0000:00:1e.0: setting latency timer to 64
[ 0.604518] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7]
[ 0.604526] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[ 0.604535] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[ 0.604543] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[ 0.604551] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[ 0.604559] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[ 0.604568] pci_bus 0000:00: resource 10 [mem 0x40000000-0xf7ffffff]
[ 0.604576] pci_bus 0000:00: resource 11 [io 0x0d00-0xfdff]
[ 0.604584] pci_bus 0000:05: resource 0 [io 0x4000-0x4fff]
[ 0.604592] pci_bus 0000:05: resource 1 [mem 0x40000000-0x401fffff]
[ 0.604601] pci_bus 0000:05: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[ 0.604610] pci_bus 0000:07: resource 0 [io 0x2000-0x2fff]
[ 0.604618] pci_bus 0000:07: resource 1 [mem 0xf0100000-0xf01fffff]
[ 0.604627] pci_bus 0000:07: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[ 0.604636] pci_bus 0000:09: resource 0 [io 0x3000-0x3fff]
[ 0.604645] pci_bus 0000:09: resource 1 [mem 0x40600000-0x409fffff]
[ 0.604653] pci_bus 0000:09: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[ 0.604662] pci_bus 0000:11: resource 4 [io 0x0000-0x0cf7]
[ 0.604671] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[ 0.604680] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[ 0.604689] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[ 0.604697] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[ 0.604705] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[ 0.604714] pci_bus 0000:11: resource 10 [mem 0x40000000-0xf7ffffff]
[ 0.604722] pci_bus 0000:11: resource 11 [io 0x0d00-0xfdff]
[ 0.604825] NET: Registered protocol family 2
[ 0.604998] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.605618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.606681] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.607304] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.607317] TCP reno registered
[ 0.607330] UDP hash table entries: 512 (order: 2, 16384 bytes)
[ 0.607356] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[ 0.607602] NET: Registered protocol family 1
[ 0.607647] pci 0000:00:02.0: Boot video device
[ 0.607827] PCI: CLS 32 bytes, default 64
[ 0.607881] Simple Boot Flag at 0x35 set to 0x1
[ 0.608342] cpufreq-nforce2: No nForce2 chipset.
[ 0.608422] Scanning for low memory corruption every 60 seconds
[ 0.608805] audit: initializing netlink socket (disabled)
[ 0.608831] type=2000 audit(1299070904.604:1): initialized
[ 0.631842] highmem bounce pool size: 64 pages
[ 0.631861] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.636737] VFS: Disk quotas dquot_6.5.2
[ 0.636928] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.638906] fuse init (API version 7.14)
[ 0.639225] msgmni has been set to 1709
[ 0.646392] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.646403] io scheduler noop registered
[ 0.646409] io scheduler deadline registered
[ 0.646463] io scheduler cfq registered (default)
[ 0.646765] pcieport 0000:00:1c.0: setting latency timer to 64
[ 0.646823] alloc irq_desc for 40 on node -1
[ 0.646830] alloc kstat_irqs on node -1
[ 0.646850] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[ 0.647056] pcieport 0000:00:1c.1: setting latency timer to 64
[ 0.647115] alloc irq_desc for 41 on node -1
[ 0.647122] alloc kstat_irqs on node -1
[ 0.647140] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[ 0.647352] pcieport 0000:00:1c.2: setting latency timer to 64
[ 0.647405] alloc irq_desc for 42 on node -1
[ 0.647411] alloc kstat_irqs on node -1
[ 0.647428] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[ 0.647693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.647978] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.647998] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.648351] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.648370] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.648711] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.648730] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.649110] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.649129] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.649455] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.649474] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.649823] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[ 0.649842] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f2a0), AE_ALREADY_EXISTS
[ 0.649961] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.650231] intel_idle: MWAIT substates: 0x20220
[ 0.650238] intel_idle: v0.4 model 0x1C
[ 0.650243] intel_idle: lapic_timer_reliable_states 0x6
[ 0.650259] Marking TSC unstable due to TSC halts in idle states deeper than C2
[ 0.650448] Switching to clocksource hpet
[ 0.650985] ACPI: AC Adapter [ACAD] (on-line)
[ 0.651235] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/PNP0C0D:00/input/input0
[ 0.651341] ACPI: Lid Switch [LID0]
[ 0.651509] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0C:00/input/input1
[ 0.651523] ACPI: Power Button [PWRB]
[ 0.651665] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[ 0.651678] ACPI: Power Button [PWRF]
[ 0.652320] ACPI: acpi_idle yielding to intel_idle
[ 0.684332] ERST: Table is not found!
[ 0.684742] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.689052] brd: module loaded
[ 0.690828] loop: module loaded
[ 0.692362] Fixed MDIO Bus: probed
[ 0.692471] PPP generic driver version 2.4.2
[ 0.692617] tun: Universal TUN/TAP device driver, 1.6
[ 0.692624] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 0.692850] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.692908] alloc irq_desc for 23 on node -1
[ 0.692915] alloc kstat_irqs on node -1
[ 0.692932] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 0.692971] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 0.692980] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 0.693388] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 0.693491] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[ 0.693514] ehci_hcd 0000:00:1d.7: debug port 1
[ 0.697416] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 0.697470] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x40a00000
[ 0.701452] isapnp: Scanning for PnP cards...
[ 0.788520] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 0.788902] hub 1-0:1.0: USB hub found
[ 0.788917] hub 1-0:1.0: 8 ports detected
[ 0.789158] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.789207] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.789296] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 0.789315] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 0.789325] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 0.789479] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 0.789530] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[ 0.789898] hub 2-0:1.0: USB hub found
[ 0.789916] hub 2-0:1.0: 2 ports detected
[ 0.790072] alloc irq_desc for 19 on node -1
[ 0.790079] alloc kstat_irqs on node -1
[ 0.790095] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 0.790111] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 0.790120] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 0.790233] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 0.790300] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[ 0.790666] hub 3-0:1.0: USB hub found
[ 0.790680] hub 3-0:1.0: 2 ports detected
[ 0.790842] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 0.790859] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 0.790869] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 0.790980] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 0.791044] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[ 0.791420] hub 4-0:1.0: USB hub found
[ 0.791434] hub 4-0:1.0: 2 ports detected
[ 0.791587] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 0.791603] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 0.791612] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 0.791729] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 0.791796] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[ 0.792156] hub 5-0:1.0: USB hub found
[ 0.792170] hub 5-0:1.0: 2 ports detected
[ 0.792480] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13S2M] at 0x60,0x64 irq 1,12
[ 0.813161] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.813196] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.854351] mice: PS/2 mouse device common for all mice
[ 0.854748] rtc_cmos 00:04: RTC can wake from S4
[ 0.854866] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[ 0.854916] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[ 0.855306] device-mapper: uevent: version 1.0.3
[ 0.875092] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 0.888900] ACPI: Battery Slot [BAT1] (battery present)
[ 0.896696] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[ 0.924668] device-mapper: multipath: version 1.1.1 loaded
[ 0.924678] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.932774] EISA: Probing bus 0 at eisa.0
[ 0.932784] EISA: Cannot allocate resource for mainboard
[ 0.932791] Cannot allocate resource for EISA slot 1
[ 0.932797] Cannot allocate resource for EISA slot 2
[ 0.932803] Cannot allocate resource for EISA slot 3
[ 0.932809] Cannot allocate resource for EISA slot 4
[ 0.932814] Cannot allocate resource for EISA slot 5
[ 0.932820] Cannot allocate resource for EISA slot 6
[ 0.932826] Cannot allocate resource for EISA slot 7
[ 0.932832] Cannot allocate resource for EISA slot 8
[ 0.932837] EISA: Detected 0 cards.
[ 0.979116] cpuidle: using governor ladder
[ 0.979389] cpuidle: using governor menu
[ 0.980250] TCP cubic registered
[ 0.980652] NET: Registered protocol family 10
[ 0.981619] lo: Disabled Privacy Extensions
[ 0.982245] NET: Registered protocol family 17
[ 0.983461] Using IPI No-Shortcut mode
[ 0.983716] PM: Resume from disk failed.
[ 0.983744] registered taskstats version 1
[ 0.984322] Magic number: 3:469:27
[ 0.984446] rtc_cmos 00:04: setting system clock to 2011-03-02 13:01:45 UTC (1299070905)
[ 0.984455] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.984461] EDD information not available.
[ 1.010467] Freeing initrd memory: 10512k freed
[ 1.060492] isapnp: No Plug & Play device found
[ 1.060535] Freeing unused kernel memory: 684k freed
[ 1.061171] Write protecting the kernel text: 4932k
[ 1.061246] Write protecting the kernel read-only data: 1976k
[ 1.098871] udev[77]: starting version 163
[ 1.128117] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 1.375821] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.375868] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.375934] r8169 0000:09:00.0: setting latency timer to 64
[ 1.375947] r8169 0000:09:00.0: (unregistered net_device): unknown MAC, using family default
[ 1.389083] usb 1-8: new high speed USB device using ehci_hcd and address 3
[ 1.415940] alloc irq_desc for 43 on node -1
[ 1.415949] alloc kstat_irqs on node -1
[ 1.415980] r8169 0000:09:00.0: irq 43 for MSI/MSI-X
[ 1.417564] r8169 0000:09:00.0: eth0: RTL8101e at 0xf808e000, 1c:75:08:75:d1:b0, XID 00900000 IRQ 43
[ 1.460218] ahci 0000:00:1f.2: version 3.0
[ 1.460254] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1.460334] alloc irq_desc for 44 on node -1
[ 1.460342] alloc kstat_irqs on node -1
[ 1.460363] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[ 1.460487] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[ 1.460500] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[ 1.460512] ahci 0000:00:1f.2: setting latency timer to 64
[ 1.461068] scsi0 : ahci
[ 1.461490] scsi1 : ahci
[ 1.461767] scsi2 : ahci
[ 1.462020] scsi3 : ahci
[ 1.462494] ata1: SATA max UDMA/133 abar m1024@0x40a00400 port 0x40a00500 irq 44
[ 1.462507] ata2: SATA max UDMA/133 abar m1024@0x40a00400 port 0x40a00580 irq 44
[ 1.462517] ata3: SATA max UDMA/133 abar m1024@0x40a00400 port 0x40a00600 irq 44
[ 1.462527] ata4: SATA max UDMA/133 abar m1024@0x40a00400 port 0x40a00680 irq 44
[ 1.501606] Initializing USB Mass Storage driver...
[ 1.501914] scsi4 : usb-storage 1-4:1.0
[ 1.502174] usbcore: registered new interface driver usb-storage
[ 1.502182] USB Mass Storage support registered.
[ 1.780083] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.780131] ata4: SATA link down (SStatus 0 SControl 300)
[ 1.780158] ata2: SATA link down (SStatus 0 SControl 300)
[ 1.780182] ata3: SATA link down (SStatus 0 SControl 300)
[ 1.781167] ata1.00: ATA-8: Hitachi HTS545025B9A300, PB2OC64G, max UDMA/133
[ 1.781179] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[ 1.782544] ata1.00: configured for UDMA/133
[ 1.796348] scsi 0:0:0:0: Direct-Access ATA Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[ 1.796811] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.797163] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 1.797318] sd 0:0:0:0: [sda] Write Protect is off
[ 1.797325] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.797391] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.797778] sda: sda1 sda2 sda3
[ 1.823983] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.503258] scsi 4:0:0:0: Direct-Access Generic- Multi-Card 1.00 PQ: 0 ANSI: 0 CCS
[ 2.504794] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 2.659777] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[ 3.197963] sd 4:0:0:0: [sdb] 1950720 512-byte logical blocks: (998 MB/952 MiB)
[ 3.198815] sd 4:0:0:0: [sdb] Write Protect is off
[ 3.198822] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3.198828] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3.201312] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3.201323] sdb: sdb1
[ 3.204190] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3.204200] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 11.294992] udev[345]: starting version 163
[ 11.645055] lp: driver loaded but no devices found
[ 12.135916] Linux video capture interface: v2.00
[ 12.159218] Linux agpgart interface v0.103
[ 12.237894] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[ 12.238851] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[ 12.262753] uvcvideo: Found UVC 1.00 device CNF9055 (04f2:b1d6)
[ 12.280635] input: CNF9055 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input4
[ 12.281837] usbcore: registered new interface driver uvcvideo
[ 12.281846] USB Video Class driver (v0.1.0)
[ 12.322974] type=1400 audit(1299099716.835:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=584 comm="apparmor_parser"
[ 12.324293] type=1400 audit(1299099716.835:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=584 comm="apparmor_parser"
[ 12.331916] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[ 12.333996] type=1400 audit(1299099716.847:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=584 comm="apparmor_parser"
[ 12.654280] [drm] Initialized drm 1.1.0 20060810
[ 12.754740] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 12.754754] i915 0000:00:02.0: setting latency timer to 64
[ 12.839191] alloc irq_desc for 45 on node -1
[ 12.839200] alloc kstat_irqs on node -1
[ 12.839217] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[ 12.839239] [drm] set up 7M of stolen space
[ 12.941777] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+memwns=io+mem
[ 12.942248] [drm] initialized overlay support
[ 13.257038] Skipping EDID probe due to cached edid
[ 13.411701] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
[ 13.490645] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[ 13.724782] Console: switching to colour frame buffer device 128x37
[ 13.733426] fb0: inteldrmfb frame buffer device
[ 13.733432] drm: registered panic notifier
[ 13.733456] Slow work thread pool: Starting up
[ 13.733607] Slow work thread pool: Ready
[ 13.733674] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[ 13.734102] alloc irq_desc for 22 on node -1
[ 13.734111] alloc kstat_irqs on node -1
[ 13.734130] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 13.734211] alloc irq_desc for 46 on node -1
[ 13.734219] alloc kstat_irqs on node -1
[ 13.734241] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[ 13.734303] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 13.808362] hda_codec: ALC259: BIOS auto-probing.
[ 13.808733] hda_codec: connection list not available for 0x24
[ 13.848107] Skipping EDID probe due to cached edid
[ 16.334359] Adding 261116k swap on /host/ubuntu/disks/swap.disk. Priority:-1 extents:1 across:261116k
[ 16.381279] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[ 16.665453] ppdev: user-space parallel port driver
[ 16.748051] type=1400 audit(1299099721.259:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=823 comm="apparmor_parser"
[ 16.748857] type=1400 audit(1299099721.259:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[ 16.767555] type=1400 audit(1299099721.275:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
[ 16.769017] type=1400 audit(1299099721.279:: apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=824 comm="apparmor_parser"
[ 16.795223] type=1400 audit(1299099721.303:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=824 comm="apparmor_parser"
[ 16.807788] type=1400 audit(1299099721.315:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=829 comm="apparmor_parser"
[ 16.808943] type=1400 audit(1299099721.319:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=829 comm="apparmor_parser"
[ 16.855708] r8169 0000:09:00.0: eth0: link down
[ 16.856355] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 17.185324] Skipping EDID probe due to cached edid
[ 17.217275] Skipping EDID probe due to cached edid
[ 17.605189] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[ 18.248118] Skipping EDID probe due to cached edid
[ 18.284110] Skipping EDID probe due to cached edid
[ 18.320107] Skipping EDID probe due to cached edid
[ 18.352107] Skipping EDID probe due to cached edid
[ 19.647580] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[ 33.169130] Skipping EDID probe due to cached edid
[ 33.209127] Skipping EDID probe due to cached edid
[ 33.245153] Skipping EDID probe due to cached edid
[ 33.280121] Skipping EDID probe due to cached edid
[ 40.008123] Skipping EDID probe due to cached edid


command line: sudo lshw -C network
> 
jim@ubuntu:~$ sudo lshw -C network
[sudo] password line
PCI (sysfs)
*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:07:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:2000(size=256) memory:f0100000-f0103fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 05
serial: 1c:75:08:75:d1:b0
size: 10MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff



command line: iwlist scan
> 
jim@ubuntu:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.


command line: lsb_release -d
> 
jim@ubuntu:~$ lsb_release -d
Description: Ubuntu 10.10

command line: uname -mr
> 
jim@ubuntu:~$ uname -mr
2.6.35-22-generic i686

> 
jim@ubuntu:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...



i have tried to install the drivers for this card from manucactures site and code prompting i used to try and install the drivers
> 
jim@ubuntu:~$ cd Desktop/ieee80211
jim@ubuntu:~/Desktop/ieee80211$ make
make -C /lib/modules/2.6.35-22-generic/build M=/home/jim/Desktop/ieee80211 CC=gcc modules
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
CC [M] /home/jim/Desktop/ieee80211/ieee80211_softmac.o
/bin/sh: gcc: not found
make[2]: *** [/home/jim/Desktop/ieee80211/ieee80211_softmac.o] Error 127
make[1]: *** [_module_/home/jim/Desktop/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2
jim@ubuntu:~/Desktop/ieee80211$ make install
make -C /lib/modules/2.6.35-22-generic/build M=/home/jim/Desktop/ieee80211 CC=gcc modules
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
CC [M] /home/jim/Desktop/ieee80211/ieee80211_softmac.o
/bin/sh: gcc: not found
make[2]: *** [/home/jim/Desktop/ieee80211/ieee80211_softmac.o] Error 127
make[1]: *** [_module_/home/jim/Desktop/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2



---

