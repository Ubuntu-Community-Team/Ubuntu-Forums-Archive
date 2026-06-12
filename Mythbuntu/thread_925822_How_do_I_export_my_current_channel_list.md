---
title: "How do I export my current channel list?"
date: 2008-09-21
forum: Mythbuntu
---

### Post by jaakan on 2008-09-21
I would like do export my current channels, wipe my setup, install 8.10, and import my channel list.

How do I export to a file that is usable for importing?

---

### Post by ian dobson on 2008-09-21
Hi,

To just dump the channels just do:-

mysqldump -u username -ppassword --opt mythconverg channel > channel.sql


from the command line. Username/password is for access to the SQL database. Note the -p then the password without a space.

Regards
Ian Dobson

---

