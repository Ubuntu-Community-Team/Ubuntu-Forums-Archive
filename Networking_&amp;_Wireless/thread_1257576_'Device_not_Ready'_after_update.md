---
title: "'Device not Ready' after update"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Dumbestcrayon on 2009-09-04
My wireless was working until I did some updates

I checked this thread and I couldn't seem to get anything going

Here are my results for lsmod | grep ath

```
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  1 ath5k
cfg80211               38288  2 ath5k,mac80211
```

I noticed that he said to add athk5 to the blacklist but I don't think this is for my case or maybe mine is a little different.

If you need more information let me know.

---

### Post by superprash2003 on 2009-09-04
did it upgrade you to a new kernel?

---

### Post by Dumbestcrayon on 2009-09-06
I'm not sure, I just switched to madwifi and its working good now.

---

