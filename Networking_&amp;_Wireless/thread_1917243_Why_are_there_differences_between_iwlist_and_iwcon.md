---
title: "Why are there differences between iwlist and iwconfig?"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2012-01-29
Sitting a few metres away from my wifi access point, I can use iwconfig and record Link Quality as 92/100 (92%). This figure is validated by examining /proc/net/wireless.

However, when I run "iwlist eth1 scan" Quality is 46

Now, its possible that the iwlist result is scaled differently (i.e. 2 x 46 = 92) except that a neighbouring access point returns Quality: 67.

The results for Signal Level are also different. iwconfig looks realistic (-65dBm), while iwlist just returns 0.

'Buntu uses wireless-tools version 30 pre 9 which seems to be the latest Beta (Oh dear!).
Also, I think there are differences between drivers (I'm using ipw2100) so maybe this is where the problem is?

Can anyone explain...or at least do this check on their computer?

---

