---
title: "unable to play videos from internet"
date: 2009-10-21
forum: Multimedia Software
---

### Post by rmcellig on 2009-10-21
I installed the ubuntu-restricted-extras package, and restarted Firefox. When I go to a web site to playa video, I get a notice that the plugins are missing. What should I do?

This is where I am going:

[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

Enclosed are a couple of errors I get when I go to the apple site or the site above.

I am running 9.04

---

### Post by lovinglinux on 2009-10-21
See the troubleshooting section of [Comprehensive Multimedia & Video Howto - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=766683). It has a hack to deal with these QuickTime issues.

I also recommend gecko-mediaplayer instead of the default plugin. See the beginning of that tutorial for instructions.

---

### Post by vinutux on 2009-10-21
Try this
```
sudo apt-get install mozilla-mplayer
```

or

```
sudo apt-get install mozilla-plugin-vlc
```

---

