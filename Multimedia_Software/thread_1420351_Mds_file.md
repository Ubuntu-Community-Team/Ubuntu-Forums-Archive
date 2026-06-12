---
title: "Mds file"
date: 2010-03-03
forum: Multimedia Software
---

### Post by adamhy on 2010-03-03
Just moved completely to Ubuntu 10.04. I have many educational materials in (video)mds.files. What do we use to mount those files so that I can watch them? Please help!
 
mds was created from Alcohol 52, great software.

---

### Post by polki@mac.com on 2010-03-03
It's from 2007, I have no idea how it works or even IF it works but here you go:
```

http://sathyasays.com/2007/12/15/mounting-iso-and-mdsmdf-files-in-linux/

```

---

### Post by andrew.46 on 2010-03-04
Hi adamhy,

> **adamhy said:**
> I have many educational materials in (video)mds.files. What do we use to mount those files so that I can watch them? 

Unfortunately I have no mds files to test but some of [the documentation]("http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ") claims that MPlayer can play these files:

```
mplayer file.mds -demuxer rawaudio -rawaudio format=0x1 
```

Is there a sample somewhere online for these files?

Andrew

---

