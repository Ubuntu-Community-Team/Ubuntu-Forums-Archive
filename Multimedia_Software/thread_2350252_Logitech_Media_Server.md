---
title: "Logitech Media Server"
date: 2017-01-22
forum: Multimedia Software
---

### Post by merlinus on 2017-01-22
I just installed this from the downloaded .deb file at their website.  It appeared to install successfully, but does not appear on any of the menus, and I cannot find the correct command to run it from the terminal.

Help is appreciated!  I am running Ubuntu 16.04.

---

### Post by ian-weisser on 2017-01-22
Try dpkg -L <packagename> to list the files, including executables, installed by the package.

---

### Post by merlinus on 2017-01-22
This looks like the command:  /usr/sbin/squeezeboxserver

but when I click on that file it opens the perl code in gedit, and nothing happens.

---

### Post by cariboo on 2017-01-24
Run:

```
/usr/sbin/squeezeboxserver
```

as a regular user in a terminal then access it at:

```
http://localhost:9000
```

---

