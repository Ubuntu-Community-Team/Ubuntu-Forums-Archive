---
title: "mythfilldatabase won't download"
date: 2012-10-14
forum: Mythbuntu
---

### Post by daninca on 2012-10-14
I had mythtv working nicely under Mythbuntu 12.04.  Then I moved to another area and I can't get the schedules direct download to work anymore.

I've setup a new lineup in schedules direct and deleted the old.  I deleted all the old myth channels, sources, and tuners; and then re-added.  

Setup can get the channel list (although I always have to try twice), so I know the password is right.  tv_grab_na_dd can download fine, but I can't figure out how to get that data into mythfilldatabase.

I found this thread.  [http://www.gossamer-threads.com/lists/mythtv/users/520453](http://www.gossamer-threads.com/lists/mythtv/users/520453)  I traced with WireShark and found that it does the POST and gets a 401 not authorized (which is expected).  However, it doesn't try anything more after that.  They said it should try again with info from the "rejection".

I was doing:  
mythfilldatabase --dd-grab-all  --nodblog -v file,network --loglevel debug --logpath /tmp
And got:
D  DownloadManager: Aborting download - lack of data transfer
E  DataDirect: Failed to get data: Download error
E  Encountered error in grabbing data.
E  Failed to fetch some program info

I also tried:
tv_grab_na_dd --dd-data /tmp/sched2-dd.xml > /tmp/sched2.xml
mythfilldatabase --dd-file --sourceid DVB --lineupid 80503 --offset 0 --xmlfile /tmp/sched2-dd.xml

However, there is no documentation for the arguments to --sourceid --lineupid or --offset.  Mythfilldatabase doesn't seem to do any sanity checking and just bombs along with garbage inputs.  It prints lots of stuff, but I still don't have a schedule.

Does anybody either know a way to debug mythfilldatabase or know how to load the data that tv_grab_na_dd retrieves?

I'm running mythbackend version 0.25.2+fixes.20121002.139bd59-0ubuntu0mythbuntu4 on 64bit ubuntu 12.04 with all updates.

Thanks,
-Dan

---

