---
title: "help me fix this error in backend log"
date: 2010-04-12
forum: Mythbuntu
---

### Post by xinix on 2010-04-12
I was looking at the /var/log/mythtv/mythbackend.log and it is filled with this error:```
2010-04-12 11:14:37.333 UPnPautoconf() - No UPnP backends found
2010-04-12 11:14:37.334 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-04-12 11:14:37.336 Deleting UPnP client...
2010-04-12 11:14:38.042 Failed to init MythContext, exiting.
2010-04-12 11:14:38.162 mythbackend version: branches/release-0-23-fixes [24009] www.mythtv.org
2010-04-12 11:14:38.163 Using runtime prefix = /usr
2010-04-12 11:14:38.164 Using configuration directory = /.mythtv
2010-04-12 11:14:38.164 Unable to read configuration file mysql.txt
2010-04-12 11:14:38.165 Empty LocalHostName.
2010-04-12 11:14:38.165 Using localhost value of vampiro
2010-04-12 11:14:38.173 New DB connection, total: 1
2010-04-12 11:14:38.176 Unable to connect to database!
2010-04-12 11:14:38.177 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```

on the surface in the frontend everything seems to be working.  It records and plays back just fine. I'd like to fix this since the log is getting filled up by this error.

Any suggestions?

---

### Post by ian dobson on 2010-04-12
Hi,

It looks as if your backend doesn't think it's a master backend. Check your configuration for the IP address of the backend and that of the master backend. If you only have one backend they both should be the same.

Have a look here:- [http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade](http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade)

or maybe here:- [https://bugs.launchpad.net/mythbuntu/+bug/546616](https://bugs.launchpad.net/mythbuntu/+bug/546616)
Regards
Ian Dobson

---

### Post by xinix on 2010-04-12
Ian,
thanks for the help.  I applied the modified "/etc/init/mythtv-backend.conf" file and the error went away.

---

### Post by jMon54 on 2010-04-22
I would like to ask how exactly you applied the fix.  I am having this issue and I inserted the code to the best of my understanding in two different places but still have the issue.  Thanks in advance.

> **xinix said:**
> Ian,
thanks for the help.  I applied the modified "/etc/init/mythtv-backend.conf" file and the error went away.

---

### Post by xinix on 2010-04-22
I replaced the contents of /etc/init/mythtv-backend.conf witht he ones provided in this post: [https://bugs.launchpad.net/mythbuntu/+bug/546616/comments/7](https://bugs.launchpad.net/mythbuntu/+bug/546616/comments/7)

The link to the attachment is not clear so here's the content:
```
# MythTV Backend service

description     "MythTV Backend"
author          "Giovanni Aneloni <yota@opensystems.ath.cx>"

start on (stopped rc-sysinit and net-device-up IFACE=lo)
stop on runlevel [016]

env HOME=/home/mythtv

#expect fork
respawn

script
        sleep 10
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su - -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

At least this is what worked for me.  It also looks like this has the backend start after a 10 second delay ( the 'sleep 10' line),  which is fine for me since I've been having an issue where the backend starts before my tuner is fully loaded.

---

