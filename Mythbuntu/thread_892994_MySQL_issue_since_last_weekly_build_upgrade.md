---
title: "MySQL issue since last weekly build upgrade"
date: 2008-08-17
forum: Mythbuntu
---

### Post by uncle hammy on 2008-08-17
I think there is some bug introduced with the latest weekly build upgrade.  After it ran, I got a message saying that there were dependency issues, and 3 packages could not be installed, and mythtv-database was being left unconfigured.  Everything still worked, however every time apt-get upgrade was run, the output started with the following error message, then left 3 packages uninstalled and one "unconfigured"....

SQL: GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY 'password'\nAccess denied for user 'root'@'192.168.25.%' to database 'mythconverg' at -e line 8, <> line 1.

I tried adding access on MySQL (which had been added long ago, and I have no issues connecting to it with the MySQL Administrator from remote machines)....

GRANT ALL ON *.* TO root@'192.168.25.%' IDENTIFIED BY 'password'
as well as 
GRANT ALL ON *.* TO root@'192.168.25.%' IDENTIFIED BY ''
and 
GRANT ALL ON *.* TO root@'192.168.25.%'

with no luck

sudo dpkg-reconfigure mythtv-database resulted in an error message "mythtv-database not completely installed".

Finally, I tried apt-get remove --purge mythtv-database / apt-get install mythv-database, also with no luck, and was then unable to connect anymore.

Now, I had made some major changes to my network last week, and thought perhaps this had something to do with all my troubles (they first started on the day I made the changes), so I decided to just do a clean install of my backend.  After the installation, I downloaded all the available updates, and I'm right back in the same boat, though I did manage to get the database configured, and connected.

However, if I go dpkg-reconfigure mythtv-database, it works, and I can configure the database, but as soon as it exits, I get the error message.

SQL: GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY 'password'\nAccess denied for user 'root'@'192.168.25.%' to database 'mythconverg' at -e line 8, <> line 1.

Has anyone else encountered this since the latest weekly build updates, and if so have any ideas on rectifying the situation?

Thanks,
Scott

---

### Post by uncle hammy on 2008-08-17
I should also add, here's the output from select Host, User from users, showing the entry for root @ 192.168.25.%, which the error is complaining about....

+--------------+------------------+
| Host         | User             |
+--------------+------------------+
| %            | mythtv           |
| 127.0.0.1    | root             |
***| 192.168.25.% | root             |***
| localhost    | debian-sys-maint |
| localhost    | mythtv           |
| localhost    | root             |
| ultramagnus  |                  |
| ultramagnus  | root             |
+--------------+------------------+

P.S. Can anyone tell me what the ultramagnus entries are from?  THis is a perfectly clean install, with only the standard updates applied.

---

### Post by uncle hammy on 2008-08-19
No one has any ideas on this?

---

