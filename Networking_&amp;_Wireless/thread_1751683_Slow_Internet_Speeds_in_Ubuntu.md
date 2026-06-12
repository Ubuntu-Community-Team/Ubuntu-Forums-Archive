---
title: "Slow Internet Speeds in Ubuntu"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by agentsmith23 on 2011-05-06
I have something very odd happening in Ubuntu. I just installed Ubuntu 11.04 and upgraded my internet speed from 7Mbps to 15Mbps a few days after installing 11.04. The issue is the speed I get in Ubuntu previously in 10.10 I got excellent speeds when downloading or running a speed test and everything seemed to be find in 11.04 under the 7Mb connection also (never ran a speed test for the 7Mb connection under 11.04). With the 15Mb connection I am only downloading around 110KBps and speed tests reflect around 1.2-1.5Mbps and that is when connected wired or wireless through my Asus RT-N16 router running Tomato. If I eliminate the router I get full speed when connected directly to the modem. Normally that would make me think there is an issue with my router however when booting into Windows 7 on the same laptop I get excellent speeads when connected wired or wirelessly to the RT-N16. I have tried factory resetting the router and clearing nvram and running a speed test with just the stock router configuration and get the same results. I troubleshoot internet service for a living for a large ISP but have never seen anything like this, what could cause it?


Just ran a speed test on my desktop running 11.04 and got great speeds on it. It is connected a little differently though. It is hardwired into a Linksys E2000 running DD-WRT operating as a repeater bridge of the RT-N16.

---

### Post by agentsmith23 on 2011-05-07
I think I may have discovered the problem while searching the forum. Seems that there is a known issue with Atheros chipsets on 11.04, I think it is an atheros chipset but not 100% sure (not at home to check). From what I have been reading though it only mentions issues with wireless, does it also affect wired connections as well?

---

### Post by agentsmith23 on 2011-05-08
So it is an atheros chipset but the fix that I have read about didn't fix it completely. The fix I am referring to says to run this:

```
sudo apt-get install linux-backports-modules-net-natty-genetic
```

Then reboot, it did take my speed test results up to around 5Mb/s but not up to what it should be. Is there any other way to fix this issue?

---

### Post by BlacqWolf on 2011-05-08
Can you try disabling encryption? I have a Atheros wireless card and the internet was slow, but after disabling security the speed went up to about what it is on the other computers and game consoles.

---

