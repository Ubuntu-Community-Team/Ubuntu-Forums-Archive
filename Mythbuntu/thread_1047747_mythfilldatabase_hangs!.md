---
title: "mythfilldatabase hangs!"
date: 2009-01-22
forum: Mythbuntu
---

### Post by AngelusNocits on 2009-01-22
Hi

I installed yesterday mythbuntu 8.10.

My problem is that mythfilldatabase hangs everytime on the same place!


```

angelus@Mediabox:~$ mythfilldatabase
2009-01-23 01:04:31.117 Using runtime prefix = /usr
2009-01-23 01:04:31.117 Empty LocalHostName.
2009-01-23 01:04:31.118 Using localhost value of Mediabox
2009-01-23 01:04:31.122 New DB connection, total: 1
2009-01-23 01:04:31.124 Connected to database 'mythconverg' at host: localhost
2009-01-23 01:04:31.125 Closing DB connection named 'DBManager0'
2009-01-23 01:04:31.125 Connected to database 'mythconverg' at host: localhost
2009-01-23 01:04:31.127 New DB connection, total: 2
2009-01-23 01:04:31.127 Connected to database 'mythconverg' at host: localhost
2009-01-23 01:04:32.000 Updating source #1 (Schweiz) with grabber tv_grab_ch_sea                                                                                                                                                             rch
2009-01-23 01:04:32.001 Found 99 channels for source 1 which use grabber
2009-01-23 01:04:32.269 Grabber has capabilities: baseline manualconfig cache
2009-01-23 01:04:32.269
2009-01-23 01:04:32.269 Checking day @ offset 0, date: Fre Jan 23 2009
2009-01-23 01:04:32.344 Data is already present for Fre Jan 23 2009, skipping
2009-01-23 01:04:32.344
2009-01-23 01:04:32.344 Checking day @ offset 1, date: Sam Jan 24 2009
2009-01-23 01:04:32.345 Data Refresh always needed for tomorrow
2009-01-23 01:04:32.345 Refreshing data for Sam Jan 24 2009
2009-01-23 01:04:32.345 New DB connection, total: 3
2009-01-23 01:04:32.345 Connected to database 'mythconverg' at host: localhost
2009-01-23 01:04:32.346 XMLTV config file is: /home/angelus/.mythtv/Schweiz.xmlt    
```

```
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
2009-01-23 01:16:34.317 Updating icons for sourceid: 1
2009-01-23 01:16:36.309 Updated programs: 126 Unchanged programs: 2558
2009-01-23 01:16:36.318
2009-01-23 01:16:36.318 Checking day @ offset 5, date: Mit Jan 28 2009
2009-01-23 01:16:36.371 Data is already present for Mit Jan 28 2009, skipping
2009-01-23 01:16:36.371
2009-01-23 01:16:36.371 Checking day @ offset 6, date: Don Jan 29 2009
2009-01-23 01:16:36.421 Data is already present for Don Jan 29 2009, skipping
2009-01-23 01:16:36.421
2009-01-23 01:16:36.421 Checking day @ offset 7, date: Fre Jan 30 2009
2009-01-23 01:16:36.471 Data is already present for Fre Jan 30 2009, skipping
2009-01-23 01:16:36.471
2009-01-23 01:16:36.471 Checking day @ offset 8, date: Sam Jan 31 2009
2009-01-23 01:16:36.521 Data is already present for Sam Jan 31 2009, skipping
2009-01-23 01:16:36.521
2009-01-23 01:16:36.521 Checking day @ offset 9, date: Son Feb 1 2009
2009-01-23 01:16:36.569 Data is already present for Son Feb 1 2009, skipping
2009-01-23 01:16:36.569
2009-01-23 01:16:36.569 Checking day @ offset 10, date: Mon Feb 2 2009
2009-01-23 01:16:36.617 Data is already present for Mon Feb 2 2009, skipping
2009-01-23 01:16:36.617
2009-01-23 01:16:36.617 Checking day @ offset 11, date: Die Feb 3 2009
2009-01-23 01:16:36.665 Data is already present for Die Feb 3 2009, skipping
2009-01-23 01:16:36.665
2009-01-23 01:16:36.665 Checking day @ offset 12, date: Mit Feb 4 2009
2009-01-23 01:16:36.711 Data is already present for Mit Feb 4 2009, skipping
2009-01-23 01:16:36.712
2009-01-23 01:16:36.712 Checking day @ offset 13, date: Don Feb 5 2009
2009-01-23 01:16:36.758 Data is already present for Don Feb 5 2009, skipping
2009-01-23 01:16:36.758
2009-01-23 01:16:36.758 Checking day @ offset 14, date: Fre Feb 6 2009
2009-01-23 01:16:36.804 Data is already present for Fre Feb 6 2009, skipping
2009-01-23 01:16:36.804
2009-01-23 01:16:36.804 Checking day @ offset 15, date: Sam Feb 7 2009
2009-01-23 01:16:36.849 Data refresh needed because only 39 out of 99 channels have at least one program listed for day @ offset 15 from 8PM - midnight.  Previous day had 51 channels with data in that time period.
2009-01-23 01:16:36.849 Refreshing data for Sam Feb 7 2009
2009-01-23 01:16:36.849 XMLTV config file is: /home/angelus/.mythtv/Schweiz.xmltv


```


HEEEEEEEEEELP

---

### Post by AngelusNocits on 2009-01-24
help!!

---

