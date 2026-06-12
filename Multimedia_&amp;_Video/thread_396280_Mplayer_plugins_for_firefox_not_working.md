---
title: "Mplayer plugins for firefox not working?"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by Hoaxe on 2007-03-29
I downloaded Mplayer through the package manager but the plugins don't work in firefox

everytime i try to watch a video on firefox, it's using Totem to read the stream.

any one else having this problem?

---

### Post by Flashgordon20 on 2007-03-29
This tutorial might solve that problem. [http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html](http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html)

---

### Post by Obor on 2007-03-29
```
sudo apt-get remove totem-mozilla
sudo apt-get install mozilla-mplayer
```

should work

---

### Post by Ambimom on 2007-03-29
Firefox has an extension (MediaPlayer Connectivity) that might help you configure the defaults too.

---

### Post by Hoaxe on 2007-03-29
awesome. the code worked very well.

now i have other issues though. my default player is still Totem, which i don't have anymore. and Mplayer can't read a *.Mov file that i download [just a regular quick time file] it's something about a device that isn't loaded or something.

i'll look into all of it when i get home, cuz for the next 5 hours, it's working time!

thanks everyone.

---

