---
title: "disable automatic database backups"
date: 2013-04-17
forum: Mythbuntu
---

### Post by iitywygms on 2013-04-17
Hi All:

What is the best way to disable the automatic database backup? (mythconverg)
Reason I ask is that I have another backup procedure I want to use.
Thanks to all.

using mythbuntu 12.04 with the latest from the mythbuntu repos.

---

### Post by klc5555 on 2013-04-17
Database backup schemes aren't mutually exclusive --there's no reason not to allow myth's automated scheme to continue to chug away, even if you have your own scheme implemented. The extra method adds a bit of redundancy, in case your preferred method fails. So while I use the same simple daily mysqldump backup bash script that I've relied on since mythtv 0.20 in 2007, a script which has never failed, nevertheless I've gotten out of the habit of "chmod -x" 'ing, renaming, removing, or even unlinking from cron the file   /usr/share/mythtv/mythconverg_backup.pl, which I used to do regularly on new installations in the years following its introduction.

---

