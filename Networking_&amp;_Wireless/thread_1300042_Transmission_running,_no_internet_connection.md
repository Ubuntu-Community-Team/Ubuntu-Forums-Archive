---
title: "Transmission running, no internet connection"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2009-10-24
Using Ubuntu 9.04, it seems that when I am downloading torrents, I no longer have the ability to access webpages through Chromium or Firefox, connection just times out. What gives?

---

### Post by donato roque on 2009-10-24
It looks like you have to put a cap/limit to Transmission.  

First you have to know your upload speed.  You can check your upload speed at [http://www.speedtest.net](http://www.speedtest.net)

In Transmission go to Edit->Preferences->Bandwidth.  Set you upload cap at 70% of your average upload speed.  You can adjust the cap according to preference.

---

### Post by 98cwitr on 2009-10-25
already set and adjusted...not it

---

### Post by ken_do_san on 2009-10-25
I had the same problem, I switched to qBittorrent (it's in the repositories), I've had no problems since.  Pages load quickly and I can still downlaod (you could also try ktoorent which I did first).

Cheers

---

### Post by ken_do_san on 2009-10-25
Appendum to to my previous post, my spelling sucks at times lol, fingers too slow for the brain (maybe I should learn to proofread lol).

---

### Post by 98cwitr on 2009-10-25
cool, thank you, I will try an new torrent program. I'm using Vuze on the my media server, so lets see where that gets me :)

---

### Post by Saprissa on 2009-10-25
I am also experiencing this problem in Karmic.

It wasn't like this a few weeks ago.

:(

---

### Post by Saprissa on 2009-10-25
For me, something in todays update fixed the problem.

Transmission is happy again.

:guitar:

---

