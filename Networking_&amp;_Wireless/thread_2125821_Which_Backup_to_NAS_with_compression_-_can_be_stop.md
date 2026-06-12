---
title: "Which Backup to NAS with compression - can be stopped/started?"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by chortle on 2013-03-15
Hi all

I have irregular power where I live. So I would prefer a backup solution which I can stop and then continue later. 

I'm backing up from an external HD (USB 3.0) onto my NAS (on fast ethernet). One thing I will be backing up is an 800 GB directory containing family photos, my saved ebooks, notes, all sorts of files. I guess I can save a lot of space with compression. 

What will be the best backup solution for me? I thought of using tar (with compression). But then I would have a problem with backups that I would have to suspend/stop part way through.

I started going through posts about some backup solutions, such as rsync, but I'm not knowledgeable enough to evaluate these solutions. I therefore throw myself upon the wisdom of the collective. Please let me know which solutions *won't* work for me, so at least I can look at the possibles.

---

### Post by tgalati4 on 2013-03-15
*rsync* would work since it updates only files that have changed since the last backup.  There are lots of tutorials available with different configurations.  Your next investment should be an UPS that you put your NAS, PC, and router on.  Many file formats are already compressed (music and photos for example) so you are really not saving that much with compression, but you are adding backup risk.

---

