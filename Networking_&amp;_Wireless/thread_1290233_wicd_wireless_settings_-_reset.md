---
title: "wicd wireless settings - reset?"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by PeaSoup on 2009-10-13
For various reasons I had to change the name of my wireless SSID. (That was done from a different PC). However, when I go back into wicd to connect, it doesn't pick up the new SSID. It keeps detecting the same set as it did before I changed the name. As a result I cannot connect to internet. [Ubuntu 9.04, wicd 1.6.2.2]

I've tried removing and reinstalling wicd, but I get the same issue. My old settings are still there, even after the reinstall.

My guess is that I need to specifically delete the old settings which are associated with my wicd.  Does that seem correct, and how do I do that?

---

### Post by PeaSoup on 2009-10-13
This was solved by editing the wireless-settings.conf file and changing the name of the SSID which wicd was automatically trying to look for.

---

