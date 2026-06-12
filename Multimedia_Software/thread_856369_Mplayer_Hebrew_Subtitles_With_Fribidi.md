---
title: "Mplayer Hebrew Subtitles With Fribidi"
date: 2008-07-11
forum: Multimedia Software
---

### Post by ForksHolder on 2008-07-11
Hello,

Well, i've been trying to enable hebrew by this guide:
[https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

It showed a fliped hebrew, witch ofcourse i can't understand.

I saw that i can flip it with Fribidi but it says that i haven't enabled it.


Do you know how to successfully enable Hebrew subtitles in Mplayer?

Thanks,
~ForksHolder.

---

### Post by ForksHolder on 2008-07-13
Bump?...

---

### Post by ForksHolder on 2008-07-13
Bump.......

---

### Post by rd1381 on 2009-11-10
i dont know about hebrew but fribidi is a package for handling bi-directional text in unix so in Hebrew is like Persian( right-to left) maybe this will apply:

download and compile the latest version of fribidi from its website (the one shipped with ubuntu it old,(or maybe more stable)) [http://fribidi.org/download/fribidi-0.19.2.tar.gz.and](http://fribidi.org/download/fribidi-0.19.2.tar.gz.and) install as root
if you dont know how to compile ,ask and i will tell you but its not that hard

you dont have to restart after installing but maybe you need to  tell your system to renew its library index with  'sudo ldconfig'

on another note vlc uses fribidi too so using that it still needs fibidi new version

---

