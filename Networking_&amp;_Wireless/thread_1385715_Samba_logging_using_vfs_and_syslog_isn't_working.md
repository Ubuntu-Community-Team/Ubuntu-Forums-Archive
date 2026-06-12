---
title: "Samba logging using vfs and syslog isn't working"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by Huufarted on 2010-01-19
I'm looking into setting up logging for Samba that logs every file downloaded, uploaded, renamed, deleted, etc, etc.  It's currently working, but I'm trying to get it to output to /var/log/samba/audit.log and it's still outputtin  Here are my current settings:

/etc/syslog.conf:
```
local7.*                        /var/log/samba/audit.log

```
That line is currently at the beginning of the file.  I've also tried the same line at the end of the file with the same results.  The syslog excerpt above is the only change from the default syslog.conf

```
art@atom1:/var/log$ cat /etc/samba/smb.conf
[global]
        netbios name = ATOM1
        workgroup = WORKGROUP
        server string = Samba Server
        interfaces = eth1 lo eth0
        #bind interfaces only = yes
        map to guest = bad user
        guest account = nobody
        #security = share
        security = user
        hide files = /.*/
        invalid users = root

        log level = 0 vfs:[012]
        log file = /var/log/samba/samba.log
        max log size = 50000
        debug timestamp = yes
        syslog = 0

[music]
        guest ok = yes
        read only = yes
        path = /home/storage/Media/Music
        browseable = yes
        comment = music
        vfs objects = full_audit
        full_audit:prefix = %u|%I|%m|%S
        full_audit:success = mkdir rename unlink rmdir pwrite open
        full_audit:failure = all
        full_audit:facility = LOCAL7
        full_audit:priority = NOTICE

```

So can someone tell me why my logs aren't going to the audit.log I'm trying for?  They're instead going straight to /var/log/syslog

---

### Post by Huufarted on 2010-01-21
Is there a way to just tell samba/vfs not to use syslog and use its own logging instead?

---

### Post by mikedep333 on 2010-04-10
BUMP.

I would like to know this too.

I don't know whether I should use audit, extd_audit, or full_audit.

My shares are read-only to other people, so I only need access logging, preferably of both accessing file and browsing directories.

I also need per machine logging, i have %m in my "log file" option. This is Ubuntu's default and I need it because we use anonymous logins. Of course, all it is logging per-machine now is errors, not access.

---

### Post by mikedep333 on 2010-04-10
Hey,

I followed the instructions here and it worked:
[http://a32.me/2009/10/samba-audit-trail/](http://a32.me/2009/10/samba-audit-trail/)

Maybe your issue is that "local7" is not the same as "LOCAL7".

-Mike

---

