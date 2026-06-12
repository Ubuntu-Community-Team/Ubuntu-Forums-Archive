---
title: "KWorld/Vstream Xpert DVB-T... halp"
date: 2009-03-30
forum: Multimedia Software
---

### Post by epidemiks on 2009-03-30
Just wacked in a KWorld/Vstream Xpert DVB-T card, and a bit lost really..
linuxtv wiki seems to be lacking in depth info on getting this card to run.. what exactly do I need to do?
Any help appreciated.

lspci -vnn  
```
00:0b.0 Multimedia video controller [0400]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
        Subsystem: KWorld Computer Co. Ltd. KWorld/VStream XPert DVB-T with cx22702 [17de:08a1]
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at eb000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

00:0b.2 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
        Subsystem: KWorld Computer Co. Ltd. XPert DVB-T PCI BDA DVBT 23880 Transport Stream Capture [17de:08a1]
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

```

---

### Post by whollygrael on 2011-02-09
Did you ever get your KWorld/Vstream card working.  I have the same card and have been trying to get it to work for about a fortnight now, without any success.

---

