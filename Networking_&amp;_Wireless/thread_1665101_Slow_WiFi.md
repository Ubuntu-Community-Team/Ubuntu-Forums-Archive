---
title: "Slow WiFi"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by s31523 on 2011-01-11
OK, so my Ubuntu 10.10 install was driving me crazy.   Copying files from my network drive was going so s-l-o-w.  Like 150kb/sec slow...  I finally found a suggestion in another forum that I thought I would share (it worked and I now get 1MB/sec).  

The suggestion was to disable the power-management setting for the wifi card.

The code:
```
sudo iwconfig eth1 power off
```

---

