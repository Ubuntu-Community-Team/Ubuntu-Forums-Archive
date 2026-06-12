---
title: "Using OSS in MythTV"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by pteri498 on 2008-01-03
I have a PCHDTV 5500, and for the past few weeks have had nothing but trouble trying to configure it.

Finally, I've got video going through the analog driver, but for mythtv, audio is VERY choppy. I can't make a word out.

Fortunately, I found the following command:

```
sox -t ossdsp -r 48000 -b -c 2 /dev/dsp1 -t ossdsp /dev/dsp 
```

Which plays perfect audio through the terminal as a separate process. However, I'm wondering whether I can implement this in mythtv. I don't know if mythtv is using alsa or oss drivers, and assuming alsa, how could I change to oss?

The audio driver that mythtv is using is, in fact, /dev/dsp1, so i don't know what the problem is.

Worst case scenario, I could just route mythtv to /dev/null and always run audio through sox, but that seems like a needless extra step. Plus I don't know how that would affect recording.

---

### Post by pteri498 on 2008-01-04
*badum bum bump*

---

