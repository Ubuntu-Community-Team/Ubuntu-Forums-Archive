---
title: "I have no channel listings."
date: 2008-04-28
forum: Mythbuntu
---

### Post by DucoNihilum on 2008-04-28
When I try to run mythfilldatabase I get several errors, I haven't had channel listings for some time now. 

Here's a snipit 

 Updating programs.
2008-04-28 19:47:51.093 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:47:53.002 Program table update complete.
2008-04-28 19:47:53.004 Failed to fetch some program info
2008-04-28 19:47:53.004 Adjusting program database end times.


how can i fix this?

---

### Post by DucoNihilum on 2008-04-28
FULL LOG BELOW

Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:37:42.388 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                           ] 195,782       75.64K/s             

19:37:45 (75.56 KB/s) - `-' saved [195782]

2008-04-28 19:37:45.691 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:38:05.713 Grab complete.  Actual data from Fri May 2 05:00:00 2008 to Sat May 3 05:00:00 2008 (UTC)
2008-04-28 19:38:05.714 Main temp tables populated.
2008-04-28 19:38:05.734 Did not find any new program data.
2008-04-28 19:38:05.734 
2008-04-28 19:38:05.734 Checking day @ offset 5, date: Sat May 3 2008
2008-04-28 19:38:05.736 Data Refresh because we are unable to query the data for day @ offset 4 to determine how much we should have for offset day 5.
2008-04-28 19:38:05.736 Refreshing data for Sat May 3 2008
2008-04-28 19:38:05.736 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:38:05.736 We should keep data around after this one
2008-04-28 19:38:05.737 Retrieving datadirect data.
2008-04-28 19:38:05.737 Grabbing data for Mon Apr 28 2008 offset 5
2008-04-28 19:38:05.738 From Sat May 3 05:00:00 2008 to Sun May 4 05:00:00 2008 (UTC)
2008-04-28 19:38:05.738 Grabbing listing data
--19:38:05--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:38:05.773 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 179,087       78.35K/s             

19:38:08 (78.26 KB/s) - `-' saved [179087]

2008-04-28 19:38:08.745 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:38:25.966 Grab complete.  Actual data from Sat May 3 05:00:00 2008 to Sun May 4 05:00:00 2008 (UTC)
2008-04-28 19:38:25.967 Main temp tables populated.
2008-04-28 19:38:25.983 Did not find any new program data.
2008-04-28 19:38:25.984 
2008-04-28 19:38:25.984 Checking day @ offset 6, date: Sun May 4 2008
2008-04-28 19:38:25.985 Data Refresh because we are unable to query the data for day @ offset 5 to determine how much we should have for offset day 6.
2008-04-28 19:38:25.986 Refreshing data for Sun May 4 2008
2008-04-28 19:38:25.986 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:38:25.986 We should keep data around after this one
2008-04-28 19:38:25.987 Retrieving datadirect data.
2008-04-28 19:38:25.987 Grabbing data for Mon Apr 28 2008 offset 6
2008-04-28 19:38:25.987 From Sun May 4 05:00:00 2008 to Mon May 5 05:00:00 2008 (UTC)
2008-04-28 19:38:25.987 Grabbing listing data
--19:38:26--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:38:26.026 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 175,268       80.08K/s             

19:38:28 (79.92 KB/s) - `-' saved [175268]

2008-04-28 19:38:28.750 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:38:46.244 Grab complete.  Actual data from Sun May 4 05:00:00 2008 to Mon May 5 05:00:00 2008 (UTC)
2008-04-28 19:38:46.245 Main temp tables populated.
2008-04-28 19:38:46.262 Did not find any new program data.
2008-04-28 19:38:46.262 
2008-04-28 19:38:46.262 Checking day @ offset 7, date: Mon May 5 2008
2008-04-28 19:38:46.264 Data Refresh because we are unable to query the data for day @ offset 6 to determine how much we should have for offset day 7.
2008-04-28 19:38:46.264 Refreshing data for Mon May 5 2008
2008-04-28 19:38:46.264 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:38:46.264 We should keep data around after this one
2008-04-28 19:38:46.265 Retrieving datadirect data.
2008-04-28 19:38:46.266 Grabbing data for Mon Apr 28 2008 offset 7
2008-04-28 19:38:46.266 From Mon May 5 05:00:00 2008 to Tue May 6 05:00:00 2008 (UTC)
2008-04-28 19:38:46.266 Grabbing listing data
--19:38:46--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:38:46.310 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                           ] 193,258       84.27K/s             

19:38:49 (84.20 KB/s) - `-' saved [193258]

2008-04-28 19:38:49.185 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:39:09.014 Grab complete.  Actual data from Mon May 5 05:00:00 2008 to Tue May 6 05:00:00 2008 (UTC)
2008-04-28 19:39:09.015 Main temp tables populated.
2008-04-28 19:39:09.033 Did not find any new program data.
2008-04-28 19:39:09.033 
2008-04-28 19:39:09.034 Checking day @ offset 8, date: Tue May 6 2008
2008-04-28 19:39:09.035 Data Refresh because we are unable to query the data for day @ offset 7 to determine how much we should have for offset day 8.
2008-04-28 19:39:09.035 Refreshing data for Tue May 6 2008
2008-04-28 19:39:09.035 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:39:09.036 We should keep data around after this one
2008-04-28 19:39:09.036 Retrieving datadirect data.
2008-04-28 19:39:09.037 Grabbing data for Mon Apr 28 2008 offset 8
2008-04-28 19:39:09.037 From Tue May 6 05:00:00 2008 to Wed May 7 05:00:00 2008 (UTC)
2008-04-28 19:39:09.037 Grabbing listing data
--19:39:09--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:39:09.072 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                           ] 188,829       64.67K/s             

19:39:12 (64.64 KB/s) - `-' saved [188829]

2008-04-28 19:39:12.539 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:39:31.979 Grab complete.  Actual data from Tue May 6 05:00:00 2008 to Wed May 7 05:00:00 2008 (UTC)
2008-04-28 19:39:31.980 Main temp tables populated.
2008-04-28 19:39:31.999 Did not find any new program data.
2008-04-28 19:39:31.999 
2008-04-28 19:39:32.000 Checking day @ offset 9, date: Wed May 7 2008
2008-04-28 19:39:32.001 Data Refresh because we are unable to query the data for day @ offset 8 to determine how much we should have for offset day 9.
2008-04-28 19:39:32.001 Refreshing data for Wed May 7 2008
2008-04-28 19:39:32.002 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:39:32.002 We should keep data around after this one
2008-04-28 19:39:32.003 Retrieving datadirect data.
2008-04-28 19:39:32.003 Grabbing data for Mon Apr 28 2008 offset 9
2008-04-28 19:39:32.003 From Wed May 7 05:00:00 2008 to Thu May 8 05:00:00 2008 (UTC)
2008-04-28 19:39:32.004 Grabbing listing data
--19:39:32--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:39:32.042 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 189,670       84.15K/s             

19:39:34 (83.99 KB/s) - `-' saved [189670]

2008-04-28 19:39:34.857 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:39:54.214 Grab complete.  Actual data from Wed May 7 05:00:00 2008 to Thu May 8 05:00:00 2008 (UTC)
2008-04-28 19:39:54.215 Main temp tables populated.
2008-04-28 19:39:54.237 Did not find any new program data.
2008-04-28 19:39:54.238 
2008-04-28 19:39:54.238 Checking day @ offset 10, date: Thu May 8 2008
2008-04-28 19:39:54.241 Data Refresh because we are unable to query the data for day @ offset 9 to determine how much we should have for offset day 10.
2008-04-28 19:39:54.272 Refreshing data for Thu May 8 2008
2008-04-28 19:39:54.272 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:39:54.272 We should keep data around after this one
2008-04-28 19:39:54.273 Retrieving datadirect data.
2008-04-28 19:39:54.273 Grabbing data for Mon Apr 28 2008 offset 10
2008-04-28 19:39:54.274 From Thu May 8 05:00:00 2008 to Fri May 9 05:00:00 2008 (UTC)
2008-04-28 19:39:54.274 Grabbing listing data
--19:39:54--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:39:54.282 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [            <=>                      ] 189,483       56.36K/s             

19:39:58 (56.26 KB/s) - `-' saved [189483]

2008-04-28 19:39:58.239 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:40:17.898 Grab complete.  Actual data from Thu May 8 05:00:00 2008 to Fri May 9 05:00:00 2008 (UTC)
2008-04-28 19:40:17.899 Main temp tables populated.
2008-04-28 19:40:17.917 Did not find any new program data.
2008-04-28 19:40:17.918 
2008-04-28 19:40:17.918 Checking day @ offset 11, date: Fri May 9 2008
2008-04-28 19:40:17.920 Data Refresh because we are unable to query the data for day @ offset 10 to determine how much we should have for offset day 11.
2008-04-28 19:40:17.920 Refreshing data for Fri May 9 2008
2008-04-28 19:40:17.920 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:40:17.920 We should keep data around after this one
2008-04-28 19:40:17.921 Retrieving datadirect data.
2008-04-28 19:40:17.921 Grabbing data for Mon Apr 28 2008 offset 11
2008-04-28 19:40:17.921 From Fri May 9 05:00:00 2008 to Sat May 10 05:00:00 2008 (UTC)
2008-04-28 19:40:17.922 Grabbing listing data
--19:40:17--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:40:17.960 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 186,158       90.22K/s             

19:40:20 (90.12 KB/s) - `-' saved [186158]

2008-04-28 19:40:20.681 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:40:39.949 Grab complete.  Actual data from Fri May 9 05:00:00 2008 to Sat May 10 05:00:00 2008 (UTC)
2008-04-28 19:40:39.950 Main temp tables populated.
2008-04-28 19:40:39.969 Did not find any new program data.
2008-04-28 19:40:39.969 
2008-04-28 19:40:39.970 Checking day @ offset 12, date: Sat May 10 2008
2008-04-28 19:40:39.971 Data Refresh because we are unable to query the data for day @ offset 11 to determine how much we should have for offset day 12.
2008-04-28 19:40:39.971 Refreshing data for Sat May 10 2008
2008-04-28 19:40:39.971 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:40:39.972 We should keep data around after this one
2008-04-28 19:40:39.972 Retrieving datadirect data.
2008-04-28 19:40:39.973 Grabbing data for Mon Apr 28 2008 offset 12
2008-04-28 19:40:39.973 From Sat May 10 05:00:00 2008 to Sun May 11 05:00:00 2008 (UTC)
2008-04-28 19:40:39.973 Grabbing listing data
--19:40:40--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:40:40.012 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 165,281       77.43K/s             

19:40:47 (77.40 KB/s) - `-' saved [165281]

2008-04-28 19:40:47.767 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:41:04.221 Grab complete.  Actual data from Sat May 10 05:00:00 2008 to Sun May 11 05:00:00 2008 (UTC)
2008-04-28 19:41:04.223 Main temp tables populated.
2008-04-28 19:41:04.238 Did not find any new program data.
2008-04-28 19:41:04.239 
2008-04-28 19:41:04.239 Checking day @ offset 13, date: Sun May 11 2008
2008-04-28 19:41:04.241 Data Refresh because we are unable to query the data for day @ offset 12 to determine how much we should have for offset day 13.
2008-04-28 19:41:04.241 Refreshing data for Sun May 11 2008
2008-04-28 19:41:04.241 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:41:04.241 We should keep data around after this one
2008-04-28 19:41:04.242 Retrieving datadirect data.
2008-04-28 19:41:04.242 Grabbing data for Mon Apr 28 2008 offset 13
2008-04-28 19:41:04.242 From Sun May 11 05:00:00 2008 to Mon May 12 05:00:00 2008 (UTC)
2008-04-28 19:41:04.243 Grabbing listing data
--19:41:04--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 2008-04-28 19:41:04.277 DataDirect: Saving listings to DD cache
206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 165,850       66.55K/s             

19:41:07 (66.44 KB/s) - `-' saved [165850]

2008-04-28 19:41:07.420 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:41:24.191 Grab complete.  Actual data from Sun May 11 05:00:00 2008 to Mon May 12 05:00:00 2008 (UTC)
2008-04-28 19:41:24.192 Main temp tables populated.
2008-04-28 19:41:24.209 Did not find any new program data.
2008-04-28 19:41:24.213 Updating source #2 (Schedules Direct) with grabber schedulesdirect1
2008-04-28 19:41:24.214 Found 79 channels for source 2 which use grabber
2008-04-28 19:41:24.214 
2008-04-28 19:41:24.214 Checking day @ offset 0, date: Mon Apr 28 2008
2008-04-28 19:41:24.241 Data Refresh because we are unable to query the data for day @ offset -1 to determine how much we should have for offset day 0.
2008-04-28 19:41:24.241 Refreshing data for Mon Apr 28 2008
2008-04-28 19:41:24.241 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:41:24.241 We should use cached data for this one
2008-04-28 19:41:24.242 Retrieving datadirect data.
2008-04-28 19:41:24.243 Grabbing data for Mon Apr 28 2008 offset 0
2008-04-28 19:41:24.243 From Mon Apr 28 05:00:00 2008 to Tue Apr 29 05:00:00 2008 (UTC)
2008-04-28 19:41:24.243 Grabbing listing data
2008-04-28 19:41:24.244 DataDirect: Copying from DD cache
2008-04-28 19:41:24.370 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:41:45.100 Grab complete.  Actual data from Mon Apr 28 05:00:00 2008 to Tue Apr 29 05:00:00 2008 (UTC)
2008-04-28 19:41:45.102 Main temp tables populated.
2008-04-28 19:41:45.102 Updating myth channels.
2008-04-28 19:41:45.126 Updating icons for sourceid: 2
2008-04-28 19:41:45.128 Channels updated.
2008-04-28 19:41:45.400 Clearing data for source.
2008-04-28 19:41:45.401 Clearing from Mon Apr 28 00:00:00 2008 to Tue Apr 29 00:00:00 2008 (localtime)
2008-04-28 19:41:45.403 New DB connection, total: 4
2008-04-28 19:41:45.404 Connected to database 'mythconverg' at host: localhost
2008-04-28 19:42:15.245 Data for source cleared.
2008-04-28 19:42:15.245 Updating programs.
2008-04-28 19:42:15.248 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:42:31.120 Program table update complete.
2008-04-28 19:42:31.120 
2008-04-28 19:42:31.120 Checking day @ offset 1, date: Tue Apr 29 2008
2008-04-28 19:42:31.120 Data Refresh always needed for tomorrow
2008-04-28 19:42:31.120 Refreshing data for Tue Apr 29 2008
2008-04-28 19:42:31.120 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:42:31.120 We should use cached data for this one
2008-04-28 19:42:31.125 Retrieving datadirect data.
2008-04-28 19:42:31.125 Grabbing data for Mon Apr 28 2008 offset 1
2008-04-28 19:42:31.125 From Tue Apr 29 05:00:00 2008 to Wed Apr 30 05:00:00 2008 (UTC)
2008-04-28 19:42:31.125 Grabbing listing data
2008-04-28 19:42:31.125 DataDirect: Copying from DD cache
2008-04-28 19:42:31.256 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:42:52.463 Grab complete.  Actual data from Tue Apr 29 05:00:00 2008 to Wed Apr 30 05:00:00 2008 (UTC)
2008-04-28 19:42:52.465 Main temp tables populated.
2008-04-28 19:42:52.765 Clearing data for source.
2008-04-28 19:42:52.765 Clearing from Tue Apr 29 00:00:00 2008 to Wed Apr 30 00:00:00 2008 (localtime)
2008-04-28 19:42:59.888 Data for source cleared.
2008-04-28 19:42:59.888 Updating programs.
2008-04-28 19:42:59.890 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:43:08.046 Program table update complete.
2008-04-28 19:43:08.047 
2008-04-28 19:43:08.047 Checking day @ offset 2, date: Wed Apr 30 2008
2008-04-28 19:43:08.049 Data Refresh because we are unable to query the data for day @ offset 1 to determine how much we should have for offset day 2.
2008-04-28 19:43:08.049 Refreshing data for Wed Apr 30 2008
2008-04-28 19:43:08.049 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:43:08.049 We should use cached data for this one
2008-04-28 19:43:08.054 Retrieving datadirect data.
2008-04-28 19:43:08.054 Grabbing data for Mon Apr 28 2008 offset 2
2008-04-28 19:43:08.054 From Wed Apr 30 05:00:00 2008 to Thu May 1 05:00:00 2008 (UTC)
2008-04-28 19:43:08.054 Grabbing listing data
2008-04-28 19:43:08.055 DataDirect: Copying from DD cache
2008-04-28 19:43:08.178 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:43:29.155 Grab complete.  Actual data from Wed Apr 30 05:00:00 2008 to Thu May 1 05:00:00 2008 (UTC)
2008-04-28 19:43:29.156 Main temp tables populated.
2008-04-28 19:43:29.423 Clearing data for source.
2008-04-28 19:43:29.423 Clearing from Wed Apr 30 00:00:00 2008 to Thu May 1 00:00:00 2008 (localtime)
2008-04-28 19:43:35.081 Data for source cleared.
2008-04-28 19:43:35.082 Updating programs.
2008-04-28 19:43:35.083 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:43:40.642 Program table update complete.
2008-04-28 19:43:40.642 
2008-04-28 19:43:40.642 Checking day @ offset 3, date: Thu May 1 2008
2008-04-28 19:43:40.644 Data Refresh because we are unable to query the data for day @ offset 2 to determine how much we should have for offset day 3.
2008-04-28 19:43:40.644 Refreshing data for Thu May 1 2008
2008-04-28 19:43:40.644 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:43:40.644 We should use cached data for this one
2008-04-28 19:43:40.648 Retrieving datadirect data.
2008-04-28 19:43:40.648 Grabbing data for Mon Apr 28 2008 offset 3
2008-04-28 19:43:40.648 From Thu May 1 05:00:00 2008 to Fri May 2 05:00:00 2008 (UTC)
2008-04-28 19:43:40.649 Grabbing listing data
2008-04-28 19:43:40.649 DataDirect: Copying from DD cache
2008-04-28 19:43:40.780 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:44:01.683 Grab complete.  Actual data from Thu May 1 05:00:00 2008 to Fri May 2 05:00:00 2008 (UTC)
2008-04-28 19:44:01.684 Main temp tables populated.
2008-04-28 19:44:01.959 Clearing data for source.
2008-04-28 19:44:01.960 Clearing from Thu May 1 00:00:00 2008 to Fri May 2 00:00:00 2008 (localtime)
2008-04-28 19:44:02.390 Data for source cleared.
2008-04-28 19:44:02.391 Updating programs.
2008-04-28 19:44:02.392 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:44:04.792 Program table update complete.
2008-04-28 19:44:04.792 
2008-04-28 19:44:04.792 Checking day @ offset 4, date: Fri May 2 2008
2008-04-28 19:44:04.794 Data Refresh because we are unable to query the data for day @ offset 3 to determine how much we should have for offset day 4.
2008-04-28 19:44:04.794 Refreshing data for Fri May 2 2008
2008-04-28 19:44:04.794 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:44:04.794 We should use cached data for this one
2008-04-28 19:44:04.799 Retrieving datadirect data.
2008-04-28 19:44:04.799 Grabbing data for Mon Apr 28 2008 offset 4
2008-04-28 19:44:04.799 From Fri May 2 05:00:00 2008 to Sat May 3 05:00:00 2008 (UTC)
2008-04-28 19:44:04.799 Grabbing listing data
2008-04-28 19:44:04.800 DataDirect: Copying from DD cache
2008-04-28 19:44:04.930 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:44:26.196 Grab complete.  Actual data from Fri May 2 05:00:00 2008 to Sat May 3 05:00:00 2008 (UTC)
2008-04-28 19:44:26.197 Main temp tables populated.
2008-04-28 19:44:26.455 Clearing data for source.
2008-04-28 19:44:26.455 Clearing from Fri May 2 00:00:00 2008 to Sat May 3 00:00:00 2008 (localtime)
2008-04-28 19:44:26.896 Data for source cleared.
2008-04-28 19:44:26.897 Updating programs.
2008-04-28 19:44:26.898 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:44:29.939 Program table update complete.
2008-04-28 19:44:29.939 
2008-04-28 19:44:29.939 Checking day @ offset 5, date: Sat May 3 2008
2008-04-28 19:44:29.941 Data Refresh because we are unable to query the data for day @ offset 4 to determine how much we should have for offset day 5.
2008-04-28 19:44:29.941 Refreshing data for Sat May 3 2008
2008-04-28 19:44:29.941 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:44:29.941 We should use cached data for this one
2008-04-28 19:44:29.945 Retrieving datadirect data.
2008-04-28 19:44:29.946 Grabbing data for Mon Apr 28 2008 offset 5
2008-04-28 19:44:29.946 From Sat May 3 05:00:00 2008 to Sun May 4 05:00:00 2008 (UTC)
2008-04-28 19:44:29.946 Grabbing listing data
2008-04-28 19:44:29.946 DataDirect: Copying from DD cache
2008-04-28 19:44:30.061 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:44:48.492 Grab complete.  Actual data from Sat May 3 05:00:00 2008 to Sun May 4 05:00:00 2008 (UTC)
2008-04-28 19:44:48.493 Main temp tables populated.
2008-04-28 19:44:48.750 Clearing data for source.
2008-04-28 19:44:48.750 Clearing from Sat May 3 00:00:00 2008 to Sun May 4 00:00:00 2008 (localtime)
2008-04-28 19:44:49.181 Data for source cleared.
2008-04-28 19:44:49.182 Updating programs.
2008-04-28 19:44:49.183 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:44:52.512 Program table update complete.
2008-04-28 19:44:52.512 
2008-04-28 19:44:52.513 Checking day @ offset 6, date: Sun May 4 2008
2008-04-28 19:44:52.514 Data Refresh because we are unable to query the data for day @ offset 5 to determine how much we should have for offset day 6.
2008-04-28 19:44:52.514 Refreshing data for Sun May 4 2008
2008-04-28 19:44:52.514 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:44:52.515 We should use cached data for this one
2008-04-28 19:44:52.519 Retrieving datadirect data.
2008-04-28 19:44:52.519 Grabbing data for Mon Apr 28 2008 offset 6
2008-04-28 19:44:52.520 From Sun May 4 05:00:00 2008 to Mon May 5 05:00:00 2008 (UTC)
2008-04-28 19:44:52.520 Grabbing listing data
2008-04-28 19:44:52.520 DataDirect: Copying from DD cache
2008-04-28 19:44:52.633 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:45:10.265 Grab complete.  Actual data from Sun May 4 05:00:00 2008 to Mon May 5 05:00:00 2008 (UTC)
2008-04-28 19:45:10.266 Main temp tables populated.
2008-04-28 19:45:10.520 Clearing data for source.
2008-04-28 19:45:10.520 Clearing from Sun May 4 00:00:00 2008 to Mon May 5 00:00:00 2008 (localtime)
2008-04-28 19:45:10.964 Data for source cleared.
2008-04-28 19:45:10.964 Updating programs.
2008-04-28 19:45:10.966 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:45:13.846 Program table update complete.
2008-04-28 19:45:13.846 
2008-04-28 19:45:13.846 Checking day @ offset 7, date: Mon May 5 2008
2008-04-28 19:45:13.848 Data Refresh because we are unable to query the data for day @ offset 6 to determine how much we should have for offset day 7.
2008-04-28 19:45:13.848 Refreshing data for Mon May 5 2008
2008-04-28 19:45:13.848 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:45:13.848 We should use cached data for this one
2008-04-28 19:45:13.853 Retrieving datadirect data.
2008-04-28 19:45:13.853 Grabbing data for Mon Apr 28 2008 offset 7
2008-04-28 19:45:13.853 From Mon May 5 05:00:00 2008 to Tue May 6 05:00:00 2008 (UTC)
2008-04-28 19:45:13.853 Grabbing listing data
2008-04-28 19:45:13.854 DataDirect: Copying from DD cache
2008-04-28 19:45:14.037 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:45:34.655 Grab complete.  Actual data from Mon May 5 05:00:00 2008 to Tue May 6 05:00:00 2008 (UTC)
2008-04-28 19:45:34.656 Main temp tables populated.
2008-04-28 19:45:34.921 Clearing data for source.
2008-04-28 19:45:34.921 Clearing from Mon May 5 00:00:00 2008 to Tue May 6 00:00:00 2008 (localtime)
2008-04-28 19:45:35.364 Data for source cleared.
2008-04-28 19:45:35.364 Updating programs.
2008-04-28 19:45:35.368 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:45:38.876 Program table update complete.
2008-04-28 19:45:38.877 
2008-04-28 19:45:38.877 Checking day @ offset 8, date: Tue May 6 2008
2008-04-28 19:45:38.879 Data Refresh because we are unable to query the data for day @ offset 7 to determine how much we should have for offset day 8.
2008-04-28 19:45:38.879 Refreshing data for Tue May 6 2008
2008-04-28 19:45:38.879 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:45:38.879 We should use cached data for this one
2008-04-28 19:45:38.884 Retrieving datadirect data.
2008-04-28 19:45:38.884 Grabbing data for Mon Apr 28 2008 offset 8
2008-04-28 19:45:38.884 From Tue May 6 05:00:00 2008 to Wed May 7 05:00:00 2008 (UTC)
2008-04-28 19:45:38.884 Grabbing listing data
2008-04-28 19:45:38.884 DataDirect: Copying from DD cache
2008-04-28 19:45:39.012 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:45:59.144 Grab complete.  Actual data from Tue May 6 05:00:00 2008 to Wed May 7 05:00:00 2008 (UTC)
2008-04-28 19:45:59.145 Main temp tables populated.
2008-04-28 19:45:59.404 Clearing data for source.
2008-04-28 19:45:59.405 Clearing from Tue May 6 00:00:00 2008 to Wed May 7 00:00:00 2008 (localtime)
2008-04-28 19:45:59.852 Data for source cleared.
2008-04-28 19:45:59.852 Updating programs.
2008-04-28 19:45:59.854 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:46:02.624 Program table update complete.
2008-04-28 19:46:02.625 
2008-04-28 19:46:02.625 Checking day @ offset 9, date: Wed May 7 2008
2008-04-28 19:46:02.626 Data Refresh because we are unable to query the data for day @ offset 8 to determine how much we should have for offset day 9.
2008-04-28 19:46:02.627 Refreshing data for Wed May 7 2008
2008-04-28 19:46:02.627 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:46:02.627 We should use cached data for this one
2008-04-28 19:46:02.632 Retrieving datadirect data.
2008-04-28 19:46:02.632 Grabbing data for Mon Apr 28 2008 offset 9
2008-04-28 19:46:02.632 From Wed May 7 05:00:00 2008 to Thu May 8 05:00:00 2008 (UTC)
2008-04-28 19:46:02.633 Grabbing listing data
2008-04-28 19:46:02.633 DataDirect: Copying from DD cache
2008-04-28 19:46:02.752 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:46:23.022 Grab complete.  Actual data from Wed May 7 05:00:00 2008 to Thu May 8 05:00:00 2008 (UTC)
2008-04-28 19:46:23.023 Main temp tables populated.
2008-04-28 19:46:23.298 Clearing data for source.
2008-04-28 19:46:23.299 Clearing from Wed May 7 00:00:00 2008 to Thu May 8 00:00:00 2008 (localtime)
2008-04-28 19:46:23.741 Data for source cleared.
2008-04-28 19:46:23.742 Updating programs.
2008-04-28 19:46:23.744 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:46:26.037 Program table update complete.
2008-04-28 19:46:26.037 
2008-04-28 19:46:26.037 Checking day @ offset 10, date: Thu May 8 2008
2008-04-28 19:46:26.039 Data Refresh because we are unable to query the data for day @ offset 9 to determine how much we should have for offset day 10.
2008-04-28 19:46:26.039 Refreshing data for Thu May 8 2008
2008-04-28 19:46:26.039 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:46:26.039 We should use cached data for this one
2008-04-28 19:46:26.044 Retrieving datadirect data.
2008-04-28 19:46:26.044 Grabbing data for Mon Apr 28 2008 offset 10
2008-04-28 19:46:26.044 From Thu May 8 05:00:00 2008 to Fri May 9 05:00:00 2008 (UTC)
2008-04-28 19:46:26.045 Grabbing listing data
2008-04-28 19:46:26.045 DataDirect: Copying from DD cache
2008-04-28 19:46:26.172 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:46:46.782 Grab complete.  Actual data from Thu May 8 05:00:00 2008 to Fri May 9 05:00:00 2008 (UTC)
2008-04-28 19:46:46.783 Main temp tables populated.
2008-04-28 19:46:47.047 Clearing data for source.
2008-04-28 19:46:47.048 Clearing from Thu May 8 00:00:00 2008 to Fri May 9 00:00:00 2008 (localtime)
2008-04-28 19:46:47.508 Data for source cleared.
2008-04-28 19:46:47.508 Updating programs.
2008-04-28 19:46:47.510 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:46:49.882 Program table update complete.
2008-04-28 19:46:49.883 
2008-04-28 19:46:49.883 Checking day @ offset 11, date: Fri May 9 2008
2008-04-28 19:46:49.884 Data Refresh because we are unable to query the data for day @ offset 10 to determine how much we should have for offset day 11.
2008-04-28 19:46:49.884 Refreshing data for Fri May 9 2008
2008-04-28 19:46:49.885 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:46:49.885 We should use cached data for this one
2008-04-28 19:46:49.890 Retrieving datadirect data.
2008-04-28 19:46:49.890 Grabbing data for Mon Apr 28 2008 offset 11
2008-04-28 19:46:49.890 From Fri May 9 05:00:00 2008 to Sat May 10 05:00:00 2008 (UTC)
2008-04-28 19:46:49.891 Grabbing listing data
2008-04-28 19:46:49.891 DataDirect: Copying from DD cache
2008-04-28 19:46:50.022 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:47:10.306 Grab complete.  Actual data from Fri May 9 05:00:00 2008 to Sat May 10 05:00:00 2008 (UTC)
2008-04-28 19:47:10.307 Main temp tables populated.
2008-04-28 19:47:10.583 Clearing data for source.
2008-04-28 19:47:10.583 Clearing from Fri May 9 00:00:00 2008 to Sat May 10 00:00:00 2008 (localtime)
2008-04-28 19:47:11.031 Data for source cleared.
2008-04-28 19:47:11.032 Updating programs.
2008-04-28 19:47:11.033 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:47:13.386 Program table update complete.
2008-04-28 19:47:13.387 
2008-04-28 19:47:13.387 Checking day @ offset 12, date: Sat May 10 2008
2008-04-28 19:47:13.388 Data Refresh because we are unable to query the data for day @ offset 11 to determine how much we should have for offset day 12.
2008-04-28 19:47:13.389 Refreshing data for Sat May 10 2008
2008-04-28 19:47:13.389 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:47:13.389 We should use cached data for this one
2008-04-28 19:47:13.393 Retrieving datadirect data.
2008-04-28 19:47:13.394 Grabbing data for Mon Apr 28 2008 offset 12
2008-04-28 19:47:13.394 From Sat May 10 05:00:00 2008 to Sun May 11 05:00:00 2008 (UTC)
2008-04-28 19:47:13.394 Grabbing listing data
2008-04-28 19:47:13.394 DataDirect: Copying from DD cache
2008-04-28 19:47:13.510 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:47:30.408 Grab complete.  Actual data from Sat May 10 05:00:00 2008 to Sun May 11 05:00:00 2008 (UTC)
2008-04-28 19:47:30.410 Main temp tables populated.
2008-04-28 19:47:30.673 Clearing data for source.
2008-04-28 19:47:30.673 Clearing from Sat May 10 00:00:00 2008 to Sun May 11 00:00:00 2008 (localtime)
2008-04-28 19:47:31.109 Data for source cleared.
2008-04-28 19:47:31.109 Updating programs.
2008-04-28 19:47:31.111 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:47:33.018 Program table update complete.
2008-04-28 19:47:33.019 
2008-04-28 19:47:33.019 Checking day @ offset 13, date: Sun May 11 2008
2008-04-28 19:47:33.020 Data Refresh because we are unable to query the data for day @ offset 12 to determine how much we should have for offset day 13.
2008-04-28 19:47:33.020 Refreshing data for Sun May 11 2008
2008-04-28 19:47:33.021 This DataDirect listings source is shared by 2 MythTV lineups
2008-04-28 19:47:33.021 We should use cached data for this one
2008-04-28 19:47:33.025 Retrieving datadirect data.
2008-04-28 19:47:33.025 Grabbing data for Mon Apr 28 2008 offset 13
2008-04-28 19:47:33.025 From Sun May 11 05:00:00 2008 to Mon May 12 05:00:00 2008 (UTC)
2008-04-28 19:47:33.026 Grabbing listing data
2008-04-28 19:47:33.026 DataDirect: Copying from DD cache
2008-04-28 19:47:33.141 DataDirect: Your subscription expires on 10/05/2008 03:14:46 PM
2008-04-28 19:47:50.397 Grab complete.  Actual data from Sun May 11 05:00:00 2008 to Mon May 12 05:00:00 2008 (UTC)
2008-04-28 19:47:50.398 Main temp tables populated.
2008-04-28 19:47:50.652 Clearing data for source.
2008-04-28 19:47:50.652 Clearing from Sun May 11 00:00:00 2008 to Mon May 12 00:00:00 2008 (localtime)
2008-04-28 19:47:51.092 Data for source cleared.
2008-04-28 19:47:51.092 Updating programs.
2008-04-28 19:47:51.093 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and should be repaired

2008-04-28 19:47:53.002 Program table update complete.
2008-04-28 19:47:53.004 Failed to fetch some program info
2008-04-28 19:47:53.004 Adjusting program database end times.
2008-04-28 19:47:53.006 fix_end_times query failed: SELECT chanid, starttime, endtime FROM program WHERE (DATE_FORMAT(endtime,'%H%i') = '0000') ORDER BY chanid, starttime;
2008-04-28 19:47:53.006 fix_end_times failed!
2008-04-28 19:47:53.007 Marking generic episodes.
2008-04-28 19:47:53.008     Found -1
2008-04-28 19:47:53.008 Marking repeats.
2008-04-28 19:47:53.018     Found -1
2008-04-28 19:47:53.019 Unmarking new episode rebroadcast repeats.
2008-04-28 19:47:53.020     Found -1
2008-04-28 19:47:53.021 Marking episode first showings.
2008-04-28 19:47:53.024     Found -2
2008-04-28 19:47:53.024 Marking episode last showings.
2008-04-28 19:47:53.027     Found -2
2008-04-28 19:47:53.061 Grabbing next suggested grabbing time
2008-04-28 19:47:53.665 DataDirect: BlockedTime is: 2008-04-28T19:47:53
2008-04-28 19:47:53.666 DataDirect: NextSuggestedTime is: 2008-04-29T09:04:22
2008-04-28 19:47:53.672 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-04-28 19:47:53.687 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 19:47:53.690 Using protocol version 40
2008-04-28 19:47:54.634 Received a remote 'Clear Cache' request
2008-04-28 19:47:54.684 mythfilldatabase run complete.
2008-04-28 19:47:54.685 DataDirect: Deleting temporary files
ICE default IO error handler doing an exit(), pid = 6403, errno = 32
ducodihilum@ducodihilum-desktop:~$

---

### Post by justanotherhack on 2008-04-29
Well, according to your logs, your DB is damaged. Two ways to fix that.

The better way (to keep your data) is to repair the table(s). The following snippet does a connect, check and repair on the table program and checks it again.
```
mysql -u mythtv -p mythconverg
CHECK TABLE program EXTENDED;
REPAIR TABLE program EXTENDED;
CHECK TABLE program EXTENDED;
```

You should get a message like the following for the last check.
```
+---------------------+-------+----------+----------+
| Table               | Op    | Msg_type | Msg_text |
+---------------------+-------+----------+----------+
| mythconverg.program | check | status   | OK       | 
+---------------------+-------+----------+----------+
```

In case this won't work, you might have to try the other way and create a new database. For this, shut down all of MythTV. After this, the following lines will connect to the database as root, rename the old database (to keep it as backup), create a new one and reset the privileges on it.
```
mysql -u root -p
RENAME DATABASE mythconverg TO mythconvergbackup;
CREATE DATABASE mythconverg;
GRANT ALL ON mythconverg.* TO 'mythtv'@'localhost';
```

After that you have to refill the database via MythTV and do all your settings again.
If you want to convert some settings from the old database to the new one, post again, then I'll describe a way for that.

---

### Post by laga on 2008-04-29
Or just run ```
 perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```

---

### Post by justanotherhack on 2008-04-29
Oh, that sounds way too simple ;) .
(Okay, I admit it, too much a DB admin to even think about "boxed" solutions ;) .)

---

