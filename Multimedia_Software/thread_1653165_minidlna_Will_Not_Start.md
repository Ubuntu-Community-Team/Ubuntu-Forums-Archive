---
title: "minidlna Will Not Start"
date: 2010-12-26
forum: Multimedia Software
---

### Post by klyndt on 2010-12-26
I'm trying to get minidlna to autostart at boot.  I've followed the directions here:
[http://www.audiodude.nl/?p=84](http://www.audiodude.nl/?p=84)
and here:
[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

The result is that it autostarts the very first reboot after installation and after that it no longer autostarts.  There are some interesting entries in the minidlna.log file, but I don't know what to do with the information. I'm hoping someone here will be able to point me somewhere to continue my debug.
```
[2010/12/26 08:22:31] minidlna.c:720: warn: Starting MiniDLNA version 1.0.18.2_stedy_PPA_CVS302 [SQLite 3.6.22].
[2010/12/26 08:22:31] minidlna.c:808: warn: HTTP listening on port 8200
[2010/12/26 08:22:37] minidlna.c:115: warn: received signal 15, good-bye
```

I can start the server after I log in. Everything works well then.  Where can I look to see why the server is being stopped 6 sec after it is started?  What might be causing this?

Thanks,
Klyndt

---

### Post by klyndt on 2010-12-28
Maybe I should ask this question more generically.  If I have a service that should be starting on its own and isn't, where should I look? Where could commands to stop the service be coming from? init.d? update-rc.d? Somewhere else?

Thanks for any ideas,
Klyndt

---

### Post by SirWeazel on 2011-12-16
Did you ever figure this out... i'm having the same problem. i've tired the "update-rc.d" thing, but no luck.  For now i have it autostart when i login, but this ins't pratical.

---

