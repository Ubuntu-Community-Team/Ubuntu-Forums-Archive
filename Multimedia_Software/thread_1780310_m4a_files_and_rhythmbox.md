---
title: "m4a files and rhythmbox?"
date: 2011-06-11
forum: Multimedia Software
---

### Post by soylentcola on 2011-06-11
So having just imported my library through to rhythmbox, I'm having an issue trying to figure out why it won't play my m4a audio files.  Is there a codec out there that I'm missing that should be installed?

Also, I got this error when trying to import a certain mp3 file: "Additional GStreamer plugins are required to play this file: ID3 tag demuxer" but I can't seem to find it anywhere...

Any help would be appreciated. :D

---

### Post by Yellow Pasque on 2011-06-11
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Yellow Pasque on 2011-06-12
> **Temüjin said:**
> ```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```
Hmm.. I'm not sure how I came to that conclusion. Maybe I was thinking of gstreamer0.10-plugins-ugly, which pulls in libid3tag0.

---

