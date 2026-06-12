---
title: "Wireless packet pollution!"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by vinay_wagh on 2013-08-17
I have a Ubuntu 13.04 installed on my laptop (DELL Vostro 3700). The system has Broadcom wirelss device.
```
vinay @ vinay-laptop:~ $ lspci -nn | grep 0280
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

I have observed a very strange behaviour: Whenever I enable my wirelsss, the wi-fi connectivity of other devices is hampered. All of them get disconnected. Disabling the wi-fi of my laptop restores their connection!

I tried going through my logs, but couldnt find anything unusual there.

Has anybodyexperienced this? And/Or can anybody explain me what is happening?

Thanks in advance

VInay

---

### Post by tgalati4 on 2013-08-17
Make sure you have the correct country code set for your wireless.  Wireless G has 11 or 13 frequency bands depending on country.  If set incorrectly, that might clobber other devices.  It's also possible that the N mode is causing interference to older devices.  Or, your wireless chipset is defective, sending out too wide a frequency band that clobbers other devices.

There may be a wireless software switch for "High Interference Area" which will tighten up the frequency bands.

A google search on *bcm4313 wireless interference* provides interesting reading.  It looks like a bug in the proprietary driver for 13.04.  Use the open driver until fixed.

---

### Post by vinay_wagh on 2013-08-18
Thanks @tgalati4. 

It seems this is a bug in wireless drivers in ubuntu. The fix has been released for saucy.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1174145](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1174145)

Regards

VInay

---

