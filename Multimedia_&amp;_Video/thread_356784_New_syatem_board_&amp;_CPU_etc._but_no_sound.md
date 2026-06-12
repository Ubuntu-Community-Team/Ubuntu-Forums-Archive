---
title: "New syatem board &amp; CPU etc. but no sound"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by jbag on 2007-02-08
Hi Guys

I had a complete system failure after a storm & lost everything on my old computer.
I now have a new system & all seems to work but the sound card.
The card is on-board VIA82xx . I have been trying to get the card to work & was going through the procedure as outlined in the "Comprehensive Sound Problem Solutions Guide" but can only get so far.

I get as far as the command "sudo dpkg-reconfigure alsa-source" & the following error appears


jimbo@jimbo-desktop:~$ sudo dpkg-reconfigure alsa-source
Package `alsa-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-source is not installed
jimbo@jimbo-desktop:~$

First off ___ How do I install or find alsa-source? 

Secondly __ Upon checking within the Alsa Mixer I found the following

  Card: HDA VIA VT82xx
  Chip: Generic 1106  ID 1708
  View: PLAYBACK  CAPTURE  [ALL]
  Item: Master

  The Alsa Mixer shows 3 vertical volume controls

   Master       PCM       Capture
 
The Master is unmuted, the others have no way that I can see of muting or unmuting

I don't know if this will help but here is the rest of what I have so far

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



jimbo@jimbo-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.15-27-686/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-686 SMP preempt 686 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92
jimbo@jimbo-desktop:~$



jimbo@jimbo-desktop:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0327
        Subsystem: VIA Technologies, Inc.: Unknown device 0327
        Flags: bus master, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1327
        Subsystem: VIA Technologies, Inc.: Unknown device 1327
        Flags: bus master, medium devsel, latency 0

0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2327
        Subsystem: VIA Technologies, Inc.: Unknown device 2327
        Flags: bus master, medium devsel, latency 0

0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3327
        Flags: bus master, medium devsel, latency 0

0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4327
        Subsystem: VIA Technologies, Inc.: Unknown device 4327
        Flags: bus master, medium devsel, latency 0

0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5327 (prog-if 20 [IO(X)-APIC])
        Flags: bus master, fast devsel, latency 0

0000:00:00.6 Host bridge: VIA Technologies, Inc.: Unknown device 6327
        Flags: bus master, fast devsel, latency 0

0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7327
        Flags: bus master, medium devsel, latency 0

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <available only to root>

0000:00:02.0 PCI bridge: VIA Technologies, Inc.: Unknown device a327 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: fa900000-fe9fffff
        Prefetchable memory behind bridge: 00000000bff00000-00000000dfe00000
        Capabilities: <available only to root>

0000:00:03.0 PCI bridge: VIA Technologies, Inc.: Unknown device c327 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 32
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at ec00 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at e880 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 225
        I/O ports at e800 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 233
        I/O ports at e480 [size=32]
        Capabilities: <available only to root>

0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Flags: medium devsel
        Capabilities: <available only to root>

0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc.: Unknown device 337e
        Flags: bus master, medium devsel, latency 128
        Capabilities: <available only to root>

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 233
        I/O ports at e000 [size=256]
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fea00000-feafffff
        Capabilities: <available only to root>

0000:00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <available only to root>

0000:02:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 0271
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at fe9e0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:04:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7255
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

It looks to me as if the the card is recognized by the OS but for some reason will not work.


  If anyone can help it would be greatly appreciated.

---

