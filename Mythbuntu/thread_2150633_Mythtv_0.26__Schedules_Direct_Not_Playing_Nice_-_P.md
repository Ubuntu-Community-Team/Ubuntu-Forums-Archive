---
title: "Mythtv 0.26 / Schedules Direct Not Playing Nice - Program data applied to incorrect d"
date: 2013-06-01
forum: Mythbuntu
---

### Post by g8keepR on 2013-06-01
Hello,

I've tried nuking (truncate) the program table, and even starting from a fresh database and still no luck.  Basically, in the terminal it shows that the new program data is being retrieved, but it thinks it is always for  2013-05-23T20:00:00 to 2013-05-24T20:00:00 in the end

Here's the output :

2013-06-01 16:42:36.092827 I  Checking day @ offset 3, date: Tue Jun 4 2013 ** [ <== ok, this looks correct ]**
2013-06-01 16:42:36.108874 I  Data refresh needed because no data exists for day @ offset 3 from 8PM - midnight.   ** [ <== ok, this looks correct ]**
2013-06-01 16:42:36.108884 N  Refreshing data for Tue Jun 4 2013** [ <== ok, this looks correct ]**
2013-06-01 16:42:36.109509 I  Retrieving datadirect data.
2013-06-01 16:42:36.109529 I  Grabbing data for Sat Jun 1 2013 offset 3
2013-06-01 16:42:36.109546 I  From 2013-06-04T00:00:00Z to 2013-06-05T00:00:00Z (UTC)
2013-06-01 16:42:36.109555 I  DataDirect: Grabbing listing data
2013-06-01 16:42:36.109578 I  Downloading DataDirect feed
2013-06-01 16:42:55.731047 I  Downloaded 452109 bytes
2013-06-01 16:42:55.731066 I  Uncompressing DataDirect feed
2013-06-01 16:42:55.783904 I  Uncompressed to 4181541 bytes
2013-06-01 16:42:55.851237 I  DataDirect: Your subscription expires on Thu Dec 26 2013 7:08 AM
2013-06-01 16:43:08.039365 I  Grab complete.  Actual data from 2013-05-24T00:00:00Z to 2013-05-25T00:00:00Z (UTC)** [ <== what? ]**
2013-06-01 16:43:08.039868 I  Main temp tables populated.
2013-06-01 16:43:08.558008 I  Clearing data for source.
2013-06-01 16:43:08.558060 I  Clearing from 2013-05-23T20:00:00 to 2013-05-24T20:00:00 (localtime)
2013-06-01 16:43:11.552998 I  Data for source cleared.
2013-06-01 16:43:11.553006 I  Updating programs.
2013-06-01 16:43:14.733467 I  Program table update complete.

etc...

This worked fine until 5/24 5/25 now it's just stuck ...

I am running ubuntu 12.04 w/ mythtv 0.26 latest packages

Any ideas?

Thanks.

---

### Post by g8keepR on 2013-06-02
I should note that the schema version is 1307 and I have verified the tables match from the default install.

---

### Post by g8keepR on 2013-06-02
Ok, it looks like I have resolved my issue ... what I did was the following ( after searching more regarding mythfilldatabase ) :

truncated program table ( again )
cleaned up anything mythtv related in /tmp
cleaned out ~/.mythtv to copy in a fresh config.xml and linked /etc/mythtv/mysql.txt -> ~/.mythtv/mysql.txt
mythfilldatabase --nodblog --loglevel debug --verbose file,network --logpath /tmp --dd-grab-all

I had to do this twice for some reason, the first time it just grabbed my favorite 5/24 date it was holding on to.  The second time it grabbed a lot more data.  Now my program table went from ~8000 entries to ~143,000 and all of the data is there.

---

