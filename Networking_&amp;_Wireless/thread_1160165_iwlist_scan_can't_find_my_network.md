---
title: "iwlist scan can't find my network"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by e&gt;&lt;ogenic on 2009-05-15
I'm kind of following on from [http://ubuntuforums.org/showthread.php?t=1159121](http://ubuntuforums.org/showthread.php?t=1159121) where another community member helped me get a driver for my wireless adapter working.

Even though everything appears to be working correctly, I can't get iwlist scan to return any results. I'm told this might be down to the physical locations of the adpater and router, but both work totally fine in Windows (I'm dual-booting with XP Home SP3 at the moment).

Is there anything I can do about this, or am I doomed to no internet in Ubuntu until I can afford network hardware that's more compatible?

---

### Post by superprash2003 on 2009-05-15
what is the output of iwlist command?? could you post it.. did you add sudo?

---

### Post by e&gt;&lt;ogenic on 2009-05-15
I tried it with and without sudo and the ouput is the same for both:

```
exogenic@deadbox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

exogenic@deadbox:~$
```

---

### Post by e&gt;&lt;ogenic on 2009-05-15
You can safely ignore this thread. My bad - I posted whilst trying to do a million-and-one things at the same time and ommitted all relevant info.

*slaps self on wrist*

New thread with all info included is [http://ubuntuforums.org/showthread.php?p=7285306](http://ubuntuforums.org/showthread.php?p=7285306) so please post anything helpful there :)

---

