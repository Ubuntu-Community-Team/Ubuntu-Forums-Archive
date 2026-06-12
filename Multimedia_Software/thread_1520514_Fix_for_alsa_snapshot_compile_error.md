---
title: "Fix for alsa snapshot compile error"
date: 2010-06-29
forum: Multimedia Software
---

### Post by nh7o_hi on 2010-06-29
For those who need more recent alsa versions than found in the stock kernel:

The snapshots have lately given a compile error, "Error 2 ...blah blah not found". The problem is in the included Makefile,  which has recently changed from what was included with 1.0.23.  Go to  line 163, which starts like:

$(MAKE) -C $(CONFIG_SND_KERNELBUILD) ........

and change it to:

$(MAKE) -C $(CONFIG_SND_KERNELDIR) .......

leaving the rest of the line the same. I found this by comparing the  Makefiles from the older and newer snapshots, and this is the only  difference. Why the change I don't know, but editing the Makefile as  above, ie reverting it to the older version, allows the compilation to  proceed normally. I just compiled the latest snapshot and it went just  fine.

---

