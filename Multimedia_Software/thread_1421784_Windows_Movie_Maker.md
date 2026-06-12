---
title: "Windows Movie Maker"
date: 2010-03-04
forum: Multimedia Software
---

### Post by maddg3241 on 2010-03-04
Is there something on Ubuntu That can replace Windows Movie Maker?

---

### Post by blur xc on 2010-03-04
kdenlive, opeshot, pitivi.  

I've used kdenlive a bit, never got openshot installed (last time I tried it was not in the repos, don't even know if it is now or not), and pitivi was still in early development.  I don't know how far along they've come.

BM

---

### Post by maddg3241 on 2010-03-04
thanks

---

### Post by no2498 on 2010-03-04
you may try lives 
this is just its how too 
[http://lives.sourceforge.net/manual/LiVES_manual.html#section3.1](http://lives.sourceforge.net/manual/LiVES_manual.html#section3.1)

you can find it at getdeb

---

### Post by Thomas Garman on 2010-03-04
Not really.  Pitivi is not even close to the level of functionality and nothing else is even close to the simplicity, but I use KINO for simple video editing tasks.  My suggestion is this:

Use XP in a virtualbox and run Movie Maker in there.

---

### Post by maddg3241 on 2010-03-05
ok will do thank you for all your help

---

### Post by DexterP17 on 2010-03-05
Try using Openshot it is a very good movie editor. and way better than pitivi at the moment. Just yahoo openshot movie editor and it will show you how to install it into the repositories.

---

### Post by SonicSteve on 2010-03-05
I have to agree with DEX,

OPENSHOT is awesome! I just found it earlier today and It is was exactly what everyone has been asking for. Something as simple as Windows Movie maker for Linux. So far I like this program far more. 

Give it a try, I haven't used WMM in 4 years but from what remember of it openshot is better, and easier.

I did have some install issues. 

This bug cropped up on one of my computers,

[https://answers.launchpad.net/openshot/+question/87661](https://answers.launchpad.net/openshot/+question/87661)
The last post is what fixed it.
In a terminal type
sudo ln -s $(ls -C /usr/lib/libmlt++.so.* | cut -f 1 -d' ') /usr/lib/libmlt++.so.2

---

### Post by maddg3241 on 2010-03-05
ok thanx

---

### Post by philip5 on 2010-03-11
I have packaged the latest version of both Openshot (1.1), Kdenlive (0.7.7.1) and the framework MLT (0.5.2), that both openshot and kdenlive use to handling media content, for Ubuntu 9.10 (Karmic) on my PPA.

More info about my repository on Launchpad is found if you follow the link in my signature.

Have fun!

---

