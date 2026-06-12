---
title: "ATI Quad Monitor Support"
date: 2012-11-05
forum: Multimedia Software
---

### Post by 3gotist on 2012-11-05
Backstory: At work, we use dual ATI graphics cards (HD 5450 in my case) with DMS-59 connectors to enable the use of up to four displays in Windows via DMS-59 to dual DVI Y-Cables. 

I can't seem to get the same functionality in Ubuntu 12.10 with any driver (proprietary or open source). Can anyone walk me through troubleshooting this issue? I'd really like to make Ubuntu my primary work OS, but I can't do that if I only have two out of four displays working correctly. My personal PCs are all nVidia-based (having been painfully instructed by personal experience that Linux and AMD/ATI graphics solutions are not much fun), so I have no experience with even the GUI options in Catalyst Control Center.

---

### Post by 3gotist on 2012-11-07
Still looking for a solution on this. Can anyone point me in the right direction?

---

### Post by 3gotist on 2012-11-26
Bump again. Anyone?

---

### Post by QIII on 2012-11-26
When you installed the ATI fglrx driver, did you do```
sudo aticonfig --adapter=all --initial
```

---

