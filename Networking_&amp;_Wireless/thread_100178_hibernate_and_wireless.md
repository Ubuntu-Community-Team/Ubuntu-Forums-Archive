---
title: "hibernate and wireless"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-12-07
I finally sat down to try to get suspend2 working with my laptop, following the directions <a href="http://www.ubuntuforums.org/showthread.php?t=75443&highlight=suspend2">here</a>. However, upon patching my kernel, my wireless interface (ipw2200) was simply not recognized. That is, if I ran ifconfig, it would display lo, eth0, and sit0, but not eth1 (which has always been what my wireless device has been configured as).

I've looked and looked again through the kernel config options, but I don't see anything that would be causing the card not to be recognized. The ip2200 module is loaded.

I'd love to get suspend2 working with networking, so any ideas?

---

### Post by daller on 2005-12-07
Try running "modprobe ipw2200"

---

### Post by Strife on 2005-12-07
Well, the module is already loaded.

But I did already try that, and there was no change.

---

### Post by Strife on 2005-12-07
Okay, so it turns out that somehow the problem is related to ieee80211 modules not building (I don't know how I proceeded last time building the kernel...). But anyay, I get this error:

make[4]: *** No rule to make target `drivers/net/wireless/ieee80211/ieee80211_module.s', needed by `drivers/net/wireless/ieee80211/ieee80211_module.o'.  Stop.

Now obviously I need this module to be able to have wireless support. This is trying to build kernel 2.6.12.

Any ideas as to what the problem might be?

---

