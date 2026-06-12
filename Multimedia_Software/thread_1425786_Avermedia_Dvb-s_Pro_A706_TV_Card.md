---
title: "Avermedia Dvb-s Pro A706 TV Card"
date: 2010-03-09
forum: Multimedia Software
---

### Post by bebornagain on 2010-03-09
Hello.
I have an Avermedia Dvb-s Pro A706 TV Card, but i dont know how to enable it.
Here are the lspci -vnn and lsmod outputs:

```

```oguncak@oguncak-ubuntu:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
    Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: cc000000-cfffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Capabilities: [88] Subsystem: Intel Corporation Device 0000
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at cbdf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: cbf00000-cbffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 9880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 9c00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at a000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at a080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at cbdffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: cbe00000-cbefffff
    Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 2601
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at ac00 [size=8]
    I/O ports at a880 [size=4]
    I/O ports at a800 [size=8]
    I/O ports at a480 [size=4]
    I/O ports at a400 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: medium devsel
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:09.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: Avermedia Technologies Inc Device 2155
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at cbeff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: saa7134
    Kernel modules: saa7134

01:0a.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
    Subsystem: VIA Technologies, Inc. Device 0106
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at b800 [size=256]
    Memory at cbeffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
    Subsystem: ASUSTeK Computer Inc. Device 8142
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at cbffc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at c800 [size=256]
    Expansion ROM at cbfc0000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Vital Product Data <?>
    Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel driver in use: sky2
    Kernel modules: sky2

04:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 2043
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at cf000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at cef80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

```

```oguncak@oguncak-ubuntu:~$ sudo lsmod
Module                  Size  Used by
usb_storage            52800  0 
usblp                  12636  0 
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          27016  3 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
saa7134_alsa           12192  2 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75520  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,saa7134_alsa
snd_seq_dummy           2656  0 
saa7134               153672  1 saa7134_alsa
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
ir_common              48512  1 saa7134
snd_rawmidi            22176  1 snd_seq_midi
v4l2_common            17500  1 saa7134
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
videodev               36736  2 saa7134,v4l2_common
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l1_compat            14336  1 videodev
iptable_filter          3100  0 
videobuf_dma_sg        12608  2 saa7134_alsa,saa7134
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
videobuf_core          17952  2 saa7134,videobuf_dma_sg
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,saa7134_alsa,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               16544  1 ip_tables
lp                      8964  0 
parport_pc             32228  1 
tveeprom               11872  1 saa7134
soundcore               7264  3 snd
nvidia               9587272  36 
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
asus_atk0110            8252  0 
parport                35340  3 ppdev,lp,parport_pc
joydev                 10240  0 
usbhid                 38304  0 
floppy                 54980  0 
sky2                   47040  0 
via_rhine              22532  0 
mii                     5212  1 via_rhine
intel_agp              27940  0 
agpgart                35020  2 nvidia,intel_agp

I hope someone can help me.
Thanks everybody.

---

### Post by steefjeqv on 2010-03-10
Hi,

Your card seems to be recognized and the drivers are loaded (saa71XX).

You can check if your card works by installing Kaffeine. If there's a DVB folder available in Kaffeine, you can try scanning for channels.

Greetings,
Steven

---

### Post by bebornagain on 2010-03-13
hello. thanks for your reply.
i had installed kaffeine but there were no dvb folder. when i tried to make settings for digital tv, there were no available devices to make scan.

i dont understand the problem.

---

### Post by bebornagain on 2010-03-13
Also, here is the me-tv -v output:

```

```03/13/2010 08:53:37: Scanning DVB devices ...
03/13/2010 08:53:37: Database 'exists' 
03/13/2010 08:53:37: Opening database file '/home/oguncak/.me-tv/me-tv.db'
03/13/2010 08:53:37: Application constructor
03/13/2010 08:53:37: sqlite3_threadsafe() = 1
03/13/2010 08:53:37: Loading GtkBuilder file '/usr/share/me-tv/glade/me-tv.ui' ...
03/13/2010 08:53:38: Application constructed
03/13/2010 08:53:38: Initialising table 'version'
03/13/2010 08:53:38: Required Database version: 2
03/13/2010 08:53:38: Actual Database version: 2
03/13/2010 08:53:38: Me TV database initialised successfully
03/13/2010 08:53:38: Loading channels ...
03/13/2010 08:53:38: Channels loaded
03/13/2010 08:53:38: StatusIcon constructor started
03/13/2010 08:53:38: StatusIcon constructed
03/13/2010 08:53:38: MainWindow constructor
03/13/2010 08:53:38: Setting integer combo box size to 0
03/13/2010 08:53:38: MainWindow constructed
03/13/2010 08:53:38: Setting geometry (10, 33, 500, 500)
03/13/2010 08:53:38: Updating EPG
03/13/2010 08:53:38: EPG update complete
03/13/2010 08:53:38: Exception: There are no available DVB tuner devices
03/13/2010 08:53:38: Error message: 'There are no available DVB tuner devices'
03/13/2010 08:53:39: Poking screensaver
03/13/2010 08:53:39: Checking scheduled recordings
03/13/2010 08:53:39: Removing scheduled recordings older than 1268463219
03/13/2010 08:53:39: Saving 0 scheduled recordings
03/13/2010 08:53:39: Deleting old scheduled recordings ending before 1268463219
03/13/2010 08:53:39: Scheduled recordings saved
03/13/2010 08:53:39: Saving channels
03/13/2010 08:53:39: Channels saved
03/13/2010 08:53:39: Deleting old EPG events
03/13/2010 08:53:39: EPG events saved
03/13/2010 08:53:39: Updating EPG
03/13/2010 08:53:39: EPG update complete
03/13/2010 08:53:41: Saved geometry (10, 33, 500, 500)
03/13/2010 08:53:41: Stopping engine
03/13/2010 08:53:41: Engine stopped
03/13/2010 08:54:00: Checking scheduled recordings
03/13/2010 08:54:00: Removing scheduled recordings older than 1268463240
03/13/2010 08:54:00: Saving 0 scheduled recordings
03/13/2010 08:54:00: Deleting old scheduled recordings ending before 1268463240
03/13/2010 08:54:00: Scheduled recordings saved
03/13/2010 08:54:00: Saving channels
03/13/2010 08:54:00: Channels saved
03/13/2010 08:54:00: Deleting old EPG events
03/13/2010 08:54:00: EPG events saved
03/13/2010 08:54:00: Updating EPG
03/13/2010 08:54:00: EPG update complete
03/13/2010 08:55:00: Checking scheduled recordings
03/13/2010 08:55:00: Removing scheduled recordings older than 1268463300
03/13/2010 08:55:00: Saving 0 scheduled recordings
03/13/2010 08:55:00: Deleting old scheduled recordings ending before 1268463300
03/13/2010 08:55:00: Scheduled recordings saved
03/13/2010 08:55:00: Saving channels
03/13/2010 08:55:00: Channels saved
03/13/2010 08:55:00: Deleting old EPG events
03/13/2010 08:55:00: EPG events saved
03/13/2010 08:55:00: Updating EPG
03/13/2010 08:55:00: EPG update complete
03/13/2010 08:56:00: Checking scheduled recordings
03/13/2010 08:56:00: Removing scheduled recordings older than 1268463360
03/13/2010 08:56:00: Saving 0 scheduled recordings
03/13/2010 08:56:00: Deleting old scheduled recordings ending before 1268463360
03/13/2010 08:56:00: Scheduled recordings saved
03/13/2010 08:56:00: Saving channels
03/13/2010 08:56:00: Channels saved
03/13/2010 08:56:00: Deleting old EPG events
03/13/2010 08:56:00: EPG events saved
03/13/2010 08:56:00: Updating EPG
03/13/2010 08:56:00: EPG update complete
03/13/2010 08:57:00: Checking scheduled recordings
03/13/2010 08:57:00: Removing scheduled recordings older than 1268463420
03/13/2010 08:57:00: Saving 0 scheduled recordings
03/13/2010 08:57:00: Deleting old scheduled recordings ending before 1268463420
03/13/2010 08:57:00: Scheduled recordings saved
03/13/2010 08:57:00: Saving channels
03/13/2010 08:57:00: Channels saved
03/13/2010 08:57:00: Deleting old EPG events
03/13/2010 08:57:00: EPG events saved
03/13/2010 08:57:00: Updating EPG
03/13/2010 08:57:00: EPG update complete
03/13/2010 08:58:00: Checking scheduled recordings
03/13/2010 08:58:00: Removing scheduled recordings older than 1268463480
03/13/2010 08:58:00: Saving 0 scheduled recordings
03/13/2010 08:58:00: Deleting old scheduled recordings ending before 1268463480
03/13/2010 08:58:00: Scheduled recordings saved
03/13/2010 08:58:00: Saving channels
03/13/2010 08:58:00: Channels saved
03/13/2010 08:58:00: Deleting old EPG events
03/13/2010 08:58:00: EPG events saved
03/13/2010 08:58:00: Updating EPG
03/13/2010 08:58:00: EPG update complete
03/13/2010 08:59:00: Checking scheduled recordings
03/13/2010 08:59:00: Removing scheduled recordings older than 1268463540
03/13/2010 08:59:00: Saving 0 scheduled recordings
03/13/2010 08:59:00: Deleting old scheduled recordings ending before 1268463540
03/13/2010 08:59:00: Scheduled recordings saved
03/13/2010 08:59:00: Saving channels
03/13/2010 08:59:00: Channels saved
03/13/2010 08:59:00: Deleting old EPG events
03/13/2010 08:59:00: EPG events saved
03/13/2010 08:59:00: Updating EPG
03/13/2010 08:59:00: EPG update complete
03/13/2010 09:00:00: Checking scheduled recordings
03/13/2010 09:00:00: Removing scheduled recordings older than 1268463600
03/13/2010 09:00:00: Saving 0 scheduled recordings
03/13/2010 09:00:00: Deleting old scheduled recordings ending before 1268463600
03/13/2010 09:00:00: Scheduled recordings saved
03/13/2010 09:00:00: Saving channels
03/13/2010 09:00:00: Channels saved
03/13/2010 09:00:00: Deleting old EPG events
03/13/2010 09:00:00: EPG events saved
03/13/2010 09:00:00: Updating EPG
03/13/2010 09:00:00: EPG update complete

---

### Post by steefjeqv on 2010-03-13
Hi,

Can you post your dmesg output ?

Greetings,
Steven

---

### Post by bebornagain on 2010-03-18
Thanks.
Here is the dmesg output:

```
[    0.120309] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.120317] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.120324] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.120379] pci 0000:00:1f.2: reg 10 io port: [0xac00-0xac07]
[    0.120388] pci 0000:00:1f.2: reg 14 io port: [0xa880-0xa883]
[    0.120395] pci 0000:00:1f.2: reg 18 io port: [0xa800-0xa807]
[    0.120403] pci 0000:00:1f.2: reg 1c io port: [0xa480-0xa483]
[    0.120410] pci 0000:00:1f.2: reg 20 io port: [0xa400-0xa40f]
[    0.120440] pci 0000:00:1f.2: PME# supported from D3hot
[    0.120445] pci 0000:00:1f.2: PME# disabled
[    0.120498] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.120566] pci 0000:04:00.0: reg 10 32bit mmio: [0xcf000000-0xcfffffff]
[    0.120578] pci 0000:04:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.120589] pci 0000:04:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]
[    0.120597] pci 0000:04:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.120604] pci 0000:04:00.0: reg 30 32bit mmio: [0xcef80000-0xceffffff]
[    0.120685] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.120690] pci 0000:00:01.0: bridge 32bit mmio: [0xcc000000-0xcfffffff]
[    0.120695] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.120743] pci 0000:00:1c.0: bridge io port: [0xd000-0xdfff]
[    0.120819] pci 0000:02:00.0: reg 10 64bit mmio: [0xcbffc000-0xcbffffff]
[    0.120830] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.120860] pci 0000:02:00.0: reg 30 32bit mmio: [0xcbfc0000-0xcbfdffff]
[    0.120907] pci 0000:02:00.0: supports D1 D2
[    0.120910] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120916] pci 0000:02:00.0: PME# disabled
[    0.120967] pci 0000:00:1c.1: bridge io port: [0xc000-0xcfff]
[    0.120972] pci 0000:00:1c.1: bridge 32bit mmio: [0xcbf00000-0xcbffffff]
[    0.121033] pci 0000:01:09.0: reg 10 32bit mmio: [0xcbeff000-0xcbeff7ff]
[    0.121089] pci 0000:01:09.0: supports D1 D2
[    0.121131] pci 0000:01:0a.0: reg 10 io port: [0xb800-0xb8ff]
[    0.121140] pci 0000:01:0a.0: reg 14 32bit mmio: [0xcbeffc00-0xcbeffcff]
[    0.121193] pci 0000:01:0a.0: supports D1 D2
[    0.121195] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.121201] pci 0000:01:0a.0: PME# disabled
[    0.121240] pci 0000:00:1e.0: transparent bridge
[    0.121245] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.121250] pci 0000:00:1e.0: bridge 32bit mmio: [0xcbe00000-0xcbefffff]
[    0.121277] pci_bus 0000:00: on NUMA node 0
[    0.121283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.121489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.121550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.121696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.121756] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.124996] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.125147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.125295] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.125445] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.125592] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.125741] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.125888] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.126040] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.126295] SCSI subsystem initialized
[    0.126363] libata version 3.00 loaded.
[    0.126462] usbcore: registered new interface driver usbfs
[    0.126482] usbcore: registered new interface driver hub
[    0.126517] usbcore: registered new device driver usb
[    0.126684] ACPI: WMI: Mapper loaded
[    0.126687] PCI: Using ACPI for IRQ routing
[    0.126875] Bluetooth: Core ver 2.15
[    0.126912] NET: Registered protocol family 31
[    0.126915] Bluetooth: HCI device and connection manager initialized
[    0.126919] Bluetooth: HCI socket layer initialized
[    0.126921] NetLabel: Initializing
[    0.126923] NetLabel:  domain hash size = 128
[    0.126925] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.126942] NetLabel:  unlabeled traffic allowed by default
[    0.127076] hpet clockevent registered
[    0.127080] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.127086] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.127093] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.133895] pnp: PnP ACPI init
[    0.133918] ACPI: bus type pnp registered
[    0.139741] pnp: PnP ACPI: found 18 devices
[    0.139745] ACPI: ACPI bus type pnp unregistered
[    0.139751] PnPBIOS: Disabled by ACPI PNP
[    0.139768] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.139779] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.139788] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.139791] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.139795] system 00:09: ioport range 0x400-0x41f has been reserved
[    0.139799] system 00:09: ioport range 0x480-0x4bf has been reserved
[    0.139803] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.139807] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.139811] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.139815] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.139822] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.139831] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.139835] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.139842] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.139849] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.139857] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.139861] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.139865] system 00:11: iomem range 0x100000-0x7fffffff could not be reserved
[    0.174590] AppArmor: AppArmor Filesystem Enabled
[    0.174637] pci 0000:00:01.0: PCI bridge, secondary bus 0000:04
[    0.174641] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.174647] pci 0000:00:01.0:   MEM window: 0xcc000000-0xcfffffff
[    0.174652] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.174657] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.174661] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.174666] pci 0000:00:1c.0:   MEM window: disabled
[    0.174671] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.174676] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.174680] pci 0000:00:1c.1:   IO window: 0xc000-0xcfff
[    0.174686] pci 0000:00:1c.1:   MEM window: 0xcbf00000-0xcbffffff
[    0.174691] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.174696] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.174700] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.174706] pci 0000:00:1e.0:   MEM window: 0xcbe00000-0xcbefffff
[    0.174711] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.174726]   alloc irq_desc for 16 on node -1
[    0.174729]   alloc kstat_irqs on node -1
[    0.174737] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.174743] pci 0000:00:01.0: setting latency timer to 64
[    0.174753] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.174758] pci 0000:00:1c.0: setting latency timer to 64
[    0.174767]   alloc irq_desc for 17 on node -1
[    0.174769]   alloc kstat_irqs on node -1
[    0.174774] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.174779] pci 0000:00:1c.1: setting latency timer to 64
[    0.174787] pci 0000:00:1e.0: setting latency timer to 64
[    0.174794] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.174798] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.174801] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.174805] pci_bus 0000:04: resource 1 mem: [0xcc000000-0xcfffffff]
[    0.174808] pci_bus 0000:04: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.174812] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.174815] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.174818] pci_bus 0000:02: resource 1 mem: [0xcbf00000-0xcbffffff]
[    0.174822] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.174825] pci_bus 0000:01: resource 1 mem: [0xcbe00000-0xcbefffff]
[    0.174828] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.174831] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.174880] NET: Registered protocol family 2
[    0.175009] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.175420] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.175980] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.176365] TCP: Hash tables configured (established 131072 bind 65536)
[    0.176370] TCP reno registered
[    0.176511] NET: Registered protocol family 1
[    0.176600] Trying to unpack rootfs image as initramfs...
[    0.435258] Freeing initrd memory: 7485k freed
[    0.440490] cpufreq-nforce2: No nForce2 chipset.
[    0.440530] Scanning for low memory corruption every 60 seconds
[    0.440660] audit: initializing netlink socket (disabled)
[    0.440680] type=2000 audit(1268926332.440:1): initialized
[    0.450796] highmem bounce pool size: 64 pages
[    0.450804] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.452518] VFS: Disk quotas dquot_6.5.2
[    0.452590] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.453303] fuse init (API version 7.12)
[    0.453412] msgmni has been set to 1709
[    0.453648] alg: No test for stdrng (krng)
[    0.453667] io scheduler noop registered
[    0.453670] io scheduler anticipatory registered
[    0.453672] io scheduler deadline registered
[    0.453730] io scheduler cfq registered (default)
[    0.453849] pci 0000:04:00.0: Boot video device
[    0.453987]   alloc irq_desc for 24 on node -1
[    0.453991]   alloc kstat_irqs on node -1
[    0.454003] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.454012] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.454141]   alloc irq_desc for 25 on node -1
[    0.454144]   alloc kstat_irqs on node -1
[    0.454154] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.454164] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.454311]   alloc irq_desc for 26 on node -1
[    0.454314]   alloc kstat_irqs on node -1
[    0.454324] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.454334] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.454450] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.454557] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.454730] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.454735] ACPI: Power Button [PWRF]
[    0.454805] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.454809] ACPI: Power Button [PWRB]
[    0.455299] processor LNXCPU:00: registered as cooling_device0
[    0.455304] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.458002] isapnp: Scanning for PnP cards...
[    0.628076] Switched to high resolution mode on CPU 0
[    0.811484] isapnp: No Plug & Play device found
[    0.812956] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.813121] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.813646] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.814953] brd: module loaded
[    0.815525] loop: module loaded
[    0.815621] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.815754] ata_piix 0000:00:1f.1: version 2.13
[    0.815773]   alloc irq_desc for 18 on node -1
[    0.815776]   alloc kstat_irqs on node -1
[    0.815785] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.815832] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.815920] scsi0 : ata_piix
[    0.816045] scsi1 : ata_piix
[    0.818215] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.818220] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.818494]   alloc irq_desc for 19 on node -1
[    0.818498]   alloc kstat_irqs on node -1
[    0.818504] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.818510] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.818556] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.818613] scsi2 : ata_piix
[    0.818682] scsi3 : ata_piix
[    0.818730] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[    0.818734] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[    0.819872] Fixed MDIO Bus: probed
[    0.819920] PPP generic driver version 2.4.2
[    0.820067] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.820090]   alloc irq_desc for 23 on node -1
[    0.820094]   alloc kstat_irqs on node -1
[    0.820100] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.820122] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.820127] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.820166] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.824077] ehci_hcd 0000:00:1d.7: debug port 1
[    0.824085] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.824216] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xcbdffc00
[    0.840014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.840120] usb usb1: configuration #1 chosen from 1 choice
[    0.840163] hub 1-0:1.0: USB hub found
[    0.840174] hub 1-0:1.0: 8 ports detected
[    0.840247] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.840267] uhci_hcd: USB Universal Host Controller Interface driver
[    0.840304] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.840313] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.840317] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.840356] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.840383] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009880
[    0.840483] usb usb2: configuration #1 chosen from 1 choice
[    0.840521] hub 2-0:1.0: USB hub found
[    0.840531] hub 2-0:1.0: 2 ports detected
[    0.840583] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.840590] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.840594] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.840634] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.840660] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009c00
[    0.840752] usb usb3: configuration #1 chosen from 1 choice
[    0.840789] hub 3-0:1.0: USB hub found
[    0.840798] hub 3-0:1.0: 2 ports detected
[    0.840849] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.840857] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.840861] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.840898] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.840932] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a000
[    0.841024] usb usb4: configuration #1 chosen from 1 choice
[    0.841067] hub 4-0:1.0: USB hub found
[    0.841076] hub 4-0:1.0: 2 ports detected
[    0.841134] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.841144] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.841149] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.841184] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.841218] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a080
[    0.841309] usb usb5: configuration #1 chosen from 1 choice
[    0.841345] hub 5-0:1.0: USB hub found
[    0.841355] hub 5-0:1.0: 2 ports detected
[    0.841480] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.841483] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.842012] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.842089] mice: PS/2 mouse device common for all mice
[    0.842212] rtc_cmos 00:03: RTC can wake from S4
[    0.842256] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.842284] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.842425] device-mapper: uevent: version 1.0.3
[    0.842531] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.842625] device-mapper: multipath: version 1.1.0 loaded
[    0.842629] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.842778] EISA: Probing bus 0 at eisa.0
[    0.842810] EISA: Detected 0 cards.
[    0.842862] cpuidle: using governor ladder
[    0.842866] cpuidle: using governor menu
[    0.843482] TCP cubic registered
[    0.843650] NET: Registered protocol family 10
[    0.844223] lo: Disabled Privacy Extensions
[    0.844614] NET: Registered protocol family 17
[    0.844642] Bluetooth: L2CAP ver 2.13
[    0.844645] Bluetooth: L2CAP socket layer initialized
[    0.844648] Bluetooth: SCO (Voice Link) ver 0.6
[    0.844650] Bluetooth: SCO socket layer initialized
[    0.844689] Bluetooth: RFCOMM TTY layer initialized
[    0.844693] Bluetooth: RFCOMM socket layer initialized
[    0.844696] Bluetooth: RFCOMM ver 1.11
[    0.844730] Using IPI No-Shortcut mode
[    0.844815] PM: Resume from disk failed.
[    0.844836] registered taskstats version 1
[    0.844960]   Magic number: 2:402:538
[    0.845033] rtc_cmos 00:03: setting system clock to 2010-03-18 15:32:13 UTC (1268926333)
[    0.845037] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.845039] EDD information not available.
[    0.862075] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.995159] ata1.00: NODEV after polling detection
[    0.995201] ata1.01: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
[    0.995462] ata3.00: ATA-7: SAMSUNG HD160JJ, ZM100-47, max UDMA7
[    0.995466] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.008419] ata1.01: configured for UDMA/66
[    1.011024] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.05 PQ: 0 ANSI: 5
[    1.015208] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.015212] Uniform CD-ROM driver Revision: 3.20
[    1.015322] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.015388] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.032365] ata3.00: configured for UDMA/133
[    1.032470] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[    1.032610] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.032659] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.032730] sd 2:0:0:0: [sda] Write Protect is off
[    1.032734] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.032770] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.032939]  sda: sda1
[    1.042697] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.196202] ata4.01: HPA unlocked: 234439535 -> 234441648, native 234441648
[    1.196209] ata4.01: ATA-7: ST3120813AS, 3.AAE, max UDMA/133
[    1.196213] ata4.01: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.242714] ata4.01: configured for UDMA/133
[    1.242816] scsi 3:0:1:0: Direct-Access     ATA      ST3120813AS      3.AA PQ: 0 ANSI: 5
[    1.242957] sd 3:0:1:0: Attached scsi generic sg2 type 0
[    1.243007] sd 3:0:1:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.243074] sd 3:0:1:0: [sdb] Write Protect is off
[    1.243079] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.243114] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.243274]  sdb: sdb1 sdb2 < sdb5 >
[    1.299772] sd 3:0:1:0: [sdb] Attached SCSI disk
[    1.299795] Freeing unused kernel memory: 544k freed
[    1.300214] Write protecting the kernel text: 4604k
[    1.300278] Write protecting the kernel read-only data: 1840k
[    1.340045] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.532638] Linux agpgart interface v0.103
[    1.552471] usb 3-1: configuration #1 chosen from 1 choice
[    1.575491] Floppy drive(s): fd0 is 1.44M
[    1.580887] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.580931]   alloc irq_desc for 21 on node -1
[    1.580934]   alloc kstat_irqs on node -1
[    1.580943] via-rhine 0000:01:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.590482] sky2 driver version 1.23
[    1.590518] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.590532] sky2 0000:02:00.0: setting latency timer to 64
[    1.590560] sky2 0000:02:00.0: Yukon-2 EC chip revision 2
[    1.590648]   alloc irq_desc for 27 on node -1
[    1.590650]   alloc kstat_irqs on node -1
[    1.590667] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
[    1.591541] sky2 eth0: addr 00:11:d8:ba:e9:f0
[    1.602756] FDC 0 is a post-1991 82077
[    1.663821] eth1: VIA Rhine III at 0xcbeffc00, 00:02:44:9d:9b:28, IRQ 21.
[    1.664542] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.733232] usbcore: registered new interface driver hiddev
[    1.748151] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[    1.748245] generic-usb 0003:09DA:024F.0001: input,hidraw0: USB HID v1.11 Keyboard [A4Tech RF USB Receiver] on usb-0000:00:1d.1-1/input0
[    1.774680] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input5
[    1.774805] generic-usb 0003:09DA:024F.0002: input,hidraw1: USB HID v1.11 Mouse [A4Tech RF USB Receiver] on usb-0000:00:1d.1-1/input1
[    1.774832] usbcore: registered new interface driver usbhid
[    1.774837] usbhid: v2.6:USB HID core driver
[    3.083253] PM: Starting manual resume from disk
[    3.083259] PM: Resume from partition 8:17
[    3.083261] PM: Checking hibernation image.
[    3.083409] PM: Resume from disk failed.
[    3.097705] EXT4-fs (sdb5): barriers enabled
[    3.114116] kjournald2 starting: pid 366, dev sdb5:8, commit interval 5 seconds
[    3.114155] EXT4-fs (sdb5): delayed allocation enabled
[    3.114160] EXT4-fs: file extents enabled
[    3.128814] EXT4-fs: mballoc enabled
[    3.128835] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[    3.758476] type=1505 audit(1268926336.412:2): operation="profile_load" pid=390 name=/usr/share/gdm/guest-session/Xsession
[    3.762776] type=1505 audit(1268926336.414:3): operation="profile_load" pid=391 name=/sbin/dhclient3
[    3.763598] type=1505 audit(1268926336.414:4): operation="profile_load" pid=391 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.764061] type=1505 audit(1268926336.418:5): operation="profile_load" pid=391 name=/usr/lib/connman/scripts/dhclient-script
[    3.817110] type=1505 audit(1268926336.470:6): operation="profile_load" pid=392 name=/usr/bin/evince
[    3.830537] type=1505 audit(1268926336.482:7): operation="profile_load" pid=392 name=/usr/bin/evince-previewer
[    3.838432] type=1505 audit(1268926336.490:8): operation="profile_load" pid=392 name=/usr/bin/evince-thumbnailer
[    3.860059] type=1505 audit(1268926336.514:9): operation="profile_load" pid=394 name=/usr/lib/cups/backend/cups-pdf
[    3.861015] type=1505 audit(1268926336.514:10): operation="profile_load" pid=394 name=/usr/sbin/cupsd
[   16.083512] Adding 7815580k swap on /dev/sdb1.  Priority:-1 extents:1 across:7815580k 
[   16.120230] udev: starting version 147
[   16.279337] lp: driver loaded but no devices found
[   16.358959] EXT4-fs (sdb5): internal journal on sdb5:8
[   16.656617] parport_pc 00:07: reported by Plug and Play ACPI
[   16.656734] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   16.749025] lp0: using parport0 (interrupt-driven).
[   16.793997] nvidia: module license 'NVIDIA' taints kernel.
[   16.794004] Disabling lock debugging due to kernel taint
[   17.075816] intel_rng: FWH not detected
[   17.090210] Linux video capture interface: v2.00
[   17.200078] saa7130/34: v4l2 driver version 0.2.15 loaded
[   17.200145] saa7134 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.200155] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 17, latency: 64, mmio: 0xcbeff000
[   17.200164] saa7133[0]: subsystem: 1461:2155, board: UNKNOWN/GENERIC [card=0,autodetected]
[   17.200185] saa7133[0]: board init: gpio is 500
[   17.200192] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.205462] ppdev: user-space parallel port driver
[   17.260425] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.466656] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.466700] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.515894] saa7133[0]: i2c eeprom 00: 61 14 55 21 00 00 00 00 00 00 00 00 00 00 00 00
[   17.515909] saa7133[0]: i2c eeprom 10: ff ff dd ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   17.515920] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 04 06 ff 00 35 ff ff ff ff
[   17.515932] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.515982] saa7133[0]: i2c eeprom 40: ff 89 00 c0 ff 1c 08 19 97 89 ff ff 80 15 0a ff
[   17.515993] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516025] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516037] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516048] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516059] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516070] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516081] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516092] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516103] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516114] saa7133[0]: i2c eeprom e0: 00 01 81 b0 62 bf ff ff ff ff ff ff ff ff ff ff
[   17.516125] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.516139] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[   17.517068] saa7133[0]: registered device video0 [v4l2]
[   17.517101] saa7133[0]: registered device vbi0
[   17.571028] saa7134 ALSA driver for DMA sound loaded
[   17.571045] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.571073] saa7133[0]/alsa: saa7133[0] at 0xcbeff000 irq 17 registered as card -2
[   17.648429] sky2 eth0: enabling interface
[   17.673849] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.676136] eth1: link down
[   17.676301] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.684319] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   17.804307] __ratelimit: 3 callbacks suppressed
[   17.804312] type=1505 audit(1268919150.458:12): operation="profile_replace" pid=921 name=/usr/share/gdm/guest-session/Xsession
[   17.806808] type=1505 audit(1268919150.458:13): operation="profile_replace" pid=922 name=/sbin/dhclient3
[   17.807635] type=1505 audit(1268919150.458:14): operation="profile_replace" pid=922 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.808108] type=1505 audit(1268919150.462:15): operation="profile_replace" pid=922 name=/usr/lib/connman/scripts/dhclient-script
[   17.813288] type=1505 audit(1268919150.466:16): operation="profile_replace" pid=923 name=/usr/bin/evince
[   17.878761] type=1505 audit(1268919150.530:17): operation="profile_replace" pid=923 name=/usr/bin/evince-previewer
[   17.914102] type=1505 audit(1268919150.566:18): operation="profile_replace" pid=923 name=/usr/bin/evince-thumbnailer
[   17.952993] type=1505 audit(1268919150.606:19): operation="profile_replace" pid=937 name=/usr/lib/cups/backend/cups-pdf
[   17.953952] type=1505 audit(1268919150.606:20): operation="profile_replace" pid=937 name=/usr/sbin/cupsd
[   18.005090] type=1505 audit(1268919150.658:21): operation="profile_replace" pid=955 name=/usr/sbin/tcpdump
[   18.061842] nvidia 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.061855] nvidia 0000:04:00.0: setting latency timer to 64
[   18.062105] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   19.332476] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   19.332636] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.668026] eth0: no IPv6 routers present

```

the output seemed to be too long to display, i hope this will be enough.

---

### Post by steefjeqv on 2010-03-20
Hi,

Sorry for the late reply.

Your card isn't properly detected, I'm afraid.

17.200164] saa7133[0]: subsystem: 1461:2155, board: UNKNOWN/GENERIC [card=0,autodetected]

You can upgrade the v4l driver :

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Build_and_Installation_Instructions]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Build_and_Installation_Instructions")

Greetings,
Steven

---

### Post by tydaikho on 2010-03-24
I got similar matter with my DVB USB card... My card was detected:
lsusb
> Bus 003 Device 002: ID 192f:0116 Avago Technologies, Pte. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 10b8:0066 DiBcom 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But it is not recognized as DTB... I follow linuxtv.org and make&make install with v4l-dvb but my card still works nothing...
> [    2.008008] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.140914] usb 1-1: New USB device found, idVendor=10b8, idProduct=0066
[    2.140917] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.140918] usb 1-1: Product: HOOK
[    2.140920] usb 1-1: Manufacturer: DiBcom SA
[    2.140978] usb 1-1: configuration #1 chosen from 1 choice
[    2.216646] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:26:b9:11:5d:bc
[    2.216650] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3


my dmesg results not like below example:
> [ 3076.564204] usb 1-4.1.2: new high speed USB device using ehci_hcd and address 12
[ 3076.697132] usb 1-4.1.2: configuration #1 chosen from 1 choice
[ 3076.766546] dvb-usb: found a 'DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver' in warm state.
[ 3076.766561] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 3076.766779] DVB: registering new adapter (DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver)
[ 3076.767389] +rtd2831u_fe_attach
[ 3076.767516] -rtd2831u_fe_attach
[ 3076.767524] DVB: registering adapter 0 frontend 0 (Realtek RTD2830 DVB-T)...
[ 3076.767740] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4.1/1-4.1.2/input/input10
[ 3076.800272] dvb-usb: schedule remote query interval to 300 msecs.
[ 3076.800284] dvb-usb: DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver successfully initialized and connected.
[ 3076.800331] usbcore: registered new interface driver dvb_usb_rtd2831u
No DVB device exists...
ls /dev
> block         dvd      input  loop7             psaux   sda1  sg1         tty0   tty18  tty27  tty36  tty45    tty54  tty63    vcs   vcsa1       xconsole
bsg         dvdrw      kmsg     MAKEDEV         ptmx    sda2  shm         tty1   tty19  tty28  tty37  tty46    tty55  tty7    vcs1  vcsa2       zero
bus         fb0      log     mcelog             pts     sda3  snapshot  tty10  tty2   tty29  tty38  tty47    tty56  tty8    vcs2  vcsa3
cdrom         fd      loop0  mem             random  sda4  snd         tty11  tty20  tty3   tty39  tty48    tty57  tty9    vcs3  vcsa4
cdrw         full      loop1  net             rfkill  sda5  sndstat   tty12  tty21  tty30  tty4     tty49    tty58  ttyS0    vcs4  vcsa5
char         fuse      loop2  network_latency     root    sda6  sr0         tty13  tty22  tty31  tty40  tty5    tty59  ttyS1    vcs5  vcsa6
console         fw0      loop3  network_throughput  rtc     sda7  stderr    tty14  tty23  tty32  tty41  tty50    tty6   ttyS2    vcs6  vcsa7
core         hidraw0  loop4  null             rtc0    sda8  stdin     tty15  tty24  tty33  tty42  tty51    tty60  ttyS3    vcs7  vcsa8
cpu_dma_latency  hpet      loop5  port             scd0    sda9  stdout    tty16  tty25  tty34  tty43  tty52    tty61  urandom    vcs8  vga_arbiter
disk         initctl  loop6  ppp             sda     sg0   tty         tty17  tty26  tty35  tty44  tty53    tty62  v4l    vcsa  video0


Please help me this ... thank you...

---

