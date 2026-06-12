---
title: "Video Problems with 9.10"
date: 2009-11-07
forum: Multimedia Software
---

### Post by mrwoody on 2009-11-07
Hi *. 
After I upgraded to 9.10, I am having weird problems with video. It looks like it is showing the negative colors. This happens with all the softwares. It can be solved if I use something like mplayer -vo gl ...
I have this problem with 2 different computers. Does anyone know how to fix it? 

**Thanks!!**

---

### Post by sc30317 on 2009-11-07
What kind of graphics card?

---

### Post by mrwoody on 2009-11-07
> **sc30317 said:**
> What kind of graphics card?

Nvidia on both of them:
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)

---

### Post by xc3RnbFO8P on 2009-11-07
> **mrwoody said:**
> Hi *. 
After I upgraded to 9.10, I am having weird problems with video. It looks like it is showing the negative colors. This happens with all the softwares. It can be solved if I use something like mplayer -vo gl ...
I have this problem with 2 different computers. Does anyone know how to fix it? 

**Thanks!!**

I had this problem when upgraded 9.10,
fresh install solved the problem.

You can check if you got the right kernel installed:
> uname -a

---

### Post by mrwoody on 2009-11-07
> **Ringi said:**
> I had this problem when upgraded 9.10,
fresh install solved the problem.

You can check if you got the right kernel installed:

Well I am a bit too lazy to fresh install everything. This problem should be solved and I am surprised people are not talking about this. 

```

queens:~$ uname -a 
Linux queens 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux


```

---

### Post by xc3RnbFO8P on 2009-11-07
> Well I am a bit too lazy to fresh install everything. This problem should be solved and I am surprised people are not talking about this.
You can spend hours to find solution, when it only takes 1,5 hour to make a fresh install with all codec and programs that I need :)

---

### Post by mrwoody on 2009-11-07
> **Ringi said:**
> You can spend hours to find solution, when it only takes 1,5 hour to make a fresh install with all codec and programs that I need :)

Well I have this problem on 3 different computers. And anyway I do think that a solution needs to be found. You cannot ask people to fresh install every 6 months.

---

### Post by xc3RnbFO8P on 2009-11-07
Try this (if got Nvida card):
[http://ubuntuforums.org/showthread.php?t=1308346]("http://ubuntuforums.org/showthread.php?t=1308346")

---

### Post by mrwoody on 2009-11-08
> **Ringi said:**
> Try this (if got Nvida card):
[http://ubuntuforums.org/showthread.php?t=1308346]("http://ubuntuforums.org/showthread.php?t=1308346")

Thanks for the hint! 
Apparently, it has not been solved yet, but I am glad that I am not alone. 
I suppose any discussion on this bug should continue there.

---

