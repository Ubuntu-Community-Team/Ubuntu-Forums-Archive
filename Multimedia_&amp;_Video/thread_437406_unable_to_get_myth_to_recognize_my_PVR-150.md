---
title: "unable to get myth to recognize my PVR-150"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by halo6819 on 2007-05-08
hey all, Im having some trouble getting mythtv to recognize my Haupage pvr-150 card. i followed the instructions to a T from the sticky, tried twice actually (this time from a fresh install) and still no luck. here is some screen shots of whats going on.

Going to the Capture Card Page:
[IMG]http://img.photobucket.com/albums/v493/halo6819/Screenshot1.png[/IMG]

Setting up the card:
[IMG]http://img.photobucket.com/albums/v493/halo6819/Screenshot2.png[/IMG]

and voila, nothing happens!
[IMG]http://img.photobucket.com/albums/v493/halo6819/Screenshot3.png[/IMG]

the system im setting this up on is Rei, system specs in signiture
(i have not installed the ATI Drivers yet as per the recommendation of the Sticky, though the first time i tried installing Myth, i did have the drivers installed.)

---

### Post by newlinux on 2007-05-08
Hmm, sounds like it isn't saving your tuner, which probably means you have a database problem. Have you looked at your mythbackend logs?
```

tail /var/log/mythtv/mythbackend.log

```

Let us know what you see. There was another person I helped on another board that had this problem (he couldn't get it to save video sources either) and it was a mysql problem. He ended up reinstalling the mythdatabase.

We should be able to verify it is a database problem from your logs. Post the results.

---

### Post by halo6819 on 2007-05-08
> tail /var/log/mythtv/mythbackend.log
2007-05-08 16:44:34.585 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-08 16:44:34.589 New DB connection, total: 3
2007-05-08 16:44:34.592 Connected to database 'mythconverg' at host: localhost
2007-05-08 16:44:34.648 Told to create a NEW database schema, but the database
already has 22 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-08 16:44:34.655 Database Schema upgrade FAILED, unlocking.
2007-05-08 16:44:34.658 Couldn't upgrade database to new schema


this is what i got. must admit, its all Greek to me :)

---

### Post by newlinux on 2007-05-08
Sounds like database corruption of some sort. Since this is a new installation, I recommend removing and reinstalling the database:
```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database
```

And try setup again.

---

### Post by halo6819 on 2007-05-09
thanks that did the trick

---

### Post by cainmark on 2007-05-10
> **newlinux said:**
> Sounds like database corruption of some sort. Since this is a new installation, I recommend removing and reinstalling the database:
```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database
```

And try setup again.

Thank you!  That finally got my MythTV to work correctly in Edgy Eft.

---

