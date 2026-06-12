---
title: "Arrgh! Backend not starting now..help!"
date: 2008-06-01
forum: Mythbuntu
---

### Post by strokeboy on 2008-06-01
Hi
I am running Mythbuntu 8.04 with a HDhomerun on an AMD64 and so far so good (new install) but then I think I was trying to overcome the problem of the HDHR not being ready by the time the backend tries to start. see [this thread.]("http://ubuntuforums.org/showthread.php?t=683389") And I tried to deselect roaming on both wireless and wired network connections but then I noticed that the backend wasn't running.  So, I reset everything back and still no backend. :( Please, someone tell me where to look to obtain a log or something to help isolate the issue.  I normally would re-install everything but I was hoping to start trying to fix it if it is an easy fix.  Thanks for any help.:KS

---

### Post by zoiks on 2008-06-02
Uhm, I don't know the details about why your backend isn't starting, etc., but the backend log should appear at /var/log/mythtv/mythbackend.log.

Note: When I installed 8.04, mythbackend was *not* writing to this log. The mythbackend.log file *was* there, but remained empty. I saw that the ownership of the file was set to root.mythtv (user = root, group = mythtv), but it did not have group write permission. Therefore, a simple sudo chmod g+w /var/log/mythtv/mythbackend.log did the trick (though I suppose changing the owner might have been better).

---

### Post by strokeboy on 2008-06-02
Thanks for the info.  I checked the log and at first glance it looked like gibberish but then I started reading it and I traced the problem back in time...to when the movers came...and unplugged the HDHomerun.:lolflag:  Thanks much for where to start troubleshooting!  jd

---

