---
title: "my WiFi stopped working help"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by awesomejeff1998 on 2012-02-29
i disabled my WiFi on my dell inspiron mini running Ubuntu 11.10 to save battery life but when i try to re enable it says wireless is disabled by hardware switch i tried my hardware switch but it does not help thanks in advance :confused:

---

### Post by clausrei on 2012-03-01
Did you try this:
```

sudo ifconfig wlan0 up 

```
wlan0 must be exchanged by your own wifi device.

---

