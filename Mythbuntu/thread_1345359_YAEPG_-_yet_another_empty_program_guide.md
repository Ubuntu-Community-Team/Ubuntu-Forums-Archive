---
title: "YAEPG - yet another empty program guide"
date: 2009-12-04
forum: Mythbuntu
---

### Post by MountainX on 2009-12-04
Running Mythbuntu 9.10 with latest updates as of today. 
The frontend running on this machine doesn't have any program guide data from my cable TV video source. 
 
I have a schedulesdirect.org subscription and I have a lineup added (and I re-added, as I saw suggested for troubleshooting). Mythfilldatabase is running (and I have manually rerun it several times today).
 
My main tuner card is an PVR-150 and it is configured with the video source that uses schedulesdirect.org.
 
What else can I do to resolve this?
 
Here is the output from mythfilldatabase:

```
me@myMythBE:/$ sudo mythfilldatabase 
2009-12-03 23:04:21.252 Using runtime prefix = /usr
2009-12-03 23:04:21.252 Using configuration directory = /home/me/.mythtv
2009-12-03 23:04:21.253 Empty LocalHostName.
2009-12-03 23:04:21.253 Using localhost value of myMythBE
2009-12-03 23:04:21.263 New DB connection, total: 1
2009-12-03 23:04:21.270 Connected to database 'mythconverg' at host: localhost
2009-12-03 23:04:21.270 Closing DB connection named 'DBManager0'
2009-12-03 23:04:21.271 Connected to database 'mythconverg' at host: localhost
2009-12-03 23:04:21.276 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-03 23:04:21.280 New DB connection, total: 2
2009-12-03 23:04:21.281 Connected to database 'mythconverg' at host: localhost
2009-12-03 23:04:21.283 Updating source #2 (ComcastDigitalCable) with grabber schedulesdirect1
2009-12-03 23:04:21.284 No channels are configured to use grabber.
2009-12-03 23:04:21.284 
2009-12-03 23:04:21.284 Checking day @ offset 0, date: Thu Dec 3 2009
2009-12-03 23:04:21.286 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2009-12-03 23:04:21.286 Refreshing data for Thu Dec 3 2009
2009-12-03 23:04:21.286 New DB DataDirect connection
2009-12-03 23:04:21.287 Connected to database 'mythconverg' at host: localhost
2009-12-03 23:04:21.289 Retrieving datadirect data.
2009-12-03 23:04:21.289 Grabbing data for Thu Dec 3 2009 offset 0
2009-12-03 23:04:21.289 From Thu Dec 3 05:00:00 2009 to Fri Dec 4 05:00:00 2009 (UTC)
2009-12-03 23:04:21.290 Grabbing listing data
--2009-12-03 23:04:21--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                                  <=>  ] 30,886      1.43K/s              2009-12-03 23:04:55.051 New DB connection, total: 3
2009-12-03 23:04:55.051 Connected to database 'mythconverg' at host: localhost
2009-12-03 23:04:55.054 DataDirect: Your subscription expires on Thu Jan 7 (2010) 9:12 PM
2009-12-03 23:04:55.430 sourceid 2 has lineup type: CableDigital
    [   <=>                                 ] 522,842     30.3K/s   in 63s     

2009-12-03 23:05:26 (8.08 KB/s) - `-' saved [522842]

2009-12-03 23:05:31.715 Grab complete.  Actual data from Thu Dec 3 05:00:00 2009 to Fri Dec 4 05:00:00 2009 (UTC)
2009-12-03 23:05:31.715 Main temp tables populated.
2009-12-03 23:05:31.715 Updating myth channels.
2009-12-03 23:05:31.793 SourceUtil::IsProperlyConnected(): Source ID 2 appears to be connected
            to 1 scanable input, and 3 non-scanable inputs. This may be a problem.
2009-12-03 23:05:31.794 IconData: Updating icons for sourceid: 2
2009-12-03 23:05:31.795 Channels updated.
2009-12-03 23:05:31.946 Did not find any new program data.
2009-12-03 23:05:31.946 
2009-12-03 23:05:31.946 Checking day @ offset 1, date: Fri Dec 4 2009
2009-12-03 23:05:31.946 Data Refresh always needed for tomorrow
2009-12-03 23:05:31.946 Refreshing data for Fri Dec 4 2009
2009-12-03 23:05:31.947 Retrieving datadirect data.
2009-12-03 23:05:31.947 Grabbing data for Thu Dec 3 2009 offset 1
2009-12-03 23:05:31.947 From Fri Dec 4 05:00:00 2009 to Sat Dec 5 05:00:00 2009 (UTC)
2009-12-03 23:05:31.947 Grabbing listing data
--2009-12-03 23:05:31--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                                <=>    ] 30,858      1.43K/s              2009-12-03 23:06:03.608 DataDirect: Your subscription expires on Thu Jan 7 (2010) 9:12 PM
    [           <=>                         ] 521,450     31.8K/s   in 55s     

2009-12-03 23:06:30 (9.20 KB/s) - `-' saved [521450]

2009-12-03 23:06:35.975 Grab complete.  Actual data from Fri Dec 4 05:00:00 2009 to Sat Dec 5 05:00:00 2009 (UTC)
2009-12-03 23:06:35.976 Main temp tables populated.
2009-12-03 23:06:36.127 Did not find any new program data.
2009-12-03 23:06:36.127 
2009-12-03 23:06:36.127 Checking day @ offset 2, date: Sat Dec 5 2009
[snip...]
2009-12-03 23:17:24.861 Did not find any new program data.
2009-12-03 23:17:24.861 
2009-12-03 23:17:24.861 Checking day @ offset 13, date: Wed Dec 16 2009
2009-12-03 23:17:24.862 Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2009-12-03 23:17:24.862 Refreshing data for Wed Dec 16 2009
2009-12-03 23:17:24.863 Retrieving datadirect data.
2009-12-03 23:17:24.863 Grabbing data for Thu Dec 3 2009 offset 13
2009-12-03 23:17:24.863 From Wed Dec 16 05:00:00 2009 to Thu Dec 17 05:00:00 2009 (UTC)
2009-12-03 23:17:24.863 Grabbing listing data
--2009-12-03 23:17:24--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

    [                           <=>         ] 31,032      1.43K/s              2009-12-03 23:17:50.978 DataDirect: Your subscription expires on Thu Jan 7 (2010) 9:12 PM
    [                 <=>                   ] 491,946     31.1K/s   in 49s     

2009-12-03 23:18:16 (9.75 KB/s) - `-' saved [491946]

2009-12-03 23:18:22.059 Grab complete.  Actual data from Wed Dec 16 05:00:00 2009 to Thu Dec 17 05:00:00 2009 (UTC)
2009-12-03 23:18:22.060 Main temp tables populated.
2009-12-03 23:18:22.277 Did not find any new program data.
2009-12-03 23:18:22.278 Source 3 configured to use only the broadcasted guide data. Skipping.
2009-12-03 23:18:22.279 Failed to fetch some program info
2009-12-03 23:18:22.279 Adjusting program database end times.
2009-12-03 23:18:22.280     0 replacements made
2009-12-03 23:18:22.280 Marking generic episodes.
2009-12-03 23:18:22.280     Found 0
2009-12-03 23:18:22.280 Fudging non-unique programids with multiple parts.
2009-12-03 23:18:22.281     Found -1
2009-12-03 23:18:22.281 Marking repeats.
2009-12-03 23:18:22.282     Found 0
2009-12-03 23:18:22.282 Unmarking new episode rebroadcast repeats.
2009-12-03 23:18:22.283     Found 0
2009-12-03 23:18:22.283 Marking episode first showings.
2009-12-03 23:18:22.283     Found 0
2009-12-03 23:18:22.283 Marking episode last showings.
2009-12-03 23:18:22.284     Found 0
2009-12-03 23:18:22.286 Grabbing next suggested grabbing time
2009-12-03 23:18:22.814 DataDirect: BlockedTime is: 2009-12-03T23:18:22
2009-12-03 23:18:22.815 DataDirect: NextSuggestedTime is: 2009-12-04T22:52:15
2009-12-03 23:18:22.820 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-12-03 23:18:22.828 MythContext: Connecting to backend server: 192.168.2.7:6543 (try 1 of 1)
QWidget: Cannot create a QWidget when no GUI is being used

```

---

### Post by cooper814 on 2010-04-11
I'm having the EXACT same problem with a HVR-2250 - same "No channels are configured to use grabber" and "Did not find any new program data" errors.
If you were able to resolve this problem, I'd love to know how!

---

