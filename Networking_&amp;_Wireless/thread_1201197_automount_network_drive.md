---
title: "automount network drive"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by xstepalex on 2009-06-30
hello, I am a long time windows user, and i'm trying to automount a lacie ethernet disk mini. I can see it and browse into it in my network folder but I would like it to mount automatically on startup. Also, in windows I could make the network drive a part of the system and rename it  C:\\ for exemple, and i'd like to know if I can do something similar in ubuntu.

I'm running jaunty 9.04

---

### Post by Boondoklife on 2009-06-30
Well I know you can do it by editing the fstab file and adding cif mounts to it, and here is an article with another method [http://ubuntuforums.org/showthread.php?t=1186877&highlight=fstab+cifs](http://ubuntuforums.org/showthread.php?t=1186877&highlight=fstab+cifs)

---

### Post by xstepalex on 2009-07-01
ok nice thanks for the quick answer, that seams to be exactly what i needed. Do I need to set up a samba server to use this method ?

---

### Post by Boondoklife on 2009-07-01
You will need samba installed to get it working but I dont think the server side has to be up.

---

