---
title: "Two DVB-T Cards not working together"
date: 2007-11-19
forum: Mythbuntu
---

### Post by s_g_robertson on 2007-11-19
I am trying to set up a MythTV box and it has all been going very well until I've tried to add a second tuner card.

I'm using two Hauppage Nova-t terrestrial digital decoders. Identical models.

The relevant output from lspci


```
00:0b.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Unknown device 9002
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Unknown device 9002
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
```

Both cards work if they are in the machine by themselves but when they are both in at the same time, one of them can never get a lock when it is being tuned in.


Any suggestions?

---

### Post by foxbuntu on 2007-11-19
This sounds like a hardware resource conflict on your PCI Bus. Can you try moving the cards so an empty PCI slot seperates them?

---

