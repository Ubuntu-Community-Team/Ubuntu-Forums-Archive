---
title: "Did Location of MythTV Logs Change?"
date: 2017-05-06
forum: Multimedia Software
---

### Post by jamoody on 2017-05-06
Since upgrading to 0.28.1-21 none of the MythTV logs are being written to /var/log/mythtv/.  Did the location change?  I searched for mythfrontend.log (for example) and only found the copy on /var/log/mythtv/ which was last written to up to the time of the update and not since.  Same for mythbackend.log, mythcommflag.log, etc

---

### Post by jamoody on 2017-05-06
The problem turned out to be /etc/rsyslog.d/40-mythtv.conf no longer existed causing the logs to be written to /var/log/syslog.  Restored 40-mythtv.conf from a backup and after reboot logs are now being written to /var/log/mythtv/ again.

---

