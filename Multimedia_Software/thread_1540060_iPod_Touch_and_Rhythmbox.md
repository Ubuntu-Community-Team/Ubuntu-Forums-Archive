---
title: "iPod Touch and Rhythmbox"
date: 2010-07-27
forum: Multimedia Software
---

### Post by arrimapirate on 2010-07-27
My iPod (a second gen. 16gb touch) can only be synced with Rhythmbox when im logged in as root. When im logged in as my regular user, i can see my ipod mounted and browse through it but it is not seen by Rhythmbox and can not be synced.

It should be mounting with the gvfs-fuse-daemon in my home folder but for some reason its mounting somewhere else (i have no idea where and cant seem to find out...)

Does anyone know what could be causing this or how i can fix it?

---

### Post by algoban on 2010-09-26
Hi

It works for me installing gvfs-fuse and i dont need to log in as root.

Did you try mount manually with ifuse?

---

### Post by arrimapirate on 2010-09-28
Sorry i forgot to mark this as "Solved" after i figured it out. I couldnt mount iit manually so i just created a new user and that wrked. Than you for your help

---

