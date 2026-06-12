---
title: "ACPI wakeup/shutdown - scheduled recordings do not record"
date: 2009-06-09
forum: Mythbuntu
---

### Post by DominicF on 2009-06-09
Hi,

I'm using Mythbuntu 9.04 and have setup acpi wakeup/shutdown.  The problem is when the machine wakes up (after its auto shutdown) it doesn't begin the recording process.  When I check "upcoming Recordings" the list appears empty and hence it doesn't record anything.  The observation I made afterwards was when I go back into "schedule recording" (viewing the EPG) to setup the recordings again - when I select the first item and press "r" on the  keyboard I notice the other programmes I had set to record previously get highlighted with the "S" symbols.  It's like it remembered that I had previously set those up but it keeps happening, after the startup it forgets again.

Any ideas what's going on here?

---

### Post by DominicF on 2009-06-09
Using the Mythweb interface I can see all my attempts to setup the recording under "Schedule Recordings (manual,custom).  The Recording Priority for these programme items show as being zero "0".

---

### Post by laffinet on 2009-06-09
Does this only happen when using wakeup/shutdown ? 
Does the machine record properly when running normally, ie without coming back from an automated shut down ?

---

### Post by DominicF on 2009-06-10
Hi, 

Discovered that it not due to the wakeup/shutdown routine.  It even happens if I manually shutdown and restart the machine.  At restart the recordings scheduled disappear from the "upcoming recordings" list.

If I leave the machine (after setting up some recordings) it does continue to record at the scheduled time.

---

### Post by jfsylvain on 2009-06-10
> **DominicF said:**
> When I check "upcoming Recordings" the list appears empty and hence it doesn't record anything.

I had the same problem.  It is probably related to a mysql bug.  See [_this Launchpad discussion_]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/326768").

[_This post_]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/326768/comments/35") from that discussion fixed it for me.

---

### Post by DominicF on 2009-06-11
Looks good but not sure how to apply the fix.

Any advice?

---

### Post by jfsylvain on 2009-06-11
> **DominicF said:**
> Looks good but not sure how to apply the fix.

Any advice?

1. /usr/bin/mysqld_safe is a shell script, open it in an editor.

2. change this line:
trap '/usr/bin/mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf refresh' 1 # HUP

to this:
trap '/usr/bin/mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf refresh [COLOR="Red"]& wait[/COLOR]' 1 # HUP

3. save the file

4. reboot

---

### Post by DominicF on 2009-06-14
Looking at the file on my machine:

/usr/bin/mysqld_safe

it already has this line:

trap '/usr/bin/mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf refresh & wait' 1 # HUP

---

### Post by DominicF on 2009-06-14
I setup some recordings in mythtv.

I removed the & wait from the file, saved and rebooted.

At the restart I checked upcoming recording - none listed.  I put back the & wait in the file, saved and rebooted.

At the restart I checked again upcoming recodings and now they are listed.

Great it works now!

---

