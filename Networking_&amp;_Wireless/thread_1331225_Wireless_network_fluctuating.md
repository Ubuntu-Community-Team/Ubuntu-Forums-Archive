---
title: "Wireless network fluctuating"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by jir0 on 2009-11-19
Hello, 

I'm fairly new in the ubuntu community and honestly a newb with this OS.

I just installed 9.10 last night.  It detected everything except that everytime i connect to my home network, i always get disconnected, and its protected.  Then tonight I connected to an unprotected wi-fi source around my apartment and I was never kicked off or disconnected.  I have dell inspiron e1505, intel pro wireles AG(N), with Vista on another partition.

P.S. vista connection to wireless does not fluctuate. Only when im using Ubuntu.

If there were any solution for this problem, can someone direct me to that thread? 

Thanks a whole lot!

---

### Post by hal10000 on 2009-11-19
A solution could be to remove the crappy **network-manager** package and install **wicd** instead. The configuration is the same as in network-manager, but it works much better with wireless connections.

---

### Post by zaphod777 on 2009-11-19
Check this thread
[http://ubuntuforums.org/showthread.php?t=1318375](http://ubuntuforums.org/showthread.php?t=1318375)

it has a few different solutions

it seams that 9.10 has some wireless issues you might want to try 9.04 if you can't get it to work.

---

### Post by hal10000 on 2009-11-19
The intel pro wireles AG(N) drivers (iwlagn) itself works very well, but together with network-manager the card had ranomly timeouts and was disconnected sometimes. I noticed that network-manager sometimes is not able to reconnect automatically. After i installed wicd those problems were all gone.

---

### Post by jir0 on 2009-11-20
> **hal10000 said:**
> A solution could be to remove the crappy **network-manager** package and install **wicd** instead. The configuration is the same as in network-manager, but it works much better with wireless connections.


thank you! wicd worked well and now i can explore the wonders of linux.

---

