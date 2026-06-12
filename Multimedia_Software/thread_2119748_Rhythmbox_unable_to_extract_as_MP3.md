---
title: "Rhythmbox unable to extract as MP3"
date: 2013-02-24
forum: Multimedia Software
---

### Post by ujoni08 on 2013-02-24
Rhythmbox is currently extracting CD tracks as .ogg files, but my portable MP3 player doesn't support that format, so I went into 'edit', 'preferences' to change it to extract as MP3, but it needs a plugin, which I then clicked to download, but got this error message: 'Python (v2.7) requires to install plugins to create media files of the following type: ID3 tag muxer'. Can anyone tell me what to do next (in layman's terms, please!). Thanks.

---

### Post by Yellow Pasque on 2013-02-25
From terminal (Ctrl+Alt+T):
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by speartip on 2013-02-25
Or you could use a specific application to rip your cds such as Asunder or Rubyripper, they're much more configurable.

---

### Post by ujoni08 on 2013-02-25
Thanks, you guys! The restricted extras worked. I also plan to take a look at the the other rippers.

---

### Post by nick6 on 2013-08-03
I have done this, and it still doesnt recognize the installed codecs.  in the software manager the gst-plugin0.10 good bad and ugly are all installed

---

### Post by Yellow Pasque on 2013-08-03
rhythmbox uses gstreamer1.0 as of Ubuntu 13.04, so make sure you have gstreamer1.0 good/bad/ugly plugins as well.

---

