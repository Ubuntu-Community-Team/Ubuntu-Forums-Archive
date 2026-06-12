---
title: "Cannot share Internet with WinXP"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by houyunqing on 2010-12-14
I have a WinXP desktop with an external TP-Link TL-WN321G+ wireless adapter. This desktop is connected to the Internet. I could share its internet through ad-hoc to my laptop, which normally runs Win7. It could also be shared with my iPod Touch. But now I've installed Ubuntu Desktop on my laptop, it seems that my Ubuntu could no longer connect to the ad-hoc network created by my desktop machine.

However, if I connect my iPod Touch to the ad-hoc network first, then my Ubuntu can connect with no problem. Why is it like this? Is there a way to solve it?

I followed the help instruction here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
all the way until the Connection section. There's no problem with the driver(iwl3945, v2.6.35, cos my laptop wireless adapter is intel 3945).

[I tried with Fedora previously. Same problem existed]

I tried iwconfig. It gives no output, but it's just not connected anyway.
I originally tested with an ad-hoc network with WEP encryption. Then I removed the encryption but nothing changed.

So basically I've come to the second bullet point of 2.1.3 of the connections page of the troubleshooting document, and it tells me "check if other devices can connect wirelessly". Yes my iTouch could. But from here the document gives me no more hint.

Anyone can help me identify the problem? I appreciate any help:D

[I tried with Fedora previously and same problem existed]

---

### Post by Cabalbl4 on 2010-12-14
Try guide here:
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)
(look comments too!)

But there may be a problem: I have an ubuntu host with internet at home, other ubuntus work with it, XP machines work with it, but when my friend came with win7 machine - it was almost unable to connect, as if the wireless driver of win7 is incompatible with older ad-hocs :( For now i have no clue, as I do not use win7 at all.

---

### Post by houyunqing on 2010-12-14
> **Cabalbl4 said:**
> Try guide here:
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)
(look comments too!)

But there may be a problem: I have an ubuntu host with internet at home, other ubuntus work with it, XP machines work with it, but when my friend came with win7 machine - it was almost unable to connect, as if the wireless driver of win7 is incompatible with older ad-hocs :( For now i have no clue, as I do not use win7 at all.

thanks cabalbl but that guide does not seem to work

Previously I was always using XP to create the ad-hoc network. So I thought maybe I could try doing that with Ubuntu. Then I created an ad-hod network on my ubuntu but neither my XP nor my iTouch could detect that network. It's not that the SSID is not broadcasted. It's that the ad-hoc network which seems to exist with no flaw on Ubuntu is simply not created at all.

---

