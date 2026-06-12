---
title: "Sound Stops Then Starts"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by RSL on 2006-10-16
ARG! I've had it up to here [points to two inches above my head] with Ubuntu sound issues. I'm sure I should consider myself lucky to even HAVE sound looking at some of the threads on the board. However, it's really annoying that my sound works then stops then starts then stops. Here's the rundown...

1. Fresh install. Sound works GREAT! Everything rocks!
2. Setup everything just like I like. Sound still rockin'!
3. Actually get to work on my WORK [not just screwing around with Linux]. Sound's still there.
4. Random system upgrade/update via Synaptic. Never has anything to do with sound but inexorably leads to the disruption of my sound.
5. GOTO 1

There's got to be a better way. It's really hard to evangelize an OS that has such buggy issues with basic stuff like sound. What the heck!? Anyhow...

Here's my "aplay -l" results:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

"lspci -v":

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: fast devsel
        Memory at 30000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at fff80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        I/O ports at fff8 [disabled] [size=8]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at c800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at cc00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d000 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at ffaff400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: c6b00000-e6afffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 38000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 169
        I/O ports at ec00 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at dc00 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: medium devsel, IRQ 9
        I/O ports at d800 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 209
        Memory at ffaffc00 (32-bit, non-prefetchable) [size=512]
        Memory at ffaff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA])
        Subsystem: Diamond Multimedia Systems Unknown device 0160
        Flags: bus master, medium devsel, latency 32, IRQ 225
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b800 [size=256]
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c6b00000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
        Subsystem: Diamond Multimedia Systems Unknown device 0161
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at ff890000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

01:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Adaptec Unknown device 0030
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at ff8ee000 (32-bit, non-prefetchable) [size=2K]
        Memory at ff8e8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

01:02.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys Unknown device 0574
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at b400 [size=256]
        Memory at ff8eec00 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at c6b20000 [disabled] [size=128K]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 32, IRQ 217
        Memory at ff8ef000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=64]
        Capabilities: <access denied>
```


Help!? Anyone!? PLEEEEEEASE? I really don't want to reinstall the OS just to get back my sound. Temporarily. But I can't figure this one out. :/

---

### Post by Kateikyoushi on 2006-10-16
Did you try to play around with alsamixer ?
Might be that something got turned off.

---

### Post by RSL on 2006-10-16
I've tried that many times but it doesn't affect anything. Neither does a --purge remove of the linux-sound-base alsa-utils and alsa-base. [Reinstalling them too, of course.]

And, just to clarify, it's not that I have NO sound but that the sound goes in and out. I wish I knew how to record what it's doing. It'll play about half a minute or so then stop for a long time then suddenly start again but starting from the place it stopped then skipping ahead a bit. Sigh. It's really leaving a bad taste in my mouth for Ubuntu. Do all Linux distros have this history of sound problems?

---

### Post by RSL on 2006-10-16
Could this have anything to do with this problem? I can't see how but there WAS an upgrade of xserver-xorg this morning right before the problems started today.

```
rsl@sneaky:/etc/apt$ amarokapp
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
STARTUP
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c2807a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c284ed
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c287c4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c28a7f
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c292e2
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c29d99
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c2a25d
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c2a6a1
```

---

