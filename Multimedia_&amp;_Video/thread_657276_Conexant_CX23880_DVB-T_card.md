---
title: "Conexant CX23880 DVB-T card"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Lupin003 on 2008-01-03
lspci -v output for the dvb-t card:

```
02:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Conexant Conexant DVB-T reference design
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

02:06.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Conexant Conexant DVB-T reference design
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

```

The card seems to be installed fine (modules are loaded). I tried to scan for channels using an init file and the "scan" command (no channels found). Today i used w_scan ([http://wirbel.htpc-forum.de/w_scan/index2.html](http://wirbel.htpc-forum.de/w_scan/index2.html)) but after a while of tuning to frequencies it just said this: "ERROR: Sorry - i couldn't get any working frequency/transponder"

Anyone got ideas how i might get it work or where i should look for errors?

Edit: I forgot to mention that the card is a Geniatech T800X. The big IC on the card is labeled CX23881-19

---

### Post by Lupin003 on 2008-01-03
I just found this thread where the same card and problem is mentioned... I guess the card just doesn't work (for some mysterious reason)???

[http://g-ding.tv/?q=node/1659](http://g-ding.tv/?q=node/1659)

---

