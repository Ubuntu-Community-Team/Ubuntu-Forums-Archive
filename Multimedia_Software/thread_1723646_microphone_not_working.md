---
title: "microphone not working"
date: 2011-04-07
forum: Multimedia Software
---

### Post by secario on 2011-04-07
hi all! I have lenovo v560 laptop with installed ubuntu 10.04, everything ok except that my mic(internal, and external from my headset) doesn't work. i've checked everywhere to unmute it, installed padevchooser. tried searching through different topics in here, but still no luck. any help would be great
here are some params:
sudo lspci -v
```
 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Lenovo Device 38af
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0

```

---

### Post by secario on 2011-04-08
well, thanks a lot for your helpful advices..... problem solved with update to 10.10.

---

