---
title: "OpenGL &quot;missing pixels&quot; but only red &amp; blue (pic)"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by forek on 2007-06-01
**Update:**  Turns out the card was bad.  I swapped it out with another one and the checkerboard problem went away.

**Original post:**  I'm having troubles with anything OpenGL.  The red and blue have "missing pixels", resulting in a grainy picture.  The green is fine.  Has anyone seen anything like this?

[IMG]http://img357.imageshack.us/img357/5444/ubuntuatiopenglgrainycr6.png[/IMG]

I'm on Feisty and installed the fglrx driver using restricted-manager (although it happens with the radeon driver as well).  Here's some info:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

$ glxinfo |grep direct
direct rendering: Yes

$ lspci -vv
...snip...
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 0082
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 80000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 2000 [size=256]
        Region 2: Memory at 88110000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at 88120000 [disabled] [size=128K]
        Capabilities: <access denied>
...snip...

```

Anyone have any ideas what could be happening?

---

