---
title: "Dell Inspiron 6400 no wired or wireless connection"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by mfamike on 2013-06-11
Hi,

I am new to ubuntu and cannot get any network connection either using a wired ethernet, let alone having any wireless. I have spent hours on the forums trying to find a solution and nothing will work.

If anyone can help I can post up the results of any tests which you would need to see.

Thanks in advance,

Mike

---

### Post by chili555 on 2013-06-11
Let's start with:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by ahallubuntu on 2013-06-11
~

---

