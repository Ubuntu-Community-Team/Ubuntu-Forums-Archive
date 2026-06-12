---
title: "&quot;testing apt repository&quot; hang"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by jrjbertram on 2006-02-04
This is a post to let everyone know about a problem that I ran into when trying to install ubuntu 5.10 on one of my PCs.  During the install process, DHCP would complete successfully, but the install process would apparently hang a few steps later when it was testing the apt repository.  After something like 10 or 15 minutes later, I realized that it would come back with a detailed message saying that connections to various repositories timed out, including hyperlinks to the repositories.

It turns out that the issue was my router.  It's a linksys "network everywhere cable/dsl 4-port router" model number NR041.  It's a cheap linksys knock off and is labled "the Basic Solution Line From Linksys" right on the outside.  No kidding.  Taking that router out of my internal network allowed me to get to the apt repository.

The wierd thing about it is that I could use firefox or IE from another PC on the same router to get to the repostories that were failing under linux.

And, I had issues in the past with linux where wget would work but lynx and mozilla browsers would fail.  At this point, I'm assuming that was the issue... which I would've figured this out then. 

Anyway, just a friendly post to hopefully save someone some time.  Good luck!

---

