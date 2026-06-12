---
title: "Slow DNS and Package Loss"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by jasonsantos on 2010-07-04
After installing Lucid I am experiencing very slow DNS resolution and a package loss of exactly 50%.

I have made a clean installation (with formatting) on a machine that worked fine with Karmic, but when it was all finished, I changed the host name. I have read the instructions here[1] in the forum to make the change.

I have installed **dnsmasq** and it made web navigation *bearable*, so I believe it probably is a DNS-related problem.

However, when I **dig** new addresses, the query times are all very fast, but the dig command itself takes several seconds.

What intrigues me the most is the **ping **command: it looses exactly 50% of the packages -- every odd-numbered package is lost.

Does anyone know how can I troubleshoot this? 

[1] [http://ubuntuforums.org/showthread.php?t=774029](http://ubuntuforums.org/showthread.php?t=774029)

---

### Post by jasonsantos on 2010-08-16
bump

---

