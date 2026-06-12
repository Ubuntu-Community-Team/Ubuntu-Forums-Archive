---
title: "RT73 Drivers No Longer Available"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by Chris Riley on 2009-05-07
Hi,
I've just upgraded a laptop to Ubuntu Hardy and got rid of the Windoze bloatware. Although Ethernet good, unfortunately WLAN not working properly, although I seem to have connection to router. Following the advice at thread 848445, I tried to download drivers from serialmonkey.com, but apparently the RT2x00 drivers are not available any more.
Grateful for advice on what to do next. If anybody has a copy of the drivers, please post.

---

### Post by hajk on 2009-05-07
The SerialMonkey drivers have been supplanted by those in the rt2x00 suite of kernel drivers. The ones included with the 2.6.28 kernel (as in Jaunty 9.04) work fine, you could also check backports for a 2.6.28 kernel for your Hardy. Note that RT73 also requires firmware, the package name is something like "firmware-ralink" (or v.v).

---

