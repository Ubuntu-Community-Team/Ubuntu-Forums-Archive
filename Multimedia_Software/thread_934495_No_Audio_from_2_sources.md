---
title: "No Audio from 2 sources"
date: 2008-09-30
forum: Multimedia Software
---

### Post by gukarma on 2008-09-30
Hey there,

Recently installed Unbuntu and am loving it; don't even want to dual boot anymore.

I am having a slight problem, however: I can only play audio from one source at once. It is more annoying than you think. For instance, if I am listening to music and want to check something out on Youtube, I have to completely exit out of the audio program, restart firefox, and then Youtube will play audio. 

What gives?

Thanks,

Gustavo

---

### Post by Crafty Kisses on 2008-09-30
What are the results of this command > lspci

---

### Post by wolfen69 on 2008-09-30
this is a very common problem. open terminal and:
```
sudo apt-get install libflashsupport
``` then restart firefox.

---

### Post by WWSmith36 on 2008-09-30
I had that same problem but by following this thread, I fixed my sound.

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

Hope it helps

---

### Post by gukarma on 2008-09-30
> **wolfen69 said:**
> this is a very common problem. open terminal and:
```
sudo apt-get install libflashsupport
``` then restart firefox.

This worked very well. Thanks.

---

