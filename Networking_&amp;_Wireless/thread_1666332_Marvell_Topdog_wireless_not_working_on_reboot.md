---
title: "Marvell Topdog wireless not working on reboot"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by pacojoseph on 2011-01-13
I'm a newbie but I figured that I'd post here rather than the newbie section. Anyhow, I have a Gateway M1617 laptop, with a Marvell Topdog **(EC85) wireless card,** that I'm triple booting with Windows 7 and XP.  After installing Ubuntu, my wireless wasn't working. After searching this forum I found a thread in the archives with others who had the same problem and who had suggestions on how to solve it. The thread is at [http://ubuntuforums.org/showthread.php?t=575785&page=3](http://ubuntuforums.org/showthread.php?t=575785&page=3)  . After following the suggestions listed there, which involved installing a Netgear Windows driver, I finally got my wireless to work. However, every time I reboot, I have the same problem that the next to last poster in the  archived thread had, namely, that my wirless is again not working. To get it to work, I have to enter the command "sudo modprobe ndiswrapper" into Terminal and that fixes the problem- until I reboot. My question is, is there any way to fix this so I don't have use Terminal to start my wireless every time I start my laptop?

---

