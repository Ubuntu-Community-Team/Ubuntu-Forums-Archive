---
title: "Find orphaned files...."
date: 2008-12-30
forum: Mythbuntu
---

### Post by jakev383 on 2008-12-30
Okay, so I had to restore my whole system to new hardware due to a crash. I went ahead and upgraded to 8.10 while I was at it (was running 7.10 still), but ran into an issue when copying over my old recordings....
I now have some shows that were deleted on the new machine (using the remote in mythfrontend), but the files are copied over from the old machine copied over after they were deleted on the front end... Don't ask). How do I go about finding these orphaned files that are deleted from the database so that I can reclaim the HD space?
Thanks!

---

### Post by klc5555 on 2008-12-30
> **jakev383 said:**
> Okay, so I had to restore my whole system to new hardware due to a crash. I went ahead and upgraded to 8.10 while I was at it (was running 7.10 still), but ran into an issue when copying over my old recordings....
I now have some shows that were deleted on the new machine (using the remote in mythfrontend), but the files are copied over from the old machine copied over after they were deleted on the front end... Don't ask). How do I go about finding these orphaned files that are deleted from the database so that I can reclaim the HD space?
Thanks!

From the /contrib directory (or [http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/)), you need to set up and run the script myth.find_orphans.pl 

It will allow you to either delete files which have no db entry, or fix the db entry when there is no matching file. Instructions for the script's use are contained in the comments at the beginning of the script itself, as the wiki entry is somewhat less than useful.

Cheers! :)

---

### Post by 2hot6ft2 on 2008-12-30
Here are a few ways to reclaim space.
This has a nice cleanup feature [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
Also if you run

```
sudo apt-get autoremove
```

it will clear out some packages that are no longer needed.

Localepurge - purges language files for things you don't speak or anticipate speaking.

GtkOrphan- removes orphaned files, frees disk space
INSTEAD... You could just install deborphan and create a new filter in Synaptics:

Settings > Filters > New and uncheck all boxes except 'Orphaned'. You'll now have a new category in the Custom tab that does the same as gtkorphan.

---

### Post by tgm4883 on 2008-12-30
> **2hot6ft2 said:**
> Here are a few ways to reclaim space.
This has a nice cleanup feature [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
Also if you run

```
sudo apt-get autoremove
```

it will clear out some packages that are no longer needed.

Localepurge - purges language files for things you don't speak or anticipate speaking.

GtkOrphan- removes orphaned files, frees disk space
INSTEAD... You could just install deborphan and create a new filter in Synaptics:

Settings > Filters > New and uncheck all boxes except 'Orphaned'. You'll now have a new category in the Custom tab that does the same as gtkorphan.

Please read the OP and not just the topic.  While your information is good, it is not relevant to the discussion here.

:EDIT:

At the very least, look at what forum you are posting in.

---

### Post by ian dobson on 2008-12-31
Hi,

I've written a small script (MythCheckDB.pl) that as the name says checks your database against your fs/system configuration.

You can download it from my website (under software tools)

Regards
Ian Dobson

---

### Post by jakev383 on 2008-12-31
> **klc5555 said:**
> From the /contrib directory (or [http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/)), you need to set up and run the script myth.find_orphans.pl 

It will allow you to either delete files which have no db entry, or fix the db entry when there is no matching file. Instructions for the script's use are contained in the comments at the beginning of the script itself, as the wiki entry is somewhat less than useful.

Cheers! :)

Tried your suggestion... but didn't work. I got an error:
```

root@myth-server:/usr/local/sbin# ./myth.find_orphans.pl 
DBI connect('database=mythconverg:host=myth-server','mythtv',...) failed: Can't connect to MySQL server on 'myth-server' (111) at ./myth.find_orphans.pl line 99
Cannot connect to database mythconverg on host myth-server:

```

Any ideas on that one?

---

### Post by klc5555 on 2009-01-01
> **jakev383 said:**
> Tried your suggestion... but didn't work. I got an error:
```

root@myth-server:/usr/local/sbin# ./myth.find_orphans.pl 
DBI connect('database=mythconverg:host=myth-server','mythtv',...) failed: Can't connect to MySQL server on 'myth-server' (111) at ./myth.find_orphans.pl line 99
Cannot connect to database mythconverg on host myth-server:

```

Any ideas on that one?


Looks like you may not have given the script the MYSQL password in the --pass variable. Also, --user should likely be mythtv rather than root, since a quirk of Mythbuntu is that root doesn't get access to MYSQL and mythconverg.

Cheers! :)

---

### Post by jakev383 on 2009-01-02
Thanks! Adding the command line --user and --pass worked for me.
It shows that *ALL* of my imported files do not have DB entries; they do show up under my front end and I can watch them, but I get a weird issue that when I exit from watching a video it will then show the file as unavailable as well as all others in the same TV series until I exit from the menu and then come back to it. Then they all work correctly again until I exit from a show again.
The only file that it shows IS in the DB is the one show it recorded yesterday. I'm assuming the DB format changed a little/some and that's why my imported shows do not work 100% correctly. I'll be through them all soon anyway (moving most to DVD) so hopefully I'll get them all cleaned off in the next couple weeks. I'll try the script again then, I guess.
(BTW - was there a step I missed when importing a .20 DB into the .21 system by chance? I know I get no icons for any of the old system's shows in mythweb either.....)

---

### Post by klc5555 on 2009-01-02
> **jakev383 said:**
> Thanks! Adding the command line --user and --pass worked for me.
It shows that *ALL* of my imported files do not have DB entries; they do show up under my front end and I can watch them, but I get a weird issue that when I exit from watching a video it will then show the file as unavailable as well as all others in the same TV series until I exit from the menu and then come back to it. Then they all work correctly again until I exit from a show again.
The only file that it shows IS in the DB is the one show it recorded yesterday. I'm assuming the DB format changed a little/some and that's why my imported shows do not work 100% correctly. I'll be through them all soon anyway (moving most to DVD) so hopefully I'll get them all cleaned off in the next couple weeks. I'll try the script again then, I guess.
(BTW - was there a step I missed when importing a .20 DB into the .21 system by chance? I know I get no icons for any of the old system's shows in mythweb either.....)


What a nightmare! This is one reason (of several) why I kept my master backend running 7.10 while upgrading the myth packages themselves to 0.21. 

Anyway, if you wish to, and if you know what the imported files actually are (which shows, etc.), you could add them all back in with myth.rebuilddatabase.pl  It will check the schedules for the last 10 days (or to whenever your new database came up if less than 10 days ago) for information; other titles you have to add by hand. Then keep what you want and delete what you don't from the frontend. The script will take some considerable time to run, as it will request user input with each file and will want to commflag the added file.

Good luck!

---

### Post by august495 on 2009-01-03
I tried:

```
 ./myth.find_orphans.pl --user=mythtv --pass=XXXXX 
```

But I still can't get it to connect to the database, any ideas?

---

### Post by ian dobson on 2009-01-03
Hi,

Try downloading my script from [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt) it does the same as myth.find_orphans.pl and is abit easier to use.

Regards
Ian Dobson

---

### Post by august495 on 2009-01-03
Worked like a charm, thanks!

---

### Post by mtader on 2009-04-08
I am looking for a way to clean up orphaned files on my backend.  The programs were deleted via the frontend, but the .mpg files still exist on the backend.  When you physically count the programs that are in the recorded area, they do not match the number it thinks it has.  Is there a script that will delete these files?  I tried running check_recordings.4.pl, and it comes back and says "known file" for every one.  I can look at the filename and it is one that I recognize that I just deleted from the front end.  I ran your script from you site in hopes that it would also clean it up, but it did not.  I may not have run it properly, etc.   I am somewhat a newbie, so any help would be appreciated!!!

---

### Post by newlinux on 2009-04-09
> **mtader said:**
> I am looking for a way to clean up orphaned files on my backend.  The programs were deleted via the frontend, but the .mpg files still exist on the backend.  When you physically count the programs that are in the recorded area, they do not match the number it thinks it has.  Is there a script that will delete these files?  I tried running check_recordings.4.pl, and it comes back and says "known file" for every one.  I can look at the filename and it is one that I recognize that I just deleted from the front end.  I ran your script from you site in hopes that it would also clean it up, but it did not.  I may not have run it properly, etc.   I am somewhat a newbie, so any help would be appreciated!!!

Have you checked that those extra recordings files aren't liveTV recordings? Just double checking that that isn't the issue... I know you said you verified these were the files you deleted from the frontend.

---

### Post by tgm4883 on 2009-04-09
Also, if you have selected slow delete (I think in mythtv-setup) or there is also a setting where it doesn't delete the files until it needs space, then those files will exist until mythtv needs the disk space or the files have been shrunk enough to be deleted.

Both of those option are off by default.  If you go into mythweb, and access the recorded programs page, find the drop down menu for "Show Group" and select it.  If you see a "Deleted" option, then the shows won't delete until mythtv needs the space.

If you want to check to see if you have slow delete on, then while not recording anything (and doing nothing else that will write or delete things from the disk) you can open a terminal and do a 'df' every couple seconds, if you see your recording partition used space slowly getting smaller, that is an indicator you have it set active.

---

### Post by mtader on 2009-04-09
These are definately formal recorded programs, to the tune of about 300+ programs!  I did a couple of deletes specifically to watch to see if the related files were deleted and they were not, so I am sure that they are not LiveTV.  I also do not have "slow delete" on since my server can handle a reasonably heavy load.

hmmm  .. I do not recall a setting that keeps the files until it needs space.  Do you know what setup screen that is on, or what that parameter is called?  I will look for it as well, but do not recall that one.

---

### Post by mtader on 2009-04-09
I found what I think you were referring to....  There is a check box in the setup / TV Settings / General, that says "auto expire instead of delete recording".  That was checked, so it creates another group that I never noticed called deleted.  All of my programs were still in there, so the mpg files stayed obviously, and the scripts I ran to clean up the files in the database said "known file" because it was still known to the system in the deleted group.  Simple, stupid, but simple to not see the extra added group since I do not use groups, so I have it set not to prompt for groups.  Never saw it....  Thanks a ton!!!

---

### Post by tgm4883 on 2009-04-10
> **mtader said:**
> I found what I think you were referring to....  There is a check box in the setup / TV Settings / General, that says "auto expire instead of delete recording".  That was checked, so it creates another group that I never noticed called deleted.  All of my programs were still in there, so the mpg files stayed obviously, and the scripts I ran to clean up the files in the database said "known file" because it was still known to the system in the deleted group.  Simple, stupid, but simple to not see the extra added group since I do not use groups, so I have it set not to prompt for groups.  Never saw it....  Thanks a ton!!!

Yep thats the setting.

---

### Post by mathog on 2009-07-08
> **ian dobson said:**
> Hi,

Try downloading my script from [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt) it does the same as myth.find_orphans.pl and is abit easier to use.


It doesn't run on my 8.10 system.  

./CheckMythDB.pl

```

[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--] Using HostName 'mediahog', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'XXXXXXX'
[--].Checking configuration for host 'mediahog'
[OK].Found 2 video sources
[OK].Videosource (1) 'SchedulesDirect' has a EPG source defined (schedulesdirect1)
[OK].Videosource (7) 'FakeForComposite' has a EPG source defined (/bin/true)
[OK].Found 2 card inputs for Videoinput 1
[OK].Found 3 card inputs for Videoinput 7
[--].Checking start channel for each cardinput
DBD::mysql::st execute failed: Unknown column '4_1' in 'where clause' at ./CheckMythDB.pl line 547.
Couldn't execute statement: Unknown column '4_1' in 'where clause' at ./CheckMythDB.pl line 547.
```

Not quite sure what the problem is.  It would help if the script would run with 

```
use strict;
```

but there were a lot of warnings with that added.

Anyway, line 547 is in SQLQuerySimple and is

```
   $table_data->execute or die "Couldn't execute statement: " . $table_data->errstr;
```

---

### Post by ian dobson on 2009-07-09
Hi,

I know the code isn't strict safe, maybe one day....

Sounds as if the script you download is corrupt, try downloading it again. Other than that column 4_1 is not used anywhere in the program. Maybe your database/perl bindings are screwed up.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-07-09
Hi,

Could you try downloading the latest version of the script and setting the variable $DEBUG to a value greater than 1.

This will produce alot of output, including the last SQL query called before the crash.

I've had a look at the warning with USE strict; and all of them are just caused by the use of global variables, nothing to really worry about and it wouldn't make it any easier to debug the code, global variable are just bad programming style. 

I have a feeling your problem is being caused by one of the following:-

1) You appear to have a dummy tuner "FakeForComposite" with 3 inputs, I'm not sure how the script would react to that.
2) The code appears to die in the start channel table, so this could be caused by bad escaping in the SQL routine. What are the start channels called for each of your tuners?

With the debug info I should be able to findout whats upsetting the script.

regards
Ian Dobson

---

### Post by mathog on 2009-07-09
Downloaded latest and set $DEBUG=2,  It differed only at the end:



```
SELECT sourceid,startchan,cardinputid  from `cardinput` order by cardinputid
SELECT count(*) from channel where channum=7_1  and sourceid=1
DBD::mysql::st execute failed: Unknown column '7_1' in 'where clause' at ./CheckMythDB.pl line 547.
Couldn't execute statement: Unknown column '7_1' in 'where clause' at ./CheckMythDB.pl line 547.
```

This time it blew up on channel 7_1, last time it was 4_1.  Those are both valid channels for the first set of tuners (an HDhomerun).  The fakeforcomposite is for an analog input card, which has Svideo, NTSC tuner and composite inputs.  Only one of these three has an associated real channel, the others are there for making quick captures from a camcorder or similar device.

Thanks.

---

### Post by ian dobson on 2009-07-09
Hi,

OK, I've got it just need to wrap '' around the channum=ChanNumber, mysql doesn't like the exposed _ character.

I'll bang out a new version tonight, I've also fixed up the use strict / -w and fixed afew really obscure bugs.

Uploaded a new copy now.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-07-10
Hi,

OK I've fixed up afew more "unprotected" variable names in SQL queries. I nover thought that channelID could be an alpha numeric, I always thought it was numeric. But anyway the problem is solved now.

Regards
Ian Dobson

---

### Post by mathog on 2009-07-11
> **ian dobson said:**
> Hi,
OK I've fixed up afew more "unprotected" variable names in SQL queries. I nover thought that channelID could be an alpha numeric, I always thought it was numeric. But anyway the problem is solved now.


The new version runs well.  Good work.  Here is the output once it figured out how to connect to the database and did so:

```

[OK].Found 2 video sources
[OK].Videosource (1) 'SchedulesDirect' has a EPG source defined (schedulesdirect1)
[OK].Videosource (7) 'FakeForComposite' has a EPG source defined (/bin/true)
[OK].Found 2 card inputs for Videoinput 1
[OK].Found 3 card inputs for Videoinput 7
[--].Checking start channel for each cardinput
[!!].Cardinput (5) Start channel (100)invalid
[!!].Cardinput (6) Start channel (Please add)invalid
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 68 visible and 0 invisible channels defined
[OK].Videosource 7 has 1 visible and 0 invisible channels defined
[!!].sorry I don't know how to check cardinput 1 type HDHOMERUN device 1011f855
[!!].sorry I don't know how to check cardinput 2 type HDHOMERUN device 1011f855
[!!].sorry I don't know how to check cardinput 4 type V4L device /dev/video0
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].10 dtv_multiplex entries do not have a valid channel
[!!].Channel KXLA-DT has 0 programs in EPG.No EPG data
[!!].Channel VYV-DT has 0 programs in EPG.No EPG data
[!!].Channel KRCA-DT has 0 programs in EPG.No EPG data
[!!].Channel VideoIn has 0 programs in EPG.No EPG data
[!!].Channel KBEH.2  has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 1 storage groups for 'mediahog'
[OK].Storage group 'Default' exists in file system at (/home/mythdbstorage/)
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined
Took 160 SQL queries
```

Most of that looks good.  The channels listed are those which do not come in reliably, so they go in and out of the listings.  Not quite sure what VYV-DT might be though.  

The "LiveTV" stuff is a bit odd.  I can use that as a filter, as opposed to "Default" or "All Programs", should it also be defined as a storage group?

---

### Post by ian dobson on 2009-07-12
Hi,

Try calling the script with the -a option. That'll scan all programs recorded (DB and file system) as well as checking the storage groups.

MythTV requires a storage group "LiveTV" if it doesn't exist the recording will be written to the "default" storage group and my script is complaining because there are recordings in the database that are saved to the LiveTV storage group but the liveTV storage group doesn't exist.

As I don't have a HDHomeRun I'm not sure what to check in th dev fs for cardinput 1/2 same goes for input 4.

VYV-DT is a channel in your channel list.

Also Cardinput (5/6) have an invalid start channel. That's not a major problem if your not using them for LiveTV as it's only used when you start watching live tv from that tuner.

Regards
Ian Dobson

---

