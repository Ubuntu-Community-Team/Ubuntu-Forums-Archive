---
title: "Audacious on the command line..."
date: 2008-06-10
forum: Multimedia Software
---

### Post by rmflagg on 2008-06-10
Hi everyone,

   I am trying to run Audacious' audtool from a script that I have in my crontab, and everytime that it runs, it fails and I get a D-Bus error:
"In program audtool:
* While attempting to connect to the D-Bus session bus
Error: D-Bus Error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
   All that the script is asking of audtool is to get the currently playing song.  I use the command: 'audtool --current-song'.  That's it.  I did notice that I get the same error if I try the command as any user other than the one that started Audacious.
   Does anyone know of a fix or a work-around?

Thanks,
RMFLagg

---

### Post by krisek on 2008-08-10
Hi,

I have exactly the same problem. Any idea?

Many thanks,
Kristof

---

### Post by rmflagg on 2008-08-11
Unfortunately, my solution was to go back to using XMMS for that task. >:(

RMF

---

### Post by krisek on 2008-08-12
I've found something, first let me clarify my goal:

- symlink the currently played directory into a folder called recent
- update a file called 'last_played_YYYY_MM_DD_hh_mm' (the file name contains the current timestamp) in the currently played directory

The original idea was to run a cron job in each 3 minute to query Audacious playlist, but this failed as described above. But there's a Audacious plugin called 'Song Change' which can run any script when a new  song is started and Audacious can pass the current filename (beside a lot of things) as argument to this script. 

This is exactly what I want.

(I can upload my script if anyone's interested.)

---

