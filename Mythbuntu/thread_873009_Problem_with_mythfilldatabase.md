---
title: "Problem with mythfilldatabase"
date: 2008-07-28
forum: Mythbuntu
---

### Post by shawnblais on 2008-07-28
I am having a problem running mythfilldatabase. I setup an account with SchedulesDirect, and I have verified that I have the correct username and password entered in the backend setup. 

When it tries to get program listings, it starts downloading the file, but then stops and starts over again. Here is a portion of what I saw:

```

2008-07-28 15:04:13.660 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-28 15:04:13.674 Empty LocalHostName.
2008-07-28 15:04:13.676 Using localhost value of blais-dvr
2008-07-28 15:04:13.733 New DB connection, total: 1
2008-07-28 15:04:13.756 Connected to database 'mythconverg' at host: localhost
2008-07-28 15:04:13.761 Closing DB connection named 'DBManager0'
2008-07-28 15:04:13.766 Connected to database 'mythconverg' at host: localhost
2008-07-28 15:04:13.781 New DB connection, total: 2
2008-07-28 15:04:13.786 Connected to database 'mythconverg' at host: localhost
2008-07-28 15:04:13.790 Updating source #1 (SchedulesDirect.org) with grabber schedulesdirect1
2008-07-28 15:04:13.794 No channels are configured to use grabber.
2008-07-28 15:04:13.795 
2008-07-28 15:04:13.795 Checking day @ offset 0, date: Mon Jul 28 2008
2008-07-28 15:04:13.798 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2008-07-28 15:04:13.800 Refreshing data for Mon Jul 28 2008
2008-07-28 15:04:13.802 New DB DataDirect connection
2008-07-28 15:04:13.806 Connected to database 'mythconverg' at host: localhost
2008-07-28 15:04:13.811 Retrieving datadirect data.
2008-07-28 15:04:13.812 Grabbing data for Mon Jul 28 2008 offset 0
2008-07-28 15:04:13.813 From Mon Jul 28 04:00:00 2008 to Tue Jul 29 04:00:00 2008 (UTC)
2008-07-28 15:04:13.815 Grabbing listing data
--15:04:13--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [        <=>                          ] 198,181       84.55K/s             

15:04:17 (84.37 KB/s) - `-' saved [198181]

2008-07-28 15:04:17.817 DataDirect: Your subscription expires on 08/04/2008 10:18:35 AM
2008-07-28 15:04:18.440 New DB connection, total: 3
2008-07-28 15:04:18.453 Connected to database 'mythconverg' at host: localhost
2008-07-28 15:04:18.455 sourceid 1 has lineup type: Cable
2008-07-28 15:04:54.427 Grab complete.  Actual data from Mon Jul 28 04:00:00 2008 to Tue Jul 29 04:00:00 2008 (UTC)
2008-07-28 15:04:54.440 Main temp tables populated.
2008-07-28 15:04:54.452 Updating myth channels.
2008-07-28 15:04:54.483 DataDirect: Not inserting channels into disconnected source 1.
2008-07-28 15:04:54.483 Updating icons for sourceid: 1
2008-07-28 15:04:54.486 Channels updated.
2008-07-28 15:04:54.499 Did not find any new program data.
2008-07-28 15:04:54.500 
2008-07-28 15:04:54.500 Checking day @ offset 1, date: Tue Jul 29 2008
2008-07-28 15:04:54.500 Data Refresh always needed for tomorrow
2008-07-28 15:04:54.500 Refreshing data for Tue Jul 29 2008
2008-07-28 15:04:54.501 Retrieving datadirect data.
2008-07-28 15:04:54.502 Grabbing data for Mon Jul 28 2008 offset 1
2008-07-28 15:04:54.502 From Tue Jul 29 04:00:00 2008 to Wed Jul 30 04:00:00 2008 (UTC)
2008-07-28 15:04:54.502 Grabbing listing data
--15:04:54--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                            ] 199,865       78.82K/s             

15:04:59 (78.68 KB/s) - `-' saved [199865]

2008-07-28 15:04:59.859 DataDirect: Your subscription expires on 08/04/2008 10:18:35 AM

```

After it fails to download the file, I get the "DataDirect: Your subscription expires on 08/04/2008 10:18:35 AM" message, and then a it starts over with the same exact text. Any help you can provide would be appreciated!

Thanks,
Shawn

---

### Post by mrand on 2008-07-28
> **shawnblais said:**
> I am having a problem running mythfilldatabase. I setup an account with SchedulesDirect, and I have verified that I have the correct username and password entered in the backend setup. 

When it tries to get program listings, it starts downloading the file, but then stops and starts over again. Here is a portion of what I saw:

<...>

After it fails to download the file, I get the "DataDirect: Your subscription expires on 08/04/2008 10:18:35 AM" message, and then a it starts over with the same exact text. Any help you can provide would be appreciated!

Thanks,
ShawnHowdy Shawn, 

mythfilldatabase output is fairly cryptic and at first glance, repetitive.  I don't see it ultimately failing the grab.  It always gives everyone the "401 Unauthorized" on the first attempt for each connection. The retrieval appears to be working... your log shows: 

```
2008-07-28 15:04:13.800 Refreshing data for Mon Jul 28 2008
and
2008-07-28 15:04:13.813 From Mon Jul 28 04:00:00 2008 to Tue Jul 29 04:00:00 2008 (UTC)
and
2008-07-28 15:04:54.427 Grab complete.  Actual data from Mon Jul 28 04:00:00 2008 to Tue Jul 29 04:00:00 2008 (UTC)

and then later...

2008-07-28 15:04:54.500 Refreshing data for Tue Jul 29 2008
<and>
2008-07-28 15:04:54.502 From Tue Jul 29 04:00:00 2008 to Wed Jul 30 04:00:00 2008 (UTC)
```

This may be your problem though:
```
2008-07-28 15:04:54.483 DataDirect: Not inserting channels into disconnected source 1.
```

If you google that error message, the first hit suggests:
> Go into mythtv-setup and make sure you've defined your input connections. The input connections are what tell Myth which listings sources go with which capture card inputs.

[INDENT]Marc[/INDENT]

---

### Post by bah1976 on 2008-07-28
Also - let it run.  

Especially the first time, give it awhile to complete.  If you notice:
> 2008-07-28 15:04:13.795 Checking day @ offset 0, date: Mon Jul 28 2008
2008-07-28 15:04:13.798 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2008-07-28 15:04:13.800 Refreshing data for Mon Jul **28 **2008


And then:

> 2008-07-28 15:04:54.500 Checking day @ offset 1, date: Tue Jul 29 2008
2008-07-28 15:04:54.500 Data Refresh always needed for tomorrow
2008-07-28 15:04:54.500 Refreshing data for Tue Jul **29 **2008


It will run for 14 days worth of data, and just look like it's re-running.  Mine also only downloads a portion of the file - presumably because it doesn't need the entire thing.

This is, of course, in addition to making sure the connection is assigned to a card input in backend setup.

---

