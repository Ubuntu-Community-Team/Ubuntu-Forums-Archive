---
title: "SDL installation problem"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Sordelka on 2007-12-21
Hello, I am trying to install SDL libraries. Any packages from the repositories or from the 

[www.packages.ubuntu.com](www.packages.ubuntu.com) gives me this error during install:

[[IMG]http://img205.imageshack.us/img205/2803/screenshotgdebigtkov9.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotgdebigtkov9.png)

I am on Ubuntu Gutsy 7.10, i386 machine. Video card: Nvidia

---

### Post by Nicholai on 2008-01-10
I'm having the exact same problem I've tried removing and reinstalling the package with synaptec and apt-get with no luck.  Any advice?

---

### Post by Nicholai on 2008-01-12
Figured it out 8-)
Just download libsdl1.2debian-alsa from ]http://packages.ubuntu.com/gutsy/libs/libsdl1.2debian-alsa[/URL] and then ```
sudo dpkg -i --force-overwrite (path to .deb)
```

---

