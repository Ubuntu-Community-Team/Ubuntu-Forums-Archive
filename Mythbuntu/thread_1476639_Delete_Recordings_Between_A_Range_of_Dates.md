---
title: "Delete Recordings Between A Range of Dates"
date: 2010-05-08
forum: Mythbuntu
---

### Post by dsbw on 2010-05-08
Hey, all--

My MythTV setup went berserk over the week and failed recording by creating a bunch of entries for the same recording over the week. They're all bad, so I need to delete everything between the 3rd and the 6th. This is dozens, if not hundreds.

I'm sure I can do it with a SQL statement, but hoping someone has a starter and any gotchas to look out for.

---

### Post by ian dobson on 2010-05-08
Hi,

With a sql statement along the lines of

SELECT * 
FROM `recorded` 
WHERE `starttime` >= '2010-05-03 00:00:00'
and 
`starttime` <= '2010-05-06 23:59:00'

should display a list of recordings from  between 3rd and 6th. When your happy with the query just change select * to delete and let it rip.

Don't forget make a backup of your database first.


Regards
Ian Dobson

---

### Post by dsbw on 2010-05-08
Thanks, that did it.

I was concerned about referential integrity but I guess there isn't any?

---

### Post by ian dobson on 2010-05-09
Hi,

I've written a perl script that checks the database for errors.

In yor case if you deleted recordings that have entries in the seek/commflag table the script will find them. 

Have a look in this thread for more information:
[http://ubuntuforums.org/showthread.php?t=885411&highlight=CheckMythDB.pl](http://ubuntuforums.org/showthread.php?t=885411&highlight=CheckMythDB.pl)

Regards
Ian Dobson

---

