---
title: "Extremely slow Internet Connection Ubuntu 9.10 Dell Inspiron 1100"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Mokacoffay on 2010-03-02
Hello once again everyone, I'm very new to Ubuntu in general and I just got my internet working through the wireless card with some help. However, my downloading speeds are beyond extremely slow.  While I type on this computer, I am downloading things @ ~500-700kb/s, but when I try to download the package updates etc for my Ubuntu 9.10 laptop, It downloads @ ~ 4k b/s- which is UNBEARABLY slow, putting me at 14h left to complete a 200 mb update.  Could anybody give me a hand here? 

                                                                     
                                                                     
                                                                     
                                             
**Dell Inspiron 1100**

**Ubuntu 9.10**

**$ lspci**

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**$ ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:0d:56:af:b9:ea  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:49:7f:b7  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe49:7fb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7005315 (7.0 MB)  TX bytes:407169 (407.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-49-7F-B7-34-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:7C:C6:39   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**$ lsmod**

Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
nls_utf8                1568  1 
isofs                  31620  1 
usb_storage            52544  2 
binfmt_misc             8356  1 
ppdev                   6688  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
arc4                    1660  2 
ecb                     2524  2 
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
snd_intel8x0           30168  2 
led_class               4096  1 b43
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
dell_wmi                2564  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
joydev                 10272  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
yenta_socket           24200  2 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
lp                      8964  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
dcdbas                  7292  0 
serio_raw               5280  0 
soundcore               7264  1 snd
parport                35340  2 ppdev,lp
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
b44                    28684  0 
ssb                    35300  2 b43,b44
mii                     5212  1 b44
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

**$ dmesg**

[    0.164429] system 00:0b: ioport range 0x5bc0-0x5bdf has been reserved
[    0.164435] system 00:0b: ioport range 0x5fb0-0x5fbb has been reserved
[    0.164442] system 00:0b: ioport range 0x5fc0-0x5fdf has been reserved
[    0.164449] system 00:0b: ioport range 0x63b0-0x63bb has been reserved
[    0.164455] system 00:0b: ioport range 0x63c0-0x63df has been reserved
[    0.164462] system 00:0b: ioport range 0x67b0-0x67bb has been reserved
[    0.164468] system 00:0b: ioport range 0x67c0-0x67df has been reserved
[    0.164475] system 00:0b: ioport range 0x6bb0-0x6bbb has been reserved
[    0.164481] system 00:0b: ioport range 0x6bc0-0x6bdf has been reserved
[    0.164488] system 00:0b: ioport range 0x6fb0-0x6fbb has been reserved
[    0.164494] system 00:0b: ioport range 0x6fc0-0x6fdf has been reserved
[    0.164501] system 00:0b: ioport range 0x73b0-0x73bb has been reserved
[    0.164508] system 00:0b: ioport range 0x73c0-0x73df has been reserved
[    0.164515] system 00:0b: ioport range 0x77b0-0x77bb has been reserved
[    0.164521] system 00:0b: ioport range 0x77c0-0x77df has been reserved
[    0.164528] system 00:0b: ioport range 0x7bb0-0x7bbb has been reserved
[    0.164535] system 00:0b: ioport range 0x7bc0-0x7bdf has been reserved
[    0.164541] system 00:0b: ioport range 0x7fb0-0x7fbb has been reserved
[    0.164548] system 00:0b: ioport range 0x7fc0-0x7fdf has been reserved
[    0.164555] system 00:0b: ioport range 0x83b0-0x83bb has been reserved
[    0.164562] system 00:0b: ioport range 0x83c0-0x83df has been reserved
[    0.164569] system 00:0b: ioport range 0x87b0-0x87bb has been reserved
[    0.164577] system 00:0b: ioport range 0x87c0-0x87df has been reserved
[    0.164584] system 00:0b: ioport range 0x8bb0-0x8bbb has been reserved
[    0.164591] system 00:0b: ioport range 0x8bc0-0x8bdf has been reserved
[    0.164599] system 00:0b: ioport range 0x8fb0-0x8fbb has been reserved
[    0.164607] system 00:0b: ioport range 0x8fc0-0x8fdf has been reserved
[    0.164615] system 00:0b: ioport range 0x93b0-0x93bb has been reserved
[    0.164622] system 00:0b: ioport range 0x93c0-0x93df has been reserved
[    0.164630] system 00:0b: ioport range 0x97b0-0x97bb has been reserved
[    0.164638] system 00:0b: ioport range 0x97c0-0x97df has been reserved
[    0.164645] system 00:0b: ioport range 0x9bb0-0x9bbb has been reserved
[    0.164653] system 00:0b: ioport range 0x9bc0-0x9bdf has been reserved
[    0.164661] system 00:0b: ioport range 0x9fb0-0x9fbb has been reserved
[    0.164668] system 00:0b: ioport range 0x9fc0-0x9fdf has been reserved
[    0.164676] system 00:0b: ioport range 0xa3b0-0xa3bb has been reserved
[    0.164683] system 00:0b: ioport range 0xa3c0-0xa3df has been reserved
[    0.164691] system 00:0b: ioport range 0xa7b0-0xa7bb has been reserved
[    0.164699] system 00:0b: ioport range 0xa7c0-0xa7df has been reserved
[    0.164707] system 00:0b: ioport range 0xabb0-0xabbb has been reserved
[    0.164715] system 00:0b: ioport range 0xabc0-0xabdf has been reserved
[    0.164722] system 00:0b: ioport range 0xafb0-0xafbb has been reserved
[    0.164730] system 00:0b: ioport range 0xafc0-0xafdf has been reserved
[    0.164738] system 00:0b: ioport range 0xb3b0-0xb3bb has been reserved
[    0.164746] system 00:0b: ioport range 0xb3c0-0xb3df has been reserved
[    0.164754] system 00:0b: ioport range 0xb7b0-0xb7bb has been reserved
[    0.164763] system 00:0b: ioport range 0xb7c0-0xb7df has been reserved
[    0.164771] system 00:0b: ioport range 0xbbb0-0xbbbb has been reserved
[    0.164779] system 00:0b: ioport range 0xbbc0-0xbbdf has been reserved
[    0.164787] system 00:0b: ioport range 0xbfb0-0xbfbb has been reserved
[    0.164796] system 00:0b: ioport range 0xbfc0-0xbfdf has been reserved
[    0.164804] system 00:0b: ioport range 0xc3b0-0xc3bb has been reserved
[    0.164812] system 00:0b: ioport range 0xc3c0-0xc3df has been reserved
[    0.164821] system 00:0b: ioport range 0xc7b0-0xc7bb has been reserved
[    0.164829] system 00:0b: ioport range 0xc7c0-0xc7df has been reserved
[    0.164837] system 00:0b: ioport range 0xcbb0-0xcbbb has been reserved
[    0.164846] system 00:0b: ioport range 0xcbc0-0xcbdf has been reserved
[    0.164854] system 00:0b: ioport range 0xcfb0-0xcfbb has been reserved
[    0.164863] system 00:0b: ioport range 0xcfc0-0xcfdf has been reserved
[    0.164883] system 00:0b: ioport range 0xf3b0-0xf3bb has been reserved
[    0.164892] system 00:0b: ioport range 0xf3c0-0xf3df has been reserved
[    0.164901] system 00:0b: ioport range 0xf7b0-0xf7bb has been reserved
[    0.164910] system 00:0b: ioport range 0xf7c0-0xf7df has been reserved
[    0.164921] system 00:0b: ioport range 0xfbb0-0xfbbb has been reserved
[    0.164930] system 00:0b: ioport range 0xfbc0-0xfbdf has been reserved
[    0.164939] system 00:0b: ioport range 0xffb0-0xffbb has been reserved
[    0.164948] system 00:0b: ioport range 0xffc0-0xffdf has been reserved
[    0.199886] AppArmor: AppArmor Filesystem Enabled
[    0.199949] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.199954] pci 0000:02:04.0:   IO window: 0x00d000-0x00d0ff
[    0.199962] pci 0000:02:04.0:   IO window: 0x00d400-0x00d4ff
[    0.199969] pci 0000:02:04.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.199977] pci 0000:02:04.0:   MEM window: 0xf8000000-0xfbffffff
[    0.199984] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.200018] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.200027] pci 0000:00:1e.0:   MEM window: 0xf8000000-0xfdffffff
[    0.200035] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.200058] pci 0000:00:1e.0: setting latency timer to 64
[    0.200071] pci 0000:02:04.0: enabling device (0000 -> 0003)
[    0.200383] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.200390] PCI: setting IRQ 11 as level-triggered
[    0.200398] pci 0000:02:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.200413] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.200418] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.200424] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.200429] pci_bus 0000:02: resource 1 mem: [0xf8000000-0xfdffffff]
[    0.200434] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.200439] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.200444] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.200450] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.200454] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.200459] pci_bus 0000:03: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.200464] pci_bus 0000:03: resource 3 mem: [0xf8000000-0xfbffffff]
[    0.200526] NET: Registered protocol family 2
[    0.200686] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.201132] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.201203] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.201276] TCP: Hash tables configured (established 8192 bind 8192)
[    0.201283] TCP reno registered
[    0.201522] NET: Registered protocol family 1
[    0.201662] Trying to unpack rootfs image as initramfs...
[    0.540777] Freeing initrd memory: 7463k freed
[    0.556085] cpufreq-nforce2: No nForce2 chipset.
[    0.556140] Scanning for low memory corruption every 60 seconds
[    0.556354] audit: initializing netlink socket (disabled)
[    0.556384] type=2000 audit(1267545051.556:1): initialized
[    0.566436] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.568982] VFS: Disk quotas dquot_6.5.2
[    0.569121] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.570400] fuse init (API version 7.12)
[    0.570620] msgmni has been set to 486
[    0.571206] alg: No test for stdrng (krng)
[    0.571260] io scheduler noop registered
[    0.571265] io scheduler anticipatory registered
[    0.571269] io scheduler deadline registered
[    0.571402] io scheduler cfq registered (default)
[    0.571431] pci 0000:00:02.0: Boot video device
[    0.571698] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.571751] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.572371] ACPI: AC Adapter [AC] (on-line)
[    0.572530] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.572945] ACPI: Lid Switch [LID]
[    0.573049] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.573060] ACPI: Power Button [PBTN]
[    0.573146] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.573153] ACPI: Sleep Button [SBTN]
[    0.573710] processor LNXCPU:00: registered as cooling_device0
[    0.573719] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.579803] thermal LNXTHERM:01: registered as thermal_zone0
[    0.579825] ACPI: Thermal Zone [THM] (25 C)
[    0.604184] isapnp: Scanning for PnP cards...
[    0.700044] Switched to high resolution mode on CPU 0
[    0.923871] ACPI: Battery Slot [BAT0] (battery present)
[    0.967500] isapnp: No Plug & Play device found
[    0.970663] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.971608] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    0.971616] PCI: setting IRQ 7 as level-triggered
[    0.971624] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    0.971636] serial 0000:00:1f.6: PCI INT B disabled
[    0.973708] brd: module loaded
[    0.974804] loop: module loaded
[    0.975029] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.975281] ata_piix 0000:00:1f.1: version 2.13
[    0.975303] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.975317] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.975398] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.975591] scsi0 : ata_piix
[    0.975861] scsi1 : ata_piix
[    0.976218] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.976225] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.978396] Fixed MDIO Bus: probed
[    0.978487] PPP generic driver version 2.4.2
[    0.978748] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.979121] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.979131] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.979162] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.979168] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.979345] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.983286] ehci_hcd 0000:00:1d.7: debug port 1
[    0.983297] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.983722] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6f7fc00
[    0.996043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.996246] usb usb1: configuration #1 chosen from 1 choice
[    0.996324] hub 1-0:1.0: USB hub found
[    0.996352] hub 1-0:1.0: 6 ports detected
[    0.996531] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.996593] uhci_hcd: USB Universal Host Controller Interface driver
[    0.996694] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.996715] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.996722] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.996845] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.996888] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.997079] usb usb2: configuration #1 chosen from 1 choice
[    0.997172] hub 2-0:1.0: USB hub found
[    0.997205] hub 2-0:1.0: 2 ports detected
[    0.997674] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.997683] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.997703] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.997710] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.997856] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.997899] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.998103] usb usb3: configuration #1 chosen from 1 choice
[    0.998181] hub 3-0:1.0: USB hub found
[    0.998208] hub 3-0:1.0: 2 ports detected
[    0.998670] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.998679] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.998699] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.998706] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.998837] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.998881] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.999075] usb usb4: configuration #1 chosen from 1 choice
[    0.999161] hub 4-0:1.0: USB hub found
[    0.999193] hub 4-0:1.0: 2 ports detected
[    0.999437] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.999618] i8042.c: Warning: Keylock active.
[    1.002175] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.002190] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.002397] mice: PS/2 mouse device common for all mice
[    1.002798] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.002829] rtc0: alarms up to one day, 114 bytes nvram
[    1.003090] device-mapper: uevent: version 1.0.3
[    1.003394] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.003716] device-mapper: multipath: version 1.1.0 loaded
[    1.003724] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.004212] EISA: Probing bus 0 at eisa.0
[    1.004247] EISA: Detected 0 cards.
[    1.004448] cpuidle: using governor ladder
[    1.004453] cpuidle: using governor menu
[    1.005307] TCP cubic registered
[    1.005602] NET: Registered protocol family 10
[    1.006351] lo: Disabled Privacy Extensions
[    1.006800] NET: Registered protocol family 17
[    1.006866] Bluetooth: L2CAP ver 2.13
[    1.006870] Bluetooth: L2CAP socket layer initialized
[    1.006876] Bluetooth: SCO (Voice Link) ver 0.6
[    1.006879] Bluetooth: SCO socket layer initialized
[    1.007045] Bluetooth: RFCOMM TTY layer initialized
[    1.007054] Bluetooth: RFCOMM socket layer initialized
[    1.007058] Bluetooth: RFCOMM ver 1.11
[    1.007128] Using IPI No-Shortcut mode
[    1.007316] PM: Resume from disk failed.
[    1.007356] registered taskstats version 1
[    1.007542]   Magic number: 2:508:840
[    1.007670] rtc_cmos 00:06: setting system clock to 2010-03-02 15:50:52 UTC (1267545052)
[    1.007678] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.007681] EDD information not available.
[    1.008193] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.100059] hub 2-0:1.0: over-current change on port 1
[    1.144705] ata2.00: ATA-6: IC25N020ATMR04-0, MO1OAD0A, max UDMA/100
[    1.144711] ata2.00: 39070080 sectors, multi 8: LBA48 
[    1.160491] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4240N, E112, max UDMA/33
[    1.160956] ata2.00: configured for UDMA/100
[    1.176255] ata1.00: configured for UDMA/33
[    1.181262] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4240N E112 PQ: 0 ANSI: 5
[    1.192393] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.192402] Uniform CD-ROM driver Revision: 3.20
[    1.192591] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.192733] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.193007] scsi 1:0:0:0: Direct-Access     ATA      IC25N020ATMR04-0 MO1O PQ: 0 ANSI: 5
[    1.193293] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.193457] sd 1:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.193693] sd 1:0:0:0: [sda] Write Protect is off
[    1.193700] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.193820] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.194399]  sda: sda1 sda2 < sda5 >
[    1.261013] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.261046] Freeing unused kernel memory: 540k freed
[    1.262056] Write protecting the kernel text: 4568k
[    1.262097] Write protecting the kernel read-only data: 1836k
[    1.659642] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/input/input5
[    1.659732] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.721173] Linux agpgart interface v0.103
[    1.726356] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    1.726531] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[    1.729108] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    2.001232] [drm] Initialized drm 1.1.0 20060810
[    2.027757] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.027769] i915 0000:00:02.0: setting latency timer to 64
[    2.058603] b44 0000:02:01.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    2.173742] [drm] DAC-5: set mode 640x480 0
[    2.637165] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[    2.637228] b44.c:v2.0
[    2.646163] i2c-adapter i2c-1: unable to read EDID block.
[    2.646175] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.655748] [drm] fb0: inteldrmfb frame buffer device
[    2.655769] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.657122] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:af:b9:ea
[    2.799688] render error detected, EIR: 0x00000010
[    2.799696] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.799710] render error detected, EIR: 0x00000010
[    2.806718] [drm] LVDS-7: set mode 1024x768 a
[    2.972789] Console: switching to colour frame buffer device 128x48
[    3.425193] PM: Starting manual resume from disk
[    3.425203] PM: Resume from partition 8:5
[    3.425206] PM: Checking hibernation image.
[    3.425485] PM: Resume from disk failed.
[    3.466578] EXT4-fs (sda1): barriers enabled
[    3.483326] kjournald2 starting: pid 316, dev sda1:8, commit interval 5 seconds
[    3.483367] EXT4-fs (sda1): delayed allocation enabled
[    3.483373] EXT4-fs: file extents enabled
[    3.486047] EXT4-fs: mballoc enabled
[    3.486091] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.607548] type=1505 audit(1267545056.098:2): operation="profile_load" pid=339 name=/usr/share/gdm/guest-session/Xsession
[    4.613255] type=1505 audit(1267545056.104:3): operation="profile_load" pid=340 name=/sbin/dhclient3
[    4.614035] type=1505 audit(1267545056.104:4): operation="profile_load" pid=340 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.614493] type=1505 audit(1267545056.104:5): operation="profile_load" pid=340 name=/usr/lib/connman/scripts/dhclient-script
[    4.680407] type=1505 audit(1267545056.172:6): operation="profile_load" pid=341 name=/usr/bin/evince
[    4.692627] type=1505 audit(1267545056.184:7): operation="profile_load" pid=341 name=/usr/bin/evince-previewer
[    4.699847] type=1505 audit(1267545056.188:8): operation="profile_load" pid=341 name=/usr/bin/evince-thumbnailer
[    4.731984] type=1505 audit(1267545056.220:9): operation="profile_load" pid=343 name=/usr/lib/cups/backend/cups-pdf
[    4.733026] type=1505 audit(1267545056.224:10): operation="profile_load" pid=343 name=/usr/sbin/cupsd
[    6.540538] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
[    6.733468] udev: starting version 147
[    7.006132] EXT4-fs (sda1): internal journal on sda1:8
[    7.488449] intel_rng: FWH not detected
[    7.541585] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.755285] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.855374] lp: driver loaded but no devices found
[    9.970816] yenta_cardbus 0000:02:04.0: CardBus bridge found [1028:0149]
[    9.970841] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[    9.970846] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[    9.970854] yenta_cardbus 0000:02:04.0: TI: mfunc 0x00001002, devctl 0x64
[   10.176102] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   10.200691] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0478, PCI irq 11
[   10.200699] yenta_cardbus 0000:02:04.0: Socket status: 30000020
[   10.200706] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   10.200724] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   10.200731] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   10.201800] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   10.201806] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x13ffffff
[   10.229278] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   10.328794] dell-wmi: No known WMI GUID found
[   10.848356] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   10.848401] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   10.848660] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   10.848681] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.848698] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   10.912187] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   11.090936] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.092330] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   11.092934] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.093098] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.094072] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.117123] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[   11.117195] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.173291] cfg80211: Calling CRDA to update world regulatory domain
[   11.350658] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   11.594875] cfg80211: World regulatory domain updated:
[   11.594885] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.594891] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.594896] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.594901] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.594906] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.594910] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.661005] phy0: Selected rate control algorithm 'minstrel'
[   11.662229] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   11.944101] intel8x0_measure_ac97_clock: measured 55154 usecs (2657 samples)
[   11.944108] intel8x0: clocking to 48000
[   13.396213] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.236470] __ratelimit: 3 callbacks suppressed
[   14.236477] type=1505 audit(1267566665.728:12): operation="profile_replace" pid=736 name=/usr/share/gdm/guest-session/Xsession
[   14.241459] type=1505 audit(1267566665.732:13): operation="profile_replace" pid=737 name=/sbin/dhclient3
[   14.242262] type=1505 audit(1267566665.732:14): operation="profile_replace" pid=737 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.242719] type=1505 audit(1267566665.732:15): operation="profile_replace" pid=737 name=/usr/lib/connman/scripts/dhclient-script
[   14.259685] type=1505 audit(1267566665.748:16): operation="profile_replace" pid=738 name=/usr/bin/evince
[   14.273074] type=1505 audit(1267566665.764:17): operation="profile_replace" pid=738 name=/usr/bin/evince-previewer
[   14.281351] type=1505 audit(1267566665.772:18): operation="profile_replace" pid=738 name=/usr/bin/evince-thumbnailer
[   14.296568] type=1505 audit(1267566665.788:19): operation="profile_replace" pid=740 name=/usr/lib/cups/backend/cups-pdf
[   14.297547] type=1505 audit(1267566665.788:20): operation="profile_replace" pid=740 name=/usr/sbin/cupsd
[   14.302898] type=1505 audit(1267566665.792:21): operation="profile_replace" pid=741 name=/usr/sbin/tcpdump
[   18.055753] ppdev: user-space parallel port driver
[   19.015721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.104125] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[   19.570286] b43 ssb1:0: firmware: requesting b43/pcm5.fw
[   19.735404] b43 ssb1:0: firmware: requesting b43/b0g0initvals5.fw
[   20.265540] b43 ssb1:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.396060] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.448476] Registered led device: b43-phy0::tx
[   20.448543] Registered led device: b43-phy0::rx
[   20.448593] Registered led device: b43-phy0::radio
[   20.449029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.326940] i2c-adapter i2c-0: unable to read EDID block.
[   22.326950] i915 0000:00:02.0: VGA-1: no EDID data
[   22.336671] i2c-adapter i2c-0: unable to read EDID block.
[   22.336681] i915 0000:00:02.0: VGA-1: no EDID data
[   22.342791] i2c-adapter i2c-1: unable to read EDID block.
[   22.342801] i915 0000:00:02.0: LVDS-1: no EDID data
[   22.357172] i2c-adapter i2c-0: unable to read EDID block.
[   22.357185] i915 0000:00:02.0: VGA-1: no EDID data
[   22.378254] i2c-adapter i2c-0: unable to read EDID block.
[   22.378266] i915 0000:00:02.0: VGA-1: no EDID data
[   22.441008] i2c-adapter i2c-1: unable to read EDID block.
[   22.441018] i915 0000:00:02.0: LVDS-1: no EDID data
[   27.550769] i2c-adapter i2c-0: unable to read EDID block.
[   27.550781] i915 0000:00:02.0: VGA-1: no EDID data
[   27.561661] i2c-adapter i2c-0: unable to read EDID block.
[   27.561671] i915 0000:00:02.0: VGA-1: no EDID data
[   27.573321] i2c-adapter i2c-1: unable to read EDID block.
[   27.573329] i915 0000:00:02.0: LVDS-1: no EDID data
[   27.592710] i2c-adapter i2c-0: unable to read EDID block.
[   27.592720] i915 0000:00:02.0: VGA-1: no EDID data
[   27.605389] i2c-adapter i2c-0: unable to read EDID block.
[   27.605401] i915 0000:00:02.0: VGA-1: no EDID data
[   27.613447] i2c-adapter i2c-1: unable to read EDID block.
[   27.613459] i915 0000:00:02.0: LVDS-1: no EDID data
[   27.665991] i2c-adapter i2c-0: unable to read EDID block.
[   27.666003] i915 0000:00:02.0: VGA-1: no EDID data
[   27.675947] i2c-adapter i2c-0: unable to read EDID block.
[   27.675958] i915 0000:00:02.0: VGA-1: no EDID data
[   27.684390] i2c-adapter i2c-1: unable to read EDID block.
[   27.684400] i915 0000:00:02.0: LVDS-1: no EDID data
[   50.926966] i2c-adapter i2c-0: unable to read EDID block.
[   50.926978] i915 0000:00:02.0: VGA-1: no EDID data
[   50.936781] i2c-adapter i2c-0: unable to read EDID block.
[   50.936790] i915 0000:00:02.0: VGA-1: no EDID data
[   50.944590] i2c-adapter i2c-1: unable to read EDID block.
[   50.944602] i915 0000:00:02.0: LVDS-1: no EDID data
[   50.979026] i2c-adapter i2c-0: unable to read EDID block.
[   50.979037] i915 0000:00:02.0: VGA-1: no EDID data
[   51.006386] i2c-adapter i2c-0: unable to read EDID block.
[   51.006397] i915 0000:00:02.0: VGA-1: no EDID data
[   51.022841] i2c-adapter i2c-1: unable to read EDID block.
[   51.022852] i915 0000:00:02.0: LVDS-1: no EDID data
[   51.071653] i2c-adapter i2c-0: unable to read EDID block.
[   51.071665] i915 0000:00:02.0: VGA-1: no EDID data
[   51.089288] i2c-adapter i2c-0: unable to read EDID block.
[   51.089301] i915 0000:00:02.0: VGA-1: no EDID data
[   51.109171] i2c-adapter i2c-1: unable to read EDID block.
[   51.109183] i915 0000:00:02.0: LVDS-1: no EDID data
[  240.905947] wlan0: authenticate with AP 00:14:bf:7c:c6:39
[  240.908847] wlan0: authenticated
[  240.908856] wlan0: associate with AP 00:14:bf:7c:c6:39
[  240.916940] wlan0: RX AssocResp from 00:14:bf:7c:c6:39 (capab=0x401 status=0 aid=4)
[  240.916949] wlan0: associated
[  240.918084] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  251.280046] wlan0: no IPv6 routers present
[ 1415.896080] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 1416.044602] usb 1-3: configuration #1 chosen from 1 choice
[ 1416.835388] Initializing USB Mass Storage driver...
[ 1416.837024] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1416.837617] usbcore: registered new interface driver usb-storage
[ 1416.837631] USB Mass Storage support registered.
[ 1416.839335] usb-storage: device found at 2
[ 1416.839342] usb-storage: waiting for device to settle before scanning
[ 1421.848179] usb-storage: device scan complete
[ 1421.853342] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[ 1421.854470] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0
[ 1421.856262] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1421.890000] sd 2:0:0:0: [sdb] 3915775 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1421.893853] sd 2:0:0:0: [sdb] Write Protect is off
[ 1421.893862] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 1421.893867] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1421.894657] sr1: scsi3-mmc drive: 48x/48x tray
[ 1421.894998] sr 2:0:0:1: Attached scsi CD-ROM sr1
[ 1421.895201] sr 2:0:0:1: Attached scsi generic sg3 type 5
[ 1421.912216] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1421.912231]  sdb: sdb1
[ 1421.929730] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1421.929745] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1424.062105] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1424.183289] ISOFS: changing to secondary root

**$ sudo lshw -C network**

  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:af:b9:ea
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:7 memory:fcffe000-fcffffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:f8000000-f8001fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:bf:49:7f:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bg

**$ iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:7C:C6:39
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000074baea9354
                    Extra: Last beacon: 51276ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0

**$ uname -mr**

2.6.31-14-generic i686

-Thanks, Ubuntu noobzor

---

### Post by wojox on 2010-03-02
You could try disabling ipv6: [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

Tweak firefox: [http://wojox.homelinux.net/?p=33](http://wojox.homelinux.net/?p=33)

---

### Post by Mokacoffay on 2010-03-02
I'll give it a shot, thanks!

---

### Post by Ghost|BTFH on 2010-03-02
Okay, so it's only slow when you're updating?

Here's the trick:

System -> Administration -> Synaptic Package Manager

Click on Settings -> Repositories

Click on Download From box, and select "Other"

Select your country.

Click on the button that says, "Select Best Server"

Wait.

Wait some more..

Still waiting?  Patience...

FINALLY...okay...it's now selected the best server for you.  Click "Choose Server" and "Close."

Now make sure you click "Reload" before you search/update/etc.

Enjoy the new speed.

You may have to do this from time to time if you notice a dramatic drop in speed - it usually means the server's having issues or your connection to it is. :)

Cheers,
Ghost|BTFH

---

### Post by jpl888 on 2010-03-02
I don't think that will help since you don't seem to have a public routable ipv6 addresses. I would recommend changing the server you are connecting to for updates. See attached screen shot.

---

### Post by Mokacoffay on 2010-03-02
> **Ghost|BTFH said:**
> 

Cheers,
Ghost|BTFH

It is very slow while updating, the first method didn't seem to do anything so I'm trying this one.  However it does drop dramatically from normal speeds down to absolutely nothing every 5 or so seconds while downloading from firefox.. The test came back and said "No suitable download server was found. Please check your Internet connection." (Internet browsing works fine)

---

### Post by Ghost|BTFH on 2010-03-02
> **Mokacoffay said:**
> It is very slow while updating, the first method didn't seem to do anything so I'm trying this one.  However it does drop dramatically from normal speeds down to absolutely nothing every 5 or so seconds while downloading from firefox.. The test came back and said "No suitable download server was found. Please check your Internet connection." (Internet browsing works fine)

The only other thing I could think of would be updates are choking your wireless.  Have you tried the same connected via cat5 cable?

My wife's laptop occasionally chokes on updates if she's in the back bedroom with a 50% signal.

Hope it helps.

Cheers,
Ghost|BTFH

---

### Post by Mokacoffay on 2010-03-02
> **Ghost|BTFH said:**
> Have you tried the same connected via cat5 cable?

I have not, but it appears I may have to... this is a very old laptop and I am upstairs and the router is downstairs in another room.  I just figured 5000 b/s was extremely slow.. I usually get around 500 or so kb/s on my normal desktop computer in the same room. It actually begins every download at normal speed but then drops down extremely low within the first 10 seconds and stays very slow for some reason...

Thanks for the help though gents.

---

### Post by MikeG0 on 2010-05-27
I've a Dell Inspiron 1100 too ... the internet connection slows down a bit, but I think it might be an overall X windows issue with the Intel 845G video card.  Does X  drop to a blank screen and then go into crazy loop ...

  1) Blank screen
  2) VT with last 2 syslog entries
  3) Black screen with a panel of vertical black and white lines top  center
  4) Loop


What's the output of xrandr for you?


Thanks for any help,




Mike

---

