---
title: "recording streaming video"
date: 2010-06-20
forum: Multimedia Software
---

### Post by linux_noob0 on 2010-06-20
Hi there! I've finally found a way to actually stream .asx stuff using mplayer ( by extracting the actual link to the video from it ), and now I'd like to record it. In the asx, I've found a link to an .asf file, which I can stream using mplayer. How can I save this to view it locally? Thanks!

---

### Post by ron999 on 2010-06-20
Hi
Try using the **dumpstream** option, it should put a file on your hard drive named **stream.dump**.
Like this:-
```
mplayer -dumpstream < URL >
```

---

### Post by linux_noob0 on 2010-06-20
I've tried the -dumpstream option, but this is what I get:
```
Cache size set to 190 KBytes
Stream not seekable!


MPlayer interrupted by signal 2 in module: dumpstream
nop_streaming_read error : Interrupted system call
Error while reading network stream.
Core dumped ;)

```

Thanks again :)

---

