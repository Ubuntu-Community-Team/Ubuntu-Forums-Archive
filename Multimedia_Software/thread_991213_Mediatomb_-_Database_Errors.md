---
title: "Mediatomb - Database Errors"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Wanko The Sane on 2008-11-23
Im trying to setup mediatomb to use with my PS3, but when im in the user interface trying to add files to the database i will get the error:

2008-11-23 13:22:50 WARNING: skipping /home/karl/Videos/South park Season 11 Complete/14 The List.avi : SQLITE3: (11) database disk image is malformed
Query:INSERT INTO "mt_cds_object" ("parent_id","object_type","upnp_class","dc_title","location","location_hash","ref_id") VALUES (3,1,'object.container','Videos','D/home/karl/Videos',4162592599,NULL)
error: database disk image is malformed


This error will repeat for ever file i try to add. I also am unable to remove to old files that i was able to add. I will get the same error. I have removed mediatomb and reinstalled it, but when i do it comes up the same way as it did before i deleted it.

Thanks

---

### Post by Risoh on 2009-11-18
I have the same issue. Anyone, please?

---

### Post by hradek on 2010-12-12
Hi, the database file was corrupted. Since I rescan every so often I was ok just deleting the database. It seems to have fixed it for me. Anyway, here is the command I ran:

```
$ sudo rm /var/lib/mediatomb/mediatomb.db
```

However, if you changed your database to be called something different you'll need to check in your MediaTomb config file.

---

