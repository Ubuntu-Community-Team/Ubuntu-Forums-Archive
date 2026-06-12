---
title: "Mythfilldatabase not fetching guide data past Oct 10"
date: 2014-10-03
forum: Mythbuntu
---

### Post by garsh on 2014-10-03
I noticed recently that I no longer have the usual two weeks worth of guide data.
For some reason, mythfilldatabase is no longer fetching data past Oct 10.

My mythweb status page says: There's guide data until 2014-10-10 03:00:00 (7 days).

My Schedules Direct account is paid up through June 2015.

Here's a log of my last manually-initiated mythfilldatabase run.
Do you see anything suspicious in here?  I don't see any errors or warnings.
```
[COLOR=#000000]2014-10-03 11:17:17.580429 C [22961/22961] thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) - mythfilldatabase version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org[/COLOR]2014-10-03 11:17:17.580459 C [22961/22961] thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) - Qt version: compile: 4.8.6, runtime: 4.8.6
2014-10-03 11:17:17.580480 N [22961/22961] thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) - Enabled verbose msgs:  general
2014-10-03 11:17:17.580599 N [22961/22961] thread_unknown logging.cpp:914 (logStart) - Setting Log Level to LOG_INFO
2014-10-03 11:17:17.591795 I [22961/22964] Logger logging.cpp:315 (run) - Added logging to the console
2014-10-03 11:17:17.592892 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Interrupt handler
2014-10-03 11:17:17.592909 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Terminated handler
2014-10-03 11:17:17.592924 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Segmentation fault handler
2014-10-03 11:17:17.592940 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Aborted handler
2014-10-03 11:17:17.592951 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Bus error handler
2014-10-03 11:17:17.592966 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Floating point exception handler
2014-10-03 11:17:17.592977 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Illegal instruction handler
2014-10-03 11:17:17.592995 I [22961/22961] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Real-time signal 0 handler
2014-10-03 11:17:17.593055 N [22961/22961] thread_unknown mythdirs.cpp:55 (InitializeMythDirs) - Using runtime prefix = /usr
2014-10-03 11:17:17.593077 N [22961/22961] thread_unknown mythdirs.cpp:68 (InitializeMythDirs) - Using configuration directory = /home/garsh/.mythtv
2014-10-03 11:17:17.593195 I [22961/22961] CoreContext mythcorecontext.cpp:254 (Init) - Assumed character encoding: en_US.UTF-8
2014-10-03 11:17:17.697176 I [22961/22963] LogForward loggingserver.cpp:1372 (forwardMessage) - New Client:  (#1)
2014-10-03 11:17:17.981125 I [22961/22963] LogForward loggingserver.cpp:142 (FileLogger) - Added logging to /home/garsh/mythfilldatabase.20141003151717.22961.log
2014-10-03 11:17:18.107778 N [22961/22961] CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) - Empty LocalHostName.
2014-10-03 11:17:18.107813 I [22961/22961] CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) - Using localhost value of fox
2014-10-03 11:17:18.157891 N [22961/22961] CoreContext mythcorecontext.cpp:1328 (InitLocale) - Setting QT default locale to EN_US
2014-10-03 11:17:18.158078 I [22961/22961] CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) - Current locale EN_US
2014-10-03 11:17:18.158230 N [22961/22961] CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) - Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-10-03 11:17:18.208680 I [22961/22961] CoreContext mythtranslation.cpp:65 (load) - Loading en_us translation for module mythfrontend
2014-10-03 11:17:18.222501 I [22961/22961] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1317
2014-10-03 11:17:18.227392 I [22961/22961] CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket) - MythCoreContext: Connecting to backend server: 192.168.253.5:6543 (try 1 of 1)
2014-10-03 11:17:18.232408 I [22961/22961] CoreContext mythcorecontext.cpp:1241 (CheckProtoVersion) - Using protocol version 77
2014-10-03 11:17:18.233817 I [22961/22961] CoreContext main.cpp:327 (main) - Opening blocking connection to master backend
2014-10-03 11:17:22.443835 I [22961/22961] CoreContext filldata.cpp:569 (Run) - Updating source #1 (Armstrong Digital Cable) with grabber schedulesdirect1
2014-10-03 11:17:22.445479 I [22961/22961] CoreContext filldata.cpp:583 (Run) - Found 198 channels for source 1 which use grabber
2014-10-03 11:17:22.445602 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 0, date: Fri Oct 3 2014
2014-10-03 11:17:24.110146 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Fri Oct 3 2014, skipping
2014-10-03 11:17:24.110201 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 1, date: Sat Oct 4 2014
2014-10-03 11:17:24.110208 I [22961/22961] CoreContext filldata.cpp:742 (Run) - Data Refresh always needed for tomorrow
2014-10-03 11:17:24.110214 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Sat Oct 4 2014
2014-10-03 11:17:24.151239 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:17:24.151277 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 1
2014-10-03 11:17:24.151300 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-04T00:00:00Z to 2014-10-05T00:00:00Z (UTC)
2014-10-03 11:17:24.151333 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:17:24.151394 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:17:36.727310 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 287947 bytes
2014-10-03 11:17:36.727337 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:17:36.761188 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2585810 bytes
2014-10-03 11:17:36.854713 I [22961/22961] CoreContext mythdbcon.cpp:436 (getStaticCon) - New static DB connectionDataDirectCon
2014-10-03 11:17:36.881594 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:17:36.994182 I [22961/22961] CoreContext datadirect.cpp:2318 (set_lineup_type) - DataDirect: sourceid 1 has lineup type: CableDigital
2014-10-03 11:17:44.085525 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:17:44.086656 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:17:44.086665 I [22961/22961] CoreContext filldata.cpp:261 (GrabDDData) - Updating MythTV channels.
2014-10-03 11:17:44.109908 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.122866 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.135748 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.154549 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.167436 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.180333 I [22961/22961] CoreContext cardutil.cpp:117 (IsCableCardPresent) - Cardutil: HDHomeRun Cablecard Present.
2014-10-03 11:17:44.180470 I [22961/22961] CoreContext filldata.cpp:263 (GrabDDData) - Channels updated.
2014-10-03 11:17:44.521417 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:17:44.521497 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:18:30.511057 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:18:30.511080 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:18:35.366911 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:18:35.367024 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 2, date: Sun Oct 5 2014
2014-10-03 11:18:35.584088 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Sun Oct 5 2014, skipping
2014-10-03 11:18:35.584141 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 3, date: Mon Oct 6 2014
2014-10-03 11:18:35.738550 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Mon Oct 6 2014, skipping
2014-10-03 11:18:35.738602 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 4, date: Tue Oct 7 2014
2014-10-03 11:18:35.892496 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Tue Oct 7 2014, skipping
2014-10-03 11:18:35.892552 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 5, date: Wed Oct 8 2014
2014-10-03 11:18:36.043433 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Wed Oct 8 2014, skipping
2014-10-03 11:18:36.043486 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 6, date: Thu Oct 9 2014
2014-10-03 11:18:36.192062 N [22961/22961] CoreContext filldata.cpp:913 (Run) - Data is already present for Thu Oct 9 2014, skipping
2014-10-03 11:18:36.192115 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 7, date: Fri Oct 10 2014
2014-10-03 11:18:36.276014 I [22961/22961] CoreContext filldata.cpp:827 (Run) - Data refresh needed because only 0 out of 198 channels have at least one program listed for day @ offset 7 from 8PM - midnight.  Previous day had 133 channels with data in that time period.
2014-10-03 11:18:36.276032 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Fri Oct 10 2014
2014-10-03 11:18:36.294387 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:18:36.294415 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 7
2014-10-03 11:18:36.294446 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-10T00:00:00Z to 2014-10-11T00:00:00Z (UTC)
2014-10-03 11:18:36.294462 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:18:36.294499 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:18:47.505279 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 286823 bytes
2014-10-03 11:18:47.505303 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:18:47.545681 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2629991 bytes
2014-10-03 11:18:47.589555 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:18:54.942268 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:18:54.943341 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:18:55.233768 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:18:55.233837 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:18:58.478166 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:18:58.478178 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:19:02.331073 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:19:02.331184 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 8, date: Sat Oct 11 2014
2014-10-03 11:19:02.350610 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 8 from 8PM - midnight.
2014-10-03 11:19:02.350624 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Sat Oct 11 2014
2014-10-03 11:19:02.352803 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:19:02.352828 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 8
2014-10-03 11:19:02.352848 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-11T00:00:00Z to 2014-10-12T00:00:00Z (UTC)
2014-10-03 11:19:02.352861 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:19:02.352898 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:19:13.162225 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 276302 bytes
2014-10-03 11:19:13.162262 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:19:13.193231 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2498765 bytes
2014-10-03 11:19:13.234274 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:19:20.447221 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:19:20.448308 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:19:20.738247 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:19:20.738320 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:19:23.787870 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:19:23.787884 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:19:27.345126 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:19:27.345229 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 9, date: Sun Oct 12 2014
2014-10-03 11:19:27.364639 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 9 from 8PM - midnight.
2014-10-03 11:19:27.364656 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Sun Oct 12 2014
2014-10-03 11:19:27.366734 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:19:27.366758 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 9
2014-10-03 11:19:27.366779 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-12T00:00:00Z to 2014-10-13T00:00:00Z (UTC)
2014-10-03 11:19:27.366793 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:19:27.366830 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:19:39.177400 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 262846 bytes
2014-10-03 11:19:39.177432 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:19:39.206554 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2345852 bytes
2014-10-03 11:19:39.247757 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:19:46.476614 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:19:46.477831 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:19:46.767985 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:19:46.768053 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:19:49.835722 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:19:49.835735 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:19:53.342367 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:19:53.342471 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 10, date: Mon Oct 13 2014
2014-10-03 11:19:53.361721 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2014-10-03 11:19:53.361732 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Mon Oct 13 2014
2014-10-03 11:19:53.363711 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:19:53.363735 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 10
2014-10-03 11:19:53.363756 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-13T00:00:00Z to 2014-10-14T00:00:00Z (UTC)
2014-10-03 11:19:53.363769 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:19:53.363805 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:20:03.573073 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 280256 bytes
2014-10-03 11:20:03.573106 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:20:03.604462 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2603168 bytes
2014-10-03 11:20:03.650994 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:20:10.889552 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:20:10.890595 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:20:11.181349 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:20:11.181420 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:20:14.299681 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:20:14.299695 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:20:19.421415 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:20:19.421602 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 11, date: Tue Oct 14 2014
2014-10-03 11:20:19.454007 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2014-10-03 11:20:19.454026 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Tue Oct 14 2014
2014-10-03 11:20:19.457768 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:20:19.457800 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 11
2014-10-03 11:20:19.457826 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-14T00:00:00Z to 2014-10-15T00:00:00Z (UTC)
2014-10-03 11:20:19.457841 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:20:19.457881 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:20:30.668353 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 269948 bytes
2014-10-03 11:20:30.668386 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:20:30.699138 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2563086 bytes
2014-10-03 11:20:30.761005 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:20:37.970411 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:20:37.971395 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:20:38.261343 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:20:38.261411 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:20:41.328382 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:20:41.328395 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:20:44.823851 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:20:44.823955 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 12, date: Wed Oct 15 2014
2014-10-03 11:20:44.843111 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2014-10-03 11:20:44.843124 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Wed Oct 15 2014
2014-10-03 11:20:44.845221 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:20:44.845248 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 12
2014-10-03 11:20:44.845269 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-15T00:00:00Z to 2014-10-16T00:00:00Z (UTC)
2014-10-03 11:20:44.845283 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:20:44.845320 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:20:58.256468 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 266099 bytes
2014-10-03 11:20:58.256494 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:20:58.286893 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2523737 bytes
2014-10-03 11:20:58.322083 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:21:05.554618 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:21:05.555742 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:21:05.845521 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:21:05.845588 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:21:08.893976 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:21:08.893989 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:21:14.466238 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:21:14.466470 I [22961/22961] CoreContext filldata.cpp:733 (Run) - Checking day @ offset 13, date: Thu Oct 16 2014
2014-10-03 11:21:14.502806 I [22961/22961] CoreContext filldata.cpp:835 (Run) - Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2014-10-03 11:21:14.502837 N [22961/22961] CoreContext filldata.cpp:891 (Run) - Refreshing data for Thu Oct 16 2014
2014-10-03 11:21:14.761762 I [22961/22961] CoreContext filldata.cpp:212 (GrabDDData) - Retrieving datadirect data.
2014-10-03 11:21:14.761813 I [22961/22961] CoreContext filldata.cpp:230 (GrabDDData) - Grabbing data for Fri Oct 3 2014 offset 13
2014-10-03 11:21:14.761851 I [22961/22961] CoreContext filldata.cpp:233 (GrabDDData) - From 2014-10-16T00:00:00Z to 2014-10-17T00:00:00Z (UTC)
2014-10-03 11:21:14.761878 I [22961/22961] CoreContext datadirect.cpp:1155 (GrabData) - DataDirect: Grabbing listing data
2014-10-03 11:21:14.761963 I [22961/22961] CoreContext datadirect.cpp:1017 (DDPost) - Downloading DataDirect feed
2014-10-03 11:21:23.771318 I [22961/22961] CoreContext datadirect.cpp:1029 (DDPost) - Downloaded 268305 bytes
2014-10-03 11:21:23.771345 I [22961/22961] CoreContext datadirect.cpp:1031 (DDPost) - Uncompressing DataDirect feed
2014-10-03 11:21:23.801625 I [22961/22961] CoreContext datadirect.cpp:1036 (DDPost) - Uncompressed to 2494625 bytes
2014-10-03 11:21:23.842698 I [22961/22961] CoreContext datadirect.cpp:463 (characters) - DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-03 11:21:31.058102 I [22961/22961] CoreContext filldata.cpp:254 (GrabDDData) - Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-03 11:21:31.059197 I [22961/22961] CoreContext filldata.cpp:258 (GrabDDData) - Main temp tables populated.
2014-10-03 11:21:31.348272 I [22961/22961] CoreContext filldata.cpp:291 (GrabDDData) - Clearing data for source.
2014-10-03 11:21:31.348339 I [22961/22961] CoreContext filldata.cpp:297 (GrabDDData) - Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-03 11:21:34.409864 I [22961/22961] CoreContext filldata.cpp:299 (GrabDDData) - Data for source cleared.
2014-10-03 11:21:34.409877 I [22961/22961] CoreContext filldata.cpp:301 (GrabDDData) - Updating programs.
2014-10-03 11:21:37.896032 I [22961/22961] CoreContext filldata.cpp:303 (GrabDDData) - Program table update complete.
2014-10-03 11:21:38.494908 N [22961/22961] CoreContext main.cpp:450 (main) - Data fetching complete.
2014-10-03 11:21:38.494948 I [22961/22961] CoreContext main.cpp:458 (main) - Adjusting program database end times.
2014-10-03 11:21:39.939911 I [22961/22961] CoreContext main.cpp:464 (main) -     0 replacements made
2014-10-03 11:21:39.939925 I [22961/22961] CoreContext main.cpp:466 (main) - Marking generic episodes.
2014-10-03 11:21:40.970546 I [22961/22961] CoreContext main.cpp:478 (main) -     Found 1379
2014-10-03 11:21:40.970561 I [22961/22961] CoreContext main.cpp:481 (main) - Extending non-unique programids with multiple parts.
2014-10-03 11:21:41.180606 I [22961/22961] CoreContext main.cpp:532 (main) -     Found 0
2014-10-03 11:21:41.180620 I [22961/22961] CoreContext main.cpp:534 (main) - Fixing missing original airdates.
2014-10-03 11:21:42.583168 I [22961/22961] CoreContext main.cpp:549 (main) -     Found 0 with programids
2014-10-03 11:21:42.585393 I [22961/22961] CoreContext main.cpp:569 (main) -     Found 0 without programids
2014-10-03 11:21:42.585400 I [22961/22961] CoreContext main.cpp:573 (main) - Marking repeats.
2014-10-03 11:21:43.203731 I [22961/22961] CoreContext main.cpp:587 (main) -     Found 2593
2014-10-03 11:21:43.203748 I [22961/22961] CoreContext main.cpp:589 (main) - Unmarking new episode rebroadcast repeats.
2014-10-03 11:21:43.710426 I [22961/22961] CoreContext main.cpp:599 (main) -     Found 0
2014-10-03 11:21:46.268599 I [22961/22961] CoreContext main.cpp:608 (main) - Marking episode first showings.
2014-10-03 11:21:48.539442 I [22961/22961] CoreContext main.cpp:638 (main) -     Found 33731
2014-10-03 11:21:48.539467 I [22961/22961] CoreContext main.cpp:640 (main) - Marking episode last showings.
2014-10-03 11:21:50.827399 I [22961/22961] CoreContext main.cpp:670 (main) -     Found 33638
2014-10-03 11:21:50.871607 I [22961/22961] CoreContext datadirect.cpp:1057 (GrabNextSuggestedTime) - DataDirect: Grabbing next suggested grabbing time
2014-10-03 11:21:51.273439 I [22961/22961] CoreContext datadirect.cpp:1099 (GrabNextSuggestedTime) - Suggested Time data: 612 bytes
2014-10-03 11:21:51.274532 I [22961/22961] CoreContext datadirect.cpp:1135 (GrabNextSuggestedTime) - DataDirect: BlockedTime is: 2014-10-03T15:21:55Z
2014-10-03 11:21:51.274879 I [22961/22961] CoreContext datadirect.cpp:1124 (GrabNextSuggestedTime) - DataDirect: nextSuggestedTime is: 2014-10-04T07:16:43Z
2014-10-03 11:21:51.282818 I [22961/22961] CoreContext main.cpp:697 (main) - 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2014-10-03 11:21:51.286032 N [22961/22961] CoreContext main.cpp:707 (main) - mythfilldatabase run complete. [COLOR=#000000]2014-10-03 11:21:51.286207 I [22961/22961] CoreContext mythcontext.cpp:1194 (~MythContext) - Waiting for threads to exit.[/COLOR]
```

---

### Post by topcat5 on 2014-10-04
Something very odd is going on with the scheduling that has started up in the last few days.  I've seen some, but not all,  long term schedules all of a sudden not find new episodes even though these same profiles have recorded in the past.  The only changing variable in this are the updates coming through mythfilldatabase.

---

### Post by tgm4883 on 2014-10-04
> **topcat5 said:**
> Something very odd is going on with the scheduling that has started up in the last few days.  I've seen some, but not all,  long term schedules all of a sudden not find new episodes even though these same profiles have recorded in the past.  The only changing variable in this are the updates coming through mythfilldatabase.

I think you mean pending changes. Nothing has been changed yet, so I'm not sure how that could be the issue. 

What options is OP running for mythfilldatabase? I've use --dd-grab-all and have a full 16 days of data.

---

### Post by garsh on 2014-10-04
I ran with no options (other than --logpath).
I just now ran with --dd-grab-all.  I still have nothing past Oct 10.
```

$ mythfilldatabase --logpath /home/garsh --dd-grab-all
2014-10-04 11:26:42.523596 C  mythfilldatabase version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-10-04 11:26:42.523650 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-10-04 11:26:42.523687 N  Enabled verbose msgs:  general
2014-10-04 11:26:42.523899 N  Setting Log Level to LOG_INFO
2014-10-04 11:26:42.538195 I  Setup Interrupt handler
2014-10-04 11:26:42.538211 I  Setup Terminated handler
2014-10-04 11:26:42.538228 I  Setup Segmentation fault handler
2014-10-04 11:26:42.538245 I  Setup Aborted handler
2014-10-04 11:26:42.538256 I  Setup Bus error handler
2014-10-04 11:26:42.538272 I  Setup Floating point exception handler
2014-10-04 11:26:42.538282 I  Setup Illegal instruction handler
2014-10-04 11:26:42.538301 I  Setup Real-time signal 0 handler
2014-10-04 11:26:42.538364 N  Using runtime prefix = /usr
2014-10-04 11:26:42.538386 N  Using configuration directory = /home/garsh/.mythtv
2014-10-04 11:26:42.538503 I  Assumed character encoding: en_US.UTF-8
2014-10-04 11:26:42.538956 I  Added logging to the console
2014-10-04 11:26:42.641910 I  New Client:  (#1)
2014-10-04 11:26:42.929859 I  Added logging to /home/garsh/mythfilldatabase.20141004152642.31837.log
2014-10-04 11:26:42.936387 N  Empty LocalHostName.
2014-10-04 11:26:42.936424 I  Using localhost value of fox
2014-10-04 11:26:42.990798 N  Setting QT default locale to EN_US
2014-10-04 11:26:42.990966 I  Current locale EN_US
2014-10-04 11:26:42.991109 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-10-04 11:26:43.025264 I  Loading en_us translation for module mythfrontend
2014-10-04 11:26:43.073795 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-10-04 11:26:43.078011 I  MythCoreContext: Connecting to backend server: 192.168.253.5:6543 (try 1 of 1)
2014-10-04 11:26:43.096513 I  Using protocol version 77
2014-10-04 11:26:43.097779 I  Opening blocking connection to master backend
2014-10-04 11:26:43.743097 I  Updating source #1 (Armstrong Digital Cable) with grabber schedulesdirect1
2014-10-04 11:26:43.744011 I  Found 198 channels for source 1 which use grabber
2014-10-04 11:26:43.755762 I  Retrieving datadirect data.
2014-10-04 11:26:43.755774 I  Grabbing ALL available data.
2014-10-04 11:26:43.755825 I  DataDirect: Grabbing listing data
2014-10-04 11:26:43.755888 I  Downloading DataDirect feed
2014-10-04 11:28:03.671241 I  Downloaded 2609389 bytes
2014-10-04 11:28:03.671267 I  Uncompressing DataDirect feed
2014-10-04 11:28:03.950663 I  Uncompressed to 32415657 bytes
2014-10-04 11:28:04.407151 I  New static DB connectionDataDirectCon
2014-10-04 11:28:04.434108 I  DataDirect: Your subscription expires on Tue Jun 16 (2015) 1:49 PM
2014-10-04 11:28:04.562418 I  DataDirect: sourceid 1 has lineup type: CableDigital
2014-10-04 11:28:11.638917 I  Grab complete.  Actual data from 2014-10-09T00:00:00Z to 2014-10-10T00:00:00Z (UTC)
2014-10-04 11:28:11.640236 I  Main temp tables populated.
2014-10-04 11:28:11.640246 I  Updating MythTV channels.
2014-10-04 11:28:11.701600 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.715510 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.729442 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.754661 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.768448 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.782607 I  Cardutil: HDHomeRun Cablecard Present.
2014-10-04 11:28:11.788203 I  Channels updated.
2014-10-04 11:28:12.130369 I  Clearing data for source.
2014-10-04 11:28:12.130443 I  Clearing from 2014-10-08T20:00:00 to 2014-10-09T20:00:00 (localtime)
2014-10-04 11:28:15.241885 I  Data for source cleared.
2014-10-04 11:28:15.241897 I  Updating programs.
2014-10-04 11:28:18.639126 I  Program table update complete.
2014-10-04 11:28:19.220137 N  Data fetching complete.
2014-10-04 11:28:19.220176 I  Adjusting program database end times.
2014-10-04 11:28:20.306169 I      0 replacements made
2014-10-04 11:28:20.306183 I  Marking generic episodes.
2014-10-04 11:28:21.299786 I      Found 1379
2014-10-04 11:28:21.299802 I  Extending non-unique programids with multiple parts.
2014-10-04 11:28:21.506714 I      Found 0
2014-10-04 11:28:21.506729 I  Fixing missing original airdates.
2014-10-04 11:28:22.847311 I      Found 0 with programids
2014-10-04 11:28:22.849614 I      Found 0 without programids
2014-10-04 11:28:22.849623 I  Marking repeats.
2014-10-04 11:28:23.450710 I      Found 2593
2014-10-04 11:28:23.450725 I  Unmarking new episode rebroadcast repeats.
2014-10-04 11:28:23.960650 I      Found 0
2014-10-04 11:28:26.440244 I  Marking episode first showings.
2014-10-04 11:28:28.582076 I      Found 32377
2014-10-04 11:28:28.582101 I  Marking episode last showings.
2014-10-04 11:28:30.772287 I      Found 32274
2014-10-04 11:28:30.793863 I  DataDirect: Grabbing next suggested grabbing time
2014-10-04 11:28:31.196730 I  Suggested Time data: 612 bytes
2014-10-04 11:28:31.197839 I  DataDirect: BlockedTime is: 2014-10-04T15:28:35Z
2014-10-04 11:28:31.198141 I  DataDirect: nextSuggestedTime is: 2014-10-05T17:09:55Z
2014-10-04 11:28:31.200659 I
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2014-10-04 11:28:31.205620 N  mythfilldatabase run complete.
2014-10-04 11:28:31.206639 I  Waiting for threads to exit.
2014-10-04 11:28:31.319369 I  Removed logging to /home/garsh/mythfilldatabase.20141004152642.31837.log
```

---

### Post by garsh on 2014-10-04
It appears to be a problem with Schedules Direct.
When I go to [http://www.schedulesdirect.org/getdata](http://www.schedulesdirect.org/getdata), I only see a handful of listings for today.
```
[COLOR=#000000]<?xml version='1.0' encoding='utf-8'?>[/COLOR]<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/' xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENC='http://schemas.xmlsoap.org/soap/encoding/'>
<SOAP-ENV:Body>
<ns1:downloadResponse
SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'
xmlns:ns1='urn:TMSWebServices'>
<xtvdResponse xsi:type='ns1:xtvdResponse'>
<messages xsi:type='ns1:messages'>
<message>Your subscription will expire: 2015-06-16T13:49:11Z</message>
</messages>
<xtvd from='2014-10-04T15:45:20Z' to='2014-10-04T15:45:50Z' schemaVersion='1.3' xmlns='urn:TMSWebServices' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xsi:schemaLocation='urn:TMSWebServices http://docs.tms.tribune.com/tech/xml/schemas/tmsxtvd.xsd'>
<stations>
<station id='10021'>
<callSign>AMC</callSign>
<name>AMC</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10035'>
<callSign>AETV</callSign>
<name>A&amp;E Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10057'>
<callSign>BRAVO</callSign>
<name>Bravo</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10093'>
<callSign>ABCF</callSign>
<name>ABC Family</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10138'>
<callSign>CMTV</callSign>
<name>Country Music Television</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10139'>
<callSign>CNBC</callSign>
<name>CNBC</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10142'>
<callSign>CNN</callSign>
<name>Cable News Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10145'>
<callSign>HLN</callSign>
<name>HLN</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10149'>
<callSign>COMEDY</callSign>
<name>Comedy Central</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10153'>
<callSign>TRUTV</callSign>
<name>truTV</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10161'>
<callSign>CSPAN</callSign>
<name>CSPAN</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10171'>
<callSign>DISN</callSign>
<name>Disney Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10179'>
<callSign>ESPN</callSign>
<name>ESPN</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='10183'>
<callSign>EWTN</callSign>
<name>Eternal Word Television Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10269'>
<callSign>HSN</callSign>
<name>HSN</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10404'>
<callSign>KDKA</callSign>
<name>KDKA</name>
<fccChannelNumber>2</fccChannelNumber>
<affiliate>CBS Affiliate</affiliate>
</station>
<station id='10918'>
<callSign>LIFE</callSign>
<name>Lifetime</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10986'>
<callSign>MTV</callSign>
<name>MTV - Music Television</name>
<affiliate>Satellite</affiliate>
</station>
<station id='10989'>
<callSign>E</callSign>
<name>E! Entertainment Television</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11006'>
<callSign>NIK</callSign>
<name>Nickelodeon</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11044'>
<callSign>PCN</callSign>
<name>Pennsylvania Cable Network</name>
<affiliate>Regional</affiliate>
</station>
<station id='11066'>
<callSign>INSP</callSign>
<name>INSP</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11069'>
<callSign>QVC</callSign>
<name>QVC</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11097'>
<callSign>SYFY</callSign>
<name>Syfy</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11150'>
<callSign>DSC</callSign>
<name>The Discovery Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11158'>
<callSign>TLC</callSign>
<name>The Learning Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11163'>
<callSign>SPIKETV</callSign>
<name>Spike TV</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11164'>
<callSign>TNT</callSign>
<name>Turner Network TV</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11180'>
<callSign>TRAV</callSign>
<name>The Travel Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11187'>
<callSign>WEATH</callSign>
<name>The Weather Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11207'>
<callSign>USA</callSign>
<name>USA Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11218'>
<callSign>VH1</callSign>
<name>VH1</name>
<affiliate>Satellite</affiliate>
</station>
<station id='11773'>
<callSign>WPCB</callSign>
<name>WPCB-TV 16</name>
<fccChannelNumber>40</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='11776'>
<callSign>WPGH</callSign>
<name>WPGH</name>
<fccChannelNumber>53</fccChannelNumber>
<affiliate>Fox Affiliate</affiliate>
</station>
<station id='11790'>
<callSign>WPMY</callSign>
<name>WPMY</name>
<fccChannelNumber>22</fccChannelNumber>
<affiliate>MyNetworkTV Affiliate</affiliate>
</station>
<station id='11800'>
<callSign>WQED</callSign>
<name>WQED</name>
<fccChannelNumber>13</fccChannelNumber>
<affiliate>PBS Affiliate</affiliate>
</station>
<station id='11801'>
<callSign>WINP</callSign>
<name>WINP</name>
<fccChannelNumber>16</fccChannelNumber>
<affiliate>ION Affiliate</affiliate>
</station>
<station id='11863'>
<callSign>WTAE</callSign>
<name>WTAE</name>
<fccChannelNumber>4</fccChannelNumber>
<affiliate>ABC Affiliate</affiliate>
</station>
<station id='11867'>
<callSign>TBS</callSign>
<name>Turner Broadcasting System</name>
<affiliate>Satellite</affiliate>
</station>
<station id='12125'>
<callSign>WPXI</callSign>
<name>WPXI</name>
<fccChannelNumber>11</fccChannelNumber>
<affiliate>NBC Affiliate</affiliate>
</station>
<station id='12131'>
<callSign>TOON</callSign>
<name>Cartoon Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='12444'>
<callSign>ESPN2</callSign>
<name>ESPN2</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='12574'>
<callSign>FOOD</callSign>
<name>Food Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='12852'>
<callSign>TCM</callSign>
<name>Turner Classic Movies</name>
<affiliate>Satellite</affiliate>
</station>
<station id='14321'>
<callSign>FX</callSign>
<name>FX</name>
<affiliate>Satellite</affiliate>
</station>
<station id='14771'>
<callSign>HISTORY</callSign>
<name>History</name>
<affiliate>Satellite</affiliate>
</station>
<station id='14902'>
<callSign>HGTV</callSign>
<name>Home &amp; Garden Television</name>
<affiliate>Satellite</affiliate>
</station>
<station id='14948'>
<callSign>SHOPHQ</callSign>
<name>ShopHQ</name>
<affiliate>Satellite</affiliate>
</station>
<station id='15749'>
<callSign>EDAC</callSign>
<name>Educational Access - EDAC</name>
<affiliate>Educational</affiliate>
</station>
<station id='16123'>
<callSign>TVLAND</callSign>
<name>TV Land</name>
<affiliate>Satellite</affiliate>
</station>
<station id='16300'>
<callSign>MSNBC</callSign>
<name>MSNBC</name>
<affiliate>Satellite</affiliate>
</station>
<station id='16331'>
<callSign>APL</callSign>
<name>Animal Planet</name>
<affiliate>Satellite</affiliate>
</station>
<station id='16356'>
<callSign>GRTV</callSign>
<name>Guthy-Renker TV - GRTV</name>
<affiliate>Satellite</affiliate>
</station>
<station id='16374'>
<callSign>FNC</callSign>
<name>Fox News Channel</name>
<affiliate>Satellite</affiliate>
</station>
<station id='16473'>
<callSign>PCNC</callSign>
<name>Pittsburgh Cable News Channel</name>
<affiliate>Cablecast</affiliate>
</station>
<station id='16491'>
<callSign>WPCW</callSign>
<name>WPCW</name>
<fccChannelNumber>19</fccChannelNumber>
<affiliate>CW Affiliate</affiliate>
</station>
<station id='16715'>
<callSign>TVGN</callSign>
<name>TV Guide Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='19615'>
<callSign>WTAEDT</callSign>
<name>WTAEDT (WTAE-DT)</name>
<fccChannelNumber>51</fccChannelNumber>
<affiliate>ABC Affiliate</affiliate>
</station>
<station id='20369'>
<callSign>WPXIDT</callSign>
<name>WPXIDT (WPXI-DT)</name>
<fccChannelNumber>48</fccChannelNumber>
<affiliate>NBC Affiliate</affiliate>
</station>
<station id='21248'>
<callSign>KDKADT</callSign>
<name>KDKADT (KDKA-DT)</name>
<fccChannelNumber>25</fccChannelNumber>
<affiliate>CBS Affiliate</affiliate>
</station>
<station id='21249'>
<callSign>WPGHDT</callSign>
<name>WPGHDT (WPGH-DT)</name>
<fccChannelNumber>43</fccChannelNumber>
<affiliate>Fox Affiliate</affiliate>
</station>
<station id='22164'>
<callSign>EDAC050</callSign>
<name>Educational Access - EDAC050</name>
<affiliate>Educational</affiliate>
</station>
<station id='26028'>
<callSign>RTNP</callSign>
<name>ROOT Sports Pittsburgh (Main Transponder</name>
<affiliate>Sports Regional</affiliate>
</station>
<station id='26385'>
<callSign>INFO069</callSign>
<name>Information Channel - INFO069</name>
<affiliate>Cablecast</affiliate>
</station>
<station id='28506'>
<callSign>AXSTV</callSign>
<name>AXS TV</name>
<affiliate>Satellite</affiliate>
</station>
<station id='30420'>
<callSign>NIKTON</callSign>
<name>Nicktoons Network</name>
<affiliate>Satellite</affiliate>
</station>
<station id='31046'>
<callSign>VEL</callSign>
<name>Velocity</name>
<affiliate>Satellite</affiliate>
</station>
<station id='32645'>
<callSign>ESPNHD</callSign>
<name>ESPNHD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='34555'>
<callSign>WQEDDT3</callSign>
<name>WQEDDT3 (WQED-DT3)</name>
<fccChannelNumber>13</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='34763'>
<callSign>UHD</callSign>
<name>Universal HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='42642'>
<callSign>TNTHD</callSign>
<name>Turner Network TV HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='44626'>
<callSign>DODNWS</callSign>
<name>DoD News</name>
<affiliate>Satellite</affiliate>
</station>
<station id='45399'>
<callSign>NFLHD</callSign>
<name>NFL Network HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='45507'>
<callSign>ESPN2HD</callSign>
<name>ESPN2 HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='46273'>
<callSign>WQEDDT2</callSign>
<name>WQEDDT2 (WQED-DT2)</name>
<fccChannelNumber>13</fccChannelNumber>
<affiliate>PBS Affiliate</affiliate>
</station>
<station id='46710'>
<callSign>HMMHD</callSign>
<name>Hallmark Movies &amp; Mysteries HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='46737'>
<callSign>OUTHD</callSign>
<name>Outdoor Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='46798'>
<callSign>WPXIDT2</callSign>
<name>WPXIDT2 (WPXI-DT2)</name>
<fccChannelNumber>48</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='48639'>
<callSign>NBCSNHD</callSign>
<name>NBCSN HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='49141'>
<callSign>PLDHD</callSign>
<name>PALLADIA</name>
<affiliate>Satellite</affiliate>
</station>
<station id='49438'>
<callSign>NGCHD</callSign>
<name>National Geographic Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='49788'>
<callSign>HGTVD</callSign>
<name>Home &amp; Garden Television HD (HGHD)</name>
<affiliate>Satellite</affiliate>
</station>
<station id='49882'>
<callSign>RTPHD</callSign>
<name>ROOT Sports Pittsburgh HD</name>
<affiliate>Sports Regional</affiliate>
</station>
<station id='50747'>
<callSign>FOODHD</callSign>
<name>Food Network HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='51529'>
<callSign>AETVHD</callSign>
<name>A&amp;E Network HD East</name>
<affiliate>Satellite</affiliate>
</station>
<station id='51809'>
<callSign>WQEDDT</callSign>
<name>WQEDDT (WQED-DT)</name>
<fccChannelNumber>13</fccChannelNumber>
<affiliate>PBS Affiliate</affiliate>
</station>
<station id='55776'>
<callSign>WTAEDT2</callSign>
<name>WTAEDT2 (WTAE-DT2)</name>
<fccChannelNumber>51</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='55887'>
<callSign>LMNHD</callSign>
<name>Lifetime Movie Network HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='56905'>
<callSign>DSCHD</callSign>
<name>The Discovery Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='57390'>
<callSign>SCIHD</callSign>
<name>Science Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='57391'>
<callSign>TLCHD</callSign>
<name>The Learning Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='57394'>
<callSign>APLHD</callSign>
<name>Animal Planet HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='57708'>
<callSign>HSTRYHD</callSign>
<name>History HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58452'>
<callSign>USAHD</callSign>
<name>USA Network HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58515'>
<callSign>TBSHD</callSign>
<name>TBS HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58530'>
<callSign>MGMHD</callSign>
<name>MGM HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58574'>
<callSign>FXHD</callSign>
<name>FX HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58623'>
<callSign>SYFYHD</callSign>
<name>Syfy HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58625'>
<callSign>BRAVOHD</callSign>
<name>Bravo HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58646'>
<callSign>CNNHD</callSign>
<name>CNN HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58690'>
<callSign>NHLHD</callSign>
<name>NHL Network HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='58718'>
<callSign>FBNHD</callSign>
<name>Fox Business HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58780'>
<callSign>CNBCHD</callSign>
<name>CNBC HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='58812'>
<callSign>WEATHHD</callSign>
<name>The Weather Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59186'>
<callSign>SPIKEHD</callSign>
<name>Spike TV HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59337'>
<callSign>AMCHD</callSign>
<name>AMC HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59432'>
<callSign>NIKHD</callSign>
<name>Nickelodeon HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59440'>
<callSign>CMTVHD</callSign>
<name>Country Music Television HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59615'>
<callSign>ABCFHD</callSign>
<name>ABC Family HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='59684'>
<callSign>DISNHD</callSign>
<name>Disney Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60046'>
<callSign>VH1HD</callSign>
<name>VH1 HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60048'>
<callSign>TOONHD</callSign>
<name>Cartoon Network HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60150'>
<callSign>LIFEHD</callSign>
<name>Lifetime HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60179'>
<callSign>FNCHD</callSign>
<name>Fox News Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60222'>
<callSign>QVCHD</callSign>
<name>QVC HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60468'>
<callSign>DESTHD</callSign>
<name>Destination America HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='60696'>
<callSign>ESPNUHD</callSign>
<name>ESPN University HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='60860'>
<callSign>WPCWCAB</callSign>
<name>WPCW HD Cable Feed</name>
<affiliate>Cablecast</affiliate>
</station>
<station id='60964'>
<callSign>MTVHD</callSign>
<name>MTV - Music Television HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='61812'>
<callSign>EHD</callSign>
<name>E! Entertainment Television HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='61854'>
<callSign>GOLFHD</callSign>
<name>The Golf Channel HD</name>
<affiliate>Sports Satellite</affiliate>
</station>
<station id='62077'>
<callSign>HSNHD</callSign>
<name>HSN HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='62420'>
<callSign>CCHD</callSign>
<name>Comedy Central HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='64020'>
<callSign>WPCWDT</callSign>
<name>WPCWDT (WPCW-DT)</name>
<fccChannelNumber>11</fccChannelNumber>
<affiliate>CW Affiliate</affiliate>
</station>
<station id='64241'>
<callSign>MNBCHD</callSign>
<name>MSNBC HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='64312'>
<callSign>TCMHD</callSign>
<name>Turner Classic Movies HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='65025'>
<callSign>NFLNRZD</callSign>
<name>NFL RedZone HD</name>
<affiliate>Cablecast</affiliate>
</station>
<station id='66268'>
<callSign>HALLHD</callSign>
<name>Hallmark Channel HD</name>
<affiliate>Satellite</affiliate>
</station>
<station id='32494'>
<callSign>WWCPDT</callSign>
<name>WWCPDT (WWCP-DT)</name>
<fccChannelNumber>8</fccChannelNumber>
<affiliate>Fox Affiliate</affiliate>
</station>
<station id='34712'>
<callSign>WFMJDT</callSign>
<name>WFMJDT (WFMJ-DT)</name>
<fccChannelNumber>20</fccChannelNumber>
<affiliate>NBC Affiliate</affiliate>
</station>
<station id='46027'>
<callSign>WPGHDT2</callSign>
<name>WPGHDT2 (WPGH-DT2)</name>
<fccChannelNumber>43</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='46264'>
<callSign>WFMJDT2</callSign>
<name>WFMJDT2 (WBCB)</name>
<fccChannelNumber>20</fccChannelNumber>
<affiliate>CW Affiliate</affiliate>
</station>
<station id='51535'>
<callSign>WKBNDT</callSign>
<name>WKBNDT (WKBN-DT)</name>
<fccChannelNumber>41</fccChannelNumber>
<affiliate>CBS Affiliate</affiliate>
</station>
<station id='51557'>
<callSign>WKBNDT2</callSign>
<name>WKBNDT2 (WKBN-DT2)</name>
<fccChannelNumber>41</fccChannelNumber>
<affiliate>Fox Affiliate</affiliate>
</station>
<station id='59264'>
<callSign>WWCPDT2</callSign>
<name>WWCPDT2 (WWCP-DT2)</name>
<fccChannelNumber>8</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
<station id='60617'>
<callSign>WKBNDT3</callSign>
<name>WKBNDT3 (WKBN-DT3)</name>
<fccChannelNumber>41</fccChannelNumber>
<affiliate>Independent</affiliate>
</station>
</stations>
<lineups>
<lineup id='PA37752:X' name='Armstrong' location='Zelienople' type='CableDigital' device='Digital' postalCode='16066'>
<map station='10021' channel='45' from='2000-11-30'/>
<map station='10035' channel='28' from='2000-11-30'/>
<map station='10057' channel='59' from='2008-01-07'/>
<map station='10093' channel='44' from='2004-07-01'/>
<map station='10138' channel='53' from='2000-11-30'/>
<map station='10139' channel='42' from='2000-11-30'/>
<map station='10142' channel='3' from='2000-11-30'/>
<map station='10145' channel='65' from='2003-06-30'/>
<map station='10149' channel='32' from='2000-11-30'/>
<map station='10153' channel='37' from='2000-11-30'/>
<map station='10161' channel='46' from='2000-11-30'/>
<map station='10171' channel='17' from='2001-05-21'/>
<map station='10179' channel='12' from='2000-11-30'/>
<map station='10183' channel='48' from='2001-09-10'/>
<map station='10269' channel='26' from='2003-06-30'/>
<map station='10404' channel='2' from='2000-11-30'/>
<map station='10918' channel='29' from='2000-11-30'/>
<map station='10986' channel='38' from='2000-11-30'/>
<map station='10989' channel='60' from='2000-11-30'/>
<map station='11006' channel='8' from='2000-11-30'/>
<map station='11044' channel='47' from='2003-01-24'/>
<map station='11066' channel='49' from='2004-07-01'/>
<map station='11069' channel='14' from='2006-11-14'/>
<map station='11097' channel='5' from='2008-01-07'/>
<map station='11150' channel='18' from='2000-11-30'/>
<map station='11158' channel='27' from='2000-11-30'/>
<map station='11163' channel='63' from='2004-07-01'/>
<map station='11164' channel='30' from='2000-11-30'/>
<map station='11180' channel='52' from='2000-11-30'/>
<map station='11187' channel='25' from='2000-11-30'/>
<map station='11207' channel='23' from='2000-11-30'/>
<map station='11218' channel='39' from='2000-11-30'/>
<map station='11773' channel='40' from='2000-11-30'/>
<map station='11776' channel='9' from='2001-05-29'/>
<map station='11790' channel='22' from='2000-11-30'/>
<map station='11800' channel='13' from='2000-11-30'/>
<map station='11801' channel='16' from='2004-07-01'/>
<map station='11863' channel='4' from='2000-11-30'/>
<map station='11867' channel='7' from='2000-11-30'/>
<map station='12125' channel='11' from='2000-11-30'/>
<map station='12131' channel='33' from='2000-11-30'/>
<map station='12444' channel='35' from='2004-07-01'/>
<map station='12574' channel='61' from='2000-11-30'/>
<map station='12852' channel='56' from='2000-11-30'/>
<map station='14321' channel='51' from='2001-09-10'/>
<map station='14771' channel='57' from='2000-11-30'/>
<map station='14902' channel='54' from='2000-11-30'/>
<map station='14948' channel='24' from='2004-07-01'/>
<map station='15749' channel='208' from='2007-12-13'/>
<map station='16011' channel='170' from='2009-03-12'/>
<map station='16123' channel='21' from='2000-11-30'/>
<map station='16300' channel='20' from='2000-11-30'/>
<map station='16331' channel='58' from='2000-11-30'/>
<map station='16356' channel='70' from='2004-07-08'/>
<map station='16374' channel='15' from='2004-07-01'/>
<map station='16473' channel='31' from='2000-11-30'/>
<map station='16491' channel='19' from='2000-11-30'/>
<map station='16715' channel='36' from='2006-11-14'/>
<map station='16715' channel='71' from='2004-07-01'/>
<map station='19615' channel='104' from='2003-03-18'/>
<map station='20369' channel='111' from='2003-03-18'/>
<map station='21248' channel='102' from='2003-03-18'/>
<map station='21249' channel='109' from='2005-02-02'/>
<map station='22164' channel='50' from='2000-11-30'/>
<map station='26028' channel='43' from='2005-11-17'/>
<map station='26385' channel='69' from='2001-06-18'/>
<map station='28506' channel='186' from='2003-11-13'/>
<map station='30420' channel='34' from='2004-07-01'/>
<map station='31046' channel='190' from='2007-12-26'/>
<map station='32645' channel='185' from='2003-11-13'/>
<map station='34555' channel='417' from='2007-08-08'/>
<map station='34763' channel='188' from='2006-01-17'/>
<map station='42642' channel='120' from='2004-09-28'/>
<map station='44626' channel='66' from='2005-03-09'/>
<map station='45399' channel='180' from='2005-07-22'/>
<map station='45507' channel='184' from='2007-09-06'/>
<map station='46273' channel='416' from='2009-03-12'/>
<map station='46710' channel='150' from='2008-12-16'/>
<map station='46737' channel='171' from='2008-02-06'/>
<map station='46798' channel='410' from='2009-05-11'/>
<map station='48639' channel='172' from='2009-01-13'/>
<map station='49141' channel='118' from='2006-12-29'/>
<map station='49438' channel='189' from='2007-06-20'/>
<map station='49788' channel='135' from='2008-06-02'/>
<map station='49882' channel='179' from='2007-02-28'/>
<map station='50747' channel='136' from='2008-06-02'/>
<map station='51529' channel='119' from='2007-02-28'/>
<map station='51809' channel='113' from='2007-10-23'/>
<map station='55776' channel='450' from='2008-04-20'/>
<map station='55887' channel='192' from='2010-03-09'/>
<map station='56905' channel='124' from='2007-11-29'/>
<map station='57390' channel='127' from='2007-12-13'/>
<map station='57391' channel='126' from='2007-11-29'/>
<map station='57394' channel='128' from='2007-12-13'/>
<map station='57708' channel='130' from='2007-12-13'/>
<map station='58452' channel='122' from='2008-01-24'/>
<map station='58508' channel='170' from='2010-01-20'/>
<map station='58515' channel='121' from='2007-10-29'/>
<map station='58530' channel='191' from='2008-03-13'/>
<map station='58574' channel='133' from='2008-04-23'/>
<map station='58623' channel='123' from='2008-01-24'/>
<map station='58625' channel='132' from='2008-02-06'/>
<map station='58646' channel='115' from='2008-01-24'/>
<map station='58690' channel='173' from='2008-12-04'/>
<map station='58718' channel='154' from='2010-07-29'/>
<map station='58780' channel='153' from='2010-03-09'/>
<map station='58812' channel='117' from='2008-12-16'/>
<map station='59186' channel='144' from='2010-07-29'/>
<map station='59337' channel='131' from='2008-01-15'/>
<map station='59432' channel='141' from='2010-07-29'/>
<map station='59440' channel='147' from='2010-09-30'/>
<map station='59615' channel='139' from='2009-07-09'/>
<map station='59684' channel='140' from='2008-12-16'/>
<map station='60046' channel='146' from='2010-09-30'/>
<map station='60048' channel='142' from='2009-07-09'/>
<map station='60150' channel='134' from='2009-04-09'/>
<map station='60179' channel='116' from='2008-10-23'/>
<map station='60222' channel='114' from='2009-01-13'/>
<map station='60468' channel='125' from='2010-01-20'/>
<map station='60696' channel='182' from='2010-01-20'/>
<map station='60860' channel='110' from='2008-12-04'/>
<map station='60964' channel='145' from='2010-07-29'/>
<map station='61812' channel='137' from='2010-01-20'/>
<map station='61854' channel='174' from='2009-01-13'/>
<map station='62077' channel='129' from='2010-07-29'/>
<map station='62420' channel='143' from='2010-07-29'/>
<map station='64020' channel='110' from='2010-11-04'/>
<map station='64241' channel='152' from='2010-03-09'/>
<map station='64312' channel='151' from='2010-01-20'/>
<map station='65025' channel='181' from='2010-09-30'/>
<map station='66268' channel='149' from='2010-03-09'/>
</lineup>
<lineup id='PC:16066' name='Local Broadcast Listings' location='Antenna' type='LocalBroadcast' postalCode='16066'>
<map station='20369' channel='11' channelMinor='1'/>
<map station='21248' channel='2' channelMinor='1'/>
<map station='21249' channel='53' channelMinor='1'/>
<map station='32494' channel='8' channelMinor='1'/>
<map station='34555' channel='13' channelMinor='3'/>
<map station='34712' channel='21' channelMinor='1'/>
<map station='46027' channel='53' channelMinor='2'/>
<map station='46264' channel='21' channelMinor='2'/>
<map station='46273' channel='13' channelMinor='2'/>
<map station='46798' channel='11' channelMinor='2'/>
<map station='51535' channel='27' channelMinor='1'/>
<map station='51557' channel='27' channelMinor='2'/>
<map station='51809' channel='13' channelMinor='1'/>
<map station='59264' channel='8' channelMinor='2'/>
<map station='60617' channel='27' channelMinor='3'/>
</lineup>
</lineups>
<schedules>
<schedule program='EP000186270068' station='10021' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP007537910100' station='10035' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' closeCaptioned='true'/>
<schedule program='EP015634100036' station='10057' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14'/>
<schedule program='MV000499840000' station='10093' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-14'/>
<schedule program='EP016704140052' station='10138' time='2014-10-04T15:00:00Z' duration='PT03H00M' tvRating='TV-PG' closeCaptioned='true' new='true'/>
<schedule program='SH017168400000' station='10139' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH000690190000' station='10142' time='2014-10-04T15:00:00Z' duration='PT01H00M' new='true'/>
<schedule program='SH017672160000' station='10145' time='2014-10-04T11:00:00Z' duration='PT05H00M'/>
<schedule program='MV002024230000' station='10149' time='2014-10-04T13:53:00Z' duration='PT02H00M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP010221680150' station='10153' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14'/>
<schedule program='SH020206330000' station='10161' time='2014-10-04T15:00:00Z' duration='PT00H55M' stereo='true'/>
<schedule program='MV003978370000' station='10171' time='2014-10-04T14:10:00Z' duration='PT01H50M' tvRating='TV-PG' stereo='true' closeCaptioned='true'/>
<schedule program='EP000369830148' station='10179' time='2014-10-04T13:00:00Z' duration='PT03H00M' closeCaptioned='true' new='true'/>
<schedule program='EP010213590057' station='10183' time='2014-10-04T13:30:00Z' duration='PT02H30M' new='true'/>
<schedule program='EP016314260005' station='10269' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-G' new='true'/>
<schedule program='SH003694920000' station='10404' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP010844040169' station='10918' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP013740110098' station='10986' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true'/>
<schedule program='EP006810660608' station='10989' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-14'/>
<schedule program='EP003077660516' station='11006' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y7' stereo='true' closeCaptioned='true'/>
<schedule program='SH011027320000' station='11044' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH010973990000' station='11066' time='2014-10-04T14:00:00Z' duration='PT02H00M' tvRating='TV-G'/>
<schedule program='EP012147960047' station='11069' time='2014-10-04T14:00:00Z' duration='PT04H00M' tvRating='TV-G' new='true'/>
<schedule program='MV002227280000' station='11097' time='2014-10-04T14:30:00Z' duration='PT02H00M' tvRating='TV-14'/>
<schedule program='EP015676680032' station='11150' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' closeCaptioned='true'/>
<schedule program='EP007973540336' station='11158' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' closeCaptioned='true'/>
<schedule program='EP014228840026' station='11163' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true'/>
<schedule program='MV002529780000' station='11164' time='2014-10-04T15:00:00Z' duration='PT02H45M' tvRating='TV-14' closeCaptioned='true'/>
<schedule program='EP008003660161' station='11180' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='SH006197570000' station='11187' time='2014-10-04T15:00:00Z' duration='PT03H00M' closeCaptioned='true' new='true'/>
<schedule program='EP006819110071' station='11207' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' closeCaptioned='true'/>
<schedule program='EP000037100886' station='11218' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' closeCaptioned='true'/>
<schedule program='SH006755370000' station='11773' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH000000010000' station='11776' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH019054090000' station='11790' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP017922990022' station='11800' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true'/>
<schedule program='EP004461730071' station='11801' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' closeCaptioned='true'/>
<schedule program='SH017746030000' station='11863' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true' ei='true'/>
<schedule program='MV002565500000' station='11867' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-PG'/>
<schedule program='EP006795090002' station='12125' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y' stereo='true' closeCaptioned='true' ei='true'/>
<schedule program='EP016164320036' station='12131' time='2014-10-04T15:45:00Z' duration='PT00H15M' tvRating='TV-PG'/>
<schedule program='SH000199170000' station='12444' time='2014-10-04T13:00:00Z' duration='PT03H00M' closeCaptioned='true' new='true'/>
<schedule program='EP018375220038' station='12574' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-G' new='true'/>
<schedule program='MV000043320000' station='12852' time='2014-10-04T14:30:00Z' duration='PT01H30M' closeCaptioned='true'/>
<schedule program='MV002709840000' station='14321' time='2014-10-04T15:00:00Z' duration='PT02H30M' tvRating='TV-14'/>
<schedule program='SH012025140000' station='14771' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-PG' stereo='true' closeCaptioned='true'/>
<schedule program='EP019542070004' station='14902' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' closeCaptioned='true'/>
<schedule program='EP018940630002' station='14948' time='2014-10-04T15:00:00Z' duration='PT01H00M'/>
<schedule program='SH000240640000' station='15749' time='2014-10-04T14:00:00Z' duration='PT04H00M'/>
<schedule program='EP013320550386' station='16123' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-PG' stereo='true' closeCaptioned='true'/>
<schedule program='EP015295260201' station='16300' time='2014-10-04T14:00:00Z' duration='PT02H00M' new='true'/>
<schedule program='EP011934460051' station='16331' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' closeCaptioned='true'/>
<schedule program='SH000000010000' station='16356' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH004460220000' station='16374' time='2014-10-04T15:30:00Z' duration='PT00H30M' closeCaptioned='true' new='true'/>
<schedule program='SH017950540000' station='16473' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP019771790001' station='16491' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true' new='true' ei='true'/>
<schedule program='SH011905870000' station='16715' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH017746030000' station='19615' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' hdtv='true' closeCaptioned='true' ei='true'/>
<schedule program='EP006795090002' station='20369' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y' stereo='true' hdtv='true' closeCaptioned='true' ei='true'/>
<schedule program='SH003694920000' station='21248' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH000000010000' station='21249' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH000240640000' station='22164' time='2014-10-04T14:00:00Z' duration='PT04H00M'/>
<schedule program='SH019776960000' station='26028' time='2014-10-04T15:00:00Z' duration='PT01H00M' new='true'/>
<schedule program='SH003722760000' station='26385' time='2014-10-04T14:00:00Z' duration='PT04H00M'/>
<schedule program='EP018098690023' station='28506' time='2014-10-04T15:30:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' hdtv='true' closeCaptioned='true' dolby='Dolby'/>
<schedule program='EP014763920018' station='30420' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y7' stereo='true' closeCaptioned='true'/>
<schedule program='EP015291080031' station='31046' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='SH000000010000' station='32494' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP000369830148' station='32645' time='2014-10-04T13:00:00Z' duration='PT03H00M' hdtv='true' closeCaptioned='true' new='true'/>
<schedule program='SH010964760000' station='34555' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-G' stereo='true' closeCaptioned='true'/>
<schedule program='EP006795090002' station='34712' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y' stereo='true' hdtv='true' closeCaptioned='true' ei='true'/>
<schedule program='EP015213560075' station='34763' time='2014-10-04T15:00:00Z' duration='PT01H30M' hdtv='true'/>
<schedule program='MV002529780000' station='42642' time='2014-10-04T15:00:00Z' duration='PT02H45M' tvRating='TV-14' hdtv='true' closeCaptioned='true'/>
<schedule program='SH015774170000' station='44626' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP006186160177' station='45399' time='2014-10-04T15:00:00Z' duration='PT01H00M' stereo='true' hdtv='true'/>
<schedule program='SH000199170000' station='45507' time='2014-10-04T13:00:00Z' duration='PT03H00M' hdtv='true' closeCaptioned='true' new='true'/>
<schedule program='MV000208930000' station='46027' time='2014-10-04T14:20:00Z' duration='PT01H40M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP019771790001' station='46264' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true' dolby='Dolby' new='true' ei='true'/>
<schedule program='EP015507510006' station='46273' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y' stereo='true' closeCaptioned='true' ei='true'/>
<schedule program='MV001393750000' station='46710' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-14' hdtv='true' closeCaptioned='true'/>
<schedule program='EP019466180001' station='46737' time='2014-10-04T15:30:00Z' duration='PT00H30M' hdtv='true'/>
<schedule program='EP000011610024' station='46798' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG'/>
<schedule program='EP005212625900' station='48639' time='2014-10-04T14:00:00Z' duration='PT02H00M' stereo='true' hdtv='true' new='true'/>
<schedule program='SH019795240000' station='49141' time='2014-10-04T14:00:00Z' duration='PT02H00M' tvRating='TV-14' hdtv='true'/>
<schedule program='SH010524820000' station='49438' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' hdtv='true'/>
<schedule program='EP019542070004' station='49788' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' hdtv='true' closeCaptioned='true'/>
<schedule program='SH019776960000' station='49882' time='2014-10-04T15:00:00Z' duration='PT01H00M' new='true'/>
<schedule program='EP018375220038' station='50747' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-G' hdtv='true' new='true'/>
<schedule program='EP007537910100' station='51529' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP017729720028' station='51535' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' hdtv='true' closeCaptioned='true' new='true' ei='true'/>
<schedule program='SH000000010000' station='51557' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='EP017922990022' station='51809' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true'/>
<schedule program='MV000239930000' station='55776' time='2014-10-04T14:00:00Z' duration='PT02H00M' tvRating='TV-G' closeCaptioned='true'/>
<schedule program='MV000381640000' station='55887' time='2014-10-04T14:00:00Z' duration='PT02H00M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP015676680032' station='56905' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP017719770015' station='57390' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP007973540336' station='57391' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP011934460051' station='57394' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='SH012025140000' station='57708' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP006819110071' station='58452' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='MV002565500000' station='58515' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-PG' hdtv='true'/>
<schedule program='MV000247890000' station='58530' time='2014-10-04T14:25:00Z' duration='PT02H20M' hdtv='true' closeCaptioned='true'/>
<schedule program='MV002709840000' station='58574' time='2014-10-04T15:00:00Z' duration='PT02H30M' tvRating='TV-14' hdtv='true'/>
<schedule program='MV002227280000' station='58623' time='2014-10-04T14:30:00Z' duration='PT02H00M' tvRating='TV-14' hdtv='true'/>
<schedule program='EP015634100036' station='58625' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' hdtv='true'/>
<schedule program='SH000690190000' station='58646' time='2014-10-04T15:00:00Z' duration='PT01H00M' hdtv='true' new='true'/>
<schedule program='EP014984720076' station='58690' time='2014-10-04T15:00:00Z' duration='PT01H00M' hdtv='true'/>
<schedule program='SH018595590000' station='58718' time='2014-10-04T15:30:00Z' duration='PT00H30M' hdtv='true'/>
<schedule program='SH017168400000' station='58780' time='2014-10-04T15:30:00Z' duration='PT00H30M'/>
<schedule program='SH006197570000' station='58812' time='2014-10-04T15:00:00Z' duration='PT03H00M' closeCaptioned='true' new='true'/>
<schedule program='EP014228840026' station='59186' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true'/>
<schedule program='SH014417700000' station='59264' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' closeCaptioned='true' ei='true'/>
<schedule program='EP000186270068' station='59337' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='EP003077660516' station='59432' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-Y7' stereo='true' closeCaptioned='true'/>
<schedule program='EP016704140052' station='59440' time='2014-10-04T15:00:00Z' duration='PT03H00M' tvRating='TV-PG' hdtv='true' closeCaptioned='true' new='true'/>
<schedule program='MV000499840000' station='59615' time='2014-10-04T15:00:00Z' duration='PT02H00M' tvRating='TV-14' hdtv='true'/>
<schedule program='MV003978370000' station='59684' time='2014-10-04T14:10:00Z' duration='PT01H50M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP000037100886' station='60046' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-14' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='EP016164320036' station='60048' time='2014-10-04T15:45:00Z' duration='PT00H15M' tvRating='TV-PG' hdtv='true'/>
<schedule program='EP010844040169' station='60150' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' closeCaptioned='true'/>
<schedule program='SH004460220000' station='60179' time='2014-10-04T15:30:00Z' duration='PT00H30M' hdtv='true' closeCaptioned='true' new='true'/>
<schedule program='EP012147960047' station='60222' time='2014-10-04T14:00:00Z' duration='PT04H00M' tvRating='TV-G' hdtv='true' new='true'/>
<schedule program='EP019871170002' station='60468' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true' closeCaptioned='true'/>
<schedule program='SH000191120000' station='60617' time='2014-10-04T10:00:00Z' duration='PT08H00M'/>
<schedule program='SH019855630000' station='60696' time='2014-10-04T15:00:00Z' duration='PT01H00M' hdtv='true' new='true'/>
<schedule program='EP019771790001' station='60860' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' hdtv='true' closeCaptioned='true' dolby='Dolby' new='true' ei='true'/>
<schedule program='EP013740110098' station='60964' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-PG' stereo='true' hdtv='true'/>
<schedule program='EP006810660608' station='61812' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-14' hdtv='true'/>
<schedule program='EP005544752374' station='61854' time='2014-10-04T12:00:00Z' duration='PT04H00M' hdtv='true' new='true'/>
<schedule program='EP016314260005' station='62077' time='2014-10-04T15:00:00Z' duration='PT01H00M' tvRating='TV-G' hdtv='true' new='true'/>
<schedule program='MV002024230000' station='62420' time='2014-10-04T13:53:00Z' duration='PT02H00M' tvRating='TV-PG' hdtv='true' closeCaptioned='true'/>
<schedule program='EP019771790001' station='64020' time='2014-10-04T15:30:00Z' duration='PT00H30M' tvRating='TV-G' stereo='true' hdtv='true' closeCaptioned='true' dolby='Dolby' new='true' ei='true'/>
<schedule program='EP015295260201' station='64241' time='2014-10-04T14:00:00Z' duration='PT02H00M' hdtv='true' new='true'/>
<schedule program='MV000043320000' station='64312' time='2014-10-04T14:30:00Z' duration='PT01H30M' closeCaptioned='true'/>
<schedule program='SH011840760000' station='65025' time='2014-10-04T14:00:00Z' duration='PT02H00M' hdtv='true'/>
<schedule program='MV005479230000' station='66268' time='2014-10-04T14:00:00Z' duration='PT02H00M' tvRating='TV-G' hdtv='true' closeCaptioned='true'/>
</schedules>
<programs>
<program id='EP000011610024'>
<title>Daniel Boone</title>
<subtitle>The Far Side of Fury</subtitle>
<description>Believing his son dead, Gideon takes revenge on Boone by stealing Israel.</description>
<showType>Series</showType>
<series>EP00001161</series>
<syndicatedEpisodeNumber>1424</syndicatedEpisodeNumber>
<originalAirDate>1968-03-07</originalAirDate>
</program>
<program id='EP000037100886'>
<title>Saturday Night Live</title>
<description>Host Tina Fey; Arcade Fire performs.</description>
<showType>Series</showType>
<series>EP00003710</series>
<originalAirDate>2013-09-28</originalAirDate>
</program>
<program id='EP000186270068'>
<title>The Rifleman</title>
<subtitle>The Prisoner</subtitle>
<description>A former POW imprisons Lucas for his role in the Civil War.</description>
<showType>Series</showType>
<series>EP00018627</series>
<colorCode>B &amp; W</colorCode>
<syndicatedEpisodeNumber>3565</syndicatedEpisodeNumber>
<originalAirDate>1961-03-14</originalAirDate>
</program>
<program id='EP000369830148'>
<title>College GameDay</title>
<description>From Oxford, Miss.</description>
<showType>Series</showType>
<series>EP00036983</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP003077660516'>
<title>SpongeBob SquarePants</title>
<subtitle>Ghoul Fools</subtitle>
<description>SpongeBob and Patrick get caught in the feud between a crew of ghost pirates and the Flying Dutchman.</description>
<showType>Series</showType>
<series>EP00307766</series>
<syndicatedEpisodeNumber>162</syndicatedEpisodeNumber>
<originalAirDate>2011-10-21</originalAirDate>
</program>
<program id='EP004461730071'>
<title>Law &amp; Order: Criminal Intent</title>
<subtitle>The Posthumous Collection</subtitle>
<description>An avante garde photographer is found murdered and handcuffed to the wheel of a crashed car, prompting an investigation into his secretive and controversial life.</description>
<showType>Series</showType>
<series>EP00446173</series>
<syndicatedEpisodeNumber>E5441</syndicatedEpisodeNumber>
<originalAirDate>2004-10-03</originalAirDate>
</program>
<program id='EP005212625900'>
<title>English Premier League Soccer</title>
<subtitle>Liverpool FC vs. West Bromwich Albion FC</subtitle>
<description>Liverpool (7 pts), coming off a draw match against Everton, takes on West Brom (8 pts.), who recently defeated Burnley 4-0.</description>
<showType>Series</showType>
<series>EP00521262</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP005544752374'>
<title>European PGA Tour Golf</title>
<subtitle>Alfred Dunhill Links Championship, Third Round</subtitle>
<description>Players expected to compete include Rory McIlroy, Martin Kaymer, Victor Dubuisson, Ernie Els, Colin Montgomerie, Nick Faldo, Paul McGinley. From St. Andrews, Scotland.</description>
<showType>Series</showType>
<series>EP00554475</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP006186160177'>
<title>Playbook</title>
<subtitle>Week 5</subtitle>
<description>The X&apos;s and O&apos;s, expert analysis that will answer who will win and why in the week 5 NFL matchups.</description>
<showType>Series</showType>
<series>EP00618616</series>
<originalAirDate>2014-10-03</originalAirDate>
</program>
<program id='EP006795090002'>
<title>LazyTown</title>
<subtitle>Welcome to LazyTown</subtitle>
<description>Stephanie meets new friends while staying with her uncle for the summer.</description>
<showType>Series</showType>
<series>EP00679509</series>
<syndicatedEpisodeNumber>106</syndicatedEpisodeNumber>
<originalAirDate>2004-08-16</originalAirDate>
</program>
<program id='EP006810660608'>
<title>The Soup</title>
<subtitle>Wendy Mclendon-Covey</subtitle>
<description>With Actor Wendi McLendon-Covey.</description>
<showType>Series</showType>
<series>EP00681066</series>
<syndicatedEpisodeNumber>1140</syndicatedEpisodeNumber>
<originalAirDate>2014-10-01</originalAirDate>
</program>
<program id='EP006819110071'>
<title>NCIS</title>
<subtitle>Sandblast</subtitle>
<description>Gibbs&apos; team works with the Army Criminal Investigative Unit to investigate a suspected terrorist attack that killed a Marine colonel at a military country club.</description>
<showType>Series</showType>
<series>EP00681911</series>
<syndicatedEpisodeNumber>407</syndicatedEpisodeNumber>
<originalAirDate>2006-11-07</originalAirDate>
</program>
<program id='EP007537910100'>
<title>Criminal Minds</title>
<subtitle>The Eyes Have It</subtitle>
<description>The team tracks a serial killer who keeps his victims&apos; eyes as souvenirs.</description>
<showType>Series</showType>
<series>EP00753791</series>
<syndicatedEpisodeNumber>506</syndicatedEpisodeNumber>
<originalAirDate>2009-11-04</originalAirDate>
</program>
<program id='EP007973540336'>
<title>Little People, Big World</title>
<subtitle>Don&apos;t Rain on Our Parade</subtitle>
<description>Matt and Amy invest in an elaborate float hoping to bring in business this pumpkin season; Jeremy and Audrey are knee deep in wedding preparations.</description>
<showType>Series</showType>
<series>EP00797354</series>
<syndicatedEpisodeNumber>804</syndicatedEpisodeNumber>
<originalAirDate>2014-09-16</originalAirDate>
</program>
<program id='EP008003660161'>
<title>Anthony Bourdain: No Reservations</title>
<subtitle>Cuba</subtitle>
<description>In a stadium filled with excited fans, Tony experiences baseball through the eyes of the Cuban spectator; Tony visits Robert Salas, who shows him some incredible pictures of Castro and the revolution.</description>
<showType>Series</showType>
<series>EP00800366</series>
<syndicatedEpisodeNumber>706</syndicatedEpisodeNumber>
<originalAirDate>2011-07-11</originalAirDate>
</program>
<program id='EP010213590057'>
<title>Cathedrals Across America</title>
<subtitle>Beatification of Miriam Teresa Demjanovich</subtitle>
<description>Live from the Cathedral Basilica of the Sacred Heart in Newark, NJ.</description>
<showType>Special</showType>
<series>EP01021359</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP010221680150'>
<title>World&apos;s Dumbest ...</title>
<subtitle>World&apos;s Dumbest Thrillseekers 5</subtitle>
<description>A hung over hang glider; BMX klutzes; commentary from Tony Harding, Danny Bonaduce and Daniel Baldwin.</description>
<showType>Series</showType>
<series>EP01022168</series>
<syndicatedEpisodeNumber>1301</syndicatedEpisodeNumber>
<originalAirDate>2012-02-09</originalAirDate>
</program>
<program id='EP010844040169'>
<title>Unsolved Mysteries</title>
<description>New evidence suggests that more than one gunman was present when Robert F. Kennedy was assassinated; a woman searches for her two younger brothers.</description>
<showType>Series</showType>
<series>EP01084404</series>
<syndicatedEpisodeNumber>169</syndicatedEpisodeNumber>
<originalAirDate>2010-10-20</originalAirDate>
</program>
<program id='EP011934460051'>
<title>Pit Bulls and Parolees</title>
<subtitle>Battle Scars</subtitle>
<description>Team races into the city searching for a dog hit by a car; hopes are pinned on a cop adopting with kennels at full capacity.</description>
<showType>Series</showType>
<series>EP01193446</series>
<syndicatedEpisodeNumber>505</syndicatedEpisodeNumber>
<originalAirDate>2014-01-25</originalAirDate>
</program>
<program id='EP012147960047'>
<title>Saturday Morning Q</title>
<subtitle>Serta</subtitle>
<description>Featuring products by Serta.</description>
<showType>Series</showType>
<series>EP01214796</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP013320550386'>
<title>Family Feud</title>
<showType>Series</showType>
<series>EP01332055</series>
<syndicatedEpisodeNumber>FF12020</syndicatedEpisodeNumber>
<originalAirDate>2012-09-17</originalAirDate>
</program>
<program id='EP013740110098'>
<title>Teen Mom 2</title>
<subtitle>Cabin Fever</subtitle>
<description>Jenelle and Barbara clash over Jace&apos;s behavioral difficulties; Kailyn tries to get the children ready for Javi&apos;s return; Leah takes Corey to court; Chelsea learns of Adam&apos;s new girlfriend.</description>
<showType>Series</showType>
<series>EP01374011</series>
<syndicatedEpisodeNumber>521</syndicatedEpisodeNumber>
<originalAirDate>2014-09-03</originalAirDate>
</program>
<program id='EP014228840026'>
<title>Bar Rescue</title>
<subtitle>Empty Pockets</subtitle>
<description>Jon tries to help an owner of a Denver pool hall fulfill his American Dream.</description>
<showType>Series</showType>
<series>EP01422884</series>
<syndicatedEpisodeNumber>305</syndicatedEpisodeNumber>
<originalAirDate>2013-03-10</originalAirDate>
</program>
<program id='EP014763920018'>
<title>Kung Fu Panda: Legends of Awesomeness</title>
<subtitle>Big Bro Po</subtitle>
<description>Po invites Mr. Ping to stay at the Jade Palace.</description>
<showType>Series</showType>
<series>EP01476392</series>
<syndicatedEpisodeNumber>118</syndicatedEpisodeNumber>
<originalAirDate>2011-12-02</originalAirDate>
</program>
<program id='EP014984720076'>
<title>NHL Tonight</title>
<subtitle>2014-15 Season Preview</subtitle>
<showType>Series</showType>
<series>EP01498472</series>
<originalAirDate>2014-10-03</originalAirDate>
</program>
<program id='EP015213560075'>
<title>Red Bull Signature Series</title>
<subtitle>Joyride</subtitle>
<description>From Whistler, B.C.</description>
<showType>Series</showType>
<series>EP01521356</series>
<originalAirDate>2014-09-28</originalAirDate>
</program>
<program id='EP015291080031'>
<title>All Girls Garage</title>
<subtitle>Baja Style Buggies</subtitle>
<description>The women get the opportunity to work on some modified VW off-road Baja-style buggies.</description>
<showType>Series</showType>
<series>EP01529108</series>
<syndicatedEpisodeNumber>305</syndicatedEpisodeNumber>
<originalAirDate>2014-05-02</originalAirDate>
</program>
<program id='EP015295260201'>
<title>Melissa Harris-Perry</title>
<showType>Series</showType>
<series>EP01529526</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP015507510006'>
<title>Daniel Tiger&apos;s Neighborhood</title>
<subtitle>Daniel and Miss Elaina Play Rocketship; Daniel Plays at the Castle</subtitle>
<description>Daniel and Miss Elaine play outer space; Daniel is sad when Prince Wednesday tells him his rock collection is too delicate to play with.</description>
<showType>Series</showType>
<series>EP01550751</series>
<syndicatedEpisodeNumber>106</syndicatedEpisodeNumber>
<originalAirDate>2012-09-07</originalAirDate>
</program>
<program id='EP015634100036'>
<title>Million Dollar Listing: Los Angeles</title>
<subtitle>Hard Cold Cash</subtitle>
<description>Josh Altman&apos;s client goes ballistic during a negotiation; rapper Tyga checks out David and James&apos; bachelor pad in the Hollywood Hills; Josh Flagg goes back in time to sell a 1919 Beverly Hills tear-down that cannot be torn down.</description>
<showType>Series</showType>
<series>EP01563410</series>
<syndicatedEpisodeNumber>706</syndicatedEpisodeNumber>
<originalAirDate>2014-09-24</originalAirDate>
</program>
<program id='EP015676680032'>
<title>Fast N&apos; Loud</title>
<subtitle>No Bull Bonneville</subtitle>
<description>The crew is given 72 hours to fix a &apos;59 Bonneville.</description>
<showType>Series</showType>
<series>EP01567668</series>
<syndicatedEpisodeNumber>23</syndicatedEpisodeNumber>
<originalAirDate>2013-06-24</originalAirDate>
</program>
<program id='EP016164320036'>
<title>Steven Universe</title>
<subtitle>Ocean Gem</subtitle>
<description>The inhabitants of Beach City panic when the ocean disappears on the first day of summer.</description>
<showType>Series</showType>
<series>EP01616432</series>
<syndicatedEpisodeNumber>26</syndicatedEpisodeNumber>
<originalAirDate>2014-09-25</originalAirDate>
</program>
<program id='EP016314260005'>
<title>Randy Jackson Guitar Collection</title>
<subtitle>2nd Anniversary Featuring Studio Series Guitar Premiere</subtitle>
<showType>Series</showType>
<series>EP01631426</series>
<syndicatedEpisodeNumber>1100</syndicatedEpisodeNumber>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP016704140052'>
<title>Hot 20 Countdown</title>
<subtitle>From the iHeart Radio Music Festival in Las Vegas</subtitle>
<description>The 20 best videos of the week and the latest in country music news from the iHeart Radio Music Festival in Las Vegas; interviews and performances from Taylor Swift, Eric Church, Zac Brown Band, and Kacey Musgraves.</description>
<showType>Series</showType>
<series>EP01670414</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP017719770015'>
<title>The Unexplained Files</title>
<subtitle>Curse of Flannan Lighthouse and Aleshenka: Russian Mummy</subtitle>
<description>Three people go missing from a tiny lighthouse island; a mummified alien baby in Russia.</description>
<showType>Series</showType>
<series>EP01771977</series>
<syndicatedEpisodeNumber>204</syndicatedEpisodeNumber>
<originalAirDate>2014-08-19</originalAirDate>
</program>
<program id='EP017729720028'>
<title>Game Changers With Kevin Frazier</title>
<subtitle>Flash Point</subtitle>
<description>A high-tech photo shoot with professional basketball player Damian Lillard; soccer player Omar Gonzalez; NFL star Matt Hasselbeck.</description>
<showType>Series</showType>
<series>EP01772972</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP017922990022'>
<title>Lidia&apos;s Kitchen</title>
<subtitle>Chicken Three Ways</subtitle>
<description>Poached chicken breast salad; shells with zucchini and chicken; chicken breasts with orange and Gaeta olives.</description>
<showType>Series</showType>
<series>EP01792299</series>
<syndicatedEpisodeNumber>122</syndicatedEpisodeNumber>
<originalAirDate>2014-03-01</originalAirDate>
</program>
<program id='EP018098690023'>
<title>The Big Interview</title>
<subtitle>Gene Simmons</subtitle>
<description>Gene Simmons discusses marketing and media relations.</description>
<showType>Series</showType>
<series>EP01809869</series>
<syndicatedEpisodeNumber>218</syndicatedEpisodeNumber>
<originalAirDate>2014-09-30</originalAirDate>
</program>
<program id='EP018375220038'>
<title>The Kitchen</title>
<subtitle>Grown-Up Comfort Food</subtitle>
<description>Apple butter-braised pork chops; red wine braised short ribs; baked BLT mac and cheese and stovetop mac and cheese with mushrooms and thyme; Laura Vitale whips up Italian cannoli.</description>
<showType>Series</showType>
<series>EP01837522</series>
<syndicatedEpisodeNumber>KC0312</syndicatedEpisodeNumber>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP018940630002'>
<title>Labradorite Gemstone Jewelry</title>
<subtitle>World Jewelry Show: HK 2014</subtitle>
<showType>Series</showType>
<series>EP01894063</series>
<originalAirDate>2014-10-03</originalAirDate>
</program>
<program id='EP019466180001'>
<title>Raised Hunting</title>
<subtitle>Proud</subtitle>
<showType>Series</showType>
<series>EP01946618</series>
<originalAirDate>2014-06-30</originalAirDate>
</program>
<program id='EP019542070004'>
<title>My Big Family Renovation</title>
<subtitle>Industrial Farmhouse Kitchen</subtitle>
<description>Tired of the makeshift outdoor kitchen, the family prepares to add the kitchen to the house, embracing product combinations in the design.</description>
<showType>Series</showType>
<series>EP01954207</series>
<syndicatedEpisodeNumber>104</syndicatedEpisodeNumber>
<originalAirDate>2014-08-14</originalAirDate>
</program>
<program id='EP019771790001'>
<title>Reluctantly Healthy</title>
<subtitle>Hula Hoops, Hot Yoga and Chocolate</subtitle>
<description>In search of a healthier lifestyle, Judy trains with a hula hoop, prepares maple-mustard dressing, practices hot yoga and learns about the health benefits of chocolate.</description>
<showType>Series</showType>
<series>EP01977179</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
<program id='EP019871170002'>
<title>Building Log Homes</title>
<subtitle>Gone Fishing</subtitle>
<description>Beat&apos;s Arkansas house build is jeopardized when delivery trucks arrive out of order; Bryan Jr. remodels a local bar; Peter solves a work yard problem.</description>
<showType>Series</showType>
<series>EP01987117</series>
<syndicatedEpisodeNumber>2</syndicatedEpisodeNumber>
<originalAirDate>2014-09-17</originalAirDate>
</program>
<program id='MV000043320000'>
<title>Dr. Kildare&apos;s Crisis</title>
<description>Dr. Gillespie (Lionel Barrymore) corrects Kildare&apos;s (Lew Ayres) diagnosis of nurse Lamont&apos;s brother&apos;s (Robert Young) head problem.</description>
<mpaaRating>NR</mpaaRating>
<starRating>**</starRating>
<runTime>PT01H15M</runTime>
<year>1940</year>
<colorCode>B &amp; W</colorCode>
</program>
<program id='MV000208930000'>
<title>New Orleans Uncensored</title>
<description>A Navy veteran (Arthur Franz) works with the police to trap a waterfront racketeer.</description>
<mpaaRating>NR</mpaaRating>
<starRating>*+</starRating>
<runTime>PT01H16M</runTime>
<year>1955</year>
<colorCode>B &amp; W</colorCode>
</program>
<program id='MV000239930000'>
<title>Puss in Boots</title>
<description>A miller&apos;s son (Jason Connery) leaves home with a cat which can change into a man (Christopher Walken) of the world.</description>
<mpaaRating>G</mpaaRating>
<starRating>**+</starRating>
<runTime>PT01H36M</runTime>
<year>1988</year>
</program>
<program id='MV000247890000'>
<title>Colors</title>
<description>A veteran policeman (Robert Duvall) and his rookie partner (Sean Penn) fight Los Angeles street gangs.</description>
<mpaaRating>R</mpaaRating>
<starRating>***</starRating>
<runTime>PT02H00M</runTime>
<year>1988</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Language</advisory>
<advisory>Nudity</advisory>
<advisory>Violence</advisory>
</advisories>
</program>
<program id='MV000381640000'>
<title>Cries Unheard: The Donna Yaklich Story</title>
<description>An imprisoned Colorado woman (Jaclyn Smith) must tell her teenage son (David Lascher) why she hired two men to kill his father (Brad Johnson).</description>
<mpaaRating>NR</mpaaRating>
<runTime>PT01H36M</runTime>
<year>1994</year>
</program>
<program id='MV000499840000'>
<title>Liar Liar</title>
<description>A boy&apos;s birthday wish comes true that his neglectful father (Jim Carrey), a fast-talking lawyer, will not be able to tell a lie for 24 hours.</description>
<mpaaRating>PG-13</mpaaRating>
<starRating>**+</starRating>
<runTime>PT01H27M</runTime>
<year>1997</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Language</advisory>
</advisories>
</program>
<program id='MV001393750000'>
<title>Twelve Mile Road</title>
<description>A divorced farmer (Tom Selleck) deals with the unexpected arrival of his troubled daughter (Maggie Grace).</description>
<mpaaRating>NR</mpaaRating>
<runTime>PT01H36M</runTime>
<year>2003</year>
</program>
<program id='MV002024230000'>
<title>First Sunday</title>
<description>Bumbling thieves (Ice Cube, Tracy Morgan) decide to rob a church to raise some much-needed cash, but they discover that someone else has already beaten them to the punch.</description>
<mpaaRating>PG-13</mpaaRating>
<starRating>**</starRating>
<runTime>PT01H38M</runTime>
<year>2008</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Language</advisory>
</advisories>
</program>
<program id='MV002227280000'>
<title>Swamp Devil</title>
<description>A mysterious, swamp-dwelling creature terrorizes small-town Southerners.</description>
<mpaaRating>NR</mpaaRating>
<starRating>**</starRating>
<runTime>PT01H30M</runTime>
<year>2008</year>
<advisories>
<advisory>Adult Situations</advisory>
</advisories>
</program>
<program id='MV002529780000'>
<title>Sherlock Holmes</title>
<description>The resourceful detective (Robert Downey Jr.) and his astute partner, Dr. Watson (Jude Law), meet a powerful criminal, a devotee of black magic who arises from his grave.</description>
<mpaaRating>PG-13</mpaaRating>
<starRating>**+</starRating>
<runTime>PT02H08M</runTime>
<year>2009</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Violence</advisory>
</advisories>
</program>
<program id='MV002565500000'>
<title>The Spy Next Door</title>
<description>A CIA operative (Jackie Chan) must protect his girlfriend&apos;s children from a Russian terrorist after one kid mistakenly downloads a top-secret formula.</description>
<mpaaRating>PG</mpaaRating>
<starRating>*+</starRating>
<runTime>PT01H32M</runTime>
<year>2010</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Violence</advisory>
</advisories>
</program>
<program id='MV002709840000'>
<title>Knight and Day</title>
<description>A woman (Cameron Diaz) gets ensnared in a deadly, global adventure when she becomes the reluctant partner of a fugitive spy (Tom Cruise).</description>
<mpaaRating>PG-13</mpaaRating>
<starRating>**+</starRating>
<runTime>PT01H49M</runTime>
<year>2010</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Language</advisory>
<advisory>Violence</advisory>
</advisories>
</program>
<program id='MV003978370000'>
<title>Wreck-It Ralph</title>
<description>After years of losing to his adversary (Jack McBrayer), an arcade-game character (John C. Reilly) grows tired of always being the bad guy and takes matters into his own hands to finally become a hero. Animated.</description>
<mpaaRating>PG</mpaaRating>
<starRating>***+</starRating>
<runTime>PT01H41M</runTime>
<year>2012</year>
<advisories>
<advisory>Adult Situations</advisory>
<advisory>Mild Violence</advisory>
</advisories>
</program>
<program id='MV005479230000'>
<title>A Lesson in Romance</title>
<description>Hoping to keep her family together, a woman (Kristy Swanson) takes college classes with her husband (Scott Grimes) and children.</description>
<mpaaRating>NR</mpaaRating>
<runTime>PT01H30M</runTime>
<year>2014</year>
</program>
<program id='SH000000010000'>
<title>Paid Programming</title>
<description>Paid programming.</description>
<showType>Paid Programming</showType>
<series>EP00000001</series>
</program>
<program id='SH000191120000'>
<title>SIGN OFF</title>
<showType>Special</showType>
<series>EP00019112</series>
</program>
<program id='SH000199170000'>
<title>SportsCenter</title>
<description>ESPN&apos;s flagship program provides sports news, highlights and analysis.</description>
<showType>Series</showType>
<series>EP00019917</series>
<originalAirDate>1979-09-07</originalAirDate>
</program>
<program id='SH000240640000'>
<title>Educational Access</title>
<showType>Series</showType>
<series>EP00024064</series>
<originalAirDate>2000-01-01</originalAirDate>
</program>
<program id='SH000690190000'>
<title>CNN Newsroom</title>
<description>Latest on the day&apos;s top news stories with a focus on global news, trends and destinations.</description>
<showType>Series</showType>
<series>EP00069019</series>
<originalAirDate>2006-11-07</originalAirDate>
</program>
<program id='SH003694920000'>
<title>Hometown High Q</title>
<description>Academic quiz show.</description>
<showType>Series</showType>
<series>EP00369492</series>
<originalAirDate>2000-03-18</originalAirDate>
</program>
<program id='SH003722760000'>
<title>Information Channel</title>
<description>Instructions on how to order pay per view and how to use your epg.</description>
<showType>Series</showType>
<series>EP00372276</series>
<originalAirDate>2000-03-19</originalAirDate>
</program>
<program id='SH004460220000'>
<title>Cashin&apos; In</title>
<description>A practical look at money management.</description>
<showType>Series</showType>
<series>EP00446022</series>
<originalAirDate>2001-05-19</originalAirDate>
</program>
<program id='SH006197570000'>
<title>Weather Center Live</title>
<description>Tomorrow&apos;s forecast; recap of weather stories from around the world.</description>
<showType>Series</showType>
<series>EP00619757</series>
<originalAirDate>2001-10-14</originalAirDate>
</program>
<program id='SH006755370000'>
<title>ACLJ This Week</title>
<description>Legal, political and cultural issues of the day with Jay Sekulow.</description>
<showType>Series</showType>
<series>EP00675537</series>
<originalAirDate>2004-07-09</originalAirDate>
</program>
<program id='SH010524820000'>
<title>The Girl With Eight Limbs</title>
<description>Doctors prepare to perform surgery on 2-year-old Lakshmi Tatma whose body remained fused that of her twin.</description>
<showType>Special</showType>
<series>EP01052482</series>
<originalAirDate>2008-06-22</originalAirDate>
</program>
<program id='SH010964760000'>
<title>Gardens of Pennsylvania</title>
<description>Interesting gardens.</description>
<showType>Special</showType>
<series>EP01096476</series>
<originalAirDate>2008-10-30</originalAirDate>
</program>
<program id='SH010973990000'>
<title>Campmeeting</title>
<showType>Series</showType>
<series>EP01097399</series>
<originalAirDate>2008-10-08</originalAirDate>
</program>
<program id='SH011027320000'>
<title>Healthy Meals in Minutes!</title>
<description>The patented NuWave Oven Pro featuring our triple combo cooking power will give you the most affordable, easy, healthy, and delicious method of cooking.</description>
<showType>Paid Programming</showType>
<series>EP01102732</series>
</program>
<program id='SH011840760000'>
<title>NFL RedZone</title>
<description>Whip around coverage of every NFL game showcasing touchdowns and exciting moments inside the 20-yard line; live look-ins, highlights and updates in real time.</description>
<showType>Series</showType>
<series>EP01184076</series>
<originalAirDate>2009-09-01</originalAirDate>
</program>
<program id='SH011905870000'>
<title>Looking for a Medicare plan? Tune in now!</title>
<description>The Medicare annual election period ends on December 7. Watch and learn about Humana Medicare Advantage plans.</description>
<showType>Paid Programming</showType>
<series>EP01190587</series>
</program>
<program id='SH012025140000'>
<title>After Armageddon</title>
<description>An analysis of how human beings have survived disasters of the past.</description>
<showType>Special</showType>
<series>EP01202514</series>
<originalAirDate>2009-11-15</originalAirDate>
</program>
<program id='SH014417700000'>
<title>Born to Explore</title>
<showType>Series</showType>
<series>EP01441770</series>
<originalAirDate>2011-09-03</originalAirDate>
</program>
<program id='SH015774170000'>
<title>Grateful Nation</title>
<showType>Series</showType>
<series>EP01577417</series>
<originalAirDate>2012-06-09</originalAirDate>
</program>
<program id='SH017168400000'>
<title>Cancer: Winning the Fight, Every Day</title>
<description>Inspiring stories of how Cancer Treatment Centers of America is giving patients more hope through their unique treatment model.</description>
<showType>Paid Programming</showType>
<series>EP01716840</series>
</program>
<program id='SH017672160000'>
<title>HLN Weekend Express</title>
<description>A look at the day&apos;s news and stories.</description>
<showType>Series</showType>
<series>EP01767216</series>
<originalAirDate>2013-07-13</originalAirDate>
</program>
<program id='SH017746030000'>
<title>The Wildlife Docs</title>
<description>A veterinary team cares for more than 2,000 animals.</description>
<showType>Series</showType>
<series>EP01774603</series>
<originalAirDate>2013-10-05</originalAirDate>
</program>
<program id='SH017950540000'>
<title>Larry King Reports</title>
<description>Larry King investigates Omega XL, the ultimate all natural solution for pain and inflammation.</description>
<showType>Paid Programming</showType>
<series>EP01795054</series>
</program>
<program id='SH018595590000'>
<title>Buy gold, at-cost!</title>
<description>Here&apos;s your chance to buy Government-issued Gold Coins from the U.S. Mint! If you&apos;re ready to make a gold purchase, you cannot afford to miss this opportunity: American Gold Eagles are being sold at-cost, for $145 per gold coin!</description>
<showType>Paid Programming</showType>
<series>EP01859559</series>
</program>
<program id='SH019054090000'>
<title>Easy Outdoor Cleaning</title>
<description>Revolutionary, Outdoor Yard Cleaner!</description>
<showType>Paid Programming</showType>
<series>EP01905409</series>
</program>
<program id='SH019776960000'>
<title>Mountaineer Gameday &apos;14</title>
<showType>Series</showType>
<series>EP01977696</series>
<originalAirDate>2014-08-30</originalAirDate>
</program>
<program id='SH019795240000'>
<title>Radio 1 Big Weekend 2014</title>
<description>Highlights from the festival in Glasgow; performers include Katy Perry, Pharrell Williams, Coldplay, Kings of Leon, One Direction, Lorde, Ed Sheeran, Bastille, The 1975, Chvrches, Sam Smith, John Newman and Paolo Nutini.</description>
<showType>Special</showType>
<series>EP01979524</series>
<originalAirDate>2014-08-30</originalAirDate>
</program>
<program id='SH019855630000'>
<title>The Edge</title>
<showType>Series</showType>
<series>EP01985563</series>
<originalAirDate>2014-08-30</originalAirDate>
</program>
<program id='SH020206330000'>
<title>Eliminating Syria&apos;s Chemical Weapons</title>
<description>Sigrid Kaag discusses her experiences in eliminating the Syrian chemical weapons arsenal in the midst of a civil war.</description>
<showType>Special</showType>
<series>EP02020633</series>
<originalAirDate>2014-10-04</originalAirDate>
</program>
</programs>
<productionCrew>
<crew program='EP000011610024'>
<member>
<role>Actor</role>
<givenname>Fess</givenname>
<surname>Parker</surname>
</member>
<member>
<role>Actor</role>
<givenname>Patricia</givenname>
<surname>Blair</surname>
</member>
<member>
<role>Actor</role>
<givenname>Darby</givenname>
<surname>Hinton</surname>
</member>
<member>
<role>Actor</role>
<givenname>Dal</givenname>
<surname>McKennon</surname>
</member>
<member>
<role>Actor</role>
<givenname>Ed</givenname>
<surname>Ames</surname>
</member>
</crew>
<crew program='EP000037100886'>
<member>
<role>Actor</role>
<givenname>Kenan</givenname>
<surname>Thompson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Seth</givenname>
<surname>Meyers</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kate</givenname>
<surname>McKinnon</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nasim</givenname>
<surname>Pedrad</surname>
</member>
<member>
<role>Actor</role>
<givenname>Vanessa</givenname>
<surname>Bayer</surname>
</member>
<member>
<role>Actor</role>
<givenname>Bobby</givenname>
<surname>Moynihan</surname>
</member>
<member>
<role>Actor</role>
<givenname>Taran</givenname>
<surname>Killam</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jay</givenname>
<surname>Pharoah</surname>
</member>
<member>
<role>Actor</role>
<givenname>Cecily</givenname>
<surname>Strong</surname>
</member>
<member>
<role>Actor</role>
<givenname>Aidy</givenname>
<surname>Bryant</surname>
</member>
<member>
<role>Actor</role>
<givenname>Beck</givenname>
<surname>Bennett</surname>
</member>
<member>
<role>Actor</role>
<givenname>John</givenname>
<surname>Milhiser</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kyle</givenname>
<surname>Mooney</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mike</givenname>
<surname>O&apos;Brien</surname>
</member>
<member>
<role>Actor</role>
<givenname>NoÃ«l</givenname>
<surname>Wells</surname>
</member>
<member>
<role>Actor</role>
<givenname>Brooks</givenname>
<surname>Wheelan</surname>
</member>
<member>
<role>Host</role>
<givenname>Tina</givenname>
<surname>Fey</surname>
</member>
<member>
<role>Musical guest</role>
<givenname xsi:nil='true'/>
<surname>Arcade Fire</surname>
</member>
</crew>
<crew program='EP000186270068'>
<member>
<role>Actor</role>
<givenname>Chuck</givenname>
<surname>Connors</surname>
</member>
<member>
<role>Actor</role>
<givenname>Johnny</givenname>
<surname>Crawford</surname>
</member>
<member>
<role>Actor</role>
<givenname>Paul</givenname>
<surname>Fix</surname>
</member>
<member>
<role>Actor</role>
<givenname>Joan</givenname>
<surname>Taylor</surname>
</member>
<member>
<role>Actor</role>
<givenname>Bill</givenname>
<surname>Quinn</surname>
</member>
<member>
<role>Director</role>
<givenname>Joseph H.</givenname>
<surname>Lewis</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>John</givenname>
<surname>Dehner</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Adam</givenname>
<surname>Williams</surname>
</member>
<member>
<role>Producer</role>
<givenname>Arthur</givenname>
<surname>Gardner</surname>
</member>
<member>
<role>Producer</role>
<givenname>Arnold</givenname>
<surname>Laven</surname>
</member>
<member>
<role>Producer</role>
<givenname>Jules</givenname>
<surname>Levy</surname>
</member>
<member>
<role>Writer</role>
<givenname>Arthur</givenname>
<surname>Browne Jr.</surname>
</member>
</crew>
<crew program='EP000369830148'>
<member>
<role>Host</role>
<givenname>Chris</givenname>
<surname>Fowler</surname>
</member>
</crew>
<crew program='EP003077660516'>
<member>
<role>Actor</role>
<givenname>Tom</givenname>
<surname>Kenny</surname>
</member>
<member>
<role>Actor</role>
<givenname>Bill</givenname>
<surname>Fagerbakke</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rodger</givenname>
<surname>Bumpass</surname>
</member>
<member>
<role>Actor</role>
<givenname>Clancy</givenname>
<surname>Brown</surname>
</member>
<member>
<role>Actor</role>
<givenname>Carolyn</givenname>
<surname>Lawrence</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mr.</givenname>
<surname>Lawrence</surname>
</member>
</crew>
<crew program='EP004461730071'>
<member>
<role>Actor</role>
<givenname>Vincent</givenname>
<surname>D&apos;Onofrio</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kathryn</givenname>
<surname>Erbe</surname>
</member>
<member>
<role>Actor</role>
<givenname>Courtney B.</givenname>
<surname>Vance</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jamey</givenname>
<surname>Sheridan</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>****</givenname>
<surname>Wolf</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Rene</givenname>
<surname>Balcer</surname>
</member>
</crew>
<crew program='EP006186160177'>
<member>
<role>Actor</role>
<givenname>Sterling</givenname>
<surname>Sharpe</surname>
</member>
<member>
<role>Actor</role>
<givenname>Shaun</givenname>
<surname>O&apos;Hara</surname>
</member>
<member>
<role>Actor</role>
<givenname>Brian</givenname>
<surname>Billick</surname>
</member>
</crew>
<crew program='EP006810660608'>
<member>
<role>Actor</role>
<givenname>Wendi</givenname>
<surname>McLendon-Covey</surname>
</member>
<member>
<role>Host</role>
<givenname>Joel</givenname>
<surname>McHale</surname>
</member>
</crew>
<crew program='EP006819110071'>
<member>
<role>Actor</role>
<givenname>Mark</givenname>
<surname>Harmon</surname>
</member>
<member>
<role>Actor</role>
<givenname>Michael</givenname>
<surname>Weatherly</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>McCallum</surname>
</member>
<member>
<role>Actor</role>
<givenname>Pauley</givenname>
<surname>Perrette</surname>
</member>
<member>
<role>Actor</role>
<givenname>Sean</givenname>
<surname>Murray</surname>
</member>
<member>
<role>Actor</role>
<givenname>Cote</givenname>
<surname>De Pablo</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lauren</givenname>
<surname>Holly</surname>
</member>
<member>
<role>Director</role>
<givenname>Dennis</givenname>
<surname>Smith</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Donald P.</givenname>
<surname>Bellisario</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Susanna</givenname>
<surname>Thompson</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Scottie</givenname>
<surname>Thompson</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Blake</givenname>
<surname>Bashoff</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Enzo</givenname>
<surname>Cilenti</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Arnell</givenname>
<surname>Powell</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>David</givenname>
<surname>Fabrizio</surname>
</member>
<member>
<role>Writer</role>
<givenname>Robert</givenname>
<surname>Palm</surname>
</member>
</crew>
<crew program='EP007537910100'>
<member>
<role>Actor</role>
<givenname>Joe</givenname>
<surname>Mantegna</surname>
</member>
<member>
<role>Actor</role>
<givenname>Thomas</givenname>
<surname>Gibson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Paget</givenname>
<surname>Brewster</surname>
</member>
<member>
<role>Actor</role>
<givenname>Shemar</givenname>
<surname>Moore</surname>
</member>
<member>
<role>Actor</role>
<givenname>Matthew Gray</givenname>
<surname>Gubler</surname>
</member>
<member>
<role>Actor</role>
<givenname>A. J.</givenname>
<surname>Cook</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kirsten</givenname>
<surname>Vangsness</surname>
</member>
<member>
<role>Director</role>
<givenname>Glenn</givenname>
<surname>Kershaw</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Mark</givenname>
<surname>Gordon</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Ed</givenname>
<surname>Bernero</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Salli Richardson</givenname>
<surname>Whitfield</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Jayne</givenname>
<surname>Atkinson</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Todd</givenname>
<surname>Giebenhain</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>James</givenname>
<surname>McCauley</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Jennifer</givenname>
<surname>Del Rosario</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Jen</givenname>
<surname>Lilley</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Samantha</givenname>
<surname>Cutaran</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Anzu</givenname>
<surname>Lawson</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Jessie</givenname>
<surname>Graff</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Marco</givenname>
<surname>Aiello</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>G.O.</givenname>
<surname>Parsons</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Amanda</givenname>
<surname>Jaros</surname>
</member>
<member>
<role>Guest Star</role>
<givenname>Cheryl</givenname>
<surname>Dooley</surname>
</member>
<member>
<role>Writer</role>
<givenname>Oanh</givenname>
<surname>Ly</surname>
</member>
</crew>
<crew program='EP007973540336'>
<member>
<role>Actor</role>
<givenname>Matthew</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amy</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Actor</role>
<givenname>Zach</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jeremy</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Actor</role>
<givenname>Molly</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jacob</givenname>
<surname>Roloff</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Gay</givenname>
<surname>Rosenthal</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Paul</givenname>
<surname>Barrosse</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Joseph</givenname>
<surname>Freed</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Nicholas</givenname>
<surname>Caprio</surname>
</member>
</crew>
<crew program='EP008003660161'>
<member>
<role>Host</role>
<givenname>Anthony</givenname>
<surname>Bourdain</surname>
</member>
</crew>
<crew program='EP010221680150'>
<member>
<role>Narrator</role>
<givenname>Chip</givenname>
<surname>Bolcik</surname>
</member>
</crew>
<crew program='EP010844040169'>
<member>
<role>Host</role>
<givenname>Dennis</givenname>
<surname>Farina</surname>
</member>
</crew>
<crew program='EP011934460051'>
<member>
<role>Actor</role>
<givenname>Tia</givenname>
<surname>Torres</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Rasha</givenname>
<surname>Drachkovitch</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Lisa</givenname>
<surname>Lucas</surname>
</member>
</crew>
<crew program='EP013320550386'>
<member>
<role>Executive Producer</role>
<givenname>Joel</givenname>
<surname>Klein</surname>
</member>
<member>
<role>Host</role>
<givenname>Steve</givenname>
<surname>Harvey</surname>
</member>
</crew>
<crew program='EP013740110098'>
<member>
<role>Actor</role>
<givenname>Jenelle</givenname>
<surname>Evans</surname>
</member>
<member>
<role>Actor</role>
<givenname>Chelsea</givenname>
<surname>Houska</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kailyn</givenname>
<surname>Lowry</surname>
</member>
<member>
<role>Actor</role>
<givenname>Leah</givenname>
<surname>Messer</surname>
</member>
</crew>
<crew program='EP014228840026'>
<member>
<role>Actor</role>
<givenname>Jon</givenname>
<surname>Taffer</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>J.D.</givenname>
<surname>Roth</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Todd A.</givenname>
<surname>Nelson</surname>
</member>
</crew>
<crew program='EP014763920018'>
<member>
<role>Actor</role>
<givenname>Mick</givenname>
<surname>Wingert</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lucy</givenname>
<surname>Liu</surname>
</member>
<member>
<role>Actor</role>
<givenname>James</givenname>
<surname>Hong</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kari</givenname>
<surname>Wahlgren</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amir</givenname>
<surname>Talai</surname>
</member>
<member>
<role>Actor</role>
<givenname>Max</givenname>
<surname>Koch</surname>
</member>
<member>
<role>Actor</role>
<givenname>Fred</givenname>
<surname>Tatasciore</surname>
</member>
<member>
<role>Actor</role>
<givenname>James</givenname>
<surname>Sie</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Peter</givenname>
<surname>Hastings</surname>
</member>
</crew>
<crew program='EP015213560075'>
<member>
<role>Actor</role>
<givenname>Sal</givenname>
<surname>Masekela</surname>
</member>
</crew>
<crew program='EP015291080031'>
<member>
<role>Host</role>
<givenname>Jessi</givenname>
<surname>Combs</surname>
</member>
<member>
<role>Host</role>
<givenname>Sarah &apos;&apos;Bogi&apos;&apos;</givenname>
<surname>Lateiner</surname>
</member>
<member>
<role>Host</role>
<givenname>Cristy</givenname>
<surname>Lee</surname>
</member>
</crew>
<crew program='EP015295260201'>
<member>
<role>Actor</role>
<givenname>Melissa</givenname>
<surname>Harris-Perry</surname>
</member>
</crew>
<crew program='EP015507510006'>
<member>
<role>Actor</role>
<givenname>Jake</givenname>
<surname>Beale</surname>
</member>
<member>
<role>Actor</role>
<givenname>Ted</givenname>
<surname>Dykstra</surname>
</member>
<member>
<role>Actor</role>
<givenname>Heather</givenname>
<surname>Bambrick</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amariah</givenname>
<surname>Faulkner</surname>
</member>
<member>
<role>Actor</role>
<givenname>Stuart</givenname>
<surname>Ralston</surname>
</member>
<member>
<role>Actor</role>
<givenname>Zachary</givenname>
<surname>Bloch</surname>
</member>
<member>
<role>Actor</role>
<givenname>Addison</givenname>
<surname>Holley</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nicholas</givenname>
<surname>Kaegi</surname>
</member>
</crew>
<crew program='EP015634100036'>
<member>
<role>Actor</role>
<givenname>Josh</givenname>
<surname>Altman</surname>
</member>
<member>
<role>Actor</role>
<givenname>Josh</givenname>
<surname>Flagg</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>Parnes</surname>
</member>
<member>
<role>Actor</role>
<givenname>James</givenname>
<surname>Harris</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Fenton</givenname>
<surname>Bailey</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Randy</givenname>
<surname>Barbato</surname>
</member>
</crew>
<crew program='EP015676680032'>
<member>
<role>Actor</role>
<givenname>Richard</givenname>
<surname>Rawlings</surname>
</member>
<member>
<role>Actor</role>
<givenname>Aaron</givenname>
<surname>Kaufman</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Craig</givenname>
<surname>Piligian</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Eddie</givenname>
<surname>Rohwedder</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Craig</givenname>
<surname>Coffman</surname>
</member>
</crew>
<crew program='EP016164320036'>
<member>
<role>Actor</role>
<givenname>Zach</givenname>
<surname>Callison</surname>
</member>
<member>
<role>Actor</role>
<givenname xsi:nil='true'/>
<surname>Estelle</surname>
</member>
<member>
<role>Actor</role>
<givenname>Deedee</givenname>
<surname>Magno Hall</surname>
</member>
<member>
<role>Actor</role>
<givenname>Michaela</givenname>
<surname>Dietz</surname>
</member>
</crew>
<crew program='EP016704140052'>
<member>
<role>Executive Producer</role>
<givenname>John</givenname>
<surname>Hamlin</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Lewis</givenname>
<surname>Bogach</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Ritch</givenname>
<surname>Sublett</surname>
</member>
<member>
<role>Host</role>
<givenname>Cody</givenname>
<surname>Alan</surname>
</member>
<member>
<role>Host</role>
<givenname>Alecia</givenname>
<surname>Davis</surname>
</member>
<member>
<role>Host</role>
<givenname>Katie</givenname>
<surname>Cook</surname>
</member>
</crew>
<crew program='EP017719770015'>
<member>
<role>Executive Producer</role>
<givenname>Josh</givenname>
<surname>Berkley</surname>
</member>
</crew>
<crew program='EP017729720028'>
<member>
<role>Host</role>
<givenname>Kevin</givenname>
<surname>Frazier</surname>
</member>
</crew>
<crew program='EP017922990022'>
<member>
<role>Host</role>
<givenname>Lidia</givenname>
<surname>Bastianich</surname>
</member>
</crew>
<crew program='EP018098690023'>
<member>
<role>Host</role>
<givenname>Dan</givenname>
<surname>Rather</surname>
</member>
</crew>
<crew program='EP018375220038'>
<member>
<role>Host</role>
<givenname>Katie</givenname>
<surname>Lee</surname>
</member>
<member>
<role>Host</role>
<givenname>Sunny</givenname>
<surname>Anderson</surname>
</member>
<member>
<role>Host</role>
<givenname>Geoffrey</givenname>
<surname>Zakarian</surname>
</member>
<member>
<role>Host</role>
<givenname>Marcela</givenname>
<surname>Valladolid</surname>
</member>
<member>
<role>Host</role>
<givenname>Jeff</givenname>
<surname>Mauro</surname>
</member>
</crew>
<crew program='EP019466180001'>
<member>
<role>Host</role>
<givenname>David</givenname>
<surname>Holder</surname>
</member>
<member>
<role>Host</role>
<givenname>Karin</givenname>
<surname>Holder</surname>
</member>
<member>
<role>Host</role>
<givenname>Warren</givenname>
<surname>Holder</surname>
</member>
<member>
<role>Host</role>
<givenname>Easton</givenname>
<surname>Holder</surname>
</member>
</crew>
<crew program='EP019542070004'>
<member>
<role>Actor</role>
<givenname>Jen</givenname>
<surname>Hatmaker</surname>
</member>
<member>
<role>Actor</role>
<givenname>Brandon</givenname>
<surname>Hatmaker</surname>
</member>
</crew>
<crew program='EP019771790001'>
<member>
<role>Host</role>
<givenname>Judy</givenname>
<surname>Greer</surname>
</member>
</crew>
<crew program='MV000043320000'>
<member>
<role>Actor</role>
<givenname>Lew</givenname>
<surname>Ayres</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lionel</givenname>
<surname>Barrymore</surname>
</member>
<member>
<role>Actor</role>
<givenname>Robert</givenname>
<surname>Young</surname>
</member>
<member>
<role>Actor</role>
<givenname>Laraine</givenname>
<surname>Day</surname>
</member>
<member>
<role>Actor</role>
<givenname>Emma</givenname>
<surname>Dunn</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nat</givenname>
<surname>Pendleton</surname>
</member>
<member>
<role>Actor</role>
<givenname>Bobs</givenname>
<surname>Watson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Walter</givenname>
<surname>Kingsford</surname>
</member>
<member>
<role>Actor</role>
<givenname>Alma</givenname>
<surname>Kruger</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nell</givenname>
<surname>Craig</surname>
</member>
<member>
<role>Actor</role>
<givenname>Frank</givenname>
<surname>Orth</surname>
</member>
<member>
<role>Actor</role>
<givenname>Marie</givenname>
<surname>Blake</surname>
</member>
<member>
<role>Actor</role>
<givenname>Horace</givenname>
<surname>MacMahon</surname>
</member>
<member>
<role>Director</role>
<givenname>Harold S.</givenname>
<surname>Bucquet</surname>
</member>
</crew>
<crew program='MV000208930000'>
<member>
<role>Actor</role>
<givenname>Arthur</givenname>
<surname>Franz</surname>
</member>
<member>
<role>Actor</role>
<givenname>Beverly</givenname>
<surname>Garland</surname>
</member>
<member>
<role>Actor</role>
<givenname>Helene</givenname>
<surname>Stanton</surname>
</member>
<member>
<role>Actor</role>
<givenname>Michael</givenname>
<surname>Ansara</surname>
</member>
<member>
<role>Actor</role>
<givenname>Stacy</givenname>
<surname>Harris</surname>
</member>
<member>
<role>Actor</role>
<givenname>William</givenname>
<surname>Henry</surname>
</member>
<member>
<role>Actor</role>
<givenname>Michael</givenname>
<surname>Granger</surname>
</member>
<member>
<role>Director</role>
<givenname>William</givenname>
<surname>Castle</surname>
</member>
</crew>
<crew program='MV000239930000'>
<member>
<role>Actor</role>
<givenname>Christopher</givenname>
<surname>Walken</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jason</givenname>
<surname>Connery</surname>
</member>
<member>
<role>Actor</role>
<givenname>Yossi</givenname>
<surname>Graber</surname>
</member>
<member>
<role>Actor</role>
<givenname>Carmela</givenname>
<surname>Marner</surname>
</member>
<member>
<role>Actor</role>
<givenname>Elki</givenname>
<surname>Jacobs</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amnon</givenname>
<surname>Meskin</surname>
</member>
<member>
<role>Director</role>
<givenname>Eugene</givenname>
<surname>Marner</surname>
</member>
<member>
<role>Producer</role>
<givenname>Menahem</givenname>
<surname>Golan</surname>
</member>
<member>
<role>Producer</role>
<givenname>Yoram</givenname>
<surname>Globus</surname>
</member>
</crew>
<crew program='MV000247890000'>
<member>
<role>Actor</role>
<givenname>Sean</givenname>
<surname>Penn</surname>
</member>
<member>
<role>Actor</role>
<givenname>Robert</givenname>
<surname>Duvall</surname>
</member>
<member>
<role>Actor</role>
<givenname>Maria Conchita</givenname>
<surname>Alonso</surname>
</member>
<member>
<role>Actor</role>
<givenname>Randy</givenname>
<surname>Brooks</surname>
</member>
<member>
<role>Actor</role>
<givenname>Grand</givenname>
<surname>Bush</surname>
</member>
<member>
<role>Actor</role>
<givenname>Don</givenname>
<surname>Cheadle</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rudy</givenname>
<surname>Ramos</surname>
</member>
<member>
<role>Actor</role>
<givenname>Trinidad</givenname>
<surname>Silva</surname>
</member>
<member>
<role>Actor</role>
<givenname>Damon</givenname>
<surname>Wayans</surname>
</member>
<member>
<role>Director</role>
<givenname>Dennis</givenname>
<surname>Hopper</surname>
</member>
</crew>
<crew program='MV000381640000'>
<member>
<role>Actor</role>
<givenname>Jaclyn</givenname>
<surname>Smith</surname>
</member>
<member>
<role>Actor</role>
<givenname>Brad</givenname>
<surname>Johnson</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>Lascher</surname>
</member>
<member>
<role>Actor</role>
<givenname>Hilary</givenname>
<surname>Swank</surname>
</member>
<member>
<role>Actor</role>
<givenname>Carolyn</givenname>
<surname>McCormick</surname>
</member>
<member>
<role>Actor</role>
<givenname>Andrew</givenname>
<surname>Lawrence</surname>
</member>
<member>
<role>Actor</role>
<givenname>Ramsay</givenname>
<surname>Midwood</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jason</givenname>
<surname>Kristofer</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>Gianopoulos</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>Byron</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lisa Robin</givenname>
<surname>Kelly</surname>
</member>
<member>
<role>Actor</role>
<givenname>Gary</givenname>
<surname>Hudson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rosanna</givenname>
<surname>Huffman</surname>
</member>
<member>
<role>Actor</role>
<givenname>David</givenname>
<surname>Cromwell</surname>
</member>
<member>
<role>Actor</role>
<givenname>Tom</givenname>
<surname>Nibley</surname>
</member>
<member>
<role>Actor</role>
<givenname>Malissa</givenname>
<surname>Feruzzi</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nomi</givenname>
<surname>Mitty</surname>
</member>
<member>
<role>Actor</role>
<givenname>Aixa</givenname>
<surname>Clemente</surname>
</member>
<member>
<role>Actor</role>
<givenname>Ron</givenname>
<surname>Frazier</surname>
</member>
<member>
<role>Actor</role>
<givenname>Richard</givenname>
<surname>Ryder</surname>
</member>
<member>
<role>Director</role>
<givenname>Armand</givenname>
<surname>Mastroianni</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Felice</givenname>
<surname>Gordon</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Carla</givenname>
<surname>Singer</surname>
</member>
<member>
<role>Producer</role>
<givenname>Christopher</givenname>
<surname>Canaan</surname>
</member>
<member>
<role>Producer</role>
<givenname>Joan</givenname>
<surname>Carson</surname>
</member>
</crew>
<crew program='MV000499840000'>
<member>
<role>Actor</role>
<givenname>Jim</givenname>
<surname>Carrey</surname>
</member>
<member>
<role>Actor</role>
<givenname>Maura</givenname>
<surname>Tierney</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jennifer</givenname>
<surname>Tilly</surname>
</member>
<member>
<role>Actor</role>
<givenname>Swoosie</givenname>
<surname>Kurtz</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amanda</givenname>
<surname>Donohoe</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jason</givenname>
<surname>Bernard</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mitchell</givenname>
<surname>Ryan</surname>
</member>
<member>
<role>Actor</role>
<givenname>Anne</givenname>
<surname>Haney</surname>
</member>
<member>
<role>Actor</role>
<givenname>Justin</givenname>
<surname>Cooper</surname>
</member>
<member>
<role>Actor</role>
<givenname>Chip</givenname>
<surname>Mayer</surname>
</member>
<member>
<role>Actor</role>
<givenname>Randall &apos;&apos;Tex&apos;&apos;</givenname>
<surname>Cobb</surname>
</member>
<member>
<role>Actor</role>
<givenname>Cary</givenname>
<surname>Elwes</surname>
</member>
<member>
<role>Director</role>
<givenname>Tom</givenname>
<surname>Shadyac</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Michael</givenname>
<surname>Bostick</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>James D.</givenname>
<surname>Brubaker</surname>
</member>
<member>
<role>Producer</role>
<givenname>Brian</givenname>
<surname>Grazer</surname>
</member>
<member>
<role>Writer</role>
<givenname>Paul</givenname>
<surname>Guay</surname>
</member>
<member>
<role>Writer</role>
<givenname>Stephen</givenname>
<surname>Mazur</surname>
</member>
</crew>
<crew program='MV001393750000'>
<member>
<role>Actor</role>
<givenname>Tom</givenname>
<surname>Selleck</surname>
</member>
<member>
<role>Actor</role>
<givenname>Wendy</givenname>
<surname>Crewson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Maggie</givenname>
<surname>Grace</surname>
</member>
<member>
<role>Actor</role>
<givenname>Anna</givenname>
<surname>Gunn</surname>
</member>
<member>
<role>Actor</role>
<givenname>Patrick</givenname>
<surname>Flueger</surname>
</member>
<member>
<role>Actor</role>
<givenname>Tegan</givenname>
<surname>Moss</surname>
</member>
<member>
<role>Actor</role>
<givenname>Tim</givenname>
<surname>Henry</surname>
</member>
<member>
<role>Actor</role>
<givenname>Daniel</givenname>
<surname>Petronijevic</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jenna</givenname>
<surname>Friedenberg</surname>
</member>
<member>
<role>Actor</role>
<givenname>Sylvia</givenname>
<surname>Wong</surname>
</member>
<member>
<role>Actor</role>
<givenname>Hamish</givenname>
<surname>Boyd</surname>
</member>
<member>
<role>Director</role>
<givenname>Richard</givenname>
<surname>Friedenberg</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Laurie Marie</givenname>
<surname>Parker</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Wendy</givenname>
<surname>Hill-Tout</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Lisa</givenname>
<surname>Demberg</surname>
</member>
<member>
<role>Producer</role>
<givenname>Avi Noam</givenname>
<surname>Levy</surname>
</member>
<member>
<role>Writer</role>
<givenname>Richard</givenname>
<surname>Friedenberg</surname>
</member>
</crew>
<crew program='MV002024230000'>
<member>
<role>Actor</role>
<givenname>Ice</givenname>
<surname>Cube</surname>
</member>
<member>
<role>Actor</role>
<givenname>Katt</givenname>
<surname>Williams</surname>
</member>
<member>
<role>Actor</role>
<givenname>Tracy</givenname>
<surname>Morgan</surname>
</member>
<member>
<role>Actor</role>
<givenname>Loretta</givenname>
<surname>Devine</surname>
</member>
<member>
<role>Actor</role>
<givenname>Michael</givenname>
<surname>Beach</surname>
</member>
<member>
<role>Actor</role>
<givenname>Regina</givenname>
<surname>Hall</surname>
</member>
<member>
<role>Actor</role>
<givenname>Keith</givenname>
<surname>David</surname>
</member>
<member>
<role>Actor</role>
<givenname>Malinda</givenname>
<surname>Williams</surname>
</member>
<member>
<role>Actor</role>
<givenname>Chi</givenname>
<surname>McBride</surname>
</member>
<member>
<role>Actor</role>
<givenname>Clifton</givenname>
<surname>Powell</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nicholas</givenname>
<surname>Turturro</surname>
</member>
<member>
<role>Actor</role>
<givenname>Olivia</givenname>
<surname>Cole</surname>
</member>
<member>
<role>Actor</role>
<givenname>Red</givenname>
<surname>Grant</surname>
</member>
<member>
<role>Actor</role>
<givenname>C.J.</givenname>
<surname>Sanders</surname>
</member>
<member>
<role>Director</role>
<givenname>David E.</givenname>
<surname>Talbert</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Stacy Kolker</givenname>
<surname>Cramer</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Neil</givenname>
<surname>Machlis</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Julie</givenname>
<surname>Yorn</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Ronald</givenname>
<surname>Muhammad</surname>
</member>
<member>
<role>Producer</role>
<givenname>David E.</givenname>
<surname>Talbert</surname>
</member>
<member>
<role>Producer</role>
<givenname>David</givenname>
<surname>McIlvain</surname>
</member>
<member>
<role>Producer</role>
<givenname>Tim</givenname>
<surname>Story</surname>
</member>
<member>
<role>Producer</role>
<givenname>Ice</givenname>
<surname>Cube</surname>
</member>
<member>
<role>Producer</role>
<givenname>Matt</givenname>
<surname>Alvarez</surname>
</member>
<member>
<role>Writer</role>
<givenname>David E.</givenname>
<surname>Talbert</surname>
</member>
</crew>
<crew program='MV002227280000'>
<member>
<role>Actor</role>
<givenname>Bruce</givenname>
<surname>Dern</surname>
</member>
<member>
<role>Actor</role>
<givenname>Cindy</givenname>
<surname>Sampson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nicolas</givenname>
<surname>Wright</surname>
</member>
<member>
<role>Actor</role>
<givenname>Allison</givenname>
<surname>Graham</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kwasi</givenname>
<surname>Songui</surname>
</member>
<member>
<role>Actor</role>
<givenname>James</givenname>
<surname>Kidnie</surname>
</member>
<member>
<role>Actor</role>
<givenname>Bronwen</givenname>
<surname>Mantel</surname>
</member>
<member>
<role>Actor</role>
<givenname>Robert</givenname>
<surname>Higden</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mari-Pier</givenname>
<surname>Gaudet</surname>
</member>
<member>
<role>Director</role>
<givenname>David</givenname>
<surname>Winning</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Robert</givenname>
<surname>Halmi Sr.</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Robert</givenname>
<surname>Halmi Jr.</surname>
</member>
<member>
<role>Writer</role>
<givenname>Gary</givenname>
<surname>Dauberman</surname>
</member>
<member>
<role>Writer</role>
<givenname>Ethlie Ann</givenname>
<surname>Vare</surname>
</member>
</crew>
<crew program='MV002529780000'>
<member>
<role>Actor</role>
<givenname>Robert</givenname>
<surname>Downey Jr.</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jude</givenname>
<surname>Law</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rachel</givenname>
<surname>McAdams</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mark</givenname>
<surname>Strong</surname>
</member>
<member>
<role>Actor</role>
<givenname>Eddie</givenname>
<surname>Marsan</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kelly</givenname>
<surname>Reilly</surname>
</member>
<member>
<role>Actor</role>
<givenname>James</givenname>
<surname>Fox</surname>
</member>
<member>
<role>Actor</role>
<givenname>Robert</givenname>
<surname>Maillet</surname>
</member>
<member>
<role>Director</role>
<givenname>Guy</givenname>
<surname>Ritchie</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Michael</givenname>
<surname>Tadross</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Bruce</givenname>
<surname>Berman</surname>
</member>
<member>
<role>Producer</role>
<givenname>Joel</givenname>
<surname>Silver</surname>
</member>
<member>
<role>Producer</role>
<givenname>Lionel</givenname>
<surname>Wigram</surname>
</member>
<member>
<role>Producer</role>
<givenname>Susan</givenname>
<surname>Downey</surname>
</member>
<member>
<role>Producer</role>
<givenname>Dan</givenname>
<surname>Lin</surname>
</member>
</crew>
<crew program='MV002565500000'>
<member>
<role>Actor</role>
<givenname>Jackie</givenname>
<surname>Chan</surname>
</member>
<member>
<role>Actor</role>
<givenname>Amber</givenname>
<surname>Valletta</surname>
</member>
<member>
<role>Actor</role>
<givenname>George</givenname>
<surname>Lopez</surname>
</member>
<member>
<role>Actor</role>
<givenname>Billy Ray</givenname>
<surname>Cyrus</surname>
</member>
<member>
<role>Actor</role>
<givenname>Madeline</givenname>
<surname>Carroll</surname>
</member>
<member>
<role>Actor</role>
<givenname>Will</givenname>
<surname>Shadley</surname>
</member>
<member>
<role>Actor</role>
<givenname>Magnus</givenname>
<surname>Scheving</surname>
</member>
<member>
<role>Actor</role>
<givenname>Alina</givenname>
<surname>Foley</surname>
</member>
<member>
<role>Actor</role>
<givenname>Katherine</givenname>
<surname>Boecher</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lucas</givenname>
<surname>Till</surname>
</member>
<member>
<role>Director</role>
<givenname>Brian</givenname>
<surname>Levant</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Ryan</givenname>
<surname>Kavanaugh</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Tucker</givenname>
<surname>Tooley</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Ira</givenname>
<surname>Shuman</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Solon</givenname>
<surname>So</surname>
</member>
<member>
<role>Producer</role>
<givenname>Robert</givenname>
<surname>Simonds</surname>
</member>
</crew>
<crew program='MV002709840000'>
<member>
<role>Actor</role>
<givenname>Tom</givenname>
<surname>Cruise</surname>
</member>
<member>
<role>Actor</role>
<givenname>Cameron</givenname>
<surname>Diaz</surname>
</member>
<member>
<role>Actor</role>
<givenname>Peter</givenname>
<surname>Sarsgaard</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jordi</givenname>
<surname>MollÃ </surname>
</member>
<member>
<role>Actor</role>
<givenname>Viola</givenname>
<surname>Davis</surname>
</member>
<member>
<role>Actor</role>
<givenname>Paul</givenname>
<surname>Dano</surname>
</member>
<member>
<role>Actor</role>
<givenname>Maggie</givenname>
<surname>Grace</surname>
</member>
<member>
<role>Actor</role>
<givenname>Marc</givenname>
<surname>Blucas</surname>
</member>
<member>
<role>Actor</role>
<givenname>Celia</givenname>
<surname>Weston</surname>
</member>
<member>
<role>Actor</role>
<givenname>Falk</givenname>
<surname>Hentschel</surname>
</member>
<member>
<role>Actor</role>
<givenname>Lennie</givenname>
<surname>Loftin</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rich</givenname>
<surname>Manley</surname>
</member>
<member>
<role>Actor</role>
<givenname>Dale</givenname>
<surname>Dye</surname>
</member>
<member>
<role>Actor</role>
<givenname>Gal</givenname>
<surname>Gadot</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jack A.</givenname>
<surname>O&apos;Connell</surname>
</member>
<member>
<role>Actor</role>
<givenname>Trevor</givenname>
<surname>Loomis</surname>
</member>
<member>
<role>Actor</role>
<givenname>Nilaja</givenname>
<surname>Sun</surname>
</member>
<member>
<role>Director</role>
<givenname>James</givenname>
<surname>Mangold</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Joe</givenname>
<surname>Roth</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>Arnon</givenname>
<surname>Milchan</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>E. Bennett</givenname>
<surname>Walsh</surname>
</member>
<member>
<role>Producer</role>
<givenname>Cathy</givenname>
<surname>Konrad</surname>
</member>
<member>
<role>Producer</role>
<givenname>Steve</givenname>
<surname>Pink</surname>
</member>
<member>
<role>Producer</role>
<givenname>Todd</givenname>
<surname>Garner</surname>
</member>
</crew>
<crew program='MV003978370000'>
<member>
<role>Actor</role>
<givenname>John C.</givenname>
<surname>Reilly</surname>
</member>
<member>
<role>Actor</role>
<givenname>Sarah</givenname>
<surname>Silverman</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jack</givenname>
<surname>McBrayer</surname>
</member>
<member>
<role>Actor</role>
<givenname>Jane</givenname>
<surname>Lynch</surname>
</member>
<member>
<role>Actor</role>
<givenname>Alan</givenname>
<surname>Tudyk</surname>
</member>
<member>
<role>Actor</role>
<givenname>Mindy</givenname>
<surname>Kaling</surname>
</member>
<member>
<role>Actor</role>
<givenname>Joe</givenname>
<surname>Lo Truglio</surname>
</member>
<member>
<role>Actor</role>
<givenname>Ed</givenname>
<surname>O&apos;Neill</surname>
</member>
<member>
<role>Actor</role>
<givenname>Dennis</givenname>
<surname>Haysbert</surname>
</member>
<member>
<role>Actor</role>
<givenname>Adam</givenname>
<surname>Carolla</surname>
</member>
<member>
<role>Actor</role>
<givenname>Horatio</givenname>
<surname>Sanz</surname>
</member>
<member>
<role>Actor</role>
<givenname>Edie</givenname>
<surname>McClurg</surname>
</member>
<member>
<role>Actor</role>
<givenname>Roger Craig</givenname>
<surname>Smith</surname>
</member>
<member>
<role>Actor</role>
<givenname>Gerald C.</givenname>
<surname>Rivers</surname>
</member>
<member>
<role>Actor</role>
<givenname>Rachael</givenname>
<surname>Harris</surname>
</member>
<member>
<role>Actor</role>
<givenname>Stefanie</givenname>
<surname>Scott</surname>
</member>
<member>
<role>Actor</role>
<givenname>Reuben</givenname>
<surname>Langdon</surname>
</member>
<member>
<role>Actor</role>
<givenname>Kyle</givenname>
<surname>Hebert</surname>
</member>
<member>
<role>Director</role>
<givenname>Rich</givenname>
<surname>Moore</surname>
</member>
<member>
<role>Executive Producer</role>
<givenname>John</givenname>
<surname>Lasseter</surname>
</member>
<member>
<role>Producer</role>
<givenname>Clark</givenname>
<surname>Spencer</surname>
</member>
</crew>
<crew program='MV005479230000'>
<member>
<role>Actor</role>
<givenname>Kristy</givenname>
<surname>Swanson</surname>
</member>
<member>
<role>Actor</role>
<givenname>Scott</givenname>
<surname>Grimes</surname>
</member>
<member>
<role>Actor</role>
<givenname>Paul</givenname>
<surname>Butcher</surname>
</member>
<member>
<role>Actor</role>
<givenname>Allie</givenname>
<surname>Gonino</surname>
</member>
</crew>
<crew program='SH000690190000'>
<member>
<role>Anchor</role>
<givenname>Don</givenname>
<surname>Lemon</surname>
</member>
</crew>
<crew program='SH004460220000'>
<member>
<role>Host</role>
<givenname>Terry</givenname>
<surname>Keenan</surname>
</member>
</crew>
<crew program='SH006197570000'>
<member>
<role>Anchor</role>
<givenname>Vivian</givenname>
<surname>Brown</surname>
</member>
</crew>
<crew program='SH014417700000'>
<member>
<role>Host</role>
<givenname>Richard</givenname>
<surname>Wiese</surname>
</member>
</crew>
<crew program='SH017672160000'>
<member>
<role>Executive Producer</role>
<givenname>Valerie</givenname>
<surname>Butler</surname>
</member>
<member>
<role>Host</role>
<givenname>Lynn</givenname>
<surname>Berry</surname>
</member>
</crew>
<crew program='SH017746030000'>
<member>
<role>Host</role>
<givenname>Rachel</givenname>
<surname>Reenstra</surname>
</member>
</crew>
</productionCrew>
<genres>
<programGenre program='EP000011610024'>
<genre>
<class>Drama</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Western</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP000037100886'>
<genre>
<class>Comedy</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP000186270068'>
<genre>
<class>Drama</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Western</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP000369830148'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Football</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP003077660516'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Comedy</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Fantasy</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Animated</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP004461730071'>
<genre>
<class>Crime drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP005212625900'>
<genre>
<class>Sports event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Soccer</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP005544752374'>
<genre>
<class>Sports event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Golf</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP006186160177'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Football</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP006795090002'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Fantasy</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Educational</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP006810660608'>
<genre>
<class>Entertainment</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Comedy</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP006819110071'>
<genre>
<class>Crime drama</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Action</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Mystery</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP007537910100'>
<genre>
<class>Suspense</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Crime drama</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Mystery</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP007973540336'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP008003660161'>
<genre>
<class>Cooking</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Travel</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP010213590057'>
<genre>
<class>Religious</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP010221680150'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP010844040169'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Mystery</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP011934460051'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Animals</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP012147960047'>
<genre>
<class>Shopping</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP013320550386'>
<genre>
<class>Game show</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP013740110098'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP014228840026'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP014763920018'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Comedy</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Animated</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP014984720076'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Hockey</class>
<relevance>1</relevance>
</genre>
<genre>
<class>News</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP015213560075'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Action sports</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP015291080031'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Auto</class>
<relevance>1</relevance>
</genre>
<genre>
<class>How-to</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP015295260201'>
<genre>
<class>Talk</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Public affairs</class>
<relevance>1</relevance>
</genre>
<genre>
<class>News</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP015507510006'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Educational</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Entertainment</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Animated</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP015634100036'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP015676680032'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Auto</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='EP016164320036'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Fantasy</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Animated</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP016314260005'>
<genre>
<class>Shopping</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP016704140052'>
<genre>
<class>Music</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP017719770015'>
<genre>
<class>Documentary</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP017729720028'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP017922990022'>
<genre>
<class>Cooking</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP018098690023'>
<genre>
<class>Interview</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP018375220038'>
<genre>
<class>Cooking</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP018940630002'>
<genre>
<class>Shopping</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP019466180001'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Outdoors</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Hunting</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Archery</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='EP019542070004'>
<genre>
<class>Reality</class>
<relevance>0</relevance>
</genre>
<genre>
<class>House/garden</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Home improvement</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='EP019771790001'>
<genre>
<class>Health</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='EP019871170002'>
<genre>
<class>House/garden</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV000043320000'>
<genre>
<class>Drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV000208930000'>
<genre>
<class>Crime drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV000239930000'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Fantasy</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='MV000247890000'>
<genre>
<class>Crime drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV000381640000'>
<genre>
<class>Docudrama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV000499840000'>
<genre>
<class>Comedy</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV001393750000'>
<genre>
<class>Drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV002024230000'>
<genre>
<class>Comedy</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='MV002227280000'>
<genre>
<class>Horror</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Suspense</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='MV002529780000'>
<genre>
<class>Action</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Mystery</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='MV002565500000'>
<genre>
<class>Comedy</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Action</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='MV002709840000'>
<genre>
<class>Action</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Comedy</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='MV003978370000'>
<genre>
<class>Children</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Comedy</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Adventure</class>
<relevance>2</relevance>
</genre>
<genre>
<class>Animated</class>
<relevance>3</relevance>
</genre>
</programGenre>
<programGenre program='MV005479230000'>
<genre>
<class>Comedy-drama</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH000000010000'>
<genre>
<class>Shopping</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH000191120000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH000199170000'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>News</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Sports talk</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='SH000240640000'>
<genre>
<class>Educational</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH000690190000'>
<genre>
<class>News</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH003694920000'>
<genre>
<class>Educational</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Game show</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH004460220000'>
<genre>
<class>Talk</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Bus./financial</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH006197570000'>
<genre>
<class>Weather</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH006755370000'>
<genre>
<class>Religious</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH010524820000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Documentary</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Medical</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='SH010964760000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Agriculture</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH010973990000'>
<genre>
<class>Religious</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH011027320000'>
<genre>
<class>Shopping</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH011840760000'>
<genre>
<class>Football</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH011905870000'>
<genre>
<class>Consumer</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH012025140000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
<genre>
<class>History</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Science</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='SH014417700000'>
<genre>
<class>Outdoors</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Educational</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH015774170000'>
<genre>
<class>Military</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH017168400000'>
<genre>
<class>Consumer</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH017672160000'>
<genre>
<class>News</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH017746030000'>
<genre>
<class>Animals</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Educational</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH017950540000'>
<genre>
<class>Consumer</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH018595590000'>
<genre>
<class>Consumer</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH019054090000'>
<genre>
<class>Consumer</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH019776960000'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
<genre>
<class>News</class>
<relevance>1</relevance>
</genre>
<genre>
<class>Football</class>
<relevance>2</relevance>
</genre>
</programGenre>
<programGenre program='SH019795240000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Music</class>
<relevance>1</relevance>
</genre>
</programGenre>
<programGenre program='SH019855630000'>
<genre>
<class>Sports non-event</class>
<relevance>0</relevance>
</genre>
</programGenre>
<programGenre program='SH020206330000'>
<genre>
<class>Special</class>
<relevance>0</relevance>
</genre>
<genre>
<class>Talk</class>
<relevance>1</relevance>
</genre>
</programGenre>
</genres>
</xtvd>
</xtvdResponse>
</ns1:downloadResponse>
</SOAP-ENV:Body> [COLOR=#000000]</SOAP-ENV:Envelope>[/COLOR]
```

---

### Post by tgm4883 on 2014-10-04
I'm checking with SD now, but I'm wondering if you are running mythfilldatabase as the mythtv user or not?

---

### Post by garsh on 2014-10-04
I was not, but certainly the normal automated nightly run of mythfilldatabase is doing so.
I've filed a ticket with SD as well.

---

### Post by tgm4883 on 2014-10-04
> **garsh said:**
> I was not, but certainly the normal automated nightly run of mythfilldatabase is doing so.
I've filed a ticket with SD as well.

While that is true, doing so can cause the temp files to become writable by a single user and thus cause problems exactly like the one that you are describing.

As for SD and /getdata. I asked some SD guys to look at your output and they responded with

> <rmeden> tgm4883: /getdata only returns "what's on now".  So it should have 1 schedule per station... it looks good to me

and

> <bill6502> tgm4883: the user's log looks like a case of a stale /tmp/mythtv_ddp_data file. It was fixed for folks with more than 1 source, it appears he only has 1.

So I would delete that temp file and try running it again, as the mythtv user.

---

### Post by garsh on 2014-10-04
That was it!
After deleting /tmp/mythtv_ddp_data & running mythfilldatabase as mythtv, I once again have two weeks worth of guide data.
Thanks!

---

### Post by topcat5 on 2014-10-04
> **tgm4883 said:**
> I think you mean pending changes. Nothing has been changed yet, so I'm not sure how that could be the issue. 

What options is OP running for mythfilldatabase? I've use --dd-grab-all and have a full 16 days of data.Indeed.  I've tried that several times.  

I've never seen it do something like this before.   I don't see anything obvious in the logs.  A handful of recording schedules will no longer set up a program to be recorded.  I can recreate the recording schedule and it works again.   I assumed it was something to do with the pending updates to the schedule since it is the only thing that is changing on this system.   

I did have a direct look at the Records Table and the only difference that I see between one that works vs one that doesn't is the chanID has been changed to 0 on the non-working.    I've no idea what caused that.  In any case, maybe it's just a remarkable coincidence.

---

