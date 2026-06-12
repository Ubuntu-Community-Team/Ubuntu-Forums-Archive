---
title: "firefox crashes when youtube is opened"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by nikhilpaikada on 2009-07-23
I am using ubuntu ultimate edition 2.0.whenever i open youtube firefox will not respond and finally crashes.this  also happens for other sites which contains youtube videos.plz help..

---

### Post by jerrrys on 2009-07-23
may want to try

[http://www.google.com/search?q=youtube+plugin+firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=youtube+plugin+firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

is this a new install?  is this ff 3.0 or 3.5

---

### Post by nikhilpaikada on 2009-07-23
it is firefox 3.0.12

---

### Post by philcamlin on 2009-07-23
try installing the 3.5 version  :popcorn:

---

### Post by jerrrys on 2009-07-23
> **philcamlin said:**
> try installing the 3.5 version  :popcorn:
may work for you.

if this is a new install do you have flash installed?  Ubuntu Restricted Extras?  also

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

---

### Post by nikhilpaikada on 2009-07-24
thank u very much..its working now..

---

### Post by jerrrys on 2009-07-24
What was the fix?  May be helpful to others...

---

### Post by nikhilpaikada on 2009-07-24
1.Installed firefox 3.5 with the following command in terminal
" wget -O - [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2) | tar xj -C ~"
2.downloaded .tar.gz. version of flashplayer10.
3.while extracting v will get a file named libflashplayer.so
4.go to home folder.press ctrl+h.it will show hidden files.go to .mozilla
5.create a folder "plugins"
6.cut and paste "libflashplayer.so" in this folder
7.when u open firefox,we can suitably watch youtube videos

---

### Post by jerrrys on 2009-07-24
nice

---

