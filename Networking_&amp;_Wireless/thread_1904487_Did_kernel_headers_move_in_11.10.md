---
title: "Did kernel headers move in 11.10?"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by lordbah on 2012-01-04
For a few years now with every new Ubuntu release my network has dropped from gigabit down to 10 Mb/s until I rebuild the e1000 driver with certain flags. I've just upgraded to 11.10 and I'm unable to rebuild. The message from the e1000 Makefile says I need to install kernel-devel. Synaptic knows nothing by that name. I looked around for linux-kernel-devel, but it seems there is no such package any more? I installed linux-headers-3.0.0-15 to match the linux-image-3.0.0-15 I have installed, but e1000 still says it can't find the kernel header files in any of the expected places. Has the location of these files changed? What should I try next?

---

### Post by chili555 on 2012-01-04
Do you have linux-headers-generic installed? *make* works for me perfectly.

I assume you are building e1000-8.0.35.

---

### Post by lordbah on 2012-01-04
No, I didn't have linux-headers-generic. I wonder why. Thanks. Got e1000 built and back up to gigabit speed.

---

