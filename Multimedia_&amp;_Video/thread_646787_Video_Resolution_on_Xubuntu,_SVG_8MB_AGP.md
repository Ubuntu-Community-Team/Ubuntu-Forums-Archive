---
title: "Video Resolution on Xubuntu, SVG 8MB AGP"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by necodemus on 2007-12-21
I have a Intel PIII 550 mhz Emachine w/ a Savage 8mb AGP video card.  My max resultion is 640x480.  That aint gonna work :)  Any ideas, I have read over the Ubuntu site but cant get none of their stuff to work.

I am running Xubuntu 6.xx

Also...is Wine available on Xubuntu?  I cant find it in the Package Manager.

---

### Post by mouseboyx on 2007-12-21
Run this command: ```
dpkg-reconfigure xserver-xorg
``` and tell the reconfig to use the resolution you want.

And you probably need to update your, package lists for it to appear in the package manager:

```
sudo apt-get update
```

---

### Post by necodemus on 2007-12-21
ok, the 2nd item did some stuff and downloaded some headers.  Great, but the first thing about reseting the resolution states that the file must be run as a root.  I have no idea how to do that.  

Any more help would be greatly appreriated.

Necodemus

---

### Post by The Mad Scientist on 2007-12-26
Use "sudo" before the first command, just like you did before the second, and you should be good.

---

### Post by Yellow Pasque on 2007-12-26
To add WINE to your sources, go here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by pinoyboyf4i on 2008-01-22
Thanks mouseboyx.  dpkg-reconfigure xserver-xorg helped me get 1400x1050 resolution on my T21 with Savage IX on 7.10.

---

