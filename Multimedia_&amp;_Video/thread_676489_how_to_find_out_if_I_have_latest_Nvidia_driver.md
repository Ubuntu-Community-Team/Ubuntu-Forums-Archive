---
title: "how to find out if I have latest Nvidia driver?"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by neatokino on 2008-01-23
I'm successfully running a 7300GT card with Gutsy, but I don't know if I have the latest driver.  Can someone tell me how to find out which driver I have, if it's the latest version of the driver, and, if not, how I upgrade it.

My restricted drivers manager window says I have the NVidia proprietary driver, but it doesn't tell me anything else about it.

If I don't have the latest version of the driver, is there any reason to upgrade?  The card works well with compiz, etc. and is just slightly glitchy when I watch DVDs (could just be limitations of the card).

TIA

Michael

---

### Post by chewearn on 2008-01-23
Open a terminal, run:
```
nvidia-settings
```The driver version will be right in there.


Don't mess with it, it it ain't broken.  (enough people has come to grief with these closed source drivers [-o<).

.

---

