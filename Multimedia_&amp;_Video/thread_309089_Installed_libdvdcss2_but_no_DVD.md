---
title: "Installed libdvdcss2 but no DVD"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by rpradeep on 2006-11-29
I  have installed gxine and w32codecs. ALso libdvdcss2 from .deb file.
But when i start dvd it says "are you trying to play a encrypted dvd without libdvdcss2" (something similar)

Please help me!

---

### Post by DerHesse on 2006-11-29
.. probably becaus you installed a .deb-file without dependencies. 
Ad restricted/universe repositories to your sources list and use synaptic.

Give a try to mplayer. :D

---

### Post by az on 2006-11-29
> **rpradeep said:**
> I  have installed gxine and w32codecs. ALso libdvdcss2 from .deb file.
But when i start dvd it says "are you trying to play a encrypted dvd without libdvdcss2" (something similar)

Please help me!

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You need to run a script to enable decryption:
[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by rpradeep on 2006-12-01
Thanx the script works fine.
However the response of gxine is very very slow. Totem is ok but non smooth movie flow.
Any idea?

---

