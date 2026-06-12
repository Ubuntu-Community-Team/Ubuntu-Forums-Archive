---
title: "kernel module sbb and broadcom 'wl' driver"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by JohnLloydJones on 2010-01-04
After I upgraded my Dell Studio 1535 to Karmic, I lost my wireless connection (ifconfig didn't even list eth1). After much searching, I find that the broadcom wireless driver 'wl' is loading, but the wpa_supplicant reports "Unsupported driver 'wl'.". Odd, because it is one of the drivers listed as being supported. As I was almost ready to give up, I found a reference to modules that need to be blacklisted and discover that one -- sbb -- is loaded. Immediately on removing sbb, my wireless connection starts up. 

Now the question: By removing (and blacklisting) sbb, am I going to cause myself problems? I have no clue what sbb does and if, sometime in the future, I will have grief because it's not there.

---

