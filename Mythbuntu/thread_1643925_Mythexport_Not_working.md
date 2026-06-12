---
title: "Mythexport Not working"
date: 2010-12-12
forum: Mythbuntu
---

### Post by TomGar on 2010-12-12
I've installed this via the Mythbuntu control centre and it sets up nicely and I can access it via the //localhost/mythexport interface. But when I kick a job off it fails and it seems to be a permissions problem but I can't work out what the problem is.

Here's the log output


December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: ERROR: Directory  is not writeable.
 at line 283 in /usr/bin/mythexport-daemon
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Creating mysql dump
sh: cannot create /mythimport.sql: Permission denied
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: ERROR: mysqldump -hlocalhost -umythtv -pmythtv -P3306 mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1001' and starttime='2009-12-29 14:35:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 297 in /usr/bin/mythexport-daemon
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Copying /var/lib/mythtv/recordings/1001_20091229143500.mpg to /1001_20091229143500.mpg
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Unable to copy /var/lib/mythtv/recordings/1001_20091229143500.mpg to /1001_20091229143500.mpg at line 319 in /usr/bin/mythexport-daemon


If anyone can point me in the right direction that would be much appreciated.

---

### Post by itlarson on 2010-12-14
Have you tried restarting the mythexport daemon?  Mine won't start ffmpeg until I do this.  The command is "/etc/init.d/mythexport restart" .

---

### Post by ZedThou on 2010-12-15
> **TomGar said:**
> I've installed this via the Mythbuntu control centre and it sets up nicely and I can access it via the //localhost/mythexport interface. But when I kick a job off it fails and it seems to be a permissions problem but I can't work out what the problem is.

Here's the log output


December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: ERROR: Directory  is not writeable.
 at line 283 in /usr/bin/mythexport-daemon
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Creating mysql dump
sh: cannot create /mythimport.sql: Permission denied
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: ERROR: mysqldump -hlocalhost -umythtv -pmythtv -P3306 mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1001' and starttime='2009-12-29 14:35:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 297 in /usr/bin/mythexport-daemon
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Copying /var/lib/mythtv/recordings/1001_20091229143500.mpg to /1001_20091229143500.mpg
December 12 19:45:12 Wimsy /usr/bin/mythexport-daemon[13545]: Unable to copy /var/lib/mythtv/recordings/1001_20091229143500.mpg to /1001_20091229143500.mpg at line 319 in /usr/bin/mythexport-daemon


If anyone can point me in the right direction that would be much appreciated.

That last line is the best clue. You need to put in a directory location in the "Choose a location" field, to which the recording is going to be copied (it seems that's all the builtin "full-featured" option does with the video).

---

### Post by TomGar on 2010-12-19
Thanks for the feedback, I didn't realize you have to specify a directory every time you want to run a job. Anyway all working now (I think!)

---

