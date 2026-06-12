---
title: "Problems with Totem Movie Player"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by DrScum on 2007-05-13
I try to playback a DVD using Totem. On the first attempt I am told that the necessary codecs are not installed, but they are searched for and installed.
After that Totem tells me that I cannot play the movie since the appropriate plugins are not installed. Where do I get those?

(using ubuntu 7.04)

---

### Post by bear54 on 2007-05-13
Hello I have the same problem. If I find a fix I will let you know. I also have another question related to totem. On some web sites to view the video windows media player is required. Can totem view this type of media file with the correct plugin? Maybe a player other than totem would work better.  Any help is greatly appreciated!
Bear54 :cool:

---

### Post by Iceni on 2007-05-15
Do as follows:

```
gksudo gedit /etc/apt/sources.list
```

add the following:

```
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

save and close

then
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

then

```
sudo apt-get update
```

then two final steps:

```
sudo apt-get install libdvdcss2 w32codecs libdvdread3
```

and finally

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

hope this helps!

---

### Post by juseal on 2007-05-17
Thanks sooo much!  Worked like a charm!

---

