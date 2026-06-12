---
title: "Play .mov files"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by tirengarfio on 2007-04-05
Hi,

I want to see a mov file, 

what i have to do at edgy?

---

### Post by davidexpogon on 2007-04-05
Hi,

you can see it with mplayer or vlc

---

### Post by bashologist on 2007-04-05
To install mplayer enable the extra repositories then paste these lines:
if sudo apt-get install mplayer; then cd /tmp; wget [noparse]http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2[/noparse] \
&& tar -xvjf all-20061022.tar.bz2; sudo mkdir /usr/lib/win32; sudo mv all-20061022/* /usr/lib/win32/; fi

---

### Post by shirilover on 2007-04-05
You may want to use /usr/lib/codecs instead

---

