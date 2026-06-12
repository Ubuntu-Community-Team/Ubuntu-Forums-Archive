---
title: "Mythlink.pl as a cron job"
date: 2011-01-09
forum: Mythbuntu
---

### Post by The Odometer on 2011-01-09
I know this one should be straight forward...but I haven't been able to figure it out for the life of me...

I'm trying to set up mythlink.pl to run as a cron job. It never seems to run and I get errors in my syslog when I check it. 

Here's what I've done.

```
chris@mythbox:/crontab -e


```

When I get into crontab, here's my line for mythlink:
```
@hourly /usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --dest /recordings --format '%T/%Y%m%d-%H%i-%eH%ei-%SS'

```

When I run syslog, I get:

Jan  9 09:00:01 mythbox CRON[7364]: (chris) CMD (/usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --dest /recordings --format ')
Jan  9 09:00:01 mythbox CRON[7362]: (CRON) error (grandchild #7364 failed with exit status 2)
Jan  9 09:00:01 mythbox CRON[7362]: (CRON) error (grandchild #7365 terminated by signal 13)


I'm lost at what I'm doing wrong. Thanks in advance for anyone's help.

---

### Post by Chunk of Earth on 2011-01-09
You need to escape out all your percent signs:
```
@hourly /usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --dest /recordings --format '\%T/\%Y\%m\%d-\%H\%i-\%eH\%ei-\%SS'
```

---

### Post by The Odometer on 2011-01-09
That worked! Thanks!

---

