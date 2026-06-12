---
title: "Telstra prepaid USB broadband issues"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by jonmokoko on 2010-03-16
Hi,
Just wondering if anyone can help me out. I've recently decided to abandon XP and install Ubuntu 9.10 on my laptop, however when I tried to get onto the internet using my Telstra USB ([http://www.telstra.com.au/bigpond_internet/get-started.html](http://www.telstra.com.au/bigpond_internet/get-started.html)) I couldn't install the software necessary for the USB. So at the moment the way I'm getting around the problem is by partitioning my HDD and just booting up Xp when I need the net (I had tried using VirtualBox but it ran too slow for my uses).
If anybody has a solution it would be appreciated.

Also if you have solution can you explain it simply for me, as I'm still a complete n00b :rolleyes:when it comes to Ubuntu...

Thanks

Jonmokoko

---

### Post by pdc on 2010-03-18
I think ............ that Telstra uses a ZTE MF636 modem .....

......... if so ...........

this was what worked for me using wvdial

[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271)

if it works, I can guide you on automating the initial "eject" command

this link 

[http://www.flexispy.com/Mobile%20APN%20Setting%20to%20use%20GPRS.htm](http://www.flexispy.com/Mobile%20APN%20Setting%20to%20use%20GPRS.htm)

should allow you to look up telstra's apn settings and paste them into the wvdial.conf file in the IP line .......... make sense ????

---

