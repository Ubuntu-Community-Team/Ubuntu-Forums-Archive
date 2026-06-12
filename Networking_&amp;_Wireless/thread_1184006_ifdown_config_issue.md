---
title: "ifdown config issue"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by zeroTOLERANCE on 2009-06-10
ok, I was trying to put my wireless card into monitor mode, but first I have to bring it down. so I used:           sudo ifdown wlan0          I got the following error, and am wondering how I can fix it.                 ifdown: interface wlan0 not configured                           thanks in advance for any help you can give.  by the way, the reason why its all just spaced is because my enter key got fried. I will be replacing it soon

---

### Post by thieaux on 2009-06-10
see if its recognized first,  ifconfig -a
then try ifconfig wlan0 down

---

### Post by zeroTOLERANCE on 2009-06-11
ok, next time I'm on that computer I will try that. I ended up just creating a virtual device that was bridged to it that was in monitor mode, and it worked.

---

