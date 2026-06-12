---
title: "how do i play .rm video"
date: 2008-09-28
forum: Multimedia Software
---

### Post by squiddy on 2008-09-28
hi.. 
i cannot play .rm video format.

i have tried with RealPlayer, but then all my video got bluish during playback..

here's the error with MPlayer 
[http://paste.ubuntu.com/51789/](http://paste.ubuntu.com/51789/)

---

### Post by DrMega on 2008-09-28
> **squiddy said:**
> hi.. 
i cannot play .rm video format.

i have tried with RealPlayer, but then all my video got bluish during playback..

here's the error with MPlayer 
[http://paste.ubuntu.com/51789/](http://paste.ubuntu.com/51789/)

Have you installed all the codecs? Most are not there by default. If memory serves me right there is a package which you can find in Synaptic called 'Linux-restricted-extras' that contains them.

---

### Post by steveneddy on 2008-09-28
From a link in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron)

then install VLC media player.

```
sudo apt-get install vlc
```

---

### Post by squiddy on 2008-09-28
from 2 responses above, yes, i have installed ubuntu-restricted-extras ad VLC.. both didn't came up with solution for me :(

---

### Post by squiddy on 2008-09-28
it worked after i install w32codecs from medibuntu repo

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install w32codecs


thx for the responses

---

