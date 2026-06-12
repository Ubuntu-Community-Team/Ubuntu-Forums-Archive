---
title: "New RaLink RT3090 causes kernel panic"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by Starcruiser322 on 2012-09-27
I've been using Linux for a while now, and my old wireless card was causing WAY too many issues that no one could figure out (kernel maybe), so I checked my computer's guide for a list of supported replacement cards and did some digging to find a suitable replacement.
I decided on the RT3090 finally, and after installing I noticed the bluetooth was working right away, but the wireless was not. I had the foresight to download the driver package and linux-firmware package (the latter refused to install, eventually gave up). After a quick tweak to fix my first issue (kernel version too new? really?), many minutes of compiling the HUGE tarball (1900 files?), I got the wireless working fine using Wicd.
As I am on dual-boot, I then proceed to install the drivers into Windows 7. No problems here (interesting note: wifi working out of the box, not BT, reverse of Linux lol).

I then go back to my Ubuntu desktop, and all seems well until I get the "Connecting to (my network)" message. All of a sudden I get a kernel panic and I have to force shut down.

Upon further investigation, if I RF_KILL on startup, the panic does not occur and I can load the desktop normally. If I then re-activate the wireless with Wicd open to see progress, it panics on "putting the interface up". The panic occurs every time it reaches that step.
What puzzles me is that it worked before after a couple reboots, but as soon as I install it on Windows, it hates me!

If you need it I can post ifconfig/iwconfig/lspci/etc

[strikethrough]UPDATE:  I can connect now by removing a blacklist for the RT2680 driver... Go ahead and bash me, I'm an idiot for listening to the solution page that told me to do it. One difference from before though: instead of ra0 it is in my iwconfig as wlan1. No clue why.[/strikethrough]

Update 2: It was working because it loaded the wrong driver (oddly enough). after forcing it to load the right driver, I managed to ifup ra0 without incident. After that, I just got another panic handler. Seems it's STILL using the wrong driver, before it crashed I noticed it said "rt2850sta" was my driver, that should be "rt2860sta" since thats the chipset.

---

### Post by Starcruiser322 on 2012-09-27
BUMP

Please? someone? help?

I've pinpointed the problem to the WPA, it works with WEP and OPEN.
When compiling, I get several errors, mainly format errors (it was made for a 2.3 kernel I believe) but it does compile and install. Already tried several "patches".

---

### Post by josephmills on 2012-09-27
Could you paste the outputs off these commands here please and thanks. 

```
lspci -vnn 
```
```
lsmod
```
```
uname -a
```
and 
```
 lsb_release -c

```

Thanks again

---

### Post by Starcruiser322 on 2012-09-27
I put important parts in bold/underline

Kernel driver is the 2860 (correct for chipset) with the 3090 module loaded.
```

root@nick-Presario-CQ62-Notebook-PC:~# lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f03fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device [1022:1235]
    Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device [103c:1444]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0500000-f05fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device [103c:1444]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4038 [size=8]
    I/O ports at 404c [size=4]
    I/O ports at 4030 [size=8]
    I/O ports at 4048 [size=4]
    I/O ports at 4010 [size=16]
    Memory at f0408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci

00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0408600 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 41)
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: 66MHz, medium devsel
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] [1002:9712] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=64K]
    Memory at f0200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon

[U][B]02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Hewlett-Packard Company Device [103c:1453]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0100000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-48-11-57-82-2a-e0
    Kernel driver in use: rt2860
    Kernel modules: rt3090sta[/B][/U]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at f0010000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f0020000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

``````

root@nick-Presario-CQ62-Notebook-PC:~# lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  12 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
radeon                804426  3 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
_**rt3090sta             965649  1 **_
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
psmouse                97362  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
edac_core              53746  0 
sp5100_tco             13791  0 
wmi                    19256  1 hp_wmi
i2c_algo_bit           13423  1 radeon
edac_mce_amd           23709  0 
k10temp                13166  0 
video                  19596  0 
i2c_piix4              13301  0 
shpchp                 37277  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 

``````

root@nick-Presario-CQ62-Notebook-PC:~# uname -a
Linux nick-Presario-CQ62-Notebook-PC 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````

root@nick-Presario-CQ62-Notebook-PC:~# lsb_release -c
Codename:    precise

```

---

### Post by Starcruiser322 on 2012-09-28
Bump?
Still no luck, even tried a couple other packages...
And now I've noticed the bluetooth isn't working right either  :frown:
I'm going to stop trying to fix it until tomorrow, but please post ANY ideas.

---

### Post by Starcruiser322 on 2012-09-28
I guess I just have a knack for finding problems that no one knows how to fix.
I challenge anybody that knows about old kernel drivers on new kernels to come up with ideas!

Thanks for the help everyone. </sarcasm>
I finally gave up after finding a ppa that would help me... if I had 11.04 still. It was either downgrade to the older kernel that was used in 11.04 or get something else that would work. It seemed a lot less work to buy an atheros usb card for $10 off ebay that will run off the ath9k_htc driver.

---

