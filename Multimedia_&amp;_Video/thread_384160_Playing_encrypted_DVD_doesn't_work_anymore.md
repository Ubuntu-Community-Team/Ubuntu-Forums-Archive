---
title: "Playing encrypted DVD doesn't work anymore"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by Romu on 2007-03-14
Hi all,
I'm using Edgy on my Macbook Pro and Edgy is my only computer OS.

Some weeks ago, I was able to read DVD encrypted or not without any problem.

I've updated Edgy regularly as updates was announced on the update manager, and yesterday when I tried to play a DVD I've got a GXine message : "Encrypted DVD" or something similar.

I tried to run GXine in a terminal and the trace is:

```
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000134
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004c31
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00020317
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
Xlib: unexpected async reply (sequence 0x8dd8)!
```

I ran regionset and the result is 2/0xFD.

Any help would be greatly appreciated, thanks in advance.

---

### Post by Romu on 2007-03-14
Little up, I need help, please.

---

