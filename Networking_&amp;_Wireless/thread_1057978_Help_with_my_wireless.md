---
title: "Help with my wireless"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by 2_Thumbs_Up on 2009-02-02
Hi!

First post here but the forum is great and I've learned a lot just by reading.

I have a problem. I have been using Ubuntu 8.10 for about a month and everything have been working just fine. But we are switching to a wireless network now and I can't get it to work. I have no idea where the problem is or how to find that out. I have no idea wether it's a software problem or a hardware problem and I'm quite lost as where to go from here. I have a new network card (D-Link DWL-G510, says it's linux supported) for my PC but I have no idea wether my computer actually finds it. The network is using a EPC 2434 modem and is working just fine on the windows computers in the house. I appreciate any help. Thanks.

---

### Post by utnubuuser on 2009-02-02
try > lspci    or  lshw (either of those commands)  in a terminal to see if the card is detected.

Then you might check in Systems>>Administration>>Hardware Drivers
to see if there are any drivers listed that aren't enabled. (Probably not, but it wont hurt to check).

and> [http://ubuntuforums.org/showthread.php?t=603763](http://ubuntuforums.org/showthread.php?t=603763)

and mostly, go to this Ubuntu wiki:> [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw)

---

