---
title: "I have to log into windows first to get wifi to connect in ubuntu 12.04"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by samthedrunk on 2012-05-15
I have a odd problem, I have just install ubuntu 12.04 in a dualboot with Win7 on my SSD hard drive. I shrank the partition and then installed.


It all works wonderfully but the problem I am having is. When I first turn on my PC and boot into Ubuntu. My PCI wifi card will not connect not matter what I do unless I boot into windows first  and then get a connection on wifi for windows then reboot again and log into ubuntu and it connects straight away first time.

I do not have to do anything in windows just let the connection start then reboot and its fixed.

Any ideas what I can do to fix this crazy problem?

---

### Post by tehchibipanda on 2012-05-15
Could you post the following results?

```
sudo lshw -C network
``````
iwconfig
```

---

