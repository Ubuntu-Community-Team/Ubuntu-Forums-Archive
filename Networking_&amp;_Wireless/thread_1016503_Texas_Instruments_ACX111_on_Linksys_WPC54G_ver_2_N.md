---
title: "Texas Instruments ACX111 on Linksys WPC54G ver 2: Not recognized on LiveCD?"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Psycho Sonic on 2008-12-20
I tried the Heron LiveCD today on Kubuntu, and it didn't recognize my PCMCIA wireless card, even though the hardware page says that it's supported out of the box. Any reason for this, or is it just because it's the LiveCD?

---

### Post by Psycho Sonic on 2008-12-20
Guess I'll bump this. Just wanna know if it's because of the LiveCD.

---

### Post by Ayuthia on 2008-12-20
You can check and see if it is listed when you go into the Terminal
```
lspci
lspcmcia
lsusb
```It should show up under one of them.  I can't recall if it is a Broadcom or Atheros chipset.

Most likely, you could activate it through System->Administration->Hardware Drivers.

---

