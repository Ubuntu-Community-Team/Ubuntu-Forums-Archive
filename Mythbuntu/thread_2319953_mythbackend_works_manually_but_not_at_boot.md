---
title: "mythbackend works manually but not at boot"
date: 2016-04-08
forum: Mythbuntu
---

### Post by yonkiman on 2016-04-08
I just ran into this and wanted to post my solution in case anyone else has the same problem.

Just installed mythbuntu onto a new 16.04 install and got mythbackend to run happily when I launched it, but it wouldn't be running after I rebooted.

Looking at syslog and mythtv/mythbackend.log, I saw it was a permissions issue.  When I launched it, mythbackend used the /home/fred/.mythtv/config.xml (~/.mythtv/config.xml universally) file.
But at boot, mythbackend was using /home/mythtv/.mythtv/config.xml
So I deleted /home/mythtv/.mythtv/config.xml and linked the working xml file to the other location with:
```
sudo ln -s /home/fred/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
```

And it works...

---

