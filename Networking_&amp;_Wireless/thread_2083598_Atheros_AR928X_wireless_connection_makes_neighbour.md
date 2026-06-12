---
title: "Atheros AR928X wireless connection makes neighbourhood machine drop off line"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by funicorn on 2012-11-13
I have an Acer laptop with Atheros AR928X wireless card  installed, supported by ath9k driver in the linux kernel. There are  other 5 computers sharing wireless connection via a TPLink 150Mbit/s  wireless router. At first I found the network is a little bit slower  than it's in Windows7, which I accepted as it should be. However a very  strange thing is, **each time I connected to the router and  downloaded stuff for a while, one of the computers running Windows7 in  my local network dropped off from the router. And if I run my laptop  under Windows7, everything is fine**. What's even stranger is  although the network becomes slower, only the certain computer drops and  totally freezes in connection with the router. I'm not willing to  conclude it's due to the unhealthy connection from my laptop to the  router, however we have confirmed this for more than one times and there  is no problem with the network when I'm running WIndows7.

  I'm extremely confused about what's going on. As a Linux user running  Ubuntu over 5 years, I am awared that wireless driver in Linux is badly  notorious of lack of stability and slow speed. But is it so bad that  the unhealthy wireless connection can do damage to another computer in  the same local network? I do see a lot of "Tx excessive retries" in  iwconfig output. But how exactly does this happen ?

---

### Post by kurt18947 on 2012-11-13
I'm not sure this will fix your problem but there's no downside that I'm aware of trying it.  If it causes problems, simply delete the file and reboot.   Thread here:
[http://ubuntuforums.org/showthread.php?t=2083063](http://ubuntuforums.org/showthread.php?t=2083063)

---

### Post by funicorn on 2012-11-14
[COLOR=#222222][FONT=Helvetica]Yes, I have realized 'Options ath9k nohwcrypt=1' might be problematic when coexisting with other wireless clients. Hence I disabled it but the problem was not gone. I found somewhere that my wireless card is a 802.11n **legacy** product, i.e., only complies to **802.11n Draft**. And there might be problem when it connects to a router working in 11n mode behind which there are other 802.11n clients. This also confuses me because there is no problem with wireless connection when I'm running Windows7.
 [/FONT][/COLOR]

---

### Post by kurt18947 on 2012-11-15
That your device works with Windows 7 makes a hardware problem doubtful.  My suspicion would be the wpa supplicant or related.  I have no clue how to trouble shoot it though.  Sorry I can't be of more help.  As far as the difference between N and draft N perhaps this will shed some light:

[http://superuser.com/questions/150150/802-11n-vs-802-11n-draft](http://superuser.com/questions/150150/802-11n-vs-802-11n-draft)

---

