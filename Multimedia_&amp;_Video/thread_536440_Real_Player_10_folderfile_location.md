---
title: "Real Player 10 folder/file location"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by rggavubt on 2007-08-27
I installed RealPlayer 10 and put the RealPlayer folder in my home directory.  I have been reading some posts and think I should have put the folder in /usr/bin/RealPlayer.  RealPlayer works....should I move the folder to /usr/bin???  

I'm thinking the command would be as root:

     mv /home/roy/RealPlayer /usr/bin/RealPlayer

---

### Post by K.Mandla on 2007-08-27
If I remember right it's actually "realplay" ... try

```
whereis realplay
```
for the path.

Edit: I misunderstood your question; sorry about that. :oops: I think it should be in /usr/share/bin, but I don't know if that's right or not; I haven't installed it in a very long time.

---

### Post by rggavubt on 2007-08-28
> **K.Mandla said:**
> If I remember right it's actually "realplay" ... try

```
whereis realplay
```
for the path.

Edit: I misunderstood your question; sorry about that. :oops: I think it should be in /usr/share/bin, but I don't know if that's right r not; I haven't installed it in a very long time.

I'm referring to the folder in my /home directory which is called "RealPlayer"  I looked in the folder and the execute command is 'realplay" in that folder.

---

