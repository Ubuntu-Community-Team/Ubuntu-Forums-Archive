---
title: "playing a the rmvb format"
date: 2009-10-29
forum: Multimedia Software
---

### Post by 10ghost on 2009-10-29
I tried playing a video file with the format rmvb on vlc but it could not play it. THose anyone know a video player that can play this format or is there something i can do to my vlc to play such?

---

### Post by RichardLinx on 2009-10-29
Open a terminal and type:
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

```
sudo apt-get install w32codecs
```

.RM and .RMVB files should play fine in VLC and Totem now.

---

### Post by andrew.46 on 2009-10-29
Hi Richard,

> **RichardLinx said:**
> 

```
sudo apt-get install w32codecs
```

.RM and .RMVB files should play fine in VLC and Totem now.

I do not know much about Totem but I believe the w32codecs will only be of use to vlc if the *--enable-loader* configure option has been used during compilation, and this is not true of the Ubuntu repository versions of vlc. However if the OP is running a 32bit system installing MPlayer + the w32codecs + SMPlayer might be a good option...

Andrew

---

