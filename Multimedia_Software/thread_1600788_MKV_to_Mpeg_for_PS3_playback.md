---
title: "MKV to Mpeg for PS3 playback"
date: 2010-10-19
forum: Multimedia Software
---

### Post by F12OST on 2010-10-19
B4 I had ubuntu i use win7 and use mkv2vob to mux to mpeg for playback  on ps3 but what can i use to convert in linux and not with wine thanks

---

### Post by sohlinux on 2010-10-19
> **F12OST said:**
> B4 I had ubuntu i use win7 and use mkv2vob to mux to mpeg for playback  on ps3 but what can i use to convert in linux and not with wine thanks

mencoder will do it :)

---

### Post by F12OST on 2010-10-19
thanks ill give it a go

---

### Post by F12OST on 2010-10-19
please help what the commands to covert mkv x264 720p/1080p files to mpeg for ps3

---

### Post by sohlinux on 2010-10-19
> **F12OST said:**
> please help what the commands to covert mkv x264 720p/1080p files to mpeg for ps3

it may be easier to use a gui for mencoder, there are several options, I think this one will do the trick [http://gmencoder.sourceforge.net/](http://gmencoder.sourceforge.net/)

mplayer also will serve as a gui for mencoder

---

### Post by F12OST on 2010-10-19
bit dumb but how do u install that program im new

---

### Post by sohlinux on 2010-10-19
> **F12OST said:**
> bit dumb but how do u install that program im new


yep linux can get a bit complicated, if you dont already have make installed you need to install it first then type 

 tar xvzf package.tar.gz (or tar xvjf package.tar.bz2) depending on package type

cd package

./configure

 make

 make install

or maybe you will find the following thread easier

MKV to PS3 conversion
[http://ubuntuforums.org/showthread.php?t=548547](http://ubuntuforums.org/showthread.php?t=548547)

:)

---

### Post by F12OST on 2010-10-19
its gmencoder-0.1.0.tgz

---

### Post by F12OST on 2010-10-19
Update 

I managed to get that mkv2vob working in wine finally mwahhh , I use this [link ]("http://www.unyttig.info/2009/04/23/it-works-mkv2vob/")

---

### Post by Ferrat on 2010-10-19
Have you looked in to Playstation Media Server? with that you don't need to encode them but for 1080p it needs a dual core at the least, quad is recommended for heavier mkv files.

---

### Post by F12OST on 2010-10-19
Na I rather use the power of the ps3 to play my HD content and with that streaming u have the problems with not been able to rewind n forward good plus I like having a standalone player until I save enough to get a banging pc to handle HD well and for Diablo3

---

### Post by sohlinux on 2010-10-20
> **F12OST said:**
> Update 

I managed to get that mkv2vob working in wine finally mwahhh , I use this [link ]("http://www.unyttig.info/2009/04/23/it-works-mkv2vob/")

great:P

---

### Post by heyjean on 2010-10-20
information from this post may also be helpful.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1064999](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1064999)

---

### Post by yavez on 2010-10-21
1. Extract the streams from MKV with MKVExtract (commandline)

2. Mux them into an .m2ts container with TSMuxer

3. Playback natively on PS3


MKV Extract is part of the MKVTOOLNIX package

```
sudo apt-get install mkvtoolnix
```

TSMuxer can be downloaded here: 
[http://www.smlabs.net/tsmuxer_en.html](http://www.smlabs.net/tsmuxer_en.html)

---

### Post by HiFiJive on 2010-11-12
I have been trying to figure out a way to re-encode mkv files to m2ts so the PS3 could stream them from my nas. After searching and following some wild geese I stumbled on [tsmuxer]("http://www.smlabs.net/tsmuxer_en.html"). I just dropped the binaries into /usr/local/bin and ran the gui.. if you'r a command line guy I can paste in a sample meta file. 

Since the readme is in russian only here is how you use it on command line.

tsMuxeR mymovie.meta /media/nas/movies/mymovies.m2ts

The source file is referenced in mymovie.meta. Best of all w/the movie I mux'd I was able to get Dolby digital 5.1 to my receiver! That almost never works. I'll have to run a few more through to see if its consistent.

---

### Post by coriolus on 2011-03-15
Try this:

[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589&start=420](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589&start=420)

---

