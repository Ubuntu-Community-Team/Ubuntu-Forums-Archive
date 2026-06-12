---
title: "how do i burn video ts folders?"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Malik on 2007-10-27
so it can play like a real dvd?

---

### Post by archivator on 2007-10-27
I'm afraid there's no GUI way to do it (or at least I haven't found it yet).

Open up a terminal and browse to the directory that contains the VIDEO_TS folder.
This directory should contain only a VIDEO_TS directory and (optionally) an AUDIO_TS directory. Nothing else.

```
archivator@Serenity:~/my_dvd$mkisofs -dvd-video -o my_dvd.iso .
```
Wait for it to finish and then open this directory in Nautilus. Right click on my_dvd.iso and select *Write to disc* ;)

---

### Post by taurus on 2007-10-27
K3b can do that for you.  Just pick the Make Video and drag the VIDEO_TS directory from the top window into the second/bottom window and you are all set.

---

### Post by gottifour on 2008-03-20
> **taurus said:**
> K3b can do that for you.  Just pick the Make Video and drag the VIDEO_TS directory from the top window into the second/bottom window and you are all set.

Thanks this works great...

---

