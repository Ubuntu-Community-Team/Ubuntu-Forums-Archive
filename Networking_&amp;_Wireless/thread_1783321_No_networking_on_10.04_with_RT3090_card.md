---
title: "No networking on 10.04 with RT3090 card"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by tome9999 on 2011-06-15
I have an HP ProBook 4520 with RT3090 card that I cannot get wireless (or wired) network to work.

I looked at many of the threads here but can't seem to get anything to work.

Attached is the output from lspci, lsmod, and iwconfig and dmesg output is here:  [http://pastebin.com/NfnEZq3h](http://pastebin.com/NfnEZq3h)

Any ideas?
Thanks,
Tom

---

### Post by tome9999 on 2011-06-15
Nevermind.  I reinstalled 10.04 and built the rt3090sta drivers from Ralink loosely following this link: [http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090)

All is working now.
Tom

---

