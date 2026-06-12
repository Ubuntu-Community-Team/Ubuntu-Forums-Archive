---
title: "MythExport daemon not starting during reboot"
date: 2009-06-04
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-04
I've installed the mythexport plugin from the PPA repository on mythbuntu 9.04 and all was working well, until I needed to reboot my machine for unrelated reasons.  When it came back up, the mythexport daemon was not running.  I was able to start it from the terminal with "sudo service mythexport start".  The startup script is in /etc/init.d and there is a link to it as S25mythexport in /etc/rc2.d.  I can find no errors in a log file as to why it was not running.

Related to this, with the daemon not running, the export jobs I queued up from the frontend displayed no errors and the logs on the system status page shows they completed successfully.  However, I had no transcoded recordings obviously since the daemon was not running.  There should probably be some type of feedback when the daemon is not started in mythfrontend.  I had to figure this out by ssh into the box and doing a pgrep.

---

### Post by LorenzoS on 2009-06-21
I just noticed the same problem.  I'm on 8.10.  When I try to check the status:
```
/etc/init.d/mythexport status
```I get the following error:
```
chown: changing ownership of `/var/run/mythtv/mythbackend.pid': Operation not permitted
chown: changing ownership of `/var/run/mythtv': Operation not permitted

```Running the command as root does work successfully.

---

### Post by rhpot1991 on 2009-06-22
The issue here is that the Backend sometimes isn't ready when it should be, normally getting held up by MySQL.  The quickest way to deal with this would be to sudo /etc/init.d/mythexport restart after the backend is ready.  If I can find a better placement I may change the PPA.  If it bothers you a lot you can rename S25mythexport to S99mythexport for the time being.

---

### Post by rhpot1991 on 2009-06-22
> **LorenzoS said:**
> I just noticed the same problem.  I'm on 8.10.  When I try to check the status:
```
/etc/init.d/mythexport status
```I get the following error:
```
chown: changing ownership of `/var/run/mythtv/mythbackend.pid': Operation not permitted
chown: changing ownership of `/var/run/mythtv': Operation not permitted

```Running the command as root does work successfully.

Yep, you need to sudo the init script.

---

