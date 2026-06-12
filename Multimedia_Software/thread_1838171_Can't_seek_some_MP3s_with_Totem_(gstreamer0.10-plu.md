---
title: "Can't seek some MP3s with Totem (gstreamer0.10-plugins-ugly already installed)"
date: 2011-09-03
forum: Multimedia Software
---

### Post by Buntunz on 2011-09-03
Hello there! :)
I installed the 64bit edition of Ubuntu on my notebook: all works fine, except Totem. It plays correctly all media files, but with some MP3s I'm unable to seek with some songs. I searched for a solution and many people resolved installing "gstreamer0.10-plugins-ugly", but it is already installed. How can I resolve this problem? Thanks

---

### Post by jdorenbush on 2011-11-02
Run both of the following:

```
sudo apt-get remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-plugins-mp3-partner
```

---

