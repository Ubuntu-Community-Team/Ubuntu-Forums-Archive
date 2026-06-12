---
title: "Trying to get program guide to populate"
date: 2007-12-27
forum: Mythbuntu
---

### Post by John Lentz on 2007-12-27
Hi,

I'm trying to get my myth box set up and I'm not able to get any program guide data.  I've done step 3 where I set it up for Schedules Direct.  I give it my username/password and it autofills the correct location, so I know I gave it the correct username/password.  I then tell it to autofill the db and let it go.  It runs for a while, but the program guide is totally blank.  The only thing on it is the times across the top.  I've let it set running for days, and nothing is ever populated - only the times appear at the top.  What is required for populating the program guide besides setting up the schedules Direct part?

Thanks,

John

---

### Post by andrewb78 on 2007-12-27
It shouldn't take days to populate.  Are there any messages of interest when mythfilldatabase runs?  Specifically, are there a significant number of messages like "401 Not Authorized", and if so, are there times where it appears that the download of schedule information was successful?

Maybe run:

```
mythfilldatabase
```

and post the output here.

---

### Post by John Lentz on 2007-12-27
> **andrewb78 said:**
> It shouldn't take days to populate.  Are there any messages of interest when mythfilldatabase runs?  Specifically, are there a significant number of messages like "401 Not Authorized", and if so, are there times where it appears that the download of schedule information was successful?

Maybe run:

```
mythfilldatabase
```

and post the output here.

Here is the output:  Thanks for any guidance.  I didn't set up any channels or anything else other than select the video source as Schedules Direct:

 mythfilldatabase
2007-12-27 20:48:17.041 Using runtime prefix = /usr
2007-12-27 20:48:17.051 New DB connection, total: 1
2007-12-27 20:48:17.056 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:48:17.061 New DB connection, total: 2
2007-12-27 20:48:17.062 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:48:17.062 Updating source #1 (Schedules Direct) with grabber schedulesdirect1
2007-12-27 20:48:17.063 No channels are configured to use grabber.
2007-12-27 20:48:17.063 
2007-12-27 20:48:17.063 Checking day @ offset 0, date: Thu Dec 27 2007
2007-12-27 20:48:17.063 Data refresh needed because no data exists for day @ offset 0 from 6PM - midnight.
2007-12-27 20:48:17.064 Refreshing data for Thu Dec 27 2007
2007-12-27 20:48:17.064 New DB DataDirect connection
2007-12-27 20:48:17.065 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:48:17.067 Retrieving datadirect data.
2007-12-27 20:48:17.067 Grabbing data for Thu Dec 27 2007 offset 0
2007-12-27 20:48:17.067 From Thu Dec 27 05:00:00 2007 to Fri Dec 28 05:00:00 2007 (UTC)
2007-12-27 20:48:17.067 Grabbing listing data
--20:48:17--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [    <=>                              ] 64,954        47.93K/s             

20:48:18 (47.85 KB/s) - `-' saved [64954]

2007-12-27 20:48:19.034 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:19.086 New DB connection, total: 3
2007-12-27 20:48:19.086 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:48:19.087 sourceid 1 has lineup type: LocalBroadcast
2007-12-27 20:48:21.964 Grab complete.  Actual data from Thu Dec 27 05:00:00 2007 to Fri Dec 28 05:00:00 2007 (UTC)
2007-12-27 20:48:21.964 Main temp tables populated.
2007-12-27 20:48:21.965 Updating myth channels.
2007-12-27 20:48:21.969 DataDirect, Warning: Not inserting channels into disconnected source 1.
2007-12-27 20:48:21.969 Updating icons for sourceid: 1
2007-12-27 20:48:21.969 Channels updated.
2007-12-27 20:48:21.973 Did not find any new program data.
2007-12-27 20:48:21.973 
2007-12-27 20:48:21.973 Checking day @ offset 1, date: Fri Dec 28 2007
2007-12-27 20:48:21.973 Data Refresh always needed for tomorrow
2007-12-27 20:48:21.973 Refreshing data for Fri Dec 28 2007
2007-12-27 20:48:21.973 Retrieving datadirect data.
2007-12-27 20:48:21.976 Grabbing data for Thu Dec 27 2007 offset 1
2007-12-27 20:48:21.976 From Fri Dec 28 05:00:00 2007 to Sat Dec 29 05:00:00 2007 (UTC)
2007-12-27 20:48:21.977 Grabbing listing data
--20:48:21--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 62,910        62.19K/s             

20:48:23 (62.13 KB/s) - `-' saved [62910]

2007-12-27 20:48:23.324 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:26.003 Grab complete.  Actual data from Fri Dec 28 05:00:00 2007 to Sat Dec 29 05:00:00 2007 (UTC)
2007-12-27 20:48:26.003 Main temp tables populated.
2007-12-27 20:48:26.006 Did not find any new program data.
2007-12-27 20:48:26.006 
2007-12-27 20:48:26.006 Checking day @ offset 2, date: Sat Dec 29 2007
2007-12-27 20:48:26.007 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2007-12-27 20:48:26.007 Refreshing data for Sat Dec 29 2007
2007-12-27 20:48:26.007 Retrieving datadirect data.
2007-12-27 20:48:26.007 Grabbing data for Thu Dec 27 2007 offset 2
2007-12-27 20:48:26.007 From Sat Dec 29 05:00:00 2007 to Sun Dec 30 05:00:00 2007 (UTC)
2007-12-27 20:48:26.008 Grabbing listing data
--20:48:26--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 63,251        54.98K/s             

20:48:27 (54.94 KB/s) - `-' saved [63251]

2007-12-27 20:48:27.556 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:30.189 Grab complete.  Actual data from Sat Dec 29 05:00:00 2007 to Sun Dec 30 05:00:00 2007 (UTC)
2007-12-27 20:48:30.190 Main temp tables populated.
2007-12-27 20:48:30.192 Did not find any new program data.
2007-12-27 20:48:30.192 
2007-12-27 20:48:30.192 Checking day @ offset 3, date: Sun Dec 30 2007
2007-12-27 20:48:30.193 Data refresh needed because no data exists for day @ offset 3 from 6PM - midnight.
2007-12-27 20:48:30.193 Refreshing data for Sun Dec 30 2007
2007-12-27 20:48:30.193 Retrieving datadirect data.
2007-12-27 20:48:30.193 Grabbing data for Thu Dec 27 2007 offset 3
2007-12-27 20:48:30.194 From Sun Dec 30 05:00:00 2007 to Mon Dec 31 05:00:00 2007 (UTC)
2007-12-27 20:48:30.194 Grabbing listing data
--20:48:30--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 56,577        47.98K/s             

20:48:31 (47.94 KB/s) - `-' saved [56577]

2007-12-27 20:48:31.688 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:34.093 Grab complete.  Actual data from Sun Dec 30 05:00:00 2007 to Mon Dec 31 05:00:00 2007 (UTC)
2007-12-27 20:48:34.093 Main temp tables populated.
2007-12-27 20:48:34.096 Did not find any new program data.
2007-12-27 20:48:34.096 
2007-12-27 20:48:34.096 Checking day @ offset 4, date: Mon Dec 31 2007
2007-12-27 20:48:34.096 Data refresh needed because no data exists for day @ offset 4 from 6PM - midnight.
2007-12-27 20:48:34.096 Refreshing data for Mon Dec 31 2007
2007-12-27 20:48:34.097 Retrieving datadirect data.
2007-12-27 20:48:34.097 Grabbing data for Thu Dec 27 2007 offset 4
2007-12-27 20:48:34.097 From Mon Dec 31 05:00:00 2007 to Tue Jan 1 05:00:00 2008 (UTC)
2007-12-27 20:48:34.097 Grabbing listing data
--20:48:34--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 63,665        63.34K/s             

20:48:35 (63.27 KB/s) - `-' saved [63665]

2007-12-27 20:48:35.440 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:38.245 Grab complete.  Actual data from Mon Dec 31 05:00:00 2007 to Tue Jan 1 05:00:00 2008 (UTC)
2007-12-27 20:48:38.245 Main temp tables populated.
2007-12-27 20:48:38.248 Did not find any new program data.
2007-12-27 20:48:38.248 
2007-12-27 20:48:38.249 Checking day @ offset 5, date: Tue Jan 1 2008
2007-12-27 20:48:38.249 Data refresh needed because no data exists for day @ offset 5 from 6PM - midnight.
2007-12-27 20:48:38.249 Refreshing data for Tue Jan 1 2008
2007-12-27 20:48:38.249 Retrieving datadirect data.
2007-12-27 20:48:38.250 Grabbing data for Thu Dec 27 2007 offset 5
2007-12-27 20:48:38.250 From Tue Jan 1 05:00:00 2008 to Wed Jan 2 05:00:00 2008 (UTC)
2007-12-27 20:48:38.250 Grabbing listing data
--20:48:38--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 57,297        55.93K/s             

20:48:39 (55.87 KB/s) - `-' saved [57297]

2007-12-27 20:48:39.604 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:42.071 Grab complete.  Actual data from Tue Jan 1 05:00:00 2008 to Wed Jan 2 05:00:00 2008 (UTC)
2007-12-27 20:48:42.072 Main temp tables populated.
2007-12-27 20:48:42.074 Did not find any new program data.
2007-12-27 20:48:42.074 
2007-12-27 20:48:42.075 Checking day @ offset 6, date: Wed Jan 2 2008
2007-12-27 20:48:42.075 Data refresh needed because no data exists for day @ offset 6 from 6PM - midnight.
2007-12-27 20:48:42.075 Refreshing data for Wed Jan 2 2008
2007-12-27 20:48:42.076 Retrieving datadirect data.
2007-12-27 20:48:42.076 Grabbing data for Thu Dec 27 2007 offset 6
2007-12-27 20:48:42.076 From Wed Jan 2 05:00:00 2008 to Thu Jan 3 05:00:00 2008 (UTC)
2007-12-27 20:48:42.076 Grabbing listing data
--20:48:42--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 62,136        61.41K/s             

20:48:43 (61.35 KB/s) - `-' saved [62136]

2007-12-27 20:48:43.451 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:46.153 Grab complete.  Actual data from Wed Jan 2 05:00:00 2008 to Thu Jan 3 05:00:00 2008 (UTC)
2007-12-27 20:48:46.153 Main temp tables populated.
2007-12-27 20:48:46.156 Did not find any new program data.
2007-12-27 20:48:46.156 
2007-12-27 20:48:46.156 Checking day @ offset 7, date: Thu Jan 3 2008
2007-12-27 20:48:46.157 Data refresh needed because no data exists for day @ offset 7 from 6PM - midnight.
2007-12-27 20:48:46.157 Refreshing data for Thu Jan 3 2008
2007-12-27 20:48:46.157 Retrieving datadirect data.
2007-12-27 20:48:46.157 Grabbing data for Thu Dec 27 2007 offset 7
2007-12-27 20:48:46.157 From Thu Jan 3 05:00:00 2008 to Fri Jan 4 05:00:00 2008 (UTC)
2007-12-27 20:48:46.157 Grabbing listing data
--20:48:46--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [     <=>                             ] 63,224        23.37K/s             

20:48:52 (23.36 KB/s) - `-' saved [63224]

2007-12-27 20:48:52.210 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:54.981 Grab complete.  Actual data from Thu Jan 3 05:00:00 2008 to Fri Jan 4 05:00:00 2008 (UTC)
2007-12-27 20:48:54.981 Main temp tables populated.
2007-12-27 20:48:54.984 Did not find any new program data.
2007-12-27 20:48:54.984 
2007-12-27 20:48:54.984 Checking day @ offset 8, date: Fri Jan 4 2008
2007-12-27 20:48:54.985 Data refresh needed because no data exists for day @ offset 8 from 6PM - midnight.
2007-12-27 20:48:54.985 Refreshing data for Fri Jan 4 2008
2007-12-27 20:48:54.985 Retrieving datadirect data.
2007-12-27 20:48:54.985 Grabbing data for Thu Dec 27 2007 offset 8
2007-12-27 20:48:54.986 From Fri Jan 4 05:00:00 2008 to Sat Jan 5 05:00:00 2008 (UTC)
2007-12-27 20:48:54.986 Grabbing listing data
--20:48:54--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 62,110        59.10K/s             

20:48:56 (59.04 KB/s) - `-' saved [62110]

2007-12-27 20:48:56.761 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:48:59.470 Grab complete.  Actual data from Fri Jan 4 05:00:00 2008 to Sat Jan 5 05:00:00 2008 (UTC)
2007-12-27 20:48:59.470 Main temp tables populated.
2007-12-27 20:48:59.473 Did not find any new program data.
2007-12-27 20:48:59.473 
2007-12-27 20:48:59.473 Checking day @ offset 9, date: Sat Jan 5 2008
2007-12-27 20:48:59.474 Data refresh needed because no data exists for day @ offset 9 from 6PM - midnight.
2007-12-27 20:48:59.474 Refreshing data for Sat Jan 5 2008
2007-12-27 20:48:59.474 Retrieving datadirect data.
2007-12-27 20:48:59.474 Grabbing data for Thu Dec 27 2007 offset 9
2007-12-27 20:48:59.474 From Sat Jan 5 05:00:00 2008 to Sun Jan 6 05:00:00 2008 (UTC)
2007-12-27 20:48:59.475 Grabbing listing data
--20:48:59--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 60,230        53.62K/s             

20:49:00 (53.57 KB/s) - `-' saved [60230]

2007-12-27 20:49:00.934 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:49:03.531 Grab complete.  Actual data from Sat Jan 5 05:00:00 2008 to Sun Jan 6 05:00:00 2008 (UTC)
2007-12-27 20:49:03.532 Main temp tables populated.
2007-12-27 20:49:03.534 Did not find any new program data.
2007-12-27 20:49:03.534 
2007-12-27 20:49:03.534 Checking day @ offset 10, date: Sun Jan 6 2008
2007-12-27 20:49:03.535 Data refresh needed because no data exists for day @ offset 10 from 6PM - midnight.
2007-12-27 20:49:03.535 Refreshing data for Sun Jan 6 2008
2007-12-27 20:49:03.536 Retrieving datadirect data.
2007-12-27 20:49:03.536 Grabbing data for Thu Dec 27 2007 offset 10
2007-12-27 20:49:03.536 From Sun Jan 6 05:00:00 2008 to Mon Jan 7 05:00:00 2008 (UTC)
2007-12-27 20:49:03.536 Grabbing listing data
--20:49:03--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 56,157        55.81K/s             

20:49:04 (55.78 KB/s) - `-' saved [56157]

2007-12-27 20:49:04.947 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:49:07.390 Grab complete.  Actual data from Sun Jan 6 05:00:00 2008 to Mon Jan 7 05:00:00 2008 (UTC)
2007-12-27 20:49:07.391 Main temp tables populated.
2007-12-27 20:49:07.393 Did not find any new program data.
2007-12-27 20:49:07.393 
2007-12-27 20:49:07.393 Checking day @ offset 11, date: Mon Jan 7 2008
2007-12-27 20:49:07.394 Data refresh needed because no data exists for day @ offset 11 from 6PM - midnight.
2007-12-27 20:49:07.394 Refreshing data for Mon Jan 7 2008
2007-12-27 20:49:07.394 Retrieving datadirect data.
2007-12-27 20:49:07.395 Grabbing data for Thu Dec 27 2007 offset 11
2007-12-27 20:49:07.395 From Mon Jan 7 05:00:00 2008 to Tue Jan 8 05:00:00 2008 (UTC)
2007-12-27 20:49:07.395 Grabbing listing data
--20:49:07--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 59,507        43.48K/s             

20:49:09 (43.45 KB/s) - `-' saved [59507]

2007-12-27 20:49:09.113 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:49:11.753 Grab complete.  Actual data from Mon Jan 7 05:00:00 2008 to Tue Jan 8 05:00:00 2008 (UTC)
2007-12-27 20:49:11.754 Main temp tables populated.
2007-12-27 20:49:11.756 Did not find any new program data.
2007-12-27 20:49:11.757 
2007-12-27 20:49:11.757 Checking day @ offset 12, date: Tue Jan 8 2008
2007-12-27 20:49:11.757 Data refresh needed because no data exists for day @ offset 12 from 6PM - midnight.
2007-12-27 20:49:11.757 Refreshing data for Tue Jan 8 2008
2007-12-27 20:49:11.758 Retrieving datadirect data.
2007-12-27 20:49:11.758 Grabbing data for Thu Dec 27 2007 offset 12
2007-12-27 20:49:11.758 From Tue Jan 8 05:00:00 2008 to Wed Jan 9 05:00:00 2008 (UTC)
2007-12-27 20:49:11.758 Grabbing listing data
--20:49:11--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 59,798        54.28K/s             

20:49:13 (54.17 KB/s) - `-' saved [59798]

2007-12-27 20:49:13.244 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:49:15.936 Grab complete.  Actual data from Tue Jan 8 05:00:00 2008 to Wed Jan 9 05:00:00 2008 (UTC)
2007-12-27 20:49:15.936 Main temp tables populated.
2007-12-27 20:49:15.939 Did not find any new program data.
2007-12-27 20:49:15.939 
2007-12-27 20:49:15.939 Checking day @ offset 13, date: Wed Jan 9 2008
2007-12-27 20:49:15.940 Data refresh needed because no data exists for day @ offset 13 from 6PM - midnight.
2007-12-27 20:49:15.940 Refreshing data for Wed Jan 9 2008
2007-12-27 20:49:15.940 Retrieving datadirect data.
2007-12-27 20:49:15.941 Grabbing data for Thu Dec 27 2007 offset 13
2007-12-27 20:49:15.941 From Wed Jan 9 05:00:00 2008 to Thu Jan 10 05:00:00 2008 (UTC)
2007-12-27 20:49:15.941 Grabbing listing data
--20:49:15--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 60,014        50.37K/s             

20:49:17 (50.33 KB/s) - `-' saved [60014]

2007-12-27 20:49:17.492 DataDirect: Your subscription expires on 12/22/2008 06:36:29 PM
2007-12-27 20:49:20.160 Grab complete.  Actual data from Wed Jan 9 05:00:00 2008 to Thu Jan 10 05:00:00 2008 (UTC)
2007-12-27 20:49:20.161 Main temp tables populated.
2007-12-27 20:49:20.163 Did not find any new program data.
2007-12-27 20:49:20.166 New DB connection, total: 4
2007-12-27 20:49:20.167 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:49:20.168 New DB connection, total: 5
2007-12-27 20:49:20.168 Connected to database 'mythconverg' at host: localhost
2007-12-27 20:49:20.170 Failed to fetch some program info
2007-12-27 20:49:20.170 Adjusting program database end times.
2007-12-27 20:49:20.171     0 replacements made
2007-12-27 20:49:20.172 Marking generic episodes.
2007-12-27 20:49:20.172     Found 0
2007-12-27 20:49:20.172 Marking repeats.
2007-12-27 20:49:20.174     Found 0
2007-12-27 20:49:20.174 Unmarking new episode rebroadcast repeats.
2007-12-27 20:49:20.174     Found 0
2007-12-27 20:49:20.175 Marking episode first showings.
2007-12-27 20:49:20.175     Found 0
2007-12-27 20:49:20.175 Marking episode last showings.
2007-12-27 20:49:20.175     Found 0
2007-12-27 20:49:20.177 Grabbing next suggested grabbing time
2007-12-27 20:49:20.606 DataDirect: BlockedTime is: 2007-12-27T20:49:31
2007-12-27 20:49:20.607 DataDirect: NextSuggestedTime is: 2007-12-28T13:24:25
2007-12-27 20:49:20.610 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-12-27 20:49:20.613 Connecting to backend server: 192.168.2.65:6543 (try 1 of 5)
2007-12-27 20:49:20.614 Using protocol version 31
2007-12-27 20:49:20.624 mythfilldatabase run complete.
ICE default IO error handler doing an exit(), pid = 6306, errno = 32
2007-12-27 20:49:20.625 DataDirect: Deleting temporary files
john@babylon:/$

---

### Post by ZyzzyxU on 2007-12-27
I've got a similar problem. Been using everything fine for the last few weeks.  Came home to check things out tonight and my schedule is completely blank.  As such there are no upcoming recordings either.

I've run *mythfilldatabase* with no success.

I'm lost, wish I knew more of what was going on here. Guess this is gonna be a good time to learn. Would like to get it going before I leave for the weekend though.  (don't want to miss the *Twilight Zone* marathon)

```

2007-12-27 19:07:03.616 Using runtime prefix = /usr
2007-12-27 19:07:03.777 New DB connection, total: 1
2007-12-27 19:07:03.808 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:07:03.840 New DB connection, total: 2
2007-12-27 19:07:03.841 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:07:12.776 Updating source #1 (Cable) with grabber schedulesdirect1
2007-12-27 19:07:12.777 Found 81 channels for source 1 which use grabber
2007-12-27 19:07:12.778 
2007-12-27 19:07:12.778 Checking day @ offset 0, date: Thu Dec 27 2007
2007-12-27 19:07:13.710 Data is already present for Thu Dec 27 2007, skipping
2007-12-27 19:07:13.710 
2007-12-27 19:07:13.711 Checking day @ offset 1, date: Fri Dec 28 2007
2007-12-27 19:07:13.711 Data Refresh always needed for tomorrow
2007-12-27 19:07:13.711 Refreshing data for Fri Dec 28 2007
2007-12-27 19:07:13.712 New DB DataDirect connection
2007-12-27 19:07:13.714 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:07:13.809 Retrieving datadirect data.
2007-12-27 19:07:13.809 Grabbing data for Thu Dec 27 2007 offset 1
2007-12-27 19:07:13.809 From Fri Dec 28 08:00:00 2007 to Sat Dec 29 08:00:00 2007 (UTC)
2007-12-27 19:07:13.810 Grabbing listing data
--19:07:14--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [         <=>                         ] 198,959       97.51K/s             

19:07:27 (97.33 KB/s) - `-' saved [198959]

2007-12-27 19:07:27.486 DataDirect: Your subscription expires on 12/15/2008 02:23:25 PM
2007-12-27 19:07:27.786 New DB connection, total: 3
2007-12-27 19:07:27.787 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:07:27.788 sourceid 1 has lineup type: Cable
2007-12-27 19:07:58.912 Grab complete.  Actual data from Fri Dec 28 08:00:00 2007 to Sat Dec 29 08:00:00 2007 (UTC)
2007-12-27 19:07:58.913 Main temp tables populated.
2007-12-27 19:07:58.914 Updating myth channels.
2007-12-27 19:07:58.990 Updating icons for sourceid: 1
2007-12-27 19:07:59.018 Channels updated.
2007-12-27 19:07:59.338 Clearing data for source.
2007-12-27 19:07:59.338 Clearing from Fri Dec 28 00:00:00 2007 to Sat Dec 29 00:00:00 2007 (localtime)
2007-12-27 19:07:59.341 New DB connection, total: 4
2007-12-27 19:07:59.342 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:08:13.699 Data for source cleared.
2007-12-27 19:08:13.699 Updating programs.
2007-12-27 19:08:19.751 Program table update complete.
2007-12-27 19:08:19.751 
2007-12-27 19:08:19.751 Checking day @ offset 2, date: Sat Dec 29 2007
2007-12-27 19:08:20.035 Data is already present for Sat Dec 29 2007, skipping
2007-12-27 19:08:20.035 
2007-12-27 19:08:20.035 Checking day @ offset 3, date: Sun Dec 30 2007
2007-12-27 19:08:20.234 Data is already present for Sun Dec 30 2007, skipping
2007-12-27 19:08:20.234 
2007-12-27 19:08:20.234 Checking day @ offset 4, date: Mon Dec 31 2007
2007-12-27 19:08:20.471 Data is already present for Mon Dec 31 2007, skipping
2007-12-27 19:08:20.472 
2007-12-27 19:08:20.472 Checking day @ offset 5, date: Tue Jan 1 2008
2007-12-27 19:08:20.655 Data is already present for Tue Jan 1 2008, skipping
2007-12-27 19:08:20.655 
2007-12-27 19:08:20.655 Checking day @ offset 6, date: Wed Jan 2 2008
2007-12-27 19:08:20.838 Data is already present for Wed Jan 2 2008, skipping
2007-12-27 19:08:20.838 
2007-12-27 19:08:20.839 Checking day @ offset 7, date: Thu Jan 3 2008
2007-12-27 19:08:21.075 Data is already present for Thu Jan 3 2008, skipping
2007-12-27 19:08:21.075 
2007-12-27 19:08:21.076 Checking day @ offset 8, date: Fri Jan 4 2008
2007-12-27 19:08:21.268 Data is already present for Fri Jan 4 2008, skipping
2007-12-27 19:08:21.268 
2007-12-27 19:08:21.268 Checking day @ offset 9, date: Sat Jan 5 2008
2007-12-27 19:08:21.509 Data is already present for Sat Jan 5 2008, skipping
2007-12-27 19:08:21.509 
2007-12-27 19:08:21.510 Checking day @ offset 10, date: Sun Jan 6 2008
2007-12-27 19:08:21.687 Data is already present for Sun Jan 6 2008, skipping
2007-12-27 19:08:21.687 
2007-12-27 19:08:21.687 Checking day @ offset 11, date: Mon Jan 7 2008
2007-12-27 19:08:21.915 Data is already present for Mon Jan 7 2008, skipping
2007-12-27 19:08:21.915 
2007-12-27 19:08:21.915 Checking day @ offset 12, date: Tue Jan 8 2008
2007-12-27 19:08:22.146 Data is already present for Tue Jan 8 2008, skipping
2007-12-27 19:08:22.146 
2007-12-27 19:08:22.146 Checking day @ offset 13, date: Wed Jan 9 2008
2007-12-27 19:08:22.324 Data is already present for Wed Jan 9 2008, skipping
2007-12-27 19:08:29.846 New DB connection, total: 5
2007-12-27 19:08:29.847 Connected to database 'mythconverg' at host: localhost
2007-12-27 19:08:29.949 Data fetching complete.
2007-12-27 19:08:29.949 Adjusting program database end times.
2007-12-27 19:08:32.297     0 replacements made
2007-12-27 19:08:32.297 Marking generic episodes.
2007-12-27 19:08:32.857     Found 524
2007-12-27 19:08:32.857 Marking repeats.
2007-12-27 19:08:33.277     Found 52
2007-12-27 19:08:33.277 Unmarking new episode rebroadcast repeats.
2007-12-27 19:08:33.737     Found 136
2007-12-27 19:08:34.652 Marking episode first showings.
2007-12-27 19:09:00.889     Found 14411
2007-12-27 19:09:00.889 Marking episode last showings.
2007-12-27 19:09:27.494     Found 14411
2007-12-27 19:09:27.756 Grabbing next suggested grabbing time
2007-12-27 19:09:29.146 DataDirect: BlockedTime is: 2007-12-27T19:09:19
2007-12-27 19:09:29.148 DataDirect: NextSuggestedTime is: 2007-12-28T21:55:02
2007-12-27 19:09:29.275 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-12-27 19:09:29.325 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-12-27 19:09:29.327 Using protocol version 31
2007-12-27 19:09:29.480 mythfilldatabase run complete.
ICE default IO error handler doing an exit(), pid = 6119, errno = 32
2007-12-27 19:09:29.487 DataDirect: Deleting temporary files

```

---

### Post by ZyzzyxU on 2007-12-27
Well, don't know if this will be the same as the OP, but I fixed mine. Turned out to be a corrupt table.  Ran *mysqlcheck --repair -umythtv -p mythconverg* to repair it (after some research on that command) and looks like things are a go for me again.

---

### Post by John Lentz on 2007-12-28
I could try that, but mine is a new install.  I've installed mythbuntu more than once (because I messed things up while learning), and each time the program guide has never populated.  So I think I'm just not getting something set up properly from the beginning.  However, I'm not sure what the absolute minimum is needed to get the program guide to work.  All I've set up is the info for the Schedules Direct account.

John

---

### Post by Lido on 2008-01-06
I was having the problem here. Lots of "401 Unauthorized" and "500 Internal Server Error" messages. I put in my user name and password a bunch of times and still got the error. Then I noticed a post on the SD forums where someone mentioned that you have to add a "lineup" to an SD account to get it to work. I just did that. Not sure if it will fix the problem, but I'm hoping it will.

---

### Post by openbox9 on 2008-01-09
John, I don't know if you've solved your problem yet or not. I had the same problem as you and I fixed it by removing all of my tuners and then adding them back and selecting "Fetch channels from listings source" for each tuner under the Input connections in MythTV Setup. Originally, I scanned for my channels which apparently doesn't work even though I was using my SD setup.

---

### Post by Lido on 2008-01-09
I've tried that but my schedule is still blank. I can get the lineup name to show up, but when I select "Fetch channels from listing source" nothing happens. I've got two tuner cards sharing one listing source. Could that be the problem?

> **openbox9 said:**
> John, I don't know if you've solved your problem yet or not. I had the same problem as you and I fixed it by removing all of my tuners and then adding them back and selecting "Fetch channels from listings source" for each tuner under the Input connections in MythTV Setup. Originally, I scanned for my channels which apparently doesn't work even though I was using my SD setup.

---

### Post by LarryJ2 on 2008-06-13
I had a problem where there was no future (past todays date) program guide listings.  I did the usual  mythfilldatabase --xxx but nothing helped.   I ran the perl repair database script... nothing.   So I deleted all the tuners following "openbox9" suggestions.  mythfilldatabase ran immediately after exiting  mythbackend setup and the guide then showed normal 14 days of listings.

I think I messed this up when trying to set up a second backend.  I noticed that I had a status message that showed two extra tuners located on another machine.  

Thanks  OpenBox9 for the hint.

---

### Post by rkn5555 on 2008-08-26
> **John Lentz said:**
> I could try that, but mine is a new install.  I've installed mythbuntu more than once (because I messed things up while learning), and each time the program guide has never populated.  So I think I'm just not getting something set up properly from the beginning.  However, I'm not sure what the absolute minimum is needed to get the program guide to work.  All I've set up is the info for the Schedules Direct account.

John
you need to go to [https://www.schedulesdirect.org/account](https://www.schedulesdirect.org/account)
in your regular browser from any computer. and there click the link
Subscribed Lineups:
Add a new lineup 
and follow gettin your local line up listed

---

