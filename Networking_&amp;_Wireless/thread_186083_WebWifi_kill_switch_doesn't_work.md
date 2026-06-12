---
title: "Web/Wifi kill switch doesn't work"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by LTK on 2006-06-01
I can't turn my wireless card on.

I have a Fujutsu Siemens amilo pro 2000
I Had the same problem in breezy, but thanks to fsam7400 i was able to turn the kill switch on.

In dapper it stops at the finishline with this error:

ltk@Chaimber:~$ sudo echo 1 > /proc/driver/wireless/radio
bash: /proc/driver/wireless/radio: Permission denied

I have built the fsam7400 module and the modprobe fsam7400 command
seems to work fine.

Is fsam7400 obsolete in Dapper? In that case, how do I turn my wirelesscard turned on? 
Any tip would be greatly appreciated

---

