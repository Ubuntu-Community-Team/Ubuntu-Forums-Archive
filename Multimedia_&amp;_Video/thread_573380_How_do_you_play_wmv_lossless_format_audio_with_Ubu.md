---
title: "How do you play wmv lossless format audio with Ubuntu?"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by smacfarl on 2007-10-11
I have a large (60gigs) collection of ripped music from my CD collection. I ripped it lossless on Windows, now that I am on Ubuntu I would like to listen to this music.

If I can't listen to WMV lossless, does any one know of a freeware conversion tool so that I can convert the files to flac?

Thoughts?

---

### Post by nzadLithium on 2007-10-11
dunno about how to convert it. You might want to try soundconverter i reckon it will be able to do it. Its in synaptic. and wouldn't you have ripped it as a wma? seems odd to rip sound to a video format :S

VLC should be able to play wma's. All the wma's i played with it worked without any trouble.

---

### Post by kostkon on 2007-10-11
If they are not encrypted it's easy to play them. Most of the media players will be able to play these files out of the box, some of them maybe will need the *w32codecs* packages to be installed. This package provides various codecs that are only native to Windows.

In my case, I can play *wma* files with both *Totem* and *Rhythmbox*, the two media players on my system.

I believe you will be able to convert them to another format, e.g. *ogg* or *mp3*, with *ffmpeg*. You will need to install the version of *ffmpeg* that is provided by the [*Medibuntu*]("http://medibuntu.org/") repository.

Put this repository to you software sources list ([here]("http://help.ubuntu.com/community/Medibuntu") you will find how to do it), then go to Synaptic and install *ffmpeg*.

Because *ffmpeg* is a command line tool, it would be better to find a graphical front-end for it. There are many, just search this forum or use *Google*, for example. I can recommend you one, although is very simplistic: [*WinFF*]("http://biggmatt.com/winff/").

---

### Post by smacfarl on 2007-10-13
So installing the 1007 w32codecs which supposed has a wma library does not work.

The debian package installed but every media player chokes when trying to open or play wma lossless. Any suggestions?

---

