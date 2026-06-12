---
title: "Songbird on Kubuntu"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by theredcross on 2007-05-08
Songbird looks neat indeed, but I've run into the little problem of it _not playing any of my music files, regardless of extension_. I don't know what the deal is, I tried installation through automatix2 as well as unpacking the tar.gz from the website and it does the same thing. Amarok plays fine, videos play fine, can't see whats the matter with it. help?

---

### Post by anachreon_ on 2007-05-08
theredcross, it's a codec issue - you probably don't have the gstreamer codecs installed by default on your ubuntu box.  Go here to see what packages to install :

[http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer)

I had the same issue as you and it was solved by installing the correct codecs.  Good luck.

---

### Post by theredcross on 2007-05-08
sweet, thanks. all set now.

---

