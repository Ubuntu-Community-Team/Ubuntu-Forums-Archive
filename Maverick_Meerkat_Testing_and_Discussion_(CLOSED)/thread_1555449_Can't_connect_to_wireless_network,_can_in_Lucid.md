---
title: "Can't connect to wireless network, can in Lucid"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by fluteflute on 2010-08-18
Network manager cannot connect to my home wireless network, secured by a "WPA Pre-shared key" under Maverick. No difficulties under Lucid.(WAG354C router, WUSB54GC 'dongle')

Just wondering if anyone was having any similar issues, where networking works fine in Lucid, but not in Maverick?

---

### Post by lonniehenry on 2010-08-18
Try the suggestions in this post.  I had to do this in Lucid but not in Maverick with the usb dongle that I use. (Slightly different version number)  [http://ubuntuforums.org/showthread.php?t=1492307&highlight=WUSB54GC&page=2](http://ubuntuforums.org/showthread.php?t=1492307&highlight=WUSB54GC&page=2)

---

### Post by dxxvi on 2010-08-19
I have the same problem but don't know how to fix.

---

### Post by fluteflute on 2010-08-19
> **lonniehenry said:**
> Try the suggestions in this post.  I had to do this in Lucid but not in Maverick with the usb dongle that I use. (Slightly different version number)  [http://ubuntuforums.org/showthread.php?t=1492307&highlight=WUSB54GC&page=2](http://ubuntuforums.org/showthread.php?t=1492307&highlight=WUSB54GC&page=2)
Mine is a WUSB54GC v1. I'm going away but I'll have a play in a few days.

[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/619093](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/619093)

---

### Post by fluteflute on 2010-08-23
> **dxxvi said:**
> I have the same problem but don't know how to fix.
Can you please mark the [bug report]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/619093") as affecting you? And add any additional details to it if there are any.

The suggestion in that thread didn't work. This is a definite difference between lucid and maverick - regression!

---

### Post by Reiger on 2010-08-23
Recently had similar trouble with wicd. Solved it by configuring my router to use AES (WPA2) only rather than TKIP+AES (WPA/WPA2).

---

### Post by fluteflute on 2010-08-24
> **Reiger said:**
> Recently had similar trouble with wicd. Solved it by configuring my router to use AES (WPA2) only rather than TKIP+AES (WPA/WPA2).
Unfortunately that's not an option on my router. Thanks for the information though, so for you it works on lucid but not maverick?

---

