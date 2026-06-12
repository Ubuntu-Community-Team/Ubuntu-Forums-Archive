---
title: "No audio over HDMI (Revo R3700)"
date: 2010-12-29
forum: Multimedia Software
---

### Post by Scorpuk on 2010-12-29
Anyone have a solution to getting audio over HDMI on a Revo R3700 with Ubuntu 10.10?


aplay -l

```
living-room@livingroom-Aspire-R3700:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L

```
living-room@livingroom-Aspire-R3700:~$ aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

```

lspci -v

```
living-room@livingroom-Aspire-R3700:~$ sudo lspci -v
[sudo] password for living-room: 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=08 <?>
	Kernel modules: intel-agp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fcf00000-fdffffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 047a
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 047a
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: 80200000-805fffff
	Prefetchable memory behind bridge: 00000000fbf00000-00000000fbffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 047a
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at feafbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 047a

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b880 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=16]
	Memory at feafb800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 047a
	Flags: medium devsel, IRQ 5
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 047a
	Physical Slot: 32
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fcf80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 047a
	Physical Slot: 32
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fcf7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Lite-On Communications Inc Device 6622
	Physical Slot: 34
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-a6-a3-59-9d-65-1c
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta, rt2800pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 8000
	Physical Slot: 35
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at e800 [size=256]
	Memory at fbffb000 (64-bit, prefetchable) [size=4K]
	Memory at fbffc000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number af-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```


I have unmuted all spdif outputs in alsamixer, but to no avail.

The headphone socket audio works no problem. Just nothing over HDMI. :-(



Thanks for any help on this as it is much appreciated.

---

### Post by lidex on 2010-12-29
You'll want this:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by Scorpuk on 2010-12-29
Tnx for the link


Finally solved it, although probably not pure HD audio coming therough.


Followed the link and added latest alsa drives to no availa.

BUT


It was one of the posts that refered to alsamixer and pressing F6.


DOH.

The nvidia cards channels were all muted.

Unmuted them and then used vlc to work out shich plg it was. Eventually found it to be 1,7.

Added that to MythTV and its now working.


Also added my user to the audio group as he wasnt in it by default.

---

### Post by pablo0151 on 2010-12-30
> **Scorpuk said:**
> Tnx for the link


Finally solved it, although probably not pure HD audio coming therough.


Followed the link and added latest alsa drives to no availa.

BUT


It was one of the posts that refered to alsamixer and pressing F6.


DOH.

The nvidia cards channels were all muted.

Unmuted them and then used vlc to work out shich plg it was. Eventually found it to be 1,7.

Added that to MythTV and its now working.


Also added my user to the audio group as he wasnt in it by default.

Hi

Thanks for the useful info, I've got one of these machines myself and have had the same problem as uyou.

I've tried matching my settings to what you've suggested but still no joy. Any chance you could explain the VLC bit to me in more depth (sorry if I sound a bit thick)??

Cheers

Paul

---

### Post by Tim_Fox on 2011-09-28
I have a bit of a problem with the sound on my Revo R3700. 
I can get sound out over HDMI when I watch a youtube video on Chrome. However, if I play a film using movie player I have pictures but no sound.
I have also installed Wine and Spotify and again there is no sound??

Any help much appreciated.

Thanks

---

### Post by 4Orbs on 2011-09-28
Suggestion: I found it necessary to turn-off the other sound device (motherboard sound chip) in addition to selecting to activate the desired sound device. In the sound configuration (gnome mixer) click on the unwanted sound device, then in the dropdown menu select "off". This fixed it for me, however I don't have a Revo. If you only have one sound device... this post will be of no help.

---

