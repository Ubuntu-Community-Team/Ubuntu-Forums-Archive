---
title: "No Sound"
date: 2008-05-25
forum: Multimedia Software
---

### Post by kinpower on 2008-05-25
Hi, I appear to be having a problem with no sound on my ubuntu 7.10
I have gone through a fw of these comprhensive guides for fixing this, but nonne have helped, could just be me doing something wrong but i don't know
I use VLC for all music and movies because none of the others work for me
when I write lspci -v in the terminal I get
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e8100000-e81fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at e8001000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at e8002000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1a)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: 66MHz, medium devsel
        I/O ports at 8060 [size=16]
        Memory at e8004000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8070 [size=16]

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=68
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8200000-e82fffff
        Prefetchable memory behind bridge: 30000000-33ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at e8004400 (32-bit, non-prefetchable) [size=256]

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at e8004800 (32-bit, non-prefetchable) [size=256]

01:05.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at e8200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at a400 [size=128]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 128, IRQ 18
        I/O ports at a000 [size=256]
        Memory at e8200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e8202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 0000a800-0000a8ff
        I/O window 1: 0000ac00-0000acff
        16-bit legacy interface ports at 0001

02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e8200c00 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at e8201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e8201400 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

and aplay -l give me
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
I am using a Toshiba Satellite p30-141 Laptop

Thanks in Advance
Nik

---

### Post by kinpower on 2008-05-25
That Problem is now gone, but now i have a new problem, whenever I start a new program, of go to a new page in opera, music stops for about 15 seconds, anyone have an idea why and also how to fix it

---

### Post by Whydoe on 2008-05-25
Looks like a similar problem that I'm having because my sound card and modem share the same IRQ.  Apparently, changing the PCI slot works sometimes, but I have yet to do that.  If it works though, let me know.

---

### Post by leodido on 2008-05-25
I have the same problem with VLC, but this is odd because i can play Mp3 in audacious but when i try to play a divx i get the picture but no sound!

---

### Post by kinpower on 2008-05-25
wooooo, more problems, whenever I play a DVD i get sound for a little bit, then it goes away :(, it ocasianly comes back by itself, and it comes back if i go into prefrences, alsa, reselect my sound thing and then save :confused: but only for a little bit then goes again and is replaced by some buzzing

---

