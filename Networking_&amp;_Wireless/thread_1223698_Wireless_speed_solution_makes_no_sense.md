---
title: "Wireless speed solution makes no sense"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by hhh on 2009-07-26
The problem I had was my Belkin F5D7050 wireless usb adapter was working out of the box on Jaunty with the rt73usb driver, but was noticeably slower than on Windows even though the connection information showed a rate of 54M, the card's limit. After a LOT of frustration with trying to get another driver or ndiswrapper working, I found this thread...
[http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109)

And it works. Open a terminal, slap in the rate...```
sudo iwconfig wlan0 rate 36M
```...reconnect and boom goes the dynamite, the rt73usb speed doubled. After setting the rate higher and lower and checking my connection speed with the various speed tests on the web, I've now limited the rate to 18M as this is giving me the best performance, equal or maybe even better to what I was getting on XP.

My question: why would a slower rate give me a faster connection?

---

### Post by martinbaselier on 2009-07-26
It's usually some issue with the driver not working as good as it should. The problem with drivers is that it's usually quite hard to get proper information about the way the hardware, since most manufacturers don't provide it.

---

