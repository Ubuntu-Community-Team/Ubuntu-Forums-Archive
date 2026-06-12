---
title: "mythtv unable to record"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by imcecil on 2007-10-06
i managed to setup mythtv and every things working well except I'm unable to record.  selecting one of the record methods (record only this show, record one showing of this title) then selecting save these settings does not seem to save anything.

I've found a couple of posts that appear to relate to this
one relating to a bug that [save these settings] wouldn't save anything, although this was fixed along time ago
[http://www.mail-archive.com/mythtv-commits@mythtv.org/msg07513.html](http://www.mail-archive.com/mythtv-commits@mythtv.org/msg07513.html)
and
[http://ubuntuforums.org/showthread.php?t=338651](http://ubuntuforums.org/showthread.php?t=338651)
which seems to be more about the user rights

I had a look at the log output from
 tail /var/log/mythtv/mythbackend.log
and the only errors are
2007-10-06 17:16:18.031 MythSocket(b2106230:-1): writeStringList: Error, called with unconnected socket.
and nothing user related

thanks Cecil

---

