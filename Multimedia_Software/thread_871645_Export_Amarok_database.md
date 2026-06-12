---
title: "Export Amarok database?"
date: 2008-07-27
forum: Multimedia Software
---

### Post by anj on 2008-07-27
Is there any way to export/import Amarok's database to another system? i.e. keeping play counts, etc.

---

### Post by maphilli14 on 2008-08-13
I've not tried this yet myself but intend to very soon:

[http://amarok.kde.org/wiki/MySQL_HowTo#Automatic_Backups](http://amarok.kde.org/wiki/MySQL_HowTo#Automatic_Backups)

I'll let you know.

Mike

---

### Post by maphilli14 on 2008-08-13
WHOA, play counts and ratings don't seem to carry over.  Easier directions here:

[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

Mike

PS - see this one through, as even though I'm not sure I got 100% of my stats, I got the majority.  Sorry for the blow by blow, but try this one:

[http://amarok.kde.org/wiki/MySQL_HowTo:](http://amarok.kde.org/wiki/MySQL_HowTo:)

In particular
> An alternate method is to import my SQLite data as follows:

    * Start Amarok, change to MySQL, and build the database (but don't play any songs)
    * Download SQLite Database Browser
    * Export the statistics database to a dump file, amarok_dump.sql
    * Remove all BEGIN TRANSACTION, COMMIT and CREATE sql commands
    * Import the file using MySQL: 


Let me know if this works as it's somewhat obtuse directions.

---

### Post by afrodeity on 2010-12-23
How do I clear the amarok database? Need to reset it, or force it to rescan, its only taking one example from each album, very irritating, maverick

---

