---
title: "http UNBEARABLY slow to initially load page"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by zenon222 on 2010-10-21
I have a buffalo router with PPPoE DSL serving the computers in my home, including one suse box, a couple winXP's, and my ubuntu.

Recently my http browsing has become unbearable on the ubuntu box. I disabled IPv6 support in the kernel (I use vanilla source with optimizations around realtime performance) and found an improvement from unbearably slow to unbelievably slow.

I believe it may possibly be related to DNS requests, but am completely open to ideas.

This is a wired Ethernet connection.

ANY ideas are very welcome.

TIA.

---

### Post by zenon222 on 2010-10-25
*bump*

What are the obvious things to check?

---

### Post by zenon222 on 2010-11-07
Uninstalling the "avahi-daemon" package solved my issue in Lucid (10.04).

---

