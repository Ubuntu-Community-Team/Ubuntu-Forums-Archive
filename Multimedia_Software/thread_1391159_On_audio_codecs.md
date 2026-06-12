---
title: "On audio codecs"
date: 2010-01-26
forum: Multimedia Software
---

### Post by white_tigris on 2010-01-26
Hello, tell me please, how I can use in my Kubuntu 9.10, audio codec - <voxware metasound audio codec>?
 P.S. Sorry for my bad english. I look forward to an answer, thanks you.

---

### Post by myth1914 on 2010-01-26
Are you asking how to install the codec or how to force it's use on a particular file?

---

### Post by white_tigris on 2010-01-26
How i can view video-file whith sound. I have Kubuntu amd64.

---

### Post by llawwehttam on 2010-01-26
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo apt-get install libdvdread4
```

---

### Post by myth1914 on 2010-01-26
Try this:  [http://ubuntuforums.org/showthread.php?p=8725914](http://ubuntuforums.org/showthread.php?p=8725914)

Also, to install additional codecs and various other "non-free" stuff, run the following:

sudo aptitude install ubuntu-restricted-extras

---

### Post by white_tigris on 2010-01-26
I did it, did not help ((

---

### Post by Chris Musampa on 2010-01-26
It depends which video player you're using, try:
sudo aptitude install **k**ubuntu-restricted-extras

---

### Post by white_tigris on 2010-01-26
already installed ((. VideoPlayers: DragonPlayer, Mplayer, VLC, xine. and nothing ((

I have found in previous issues that need to install, w32codecs, and this package I have already installed

---

