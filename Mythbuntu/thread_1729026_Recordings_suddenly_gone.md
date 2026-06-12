---
title: "Recordings suddenly gone?"
date: 2011-04-14
forum: Mythbuntu
---

### Post by rvindum on 2011-04-14
Been away for some days on holiday and came back to a Myth with a lot of recordings. Recordings can be viewed on the web interface (and deleted).
 
Local MythFrontend and remote states that there are no recordings - even though web sees it, and the files are there.
 
Happended while I was gone.
 
Anyone know how to get around this bug - all my recordings are quite ****** until I can get them to show on the frontends.
 
No patches was applied (I was just away for 2 weeks)
No filters are active when pressing M on the recordings screen.
LiveTV works fine
Seems to record new programs as it should
 
Help is really needed - thanks in advance.

---

### Post by agamotto on 2011-04-14
Go into the main menu, and under System, enter the Backend Setup, saying yes to the prompt.  When you are in the Setup, escape out, run/don't run Mythfilldatabase as you wish, bring the frontend back up, this should solve your problem.  I get this same problem randomly at boot.  There may be other solutions, but this one is the easiest I have found so far.

It has something to do with the backend not starting before some other process, and thus, the frontend loses the connection to the backend... as I understand it.

---

### Post by rvindum on 2011-04-15
In general the system seems to be up - only recordings and recording schedules are missing? The trick with running backend setup and quitting have fixes issues before after a reboot - but this time it doesn't work. :(

---

### Post by ian dobson on 2011-04-15
Hi,

Do you see anything interesting in the backend log file? That's the best place to start. Maybe you have database corruption that's taken out your recorded table.

Regards
Ian Dobson

---

### Post by rvindum on 2011-04-16
Cleared the logs, restarted and checked the logs. Nothing there really? The web frontend shows the recordings though - but not the real frontend.

This is from the frontend app, which runs with the backend directly.

---START ---
Starting mythfrontend.real..
2011-04-16 21:00:24.057 mythfrontend version: branches/release-0-23-fixes [26863] [www.mythtv.org]("http://www.mythtv.org")
2011-04-16 21:00:24.058 Using runtime prefix = /usr
2011-04-16 21:00:24.058 Using configuration directory = /home/mtv/.mythtv
2011-04-16 21:00:24.757 Empty LocalHostName.
2011-04-16 21:00:24.757 Using localhost value of mtv-tsl-001
2011-04-16 21:00:24.764 New DB connection, total: 1
2011-04-16 21:00:24.768 Connected to database 'mythconverg' at host: localhost
2011-04-16 21:00:24.770 Closing DB connection named 'DBManager0'
2011-04-16 21:00:24.781 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-16 21:00:24.782 DPMS is disabled.
2011-04-16 21:00:24.784 Primary screen: 0.
2011-04-16 21:00:24.785 Connected to database 'mythconverg' at host: localhost
2011-04-16 21:00:24.786 Using screen 0, 1024x768 at 0,0
2011-04-16 21:00:24.800 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2011-04-16 21:00:24.801 Desktop video mode: 0x0 0 Hz
2011-04-16 21:00:24.822 MythUI Image Cache size set to 20971520 bytes
2011-04-16 21:00:24.844 Enabled verbose msgs:  important general
2011-04-16 21:00:24.851 Primary screen: 0.
2011-04-16 21:00:24.851 Using screen 0, 1024x768 at 0,0
2011-04-16 21:00:24.852 Using theme base resolution of 1280x720
2011-04-16 21:00:24.856 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-04-16 21:00:24.856 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mtv/.mythtv/joystickmenurc
2011-04-16 21:00:24.891 Using Frameless Window
2011-04-16 21:00:24.891 Using Full Screen Window
2011-04-16 21:00:25.070 Using the Qt painter
2011-04-16 21:00:25.288 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-04-16 21:00:25.298 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-04-16 21:00:25.304 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-04-16 21:00:25.304 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-04-16 21:00:25.327 Current MythTV Schema Version (DBSchemaVer): 1254
2011-04-16 21:00:25.780 Registering Internal as a media playback plugin.
2011-04-16 21:00:25.804 Cannot load language en_us for module mytharchive
2011-04-16 21:00:25.828 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-16 21:00:25.829 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-16 21:00:25.829 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-16 21:00:25.830 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-16 21:00:25.830 Cannot load language en_us for module mythgallery
2011-04-16 21:00:25.832 Cannot load language en_us for module mythmovies
2011-04-16 21:00:25.851 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-16 21:00:25.886 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-16 21:00:25.891 Cannot load language en_us for module mythmusic
2011-04-16 21:00:25.897 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-04-16 21:00:25.921 Cannot load language en_us for module mythvideo
2011-04-16 21:00:25.926 Cannot load language en_us for module mythweather
2011-04-16 21:00:25.928 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-04-16 21:00:26.008 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-04-16 21:00:26.012 Found mainmenu.xml for theme 'Mythbuntu'
2011-04-16 21:00:26.809 MythContext: Connecting to backend server: 172.30.1.5:6543 (try 1 of 1)
2011-04-16 21:00:26.810 Using protocol version 23056
2011-04-16 21:00:28.430 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2011-04-16 21:00:29.293 New DB connection, total: 2
2011-04-16 21:00:29.293 Connected to database 'mythconverg' at host: localhost
2011-04-16 21:00:29.295 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
length mismatch between programinfo
2011-04-16 21:00:29.519 PlaybackBox Error: SortedList is Empty
2011-04-16 21:00:29.635 PlaybackBox Error: SortedList is Empty
2011-04-16 21:00:33.149 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2011-04-16 21:00:34.342 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml
2011-04-16 21:00:34.419 ProgramInfo(): FromStringList, not enough items in list.
2011-04-16 21:00:34.419 LoadFromScheduler(): Length mismatch.
2011-04-16 21:00:36.862 Deleting UPnP client...
--- end ---

There are a few errors of some sort - but nothing that helps me here. :(

Additional note - deleting recordings from the webfrontend is really slow now???

Thanks for any input.....

---

### Post by klc5555 on 2011-04-16
I suppose you've already done the usual thing when the database is having a crash or corruption problem with one of its tables, which is to run 

mysqlcheck --auto-repair mythconverg  

or maybe 

mysqlcheck --auto-repair --all-databases 

on it?

---

### Post by rvindum on 2011-04-17
Hi there.
 
Nope, but did it now - and no luck :(
States ok on all tables and nothing has changed after this....
 
\René

---

### Post by rvindum on 2011-04-17
Seems the following command works:
 
mysql -u root -p -D mythconverg -E --default-character-set=utf8 -e "UPDATE recorded SET subtitle=REPLACE(subtitle, '\0', '');"
 
Found a discussions about this, where the error seemed to come frome the EIT and caused unsupported chars in the database.
 
Just tried it, and it seemed to work - don't know if the error returns after next recording, but time will tell.

---

### Post by klc5555 on 2011-04-17
Well done! It's good to have a fix like this documented in this particular forum.

Though I'm surprised that MySQL allows the login for root --usually the only authorized user in a Mythbuntu installation is "mythtv" 

I suppose that if the symptoms recur after particular events (rebooting, say, or after some recordings) it would seem that a one-line script incorporating this command (but with the -p parameter specified) would be very easy to have the system run wherever appropriate (somewhere under /etc/init.d, or as an hourly cron job or whatever).

---

### Post by rvindum on 2011-04-17
As far as I could find in the danish forum about the bug I had, it was caused by the Electronical Program Guide - and a fix was posted on the Myth patchlist.
 
Old bugs was to be removed by hand though - and not sure this patch was released on the .23 version though.
 
Will upgrade later on - but just glad that my recordings are back.
 
Thanks all for feedback and ideas.

---

### Post by ian dobson on 2011-04-18
> **rvindum said:**
> Seems the following command works:
 
mysql -u root -p -D mythconverg -E --default-character-set=utf8 -e "UPDATE recorded SET subtitle=REPLACE(subtitle, '\0', '');"
 
Found a discussions about this, where the error seemed to come frome the EIT and caused unsupported chars in the database.
 
Just tried it, and it seemed to work - don't know if the error returns after next recording, but time will tell.

Now thats really obscure. I'm supprised that mysql allows null characters to be passed in a field, unless the field is defined as a blob.

But glab to hear you fixed your problem.

Regards
Ian Dobson

---

### Post by rvindum on 2011-04-18
Hi Ian.
 
Yeah I agree. Sad to say, that the error reoccours when I record, so the patch isn't available for the 0,23.1 version. Will try to upgrade til .24 in the easter and see if this makes a difference.
 
Hopefully the fix is included here, as I would hate to run the SQL command after each recording.
 
Regards
René

---

### Post by klc5555 on 2011-04-18
If it turns out that the upgrade is inconvenient or fails to solve the issue on its own, it would seem that you could set the MySQL command up as a myth user job that would run automatically after every recording. Not the most elegant solution, but would keep the issue out of your hair.

---

### Post by BookofJarom on 2013-03-31
I've been fighting this same problem today.  rvindum's suggestion (*UPDATE recorded SET subtitle=REPLACE(subtitle, '\0', '');*) sounded familiar and has worked for me before, but not this time.

Relevant portion of my log file:
  2013-03-31 09:38:05.031 RemoteGetRecordingList() list size appears to be incorrect.
  2013-03-31 09:38:05.078 PlaybackBox Error: SortedList is Empty

_**Short story**_
"*UPDATE recorded SET subtitle=REPLACE(subtitle, '\0', '');*" covers the "subtitle" field of the "recorded" table.  Other fields can have the offending "\0" character.  In my case, it was in the "name" field of the "channel" table.  The query that was needed was
*  UPDATE channel SET name=REPLACE(name,'\0','');*

Perhaps the long story will help someone debug another problem.  So, here it is...

_**Long story**_
To track down the problem, I did the following:
1) Copied the "recorded" MySQL table to a backup copy ("*CREATE TABLE recorded_BACKUP SELECT * FROM recorded;*")
2) Deleted a select few entries in the "recorded" MySQL table using MySQL "*DELETE FROM recorded WHERE ...;*" commands.
3) Re-opened MythTV's "Watch Recordings" screen, checked to see if any recordings appeared, then escaped back out of that screen.
4) Repeated steps 2 and 3 until the "Watch Recordings" screen worked.  (IMPORTANT: You can't just leave the "Watch Recordings" screen open--you have to close it and, after each "*DELETE FROM recorded WHERE ...;*" command, reopen it.)
5) Found the problem was an entry using ChanID 4391.
6) Restored that entry from the backup table ("*INSERT INTO recorded SELECT * FROM recorded_BACKUP WHERE chanid=4391;*").
7) Studied the data in that entry ("*SELECT * FROM recorded WHERE chanid=4391 \G*") to find out what was wrong.  "*UPDATE recorded SET subtitle=REPLACE(subtitle, '\0', '');*" had already been done, and I had even run it on other fields...
   "*UPDATE recorded SET title=REPLACE(title,'\0','');*"
   "*UPDATE recorded SET description=REPLACE(description,'\0','');*"
   etc.
So, I was looking for something new.  I didn't find anything in this step.
8) Somewhere through googling, I found a suggestion to run mysqldump and study the data in the resulting file.  So, I exited out of mysql, then I ran "*mysqldump --extended-insert=FALSE -u[username] -p[password] mythconverg > mythconverg_debug.sql*".
9) Opened Step 8's mythconverg_debug.sql in a text editor.
10) Knowing the offending entry had to do with chanid 4391, I ran a search in that text editor for "4391".

This took me straight to the problem--the very first hit was the following line.
INSERT INTO `channel` VALUES (4391,'39_1','39',4,'KSVN','Azteca\0\0\0\0\0\0\0\0\0\0\0\0\0\0','',NULL,'','',0,32768,32768,32768,32768,'ATSC',1,'',1,8,1,0,39,1,'0000-00-00 00:00:00','',-1);

Note the evil "\0" that occurs 14 times on that line.  A quick "*UPDATE channel SET name=REPLACE(name,'\0','');*" (or simply "*UPDATE channel SET name='Azteca' WHERE chanid=4391;*") fixed the problem.

11) Restored all the entries from Step 1's backup table.
   "*DELETE FROM recorded;*"
   "*INSERT INTO recorded SELECT * FROM recorded_BACKUP;*"
   "*DROP TABLE recorded_BACKUP;*"

Perhaps those steps can help others get through this problem, and perhaps the "mysqldump" idea from Step 8 can help someone diagnose other data problems.  Or, more likely, perhaps this post will come up in a Google search the next time I have this problem and can't remember how in the world I fixed it.  :-)

---

### Post by wildmanne39 on 2013-03-31
Thread closed. Please do not post in old threads.

---

