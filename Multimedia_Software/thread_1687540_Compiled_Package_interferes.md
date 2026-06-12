---
title: "Compiled Package interferes?"
date: 2011-02-14
forum: Multimedia Software
---

### Post by AndrewSimoes on 2011-02-14
I compiled mplayer , but badly . 
After that, I installed k9copy from the repositories. Now I want to remove mplayer but it says that k9copy depends on mplayer.
I have no problem with starting afresh after uninstalling all dependent packages . 
My real question is : 
Since k9copy depends on mplayer , when you fire in apt-get install k9copy , does a repository version of mplayer get installed by default even if you have already compiled one? 
If it's true , it's plain annoying. How to get around something like this? One wants to compile some packages , and apt-get others. 
A double package would be a headache.

---

### Post by luigi_mb on 2011-02-14
I believe it is possible to uninstall the manually compiled MPlayer from the folder where you did the compilation/installation:

```

sudo make uninstall

```

I don't know how "badly" you compiled it, so the uninstallation may fail, but it's worth a try.


/luigi

---

### Post by AndrewSimoes on 2011-02-15
Badly meaning , grossly lacking certain functionality that I need.
I used checkinstall .

---

