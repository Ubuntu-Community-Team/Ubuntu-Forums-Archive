---
title: "No Sound from Panasonic CF29 Toughbook Notebook"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by kw1502 on 2006-10-07
I cannot get the sound working on my Panasonic CF29 Touchbook notebook using 6.06.1. The sound card is the Intel 82801DB-ICH4 and I've included the outputs of the aplay, lspci and lsmod commands and have followed the steps per the "Comprehensive Sound Problems Solutions Guide" by LordRaiden. I've also verified that the sound is not muted and have checked all settings using alsamixer all with no success. Any help would be greatly appreciated.

ken@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ken@ubuntu:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, fast devsel, latency 0
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc essor to I/O Controller (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc essor to I/O Controller (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, fast devsel, latency 0

0000:00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor t o AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated  Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphi cs Device (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1840 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, medium devsel, latency 0, IRQ 9
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (pro g-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 03)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: medium devsel, IRQ 9
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8346
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corporation: Unknown device 2701
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at 3000 [size=256]
        Memory at e0201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

ken@ubuntu:~$ lsmod | grep snd
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm


:confused:

---

### Post by kw1502 on 2006-10-26
I could never this to work with Dapper but it "just works" in Edgy!

---

