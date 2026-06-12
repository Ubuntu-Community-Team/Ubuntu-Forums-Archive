---
title: "Kino not grabbing DV from Canon MVX450"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by cd-r80 on 2007-04-01
I have loaded dv1394 & raw1394. Still Kino says:
WARNING: dv1394 module not loaded or cannot read /dev/dv1394/0.

What I'm missing, so I can grab my DV from Canon MVX450 (Elura)?

lspci
0000:00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

Edit: Ok I found the reason: There is no /dev/1394/0 it is /dev/1394-0.

---

### Post by sysyphus on 2007-04-08
Hi I've got a similar problem with kino, how did you fix this?

---

### Post by cd-r80 on 2007-04-09
I haven't got Kino working. I have tried many manuals and versions.

---

