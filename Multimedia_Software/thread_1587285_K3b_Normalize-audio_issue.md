---
title: "K3b Normalize-audio issue"
date: 2010-10-03
forum: Multimedia Software
---

### Post by Swagman on 2010-10-03
It's been ages since I compiled my own mp3 cd's so I thought I'd burn a new one. I prefer to use K3B but I haven't done this on Lucid (32bit).

So.. Fire up K3B

Build burn list
Select burn options and try and select Normalize. Now you already know what happens next .. Normalize-audio isn't installed right ?

Correct

So
```
 sudo apt-get install normalize-audio
```

Job sorted.... right ?

**WRONG**

Bah!
[img]http://www.upload3r.com/serve/031010/1286112453.jpeg[/img]


Ok.. Anyone help me out get this sorted please ? I have tried reinstalling only to be told the latest version **IS** installed .. I've restarted the app...Rebooted.. Shouted at it..

Grrrr

I'm crap at googling the only results I'm getting are from 2006

---

### Post by Swagman on 2010-10-03
No answer....

I want me money back !!

Oh.. Wait !!

AKA.. BUMP!

:)

---

### Post by yabbadabbadont on 2010-10-03
I wonder if it is looking for /usr/bin/normalize instead of /usr/bin/normalize-audio.  Just as a test, try creating a symbolic link and see if it detects it.

```
sudo ln -s /usr/bin/normalize-audo /usr/bin/normalize
```

---

### Post by Swagman on 2010-10-03
Hey thanks for reply.. I assume you missed an **i** out in that command (aud**i**o) ?

---

### Post by yabbadabbadont on 2010-10-03
Yup.   Umm... I mean, I was just checking to see if you were paying attention.  :D

---

### Post by Swagman on 2010-10-03
I tried that but it didn't cure it

:-(

I burnt (& normalised) my  project in Brasero (which I dislike) and it did it successfully.

oh well !!


Time to try it out in my truck (Time for WorkyPooz)

---

