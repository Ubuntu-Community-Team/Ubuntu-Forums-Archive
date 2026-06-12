---
title: "mythconverg upgrade for mythtv 0.23 fails"
date: 2011-05-28
forum: Mythbuntu
---

### Post by MartinusEx on 2011-05-28
Hi folks,

i did an upgrade ubuntu 8.04 / mythtv 0.21 to ubuntu 10.04 / mythtv 0.23

Unluckily I believed this would work as usual and so I did not read ahead of this.

Well, in the aftermath I got to the utf-8 / latin1 issue in the mythconverg database.
Unluckily as well I probably mixed up backups.
Now I have one backup which I'm quite sure it is the original one.

googling I found this page
[http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding]("http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding")

Running the scripts as proposed seems not to have the desired effect.

When I run mytbackend_setup, it ends up in failing to update the database from 1215 to 1254.
The error message always tells me that the scheme of the database is not correct althoug i did the things as said above.

Here is my questions:

Are any other ways known to convert mythconverg to the correct scheme

Any other reasons beside the necessary conversion why this fails

Any other method to determine what is wrong with my now "uncorrupted" database

THX a lot

Martin

---

### Post by BicyclerBoy on 2011-05-28
I have a dim distant memory of a database schema upgrade blockage around the time of 0.21.
The problem was caused by the mythvideo plugin schema change.
I had upgraded the MythTV version & had not re-installed mythvideo. Then overall schema upgrade would fail. 

The solution was to re-install the plugins & re-run mythtv-setup.
The individual plugins have schema versions as well.

I'm fairly sure this was needed as well ...
[http://www.gossamer-threads.com/lists/mythtv/users/406462#406462](http://www.gossamer-threads.com/lists/mythtv/users/406462#406462)

Very unlikely to help:
There are a couple of database optimisation scripts to try..
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)

---

### Post by MartinusEx on 2011-05-29
Hi BicyclerBoy.

thank you for your input.
I went through tho attached links.
Especially the maintenance link is now bookmarked.

When mythtv swithced from 0.21fies upwards there seem to have been several issues regarding the database, which made it hard to aupgrade.

Some error messages talk about "real" database errors like missing tables where mythback-end, on my box, when try to upgrade talks about "wrong scheme".
I never was able to take a close look to the message because it vabishes quickly.


Nevertheless I "somehow" managed to have an upgraded database available.
I'M not sure if it contains the listing of recent recordings, but for sure it does NOT contain settings.
So this is where I'm stuck now, setting up the box.


Thanks again for your contribution


Martin

---

### Post by BicyclerBoy on 2011-05-29
If you run/launch **mythtv-settings** from a terminal you will get the error messages to 'stick'.
It should have some cmdline options for **--verbose** level.

BTW The char set encoding mess was fixable without doing any update/upgrade.

Remember MythTV does a database backup before schema upgrades..

You can always dump the current database & re-instate the old database backup..
Fix the char set encoding & remove any mythvideo junk as per the link..
Run the optimisation/cleanup script..

Then let the 0.23 mythtv-settings upgrade the schema...

---

### Post by MartinusEx on 2011-05-30
Hi BB ;)
I'll give that a try.. come back later

THX so far

Martin

---

