---
title: "[SOLVED] Playing Movies"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by famous3warriors on 2007-12-30
I am using Kaffeine  movie player and the movie stalls about one second then continues to play and does this throughout the whole movie.  The movies stalls and continues.  The sound is great goes along with the movie.  Is there anything that I can do to fix that.

---

### Post by famous3warriors on 2007-12-30
Thanks for your help I really do appreciate it.

---

### Post by taurus on 2007-12-30
Have you tried the same movie with another player to see if it behaves the same?

---

### Post by famous3warriors on 2007-12-30
now I have not I will do that so I could see what is happening.  Thanks.

---

### Post by ahaslam on 2007-12-30
> **famous3warriors said:**
> Thanks for your help I really do appreciate it.

;)

---

### Post by famous3warriors on 2007-12-30
I installed totem xine and it runs the same and I get this msg.  I did install w32codecs and have medibentu.  I get this msg and I do not know how to fix that.:confused:

---

### Post by ahaslam on 2007-12-30
Just get libdvdcss from medibuntu as well...

---

### Post by famous3warriors on 2007-12-30
I redid medibuntu now this is what I get when I try to update. :confused:

---

### Post by taurus on 2007-12-30
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by famous3warriors on 2007-12-30
this is what I have in my source list.

---

### Post by famous3warriors on 2007-12-30
Thanks Taurus I really do appreciate your help.  I did what you suggested and it worked.  I don't know what happened.  I had it working before then for some reason it stopped working correctly.  Thanks once again.

---

