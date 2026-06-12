---
title: "Mplayer can't detect libmp3lame"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by reloadxero on 2008-01-19
i'm running a debian server and i cant get mplayer to recognize libmp3lame

i installed lame-3.97.tar.gz

after that i extract 

MPlayer-1.0rc1.tar.tar

and run 

./configure

**Checking for libmp3lame (for mencoder) ... no**

this is line should be yes because i already have lame installed why does it not see the libraries?

been trying for 6 hours now. please help.

---

### Post by cor2y on 2008-01-19
latest stable mplayer is Mplayer-1.0rc2
Latest stable mp3lame is indeed 3.97.
first of uninstall the version you compiled and use liblame-dev in synaptic see if that is recognized.
If that is not listed in synaptic you need to enable the restricted repos universal,multiverse etc.
Remember if you have all the restricted repos enabled then most of the dev files necessary to compile mplayer are already there, only esoteric ones like the libraries necessary for 3gp support and libdvdnav etc will have to be self compiled.

---

