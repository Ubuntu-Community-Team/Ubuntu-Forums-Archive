---
title: "HELP: ATI=OK, nVidia=OK, ATI+nVidia=FAILED"
date: 2011-04-20
forum: Multimedia Software
---

### Post by viodea on 2011-04-20
I have a strange issue.
When I use the on-board ATI video card only, it works.
When I disable ATI and use the PCI nVidia video card only, it works.
When I use both ATI and nVidia, only ATI is working.

---

### Post by viodea on 2011-04-20
This is what I see when ATI is disable and using nVidia only.
nouveau driver is being used.

02:05.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device b091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at febe0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: **nouveau**
        Kernel modules: nvidia-96, nouveau, nvidiafb

---

### Post by viodea on 2011-04-20
This is what I see when both ATI and nVidia is used.
nvidia driver is being used.
I also got this message.
drm nouvean 0000:03:05.0 : unable to POST this chip


01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250] (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 843e
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at d000 [size=256]
        Memory at fcfe0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fce00000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

03:05.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device b091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at febe0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: **nvidia**
        Kernel modules: nvidia-96, nouveau, nvidiafb

---

### Post by viodea on 2011-04-21
bump

---

