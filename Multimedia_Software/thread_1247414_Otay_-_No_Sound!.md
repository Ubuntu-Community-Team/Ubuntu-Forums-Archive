---
title: "Otay - No Sound!"
date: 2009-08-22
forum: Multimedia Software
---

### Post by c5vetter on 2009-08-22
relative newb to Ubuntu - finally got OS loaded, and figured out how to get wireless working, etc. - attempted to get sound working the last couple of days following the Guide - had soundcard recognized, but tonite when login NO SOUNDCARD!!!!!

so, back to the Guide, and this is what I have done so far.........not looking good, so someone needs to steer me here!

opened terminal and typed lspci - v | less and got the following:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Device 30a5
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT 
Express PCI Express Root Port (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

so, where to from here?

---

### Post by c5vetter on 2009-08-22
otay - started over and went into terminal and typed aplay -l

it is worse than I thought NO SOUNDCARD FOUND!

---

