---
title: "Ubuntu 'Share Connection' half-working??"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by Inkybro on 2010-10-07
I spent two or three hours last night getting the RT2870 driver to work for my USB wifi dongle. The good news is it finally worked, but the bad is the connection quality sucks. I get good quality on my laptop, though, which lead to the idea of sharing my laptop's wifi connection through eth0 with a crossover in between computers.

So I looked online and found the easy way (Firestarter won't work). I simply edited eth0 and set the 'Method' to 'Share with other computers'. The good news now is that the connection IS shared (as it's active and working, and I can ping in between the two computers successfully). But unfortunately there's bad news again -- and it's weird. If I type 'ping google.com', it resolves the IP but then doesn't get the pings through. It eventually times out without receiving any packets, but it DOES show the IP that was resolved.

Can anyone help me out?

---

### Post by xihad76 on 2010-10-08
Though my problem was more or less like yours, i was using wired connection to do the sharing. have a look at [this threa]("http://ubuntuforums.org/showthread.php?t=1585868")d i stared a few days ago. it might help you anyway. good luck

---

