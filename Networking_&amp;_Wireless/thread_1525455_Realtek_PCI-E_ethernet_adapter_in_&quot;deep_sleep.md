---
title: "Realtek PCI-E ethernet adapter in &quot;deep sleep&quot;"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by s.v.z on 2010-07-06
Hi everyone. I`ve got a dual boot of win 7 and ubuntu 10.04. After I put the system to sleep in win7, it was unable to start the ethternet adapter back (Now after system boot, the lights around the ethernet port blink for a few times and then turn off. This repeats in a while). Now it is disabled in ubuntu too. Is there any way to start it again?

It is a Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller.

---

### Post by doughless on 2010-07-31
I have this same issue with my realtek adapter; unfortunately, the only way I know to fix it is to make sure the power to the computer has been completely cut off. That is, simply shutting the computer down and leaving it plugged in won't do the trick for me; I unplug it until the LED on a USB device I have plugged in goes out (usually takes about 15-30 seconds). A couple websites I've read say you actually need to reset the CMOS, but I've never had to go that far.

---

### Post by s.v.z on 2010-09-04
The techsupport have confirmed that there is something wrong with their adapters. Well, instead of waiting you can just unplug the PC and push the power button for a sec to drain all the electricity from the condensators. This may save you 14-29 seconds =)

---

### Post by alexbj on 2011-01-19
Thanks, that method works, nice to find out there's nothing wrong with my hardware (or, at least, that it's not broken...).

So this happened to me without dual boot or Windows, I only run Ubuntu, and I can't recall ever having put the card to sleep (but I guess I did, then).

Thanks again,
Alex

---

