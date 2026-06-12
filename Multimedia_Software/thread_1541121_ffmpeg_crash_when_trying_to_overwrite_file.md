---
title: "ffmpeg crash when trying to overwrite file"
date: 2010-07-28
forum: Multimedia Software
---

### Post by Wiggoggs on 2010-07-28
Hello, I'm getting some funny behavior from ffmpeg when I'm trying to increase the volume of an mp3 file and have it overwrite itself.  For example, if I execute the following command:

```
ffmpeg -i name.mp3 -vol 1024 -y name.mp3
```

it will code the first 5 seconds or so and then quit with:

```
[mp3 @ 0x2db16d0]incomplete frame
Error while decoding stream #0.0                                                                                                                                                                          
size=      43kB time=5.54 bitrate=  64.0kbits/s    
video:0kB audio:43kB global headers:0kB muxing overhead 0.074405%
```

or something similar.

Any ideas as to why this is happening or how to avoid it?

---

### Post by ron999 on 2010-07-28
> **Wiggoggs said:**
> ... how to avoid it?

Don't try to over-write them.
Make a **temp** folder to put them in.
Then delete the originals afterwards.

This command will double the volume:-
```
ffmpeg -i name.mp3 -vol 512 temp/name.mp3

```

---

