---
title: "[SOLVED] Internal speakers continue playing when using headphones"
date: 2008-07-24
forum: Multimedia Software
---

### Post by desideratha on 2008-07-24
I am using Ubuntu Studio on a Sony Vaio Laptop. 

Internal speakers continue playing when headphones are connected!

Any help apperciated.

---

### Post by desideratha on 2008-08-15
options snd-hda-intel model=basic probe_mask=1

this is the solution, add this line to the alsa-base

---

