---
title: "Ubuntu 64-bit and flash"
date: 2009-09-15
forum: Multimedia Software
---

### Post by ravalox on 2009-09-15
Okay so I've got a 64-bit installation of 8.04 that I've struggled to get flash working with.  I finally got it working using this:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Which worked until I closed the browser, I opened it and the icons are missing on the theme and flash isn't working.  Going through the troubleshooting I managed to get my icons back, but flash is still busted.  Tried changing permissions on the flash plugin folder with no joy.  So what am I left with aside from scrapping Ubuntu?

---

### Post by steveneddy on 2009-09-15
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by HappyFeet on 2009-09-15
I am running 64bit ubuntu with the 64bit flash plugin no problems.

Remove whatever flash (or gnash) you have installed first.

Go [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and download the 64bit flash file. Right click and **extract here**. Then copy the resulting **libflashplayer.so** file. Then go to your home folder and do Ctrl-H. You will now see the hidden folders that start with a dot. Open the .mozilla folder and create a new folder called **plugins**. Paste the **libflashplayer.so** file there. Close out and restart firefox.

---

