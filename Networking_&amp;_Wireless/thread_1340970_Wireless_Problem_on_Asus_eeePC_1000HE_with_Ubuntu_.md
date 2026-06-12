---
title: "Wireless Problem on Asus eeePC 1000HE with Ubuntu 9.04"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by hypnonebula on 2009-11-29
Hello everyone,

I used Wubi to install Ubuntu Jaunty in my netbook, everything works fine, except for some problems with sound (but that is another issue here). The internet works fine for a few months but suddenly, yesterday my computer are not able to connect to the wireless.

Thinking that it might be a problem with my wireless adapter, I used windows and the internet works fine. So I believe that it's either my wireless router is set with wrong configuration or my netbook is set with wrong configuration.

And one more thing, every time I tried to connect, I would be asked to enter the WEP key (which is normal). But what's puzzling is, after a few minutes, I will be asked again for the key. This time however, the spaces are prefilled, but with different key than what I entered before and what is stated on the wireless router.

Output from $ lspci and $ ifconfig

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01) 
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0) 

And Output from $ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:8c:47:7f:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4464 (4.4 KB)  TX bytes:4464 (4.4 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:22:43:71:c5:17  
          inet6 addr: fe80::222:43ff:fe71:c517/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2036 (2.0 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-71-C5-17-35-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

Output from $ lsmod 

```
Module                  Size  Used by 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat 
i915                   67844  2 
drm                    96424  3 i915 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge 
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp 
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         436148  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
ath9k                 280760  0 
snd_seq_midi           14336  0 
uvcvideo               63368  0 
mac80211              217592  1 ath9k 
snd_rawmidi            29696  1 snd_seq_midi 
compat_ioctl32          9344  1 uvcvideo 
videodev               41600  1 uvcvideo 
psmouse                61972  0 
pcspkr                 10496  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
serio_raw              13444  0 
v4l1_compat            21764  2 uvcvideo,videodev 
cfg80211               38288  1 mac80211 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
video                  25872  0 
btusb                  19608  2 
led_class              12036  1 ath9k 
output                 11008  1 video 
intel_agp              34108  1 
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
eeepc_laptop           18452  0 
agpgart                42696  3 drm,intel_agp 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm 
usbhid                 42336  0 
atl1e                  40212  0 
usb_storage            99648  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit
```

Output from $ dmesg

```
[    0.636670] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63 
[    0.636670] PCI: Not using MMCONFIG. 
[    0.636781] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5 
[    0.636786] PCI: Using configuration type 1 for base access 
[    0.641602] ACPI: EC: Look up EC in DSDT 
[    0.659084] ACPI: Interpreter enabled 
[    0.659093] ACPI: (supports S0 S1 S3 S4 S5) 
[    0.659137] ACPI: Using IOAPIC for interrupt routing 
[    0.659250] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63 
[    0.663100] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources 
[    0.663106] PCI: Using MMCONFIG for extended config space 
[    0.674200] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62 
[    0.674205] ACPI: EC: driver started in poll mode 
[    0.674492] ACPI: No dock devices found. 
[    0.674634] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.674749] pci 0000:00:02.0: reg 10 32bit mmio: [0xf7f00000-0xf7f7ffff] 
[    0.674758] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07] 
[    0.674766] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff] 
[    0.674773] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf7ec0000-0xf7efffff] 
[    0.674811] pci 0000:00:02.1: reg 10 32bit mmio: [0xf7f80000-0xf7ffffff] 
[    0.674937] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7eb8000-0xf7ebbfff] 
[    0.674985] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.674993] pci 0000:00:1b.0: PME# disabled 
[    0.675069] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.675076] pci 0000:00:1c.0: PME# disabled 
[    0.675155] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    0.675162] pci 0000:00:1c.1: PME# disabled 
[    0.675242] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold 
[    0.675249] pci 0000:00:1c.3: PME# disabled 
[    0.675322] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f] 
[    0.675395] pci 0000:00:1d.1: reg 20 io port: [0xd480-0xd49f] 
[    0.675471] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f] 
[    0.675543] pci 0000:00:1d.3: reg 20 io port: [0xd880-0xd89f] 
[    0.675619] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7eb7c00-0xf7eb7fff] 
[    0.675674] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
[    0.675681] pci 0000:00:1d.7: PME# disabled 
[    0.675848] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO 
[    0.675855] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO 
[    0.675912] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07] 
[    0.675923] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03] 
[    0.675934] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07] 
[    0.675944] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03] 
[    0.675955] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf] 
[    0.675984] pci 0000:00:1f.2: PME# supported from D3hot 
[    0.676007] pci 0000:00:1f.2: PME# disabled 
[    0.676172] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff] 
[    0.676186] pci 0000:03:00.0: reg 18 io port: [0xec00-0xec7f] 
[    0.676239] pci 0000:03:00.0: PME# supported from D3hot D3cold 
[    0.676248] pci 0000:03:00.0: PME# disabled 
[    0.676328] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff] 
[    0.676336] pci 0000:00:1c.1: bridge 32bit mmio: [0xfbf00000-0xfbffffff] 
[    0.676423] pci 0000:01:00.0: reg 10 64bit mmio: [0xfbef0000-0xfbefffff] 
[    0.676484] pci 0000:01:00.0: supports D1 
[    0.676488] pci 0000:01:00.0: PME# supported from D0 D1 D3hot 
[    0.676497] pci 0000:01:00.0: PME# disabled 
[    0.676584] pci 0000:00:1c.3: bridge 32bit mmio: [0xf8000000-0xfbefffff] 
[    0.676596] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf6ffffff] 
[    0.676664] pci 0000:00:1e.0: transparent bridge 
[    0.676709] bus 00 -> node 0 
[    0.676724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.677187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT] 
[    0.677370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT] 
[    0.699746] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[    0.700056] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15) 
[    0.700350] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15) 
[    0.700640] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[    0.700923] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[    0.701211] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[    0.701496] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[    0.701780] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[    0.702068] ACPI: WMI: Mapper loaded 
[    0.702190] SCSI subsystem initialized 
[    0.702190] libata version 3.00 loaded. 
[    0.702190] usbcore: registered new interface driver usbfs 
[    0.702190] usbcore: registered new interface driver hub 
[    0.702190] usbcore: registered new device driver usb 
[    0.702190] PCI: Using ACPI for IRQ routing 
[    0.708020] Bluetooth: Core ver 2.13 
[    0.708056] NET: Registered protocol family 31 
[    0.708056] Bluetooth: HCI device and connection manager initialized 
[    0.708056] Bluetooth: HCI socket layer initialized 
[    0.708056] NET: Registered protocol family 8 
[    0.708056] NET: Registered protocol family 20 
[    0.708076] NetLabel: Initializing 
[    0.708079] NetLabel:  domain hash size = 128 
[    0.708082] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.708105] NetLabel:  unlabeled traffic allowed by default 
[    0.708135] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.708144] hpet0: 3 comparators, 64-bit 14.318180 MHz counter 
[    0.712111] AppArmor: AppArmor Filesystem Enabled 
[    0.716023] Switched to high resolution mode on CPU 0 
[    0.716375] Switched to high resolution mode on CPU 1 
[    0.720025] pnp: PnP ACPI init 
[    0.720047] ACPI: bus type pnp registered 
[    0.723948] pnp: PnP ACPI: found 13 devices 
[    0.723955] ACPI: ACPI bus type pnp unregistered 
[    0.723962] PnPBIOS: Disabled by ACPI PNP 
[    0.723986] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved 
[    0.724026] system 00:08: ioport range 0x25c-0x25f has been reserved 
[    0.724032] system 00:08: ioport range 0x380-0x383 has been reserved 
[    0.724038] system 00:08: ioport range 0x400-0x41f has been reserved 
[    0.724043] system 00:08: ioport range 0x4d0-0x4d1 has been reserved 
[    0.724049] system 00:08: ioport range 0x800-0x87f has been reserved 
[    0.724055] system 00:08: ioport range 0x480-0x4bf has been reserved 
[    0.724061] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved 
[    0.724067] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved 
[    0.724073] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved 
[    0.724079] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved 
[    0.724085] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved 
[    0.724091] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved 
[    0.724104] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved 
[    0.724110] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved 
[    0.724120] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved 
[    0.724132] system 00:0c: iomem range 0x0-0x9ffff could not be reserved 
[    0.724138] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved 
[    0.724144] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved 
[    0.724150] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved 
[    0.759050] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04 
[    0.759056] pci 0000:00:1c.0:   IO window: disabled 
[    0.759065] pci 0000:00:1c.0:   MEM window: disabled 
[    0.759072] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    0.759083] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03 
[    0.759090] pci 0000:00:1c.1:   IO window: 0xe000-0xefff 
[    0.759099] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff 
[    0.759106] pci 0000:00:1c.1:   PREFETCH window: disabled 
[    0.759117] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01 
[    0.759121] pci 0000:00:1c.3:   IO window: disabled 
[    0.759130] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xfbefffff 
[    0.759138] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff 
[    0.759149] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05 
[    0.759153] pci 0000:00:1e.0:   IO window: disabled 
[    0.759162] pci 0000:00:1e.0:   MEM window: disabled 
[    0.759168] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.759196] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.759206] pci 0000:00:1c.0: setting latency timer to 64 
[    0.759222] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.759230] pci 0000:00:1c.1: setting latency timer to 64 
[    0.759244] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    0.759252] pci 0000:00:1c.3: setting latency timer to 64 
[    0.759264] pci 0000:00:1e.0: setting latency timer to 64 
[    0.759271] bus: 00 index 0 io port: [0x00-0xffff] 
[    0.759276] bus: 00 index 1 mmio: [0x000000-0xffffffff] 
[    0.759280] bus: 04 index 0 mmio: [0x0-0x0] 
[    0.759284] bus: 04 index 1 mmio: [0x0-0x0] 
[    0.759288] bus: 04 index 2 mmio: [0x0-0x0] 
[    0.759292] bus: 04 index 3 mmio: [0x0-0x0] 
[    0.759296] bus: 03 index 0 io port: [0xe000-0xefff] 
[    0.759301] bus: 03 index 1 mmio: [0xfbf00000-0xfbffffff] 
[    0.759305] bus: 03 index 2 mmio: [0x0-0x0] 
[    0.759309] bus: 03 index 3 mmio: [0x0-0x0] 
[    0.759312] bus: 01 index 0 mmio: [0x0-0x0] 
[    0.759317] bus: 01 index 1 mmio: [0xf8000000-0xfbefffff] 
[    0.759321] bus: 01 index 2 mmio: [0xf0000000-0xf6ffffff] 
[    0.759326] bus: 01 index 3 mmio: [0x0-0x0] 
[    0.759330] bus: 05 index 0 mmio: [0x0-0x0] 
[    0.759333] bus: 05 index 1 mmio: [0x0-0x0] 
[    0.759337] bus: 05 index 2 mmio: [0x0-0x0] 
[    0.759341] bus: 05 index 3 io port: [0x00-0xffff] 
[    0.759345] bus: 05 index 4 mmio: [0x000000-0xffffffff] 
[    0.759366] NET: Registered protocol family 2 
[    0.772126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.772625] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.773469] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.773913] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.773919] TCP reno registered 
[    0.780182] NET: Registered protocol family 1 
[    0.780399] checking if image is initramfs... it is 
[    1.766147] Freeing initrd memory: 7632k freed 
[    1.766554] cpufreq: No nForce2 chipset. 
[    1.766809] audit: initializing netlink socket (disabled) 
[    1.766848] type=2000 audit(1259501009.764:1): initialized 
[    1.780519] highmem bounce pool size: 64 pages 
[    1.780535] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.783261] VFS: Disk quotas dquot_6.5.1 
[    1.783381] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.784667] fuse init (API version 7.10) 
[    1.784842] msgmni has been set to 1724 
[    1.785195] alg: No test for stdrng (krng) 
[    1.785226] io scheduler noop registered 
[    1.785231] io scheduler anticipatory registered 
[    1.785235] io scheduler deadline registered 
[    1.785272] io scheduler cfq registered (default) 
[    1.785295] pci 0000:00:02.0: Boot video device 
[    1.788459] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    1.788519] pcieport-driver 0000:00:1c.0: found MSI capability 
[    1.788564] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X 
[    1.788584] pci_express 0000:00:1c.0:pcie00: allocate port service 
[    1.788616] pci_express 0000:00:1c.0:pcie02: allocate port service 
[    1.788642] pci_express 0000:00:1c.0:pcie03: allocate port service 
[    1.788738] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[    1.788794] pcieport-driver 0000:00:1c.1: found MSI capability 
[    1.788834] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X 
[    1.788854] pci_express 0000:00:1c.1:pcie00: allocate port service 
[    1.788880] pci_express 0000:00:1c.1:pcie02: allocate port service 
[    1.788905] pci_express 0000:00:1c.1:pcie03: allocate port service 
[    1.789018] pcieport-driver 0000:00:1c.3: setting latency timer to 64 
[    1.789073] pcieport-driver 0000:00:1c.3: found MSI capability 
[    1.789113] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X 
[    1.789133] pci_express 0000:00:1c.3:pcie00: allocate port service 
[    1.789166] pci_express 0000:00:1c.3:pcie02: allocate port service 
[    1.789196] pci_express 0000:00:1c.3:pcie03: allocate port service 
[    1.789314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    1.790240] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    1.790466] ACPI: AC Adapter [AC0] (on-line) 
[    1.790674] ACPI: Battery Slot [BAT0] (battery absent) 
[    1.790813] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0 
[    1.790819] ACPI: Power Button (FF) [PWRF] 
[    1.790928] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1 
[    1.792113] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[    1.800611] ACPI: Lid Switch [LID] 
[    1.800712] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2 
[    1.800718] ACPI: Sleep Button (CM) [SLPB] 
[    1.800805] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3 
[    1.800811] ACPI: Power Button (CM) [PWRB] 
[    1.801981] ACPI: SSDT 3F7AE180, 01FA (r1  PmRef  Cpu0Ist     3000 INTL 20051117) 
[    1.802690] ACPI: SSDT 3F7AE410, 0724 (r1  PmRef  Cpu0Cst     3001 INTL 20051117) 
[    1.803419] Monitor-Mwait will be used to enter C-1 state 
[    1.803426] Monitor-Mwait will be used to enter C-2 state 
[    1.803455] ACPI: CPU0 (power states: C1[C1] C2[C2]) 
[    1.803503] processor ACPI_CPU:00: registered as cooling_device0 
[    1.803512] ACPI: Processor [P001] (supports 8 throttling states) 
[    1.804215] ACPI: SSDT 3F7AE0B0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117) 
[    1.804855] ACPI: SSDT 3F7AE380, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117) 
[    1.805745] ACPI: CPU1 (power states: C1[C1] C2[C2]) 
[    1.805786] processor ACPI_CPU:01: registered as cooling_device1 
[    1.805794] ACPI: Processor [P002] (supports 8 throttling states) 
[    1.818894] thermal LNXTHERM:01: registered as thermal_zone0 
[    1.838211] ACPI: Thermal Zone [TZ00] (57 C) 
[    1.838304] isapnp: Scanning for PnP cards... 
[    2.191921] isapnp: No Plug & Play device found 
[    2.208474] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    2.210387] brd: module loaded 
[    2.211019] loop: module loaded 
[    2.211183] Fixed MDIO Bus: probed 
[    2.211194] PPP generic driver version 2.4.2 
[    2.211315] input: Macintosh mouse button emulation as /devices/virtual/input/input4 
[    2.211376] Driver 'sd' needs updating - please use bus_type methods 
[    2.211395] Driver 'sr' needs updating - please use bus_type methods 
[    2.211541] ata_piix 0000:00:1f.2: version 2.12 
[    2.211567] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.211574] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ] 
[    2.211637] ata_piix 0000:00:1f.2: setting latency timer to 64 
[    2.211810] scsi0 : ata_piix 
[    2.212020] scsi1 : ata_piix 
[    2.214752] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14 
[    2.214759] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15 
[    2.376772] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133 
[    2.376778] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    2.392723] ata1.00: configured for UDMA/133 
[    2.548274] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5 
[    2.548479] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB) 
[    2.548519] sd 0:0:0:0: [sda] Write Protect is off 
[    2.548525] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.548592] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.548728] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB) 
[    2.548767] sd 0:0:0:0: [sda] Write Protect is off 
[    2.548772] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.548838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.548847]  sda: sda1 sda2 sda3 sda4 
[    2.800785] sd 0:0:0:0: [sda] Attached SCSI disk 
[    2.800876] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    2.802236] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    2.802283] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.802330] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    2.802338] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    2.802455] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
[    2.806386] ehci_hcd 0000:00:1d.7: debug port 1 
[    2.806396] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    2.806423] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00 
[    2.820020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    2.820173] usb usb1: configuration #1 chosen from 1 choice 
[    2.820230] hub 1-0:1.0: USB hub found 
[    2.820244] hub 1-0:1.0: 8 ports detected 
[    2.820463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    2.820504] uhci_hcd: USB Universal Host Controller Interface driver 
[    2.820567] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.820580] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    2.820586] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    2.820676] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    2.820711] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400 
[    2.820856] usb usb2: configuration #1 chosen from 1 choice 
[    2.820914] hub 2-0:1.0: USB hub found 
[    2.820928] hub 2-0:1.0: 2 ports detected 
[    2.821094] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.821105] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    2.821111] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    2.821191] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
[    2.821238] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480 
[    2.821381] usb usb3: configuration #1 chosen from 1 choice 
[    2.821433] hub 3-0:1.0: USB hub found 
[    2.821446] hub 3-0:1.0: 2 ports detected 
[    2.821609] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    2.821623] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    2.821629] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    2.821711] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
[    2.821755] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800 
[    2.821911] usb usb4: configuration #1 chosen from 1 choice 
[    2.821963] hub 4-0:1.0: USB hub found 
[    2.821976] hub 4-0:1.0: 2 ports detected 
[    2.822137] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
[    2.822148] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[    2.822154] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    2.822238] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
[    2.822283] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880 
[    2.822431] usb usb5: configuration #1 chosen from 1 choice 
[    2.822483] hub 5-0:1.0: USB hub found 
[    2.822496] hub 5-0:1.0: 2 ports detected 
[    2.822753] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    2.855120] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    2.855133] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    2.856084] mice: PS/2 mouse device common for all mice 
[    2.876141] rtc_cmos 00:03: RTC can wake from S4 
[    2.876222] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    2.876266] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs 
[    2.876408] device-mapper: uevent: version 1.0.3 
[    2.876606] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email] 
[    2.876769] device-mapper: multipath: version 1.0.5 loaded 
[    2.876774] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    2.876956] EISA: Probing bus 0 at eisa.0 
[    2.876999] EISA: Detected 0 cards. 
[    2.877214] cpuidle: using governor ladder 
[    2.877385] cpuidle: using governor menu 
[    2.878406] TCP cubic registered 
[    2.878622] NET: Registered protocol family 10 
[    2.879427] lo: Disabled Privacy Extensions 
[    2.880161] NET: Registered protocol family 17 
[    2.880207] Bluetooth: L2CAP ver 2.11 
[    2.880211] Bluetooth: L2CAP socket layer initialized 
[    2.880216] Bluetooth: SCO (Voice Link) ver 0.6 
[    2.880219] Bluetooth: SCO socket layer initialized 
[    2.880296] Marking TSC unstable due to TSC halts in idle 
[    2.880333] Bluetooth: RFCOMM socket layer initialized 
[    2.880346] Bluetooth: RFCOMM TTY layer initialized 
[    2.880349] Bluetooth: RFCOMM ver 1.10 
[    2.881311] Using IPI No-Shortcut mode 
[    2.881500] registered taskstats version 1 
[    2.881692]   Magic number: 1:412:383 
[    2.881709] usb usb1: hash matches 
[    2.881812] rtc_cmos 00:03: setting system clock to 2009-11-29 13:23:32 UTC (1259501012) 
[    2.881819] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    2.881823] EDD information not available. 
[    2.882177] Freeing unused kernel memory: 532k freed 
[    2.882458] Write protecting the kernel text: 4120k 
[    2.882555] Write protecting the kernel read-only data: 1524k 
[    2.899364] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5 
[    3.133063] usb 1-2: new high speed USB device using ehci_hcd and address 2 
[    3.290575] usb 1-2: configuration #1 chosen from 1 choice 
[    3.400610] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    3.400637] ATL1E 0000:03:00.0: setting latency timer to 64 
[    3.569066] usb 1-8: new high speed USB device using ehci_hcd and address 5 
[    3.746206] usb 1-8: configuration #1 chosen from 1 choice 
[    3.851261] Initializing USB Mass Storage driver... 
[    3.853405] scsi2 : SCSI emulation for USB Mass Storage devices 
[    3.853868] usb-storage: device found at 2 
[    3.853875] usb-storage: waiting for device to settle before scanning 
[    3.853934] usbcore: registered new interface driver usb-storage 
[    3.853944] USB Mass Storage support registered. 
[    4.008097] usb 3-2: new low speed USB device using uhci_hcd and address 2 
[    4.183536] usb 3-2: configuration #1 chosen from 1 choice 
[    4.198405] usbcore: registered new interface driver hiddev 
[    4.213919] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6 
[    4.216255] generic-usb 0003:046D:C052.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1d.1-2/input0 
[    4.216314] usbcore: registered new interface driver usbhid 
[    4.216325] usbhid: v2.6:USB HID core driver 
[    4.424095] usb 5-1: new full speed USB device using uhci_hcd and address 2 
[    4.599601] usb 5-1: configuration #1 chosen from 1 choice 
[    5.089758] EXT3-fs: INFO: recovery required on readonly filesystem. 
[    5.089768] EXT3-fs: write access will be enabled during recovery. 
[    6.470243] kjournald starting.  Commit interval 5 seconds 
[    6.470281] EXT3-fs: recovery complete. 
[    6.470770] EXT3-fs: mounted filesystem with ordered data mode. 
[    8.853360] usb-storage: device scan complete 
[    8.853969] scsi 2:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4 
[    8.855697] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB) 
[    8.856303] sd 2:0:0:0: [sdb] Write Protect is off 
[    8.856310] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00 
[    8.856314] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[    8.857168] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB) 
[    8.857818] sd 2:0:0:0: [sdb] Write Protect is off 
[    8.857828] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00 
[    8.857835] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[    8.857849]  sdb: sdb1 
[    8.876138] sd 2:0:0:0: [sdb] Attached SCSI disk 
[    8.876265] sd 2:0:0:0: Attached scsi generic sg1 type 0 
[   11.630772] udev: starting version 141 
[   11.865477] eeepc: Eee PC Hotkey Driver 
[   11.867393] eeepc: Hotkey init flags 0x41 
[   11.867607] eeepc: Get control methods supported: 0x101713 
[   11.867888] input: Asus EeePC extra buttons as /devices/virtual/input/input7 
[   11.928802] Linux agpgart interface v0.103 
[   12.165812] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input8 
[   12.197224] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   12.328176] agpgart-intel 0000:00:00.0: Intel 945GME Chipset 
[   12.328450] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
[   12.331233] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000 
[   12.368279] intel_rng: FWH not detected 
[   12.434973] cfg80211: Calling CRDA to update world regulatory domain 
[   12.541176] Bluetooth: Generic Bluetooth USB driver ver 0.3 
[   12.541488] usbcore: registered new interface driver btusb 
[   12.955718] input: PC Speaker as /devices/platform/pcspkr/input/input9 
[   12.994987] cfg80211: World regulatory domain updated: 
[   12.994995] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   12.995001] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.995007] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.995012] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.995017] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.995022] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   13.122071] Linux video capture interface: v2.00 
[   13.142868] iTCO_vendor_support: vendor-support=0 
[   13.317781] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume 
[   13.339393] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05 
[   13.339694] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x0860) 
[   13.339850] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   13.486023] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071) 
[   13.487842] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input10 
[   13.489717] usbcore: registered new interface driver uvcvideo 
[   13.489859] USB Video Class driver (v0.1.0) 
[   13.625434] ath9k: 0.1 
[   13.625524] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   13.625544] ath9k 0000:01:00.0: setting latency timer to 64 
[   13.883044] psmouse serio1: ID: 10 00 64<7>phy0: Selected rate control algorithm 'ath9k_rate_control' 
[   14.092957] elantech.c: assuming hardware version 2, firmware version 2.48 
[   14.166634] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64. 
[   14.239498] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   14.239594] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   14.366485] Registered led device: ath9k-phy0:radio 
[   14.366532] Registered led device: ath9k-phy0:assoc 
[   14.366575] Registered led device: ath9k-phy0:tx 
[   14.366617] Registered led device: ath9k-phy0:rx 
[   14.367575] phy0: Atheros 9280: mem=0xf7f20000, irq=19 
[   14.379178] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input11 
[   16.706981] lp: driver loaded but no devices found 
[   17.449996] EXT3 FS on loop0, internal journal 
[   25.595058] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   26.079424] type=1505 audit(1259497435.694:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2166 
[   26.187079] type=1505 audit(1259497435.802:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2170 
[   26.187356] type=1505 audit(1259497435.802:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2170 
[   26.187480] type=1505 audit(1259497435.802:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2170 
[   26.187581] type=1505 audit(1259497435.802:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2170 
[   26.492347] type=1505 audit(1259497436.110:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2175 
[   26.492720] type=1505 audit(1259497436.110:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2175 
[   26.554402] type=1505 audit(1259497436.170:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2179 
[   30.846500] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   30.846509] Bluetooth: BNEP filters: protocol multicast 
[   30.888095] Bridge firewalling registered 
[   32.072558] ppdev: user-space parallel port driver 
[   33.463276] [drm] Initialized drm 1.1.0 20060810 
[   33.476699] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   33.476713] pci 0000:00:02.0: setting latency timer to 64 
[   33.477649] [drm] Initialized i915 1.6.0 20080730 on minor 0 
[   33.479902] [drm:i915_setparam] *ERROR* unknown parameter 4 
[   33.479970] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   34.635843] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   36.384243] ATL1E 0000:03:00.0: irq 2300 for MSI/MSI-X 
[   36.384932] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   36.408876] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   77.207304] wlan0: direct probe to AP 00:24:d2:3e:1c:e7 try 1 
[   77.404050] wlan0: direct probe to AP 00:24:d2:3e:1c:e7 try 2 
[   77.604628] wlan0: direct probe to AP 00:24:d2:3e:1c:e7 try 3 
[   77.808067] wlan0: direct probe to AP 00:24:d2:3e:1c:e7 timed out 
[   87.965337] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[   88.164087] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[   88.364087] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[   88.564086] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out 
[   98.001067] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[   98.009403] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[   98.208132] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[   98.408095] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[   98.609107] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out 
[  108.945948] wlan0 direct probe responded 
[  108.945964] wlan0: authenticate with AP 00:24:d2:24:e8:e3 
[  109.144117] wlan0: authenticate with AP 00:24:d2:24:e8:e3 
[  109.146100] wlan0: authenticated 
[  109.146112] wlan0: associate with AP 00:24:d2:24:e8:e3 
[  109.344123] wlan0: associate with AP 00:24:d2:24:e8:e3 
[  109.548055] wlan0: associate with AP 00:24:d2:24:e8:e3 
[  109.744124] wlan0: association with AP 00:24:d2:24:e8:e3 timed out 
[  115.384096] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  115.588107] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  115.788060] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  115.984059] wlan0: authentication with AP 00:02:cf:a9:51:bc timed out 
[  125.392506] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  125.400783] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  125.400866] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  125.596153] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  125.796122] wlan0: authenticate with AP 00:02:cf:a9:51:bc 
[  125.997086] wlan0: authentication with AP 00:02:cf:a9:51:bc timed out 
[  153.572187] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  153.772074] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[  153.972085] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[  154.172079] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out 
[  164.505359] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  164.513970] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  164.712705] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[  164.913087] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[  165.113106] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out 
[  181.166159] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  181.174860] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  181.374133] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[  181.573112] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[  181.773119] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out 
[  191.887666] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 1 
[  192.085085] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 2 
[  192.285072] wlan0: direct probe to AP 00:24:d2:24:e8:e3 try 3 
[  192.485086] wlan0: direct probe to AP 00:24:d2:24:e8:e3 timed out
```

Network Configuration

```
*-network               
       description: Ethernet interface 
       product: L1e Gigabit Ethernet Adapter 
       vendor: Attansic Technology Corp. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: b0 
       serial: 00:24:8c:47:7f:f1 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair 
  *-network 
       description: Wireless interface 
       product: AR928X Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:22:43:71:c5:17 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 5a:48:99:3c:ae:c3 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```

Kernel/architecture

```
2.6.28-16-generic i686
```

Restarting the network
```
* Reconfiguring network interfaces...                                                                                [ OK ]
```

---

### Post by hypnonebula on 2009-12-01
I didn't actually find the problems, but an upgrade to Karmic Koala solves everything.

---

