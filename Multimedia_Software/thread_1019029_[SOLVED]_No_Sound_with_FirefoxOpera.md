---
title: "[SOLVED] No Sound with Firefox/Opera"
date: 2008-12-22
forum: Multimedia Software
---

### Post by Terraman on 2008-12-22
Hi,

Despite the fact that I can listen a CD or radio from Rhythmbox, I can not listen from the WEB with Firefox or Opera, e.g. YouTube.

Any help?

Thanks in advance!

Ubuntu 8.10

---

### Post by poo_22 on 2008-12-24
same here. Happend when i switched to Intrepid. Flash works for sure though because i can watch youtube, just no sound :(

---

### Post by linux_tech on 2008-12-24
If you are using intrepid and havn't already installed these, they are recommended:
```

sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:
```
gnome-volume-control
```

To open gnome-alsamixer type
```
gnome-alsamixer
```

---

### Post by namdung on 2008-12-24
Try reinstalling flash player. But 1st remove the current flash plugin, download one from adobe website and install.

[http://ubuntuforums.org/showthread.php?t=1012893](http://ubuntuforums.org/showthread.php?t=1012893)
[http://ubuntuforums.org/showthread.php?t=1013945](http://ubuntuforums.org/showthread.php?t=1013945)

---

### Post by HamHamT on 2009-01-03
im also having this problem, it took me a dumbass while (3 days) to get my sound finally working, but it doesnt work for youtube in opera, and also when trying to use other music players beside rhythom box i dont get any sound either

any clue anyone?

---

