---
title: "No Sound, except once in gaim just now"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by charims on 2006-08-28
I have no sound whatsoever, i don't know if I am using the wrong diver or what, maybe someone can help me, but i have gone through the entire "comprehensive sound problem solutions guide" here on the forums, and to no avail. I would really like sound, and, if i can't get it using my onboard sound card, i can install some cheap old soundcard(I have a few) that will do the job too.

Okay, so here is my output from


```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK8 [NVidia CK8], device 0: Intel ICH [NVidia CK8]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8 [NVidia CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and this

```
lspci -v
```




```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel, IRQ 9
        I/O ports at e400 [size=32]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel, IRQ 177
        Memory at eb002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at eb003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at eb004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at eb001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at eb005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e8000000-e8ffffff

0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3) (prog-if 8a [Master SecP PriP])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e9000000-eaffffff
        Prefetchable memory behind bridge: d8000000-dfffffff

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2018
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant: Unknown device 2000
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at c000 [size=8]
        Capabilities: <available only to root>

```


I have been attempting to use the snd-intel8x0 driver, but i have also tried snd-ac97-bus and snd-ac97-codec.

I also ended up compiling my own driver for snd-intel8x0 as directed by the "Comprehensive sound problem solutions guide".

To no avail, nothing seems to work . I have rememberd to restart each time, to reset the sound system, but it jsut won't work.

Edit: okay, so I started my computer today, and immediately started Gaim(Instant messenger) and suddenly, i had sound. I heard the sound for sending and recieving messages. I was so amazed, i tried playing an MP3. So, i ran "MPG123 test.mp3". I heard nothing, it said it was playing. Not only that, gaim no longer made sounds after that :( . I need help bad, but i got sound for a minute, thats an improvement, right?

---

