---
title: "How does one remove Realplayer?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by james_xxx on 2008-05-18
I have realplayer 10 installed, but for the life of me, I cannot figure out how to remove it. I might possibly like to upgrade to realplayer 11, or just get rid of it altogether.

Any help would be appreciated!

---

### Post by chunchengch on 2008-05-18
maybe you have to remove it manually, first, run these commands to find out all the directories and files corresponding to RealPlayer

[COLOR="Red"]$ sudo slocate -u
$ slocate realplay
[/COLOR]
than delete one by one carefully.

---

### Post by james_xxx on 2008-05-19
Thanks! 

Your solution worked well, and introduced me to 'slocate', which I had never before used.

---

### Post by gchatzim on 2010-04-12
THis is the automatic uninstall that what worked for me:

$ sudo -i
# /opt/real/RealPlayer/postinst/postuninst.sh
# rm -rf /opt/real/RealPlayer/

from
[http://ubuntuforums.org/showthread.php?t=920171](http://ubuntuforums.org/showthread.php?t=920171)

---

