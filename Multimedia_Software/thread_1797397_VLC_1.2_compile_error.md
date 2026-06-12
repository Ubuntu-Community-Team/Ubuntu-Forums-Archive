---
title: "VLC 1.2 compile error"
date: 2011-07-05
forum: Multimedia Software
---

### Post by capn.hector on 2011-07-05
running ubuntu 11.04 and trying to compile vlc 1.2 from git.  ran apt-get build-dep vlc, git for the vlc source, bootstraped fine, the error is on configure

ran ./configure --enable-x264 and got the error

> configure: error: Package requirements (xcb-composite) were not met:

No package 'xcb-composite' found

any help would be great.  made sure the xcb library was installed and googled my fingers to the bone looking for any solutions  and cant find any out on the web.

---

### Post by mc4man on 2011-07-05
It built ok here earlier, may sure that this is installed
libxcb-composite0-dev

Otherwise, (or anyway),  you may want to try a slightly different build method
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

---

### Post by capn.hector on 2011-07-05
mc4man, thanks for the library its compiling now and has been for a while.  ill post in the morning whether it was a success.  i had looked at the library's and saw libxcb-dev and was wondering why it was erroring out.

---

