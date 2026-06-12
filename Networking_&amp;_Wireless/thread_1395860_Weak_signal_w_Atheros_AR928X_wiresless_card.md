---
title: "Weak signal w/ Atheros AR928X wiresless card"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by sudanmas on 2010-02-01
A quick shout out to the Ubuntu Dev Team - thanks for all your hard work.  Great to have a community where folks like myself who are starting from scratch wrt Ubuntu are welcome to ask and receive help!  I was also very impressed after my 9.10 install that there was  almost no post-config needed.  All of the devices and drivers work immediately after install (unlike that **other** OS ;-)

The only issue I was having were with wireless signal strength.  I'd get 95% on bootup and it would slide to 48% after 10 seconds following login.

I found a thread suggesting a driver rollback:

[http://swiss.ubuntuforums.org/showthread.php?t=1316126&page=3](http://swiss.ubuntuforums.org/showthread.php?t=1316126&page=3)
[B]
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic[/B]

That fixed my problem.  I now get between 80% and 90% signal strength consistently and with no sudden disconnects.

Over and out.

Robert

---

