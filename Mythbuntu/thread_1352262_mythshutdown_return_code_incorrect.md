---
title: "mythshutdown return code incorrect"
date: 2009-12-11
forum: Mythbuntu
---

### Post by bcgrown on 2009-12-11
Hi all,

I am using Mythbuntu 9.10 and the standard mythtv 0.22 that comes with it, for a combined frontend/backend.

The PC uses ACPI wakeup to turn on at the appropriate time, and if I do nothing then MythWelcome will shut down after the idle time is up.

However, if I schedule a recording it starts up, records, transcodes, and never shuts down afterwards.  MythWelcome gets stuck on "busy transcoding" even after the transcode is finished.

When this happened I ran the following commands:
```
mythshutdown --check
echo $!
```

Mythshutdown erroneously returns "1" for "transcoding" when the system should be idle.  I checked via MythWeb to make sure the transcode job was actually finished.

I couldn't see anything in mythbackend.log, or mythwelcome.log that gave me any clues.  If there is anything specific I should look for I can post log files later when I am at home.

Anyone have any ideas?

Hardware:
[LIST]
[*]Intel D865GLC motherboard
[*]Celeron 2.4GHz
[*]768MB ram
[*]GeForce FX 5500
[*]SB Audigy SE 7.1
[*]WinTV-PVR-USB2
[*]Agere 323-chipset firewire card (no devices connected)
[/LIST]

---

### Post by jlagrone on 2009-12-11
I'm having the same problem.  Looking at it, it looks like mythtranscode is not exiting properly.  Perhaps related to this [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/481104](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/481104) ?  Someone posted a script to kill all transcode jobs using less than 1% cpu at the bottom - it seems functional if run as a cron job, but really a less than ideal solution.

---

### Post by bcgrown on 2009-12-12
I didn't put two and two together and check if mythtranscode was still running, but it is.  If I kill the phantom transcode job, the system goes idle and shuts down like it's supposed to.

Will apply the hack for now, but this really seems like a major bug so hopefully a dev will be able to fix it "soon".

---

### Post by bcgrown on 2009-12-12
I am marking this as solved because this one issue is now fixed (with the ugly hack), only to reveal another issue.  See [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8487151#post8487151")

---

