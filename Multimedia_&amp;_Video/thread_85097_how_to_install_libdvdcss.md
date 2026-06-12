---
title: "how to install libdvdcss"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by jinxed05 on 2005-11-01
hi eveyone ,i'm sure if this the place to post this but does anyone know how to install libdvdcss 1.2.9 ? not having any luck . i'm a newbie

---

### Post by phanboy_iv on 2005-11-01
Try searching the forum. And the Wiki.
That's how I figured it out.

---

### Post by Kyral on 2005-11-01
Read this

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bored2k on 2005-11-01
From a terminal:```
wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb -c
wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2-dev_1.2.8-1_i386.deb -c
sudo dpkg -i *.deb
```

---

