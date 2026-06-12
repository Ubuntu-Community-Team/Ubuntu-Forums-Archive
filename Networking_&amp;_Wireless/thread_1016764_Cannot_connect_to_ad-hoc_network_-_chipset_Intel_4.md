---
title: "Cannot connect to ad-hoc network - chipset Intel 4965AGN - Intrepid 64bit"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by louis_nichols on 2008-12-20
Hi!

I just got a new laptop HP DV6930us with a wireless chipset Intel 4965AGN and I installed Intrepid 64 bit on it. It works well in general. However, wireless is buggy.

Basically, I can connect to infrastructure networks but not to ad-hoc. It keeps asking for the password although I have entered it a thousand times and I KNOW I get it right. And I really need this.

I saw several discussions on the web about this chipset and the driver iwl4965 but I am not sure whether I should install that driver, since wireless partly works. I am thinking perhaps it is a configuration thing. Here is my lsmod:
```
myself@Ubuntu:~$ lsmod | grep iwl
iwlagn                113668  0 
iwlcore               105540  1 iwlagn
rfkill                 19364  2 iwlcore
led_class              13192  1 iwlcore
mac80211              253440  2 iwlagn,iwlcore
cfg80211               37136  3 iwlagn,iwlcore,mac80211

```


Does anyone have any suggestion?

---

