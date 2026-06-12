---
title: "Database Issue"
date: 2014-03-30
forum: Mythbuntu
---

### Post by Al_Vampyre on 2014-03-30
I think I may be having a problem with my database but I'm not sure where to go next. This is the second time this issue has reared its head so I need to find out what is causing it. For some reason every single recording I have scheduled is showing as a duplicate, now I know that some of them are duplicates so that's OK but I also know that some of them are not. The last time this happened (a couple of weeks ago) I dropped the database and restored from the last backup and it seemed to sort the problem. Now that it has happened again I think I need to be preventing the issue rather than curing it when it happens...

Any ideas would be gratefully received :D

---

### Post by Al_Vampyre on 2014-04-07
No one has any ideas?

Is it possible this is a permissions issue? If so, how would I go about checking that?

---

### Post by blm-ubunet on 2014-04-07
Database:
There are 2 DB checking scripts included with mythtv..
One is mentioned here:
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)

You can (easily) access/run them via MythWeb (DB screen).
Probably safer to run from mythweb & when your system is not recording anything (or playing).
One of the scripts can take couple minutes..

You can invoke them from terminal.
Makes sense to check you can manually create a DB backup first..

Listings:
Depending on how you get your program listings..I would eyeball the raw xmltv files & check there are unique episode/series numbers &/or unique program details...

Check the recording rules.
Maybe one rule is causing a match on all/any recordings.
Maybe delete some/all of them & recreate.
I think the "previous recording" screen lets you access the recording rule used.

---

### Post by Al_Vampyre on 2014-04-08
Thanks for your reply, I have tried the Optimize and Repair Scripts and the only thing I've spotted is that the Record table says "Found row where the auto_increment column has the value 0" everything else is marked OK.

I'll try deleting the recording rules and see if it helps...

[EDIT] Looks like deleting some of the recording rules has made a difference, Thank You so much for the suggestion!! [/EDIT]

---

### Post by Al_Vampyre on 2014-04-16
> **blm-ubunet said:**
> Database:

Check the recording rules.
Maybe one rule is causing a match on all/any recordings.
Maybe delete some/all of them & recreate.
I think the "previous recording" screen lets you access the recording rule used.

Thanks to blm-ubunet my existing problem is now *mostly* solved (as in *mostly* harmless) what I would like to know is what would cause a recording rule to mark everything else as a duplicate? Is there any way of viewing the parameters that might affect other recording rules?

I guess I'm worried that this is a symptom rather than the actual disease and maybe there is something else I should be fixing...

---

