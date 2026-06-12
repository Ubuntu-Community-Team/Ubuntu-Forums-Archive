---
title: "Problem with flash sound on ubuntu 9.10"
date: 2010-04-10
forum: Multimedia Software
---

### Post by Maragato on 2010-04-10
Folks flash has no sound here Ive looked on the forums and tried the suggested solutions as [http://kubuntuforums.net/forums/index.php?topic=3102419.0](http://kubuntuforums.net/forums/index.php?topic=3102419.0) and [http://ubuntuforums.org/showthread.php?t=1306234](http://ubuntuforums.org/showthread.php?t=1306234) no luck thou. What else can I do?
Btw for multimidia as amarok sound is oki.

---

### Post by WinterRain on 2010-04-10
Remove the flash you have, and download the latest [64bit Flash Plugin]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz"). Then extract the file and put libflashplayer.so file into /usr/lib64/mozilla/plugins

Restart firefox.

---

### Post by Maragato on 2010-04-10
> **WinterRain said:**
> Remove the flash you have, and download the latest [64bit Flash Plugin]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz"). Then extract the file and put libflashplayer.so file into /usr/lib64/mozilla/plugins

Restart firefox.

It did work thanks a lot.

---

