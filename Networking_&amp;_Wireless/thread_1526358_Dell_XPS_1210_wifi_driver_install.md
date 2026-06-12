---
title: "Dell XPS 1210 wifi driver install"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by maskeman on 2010-07-07
I'm new to Ubuntu and installed it (10.04 LTS) on my Dell XPS M1210. Everything works just great but my Wifi. I have a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01) and finally found a driver from Broadcom that is supposed to work. The issue is that I’m new and am not sure how to install it. I down loaded the patch and unzipped it and put it in my home directory (“mark”) in a sub directory named “Broadcom” and in that is the file “Patch”. The instructions read, 

“cd top level directory
'ls' should show src, lib, Makefile, etc”
.
Patch -p0 < patch

I’m not sure what the top level would be, /root or /dev? When
I go there and look for src I don’t find it. I did find lib, I'm guessing I'm supposed to run the Makefile utility in the lib directory but not sure how it should work. I tried it a few times but I can't get the correct syntax.

Can anyone help maybe w/a step by step please?

---

