---
title: "PenguinTV in Gutsy"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by Grump60 on 2007-10-26
Does anyone know how to get PenguinTV to work in Gutsy?  It worked fine for me in Feisty, but now it won't start.
:confused:

---

### Post by abbot on 2007-10-28
Same Here.  It's one of my most used programs.  This is what i get in terminal when i try to run it.  Does the same happen to you?

```
adam@adam-laptop:~$ PenguinTV
gecko proxy settings up to date
initializing mozilla in /usr/lib/firefox
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:301: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  self.app_window.resize(w,h)
Segmentation fault (core dumped)
```

I also found this thread in the archives.

[http://ubuntuforums.org/showthread.php?t=548022](http://ubuntuforums.org/showthread.php?t=548022)

It seems that Miro doesn't work for me either and when I did use Democracy a while back it slowed down my computer to a crawl even when it wasn't downloading.  Not having a working bittorrent supported RSS downloader is enough to make me switch back to Feisty.  Does anyone know of a fix?

---

### Post by Priit Tamboom on 2007-11-01
I got the same error.

I got it working:
1) first uninstall it from api-get
2) go to [http://penguintv.sourceforge.net/#download](http://penguintv.sourceforge.net/#download) and download latest deb.

hope it helps

---

### Post by Grump60 on 2007-11-02
Thank you for that. I installed the deb package from sourceforge and although the installer threw an error, Update Manager kicked in a few minutes later with a further update, and now it works!  Excellent!

---

### Post by Zerocool10482 on 2007-12-27
I tried the same thing but it didn't work for me. Oh well I'll try another rss feeder.

---

### Post by magiver on 2008-01-17
I found a solution in [https://bugs.launchpad.net/ubuntu/+source/penguintv/+bug/131958]("https://bugs.launchpad.net/ubuntu/+source/penguintv/+bug/131958")
just 
```
$ export LD_LIBRARY_PATH=/usr/lib/firefox
$ export MOZILLA_FIVE_HOME=/usr/lib/firefox
```
and it'll work

---

