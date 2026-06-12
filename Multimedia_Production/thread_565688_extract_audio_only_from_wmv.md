---
title: "extract audio only from wmv"
date: 2007-10-02
forum: Multimedia Production
---

### Post by ragwing on 2007-10-02
Anyone know how to extract audio only from wmv file. I did a movie on my video camera and now have a nice movie, but would like to use just the audio for a podcast. Any suggestions would be great!
Thanks

---

### Post by disraeli on 2007-10-03
I don't know whether there are any programs written specifically for that, but with this kind of task I would just start up a wave editing program and record in background the movie while it plays. I'm not an expert in audio recording under Linux, but Goldwave works just fine with wine.

---

### Post by eye208 on 2007-10-04
> **ragwing said:**
> Anyone know how to extract audio only from wmv file.
ffmpeg -i video.wmv audio.wav

---

