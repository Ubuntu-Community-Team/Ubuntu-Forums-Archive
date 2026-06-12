---
title: "Install problem"
date: 2008-10-16
forum: Mythbuntu
---

### Post by ubv1308 on 2008-10-16
I installed Mythbuntu and I'm getting to the desktop but if I try to start the frontend or backend, I'm getting : No UPnP Backend found

I found those three threads :

[http://ubuntuforums.org/showthread.php?t=883583](http://ubuntuforums.org/showthread.php?t=883583)
[http://ubuntuforums.org/showthread.php?t=881876](http://ubuntuforums.org/showthread.php?t=881876)
[http://ubuntuforums.org/showthread.php?t=726680](http://ubuntuforums.org/showthread.php?t=726680)

I'm pretty much a linux newbie but if I understand the frontend and backend are not communicating with each other (because the mythconverg database was not being created). Just to mention it, I've installed everything on the same machine, frontend and backend.

To check if the backend is installed i did:
marie@marie:~$ ps aux | grep mythbackend
mythtv   13306  0.8  1.5  72212  8108 ?        Ssl  15:18   0:18 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
marie    19472  0.0  0.1   3004   752 pts/0    R+   15:54   0:00 grep mythbackend


What do I do from here ? I'm at a total lost. I would post what's written in the terminal but when I do crtl-c the windows close. I'm guessing there's a command for that.

---

### Post by SiHa on 2008-10-17
To answer your last problem, to copy from a terminal it's CTRL+SHIFT+C.

---

