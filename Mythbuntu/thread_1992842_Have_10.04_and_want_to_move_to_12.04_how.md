---
title: "Have 10.04 and want to move to 12.04 how?"
date: 2012-06-01
forum: Mythbuntu
---

### Post by rramesh on 2012-06-01
Hi,

  I have been using mythbuntu for a couple of years and automatic updates
have me at 10.04. I want to do a clean install to 12.04, but want to keep old
database. The instructions on mythbuntu site tell me to read twki on mythtv about database backup. I am not too happy with twiki as it does not say as what user I should execute the backup/restore commands. I tried it as myself and that does not work. Do I need to be root/sudo the backup? Also, there is a lot of information about restore and I am not sure which one of the method I should use? More importantly the backup will be done with my current system so mythtv 0.23 (I think) and restore will be, I suppose, on a newer version. Will this work? I mean can I restore backup from old schema (or whatever it is called) on to a new one?

Is there a 12.04 upgrade for dummies type document somewhere? Simple googling did not get me that info. So, I am not sure.

Thanks
Ramesh

---

### Post by nickrout on 2012-06-01
you can run the backup on a 0.23 database and restore it to your 0.25/12.04 system. 0.25 will upgrade the database to the current schema.

I am not sure it matters too much which user you run it as.

Also running /etc/cron.weekly/mythtv-database will create a backup.

---

### Post by rramesh on 2012-06-01
Thank you. I suppose it is that simple. May be that is why no other document exist. I will
try and it mark the thread solved after success.

Ramesh

---

