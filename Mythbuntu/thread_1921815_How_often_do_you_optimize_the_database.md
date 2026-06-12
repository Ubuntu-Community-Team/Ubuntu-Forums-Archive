---
title: "How often do you optimize the database?"
date: 2012-02-07
forum: Mythbuntu
---

### Post by GaryP2 on 2012-02-07
Can anyone comment on how frequently they optimize the database and what your experience has been? Has it changed the performance for better or for worse, or has it broken anything? Lately I’ve noticed slight playback pauses or glitches, typically I think at the top of the hour when recordings start or stop, or when I’m deleting a recording. I have a single drive system (OS and recordings on the same drive) and am using XFS for the recordings partition. When I built the system 18 months ago I stressed tested it and found little or no issues like this. I have my XFS partition mounting with allocsize=512m and xfs_db is indicating a fragmentation factor of about 68% (which is considered okay according to the wiki). My system is frequently recording 2-3 shows at a time.
 
I do daily cron-scheduled database backups to NAS but otherwise haven’t had to do much other maintenance activities to this point (except periodic offline clonezilla backups of the OS partition). I’m only assuming at this point that the glitches I’m of might be related to database fragmentation. I’ve upgraded from 23.1 to a couple months back 24.1 and Mythbuntu/MythTV has exceed my expectations overall.

 *Edit to add:* OS partition is about 75% full and recording partition is typically 33-66% full. The system is primarily used for timeshifting and not archiving shows.
  
I was going to follow these instructions but wanted to hear other’s experience before I tried the script. Thanks much.
 
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database)
 
Here are my recording statistics from the past 18 months if that is of any interest.
 
Number of shows: 231 
Number of episodes: 11873 
First recording: Friday August 20th, 2010 
Last recording: Tuesday February 7th, 2012 
Total Running Time: 1 year 5 months 18 days 5 hrs 15 mins 
Total Recorded: 1 year 14 days 11 hrs 21 mins 
Percent of time spent recording: 7%

---

### Post by wyliecoyoteuk on 2012-02-07
well, IIRC, there is an "optimise database" tickbox in mythbuntu contorl centre, and you can also activate db repair cron jobs from there (in 11.10 anyway)
so you can try it from there to see if that is the problem.

---

### Post by nickrout on 2012-02-07
mythbuntu sets the system to check the database and back it up weekly via ```
/etc/cron.weekly/mythtv-database
```

you can run the script manually any time you want.

personally I move it to /etc/cron.daily and set it to keep 2 or 3 weeks of backups.

---

### Post by GaryP2 on 2012-02-07
Thanks for replies.
> **wyliecoyoteuk said:**
> well, IIRC, there is an "optimise database" tickbox in mythbuntu contorl centre, and you can also activate db repair cron jobs from there (in 11.10 anyway)
so you can try it from there to see if that is the problem.
 
I see two options appears in my 10.04 Mythbuntu Control Centre under MySQL: "Enable daily MySQL DB OptimizeRepair cron job" and "Enable MySQL performance tweaks". Neither of them are enabled. Does anyone know what scripts these enable or if having them enabled has ever caused any undesirable effects?
 
> **nickrout said:**
> mythbuntu sets the system to check the database and back it up weekly via ```
/etc/cron.weekly/mythtv-database
```
 
you can run the script manually any time you want.
 
personally I move it to /etc/cron.daily and set it to keep 2 or 3 weeks of backups.
I actually have a /etc/cron.daily/mythtv-database also that does my daily backup, mounting a CIFS share and then performing an rsync against the directory where I have rotation backups. I edited this script some time ago from some examples I found somwhere to do both some sort of DB check and also do a backup to my remote NAS disk. In that script, amongst other lines to do the backup, CIFS mount, and rsync, there are the following lines:
 
 
```
 
DBNAME="mythconverg"
DEBIAN="--defaults-extra-file=/etc/mysql/debian.cnf"
/usr/bin/mysqlcheck $DEBIAN -s $DBNAME

```
 
 
The wiki I referenced in my first post is outdated because the file no longer exists at that location. I found the file /usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl that contains the following code: 
 
```
 
#!/usr/bin/perl -w
#
# Connects to the mythtv database and repairs/optimizes the tables that it
# finds.  Suggested use is to cron it to run once per day.
#
# @url       $URL$
# @date      $Date$
# @version   $Revision$
# @author    $Author$
# @license   GPL
#
# Includes
    use DBI;
    use MythTV;
# Connect to mythbackend
    my $Myth = new MythTV({'connect' => 0});
# Connect to the database
    $dbh = $Myth->{'dbh'};
# Repair and optimize each table
    foreach $table ($dbh->tables) {
        unless ($dbh->do("REPAIR TABLE $table")) {
            print "Skipped:  $table\n";
            next;
        };
        if ($dbh->do("OPTIMIZE TABLE $table")) {
            print "Repaired/Optimized: $table\n";
        }
        if ($dbh->do("ANALYZE TABLE $table")) {
            print "Analyzed: $table\n";
        }
    }

```
 
I'd like to understand what the difference between what the mysqlcheck is doing in the script I already have running vs. what the mythdb.pl script in the second example vs. what happens when I check one of both of the options in Mythbuntu Control Centre. Thanks again!

---

### Post by GaryP2 on 2012-02-20
Running the OptimizeRepair script eliminated the brief pauses I was seeing during playback when other recordings start, stop, or are deleted. Turning on the option "Enable daily MySQL DB OptimizeRepair cron job" placed a copy of optimize_mythdb in /etc/cron.daily. I ran the script manually the first time – it walked through and optimized the tables in just a few seconds and I could immediately see that things were running smoother. I’ve had it running daily for over a week with no issues.
 
A couple days ago I turned on "Enable MySQL performance tweaks”. This created the file /etc/mysql/conf.d/mythtv-tweaks.cnf with the following contents. Enabling this may have made my frontends start playback slightly faster, but otherwise I can’t really tell any other difference. Note that the contents of this file is just slightly different than what’s documented in the mythtv.org wiki MySQL Database Tweaks.
 
```
[mysqld]
# The following values were partly taken from:
# http://www.gossamer-threads.com/lists/mythtv/users/90942#90942
# key_buffer = 48M
# max_allowed_packet = 8M
table_cache = 128
sort_buffer_size = 48M
net_buffer_length = 8M
# thread_cache_size = 4
query_cache_type = 1
query_cache_size = 32M
# don't do binary logs for mythconverg
binlog_ignore_db = mythconverg
```
 
I just thought I’d give an update to this thread in what effects I found these two options gave me. My database slowly got more and more fragmented to where I didn’t really notice it until in recent weeks. I should have just enabled both of these options on day one but was reluctant to change any defaults given that I was new to MythTV.

---

