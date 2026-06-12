---
title: "Wireless adaptor speed too slow"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by bean1945 on 2009-11-14
I have just upgraded my wireless router from a Linksys WRT 45 G to a D-Link  DIR-655
Xtreme N Gigabit router. Comcast has upgraded our donload speeds  and both  our Toshiba  Satellite (Vista) and MSI netbook (XP)  that are wireless n equipped  are indicating download speeds  on the order of 10-20 Mbits/sec  (upload around 3 Mbits/sec).However I have added a D-link Xtreme N Desktop adaptor DWA-552 to my Dell Dimension 3000  (Ubuntu 9.04) and the download speeds are consistenly less than the upload speeds (using same  speed test site on all 3 machines). Any suggestions on what might cause this problem?

---

### Post by bean1945 on 2009-11-23
The problem is due to the native driver installed by UBUNTU (ath9k).
I installed a windows driver using ndiswrapper and now the download speeds are greater than the upload speeds  (as on our other two windows OS machines with n cards) and both much greater than with  the ath9k driver. However ndiswrapper installed a g driver instead of the n driver  (probably becasue the D-Link 552 adaptor is so new). Any way I hope this saves others the  waste of time.

---

