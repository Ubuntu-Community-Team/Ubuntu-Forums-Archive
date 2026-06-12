---
title: "Putty ssh access denied"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by shouse on 2011-02-09
I'm trying to access a Ubuntu desktop remotely via the WAN IP using Putty and am getting 'access denied' errors.  The user name and password work when I access with the LAN IP so I'm pretty sure the username and password aren't the real issue.  

I believe the I have the correct things set to yes in the config files.

---

### Post by Zyprexa on 2011-02-09
I had this problem too. Since my password contained non english characters, and i had not set the putty session to utf-8 character set, my password was rejected when trying to log in by ssh. Can it be that's what's wrong in your case too?

---

### Post by papibe on 2011-02-09
Try looking the log to see if you can find any clues:
```
$ tail /var/log/auth.log
```
Regards.

---

