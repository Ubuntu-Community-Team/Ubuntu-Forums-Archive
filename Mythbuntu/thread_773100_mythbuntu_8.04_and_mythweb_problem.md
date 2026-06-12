---
title: "mythbuntu 8.04 and mythweb problem"
date: 2008-04-28
forum: Mythbuntu
---

### Post by declanh on 2008-04-28
I am getting the following message when trying to access mythweb

"Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.
"

mysql and /usr/share/mythtv/mythweb/mythweb.conf.apache
both have the same password for the DB. I have tried logging into mysql from the commandline ok but mythweb is still broken. I think this worked ok for me on 8.04RC
# setenv db_server "localhost"
setenv db_server "192.168.1.xxx"
setenv db_name "mythconverg"
setenv db_login "mythtv"
setenv db_password "<pwd>"

any ideas what else to try ?
My previous install (8.04 rc) i was using dynamic ip address - but on this one Ive changed this install to run with static IP - that should not make any diff should it ?

D

---

### Post by laga on 2008-04-28
Is the password in /etc/apache2/sites-enabled/mythweb.conf correct, too?

---

### Post by declanh on 2008-04-28
> **laga said:**
> Is the password in /etc/apache2/sites-enabled/mythweb.conf correct, too?

no, it wasn't - but it is now and its working ! 
Many thanks :)
D

---

### Post by ubunaut on 2008-05-05
> **declanh said:**
> no, it wasn't - but it is now and its working ! 
Many thanks :)
D

that worked for me too, just don't forget to restart apache :D

---

