---
title: "Can't retrieve lineups or schedules in backend setup"
date: 2008-01-07
forum: Mythbuntu
---

### Post by Lido on 2008-01-07
I've got my Schedules Direct account set up and a lineup selected on the site, but when I run the backend setup and click "retrieve lineups", nothing comes up. Then I can't get the schedule data either. I am sure I entered my username and pw correctly in the mythtv backend setup under Video sources. Any suggestions?

Here are the errors I'm getting when I run mythfilldatabase, but this may be due to the fact that mythtv doesn't have a lineup selected in the backend, I don't know. Maybe the 401 unauth error and the 500 internal server error are also causing the  problem retrieving the lineups in the backend setup (also note the segmentation fault at the very end, what's that all about?).
```

Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to [COLOR="Red"]webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
23:37:38 ERROR 500: Internal Server Error.
[/COLOR]
2008-01-06 23:37:38.924 Grab complete.  Actual data from  to  (UTC)
2008-01-06 23:37:38.924 Main temp tables populated.
2008-01-06 23:37:38.925 [COLOR="Red"]DataDirect, Error: UpdateProgramViewTable no dd_state![/COLOR]
2008-01-06 23:37:38.925 Did not find any new program data.
2008-01-06 23:37:38.927 New DB connection, total: 4
2008-01-06 23:37:38.928 Connected to database 'mythconverg' at host: localhost
2008-01-06 23:37:38.929 New DB connection, total: 5
2008-01-06 23:37:38.930 Connected to database 'mythconverg' at host: localhost
2008-01-06 23:37:38.932 Failed to fetch some program info
2008-01-06 23:37:38.932 Adjusting program database end times.
2008-01-06 23:37:38.932     0 replacements made
2008-01-06 23:37:38.933 Marking generic episodes.
2008-01-06 23:37:38.933     Found 0
2008-01-06 23:37:38.933 Marking repeats.
2008-01-06 23:37:38.934     Found 0
2008-01-06 23:37:38.934 Unmarking new episode rebroadcast repeats.
2008-01-06 23:37:38.934     Found 0
2008-01-06 23:37:38.934 Marking episode first showings.
2008-01-06 23:37:38.934     Found 0
2008-01-06 23:37:38.934 Marking episode last showings.
2008-01-06 23:37:38.935     Found 0
2008-01-06 23:37:38.936 Grabbing next suggested grabbing time
2008-01-06 23:37:39.455 DataDirect: BlockedTime is: 2008-01-06T23:37:38
2008-01-06 23:37:39.456 DataDirect: NextSuggestedTime is: 2008-01-08T02:32:22
2008-01-06 23:37:39.457 DataDirect: Provider suggested running again at 2008-01-08T02:32:22, but MythFillPeriod is 1.  Next run time will be adjusted to be 2008-01-07T02:32:22.
2008-01-06 23:37:39.459 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-01-06 23:37:39.462 Connecting to backend server: 192.168.1.3:6543 (try 1 of 5)
2008-01-06 23:37:39.463 Using protocol version 31
2008-01-06 23:37:39.477 mythfilldatabase run complete.
2008-01-06 23:37:39.478 Received a remote 'Clear Cache' request
[COLOR="Red"]Segmentation fault (core dumped)[/COLOR]

```

---

### Post by volkswagner on 2008-01-07
You are not alone.

[http://forums.schedulesdirect.org/viewtopic.php?f=5&t=475]("http://forums.schedulesdirect.org/viewtopic.php?f=5&t=475")

Some had it work out over time without any changes.  One poster changed his password back to itself.

You may need to give it time.

---

### Post by Lido on 2008-01-07
Thanks. Yeah, I read that thread. My password is the same as it was when the account was set up so I guess that leaves 'waiting' as my only option. Unfortunately my seven day test account expires today.

---

### Post by taehC on 2008-01-08
make sure that your name and password is correct.
when i set mine up my user name had a capital when i entered it in at SD but when i entered it in the backend setup i had to do all lowercase.

---

### Post by Lido on 2008-01-08
I think there was a problem with schedules direct. I emailed them today and they said to try again now. I did and I was able to get mythfilldatabase to connect. Same username and pw. Unfortunately the listings are coming up blank when I go the the frontend and hit "Watch TV". It shows the guide but it's blank. I think the issue is related to the fact that nothing happens when I'm in the backend setup under Input Connections and I select "Fetch channels from listing source" and nothing happens. Then when I exit setup I get two different the "Card x (type Television) is set to start on Channel 3, which does not exist" errors.

Here are two things that might be related from the output of mythfilldatabase. This:
```
2008-01-07 21:37:45.442 No channels are configured to use grabber.
```
and this:
```
ICE default IO error handler doing an exit(), pid = 7067, errno = 32

```

Here's the full output:```
~$ /usr/bin/mythfilldatabase
2008-01-07 21:37:45.423 Using runtime prefix = /usr
2008-01-07 21:37:45.433 New DB connection, total: 1
2008-01-07 21:37:45.437 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:37:45.441 New DB connection, total: 2
2008-01-07 21:37:45.441 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:37:45.442 Updating source #1 (SD) with grabber schedulesdirect1
2008-01-07 21:37:45.442 No channels are configured to use grabber.
2008-01-07 21:37:45.442 
2008-01-07 21:37:45.442 Checking day @ offset 0, date: Mon Jan 7 2008
2008-01-07 21:37:45.443 Data refresh needed because no data exists for day @ offset 0 from 6PM - midnight.
2008-01-07 21:37:45.443 Refreshing data for Mon Jan 7 2008
2008-01-07 21:37:45.443 New DB DataDirect connection
2008-01-07 21:37:45.444 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:37:45.446 Retrieving datadirect data.
2008-01-07 21:37:45.446 Grabbing data for Mon Jan 7 2008 offset 0
2008-01-07 21:37:45.446 From Mon Jan 7 08:00:00 2008 to Tue Jan 8 08:00:00 2008 (UTC)
2008-01-07 21:37:45.446 Grabbing listing data
--21:37:45--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                                                                                       ] 96,003        48.90K/s             

21:37:48 (48.79 KB/s) - `-' saved [96003]

2008-01-07 21:37:48.233 DataDirect: WARNING: Your subscription expires on 01/10/2008 02:07:42 AM
2008-01-07 21:37:48.265 New DB connection, total: 3
2008-01-07 21:37:48.265 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:37:48.266 sourceid 1 has lineup type: LocalBroadcast
2008-01-07 21:37:50.688 Grab complete.  Actual data from Mon Jan 7 08:00:00 2008 to Tue Jan 8 08:00:00 2008 (UTC)
2008-01-07 21:37:50.689 Main temp tables populated.
2008-01-07 21:37:50.689 Updating myth channels.
2008-01-07 21:37:50.692 DataDirect: Not adding channel 'KBEH' (KBEH).
2008-01-07 21:37:50.692 DataDirect: Not adding channel 'KTLADT (KTLA-DT)' (KTLADT).
2008-01-07 21:37:50.693 DataDirect: Not adding channel 'KCBSDT (KCBS-DT)' (KCBSDT).
2008-01-07 21:37:50.693 DataDirect: Not adding channel 'KNBCDT (KNBC-DT)' (KNBCDT).
2008-01-07 21:37:50.693 DataDirect: Not adding channel 'KABCDT (KABC-DT)' (KABCDT).
2008-01-07 21:37:50.694 DataDirect: Not adding channel 'KCOPDT (KCOP-DT)' (KCOPDT).
2008-01-07 21:37:50.694 DataDirect: Not adding channel 'KCALDT (KCAL-DT)' (KCALDT).
2008-01-07 21:37:50.694 DataDirect: Not adding channel 'KTTVDT (KTTV-DT)' (KTTVDT).
2008-01-07 21:37:50.695 DataDirect: Not adding channel 'KCETDT (KCET-DT)' (KCETDT).
2008-01-07 21:37:50.695 DataDirect: Not adding channel 'KWHYDT (KWHY-DT)' (KWHYDT).
2008-01-07 21:37:50.695 DataDirect: Not adding channel 'KSCIDT (KSCI-DT)' (KSCIDT).
2008-01-07 21:37:50.696 DataDirect: Not adding channel 'KOCEDT (KOCE-DT)' (KOCEDT).
2008-01-07 21:37:50.696 DataDirect: Not adding channel 'KRCADT (KRCA-DT)' (KRCADT).
2008-01-07 21:37:50.696 DataDirect: Not adding channel 'KCETDT2 (KCET-DT2)' (KCETDT2).
2008-01-07 21:37:50.697 DataDirect: Not adding channel 'KABCDT2 (KABC-DT2)' (KABCDT2).
2008-01-07 21:37:50.697 DataDirect: Not adding channel 'KABCDT3 (KABC-DT3)' (KABCDT3).
2008-01-07 21:37:50.697 DataDirect: Not adding channel 'KVEADT (KVEA-DT)' (KVEADT).
2008-01-07 21:37:50.698 DataDirect: Not adding channel 'KXLADT (KXLA-DT)' (KXLADT).
2008-01-07 21:37:50.698 DataDirect: Not adding channel 'KXLADT2 (KXLA-DT2)' (KXLADT2).
2008-01-07 21:37:50.698 DataDirect: Not adding channel 'KMEXDT (KMEX-DT)' (KMEXDT).
2008-01-07 21:37:50.699 DataDirect: Not adding channel 'KDOCDT (KDOC-DT)' (KDOCDT).
2008-01-07 21:37:50.699 DataDirect: Not adding channel 'KAZADT (KAZA-DT)' (KAZADT).
2008-01-07 21:37:50.699 DataDirect: Not adding channel 'KLCSDT (KLCS-DT)' (KLCSDT).
2008-01-07 21:37:50.700 DataDirect: Not adding channel 'KLCSDT2 (KLCS-DT2)' (KLCSDT2).
2008-01-07 21:37:50.700 DataDirect: Not adding channel 'KLCSDT3 (KLCS-DT3)' (KLCSDT3).
2008-01-07 21:37:50.700 DataDirect: Not adding channel 'KLCSDT4 (KLCS-DT4)' (KLCSDT4).
2008-01-07 21:37:50.700 DataDirect: Not adding channel 'KMEXDT2 (KMEX-DT2)' (KMEXDT2).
2008-01-07 21:37:50.701 DataDirect: Not adding channel 'KVCRDT (KVCR-DT)' (KVCRDT).
2008-01-07 21:37:50.701 DataDirect: Not adding channel 'KNBCDT2 (KNBC-DT2)' (KNBCDT2).
2008-01-07 21:37:50.702 DataDirect: Not adding channel 'KOCEDT2 (KOCE-DT2)' (KOCEDT2).
2008-01-07 21:37:50.703 DataDirect: Not adding channel 'KPXNDT (KPXN-DT)' (KPXNDT).
2008-01-07 21:37:50.705 DataDirect: Not adding channel 'KPXNDT3 (KPXN-DT3)' (KPXNDT3).
2008-01-07 21:37:50.705 DataDirect: Not adding channel 'KPXNDT4 (KPXN-DT4)' (KPXNDT4).
2008-01-07 21:37:50.705 DataDirect: Not adding channel 'KJLADT (KJLA-DT)' (KJLADT).
2008-01-07 21:37:50.706 DataDirect: Not adding channel 'KPXNDT2 (KPXN-DT2)' (KPXNDT2).
2008-01-07 21:37:50.706 DataDirect: Not adding channel 'KTLADT5 (KTLA-DT5)' (KTLADT5).
2008-01-07 21:37:50.706 DataDirect: Not adding channel 'KTBNDT (KTBN-DT)' (KTBNDT).
2008-01-07 21:37:50.707 DataDirect: Not adding channel 'KJLADT2 (KJLA-DT2)' (KJLADT2).
2008-01-07 21:37:50.707 DataDirect: Not adding channel 'KJLADT3 (KJLA-DT3)' (KJLADT3).
2008-01-07 21:37:50.707 DataDirect: Not adding channel 'KFTRDT (KFTR-DT)' (KFTRDT).
2008-01-07 21:37:50.708 DataDirect: Not adding channel 'KNBCDT4 (KNBC-DT4)' (KNBCDT4).
2008-01-07 21:37:50.708 DataDirect: Not adding channel 'KTBNDT2 (KTBN-DT2)' (KTBNDT2).
2008-01-07 21:37:50.708 DataDirect: Not adding channel 'KTBN-DT3 (KTBN-DT3)' (KTBNDT3).
2008-01-07 21:37:50.709 DataDirect: Not adding channel 'KTBN-DT4 (KTBN-DT4)' (KTBNDT4).
2008-01-07 21:37:50.709 DataDirect: Not adding channel 'KTBN-DT5 (KTBN-DT5)' (KTBNDT5).
2008-01-07 21:37:50.709 DataDirect: Not adding channel 'KCETDT3 (KCET-DT3)' (KCETDT3).
2008-01-07 21:37:50.710 DataDirect: Not adding channel 'KJLADT4 (KJLA-DT4)' (KJLADT4).
2008-01-07 21:37:50.710 DataDirect: Not adding channel 'KOCEDT4 (KOCE-DT4)' (KOCEDT4).
2008-01-07 21:37:50.710 DataDirect: Not adding channel 'KCETDT4 (KCET-DT4)' (KCETDT4).
2008-01-07 21:37:50.710 Updating icons for sourceid: 1
2008-01-07 21:37:50.711 Channels updated.
2008-01-07 21:37:50.713 Did not find any new program data.
2008-01-07 21:37:50.713 
2008-01-07 21:37:50.713 Checking day @ offset 1, date: Tue Jan 8 2008
2008-01-07 21:37:50.713 Data Refresh always needed for tomorrow
2008-01-07 21:37:50.713 Refreshing data for Tue Jan 8 2008
2008-01-07 21:37:50.714 Retrieving datadirect data.
2008-01-07 21:37:50.714 Grabbing data for Mon Jan 7 2008 offset 1
2008-01-07 21:37:50.714 From Tue Jan 8 08:00:00 2008 to Wed Jan 9 08:00:00 2008 (UTC)
2008-01-07 21:37:50.714 Grabbing listing data
--21:37:50--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                                                                                       ] 94,182        57.32K/s             

21:37:53 (57.24 KB/s) - `-' saved [94182]

2008-01-07 21:37:53.084 DataDirect: WARNING: Your subscription expires on 01/10/2008 02:07:42 AM
2008-01-07 21:37:55.564 Grab complete.  Actual data from Tue Jan 8 08:00:00 2008 to Wed Jan 9 08:00:00 2008 (UTC)
2008-01-07 21:37:55.564 Main temp tables populated.
2008-01-07 21:37:55.566 Did not find any new program data.
2008-01-07 21:37:55.566 
2008-01-07 21:37:55.567 Checking day @ offset 2, date: Wed Jan 9 2008
2008-01-07 21:37:55.567 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2008-01-07 21:37:55.567 Refreshing data for Wed Jan 9 2008
2008-01-07 21:37:55.567 Retrieving datadirect data.
2008-01-07 21:37:55.567 Grabbing data for Mon Jan 7 2008 offset 2
2008-01-07 21:37:55.567 From Wed Jan 9 08:00:00 2008 to Thu Jan 10 08:00:00 2008 (UTC)
2008-01-07 21:37:55.568 Grabbing listing data
--21:37:55--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [      <=>                                                                                       ] 94,371        50.11K/s             

21:37:58 (49.99 KB/s) - `-' saved [94371]

[...snip...]

2008-01-07 21:38:53.620 DataDirect: WARNING: Your subscription expires on 01/10/2008 02:07:42 AM
2008-01-07 21:38:56.023 Grab complete.  Actual data from Sun Jan 20 08:00:00 2008 to Mon Jan 21 08:00:00 2008 (UTC)
2008-01-07 21:38:56.023 Main temp tables populated.
2008-01-07 21:38:56.025 Did not find any new program data.
2008-01-07 21:38:56.027 New DB connection, total: 4
2008-01-07 21:38:56.027 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:38:56.028 New DB connection, total: 5
2008-01-07 21:38:56.029 Connected to database 'mythconverg' at host: localhost
2008-01-07 21:38:56.030 Failed to fetch some program info
2008-01-07 21:38:56.030 Adjusting program database end times.
2008-01-07 21:38:56.030     0 replacements made
2008-01-07 21:38:56.030 Marking generic episodes.
2008-01-07 21:38:56.030     Found 0
2008-01-07 21:38:56.031 Marking repeats.
2008-01-07 21:38:56.031     Found 0
2008-01-07 21:38:56.031 Unmarking new episode rebroadcast repeats.
2008-01-07 21:38:56.031     Found 0
2008-01-07 21:38:56.031 Marking episode first showings.
2008-01-07 21:38:56.032     Found 0
2008-01-07 21:38:56.032 Marking episode last showings.
2008-01-07 21:38:56.032     Found 0
2008-01-07 21:38:56.035 Grabbing next suggested grabbing time
2008-01-07 21:38:56.593 DataDirect: BlockedTime is: 2008-01-07T21:38:55
2008-01-07 21:38:56.593 DataDirect: NextSuggestedTime is: 2008-01-08T08:12:55
2008-01-07 21:38:56.596 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-01-07 21:38:56.598 Connecting to backend server: 192.168.1.3:6543 (try 1 of 5)
2008-01-07 21:38:56.599 Using protocol version 31
2008-01-07 21:38:56.618 mythfilldatabase run complete.
ICE default IO error handler doing an exit(), pid = 7067, errno = 32
2008-01-07 21:38:56.620 DataDirect: Deleting temporary files

```

---

