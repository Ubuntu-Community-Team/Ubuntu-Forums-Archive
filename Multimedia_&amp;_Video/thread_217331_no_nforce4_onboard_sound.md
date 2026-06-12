---
title: "no nforce4 onboard sound"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by sangaya on 2006-07-17
Problem: No Sound from Onboard nForce 4 sound card

System Specs:
Dapper 6.06 32bit Edition
ABIT KN8 SLI Pro
AMD64 x2
2Gb DDR RAM

Steps Taken So Far:
 - Much reading through these forums
 - Much Google Searching
 - Following the "Comprehensive Sound Problem Solutions Guide"
 - Installed build-essential and linux-headers-`uname -r`
 - Installed the nVidia nforce drivers ([http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html))
 - Unmuted everything in alsamixer

aplay -l output
```

sangaya@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

uname -r output
```

sangaya@ubuntu:~$ uname -r
2.6.15-26-server
sangaya@ubuntu:~$

```

lspci -v output
```

sangaya@ubuntu:~$ sudo lspci -v
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [01e0]
        Capabilities: [e0] #08 [a801]

0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at bc00 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: [44] Power Management version 2

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 74
        I/O ports at cc00 [size=256]
        I/O ports at c800 [size=256]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at d000 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d400 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at e800 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: f4000000-fbffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at fc00 [size=8]
        Capabilities: [44] Power Management version 2

0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: fd900000-fd9fffff
        Prefetchable memory behind bridge: 00000000fd800000-00000000fd800000
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [58] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fda00000
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [58] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdc00000
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [58] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dff00000
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [58] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7100 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ac00 [size=256]
        Expansion ROM at fdf00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7120
        Subsystem: ATI Technologies Inc: Unknown device 0b13
        Flags: fast devsel
        Memory at fdfe0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]

0000:05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1b
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at fbfff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:05:08.0 PCI bridge: Texas Instruments PCI2250 PCI-to-PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 32
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=32
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fbe00000-fbefffff
        Prefetchable memory behind bridge: fde00000-fdefffff
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] #06 [0000]

0000:05:0a.0 Multimedia audio controller: Creative Labs: Unknown device 0005
        Subsystem: Creative Labs: Unknown device 0021
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at 9c00 [size=32]
        Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:06:08.0 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
        Subsystem: Unknown device 6016:2002
        Flags: bus master, medium devsel, latency 32, IRQ 66
        Memory at fbeff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:06:08.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
        Subsystem: Unknown device 6016:2002
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at fbefe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:06:08.2 USB Controller: NEC Corporation USB 2.0 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Unknown device 6016:2001
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at fbefd000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

0000:06:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 58
        Memory at fbefc000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 8c00 [size=128]
        Capabilities: [50] Power Management version 2

```

It looks like my sound card is detected and has drivers installed.... but I'm lost as to why I still don't have sound.  Any help is extremely appreciated!

-sangaya

---

### Post by sangaya on 2006-07-17
There was a post three hours after mine about looking in /proc for hints to sound issues. I ran the command and from the output it looks like sound should work... or do I misunderstand the output?
```
sangaya@ubuntu:~$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux ubuntu 2.6.15-26-server #1 SMP Fri Jul 7 20:32:10 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
NVidia CK804 with ALC850 at 0xfe02c000, irq 74

Audio devices:
0: NVidia CK804 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC850 rev 0

```

---

### Post by sangaya on 2006-07-18
*twiddles thumb*

---

