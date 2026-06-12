---
title: "Scan Channels button doesn't work in mythtv-setup with pinnacle hybrid Pro"
date: 2009-10-11
forum: Mythbuntu
---

### Post by paulhurleyuk on 2009-10-11
Hello,

I've setup a mythbuntu karmic beta system to try things out and I can't get myht to scan for channels.  The hardware is a HP compaq Evo D530 PC which has an Intel 82865G chipset, which seems to have a choppy time of things (I couldn't do a straight install due to video issues with the chipset, so installed 9.04 and upgraded to 9.10, then installed the video for linux drivers using mercurial and downloaded the relevant firmware.)

I've setup the Analogue V4l side of the stick in mythtv setup and the UK RT XMLTV grabber, but when I match them up and click the scan for channels button, nothing happens.

As an aside tvtime won't run with a hardware overlay error, but xawtv does, and works, so the stick seems to work).

Please ask if I've missed anything.

Thanks

Paul.

```
uname -a
Linux mythb 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux

```
```

lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
 Subsystem: Hewlett-Packard Company Device 12bc
 Flags: bus master, fast devsel, latency 0
 Memory at f8000000 (32-bit, prefetchable) [size=64M]
 Capabilities: <access denied>
 Kernel driver in use: agpgart-intel
 Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Subsystem: Hewlett-Packard Company Device 12bc
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at f0000000 (32-bit, prefetchable) [size=128M]
 Memory at fc400000 (32-bit, non-prefetchable) [size=512K]
 I/O ports at 14e0 [size=8]
 Capabilities: <access denied>
 Kernel driver in use: i915
 Kernel modules: i915
```

---

