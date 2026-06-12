---
title: "Mythfilldatabase doesn't work in cron, works manually"
date: 2012-10-29
forum: Mythbuntu
---

### Post by drumz on 2012-10-29
I have a regular Kubuntu box that I use as a server with MythTV installed.  It has worked great for years.  I estimate that about 2-4 weeks ago it apparently stopped functioning correctly, but it works fine if I execute it manually from the command line.

I've noticed the following differences in output in the log file

Notice the error ('E') line for being unable to read the mysql.txt file.  This error only appears when run as a cron job.  

```
2012-10-29 04:00:01.439998 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
2012-10-29 04:00:01.440013 C  Qt version: compile: 4.8.1, runtime: 4.8.3
2012-10-29 04:00:01.440015 N  Enabled verbose msgs:  general
2012-10-29 04:00:01.440030 N  Setting Log Level to LOG_INFO
2012-10-29 04:00:01.440063 I  Added logging to the console
2012-10-29 04:00:01.440068 I  Added database logging to table logging
2012-10-29 04:00:01.440127 N  Setting up SIGHUP handler
2012-10-29 04:00:01.440248 N  Using runtime prefix = /usr
2012-10-29 04:00:01.440324 N  Using configuration directory = /root/.mythtv
2012-10-29 04:00:01.440449 I  Assumed character encoding: en_US.UTF-8
2012-10-29 04:00:01.440685 E  Unable to read configuration file mysql.txt
2012-10-29 04:00:01.440792 N  Empty LocalHostName.
2012-10-29 04:00:01.440796 I  Using localhost value of <hostname_removed>
2012-10-29 04:00:01.440876 I  Testing network connectivity to '192.168.1.12'
```

```
ls -lh /etc/mythtv/
total 12K
-rw-rw---- 1 mythtv mythtv  655 Oct 29 04:00 config.xml
-rw-rw---- 1 mythtv mythtv   79 Oct  6 11:01 mysql.txt
-rw-r--r-- 1 root   root   1.1K Apr 23  2010 session-settings
```

I see the following 'content-type' information message *only* when mythfilldatabase is executed as a cron job:

```
2012-10-29 04:00:02.607644 I  From Tue Oct 30 04:00:00 2012 to Wed Oct 31 04:00:00 2012 (UTC)
2012-10-29 04:00:02.607660 I  DataDirect: Grabbing listing data
2012-10-29 04:00:02.607687 I  Downloading DataDirect feed
content-type missing in HTTP POST, defaulting to application/x-www-form-urlencoded. Use QNetworkRequest::setHeader() to fix this problem.
content-type missing in HTTP POST, defaulting to application/x-www-form-urlencoded. Use QNetworkRequest::setHeader() to fix this problem.
2012-10-29 04:01:07.363820 I  Downloaded 786607 bytes
2012-10-29 04:01:07.363826 I  Uncompressing DataDirect feed
2012-10-29 04:01:07.389929 I  Uncompressed to 6997598 bytes
```

The following error (from execution as a cron job) appears in both (executed as a cron or manually):

```
2012-10-29 04:01:33.041308 N  Refreshing data for Sat Nov 10 2012
2012-10-29 04:01:33.041867 I  Retrieving datadirect data.
2012-10-29 04:01:33.041891 I  Grabbing data for Mon Oct 29 2012 offset 12
2012-10-29 04:01:33.041906 I  From Sat Nov 10 04:00:00 2012 to Sun Nov 11 04:00:00 2012 (UTC)
2012-10-29 04:01:33.041913 I  DataDirect: Grabbing listing data
2012-10-29 04:01:33.041930 I  Downloading DataDirect feed
content-type missing in HTTP POST, defaulting to application/x-www-form-urlencoded. Use QNetworkRequest::setHeader() to fix this problem.
2012-10-29 04:01:48.648614 E  DataDirect: Failed to get data: Download error
2012-10-29 04:01:48.648622 E  Encountered error in grabbing data.
2012-10-29 04:01:48.648691 I  Checking day @ offset 13, date: Sun Nov 11 2012
2012-10-29 04:01:48.776898 I  Data refresh needed because only 0 out of 719 channels have at least one program listed for day @ offset 13 from 8PM - midnight.  Previous day had 670 channels with data in that time period.
```

Here it is when run manually from the command line:
```

2012-10-29 11:04:48.346384 N  Refreshing data for Sat Nov 10 2012
2012-10-29 11:04:48.346827 I  Retrieving datadirect data.
2012-10-29 11:04:48.346842 I  Grabbing data for Mon Oct 29 2012 offset 12
2012-10-29 11:04:48.346855 I  From Sat Nov 10 04:00:00 2012 to Sun Nov 11 04:00:00 2012 (UTC)
2012-10-29 11:04:48.346862 I  DataDirect: Grabbing listing data
2012-10-29 11:04:48.346880 I  Downloading DataDirect feed
2012-10-29 11:05:12.957426 E  DataDirect: Failed to get data: Download error
2012-10-29 11:05:12.957433 E  Encountered error in grabbing data.
2012-10-29 11:05:12.957500 I  Checking day @ offset 13, date: Sun Nov 11 2012
2012-10-29 11:05:13.086475 I  Data refresh needed because only 0 out of 719 channels have at least one program listed for day @ offset 13 from 8PM - midnight.  Previous day had 670 channels with data in that
 time period.
```

Based on the above I think the problem is probably tied to the mysql.txt file error - but as the cron entry is in root's cron it should have read access to it.

Anyone else seeing this issue?

Thanks!

---

### Post by nickrout on 2012-10-29
Is there a /root/.mythtv/mysql.txt and is it correct?

Oh and whay are you using cron? mythbackend runs it automatically as the right user (mythtv).

---

### Post by drumz on 2012-10-29
There wasn't a /root/.mythtv/mysql.txt file.  I created it now and will see if that solves the problem with the nightly executions.

I'm calling it from a cronjob because that's the way it was supposed to be setup a really long time ago (again, this was setup a very long time ago and altough I've updated over the years if it wasn't broke why fix it ;-) ).

---

### Post by drumz on 2012-11-03
Adding the mysql.txt file to /root/.mythtv didn't resolve the issue when it was run as a cronjob.

So I switched to having the mythbackend run it automatically - and it's still not working even though the backend did run the script.  There are no error 'E' messages in the log file, and it did execute but after 2 days I'm now down to 12 days of scheduled data instead of the normal 14.

I've attached the complete log output from last nights execution.

In MythWeb here's what's shown on the backend status page:

```
Last mythfilldatabase run started on 2012-11-03 02:22:29 and ended on 2012-11-03 02:23:32. mythfilldatabase ran, but did not insert any new data into the Guide for 1 of 1 sources. This can indicate a potential grabber failure.
There's guide data until 2012-11-15 07:00 (12 days).
DataDirect Status: Your subscription expires on Wed Jun 19 (2013) 10:53 PM 
```

---

### Post by drumz on 2012-11-09
For whatever reason, now it's working as a cron job again.  Nothing has changed, haven't rebooted the system or anything.  The only difference is I'm running now during the late afternoon instead of the wee hours of the morning.

---

### Post by nickrout on 2012-11-09
> **drumz said:**
> For whatever reason, now it's working as a cron job again.  Nothing has changed, haven't rebooted the system or anything.  The only difference is I'm running now during the late afternoon instead of the wee hours of the morning.Maybe there is data now and there wasn't previously.

---

### Post by drumz on 2012-11-10
One possible explanation is they've started doing some type of maintenance on the server mythfilldatabase is pulling the data from.  Both my original cron job and the backend were executing mythfilldatabase at about the same time of day and my current cron has it set to run late in the afternoon now.

---

### Post by nickrout on 2012-11-10
> **drumz said:**
> One possible explanation is they've started doing some type of maintenance on the server mythfilldatabase is pulling the data from.  Both my original cron job and the backend were executing mythfilldatabase at about the same time of day and my current cron has it set to run late in the afternoon now.My provider has a limit to the number of times a day any one IP address can download the xmltv file. So if you do a bit of testing you end getting failures...

---

