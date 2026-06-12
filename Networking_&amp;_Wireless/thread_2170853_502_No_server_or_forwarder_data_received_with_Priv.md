---
title: "502 No server or forwarder data received with Privoxy"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by marinecomm on 2013-08-27
I'm running Privoxy 3.0.19 on Xubuntu 12.04 64-bit and from time to time I get this error message when trying to access certain webpages. It's happening a little less than half the time. For example, when I try to access [http://www.thetangledweb.net]("http://www.thetangledweb.net") I get this error message every time. It just started happening this afternoon. Earlier today I was able to access the website just fine but now, for whatever reason, I'm getting this error message. I've looked in the log file but it doesn't show anything regarding this particular website. I'm not sure what else to do. Any thoughts or ideas? Thank you.

---

### Post by marinecomm on 2013-08-27
Odd thing I found out tonight. I was playing around with Cairo-Dock and you can add wesites to your desktop. The are called weblets. Well, when I added thetangledweb.net to my desktop as a weblet, it let me go to the webpage without any problems. The only issue is that I have limited visibility of the webpage.

---

### Post by marinecomm on 2013-08-30
Problem solved. I ditched Privoxy and decided to go with Polipo. Privoxy was causing me too many error messages and it was slowing my system down a lot.

---

