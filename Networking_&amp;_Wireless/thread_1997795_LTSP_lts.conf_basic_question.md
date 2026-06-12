---
title: "LTSP lts.conf basic question"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by v4169sgr on 2012-06-05
Hi Folks,

Having a 'senior moment' here: I am sure the answer is perfectly obvious, but I am struggling to remember just how I did this two years ago with 10.04 ...

Running Ubuntu 12.04 alternate install with ltsp-server-standalone & have built i386 client images on my core i5 64 bit install. I am now trying to fix my thin client screen resolution problems by accessing and modifying the copy of lts.conf in /var/lib/tftpboot/ltsp/i386.

Question: what do I need to do to get the changes to the lts.conf file to have any effect?

Realise the answer is going to make me feel like a chump, but better to ask the silly question than be stuck in igorance / lack of memory ..

Cheers!

---

### Post by v4169sgr on 2012-06-06
A basic answer:

* lts.conf has a specific config: in particular it is best for the configuration items in each group to start with a <TAB> on each line;
* No service restart is required: the lts.conf will take effect on the next thin client boot.

---

