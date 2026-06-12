---
title: "new user cant get video"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by Xxbrandnew10xX on 2008-03-24
I just installed gutsy today and have been working out my wireless kinks and everything seems to work awesome i even got the cube to work with compiz but now i notice when i search the web under firefox i cant view any video streaming or downloadable  ex: youtube, or google video any ideas 
Ive been trying to search for anything on this but i cant find anything.

I found where i can download real player, but im not sure i never really liked realplayer is there a better alternative

---

### Post by wolfen69 on 2008-03-24
the following is what *_i do_* to get multimedia working.

first, go to system>admin>software sources and check off all boxes. close and reload.

open terminal and:

```
sudo apt-get remove --purge totem-mozilla
```
```
sudo apt-get install mozilla-mplayer vlc flashplugin-nonfree
```
try that

to watch DVD's:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

---

### Post by muchas on 2008-03-24
you can just use the code ```
sudo apt-get gstreamer*
``` it will install all gstreamer package.

---

