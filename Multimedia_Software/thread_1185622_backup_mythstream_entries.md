---
title: "backup mythstream entries?"
date: 2009-06-12
forum: Multimedia Software
---

### Post by sr_guy on 2009-06-12
Is there a program or a good script that can backup all entries (like you tube playlists) that have been manually entered? I've got a ton of entries and would be a pain to have to add them manually after I install newest Mythbuntu 9.04

---

### Post by andrewc6l on 2009-06-13
The streams table should be backed up when you run the MythTV backup:

[http://www.mythtv.org/wiki/Backup_your_database](http://www.mythtv.org/wiki/Backup_your_database)

Alternately, you could backup the streams table only by doing:

$ mysqldump -u <myth_user> -p --extended-insert --databases <myth_db_name> --table streams > mythstream.bak
Password: <myth_password>

After that, you'll want to back up /usr/share/mythtv/mythstream and the ~/.mythtv/mythstream/ directory for your MythTV user.

---

