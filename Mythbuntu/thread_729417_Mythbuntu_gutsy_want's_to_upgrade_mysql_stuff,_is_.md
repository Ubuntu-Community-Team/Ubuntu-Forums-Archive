---
title: "Mythbuntu gutsy want's to upgrade mysql stuff, is this ok?"
date: 2008-03-19
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-03-19
Hello all,
I am running Mythbuntu Gutsy as a slave backend/frontend. I am also running Feisty with Mythtv from Fixes repo. They are both 20.2 to my knowledge. Anyway, my gutsy box is showing updates to mysql stuff and before I do it I want to know if it's going to screw up mythtv somehow. Here's what the update manager is showing:

libkrb53
libmysqlclient15off
mysql-client
mysql-client-5.0
mysql-common
tzdata

Is it ok to upgrade all these? My feisty box shows that these related packages are installed on it:

mysql-common
State: installed
Version: 5.0.38-0ubuntu1.2

mysql-client
State: installed
Version: 5.0.38-0ubuntu1.2

mysql-client-5.0
State: installed
Version: 5.0.38-0ubuntu1.2

I am guessing it's ok, but wanted to make sure first. Thanks for any help here.

---

### Post by dannyboy79 on 2008-03-26
bump. can anyone inform me if they have upgraded the following packages and your mythtv system still works including mythweb?

---

### Post by lavinog on 2008-03-26
most updates are for security reasons and rarely remove functionality.
I would go ahead and do the update.

If the mysql updates had something that messes up your machine then you would hear alot of complaints since mysql is the backbone to many setups (especially internet sites)

---

### Post by ian dobson on 2008-03-26
Hi,

Updated my mysql backend a while back and didn't have any problems. So it should be OK maybe do a backup from your database's before you try.

Regards
Ian Dobson

---

### Post by bawilson2 on 2008-03-26
I didn't have any problems doing the upgrade either.

---

### Post by dannyboy79 on 2008-03-27
thank you all, I do have backups of my mysql databases but just wanted to make sure with other users before I did it. thanks all.

---

