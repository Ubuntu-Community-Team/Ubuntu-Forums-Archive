---
title: "combining an avi with ac3"
date: 2008-09-09
forum: Multimedia Software
---

### Post by tsr on 2008-09-09
Hi,

So I got these files a movie (with japanese audio) and a spanish audio track. The movie is in a .avi file and the soundtrack is in a .ac3 file.

How do I play the movie with the spanish audio?

/tsr

---

### Post by lovinglinux on 2008-09-09
Download smplayer through Add/Remove manager or by command:

```
sudo apt-get install smplayer
```

Then open the video file, right click on the movie and select "Audio > Track" and choose the track you want. If the second audio is on a different file, do the same thing but select "Load external file" and browse the audio file you want

---

