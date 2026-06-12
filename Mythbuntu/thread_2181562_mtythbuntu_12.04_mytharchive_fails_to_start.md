---
title: "mtythbuntu 12.04 mytharchive fails to start"
date: 2013-10-18
forum: Mythbuntu
---

### Post by ceesquared on 2013-10-18
I have tried loading mytharchive through both software centre and apt-get install. Both give the same result - no go. in terminal I got this result

 colin@MythTv:~$ mytharchivehelper2013-10-18 14:02:40.844316 C  mytharchivehelper version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-10-18 14:02:40.844365 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-10-18 14:02:40.844367 N  Enabled verbose msgs:  general jobqueue
2013-10-18 14:02:40.844382 N  Setting Log Level to LOG_INFO
2013-10-18 14:02:40.844414 I  Added logging to the console
2013-10-18 14:02:40.844420 I  Added database logging to table logging
2013-10-18 14:02:40.844466 N  Setting up SIGHUP handler
2013-10-18 14:02:40.844499 N  Using runtime prefix = /usr
2013-10-18 14:02:40.844507 N  Using configuration directory = /home/colin/.mythtv
2013-10-18 14:02:40.844963 C  Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
2013-10-18 14:02:40.844972 W  This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2013-10-18 14:02:40.844980 !  MythContext: Unable to allocate MythCoreContext
2013-10-18 14:02:40.844988 !  Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
2013-10-18 14:02:40.844992 W  This application is not compatible with the installed MythTV libraries.
2013-10-18 14:02:40.844996 E  Failed to init MythContext, exiting.

note 2 entries about matching libraries. Any one any ideas on how to get round this?

---

### Post by tgm4883 on 2013-10-18
> **ceesquared said:**
> I have tried loading mytharchive through both software centre and apt-get install. Both give the same result - no go. in terminal I got this result

 colin@MythTv:~$ mytharchivehelper2013-10-18 14:02:40.844316 C  mytharchivehelper version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-10-18 14:02:40.844365 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-10-18 14:02:40.844367 N  Enabled verbose msgs:  general jobqueue
2013-10-18 14:02:40.844382 N  Setting Log Level to LOG_INFO
2013-10-18 14:02:40.844414 I  Added logging to the console
2013-10-18 14:02:40.844420 I  Added database logging to table logging
2013-10-18 14:02:40.844466 N  Setting up SIGHUP handler
2013-10-18 14:02:40.844499 N  Using runtime prefix = /usr
2013-10-18 14:02:40.844507 N  Using configuration directory = /home/colin/.mythtv
2013-10-18 14:02:40.844963 C  Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
2013-10-18 14:02:40.844972 W  This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2013-10-18 14:02:40.844980 !  MythContext: Unable to allocate MythCoreContext
2013-10-18 14:02:40.844988 !  Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
2013-10-18 14:02:40.844992 W  This application is not compatible with the installed MythTV libraries.
2013-10-18 14:02:40.844996 E  Failed to init MythContext, exiting.

note 2 entries about matching libraries. Any one any ideas on how to get round this?

You need to make sure that mytharchive is the same version as mythtv. Run 'dpkg -l | grep -i myth' and see what versions you have installed. I'd bet you have builds from different days, in which case, upgrade the older package.

---

