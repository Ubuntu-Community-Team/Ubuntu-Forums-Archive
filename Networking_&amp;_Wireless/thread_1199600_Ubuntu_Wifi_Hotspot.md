---
title: "Ubuntu Wifi Hotspot"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by linuksamiko on 2009-06-29
Hej everyone,

I tried to find something on the net about this issu but I couldn't find anything. I want to turn my server into a wifi hotsport. How can I do that? The only thing that comes near is chillispot. But seam a little to much for what I want to do.
All I want is that my computer should appear as a regular wifi-hotspot where you have to login with WPA2.

I hope somebody can help me out.
THX

---

### Post by computer13137 on 2009-06-29
I've been thinking about trying this as well, but I haven't done anything specific with it yet.  I'm just going to say, you'll need a WiFi card that supports AP mode.  Most cards only support infrastructure and ad-hoc mode.  I didn't see any specific mention of hardware, but I'm guessing that you have some consumer WiFi card you bought at Walmart, and that it probably doesn't support the mode necessary to configure an access point.

-Kirk

---

### Post by philcamlin on 2009-06-29
i alwasys wondered if i could do that :D

be cool though

---

### Post by computer13137 on 2009-06-29
I know you can do it with some of the FreeBSD-based router Live CDs too, but I'm still pretty sure you need specific hardware.

-Kirk

---

### Post by linuksamiko on 2009-06-29
Since I thought I might need some special hardware I haven't done any shopping yet. Though it's good to know that the card needs the ability to do some kind of AP-mode. That is a start. Maybe somebody else knows something more and after gathering all information we might work something out that works (including drivers, hardware and software).

---

### Post by computer13137 on 2009-06-29
I thought there was an "AP-Mode" in certain WiFi cards that was a requirement... but ZeroShell.net suggests that all you need is the MadWiFi drivers and any Atheros chipset WiFi card.

[http://www.zeroshell.net/eng/wireless-access-point/](http://www.zeroshell.net/eng/wireless-access-point/)

ZeroShell is one such FreeBSD-based router live CDs I mentioned earlier.

As I've never done nor attempted this (all the WiFi desktop hardware I have is broadcom, and I don't particularly want to try it on my eeePC) it may only be Atheros chipsets that are required.  Maybe someone else here has more experience with this kind of setup than I do.

-Kirk

---

### Post by oldsoundguy on 2009-06-29
a good sized portion of the Wi_Fi hot spots are just using their router setup (some with a pass word that you get for that day at the counter when you purchase your coffee.)

But there are some that require MORE than a pass word, and those are running off an input to the server .. like in our local hospital, you have to click on a "usage  agreement" and then enter your room number .. and THEN they let you on. (they have no pass word because of the dual steps involved.)

Just remember that offering your connection makes you liable for any of the actions taken by those that USE that connection.  It is your IP number that will show up in the logs!

Also check with your provider and make sure that you have a commercial account that ALLOWS a server on line. (there are commercial nodes and resident nodes in most areas .. they place less customers on the commercial nodes to allow that extra bandwidth .. and you PAY for it!)

---

