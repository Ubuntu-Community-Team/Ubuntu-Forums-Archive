---
title: "log rotation in MythTV"
date: 2011-03-13
forum: Mythbuntu
---

### Post by gunsmoke on 2011-03-13
Hi, I have installed Ubuntu 10.10 + Mythbuntu Control Center with 0.23.1 +fixes.

I was following the instruction on this page [http://www.mythtv.org/wiki/Log_File_Rotation](http://www.mythtv.org/wiki/Log_File_Rotation) and noticed that there was alredy two files in the /etc/logrotate.d:

mythtv-backend
mythtv-frontend

Content in frontend file:
> /var/log/mythtv/mythfrontend.log {
        daily
	size=10M
        rotate 7
        notifempty
        copytruncate
	missingok
}

/var/log/mythtv/mythwelcome.log {
        daily
	size=10M
        rotate 7
        notifempty
        copytruncate
        missingok
}

It is simular to the example in the wiki:
> /var/log/mythtv/mythfrontend.log {
        copytruncate
        daily
        size 10M
        missingok
        rotate 7
        compress
        notifempty
}


But without compressing of the file...

Is there log rotation as default now, and that wiki page are refering to and older mythtv version?

Still learing here, Regards from a noob):P

---

### Post by newlinux on 2011-03-13
The wiki is for generic mythtv, but the packaging for mythtv in ubuntu includes log rotation by default. So I wouldn't say it is that the wiki is old, it just isn't specific to ubuntu.

---

### Post by gunsmoke on 2011-03-13
> **newlinux said:**
> The wiki is for generic mythtv, but the packaging for mythtv in ubuntu includes log rotation by default. So I wouldn't say it is that the wiki is old, it just isn't specific to ubuntu.

Thanks for the replay newlinux:)

I ran the command:

```
logrotate -f -s /var/lib/logrotate/status /etc/logrotate.d/mythtv-backend
```

and this produced a file with the mythbackend.log.1 exstension, and a new blank mythbackend.log

However, I have been using the setup now for a couple of days. should it not run once a day? ergo there should be up to 7 log files, due to rotate 7 command?

---

### Post by newlinux on 2011-03-13
based on the size=10M parameter you have, I think the daily cronjob won't rotate the file until the filesize is 10M or greater. The rotate 7 simply says to keep up to 7 files (could be 7 weekly, monthly or 7 files greater than 10M, etc.). It's the daily command that should make it rotate daily, but I believe that is being overriden by the size=10M parameter.

---

### Post by gunsmoke on 2011-03-13
> **newlinux said:**
> based on the size=10M parameter you have, I think the daily cronjob won't rotate the file until the filesize is 10M or greater. The rotate 7 simply says to keep up to 7 files (could be 7 weekly, monthly or 7 files greater than 10M, etc.). It's the daily command that should make it rotate daily, but I believe that is being overriden by the size=10M parameter.

Thanks! I will check it from time to time, just to get the feel of it :)

---

