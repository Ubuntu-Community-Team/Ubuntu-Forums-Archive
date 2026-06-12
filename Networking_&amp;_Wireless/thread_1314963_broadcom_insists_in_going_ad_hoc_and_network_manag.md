---
title: "broadcom insists in going ad hoc and network manager disappears"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by santiagozky on 2009-11-04
Hello everyone,

I installed karmic a few days ago and I'm having problems with my broadcom. It seems that wifi works sporadically. Sometimes it works fine and sometimes nm-applet just dies or if it works my card insists in going adhoc (with an essid equal to my username) and NM says I'm connected to 'santiago' (the ad hoc connection created and my username).

It start working after taking down and up the wlan a several times and setting the mode to Managed.

Some info:
 card: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
firmware installed with b43-fwcutter
all my /home belongs to a jaunty install, the rest of the system is a fresh karmic.

This is getting quite annoying. Anyone knows how to solve this or how to get more info in order to give a better diagnosos?

Thanks

---

### Post by papangul on 2009-11-04
Why don't you first try out the alternate wicd network manager?

---

### Post by santiagozky on 2009-11-05
thanks, I was not aware of an alternative to network manager. Wicd looks kind of ugly to my taste, but It seems to work fine.

---

