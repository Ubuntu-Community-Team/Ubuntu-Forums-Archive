---
title: "Compro X200, MythTV and Ubuntu...."
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by yamagami on 2007-11-03
Hi there
I'm trying to set up a Compro X200 card in ubuntu 7.10 to work with mythTV.
I can see the card on the Device Manager but i'm not really sure its working ok. 
In MythTV it cant seem to find any channels when its scanning, though i don't get an error or anything like that. 
I can see on the compro site that they have specific drivers for mandriva and FC6, and I REALLY don't feel like  installing any of those to get a mythTV set up going.

How can I tell if the card has drivers installed ok? Anyone has experience with that card? 
MythTV wiki say they know another 2 compro cards seem to work and the fact they have linux drivers is encouraging. Just need to get it working on ubuntu and i be a happy puppy.

Thanks
Harel

l[FONT="Courier New"]spci -v
00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Compro Technology, Inc. Unknown device e000
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at cd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

00:09.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: Compro Technology, Inc. Unknown device e000
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

[/FONT]

---

