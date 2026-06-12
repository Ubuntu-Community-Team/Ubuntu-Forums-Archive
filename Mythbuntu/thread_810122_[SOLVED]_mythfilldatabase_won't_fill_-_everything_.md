---
title: "[SOLVED] mythfilldatabase won't fill - everything else works!"
date: 2008-05-28
forum: Mythbuntu
---

### Post by jubxie on 2008-05-28
Well, I've been battling this for two days now. I can't get mythfilldatabase to fill the program guide. I'm using schedules direct. I have had it working on previous frontend/backend systems. I installed the new backend/frontend on my main desktop with an existing desktop install. Everything works;watching tv, recording, everything....except this. Specs:

hardy i386
intel q6600/intel dq35joe
hdhomerun tuner

I even tried changing the password on schedules direct. Something I did caused it to add a few hours of info, but I don't know what I did. Been reading the forums and tried all the easy things. Any ideas?? I feel like it is a permissions or mysql issue, I just don't know anything about mysql. Here is some printout. Thanks!!

```
2008-05-27 21:06:50.804 DataDirect: Your subscription expires on 25/12/08 10:30:17 PM
2008-05-27 21:06:51.585 Grab complete.  Actual data from Sun Jun 8 07:00:00 2008 to Mon Jun 9 07:00:00 2008 (UTC)
2008-05-27 21:06:51.585 Main temp tables populated.
2008-05-27 21:06:51.601 Did not find any new program data.
2008-05-27 21:06:51.601 
2008-05-27 21:06:51.601 Checking day @ offset 13, date: Mon Jun 9 2008
2008-05-27 21:06:51.601 Data Refresh needed because of user request
2008-05-27 21:06:51.601 Refreshing data for Mon Jun 9 2008
2008-05-27 21:06:51.602 Retrieving datadirect data.
2008-05-27 21:06:51.602 Grabbing data for Tue May 27 2008 offset 13
2008-05-27 21:06:51.602 From Mon Jun 9 07:00:00 2008 to Tue Jun 10 07:00:00 2008 (UTC)
2008-05-27 21:06:51.602 Grabbing listing data
--21:06:51--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [   <=>                               ] 44,163        53.11K/s             

21:06:52 (53.08 KB/s) - `-' saved [44163]

2008-05-27 21:06:52.922 DataDirect: Your subscription expires on 25/12/08 10:30:17 PM
2008-05-27 21:06:53.887 Grab complete.  Actual data from Mon Jun 9 07:00:00 2008 to Tue Jun 10 07:00:00 2008 (UTC)
2008-05-27 21:06:53.888 Main temp tables populated.
2008-05-27 21:06:53.906 Did not find any new program data.
2008-05-27 21:06:53.906 Failed to fetch some program info
2008-05-27 21:06:53.906 Adjusting program database end times.
2008-05-27 21:06:53.907     0 replacements made
2008-05-27 21:06:53.907 Marking generic episodes.
2008-05-27 21:06:53.908     Found 0
2008-05-27 21:06:53.908 Marking repeats.
2008-05-27 21:06:53.910     Found 0
2008-05-27 21:06:53.910 Unmarking new episode rebroadcast repeats.
2008-05-27 21:06:53.910     Found 0
2008-05-27 21:06:53.913 Marking episode first showings.
2008-05-27 21:06:53.942     Found 98
2008-05-27 21:06:53.942 Marking episode last showings.
2008-05-27 21:06:53.971     Found 98
2008-05-27 21:06:53.972 Grabbing next suggested grabbing time
2008-05-27 21:06:54.385 DataDirect: BlockedTime is: 2008-05-27T21:06:54
2008-05-27 21:06:54.385 DataDirect: NextSuggestedTime is: 2008-05-28T19:17:01
2008-05-27 21:06:54.387 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-05-27 21:06:54.390 Connecting to backend server: 192.168.0.101:6543 (try 1 of 5)
2008-05-27 21:06:54.391 Using protocol version 40
2008-05-27 21:06:54.409 Received a remote 'Clear Cache' request
2008-05-27 21:06:54.410 mythfilldatabase run complete.
2008-05-27 21:06:54.414 DataDirect: Deleting temporary files

```

---

### Post by jubxie on 2008-05-28
Well, using phpmyadmin, I can't find new program data in the database. Seems funny that the collation would be latin1_swedish?(since im in the us). The few programs that did download are there though. I'm at a loss. I looks like the data is not getting into the mysql database. Any ideas why?

---

### Post by jubxie on 2008-05-30
Got it! I needed to add the xmlid for each channel as I am using QAM. I forgot I had done this on the last install. That was it!

---

