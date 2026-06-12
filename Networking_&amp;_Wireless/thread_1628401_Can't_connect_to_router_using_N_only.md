---
title: "Can't connect to router using N only"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Pandemic187 on 2010-11-22
Hey all.

So, maybe I haven't done enough Googling here, but I can't seem to connect to my router using N only mode with Ubuntu 10.10. The wireless adapter is an Intel PRO/Wireless 4965AGN.

What's weird is it finds the router, but after it prompts me for a password, the laptop just won't connect. I suspect it's an issue with AES encryption. Even if I set the router to N and G mode, it will work if I use TKIP + AES, but if I set it to AES only, I can't connect.

Again, sorry if this has already been covered somewhere, but I can't figure out if this is a driver issue or some sort of config on my end.

EDIT: After some digging, I found the answer. I had to comment out /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf.

---

