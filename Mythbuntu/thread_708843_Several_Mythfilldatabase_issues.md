---
title: "Several Mythfilldatabase issues"
date: 2008-02-26
forum: Mythbuntu
---

### Post by Rhiadon on 2008-02-26
I have set mythfilldatabase to run automatically. Whether it actually completes or not seems to be one of my problems. Sometimes, I'll be checking mythweb and I'll no upcoming recordings. This seems to indicate that mythfilldatabase crashed during an update. It requires that I run mysqlcheck to fix the database. Once I've done that, my upcoming recordings are back.

First, does anybody esle have a similar issue with mythfilldatabase corrupting the database?

Second, what did you do to fix it?

Third, I currently have no dates in the drop down box under Listings in mythweb. Running mysqlcheck didn't clear it up. I have all of my upcoming recordings still, just not dates in the drop down. Any ideas why this might be?

EDIT: I forgot to mention somethign that might be significant. My backend is running on a Athlon 64 X2 4200+. I saw some hints that there may be dual core issues with mythfilldatabase but my digging hasn't revealed anythign conclusive yet. If you know for certain that this causes the problem and know of a way to fix it, please let me know.

---

### Post by foxbuntu on 2008-02-28
Try running the following and see if the DB gets corrupted or if the issues resolve. Also make sure that your data grabber info (Connection to SchedulesDirect or whatever you use) is correct. Make sure your data source on the other end is also correct (It all sounds like it is however double check:

```
mythfilldatabase --replace-all
```

---

### Post by Rhiadon on 2008-02-28
Just so I understand...

--replace-all forces mythfilldatabase to re write all of the data from datadirect whether or not there is already data in the database?

---

### Post by newlinux on 2008-02-28
I think

```

mythfilldatabase --refresh-all

```

does that...

[http://www.mythtv.org/wiki/index.php/Mythfilldatabase](http://www.mythtv.org/wiki/index.php/Mythfilldatabase)

---

