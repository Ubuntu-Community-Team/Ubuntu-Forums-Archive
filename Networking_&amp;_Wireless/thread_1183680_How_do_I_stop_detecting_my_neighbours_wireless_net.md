---
title: "How do I stop detecting my neighbours wireless networks?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-06-10
Hi.
How do I stop detecting my neighbours wireless network? There are two other networks that keeping popping up on my NetworkManager Applet. How can I prevent these wireless networks from being detected?
Thanks.

---

### Post by yaroto98 on 2009-06-10
Well, in that manager, you can click and delete them. But I don't think that's what you're asking. As far as discovery goes, you don't need your network manager running. I believe you can remove it from your startup, and in it's place make a bash script that does a "ifconfig wlan0 homewireless key" or something like that.

---

