---
title: "Mythfilldatabase and Cron not working"
date: 2014-03-21
forum: Mythbuntu
---

### Post by diesel48 on 2014-03-21
Lately the automatic mythfilldatabase has not been working. I have no idea why it worked great until maybe a month ago. If I log into my server and run mythfilldatabase --dd-grab-all it will pull in the latest guide data. Since that worked I wanted to create a cron job to do it. so I did the following.

crontab -e
added the following to the crontab
0 2 * * * /usr/bin/mythfilldatabase --dd-grab-all


Well something is not working as this command is not pulling in data. Does anyone have suggestions on how to get this to work so I do not need to do it manually?
Thanks!

---

### Post by blm-ubunet on 2014-03-21
Mythfilldatabase is meant to be run automatically by the BE. So it runs as the BE user "mythtv".
When you run it from terminal you are (probably) running it as FE or current logged in user.

Any clues in /var/log/mythtv/"some-logfile" ?

You can run from terminal as the BE user (to debug):
```
sudo -u mythtv mythfilldatabase
```
this cmd might except --loglevel=debug

This is interesting..
[https://forum.mythtv.org/viewtopic.php?f=36&t=34](https://forum.mythtv.org/viewtopic.php?f=36&t=34)

---

### Post by diesel48 on 2014-03-27
Looked at your link but that file does not exist on my backend server. Not sure why it all of sudden just stopped working but works fine when I run it manually. Of course cron does not work though.

---

### Post by martin41 on 2014-03-28
I had a similar problem after upgrading to 0.27.  I am not sure if this is when your problem occurred but I almost went the cron way too until someone mentioned setting up the mythfilldatabase in the backend to run from a specified time instead of when Schedules Direct says to run it.  I've linked these posts below for your reference.  Another option is run cron in /etc/crond.d/mythbuntu-bare if you are running mythbuntu-bare.  This is the file I run all my cron jobs from and I have had no issues. 

[http://ubuntuforums.org/showthread.php?t=2208646&](http://ubuntuforums.org/showthread.php?t=2208646&)

---

### Post by aelfric55 on 2014-04-03
I've never really thought this issue had to do with Mythtv 0.27 or any other specific Mythtv version, since it was also being reported by users of older Mythtv versions whose systems had been stable and unchanged for a long time but then began experiencing mythfilldatabase issues starting about a couple of months ago. dd datagrab errors in the mythfilldatabase log seemed to point more toward a problem on the Schedules Direct end.  It appears that the Schedules Direct folk may believe so too: on their site from March 26: 
**> Problems downloading data**> 
 We are aware of problems members have been having downloading data  recently, and have reported the problem to our data source. 
  At this point I have nothing to report, other that our monitoring system has detected the problem (and auto-reported it to Tribune Media Services), but we are following up manually. 

I only mention this because this week, my cron mythfilldatabase job (Mythtv 0.25.3) began working again on its own, for the first time since the end of Feb. Wednesday night's (2 AM) cron grab took well over an hour, but completed; last night's grab also completed, but in a more normal 20 minutes.

Anyone else suddenly finding their cron mythfilldatabase jobs are completing successfully? Perhaps they've located the problem.

---

### Post by diesel48 on 2014-04-03
Did you setup a cron job or are you running it with Mythtv built in program? If you are running it via cron what does your cron script look like? It always works when I run it manually, just never automatically.

---

### Post by aelfric55 on 2014-04-03
I run it from a cron job. Actually just a single crontab line:  ```
4 2 * * * /usr/bin/mythfilldatabase  --dd-grab-all --logpath /var/log
```

When the cron job stopped completing a couple of months ago, and the usual posted solutions (clearing out the /tmp files; restarting, etc.) had no discernible effect, I got into the habit of running mythfilldatabase manually from a terminal every three or four days. Which worked.

But I became so annoyed at remembering to run mythfilldatabase manually, that I wrote an 'expect' script as a cron job for another machine on my network --the second machine would spawn an ssh thread, log into my master backend machine, and run mythfilldatabase. The script worked, but mythfilldatabase would still fail on this type of job, with the same "dd datagrab failed" errors. Running mythfilldatabase manually still worked. 

So I was surprised today when I noticed, as I was about to manually run mythfilldatabase again, that the cron and cron/ssh runs of mythfilldatabase had both been completing successfully for the last couple of days without any further steps having been taken on my part.

---

### Post by aelfric55 on 2014-04-08
Seems my cautious optimism about Schedules Direct was premature. After four days of no issues, the data stopped downloading again over the weekend. But this time around, the manual running of mythfilldatabase from a terminal is also producing download failed errors.

Anyone having success with their Schedules Direct loads?

---

