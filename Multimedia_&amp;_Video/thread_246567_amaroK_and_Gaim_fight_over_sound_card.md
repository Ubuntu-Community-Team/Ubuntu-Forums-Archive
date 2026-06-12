---
title: "amaroK and Gaim fight over sound card"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by The Warlock on 2006-08-29
When amaroK is playing, Gaim can't make sounds, and vice versa. If I switch everything over to ESD, my music starts skipping (probably too much of a strain on my system). Any way to fix this without resorting to ESD?

---

### Post by gustolove on 2006-08-29
I have the same issue, I can only get one application to use the sound card at a time. It's a really common issue it seems because I've found numerous posts about it on these forums. I have yet to find a fix for it though. Someone please help.

Nforce 4 board (Gigabyte A8N-SLI)

And when i do lspci i get:

```
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d2003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

and for aplay -l i get: 
```
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC95 8]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

