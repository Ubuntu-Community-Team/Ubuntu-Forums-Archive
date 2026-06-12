---
title: "Trouble connecting to your own wireless network ? check your router channel !"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by pjnsmb on 2009-01-26
The same answer to my previous thread is posted here :

[http://ubuntuforums.org/showthread.php?t=1045276](http://ubuntuforums.org/showthread.php?t=1045276)


I feel the answer is too important to be missed though, so I have added another thread with a more accurate Title...........


Browsing for an answer I came across this page  -


[http://www.ubuntugeek.com/ubuntu-har...-wireless.html](http://www.ubuntugeek.com/ubuntu-har...-wireless.html)


Halfway down the page I saw :


"If you are in Europe and using a European only wifi channel (such as channel 12 or 13) note that Intrepid by default does not use these channels.

It is US by default regardless of your region.

You need to add the following line to /etc/modprobe.d/options :

options cfg80211 ieee80211_regdom=”EU”



Answer =

I changed my Netgear router to channel 8 from channel 12 and connected straight away ! :D


First time I had seen anything anywhere about wireless channel numbers causing problems................

hope this helps others in the future.:)

---

### Post by Byb on 2009-12-20
> **pjnsmb said:**
> ....
[http://www.ubuntugeek.com/ubuntu-har...-wireless.html](http://www.ubuntugeek.com/ubuntu-har...-wireless.html)

[The working link]("http://www.ubuntugeek.com/ubuntu-hardyintrepid-intel3945-wireless.html")

---

### Post by Byb on 2009-12-20
Just to subscribe to notifs

---

