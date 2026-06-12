---
title: "One system hogging bandwidth"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by dnr1128 on 2013-01-31
I have two laptops, both running 12.10.  The router is a Netgear N300.  One of the systems, my lenovo z565, works fine.  The other, a lenovo N585, works fine until we're both using the network for about 30 minutes, then the downstream speeds will drastically slow down for that system.  If I disconnect the 565 from the router, the speeds on the 585 will go back to normal.  I've looked through all the apps, there's nothing on this system that I can see that is hogging bandwidth, there's no QoS protocol in place on the router.  I'm stumped.  

Any ideas or places to look for what is causing this?

ETA:  The problem is on the 565.  When I booted it into windows, and did speed tests from speakeasy.net on both systems at the same time, they both showed 1.6 Mbps downstream on a 3Mbps cable hookup.  When I ran the 565 in ubuntu and did the same thing, the 565 showed 2.5 Mbps and the 585 0.6 Mbps.

---

### Post by dnr1128 on 2013-02-01
*Might* have found the problem:

Software updater-->additional drivers.  The "broadcome STA driver" was selected.  I selected "do not use this device" and rebooted.  After reboot, the wireless is still working fine, checked to make sure it's still unselected, it is.  

Did a speed test on both systems at the time from speakeasy.net, both systems showed even speeds.  

Maybe I'm the only one who's had this problem.  :)

---

### Post by SmallWorld on 2013-05-13
You're not alone - I've had this same exact problem the past few months.  I was traveling for a while and half the time when I logged on to a wifi network with Ubuntu, everyone else's (Windows and Mac) connections would slow to a crawl, for as long as I was connected with Ubuntu.  If I disconnected, or rebooted my machine into Windows and connected to the same network, the effect would disappear.  This even happened while using a brand-spanking-new Clear(wire) Spot Voyager router/modem I bought at the beginning of April.

My machine is a HP dv6 6140us with a Broadcom BCM4313.

I've been using the propriety Broadcom STA driver for a long time.  I'll try disabling it whenever I next have some other devices to play with.

---

### Post by gnomeout on 2013-07-09
Yes, you are not alone. I also am experiencing this. Excited to try disabling the broadcom driver (I remember explicitly enabling it). I'll post back if it doesn't work or I find something new.

I also encountered this a couple years ago with my older laptop. Every other machine in the house would slow once my laptop was running and connected to the internet. Never found a solution back then, but wasn't really bothered (since all the other slow devices in the house were not mine).

---

