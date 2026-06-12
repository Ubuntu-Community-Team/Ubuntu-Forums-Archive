---
title: "Suddenly No Sound.  Permissions problem?"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Saprissa on 2009-12-07
All of a sudden, I lost sound under Karmic.

Following the comprehensive solutions guide here in the forums, I get to the step 2:

```
lspci -v
```

And the result is

> 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 1207
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fc000000 [disabled] [size=64K]
    Capabilities: <access denied>

04:03.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: VIA Technologies Inc. Device 2403
    Flags: ?? devsel, IRQ 16
    I/O ports at 9080 [size=32]
    I/O ports at 9000 [size=128]
    Memory at <ignored> (32-bit, non-prefetchable) [disabled]
    Memory at <ignored> (32-bit, non-prefetchable) [disabled]
    Memory at <ignored> (32-bit, non-prefetchable) [disabled]
    Memory at <ignored> (32-bit, non-prefetchable) [disabled]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: snd-ice1724


I noticed the "<access denied> status and tried

```
sudo lspci -v
```

and the result is

> 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 1207
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fc000000 [disabled] [size=64K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] AGP version 3.0

04:03.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: VIA Technologies Inc. Device 2003
    Flags: medium devsel, IRQ 16
    I/O ports at 9080 [size=32]
    I/O ports at 9000 [size=128]
    Capabilities: [80] Power Management version 1
    Kernel modules: snd-ice1724


I am a member of the group "audio", and I don't know why this would have suddenly caused audio to stop working, but does anyone have a suggestion regarding solving the problem?

Thanks so much!

---

### Post by lidex on 2009-12-07
Can you post output of this command:
```
sudo lshw -C sound
```
Also run this:
```
alsamixer
```
and make sure levels are up/unmuted

---

### Post by Saprissa on 2009-12-07
Thanks for the assistance.

It must have been a physical problem.

I removed and reseated the sound card and sound is back. :P

Joy!

---

