---
title: "mythweb error"
date: 2010-05-31
forum: Mythbuntu
---

### Post by hylsan on 2010-05-31
Im trying to get a second frontend to work but while I was doing this I must have managed to screw something up with MythWeb because now I get this when clicking listnings and the other links.

```
User Notice at /usr/share/mythtv/mythweb/classes/MythBackend.php, line 102:
Unexpected response to MYTH_PROTO_VERSION '50':

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:148)
``` 

Does anyone know what could be wrong???

Thanks in advance!

---

### Post by kja999 on 2010-06-01
My guess would be the backend version is different to the mythweb version .. and so the expected protocol is different ?!?

---

### Post by michaeldoc on 2010-06-01
I have the same problem. I can't find what version of Mythweb I am using. Where is this data? I see that BrowserDBSchemaVer is 1002. Is this relevant? My time in Mythweb seems to be 15 hrs behind the time on my Mythtv. I am in Victoria, Australia and the Mythtv settings are correct, as is my system time on Ubuntu.  I am not very Linux savvy. My savvy friend set up the Mythtv and mythweb. He briefly looked at it and couldn't work out why the time is incorrect. It seems this occurred with a recent upgrade. I am running Mythtv 0.22 Any ideas?

---

### Post by michaeldoc on 2010-06-01
oops sorry. Seems I have posted in the wrong thread.. My error is a time offset. I will repost appropriately.

---

### Post by michaeldoc on 2010-06-01
OK now I am really confused. This seems to be the right thread, according to Google, but the documented post seems to have disappeared. Here's how I got here.. The google link says..
mythweb error - Ubuntu Forums
2 posts - 2 authors - Last post: 1 hour ago
mythweb error Mythbuntu. ... Does anyone know what could be wrong??? Thanks in advance! .... All times are GMT -4. The time now is 05:12 AM. ...
ubuntuforums.org/showthread.php?goto=newpost&t=1498225

So any help with my incorrect time would be appreciated.

Thanks in advance

---

### Post by lofgren on 2010-07-26
For those searching for a fix - like me - I found that you need to run mythtv-setup and change your local backend from 127.0.0.1 to the actual IP of the box.

as per this post:
[http://www.gossamer-threads.com/lists/mythtv/users/424228](http://www.gossamer-threads.com/lists/mythtv/users/424228)

The localhost thing seems to be a default during the install/upgrade. In my case from 0.21 to 0.22 during a Ubuntu 9.04 to 9.10 upgrade.

---

### Post by hylsan on 2010-07-26
I've run the setup but everywhere theres the actual IP, no localhost or 127.1.1.1 (or whatever).

Does it matter if the master backend and local backend have the same IP?
(only got one backend so it should be the same)

---

