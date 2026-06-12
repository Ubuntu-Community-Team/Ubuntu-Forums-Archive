---
title: "Wireless Unstable"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by rbgCODE on 2006-06-19
I am running a cisco wireless miniPIC card in my laptop and usually it works fine, but I notice after random amounts of time, sometimes 15 minutes sometimes 2 hours it just stops working.  I will be browsing or watching a video, and my gaim disconects, my hellanzb download stops and no pages are available anymore.

While a simple reboot fixes everything it has started to become annoying.  Any thoughts or ideas?

---

### Post by icheyne on 2006-06-19
Sadly, wifi sucks.

You could try:

```
sudo ifdown wlan0
sudo ifup wlan0
```

instead of a reboot.

---

