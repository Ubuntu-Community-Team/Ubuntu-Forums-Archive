---
title: "enable mp3 support"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by jej2003 on 2008-01-03
I just installed xfce and was wondering how to nable mp3 support in totem?

---

### Post by Yellow Pasque on 2008-01-03
If you want all the packages that Ubuntu didn't include because of legal BS..

> Commonly used restricted packages
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

Please note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
for more information.

```
sudo apt-get install aptitude
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by jej2003 on 2008-01-03
I don't understand why....but I did that again (had done it before), it installed nothing, but now the mp3s play.  Thanks

---

### Post by jej2003 on 2008-01-03
For whatever reason wav files are basically inaudible...is there a way to adjust their volume?  Mp3 playback is find btw.

---

### Post by jej2003 on 2008-01-03
for whatever reason  a restart fixed the issue.

---

