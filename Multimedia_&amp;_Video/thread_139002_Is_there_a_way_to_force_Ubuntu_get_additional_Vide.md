---
title: "Is there a way to force Ubuntu get additional Video Memory from my RAM?"
date: 2006-03-03
forum: Multimedia &amp; Video
---

### Post by kenweill on 2006-03-03
How can I force Ubuntu to get additional Video Memory from RAM?
Is that possible?

In my BIOS, I can only set the Video Shared Memory until 32MB. Ubuntu(running Cedega) detected it only as im having Video Memory of 32MB only.

Under RH9, same. Only, I can set it to higher, until 64MB. How can I do the same here in Ubuntu?

I have tried running "sudo dpkg-reconfigure xserver-xorg" to no avail.
Still Cedega detects 32MB.

Is there a way to force Ubuntu get additional Video Memory from my RAM?

---

### Post by az on 2006-03-03
From recovery mode run

dpkg-reconfigure xserver-xorg

You can tell it how much memory to use, but I doubt that your card will actully use that.  I don't think the driver can override the physical limitations of the card.

---

### Post by torx on 2006-03-03
I'm not sure, but i think you can tweak MTRR (/proc/mtrr)?

Again, i'm not sure.

---

### Post by kenweill on 2006-03-04
[QUOTE=torx]I'm not sure, but i think you can tweak MTRR (/proc/mtrr)?

Again, i'm not sure.[/QUOTE]

Here's my /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size= 256MB: write-back, count=1
reg02: base=0x2df80000 ( 735MB), size= 512KB: uncachable, count=1
reg03: base=0x2e000000 ( 736MB), size=  32MB: uncachable, count=1
reg04: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=2

What should I do with this?

---

