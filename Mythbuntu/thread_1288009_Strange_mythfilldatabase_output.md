---
title: "Strange mythfilldatabase output"
date: 2009-10-10
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-10
**What does this output mean; I get it after typing "mythfilldatabase"**

Saving to: `STDOUT'

    [                   <=>                                                                                              ] 193,826     41.7K/s   in 13s     

2009-10-10 19:53:22 (14.4 KB/s) - `-' saved [193826]

2009-10-10 19:53:22.820 DataDirect: WARNING: Your subscription expires on 10/14/2009 06:23:14 PM
2009-10-10 19:53:32.932 Grab complete.  Actual data from Wed Oct 21 05:00:00 2009 to Thu Oct 22 05:00:00 2009 (UTC)
2009-10-10 19:53:32.933 Main temp tables populated.
2009-10-10 19:53:33.140 Did not find any new program data.
2009-10-10 19:53:33.140 
2009-10-10 19:53:33.140 Checking day @ offset 12, date: Thu Oct 22 2009
2009-10-10 19:53:33.142 Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2009-10-10 19:53:33.142 Refreshing data for Thu Oct 22 2009
2009-10-10 19:53:33.143 Retrieving datadirect data.
2009-10-10 19:53:33.143 Grabbing data for Sat Oct 10 2009 offset 12
2009-10-10 19:53:33.143 From Thu Oct 22 05:00:00 2009 to Fri Oct 23 05:00:00 2009 (UTC)
2009-10-10 19:53:33.143 Grabbing listing data
--2009-10-10 19:53:33--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                     <=>                                                                                            ] 195,635     41.2K/s   in 15s     

2009-10-10 19:53:49 (12.4 KB/s) - `-' saved [195635]

2009-10-10 19:53:49.107 DataDirect: WARNING: Your subscription expires on 10/14/2009 06:23:14 PM
2009-10-10 19:54:03.649 Grab complete.  Actual data from Thu Oct 22 05:00:00 2009 to Fri Oct 23 05:00:00 2009 (UTC)
2009-10-10 19:54:03.649 Main temp tables populated.
2009-10-10 19:54:03.783 Did not find any new program data.
2009-10-10 19:54:03.784 
2009-10-10 19:54:03.784 Checking day @ offset 13, date: Fri Oct 23 2009
2009-10-10 19:54:03.785 Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2009-10-10 19:54:03.785 Refreshing data for Fri Oct 23 2009
2009-10-10 19:54:03.786 Retrieving datadirect data.
2009-10-10 19:54:03.786 Grabbing data for Sat Oct 10 2009 offset 13
2009-10-10 19:54:03.786 From Fri Oct 23 05:00:00 2009 to Sat Oct 24 05:00:00 2009 (UTC)
2009-10-10 19:54:03.786 Grabbing listing data
--2009-10-10 19:54:03--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                   <=>                                                                                              ] 189,964     38.6K/s   in 14s     

2009-10-10 19:54:18 (13.2 KB/s) - `-' saved [189964]

2009-10-10 19:54:18.304 DataDirect: WARNING: Your subscription expires on 10/14/2009 06:23:14 PM
2009-10-10 19:54:29.629 Grab complete.  Actual data from Fri Oct 23 05:00:00 2009 to Sat Oct 24 05:00:00 2009 (UTC)
2009-10-10 19:54:29.630 Main temp tables populated.
2009-10-10 19:54:29.776 Did not find any new program data.
2009-10-10 19:54:29.776 Failed to fetch some program info
2009-10-10 19:54:29.776 Adjusting program database end times.
2009-10-10 19:54:29.777     0 replacements made
2009-10-10 19:54:29.777 Marking generic episodes.
2009-10-10 19:54:29.778     Found 0
2009-10-10 19:54:29.778 Marking repeats.
2009-10-10 19:54:29.780     Found 0
2009-10-10 19:54:29.780 Unmarking new episode rebroadcast repeats.
2009-10-10 19:54:29.780     Found 0
2009-10-10 19:54:29.781 Marking episode first showings.
2009-10-10 19:54:29.782     Found 0
2009-10-10 19:54:29.782 Marking episode last showings.
2009-10-10 19:54:29.782     Found 0
2009-10-10 19:54:29.784 Grabbing next suggested grabbing time
2009-10-10 19:54:30.267 DataDirect: BlockedTime is: 2009-10-10T19:54:30
2009-10-10 19:54:30.268 DataDirect: NextSuggestedTime is: 2009-10-11T19:45:20
2009-10-10 19:54:30.271 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-10-10 19:54:30.277 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-10 19:54:30.277 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-10-10 19:54:30.280 Error rescheduling id -1 in ScheduledRecording::signalChange
2009-10-10 19:54:30.280 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-10 19:54:30.280 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-10-10 19:54:30.281 mythfilldatabase run complete.
2009-10-10 19:54:30.281 DataDirect: Deleting temporary files
mythregular@mythcpu:~$ 

**I have an SD account and created a "line-up" but still get this message.  What should I do?**

---

