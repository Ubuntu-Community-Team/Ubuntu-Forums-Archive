---
title: "minidlna fails status=255/EXCEPTION"
date: 2022-10-18
forum: Multimedia Software
---

### Post by MickSulley on 2022-10-18
Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-50-generic x86_64)

I installed minidlna a long while ago and it was working.  I just tried to use it and it is not working.  I checked the setup, that all looks OK, I stopped and restarted it.  I checked the status, this is what I see
```
mick@holly:~$ sudo service minidlna status
× minidlna.service - MiniDLNA lightweight DLNA/UPnP-AV server
     Loaded: loaded (/lib/systemd/system/minidlna.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2022-10-18 12:18:02 BST; 2min 37s ago
       Docs: man:minidlnad(1)
             man:minidlna.conf(5)
    Process: 1833 ExecStart=/usr/sbin/minidlnad -f $CONFIGFILE -P /run/minidlna/minidlna.pid -S $DAEMON_OPTS (code=exited, status=255/EXCEPTION)
   Main PID: 1833 (code=exited, status=255/EXCEPTION)
        CPU: 39ms

Oct 18 12:18:02 holly systemd[1]: Started MiniDLNA lightweight DLNA/UPnP-AV server.
Oct 18 12:18:02 holly minidlnad[1833]: minidlna.c:1028: fatal: Failed to open log file '/home/common/.minidlna/minidlna.log': Permission denied
Oct 18 12:18:02 holly systemd[1]: minidlna.service: Main process exited, code=exited, status=255/EXCEPTION
Oct 18 12:18:02 holly systemd[1]: minidlna.service: Failed with result 'exit-code'.
```
There is an old log /var/log/minidlna.log.1 which is 18 months old and a newer one which is empty.
What can I do to fix it?
Thanks
Mick

---

### Post by TheFu on 2022-10-18
```
Oct 18 12:18:02 holly minidlnad[1833]: minidlna.c:1028: fatal: Failed to open log file '/home/common/.minidlna/minidlna.log': Permission denied
```

Fix that as a start.

---

### Post by MickSulley on 2022-10-18
Yes that was the problem, sorry I should have seen it.

Thanks for your help
Mick

---

### Post by TheFu on 2022-10-18
> **MickSulley said:**
> Yes that was the problem, sorry I should have seen it.

Thanks for your help
Mick

Your aren't the first person in this conversation to do exactly the same thing.  I've done it many, many, many, times.  I find the output on problems from systemd to be useless nearly always. This time, we have a clue to follow and correct, which is really nice.  A few weeks ago, I was having problems getting apt-cacher-ng server working after a fresh 20.04 install. It wouldn't start.  Tried to figure out out, tried 20 "fixes", none worked.  I was about to give up and move that service to some other system which would require touching every other system on the LAN.  As a last effort, I purged the package and reinstalled.  That seemed to fix it.  Don't know why.  Guessing it was some incompatible setting in the conf from 18.04 that I pulled forward manually, to avoid having to re-re-relearn something I'd solved 4 yrs ago.

---

