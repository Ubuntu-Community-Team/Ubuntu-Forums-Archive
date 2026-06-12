---
title: "Can not turn power management off"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by wildmanne39 on 2013-04-03
Hi, I am using 12.04 ```
sudo iwconfig wlan0 power off
``` works but not when I try to make it permanent, I googled and other people  have had the same issue in 12.04.

My wireless uses ath9k and it works better with it off.

Should I write a scrpit and what should be included?
Thanks

---

### Post by chili555 on 2013-04-03
Does it work in /etc/rc.local? As you know, it doesn't require sudo.

---

### Post by wildmanne39 on 2013-04-03
I added the option here:
```
/etc/pm/power.d/wireless
```
but it did not stick.
Thanks

---

### Post by wildmanne39 on 2013-04-03
Chili555, for some reason it took three reboots but it is now off as it should be.
Thanks

---

### Post by chili555 on 2013-04-03
> **Wild Man said:**
> Chili555, for some reason it took three reboots but it is now off as it should be.
ThanksHey, I'll take a working solution by whatever means! Glad it's working.

---

### Post by Hadaka on 2013-04-03
Hi, if it falls back out
[http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641)
post#2

---

### Post by wildmanne39 on 2013-04-03
I do not know why it did not stick the first time but I am glad it is working now.
Thanks for your help.

---

