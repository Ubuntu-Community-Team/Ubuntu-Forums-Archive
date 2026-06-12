---
title: "Sound Juicer and gstreamer0.10-plugins-really-bad?"
date: 2010-02-05
forum: Multimedia Software
---

### Post by JSeymour on 2010-02-05
I'm installing Sound Juicer to rip CDs.  The notes say it wants "gstreamer0.10-plugins-really-bad  (not available in Debian) to encode to AAC."  Now I don't know as I'll *want* to encode to AAC (I primarily plan to rip to .wav for burning compilation CDs), but I figure I might as well grab it, for completeness :).  I noticed, on Google'ing for info on that package, comments that *seem* to indicate its functionality has been replaced by gstreamer0.10-plugins-bad.  So, do I still "need" gstreamer0.10-plugins-really-bad?

Thanks,
Jim

---

### Post by mc4man on 2010-02-05
The 3 most common gstreamer plugins would be  gotten from  this (mainly for decoding
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

Then for some add., mainly encoding (including aac (faac
```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

THe multiverse is for the most part what you're seeing as 'really-bad'

---

### Post by JSeymour on 2010-02-05
> **mc4man said:**
> The 3 most common gstreamer plugins would be  gotten from  this (mainly for decoding
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```
Got 'em

> **mc4man said:**
> Then for some add., mainly encoding (including aac (faac
```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```THe multiverse is for the most part what you're seeing as 'really-bad'
You mean like this:```

$ dpkg -l |grep multiverse
ii  gstreamer0.10-plugins-bad-multiverse  0.10.13-0ubuntu1   GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1   GStreamer plugins from the "ugly" set (Multi
```?

Then I'm all set?

Thanks,
Jim

---

### Post by JSeymour on 2010-02-06
> **JSeymour said:**
> Then I'm all set?

Thanks,
Jim
Yes? No?  Maybe? Go away, son, ya bother me? :)

Jim

---

### Post by mc4man on 2010-02-06
> Then I'm all set?

As far as sound-juicer and the avail. formats to rip/encode to,  you should be.
Don't use sj , but I believe it can do 7 formats - .m4a, .flac, .ogg, .mp2, .mp3, .wav, .spx

---

### Post by JSeymour on 2010-02-06
> **mc4man said:**
> As far as sound-juicer and the avail. formats to rip/encode to,  you should be.Great!  Thanks for the help :)

Jim

---

### Post by kaminarisama on 2010-02-06
Great fix......

Ta.:D

---

