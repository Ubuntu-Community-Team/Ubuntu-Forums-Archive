---
title: "Mysterious uploading"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by jettjunker on 2011-10-25
A few times a day I notice (on gkrellm) that I upload at my maximum speed for about a minute.  I have no idea what is doing it, and have been unsuccessful in figuring it out.

First, nethogs doesn't report the activity.
Second, I disabled sshd, and automatic update checks; and I've never used Ubuntu One (and made sure it was disabled).  I've even closed all my programs excepting Firefox to see if it would still happen, and it did (and, as soon as I noticed it I closed firefox, but the uploading continued so it's not to blame).

Any ideas?  The fact that nethogs doesn't report the activity freaks me out a bit... as if someone exploited something and has my box upload my personal files a little at a time without reporting it.

[I'm still using Ubuntu 10.10.... screw Unity]

---

### Post by wojox on 2011-10-25
Look in /etc/cron.daily/popularity-contest for that file.

---

### Post by jettjunker on 2011-10-25
Yeah, I have that file.  After looking into what it is, I checked /etc/popularity-contest.conf, but it had PARTICIPATE="no", so I don't think that's it.  [I did have USEHTTP="yes", but I assume that just means that if participation is enabled it will submit data that way.  I just changed it to "no", just in case.]

BTW, I don't think it has anything to do with cron, since my syslog doesn't show any cron activity at the time it happens.  Although, it just happened and I checked again, and there was one that ran this time (/usr/lib/php5/maxlifetime), but AFAICT it doesn't upload anything.

---

