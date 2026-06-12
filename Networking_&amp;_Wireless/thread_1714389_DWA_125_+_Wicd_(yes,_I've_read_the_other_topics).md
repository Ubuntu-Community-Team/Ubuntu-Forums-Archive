---
title: "DWA 125 + Wicd (yes, I've read the other topics)"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by DMurray on 2011-03-25
Hi, everybody.
I've researched all over ubuntuforums to, first, get the DWA125 working. After following Chili555's and Flash63's guides, I finally got the USB adapter to be recognised.

- Network-manager found my wifi network but couldn't connect: password wrong (WPA2), and obviously it was right.

- Then I completely uninstalled Network-manager and installed Wicd after reading countless posts of people having the same authentication issue.
Wicd 1.7 was still complaining, so I followed someone else's guide to downgrade to 1.6. Did it, but now it complained about not being able to get an IP!

- I saw people having trouble with Wicd 1.6 too, so they suggested using static IP instead of DHCP. Set it up to static, but now it can't reach the gateway... WTF?

So the steps were: make the USB wireless adapter work, remove NM because it won't authenticate and use Wicd instead, downgrade Wicd because the new one is bad, change to static IP because DHCP doesn't work. Man, there are serious issues with wireless at least in the LTS version, no?

System is: Intel C2D, DWA125, Ubuntu 10.04 64bit, Apple Airport Express.
Any help from the wise ones?

Thanks a lot.

---

