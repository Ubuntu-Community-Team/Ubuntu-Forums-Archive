---
title: "wired connection disconnected with xps8300"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by joeradtke on 2012-06-02
I just obtained a Dell xps8300 with i7 core processor.  I believe it has a BCM57788 ethernet interface.  

After loading Ubuntu 12.04 I am unable to connect to the internet.  It wasys wireless connection disconnected.  I have checked the cable and changed it.  the connection works with another computer.  The same thing happens with 11.04.  I believe the driver is tg3 which appears to be present.  Below is some command line output which may be helpful:

```
root@ubuntu:~# uname -a
Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
root@ubuntu:~# lsmod
Module                  Size  Used by
dm_crypt               22528  0 
snd_hda_codec_hdmi     31775  2 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  0 
bnep                   17830  2 
psmouse                72846  0 
snd_timer              28931  2 snd_pcm,snd_seq
ppdev                  12849  0 
rfcomm                 38139  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     17455  0 
serio_raw              13027  0 
mei                    36570  0 
parport                40930  3 parport_pc,ppdev,lp
mac_hid                13077  0 
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             158438  10 bnep,rfcomm
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
dcdbas                 14098  0 
dm_multipath           22710  0 
squashfs               36095  1 
overlayfs              27511  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17699  0 
usb_storage            39646  1 
dm_raid45              76451  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
radeon                733693  3 
ttm                    65344  1 radeon
tg3                   141369  0 
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
root@ubuntu:~# lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Dell XPS 8300
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe600000-fe6fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Dell Device 04aa
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Dell XPS 8300
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fe708000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell XPS 8300
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at fe707000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell XPS 8300
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Dell Device 04aa
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe500000-fe5fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Dell Device 04aa
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell XPS 8300
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe706000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
	Subsystem: Dell XPS 8300
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell XPS 8300
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f050 [size=8]
	I/O ports at f040 [size=4]
	I/O ports at f020 [size=32]
	Memory at fe705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Dell XPS 8300
	Flags: medium devsel, IRQ 4
	Memory at fe704000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450] (prog-if 00 [VGA controller])
	Subsystem: Device 1b0a:909d
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe620000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at e000 [size=256]
	Expansion ROM at fe600000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: radeon
	Kernel modules: radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series]
	Subsystem: Device 1b0a:aa98
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fe640000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Dell XPS 8300
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at fe500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 18-03-73-ff-fe-e0-5c-65
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 18:03:73:e0:5c:65  
          inet6 addr: fe80::1a03:73ff:fee0:5c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89291 (89.2 KB)  TX bytes:32741 (32.7 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2400 (2.4 KB)  TX bytes:2400 (2.4 KB)
```

Any help is greatly appreciated.

Joe Radtke

---

