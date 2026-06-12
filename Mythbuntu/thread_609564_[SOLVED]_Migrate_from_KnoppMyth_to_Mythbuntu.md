---
title: "[SOLVED] Migrate from KnoppMyth to Mythbuntu"
date: 2007-11-11
forum: Mythbuntu
---

### Post by .nedberg on 2007-11-11
Hello

I just set up a new MythBox with Mythbuntu. I also have a old KnoppMyth box witch was giving me some problems bacause of faulty hardware.

I want to transfer my old recordings from the KnoppMyth box to the new Mythbuntu box. Do any of you have an idea how I could do this?

I am not going to be using the old harddrive in the new box, but I can fit it in there just to transfer the files and database info. The new box does not have any recordings yet.

By the way; Mythbuntu is really easy to set up and I really like it!

---

### Post by tgm4883 on 2007-11-15
You should just be able to copy the recordings over.  To get the recordings data though, you need to back up your old database, drop the new database, and restore the old database on the new system.

---

### Post by uopjohnson on 2007-11-15
You can just backup the recorded table and move it over along with the recordings.  
On knopmyth box:
```
mysqldump -u mythtv -p mythconverg recorded > recorded.sql
```
and then on new box
```
mysql -u mythtv -p mythconverg < recorded.sql
```
I would also mark all of the commercials as unflagged so that they can be flagged again:
```
mysql -u mythtv -p mythconverg
mysql>update recorded set commflagged=0

```
Only do that last step if you have no current recordings on your new box that have already been commercial flagged.

---

### Post by .nedberg on 2007-11-18
> **uopjohnson said:**
> You can just backup the recorded table and move it over along with the recordings.  
On knopmyth box:
```
mysqldump -u mythtv -p mythconverg recorded > recorded.sql
```
and then on new box
```
mysql -u mythtv -p mythconverg < recorded.sql
```
I would also mark all of the commercials as unflagged so that they can be flagged again:
```
mysql -u mythtv -p mythconverg
mysql>update recorded set commflagged=0

```
Only do that last step if you have no current recordings on your new box that have already been commercial flagged.

I did just as you said and it kind of worked. I had to use '-u root' instead of mythtv (might be because I new that password...). I also marked the recordings as not commflagged. Now I only have to flag them again... I probably could have moved another table from the old backend, but this is no problem. Thanks a lot!

---

### Post by uopjohnson on 2007-11-18
yea, you can move the comflag table, but I prefer to just move the minimum possible and then let myth handle getting itself up to speed.

---

### Post by .nedberg on 2007-11-19
> **uopjohnson said:**
> yea, you can move the comflag table, but I prefer to just move the minimum possible and then let myth handle getting itself up to speed.

Yes, I agree. That was why I didn't want to bring the complete DB from the old mythbox.

I just did a ```
mythcommflag --queue
``` on the new server and all the old recordings are now qued for commercial flagging!

By tha way, I am getting way better quality on Live TV on the new server compared to the old. Do tou know of any reason for this to happen? I am sure the profiles are the same. Have not checked any recordings yet, but it might be the same way... I am also able to watch live tv from two laptops via wireless, something I could not do with the old server. All in all I am very pleased with Mythbuntu!

---

### Post by larsolav on 2008-03-13
This is a great "how to." But how do you export/import all the meta data information for MythVideo? Is there a way to do it so I don't have to re-enter this info? I have a lot of videos that are not on IMDB (such as various PBS videos for the kids), and I would like to backup this data as well as the recordings data.

Thanks and cheers!

Lars

---

### Post by uopjohnson on 2008-03-13
Looks like that info is stored in the videometadata table. 
[http://www.mythtv.org/wiki/index.php/Videometadata_table](http://www.mythtv.org/wiki/index.php/Videometadata_table)
you just need to replace recorded with videometadata and you should be all set.  I haven't ever done this though so I would test it first before you remove your old system. It is possible that this table is linked to other tables which also need to be moved.

---

