---
title: "network monitor 2.12 and broadcom card"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by dubbreak on 2006-06-07
I've been running dapper since flight 5 iirc and network monitor is now acting up on me. Previously I was able to use it to configure my card (broadcom wireless bcm43xx) with no problems, but now it will just sit there when I try to change anything (ie essid) and will not grab an ip.

If I go through the motions manually:
```
sudo iwconfig eth1 essid myrouter
sudo dhclient eth1
``` 
It will work without any problems.
Once in a while I will also run:
```
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 ap any
```
but depending on where I am connecting it is unnecesary.

Any ideas why network monitor is failing to apply settings?

---

### Post by dubbreak on 2006-06-10
Bump.. no one having similar problems?

---

### Post by OldSpiceAP on 2008-06-24
Same issue here but can't find much information on it. Works fine some places others, I have to enter that in the console as well.

---

