---
title: "problems staying connected to my wierless."
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by ebola42 on 2013-01-29
i am running 12.04 and can't seem to work out my connection issue, connects and seems to work fine, then just drops. i've been trying some possiable fixes from different post. so far i can't seem to find the right one?  strait install on 12.04 (no windows) on hp pavilion g6, broadcom wireless. thanks, Cole

---

### Post by Warren Hill on 2013-01-29
One possibility is interference from other Wifi hot spots try

```
sudo iwlist scan | egrep 'Channel | ESSID'
```
Enter password when requested

You should get something similar to this

```
$ sudo iwlist scan | egrep 'Channel | ESSID'
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                    Frequency:5.18 GHz (Channel 36)
                    ESSID:"HS-1gid46vaylveagu59b3ks232h"
                    Frequency:2.412 GHz (Channel 1)
                    ESSID:"TALKTALK-63A526"
                    Frequency:2.472 GHz (Channel 13)
                    ESSID:"1gid46vaylveagu59b3ks232h"
```

Are there other Wifi hot spots using the same channel as you ?

If there are try changing the channel number in your router

---

### Post by ebola42 on 2013-01-29
thanks warren.  no, but it is showing my wireless twice? that might be the problem. not sure how to fix that. thanks again. any little bit of info helps. Cole

---

