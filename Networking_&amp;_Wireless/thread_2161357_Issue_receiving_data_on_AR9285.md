---
title: "Issue receiving data on AR9285"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by quicksilver7 on 2013-07-10
I have installed Ubuntu 11.04 on my Asus N53SV. Wireless card is the Atheros AR9285 based on lshw -C network

I've fiddled with wireless networking quite some time ago and recently booted up this partition only to find that I'm unable to receive wireless data on my wireless card. I'm able to connect to wireless networks, also have checked the wireless connection settings (it's all at default settings now)

When I try to ping my router:

ping 192.168.0.1, it showed me that I have x packets transmitted but have 0 packets received.

I'm unable to surf the net or ping other websites.

Would really appreciate any help here. Thank you!

---

### Post by sanderj on 2013-07-10
11.04 is not supported anymore (see [https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)), so why did you install it?

If your Atheros AR9285 is newer than 2011-april, 11.04 will not work with it. So better to use 12.04.2 or 13.04. Did you live-boot it to see if your Atheros AR9285 works with that version?

---

### Post by quicksilver7 on 2013-07-10
> **sanderj said:**
> 11.04 is not supported anymore (see [https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)), so why did you install it?

If your Atheros AR9285 is newer than 2011-april, 11.04 will not work with it. So better to use 12.04.2 or 13.04. Did you live-boot it to see if your Atheros AR9285 works with that version?

I installed it about 2 years back and haven't touched it for a long time.

The thing is previously it worked just fine, I was able to load web pages and all over the wireless.

---

