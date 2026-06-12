---
title: "Mythbuntu 0.25 Upgrade experience"
date: 2012-04-10
forum: Mythbuntu
---

### Post by gleepwurp on 2012-04-10
Hi Folks,

thought it would be interesting if people who have upgraded to Mythtv 0.25 from 0.24 post their experiences here?

Any issues encountered and work around found would be appreciated!

Thanks,

Gleepwurp.

PS: I haven't upgraded yet, was looking for some feedback before I attempted.

---

### Post by suinolat on 2012-04-10
I just registered to say it was completely flawless and painless; I did a double take.  MythBuntu 11.10 running 0.24, followed the instructions in the FAQ.  0 problems.

Thank you, everyone who works and has worked on MythTV.  Excellent work!

---

### Post by ransae on 2012-04-12
No problems with install. Working with a couple of glitches. Mythweb ok.


[LIST=1]
[*]Sometimes live TV freezes when the program changes. Work around is to stop and start live TV.
[*]My EPG program has problems with the --graboptions in mythfilldatabase. Have altered the cron job command and will see what happens.
[*]Frontend can't write to /var/log/mythtv/jamu.log
[/LIST]
Expect these bugs will get sorted in fixes.


Impressed.

---

### Post by utar on 2012-04-12
Re point 3 the frontend shouldn't be writing to jamu.log as jamu as been removed. In any case the frontend never did write to the jamu log, it was the jamu script which did the writing.

---

### Post by JamesNorris on 2012-04-12
My only issue was that I needed to redefine storage groups in the backend before I could play any of my recordings. Easy to fix and no other issues here.

---

### Post by Paulgirardin on 2012-04-13
I attempted the update
The update manager  told me it would attempt a partial upgrade.
First attempt the update manager closed immediately, so I used the terminal commands and the update manager down loaded the new packages but hung up on the "preparing changes" section.After an hour I closed the update manager - there was a lot of HDD activity - and I restarted mythfrontend,It still showed version 0.24.
I shut down and restarted - still shows  V 0.24
Started update manager and checked for updates - it says the system is up to
date. Still shows V 0.24

System works ok but I don't know if it updated or not.

Edit: I changed the download location from the local server to the main server and the upgrade completed successfully.No problems evident.
Edit: myth backend won't start on boot up.I have to start it manually.
Apparently no one knows how to fix this one.

---

### Post by rafe101 on 2012-05-02
I have a problem with themes. 

I have tried all the different themes and the program guide acts weird in all of them. I'm now just using the Mythbuntu theme because I thought it would be the most developed. About a third of the times, when I bring up the EPG there is no program information, channel icons or descriptions and if I try to move from one program "cell" to another, the whole screen goes blank except for the little preview window. 

It's also imposible for me to manually edit video metadata as the text and boxes in that window are totally jumbled about.

---

### Post by kcox5342 on 2012-05-03
I did a fresh wipe and install with few issues.  My keyboard doesn't have volume controls and there's no "sound" preferences anywhere that I could see so turning up the volume in XFCE took a little Googling.  (Now it does, F11 and F12.)

After 24 hours, it seems to be running smoothly.  My main complaint is that the Western Digital Live device I play most of my TV on usually doesn't show the device in its list of media servers unless I reboot it, whereas it never had a problem finding the 11.10 version.  My other DLNA players have not developed this issue, though.

---

### Post by scragglykat on 2012-05-04
I upgraded from 10.10 all the way up to 12.04 one weekend. Everything was smooth on each upgrade. Everything seemed to work properly and I had no issues. Then on 12.04, after a day of using the system, I added another tuner device, and when I went to run mythfilldatabase, it pulled the listings from SchedulesDirect and uncompressed them, then sat for over a half an hour just thrashing the harddrive. It was right after telling me about the subscription expiration date, and then showing the source1 message, which was where it sat, and which was the last item added to the mythfilldatabase log.

I finally killed the process and tried it again, and it did the same thing, so I removed the new tuner from the backend setup, and tried it again and it still did it. At this point I thought I'd screwed something up, so I did some searching online and couldn't find much about it, so I decided to reinstall at 11.10 and test it. Thankfully I made a backup of the database and content files at each upgrade. 11.10 worked fine, so I installed 12.04 on a brand new system, adding a tuner without importing any data or anything, and tried mythfilldatabase and it ran for about 45 minutes, then finally moved on to the part where it says it's marking old shows, new shows, etc., then said it was completed successfully.

So... it appears something that installs with Mythbuntu 12.04, out of the box, isn't working as it should, or is doing more than it should. Since it does work, and the database is usually filled in the night, my only concern is that about an hour of HD thrashing each night is going to wear out my drive pretty quick, and with the price of drives now, I don't want that happening.

Has anyone else run into this issue? I can reproduce it on three separate machines so I know it's not just an issue with my hardware.

---

### Post by Patrick27 on 2012-05-04
> **scragglykat said:**
> Has anyone else run into this issue? I can reproduce it on three separate machines so I know it's not just an issue with my hardware.

I run into this issue, and a similar symptom is happening on my backend and frontends as well.  The disk thrashes for a good long while on occasion.

I registered just to reply to this - it's not currently passing the wife test... :-(

---

### Post by tgm4883 on 2012-05-04
> **scragglykat said:**
> I upgraded from 10.10 all the way up to 12.04 one weekend. Everything was smooth on each upgrade. Everything seemed to work properly and I had no issues. Then on 12.04, after a day of using the system, I added another tuner device, and when I went to run mythfilldatabase, it pulled the listings from SchedulesDirect and uncompressed them, then sat for over a half an hour just thrashing the harddrive. It was right after telling me about the subscription expiration date, and then showing the source1 message, which was where it sat, and which was the last item added to the mythfilldatabase log.

I finally killed the process and tried it again, and it did the same thing, so I removed the new tuner from the backend setup, and tried it again and it still did it. At this point I thought I'd screwed something up, so I did some searching online and couldn't find much about it, so I decided to reinstall at 11.10 and test it. Thankfully I made a backup of the database and content files at each upgrade. 11.10 worked fine, so I installed 12.04 on a brand new system, adding a tuner without importing any data or anything, and tried mythfilldatabase and it ran for about 45 minutes, then finally moved on to the part where it says it's marking old shows, new shows, etc., then said it was completed successfully.

So... it appears something that installs with Mythbuntu 12.04, out of the box, isn't working as it should, or is doing more than it should. Since it does work, and the database is usually filled in the night, my only concern is that about an hour of HD thrashing each night is going to wear out my drive pretty quick, and with the price of drives now, I don't want that happening.

Has anyone else run into this issue? I can reproduce it on three separate machines so I know it's not just an issue with my hardware.

When you tested on 11.10, were you using the MythTV 0.24 packages or the MythTV 0.25 packages? Also, can you verify what options mythfilldatabase is running with?

---

### Post by tunzo on 2012-05-05
I am running into this same problem with mythfilldatabase, though this is from a fresh install and not an upgrade. After completing the backend setup last night, I was prompted to run mythfilldatabase.  It ran from about 9 pm last night until about noon today, and was still going.  I have a section of my mythfilldatabase.log below:

May  5 02:12:32 media mythfilldatabase[2909]: I CoreContext filldata.cpp:272 (GrabDDData) Grab complete.  Actual data from Mon May 7 04:00:00 2012 to Tue May 8 04:00:00 2012 (UTC)
May  5 02:12:32 media mythfilldatabase[2909]: I CoreContext filldata.cpp:276 (GrabDDData) Main temp tables populated.
May  5 02:12:34 media mythfilldatabase[2909]: I CoreContext filldata.cpp:309 (GrabDDData) Clearing data for source.
May  5 02:12:34 media mythfilldatabase[2909]: I CoreContext filldata.cpp:315 (GrabDDData) Clearing from Mon May 7 00:00:00 2012 to Tue May 8 00:00:00 2012 (localtime)
May  5 02:12:42 media mythfilldatabase[2909]: I CoreContext filldata.cpp:317 (GrabDDData) Data for source cleared.
May  5 02:12:42 media mythfilldatabase[2909]: I CoreContext filldata.cpp:319 (GrabDDData) Updating programs.
May  5 02:12:50 media mythfilldatabase[2909]: I CoreContext filldata.cpp:321 (GrabDDData) Program table update complete.
May  5 02:12:50 media mythfilldatabase[2909]: I CoreContext filldata.cpp:764 (Run) Checking day @ offset 3, date: Tue May 8 2012
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext filldata.cpp:858 (Run) Data refresh needed because only 0 out of 959 channels have at least one program listed for day @ offset 3 from 8PM - midnight.  Previous day had 946 channels with data in that time period.
May  5 02:12:51 media mythfilldatabase[2909]: N CoreContext filldata.cpp:922 (Run) Refreshing data for Tue May 8 2012
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext filldata.cpp:231 (GrabDDData) Retrieving datadirect data.
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext filldata.cpp:248 (GrabDDData) Grabbing data for Sat May 5 2012 offset 3
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext filldata.cpp:251 (GrabDDData) From Tue May 8 04:00:00 2012 to Wed May 9 04:00:00 2012 (UTC)
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1157 (GrabData) DataDirect: Grabbing listing data
May  5 02:12:51 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1020 (DDPost) Downloading DataDirect feed
May  5 02:13:27 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1032 (DDPost) Downloaded 903825 bytes
May  5 02:13:27 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1034 (DDPost) Uncompressing DataDirect feed
May  5 02:13:27 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1039 (DDPost) Uncompressed to 8140517 bytes
May  5 02:13:28 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:468 (characters) DataDirect: Your subscription expires on Sat May 4 (2013) 12:41 PM
May  5 03:17:56 media mythfilldatabase[2909]: I CoreContext filldata.cpp:272 (GrabDDData) Grab complete.  Actual data from Tue May 8 04:00:00 2012 to Wed May 9 04:00:00 2012 (UTC)
May  5 03:17:56 media mythfilldatabase[2909]: I CoreContext filldata.cpp:276 (GrabDDData) Main temp tables populated.
May  5 03:17:57 media mythfilldatabase[2909]: I CoreContext filldata.cpp:309 (GrabDDData) Clearing data for source.
May  5 03:17:57 media mythfilldatabase[2909]: I CoreContext filldata.cpp:315 (GrabDDData) Clearing from Tue May 8 00:00:00 2012 to Wed May 9 00:00:00 2012 (localtime)
May  5 03:18:05 media mythfilldatabase[2909]: I CoreContext filldata.cpp:317 (GrabDDData) Data for source cleared.
May  5 03:18:05 media mythfilldatabase[2909]: I CoreContext filldata.cpp:319 (GrabDDData) Updating programs.
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:321 (GrabDDData) Program table update complete.
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:764 (Run) Checking day @ offset 4, date: Wed May 9 2012
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:858 (Run) Data refresh needed because only 0 out of 959 channels have at least one program listed for day @ offset 4 from 8PM - midnight.  Previous day had 947 channels with data in that time period.
May  5 03:18:14 media mythfilldatabase[2909]: N CoreContext filldata.cpp:922 (Run) Refreshing data for Wed May 9 2012
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:231 (GrabDDData) Retrieving datadirect data.
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:248 (GrabDDData) Grabbing data for Sat May 5 2012 offset 4
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext filldata.cpp:251 (GrabDDData) From Wed May 9 04:00:00 2012 to Thu May 10 04:00:00 2012 (UTC)
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1157 (GrabData) DataDirect: Grabbing listing data
May  5 03:18:14 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1020 (DDPost) Downloading DataDirect feed
May  5 03:18:55 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1032 (DDPost) Downloaded 903506 bytes
May  5 03:18:55 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1034 (DDPost) Uncompressing DataDirect feed
May  5 03:18:55 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1039 (DDPost) Uncompressed to 8121333 bytes
May  5 03:18:55 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:468 (characters) DataDirect: Your subscription expires on Sat May 4 (2013) 12:41 PM
May  5 04:23:17 media mythfilldatabase[2909]: I CoreContext filldata.cpp:272 (GrabDDData) Grab complete.  Actual data from Wed May 9 04:00:00 2012 to Thu May 10 04:00:00 2012 (UTC)
May  5 04:23:17 media mythfilldatabase[2909]: I CoreContext filldata.cpp:276 (GrabDDData) Main temp tables populated.
May  5 04:23:19 media mythfilldatabase[2909]: I CoreContext filldata.cpp:309 (GrabDDData) Clearing data for source.
May  5 04:23:19 media mythfilldatabase[2909]: I CoreContext filldata.cpp:315 (GrabDDData) Clearing from Wed May 9 00:00:00 2012 to Thu May 10 00:00:00 2012 (localtime)
May  5 04:23:27 media mythfilldatabase[2909]: I CoreContext filldata.cpp:317 (GrabDDData) Data for source cleared.
May  5 04:23:27 media mythfilldatabase[2909]: I CoreContext filldata.cpp:319 (GrabDDData) Updating programs.
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:321 (GrabDDData) Program table update complete.
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:764 (Run) Checking day @ offset 5, date: Thu May 10 2012
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:858 (Run) Data refresh needed because only 0 out of 959 channels have at least one program listed for day @ offset 5 from 8PM - midnight.  Previous day had 946 channels with data in that time period.
May  5 04:23:37 media mythfilldatabase[2909]: N CoreContext filldata.cpp:922 (Run) Refreshing data for Thu May 10 2012
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:231 (GrabDDData) Retrieving datadirect data.
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:248 (GrabDDData) Grabbing data for Sat May 5 2012 offset 5
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext filldata.cpp:251 (GrabDDData) From Thu May 10 04:00:00 2012 to Fri May 11 04:00:00 2012 (UTC)
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1157 (GrabData) DataDirect: Grabbing listing data
May  5 04:23:37 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1020 (DDPost) Downloading DataDirect feed
May  5 04:24:22 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1032 (DDPost) Downloaded 902338 bytes
May  5 04:24:22 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1034 (DDPost) Uncompressing DataDirect feed
May  5 04:24:23 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:1039 (DDPost) Uncompressed to 8147707 bytes
May  5 04:24:23 media mythfilldatabase[2909]: I CoreContext datadirect.cpp:468 (characters) DataDirect: Your subscription expires on Sat May 4 (2013) 12:41 PM


Like the other person mentioned a there is a log time between the subscription expiration notice and "Grab Complete".  For me it is a little over an hour.

As far as options being added to mythfilldatabase, I am assuming none.  At least, there were none listed in the backend setup screen for this process.

Thanks!

---

### Post by tgm4883 on 2012-05-05
There was another issue with 0.25 that prevented getting data from schedules direct, although it shouldn't have affected any Ubuntu based builds. Does anyone having the issue have any non alphanumeric characters in their schedules direct user name?

---

### Post by scragglykat on 2012-05-06
> **tgm4883 said:**
> When you tested on 11.10, were you using the MythTV 0.24 packages or the MythTV 0.25 packages? Also, can you verify what options mythfilldatabase is running with?

11.10 was stock with 0.24. Im currently running 11.10 from a fresh mythbuntu install with my db from the upgraded system imported. I dont bother with the myth repo upgrades as i would prefer stability over cutting edge.

As for 12.04/0.25, that was a stock upgrade but the issue persisted with a fresh install of it as well using no previous data. Mythfilldatabase ran with no options, just typed mythfilldatabase and hit enter.

---

### Post by scragglykat on 2012-05-06
> **tgm4883 said:**
> There was another issue with 0.25 that prevented getting data from schedules direct, although it shouldn't have affected any Ubuntu based builds. Does anyone having the issue have any non alphanumeric characters in their schedules direct user name?

Just letters for me. Lower case.

---

### Post by scragglykat on 2012-05-06
> **Patrick27 said:**
> I run into this issue, and a similar symptom is happening on my backend and frontends as well.  The disk thrashes for a good long while on occasion.

I registered just to reply to this - it's not currently passing the wife test... :-(

Funny you should say that. I was up late going back to 11.10 to avoid the dreaded cranky wife when Mad Men didnt tape on time :-)

---

### Post by nopdotcom on 2012-05-06
See [http://ubuntuforums.org/showthread.php?t=1974335](http://ubuntuforums.org/showthread.php?t=1974335); short version:

Could you make /tmp into tmpfs and try adding ```
default_storage_engine=MyISAM
``` to /etc/mysql/conf.d/mythtv-tweaks.cnf and restarting mysqld?

---

### Post by scragglykat on 2012-05-06
This person may be onto something. I had looked briefly into the issue being caused by the move to mysql 5.5 in 12.04 and this post seems to confirm that something changed in mysql that is causing much more drive usage during db fills. I may have to compare both setups to see what changed. I did read that previously it did use temp tables in memory and not on the physical drive so that could be it. Not sure why that would have changed as that is a major performance hit. That does seem to be the issue though as top reports the mysql as the top process during the fill and the drive just gets hammered. Im wondering if this was done for a reason or if the package maintainer just forgot something in the config.

[http://ubuntuforums.org/showthread.php?t=1974335&highlight=mythfilldatabase]("http://ubuntuforums.org/showthread.php?t=1974335&highlight=mythfilldatabase")

---

### Post by scragglykat on 2012-05-06
Speak of the devil...:-)

My only question is why did that change? Using the physical drive for temp tables seems like a bad idea unless there was some reason not to use memory for temp tables.

---

### Post by nopdotcom on 2012-05-06
> **scragglykat said:**
> Speak of the devil...:-)I'm in the details, you know.
> **scragglykat said:**
> My only question is why did that change? Using the physical drive for temp tables seems like a bad idea unless there was some reason not to use memory for temp tables.
I don't think this was intended. 5.5 switched to InnoDB as default ([http://dev.mysql.com/doc/refman/5.5/en/innodb-default-se.html](http://dev.mysql.com/doc/refman/5.5/en/innodb-default-se.html)) but the default InnoDB setting is to use a single table space, which sounds to me like the [FONT="monospace"]tmpdir[/FONT] setting couldn't be used. Perhaps [FONT="monospace"]innodb_file_per_table[/FONT] should have been switched on by default at the same time, since it seems to be recommended for 5.5 InnoDB. It sounds like having it off only made sense if you were using InnoDB in 5.1.

It's possible mysql settings may explain why old users are not experiencing this problem to the same degree--there seems to be a lot of disconnect on how bad it is. I wanted to migrate to 64-bit, so I did a mythtv backup, a fresh 12.04-beta2 install, and a restore. This guaranteed I got a out-of-the-box mysql config. Perhaps if I had just upgraded in place I wouldn't have seen this.

I have avoided relational databases, so my suggestions and theories may be way off.

---

### Post by tgm4883 on 2012-05-06
> **scragglykat said:**
> 11.10 was stock with 0.24. Im currently running 11.10 from a fresh mythbuntu install with my db from the upgraded system imported. I dont bother with the myth repo upgrades as i would prefer stability over cutting edge.

As for 12.04/0.25, that was a stock upgrade but the issue persisted with a fresh install of it as well using no previous data. Mythfilldatabase ran with no options, just typed mythfilldatabase and hit enter.

You really need to read up on what the Mythbuntu repos offer. Sure one of the options is the development version of MythTV, but the other offerings are builds from the fixes branch. After a release, the MythTV team will fix things in the 0.25 branch and push those changes to the fixes branch. Eventually this leads to a 0.25.1 release (Which is nothing more than a snapshot in time from the 0.25 fixes branch). The Mythbuntu repos just builds a new version every day that they make a fix. Further, the MythTV version in the official Ubuntu repos is nothing more than one of the builds we pushed to the Mythbuntu repos.

---

### Post by nopdotcom on 2012-05-06
> **tgm4883 said:**
> After a release, the MythTV team will fix things in the 0.25 branch and push those changes to the fixes branch.
Having lots of versions your users all call "0.25" must make support fun. I'm having this sense of deja vu... debian-user 1996-04 archive: [http://lists.debian.org/debian-user/1996/04/msg00891.html](http://lists.debian.org/debian-user/1996/04/msg00891.html)
> **tgm4883 said:**
> Eventually this leads to a 0.25.1 release (Which is nothing more than a snapshot in time from the 0.25 fixes branch).
Yes, but it's not like that rev was chosen at random. Besides whatever stability there is in 0.25.1 by curation, it's the next significant upgrade lots of other people will install. MythTV upgrades feel scary, even the conservative stuff that goes in -fixes. I want to have the same problems as other people. I want web searches to find "this is a known problem", "it's fixed in r12345", and "it's fixed in mythbuntu package version 20120525-r12345 onward; if you need the fix more than you need stability, get a version after that or add the fixes repository."

I spent several years maintaining my own forked mythbuntu (HD-PVR was the point of no return) and I'd rather not do that again right away. 

I'm probably going to fork again eventually (is anybody ever happy with UPnP?) and at that point rejoining -fixes can get really heavyweight. But that's my problem.

---

### Post by tgm4883 on 2012-05-06
> **nopdotcom said:**
> Having lots of versions your users all call "0.25" must make support fun. I'm having this sense of deja vu... debian-user 1996-04 archive: [http://lists.debian.org/debian-user/1996/04/msg00891.html](http://lists.debian.org/debian-user/1996/04/msg00891.html)


Hmm, must be a good thing that we put the revision and build date in the version then huh.

> **nopdotcom said:**
> 
Yes, but it's not like that rev was chosen at random. Besides whatever stability there is in 0.25.1 by curation, it's the next significant upgrade lots of other people will install. MythTV upgrades feel scary, even the conservative stuff that goes in -fixes. I want to have the same problems as other people. I want web searches to find "this is a known problem", "it's fixed in r12345", and "it's fixed in mythbuntu package version 20120525-r12345 onward; if you need the fix more than you need stability, get a version after that or add the fixes repository."

<snip>

You are right, it wasn't chosen at random. It was chosen because it was the last build we could comfortably put in before Final Freeze. You'll notice that the build in 12.04

```
2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
```

was build a few days before Final Freeze (which is where we can't put any more new builds in).

> 
April 12th
Quality
NonLanguagePackTranslationDeadline (Tue), 
**FinalFreeze**, 
LanguagePackTestRebuild (Fri)

As for 0.25.1 (if there is a 0.25.1), we won't be making a special build of the released version of that. We'll make a build of the 0.25 branch for that day, just like we do every day. We'll increment the number to 0.25.1+fixes.... and keep building.

---

### Post by nopdotcom on 2012-05-07
The thread title is "Mythbuntu 0.25 experience", not 12.04-release. Users still seem to be using the terms interchangeably.

> **tgm4883 said:**
> [QUOTE=nopdotcom;11912739]Having lots of versions your users all call "0.25" must make support fun.Hmm, must be a good thing that we put the revision and build date in the version then huh.[/QUOTE]

It doesn't seem to be doing you any good right now. Let's go back and look at how people are referring to versions:

> **gleepwurp said:**
> upgraded to Mythtv 0.25 from 0.24 post their experiences
> **suinolat said:**
> MythBuntu 11.10 running 0.24, followed the instructions in the FAQ
3 messages about 0.25; unclear which Ubuntu.
> **Paulgirardin said:**
> I attempted the update. The update manager **(assuming this means the Ubuntu 11.10->12.04 update manager)** told me it would attempt a partial upgrade. … restarted mythfrontend, it still showed version 0.24
> **scragglykat said:**
> I upgraded from 10.10 all the way up to 12.04 one weekend. Everything was smooth on each upgrade. Everything seemed to work properly and I had no issues. Then on 12.04…mythfilldatabase…sat for over a half an hour just thrashing the harddrive.
This **is** probably a Mythbuntu bug report, on version 12.04--some interaction of mythtv.deb and mysql.deb versions really does look like the problem. (This is why I'm here rather than mythtv-users.)
> **scragglykat said:**
> reinstall at 11.10 … 11.10 worked fine, so I installed 12.04 … it appears something that installs with Mythbuntu 12.04, out of the box, isn't working as it should
Here's you, correctly pointing out that 11.10 does not imply 0.24:
> **tgm4883 said:**
> When you tested on 11.10, were you using the MythTV 0.24 packages or the MythTV 0.25 packages?

I understand in excruciating detail why Debian (and Ubuntu) do not and should not version in lockstep with upstream. But Mythbuntu may want to give non-opaque numbers to -fixes releases, visible in the UI--and then train users to be specific what they're reporting against. I know what "2:0.25.0+fixes.20120410.1f5962a-0ubuntu1" means, but it's the first time it came up in the discussion. It would be a lot easier to talk about something like 0.25u01 as an alias. The first fixes release would be called 0.25u02. Nobody is going to tell somebody at lunch "when I upgraded to 2:0.25.0+fixes.20120412.1badca5e-0ubuntu1 my CableCard started working". Everybody is going to call it "latest 0.25", or at best 0.25-fixes. The best you'll get is a date, and the date will be the day they hit apt-get update, not necessarily the package date.

Continuous build/ship scares me; sid is a scary kid. Somebody who doesn't have eight years of data can install before me. You don't have to do anything special for me to pin or hold or whatever my packages. I just think you'll get better feedback and less confused users if you name significant releases in a way they can see and speak compactly.

Regardless of my silly attempt to impose my naming and release system on your project, there is still a problem: a bunch of people are seeing giant performance regressions with some kinds of DataDirect feeds. This seems to be a Mythbuntu 12.04 problem.

---

### Post by tgm4883 on 2012-05-07
> **nopdotcom said:**
> <snip>

Regardless of my silly attempt to impose my naming and release system on your project, there is still a problem: a bunch of people are seeing giant performance regressions with some kinds of DataDirect feeds. This seems to be a Mythbuntu 12.04 problem.

Getting proper logs usually shows the full version number. Getting logs with the Mythbuntu log grabber will get the version number (as well as some other important logs). 

Unfortunately, people don't usually post their full logs when opening a thread, so it does require some digging. Some digging is going to be required if we release 1 build per Ubuntu release or 1000 builds.

Anyway, you had originally stated that you didn't want to use the Mythbuntu repos because you wanted stability over cutting edge. I responded to correct that statement. I'm not entirely sure why you feel the need to keep arguing about the version numbers.

Back on topic, to troubleshoot previous mythfilldatabase issues, upstream has wanted 

> mythfilldatabase run with -v file,network --loglevel
debug, AND a pcap file of it failing.

The pcap probably isn't necessary for this issue, but I'd say lets gather it in case this needs to go upstream.

---

### Post by tunzo on 2012-05-07
Hi guys.  After reading the discussion about which version is in place, etc, I will clarify my info as much as I can:
 
My fresh install is from the iso downloaded from the mythbuntu web site 5/1/12.  (so my understanding is that this is Ubuntu 12.04 + MythTV 0.25), 64 bit.  
 
Additionally, the very first line of my mythfilldatabase.log file says:
 
[FONT=Courier New][SIZE=2]May  4 21:13:30 media mythfilldatabase[2471]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfilldatabase version: fixes/0.25 [v0.25] [www.mythtv.org]("http://www.mythtv.org")[/SIZE][/FONT]

I was looking through the log just now, and my last run of mythfilldatabase occured a little bit before 2:30 am last night and finished around 7:30 am.  It appears that it took roughly 20-30 minutes to finish each day's worth of data.  
 
If you like, I can post that section of my log.  I am not super advanced, but if there is any other information that you would like me to get, please let me know and I would be happy to try to accomodate.
 
Thanks

---

### Post by nopdotcom on 2012-05-07
> **tgm4883 said:**
> Back on topic, to troubleshoot previous mythfilldatabase issues, upstream has wanted> mythfilldatabase run with -v file,network --loglevel
debug, AND a pcap file of it failing.
The pcap probably isn't necessary for this issue, but I'd say lets gather it in case this needs to go upstream.
Sure; I now have a really boring pair of packet captures...

I decided to log database as well, since the interesting thing is how much faster MyISAM is than InnoDB--all that's changed between the two runs is the default storage engine. The InnoDB run will be going for about another hour I think; here's a snapshot of MyISAM vs InnoDB:
```
nop@mythtv:/tmp/mfdblog$ head -2 mythfilldatabase.20120507114153.27610.log
2012-05-07 11:41:53.551208 C [27610/27610] thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) - mythfilldatabase version: fixes/0.25 [v0.25] www.mythtv.org
2012-05-07 11:41:53.551226 N [27610/27610] thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) - Enabled verbose msgs:  general file network database
nop@mythtv:/tmp/mfdblog$ tail -2 mythfilldatabase.20120507114153.27610.log
2012-05-07 11:47:45.781819 I [27610/27610] CoreContext datadirect.cpp:573 (~DataDirectProcessor) - DataDirect: Deleting temporary files
2012-05-07 11:47:45.785840 D [27610/27610] CoreContext mythhttppool.cpp:94 (RemoveListener) - MythHttpPool: RemoveListener(0x7fffe01ed9d0)
nop@mythtv:/tmp/mfdblog$ head -2 mythfilldatabase.20120507115634.28267.log
2012-05-07 11:56:34.991773 C [28267/28267] thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) - mythfilldatabase version: fixes/0.25 [v0.25] www.mythtv.org
2012-05-07 11:56:34.991790 N [28267/28267] thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) - Enabled verbose msgs:  general file network database
nop@mythtv:/tmp/mfdblog$ tail -2 mythfilldatabase.20120507115634.28267.log
2012-05-07 12:34:32.533679 D [28267/28267] CoreContext mythdbcon.cpp:675 (exec) - MSqlQuery::exec(DataDirectCon) INSERT INTO dd_program      ( programid,    title,       subtitle,              description,  showtype,    category_type,         mpaarating,   starrating,  stars,                 runtime,      year,        seriesid,              colorcode,    syndicatedepisodenumber, originalairdate) VALUES      ('EP015048820003',   'Hotel Impossible',      'The Penguin Hotel, South Beach, Fl.',             'Anthony travels to South Beach to save a family-run boutique hotel.', 'Series',   'series',              '',  '', '0',                '',     '',       'EP01504882',             '',   '102',    '2012-04-16')    
2012-05-07 12:34:32.569703 D [28267/28267] CoreContext mythdbcon.cpp:675 (exec) - MSqlQuery::exec(DataDirectCon) INSERT INTO dd_program      ( programid,    title,       subtitle,              description,  showtype,    category_type,         mpaarating,   starrating,  stars,                 runtime,      year,        seriesid,              colorcode,    syndicatedepisodenumber, originalairdate) VALUES      ('EP015048820005',   'Hotel Impossible',      'The Ocean Manor Resort: Fort Lauderdale Fl',             'The Ocean Manor is full of potential with its beachfront bar and sushi restaurant, but dirty rooms are ruining the hotel's chances.', 'Series',   'series',              '',  '', '0',                '',     '',       'EP01504882',             '',   '104',    '2012-05-07')    

```
You will note the first run took six minutes, and the second is chugging away 40 minutes later, with the disk light on. I'll upload the complete logs when they finish.

I'm wondering if another approach is to have DataDirectProcessor::GrabData() begin a transaction() before the XML parse into tables, and commit() after. It's not that we care about the consistency of the temp tables, but autocommit defaults to on, turning each request into a transaction. That sounds like a forced disk barrier for each. The MySQL docs suggest the InnoDB log only needs a barrier at the end of a transaction.

---

### Post by nopdotcom on 2012-05-07
I was wrong; it only took 70 minutes for the InnoDB run. Full logs and summarized captures at [http://place.org/~nop/m/mfdblog-2012-05-07.tar.xz](http://place.org/~nop/m/mfdblog-2012-05-07.tar.xz). Tar file is 6M, uncompressed 150M.

I'd like to blow away the tarball in the near future; it shouldn't be of much use to anybody who doesn't like to debug database performance issues.

---

### Post by JKMB111 on 2012-05-08
I did a fresh 64-bit install Friday 20120504 with an ISO downloaded from mythbuntu.org also from Friday 20120504.  I too ran into a problem with mythfilldatabase where the fill took 6 hours of HDD churn to complete.  I made a change, and again waited out 6 additional hours of what sounded like pain and discomfort for the HDD.

A brief search for knowledge seemed to center around ext4 defaults set to barriers on.  

Since this current release of Mythbuntu is straight LTS, and after years of wading through  MythTV/Mythbuntu upgrades, I decided to wait it out until more knowledge and available time presents itself or one of the kind distribution/package maintainers sweats the dirty work for us all.

I dusted off my backend, from its dark and hidden place, and retooled it only very recently.  I have only been on 11.10 for a couple of weeks.    All of that previous hardware was at least 10 years old, minus storage, and the last time I touched the box seems to be 3 years ago over the schedules direct migration.  The amount of dust in that forgotten and unappreciated box was horrendous.  

It is funny what we take for granted.

If the issue is ext4 barriers, I am interested in the final chosen direction.  I am thinking 3 paths:  
1) barrier=0
2) separate partition for the database
3) rewrite the extraction translation to have all of the needed data physically on the platter before the final load.

Anyway, thanks to everyone for the years of function and enjoyment the community and dedicated individuals have provided.   And thanks for making me track down what on earth my old UbuntuForums username and password was...

---

### Post by nickrout on 2012-05-08
Version information is easy to get from dpkg.

```
nick@media:~$ dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-backend                    2:0.24.2+fixes.20120316.322de47-0 A personal video recorder application (s[erver)

```

dpkg truncates if the window is too narrow, make your xterm full screen before you run it. There is a commandline option to make sure it doesn't truncate anything but I can't recall the details. All your key mythtv packages will be the same version number.

Alternatively each of the main binaries has a --version switch, so:

```
nick@media:~$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version   : v0.24.2-27-g322de47
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.6.2
Options compiled in:
 linux profile using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_crystalhd using_directfb using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

```


That can be run while the backend is running without interfering with its operation.

Note the git version 322de47 is included in the dpkg output and the --version output.

---

### Post by nopdotcom on 2012-05-08
> **JKMB111 said:**
> If the issue is ext4 barriers, I am interested in the final chosen direction.  I am thinking 3 paths:  
1) barrier=0
2) separate partition for the database
3) rewrite the extraction translation to have all of the needed data physically on the platter before the final load.
My database is on ext4 and I consider its performance acceptable. I see a decimal order of magnitude difference depending on how **temporary** tables are handled. Temporary tables do not outlive a single database connection, so if the power is lost during their creation, you won't care. ETA: ...as long as the database structure itself remains consistent.

datadirect.cpp does the right thing: it loads all its data into temps, and then asks mysql to merge the temps into the main database. The merge operation does have to be ACID, and does need a write barrier.

The problem is that in a default 12.04 install it looks like we're taking a disk write barrier per **row** of data inserted into the **temporary** tables, which is just a flat-out bug if true. Then the only question is how to fix it. I have a MySQL config change which fixes it by getting the temp tables back onto a tmpfs /tmp, where fsync is a little cheaper. :-) But looking at the datadirect.cpp code, it looks like there are a few things it could be doing to either encourage temps to go in mysql's [FONT="monospace"]tmpdir[/FONT] directory, or not implicitly require fsync so much during temporary creation, or both.

I find the behavior of mysql 5.5 to be unintuitive, but I don't know enough about dbs to claim the behavior itself is a bug.

---

### Post by Daminator on 2012-05-08
My upgrade didn't go too well,

Most of the update seemed to go without a hitch, except for upgrading the mythtv.cnf file. I got a message asking me if I wanted to keep the current file or accept the changes. I've been stung by this sort of thing before, so I cut and pasted the differences. Here's what was displayed during the install:

--- /etc/mysql/conf.d/mythtv.cnf 2012-04-18 20:27:49.000000000 +0100
+++ /etc/mysql/conf.d/mythtv.cnf.dpkg-new 2012-05-03 00:07:41.000000000 +0100
@@ -1,2 +1,3 @@
[mysqld]
-bind-address=0.0.0.0
+#bind-address=0.0.0.0
+max_connections=100

I believe I told it to keep the current file. Here's the contents of my mythtv.cnf file as it is today:

[mysqld]
bind-address=0.0.0.0
max_connections=100

The install then continued as normal and finished. Now the fun begins

I tried to run the frontend (on the same system) and a little message at the bottom of the screen (gnome) kept popping up saying that the frontend was restarting. This popped up every few seconds, so it was in some sort of loop.

I rebooted and still had the same problem.

If I try to go to the backand setup, I get asked if I would like to start the mythtv backend, which implys that the back end isn't even running any more. I click on 'yes' and am then asked if I would like to run mythfilldatabase. I click 'yes' again. At no point am I taken into the backend setup screens.

If I try to go into the backend setup again, I get asked if I want to run mythtv backend again etc etc.

I've just had a look at /var/log/mythtv/mythbackend.log and it doesn't seem to have had an entry since 3rd May. The /var/log/mythtv/mythfrontend.log file hasn't had an entry since the 2nd May.

Where can I look for some information that could help to fix this?
Damian

---

### Post by kpl388 on 2012-05-08
I am having similar issues to those reported by other users that are simultaneously upgrading to Ubuntu 12.04 and Mythtv 0.25. Mythfilldatabase is now taking hours (of intense hard drive activity) to complete.

In addition, though maybe unrelated (?), I am now getting occasional failed recordings (so far only on my HVR-1600 QAM tuner) and experiencing backend crashes after multiple channel changes on my firewire-connected dch-3200 cable box. 

Any insight into fixing any of these problems would be much appreciated.

Thanks!

---

### Post by kpl388 on 2012-05-08
Forgot to mention: my /var/lib which holds my recordings and database is mounted to an xfs partition. I'm happy to post any logs or config files that might be helpful.

---

### Post by nopdotcom on 2012-05-08
> **kpl388 said:**
> I am having similar issues to those reported by other users that are simultaneously upgrading to Ubuntu 12.04 and Mythtv 0.25. Mythfilldatabase is now taking hours (of intense hard drive activity) to complete.
Could you try what works for me? First, mount a tmpfs on /tmp if you haven't; the line for /etc/fstab is
```
tmpfs   /tmp   tmpfs   nodev,nosuid    0 0
```
and it needs a reboot to take effect.

There's a configuration change for MySQL; either do this before a reboot, or stop and start mysql after changing it. Add the following line to [FONT="monospace"]/etc/mysql/conf.d/mythtv-tweaks.cnf[/FONT]:
```
default_storage_engine=MyISAM
```
You can change back to defaults by commenting that line out with a [FONT="monospace"]#[/FONT].

Try out [FONT="monospace"]mythfilldatabase[/FONT] at the command prompt with and without this MySQL setting. Your first run may be doing more work to get you up to date, so I wouldn't treat that one as representative of performance.

---

### Post by kpl388 on 2012-05-08
I edited the fstab file as you suggested. I didn't have a mythtv-tweaks.cnf file. So I created one containing the line you recommended. After rebooting, I ran mythfilldatabase and it hung for a long time again. Next, I tried moving the default_storage_engine line to the already-existing mythtv.cnf in /etc/mysql/init.d. I restarted mysql with

```
sudo service mysql restart
```

Now mythfilldatabase completed in just ~1 minute. 

I'll see if this helps with my other issues and update later.

Thanks so much for the help! (What is this doing? - if you have a chance)

---

### Post by superm1 on 2012-05-08
For this problem with the temp tables, maybe i'm naive - but it sounds like they might do better if they are just stored with the memory engine from the get go.

[http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html](http://dev.mysql.com/doc/refman/5.0/en/memory-storage-engine.html)

They're gonna be axed after the connection is killed anyway, might as well not even BOTHER writing to disk.

Thoughts?

---

### Post by nopdotcom on 2012-05-08
> **kpl388 said:**
> I edited the fstab file as you suggested. I didn't have a mythtv-tweaks.cnf file.
It took a little hunting to find out why ***I*** have a mythtv-tweaks.cnf. It looks like /usr/bin/mythbuntu-control-centre set it up, based on /usr/share/mythbuntu/examples/mythtv-tweaks.dist. mythbuntu-control-centre is pretty cool--definitely check it out.

> **kpl388 said:**
> So I created one containing the line you recommended. After rebooting, I ran mythfilldatabase and it hung for a long time again.
This worried me. I realized that the configuration variable needed to be inside a [FONT="monospace"][****mysql][/FONT] section, so it couldn't work as a single line file.

> **kpl388 said:**
> Now mythfilldatabase completed in just ~1 minute. 

I'll see if this helps with my other issues and update later.

Thanks so much for the help! (What is this doing? - if you have a chance)
Thanks for testing it--now I know I'm not crazy. :-) I can explain what it does, but I can't explain why the default configuration is so bad for us. Please don't cite me on how mysql works, since I only know the basics, and I know I'm simplifying. (MySQL administrators can correct me--I'm writing this to try to explain to myself too.)

WALL OF TEXT FOLLOWS

Below I'm going to refer to *datadir* and *tmpdir*; they're server configuration variables and they should be in [FONT="monospace"]/etc/mysql/my.cnf[/FONT].

In the old days, MySQL used a storage format/engine called MyISAM. This keeps each table in a set of files in (by default) *datadir*/(database-name)/(table-name).{MYD,MYI,frm}. Create a new table, get a new set of files. See [http://en.wikipedia.org/wiki/MyISAM](http://en.wikipedia.org/wiki/MyISAM).

A newer engine called InnoDB ([http://en.wikipedia.org/wiki/InnoDB](http://en.wikipedia.org/wiki/InnoDB)) was introduced a while back, and finally became the default in MySQL 5.5. Among other things, it provides much better error recovery; think of how ext3 removes the need to fsck after every unclean shutdown by using a journal. For ext3 and InnoDB, after a power failure, transactions either happened, or they didn't; there are no half-complete or scrambled operations. So at the end of a transaction group, the disk really has to be physically written. Things that were buffered before the end of the transaction must be written out, and I/O stops until that completes. The synchronization point is called a write barrier, and for a bunch of reasons it is slower than ideal on disks in the real world.

Now, here's where we get into the part I don't understand. InnoDB by default uses a single "table space" to store all InnoDB table data being processed; that's what those [font="monospace"]/var/lib/mysql/ib*[/font] files are. There's an option to turn on separate files for separate tables, but it doesn't seem to much affect the important thing for us, temporary tables.

Temporary tables are what they sound like. They exist for the life of a database connection, or when the server internally needs to store intermediate results. For MyISAM, I'm now pretty certain temporary tables are written to *tmpdir*. Because they're temporary, there is no need for on-disk consistency; if the power fails, the db connection they're associated with is by definition over as well.

[font="monospace"]mythfilldatabase[/font] parses XML and stores the results in temporary tables, running an [font="monospace"]INSERT[/font] statement per data element.  By default, mysql runs in "autocommit" mode unless told otherwise (it can be set for each db connection). Autocommit means each standalone SQL statement executed should be treated as a transaction. 

Uh, wait. That means after reading every single data element in the schedules feed, mysql has to do that really expensive write barrier operation which flushes the disk buffers? That would explain why the disk light comes on and stays on.

But mysql shouldn't have to do those write barriers in this case, since we're [font="monospace"]INSERT[/font]ing into temporary tables, which don't need the consistency guarantee. At least that's what I would think. It still seems to happen, at least for InnoDB tables.

So I think the "[font="monospace"]default_storage_engine=MyISAM[/font]" line has a couple of effects. Explicitly, it says "new tables should be created using the MyISAM engine". (In a running mythtv system, all of the big tables have already been created, and they'll stay in InnoDB ***EDIT:** no, [font="monospace"]ENGINE=MyISAM[/font] is explicitly called for in the non-plugin mythconverg schema*.) Again, I believe temporary MyISAM tables (like the ones mythfilldatabase creates) are created entirely in *tmpdir*. There may be a performance advantage to MyISAM. If *tmpdir* is on a tmpfs there is obviously a performance advantage--it just goes to RAM. Finally, if you ask for a write barrier on a ramdisk, the kernel just says, "done! I guarantee you will now get very consistent results after a power failure!" :-)

The unintended result of "[font="monospace"]default_storage_engine=MyISAM[/font]" is that if there are some non-temporary tables created, they'll be in MyISAM too. I **think** the only time you'll see long-term tables created is when you install mythtv plugins or upgrade the database schema. I'm not certain. It's easy to ask mysql to upgrade any stray tables from MyISAM to InnoDB though.

Somebody who actually knows this stuff should come up with a better fix. I have a great story, but I may be completely wrong about what's going on; I'm too good at convincing myself. I suspect [font="monospace"]datadirect.cpp[/font] may need to do something to turn off autocommit at the least. And yeah, the MEMORY engine may make a lot of sense. I don't know enough about its storage requirements and the minimum RAM in a supported Mythbuntu box to say anything useful. Writing to *tmpdir* does allow somebody starved for memory to mount a no-barrier disk filesystem there instead of a (swappable) ramdisk. It may all be moot; people who have large lineups and no memory just may be out of luck no matter what choices are made in how the DB is configured.

It's beyond me to understand the issues in in the general case. I'd like to punt to upstream unless Mythbuntu wants to hotfix it locally.

---

### Post by nowhere@cox.net on 2012-05-09
Wow, this is one of the worst upgrades for MythTV ever and I've been doing it a long long time. I could go on and on and on about problems, some related to the horrible 12.04 release and other about mythtv itself. It's been a very long time since I have spent such an enormous amount of time just trying to tweak things to work on an upgrade.

Partial list (I'll keep adding to it):
[LIST]
[*]Music won't play at all. Can't adjust volume. It sees my files but just sits there.
[*]Music selection is horrible now. I have to select individual songs after drilling miles into a menu. Can't select a whole artist tree or album tree
[*]System is very laggy in general. Front end hangs up constantly.
[*]mysql change to INNODB would not allow mythfilldb to run
[*]Leftover gripe: I have to drill at least twice as far into menus to do everything compared to a couple mythtv versions ago. Thing like set aspect ratio, edit breakpoints etc.
[*]12.04 crash reports pop up for so many things I can't even list them. It sends off the report (I assume) before I can review it. I get 3 or 4 apport errors per day.
[*]12.04: If I have an encrypted folder, I have NO OPTION but encrypt my whole home folder on install. I am forced to recover my encrypted folder, move everything out, delete the encryted folder before installing.
[*]Escaping out of a video hangs the front end for 60 seconds then crashes it.
[*]There seems to be yet another volume control added to the many levels that were already in existance. I have to alsamixer, raise master and pcm, and I have to raise volume two places in Mythtv and the volume is still half what it was in previous version
[*]cx18 drivers still have red screen of death. I have to blacklist the cx18 drivers, power down my server, unplug the power cable from the PSU, wait 2 or 3 minutes, power up, modprobe cx18, remove cx18-alsa, remove cx18, wait 1 minute, modprobe cx18, capture some video to test, if still red (or pink, or grey) repeat until I get a picture every time I reboot.
[*]following DB upgrade instructions (upgrade schema to 0.25, backup mysql, upgrade system, restore mysql) overwrites encoder schemes in the back end set up. To keep all the default setting correct you HAVE to do a partial restore otherwise things like transcoders are missing
[/LIST]

One good point is that the DVB channel scanner is working better...

---

### Post by TheFuzz4 on 2012-05-09
> **tgm4883 said:**
> There was another issue with 0.25 that prevented getting data from schedules direct, although it shouldn't have affected any Ubuntu based builds. Does anyone having the issue have any non alphanumeric characters in their schedules direct user name?

I am having an issue with mythfilldatabase.  It completes like normal (Using a HP DL385 with 16GB of ram for a backend might be overkill but it sure is nice :) )but my guide data never updates.  I do not have any special characters or anything else in my username for schedules direct so I know that, that is not the issue.  When I run it by hand it looks like it is working but no new data is ever loaded into my program guide.  I am open to all tips and suggestions to resolve this.  This would be the only upgrade issue that I've ran into, other than one of my front ends a nettop box had an issue during the upgrade where it would just sit on the boot screen so after a reinstall of that front end everything is fine.  Just need to get my guide working again so that way I can get my recordings rolling again I haven't had guide data since May 4th.  Thank you all in advance for your help.

---

### Post by kpl388 on 2012-05-09
Thanks for that explanation nopdotcom. I think I (mostly) understand your description of what's going on. Sadly, this does not seem to have helped my other problems with intermittant failed recordings and backend crashes caused by channel changes on my firewire cable box. But mythfilldatabase is completing in an appropriate amount of time without railing on my hard drive! Thanks again for the help.

---

### Post by TheFuzz4 on 2012-05-09
Saw this in the mythfilldatabase output today when running manually 
```


2012-05-09 11:30:20.167648 I  Found 28 channels for source 1 which use grabber
2012-05-09 11:30:20.167752 I  New static DB connectionDataDirectCon
2012-05-09 11:30:20.174551 I  Retrieving datadirect data.
2012-05-09 11:30:20.174565 I  Grabbing ALL available data.
2012-05-09 11:30:20.174649 I  DataDirect: Grabbing listing data
2012-05-09 11:30:20.174708 I  Downloading DataDirect feed
content-type missing in HTTP POST, defaulting to application/octet-stream
content-type missing in HTTP POST, defaulting to application/octet-stream
2012-05-09 11:30:30.245269 E  DataDirect: Failed to get data: Download error
2012-05-09 11:30:30.245282 E  Encountered error in grabbing data.
2012-05-09 11:30:30.245855 E  Failed to fetch some program info
2012-05-09 11:30:30.245887 I  Adjusting program database end times.
2012-05-09 11:30:30.286063 I      0 replacements made
2012-05-09 11:30:30.286073 I  Marking generic episodes.
2012-05-09 11:30:30.339185 I      Found 0
2012-05-09 11:30:30.339256 I  Extending non-unique programids with multiple parts.
2012-05-09 11:30:30.348224 I      Found 0
2012-05-09 11:30:30.348259 I  Marking repeats.
2012-05-09 11:30:30.368409 I      Found 0
2012-05-09 11:30:30.368425 I  Unmarking new episode rebroadcast repeats.
2012-05-09 11:30:30.384834 I      Found 0
2012-05-09 11:30:30.481033 I  Marking episode first showings.
2012-05-09 11:30:31.116559 I      Found 2352
2012-05-09 11:30:31.116570 I  Marking episode last showings.
content-type missing in HTTP POST, defaulting to application/octet-stream
2012-05-09 11:30:31.721002 I      Found 2352
2012-05-09 11:30:31.724060 I  DataDirect: Grabbing next suggested grabbing time
content-type missing in HTTP POST, defaulting to application/octet-stream
2012-05-09 11:30:33.125964 I  Suggested Time data: 612 bytes
2012-05-09 11:30:33.126387 I  DataDirect: BlockedTime is: 2012-05-09T11:30:32
2012-05-09 11:30:33.126517 I  DataDirect: NextSuggestedTime is: 2012-05-09T23:14:00

```

---

### Post by TheFuzz4 on 2012-05-09
Ok so I figured out what the problem was.  For some reason a change from .24 to .25 changed the way that the mythfilldatabase was contacting Schedules Direct.  So since I am running an Astaro firewall at home, the firewall was attempting to virus scan the feed coming in from schedules direct.  A quick modification to the firewall scan rules and I am now once again receiving guide data.  Grrr stupid firewalls.

---

### Post by TheFuzz4 on 2012-05-09
> **nopdotcom said:**
> Could you try what works for me? First, mount a tmpfs on /tmp if you haven't; the line for /etc/fstab is
```
tmpfs   /tmp   tmpfs   nodev,nosuid    0 0
```
and it needs a reboot to take effect.

There's a configuration change for MySQL; either do this before a reboot, or stop and start mysql after changing it. Add the following line to [FONT="monospace"]/etc/mysql/conf.d/mythtv-tweaks.cnf[/FONT]:
```
default_storage_engine=MyISAM
```
You can change back to defaults by commenting that line out with a [FONT="monospace"]#[/FONT].

Try out [FONT="monospace"]mythfilldatabase[/FONT] at the command prompt with and without this MySQL setting. Your first run may be doing more work to get you up to date, so I wouldn't treat that one as representative of performance.

I can confirm that this fix also sped up my mythfilldatabase 100%.  Thank you very much for the tip.

---

### Post by rtrevor on 2012-05-09
I am running 0.25-fixes and have just upgraded from 11.10 to 12.04.

All seems to be well except a problem with mysql not starting via the upstart job, preventing mythtv-backend from running. When trying to start mysql service it would just return 'start: Job failed to start' and syslog would log 'init: mysql pre-start process (3381) terminated with status 1'.

MySQL would start fine by running mysqld as root which suggested my.cnf and other config was fine...

Anyway after some digging I found this thread:

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318)

In particular [comment #27]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318/comments/27") - missing an empty file /etc/apparmor.d/local/usr.sbin.mysqld - was the problem, creating this (empty) file did the trick, mysql now starts and all seems to be fine.

Thought I'd share incase anyone else has the same problem after upgrading.

Cheers

---

### Post by ScottEmery on 2012-05-09
> **nopdotcom said:**
> Could you try what works for me? First, mount a tmpfs on /tmp if you haven't; the line for /etc/fstab is
```
tmpfs   /tmp   tmpfs   nodev,nosuid    0 0
```and it needs a reboot to take effect.

There's a configuration change for MySQL; either do this before a reboot, or stop and start mysql after changing it. Add the following line to [FONT=monospace]/etc/mysql/conf.d/mythtv-tweaks.cnf[/FONT]:
```
default_storage_engine=MyISAM
```You can change back to defaults by commenting that line out with a [FONT=monospace]#[/FONT].

Try out [FONT=monospace]mythfilldatabase[/FONT] at the command prompt with and without this MySQL setting. Your first run may be doing more work to get you up to date, so I wouldn't treat that one as representative of performance.

I can also confirm that making the above changes reduced my mythfilldatabase runtimes from 70-90 minutes down to under 2 minutes. I am running Mythbuntu 12.04 and MythTV v25-82.

---

### Post by mnclayshooter on 2012-05-10
> **ScottEmery said:**
> I can also confirm that making the above changes reduced my mythfilldatabase runtimes from 70-90 minutes down to under 2 minutes. I am running Mythbuntu 12.04 and MythTV v25-82.
 
I can also confirm this worked for me as well. Finished the whole mythfilldatabase in under a minute versus nearly 2 hours prior to the above method. 
 
Thanks!

---

### Post by nopdotcom on 2012-05-10
Cool, thank you for the reports. I think I can go post about this on at least mythtv-users. Part of why I've been cautious is this will be about the third time it's come up; the previous times it's been waved off as "it's a regular barrier issue". There **are** performance issues from write barriers but I think responses in the previous threads misunderstood the nature and magnitude of this case.

This looks like it bites Fedora Core 15 people as well; they also have mysql 5.5 and default-InnoDB.

Jay Carlson
[email]nop@nop.com[/email]

---

### Post by Averyml on 2012-05-11
> **TheFuzz4 said:**
> Ok so I figured out what the problem was.  For some reason a change from .24 to .25 changed the way that the mythfilldatabase was contacting Schedules Direct.  So since I am running an Astaro firewall at home, the firewall was attempting to virus scan the feed coming in from schedules direct.  A quick modification to the firewall scan rules and I am now once again receiving guide data.  Grrr stupid firewalls.

hmmm...I'm also getting pretty much the same log and results you are after upgrading to .25, and I'm also behind an Astaro firewall...but adding a virus scanning exception rule isn't working, hopefully because I'm just doing it wrong.  Could you share the rule you changed?

---

### Post by EldonGatlin on 2012-05-19
Changing the default back to MyISAM is a mistake as pointed out if some infrastructure changes come down using SQL statements to implement.

Did some research and came up with the following configuration:

tmp_table_size=250M
innodb_buffer_pool_size=500M
innodb_additional_mem_pool_size=100M
innodb_file_io_threads=8
innodb_lock_wait_timeout=50
innodb_log_buffer_size=20M
innodb_flush_log_at_trx_commit=0

Disk activity is reasonable and the MythTVBackend approaches 100% utilization which indicates it is not waiting for disk IO.

---

### Post by tgm4883 on 2012-05-19
> **EldonGatlin said:**
> Changing the default back to MyISAM is a mistake as pointed out if some infrastructure changes come down using SQL statements to implement.

Did some research and came up with the following configuration:

tmp_table_size=250M
innodb_buffer_pool_size=500M
innodb_additional_mem_pool_size=100M
innodb_file_io_threads=8
innodb_lock_wait_timeout=50
innodb_log_buffer_size=20M
innodb_flush_log_at_trx_commit=0

Disk activity is reasonable and the MythTVBackend approaches 100% utilization which indicates it is not waiting for disk IO.

The only change that you listed that actually makes a significant difference is 

```
innodb_flush_log_at_trx_commit=0
```

And that isn't really a sane change either, as it isn't writing every transaction. I'm discussing with upstream some other possibilities (such as making the temp tables myisam), but I'm open to any other suggestions as well.

---

### Post by swells5 on 2012-05-21
i had mythtv running well on ubuntu 10.10. I have an rogers STB and hauppauge 1600 card. I was using firewire to get a few HD channels and the card to get all the channels from the cable box in SD. I had LIRC setup on a serial port. All working. When I set up the backend, I used the ivtv choice for configuring the hauppauge 1600 capture card. I use schedules direct.

When I upgraded to 12.04, clean install - in a new partition thankfully, and tried to set up the backend there was no choice for ivtv as there was in .25? I tried each of the other choices, the card was recognized by MPEG-2 encoder card choice but no channels were recognized when i did a channel scan.

After searching i found one other post about this and the response was the ivtv choice was still there and had not been touched. I can't find it!.

I went back to my 10.10 server which I still had in another partition, and all started to work again, except for my laptop which I had already upgraded to 12.04. I am still trying to get mythtv working on the laptop by reinstalling 11.10.

now that I am back to mythtv .24 I can even watch tv on my android tablet.

I am still searching for a solution to this - have upgraded every version of ubuntu since it first started it releases.

---

### Post by nickrout on 2012-05-22
> **swells5 said:**
> i had mythtv running well on ubuntu 10.10. I have an rogers STB and hauppauge 1600 card. I was using firewire to get a few HD channels and the card to get all the channels from the cable box in SD. I had LIRC setup on a serial port. All working. When I set up the backend, I used the ivtv choice for configuring the hauppauge 1600 capture card. I use schedules direct.

When I upgraded to 12.04, clean install - in a new partition thankfully, and tried to set up the backend there was no choice for ivtv as there was in .25? I tried each of the other choices, the card was recognized by MPEG-2 encoder card choice but no channels were recognized when i did a channel scan.it is the same thing, just renamed because ivtv is no longer the only driver for mpeg2 encoder cards - there are newer cards with different drivers. Anyway you shouldn't need to set up your cards again if you import your old database.> 

After searching i found one other post about this and the response was the ivtv choice was still there and had not been touched. I can't find it!.

I went back to my 10.10 server which I still had in another partition, and all started to work again, except for my laptop which I had already upgraded to 12.04. I am still trying to get mythtv working on the laptop by reinstalling 11.10.

now that I am back to mythtv .24 I can even watch tv on my android tablet.

I am still searching for a solution to this - have upgraded every version of ubuntu since it first started it releases.

---

### Post by tgm4883 on 2012-05-31
Looks like a fix was committed on May 28th, and should be in our latest builds [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/997367](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/997367) .

---

### Post by anonymousdog on 2012-06-01
> **tgm4883 said:**
> Looks like a fix was committed on May 28th, and should be in our latest builds [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/997367](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/997367) .
TGM, I want to thank you personally ):P for these commit references when bug fixes are committed to MythTV.

Despite the best efforts of the teams involved, I find it difficult to tell whether and exactly in what version (and how that matches to the Mythbuntu repo versioning) a given fix is included.

Your references clear this up and are fantastic background information that should inform the user of when a given problem should be fixed (and, possibly, when to seek other solutions/explanations if symptoms continue).

---

### Post by ScottEmery on 2012-06-01
Thanks for the information about the fix being committed. Looking at my /var/log/mythtv/mythbackend.log I see that the version I'm running is:

 > mythbackend version: fixes/0.25 [v0.25-133-g399da0a] [www.mythtv.org]("http://www.mythtv.org")Can someone confirm that this version (which I assume is the latest) does indeed contain the fix. Also, is the procedure to undo the temporary workaround which is described earlier in this thread as follows:

Comment out or remove this line in /etc/fstab:

```
tmpfs    /tmp    tmpfs    nodev,nosuid    0 0
``` I'm not sure removing the temporary file system is required, or even desired. Can someone more knowledgable chime in?
Then comment out or remove this line in [FONT=monospace]/etc/mysql/conf.d/mythtv-tweaks.cnf:
[/FONT]
```
default_storage_engine=MyISAM
```Then reboot.

---

### Post by tgm4883 on 2012-06-01
> **anonymousdog said:**
> TGM, I want to thank you personally ):P for these commit references when bug fixes are committed to MythTV.

Despite the best efforts of the teams involved, I find it difficult to tell whether and exactly in what version (and how that matches to the Mythbuntu repo versioning) a given fix is included.

Your references clear this up and are fantastic background information that should inform the user of when a given problem should be fixed (and, possibly, when to seek other solutions/explanations if symptoms continue).

Thanks for the kind words :)

> **ScottEmery said:**
> Thanks for the information about the fix being committed. Looking at my /var/log/mythtv/mythbackend.log I see that the version I'm running is:

 Can someone confirm that this version (which I assume is the latest) does indeed contain the fix. Also, is the procedure to undo the temporary workaround which is described earlier in this thread as follows:

Comment out or remove this line in /etc/fstab:

```
tmpfs    /tmp    tmpfs    nodev,nosuid    0 0
``` I'm not sure removing the temporary file system is required, or even desired. Can someone more knowledgable chime in?
Then comment out or remove this line in [FONT=monospace]/etc/mysql/conf.d/mythtv-tweaks.cnf:
[/FONT]
```
default_storage_engine=MyISAM
```Then reboot.

I'm not too good with git revision numbers, but if you do a 

```
dpkg -l mythtv-backend
```

That should list the version number of the package, which includes the date it was build in YYYYMMDD format

---

### Post by ScottEmery on 2012-06-01
```
dpkg -l mythtv-backend
``` returns: ```
2:0.25.0+fixes.20120531.399da0a-0ubuntu0mythbuntu4
``` So with that May 31, 2012 date code I would assume I have the fix. And after a quick experiment I see that I do indeed have the fix. I made the changes to back out the temporary workaround, and ran mythfilldatabase. It took only 1.5 minutes, compared to 70-90 minutes prior to the fix. So I've confirmed that this fix works.

---

### Post by LarryJ2 on 2012-06-11
Unfortunately, I started mythfilldatabase  as prompted after mythbackend setup terminated without making the two fixes as detailed in this thread.  So my hard drive sounds like a rock crusher.  

How do I safely stop the "mythfilldatabase" process so I can make the changes to /etc/fstab and /etc/mysql/conf.d/mythtv-tweaks.cnf  ?

---

### Post by bcg30506 on 2012-07-10
Ok, I just upgraded from 0.24-fixes to 0.25-fixes in mythbuntu 10.04 using the repository manager.

All went well with the upgrade except for the "partial upgrade" warning and the "mythtv.cnf" changes that others have already mentioned.  I rebooted, and everything came back up.

However, it is not perfect. I am having a few issues that I do not know how to remedy and cannot find answers from anywhere else:

1. I cannot change themes.  When I go to the theme chooser and let it refresh the list and then pick a theme, it says downloading, and gives no errors, but then always puts be in the Terra theme.  I've tried most all of them.  The frontend log showed a permissions error writing to /usr/share/mythtv/themes so I gave it full rwx access for all.  Now the error is gone but I still can't pick a theme and have it stick.

2. All my channel icons are missing.  My directory structure is the same as in 0.24 that was working as I did an Update Manager upgrade, not a fresh install.  How do I see them again?

3. How are videos accessed now in the new menu since mythvideo is no longer a plugin?  "Watch Videos" appears to be missing now under "Media Library" in the menu.

4. Every time I watch live tv or make a recording, a job is now started to download metadata.  It always fails according to the Status page.  How can I stop it from running and/or fix it to succeed?

5. The Goom music visualizer does not work fullscreen and is very slow now.  My VDPAU is still up and HD videos play fine.

6. Where did the Log viewer go in the System Status screen?  How can I view job logs now without manually going into mysql?

Other than that, so far, so good.  I won't know about mythfilldatabase until tomorrow as it runs overnight.

Any help on these few issues would be great.

---

### Post by tgm4883 on 2012-08-14
Closing thread as it's generic and people keep adding their random issues onto this thread.

---

