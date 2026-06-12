---
title: "Large and important backups"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by paulfox on 2006-01-26
Hi all,
I'm looking for a way of performing automatic backups of a number of machines. I've  got to use rsnapshot for the actual backing up, but I'm wondering how to do the automation side of things.
Normally, I'd just do this with rsnapshot running through a cron job, but because the data we're backing up is important, I need a way of checking that the command to rsnapshot was:
a - successful
b - actually backed up data
c - if it failed, try again and email someone

any thoughts on the best way to acheive this?
thanks for reading!

---

