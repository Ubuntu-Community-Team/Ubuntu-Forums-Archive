---
title: "My damned RTL2832U Gigabyte card"
date: 2010-09-26
forum: Multimedia Software
---

### Post by forcecore on 2010-09-26
I have purchased 3-rd DVB card and again i cannot get i work, can someone please give me working RTL2832U .deb simple driver that works. I tried to compile linuxtv driver but i get nonsense errors. I am on edge to crush this card with hammer because shop do not take it back and official Gigabyte page do not have driver for Ubuntu. 

Compile error log:
[http://pastebin.com/1U8DwXK0](http://pastebin.com/1U8DwXK0)

Desperate help needed...

---

### Post by forcecore on 2010-09-30
bump

---

### Post by Yellow Pasque on 2010-09-30
You have to disable the problematic firedtv module. A good set of instructions is offered in this bug report: [https://bugs.launchpad.net/ubuntu/+source/me-tv/+bug/478379](https://bugs.launchpad.net/ubuntu/+source/me-tv/+bug/478379)

---

### Post by forcecore on 2010-10-01
Thanks a lot Temüjin FIREDTV was that compile horror problem. Current small problem remains is that linuxtv did not include rtl2832u driver, does anyone knows where i can get it. I downloaded linuxtv drivers several times and installed but i cannot find any source file that indicates some rtl2832u.

I got some driver from some website but it is very unstable and hangs Ubuntu when watching tv.

---

