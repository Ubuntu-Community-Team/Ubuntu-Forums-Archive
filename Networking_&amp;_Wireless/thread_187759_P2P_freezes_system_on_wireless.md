---
title: "P2P freezes system on wireless"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by panurge77 on 2006-06-03
There was a small thread going on dapper devel forum. Some wireless users like me are having the whole system freezed when using torrents. It happens with nicotine here too. Someone said that changing to ndiswrapper solved the problem. I posted a bug report some days ago but there was no answer. Anyone's got a solution? I still hope not having to go the ndiswrapper way.](*,)

Update: azureus is running fine now. I can't figure out what else could be causing the freezes.

---

### Post by panurge77 on 2006-06-07
Well, azureus worked for a day, and now it's freezing again. It only happens when I'm using p2p.
I would gladly follow some instructions to try to pin the problem.

---

### Post by panurge77 on 2006-06-09
I changed to ndiswrapper and things look fine. I also found similar problem related to the rtl8180 driver on launchpad. My bet is ubuntu is using the latest release which is not developed anymore. Kernel >= 2.6.12 need the cvs version. I hope a dev can check it out.

---

