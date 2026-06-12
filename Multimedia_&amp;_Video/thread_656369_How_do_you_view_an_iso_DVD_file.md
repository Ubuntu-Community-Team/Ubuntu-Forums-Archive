---
title: "How do you view an iso DVD file?"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by curiousnoob on 2008-01-02
I have an iso file on my hard drive and I do not want to burn it to disc.  I just want to view it as if I had the DVD in the drive.  
I tried VLC but whenever I tried to change menus it shut down.  Movie Player will not open it at all.
Is there some program out there to view iso files?

---

### Post by kellemes on 2008-01-02
from terminal and as root..

```
mkdir /mnt/myiso
mount -o loop -t iso9660 myfile.iso /mnt/myiso/
```
Now you have access to all files in that iso via **/mnt/myiso/**

---

### Post by disturbedite on 2008-01-02
or you could just use smplayer or kaffeine to play your iso.  no mounting needed.  :)

---

