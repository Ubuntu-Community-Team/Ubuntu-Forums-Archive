---
title: "[SOLVED] Can't remember my sql database password"
date: 2008-01-06
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-01-06
I can't remember the SQL database password from when I installed mythbuntu.  The reason why I need it is because I think I need to do a repair on the database.  My scheduling information is lost.  I went to mythweb and got the following error:

Fatal Error at /usr/share/mythtv/mythweb/includes/objects/Database_Query_mysql.php, line 73:
SQL Error: Table './mythconverg/oldrecorded' is marked as crashed and should be repaired [#145]

So I'm trying to run the following command to repair my database but it's asking me for my password.

mysqlcheck --repair -umythtv -p mythconverg

I've tried my root password but it didn't work, I get the following error:

mysqlcheck: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect


I've seen posts where people have had to create a new database but I don't want to do that because I don' t want to have to reinput all of my recording preferences and such.

If I can't get my sql database password, then is there an easy way to restore a backup?  I remember reading a post saying that Mythbuntu automatically saves backups of the database.

---

### Post by Nikas on 2008-01-06
Look in
/etc/mythtv/mysql.txt
or
/usr/share/mythtv/mysql.txt

---

### Post by Meph1st0 on 2008-01-06
WONDERFUL! that worked like a charm.  Thank you very much.

---

### Post by jccubs on 2009-09-19
> **Nikas said:**
> Look in
/etc/mythtv/mysql.txt
or
/usr/share/mythtv/mysql.txt
 
how do I "look in" these places.  Not farmiliar at all with mythtv, and I did the same thing.  If these are directories, how do I access them??  I tried opening a terminal and typing this, but I only got the reply "Permission denied"   Please Please Please help - I'm going nuts with this!

---

### Post by Nikas on 2009-09-20
> **jccubs said:**
> how do I "look in" these places.  Not farmiliar at all with mythtv, and I did the same thing.  If these are directories, how do I access them??  I tried opening a terminal and typing this, but I only got the reply "Permission denied"   Please Please Please help - I'm going nuts with this!


```
sudo cat /etc/mythtv/mysql.txt
```

---

### Post by jccubs on 2009-09-20
when I did this it asked for my password.  I entered in what I thought was the password and then I got a very long message - each line started with te # sign.  The first line was TWO HOSTS MUST NOT USE THE SAME VALUE.  Does this mean that I need a different password?

---

