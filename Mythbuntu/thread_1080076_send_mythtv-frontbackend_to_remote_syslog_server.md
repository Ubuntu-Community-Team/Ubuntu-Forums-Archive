---
title: "send mythtv-front/backend to remote syslog server"
date: 2009-02-25
forum: Mythbuntu
---

### Post by mike909 on 2009-02-25
How can I have mythtv-frontend & mythtv-backend log to a remote syslog server? I see that I can run them with the "--logfile" option and specify a local file (ie /var/log/mythtv/myth-frontend.log); but I would like to have this log to a remote server.
Actually, I would like it to log to a local facility, which would be included in my catch-all of "*.* @10.0.0.104" in my syslog.conf. Not sure if I'm using the correct terminology, I'm new to syslogging, but I have managed to set up a syslog-ng server and would like to use it to help me troubleshoot my myth issues.

---

