---
title: "how do you play dvds"
date: 2009-02-22
forum: Multimedia Software
---

### Post by wolfman1221 on 2009-02-22
So I have finally managed to install a copy of ubuntu, and I would now like to watch the dark knight on dvd. If anyone knows how I would go about this it would be of great help to me. I would like to do it in a legal way if possible.

---

### Post by binbash on 2009-02-22
add medibuntu to your repos (google > medibuntu) then, install these : 

sudo apt-get install vlc w32codecs libdvdcss2

PS : you dont need w32codecs for playing dvds but you will need it at playing other video files.

---

### Post by theozzlives on 2009-02-22
> **wolfman1221 said:**
> So I have finally managed to install a copy of ubuntu, and I would now like to watch the dark knight on dvd. If anyone knows how I would go about this it would be of great help to me. I would like to do it in a legal way if possible.

Go to Applications > Accessories > Terminal and type at the prompt:
```
sudo apt-get install ubuntu-restricted-extras libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
Then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by wolfman1221 on 2009-02-22
this is how it responded. 





sudo apt-get install vlc w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by wolfman1221 on 2009-02-22
is that the legal way to do it, ozz

---

### Post by binbash on 2009-02-22
yes it is legal, just remove the w32codecs from the list : 

sudo apt-get install vlc  libdvdcss2

---

