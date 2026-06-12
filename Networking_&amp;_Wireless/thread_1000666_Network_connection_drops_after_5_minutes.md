---
title: "Network connection drops after 5 minutes"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by oBirdman on 2008-12-03
This morning I started experiencing network problems. For no apparant reason, my network activity drops after about 5 minutes. When I start the system, everything works just fine, but after 5 minutes:

- Skype and Pidgin drop
- Browsing is impossible, I can't even reach my router's admin page

The Wireless Network Connection seems to be working well. I have an IP address and even when I disable the WLAN connection, it enables without a problem and has the usual connectivity.

My laptop with Windows XP doesn´t show this behaviour. A simple restart of the Ubuntu 8.04 desktop brings back the connectivity for 5 minutes.

Anybody has any idea how I can start resolving this issue?

---

### Post by oBirdman on 2008-12-03
I have tried several things without success, like:

* /etc/init.d/networking restart
* modprobe ndiswrapper


It seems that after a while I get a temporary connection again. I conclude that based on the fact that I received a new mail in Thunderbird. This was temporary however, afterwards no browsing was possible.

---

