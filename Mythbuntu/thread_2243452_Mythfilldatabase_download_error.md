---
title: "Mythfilldatabase download error"
date: 2014-09-08
forum: Mythbuntu
---

### Post by brplut40 on 2014-09-08
When mythfilldatabase runs automatically, it does not grab the data or update the schedule. I have tried seeing if there is a mythtv_ddp_data file in /tmp according to several posts including [http://ubuntuforums.org/showthread.php?t=2153391](http://ubuntuforums.org/showthread.php?t=2153391) I had no such file. I have tried telling myth what time to run mythfilldatabase instead of the grabber suggested time according to [http://ubuntuforums.org/showthread.php?t=2208646](http://ubuntuforums.org/showthread.php?t=2208646) I have added logging to when it runs and the only useful information is below. My configuration is to run mythfilldatabase with the following options [I]--dd-grab-all --syslog local7
[/I]
I have also found that when I manually run mythfilldatabase as the user "mythtv" it fails with the same error. When I look at the packet capture when attempting to run mythfilldatabase all I see is a DNS request and response for  webservices.schedulesdirect.tmsdatadirect.com and that is it. No other connection or attempt to connect to the web server.

If I run a manual update as my local user everything works fine. Any idea why the mythtv user is not able to run mythfilldatabase properly?

```
2014-09-08 21:08:59.510504 C  mythfilldatabase version: fixes/0.27 [v0.27.3-153-g231972c] www.mythtv.org
2014-09-08 21:08:59.510522 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-09-08 21:08:59.510526 N  Enabled verbose msgs:  general
2014-09-08 21:08:59.510535 N  Setting Log Level to LOG_DEBUG
2014-09-08 21:08:59.522106 I  Added logging to the console
2014-09-08 21:08:59.523963 I  Setup Interrupt handler
2014-09-08 21:08:59.523994 I  Setup Terminated handler
2014-09-08 21:08:59.524018 I  Setup Segmentation fault handler
2014-09-08 21:08:59.524040 I  Setup Aborted handler
2014-09-08 21:08:59.524062 I  Setup Bus error handler
2014-09-08 21:08:59.524084 I  Setup Floating point exception handler
2014-09-08 21:08:59.524108 I  Setup Illegal instruction handler
2014-09-08 21:08:59.524138 I  Setup Real-time signal 0 handler
2014-09-08 21:08:59.524233 N  Using runtime prefix = /usr
2014-09-08 21:08:59.524265 N  Using configuration directory = /home/mythtv/.mythtv
2014-09-08 21:08:59.524435 I  Assumed character encoding: en_US.UTF-8
2014-09-08 21:08:59.525241 N  Empty LocalHostName.
2014-09-08 21:08:59.525259 I  Using localhost value of mythtv
2014-09-08 21:08:59.559236 D  FindDatabase() - Success!
2014-09-08 21:08:59.562563 N  Setting QT default locale to EN_US
2014-09-08 21:08:59.562632 I  Current locale EN_US
2014-09-08 21:08:59.562687 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-09-08 21:08:59.583162 I  Loading en_us translation for module mythfrontend
2014-09-08 21:08:59.588376 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-09-08 21:08:59.598985 I  MythCoreContext: Connecting to backend server: 192.168.1.57:6543 (try 1 of 1)
2014-09-08 21:08:59.603929 I  Using protocol version 77
2014-09-08 21:08:59.605566 I  Opening blocking connection to master backend
2014-09-08 21:08:59.607347 I  Updating source #4 (cable) with grabber schedulesdirect1
2014-09-08 21:08:59.608024 I  Found 197 channels for source 4 which use grabber
2014-09-08 21:08:59.608104 I  This DataDirect listings source is shared by 2 MythTV lineups
2014-09-08 21:08:59.608120 N  We should keep data around after this one
2014-09-08 21:08:59.612217 I  Retrieving datadirect data.
2014-09-08 21:08:59.612235 I  Grabbing ALL available data.
2014-09-08 21:08:59.612312 I  DataDirect: Grabbing listing data
2014-09-08 21:08:59.612612 I  Downloading DataDirect feed
2014-09-08 21:08:59.627669 I  New Client:  (#1)
2014-09-08 21:09:59.713375 E  DataDirect: Failed to get data: Download error
2014-09-08 21:09:59.713399 E  Encountered error in grabbing data.
2014-09-08 21:09:59.736048 I  Updating source #6 (cable2) with grabber schedulesdirect1
2014-09-08 21:09:59.736601 I  Found 5 channels for source 6 which use grabber
2014-09-08 21:09:59.736640 I  This DataDirect listings source is shared by 2 MythTV lineups
2014-09-08 21:09:59.736650 N  We should use cached data for this one
2014-09-08 21:09:59.739118 I  Retrieving datadirect data.
2014-09-08 21:09:59.739135 I  Grabbing ALL available data.
2014-09-08 21:09:59.739168 I  DataDirect: Grabbing listing data
2014-09-08 21:09:59.739408 I  Downloading DataDirect feed
2014-09-08 21:10:59.780820 E  DataDirect: Failed to get data: Download error
2014-09-08 21:10:59.780845 E  Encountered error in grabbing data.
2014-09-08 21:10:59.781971 E  Failed to fetch some program info
2014-09-08 21:10:59.782027 I  Adjusting program database end times.
2014-09-08 21:10:59.783415 I      0 replacements made
2014-09-08 21:10:59.783432 I  Marking generic episodes.
2014-09-08 21:11:00.193452 I      Found 0
2014-09-08 21:11:00.193474 I  Extending non-unique programids with multiple parts.
2014-09-08 21:11:00.286380 I      Found 0
2014-09-08 21:11:00.286398 I  Fixing missing original airdates.
2014-09-08 21:11:01.065026 I      Found 0 with programids
2014-09-08 21:11:01.066394 I      Found 0 without programids
2014-09-08 21:11:01.066414 I  Marking repeats.
2014-09-08 21:11:01.258650 I      Found 0
2014-09-08 21:11:01.258671 I  Unmarking new episode rebroadcast repeats.
2014-09-08 21:11:01.455106 I      Found 0
2014-09-08 21:11:02.392169 I  Marking episode first showings.
2014-09-08 21:11:03.576299 I      Found 39500
2014-09-08 21:11:03.576320 I  Marking episode last showings.
2014-09-08 21:11:05.062978 I      Found 39208
2014-09-08 21:11:05.078046 I
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2014-09-08 21:11:05.079671 N  mythfilldatabase run complete.
2014-09-08 21:11:05.079771 I  Waiting for threads to exit.
```

---

### Post by aelfric55 on 2014-09-09
This error began to be reported as occuring with mythfilldatabase and Schedules Direct back around the first of the year. Schedules Direct attributed the issue to changes in their xml source upstream, and then announced in March that they had the issue solved. Nevertheless, I (for one) have never been able to get mythfilldatabase to complete successfully again, unless I ssh into the headless master backend and run mythfilldatabase as a user. Not in 0.25.4 nor 0.27 or 0.27.3 Setting up a simple cron job to run mythfilldatabase with the main user's credentials oddly also failed with the same mythfilldatabase error.

Finally, out of annoyance I wrote a short script to run as a cron job on a secondary backend. The script on the secondary backend ssh's into the master backend as the main user, runs mythfilldatabase, and then exits. This has been successful for me -- mythfilldatabase completes and updates whenever the script runs.

The workaround seemed Rube Goldberg-y, but I've been able to just let it run for the past 5 months or so without thinking about it. When I moved to 0.25.3 in July I tried the usual ways of automating mythfilldatabase again, but I found that they were still failing for me with the same error, while manually running mythfilldatabase as the main user still worked. So I went back to using the script.

---

