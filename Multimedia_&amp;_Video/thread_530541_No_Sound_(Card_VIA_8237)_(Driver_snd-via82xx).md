---
title: "No Sound (Card: VIA 8237) (Driver: snd-via82xx)"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by ultimut on 2007-08-20
I am having trouble.  This is my situation on Feisty:

**$ aplay -l**
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

```


**$ lspci -v**
```

$ lspci -v
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
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        Capabilities: <access denied>

00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at fc00 [size=32]
        Capabilities: <access denied>

00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at f800 [size=32]
        Capabilities: <access denied>

00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0a.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
        Subsystem: Risq Modular Systems, Inc. Riptide PCI Audio Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at f400 [size=64]
        Capabilities: <access denied>

00:0a.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
        Subsystem: Risq Modular Systems, Inc. Hewlett Packard DF
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

00:0a.2 Input device controller: Rockwell International Riptide PCI Game Controller
        Subsystem: Risq Modular Systems, Inc. Riptide PCI Game Controller
        Flags: bus master, medium devsel, latency 0
        Memory at fdffe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at f000 [size=8]
        I/O ports at ec00 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e400 [size=4]
        I/O ports at e000 [size=16]
        I/O ports at dc00 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 19
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at d800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at fdffd000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 8213
        Flags: medium devsel, IRQ 22
        I/O ports at c400 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 21
        I/O ports at bc00 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 1351
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

**$ cat /etc/modules**
```

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
snd-via82xx

```


**$ grep 'audio' /etc/group**
```

$ grep 'audio' /etc/group
audio:x:29:swill

```
(that is the correct username)

[LIST]
[*]I have attempted the **Getting the ALSA drivers from a *fresh* kernel** section as well.  It did not work for me...
[*]I have checked that the **.asoundrc** file is not in my home directory (it never was).
[*]**alsamixer: **I tried with **external amplifier** turned on and off.
[*]**alsamixer: **I tried with settings: all on full, PCM at 80%, with many other combinations.  I have tried all settings I can think of.  I have tried with the IEC958 switches on and off.
[/LIST]

Still TBD:
I read somewhere in here something about the **snd-via82xx** driver having problems with the channels or something along those lines.  something about using channel two instead of channel 1.  I am not entirely sure if that is the case, but I am not sure how to test it.  

I have been working on this problem all day and I really need to find a solution soon or I am going to go insane...  If anyone has any ideas, suggestions or can just point out why I am an idiot for missing something in the above, PLEASE let me know...

Thanks...

---

### Post by ultimut on 2007-08-21
Another quick comment:
Does anyone have the PDF of the manual for a BIOSTAR P4M800Pro-M7 Motherboard?  I have tried to get it online and I have had no luck.  I have also tried to have their support team send it to me, and they have yet to reply.  

The reason is because I do not have the manual and I would like to make sure that my audio jumpers are set up correctly.  

For that matter, if anyone has that board and has sound working on it, can you give me your jumper configuration so I can confirm mine is right.

Thanks...

---

### Post by ultimut on 2007-08-22
Just wanted to post what the problem was in case anyone is following this thread.  

Everything was set up correctly in terms of the software etc.  The problem is that the motherboard had the wrong jumper placement.  On my board the jumpers needed to be in 5, 6 and 9, 10...  So it looks like this if you see it on the board.  (left is 1,2 and right is 13, 14)
: : [] . [] : :

Hope this helps someone who is also having these issues...  Cheers...

---

### Post by mefoo on 2007-08-28
Good thing I read this thread to the end. I'll give this a shot. I wonder if it's a mobo independent fix or what? I have biostar micro k8m800 -> POS.

---

