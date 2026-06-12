---
title: "Acer Aspire One Wireless disabled?"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by ZeroRider13 on 2011-01-23
Hey, after finally getting this machine tot run with ubuntu i am now on an ethernet connection because all of a sudden, my wireless says its disabled.  When iwconfig is entered, it shows my wlan 0 but says power management : off.  It is so frustrating because I feel like there should just be a button that says to switch it on haha. Please help, my wifi was working, and after a boot it is no longer.

---

### Post by dineshs on 2011-01-24
With ref to post #3 [http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked](http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked) did you try ```
sudo rfkill unblock all
```what does ```
rfkill list
```say?
You may also see [http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

---

