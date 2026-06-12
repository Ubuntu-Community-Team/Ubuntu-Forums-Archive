---
title: "Wireless card not working and no access to internet to fix it"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by hanning on 2012-06-24
Hello folks,

Like it says, I recently did a new clean install of 12.04 from 10.04 and my wireless card has stopped working.

Usually you can fix this by downloading/installing various things, but my problem is that I have no physical access to the router so can't use an ethernet connect to do this. Right now I'm typing this from my 2nd computer with working wifi.

Possible pertinent details, but let me know what other outputs are handy.

product: BCM4311 802.11b/ WLAN
vendor: broadcom corporation

---

### Post by chili555 on 2012-06-24
Please run and post:```
lspci -nn | grep 0280
```Look in the drawer and dust of that old USB key, we'll need it in a few moments.

---

### Post by hanning on 2012-06-24
```
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

---

### Post by chili555 on 2012-06-24
> Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]]Please follow the process here: [http://ubuntuforums.org/showpost.php?p=12013510&postcount=4](http://ubuntuforums.org/showpost.php?p=12013510&postcount=4)

---

### Post by hanning on 2012-06-24
Thank you so much!

---

### Post by chili555 on 2012-06-24
> **hanning said:**
> Thank you so much!So does that mean it's all fixed and you are a happy penguin? Would you care to use thread tools at the top and mark Solved? Certainly post back if you need additional assistance.

[http://en.wikipedia.org/wiki/Tux](http://en.wikipedia.org/wiki/Tux)

---

