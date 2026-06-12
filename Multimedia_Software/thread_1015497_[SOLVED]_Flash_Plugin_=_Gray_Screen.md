---
title: "[SOLVED] Flash Plugin = Gray Screen"
date: 2008-12-18
forum: Multimedia Software
---

### Post by xHero on 2008-12-18
When I load a youtube video, I get a grey screen.  Sometimes audio plays, sometimes it doesn't.  I used to be able to fix this (sometimes) by refreshing, now nothing seems to be working.

On the wiki it said to run:
```
sudo update-flashplugin
```

However, I get the following error:
sudo update-flashplugin

How can I fix this?

---

### Post by Existentialist on 2008-12-19
Are you running the 32, or 64 bit version of Ubuntu?  I'm running 64 bit and have been running the alpha version of flash player 10 from adobe for a while now.  It has worked much better than the flashplugin-nonfree I was using before which often resulted in the same errors you are experiencing.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by xHero on 2008-12-19
I'm running 64bit.  I'll try that out tomorrow.  Thanks

---

### Post by Existentialist on 2008-12-19
Not sure where the instructions for installing it are so:

-remove current flash player:
>sudo apt-get purge flashplugin-nonfree

-extract the TAR.GZ you downloaded

-copy the extracted libflashplayer.so to /usr/lib/mozilla/plugins/

-restart firefox

---

### Post by xHero on 2008-12-19
This has been working perfectly, thanks!

---

