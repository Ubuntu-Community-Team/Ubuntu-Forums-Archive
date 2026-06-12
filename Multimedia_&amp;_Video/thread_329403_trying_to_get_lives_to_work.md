---
title: "trying to get lives to work"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by lime4x4 on 2007-01-01
i've downloaded lives and compiles and built the package but when i try to start it i get this error

john@john-edgy:~/Desktop/lives-0.9.8.2$ lives
lives: error while loading shared libraries: libjack.so.0: cannot open shared object file: No such file or directory

I've downloaded and installed every libjack package from ubuntu with no luck

Any ideas?

---

### Post by pseudonym on 2007-01-01
Sounds like you need to set up a symlink 'libjack.so.0' to the Ubuntu-named libjack in /usr/lib . Then run 'sudo ldconfig' to register the change.

But why did you compile that when there is an [Ubuntu package]("http://lives.sourceforge.net/index.php?do=downloads&PHPSESSID=578e9a8976cc60707bc7a882585038b3") available at the lives website?

---

