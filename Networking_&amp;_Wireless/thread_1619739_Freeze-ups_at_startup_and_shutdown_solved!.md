---
title: "Freeze-ups at startup and shutdown solved!"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by MARP1961 on 2010-11-12
Running Lucid 10.04 in place of XP on my old Packard Bell Imedia has been good apart from the random freeze-ups that often prevent booting or stall the shutdown process. Today I think I solved it!? It appears that my wireless PCI adapter (ZyXel G-302 v3) was causing the problem. Ubuntu had installed a default driver which seemed to work OK; but I thought I'd try installing the Windows XP driver from my original ZyXel install disk as an experiment. I used ndiswrapper, got the XP driver installed and my freeze-ups have gone (touch wood).

---

### Post by hansdown on 2010-11-12
I'll cross my fingers for you, MARP1961.

Please keep let us know if it solves your freezing.

---

### Post by MARP1961 on 2010-11-25
I can happily report no more freeze ups since installing the Windows driver for my PCI wi-fi adapter.

---

### Post by hansdown on 2010-11-25
Glad you fixed it, MARP1961

---

