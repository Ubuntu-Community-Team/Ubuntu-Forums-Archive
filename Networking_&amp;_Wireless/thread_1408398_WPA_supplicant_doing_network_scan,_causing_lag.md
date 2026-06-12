---
title: "WPA supplicant doing network scan, causing lag"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by thelawenforcer on 2010-02-16
Hi,

I made a post recently about periodical Wireless lag.

Ive found the root of the problem. 

Its the wpa_supplicant scanning for other networks every two minutes.

Feb 16 16:00:40 law-desktop wpa_supplicant[871]: CTRL-EVENT-SCAN-RESULTS 
Feb 16 16:02:39 law-desktop wpa_supplicant[871]: CTRL-EVENT-SCAN-RESULTS 
Feb 16 16:04:39 law-desktop wpa_supplicant[871]: CTRL-EVENT-SCAN-RESULTS 
Feb 16 16:06:39 law-desktop wpa_supplicant[871]: CTRL-EVENT-SCAN-RESULTS 
Feb 16 16:08:39 law-desktop wpa_supplicant[871]: CTRL-EVENT-SCAN-RESULTS 

I was told that to stop this i would have to stop using WPA encryption. But i dont think this has to do with WPA encryption, i think its just scanning for different available networks. 

How can i stop this scan whilst still being able to use WPA?


*EDIT: I Downloaded Wicd, and this seems to have fixed the problem.

---

