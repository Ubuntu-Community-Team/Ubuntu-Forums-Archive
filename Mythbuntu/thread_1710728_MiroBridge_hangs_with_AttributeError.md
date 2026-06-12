---
title: "MiroBridge hangs with AttributeError"
date: 2011-03-20
forum: Mythbuntu
---

### Post by ybreton on 2011-03-20
Mirobridge hangs when it is run. I've gotten it all down to a failure here:

```
/usr/share/doc/mythtv-backend/contrib/imports/mirobridge/mirobridge.py -V
```
[FONT=Lucida Console]
2011-03-20 11:13:02,881 - mirobridge - INFO - Using python library 'pyparsing' version 1.5.2
2011-03-20 11:13:03.054 Python Database Connection: Using connection settings from /home/ybreton/.mythtv/config.xml
2011-03-20 11:13:05,714 - mirobridge - INFO - Miro Bridge version v0.5.8 with Miro version 3.5.1
2011-03-20 11:13:05,718 - mirobridge - INFO - Using mirobridge_interpreter_3_0_0
2011-03-20 11:13:05,857 - mirobridge - INFO - Miro Version (3.5.1 re5e3cabb)
2011-03-20 11:13:05,858 - mirobridge - INFO - Base Miro Video Directory (/var/lib/mythtv/videos/Podcasts/miro)
2011-03-20 11:13:05,859 - mirobridge - INFO - 
2011-03-20 11:13:05,878 - mirobridge - WARNING - There is no "Videos" Storage Group set so ONLY MythTV Frontend local paths for videos and graphics that are accessable from this MythTV Backend can be used.

==========================================================================================
Listed below are the types and base directories that will be use for processing.
The list reflects your current configuration for the 'mythbox' back end
and whether a directory is a 'SG' (storage group) or not.
Note: All directories are from settings in the MythDB specific to hostname (mythbox).
------------------------------------------------------------------------------------------
Type: Default     - SG-YES - Directory: (/var/lib/mythtv/recordings/)
Type: Cover art   - SG-YES - Directory: (/var/lib/mythtv/coverart/)
Type: Fan art     - SG-YES - Directory: (/var/lib/mythtv/fanart/)
Type: Banners     - SG-YES - Directory: (/var/lib/mythtv/banners/)
Type: Screenshots - SG-YES - Directory: (/var/lib/mythtv/screenshots/)
Type: Video       - SG-NO  - Directory: (/var/lib/mythtv/videos/)
------------------------------------------------------------------------------------------
If a directory you set from a separate Front end is not displayed it means
that the directory is not accessible from this backend OR
you must add the missing directories using the Front end on this Back end.
Front end settings are host machine specific.
==========================================================================================

2011-03-20 11:13:05,921 - mirobridge - INFO - Starting Miro Frontend and Backend
2011-03-20 11:13:05,932 INFO     Starting up Miro
2011-03-20 11:13:05,934 INFO     Version:    3.5.1
2011-03-20 11:13:05,938 INFO     Revision:   ssh://ben@git.participatoryculture.org:2191/var/git/miro - e5e3cabb
2011-03-20 11:13:05,940 INFO     Builder:    buildd@rosehip
2011-03-20 11:13:05,943 INFO     Build Time: 1291763085.04
2011-03-20 11:13:05,944 INFO     Reading HTTP Password list
2011-03-20 11:13:05,949 INFO     Starting libCURL thread
2011-03-20 11:13:05,963 INFO     Starting event loop thread
2011-03-20 11:13:05,968 INFO     Restoring database...
2011-03-20 11:13:05,971 INFO     Sqlite3 version:   3.6.16
2011-03-20 11:13:05,974 INFO     Pysqlite version:  2.4.1
2011-03-20 11:13:05,975 INFO     opening database /home/ybreton/.miro/sqlitedb
2011-03-20 11:13:05,996 TIMING   Database upgrade time: 0.027
2011-03-20 11:13:05,999 INFO     Loading video converters...
2011-03-20 11:13:06,063 INFO     setup tabs...
2011-03-20 11:13:06,088 INFO     setup theme...
2011-03-20 11:13:06,137 INFO     Checking movies directory '/var/lib/mythtv/videos/Podcasts/miro/'...
Startup success.
Traceback (most recent call last):
  File "/usr/share/doc/mythtv-backend/contrib/imports/mirobridge/mirobridge.py", line 2698, in <module>
    main()
  File "/usr/share/doc/mythtv-backend/contrib/imports/mirobridge/mirobridge.py", line 2304, in main
    app.cli_interpreter = MiroInterpreter()
  File "/usr/share/doc/mythtv-backend/contrib/imports/mirobridge/mirobridge/mirobridge_interpreter_3_0_0.py", line 91, in __init__
    self.init_database_objects()
  File "/usr/share/doc/mythtv-backend/contrib/imports/mirobridge/mirobridge/mirobridge_interpreter_3_0_0.py", line 74, in decorated
    eventloop.addUrgentCall(runThenSet, 'run in event loop')
AttributeError: 'module' object has no attribute 'addUrgentCall'[/FONT]

And then it hangs. Any ideas about how to fix this? I'm running Miro 3.5.1 and MythTV 0.23. The result of running 
```
mirobridge.py -Vt
```
gives me the all-systems-go message, so I'm a little stumped.

Thanks!

Yannick.

---

### Post by superm1 on 2011-03-21
Mirobridge bundled with 0.23 doesn't support miro 3.5.1.  You'll need to update to 0.24's mirobridge.  It may not work with MythTV 0.23 though.

So your options are:

1) Downgrade miro to 3.00, stay with mythtv 0.23, mirobridge version same.  This should work

2) Upgrade mirobridge to mythtv 0.24's, keep others same. This might not work.

3) Upgrade to Mythtv 0.24, newer mirobridge package is included.  Keep miro the same.

I would personally do <3>.  Up to you.

---

