---
title: "MythWeb (0.22) - Recorded Programs page VERY slow!"
date: 2010-01-22
forum: Mythbuntu
---

### Post by tombongo on 2010-01-22
***_[COLOR="Red"]FOR SOLUTION: LOOK AT POST #3[/COLOR]_***

Currently when I am using MythWeb and I go to the Recorded Programs page, it takes close to 10 minutes to load.  I have been using Mythbuntu 9.10 since its launch, and this just started happening in the past week or two.  It doesn't matter what computer I am using or where I am (home, work, etc).  After that, any subsequent trips to the page are normal speed.  It doesn't matter were the attempts are, it takes around 10 minutes for the first and 10 seconds for the second+ attempts.

Ex 1: first attempt - home 10min, second+ attempts home 10sec.
Ex 2: first attempt - work 10min, second+ attempts work 10sec.
Ex 3: first attempt - home 10min, second+ attempts work 10sec.
Ex 4: first attempt - work 10min, second+ attempts home 10sec.

The page loads fine until I either record a new show or delete a show.  Everything else with MythTV and MythWeb seems to behave fine.

Some more info:
When this is happening, mysqld is using over 98% of the CPU the entire time.  I ran "mysqladmin -u root -p processlist" and it returned:

```
+-----+--------+-----------+-------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+
| Id  | User   | Host      | db          | Command | Time | State          | Info                                                                                                 |
+-----+--------+-----------+-------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+
| 7   | mythtv | localhost | mythconverg | Sleep   | 39   |                |                                                                                                      |
| 12  | mythtv | localhost | mythconverg | Sleep   | 2837 |                |                                                                                                      |
| 28  | mythtv | localhost | mythconverg | Sleep   | 245  |                |                                                                                                      |
| 106 | mythtv | localhost | mythconverg | Sleep   | 55   |                |                                                                                                      |
| 143 | mythtv | localhost | mythconverg | Sleep   | 180  |                |                                                                                                      |
| 164 | mythtv | localhost | mythconverg | Sleep   | 42   |                |                                                                                                      |
| 210 | mythtv | localhost | mythconverg | Query   | 36   | Sorting result | SELECT recordedmarkup.type
                                    FROM recordedmarkup
                  |
| 216 | root   | localhost |             | Query   | 0    |                | show processlist                                                                                     |
+-----+--------+-----------+-------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+
```

This output was the same the entire time also.

---

### Post by tombongo on 2010-03-10
I am adding a little info in a desperate attempt to fix this problem.

Almost every search I do about this results in incorrect preview image generation, but that is not my problem.  Preview images are only generated when expected.

I also suspected that it might be related to the memory allocated to PHP in apache.  I raised that from 16MB to 256MB, but saw no change in the problem.

I tried a rebuild of my backend with a partial restore of the database.  This didn't fix the problem as I expected.  I believe it is related to my recordxxxxxx tables that are included in a partial restore.  I now have phpMyAdmin installed, but I am not sure what to look for and where.

Repairing (no errors reported) and optimizing the tables does not seem to affect anything.

The mysql process list shows that mysqld is performing a "SELECT recordedmarkup.type FROM recordedmarkup" query the entire time.  I am able to do the same query via the command line with no delay.  Is there something that could be blocking mysqld and making it take the entire CPU for that time period?

My next considerations are to backup and truncate the recordedmarkup table.  Another approach might be to use mytharchive to get the recordings and metadata out of the tables, and import it all into a new database.  The mytharchive option will move 300GB of recordings during the process though.  That is not very tempting.

There are no logs that I can find in /var/log and /var/log/mythtv that show any problems.

Any thoughts?  Please!

---

### Post by tombongo on 2010-03-10
FIXED! SOLVED! FIXED! SOLVED! FIXED! SOLVED!

I figured it out.  I was looking at my recordedmarkup table quite a bit this morning.  I have around 200 recordings and my recordedmarkup table had around 22,000 rows.  From what I understand to be in the table, it seemed like too many rows.  I asked a friend to look at his and he had less than ten times as many rows as recordings.  I was looking at the type column values, and noticed some values not mentioned in the wiki.  I did find them in the current programinfo.h header file.  There was a VERY large number of 30 & 31 values in the type column.  A process of elimination narrowed it down to a half dozen FireWire recordings that happened on January 18th & 19th, 2010.  I was doing my upgrades around then and most definitely had temporary FireWire issues.  Since they were not very important recordings, I deleted and re-recorded them from the MythWeb recordings page.  Now my table has around 1,500 rows and all is well!

---

