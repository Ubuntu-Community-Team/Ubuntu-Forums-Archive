---
title: "I'm having trouble adding songs to my ipod."
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Give_Peace_A_Chance on 2007-05-27
[IMG]http://i5.photobucket.com/albums/y183/shadyichigo/Screenshot-rhythmbox.png[/IMG]

Oh do i access it.

---

### Post by Pollywoggy on 2007-05-27
> **Give_Peace_A_Chance said:**
> 

Oh do i access it.

Have you tried gtkpod?  That is the command and also the name of the package.

BTW in order to get my ipod to work, I had to add a line to my /etc/fstab like this:

/dev/sda2     /media/ipod     vfat    rw,user,noauto, 0       0

I also had to create /media/ipod/  (it is owned root.root)

---

