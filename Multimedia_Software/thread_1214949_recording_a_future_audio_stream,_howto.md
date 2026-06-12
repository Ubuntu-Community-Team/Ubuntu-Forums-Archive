---
title: "recording a future audio stream, howto?"
date: 2009-07-16
forum: Multimedia Software
---

### Post by Eduardo Mercovich on 2009-07-16
Hi all.

There was a previous post in the archive ([http://ubuntuforums.org/showthread.php?t=305858](http://ubuntuforums.org/showthread.php?t=305858)) about saving a stream to hear it later. 

Finally, a solution was found using cron, a player, arecord, and others. 
I have found since then another solution, much more simpler, so this post is only to complete that other.

In your crontab (contab -e) add just 1 command:

mimms -t 1 mms://your.stream.url /home/youruser/yourdesiredfilename-$(date +%Y%m%d).wma

(or whatever extension it has).

That's all. 

Regards...

---

