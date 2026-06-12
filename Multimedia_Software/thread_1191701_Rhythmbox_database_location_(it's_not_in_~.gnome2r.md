---
title: "Rhythmbox database location (it's not in ~/.gnome2/rhythmbox)"
date: 2009-06-19
forum: Multimedia Software
---

### Post by nortexoid on 2009-06-19
Where's the rhythmbox database, rhythmdb, in Jaunty? It's not in ~/.gnome2/rhythmbox, and I need to access it to change the directory structure. I accidentally hibernated my Windows NTFS partition which has all my music on it and then when I forced an auto-mount of it, I stupidly changed the location of the mount from /media/disk-1 to /media/disk, and now rhythmbox can't find any of my music.

---

### Post by drs305 on 2009-06-19
I believe you will find it in:
> 
~/.local/share/rhythmbox/


---

### Post by nortexoid on 2009-06-19
Thank you kindly sir. A little replace of 'disk-1' with 'disk' in rhythmdb.xml did the trick.

---

### Post by eduardolara on 2010-06-23
Thanks [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945"). You are awesome. :p

I am using Ubuntu 10.04 and crashed my database. Thanks to you I could rename the file and fixed my player. **Yeahh !!!**

---

### Post by leonbravo on 2011-07-24
If you were looking for such file in your system. You can always use locate rhythmdb.

In a backup you can also use find . -name

---

