---
title: "LiveTV on Mythbuntu 9.10 stopped working"
date: 2010-01-01
forum: Mythbuntu
---

### Post by MountainX on 2010-01-01
I have not watched TV in about a month. Today I tried to watch LiveTV on Myth .22 and it simply exits back to the menu with no TV played. Here are the sections of the logs that I think are relevant:

```
2010-01-01 13:02:01.631 MythContext: Connecting to backend server: 192.168.1.107:6543 (try 1 of 1)
2010-01-01 13:02:01.649 Using protocol version 50
2010-01-01 13:02:04.132 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-01 13:02:04.133 MythContext: Connecting to backend server: 192.168.1.107:6543 (try 1 of 1)
2010-01-01 13:02:04.135 Using protocol version 50
2010-01-01 13:02:04.143 Spawning LiveTV Recorder -- begin
2010-01-01 13:02:04.548 Spawning LiveTV Recorder -- end
2010-01-01 13:02:04.549 GetEntryAt(-1) failed.
2010-01-01 13:02:04.550 EntryToProgram(0@Wed Dec 31 19:00:00 1969) **failed to get pginfo**
2010-01-01 13:02:04.550 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-01 13:02:04.550 We have a RingBuffer
2010-01-01 13:02:04.614 TV Error: LiveTV not successfully started
2010-01-01 13:02:04.635 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-01 13:02:04.636 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-01 13:02:13.654 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```

After seeing mention of "failed to get pginfo" I looked back a little further in the logs and found this, which seems to indicate no problems with scheduling data:

```
2009-12-31 09:58:57.100 Checking day @ offset 12, date: Tue Jan 12 2010
2009-12-31 09:58:57.432 Data is already present for Tue Jan 12 2010, skipping
2009-12-31 09:58:57.432 
2009-12-31 09:58:57.432 Checking day @ offset 13, date: Wed Jan 13 2010
2009-12-31 09:58:57.606 Data refresh needed because only 0 out of 374 channels have at least one program listed for day @ offset 13 from 8PM - midnight.  Previous day had 373 channels with data in that time period.
2009-12-31 09:58:57.606 Refreshing data for Wed Jan 13 2010
2009-12-31 09:58:57.606 Retrieving datadirect data.
2009-12-31 09:58:57.607 Grabbing data for Thu Dec 31 2009 offset 13
2009-12-31 09:58:57.607 From Wed Jan 13 05:00:00 2010 to Thu Jan 14 05:00:00 2010 (UTC)
2009-12-31 09:58:57.607 Grabbing listing data
--2009-12-31 09:58:57--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

     0K .......... .......... .......... .......2009-12-31 09:59:23.375 DataDirect: Your subscription expires on Thu Jan 7 (2010) 9:12 PM
... .......... 1.98K
    50K .......... .......... .......... .......... .......... 4.93K
   100K .......... .......... .......... .......... .......... 26.0K
   150K .......... .......... .......... .......... .......... 30.0K
   200K .......... .......... .......... .......... .......... 52.2K
   250K .......... .......... .......... .......... ..........  146K
   300K .......... .......... .......... .......... .......... 79.3K
   350K .......... .......... .......... .......... .......... 35.9K
   400K .......... .......... .......... .......... .......... 20.1K
   450K .......... .......... .......                          11.6K=47s

2009-12-31 09:59:45 (10.1 KB/s) - `-' saved [488606]

2009-12-31 09:59:52.938 Grab complete.  Actual data from Wed Jan 13 05:00:00 2010 to Thu Jan 14 05:00:00 2010 (UTC)
2009-12-31 09:59:52.939 Main temp tables populated.
2009-12-31 09:59:53.532 Clearing data for source.
2009-12-31 09:59:53.532 Clearing from Wed Jan 13 00:00:00 2010 to Thu Jan 14 00:00:00 2010 (localtime)
2009-12-31 09:59:54.356 Data for source cleared.
2009-12-31 09:59:54.356 Updating programs.
2009-12-31 10:00:00.976 Program table update complete.
2009-12-31 10:00:03.182 Source 2 configured to use only the broadcasted guide data. Skipping.
2009-12-31 10:00:03.185 Data fetching complete.
2009-12-31 10:00:03.185 Adjusting program database end times.
2009-12-31 10:00:10.242     0 replacements made
2009-12-31 10:00:10.243 Marking generic episodes.
2009-12-31 10:00:12.949     Found 5854
2009-12-31 10:00:12.950 Fudging non-unique programids with multiple parts.
2009-12-31 10:00:13.526     Found -1
2009-12-31 10:00:13.526 Marking repeats.
2009-12-31 10:00:16.250     Found 11978
2009-12-31 10:00:16.250 Unmarking new episode rebroadcast repeats.
2009-12-31 10:00:18.538     Found 0
2009-12-31 10:00:22.442 Marking episode first showings.
2009-12-31 10:00:46.127     Found 36248
2009-12-31 10:00:46.127 Marking episode last showings.
2009-12-31 10:01:09.544     Found 36248
2009-12-31 10:01:09.670 Grabbing next suggested grabbing time
2009-12-31 10:01:10.283 DataDirect: BlockedTime is: 2009-12-31T10:01:10
2009-12-31 10:01:10.284 DataDirect: NextSuggestedTime is: 2010-01-01T23:42:48
2009-12-31 10:01:10.288 
```

I also reviewed the backend setup and it seems OK. Nothing has changed afaik. After I exited backendsetup I ran mythfilldatabase again, and tried LiveTV again, and it still exits without playing.

The only thing that has happened recently are the Mythbuntu updates. (BTW, my system is completely up to date.) 

So that leaves me without a clue what the problem could be. I'm new to MythTV.

---

### Post by My Name on 2010-02-07
Did anyone get anywhere with this?
I have the same problem with the same error

---

### Post by rbrown3 on 2010-03-16
Actually, I have just installed Mythbuntu 9.10, and I have a very similar problem with similar logs.

Could someone please advise on this matter?

Thanks in advance...

---

### Post by larsolav on 2010-03-17
This link may help:
[http://www.gossamer-threads.com/lists/mythtv/users/409738](http://www.gossamer-threads.com/lists/mythtv/users/409738)

---

