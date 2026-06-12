---
title: "What does this mythbuntu / schedules direct terminal output mean?"
date: 2009-11-06
forum: Mythbuntu
---

### Post by cat2005 on 2009-11-06
[B]I ran "mythfilldatabase" once, but because I didn't have a chance to examine the output, I ran it again in terminal.  If I understand this output correctly, then it is having trouble connecting to my backend server.  Am I correct?

I do not fully understand the output and would appreciate your input!  Here it is:[/B] 

mythprime@mythcpu:~$ mythfilldatabase
2009-11-06 18:38:46.097 Using runtime prefix = /usr
2009-11-06 18:38:46.098 Empty LocalHostName.
2009-11-06 18:38:46.099 Using localhost value of mythcpu
2009-11-06 18:38:46.110 New DB connection, total: 1
2009-11-06 18:38:46.115 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:38:46.116 Closing DB connection named 'DBManager0'
2009-11-06 18:38:46.117 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:38:46.122 New DB connection, total: 2
2009-11-06 18:38:46.131 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:38:46.382 Updating source #1 (PVR150) with grabber schedulesdirect1
2009-11-06 18:38:46.383 Found 81 channels for source 1 which use grabber
2009-11-06 18:38:46.383 
2009-11-06 18:38:46.383 Checking day @ offset 0, date: Fri Nov 6 2009
2009-11-06 18:38:46.512 Data is already present for Fri Nov 6 2009, skipping
2009-11-06 18:38:46.512 
2009-11-06 18:38:46.512 Checking day @ offset 1, date: Sat Nov 7 2009
2009-11-06 18:38:46.512 Data Refresh always needed for tomorrow
2009-11-06 18:38:46.512 Refreshing data for Sat Nov 7 2009
2009-11-06 18:38:46.513 New DB DataDirect connection
2009-11-06 18:38:46.513 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:38:46.514 Retrieving datadirect data.
2009-11-06 18:38:46.514 Grabbing data for Fri Nov 6 2009 offset 1
2009-11-06 18:38:46.515 From Sat Nov 7 06:00:00 2009 to Sun Nov 8 06:00:00 2009 (UTC)
2009-11-06 18:38:46.515 Grabbing listing data
--2009-11-06 18:38:46--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                  <=>                                                                ] 194,083     44.6K/s   in 12s     

2009-11-06 18:38:59 (15.4 KB/s) - `-' saved [194083]

2009-11-06 18:38:59.335 DataDirect: Your subscription expires on 11/04/2010 03:18:38 PM
2009-11-06 18:38:59.433 New DB connection, total: 3
2009-11-06 18:38:59.434 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:38:59.434 sourceid 1 has lineup type: Cable
2009-11-06 18:39:09.192 Grab complete.  Actual data from Sat Nov 7 06:00:00 2009 to Sun Nov 8 06:00:00 2009 (UTC)
2009-11-06 18:39:09.192 Main temp tables populated.
2009-11-06 18:39:09.193 Updating myth channels.
2009-11-06 18:39:09.215 Updating icons for sourceid: 1
2009-11-06 18:39:09.215 Channels updated.
2009-11-06 18:39:09.425 Clearing data for source.
2009-11-06 18:39:09.425 Clearing from Sat Nov 7 00:00:00 2009 to Sun Nov 8 00:00:00 2009 (localtime)
2009-11-06 18:39:09.426 New DB connection, total: 4
2009-11-06 18:39:09.427 Connected to database 'mythconverg' at host: localhost
2009-11-06 18:39:10.666 Data for source cleared.
2009-11-06 18:39:10.666 Updating programs.
2009-11-06 18:39:12.859 Program table update complete.
2009-11-06 18:39:12.859 
2009-11-06 18:39:12.859 Checking day @ offset 2, date: Sun Nov 8 2009
2009-11-06 18:39:13.068 Data is already present for Sun Nov 8 2009, skipping
2009-11-06 18:39:13.068 
2009-11-06 18:39:13.068 Checking day @ offset 3, date: Mon Nov 9 2009
2009-11-06 18:39:13.269 Data is already present for Mon Nov 9 2009, skipping
2009-11-06 18:39:13.269 
2009-11-06 18:39:13.269 Checking day @ offset 4, date: Tue Nov 10 2009
2009-11-06 18:39:13.470 Data is already present for Tue Nov 10 2009, skipping
2009-11-06 18:39:13.470 
2009-11-06 18:39:13.470 Checking day @ offset 5, date: Wed Nov 11 2009
2009-11-06 18:39:13.671 Data is already present for Wed Nov 11 2009, skipping
2009-11-06 18:39:13.671 
2009-11-06 18:39:13.672 Checking day @ offset 6, date: Thu Nov 12 2009
2009-11-06 18:39:13.861 Data is already present for Thu Nov 12 2009, skipping
2009-11-06 18:39:13.861 
2009-11-06 18:39:13.861 Checking day @ offset 7, date: Fri Nov 13 2009
2009-11-06 18:39:14.055 Data is already present for Fri Nov 13 2009, skipping
2009-11-06 18:39:14.055 
2009-11-06 18:39:14.055 Checking day @ offset 8, date: Sat Nov 14 2009
2009-11-06 18:39:14.241 Data is already present for Sat Nov 14 2009, skipping
2009-11-06 18:39:14.241 
2009-11-06 18:39:14.241 Checking day @ offset 9, date: Sun Nov 15 2009
2009-11-06 18:39:14.426 Data is already present for Sun Nov 15 2009, skipping
2009-11-06 18:39:14.426 
2009-11-06 18:39:14.426 Checking day @ offset 10, date: Mon Nov 16 2009
2009-11-06 18:39:14.613 Data is already present for Mon Nov 16 2009, skipping
2009-11-06 18:39:14.613 
2009-11-06 18:39:14.613 Checking day @ offset 11, date: Tue Nov 17 2009
2009-11-06 18:39:14.795 Data is already present for Tue Nov 17 2009, skipping
2009-11-06 18:39:14.795 
2009-11-06 18:39:14.795 Checking day @ offset 12, date: Wed Nov 18 2009
2009-11-06 18:39:14.979 Data is already present for Wed Nov 18 2009, skipping
2009-11-06 18:39:14.979 
2009-11-06 18:39:14.979 Checking day @ offset 13, date: Thu Nov 19 2009
2009-11-06 18:39:15.161 Data is already present for Thu Nov 19 2009, skipping
2009-11-06 18:39:15.493 Data fetching complete.
2009-11-06 18:39:15.493 Adjusting program database end times.
2009-11-06 18:39:16.777     0 replacements made
2009-11-06 18:39:16.777 Marking generic episodes.
2009-11-06 18:39:17.179     Found 463
2009-11-06 18:39:17.180 Marking repeats.
2009-11-06 18:39:17.572     Found 1278
2009-11-06 18:39:17.572 Unmarking new episode rebroadcast repeats.
2009-11-06 18:39:17.921     Found 0
2009-11-06 18:39:18.681 Marking episode first showings.
2009-11-06 18:39:28.927     Found 13093
2009-11-06 18:39:28.927 Marking episode last showings.
2009-11-06 18:39:39.545     Found 13093
2009-11-06 18:39:39.602 Grabbing next suggested grabbing time
2009-11-06 18:39:40.087 DataDirect: BlockedTime is: 2009-11-06T18:39:40
2009-11-06 18:39:40.088 DataDirect: NextSuggestedTime is: 2009-11-07T18:38:50
2009-11-06 18:39:40.091 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-11-06 18:39:40.097 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-11-06 18:39:40.098 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-11-06 18:39:40.098 Error rescheduling id -1 in ScheduledRecording::signalChange
2009-11-06 18:39:40.098 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-11-06 18:39:40.098 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-11-06 18:39:40.099 mythfilldatabase run complete.
2009-11-06 18:39:40.099 DataDirect: Deleting temporary files
mythprime@mythcpu:~$

[B]This was what I received using "_us-cable_".  

Thank you.[/B]

---

### Post by cat2005 on 2009-11-06
**This is what I received using "_us-cable-hrc_" (I chopped off the upper half, which was the same as the upper half in the prior post)**

009-11-06 18:52:32.281 Checking day @ offset 12, date: Wed Nov 18 2009
2009-11-06 18:52:32.463 Data is already present for Wed Nov 18 2009, skipping
2009-11-06 18:52:32.463 
2009-11-06 18:52:32.463 Checking day @ offset 13, date: Thu Nov 19 2009
2009-11-06 18:52:32.642 Data is already present for Thu Nov 19 2009, skipping
2009-11-06 18:52:32.970 Data fetching complete.
2009-11-06 18:52:32.970 Adjusting program database end times.
2009-11-06 18:52:34.213     0 replacements made
2009-11-06 18:52:34.214 Marking generic episodes.
2009-11-06 18:52:34.567     Found 463
2009-11-06 18:52:34.567 Marking repeats.
2009-11-06 18:52:34.911     Found 1278
2009-11-06 18:52:34.911 Unmarking new episode rebroadcast repeats.
2009-11-06 18:52:35.217     Found 0
2009-11-06 18:52:35.889 Marking episode first showings.
2009-11-06 18:52:46.184     Found 13093
2009-11-06 18:52:46.184 Marking episode last showings.
2009-11-06 18:52:57.202     Found 13093
2009-11-06 18:52:57.259 Grabbing next suggested grabbing time
2009-11-06 18:52:57.761 DataDirect: BlockedTime is: 2009-11-06T18:52:57
2009-11-06 18:52:57.762 DataDirect: NextSuggestedTime is: 2009-11-07T17:42:05
2009-11-06 18:52:57.765 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-11-06 18:52:57.771 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-11-06 18:52:57.773 Using protocol version 40
2009-11-06 18:52:58.377 Received a remote 'Clear Cache' request
2009-11-06 18:52:58.379 mythfilldatabase run complete.
2009-11-06 18:52:58.437 DataDirect: Deleting temporary files
mythprime@mythcpu:~/Desktop$ 

[B]I noticed this time there was no strange message regarding the "backend" (see prior post, above this).  Since I don't have that strange message, then am I ready to watch TV?

I am afraid to proceed until someone with more knowledge can help explain what just happened / did not happen.

Thank you again so much![/B]

---

