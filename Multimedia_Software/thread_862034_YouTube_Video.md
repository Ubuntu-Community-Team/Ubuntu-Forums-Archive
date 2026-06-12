---
title: "YouTube Video"
date: 2008-07-17
forum: Multimedia Software
---

### Post by smallsea on 2008-07-17
Perhaps I'm very very dim but when I load YouTube in firefox on an up-to-date hardy heron laptop the video simply and silently fails to play. Not so much as a whimper or an error message! Why please?

---

### Post by Sef on 2008-07-17
Have you installed Adobe Flash?  It is in Add/Remove.  Applications > Add/Remove > Search: Adobe Flash > click on the Macromedia Flash box > apply changes > apply > close.

---

### Post by smallsea on 2008-08-06
Thanks Sef. Now I've installed the Macromedia Flash plugin but oddly enough it doesn't show up in add-ons > plugins, in firefox. Shockwave Flash 8 and 9 are there OK but no Macromedia Flash!? Oh and youtube video still fails silently.

---

### Post by Guy_AD on 2009-04-18
Try
```
sudo apt-get install flashplugin-nonfree
```

If that doesn't work, go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and select ".deb for Ubuntu 8.04+" and install it.

---

### Post by matrixblue on 2009-04-18
Make sure swdef and and gnash aren't installed. Type about:plugins in the address bar in FireFox and press enter.

Verify that for Shockwave flash you have:

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

---

