---
title: "Looking for a method for online access restriction"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by ryu kun on 2010-12-27
Hello Dear Community,

In order to keep myself isolated from online distractions and procrastination, I want to block my access to everything online (websites, instant messaging etc.) except for a few web sites related to my work and my work mail account.

I tried to use /etc/hosts.allow and /etc/hosts.deny files to achieve this but apparently they did not do any effect on my access to websites. I wonder what is wrong with my settings. Here are the contents of those files:

/etc/hosts.allow:
ALL: allowedwebsite1.com
ALL: allowedwebsite2.com

/etc/hosts.deny:
ALL: ALL

I would be happy if anybody can guide me into the right direction or can tell me a better alternative.

---

