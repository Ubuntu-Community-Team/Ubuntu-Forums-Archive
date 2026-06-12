---
title: "ATI Driver + Divx problem"
date: 2008-10-01
forum: Multimedia Software
---

### Post by jerryhui on 2008-10-01
Hi All,

Actually, i have encountered some problem to setup my ATI display driver.

I have used the latest binary driver from ATI, and so far the installation was success ed.  However, when i play a divx file, the "movie" will kept shining.  If I tried to disable the Composite refer [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), the movie become stable, but i will get loss the Visual Effects like "AWN' etc ...

I have no idea what's going on.  Anyone please advise. :)

Thank you so much
Jerry

---

### Post by binbash on 2008-10-01
make the out put x11 at your media player, it will be fixed.

---

### Post by jerryhui on 2008-10-02
Hi binbash,

Thanks for your quick reply.  BTW, what do you mean 'make the out put x11 at your media player !?'  Should I disable the "Composite" option in X11, or any config i have to alter ?

Please told me more if possible.  Thanks in advance.

Rgds
Jerry

---

### Post by binbash on 2008-10-02
What are you using to open your video files?VLC , mplayer, smplayer etc?

---

### Post by jerryhui on 2008-10-02
mplayer

---

### Post by binbash on 2008-10-02
gmplayer

right click and go to preferences.go to video.And select X11.

---

