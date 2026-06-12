---
title: "WPA2 on rl2860 refuses to stay connected(EEEpc 1000HE)"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by stevenmnance on 2010-03-11
Has anyone figured out how to get wpa2 to properly work on the rt2860 chipset, I've installed the most recent version of the drivers and it refuses to stay connected. If i restart my laptop,(Eee 1000he), it will connect momentarily only to drop the connection a minute or so later after which I cannot reconnect what so ever. Ive been searching the forums for the last two hours and have yet to find any solution that works.

I have the v2.3.0 of the drivers installed from, [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2), I set the two flags to yes during the install, modprobe rt2860sta, added it to my /etc/modules and restarted and it worked for a minute or so and then dropped the connection.

It then goes on to try and connect over and over again never succeding. The odd thing is if I set my router to use either only tkip or only aes it connects but when it is set to tkip/aes together it wont.

This wouldnt be a problem except for the fact that at work I need to connect to a network with tkip/aes together.

Any suggestions?

As a side note I know that it can connect to this network because last week when I was using slackware I had no problem at all connecting.

---

### Post by KwukDuck on 2010-05-20
I'm having the exact same problem...

nevermind, i found the right topic discussing the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)

---

