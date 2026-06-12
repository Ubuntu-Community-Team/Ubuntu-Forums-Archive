---
title: "How to disable RT2870 drivers"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by greencarpet on 2009-11-08
Hi
I have been having problems with connecting to (I can see them) wireless networks with my Vigor N61; By starting up with a previous kernel I can connect successfully but this breaks other things. How do I force the newer kernel to use drivers from the older kernel? Is this a blacklist thing?
Thanks

---

### Post by greencarpet on 2009-11-08
In case anyone is interested I did the following 
```

#Disable rt2800usb
blacklist rt2800usb

```

It seemed to do the trick as the wireless is now working properly. Thanks to all on this forum, there's a lot of great information out there which was a real help (even if I didn't really understand a lot of it ).
Apparently the bug has been submitted so I hope it is fixed soon.
:p

---

