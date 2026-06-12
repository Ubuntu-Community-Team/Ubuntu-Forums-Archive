---
title: "K3B mp3 support"
date: 2010-10-23
forum: Multimedia Software
---

### Post by h8train on 2010-10-23
Well the only topics I saw about k3b and mp3 support were in the archives. but since I ran into this problem and the archives didn't help me, I figured I would post how I got it working.

Problem: I Can't burn audio cd's with mp3 files in k3b.

Solution:
```
sudo apt-get install libavutil49
sudo apt-get install libavcodec51
sudo apt-get install libk3b3-extracodecs

```

I needed libk3b3-extracodecs wich needed libavcodec51 which inturn needed libavutil49.

Maybe other people will already have codec 51 and codec 49 and only need to install the extracodecs.


Now you should have no problem burning mp3's

Well hope this helps some one along the way.

h8train

---

