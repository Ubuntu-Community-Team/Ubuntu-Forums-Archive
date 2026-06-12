---
title: "HP Pavilion dv6 Wireless not Working 10.04"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by aquethys on 2012-07-23
Hi everyone!
I am a learning Android developer and installed 12.04 Ubuntu and it worked fine on my pav dv6. However, for compatibility I have to use 10.04, and when I install that, the wireless just won't connect - in the status bar at the top there's a red exclamation mark. Right clicking it, everything that's checked needs to be...help? :) Thanks

---

### Post by mikewhatever on 2012-07-23
Hi, and welcome to the forums. For guidance on how to post a wireless help request, please see this thread: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by aquethys on 2012-07-24
> **mikewhatever said:**
> Hi, and welcome to the forums. For guidance on how to post a wireless help request, please see this thread: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
Thanks! Okay, I've attached a word document that should contain everything there...

---

### Post by mikewhatever on 2012-07-24
Perfect!

**Lspci:**
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09) 
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09) 
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04) 
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4) 
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4) 
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4) 
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4) 
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04) 
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04) 
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04) 
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
0d:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01) 
13:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01) 
19:00.0 USB Controller: NEC Corporation Device 0194 (rev 04) 


**lsusb:**
Bus 003 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 001 Device 003: ID 138a:0018 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:a7:b0:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB) 

**iwconfig:**
lo        no wireless extensions. 
 
eth0      no wireless extensions. 

**lsmod:**

Module                  Size  Used by 
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat 
usb_storage            50633  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61546  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               6924  1 snd_hda_codec 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
joydev                 11104  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              23681  2 snd_pcm,snd_seq 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               62915  0 
videodev               40550  1 uvcvideo 
v4l1_compat            15495  2 uvcvideo,videodev 
v4l2_compat_ioctl32    11892  1 videodev 
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
fbcon                  39270  71 
tileblit                2487  1 fbcon 
font                    8053  1 fbcon 
bitblit                 5811  1 fbcon 
softcursor              1565  1 bitblit 
xhci                   42775  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb 
soundcore               8052  1 snd 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
psmouse                65040  0 
serio_raw               4918  0 
hp_accel               12168  0 
lis3lv02d               7648  1 hp_accel 
input_polldev           3106  1 lis3lv02d 
led_class               3764  1 hp_accel 
video                  20623  0 
output                  2503  1 video 
lp                      9336  0 
parport                37160  2 ppdev,lp 
usbhid                 41116  0 
hid                    83888  1 usbhid 
ahci                   38350  1 
r8169                  39714  0 
mii                     5237  1 r8169 

**kmesg:**
[    0.855512] system 00:05: ioport range 0xffff-0xffff has been reserved 
[    0.855515] system 00:05: ioport range 0x400-0x453 has been reserved 
[    0.855517] system 00:05: ioport range 0x458-0x47f has been reserved 
[    0.855519] system 00:05: ioport range 0x500-0x57f has been reserved 
[    0.855521] system 00:05: ioport range 0x164e-0x164f has been reserved 
[    0.855525] system 00:07: ioport range 0x454-0x457 has been reserved 
[    0.855531] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved 
[    0.855533] system 00:0a: iomem range 0xfed10000-0xfed17fff has been reserved 
[    0.855537] system 00:0a: iomem range 0xfed18000-0xfed18fff has been reserved 
[    0.855540] system 00:0a: iomem range 0xfed19000-0xfed19fff has been reserved 
[    0.855542] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved 
[    0.855544] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved 
[    0.855546] system 00:0a: iomem range 0xfed90000-0xfed93fff has been reserved 
[    0.855549] system 00:0a: iomem range 0xff000000-0xffffffff could not be reserved 
[    0.855551] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved 
[    0.855553] system 00:0a: iomem range 0xafa00000-0xafa00fff could not be reserved 
[    0.855558] system 00:0c: iomem range 0x20000000-0x201fffff could not be reserved 
[    0.855560] system 00:0c: iomem range 0x40000000-0x401fffff could not be reserved 
[    0.860210] pci 0000:13:00.0: BAR 6: no parent found for of device [0xffff0000-0xffffffff] 
[    0.860264] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    0.860266] pci 0000:00:01.0:   IO window: 0x5000-0x5fff 
[    0.860269] pci 0000:00:01.0:   MEM window: 0xc7500000-0xc84fffff 
[    0.860272] pci 0000:00:01.0:   PREFETCH window: 0x000000c0400000-0x000000c13fffff 
[    0.860276] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:07 
[    0.860280] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff 
[    0.860286] pci 0000:00:1c.0:   MEM window: 0xc6500000-0xc74fffff 
[    0.860291] pci 0000:00:1c.0:   PREFETCH window: 0x000000c1400000-0x000000c23fffff 
[    0.860300] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0d 
[    0.860303] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff 
[    0.860310] pci 0000:00:1c.1:   MEM window: 0xc5500000-0xc64fffff 
[    0.860315] pci 0000:00:1c.1:   PREFETCH window: 0x000000c2400000-0x000000c33fffff 
[    0.860326] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:13 
[    0.860329] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff 
[    0.860336] pci 0000:00:1c.2:   MEM window: 0xc4500000-0xc54fffff 
[    0.860341] pci 0000:00:1c.2:   PREFETCH window: 0x000000c3400000-0x000000c43fffff 
[    0.860350] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:19 
[    0.860351] pci 0000:00:1c.3:   IO window: disabled 
[    0.860358] pci 0000:00:1c.3:   MEM window: 0xc4400000-0xc44fffff 
[    0.860363] pci 0000:00:1c.3:   PREFETCH window: disabled 
[    0.860379]   alloc irq_desc for 16 on node -1 
[    0.860380]   alloc kstat_irqs on node -1 
[    0.860384] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.860387] pci 0000:00:01.0: setting latency timer to 64 
[    0.860397]   alloc irq_desc for 17 on node -1 
[    0.860398]   alloc kstat_irqs on node -1 
[    0.860401] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.860406] pci 0000:00:1c.0: setting latency timer to 64 
[    0.860417] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16 
[    0.860422] pci 0000:00:1c.1: setting latency timer to 64 
[    0.860432]   alloc irq_desc for 18 on node -1 
[    0.860433]   alloc kstat_irqs on node -1 
[    0.860436] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.860441] pci 0000:00:1c.2: setting latency timer to 64 
[    0.860452]   alloc irq_desc for 19 on node -1 
[    0.860453]   alloc kstat_irqs on node -1 
[    0.860455] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    0.860460] pci 0000:00:1c.3: setting latency timer to 64 
[    0.860465] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.860467] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff] 
[    0.860469] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff] 
[    0.860471] pci_bus 0000:01: resource 1 mem: [0xc7500000-0xc84fffff] 
[    0.860473] pci_bus 0000:01: resource 2 pref mem [0xc0400000-0xc13fffff] 
[    0.860475] pci_bus 0000:07: resource 0 io:  [0x4000-0x4fff] 
[    0.860477] pci_bus 0000:07: resource 1 mem: [0xc6500000-0xc74fffff] 
[    0.860478] pci_bus 0000:07: resource 2 pref mem [0xc1400000-0xc23fffff] 
[    0.860481] pci_bus 0000:0d: resource 0 io:  [0x3000-0x3fff] 
[    0.860482] pci_bus 0000:0d: resource 1 mem: [0xc5500000-0xc64fffff] 
[    0.860484] pci_bus 0000:0d: resource 2 pref mem [0xc2400000-0xc33fffff] 
[    0.860486] pci_bus 0000:13: resource 0 io:  [0x2000-0x2fff] 
[    0.860488] pci_bus 0000:13: resource 1 mem: [0xc4500000-0xc54fffff] 
[    0.860490] pci_bus 0000:13: resource 2 pref mem [0xc3400000-0xc43fffff] 
[    0.860492] pci_bus 0000:19: resource 1 mem: [0xc4400000-0xc44fffff] 
[    0.860518] NET: Registered protocol family 2 
[    0.860656] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.861490] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
[    0.862873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.863023] TCP: Hash tables configured (established 524288 bind 65536) 
[    0.863025] TCP reno registered 
[    0.863101] NET: Registered protocol family 1 
[    0.863116] pci 0000:00:02.0: Boot video device 
[    0.913864] Simple Boot Flag at 0x44 set to 0x1 
[    0.914089] Scanning for low memory corruption every 60 seconds 
[    0.914190] audit: initializing netlink socket (disabled) 
[    0.914198] type=2000 audit(1343079704.763:1): initialized 
[    0.922243] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.923354] VFS: Disk quotas dquot_6.5.2 
[    0.923396] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    0.923844] fuse init (API version 7.13) 
[    0.923907] msgmni has been set to 7803 
[    0.924112] alg: No test for stdrng (krng) 
[    0.924154] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.924156] io scheduler noop registered 
[    0.924158] io scheduler anticipatory registered 
[    0.924159] io scheduler deadline registered 
[    0.924205] io scheduler cfq registered (default) 
[    0.924303]   alloc irq_desc for 24 on node -1 
[    0.924305]   alloc kstat_irqs on node -1 
[    0.924311] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X 
[    0.924316] pcieport 0000:00:01.0: setting latency timer to 64 
[    0.924433]   alloc irq_desc for 25 on node -1 
[    0.924435]   alloc kstat_irqs on node -1 
[    0.924444] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X 
[    0.924456] pcieport 0000:00:1c.0: setting latency timer to 64 
[    0.924616]   alloc irq_desc for 26 on node -1 
[    0.924618]   alloc kstat_irqs on node -1 
[    0.924627] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X 
[    0.924639] pcieport 0000:00:1c.1: setting latency timer to 64 
[    0.924798]   alloc irq_desc for 27 on node -1 
[    0.924799]   alloc kstat_irqs on node -1 
[    0.924808] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X 
[    0.924819] pcieport 0000:00:1c.2: setting latency timer to 64 
[    0.924979]   alloc irq_desc for 28 on node -1 
[    0.924981]   alloc kstat_irqs on node -1 
[    0.924990] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X 
[    0.925001] pcieport 0000:00:1c.3: setting latency timer to 64 
[    0.925088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.925215] _OSC invalid UUID 
[    0.925318] _OSC invalid UUID 
[    0.925415] _OSC invalid UUID 
[    0.925523] _OSC invalid UUID 
[    0.925618] _OSC invalid UUID 
[    0.925712] _OSC invalid UUID 
[    0.925732] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.926693] ACPI: AC Adapter [AC] (on-line) 
[    0.926750] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0 
[    0.927630] ACPI: Lid Switch [LID] 
[    0.927673] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1 
[    0.927679] ACPI: Power Button [PWRB] 
[    0.927711] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[    0.927712] ACPI: Power Button [PWRF] 
[    0.928733] ACPI: SSDT 00000000ace70718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100806) 
[    0.931833] Monitor-Mwait will be used to enter C-1 state 
[    0.931858] Monitor-Mwait will be used to enter C-2 state 
[    0.931877] Monitor-Mwait will be used to enter C-3 state 
[    0.931921] processor LNXCPU:00: registered as cooling_device0 
[    0.932428] ACPI: SSDT 00000000ace71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100806) 
[    0.932916] ACPI: SSDT 00000000ace6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100806) 
[    0.933984] processor LNXCPU:01: registered as cooling_device1 
[    0.935373] processor LNXCPU:02: registered as cooling_device2 
[    0.952210] processor LNXCPU:03: registered as cooling_device3 
[    0.965036] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.965045] ACPI: Thermal Zone [THRM] (70 C) 
[    0.967250] Linux agpgart interface v0.103 
[    0.967276] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.968415] brd: module loaded 
[    0.968760] loop: module loaded 
[    0.968820] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    0.969103] Fixed MDIO Bus: probed 
[    0.969128] PPP generic driver version 2.4.2 
[    0.969151] tun: Universal TUN/TAP device driver, 1.6 
[    0.969152] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.969204] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.969224] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.969242] ehci_hcd 0000:00:1a.0: setting latency timer to 64 
[    0.969245] ehci_hcd 0000:00:1a.0: EHCI Host Controller 
[    0.969268] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[    0.969301] ehci_hcd 0000:00:1a.0: debug port 2 
[    0.973176] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported 
[    0.973191] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc850a000 
[    0.985614] Freeing initrd memory: 8483k freed 
[    0.991872] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00 
[    0.992022] usb usb1: configuration #1 chosen from 1 choice 
[    0.992045] hub 1-0:1.0: USB hub found 
[    0.992052] hub 1-0:1.0: 2 ports detected 
[    0.992106]   alloc irq_desc for 20 on node -1 
[    0.992108]   alloc kstat_irqs on node -1 
[    0.992115] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.992142] ehci_hcd 0000:00:1d.0: setting latency timer to 64 
[    0.992147] ehci_hcd 0000:00:1d.0: EHCI Host Controller 
[    0.992175] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    0.992206] ehci_hcd 0000:00:1d.0: debug port 2 
[    0.996089] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported 
[    0.996104] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc8509000 
[    1.009687] ACPI: Battery Slot [BAT0] (battery present) 
[    1.011844] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00 
[    1.011970] usb usb2: configuration #1 chosen from 1 choice 
[    1.011990] hub 2-0:1.0: USB hub found 
[    1.011994] hub 2-0:1.0: 2 ports detected 
[    1.012033] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    1.012045] uhci_hcd: USB Universal Host Controller Interface driver 
[    1.012110] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    1.025123] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.025129] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    1.025211] mice: PS/2 mouse device common for all mice 
[    1.025303] rtc_cmos 00:06: RTC can wake from S4 
[    1.025346] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
[    1.025381] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs 
[    1.025509] device-mapper: uevent: version 1.0.3 
[    1.025598] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[    1.025676] device-mapper: multipath: version 1.1.0 loaded 
[    1.025678] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    1.025938] cpuidle: using governor ladder 
[    1.026088] cpuidle: using governor menu 
[    1.026338] TCP cubic registered 
[    1.026467] NET: Registered protocol family 10 
[    1.027227] NET: Registered protocol family 17 
[    1.028988] PM: Resume from disk failed. 
[    1.029000] registered taskstats version 1 
[    1.029699]   Magic number: 4:97:703 
[    1.029782] rtc_cmos 00:06: setting system clock to 2012-07-23 21:41:45 UTC (1343079705) 
[    1.029786] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.029788] EDD information not available. 
[    1.029826] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    1.029902] Freeing unused kernel memory: 884k freed 
[    1.030021] Write protecting the kernel read-only data: 7716k 
[    1.044902] udev: starting version 151 
[    1.064805] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    1.064830] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.064894] r8169 0000:07:00.0: setting latency timer to 64 
[    1.064902] r8169 0000:07:00.0: unknown MAC, using family default 
[    1.064966]   alloc irq_desc for 29 on node -1 
[    1.064968]   alloc kstat_irqs on node -1 
[    1.064988] r8169 0000:07:00.0: irq 29 for MSI/MSI-X 
[    1.065592] eth0: RTL8168b/8111b at 0xffffc90000678000, 2c:27:d7:a7:b0:04, XID 0c200000 IRQ 29 
[    1.075300] ahci 0000:00:1f.2: version 3.0 
[    1.075321] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    1.075383]   alloc irq_desc for 30 on node -1 
[    1.075386]   alloc kstat_irqs on node -1 
[    1.075399] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X 
[    1.091907] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode 
[    1.091913] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.091921] ahci 0000:00:1f.2: setting latency timer to 64 
[    1.111789] scsi0 : ahci 
[    1.111909] scsi1 : ahci 
[    1.111977] scsi2 : ahci 
[    1.112041] scsi3 : ahci 
[    1.112103] scsi4 : ahci 
[    1.112163] scsi5 : ahci 
[    1.112307] ata1: SATA max UDMA/133 abar m2048@0xc8508000 port 0xc8508100 irq 30 
[    1.112309] ata2: DUMMY 
[    1.112311] ata3: DUMMY 
[    1.112313] ata4: DUMMY 
[    1.112315] ata5: DUMMY 
[    1.112318] ata6: SATA max UDMA/133 abar m2048@0xc8508000 port 0xc8508380 irq 30 
[    1.320170] usb 1-1: new high speed USB device using ehci_hcd and address 2 
[    1.469974] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.470481] usb 1-1: configuration #1 chosen from 1 choice 
[    1.470659] hub 1-1:1.0: USB hub found 
[    1.470749] hub 1-1:1.0: 6 ports detected 
[    1.473267] ata6.00: ACPI _SDD failed (AE 0x5) 
[    1.490017] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.500924] ata1.00: ATA-8: ST9500325AS, 0005HPM1, max UDMA/100 
[    1.500934] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
[    1.524958] ata1.00: configured for UDMA/100 
[    1.540096] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0005 PQ: 0 ANSI: 5 
[    1.540277] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    1.540339] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB) 
[    1.540380] sd 0:0:0:0: [sda] Write Protect is off 
[    1.540383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.540399] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.540498]  sda: sda1 sda2 sda3 sda4 
[    1.568994] sd 0:0:0:0: [sda] Attached SCSI disk 
[    1.599862] usb 2-1: new high speed USB device using ehci_hcd and address 2 
[    1.740098] usb 2-1: configuration #1 chosen from 1 choice 
[    1.740260] hub 2-1:1.0: USB hub found 
[    1.740343] hub 2-1:1.0: 6 ports detected 
[    1.829678] usb 1-1.1: new full speed USB device using ehci_hcd and address 3 
[    1.951146] usb 1-1.1: configuration #1 chosen from 1 choice 
[    2.039482] usb 1-1.2: new high speed USB device using ehci_hcd and address 4 
[    2.250961] usb 1-1.2: configuration #1 chosen from 1 choice 
[    2.339021] usb 2-1.1: new full speed USB device using ehci_hcd and address 3 
[    2.452632] usb 2-1.1: configuration #1 chosen from 1 choice 
[    2.463010] usbcore: registered new interface driver hiddev 
[    2.463967] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5 
[    2.464071] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input0 
[    2.466024] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input6 
[    2.466196] generic-usb 0003:046D:C52B.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input1 
[    2.468657] generic-usb 0003:046D:C52B.0003: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input2 
[    2.468680] usbcore: registered new interface driver usbhid 
[    2.468683] usbhid: v2.6:USB HID core driver 
[    6.812462] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    6.817121] ata6.00: ACPI _SDD failed (AE 0x5) 
[    6.817137] ata6.00: ACPI: failed the second time, disabled 
[    6.817141] ata6.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100 
[    6.818620] ata6.00: configured for UDMA/100 
[    6.837671] scsi 5:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5 
[    6.848811] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray 
[    6.848820] Uniform CD-ROM driver Revision: 3.20 
[    6.848978] sr 5:0:0:0: Attached scsi CD-ROM sr0 
[    6.849049] sr 5:0:0:0: Attached scsi generic sg1 type 5 
[    7.843957] EXT4-fs (loop0): mounted filesystem with ordered data mode 
[   19.019609] udev: starting version 151 
[   19.035532] lp: driver loaded but no devices found 
[   19.100865] vga16fb: initializing 
[   19.100870] vga16fb: mapped to 0xffff8800000a0000 
[   19.100926] fb0: VGA16 VGA frame buffer device 
[   19.102579] xhci_hcd 0000:19:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   19.102670] xhci_hcd 0000:19:00.0: setting latency timer to 64 
[   19.102678] xhci_hcd 0000:19:00.0: xHCI Host Controller 
[   19.102767] xhci_hcd 0000:19:00.0: new USB bus registered, assigned bus number 3 
[   19.102994] xhci_hcd 0000:19:00.0: irq 19, io mem 0xc4400000 
[   19.108362] usb usb3: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor 
[   19.108465] usb usb3: configuration #1 chosen from 1 choice 
[   19.108470] xHCI xhci_add_endpoint called for root hub 
[   19.108473] xHCI xhci_check_bandwidth called for root hub 
[   19.108517] hub 3-0:1.0: USB hub found 
[   19.108528] hub 3-0:1.0: 4 ports detected 
[   19.124954] lis3lv02d: laptop model unknown, using default axes configuration 
[   19.180549] Linux video capture interface: v2.00 
[   19.188832] uvcvideo: Found UVC 1.00 device HP TrueVision HD (5986:02ac) 
[   19.197701] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7 
[   19.197759] usbcore: registered new interface driver uvcvideo 
[   19.197763] USB Video Class driver (v0.1.0) 
[   19.214160] type=1505 audit(1343101323.700:2):  operation="profile_load" pid=714 name="/sbin/dhclient3" 
[   19.214994] type=1505 audit(1343101323.710:3):  operation="profile_load" pid=714 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   19.215419] type=1505 audit(1343101323.710:4):  operation="profile_load" pid=714 name="/usr/lib/connman/scripts/dhclient-script" 
[   19.233183] type=1505 audit(1343101323.720:5):  operation="profile_replace" pid=743 name="/sbin/dhclient3" 
[   19.234030] type=1505 audit(1343101323.720:6):  operation="profile_replace" pid=743 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   19.234496] type=1505 audit(1343101323.720:7):  operation="profile_replace" pid=743 name="/usr/lib/connman/scripts/dhclient-script" 
[   19.273941] Console: switching to colour frame buffer device 80x30 
[   19.292375]   alloc irq_desc for 22 on node -1 
[   19.292378]   alloc kstat_irqs on node -1 
[   19.292386] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[   19.292481] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   19.528938] lis3lv02d: unknown sensor type 0x33 
[   19.528948] lis3lv02d: probe of HPQ0004:00 failed with error -22 
[   19.528968] lis3lv02d driver loaded. 
[   19.716556] Unable to query Synaptics hardware. 
[   19.971281] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8 
[   19.995890] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9 
[   19.995987] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
[   20.168185] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261112k 
[   20.355662] type=1505 audit(1343101324.851:8):  operation="profile_load" pid=912 name="/usr/share/gdm/guest-session/Xsession" 
[   20.358320] type=1505 audit(1343101324.851:9):  operation="profile_replace" pid=913 name="/sbin/dhclient3" 
[   20.358425] type=1505 audit(1343101324.851:10):  operation="profile_load" pid=914 name="/usr/bin/evince" 
[   20.359087] type=1505 audit(1343101324.851:11):  operation="profile_replace" pid=913 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   20.392447] r8169: eth0: link down 
[   20.392962] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   20.491323] ppdev: user-space parallel port driver 
[   20.537454] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11 
[   20.663707] CPU0 attaching NULL sched-domain. 
[   20.663712] CPU1 attaching NULL sched-domain. 
[   20.663714] CPU2 attaching NULL sched-domain. 
[   20.663716] CPU3 attaching NULL sched-domain. 
[   20.733889] CPU0 attaching sched-domain: 
[   20.733893]  domain 0: span 0-1 level SIBLING 
[   20.733895]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   20.733900]   domain 1: span 0-3 level MC 
[   20.733901]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.733907] CPU1 attaching sched-domain: 
[   20.733909]  domain 0: span 0-1 level SIBLING 
[   20.733910]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   20.733914]   domain 1: span 0-3 level MC 
[   20.733916]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.733920] CPU2 attaching sched-domain: 
[   20.733921]  domain 0: span 2-3 level SIBLING 
[   20.733923]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   20.733927]   domain 1: span 0-3 level MC 
[   20.733928]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.733932] CPU3 attaching sched-domain: 
[   20.733934]  domain 0: span 2-3 level SIBLING 
[   20.733935]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   20.733939]   domain 1: span 0-3 level MC 
[   20.733940]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.734276] CPU0 attaching NULL sched-domain. 
[   20.734279] CPU1 attaching NULL sched-domain. 
[   20.734281] CPU2 attaching NULL sched-domain. 
[   20.734282] CPU3 attaching NULL sched-domain. 
[   20.863812] CPU0 attaching sched-domain: 
[   20.863815]  domain 0: span 0-1 level SIBLING 
[   20.863818]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   20.863822]   domain 1: span 0-3 level MC 
[   20.863824]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.863831] CPU1 attaching sched-domain: 
[   20.863832]  domain 0: span 0-1 level SIBLING 
[   20.863834]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   20.863838]   domain 1: span 0-3 level MC 
[   20.863839]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.863844] CPU2 attaching sched-domain: 
[   20.863845]  domain 0: span 2-3 level SIBLING 
[   20.863847]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   20.863850]   domain 1: span 0-3 level MC 
[   20.863852]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.863856] CPU3 attaching sched-domain: 
[   20.863858]  domain 0: span 2-3 level SIBLING 
[   20.863859]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   20.863863]   domain 1: span 0-3 level MC 
[   20.863865]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.542943] CPU0 attaching NULL sched-domain. 
[   21.542949] CPU1 attaching NULL sched-domain. 
[   21.542953] CPU2 attaching NULL sched-domain. 
[   21.542956] CPU3 attaching NULL sched-domain. 
[   21.603294] CPU0 attaching sched-domain: 
[   21.603297]  domain 0: span 0-1 level SIBLING 
[   21.603300]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   21.603304]   domain 1: span 0-3 level MC 
[   21.603306]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.603312] CPU1 attaching sched-domain: 
[   21.603314]  domain 0: span 0-1 level SIBLING 
[   21.603315]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   21.603319]   domain 1: span 0-3 level MC 
[   21.603321]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.603325] CPU2 attaching sched-domain: 
[   21.603326]  domain 0: span 2-3 level SIBLING 
[   21.603328]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   21.603332]   domain 1: span 0-3 level MC 
[   21.603333]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.603337] CPU3 attaching sched-domain: 
[   21.603339]  domain 0: span 2-3 level SIBLING 
[   21.603340]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   21.603344]   domain 1: span 0-3 level MC 
[   21.603345]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.603679] CPU0 attaching NULL sched-domain. 
[   21.603681] CPU1 attaching NULL sched-domain. 
[   21.603683] CPU2 attaching NULL sched-domain. 
[   21.603685] CPU3 attaching NULL sched-domain. 
[   21.693143] CPU0 attaching sched-domain: 
[   21.693147]  domain 0: span 0-1 level SIBLING 
[   21.693149]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   21.693153]   domain 1: span 0-3 level MC 
[   21.693155]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.693161] CPU1 attaching sched-domain: 
[   21.693162]  domain 0: span 0-1 level SIBLING 
[   21.693164]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   21.693168]   domain 1: span 0-3 level MC 
[   21.693170]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.693174] CPU2 attaching sched-domain: 
[   21.693175]  domain 0: span 2-3 level SIBLING 
[   21.693177]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   21.693181]   domain 1: span 0-3 level MC 
[   21.693182]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.693187] CPU3 attaching sched-domain: 
[   21.693188]  domain 0: span 2-3 level SIBLING 
[   21.693190]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   21.693193]   domain 1: span 0-3 level MC 
[   21.693195]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[  105.843559] usb 3-3: new high speed USB device using xhci_hcd and address 0 
[  105.864010] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.864383] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.864758] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.865134] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.865453] usb 3-3: configuration #1 chosen from 1 choice 
[  105.921263] Initializing USB Mass Storage driver... 
[  105.921714] scsi6 : SCSI emulation for USB Mass Storage devices 
[  105.922412] usb-storage: device found at 2 
[  105.922418] usb-storage: waiting for device to settle before scanning 
[  105.922442] usbcore: registered new interface driver usb-storage 
[  105.922452] USB Mass Storage support registered. 
[  110.915082] usb-storage: device scan complete 
[  110.915479] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS 
[  110.916560] sd 6:0:0:0: Attached scsi generic sg2 type 0 
[  110.920861] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB) 
[  110.921790] sd 6:0:0:0: [sdb] Write Protect is off 
[  110.921802] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08 
[  110.921809] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.923539] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.923553]  sdb: sdb1 
[  110.927131] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.927142] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
Net config:
[    0.860291] pci 0000:00:1c.0:   PREFETCH window: 0x000000c1400000-0x000000c23fffff 
[    0.860300] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0d 
[    0.860303] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff 
[    0.860310] pci 0000:00:1c.1:   MEM window: 0xc5500000-0xc64fffff 
[    0.860315] pci 0000:00:1c.1:   PREFETCH window: 0x000000c2400000-0x000000c33fffff 
[    0.860326] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:13 
[    0.860329] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff 
[    0.860336] pci 0000:00:1c.2:   MEM window: 0xc4500000-0xc54fffff 
[    0.860341] pci 0000:00:1c.2:   PREFETCH window: 0x000000c3400000-0x000000c43fffff 
[    0.860350] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:19 
[    0.860351] pci 0000:00:1c.3:   IO window: disabled 
[    0.860358] pci 0000:00:1c.3:   MEM window: 0xc4400000-0xc44fffff 
[    0.860363] pci 0000:00:1c.3:   PREFETCH window: disabled 
[    0.860379]   alloc irq_desc for 16 on node -1 
[    0.860380]   alloc kstat_irqs on node -1 
[    0.860384] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.860387] pci 0000:00:01.0: setting latency timer to 64 
[    0.860397]   alloc irq_desc for 17 on node -1 
[    0.860398]   alloc kstat_irqs on node -1 
[    0.860401] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.860406] pci 0000:00:1c.0: setting latency timer to 64 
[    0.860417] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16 
[    0.860422] pci 0000:00:1c.1: setting latency timer to 64 
[    0.860432]   alloc irq_desc for 18 on node -1 
[    0.860433]   alloc kstat_irqs on node -1 
[    0.860436] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.860441] pci 0000:00:1c.2: setting latency timer to 64 
[    0.860452]   alloc irq_desc for 19 on node -1 
[    0.860453]   alloc kstat_irqs on node -1 
[    0.860455] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    0.860460] pci 0000:00:1c.3: setting latency timer to 64 
[    0.860465] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.860467] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff] 
[    0.860469] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff] 
[    0.860471] pci_bus 0000:01: resource 1 mem: [0xc7500000-0xc84fffff] 
[    0.860473] pci_bus 0000:01: resource 2 pref mem [0xc0400000-0xc13fffff] 
[    0.860475] pci_bus 0000:07: resource 0 io:  [0x4000-0x4fff] 
[    0.860477] pci_bus 0000:07: resource 1 mem: [0xc6500000-0xc74fffff] 
[    0.860478] pci_bus 0000:07: resource 2 pref mem [0xc1400000-0xc23fffff] 
[    0.860481] pci_bus 0000:0d: resource 0 io:  [0x3000-0x3fff] 
[    0.860482] pci_bus 0000:0d: resource 1 mem: [0xc5500000-0xc64fffff] 
[    0.860484] pci_bus 0000:0d: resource 2 pref mem [0xc2400000-0xc33fffff] 
[    0.860486] pci_bus 0000:13: resource 0 io:  [0x2000-0x2fff] 
[    0.860488] pci_bus 0000:13: resource 1 mem: [0xc4500000-0xc54fffff] 
[    0.860490] pci_bus 0000:13: resource 2 pref mem [0xc3400000-0xc43fffff] 
[    0.860492] pci_bus 0000:19: resource 1 mem: [0xc4400000-0xc44fffff] 
[    0.860518] NET: Registered protocol family 2 
[    0.860656] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.861490] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
[    0.862873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.863023] TCP: Hash tables configured (established 524288 bind 65536) 
[    0.863025] TCP reno registered 
[    0.863101] NET: Registered protocol family 1 
[    0.863116] pci 0000:00:02.0: Boot video device 
[    0.913864] Simple Boot Flag at 0x44 set to 0x1 
[    0.914089] Scanning for low memory corruption every 60 seconds 
[    0.914190] audit: initializing netlink socket (disabled) 
[    0.914198] type=2000 audit(1343079704.763:1): initialized 
[    0.922243] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.923354] VFS: Disk quotas dquot_6.5.2 
[    0.923396] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    0.923844] fuse init (API version 7.13) 
[    0.923907] msgmni has been set to 7803 
[    0.924112] alg: No test for stdrng (krng) 
[    0.924154] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.924156] io scheduler noop registered 
[    0.924158] io scheduler anticipatory registered 
[    0.924159] io scheduler deadline registered 
[    0.924205] io scheduler cfq registered (default) 
[    0.924303]   alloc irq_desc for 24 on node -1 
[    0.924305]   alloc kstat_irqs on node -1 
[    0.924311] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X 
[    0.924316] pcieport 0000:00:01.0: setting latency timer to 64 
[    0.924433]   alloc irq_desc for 25 on node -1 
[    0.924435]   alloc kstat_irqs on node -1 
[    0.924444] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X 
[    0.924456] pcieport 0000:00:1c.0: setting latency timer to 64 
[    0.924616]   alloc irq_desc for 26 on node -1 
[    0.924618]   alloc kstat_irqs on node -1 
[    0.924627] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X 
[    0.924639] pcieport 0000:00:1c.1: setting latency timer to 64 
[    0.924798]   alloc irq_desc for 27 on node -1 
[    0.924799]   alloc kstat_irqs on node -1 
[    0.924808] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X 
[    0.924819] pcieport 0000:00:1c.2: setting latency timer to 64 
[    0.924979]   alloc irq_desc for 28 on node -1 
[    0.924981]   alloc kstat_irqs on node -1 
[    0.924990] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X 
[    0.925001] pcieport 0000:00:1c.3: setting latency timer to 64 
[    0.925088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.925215] _OSC invalid UUID 
[    0.925318] _OSC invalid UUID 
[    0.925415] _OSC invalid UUID 
[    0.925523] _OSC invalid UUID 
[    0.925618] _OSC invalid UUID 
[    0.925712] _OSC invalid UUID 
[    0.925732] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.926693] ACPI: AC Adapter [AC] (on-line) 
[    0.926750] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0 
[    0.927630] ACPI: Lid Switch [LID] 
[    0.927673] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1 
[    0.927679] ACPI: Power Button [PWRB] 
[    0.927711] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[    0.927712] ACPI: Power Button [PWRF] 
[    0.928733] ACPI: SSDT 00000000ace70718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100806) 
[    0.931833] Monitor-Mwait will be used to enter C-1 state 
[    0.931858] Monitor-Mwait will be used to enter C-2 state 
[    0.931877] Monitor-Mwait will be used to enter C-3 state 
[    0.931921] processor LNXCPU:00: registered as cooling_device0 
[    0.932428] ACPI: SSDT 00000000ace71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100806) 
[    0.932916] ACPI: SSDT 00000000ace6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100806) 
[    0.933984] processor LNXCPU:01: registered as cooling_device1 
[    0.935373] processor LNXCPU:02: registered as cooling_device2 
[    0.952210] processor LNXCPU:03: registered as cooling_device3 
[    0.965036] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.965045] ACPI: Thermal Zone [THRM] (70 C) 
[    0.967250] Linux agpgart interface v0.103 
[    0.967276] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.968415] brd: module loaded 
[    0.968760] loop: module loaded 
[    0.968820] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    0.969103] Fixed MDIO Bus: probed 
[    0.969128] PPP generic driver version 2.4.2 
[    0.969151] tun: Universal TUN/TAP device driver, 1.6 
[    0.969152] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.969204] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.969224] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.969242] ehci_hcd 0000:00:1a.0: setting latency timer to 64 
[    0.969245] ehci_hcd 0000:00:1a.0: EHCI Host Controller 
[    0.969268] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[    0.969301] ehci_hcd 0000:00:1a.0: debug port 2 
[    0.973176] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported 
[    0.973191] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc850a000 
[    0.985614] Freeing initrd memory: 8483k freed 
[    0.991872] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00 
[    0.992022] usb usb1: configuration #1 chosen from 1 choice 
[    0.992045] hub 1-0:1.0: USB hub found 
[    0.992052] hub 1-0:1.0: 2 ports detected 
[    0.992106]   alloc irq_desc for 20 on node -1 
[    0.992108]   alloc kstat_irqs on node -1 
[    0.992115] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.992142] ehci_hcd 0000:00:1d.0: setting latency timer to 64 
[    0.992147] ehci_hcd 0000:00:1d.0: EHCI Host Controller 
[    0.992175] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    0.992206] ehci_hcd 0000:00:1d.0: debug port 2 
[    0.996089] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported 
[    0.996104] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc8509000 
[    1.009687] ACPI: Battery Slot [BAT0] (battery present) 
[    1.011844] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00 
[    1.011970] usb usb2: configuration #1 chosen from 1 choice 
[    1.011990] hub 2-0:1.0: USB hub found 
[    1.011994] hub 2-0:1.0: 2 ports detected 
[    1.012033] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    1.012045] uhci_hcd: USB Universal Host Controller Interface driver 
[    1.012110] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    1.025123] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.025129] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    1.025211] mice: PS/2 mouse device common for all mice 
[    1.025303] rtc_cmos 00:06: RTC can wake from S4 
[    1.025346] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
[    1.025381] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs 
[    1.025509] device-mapper: uevent: version 1.0.3 
[    1.025598] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[    1.025676] device-mapper: multipath: version 1.1.0 loaded 
[    1.025678] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    1.025938] cpuidle: using governor ladder 
[    1.026088] cpuidle: using governor menu 
[    1.026338] TCP cubic registered 
[    1.026467] NET: Registered protocol family 10 
[    1.027227] NET: Registered protocol family 17 
[    1.028988] PM: Resume from disk failed. 
[    1.029000] registered taskstats version 1 
[    1.029699]   Magic number: 4:97:703 
[    1.029782] rtc_cmos 00:06: setting system clock to 2012-07-23 21:41:45 UTC (1343079705) 
[    1.029786] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.029788] EDD information not available. 
[    1.029826] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    1.029902] Freeing unused kernel memory: 884k freed 
[    1.030021] Write protecting the kernel read-only data: 7716k 
[    1.044902] udev: starting version 151 
[    1.064805] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    1.064830] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.064894] r8169 0000:07:00.0: setting latency timer to 64 
[    1.064902] r8169 0000:07:00.0: unknown MAC, using family default 
[    1.064966]   alloc irq_desc for 29 on node -1 
[    1.064968]   alloc kstat_irqs on node -1 
[    1.064988] r8169 0000:07:00.0: irq 29 for MSI/MSI-X 
[    1.065592] eth0: RTL8168b/8111b at 0xffffc90000678000, 2c:27:d7:a7:b0:04, XID 0c200000 IRQ 29 
[    1.075300] ahci 0000:00:1f.2: version 3.0 
[    1.075321] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    1.075383]   alloc irq_desc for 30 on node -1 
[    1.075386]   alloc kstat_irqs on node -1 
[    1.075399] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X 
[    1.091907] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode 
[    1.091913] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.091921] ahci 0000:00:1f.2: setting latency timer to 64 
[    1.111789] scsi0 : ahci 
[    1.111909] scsi1 : ahci 
[    1.111977] scsi2 : ahci 
[    1.112041] scsi3 : ahci 
[    1.112103] scsi4 : ahci 
[    1.112163] scsi5 : ahci 
[    1.112307] ata1: SATA max UDMA/133 abar m2048@0xc8508000 port 0xc8508100 irq 30 
[    1.112309] ata2: DUMMY 
[    1.112311] ata3: DUMMY 
[    1.112313] ata4: DUMMY 
[    1.112315] ata5: DUMMY 
[    1.112318] ata6: SATA max UDMA/133 abar m2048@0xc8508000 port 0xc8508380 irq 30 
[    1.320170] usb 1-1: new high speed USB device using ehci_hcd and address 2 
[    1.469974] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.470481] usb 1-1: configuration #1 chosen from 1 choice 
[    1.470659] hub 1-1:1.0: USB hub found 
[    1.470749] hub 1-1:1.0: 6 ports detected 
[    1.473267] ata6.00: ACPI _SDD failed (AE 0x5) 
[    1.490017] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.500924] ata1.00: ATA-8: ST9500325AS, 0005HPM1, max UDMA/100 
[    1.500934] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
[    1.524958] ata1.00: configured for UDMA/100 
[    1.540096] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0005 PQ: 0 ANSI: 5 
[    1.540277] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    1.540339] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB) 
[    1.540380] sd 0:0:0:0: [sda] Write Protect is off 
[    1.540383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.540399] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.540498]  sda: sda1 sda2 sda3 sda4 
[    1.568994] sd 0:0:0:0: [sda] Attached SCSI disk 
[    1.599862] usb 2-1: new high speed USB device using ehci_hcd and address 2 
[    1.740098] usb 2-1: configuration #1 chosen from 1 choice 
[    1.740260] hub 2-1:1.0: USB hub found 
[    1.740343] hub 2-1:1.0: 6 ports detected 
[    1.829678] usb 1-1.1: new full speed USB device using ehci_hcd and address 3 
[    1.951146] usb 1-1.1: configuration #1 chosen from 1 choice 
[    2.039482] usb 1-1.2: new high speed USB device using ehci_hcd and address 4 
[    2.250961] usb 1-1.2: configuration #1 chosen from 1 choice 
[    2.339021] usb 2-1.1: new full speed USB device using ehci_hcd and address 3 
[    2.452632] usb 2-1.1: configuration #1 chosen from 1 choice 
[    2.463010] usbcore: registered new interface driver hiddev 
[    2.463967] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5 
[    2.464071] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input0 
[    2.466024] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input6 
[    2.466196] generic-usb 0003:046D:C52B.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input1 
[    2.468657] generic-usb 0003:046D:C52B.0003: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input2 
[    2.468680] usbcore: registered new interface driver usbhid 
[    2.468683] usbhid: v2.6:USB HID core driver 
[    6.812462] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    6.817121] ata6.00: ACPI _SDD failed (AE 0x5) 
[    6.817137] ata6.00: ACPI: failed the second time, disabled 
[    6.817141] ata6.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100 
[    6.818620] ata6.00: configured for UDMA/100 
[    6.837671] scsi 5:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5 
[    6.848811] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray 
[    6.848820] Uniform CD-ROM driver Revision: 3.20 
[    6.848978] sr 5:0:0:0: Attached scsi CD-ROM sr0 
[    6.849049] sr 5:0:0:0: Attached scsi generic sg1 type 5 
[    7.843957] EXT4-fs (loop0): mounted filesystem with ordered data mode 
[   19.019609] udev: starting version 151 
[   19.035532] lp: driver loaded but no devices found 
[   19.100865] vga16fb: initializing 
[   19.100870] vga16fb: mapped to 0xffff8800000a0000 
[   19.100926] fb0: VGA16 VGA frame buffer device 
[   19.102579] xhci_hcd 0000:19:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   19.102670] xhci_hcd 0000:19:00.0: setting latency timer to 64 
[   19.102678] xhci_hcd 0000:19:00.0: xHCI Host Controller 
[   19.102767] xhci_hcd 0000:19:00.0: new USB bus registered, assigned bus number 3 
[   19.102994] xhci_hcd 0000:19:00.0: irq 19, io mem 0xc4400000 
[   19.108362] usb usb3: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor 
[   19.108465] usb usb3: configuration #1 chosen from 1 choice 
[   19.108470] xHCI xhci_add_endpoint called for root hub 
[   19.108473] xHCI xhci_check_bandwidth called for root hub 
[   19.108517] hub 3-0:1.0: USB hub found 
[   19.108528] hub 3-0:1.0: 4 ports detected 
[   19.124954] lis3lv02d: laptop model unknown, using default axes configuration 
[   19.180549] Linux video capture interface: v2.00 
[   19.188832] uvcvideo: Found UVC 1.00 device HP TrueVision HD (5986:02ac) 
[   19.197701] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7 
[   19.197759] usbcore: registered new interface driver uvcvideo 
[   19.197763] USB Video Class driver (v0.1.0) 
[   19.214160] type=1505 audit(1343101323.700:2):  operation="profile_load" pid=714 name="/sbin/dhclient3" 
[   19.214994] type=1505 audit(1343101323.710:3):  operation="profile_load" pid=714 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   19.215419] type=1505 audit(1343101323.710:4):  operation="profile_load" pid=714 name="/usr/lib/connman/scripts/dhclient-script" 
[   19.233183] type=1505 audit(1343101323.720:5):  operation="profile_replace" pid=743 name="/sbin/dhclient3" 
[   19.234030] type=1505 audit(1343101323.720:6):  operation="profile_replace" pid=743 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   19.234496] type=1505 audit(1343101323.720:7):  operation="profile_replace" pid=743 name="/usr/lib/connman/scripts/dhclient-script" 
[   19.273941] Console: switching to colour frame buffer device 80x30 
[   19.292375]   alloc irq_desc for 22 on node -1 
[   19.292378]   alloc kstat_irqs on node -1 
[   19.292386] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[   19.292481] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   19.528938] lis3lv02d: unknown sensor type 0x33 
[   19.528948] lis3lv02d: probe of HPQ0004:00 failed with error -22 
[   19.528968] lis3lv02d driver loaded. 
[   19.716556] Unable to query Synaptics hardware. 
[   19.971281] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8 
[   19.995890] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9 
[   19.995987] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
[   20.168185] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261112k 
[   20.355662] type=1505 audit(1343101324.851:8):  operation="profile_load" pid=912 name="/usr/share/gdm/guest-session/Xsession" 
[   20.358320] type=1505 audit(1343101324.851:9):  operation="profile_replace" pid=913 name="/sbin/dhclient3" 
[   20.358425] type=1505 audit(1343101324.851:10):  operation="profile_load" pid=914 name="/usr/bin/evince" 
[   20.359087] type=1505 audit(1343101324.851:11):  operation="profile_replace" pid=913 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   20.392447] r8169: eth0: link down 
[   20.392962] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   20.491323] ppdev: user-space parallel port driver 
[   20.537454] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11 
[   20.663707] CPU0 attaching NULL sched-domain. 
[   20.663712] CPU1 attaching NULL sched-domain. 
[   20.663714] CPU2 attaching NULL sched-domain. 
[   20.663716] CPU3 attaching NULL sched-domain. 
[   20.733889] CPU0 attaching sched-domain: 
[   20.733893]  domain 0: span 0-1 level SIBLING 
[   20.733895]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   20.733900]   domain 1: span 0-3 level MC 
[   20.733901]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.733907] CPU1 attaching sched-domain: 
[   20.733909]  domain 0: span 0-1 level SIBLING 
[   20.733910]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   20.733914]   domain 1: span 0-3 level MC 
[   20.733916]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.733920] CPU2 attaching sched-domain: 
[   20.733921]  domain 0: span 2-3 level SIBLING 
[   20.733923]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   20.733927]   domain 1: span 0-3 level MC 
[   20.733928]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.733932] CPU3 attaching sched-domain: 
[   20.733934]  domain 0: span 2-3 level SIBLING 
[   20.733935]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   20.733939]   domain 1: span 0-3 level MC 
[   20.733940]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.734276] CPU0 attaching NULL sched-domain. 
[   20.734279] CPU1 attaching NULL sched-domain. 
[   20.734281] CPU2 attaching NULL sched-domain. 
[   20.734282] CPU3 attaching NULL sched-domain. 
[   20.863812] CPU0 attaching sched-domain: 
[   20.863815]  domain 0: span 0-1 level SIBLING 
[   20.863818]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   20.863822]   domain 1: span 0-3 level MC 
[   20.863824]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.863831] CPU1 attaching sched-domain: 
[   20.863832]  domain 0: span 0-1 level SIBLING 
[   20.863834]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   20.863838]   domain 1: span 0-3 level MC 
[   20.863839]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   20.863844] CPU2 attaching sched-domain: 
[   20.863845]  domain 0: span 2-3 level SIBLING 
[   20.863847]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   20.863850]   domain 1: span 0-3 level MC 
[   20.863852]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   20.863856] CPU3 attaching sched-domain: 
[   20.863858]  domain 0: span 2-3 level SIBLING 
[   20.863859]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   20.863863]   domain 1: span 0-3 level MC 
[   20.863865]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.542943] CPU0 attaching NULL sched-domain. 
[   21.542949] CPU1 attaching NULL sched-domain. 
[   21.542953] CPU2 attaching NULL sched-domain. 
[   21.542956] CPU3 attaching NULL sched-domain. 
[   21.603294] CPU0 attaching sched-domain: 
[   21.603297]  domain 0: span 0-1 level SIBLING 
[   21.603300]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   21.603304]   domain 1: span 0-3 level MC 
[   21.603306]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.603312] CPU1 attaching sched-domain: 
[   21.603314]  domain 0: span 0-1 level SIBLING 
[   21.603315]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   21.603319]   domain 1: span 0-3 level MC 
[   21.603321]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.603325] CPU2 attaching sched-domain: 
[   21.603326]  domain 0: span 2-3 level SIBLING 
[   21.603328]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   21.603332]   domain 1: span 0-3 level MC 
[   21.603333]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.603337] CPU3 attaching sched-domain: 
[   21.603339]  domain 0: span 2-3 level SIBLING 
[   21.603340]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   21.603344]   domain 1: span 0-3 level MC 
[   21.603345]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.603679] CPU0 attaching NULL sched-domain. 
[   21.603681] CPU1 attaching NULL sched-domain. 
[   21.603683] CPU2 attaching NULL sched-domain. 
[   21.603685] CPU3 attaching NULL sched-domain. 
[   21.693143] CPU0 attaching sched-domain: 
[   21.693147]  domain 0: span 0-1 level SIBLING 
[   21.693149]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589) 
[   21.693153]   domain 1: span 0-3 level MC 
[   21.693155]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.693161] CPU1 attaching sched-domain: 
[   21.693162]  domain 0: span 0-1 level SIBLING 
[   21.693164]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[   21.693168]   domain 1: span 0-3 level MC 
[   21.693170]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178) 
[   21.693174] CPU2 attaching sched-domain: 
[   21.693175]  domain 0: span 2-3 level SIBLING 
[   21.693177]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589) 
[   21.693181]   domain 1: span 0-3 level MC 
[   21.693182]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[   21.693187] CPU3 attaching sched-domain: 
[   21.693188]  domain 0: span 2-3 level SIBLING 
[   21.693190]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589) 
[   21.693193]   domain 1: span 0-3 level MC 
[   21.693195]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178) 
[  105.843559] usb 3-3: new high speed USB device using xhci_hcd and address 0 
[  105.864010] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.864383] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.864758] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.865134] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep 
[  105.865453] usb 3-3: configuration #1 chosen from 1 choice 
[  105.921263] Initializing USB Mass Storage driver... 
[  105.921714] scsi6 : SCSI emulation for USB Mass Storage devices 
[  105.922412] usb-storage: device found at 2 
[  105.922418] usb-storage: waiting for device to settle before scanning 
[  105.922442] usbcore: registered new interface driver usb-storage 
[  105.922452] USB Mass Storage support registered. 
[  110.915082] usb-storage: device scan complete 
[  110.915479] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS 
[  110.916560] sd 6:0:0:0: Attached scsi generic sg2 type 0 
[  110.920861] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB) 
[  110.921790] sd 6:0:0:0: [sdb] Write Protect is off 
[  110.921802] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08 
[  110.921809] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.923539] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.923553]  sdb: sdb1 
[  110.927131] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  110.927142] sd 6:0:0:0: [sdb] Attached SCSI removable disk 

**~$ sudo lshw -C network **
[sudo] password for aquethys: 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 06 
       serial: 2c:27:d7:a7:b0:04 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:29 ioport:4000(size=256) memory:c1404000-c1404fff(prefetchable) memory:c1400000-c1403fff(prefetchable) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0d:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:c5500000-c5503fff 

Scan networks:
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 


Ubuntu Version:
Ubuntu 10.04.4 LTS 


Kernel/architecture
2.6.32-38-generic x86_64

---

### Post by mikewhatever on 2012-07-24
I suspect you simply need to install the driver. Hook up a cable, then check out System->Administration->Hardware Drivers.

---

### Post by aquethys on 2012-07-25
Hook up a cable to internet? 
Thanks for all your help thusfar!

---

### Post by mikewhatever on 2012-07-25
You are most welcome. In case there is no cable or internet, the following link has the steps for offline installation.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I am undecided on which driver to pick, because none actually list a BCM4727. Can you also post the output of 

**lspci -nn | grep -i net**. That should show the pci id.

---

