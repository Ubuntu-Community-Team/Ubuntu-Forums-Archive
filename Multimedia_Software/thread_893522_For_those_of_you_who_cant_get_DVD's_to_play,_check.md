---
title: "For those of you who cant get DVD's to play, check this out..."
date: 2008-08-18
forum: Multimedia Software
---

### Post by kh1116 on 2008-08-18
GeeXboX:
> GeeXboX is a free embedded Linux distribution which aims at turning your computer into a so called HTPC (Home Theater PC) or Media Center. Being a standalone LiveCD-based distribution, it's a ready to boot operating system than works on any Pentium-class x86 computer or PowerPC Macintosh, implying no software requirement. You can even use it on a diskless computer, the whole system being loaded in RAM.

Despite his tiny ISO image size, the distribution comes with a complete and automatic hardware detection, not requiring any driver to be added. It supports playback of nearly any kind of audio/video and image files and all known codecs and containers are shipped in, allowing playing them through various physical supports, either being CD, DVD, HDD, LAN or Internet. 

i couldnt get my dvd's to play in ubuntu, so here is my solution... reboot and insert the GeeXboX cd. It is basically a live cd media player about 10mb  that loads itself on the ram so you can play dvd's.

---

### Post by wolfen69 on 2008-08-18
for a more permanent solution, open terminal, and copy and paste the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2 vlc
``` (i threw in vlc for good measure)

if you use a different version of ubuntu, just replace "hardy" (in the first line) with gutsy, feisty, etc.

enjoy your movies.

---

### Post by vanden12 on 2008-08-18
O use linux mint I think that has out of the box dvd playblack..

---

### Post by SuperSonic4 on 2008-08-18
Yeah, Linux mint is essentially ubuntu with codecs pre installed

---

### Post by pparks1 on 2008-08-18
I do just what wolfen69 suggests and it works no problem.  I use gxine as my DVD player...but to each his own.

---

