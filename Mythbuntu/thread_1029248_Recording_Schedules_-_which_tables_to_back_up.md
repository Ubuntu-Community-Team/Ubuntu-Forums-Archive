---
title: "Recording Schedules - which tables to back up ?"
date: 2009-01-03
forum: Mythbuntu
---

### Post by Caysho on 2009-01-03
I want to migrate the data from knoppmyth to mythbuntu, specifically the recording schedules data shown when viewing mythweb/tv/schedules.

Is this in one table, or spread over several ?

---

### Post by newlinux on 2009-01-03
> **Caysho said:**
> I want to migrate the data from knoppmyth to mythbuntu, specifically the recording schedules data shown when viewing mythweb/tv/schedules.

Is this in one table, or spread over several ?

I can't remember the specifics right now, but the information the scheduler uses to create the recording schedule (the recording schedule is actually dynamic) spans across a couple of tables. This might help.

[http://www.mythtv.org/wiki/index.php/Category:DB_Table](http://www.mythtv.org/wiki/index.php/Category:DB_Table)

---

### Post by crez79 on 2009-01-03
> **newlinux said:**
> I can't remember the specifics right now, but the information the scheduler uses to create the recording schedule (the recording schedule is actually dynamic) spans across a couple of tables. This might help.

[http://www.mythtv.org/wiki/index.php/Category:DB_Table](http://www.mythtv.org/wiki/index.php/Category:DB_Table)

fyi that link shouldn't have :grin in it, it should be referencing the Catagory:DB_Table. I think the smilies got confused...

---

### Post by Caysho on 2009-01-05
Ok, I suspected it would be dynamic.
I had a brief look at the recording table structures.

The mythbuntu 8.10 database has storage_group and avg_delay.
The knoppmyth box doesn't have the storage group facility.
I assume there are other new fields, but I haven't looked further.

Would it be safe to dump the table contents and simply import the data into mythbuntu ?
Or will I have problems with default values being inserted for the new fields ?

---

### Post by Caysho on 2009-02-20
I installed myphpadmin and backed up the following tables:

[LIST]
[*]channel
[*]record
[/LIST]

On the new box, I had to change the storage group, but otherwise it displays everything after the listings are loaded.

---

### Post by Freddan101 on 2009-02-21
This is was I successfully did a couple of weeks ago to migrate all recordings data:

Backup
 
```
mysqldump -u root -p -t mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > recordings.sql
```
Restore

```
mysql -u root -pmythtv mythconverg –p < recordings.sql
```

---

### Post by Cuppa-Chino on 2009-02-25
how do I go about doing a merge?

what I mean is I have a live database to which I would like to **add** database info on other recordings (essentially my desktop broke and I had to use the laptop for a few weeks, now I have most things on the htpc desktop that I keep using but the laptop files would be nice to have in database too).

I do not want a new database but just to add the missing lines, unfortunately I am not a SQL-Wizard....

thanks

---

### Post by newlinux on 2009-02-25
you might want to look into myth.rebuilddatabase.pl - it is a bit tedious, but otherwise you will need to have a good understanding of the mythconverg DB and SQL.

[http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

---

### Post by Cuppa-Chino on 2009-03-01
> **newlinux said:**
> you might want to look into myth.rebuilddatabase.pl - it is a bit tedious, but otherwise you will need to have a good understanding of the mythconverg DB and SQL.

[http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

thanks for the answer - I checked it out and being a lazy guy I tried the brute force method first.

I used mysql admin & query browser to look at the tables and then used the backup & restore method from here: [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html]("http://www.mythpvr.com/mythtv/tips/migrate-recordings.html") to add the lines.

effectively I found:
backups made with mysqldump like so:
```
mysqldump -u mythtv -p -t mythconverg record recorded \ 
oldrecorded recordedprogram recordedrating \
recordedmarkup recordedseek > recordings.sql

```

could be **appended** with
```
mysql -u mythtv -p mythconverg < recordings.sql

```

but prior to doing so, I strongly recommend you do a full database backup

---

