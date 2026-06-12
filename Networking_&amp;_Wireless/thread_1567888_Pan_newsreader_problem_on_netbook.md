---
title: "Pan newsreader problem on netbook"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by manthony121 on 2010-09-04
Pan: 0.133/ Ubuntu 9.10 (netbook edition)/ lenovo S10-3t

I recently installed Pan 0.133 on my netbook.  It is abnormally slow to do simple things.
  
If I just start pan, then immediately select "File|Quit", it takes a full 2 minutes to shutdown.  During that time, "top" shows pan and at-spi-registry together using about 95% of the CPU time.  If I kill at-spi-registry, then CPU utilization of Xorg goes up so that pan and Xorg together are using 95%.

Is this a known issue with Pan?  The Lenovo has a touchscreen; could that be part of the issue?  As a side note, why is at-spi-registry running again after I disabled it with "System|Assistive Technologies Preferences|un-check "Enable Assistive Technologies"?

---

