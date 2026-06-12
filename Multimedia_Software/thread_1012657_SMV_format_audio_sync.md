---
title: "SMV format audio sync"
date: 2008-12-16
forum: Multimedia Software
---

### Post by ushills on 2008-12-16
Further to this post [http://ubuntuforums.org/showthread.php?t=875044&highlight=smv]("http://ubuntuforums.org/showthread.php?t=875044&highlight=smv")

I am able to convert video avi files to smv but suffer the problem with audio being out of sync with the video.

What am i doing wrong, using a Philips SA3245 go gear.

---

### Post by kevh on 2009-05-05
Hello ushills,
I had the same problem and reduced the quality setting from 80 to 60 and found it worked. I use the following command format
sudo smv_encode -b -g 220x176 -f 24 -n 11 -r -1 -q 60 /home/kevin/Videos/The.Matrix2

---

