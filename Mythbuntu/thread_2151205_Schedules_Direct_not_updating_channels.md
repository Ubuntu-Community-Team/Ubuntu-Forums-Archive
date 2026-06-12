---
title: "Schedules Direct not updating channels"
date: 2013-06-03
forum: Mythbuntu
---

### Post by bleve on 2013-06-03
I finally gave up on my previous BE and got a newer dual core machine that could do 64bit for BE.  I installed mythbuntu last night and got my PVR-350 card working but seem to have issues getting the HDPVR setup.  

I am able to add the video source but had to have it scan for the listing sources 5 times before it finally picked it up from schedules direct.  The failure I was getting in the mythtv-setup.log was:

>  data
Jun  3 17:51:41 mythtv01 mythtv-setup[6034]: I CoreContext datadirect.cpp:1021 (DDPost) Downloading DataDirect feed
Jun  3 17:51:51 mythtv01 mythtv-setup[6034]: E CoreContext datadirect.cpp:1186 (GrabData) DataDirect: Failed to get data: Download error


I found something about this being a timeout on the BE side but even after updating to the latest from the .25 repos it still happens.  So now on to the next problem.  Now that I have the source added I can't get it to fetch the channel information.  In the setup log all I see is:

> Jun  3 18:03:48 mythtv01 mythtv-setup[6034]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  3 18:04:00 mythtv01 mythtv-setup[6034]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices


In the mythfilldatabase.log:

> Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext main.cpp:437 (main) Running for sourceid 2 ONLY because --sourceid was given on command-line
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext filldata.cpp:600 (Run) Updating source #2 (Digital) with grabber schedulesdirect1
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext filldata.cpp:620 (Run) No channels are configured to use grabber.
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext datadirect.cpp:1158 (GrabData) DataDirect: Grabbing channel data
Jun  3 18:13:11 mythtv01 mythfilldatabase[6446]: I CoreContext datadirect.cpp:1021 (DDPost) Downloading DataDirect feed
Jun  3 18:13:23 mythtv01 mythfilldatabase[6446]: E CoreContext datadirect.cpp:1186 (GrabData) DataDirect: Failed to get data: Download error
Jun  3 18:13:23 mythtv01 mythfilldatabase[6446]: N CoreContext main.cpp:488 (main) Data fetching complete.
Jun  3 18:13:23 mythtv01 mythfilldatabase[6446]: I CoreContext datadirect.cpp:573 (~DataDirectProcessor) DataDirect: Deleting temporary files



This all worked fine with the 32bit release that is on my other machine, although this was done several weeks ago so maybe it does have the same problem now.  Any ideas where to look or get more detailed information to what is going wrong?

Thanks

---

### Post by bleve on 2013-06-03
Update:  After trying another 4 or 5 times by clicking to fetch channels it finally completed.  Still would like to know what is happening.  Anyone with ideas, please let me know.

---

### Post by bleve on 2013-06-07
Went to .26 and this issue disappeared.

---

