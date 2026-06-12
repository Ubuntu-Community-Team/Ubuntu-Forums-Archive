---
title: "MythTV Accessing XP Files"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by tez1982 on 2007-07-03
I'm Running a Feisty MythTV box on a home network. My XP machine has all my music, videos and photos on which I would like MythTV to access.

I have samba installed and can browse all the shared files on my XP Machine (tezpc). However whatever I seem to enter in MythGallery > Directory that Holds Images - I always get the error that directory does not exist???

Can anyone help?

---

### Post by newlinux on 2007-07-03
Do you just have a samba share setup, or did you actually mount the share? For myth, you may need to mount the samba share on the myth machine before accessing it.

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by MCMcButtah on 2007-07-03
I had this issue with a few apps. Basically it is what newlinux suggested, mounting the share. When you try and access samba files without mounting the share, the OS seems to want to download the file local first.

---

### Post by hansoffate on 2007-07-03
I am having trouble fully understanding what you want.  I think it is kind of what my setup is.

I have all my Musik on a folder on my Win Xp box named "Musik".  In Feisty, I have a networked folder that is setup like this:
```
/Share
          /Musik
          /Videos
          /Computer

```

I have Samba mount my windows folder "Musik" to the /Share/Musik directory so all my musik is displayed there.  I then configured Mythtv Music to look in /Share/Musik where it plays all my networked musik.

I used this tutorial on how to set up the mount. [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Does this help?
-Hans

---

### Post by MCMcButtah on 2007-07-03
Well if you are mounting the share to a directory then there goes my theory. That as the problem I had with mythtv and amarok.

---

### Post by tez1982 on 2007-07-04
Thats brilliant, yes I did need to mount the directories properly (feeling rather silly now)

Excellent guide thanks very much for the help!

---

### Post by newlinux on 2007-07-04
No need to feel silly. Some clients can access the files without specifically mounting the directories, but you are always safest if you mount them.

---

