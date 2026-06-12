---
title: "b43 Occasionally stops working"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by benjamindaines2 on 2013-08-26
Sometimes I will come back to my computer after a period of inactivity and my internet will no longer work (I am connected to the wireless network, but no data will pass).  It will also happen from time to time when I am actively using the computer, though less frequently.  I can't see anything unusual in dmesg.  Is there a way to turn on a debug log for the b43 driver?  I am running kernel 3.10.9.  I have worse issues with the version included in 3.8.x.  

Thanks.

---

### Post by tgalati4 on 2013-08-27
What is the output of:

```
modinfo b43
```

I'm running a b43 on 12.10 without problems (kernel 3.5).  So either this is a regression with kernel 3.8 or 3.10 or there is a setting that needs to be changed.

tgalati4@Mint14-Extensa ~ $ lsmod | grep b43
b43                   369857  0 
mac80211              540032  1 b43
cfg80211              206797  2 b43,mac80211
bcma                   35657  1 b43
ssb                    52037  2 b43,ssb_hcd

Perhaps set the module parameter to debug and turn on hardware power control.  Also check your BIOS for any power saving settings for wireless.  Try turning them off.

---

