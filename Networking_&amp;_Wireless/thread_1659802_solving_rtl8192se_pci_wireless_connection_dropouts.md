---
title: "solving rtl8192se_pci wireless connection dropouts"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by npallett on 2011-01-04
Like many Ubuntu users, I have been experiencing problems with wireless connection drop-outs with the rtl8192se_pci.ko module.

After much experimenting, I have a stable wireless connection on my laptop running Ubuntu 10.04 64bit, and the rtl8192se_pci.ko module.

I downloaded and installed the latest realtek driver (rtl8192se_linux_2.6.0019.1207.2010.tar.gz)from the following link:

[http://www.realtek.com.tw/downloads](http://www.realtek.com.tw/downloads)


I compiled and installed the driver to work with my 2.6.32-27 kernel.

Having done this, I was still getting wireless drop-outs every few minutes, so I reconfigured my wireless router to only work in 802.11g mode and set the security mode to WPA2 only.From this point on, I got a stable wireless connection with no further drop-outs.

Hope this information helps other users with similar problems.

---

### Post by miko sims on 2012-01-22
ok, so how did you do this? haha im confusedd! I have the same card, and my wifi doesnt work on my laptop. the blue light is on showing its on but nothing. I downloaded the latest driver to my folder, but how do I install this in terminal?? 

I am a newbie so please hellpppp!!!!

---

