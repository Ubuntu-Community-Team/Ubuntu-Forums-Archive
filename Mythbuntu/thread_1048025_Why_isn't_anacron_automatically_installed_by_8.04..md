---
title: "Why isn't anacron automatically installed by 8.04.1?"
date: 2009-01-23
forum: Mythbuntu
---

### Post by faginbagin on 2009-01-23
I just installed mythbuntu 8.04.1 and noticed that anacron wasn't automatically installed. Without it, I assume the cron,daily, weekly, etc. jobs won't run. Is there some reason anacron wasn't installed?

---

### Post by tgm4883 on 2009-01-23
Cron jobs do in fact run.  See that cron is installed

---

### Post by faginbagin on 2009-01-23
Umm, I guess I wasn't specific enough. I'm wondering about the anacron jobs found in the directories:
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly
Yes, cron is installed and is working, but I don't think it executes the scripts found in those directories. That should be anacron's job. I want to be sure /etc/cron.weekly/mythtv-database, which does a weekly backup of mythconverg, is being executed. Same for /etc/cron.daily/logrotate. So it's got me wondering if anacron was deliberately not installed by the mythbuntu desktop CD, or if it's an oversight. If it's an oversight, I'll install it, but I wonder if other users of 8.04.1 are more vulnerable to corrupt databases and to log files filling up their disks.

---

### Post by utar on 2009-01-23
I noticed this same thing on both 8.10 and earlier versions.  I personally installed anacron as some of the mythtv log files can be massive and as I don't leave my box on 24 hours a day these weren't being rotated.

I've wondered myself why anacron isn't installed by default, although this may be because it isn't on Ubuntu itself, rather then a change made by the Mythubuntu team.

---

### Post by newlinux on 2009-01-23
I think cron.daily, weekly, monthly should run without anacron. The /etc/crontab should test for anacron, and if it is not there run the crons. (not at my machine right now, but I think this is how it is setup on my machines). I don't remember explicitely install anacron but it is installed on all of my machines which are all hardy. maybe it is a dependency of something else I always install...

Are you guys both talking it is missing in ubuntu or mythbuntu?

---

### Post by utar on 2009-01-23
> **newlinux said:**
> I think cron.daily, weekly, monthly should run without anacron. The /etc/crontab should test for anacron, and if it is not there run the crons. (not at my machine right now, but I think this is how it is setup on my machines). I don't remember explicitely install anacron but it is installed on all of my machines which are all hardy. maybe it is a dependency of something else I always install...

Are you guys both talking it is missing in ubuntu or mythbuntu?

Talking about Mythbuntu.

The crons will run fine without anacron, however by default cron jobs are run in the early hours so unless your box is on 24 hours a day cron jobs never get run.

---

### Post by newlinux on 2009-01-23
> **utar said:**
> Talking about Mythbuntu.

The crons will run fine without anacron, however by default cron jobs are run in the early hours so unless your box is on 24 hours a day cron jobs never get run.


Ahh, I can't speak for mythbuntu. I always install myth ontop of ubuntu. Seems strange that anacron wouldn't be included, just for the reason you mention...

---

