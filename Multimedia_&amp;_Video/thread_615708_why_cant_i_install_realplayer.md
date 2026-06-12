---
title: "why cant i install realplayer?"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by benniebrown07 on 2007-11-17
when i try to install realplayer it says:

(Reading database ... 98382 files and directories currently installed.)
Unpacking realplay (from .../realplay_10.0.3-1.i386.deb) ...
dpkg: error processing /home/benniebrown/Desktop/realplay_10.0.3-1_i386.deb (--i
nstall):
trying to overwrite '/usr/share/mimelnk/application/vnd.rn-realmedia.desktop',
which is also in package kdelibs-data
 anyone know how to fix this

---

### Post by wolfger on 2007-11-17
Where are you getting the package "realplayer" from? I don't see it in my repositories.

---

### Post by benniebrown07 on 2007-11-17
i downloaded it from the website i believe and installed the needed software then tried to install realplayer and thats what i got in return

---

### Post by wolfger on 2007-11-17
I looked into it a bit and found that Helix is in the repos. Would that work for you? I'm not sure what else could be done aside from uninstalling the conflicting package.

---

