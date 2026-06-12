---
title: "Rip audio streams"
date: 2009-06-01
forum: Multimedia Software
---

### Post by MimziM on 2009-06-01
can anyone tell me what app/package
I can use in gnome (intrepid) to rip
online music streams to audio file ...  ?

---

### Post by logos34 on 2009-06-01
**streamripper + streamtuner** (gui)

and/or

**mplayer** (cli)

ex. (mp3 stream):
> 
mplayer <URL> -dumpstream -dumpfile stream.mp3


(.ra/.ram realaudio stream):

> mplayer -playlist "<URL>" -dumpstream -dumpfile stream.ram

---

