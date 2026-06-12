---
title: "mythexport errors in log"
date: 2012-01-17
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-17
Just installed mythexport.  When the daemon is started, and when I try to run a job "on the go" there are errors in the log that seem to indicate it is trying to write to the root directory

e.g. cannot create /mythimport.sql

(and why is it trying to do a mysql dump?)

from the log...
> January 17 17:41:55 mythbuntu4 /usr/bin/mythexport-daemon[5542]: Starting Processing:  1326786115
January 17 17:42:55 mythbuntu4 /usr/bin/mythexport-daemon[5542]: ERROR: Directory  is not writeable.
 at line 283 in /usr/bin/mythexport-daemon
January 17 17:42:55 mythbuntu4 /usr/bin/mythexport-daemon[5542]: Creating mysql dump
sh: cannot create /mythimport.sql: Permission denied
January 17 17:42:55 mythbuntu4 /usr/bin/mythexport-daemon[5542]: ERROR: mysqldump -hlocalhost -umythtv -psdf43fssd -P3306 mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1071' and starttime='2012-01-15 20:30:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 297 in /usr/bin/mythexport-daemon
January 17 17:42:56 mythbuntu4 /usr/bin/mythexport-daemon[5542]: Copying /var/lib/mythtv/recordings/1071_20120115203000.mpg to /1071_20120115203000.mpg
January 17 17:42:56 mythbuntu4 /usr/bin/mythexport-daemon[5542]: Unable to copy /var/lib/mythtv/recordings/1071_20120115203000.mpg to /1071_20120115203000.mpg at line 319 in /usr/bin/mythexport-daemon

---

### Post by ZedThou on 2012-01-21
Do you have an entry in the "Choose a Location" text field? I just put /tmp or similar there since I don't want the metadata that it writes.

edit - you should also give a default location to which it will copy the recording, this is done under the "System Setup" option.

---

### Post by ubnewbie2 on 2012-01-21
> **ZedThou said:**
> Do you have an entry in the "Choose a Location" text field? I just put /tmp or similar there since I don't want the metadata that it writes.

edit - you should also give a default location to which it will copy the recording, this is done under the "System Setup" option.

I have /var/lib/mythtv/videos as the default location in System Setup, but I missed that little location field at the the top of the OTG screen.

Trying it now... thanks

---

