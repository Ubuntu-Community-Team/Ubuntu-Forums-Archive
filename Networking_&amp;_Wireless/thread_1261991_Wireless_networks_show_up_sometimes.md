---
title: "Wireless networks show up sometimes"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by rhyno466 on 2009-09-09
I really hope i can get help so i dont have to go back to windows. I am fairly new to linux and am loving it, but sometimes my laptop does not show the wireless networks that i know are available. This is crucial because i am not always close to a wired connection, especially when i am in class. Now i dont know what it is but SOMETIMES my computer will ask for a keyring or something and then the networks show up. Most of the time they just plain dont show up. There are literally 15 wireless networks that i can see at my apartment when it works. Is there any way i can get them to show up all of the time when i have wireless enabled?

---

### Post by Sam Lars on 2009-09-10
When I was using Jaunty I noticed that sometimes my wireless would not work and I had to reboot once or twice before it would see any networks.
Could you post the output of
```
lspci | grep Network
```
in a terminal?

---

### Post by rhyno466 on 2009-09-11
lspci | grep Network
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


here

---

### Post by Sam Lars on 2009-09-11
Search the forums for bcm4318, there are a lot of posts about that card.
You should also look at the howto here:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

