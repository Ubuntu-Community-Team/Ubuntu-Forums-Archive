---
title: "ffmpeg thumbnail error"
date: 2009-08-18
forum: Multimedia Software
---

### Post by KvnBushi on 2009-08-18
Hi everyone. When running a thumbnail script, I am receiving an error that is over my head at the moment.

Here is the error :


```
/usr/bin/ffmpeg: relocation error: /usr/lib/libavdevice.so.52: symbol snd_pcm_htimestamp, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
```




EDIT : This happens when I run any ffmpeg command, not just a thumbnail command.



Any help would be HIGHLY appreciated!

---

### Post by KvnBushi on 2009-08-18
I fixed this by installing ffmpeg-devel on my Media Temple (dv) server

---

