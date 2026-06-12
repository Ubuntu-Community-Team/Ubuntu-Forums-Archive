---
title: "2 wifi-cards, 2 access points, but how?"
date: 2013-07-07
forum: Networking &amp; Wireless
---

### Post by bartgrefte on 2013-07-07
Hi :)

I've been Googling for something but found surprisingly very little.
How does one set two wifi cards at the same time as access point?

From what I've read, hostapd should be able to do it, but as for how, the only info I could find was on a mailinglist where someone said to run **hostapd -B hostapd.conf hostapd1.conf**

Haven't tried that yet though.

How is this usually being done?:confused:

---

### Post by gordintoronto on 2013-07-07
My guess is that very, very few people are doing it, so there's no "usually."

But good luck with it!

Hmmm. I'm a bit puzzled about why one would want to set up two APs in the same location, running from the same Internet connection. If you tell me, I'll probably slap my head and say, "how obvious."

---

### Post by bartgrefte on 2013-07-11
The "why" is simple:
[img]http://www.ravenslair.nl/GoT2/wifi2013-scan.jpg[/img]

The 2nd AP will be working on the 5GHz band, which is free and legal to use here and not so crowded:biggrin:. But the 2.4GHz access point will have to stay since not every device supports 5GHz wifi.

---

