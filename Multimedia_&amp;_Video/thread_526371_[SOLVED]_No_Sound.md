---
title: "[SOLVED] No Sound"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by werdna5225 on 2007-08-15
I have absolutely no sound playing from my computer.  I know the sound works because my windows system plays just fine.  I have sound set to play when the computer starts up and nothing.  I have tried playing mp3s with rhythmbox music player, kaffiene, and gxine and nothing.  I have also installed and reinstalled mp3 codecs and many other codecs that are "hidden."  Any help would be greatly appreciated.

---

### Post by Gremlinzzz on 2007-08-15
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by werdna5225 on 2007-08-21
**[SIZE="4"]This thread did not help any, when I type aplay -l I get this:[/SIZE]**

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB PCI512 [CT4790]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB PCI512 [CT4790]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB PCI512 [CT4790]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**[SIZE="3"][SIZE="4"]and when I type in lspci -v i get this:[/SIZE][/SIZE]**

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        Capabilities: <access denied>

00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4790 SoundBlaster PCI512
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at c400 [size=8]
        Capabilities: <access denied>

00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: LeadTek Research Inc. Unknown device 6609
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at fa000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: LeadTek Research Inc. Unknown device 6609
        Flags: medium devsel, IRQ 19
        Memory at fa001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fa002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Flags: medium devsel, IRQ 20
        I/O ports at 1000 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 2200
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at e000 [size=256]
        Memory at fa003000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) (prog-if 00 [VGA])
        Subsystem: Jaton Corp Unknown device 0000
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 22
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by Gremlinzzz on 2007-08-21
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---

### Post by netron on 2007-08-22
absolutely ridiculous.
normal users shouldnt have to go through such hoops to get something as basic as sound working.  this is the year 2007 , not 1999! 

i've also got no sound - hda-intel chipset , fresh feisty install.

---

