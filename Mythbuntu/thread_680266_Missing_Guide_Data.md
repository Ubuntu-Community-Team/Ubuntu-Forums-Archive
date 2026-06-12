---
title: "Missing Guide Data"
date: 2008-01-27
forum: Mythbuntu
---

### Post by Calash on 2008-01-27
Normally I am good at figuring this stuff out, but this one is beating me up to no end.

I was having a problem with my channel listings being off, so to correct it I redid my lineup at scheduledirect, and went into Mythtv-setup and reconfigured everything there.


I got it to the point where all my call signs and channel logo information is there and correct, but the guide data is coming up blank, showing up as Unknown (Unknown).

I have been up and down the settings and I can not figure out why.  The channel information looks fine, and everything else is working but the listings.

Here is the output of my Mythfilldatabase.  Let me know if I am missing something simple here.

```

2007-01-27 20:05:11.008 Using runtime prefix = /usr
2007-01-27 20:05:11.022 New DB connection, total: 1
2007-01-27 20:05:11.027 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:05:11.034 New DB connection, total: 2
2007-01-27 20:05:11.034 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:05:11.070 Updating source #1 (Cable) with grabber schedulesdirect1
2007-01-27 20:05:11.071 Found 66 channels for source 1 which use grabber
2007-01-27 20:05:11.072 
2007-01-27 20:05:11.072 Checking day @ offset 0, date: Sat Jan 27 2007
2007-01-27 20:05:11.088 Data refresh needed because no data exists for day @ offset 0 from 6PM - midnight.
2007-01-27 20:05:11.088 Refreshing data for Sat Jan 27 2007
2007-01-27 20:05:11.090 New DB DataDirect connection
2007-01-27 20:05:11.090 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:05:11.092 Retrieving datadirect data.
2007-01-27 20:05:11.092 Grabbing data for Sat Jan 27 2007 offset 0
2007-01-27 20:05:11.093 From Sat Jan 27 05:00:00 2007 to Sun Jan 28 05:00:00 2007 (UTC)
2007-01-27 20:05:11.093 Grabbing listing data
--20:05:11--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                                                        ] 237,623       91.31K/s             

20:05:14 (91.19 KB/s) - `-' saved [237623]

2007-01-27 20:05:14.528 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:05:14.644 New DB connection, total: 3
2007-01-27 20:05:14.645 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:05:14.646 sourceid 1 has lineup type: Cable
2007-01-27 20:05:34.281 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:05:34.282 Main temp tables populated.
2007-01-27 20:05:34.282 Updating myth channels.
2007-01-27 20:05:34.296 Updating icons for sourceid: 1
2007-01-27 20:05:34.297 Channels updated.
2007-01-27 20:05:34.461 Clearing data for source.
2007-01-27 20:05:34.461 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:05:34.463 New DB connection, total: 4
2007-01-27 20:05:34.464 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:05:35.679 Data for source cleared.
2007-01-27 20:05:35.679 Updating programs.
2007-01-27 20:05:37.217 Program table update complete.
2007-01-27 20:05:37.217 
2007-01-27 20:05:37.217 Checking day @ offset 1, date: Sun Jan 28 2007
2007-01-27 20:05:37.217 Data Refresh always needed for tomorrow
2007-01-27 20:05:37.217 Refreshing data for Sun Jan 28 2007
2007-01-27 20:05:37.220 Retrieving datadirect data.
2007-01-27 20:05:37.220 Grabbing data for Sat Jan 27 2007 offset 1
2007-01-27 20:05:37.220 From Sun Jan 28 05:00:00 2007 to Mon Jan 29 05:00:00 2007 (UTC)
2007-01-27 20:05:37.220 Grabbing listing data
--20:05:37--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                                                        ] 237,623       94.88K/s             

20:05:40 (94.73 KB/s) - `-' saved [237623]

2007-01-27 20:05:40.665 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:06:00.236 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:06:00.237 Main temp tables populated.
2007-01-27 20:06:00.400 Clearing data for source.
2007-01-27 20:06:00.400 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:06:01.528 Data for source cleared.
2007-01-27 20:06:01.528 Updating programs.
2007-01-27 20:06:03.025 Program table update complete.
2007-01-27 20:06:03.025 
2007-01-27 20:06:03.025 Checking day @ offset 2, date: Mon Jan 29 2007
2007-01-27 20:06:03.041 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2007-01-27 20:06:03.042 Refreshing data for Mon Jan 29 2007
2007-01-27 20:06:03.044 Retrieving datadirect data.
2007-01-27 20:06:03.044 Grabbing data for Sat Jan 27 2007 offset 2
2007-01-27 20:06:03.044 From Mon Jan 29 05:00:00 2007 to Tue Jan 30 05:00:00 2007 (UTC)
2007-01-27 20:06:03.045 Grabbing listing data
--20:06:03--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [        <=>                                                       ] 237,623       96.46K/s             

20:06:06 (96.28 KB/s) - `-' saved [237623]

2007-01-27 20:06:06.258 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:06:25.831 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:06:25.832 Main temp tables populated.
2007-01-27 20:06:25.995 Clearing data for source.
2007-01-27 20:06:25.996 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:06:27.200 Data for source cleared.
2007-01-27 20:06:27.200 Updating programs.
2007-01-27 20:06:28.725 Program table update complete.
2007-01-27 20:06:28.725 
2007-01-27 20:06:28.725 Checking day @ offset 3, date: Tue Jan 30 2007
2007-01-27 20:06:28.742 Data refresh needed because no data exists for day @ offset 3 from 6PM - midnight.
2007-01-27 20:06:28.742 Refreshing data for Tue Jan 30 2007
2007-01-27 20:06:28.745 Retrieving datadirect data.
2007-01-27 20:06:28.745 Grabbing data for Sat Jan 27 2007 offset 3
2007-01-27 20:06:28.745 From Tue Jan 30 05:00:00 2007 to Wed Jan 31 05:00:00 2007 (UTC)
2007-01-27 20:06:28.745 Grabbing listing data
--20:06:28--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                                                        ] 237,623       97.67K/s             

20:06:31 (97.52 KB/s) - `-' saved [237623]

2007-01-27 20:06:32.168 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:06:51.735 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:06:51.736 Main temp tables populated.
2007-01-27 20:06:51.901 Clearing data for source.
2007-01-27 20:06:51.901 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:06:53.034 Data for source cleared.
2007-01-27 20:06:53.034 Updating programs.
2007-01-27 20:06:54.535 Program table update complete.
2007-01-27 20:06:54.535 
2007-01-27 20:06:54.535 Checking day @ offset 4, date: Wed Jan 31 2007
2007-01-27 20:06:54.552 Data refresh needed because no data exists for day @ offset 4 from 6PM - midnight.
2007-01-27 20:06:54.552 Refreshing data for Wed Jan 31 2007
2007-01-27 20:06:54.556 Retrieving datadirect data.
2007-01-27 20:06:54.556 Grabbing data for Sat Jan 27 2007 offset 4
2007-01-27 20:06:54.556 From Wed Jan 31 05:00:00 2007 to Thu Feb 1 05:00:00 2007 (UTC)
2007-01-27 20:06:54.556 Grabbing listing data
--20:06:54--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [        <=>                                                       ] 237,623       83.88K/s             

20:06:57 (83.73 KB/s) - `-' saved [237623]

2007-01-27 20:06:58.084 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:07:17.774 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:07:17.775 Main temp tables populated.
2007-01-27 20:07:17.935 Clearing data for source.
2007-01-27 20:07:17.936 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:07:19.135 Data for source cleared.
2007-01-27 20:07:19.135 Updating programs.
2007-01-27 20:07:20.663 Program table update complete.
2007-01-27 20:07:20.663 
2007-01-27 20:07:20.663 Checking day @ offset 5, date: Thu Feb 1 2007
2007-01-27 20:07:20.680 Data refresh needed because no data exists for day @ offset 5 from 6PM - midnight.
2007-01-27 20:07:20.680 Refreshing data for Thu Feb 1 2007
2007-01-27 20:07:20.683 Retrieving datadirect data.
2007-01-27 20:07:20.683 Grabbing data for Sat Jan 27 2007 offset 5
2007-01-27 20:07:20.683 From Thu Feb 1 05:00:00 2007 to Fri Feb 2 05:00:00 2007 (UTC)
2007-01-27 20:07:20.683 Grabbing listing data
--20:07:20--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                                                      ] 237,623       76.31K/s             

20:07:24 (76.22 KB/s) - `-' saved [237623]

2007-01-27 20:07:24.792 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:07:44.476 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:07:44.478 Main temp tables populated.
2007-01-27 20:07:44.640 Clearing data for source.
2007-01-27 20:07:44.640 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:07:45.772 Data for source cleared.
2007-01-27 20:07:45.772 Updating programs.
2007-01-27 20:07:47.284 Program table update complete.
2007-01-27 20:07:47.285 
2007-01-27 20:07:47.285 Checking day @ offset 6, date: Fri Feb 2 2007
2007-01-27 20:07:47.301 Data refresh needed because no data exists for day @ offset 6 from 6PM - midnight.
2007-01-27 20:07:47.301 Refreshing data for Fri Feb 2 2007
2007-01-27 20:07:47.304 Retrieving datadirect data.
2007-01-27 20:07:47.304 Grabbing data for Sat Jan 27 2007 offset 6
2007-01-27 20:07:47.304 From Fri Feb 2 05:00:00 2007 to Sat Feb 3 05:00:00 2007 (UTC)
2007-01-27 20:07:47.304 Grabbing listing data
--20:07:47--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                                                      ] 237,623       88.44K/s             

20:07:50 (88.28 KB/s) - `-' saved [237623]

2007-01-27 20:07:50.845 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:08:10.523 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:08:10.524 Main temp tables populated.
2007-01-27 20:08:10.687 Clearing data for source.
2007-01-27 20:08:10.687 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:08:11.871 Data for source cleared.
2007-01-27 20:08:11.871 Updating programs.
2007-01-27 20:08:13.405 Program table update complete.
2007-01-27 20:08:13.405 
2007-01-27 20:08:13.405 Checking day @ offset 7, date: Sat Feb 3 2007
2007-01-27 20:08:13.421 Data refresh needed because no data exists for day @ offset 7 from 6PM - midnight.
2007-01-27 20:08:13.422 Refreshing data for Sat Feb 3 2007
2007-01-27 20:08:13.424 Retrieving datadirect data.
2007-01-27 20:08:13.424 Grabbing data for Sat Jan 27 2007 offset 7
2007-01-27 20:08:13.424 From Sat Feb 3 05:00:00 2007 to Sun Feb 4 05:00:00 2007 (UTC)
2007-01-27 20:08:13.425 Grabbing listing data
--20:08:13--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                                                      ] 237,623       73.69K/s             

20:08:17 (73.60 KB/s) - `-' saved [237623]

2007-01-27 20:08:17.379 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:08:36.959 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:08:36.960 Main temp tables populated.
2007-01-27 20:08:37.122 Clearing data for source.
2007-01-27 20:08:37.123 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:08:38.245 Data for source cleared.
2007-01-27 20:08:38.245 Updating programs.
2007-01-27 20:08:39.770 Program table update complete.
2007-01-27 20:08:39.770 
2007-01-27 20:08:39.770 Checking day @ offset 8, date: Sun Feb 4 2007
2007-01-27 20:08:39.787 Data refresh needed because no data exists for day @ offset 8 from 6PM - midnight.
2007-01-27 20:08:39.787 Refreshing data for Sun Feb 4 2007
2007-01-27 20:08:39.789 Retrieving datadirect data.
2007-01-27 20:08:39.790 Grabbing data for Sat Jan 27 2007 offset 8
2007-01-27 20:08:39.790 From Sun Feb 4 05:00:00 2007 to Mon Feb 5 05:00:00 2007 (UTC)
2007-01-27 20:08:39.790 Grabbing listing data
--20:08:39--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                                                      ] 237,623       80.76K/s             

20:08:43 (80.57 KB/s) - `-' saved [237623]

2007-01-27 20:08:43.475 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:09:03.250 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:09:03.251 Main temp tables populated.
2007-01-27 20:09:03.414 Clearing data for source.
2007-01-27 20:09:03.414 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:09:04.593 Data for source cleared.
2007-01-27 20:09:04.593 Updating programs.
2007-01-27 20:09:06.120 Program table update complete.
2007-01-27 20:09:06.120 
2007-01-27 20:09:06.120 Checking day @ offset 9, date: Mon Feb 5 2007
2007-01-27 20:09:06.136 Data refresh needed because no data exists for day @ offset 9 from 6PM - midnight.
2007-01-27 20:09:06.136 Refreshing data for Mon Feb 5 2007
2007-01-27 20:09:06.139 Retrieving datadirect data.
2007-01-27 20:09:06.139 Grabbing data for Sat Jan 27 2007 offset 9
2007-01-27 20:09:06.139 From Mon Feb 5 05:00:00 2007 to Tue Feb 6 05:00:00 2007 (UTC)
2007-01-27 20:09:06.140 Grabbing listing data
--20:09:06--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                                                      ] 237,623       73.66K/s             

20:09:10 (73.55 KB/s) - `-' saved [237623]

2007-01-27 20:09:10.469 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:09:30.120 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:09:30.122 Main temp tables populated.
2007-01-27 20:09:30.286 Clearing data for source.
2007-01-27 20:09:30.286 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:09:31.389 Data for source cleared.
2007-01-27 20:09:31.389 Updating programs.
2007-01-27 20:09:32.898 Program table update complete.
2007-01-27 20:09:32.898 
2007-01-27 20:09:32.898 Checking day @ offset 10, date: Tue Feb 6 2007
2007-01-27 20:09:32.914 Data refresh needed because no data exists for day @ offset 10 from 6PM - midnight.
2007-01-27 20:09:32.914 Refreshing data for Tue Feb 6 2007
2007-01-27 20:09:32.917 Retrieving datadirect data.
2007-01-27 20:09:32.917 Grabbing data for Sat Jan 27 2007 offset 10
2007-01-27 20:09:32.917 From Tue Feb 6 05:00:00 2007 to Wed Feb 7 05:00:00 2007 (UTC)
2007-01-27 20:09:32.918 Grabbing listing data
--20:09:32--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [           <=>                                                    ] 237,623       69.49K/s             

20:09:36 (69.38 KB/s) - `-' saved [237623]

2007-01-27 20:09:37.023 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:09:56.737 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:09:56.738 Main temp tables populated.
2007-01-27 20:09:56.902 Clearing data for source.
2007-01-27 20:09:56.903 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:09:58.095 Data for source cleared.
2007-01-27 20:09:58.095 Updating programs.
2007-01-27 20:09:59.628 Program table update complete.
2007-01-27 20:09:59.628 
2007-01-27 20:09:59.628 Checking day @ offset 11, date: Wed Feb 7 2007
2007-01-27 20:09:59.645 Data refresh needed because no data exists for day @ offset 11 from 6PM - midnight.
2007-01-27 20:09:59.645 Refreshing data for Wed Feb 7 2007
2007-01-27 20:09:59.648 Retrieving datadirect data.
2007-01-27 20:09:59.648 Grabbing data for Sat Jan 27 2007 offset 11
2007-01-27 20:09:59.648 From Wed Feb 7 05:00:00 2007 to Thu Feb 8 05:00:00 2007 (UTC)
2007-01-27 20:09:59.648 Grabbing listing data
--20:09:59--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [           <=>                                                    ] 237,623       68.89K/s             

20:10:04 (68.81 KB/s) - `-' saved [237623]

2007-01-27 20:10:04.117 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:10:24.012 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:10:24.014 Main temp tables populated.
2007-01-27 20:10:24.192 Clearing data for source.
2007-01-27 20:10:24.192 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:10:25.341 Data for source cleared.
2007-01-27 20:10:25.341 Updating programs.
2007-01-27 20:10:26.991 Program table update complete.
2007-01-27 20:10:26.992 
2007-01-27 20:10:26.992 Checking day @ offset 12, date: Thu Feb 8 2007
2007-01-27 20:10:27.008 Data refresh needed because no data exists for day @ offset 12 from 6PM - midnight.
2007-01-27 20:10:27.008 Refreshing data for Thu Feb 8 2007
2007-01-27 20:10:27.011 Retrieving datadirect data.
2007-01-27 20:10:27.011 Grabbing data for Sat Jan 27 2007 offset 12
2007-01-27 20:10:27.011 From Thu Feb 8 05:00:00 2007 to Fri Feb 9 05:00:00 2007 (UTC)
2007-01-27 20:10:27.012 Grabbing listing data
--20:10:27--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [          <=>                                                     ] 237,623       69.53K/s             

20:10:31 (69.44 KB/s) - `-' saved [237623]

2007-01-27 20:10:31.165 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:10:50.950 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:10:50.951 Main temp tables populated.
2007-01-27 20:10:51.114 Clearing data for source.
2007-01-27 20:10:51.114 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:10:52.307 Data for source cleared.
2007-01-27 20:10:52.307 Updating programs.
2007-01-27 20:10:53.849 Program table update complete.
2007-01-27 20:10:53.849 
2007-01-27 20:10:53.849 Checking day @ offset 13, date: Fri Feb 9 2007
2007-01-27 20:10:53.867 Data refresh needed because no data exists for day @ offset 13 from 6PM - midnight.
2007-01-27 20:10:53.867 Refreshing data for Fri Feb 9 2007
2007-01-27 20:10:53.869 Retrieving datadirect data.
2007-01-27 20:10:53.869 Grabbing data for Sat Jan 27 2007 offset 13
2007-01-27 20:10:53.870 From Fri Feb 9 05:00:00 2007 to Sat Feb 10 05:00:00 2007 (UTC)
2007-01-27 20:10:53.870 Grabbing listing data
--20:10:53--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [          <=>                                                     ] 237,623       68.04K/s             

20:10:57 (67.96 KB/s) - `-' saved [237623]

2007-01-27 20:10:58.042 DataDirect: Your subscription expires on 09/24/2008 07:47:17 AM
2007-01-27 20:11:17.742 Grab complete.  Actual data from Sun Jan 27 00:00:00 2008 to Mon Jan 28 23:59:59 2008 (UTC)
2007-01-27 20:11:17.743 Main temp tables populated.
2007-01-27 20:11:17.906 Clearing data for source.
2007-01-27 20:11:17.906 Clearing from Sat Jan 26 19:00:00 2008 to Mon Jan 28 18:59:59 2008 (localtime)
2007-01-27 20:11:19.030 Data for source cleared.
2007-01-27 20:11:19.030 Updating programs.
2007-01-27 20:11:20.568 Program table update complete.
2007-01-27 20:11:20.661 New DB connection, total: 5
2007-01-27 20:11:20.661 Connected to database 'mythconverg' at host: localhost
2007-01-27 20:11:20.665 Data fetching complete.
2007-01-27 20:11:20.665 Adjusting program database end times.
2007-01-27 20:11:20.795     0 replacements made
2007-01-27 20:11:20.795 Marking generic episodes.
2007-01-27 20:11:20.839     Found 905
2007-01-27 20:11:20.840 Marking repeats.
2007-01-27 20:11:20.899     Found 2054
2007-01-27 20:11:20.899 Unmarking new episode rebroadcast repeats.
2007-01-27 20:11:20.928     Found 0
2007-01-27 20:11:20.974 Marking episode first showings.
2007-01-27 20:11:23.659     Found 2861
2007-01-27 20:11:23.659 Marking episode last showings.
2007-01-27 20:11:26.350     Found 2861
2007-01-27 20:11:26.365 Grabbing next suggested grabbing time
2007-01-27 20:11:27.073 DataDirect: BlockedTime is: 2008-01-27T20:13:17
2007-01-27 20:11:27.074 DataDirect: NextSuggestedTime is: 2008-01-28T19:51:49
2007-01-27 20:11:27.078 DataDirect: Provider suggested running again at 2008-01-28T19:51:49, but MythFillPeriod is 1.  Next run time will be adjusted to be 2007-01-28T19:51:49.
2007-01-27 20:11:27.082 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-01-27 20:11:27.090 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-01-27 20:11:27.091 Using protocol version 31
2007-01-27 20:11:27.142 mythfilldatabase run complete.
2007-01-27 20:11:27.149 DataDirect: Deleting temporary files

```

---

### Post by Calash on 2008-01-29
Well, I found my solution after browsing around my database and reconfiguring everything for a couple of houts.

And yes, you are all allowed to laugh..


My time was set to 2007....not 2008.

Sigh!!!

Back up and running :)

---

