---
title: "audex doesn't give choice of formats"
date: 2017-07-07
forum: Multimedia Software
---

### Post by newblank25 on 2017-07-07
how to add ogg to audex ripper? Any help would be appreciated.

---

### Post by Yellow Pasque on 2017-07-09
Make sure vorbis-tools is installed (and flac if you want flac):
```
sudo apt-get install vorbis-tools flac
```
Then, (re)start Audex.

If you want mp3 support in Audex:
```
sudo apt-get install lame eyed3
```

---

