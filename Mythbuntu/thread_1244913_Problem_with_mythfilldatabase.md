---
title: "Problem with mythfilldatabase"
date: 2009-08-20
forum: Mythbuntu
---

### Post by PlatosGimp on 2009-08-20
I just setup mythbuntu 9.04 on a SMF Shuttle machine, Athlon 2400, 1gb etc. Video card is a Happauge PVR-350. I "beleive" I have the tuner channel setup properly as the only source right now. I then signed up for the schedulesdirect account and entered this info into the configuration area for mythbuntu. I also did a channel scan and channels did seem to be located. However, when I go to "Watch TV" nothing happens, just a black screen? Also, when I try to run mythfilldatabase, no scheduling/program info seems to be located although a connection seems to be made?

Any suggestions? I am new to mythtv

Some lines from running mythfilldatabase:


2009-08-19 20:46:09.230 Using runtime prefix = /usr
2009-08-19 20:46:09.231 Empty LocalHostName.
2009-08-19 20:46:09.232 Using localhost value of shuttle
2009-08-19 20:46:09.246 New DB connection, total: 1
2009-08-19 20:46:09.252 Connected to database 'mythconverg' at host: localhost
2009-08-19 20:46:09.253 Closing DB connection named 'DBManager0'
2009-08-19 20:46:09.254 Connected to database 'mythconverg' at host: localhost
2009-08-19 20:46:09.257 New DB connection, total: 2
2009-08-19 20:46:09.258 Connected to database 'mythconverg' at host: localhost
2009-08-19 20:46:09.260 Updating source #1 (Cable TV) with grabber schedulesdirect1
2009-08-19 20:46:09.261 No channels are configured to use grabber.
2009-08-19 20:46:09.261 
2009-08-19 20:46:09.261 Checking day @ offset 0, date: Wed Aug 19 2009
2009-08-19 20:46:09.263 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2009-08-19 20:46:09.263 Refreshing data for Wed Aug 19 2009
2009-08-19 20:46:09.264 New DB DataDirect connection
2009-08-19 20:46:09.265 Connected to database 'mythconverg' at host: localhost
2009-08-19 20:46:09.266 Retrieving datadirect data.
2009-08-19 20:46:09.266 Grabbing data for Wed Aug 19 2009 offset 0
2009-08-19 20:46:09.266 From Wed Aug 19 07:00:00 2009 to Thu Aug 20 07:00:00 2009 (UTC)
2009-08-19 20:46:09.267 Grabbing listing data
--2009-08-19 20:46:09--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-08-19 20:46:09 ERROR 500: Internal Server Error.

2009-08-19 20:46:09.822 Grab complete.  Actual data from  to  (UTC)
2009-08-19 20:46:09.823 Main temp tables populated.
2009-08-19 20:46:09.823 Updating myth channels.
2009-08-19 20:46:09.836 New DB connection, total: 3
2009-08-19 20:46:09.836 Connected to database 'mythconverg' at host: localhost
2009-08-19 20:46:09.848 Updating icons for sourceid: 1
2009-08-19 20:46:09.850 Channels updated.
2009-08-19 20:46:09.862 Did not find any new program data.
2009-08-19 20:46:09.862 
2009-08-19 20:46:09.862 Checking day @ offset 1, date: Thu Aug 20 2009
2009-08-19 20:46:09.862 Data Refresh always needed for tomorrow
2009-08-19 20:46:09.862 Refreshing data for Thu Aug 20 2009
2009-08-19 20:46:09.863 Retrieving datadirect data.
2009-08-19 20:46:09.863 Grabbing data for Wed Aug 19 2009 offset 1
2009-08-19 20:46:09.863 From Thu Aug 20 07:00:00 2009 to Fri Aug 21 07:00:00 2009 (UTC)
2009-08-19 20:46:09.863 Grabbing listing data
--2009-08-19 20:46:09--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-08-19 20:46:10 ERROR 500: Internal Server Error.

---

### Post by danwood76 on 2009-08-20
> **PlatosGimp said:**
> --2009-08-19 20:46:09-- [http://webservices.schedulesdirect.t...gs/xtvdService](http://webservices.schedulesdirect.t...gs/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144. 142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-08-19 20:46:09 ERROR 500: Internal Server Error.

This is an error with the listings and so it will probably not find any channels.
Check your configuration of the grabber, I have no experiance with schedulesdirect.

---

### Post by cat2005 on 2009-10-10
Was anyone able to resolve this?  I am having a similar problem.

---

